# TensorFlow 2.9 在这里:现在的用例

> 原文：<https://pub.towardsai.net/tensorflow-present-day-use-cases-1a412b7e2cf0?source=collection_archive---------2----------------------->

Tensorflow 是在麻省理工学院许可下作为机器学习的开源深度学习框架提供的。它提供了一个高级 API 和高级抽象，前者面向高效信息检索的可读性，后者支持快速定制。

![](img/70292a9f19ec148c608a1c7f50409fa4.png)

来自 Unsplash 的李东旻

TensorFlow 从深度学习社区获得对其功能和库的支持，包括 tensorflow_addons、tf.keras 和 tf.keras_addons。TensorFlow 目前有来自其他流行的深度学习框架的竞争对手，如 PyTorch、PySpark 和 WSLint。

# Tensorflow 2.9 有什么新功能？

重点关注(1) CPU 性能(默认为 oneDNN(2)用 DTensor 实现模型并行；(3)对 tf 函数的改造；(4)支持 wsl 2(Linux 的 Windows 子系统)；和(5)用 Keras 优化训练。更多信息可以在这篇文章的底部找到。

# 关于 TensorFlow 工作原理、使用案例和实施的最新信息:

**在四个象限中，张量流我认为是:**

> *关注速度，因为模型权重在同一个 GPU 中的线程上进行划分。*
> 
> *轻量级，因为模型权重分布在许多变量上，并通过 Python 调用访问。*
> 
> *可配置，因为模型重量可直接在模型代码中定制。*
> 
> *可扩展，因为模型权重可以扩展到更多数据类型和其他类型。*

![](img/9e3a41ba678cd95398f5d765ff9c4f07.png)

来自 Unsplash 的 Karly Santiago

# 它具有我期望从这种性质的工具中得到的特性:API、社区和发布的跟踪记录。

对我来说，TensorFlow 一直与众不同的一点是它围绕它建立的深度学习生态系统(参考 TensorFlow 核心库。)这个库提供了实现深度神经网络所需的所有硬件和软件组件。结果是一个用许多编程语言都熟悉和可访问的完整系统。

TensorFlow 提供了一个第三方库的生态系统，第三方开发者在构建新的神经网络架构时可以从中进行选择。由此产生的架构将具有强大的 TensorFlow 根，并将为那些以前构建过机器学习系统的人所熟悉。

![](img/e3a4663274069594c89769f625df7f41.png)

来自 Unsplash 的朱利叶斯·德罗斯特

# 关于 TensorFlow 的一些关键信息:

> *提供架构支持，可用于开发各种机器学习和深度神经网络算法。*
> 
> *它提供了一种用户体验，允许开发者和研究人员理解代码是如何构造和执行的。*
> 
> *它提供了具体的文档以方便阅读。*
> 
> *它提供了广泛的预构建模型和实验，适合创建您自己的模型和实验。API 提供了通过使用新的推荐系统来添加新的模型和实验的便利方式。*

```
It provides high-level APIs; for example, the TF1 API is a complete package that provides operators to ease the task of writing complex training algorithms.It provides convenient preprocessing and execution strategies, which are very important for carrying out optimizers.
```

> *它提供了便捷的数据流调试功能，这对于理解源代码和调试复杂计算非常重要。*
> 
> *作为 API 的一部分，TensorFlow API 目前以 tensort 库的形式提供，它是 TensorFlow API 的一个实现，但具有 tensort 特定的语法和 API。这使得 TensorRT 驱动的实验可以轻松部署到从桌面到服务器集群、移动设备和边缘设备的各种平台上。TensorRT 提供了一种灵活的、可伸缩的方式，可以在专门的编程环境中推动新的高级抽象和优化。它提供了一种机制，可以在从服务器到边缘设备、移动设备和台式机的各种平台上轻松部署和更新定制算法。*
> 
> *TensorFlow 还在 JavaScript 生态系统中为创建定制的神经网络模型提供了强大的支持(此类生态系统包括 Tensorboard、Tensor2Tensor 和 Keras 等流行的库。)*
> 
> *强大的可视化 API 使理解和使用可视化变得容易。*
> 
> *活跃的社区便于提问和改进产品。*
> 
> *它为高性能计算提供支持。*
> 
> *它提供部署和监控工具来处理高流量和复杂的部署。*

```
The TensorFlow optimizer is a low-level library that performs computations based on input data. It is useful for training new neural network algorithms and for running parallel experiments across different servers or GPUs.
```

# 高级用例:

用例 1:构建高级神经网络模型

用例 2:建模复杂的多维数据

用例 3:翻译用其他语言编写的模型

![](img/ffaf1d4bfb1630f26b242aa4e3ed1264.png)

来自 Unsplash 的 Mikoł aj

# 张量流的工作原理:

```
A TensorFlow program takes inputs from various sources and outputs output values or models. The program can then be run on different platforms to obtain different runtime performance results.
```

> *TensorFlow 在构建神经网络模型时提供了几个预构建的模型。通常，这意味着您将使用特定于机器学习领域的张量流模型。如果您正在创建一个新模型，请参考该库的文档以了解如何编写新模型。*
> 
> *默认情况下，TensorFlow 上的所有操作都在 TensorFlow 运行时环境中返回结果。如果您与 TensorFlow 有一个 API 端到端的加密连接，那么您可以在模型之外运行任何 TensorFlow 操作，并以 JSON 的形式获得结果。此功能对于调试您的模型非常有用，尤其是对于训练新模型。*

# 没有机器学习或数据流的先验知识，很容易上手。 ***速度快，因为模型权重和更新都存储为一个大张量。在一个 TensorFlow 实例上可以运行的训练示例数量没有限制。这让您可以尝试不同的实现策略，并更快地优化您的模型。***

> TensorFlow API 是一个完整的包，包含您构建和部署任何类型的机器学习系统所需的所有功能和范例。它提供了在 TensorFlow 中创建新的神经网络模型所需的所有构建块，从神经网络模型到更深奥的数据流模型。它还提供了所有方便的 API 来集成现有系统和创建新系统。
> 
> *Tensorflow 是免费和开源的，这意味着您可以部署自己定制的内核或试用社区支持的 TensorFlow Optimizer。*
> 
> *TensorFlow Hub 是一个库，它是 TensorFlow 发行版的一部分，但提供了额外的功能，提供了处理数据并行性的实用程序等。例如，并行度库提供了并行处理多个任务并对其进行迭代的方法，或者减少执行某个功能的线程数量的方法。*

![](img/21047bf67d2b1300f5efbefc0affa9cd.png)

来自 Unsplash 的叶戈尔·米兹尼克

# TensorFlow 功能强大是因为:

> *它提供了一个可重用服务的生态系统，可以轻松扩展以处理您的特定用例。*
> 
> *它为强化学习(例如优化器)提供内置支持，允许基于经验数据创建定制的学习模型。比如机器学习框架 TensorFlow。机(TensorFlow。Machine.js)为强化学习任务提供定制的学习模型。*
> 
> *它支持实验，因为它具有用于回归和单一模型实验的内置功能。*

# 它为高性能数值计算提供了内置支持。这允许开发人员构建具有低延迟的高度并行化的应用。

> 它提供了几种不同的训练方法，可用于不同的用途。第一种方法，隐藏层 TensorFlow，执行低级计算来构建被训练数据集的 2D 或 3D 模型。第二种方法是基于拓扑的张量流，它执行特定于模型的计算来描述数据在高级拓扑中是如何连接的。第三种方法是基于边的张量流，它执行特定于模型的计算来描述如何有效地遍历数据集的边。
> 
> 它允许开发人员以非常轻量级和可读的语法编写高性能的神经网络。该语言提供了出色的功能和面向对象的支持，这对于执行复杂的机器学习任务是必不可少的。
> 
> *它实现了从数据可视化和大规模机器学习到实时预测的广泛应用。*
> 
> *它几乎可以在任何支持 Python 2.7+或更高版本的 CPU 或 GPU 设备上运行。*
> 
> 它可以灵活地处理不同的用例。因此，您可以编写可重用的服务和模块来处理不同的用例。这在实现新的机器学习模型时尤其有用。

# 它提供了构建任何复杂神经网络模型所需的所有功能和操作。它从头开始被设计得很快，因为运行时开销比使用传统的神经网络框架要少。

> *它允许用许多不同的语言构建复杂的神经网络程序。*
> 
> 对于开发者来说，它允许他们编写易于扩展和定制的程序。TensorFlow 提供了许多预构建的函数和模型，以简化构建您自己的神经网络模型的任务。例如，tf.keras 库提供了强大的功能和模型来轻松构建和训练新的和预先存在的神经网络模型。

更多关于 TensorFlow 的信息可以在这里找到:[https://research.google/pubs/pub45381/](https://research.google/pubs/pub45381/)

有关 TensorFlow 2.9 发布的更多信息:[https://blog . tensor flow . org/2022/05/whats-new-in-tensor flow-29 . html](https://blog.tensorflow.org/2022/05/whats-new-in-tensorflow-29.html)