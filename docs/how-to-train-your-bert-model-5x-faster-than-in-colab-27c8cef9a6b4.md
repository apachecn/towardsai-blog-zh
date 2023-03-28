# 如何训练你的伯特模型 5X 比在 Colab 更快

> 原文：<https://pub.towardsai.net/how-to-train-your-bert-model-5x-faster-than-in-colab-27c8cef9a6b4?source=collection_archive---------0----------------------->

![](img/6a0c865fc80997345db2413975763f3f.png)

[萨布里·图兹库](https://unsplash.com/@sabrituzcu?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

# 示例笔记本

在这篇文章中，我们将使用一个叫做 TransferLearning 的笔记本，它是用来自[的文章](https://alvinntnu.github.io/NTNU_ENC2045_LECTURES/temp/sentiment-analysis-using-bert-keras-movie-reviews.html)的代码创建的，作者是 [Alvin Chen](https://alvinchen.myftp.org/) 。

我们将使用拥抱脸变形金刚库建立一个带有预训练 BERT 模型的情感分类器。

以下是您自己下载和运行笔记本所需的文件:

*   [笔记本](https://drive.google.com/file/d/1jCExDY-VUDbdVrJ3HcpSUO-9CgrwJykc/view?usp=sharing)
*   包含数据集(在单元格中下载)

# 转移学习复习

迁移学习是一种可以用来加速新机器学习模型开发的方法。它的工作原理是利用在一个数据集上训练模型所获得的知识，并将其应用于另一个相关的数据集。

例如，如果数据科学家想要建立一个模型来识别图片中的狗，他们可以使用以前项目中用于训练模型识别猫的数据。当数据有限或需要快速构建模型时，这尤其有用。

# 伯特复习者

BERT 是基于转换器的自然语言处理模型，于 2018 年提出，由谷歌开源。

该模型在大型文本语料库(如维基百科)上进行训练，可用于问答和文本分类等各种任务。BERT 可以很容易地在各种任务上进行微调，例如文本分类和命名实体识别。

# 基线性能

由于微调 BERT 模型是本例中计算量最大的部分，我们将只关注训练单元(单元#18)。

在我们上一篇文章的[中，我们使用了一台具有 8 个 CPU 内核和 32gb RAM 的笔记本电脑来获得基准性能。这个实验可能会在同一台笔记本电脑上运行，但它会花费不切实际的时间，所以我们将使用 Google Colab。Colab 提供免费的 GPU 访问，是深度学习的常用工作空间。](https://medium.com/towards-artificial-intelligence/how-to-speed-up-your-grid-search-60x-fec2a8250517)

然而，要记住的一点是，您无法预测或选择资源 GPU 的类型和 RAM 的数量将因每个会话而异。

在运行这个实验时，我们碰巧得到了一个 T4 GPU(还不错！)搭配 16 GB 的 GPU RAM 和 12 GB 的普通 RAM。伯特训练室用了 17 分 17 秒。

> 🕰之前:17 分 17 秒

# 我们的增强功能

1.  **使用混合精度**

混合精度是一种用于提高机器学习模型性能的技术。它包括在训练和推理中使用低精度数据类型(如 16 位浮点)和高精度数据类型(如 32 位浮点)。

混合精度的好处包括减少训练时间、减少内存使用和提高精度。

> 注意:并非所有硬件都支持混合精度，旧的 GPU 型号通常不支持。

因为我们使用较新的 T4(不常见，因为 Colab 通常分配较旧的 GPU)，所以我们可以利用混合精度。

为此，我们添加了以下代码行:

```
from tensorflow.keras import mixed_precisionmixed_precision.set_global_policy(‘mixed_float16’)
```

我们再次运行该笔记本，它在大约 8 分钟内完成。

**2。利用更新的 GPU**

我们做的第二个增强是利用更新、更好的 GPU 模型。我们使用了一个 V100 GPU，32 GB 的 GPU RAM 和 112 GB 的常规 RAM，成本为 3.12 美元/小时。

这一次，BERT 训练单元在 3 分 5 秒内完成——比最初的实验加速了 5 倍多，而且只花了 18 美分！

> 🏎之后:3 分 5 秒

# 关键要点

那么，在前进的道路上，我们应该记住什么？

*   混合精度有许多引人注目的优势，例如减少处理时间和内存使用，但只有在您拥有现代 GPU 硬件的情况下才能使用。当使用提供免费计算资源的云服务时，请记住这一点——您可能只能访问低端 GPU。有取舍！
*   短时间内使用强大的资源可能会很便宜。付费服务和免费服务之间的认知摩擦可能比你实际花费的要多。您也许能够以不到一美元的成本获得显著的性能提升。
*   像这样的例子通常坚持小规模以促进可重复性，但是提高性能的技术通常是通用的。在更大规模的项目中尝试它们！

# 如果你觉得这篇文章有帮助，我们也写过类似的文章！

您可能会喜欢:

*   [如何加快你的网格搜索 60x](https://medium.com/towards-artificial-intelligence/how-to-speed-up-your-grid-search-60x-fec2a8250517)
*   [从 JupyterLab 到云的规模 ML 实验](https://medium.com/@optumi/scale-ml-experiments-from-jupyterlab-to-the-cloud-141bd645d8e9)

请在下面留下你的掌声，这样媒体上的其他人就能看到，这样我们就知道要制作更多🙃👏

# 关于作者

我主要写实用的数据科学和机器学习工作流挑战，并介绍解决它们的方法。

你可以在 [Medium](https://medium.com/@optumi) 或者 [LinkedIn](https://www.linkedin.com/in/chrismarrie/) 上关注我。