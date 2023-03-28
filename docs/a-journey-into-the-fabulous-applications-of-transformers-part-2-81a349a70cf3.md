# 变压器神奇应用之旅——第二部分

> 原文：<https://pub.towardsai.net/a-journey-into-the-fabulous-applications-of-transformers-part-2-81a349a70cf3?source=collection_archive---------2----------------------->

## 演示重点是自然语言处理使用 Python，拥抱脸

![](img/ef8d7ebb3faee2beefacc147091326ab.png)

[Samule 孙](https://unsplash.com/@samule?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍照

Transformer 架构广泛应用于自然语言处理中，它极大地促进了大型语言模型的发展。随着使用 LLM 的 NLP 中[迁移学习](https://towardsdatascience.com/a-gentle-introduction-to-transfer-learning-in-nlp-b71e87241d66)的兴起，许多模型被构建并在[拥抱脸](https://huggingface.co/models)中与研究社区共享。

我们将会看到一些有趣的变形金刚在 NLP 中的应用，包括演示和解释。这篇文章是下面链接的上一篇文章的延续。

[](/a-journey-into-the-fabulous-applications-of-transformers-part-1-630cc80e3ce6) [## 变压器神奇应用之旅——第一部分

### 演示重点是使用 Python 的 NLP，拥抱脸。

pub.towardsai.net](/a-journey-into-the-fabulous-applications-of-transformers-part-1-630cc80e3ce6) 

本文中使用的拥抱脸模型也可以用作使用加速推理 API 的即插即用模型。请参考这篇文章，了解更多关于如何利用模型的 API。

[](https://blog.jovian.ai/plug-and-play-ml-models-with-accelerated-inference-api-from-hugging-face-964d25d9dd65) [## 即插即用的 ML 模型，带有来自拥抱脸的“加速推理 API”

### python 实现的 4 步指南

blog.jovian.ai](https://blog.jovian.ai/plug-and-play-ml-models-with-accelerated-inference-api-from-hugging-face-964d25d9dd65) 

本 [GitHub 链接](https://github.com/dharini-projects/NLP_Applications_with_Transformers)中给出了所有讨论的应用程序的演示代码以及 Colab 链接。作为一篇介绍性文章，关于所讨论的模型的细节在相应的章节中有链接。为了让所有的应用程序工作(除了句子相似性)，我们需要使用`pip install transformers.`安装`transformers`库

我们将在本文中看到的应用有

> [6。翻译](#0148)
> 
> [7。令牌分类](#a8c1)
> 
> [8。句子相似度](#db4d)
> 
> 9。零枪击分类
> 
> 10。填充蒙版

## 6.翻译

transformers 的一个有趣而有用的应用是能够在不同语言之间翻译文本。根据培训阶段使用的语言，翻译任务有几种模式可供选择。

在我们的例子中，我们将把英语文本翻译成意大利语。要知道什么模型可以执行翻译，我们必须探索拥抱人脸库。名为`[Helsinki-NLP/opus-mt-en-it](https://huggingface.co/Helsinki-NLP/opus-mt-it-en)` 的模型执行这种转换，我们将在演示中使用它。

第一步是用任务`translation.`实例化`pipeline`。任务名称根据所处理的语言而不同。关于不同语言文本翻译、相应模型和数据集的更多信息可在此[链接](https://huggingface.co/languages)中找到。

在我们的例子中，任务是`translation_en_to_it`，它和模型名称一起给出，如下所示。

```
from transformers import pipeline
text_translator = pipeline("translation_en_to_it", model="Helsinki-NLP/opus-mt-en-it")
```

`input_text`存储有我们希望翻译的英语句子。

```
input_text = "This text is translated from English to Italian"
```

在下面的代码行中，我们将输入加载到我们的模型中，并将输出存储在`italian_text.`中。

```
italian_text = text_translator(input_text, clean_up_tokenization_spaces=True)
print(italian_text)
Output:
[{'translation_text': "Questo testo è tradotto dall'inglese all'italiano"}]
```

## 7.令牌分类

[标记分类](https://huggingface.co/tasks/token-classification)是给文本中出现的单词分配一个标记/标签的任务。句子中的一个单词叫做标记。标记分类的例子有[命名实体识别](https://huggingface.co/dslim/bert-base-NER) (NER)和[词性](https://en.wikipedia.org/wiki/Part-of-speech_tagging)(词性)标注。

我们已经在文章的第一部分介绍了 NER，所以现在我们来看第二个任务，词性标注。词性标注是识别一个词的相应词性并在句子中用标签如名词、代词、形容词、副词等来标记它的过程。

我们首先导入`pipeline`并用任务`token-classification.`实例化它

```
from transformers import pipeline

pos_classifier = pipeline("token-classification", model = "vblagoje/bert-english-uncased-finetuned-pos")
```

如上所述，我们使用的型号是`[vblagoje/bert-english-uncased-finetuned-pos](https://huggingface.co/vblagoje/bert-english-uncased-finetuned-pos)`。现在我们将对代币进行分类并展示它们。

```
tags = pos_classifier("Hello I am happy when I see waterfalls.")
print(tags)

Output:
[{'entity': 'INTJ', 'score': 0.9958117, 'index': 1, 'word': 'hello', 'start': 0, 'end': 5}, {'entity': 'PRON', 'score': 0.9995704, 'index': 2, 'word': 'i', 'start': 6, 'end': 7}, {'entity': 'AUX', 'score': 0.9966484, 'index': 3, 'word': 'am', 'start': 8, 'end': 10}, {'entity': 'ADJ', 'score': 0.99829704, 'index': 4, 'word': 'happy', 'start': 11, 'end': 16}, {'entity': 'ADV', 'score': 0.99861526, 'index': 5, 'word': 'when', 'start': 17, 'end': 21}, {'entity': 'PRON', 'score': 0.9995561, 'index': 6, 'word': 'i', 'start': 22, 'end': 23}, {'entity': 'VERB', 'score': 0.99941325, 'index': 7, 'word': 'see', 'start': 24, 'end': 27}, {'entity': 'NOUN', 'score': 0.9958626, 'index': 8, 'word': 'waterfalls', 'start': 28, 'end': 38}, {'entity': 'PUNCT', 'score': 0.9996631, 'index': 9, 'word': '.', 'start': 38, 'end': 39}]
```

为了清楚地看到输出，我们将导入`pandas`并创建结果的数据帧，然后看到如下所示的输出。

```
import pandas as pd
df_tags = pd.DataFrame(tags)
print(df_tags)

Output:
  entity     score  index        word  start  end
0   INTJ  0.995812      1       hello      0    5
1   PRON  0.999570      2           i      6    7
2    AUX  0.996648      3          am      8   10
3    ADJ  0.998297      4       happy     11   16
4    ADV  0.998615      5        when     17   21
5   PRON  0.999556      6           i     22   23
6   VERB  0.999413      7         see     24   27
7   NOUN  0.995863      8  waterfalls     28   38
8  PUNCT  0.999663      9           .     38   39
```

## 8.句子相似度

transformers 的一个有趣的应用是提取句子嵌入的能力，这种能力可以捕获语义信息。嵌入的[句子是整个句子的数字表示，并被用作模型的输入。在我们的例子中，我们将使用句子转换器来生成句子嵌入，并使用它来识别两个句子之间的](https://engineering.talkdesk.com/what-are-sentence-embeddings-and-why-are-they-useful-53ed370b3f35)[相似度](https://huggingface.co/tasks/sentence-similarity)。

对于这个例子，我们必须从拥抱脸安装`[sentence-transformers](https://www.sbert.net/)`库，不像其他应用程序，我们将安装`transformers`库。有许多模型可用于句子相似性的任务，我们将在我们的示例中使用模型`[sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)`。

第一步是导入`SentenceTransformer` 和`util`，如下图所示。需要使用`util`包来使用余弦相似性函数来测量两个嵌入之间的距离。

```
!pip install sentence-transformers
from sentence_transformers import SentenceTransformer, util
```

下一步，我们在`input_sentences`中加载我们想用来测试模型的句子。我们给`SentenceTransformer`指定具体的型号名称。

```
similarity_model = SentenceTransformer('sentence-transformers/all-MiniLM-L6-v2')
input_sentences = ["I'm happy", "I'm not sad"]
```

下一步，我们提取两个句子的嵌入。两个句子的嵌入都存储在单独的变量中。

```
embedding_1= similarity_model.encode(input_sentences[0], convert_to_tensor=True)
embedding_2 = similarity_model.encode(input_sentences[1], convert_to_tensor=True)
```

在最后一步，我们利用来自`util`的`cos_sim`函数来计算两个向量之间的距离(嵌入)

```
print(util.pytorch_cos_sim(embedding_1, embedding_2))
Output:
tensor([[0.4624]])
```

该值越接近 1，句子之间的相似度越大。如果值更接近 0，我们可以理解为句子不相似。

## 9.零射击分类

零触发分类源于[零触发学习](https://joeddav.github.io/blog/2020/05/29/ZSL.html)，这基本上意味着用一组标签训练分类器，用另一组标签测试分类器。模型根本看不到评估标签集。

这意味着我们可以采用[零镜头分类](https://towardsdatascience.com/zero-shot-text-classification-with-hugging-face-7f533ba83cd6)模型，给出输入，也给出我们自己的标签。该模型将根据我们给定的标签对文本进行分类，即使该模型没有被这些标签中的任何一个训练。现在，我们将在演示中尝试同样的方法。让我们从用任务`zero-shot-classification.`实例化`pipeline`开始

```
from transformers import pipeline
zero_shot_classifier = pipeline("zero-shot-classification")
Output:
No model was supplied, defaulted to facebook/bart-large-mnli and revision c626438 (https://huggingface.co/facebook/bart-large-mnli).
Using a pipeline without specifying a model name and revision in production is not recommended.
Downloading: 100%
1.15k/1.15k [00:00<00:00, 28.0kB/s]
Downloading: 100%
1.63G/1.63G [00:26<00:00, 63.5MB/s]
Downloading: 100%
26.0/26.0 [00:00<00:00, 467B/s]
Downloading: 100%
899k/899k [00:00<00:00, 5.16MB/s]
Downloading: 100%
456k/456k [00:00<00:00, 2.73MB/s]
Downloading: 100%
1.36M/1.36M [00:00<00:00, 2.71MB/s]
```

由于我们没有给出具体的模型，模型`[facebook/bart-large-mnli](https://huggingface.co/facebook/bart-large-mnli)`由库选择，模型权重下载后参考 `zero_shot_classifier.`

下一步是定义我们需要分类的输入文本和标签。使用 `zero_shot_classifier,` 我们将输入的文本和标签进行分类。

```
input_sentence = "I am hungry and angry. I think an ice cream will make me feel good"
labels = ['food', 'travel','entertainment','sad','happy','neutral']
results = zero_shot_classifier(input_sentence, labels)
print(results)

Output:
{'sequence': 'I am hungry and angry. I think an ice cream will make me feel good', 'labels': ['food', 'sad', 'entertainment', 'travel', 'neutral', 'happy'], 'scores': [0.8720405101776123, 0.07575708627700806, 0.023996146395802498, 0.010163746774196625, 0.009797507897019386, 0.00824508722871542]}
```

为了清楚地看到输出，我们将导入`pandas`库，并在一个数据帧中看到结果。如下面的数据框所示，标签`food`和`sad`的得分高于其他标签。我们可以看到，给出的句子与标签`food` 的关联超过了所有其他标签。所以我们得到了最高分。

```
import pandas as pd
df_result = pd.DataFrame(results)
print(df_result.loc[:, ['labels','scores']])
Output:
          labels    scores
0           food  0.872041
1            sad  0.075757
2  entertainment  0.023996
3         travel  0.010164
4        neutral  0.009798
5          happy  0.008245
```

## 10.填充蒙版

[屏蔽语言建模(MLM)](https://analyticsindiamag.com/a-complete-tutorial-on-masked-language-modelling-using-bert/) 的概念处理预测单词以替换数据中有意屏蔽的单词。这有助于提高对模型训练语言的统计理解，并带来更好的文本表示。MLM 的优点是自我监督的预训练，不需要标记数据进行训练。

任务`[Fill Mask](https://huggingface.co/tasks/fill-mask),`因此处理屏蔽给定句子中的随机单词，并探索模型给出的替换屏蔽的各种建议。

让我们从用任务`fill-mask`实例化`pipeline`开始，如下所示。由于我们没有给出具体的模型，所以下载默认模型(`[distilroberta-base](https://huggingface.co/distilroberta-base)`)。

```
from transformers import pipeline
fill_mask_clf = pipeline("fill-mask")

Output:
No model was supplied, defaulted to distilroberta-base and revision ec58a5b (https://huggingface.co/distilroberta-base).
Using a pipeline without specifying a model name and revision in production is not recommended.
Downloading: 100%
480/480 [00:00<00:00, 13.5kB/s]
Downloading: 100%
331M/331M [00:08<00:00, 43.4MB/s]
Downloading: 100%
899k/899k [00:00<00:00, 1.56MB/s]
Downloading: 100%
456k/456k [00:00<00:00, 1.77MB/s]
Downloading: 100%
1.36M/1.36M [00:00<00:00, 1.77MB/s]
```

现在，我们通过用`<mask>`标记屏蔽一个单词来给模型一个句子。在打印输出时，我们会看到屏蔽单词的五个不同的可能单词、相应的分数、标记表示和带有预测单词的完整句子。

```
print(fill_mask_clf("artificial intelligence is going to be <mask> in the future"))

Output:
[{'score': 0.061495572328567505,
  'token': 30208,
  'token_str': ' commonplace',
  'sequence': 'artificial intelligence is going to be commonplace in the future'},
 {'score': 0.05322642996907234,
  'token': 25107,
  'token_str': ' ubiquitous',
  'sequence': 'artificial intelligence is going to be ubiquitous in the future'},
 {'score': 0.0344822071492672,
  'token': 5616,
  'token_str': ' useful',
  'sequence': 'artificial intelligence is going to be useful in the future'},
 {'score': 0.033160075545310974,
  'token': 6128,
  'token_str': ' everywhere',
  'sequence': 'artificial intelligence is going to be everywhere in the future'},
 {'score': 0.025654001161456108,
  'token': 956,
  'token_str': ' needed',
  'sequence': 'artificial intelligence is going to be needed in the future'}]
```

## 摘要

在本文的这两部分中，我们讨论了变压器可以实现的最重要的 10 种应用。结论是，随着变形金刚和大型语言模型的出现，原本需要大量成本和时间的复杂任务现在可以轻松完成。还必须注意的是，相同的模型可以用于不同的任务。

这个想法是理解一个模型的可能性，然后[根据自己的目的对其进行微调](https://towardsdatascience.com/advanced-techniques-for-fine-tuning-transformers-82e4e61e16e)。我们尝试得越多，学到的就越多。前进，成功！！！

> 请在此[页面](https://medium.com/@dharini_r)中找到更多与 NLP 相关的文章。
> 
> 谢谢大家！！