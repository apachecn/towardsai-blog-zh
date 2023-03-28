# 2021 年每个机器学习领域的最先进模型

> 原文：<https://pub.towardsai.net/state-of-the-art-models-in-every-machine-learning-field-2021-c7cf074da8b2?source=collection_archive---------0----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

## 你能想到的每一个 ML 领域的最好的 SOTA 模型的集合

![](img/d7a74cd34e4aba42b41e31071e609385.png)

照片由[乔恩·泰森](https://unsplash.com/@jontyson?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

最先进的模型一直在变化。作为一个已经参加 Kaggle 竞赛将近一年的人，我发现自己遇到了很多这样的竞赛，对它们进行比较、评估和测试。我认为列出每个 ML 任务的最佳模型是个好主意，这样你就知道从哪里开始了。

在我们开始之前，如果您正在寻找一个系统来处理您的机器学习工作负载，请看看 SabrePC。他们目前提供一个预建的人工智能工作站，起价 3700 美元，由多达 4 个支持 NVIDIA CUDA 的 GPU 驱动，预装了最新的深度学习软件堆栈，并包括 3 年保修。(注:虽然我推广这个产品是有经济补偿的，但是你买一个我就不收任何佣金了！)

没有别的事了，我们开始吧！

## **1。图像分类**

*   [**efficient net v2**](https://towardsdatascience.com/google-releases-efficientnetv2-a-smaller-faster-and-better-efficientnet-673a77bdd43c)

EfficientNetsV2 比最先进的图像分类网络高出 2%,同时训练速度提高了 5-11 倍，这是一个巨大的进步。模型训练速度一直是机器学习的一个巨大瓶颈，因为它只是让调试网络问题变得非常漫长。尽管它们在最近发布后还没有经过全面测试，但我想我们都同意 EfficientNet 是一个 SOTA 图像分类模型。

*   [**无规格化器网络(NF-Nets)**](https://towardsdatascience.com/deepmind-releases-a-new-state-of-the-art-image-classification-model-nfnets-75c0b3f37312)

今年对模型的一个主要关注点不是在基准数据集(如 ImageNet21k)上实现性能的大幅提升，而是在训练速度上实现大幅提升。NF-Nets 消除了批量标准化，并引入了自适应梯度裁剪，训练速度提高了 9 倍，同时在 ImageNet 上具有相同的 SOTA 性能。

## **2。图像分割**

*   [**高效 U 网**](https://openaccess.thecvf.com/content_CVPRW_2020/papers/w22/Baheti_Eff-UNet_A_Novel_Architecture_for_Semantic_Segmentation_in_Unstructured_Environment_CVPRW_2020_paper.pdf)

u-网在图像分割方面非常强大。优化 U-Net 的最近趋势是将 SOTA CNN 作为 U-Net 编码器/主干。由于 EfficientNet 是主要的 SOTA 图像分类模型之一，最近发布了一篇论文，用 efficient Net 替换 U-Net 的编码器，并显示了令人印象深刻的结果。我也可以看到 Eff-Unets 在图像分割比赛中广泛使用，从而提高了它的价值。

## 3.**物体检测**

*   [**YoloV5**](https://towardsdatascience.com/advanced-yolov5-tutorial-enhancing-yolov5-with-weighted-boxes-fusion-3bead5b71688)

当然，Yolo 在物体检测领域已经相当受欢迎。所以我不认为这部分需要更多的解释，因为有很多关于 YoloV5 的文章。

*   [**【VF-Net】**](https://arxiv.org/abs/2008.13367)

我在做一个物体探测比赛的时候偶然发现了 VF-Net，我对它的表现感到惊讶。它似乎总是匹配 Yolo 的表现，有时甚至超过它。VF-Net 的作者引入了一种新的“Iou 感知分类分数”,它在过滤预测框以获得更准确的平均精度方面做了大量工作。他们还设计了一种新的损失函数，称为**变焦距损失**，并提出了一种新的“星形包围盒”。这听起来对我来说非常有趣，我肯定会很快就此写一篇单独的文章。如果你有兴趣尝试使用 MMDetection，可以查看我的教程[这里](https://towardsdatascience.com/mmdetection-tutorial-an-end2end-state-of-the-art-object-detection-library-59064deeada3)。

## 4.表格数据和时间序列

表格数据非常受欢迎，因为许多机器学习项目都是建立在表格数据之上的。这是经典机器学习算法似乎优于深度学习网络(或至少表现相同)的少数地方之一。

*   **梯度增压机(LGBM，XGBoost & Catboost)**

我很惊讶地看到一个简单的算法(与其他 DL 网络相比)，如 Light-GBM 在 Kaggle 比赛中胜过神经网络。性能上的差异并不大，但在 90 年代达到 1-2%并不容易。

梯度推进机器已经出现了很多，它们是建立在决策树之上的。它们最吸引人的特点是它们的可解释性和易用性。如果你是机器学习的初学者，我绝对建议从梯度推进机器开始，更具体地说是基础决策树。

*   **图形神经网络**

图形神经网络已经成为机器学习领域的一个热门话题。我记得在今年流行的 ML 会议上看到了大量的 GNN 论文。

gnn 提供的最好的东西之一是它们的灵活性。许多基于文本的机器学习问题可以转化为基于图的问题，这使得 GNNs 的使用成为可能。此外，GNNs 可以通过图形卷积网络用于图像。此外，我已经看到大量的 ML 解决方案通过使用注意力来促进 GNNs。因此，我将它添加到列表中的主要原因是它提供的灵活性和 SOTA 性能。如果你感兴趣，可以看看我这篇关于 GNNs 参加挑战性 Kaggle 比赛的文章:

[](https://towardsdatascience.com/what-i-learned-from-stanfords-covid-mrna-vaccine-kaggle-competition-98d3f454eef) [## 从斯坦福的 Covid mRNA 疫苗 Kaggle 竞赛中我学到了什么

### 如果你真的对机器学习感兴趣，你一定听说过令人惊叹的数据科学竞赛…

towardsdatascience.com](https://towardsdatascience.com/what-i-learned-from-stanfords-covid-mrna-vaccine-kaggle-competition-98d3f454eef) 

## **5。自然语言处理**

你可能已经猜到变形金刚是当前 NLP 的 SOTA，而不是谈论你可能已经读过无数遍的变形金刚的基础知识，我想谈谈最近的基于变形金刚的模型。

*   **OpenAI GPT-3**

可能会围绕这个列表中的一些模型进行一些讨论，但我认为我们都同意 GPT-3 是最强大的 NLP 模型之一。有大量的文章展示了它在编写代码、编写内容、回答问题等方面的用途。尽管说实话，我仍然不认为它真的会取代编码员/编写者，等等…仅仅因为它是在网上内容上训练的，因此它将产生的所有东西都是已经存在的东西的混合物。我知道你在想什么，有些混合物可能仍然很好，但就我个人而言，我不认为 GPT-3 生产那些，也许 GPT-4！但是，平心而论，我仍然对它的功能印象深刻。

*   **伯特(当然)**
*   **尊贵提:** [**谷歌开关变形金刚**](https://towardsdatascience.com/google-switch-transformers-scaling-to-trillion-parameter-models-with-constant-computational-costs-806fd145923d)

我不确定我是否会把谷歌开关称为变形金刚 SOTA，但他们肯定会在最佳 NLP 模型的列表中。尤其是，当这些模型“扩展到万亿个参数”时

接下来的两个部分是关于无监督学习和强化学习。对于这两者，很难命名 SOTA 模型，因为没有很多评论和比较(相对于上述子领域)。

## -无监督表示学习

无监督学习得到的关注比它应该得到的少得多。我坚信无标签训练机器学习模型的力量。老实说，我做过的最愉快的项目之一是无人监管的机器学习项目。虽然有强大的无监督经典机器学习算法，但我打算和这篇文章的基调保持一致，坚持深度学习。也很难找到关于无监督算法性能的评论，因为评估它们是一件痛苦的事情。

众所周知，自动编码器和生成对抗网络一直处于深度无监督学习的前沿。然而，我将更多地关注自动编码器，因为它们更符合“表示学习”的标准。

*   [**(矢量量化)**](https://blog.usejournal.com/understanding-vector-quantized-variational-autoencoders-vq-vae-323d710a888a?gi=2dfb384ac7eb) [**变分自动编码器**](https://towardsdatascience.com/intuitively-understanding-variational-autoencoders-1bfe67eb5daf)

可变自动编码器提供了对经典编码器/解码器架构的升级。他们的瓶颈分为两层，“均值”和“标准差”。这两层然后进入采样层，这就是事情变得有趣的地方。该采样层试图表示数据集的分布。此外，您可以从该采样层“生成”数据点，因为它应该对数据集的分布进行建模。

## **-强化学习**

我不是强化学习的专家，所以我不想解释这些模型，但如果你想了解更多，我会提供有用的资源。

*   **深度 Q 网络**

[](https://towardsdatascience.com/dqn-part-1-vanilla-deep-q-networks-6eb4a00febfb) [## 普通深度 Q 网络

### 深度 Q 学习解释

towardsdatascience.com](https://towardsdatascience.com/dqn-part-1-vanilla-deep-q-networks-6eb4a00febfb) 

*   **优势影评人**

[](https://towardsdatascience.com/understanding-actor-critic-methods-931b97b6df3f) [## 理解演员-评论家方法

### 预赛

towardsdatascience.com](https://towardsdatascience.com/understanding-actor-critic-methods-931b97b6df3f) 

## **最终想法**

希望你喜欢这篇文章，如果你开始一个新的项目，希望你知道从哪里开始寻找。如果你对我的选择有任何想法，请发表评论！

如果你想定期收到关于人工智能和机器学习的最新论文的评论，请在这里添加你的电子邮件并订阅！

[https://artisanal-motivator-8249.ck.page/5524b8f934](https://artisanal-motivator-8249.ck.page/5524b8f934)