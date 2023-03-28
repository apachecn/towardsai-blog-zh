# 使用深度学习教程的 NLP:基于感知器的情感分类器(第 2/4 部分)

> 原文：<https://pub.towardsai.net/nlp-using-deepleaning-tutorials-a-sentiment-classifier-based-on-perceptron-part-2-4-f9b90b3a06bd?source=collection_archive---------2----------------------->

![](img/200e6d7dac3e16f02cac84b56f94998b.png)

该图像从[源](https://hackernoon.com/drafts/523x232ih.png)上传

自然语言处理是机器学习中最复杂的领域之一，基本上是由于语言的复杂性和模糊性。然而，它也是最成功的领域之一，有许多我们每天都在使用的真实应用，像搜索引擎、翻译工具等等。

有时最复杂的任务可以用最简单的技术解决。在这篇文章中，我将尝试探索这种说法。所以，我将基于最简单的神经网络“感知器”提出一个完整的情感分析解决方案，使用一个真实世界的任务和数据集:对 Yelp 上的餐厅评论进行正面或负面分类。

为此，我将本文分为以下四个部分:

1.  Yelp 数据集评论([链接](/nlp-using-deepleaning-tutorials-a-sentiment-classifier-based-on-perceptron-part-1-4-712eefe20899)
2.  **词汇和矢量器(本文关注这部分)**
3.  训练程序
4.  评估和推理

> **提前感谢大家的支持。如果你决定注册成为灵媒会员，这里是我的订阅页面**:[https://abdelkader-rhouati.medium.com/membership](https://abdelkader-rhouati.medium.com/membership)

# 第 2 部分:**词汇表和矢量器**

每个文本都是单词或字符的集合，这些单词或字符被称为标记。因此，预处理管道的第一步是通过 python 字典变量将每个标记映射到其自身的数字版本。这使得使用文本作为基于数学方程的神经网络的输入成为可能。

# 积累词汇

在这个例子中，我们将在记号和整数之间使用双射，这意味着有两个字典变量。两个主要的词汇类函数是 **lookup_tooken()** 和 **lookup_index()** ，分别检索给定标记的索引和对应于给定索引的标记

除了处理这种双射，词汇类还允许通过自动增加索引来添加新的标记: **add_token()** 函数。

即使有最大的语料库，词汇量也总是有限的。这就是为什么我们的词汇表需要处理一个叫做 ***UNK(未知)的特定令牌。通过使用 UNK，我们处理了在训练数据集上看不到的新标记。***

词汇课的内容是:

词汇表. py 文件的内容

# **对文本进行矢量化**

**矢量器**类封装了**词汇**特性。因此，它提供了一种机制，通过 **from_dataframe** ()函数，基于特定的数据语料库(通常语料库对应于训练数据集)来构建个性化词汇表。该函数遍历 Pandas 数据帧的行，首先计算数据集中出现的每个标记的频率，然后创建词汇表(配对标记和索引的列表)。一个好的做法是通过忽略不常用的标记来限制词汇量。这通过定义**切断**参数来完成。

除了创建词汇表，**矢量化**()函数还返回文本输入的矢量化表示(=数值向量)。在这项工作中，我们使用了**折叠的一个热点表示**。这种表示创建了一个二进制向量，其长度相当于词汇表的大小。二进制向量在对应于文本中单词的位置上有 1。这具有与未被处理的文本中的单词顺序相关的限制，并且出现多次的标记仅被考虑一次

**矢量器类**的内容是:

内容审查 _ 矢量器. py 文件

# **使用数据加载器生成小批量。**

最后一步是将矢量化数据分组为小批量。这是训练神经网络的重要部分。为此，Pytorch 提供了一个名为 DataLoaer 的内置类([2]了解更多细节)。

生成小批量的功能是:

**参考文献:**

1.  《用 Pytorch 进行自然语言处理》一书([https://www . Amazon . fr/Natural-Language-Processing-py torch-Applications/DP/1491978236](https://www.amazon.fr/Natural-Language-Processing-Pytorch-Applications/dp/1491978236))
2.  [https://py torch . org/tutorials/beginner/basics/data _ tutorial . html？高亮显示=数据加载器](https://pytorch.org/tutorials/beginner/basics/data_tutorial.html?highlight=dataloader)