# 带有 Resnet、Densenet、Inception 模块的自定义网络

> 原文：<https://pub.towardsai.net/custom-network-with-resnet-densenet-inception-blocks-c32fc595085d?source=collection_archive---------1----------------------->

## 使用 Monk，低代码深度学习工具和计算机视觉的统一包装器，使计算机视觉变得简单。

有没有想过尝试用 Resnet、Densenet、Inception 等不同的块来搭建一个网络？

我假设你已经熟悉计算机视觉的基础知识。在深入研究之前，确保你知道什么是 Resnet，什么是 Densenet，什么是 Inception。

> 我们开始吧

# 目录

1.  **安装**
2.  **加载数据**
3.  **创建并调试网络**
4.  **列车**

# **安装**

安装 Monk，一个低代码深度学习工具，也是计算机视觉的统一包装器。

```
$git clone [https://github.com/Tessellate-Imaging/monk_v1.git](https://github.com/Tessellate-Imaging/monk_v1.git)#Select the requirements file as per OS and CUDA version$cd monk_v1/installation/Linux && pip install -r requirements_cu9.txt
```

# **加载数据**

这里我们使用的是[斯坦福狗分类数据集](https://www.kaggle.com/jessicali9530/stanford-dogs-dataset)。

```
$! wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1b4tC_Pl1O80of7U-PJ7VExmszzSX3ZEM' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/**\1\n**/p')&id=1b4tC_Pl1O80of7U-PJ7VExmszzSX3ZEM" -O dogs-species-dataset.zip && rm -rf /tmp/cookies.txt
```

# **创建并调试网络**

这里我们创建一个网络，并追加 resnet_v1_block 和 resnet_v2_block。

**调试定制模型**

```
$ gtf.debug_custom_model_design(network);
```

![](img/40ba2ea6c383335e73d59f7375e5f539.png)

从下往上看

接下来，我们将追加 resnet _ v1 _ 瓶颈 _ 块和 resnet _ v2 _ 瓶颈 _ 块

**调试定制模型**

```
$ gtf.debug_custom_model_design(network);
```

![](img/4553ecd872c9f09550565d6eef1c78ea.png)

从下往上看

这里我们将追加 densenet_block，inception_a_block 和 inception_c_block。

**调试定制模型**

```
$ gtf.debug_custom_model_design(network);
```

![](img/f276080065ba9ff75ac03e88fa9d54bc.png)

从下往上看

我们展平，添加一个完全连接的层，然后是一个完全连接的层，其中神经元(单元)的数量=自定义数据集中的类的数量。

**调试定制模型**

```
$ gtf.debug_custom_model_design(network);
```

![](img/7beab85c37b99c6d469b3a5366bab895.png)

从下往上看

# 用 Netron 可视化

![](img/02205cdfba57c38044faf66a1f6cedaa.png)

# **列车**

*设置时期、优化器、损耗和学习率调度程序。*

你可以在 [Github](https://github.com/Tessellate-Imaging/monk_v1/blob/master/study_roadmaps/1_getting_started_roadmap/9_custom_network_builder/3)%20Create%20a%20custom%20network%20with%20blocks%20while%20debugging%20it-Copy1.ipynb) 上找到完整的 jupyter 笔记本。

如有疑问，可联系[阿布舍克](https://www.linkedin.com/in/abhishek-kumar-annamraju/)和[阿卡什](https://www.linkedin.com/in/akashdeepsingh01/)。请随意联系他们。

我对计算机视觉和深度学习充满热情。我是 [Monk](https://github.com/Tessellate-Imaging/Monk_Object_Detection) 库的开源贡献者。

你也可以在以下网址看到我的其他作品:

[](https://medium.com/@akulahemanth) [## 阿库拉·赫曼思·库马尔培养基

### 阅读阿库拉·赫曼思·库马尔在媒介上的作品。计算机视觉爱好者。每天，阿库拉·赫曼思·库马尔和…

medium.com](https://medium.com/@akulahemanth) ![](img/4c37da5168beeeff28953982b4788120.png)

照片由[赫克托隼](https://unsplash.com/@hectorfalcon?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/t/architecture?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄