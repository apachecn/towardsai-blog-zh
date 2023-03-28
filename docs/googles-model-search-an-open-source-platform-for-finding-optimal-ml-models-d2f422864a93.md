# Google 的模型搜索:一个寻找最佳 ML 模型的开源平台

> 原文：<https://pub.towardsai.net/googles-model-search-an-open-source-platform-for-finding-optimal-ml-models-d2f422864a93?source=collection_archive---------2----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)，[优化](https://towardsai.net/p/category/optimization)

## 从 A 到 Z 自动化关于模型架构的一切

![](img/ec519007a164ba4f5e6fe94aa656a319.png)

照片由[卢卡·布拉沃](https://unsplash.com/@lucabravo?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 拍摄

> 对于给定的问题，合适的神经网络是什么样的？应该有多深？应该使用哪种类型的层？lstm[是否足够或者变压器](https://en.wikipedia.org/wiki/Long_short-term_memory)[层是否更好？或者两者兼而有之？](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html)[组装](https://en.wikipedia.org/wiki/Ensemble_learning)或[蒸馏](https://en.wikipedia.org/wiki/Knowledge_distillation)会提升性能吗？当考虑机器学习(ML)领域时，这些棘手的问题变得更加具有挑战性，在这些领域中可能存在比其他领域更好的直觉和更深的理解。

来源:[谷歌](https://ai.googleblog.com/2021/02/introducing-model-search-open-source.html)

以上问题相当棘手。作为数据科学家，目前的方法只是尝试更有意义的可能性，评估，做出另一个选择&重复。这个过程相当耗时，网络架构搜索(NAS)已经存在一段时间了。NAS 的概念是让网络/软件为给定的任务选择最合适的架构，这样你就不必在那些冗长的实验上浪费时间。

几天前，谷歌发布了它的 NAS 框架“模型搜索”。在他们的框架中，他们试图优化 NAS 框架的现有问题，例如[1]:

1.  昂贵的计算成本
2.  需要包含大量的先验信息
3.  低概括能力

让我们从理论的角度来解释它是如何工作的。然后我们可以转到编码方面，给出一个快速教程。

那么它是如何工作的呢？

我不会深究细节，因为这不是本文的重点，你可以查看谷歌的帖子。但是，基本上，该系统运行几次试验，并且在每个周期的开始，[波束搜索算法](https://en.wikipedia.org/wiki/Beam_search)被用于基于所提供的度量来决定接下来要尝试什么。该算法是一种计算机科学启发式图搜索算法，它在这里工作得很好，因为张量流依赖于图。

该系统由多名训练员和一个评估系统组成，以便平行进行试验，并将所有模型保存到数据库中。

> 在模型搜索中实现的搜索算法是自适应的、[贪婪的](https://en.wikipedia.org/wiki/Greedy_algorithm)和增量的，这使得它们比 RL 算法收敛得更快。然而，它们确实模仿了 RL 算法的“[探索&利用](https://en.wikipedia.org/wiki/Reinforcement_learning)”本质，通过分离对良好候选的搜索(探索步骤)，并通过集合被发现的良好候选来提高准确性(利用步骤)。在对架构或训练技术应用随机改变(例如，使架构更深)之后，主搜索算法自适应地修改前 *k* 个执行实验中的一个(其中 *k* 可以由用户指定)。

来源:[谷歌](https://ai.googleblog.com/2021/02/introducing-model-search-open-source.html)

真正有趣的是，搜索算法建立在强化学习策略的基础上，它们试图平衡“探索和利用”策略，以优化模型，同时探索最佳的潜在模型。

选择的最后一点(也取决于试验)是将这些模型集成到一个模型中，还是将较大的模型提取为较小的模型。

我希望文章的下一部分更多的是关于编码，而不是理论。然而，无论如何，如果你是一个好奇的数据科学家(像我一样)，我建议看看谷歌的这篇论文，我相信很多理论都是建立在它的基础上的:

[通过大规模的神经架构搜索改进关键词定位和语言识别](https://pdfs.semanticscholar.org/1bca/d4cdfbc01fbb60a815660d034e561843d67a.pdf)

本文深入探讨了有趣的 NAS，详细介绍了塔式搜索算法、何时集合、语言识别等等。它还深入探讨了 NAS 背后的数学原理。

## 让我们把它付诸实践

他们在 [Github](https://github.com/google/model_search) 上提供了框架，它目前只支持分类问题(遗憾的是)，但我认为你可以很容易地将它用于回归问题。他们将 2 个用例分成 CSV 数据和非 CSV 数据。

## 对于第一种情况:CSV 数据

让我们从进口开始:

```
import model_search
from model_search import constants
from model_search import single_trainer
from model_search.data import csv_data
```

来源: [Github](https://github.com/google/model_search)

然后我们实例化 SingleTrainer 和 csv_data 实例

```
trainer = single_trainer.SingleTrainer(
    data=csv_data.Provider(
        label_index=0,
        logits_dimension=2, # the number of outputs, 2 is for binary
        record_defaults=[0, 0, 0, 0],
        filename="model_search/data/testdata/csv_random_data.csv"),
        spec=constants.DEFAULT_DNN)
```

来源: [Github](https://github.com/google/model_search)

“spec”参数指向存储库中您可以更改的配置。我研究了默认的 DNN 配置，它指定了最常用的 DNN 层选择:

*   深度
*   完全连接的层
*   指数式衰减
*   规范化
*   宽度
*   组装和蒸馏

最后，进行试验:

```
trainer.try_models(
    number_models=200,
    train_steps=1000,
    eval_steps=100,
    root_dir="/tmp/run_example",
    batch_size=32,
    experiment_name="example",
    experiment_owner="model_search_user")
```

来源: [Github](https://github.com/google/model_search)

## 对于第二种情况:非 CSV 数据

这个用例比前一个稍微难一点。与 Pytorch 加载器一样，您必须设计自己的类并从它们的抽象类`model_search.data.Provider.`继承，这包括定义输入函数和任务

**最终想法和要点**

我希望这篇文章能让你对 Google 的模型搜索有一个大致的了解。如果你有兴趣了解更多关于它的特性，我还没有介绍他们的 Github 库，比如:

*   向搜索空间添加模型和架构
*   创建定型独立二进制文件，而不编写主
*   分布式运行
*   云汽车

看看这个框架是否会在诸如 Kaggle 比赛这样的挑战中实际使用，或者它是否不会被社区使用，它只是被浪费掉，这将是很有趣的。(希望不会)。我想已经有很多关于 NAS 的论文了，但是大部分都没有做成框架。

**参考文献:**

[1][https://ai . Google blog . com/2021/02/introducing-model-search-open-source . html](https://ai.googleblog.com/2021/02/introducing-model-search-open-source.html)