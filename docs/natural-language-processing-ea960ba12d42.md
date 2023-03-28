# 用 Python 实现自然语言处理中的词干化和词汇化

> 原文：<https://pub.towardsai.net/natural-language-processing-ea960ba12d42?source=collection_archive---------2----------------------->

## [自然语言处理](https://towardsai.net/p/category/nlp)

## 自然语言处理中分析文本的技术

![](img/a1d8576d93f6031def1391e2e370e2cf.png)

由[米卡·博斯韦尔](https://unsplash.com/@micahboswell?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

在本文中，我们将研究自然语言处理技术中的词干化和词汇化。这两个主题对于文本数据的预处理和细化分析都非常重要。

*   **词干化:**是将带后缀的词还原为其词根的过程。这是自然语言处理中一个重要的流水线过程。像‘快乐’、‘最快乐’、‘更快乐’这样的词属于词根，即‘快乐’。
*   **词汇化:**这也是一个将单词还原到其本义的过程，但具有附加功能，如添加词性(POS)。

这两种技术都用在文本挖掘过程中，以便从文本中提取最佳信息。

词干提取过程简单快捷，主要依赖于基于模式的方法。而在词汇化中，它被用来从文本中获取更详细的信息。

用于 NLP 任务的 python 用户友好库是 Spacy、NLTK、TextBlob。

这个空间不包括词干提取过程，所以我们为这个过程选择了其他库。对于这两种方法，我们将尝试使用其他库。

stemming 提供了两个主要的库，第一个是 porter stemmer，第二个是 snowball stemmer。雪球词干分析器是波特词干分析器的一个更好的版本，可以获得更精确的词干词根。

让我们看看使用 NLTK 库进行词干提取和词汇化的 python 示例。

> ***词干***

在这种方法中，我们将讨论波特词干。首先，我们需要导入 NLTk 库，下载“punkt ”,即句子分词器。然后导入 porter 词干分析器来处理句子的词干。词干化是在保持词义不变的情况下改变词的变化的过程。

```
import nltk
nltk.download('punkt')
from nltk.stem.porter import PorterStemmer
porter_stemmer = PorterStemmer()
```

现在，我们将以句子为例进行词干分析。

```
text = "Fruits are one of the essential crops among all, which have all nutrients"# Grab the tokens from the sentence
tokens = nltk.word_tokenize(text)#To do stemming on these tokens
for w in tokens:
    print ("Actual: %s ---- Stem: %s"  % (w,porter_stemmer.stem(w)))
```

这部分代码将对 tokens 变量中的所有标记进行词干分析。

```
**#output:**
Actual: Fruits ---- Stem: fruit
Actual: are ---- Stem: are
Actual: one ---- Stem: one
Actual: of ---- Stem: of
Actual: the ---- Stem: the
Actual: essential ---- Stem: essenti
Actual: crops ---- Stem: crop
Actual: among ---- Stem: among
Actual: all ---- Stem: all
Actual: , ---- Stem: ,
Actual: which ---- Stem: which
Actual: have ---- Stem: have
Actual: all ---- Stem: all
Actual: nutrients ---- Stem: nutrient
```

波特词干分析器的另一个例子如下所示:

```
from nltk.stem import PorterStemmer
words= ["rest", "resting", "rests", "restful"]
ps =PorterStemmer()
for w in words:
    rootWord=ps.stem(w)
    print(rootWord)**#output:**
rest
rest
rest
rest
```

> ***词汇化***

对于同一个文本示例，我们将进行引理化，并注意两种方法的区别。

```
nltk.download('wordnet')
from nltk.stem import WordNetLemmatizer
lemma = WordNetLemmatizer()text = "Fruits are one of the essential crops among all, which have all nutrients"tokens = nltk.word_tokenize(text)
for w in tokens:
    print ("Actual: %s  Lemma: %s"  % (w,lemma.lemmatize(w)))
```

术语化的输出如下所示:

```
**#output:**
Actual: Fruits --- Lemma: **Fruits**
Actual: are --- Lemma: are
Actual: one --- Lemma: one
Actual: of --- Lemma: of
Actual: the --- Lemma: the
Actual: essential --- Lemma: **essential**
Actual: crops --- Lemma: crop
Actual: among --- Lemma: among
Actual: all --- Lemma: all
Actual: , --- Lemma: ,
Actual: which --- Lemma: which
Actual: have --- Lemma: have
Actual: all --- Lemma: all
Actual: nutrients --- Lemma: nutrient
```

如果我们比较这两个的结果，那么我们会清楚地看到，引理化给出了上面输出中加粗的两个不同的引理。

在业务领域中，词汇化更受欢迎，因为它比词干化更可靠、更先进。

```
from nltk.stem import WordNetLemmatizer

lem = WordNetLemmatizer()

print("days :", lem.lemmatize("days"))
print("bottles :", lem.lemmatize("bottles"))

# The pos parameter have 'a' means adjective
print("happier :", lem.lemmatize("happier", pos ="a"))**#output:**
days : day
bottles : bottle
happier : happy
```

[](/nlp-zero-to-hero-with-python-2df6fcebff6e) [## NLP——使用 Python 从零到英雄

### 学习自然语言处理基本概念的手册

pub.towardsai.net](/nlp-zero-to-hero-with-python-2df6fcebff6e) 

> ***结论***

本文给出了自然语言处理中这两种方法的基本思想。NLTK 库是一个用文本数据进行分析的极好的库。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

1. [Python:零到英雄配实例](/python-zero-to-hero-with-examples-c7a5dedb968b?source=friends_link&sk=186aff630c2241aca16522241333e3e0)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)3 .[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[在熊猫](/reading-csv-excel-json-and-html-file-formats-in-pandas-2e1e417d1d12?source=friends_link&sk=1bafcb980bf95253f8c8e19d6643ec9e)
5 中读取 CSV()、Excel()、JSON()和 HTML()文件格式。[神经网络:递归神经网络的兴起](/neural-networks-the-rise-of-recurrent-neural-networks-df740252da88?source=friends_link&sk=6844935e3de14e478ce00f0b22e419eb)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[concat()、merge()和 join()与 Python](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
的区别 9。[套索(l1)和脊(l2)正则化技术](/lasso-l1-and-ridge-l2-regularization-techniques-33b7f12ac0b?source=friends_link&sk=b77a29aac0ab8d63ba6b449c03180cd5)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)