# 如何获得确定性的 word2vec/doc2vec/paragraph 向量

> 原文：<https://pub.towardsai.net/how-to-get-same-word2vec-doc2vec-paragraph-vectors-in-every-time-of-training-335bac809c83?source=collection_archive---------1----------------------->

![](img/70acedde766255842350113467c63b64.png)

## 面向 AI 的文字嵌入和语言建模|

好了，欢迎来到我们的**嵌字系列**。这篇文章是这个系列的第一个故事。你可能会发现这个故事适合中级以上，在 [word2vec，或 doc2vec/paragraph vectors](https://skymind.ai/wiki/word2vec) 上训练过或至少尝试过一次的人。但是不要担心，我会在接下来的文章中介绍背景、先决条件和知识以及代码如何实现它。

我会尽力不把你重定向到其他一些要求你阅读乏味教程并以放弃告终的链接(相信我，我是大量在线教程的受害者:)。我想让你**和我一起从编码层面**理解单词向量，这样我们就可以知道**如何设计和实现我们的单词嵌入和语言模型**。

如果你有机会自己训练单词向量，你可能会发现，即使你输入相同的训练数据，每次训练的模型和向量表示也是不同的。这是因为在训练时间中引入了随机性。代码会自己说话，我们来看看随机性从何而来，如何彻底消除。我将使用 [DL4j](https://deeplearning4j.org/) 的[实现](https://github.com/deeplearning4j/deeplearning4j/blob/master/deeplearning4j/deeplearning4j-nlp-parent/deeplearning4j-nlp/src/main/java/org/deeplearning4j/models/paragraphvectors/ParagraphVectors.java)的[段向量](https://deeplearning4j.org/docs/latest/deeplearning4j-nlp-doc2vec)来显示代码。如果你想看看另一个包，去 [gensim 的 doc2vec](https://radimrehurek.com/gensim/models/doc2vec.html) ，它有相同的实现方法。

# 随机性从何而来

## 模型权重和向量表示的初始化

我们知道在训练之前，模型和向量表示的权重会随机初始化，而随机性是由[种子](https://en.wikipedia.org/wiki/Random_seed)控制的。因此，如果我们将种子设置为 0，那么每次都会得到完全相同的初始化。这里是[种子生效的地方](https://github.com/deeplearning4j/deeplearning4j/blob/3c66853115e0d500cf1cafc0e060478766de4f03/deeplearning4j/deeplearning4j-nlp-parent/deeplearning4j-nlp/src/main/java/org/deeplearning4j/models/embeddings/inmemory/InMemoryLookupTable.java#L141)。这里`syn0`是模型权重，由`Nd4j.rand`初始化

```
// Nd4j takes seed configuration here
Nd4j.*getRandom*().setSeed(configuration.getSeed());// Nd4j initializes a random matrix for syn0
syn0 = Nd4j.rand(new int[] {vocab.numWords(), vectorLength}, rng).subi(0.5).divi(vectorLength);
```

## PV-DBOW 算法

如果我们使用 [PV-DBOW](https://cs.stanford.edu/~quocle/paragraph_vector.pdf) 算法(我将在下面的帖子中详细解释)来训练段落向量，在训练的迭代过程中，它会从文本窗口中随机地对单词进行二次采样，以计算并更新权重。但这种随机并不是真正的随机。让我们看看[代码](https://github.com/deeplearning4j/deeplearning4j/blob/3c66853115e0d500cf1cafc0e060478766de4f03/deeplearning4j/deeplearning4j-nlp-parent/deeplearning4j-nlp/src/main/java/org/deeplearning4j/models/sequencevectors/SequenceVectors.java#L1205)。

```
// next random is an AtomicLong initialized by thread id
this.nextRandom = new AtomicLong(this.threadId);
```

`nextRandom`用于

```
trainSequence(sequence, **nextRandom**, alpha);
```

在`trainSequence`里面，它会做什么

```
nextRandom.set(nextRandom.get() * 25214903917L + 11);
```

如果我们在训练步骤上更深入，我们会发现它以同样的方式产生`nextRandom`，即做同样的数学运算(去[这个](https://en.wikipedia.org/wiki/Linear_congruential_generator)和[这个](http://www.cburch.com/logisim/docs/2.3.0/libs/mem/random.html)知道为什么)，所以这个数字只依赖于线程 id，其中线程 id 是 0，1，2，3，…。因此，它不再是随机的。

## 并行令牌化

由于复杂文本的处理可能是耗时的，所以它用于并行标记，并行标记可以帮助提高性能，但不能保证训练之间的一致性。由 tokenizer 处理的序列可以以随机顺序送入线程进行训练。从[代码](https://github.com/deeplearning4j/deeplearning4j/blob/3c66853115e0d500cf1cafc0e060478766de4f03/deeplearning4j/deeplearning4j-nlp-parent/deeplearning4j-nlp/src/main/java/org/deeplearning4j/models/word2vec/wordstore/VocabConstructor.java#L257-L264)中可以看出，如果我们将`allowParallelBuilder`设置为 false，那么正在进行标记化的`runnable`将一直等待，直到标记化完成，这样就可以保持给料数据的顺序。

```
**if** (!**allowParallelBuilder**) {
    **try** {
        runnable.awaitDone();
    } **catch** (InterruptedException e) {
        Thread.*currentThread*().interrupt();
        **throw new** RuntimeException(e);
    }
}
```

## 为每个要训练的线程提供序列的队列

这个 [LinkedBlockingQueue](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/LinkedBlockingQueue.html) 从训练文本的迭代器中获取序列，并将这些序列提供给每个线程。由于每个线程可以随机出现，所以在每次训练中，每个线程可以得到不同的序列进行训练。让我们看看这个数据提供者的[实现](https://github.com/deeplearning4j/deeplearning4j/blob/3c66853115e0d500cf1cafc0e060478766de4f03/deeplearning4j/deeplearning4j-nlp-parent/deeplearning4j-nlp/src/main/java/org/deeplearning4j/models/sequencevectors/SequenceVectors.java#L1037-L1130)。

```
// initialize a sequencer to provide data to threads
val sequencer = new AsyncSequencer(this.iterator, this.stopWords);// each threads are pointing to the same sequencer 
// worker is the number of threads we want to use
for (int x = 0; x < workers; x++) {
    threads.add(x, new VectorCalculationsThread(x, ..., sequencer);                
    threads.get(x).start();            
}// sequencer will initialize a LinkedBlockingQueue buffer
// and maintain the size between [limitLower, limitUpper]
private final LinkedBlockingQueue<Sequence<T>> buffer;
limitLower = workers * batchSize;
limitUpper = workers * batchSize * 2;// threads get data from the queue through
buffer.poll(3L, TimeUnit.SECONDS);
```

因此，如果我们将一个工人的数量设置为 1，它将在一个单独的线程中运行，并且在每次训练中具有完全相同的数据输入顺序。但是请注意，单线程会极大地降低训练速度。

## 总结

总结一下，下面是我们要彻底排除随机性需要做的:
**1。将种子设置为 0；
2。将 allowParallelTokenization 设置为 false
3。将工作线程数设置为 1。**
那么如果馈入相同的数据，我们会得到完全相同的单词向量和段落向量的结果。

最后，我们训练的代码是这样的:

```
ParagraphVectors vec = **new** ParagraphVectors.Builder()
                .minWordFrequency(1)
                .labels(labelsArray)
                .layerSize(100)
                .stopWords(**new** ArrayList<String>())
                .windowSize(5)
                .iterate(iter)
                .allowParallelTokenization(false)
                .workers(1)
                .seed(0)
                .tokenizerFactory(t)
                .build();

vec.fit();
```

如果你觉得

![](img/1fd31262d2c594aab8802a466788c5e7.png)

请关注接下来关于**单词嵌入和语言模型**的故事，我为你准备了盛宴。

## 参考

> [1] Deeplearning4j、ND4J、DataVec 等——面向 Java/Scala 的深度学习和线性代数，采用 GPU+Spark——来自 sky mind[http://deeplearning4j.org](http://deeplearning4j.org/)[https://github.com/deeplearning4j/deeplearning4j](https://github.com/deeplearning4j/deeplearning4j)
> 
> [2] Java 平台，标准版 8 API 规范[https://docs.oracle.com/javase/8/docs/api/](https://docs.oracle.com/javase/8/docs/api/)
> 
> [3]https://giphy.com/
> 
> [4]https://images.google.com/