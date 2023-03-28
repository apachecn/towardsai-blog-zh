# 机器学习模型开发

> 原文：<https://pub.towardsai.net/machine-learning-model-development-509e61f4ed36?source=collection_archive---------5----------------------->

## [云计算](https://towardsai.net/p/category/cloud-computing)

## 本文将重点介绍 GCP 专业机器学习工程师认证[第四节:ML 模型开发](https://cloud.google.com/certification/guides/machine-learning-engineer)。

![](img/e8acaede47f52ee782c025312a3fe23c.png)

照片由[布雷特·乔丹](https://unsplash.com/@brett_jordan?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/construction?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 拍摄

如果你打算参加认证，这将是一个很好的起点。如果你没有，这将帮助你开发在快速发展的机器学习生态系统中取得成功所需的基本知识。

**这不是认证学习指南。**

这篇文章的目的是对复杂的想法提供一个简单的解释，并给出一个广泛的主题观点。大纲模仿 [GCP 专业机器学习工程师认证](https://cloud.google.com/certification/guides/machine-learning-engineer)指南。

我嵌入了有用阅读材料的链接，如果你愿意的话，可以深入研究一下。

# 建立一个模型。

## **框架选择:**

像任何技术平台选择一样，您有多种选择。选择一个框架不是一项简单的技术工作。这将涉及基于以下因素的决策制定:内部人才、现有技术体系、团队的可扩展性、现有基础设施、供应商的使用、对供应商的依赖程度、解决方案的关键程度、It 领导在承担风险方面的灵活性以及学习意愿。

最容易采用和适应的三个框架是:

1.  [Scikit-learn](https://scikit-learn.org/stable/index.html) :为复杂的 ML 算法和一致的端到端 ML 管道设计提供简单的接口，从而让您专注于解决手头的业务问题，而不是迷失在技术术语中。它建立在广受欢迎的 python 库 Numpy、Scipy 和 Matplotlib 之上，这些库拥有庞大的用户社区和追随者。
2.  [Tensorflow](https://www.tensorflow.org/) :是 Google Brains 团队的跨平台产品。Tensorflow 专注于大规模机器学习，是深度学习框架最受欢迎的选项。深度学习是机器学习的一个领域，它使用神经网络来做出决策，同时处理高度非结构化的数据，如文本、视频&图像。
3.  [Cloud AutoML](https://cloud.google.com/automl/docs) :即使你对机器学习的了解有限，也能让你获得机器学习的力量。您可以使用 AutoML 来构建 Google 的机器学习功能，以创建适合您业务需求的自定义机器学习模型，然后将这些模型集成到您的应用程序和网站中。

实际上，你很少会使用任何普通的框架。因此，使用彼此适合的框架是明智的。scikit-learn & tensor flow 的 python 实现无缝工作，这主要归功于两个框架清晰一致的接口设计。如果你想在其他细节还没有解决的时候就启动这个计划，AutoML 可能是个不错的选择。

[](https://medium.com/@ODSC/top-7-machine-learning-frameworks-for-2020-7e45164914e1) [## 2020 年 7 大机器学习框架

### 机器学习是一场没有结构的噩梦。你不能从头开始构建一切，尤其是如果…

medium.com](https://medium.com/@ODSC/top-7-machine-learning-frameworks-for-2020-7e45164914e1) 

## 给定可解释性需求的建模技术

ML 模型本质上是一个黑箱。将解决方案的输出解释为*“该解决方案预测 x 是因为 1…2…3…”*对于最终用户来说至关重要，他们将根据输出做出决策。

作为一个解决方案实施者，当你选择一个模型时，确保你理解*“它做什么”*，即使你不理解技术和数学细节。每个用例都有不同的可解释性需求。不管怎样，如果你能解释为什么解决方案能预测到它所预测到的东西，你就能更好地与你的最终用户建立信任。

理解和解释人工智能解决方案的结果的能力是人工智能的一个快速发展的领域——可解释的人工智能。

[](https://cloud.google.com/explainable-ai) [## 可解释的人工智能|谷歌云

### 可解释的人工智能是一套工具和框架，帮助你理解和解释你的机器做出的预测…

cloud.google.com](https://cloud.google.com/explainable-ai) 

## 迁移学习

当你开发一个人工智能模型来解决一个问题时，你会想要重用所学的知识来解决另一个相关的问题。从一个问题到解决另一个相关问题的学习转移被称为转移学习，这是一个巨大的节约资源的机会。

大量的时间、金钱和资源被用于构建解决方案。如果我们不得不再次重复所有的活动来解决一个类似的问题，那将是可耻的。以新冠肺炎疫苗分销为例。跟踪分发、管理、副作用和对病毒传播的影响都是过去已经完成的活动，因此，由于精确的冷藏要求和冷链的可用性，必须利用以前活动的经验来管理新冠肺炎疫苗分发，这具有额外的紧迫性和重要性。

如果你理解预先训练好的模型，并且知道如何集成它，那么来自 Google 或愿意开源的组织的预先训练好的模型可以为构建你的解决方案带来巨大的价值。

[](https://www.tensorflow.org/tutorials/images/transfer_learning) [## 迁移学习和微调| TensorFlow 核心

### 此外，您应该尝试微调一小部分顶层，而不是整个 MobileNet 模型。在大多数情况下…

www.tensorflow.org](https://www.tensorflow.org/tutorials/images/transfer_learning) 

## 模型泛化和过拟合

在训练期间的监督学习中，目的是将您的预测结果与标记数据集中的实际结果进行比较。你的预测越接近实际，你的解决方案就越好。但这不是全部真相。

如果您的模型预测与您的实际值匹配程度如此之高，以至于您的解决方案不可能一般化，那么您就有一个过度拟合的问题。过度拟合是监督学习的一个问题。你的模型调整得如此之好，以至于它失去了预测任何你没有涵盖或没有数据的情景的灵活性。

为了避免这种情况，您必须一般化您的模型，以处理您在设计模型时没有意识到的场景。这可以通过适当地创建一个训练测试分割和模型验证的混合来完成。

[](https://developers.google.com/machine-learning/crash-course/generalization/peril-of-overfitting) [## 泛化:过度适应的危险|机器学习速成班

### " type": "thumb-down "，" id ":" missingtheinformationneed "，" label ":"缺少我需要的信息" }，{ "type"…

developers.google.com](https://developers.google.com/machine-learning/crash-course/generalization/peril-of-overfitting) 

# 训练和测试模型。

在开始开发模型之前，您需要将可用的数据集分成训练集和测试集。最重要的是，这两个部分在它包含的数据类型上具有相似的覆盖范围。例如，如果您根据性别进行划分:男性在训练集中，女性在测试集中，那么显然您的模型将无法通过测试。

![](img/148ab1af9041a56ceaef9ebe5e95c683.png)

将可用数据集分成训练集和测试集。

在训练集的不同截面上训练您的模型，捕获每个截面的指标以建立测试基线。用于评估模型性能的一些常用指标有:

1.  失败
2.  准确(性)
3.  精确度/召回率
4.  ROC 曲线下的面积

[](https://developers.google.com/machine-learning/testing-debugging/metrics/metrics) [## 使用指标评估模型

### " type": "thumb-down "，" id ":" missingtheinformationneed "，" label ":"缺少我需要的信息" }，{ "type"…

developers.google.com](https://developers.google.com/machine-learning/testing-debugging/metrics/metrics) 

您需要考虑的另一个方面是，您构建和训练模型的环境与使用或测试模型的环境并不相同。这将在部署模型用于生产时对服务决策产生影响。

# 为模特服务。

ML 模型服务是指将经过测试的模型部署到产品中。如何为模型服务的选择因用例而异。预测量和延迟考虑是推动决策的两个因素。

如果预测量很大，并且延迟不是问题，那么对传入数据进行批处理并将预测结果存储到表中应该就足够了。如果延迟是一个问题，那么 ML 模型应该与 REST 端点一起部署，这样使用它的应用程序可以立即获得预测结果。

[](https://bugra.github.io/posts/2020/5/25/how-to-serve-model/) [## 如何为模特服务

### 有许多方法来服务 ml(机器学习)模型，但这些是我在过去几年中观察到的最常见的 3 种模式…

bugra.github.io](https://bugra.github.io/posts/2020/5/25/how-to-serve-model/) 

# 摘要

开发一个 ML 模型包括许多由技术和非技术因素驱动的决策。

倾向于建立一个从培训到服务的简单模型，实现预期的结果，然后开始优化管道是解决问题的好方法。

## 参考

1.  [https://cloud.google.com/automl/docs](https://cloud.google.com/automl/docs)