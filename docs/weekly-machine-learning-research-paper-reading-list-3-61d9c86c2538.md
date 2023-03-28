# 每周机器学习研究论文阅读清单——# 3

> 原文：<https://pub.towardsai.net/weekly-machine-learning-research-paper-reading-list-3-61d9c86c2538?source=collection_archive---------5----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

## 本周(2020 年 17 月 8 日–2020 年 8 月 23 日),查看以下 3 篇关于边远方面挖掘的研究论文。

![](img/c7c11e5358f63a3c5598f40a6e8eae75.png)

由[威廉·艾文](https://unsplash.com/@firmbee?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

# 挖掘数值数据的无关方面

作者:，唐冠庭，简佩，，金秋子，唐

地点:数据挖掘和知识发现杂志

论文:[网址](https://link.springer.com/article/10.1007/s10618-014-0398-2)

摘要:

> 当我们在研究数据集中的一个对象时，它本身可能是也可能不是一个异常值，我们能识别该对象的异常(即，异常)方面吗？在本文中，我们确定了在数字数据上挖掘无关方面的新问题。给定一个多维数值数据集𝑂O 中的查询对象𝑜o，𝑜o 在哪个子空间中最偏远？在技术上，我们使用一个对象在子空间中的概率密度的等级来衡量该对象在子空间中的突出程度。查询对象排名最好的最小子空间是外围方面。计算一个查询对象的外围方面远非小事。一种简单的方法必须计算所有对象的概率密度，并在每个子空间中对它们进行排序，当维数很高时，这是非常昂贵的。我们系统地开发了一种启发式方法，能够有效地搜索数十维数据集。我们使用真实数据和合成数据的实证研究表明，我们的方法是有效和高效的。

# 在大型数据集中发现无关方面

作者:阮春荣，杰弗里陈，西蒙罗马诺，詹姆斯·贝利，克里斯托弗莱克基，Kotagiri Ramamohanarao 和裴健

地点:数据挖掘和知识发现杂志

论文:[网址](https://link.springer.com/article/10.1007/s10618-016-0453-2)

摘要:

> 我们解决外围方面挖掘的问题:给定一个查询对象和一个参考多维数据集，我们如何发现哪些方面(即特征子集或子空间)使查询对象最外围？外围方面挖掘可以用来解释任何感兴趣的数据点，它本身可能是一个内点或外点。在本文中，我们研究了现有外围方面挖掘技术面临的几个公开挑战，并提出了新的解决方案，包括(a)如何设计有效的评分函数，该函数在维度方面是无偏的，但在计算上是有效的，以及(b)如何有效地搜索所有可能的子空间的指数大的搜索空间。我们形式化了维度无偏性的概念，维度无偏性是外显测度的一个理想性质。然后，我们在效率、维度无偏性和可解释性方面描述了现有的评分方法以及我们新提出的方法。最后，我们评估了不同方法对异常方面发现的有效性，并展示了我们提出的方法在大型真实和合成数据集上的效用。

# 一种新的简单有效的密度估计器，可实现快速系统搜索

作者:乔纳森·R·威尔斯和明凯·丁

地点:模式识别字母

论文:[网址](https://www.sciencedirect.com/science/article/abs/pii/S0167865518309371)

摘要:

> 本文介绍了一种简单而有效的密度估计器，它可以实现快速的系统搜索。为了显示它相对于常用的核密度估计的优势，我们将其应用于离群点挖掘。外围方面挖掘发现描述查询如何从给定数据集中脱颖而出的特征子集(或子空间)。这项任务要求对子空间进行系统的搜索。我们发现，现有的边远方面挖掘器仅限于小数据大小和维度的数据集，因为它们采用核密度估计器，这在计算上是昂贵的，用于子空间评估。我们表明，最近的边远方面挖掘器可以通过简单地用建议的密度估计器替换其密度估计器来运行数量级更快，使其能够处理具有数千维的大型数据集，否则这是不可能的。

前几周阅读清单:

[每周阅读清单#1](/the-innovation/weekly-machine-learning-research-paper-reading-list-1-780a5ffac7d7)

[每周阅读清单#2](https://medium.com/the-innovation/weekly-machine-learning-research-paper-reading-list-2-c9ed61b76462)

# 关于我:

我是 [Durgesh Samariya](https://durgeshsamariya.com) ，一个 3 年级的机器学习博士生@ FedUni，澳大利亚。在网上，我被称为学生。

订阅我的时事通讯，获取我每周的片段。

# 社会化媒体

在[脸书](http://facebook.com/themlphdstudent/)、 [Instagram](https://www.instagram.com/themlphdstudent/) 、 [Twitter](https://twitter.com/themlphdstudent) 、 [Medium](/@themlphdstudent) 上关注我。

**感谢阅读。**