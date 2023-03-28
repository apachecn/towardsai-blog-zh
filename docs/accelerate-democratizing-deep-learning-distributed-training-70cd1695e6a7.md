# 加速:民主化深度学习分布式培训

> 原文：<https://pub.towardsai.net/accelerate-democratizing-deep-learning-distributed-training-70cd1695e6a7?source=collection_archive---------0----------------------->

## [深度学习](https://towardsai.net/p/category/machine-learning/deep-learning)

## 扩大模型培训的需求比以往任何时候都高；别担心，你不需要改变太多

![](img/95c1440340de6f8a79fc6fac4e586461.png)

由[粘土银行](https://unsplash.com/@claybanks?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/accelerate?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄

机器学习和深度学习领域在过去十年中取得了巨大的发展。这主要是由于硬件的进步和我们现在能够产生和收集的大量数据。

因此，将模型训练扩展到更多计算资源的需求比以往任何时候都高。但这对你来说意味着什么？除了获得或租用更多的设备，你需要学习一个新的 API 或放弃你目前的习惯吗？分布式培训需要高级软件工程技能吗？

> 如今，将模型训练扩展到更多计算资源的需求比以往任何时候都高。

幸运的是，如果你是 PyTorch 用户，你很幸运；你只需要添加/修改四行代码。事实上，最终，你的代码看起来会更简单，更容易理解！

> [学习率](https://www.dimpo.me/newsletter?utm_source=medium&utm_medium=article&utm_campaign=accelerate)是为那些对 AI 和 MLOps 的世界感到好奇的人准备的时事通讯。你会在每周五收到我关于最新人工智能新闻和文章的更新和想法。在这里订阅！

# DNN 训练的基础

首先，让我们看看如何在 PyTorch 中实现一个标准的训练循环。我们将使用它作为一个运行示例。这个脚本的目的是强调 PyTorch 训练循环的步骤，这样我们就可以直接看到我们应该改变什么以及如何改变。

通常，为了训练 DNN，我们遵循以下算法:

1.  我们在训练数据集上获得预测，并计算损失(即向前传递)
2.  我们使用反向传播算法(即反向传递)来计算梯度
3.  我们更新模型的参数(即优化步骤)

让我们看看 PyTorch 代码中的这些步骤:

首先，我们实例化我们的模型，一个转换器，并将其参数传递给我们选择的设备。然后，我们实例化优化器并加载数据集。

然后，我用代码中的注释标记了上面的三个步骤。查找第 20、23 和 25 行。

# 分发一切

基于 PyTorch 构建的几个框架提供了一种简单的方法来分发培训过程。比如这里可以看到 fastai 如何处理分布式训练[。](https://docs.fast.ai/distributed.html#DistributedTrainer)

虽然他们试图通过增加一个抽象层次来简化这个过程，但是你应该熟悉他们的 API 来创建和控制你自己的训练循环。

另一方面，Hugging Face 的新库旨在实现相同程度的简化，而不中断您的代码。再说说`Accelerate`！

安装完这个库之后，通过一个简单的`pip install accelerate`调用，在任何设备上分发 PyTorch 代码都需要做以下事情:

您需要做的第一件事是导入并实例化一个`Accelerator`对象。您不需要为`model`或`data`指定设备，因为`Accelerate`可以为您处理设备放置。

然后，在第 15 行，你准备好你的`model`、`data`和`optim`物品，开始你习惯的训练。最后，在第 24 行，您应该用`accelerator.backward(loss)`替换`loss.backward()`调用。你完了！

现在，您的培训循环更加简单，没有设备放置，也没有分发培训样板代码！

# 它是如何工作的

首先，实例化`Accelerator`对象的代码行不仅仅做这些；它还决定分布式训练运行的类型，并执行必要的初始化。我们可以通过传递一个参数`cpu=True`来强迫它使用`CPU`，或者利用`fp16=True.`进行混合精度训练

然后，`accelerator.prepare`方法准备`model`、`DataLoaders`和`optimizer`。它用适当的分发器包装模型，例如,`DistributedDataParallel`容器，它将数据批次放置到相关设备，并准备好`optimizer`来处理混合精度训练。

最后，`accelerator.backward`方法处理向后传递的必要步骤。

# 结论

深度神经网络(DNNs)一直是机器学习领域大多数最新进展背后的主要力量。然而，这些进步在很大程度上依赖于我们可支配的数据量，这是保持深度学习引擎运行的燃料。因此，将模型训练扩展到更多计算资源的需求比以往任何时候都高。

有两种方法可以实现这一点:(I)数据并行化或(ii)模型并行化，前者是最常用的方法。我们从一个简单的例子开始我们的旅程，展示 PyTorch Distributed 是如何工作的:

[](https://towardsdatascience.com/distributed-deep-learning-101-introduction-ebfc1bcd59d9) [## 分布式深度学习 101:简介

### 如何用 PyTorch 编写分布式深度学习应用的指南

towardsdatascience.com](https://towardsdatascience.com/distributed-deep-learning-101-introduction-ebfc1bcd59d9) 

然后，我们更深入一点，用一个真实的例子构建了一个教程:

[](https://towardsdatascience.com/pytorch-distributed-all-you-need-to-know-a0b6cf9301be) [## PyTorch 分发:所有你需要知道的

### 用 PyTorch 编写分布式应用程序:一个真实的例子

towardsdatascience.com](https://towardsdatascience.com/pytorch-distributed-all-you-need-to-know-a0b6cf9301be) 

最后，我们看到了如何使用 Kubeflow 和 PyTorch 操作符在 Kubernetes 上正确地完成这项工作:

[](https://towardsdatascience.com/pytorch-distributed-on-kubernetes-71ed8b50a7ee) [## 停止在一个 GPU 上训练模型

### 今天，没有什么可以阻止你在多个 GPU 上扩展你的深度学习训练过程

towardsdatascience.com](https://towardsdatascience.com/pytorch-distributed-on-kubernetes-71ed8b50a7ee) 

本文研究了如何在不中断代码的情况下扩展我们的训练循环。`[Accelerate](https://huggingface.co/docs/accelerate/)`通过[抱紧脸](https://huggingface.co/)是目前为止最简单的实现方式。你提议用什么方法来并行化你的训练循环？你打算用`Accelerate`吗？让我们在评论区开始讨论吧！

# 关于作者

我的名字是[迪米特里斯·波罗普洛斯](https://www.dimpo.me/?utm_source=medium&utm_medium=article&utm_campaign=accelerate)，我是一名为[阿里克托](https://www.arrikto.com/)工作的机器学习工程师。我曾为欧洲委员会、欧盟统计局、国际货币基金组织、欧洲央行、经合组织和宜家等主要客户设计和实施过人工智能和软件解决方案。

如果你有兴趣阅读更多关于机器学习、深度学习、数据科学和数据操作的帖子，请关注我的 [Medium](https://towardsdatascience.com/medium.com/@dpoulopoulos/follow) 、 [LinkedIn](https://www.linkedin.com/in/dpoulopoulos/) 或 Twitter 上的 [@james2pl](https://twitter.com/james2pl) 。

所表达的观点仅代表我个人，并不代表我的雇主的观点或意见。