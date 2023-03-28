# 使用 NLP 对推文进行情感分析，准确率达到 96%

> 原文：<https://pub.towardsai.net/sentiment-analysis-on-tweets-with-nlp-achieving-96-accuracy-8b63f0bcee99?source=collection_archive---------1----------------------->

## 自然语言处理

## 在我的 Github 库中可以找到完整的代码。一手资料可在 [ODSC](https://opendatascience.com/intro-to-natural-language-processing/) 获得

![](img/c276955205313b67d4423bc875535643.png)

照片由[莎拉·库菲](https://unsplash.com/@stereophototyp?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 拍摄

人工智能最复杂的用途之一是 NLP(自然语言处理)。原因是语言不同于所有其他类型的数据。例如，虽然数字和图像数据具有客观的优势，但书面文本是相对的。它的解释因文化而异:同一个句子对两个不同的人来说可能意味着完全不同的事情。

当然，数据分析师已经找到了让机器对文本内容有“基本理解”的有效解决方案。

# 情感分析

学习 NLP 模型的第一步是创建情感分析。给定一些文本，人工智能应该被训练识别它的意思是积极的还是消极的。实际上，您可以使用该工具来了解客户对产品或新闻的总体看法，尤其是在没有数字度量(如评分)而只有文本的情况下。

## 机器学习与深度学习

根据我的经验，我们必须根据问题的复杂程度使用不同的工具。在电影评论中，鉴于每个元素的复杂性，我们需要使用神经网络，但对于推文，我们可以使用机器学习，并取得非常有希望的结果。

## nltk

我将使用专门用于 NLP 的机器学习库，称为 nltk。我更喜欢使用 scikit-learn 来创建机器学习模型，但它是一个专门用于表格数据而不是自然语言处理的库。

# 步伐

在本文中，我将遵循以下步骤:

1.  导入模块
2.  创建要素和标签(编码)
3.  创建训练和测试(分割)
4.  使用模型:朴素贝叶斯分类器
5.  性能评估

像往常一样，AI 并不规范。有几种方法可以达到同样的效果。在常规的 NLP 中，我们需要以这种方式预处理数据:

*   标记化:将句子分割成单个单词
*   编码:将这些单词转换成数字
*   创建 NLP 模型

我将使用字典，因此我不会将文本编码成数字，而是编码成布尔值。

# 1.导入模块

```
!pip install nltk
import nltk
#per risolvere un bug, altrimenti da errore
nltk.download('punkt')#tokenizer
def format_sentence(sent):
  return({word: True for word in nltk.word_tokenize(sent)})
```

# 2.创建要素和标签

在这一节中，我将分别导入包含正面和负面推文的数据集，分别对它们进行预处理。

正在讨论的数据集包含 617 条正面推文和 1387 条负面推文的样本，总共 2000 条推文。

```
#   X + y
total = open('/content/drive/My Drive/Colab Notebooks/Projects/20200602_Twitter_Sentiment_Analysis/pos_tweets.txt')
Xy_pos = list()
#word tokenization
for sentence in total:
  #print(sentence)
  Xy_pos.append([format_sentence(sentence), 'pos'])
  #saves the sentence in format: [{tokenized sentence}, 'pos]
#Xy_pos#   X + y
total = open('/content/drive/My Drive/Colab Notebooks/Projects/20200602_Twitter_Sentiment_Analysis/neg_tweets.txt')
Xy_neg = list()
#word tokenization
for sentence in total:
  #print(sentence)
  Xy_neg.append([format_sentence(sentence), 'neg'])
  #saves the sentence in format: [{tokenized sentence}, 'pos]
#Xy_neg
```

因此，我将有一个嵌套在列表中的字典:

```
[dictionary, sentiment]
```

如果我们看一下 positive_tweets 的第一个元素，我们可以看到我们的数据是如何被编码的:

```
Xy_pos[0]
[{"''": True,
  "'m": True,
  ',': True,
  '.': True,
  ':': True,
  'Ballads': True,
  'Cellos': True,
  'Genius': True,
  'I': True,
  '``': True,
  'and': True,
  'by': True,
  'called': True,
  'cheer': True,
  'down': True,
  'iPod': True,
  'listening': True,
  'love': True,
  'music': True,
  'my': True,
  'myself': True,
  'of': True,
  'playlist': True,
  'taste': True,
  'to': True,
  'up': True,
  'when': True},
 'pos']
```

# 3.创建训练和测试

我们在监督学习领域工作。不幸的是，与表格数据的分析相比，至少对于 nltk 工具来说，预处理的行为有点不同。

如果我必须分析表格数据，我会将我的部分分成:

```
X_train, y_train, X_test, y_test
```

在这种特殊情况下，我需要合并标注和要素，保留:

```
Xy_train, Xy_test
```

这种变化的原因是 nltk 模型只接受一个参数，X_train 和 y_train 合并:在我们的例子中是 Xy_train

## 剧烈的

为了创建我的训练和测试部分，我必须合并 pos 和 neg，因为它们包含训练和测试部分。然后，我将拆分合并的数据集。

```
def split(pos, neg, ratio):
  train = pos[:int((1-ratio)*len(pos))] + neg[:int((1-ratio)*len(neg))]
  test = pos[int((ratio)*len(pos)):] + neg[int((ratio)*len(neg)):]
  return train, testXy_train, Xy_test = split(Xy_pos, Xy_neg, 0.1)
```

# 4.使用模型:朴素贝叶斯分类器

现在是时候创建机器学习模型了。

```
from nltk.classify import NaiveBayesClassifier#encoded thrugh dictionaries
classifier = NaiveBayesClassifier.train(Xy_train)
classifier.show_most_informative_features()
Most Informative Features                       no = True              neg : pos    =     20.6 : 1.0                  awesome = True              pos : neg    =     18.7 : 1.0                 headache = True              neg : pos    =     18.0 : 1.0                beautiful = True              pos : neg    =     14.2 : 1.0                     love = True              pos : neg    =     14.2 : 1.0                       Hi = True              pos : neg    =     12.7 : 1.0                      fan = True              pos : neg    =      9.7 : 1.0                    Thank = True              pos : neg    =      9.7 : 1.0                     glad = True              pos : neg    =      9.7 : 1.0                     lost = True              neg : pos    =      9.3 : 1.0
```

该模型将一个值与数据集中的每个单词相关联。它将对每条推文中包含的所有单词进行计算，然后做出评估:正面或负面。

# 5.性能评估

正如我们所看到的，我们在所有推文中获得了 96%的准确率(通过过度近似)!惊人的结果。

```
from nltk.classify.util import accuracy
print(accuracy(classifier, Xy_test))
0.9562326869806094
```