# 机器学习工作流:编码指南

> 原文：<https://pub.towardsai.net/machine-learning-workflow-a-coding-guide-c95dedb5b42?source=collection_archive---------3----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)，[编程](https://towardsai.net/p/category/programming)

## 探索人工神经网络模型训练步骤的初学者指南

![](img/506be35f2105f1688fc9fe525d9e959d.png)

照片由[阿尔瓦罗·雷耶斯](https://unsplash.com/@alvarordesign?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

当我是机器学习的新手时，我不知道从哪里开始，如何开始模型训练？即使我知道所有的关键点，对我来说还是很难进入编码领域，我认为这对每个新手来说都很正常。

所以我决定写 ML 工作流来解决所谓的困惑。在本文中，我们将使用 Keras 的内置 **MNIST** 影像数据集。那我们开始吧。

# 1.数据准备:

![](img/4ecc9ef1a5701307bad0ec682838c3a9.png)

照片由[米卡·鲍梅斯特](https://unsplash.com/@mbaumi?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

## a)将数据转换成 Numpy 数组:

*   在将数据(图像或文本)输入模型之前，应该先将其转换成 Numpy 数组。如果您只是从像 Keras/Tensorflow 2.0 这样的 ML 库中导入预加载的数据，那就可以了。因为数据已经进入 Numpy 数组的元组。
*   然后，将整个数组数据集分解为**训练**(训练样本+训练标签)**数据集**和**测试**(测试样本+测试标签)**数据集**。

Numpy 返回数组

## b)缩放:

*   在将图像/文本数据转换成一个 Numpy 数组并将数据分成 4 个子数据集之后，接下来要做的事情是在[0，1]区间内缩放我们的样本数据。但是我们为什么需要扩展呢？缩放的目标是加快算法的计算速度。它用于将数据集中数值列的值更改为使用通用比例，而不会扭曲值范围的差异或丢失信息。一些算法也需要正确地对数据建模。

图像的像素值为 0-255，这就是将数组除以 255.0 的原因

## c)分类编码:

如果训练和测试标签是字符串，您应该将它们转换为数值。但是，此时您必须在这两种编码方法之间做出选择:

*   **标签编码**
*   **一键编码**

如果你不知道是只做标签编码还是两者都做 [Raheel Shaikh](https://medium.com/u/8978a39fecd0?source=post_page-----c95dedb5b42--------------------------------) 的文章"[选择正确的编码方法-标签与 OneHot 编码器](https://towardsdatascience.com/choosing-the-right-encoding-method-label-vs-onehot-encoder-a4434493149b)"将帮助你做到这一点😃。

> 对我来说，标签已经是数字了。因此，我不会执行分类编码步骤。

# 2.构建模型:

现在接下来的事情是建立一个模型。当建立一个模型时，你必须考虑你选择的激活函数。一般来说，在分类问题中， **Relu** 在中间层工作得很好，但是在最终的输出层，你要仔细选择激活函数才能得到想要的结果。这里我使用了 **Softmax** ，因为我正在处理**多类分类**问题。如果你正在进行**二元类分类，你可以使用 **Sigmoid** 。**

# 3.编译步骤:

现在轮到它的编译了。

*   如果您正在处理回归预测建模问题，可以使用两个最常见的损失函数:MSE `mean_squared_error` 或 MAE `mean_absolute_error`。
*   在二元分类中，一般使用`binary_crossentropy`。然而，`hinge`与支持向量机(SVM)模型一起使用。
*   在多类，单标签分类，如果你做标签编码`categorical_crossentropy`将被使用。否则，使用`sparse_categorical_crossentropy`作为损失函数。
*   多类，多标签分类有点不一样。您将使用`binary_crossentropy`和`sigmoid`作为激活功能。

# 4.训练模型:

一旦您完成了数据预处理、构建模型架构和编译，您就可以开始训练您的模型✌️.了

# 5.评估培训:

在这一步中，您将检查您的训练模型在测试集上是否表现良好。

输出:10000/1–1s—损耗:0.0386 —精度:0.9771

# 6.重复步骤 2–5:

*   如果评估结果不令人满意，只需稍加修改即可重复这些步骤。

# 7.预测(可选):

*   最后，你可以预测你自己的(或自己创造的)随机数据。

# 8.保存您的模型:

此外，建议保存您的模型，以便将来您可以在 AI 桌面应用程序或 web 应用程序中使用它。

# 结论:

![](img/c4ad960c7dd555daa8b6fd0a269d79e8.png)

照片由 [Aaron Burden](https://unsplash.com/@aaronburden?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

让我们总结一下到目前为止所学的内容。

*1。准备数据。*

> **-加载内置数据；**作为 Numpy 数组返回。
> 
> **-加载下载/自定义数据；**将数据转换成 Numpy 数组。
> 
> **-缩放。**
> 
> **-分类编码；**标签编码/一键编码。

2.构建模型架构。

3.执行编译步骤。

4.训练模型。

5.评估训练好的模型。

6.如果你得到不满意的结果，重复这些步骤，直到你得到满意的结果。

7.预测。

8.保存训练好的模型。

![](img/6e3a40083d0e652fb0838d4358b3029e.png)

马库斯·斯皮斯克在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

在下一篇文章中，我们将学习如何使用 **Flask 开发机器学习 Web 应用程序。👍**

敬请关注。👋