# 使用深度学习教程的 NLP:基于感知器的情感分类器(第 3/4 部分)

> 原文：<https://pub.towardsai.net/nlp-using-deepleaning-tutorials-a-sentiment-classifier-based-on-perceptron-part-3-4-88fd202dba2c?source=collection_archive---------5----------------------->

![](img/6c8c05e2e3bc5422a45420f25b0b78e0.png)

该图像从[源](https://cdn.brandmentions.com/blog/wp-content/uploads/2019/05/sentiment-analysys-brandmentions.png)上传

自然语言处理是机器学习中最复杂的领域之一，基本上是由于语言的复杂性和模糊性。然而，它也是最成功的领域之一，有许多我们每天都在使用的真实应用，像搜索引擎、翻译工具等等。

有时最复杂的任务可以用最简单的技术解决。在这篇文章中，我将尝试探索这种说法。所以，我将基于最简单的神经网络“感知器”提出一个完整的情感分析解决方案，使用一个真实世界的任务和数据集:对 Yelp 上的餐厅评论进行正面或负面分类。

为此，我将本文分为以下四个部分:

1.  Yelp 数据集评论([链接](/nlp-using-deepleaning-tutorials-a-sentiment-classifier-based-on-perceptron-part-1-4-712eefe20899)
2.  词汇和矢量器([链接](/nlp-using-deepleaning-tutorials-a-sentiment-classifier-based-on-perceptron-part-2-4-f9b90b3a06bd))
3.  **训练套路(当前文章关注这部分)**
4.  评估和推理

> **提前感谢大家的支持。如果你决定注册成为灵媒会员，这里是我的订阅页面**:[https://abdelkader-rhouati.medium.com/membership](https://abdelkader-rhouati.medium.com/membership)

# 第 3 部分:**训练程序**

在这篇文章中，我们将概述日常训练的步骤。它负责实例化模型、迭代数据集、计算输出、计算损失(误差函数)以及调整模型参数以提高其性能。这个例程是通用的。你需要改变一些地方来适应新的模型，这样它就会成为习惯，并且容易开发新的深度学习过程。

# 二元分类器

我们使用的模型是感知器分类器的重新实现。要了解更多细节，你可以通过链接参考我以前写的一篇关于这个主题的文章:“ [NLP 使用深度学习教程:理解感知器](/nlp-using-deep-learning-tutorials-understand-the-perceptron-f2f20b324e63)”。感知器模型是最简单的神经网络，也是最古老的网络之一。但是在某些情况下仍然有效。

由于我们希望将每个评论分类为负面或正面，因此我们的模型是一个二元分类器。因此，正如您在下面的代码中所看到的，模型“ReviewClassifier”继承了 Pytorch 模型，并为负类或正类创建了单个线性布局和单个输出。sigmoid 函数用作最终非线性度。这就是我在文章《 [NLP 使用深度学习教程:了解激活函数](/nlp-using-deep-learning-tutorials-understand-the-activation-function-8f62613e32d2)》中详细谈到的激活函数。

二进制分类代码:

# 为培训做准备

为了处理关于模型如何工作的高度决策，建议初始化一个 args 对象来集中协调所有决策。如下所示，我们定义了关于数据集和训练步骤的所有模型参数，也称为超参数。

感知器二元分类器的超参数和选项；

为了跟踪关于训练进度的信息(时期索引、训练损失列表、训练准确度、验证损失、验证准确度、测试损失和测试准确度)，我们使用一个小的 python 字典变量，如下所示:

接下来的步骤实例化以下项目

*   指示我们使用 GPU 还是 CPU 的设备变量
*   数据集，从 CSV 文件加载数据
*   将文本项转换成数字向量的矢量器类
*   分类器模型，我们把它移动到 GPU 或 CPU 设备
*   作为损失函数的“BCEWithLogitsLoss”
*   还有 ADAM optimizer，和其他优化器竞争激烈。(详见参考文件【3】)

用于实例化的代码是:

# 训练循环

训练循环使用来自前一阶段的对象来更新模型参数，以便提高其性能和准确性。训练循环是在两个主要循环上完成的:一个是对数据集中的小批进行的内部循环，另一个是将内部循环重复多次的外部循环，称为 epochs。历元的数量控制训练应该在数据集上进行多少遍。

在外部循环的顶部，我们为 epoch 索引和批处理生成器添加了一些实例。我们还使用方法“classifier.train()”将模型切换到“训练模式”。这是更新超参数所必需的。

内部循环包含更新模型参数的基本操作。这分 5 步完成:

*   步骤 1:使用 optimizer.zero_grad()重置优化器的梯度
*   步骤 2:输出是模型中的计算机
*   步骤 3:损失函数用于计算模型输出和监督目标(数据集上的真实类别标签)之间的损失
*   步骤#4:使用“loss.backward()”将梯度反向传播到每个参数
*   第 5 步:最后一步使用“optimize.step()”方法更新模型的参数。

最后，我们将每个时期的损失和准确性跟踪到变量“train_states”中

以下是培训路线的代码:

在运行下一个时期的训练之前，我们在验证数据上添加一个循环，如下面的代码所示。目标是衡量模型对训练期间模型看不到的数据的执行情况。为此，我们使用方法“classifier.eval()”使模型参数不可变，并禁用梯度损失和传播的计算。这很重要，因为我们不希望模型根据验证数据调整其参数。

模型验证的代码:

**结论**:

在本文中，我们已经涵盖了我们工作的核心，即我们的机器学习模型的设计和训练。我们已经看到了如何定义一个基于感知器原理的二元分类器。我们创建了代码来训练分类器，并使用验证数据集测量其性能。

在下一篇文章，也是本系列的最后一篇文章中，我们将展示模型的推理部分，并以一个综合来结束，该综合恢复了所展示模型的一些可能的改进

**参考文献:**

1.  《用 Pytorch 进行自然语言处理》一书([https://www . Amazon . fr/Natural-Language-Processing-py torch-Applications/DP/1491978236](https://www.amazon.fr/Natural-Language-Processing-Pytorch-Applications/dp/1491978236))
2.  [https://py torch . org/tutorials/beginner/basics/data _ tutorial . html？高亮显示=数据加载器](https://pytorch.org/tutorials/beginner/basics/data_tutorial.html?highlight=dataloader)
3.  [https://medium . com/mlearning-ai/optimizer-in-deep-learning-7 BF 81 fed 78 a 0](https://medium.com/mlearning-ai/optimizers-in-deep-learning-7bf81fed78a0)
4.  [https://pub . toward sai . net/NLP-using-deep-learning-tutorials-understand-the-perceptron-f2f 20b 324 e 63](/nlp-using-deep-learning-tutorials-understand-the-perceptron-f2f20b324e63)
5.  [https://pub . toward sai . net/NLP-using-deep-learning-tutorials-understand-loss-function-2 AAF 73 EC 6 C2 b](/nlp-using-deep-learning-tutorials-understand-loss-function-2aaf73ec6c2b)
6.  [https://pub . toward sai . net/NLP-using-deep-learning-tutorials-understand-the-activation-function-8f 62613 e32d 2](/nlp-using-deep-learning-tutorials-understand-the-activation-function-8f62613e32d2)