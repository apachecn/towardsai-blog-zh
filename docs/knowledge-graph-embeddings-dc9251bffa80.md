# 知识图嵌入

> 原文：<https://pub.towardsai.net/knowledge-graph-embeddings-dc9251bffa80?source=collection_archive---------0----------------------->

![](img/e749a58cfe4534e584b375687a4fd1f0.png)

由 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的 [chuttersnap](https://unsplash.com/@chuttersnap?utm_source=medium&utm_medium=referral) 拍摄

在之前的故事中，我们介绍了[图嵌入简介](https://medium.com/towards-artificial-intelligence/a-gentle-introduction-to-graph-embeddings-c7b3d1db0fa8)，[节点嵌入中的随机游走](https://medium.com/towards-artificial-intelligence/random-walk-in-node-embeddings-deepwalk-node2vec-line-and-graphsage-ca23df60e493)， [4 图神经网络](https://medium.com/towards-artificial-intelligence/4-graph-neural-networks-you-need-to-know-wlg-gcn-gat-gin-1bf10d29d836)，以及当 GraphSAGE 遇到 Pinterest。

在本文中，我介绍了 TRESCAL、HolE 和 SimplE 在知识图嵌入中的应用。TRESCAL 和 HolE 都是 RESCAL 的增强版本。作者使用了不同的方法来克服重新标度的局限性。

# 特雷斯卡

TRESCAL (Chang 等人，2014 年)是 RESCAL(Nickle 等人，2011 年)的增强版。作者考虑了实体的类型和关系，以消除不必要的计算，从而减少所需的训练时间，并提高模型精度。这是零钱:

*   **领域知识**:比如我们可以确认，如果 R(关系)是“天生的”，而 E1(头部实体)和 E2(尾部实体)是一个人，则{E1，R，E2}无效。通过去除不相容的实体关系三元组，不仅减少了训练时间，而且改善了模型误差。
*   **正则化**:通过应用奇异值分解(SVD)，降低了计算复杂度。

# 孔

[HolE](https://arxiv.org/pdf/1510.04935.pdf) (Nickel et al .，2015)，又名全息嵌入，结合 RESCAL(Nickle et al .，2011)和 DistMult(Yang et al .，2015)，以更少的计算资源实现更好的结果。为了表示关系，RESCAL 需要 D 的平方(维度的大小)，而 HolE 只需要 D。另一方面，它利用循环相关性来计算关系，使得它可以支持非对称关系(即，有向图)。

# 简单的

[简单的](https://arxiv.org/pdf/1802.04868.pdf)(卡泽米和普尔，2018)，又名`Simple Embedding`，提出使用两个关系向量来学习实体嵌入。在链接预测中，我们总是有一个三元组(头实体、关系和尾实体)来训练模型。所以有四个实体嵌入(2 头 2 尾)和一个关系嵌入。问题是，在不同的情况下，有两个嵌入来表示单个实体(分别是头部和尾部)。最终造成了业绩不佳。

作者建议使用两个关系嵌入而不是一个，这样它可以解决上述问题。将评分函数定义为:

> 1/2(实体 _ 1 _ 头*相关 _a *实体 _ 2 _ 尾+实体 _ 1 _ 尾*相关 _b *实体 _ 2 _ 头)

换句话说，它同时计算头部和尾部实体嵌入。

# 延伸阅读

*   [洞](https://github.com/mnick/holographic-embeddings)储存库
*   [简单的](https://github.com/Mehran-k/SimplE)储存库

# 参考

*   K.张文伟、易文泰、杨炳良、米克良。[用于关系抽取的知识库的类型张量分解。](https://pdfs.semanticscholar.org/2a5d/9bfc8b1eb7cc19b611b17b81d6ce97f056ca.pdf) 2014 年
*   米（meter 的缩写））尼克尔、l .罗萨斯科和 t .波吉奥。[知识图的全息嵌入](https://arxiv.org/pdf/1510.04935.pdf)。2015
*   南卡泽米先生和普尔先生。[知识图中链接预测的简单嵌入](https://arxiv.org/pdf/1802.04868.pdf)。2018