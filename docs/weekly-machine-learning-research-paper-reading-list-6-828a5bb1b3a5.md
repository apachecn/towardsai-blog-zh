# 每周机器学习研究论文阅读清单— #6

> 原文：<https://pub.towardsai.net/weekly-machine-learning-research-paper-reading-list-6-828a5bb1b3a5?source=collection_archive---------4----------------------->

![](img/4d7f5db1aa90036b10ca823a935d5316.png)

## [机器学习](https://towardsai.net/p/category/machine-learning)

## 本周(2020 年 7 月 9 日–2020 年 13 月 9 日)，请查阅以下三篇研究论文。

# 4S:克服传统先验处理的可扩展子空间搜索方案

作者:Hoang Vu Nguyen、Emmanuel Müller 和 Klemens bhm

地点:2013 年 IEEE 大数据国际会议

论文:[网址](https://ieeexplore.ieee.org/document/6691596/authors#authors)

摘要:

> 在许多现实应用中，数据是在多维空间中收集的。然而，并非所有维度都与数据分析相关。相反，有趣的知识隐藏在相关的维度子集(即原始空间的子空间)中。独立于底层挖掘任务检测这些相关子空间是一个开放的研究问题。由于指数级的搜索空间，这是一个挑战。现有的方法试图通过利用先验搜索方案来解决这个问题。然而，它们表现出较差的可扩展性，并且错过了高质量的子空间。本文提出了一种可扩展的子空间搜索方案(4S ),该方案与传统的逐级搜索不同，克服了效率问题。我们提出了一个新的广义相关子空间的概念，它将搜索空间转化为维数相关图。然后，我们执行图中相关子空间的直接挖掘。最后，我们根据 MDL 原则合并子空间，得到冗余最小的高维子空间。我们从理论上证明了我们的搜索方案比现有的搜索方案更通用，并且具有明显更低的运行时间复杂度。我们的实验表明，4S 随着数据库的大小和维数而近似线性地扩展，并且产生比最先进的方法更高质量的子空间。

# 在数据的多个视图中通过子空间分析进行异常值排序

作者:Emmanuel Müller、Ira Assent、Patricia Iglesias、Yvonne Mülle 和 Klemens bhm

地点:2012 年 IEEE 第 12 届数据挖掘国际会议(ICDM)

论文:[网址](https://ieeexplore.ieee.org/document/6413873)

摘要:

> 离群数据挖掘是发现异常对象的一项重要任务。然而，在实践中，离群值和常规对象之间并不总是有明显的区别，因为对象在不同的属性集下具有不同的角色。对象可能在一个子空间中偏离，即属性的子集。同样的物体在其他子空间中可能看起来非常规则。人们可以把子空间想象成一个数据库的多个视图。传统方法只考虑一个视图(完整的属性空间)。因此，他们遗漏了隐藏在多个子空间中的复杂异常值。在这项工作中，我们提出了 Outrank，一个新的离群排序概念。Outrank 利用子空间分析来确定离群度。它将属性的不同子集视为单独的异常属性。它比较任意子空间中的聚类区域，并导出每个对象的离群值。它将多个视图有原则地集成到异常值度量中，揭示了在整个属性空间中无法检测到的异常值。我们的实验评估表明，Outrank 成功地确定了高质量的异常值排序，并且优于最先进的异常值度量。

# 一种用于无监督选择相关特征的近线性时间子空间搜索方案

作者:Hoang-Vu Nguyen、Emmanuel Müller 和 klemensbhm

地点:大数据研究

论文:[网址](https://www.sciencedirect.com/science/article/pii/S2214579614000057)

摘要:

> 在许多现实世界的应用中，数据是在高维空间中收集的。然而，并非所有维度都与数据分析相关。相反，有趣的知识隐藏在相关的维度子集(即原始空间的子空间)中。独立于底层挖掘任务检测这些相关子空间是一个开放的研究问题。由于指数级的搜索空间，这是一个挑战。现有的方法试图通过利用先验搜索方案来解决这个问题。然而，它们的最坏情况复杂度是维数的指数级；甚至在实践中，它们表现出较差的可伸缩性，同时缺少高质量的子空间。
> 
> 本文提出了一种*可扩展子空间搜索方案(4S)* ，该方案与传统的逐级搜索不同，克服了效率问题。我们提出了一个新的广义相关子空间的概念，它将搜索空间转化为维数相关图。我们在该图中执行相关子空间的直接挖掘，然后，基于 MDL 原则合并子空间，以便获得具有最小冗余的高维子空间。我们从理论上证明了我们的搜索方案比现有的搜索方案更一般。我们的实证结果表明，4S 在实践中与数据库的大小和维数成近似线性的比例，并且产生比最先进的方法更高质量的子空间。

前几周阅读清单:

[每周阅读清单#1](/the-innovation/weekly-machine-learning-research-paper-reading-list-1-780a5ffac7d7)

[每周阅读清单#2](/the-innovation/weekly-machine-learning-research-paper-reading-list-2-c9ed61b76462)

[每周阅读清单#3](/towards-artificial-intelligence/weekly-machine-learning-research-paper-reading-list-3-61d9c86c2538)

[每周阅读清单#4](/towards-artificial-intelligence/weekly-machine-learning-research-paper-reading-list-4-64442005324d)

[每周阅读清单#5](https://medium.com/towards-artificial-intelligence/weekly-machine-learning-research-paper-reading-list-5-7dc6740b9505)

# 关于我:

我是 [Durgesh Samariya](https://durgeshsamariya.com/) ，澳大利亚费杜尼大学机器学习博士三年级学生。在网上，我被称为学生。

[订阅我的简讯，获取我每周的片段](http://eepurl.com/hampwT)。

# 在互联网上:

在 [Instagram](https://www.instagram.com/themlphdstudent/) 、 [Kaggle](https://www.kaggle.com/themlphdstudent) 、 [GitHub](https://github.com/themlphdstudent) 、 [Medium](/@themlphdstudent) 上关注我。

感谢阅读。