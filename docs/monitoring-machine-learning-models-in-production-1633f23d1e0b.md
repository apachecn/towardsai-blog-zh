# 监控生产中的机器学习模型

> 原文：<https://pub.towardsai.net/monitoring-machine-learning-models-in-production-1633f23d1e0b?source=collection_archive---------1----------------------->

## 生产中的 ML 模型监控指南

![](img/e0440ebd52c44f0028fbc424291f2b30.png)

图片由[大卫·比林斯](https://unsplash.com/@dav_billings)从 [Unsplash](https://unsplash.com/photos/C-NjurcSNQM) 拍摄

本文将概述生产环境中的模型监控。我将介绍在将机器学习模型投入生产时您应该跟踪的各种指标，以及它可能带来的相关含义和影响。一旦数据科学家收到来自监控组件的反馈，我将概述模型再训练过程。以下是这篇文章的提纲。

## 目录

*   什么是模型监控？
*   你应该跟踪什么？
*   数据漂移
*   模型再训练
    -高数据漂移
    -数据变化
*   模型监控架构
*   结束语
*   资源

# 什么是模型监控？

模型监控是机器学习生命周期中的一个步骤，它评估模型在生产中随时间的表现。它监控与模型可能影响的业务案例相关的各种属性，并识别模型在该特定业务案例中的正面/负面影响。它可以简单到根据各种参数识别模型的性能，也可以复杂到识别何时需要重新训练模型。

在生产中监控模型时，您应该检查各种组件，包括数据漂移、模型退化、模型性能等[1]。该监控组件向数据科学家和股东提供了关于项目相关影响的关键反馈回路。这个反馈循环可以允许模型在未来的生产过程中更好地迭代，并从整体上提供对项目的更多洞察。这是所有数据科学和工程团队在将模型投入生产时都应该包含的一个重要组成部分。

# 你应该跟踪什么？

我将概述您可以为模型监控跟踪的各种度量。这些度量将适用于不同的用例，但是通常可以应用于大多数进入生产的模型。

*   特征分布
    -跟踪训练模型所需的每个特征的分布。此外，追踪使用模型生成预测所需的每个要素的分布。
*   目标分布
    -跟踪模型被训练的目标标签的分布(仅适用于监督学习)，还跟踪生产中被预测的目标标签的分布。
*   新目标数据的频率
    ——如果是监督学习模型，跟踪一段时间内标记数据的频率是有用的。随着时间的推移，可以观察到更多的标记信息，在大量新的标记数据之后，最好重新训练模型。
*   数据漂移
    -对于你一直在追踪的分布，你可以量化这些分布的相似性和差异性。如果它们非常相似，这是一个好迹象，如果不相似，那么您可能需要重新培训/重复之前的步骤。
*   模型性能
    ——量化关于新数据的预测。例如，在监督学习的情况下，您可以生成与您预测的标签相关联的新观察值。如果新发现的标签与模型产生的预测有重叠，那么您可以假设模型在生产中表现良好。
*   模型对商业的影响
    ——想象你已经将一个广告推荐系统投入生产以提高 CTR(点击率)。一旦模型投入生产，随着时间的推移跟踪 CTR 将是模型性能和对业务影响的良好指标。

# 数据漂移

> 数据漂移是模型精度随时间下降的主要原因之一[2]。在机器学习中，数据漂移是指模型输入数据的变化，这种变化会导致性能随着时间的推移而下降[2]。数据漂移发生的原因有很多。
> 
> -数据质量问题，例如损坏的传感器读数总是为 0。
> -数据中的自然漂移，如平均温度随季节变化。
> -特征之间关系的变化，或协变量移位。
> 
> -【2】[https://docs . Microsoft . com/en-us/azure/machine-learning/how-to-monitor-datasets？tabs=python](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-monitor-datasets?tabs=python)

您可以使用各种指标来计算数据漂移。下面我就来略述几个常见的，比较容易解读的。

*   [**kull back–lei bler**](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)**散度—** 衡量一对概率分布之间的差异。
    -在 [Scipy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.special.kl_div.html) 中找到的函数`kl_div`计算给定一对分布的詹森-香农散度。
*   [**詹森-香农**](https://en.wikipedia.org/wiki/Jensen%E2%80%93Shannon_divergence) **散度—** 衡量一对概率分布之间的相似性。
    -在 [Scipy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.distance.jensenshannon.html) 中找到的函数`jensenshannon`计算给定一对分布的詹森-香农散度。

# 模型再训练

知道何时应该重新训练您的模型对于生产中持续的高性能模型是至关重要的。我将介绍两个不同的标准，您应该在模型监控部分注意这两个标准，它们表示模型再训练。

## 高数据漂移

特征或目标分布中的高数据漂移是重新训练模型的有力指标。这意味着您当前模型所依据的数据已经过时。与您训练的特性相关的分布与您当前在生产中观察到的分布有很大的不同。

## 数据的变化

假设您正在构建一个人口统计模型，该模型预测平台上尚未提供性别的用户的性别。随着时间的推移，随着营销团队不断努力获得新用户和人口统计数据，您必须用来训练模型的标记数据的数量将会增加。如果提供了大量新的标记信息，那么这是重新训练你的模型的一个强有力的指标，因为你有更多的用户被标记为某个性别。

# 模型监控架构

![](img/c2ada8d577bd2c09518dc5e589868fa0.png)

模型监控架构。图片由作者提供。

# 结束语

本文概述了将机器学习模型推向生产环境时的模型监控过程。我还谈到了实现这个过程时的架构，您应该跟踪什么指标，以及模型监控组件的结果何时对初始机器学习模型的重新训练有吸引力。

您应该尝试识别传入模型的数据分布与模型训练数据之间的数据漂移。此外，您还需要确定该模式是否对业务的其他方面有任何负面影响。跟踪这些事情将会包含一个与模型在生产环境中的性能相关的强大的反馈循环。构建模型的数据科学家可以迭代该流程，从而为公司节省/创造收入。

请注意，本文中概述的过程是经典机器学习的一个简单用例。该监控过程可以被复制用于更复杂的场景，包括推荐系统、自然语言处理、计算机视觉等中的大型复杂模型。

如果你想转型进入数据行业，并希望得到经验丰富的导师的指导和指引，那么你可能想看看最敏锐的头脑。Sharpest Minds 是一个导师平台，导师(他们是经验丰富的实践数据科学家、机器学习工程师、研究科学家、首席技术官等。)将有助于你的发展和学习在数据领域找到一份工作。点击查看[。](https://www.sharpestminds.com/?r=vatsal-patal)

# 资源

*   [1][https://www . dominodatalab . com/data-science-dictionary/model-monitoring](https://www.dominodatalab.com/data-science-dictionary/model-monitoring)
*   [2][https://docs . Microsoft . com/en-us/azure/machine-learning/how-to-monitor-datasets？tabs=python](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-monitor-datasets?tabs=python)

如果你喜欢读这篇文章，我写的其他文章你可能也会喜欢。

[](https://towardsdatascience.com/comprehensive-guide-to-github-for-data-scientist-d3f71bd320da) [## 面向数据科学家的 GitHub 综合指南

### 通过 UI 和命令行为数据科学家提供的 GitHub 教程

towardsdatascience.com](https://towardsdatascience.com/comprehensive-guide-to-github-for-data-scientist-d3f71bd320da) [](https://towardsdatascience.com/comprehensive-guide-to-python-virtual-environments-using-conda-for-data-scientists-6ebea645c5b) [## 数据科学家使用 Conda 的 Python 虚拟环境综合指南

### Conda via 终端虚拟环境指南

towardsdatascience.com](https://towardsdatascience.com/comprehensive-guide-to-python-virtual-environments-using-conda-for-data-scientists-6ebea645c5b) [](https://towardsdatascience.com/recommendation-systems-explained-a42fc60591ed) [## 推荐系统解释

### 用 Python 解释和实现基于内容的协同过滤和混合推荐系统

towardsdatascience.com](https://towardsdatascience.com/recommendation-systems-explained-a42fc60591ed) [](https://towardsdatascience.com/link-prediction-recommendation-engines-with-node2vec-c97c429351a8) [## 使用 Node2Vec 的链接预测推荐引擎

### 在 Python 中使用节点嵌入进行链接预测

towardsdatascience.com](https://towardsdatascience.com/link-prediction-recommendation-engines-with-node2vec-c97c429351a8) [](https://towardsdatascience.com/text-summarization-in-python-with-jaro-winkler-and-pagerank-72d693da94e8) [## 用 Jaro-Winkler 和 PageRank 实现 Python 中的文本摘要

### 用 Jaro-Winkler 和 PageRank 构建一个文本摘要器

towardsdatascience.com](https://towardsdatascience.com/text-summarization-in-python-with-jaro-winkler-and-pagerank-72d693da94e8)