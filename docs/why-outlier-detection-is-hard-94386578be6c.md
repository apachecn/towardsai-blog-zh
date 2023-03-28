# 为什么异常值检测很难

> 原文：<https://pub.towardsai.net/why-outlier-detection-is-hard-94386578be6c?source=collection_archive---------1----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

## 异常检测机器学习任务的考虑因素

![](img/91d132cc40e665b67539fdf3c3c2de11.png)

图片由[汉斯](https://pixabay.com/users/hans-2/)在[皮克斯贝](https://pixabay.com/photos/pieces-of-the-puzzle-mix-hands-592798/)拍摄

O utlier detection 是一项机器学习任务，旨在识别偏离给定数据的“正常”或一般分布的罕见项目、事件或观察值。

> **异常是指引起怀疑是由不同的数据生成机制生成的东西**

# 异常值检测机器学习任务

**在离群点检测任务中，目标是训练一个无监督模型，以发现受两个约束的异常**:

1.  尽量减少假阴性(也就是尽可能多地捕捉异常)。
2.  尽量减少误报(也就是当异常被标记时，不要出错)。

在许多应用中，还有第三个约束:**什么是真正的离群值的“基本事实”可能是未知的**！

离群点检测是一项重要的机器学习任务。应用包括监控网络安全中的入侵检测、机械故障检测和数据质量。*数据质量在许多行业都很重要，包括金融和医疗保健。*

# 离群点检测算法

在深入研究这些挑战之前，有必要强调一点，即有一系列算法是为异常值检测而设计的。这些算法很多都是用 python 实现的！

`[scikit-learn](https://scikit-learn.org/stable/modules/outlier_detection.html)`已经实现了几种异常值和新颖性检测算法。

`[PyOD](https://pyod.readthedocs.io/en/latest/)`，一个较新的 python 包，实现了一套更全面的 30+离群点检测算法。您可以在此了解更多关于 PyOD 的信息:

[](https://towardsdatascience.com/pyod-a-unified-python-library-for-anomaly-detection-3608ec1fe321) [## PyOD:用于异常检测的统一 Python 库

towardsdatascience.com](https://towardsdatascience.com/pyod-a-unified-python-library-for-anomaly-detection-3608ec1fe321) [](https://towardsdatascience.com/fast-accurate-anomaly-detection-based-on-copulas-copod-3133ce9041fa) [## 基于 COPOD 的快速准确异常检测

towardsdatascience.com](https://towardsdatascience.com/fast-accurate-anomaly-detection-based-on-copulas-copod-3133ce9041fa) [](/an-in-depth-guide-to-local-outlier-factor-lof-for-outlier-detection-in-python-5a6f128e5871) [## Python 中离群点检测的局部离群点因子(LOF)深度指南

### 理论直觉、数学定义和实际代码示例

pub.towardsai.net](/an-in-depth-guide-to-local-outlier-factor-lof-for-outlier-detection-in-python-5a6f128e5871) [](https://medium.com/geekculture/replace-outlier-detection-by-simple-statistics-with-ecod-f95a7d982f79) [## 用 ECOD 简单统计取代异常值检测

### 一种新的基于 python 的、简单的、无参数的、可解释的无监督异常检测方法

medium.com](https://medium.com/geekculture/replace-outlier-detection-by-simple-statistics-with-ecod-f95a7d982f79) 

`[adtk](https://arundo-adtk.readthedocs-hosted.com/en/stable/)`(异常检测工具包)实现了几种专门针对时序数据的异常检测算法。

# 异常值检测的挑战

异常值检测的挑战有很多方面。挑战背后的主题是难以或不可能获得完整和准确的异常标记。

## 挑战 1:模型/算法选择

算法选择是困难的，因为离群点检测最好被框定为*无监督*或*半监督*任务。

为什么不训练一个*监督的*异常检测模型？

*   **有些未来可能出现的异常，过去从未出现过**。(例如:不可能在一份医疗表格中完全列举所有可能的错别字)
*   不平衡的类意味着**异常很少**(假设数据质量不差)
*   标签通常不可用或难以获得

那么，给定一组无监督的异常检测模型，如何确定哪个最适合您的数据呢？

你可以考虑一些启发法:

*   **检查标记为异常值的数据集的百分比。**如果检测器返回“大”百分比的数据集为异常(例如 25%)，并且数据预期质量良好，则很可能不太合适。
*   **抽查。**反常预测“看起来”反常吗？最高分预测的样本。
*   **请人类专家标记一些数据**并将你的模型的异常预测与人类标签进行比较。

## 挑战 2:异常等级和阈值选择

无监督异常检测器为观察值分配异常分数。这导致了两个问题:

1.  **按算法得分排名异常不完善**。许多高等级的观察可能是正常的(假阳性)。排名较低的观察值可能是实际的异常值(假阴性，或遗漏的真阳性)
2.  **必须选择异常值的阈值或截止值**来预测观察值是否为异常值。如果阈值太高，就会得到太多的假阴性。如果它太低，你会得到太多的误报。

**阈值选择很难，因为标签是不完美的。**

标签很难获得，并且很少包含所有可能的异常。此外，取决于兴趣或观点，用户可以不同地定义异常

**阈值选择至关重要，因为它直接影响模型质量。**

如果您有太多的误报，当人们检查异常值时，您会遇到以人为中心的挑战。

*   人类的时间是昂贵的，并且很难扩展来查看许多异常值。
*   人类很容易对一个经常出错的模型失去信任。如果你有太多的假阴性或错过了人类认为重要的真实异常值，人类可能会对模型失去信任，不会使用它。

## 挑战 3:维度和分布

许多无监督的异常检测器对数据分布做出假设。

关于你的数据的分布假设通常是错误的！

例如，可以基于非正态分布的数据集的 X 标准偏差来选择阈值。

**高维空间(许多特征)是稀疏的。**

单位 3D 立方体中两个随机点之间的平均距离约为 0.66。

在一个 1，000，000D 单位的立方体中，两个随机点之间的平均距离约为 408.25！

因此，高维数据中的大多数观测值彼此之间会相距很远，因此很难(或不太准确)将“常态”定义为靠近其他点

## 挑战 4:验证异常值预测

给定一个具有异常预测的模型，如何验证该模型？

实际上，解决方案是特定于领域的。

有几个通用的解决方案:

*   向人类发送一些异常值以获得反馈:
*   拥有一些预先标记的已知异常，并衡量模型标记这些异常的能力。

# 结论

面对这四个挑战，离群点检测是一项有趣且具有挑战性的机器学习任务。应对和解决这些挑战需要数据理解、分析技能以及与主题专家的合作。