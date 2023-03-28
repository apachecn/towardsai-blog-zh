# 评估指标是您需要在早期定义的

> 原文：<https://pub.towardsai.net/evaluation-metrics-are-what-you-need-to-define-in-the-earlier-stage-99dbfae51472?source=collection_archive---------1----------------------->

## 统计数字

## 为什么一开始就需要定义指标

![](img/c6ea513229508a51f95260bcabb5b625.png)

[马志威](https://unsplash.com/@makcedward?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral) 上拍照

> 如果你不知道如何证明一个模型是好是坏，这就好比你想得到某样东西却不知道它是什么。作为一名数据科学家工作了几年后，我坚信在早期阶段定义指标是非常重要的事情。

在这一系列的故事中，我将涵盖一些我们在衡量模型有多好时应该使用的通用指标。**精度**和**均方差(MSE)** 可能会在谈到度量时立即出现。然而，我想强调的是，我们的观众可能不明白它是什么。因此，我们需要准备**内部**和**外部**指标。

对于**内部**度量，我简单的引用 **Precision** 、 **MSE、**是为了与那些具备知识的人交流，以深入理解机器学习。相比之下，**外部**指标是为与高层管理人员等非技术受众沟通而设计的。这是因为我们可能需要用通俗的术语来说明我们的工作。否则，他们可能不知道我们在说什么。

## 分类问题中的外部评价指标

由于我们总是需要在**精度**和**召回之间取得平衡，**可能很难同时拥有两个好的结果。你可以向你的观众展示**精确**和**召回**的结果，但你必须解释那是什么意思。

我们需要思考，如果我们正在建立一个癌症诊断分类模型，我们是否需要更高的**精度**和**召回**。为此，我们需要考虑错误预测的成本。我认为，我们需要更高的**召回**而不是更高的**精度**。原因是我们可能更喜欢诊断一个患了癌症而不是健康的病人。

我们需要补充的不是给出一个好的**回忆**，更高的回忆意味着我们将降低把一个癌症患者归类为健康人的几率。

## 回归问题中的外部评估度量

**均方误差(MSE)** 和**平均绝对百分比误差(MAPE)** 是回归问题中一些常见的评价指标。

我们需要展示关注这些指标的影响，而不仅仅是向观众展示。MAPE 是一种测量百分比误差的方法。我总是把它转换成“准确性”，因为对于非技术观众来说，这是一个非常容易理解的术语。

如果 MAPE 是 20%，我就换算成 80%的准确率(100% — 20%)，大家就明白它有多好了，虽然就含义而言可能不是 100%准确。

更详细解释将很快发布:

*   [分类问题的度量](https://medium.com/towards-artificial-intelligence/evaluation-metrics-for-classification-problems-e7442092bc5)
*   [回归问题的度量](https://medium.com/towards-artificial-intelligence/evaluation-metrics-for-regression-problems-fff2ac8e3f43)
*   [文本问题的度量](https://medium.com/towards-artificial-intelligence/evaluation-metrics-for-textual-problems-6e881feef5ad)

# 关于我

我是湾区的数据科学家。专注于数据科学、人工智能，尤其是 NLP 和平台相关领域的最新发展。你可以通过[媒体博客](https://medium.com/@makcedward/)、 [LinkedIn](https://www.linkedin.com/in/edwardma1026) 或 [Github](https://github.com/makcedward) 联系我。