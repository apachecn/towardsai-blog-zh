# 变压器神奇应用之旅——第一部分

> 原文：<https://pub.towardsai.net/a-journey-into-the-fabulous-applications-of-transformers-part-1-630cc80e3ce6?source=collection_archive---------1----------------------->

## 演示重点是使用 Python 的 NLP，拥抱脸。

![](img/c6218183058cf80fe8c9b52c31ccbb95.png)

阿瑟尼·托古列夫在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

变形金刚的出现对人工智能产生了巨大的影响，尤其是在自然语言处理领域。

> 变形金刚为人们期待已久的自然语言处理迁移学习的成功铺平了道路。

因此，许多大型语言模型应运而生，现在我们能够在这些尖端模型之上构建有益的应用程序。

一个[转换器](https://arxiv.org/pdf/1706.03762.pdf)用更简单的语言来说就是一个两端都有[自关注](https://machinelearningmastery.com/the-transformer-attention-mechanism/)机制的编码器-解码器架构。编码器模块接收输入并将其转换为数字形式，解码器模块接收该数字形式并将其转换为文本。为了将本文局限于变压器的特定应用，我们将不深入研究其架构。请浏览*参考章节*中的链接，了解变压器的架构、发展和基本原理。

# 为什么是变形金刚？

变形金刚通过启用从预训练模型中提取的特征的可用性，帮助在 NLP 中成功建立**[**迁移学习**](https://towardsdatascience.com/a-gentle-introduction-to-transfer-learning-in-nlp-b71e87241d66)**。****

> ****这个想法是利用一个经过海量文本数据预处理的模型(也称为[大型语言模型](https://www.kdnuggets.com/2022/09/john-snow-top-open-source-large-language-models.html))，根据我们自己的目的对其进行微调。随着大量时间和费用的节省，对大量训练数据的需求也大大减少，因为我们使用的是一个已经预先训练好的模型。****

****这反过来又引发了对变压器的广泛研究，并带来了许多 NLP 预训练模型的存在。这些模型使得许多应用程序的实现成为可能，并使自然语言处理中的迁移学习得以发展。****

# ****拥抱脸****

****[拥抱脸](https://huggingface.co/)是一个由人工智能爱好者建立的图书馆，在这里无数的模型被建立并与社区共享。拥抱脸由[预训练模型](https://huggingface.co/models)组成，用于计算机视觉、自然语言处理、音频处理、表格数据、强化学习和多模态应用等领域。使用 API(应用程序编程接口)可以很容易地访问所有模型****

> ****本文的目的是利用 NLP 领域，并通过演示代码和解释来探索可能的应用。****

****要使用任何拥抱脸模型，第一步是安装如下的`transformers`库。****

```
**pip install transformers**
```

****下一步是利用`pipeline`，它有助于隐藏模型实现背后的所有复杂步骤，并为模型提供一个简单易用的 API。对于下面提到的每个主要应用程序，我们将看到代码和解释。拥抱脸**中有许多模式可用于每个领域的每个任务**。因为这篇文章是关于应用程序的感知，我们将利用库本身设置的默认模型。此外，考虑到本文是关于这些可能性的介绍，关于模型的细节可以从每一节给出的链接中查阅。****

# ****应用程序****

****在本文讨论的所有应用程序中，我们都将遵循这些步骤。****

> ****1.进口`pipeline`****
> 
> ****2.通过实例化`pipeline.`来调用相应任务的模型。在该步骤中，下载任务的默认模型的模型权重。****
> 
> ****3.通过给出所需的输入来利用该模型。****
> 
> ****4.查看结果并尝试不同的输入。****

****所有应用程序的代码和输出都在这个 [GitHub 库](https://github.com/dharini-projects/NLP_Applications_with_Transformers)中给出，还有一个 Google Colab 链接。****

****本文中讨论的应用有****

> ****[1。文本分类](#af17)****
> 
> ****[2。文本摘要](#f630)****
> 
> ****[3。问题解答](#0a57)****
> 
> ****[4。文本生成](#2dc3)****
> 
> ****[5。命名实体识别](#af1d)****

## ****1.文本分类****

****分类是将给定文本放入任何一个已知类别的过程。让我们开始导入所需的库，如下所示。****

****下一步是初始化一个名为`text_classifier`的变量，它表示在`text-classification`类别中被调用的模型。我们知道，模型是由`pipeline`函数使用任务名调用的。由于没有给出具体的模型名称，因此将下载默认模型(`distilbert-base-uncased-finetuned-sst-2-english`)，这可以在下面的输出中看到。****

```
**from transformers import pipeline
text_classifier = pipeline("text-classification")

Output:
No model was supplied, defaulted to distilbert-base-uncased-finetuned-sst-2-english and revision af0f99b (https://huggingface.co/distilbert-base-uncased-finetuned-sst-2-english).
Using a pipeline without specifying a model name and revision in production is not recommended.
Downloading: 100%
629/629 [00:00<00:00, 24.4kB/s]
Downloading: 100%
268M/268M [00:05<00:00, 62.8MB/s]
Downloading: 100%
48.0/48.0 [00:00<00:00, 1.70kB/s]
Downloading: 100%
232k/232k [00:00<00:00, 6.48MB/s]**
```

****下一步，我们使用初始化变量`text_classifier.`向文本分类模型提供输入。被调用的模型帮助我们对给定文本进行分类，并对文本的`POSITIVE`和`NEGATIVE`情感进行评分。有关该型号的更多信息，请点击此[链接](https://huggingface.co/distilbert-base-uncased-finetuned-sst-2-english)。****

****在下面给出的代码中，给出了一个表示负面情绪的句子，结果存储在`clf_result.`中。在打印输出时，我们可以看到模型将该句子归类到`NEGATIVE`类别中，并给出了一个`score`(表示情绪得分)。****

```
**clf_result = text_classifier("Oh God!!!! Its so horrible to hear about the news of aircraft")
print(clf_result)

Output
[{'label': 'NEGATIVE', 'score': 0.9992474317550659}]**
```

****现在让我们试试另一个句子，看看结果。在下面的代码片段中，可以看到结果是`POSITIVE`标签，因为我们给出了一个表示解脱的语句。****

```
**clf_result = text_classifier("Oh God!!!! So relieved to hear about the aircraft")
print(clf_result)

Output
[{'label': 'POSITIVE', 'score': 0.9974811673164368}]**
```

## ****2.文本摘要****

****文本摘要是从给定的一组句子中提取摘要的任务。第一步是导入`pipeline`，接下来，我们用自己选择的任务进行实例化(`summarization`)。文本摘要的默认模型是`sshleifer/distilbart-cnn-12–6`，要了解关于该模型的更多信息，请查看此[链接](https://huggingface.co/sshleifer/distilbart-cnn-12-6)。在变量`text_summarizer.`下调用模型****

```
**from transformers import pipeline
text_summarizer = pipeline("summarization")

Output:
No model was supplied, defaulted to sshleifer/distilbart-cnn-12-6 and revision a4f8f3e (https://huggingface.co/sshleifer/distilbart-cnn-12-6).
Using a pipeline without specifying a model name and revision in production is not recommended.
Downloading: 100%
1.80k/1.80k [00:00<00:00, 47.4kB/s]
Downloading: 100%
1.22G/1.22G [00:50<00:00, 47.4MB/s]
Downloading: 100%
26.0/26.0 [00:00<00:00, 460B/s]
Downloading: 100%
899k/899k [00:00<00:00, 1.60MB/s]
Downloading: 100%
456k/456k [00:00<00:00, 1.73MB/s]** 
```

****下面的代码片段显示了加载了要汇总的文本的`input_text`变量。****

```
**input_text = """Education is a purposeful activity directed at achieving certain aims,
such as transmitting knowledge or fostering skills and character traits. 
These aims may include the development of understanding, rationality, kindness, and honesty. 
Various researchers emphasize the role of critical thinking in order to distinguish education 
from indoctrination. Some theorists require that education results in an improvement of the student 
while others prefer a value-neutral definition of the term. In a slightly different sense, education
may also refer, not to the process, but to the product of this process: the mental states and dispositions 
possessed by educated people. Education originated as the transmission of cultural heritage from one generation 
to the next. Today, educational goals increasingly encompass new ideas such as the liberation of learners, skills 
needed for modern society, empathy, and complex vocational skills."""**
```

****使用`text_summarizer,`我们给模型输入，以及一个提到摘要最大长度的参数。在打印输出时，我们可以看到如下摘要。****

```
**summary = text_summarizer(input_text, max_length =100)
print(summary[0]['summary_text'])

Output:
Some theorists require that education results in an improvement of the student.
Others prefer a value-neutral definition of the term. Education originated 
as the transmission of cultural heritage from one generation to the next. 
Today, educational goals increasingly encompass new ideas such as the 
liberation of learners, skills needed for modern society, empathy, and 
complex vocational skills.**
```

## ****3.问题回答****

****变形金刚的另一个有趣的应用是构建问答系统的能力。这个想法是提供一个模型，一组句子作为理解的背景。基于这种理解，模型给出了问题的答案。更简单地说，**模型理解上下文，并基于该上下文提取问题的相关答案。******

****为了利用 QA 模型，让我们首先用任务`question-answering`实例化`pipeline`。任务的默认模型是`[distilbert-base-cased-distilled-squad](https://huggingface.co/distilbert-base-cased-distilled-squad),`，因此模型权重被下载。正如我们在下面的代码片段中看到的，该模型使用用户定义的变量`qna_model`来引用。****

```
**from transformers import pipeline
qna_model = pipeline("question-answering")

Output:
No model was supplied, defaulted to distilbert-base-cased-distilled-squad and revision 626af31 (https://huggingface.co/distilbert-base-cased-distilled-squad).
Using a pipeline without specifying a model name and revision in production is not recommended.
Downloading: 100%
473/473 [00:00<00:00, 2.63kB/s]
Downloading: 100%
261M/261M [00:06<00:00, 51.3MB/s]
Downloading: 100%
29.0/29.0 [00:00<00:00, 508B/s]
Downloading: 100%
213k/213k [00:00<00:00, 1.49MB/s]
Downloading: 100%
436k/436k [00:00<00:00, 1.09MB/s]**
```

****下面，我们给出了一组关于 GitHub 的句子(`input_text`)，模型将其作为上下文进行学习。****

```
**input_text = """GitHub Inc is an Internet hosting service for software development 
and version control using Git. It provides the distributed version control of 
Git plus access control, bug tracking, software feature requests, task management,
continuous integration, and wikis for every project. Headquartered in California, 
it has been a subsidiary of Microsoft since 2018\. 
It is commonly used to host open source software development projects. 
As of June 2022, GitHub reported having over 83 million developers and more 
than 200 million repositories, including at least 28 million public 
repositories. It is the largest source code host as of November 2021.
"""**
```

****如下所示，我们根据`input_text` 提出了三个问题。`question_1`是提取 GitHub 的一个定义，`question_2`是为了提取一个数字，`question_3`是为了看模型如何根据上下文回答一个是/否的问题。****

```
**question_1 = "What is GitHub?"
question_2 = "How many repositories does GitHub have?"
question_3 = "Can I use GitHub to host my project?"**
```

****现在让我们将`input_text`作为上下文，将`question_1`作为问题提供给模型，并打印出答案。瞧，我们有一个模型可以帮助我们理解一篇文章并快速得到答案！！****

```
**answer_1 = qna_model(question = question_1, context = input_text)
print(answer_1)

Output:
{'score': 0.17357327044010162,
 'start': 14,
 'end': 86,
 'answer': 'an Internet hosting service for software development and version control'}**
```

****同理，让我们试试另外两个问题，看看结果。****

```
**answer_2 = qna_model(question = question_2, context = input_text)
print(answer_2)

Output:
{'score': 0.3084281086921692,
 'start': 506,
 'end': 527,
 'answer': 'more than 200 million'}**
```

```
**answer_3 = qna_model(question = question_3, context = input_text)
answer_3

Output:
{'score': 0.471432626247406,
 'start': 364,
 'end': 433,
 'answer': 'It is commonly used to host open source software development projects'}**
```

****前两个问题给了我们想要的答案。第三个问题的答案实际上是肯定的，模型通过指出在 GitHub 中托管项目的可能性做出了类似的回答。****

## ****4.文本生成****

****下一个有趣的应用是使用变压器生成文本。我们可以通过提供`prompt,` `max_length`和`num_return_sequences`来利用文本生成模型。顾名思义，`max_length`表示生成的文本长度，`num_return_seuqences`表示生成的文本数量。A `prompt`是模型基于其生成新单词的**上下文/想法**。****

****在下面的代码中，我们用`text-generation`任务实例化`pipeline`,默认模型的(`gpt2,`查看此[链接](https://huggingface.co/gpt2)了解更多细节)权重被加载到变量`text_generator.`中****

```
**from transformers import pipeline
text_generator = pipeline("text-generation")

Output:
No model was supplied, defaulted to gpt2 and revision 6c0e608 (https://huggingface.co/gpt2).
Using a pipeline without specifying a model name and revision in production is not recommended.
Downloading: 100%
665/665 [00:00<00:00, 14.2kB/s]
Downloading: 100%
548M/548M [00:11<00:00, 40.0MB/s]
Downloading: 100%
1.04M/1.04M [00:00<00:00, 3.07MB/s]
Downloading: 100%
456k/456k [00:00<00:00, 867kB/s]
Downloading: 100%
1.36M/1.36M [00:00<00:00, 3.09MB/s]** 
```

****我们将看到三个不同提示的例子。前两个提示是关于'*基于 AI 的文本生成'*。第一个如下所示。****

```
**prompt = "AI based text generation is"
text_generator(prompt, max_length=30, num_return_sequences=5)
Output:
Setting `pad_token_id` to `eos_token_id`:50256 for open-end generation.
[{'generated_text': 'AI based text generation is a great idea as for you do not need to build and deploy your own font. The free font solution is the free Font'},
 {'generated_text': 'AI based text generation is the only system that\'s able to take the power of the internet offline."\n\nIt will work with all services underwritten'},
 {'generated_text': 'AI based text generation is available that can work with any text size on one device, including on computers running Windows or OSX. The Microsoft RDR'},
 {'generated_text': 'AI based text generation is used in this research to create a novel, non-text vector for the translation of human words, which will help reduce the'},
 {'generated_text': 'AI based text generation is essential to the efficiency of our business.\n\nIt may take a while but the key is using it to be productive for'}]**
```

****第一个和第二个提示的区别是给出的最后一个单词。在第一个例子中，我们给出了“*是*”，在第二个例子中，我们给出了“*是*”。从下面的输出可以非常清楚地看出，模型是如何根据提示高效地生成的。****

```
**prompt = "AI based text generation was"
text_generator(prompt, max_length=30, num_return_sequences=5)
Output:
Setting `pad_token_id` to `eos_token_id`:50256 for open-end generation.
[{'generated_text': 'AI based text generation was done on a fully automated system (i.e., that uses the current technology, the first machine to run the command,'},
 {'generated_text': 'AI based text generation was launched in 2010 in Turkey.\n\nThe first of this type of font will be available to the public from the next month'},
 {'generated_text': 'AI based text generation was born in 1995 on the idea that we should build a set of models that would automatically detect and translate the text in real time'},
 {'generated_text': 'AI based text generation was a major problem. Text is generated in both high performance and non-proprietary ways. As in every other field,'},
 {'generated_text': 'AI based text generation was built. However, we never considered a lot of ways to address the many potential issues with what we created with Text.org'}]**
```

****第三个提示是关于'*使用 GitHub，*结果可以看到下面。同样明显的是，该模型不会重复生成的句子，而是生成不同的句子。****

```
**prompt = "I am using Github to"
text_generator(prompt, max_length=30, num_return_sequences=5)
Output:
Setting `pad_token_id` to `eos_token_id`:50256 for open-end generation.
[{'generated_text': "I am using Github to get the job done so I'll have to follow through in this tutorial. I created all the tutorials on youtube, but I"},
 {'generated_text': 'I am using Github to start a new project, and I am wondering if you can help me make some modifications and give the repository a try.\n'},
 {'generated_text': 'I am using Github to start a blog, and this is how I create what I call a monthly blog.\n\nIf you run into anything,'},
 {'generated_text': 'I am using Github to serve the rest of the system.\n\nCreate an executable:\n\nimport os import os.path as path path ='},
 {'generated_text': "I am using Github to post updates to my work. I don't understand why people want to check in on my work and delete it while it is"}]**
```

## ****5.命名实体识别****

****变形金刚系列的下一个重要应用是识别给定文本中的实体。实体可以是个人、组织、位置等。****

****第一步，用`ner`实例化`pipeline`作为预期任务。默认模型是`bert-large-cased-finetuned-conll03-english`，相应的模型权重被下载到`named_entity_recognition`。****

```
**from transformers import pipeline
named_entity_recognition = pipeline("ner", aggregation_strategy = "simple")

Output:
No model was supplied, defaulted to dbmdz/bert-large-cased-finetuned-conll03-english and revision f2482bf (https://huggingface.co/dbmdz/bert-large-cased-finetuned-conll03-english).
Using a pipeline without specifying a model name and revision in production is not recommended.
Downloading: 100%
998/998 [00:00<00:00, 23.5kB/s]
Downloading: 100%
1.33G/1.33G [00:42<00:00, 41.7MB/s]
Downloading: 100%
60.0/60.0 [00:00<00:00, 1.07kB/s]
Downloading: 100%
213k/213k [00:00<00:00, 1.85MB/s]**
```

****现在，我们用一组句子加载`input_text`来提取实体。****

```
**input_text = """GitHub Inc is an Internet hosting service for software 
development and version control using Git. It provides the distributed 
version control of Git plus access control, bug tracking, software feature 
requests, task management, continuous integration, and wikis for every project.
Headquartered in California, it has been a subsidiary of Microsoft since 2018\. 
It is commonly used to host open source software development projects. 
As of June 2022, GitHub reported having over 83 million developers and 
more than 200 million repositories, including at least 28 million public 
repositories. It is the largest source code host as of November 2021.
"""**
```

****对于模型(`named_entity_recognition`)，我们给出`input_text`并打印结果(`tags`)。我们可以看到 GitHub Inc，微软，GitHub 被命名为组织，California 被命名为位置，Internet，Git 被命名为杂项。输出还会提到单词的开头和结尾，以及每个分类的分数。****

```
**ctags = named_entity_recognition(input_text)
print(tags)

Output:
[{'entity_group': 'ORG',
  'score': 0.99605906,
  'word': 'GitHub Inc',
  'start': 0,
  'end': 10},
 {'entity_group': 'MISC',
  'score': 0.91944593,
  'word': 'Internet',
  'start': 17,
  'end': 25},
 {'entity_group': 'MISC',
  'score': 0.9152951,
  'word': 'Git',
  'start': 93,
  'end': 96},
 {'entity_group': 'MISC',
  'score': 0.93599296,
  'word': 'Git',
  'start': 145,
  'end': 148},
 {'entity_group': 'LOC',
  'score': 0.9990779,
  'word': 'California',
  'start': 301,
  'end': 311},
 {'entity_group': 'ORG',
  'score': 0.9995492,
  'word': 'Microsoft',
  'start': 341,
  'end': 350},
 {'entity_group': 'ORG',
  'score': 0.9892499,
  'word': 'GitHub',
  'start': 452,
  'end': 458}]**
```

****为了以更易读的形式查看结果，我们可以安装并导入`pandas`库，并创建输出的`DataFrame`(`tags`)。打印它会给我们一个标签表，如下所示。****

```
**import pandas as pd
tags = named_entity_recognition(input_text)
pd.DataFrame(tags)
print(tags)

Output:
entity_group  score    word       start end
0 ORG         0.996059 GitHub Inc   0   10
1 MISC        0.919446 Internet    17   25
2 MISC        0.915295 Git         93   96
3 MISC        0.935993 Git         145  148
4 LOC         0.999078 California  301  311
5 ORG         0.999549 Microsoft   341  350
6 ORG         0.989250 GitHub      452  458**
```

## ****摘要****

****在本文中，我们介绍了变形金刚及其在迁移学习中的辅助作用。我们还看到了利用拥抱脸模型的简单步骤。我们经历了各种应用程序，如情感分析、摘要、问题回答、文本生成和命名实体生成。还有更多的应用程序需要探索，这将在本文的第 2 部分中讨论。****

****[](/a-journey-into-the-fabulous-applications-of-transformers-part-2-81a349a70cf3) [## 变压器神奇应用之旅——第二部分

### 演示重点是自然语言处理使用 Python，拥抱脸

pub.towardsai.net](/a-journey-into-the-fabulous-applications-of-transformers-part-2-81a349a70cf3) 

了解了所有这些令人着迷的应用程序的可能性之后，选择一个你感兴趣的任务，并为该任务尝试不同的模型和输入。

前进，成功！！！！

## 参考

*   变形金刚的自然语言处理:用拥抱脸构建语言应用程序。
*   https://jalammar.github.io/illustrated-transformer/
*   【https://towardsdatascience.com/transformers-89034557de14 
*   [https://www.youtube.com/watch?v=KmAISyVvE1Y&list = PLIXJ-sacf 8 u 60g 1 twcznbmk 6 rel 3 gmzmv](https://www.youtube.com/watch?v=KmAISyVvE1Y&list=PLIXJ-Sacf8u60G1TwcznBmK6rEL3gmZmV)

> 请在此[页面](https://medium.com/@dharini_r)中找到更多与 NLP 相关的文章。
> 
> 谢谢大家！！****