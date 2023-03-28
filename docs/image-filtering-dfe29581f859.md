# 滤像

> 原文：<https://pub.towardsai.net/image-filtering-dfe29581f859?source=collection_archive---------0----------------------->

## 使用 Monk，低代码深度学习工具和计算机视觉的统一包装器，使计算机视觉变得简单。

在本文中，我们将使用 going 来探索图像过滤。我们将把重点放在编码上。

有很多关于图像过滤的介绍，在媒体和其他出版物上都有，所以我不会浪费任何时间来复习基础知识。如果你不知道什么是图像过滤，一个很好的入门方法是查看 OpenCV 教程。

> ***完成过滤来完成各种目标***

*   提取重要信息。
*   移除噪音或不需要的元素。
*   提升形象。
*   给一个确定的眼神

![](img/715653f8bfdc1caaf50edddaba157115.png)

> ***图像滤波的应用***

1.  去噪
2.  超分辨率
3.  画内

![](img/0d9e6cf788fcd34d44715b56f3be4c8c.png)

# 图像模糊

> ***模糊操作***

![](img/0eb9efb646dfb485f8a60e551d46ab3c.png)

> ***实现方框模糊***

![](img/9b22fecd0e574e6e690a070969336a17.png)

原象

![](img/e1b1023369bb5e067c39db94145ff37c.png)

归一化模糊图像

![](img/4d36bd0a2c5b910412fb415ed05b898b.png)

未归一化的模糊图像

> 使用滤波器消除噪声

**椒盐噪声**

![](img/97f0486d715b3a0c53c4549c28d0f4f7.png)

# 卷积核

> ***实现卷积内核***

![](img/c26e8f1519b314b88dbaccbcb7f339e5.png)

原象

![](img/68e9a52cf8f096768cb074a7d83ecd3d.png)

过滤图像

> ***使用另一个 3*3 内核***

![](img/31d0fededfa846e1087b7d8910fdb6d3.png)

> ***使用另一个 3*3 内核***

![](img/58019ea23905c321b7398be839fef37d.png)

> 高斯核

> ***使用 OpenCV 内核的 3x3 高斯模糊***

![](img/70f25a29acf6c6bfdce69d5017d166ad.png)

> ***5x5 高斯模糊使用 OpenCV 内核***

![](img/b07344f1c217dd2e93e564d681365111.png)

> 模糊过滤

> ***5x5 模糊使用 OpenCV 内核***

![](img/3bf5b9ff48fb78b2aa2023622755da53.png)

> 锐化内核

> ***使用 OpenCV*** 锐化内核

![](img/a374aa6d17ac991177d65180c28130b3.png)

> ***图像锐化使用 OpenCV 与另一个 3*3 内核***

![](img/45b893ecb1819f5a42b296a003263f0c.png)

> ***使用枕头进行图像锐化操作***

![](img/72e11e563f05c6747fadf3cce4ec3b23.png)

> 索贝尔过滤器

> ***实现一个索贝尔滤镜***

![](img/aa9492cc2fea9b46197bed0a9b53cbf4.png)

> 沙尔滤波器

> ***实现一个沙尔滤波器***

![](img/e257c959c7c8d5f79ba0d503963d0f1e.png)

> 预维茨滤波器

> ***实现预维特滤镜***

**y 方向的 Prewitt 滤波器**

![](img/a702ad90d2b3193893cc68251bf4a916.png)

**X 方向的 Prewitt 滤波器**

![](img/e0fe6c7e1a663991e822a6e6a6432338.png)

> 伽柏滤波器

*   在图像处理中，一种以丹尼斯·加博尔命名的伽柏滤波器。
*   这是一个用于纹理分析的线性过滤器。

> ***实现一个 gabor 滤波器***

![](img/34cf90b6c22d2da4e985871e2337d197.png)

> 海森过滤器

*   海森矩阵给出了图像的二阶偏导数。
*   Hessian 滤波器用于 SIFT 特征。

> ***实现黑森滤波器***

![](img/60534956a51b1b9b74f1165d03924433.png)

> 拉普拉斯滤波器

*   拉普拉斯滤波器是导数滤波器，用于寻找图像中快速变化的区域(边缘)。

> ***实现一个拉普拉斯滤波器***

![](img/f2690bcd8a461821f78783315f74a9ed.png)

# 图像阈值处理

> ***什么是阈值处理？***

*   阈值化是从给定图像的背景中分割对象的一种简单方法。
*   它从灰度图像创建二进制图像。

> ***实现简单的阈值处理***

![](img/f436557bcb8a2ef1947c05d58471d1ec.png)![](img/343b6cfa734125e3bef225dae69c5320.png)![](img/6c3fbfcb52ad2ac64681ce5bcd7c857b.png)

> 自适应阈值

*   自适应阈值处理是一种阈值处理方法，其中为图像中较小的不同区域计算阈值。

> ***实现自适应阈值***

![](img/8a1b713abdbb630e3b3ac0720eb17c03.png)![](img/e72573b19915d09950176adca9d85c3f.png)

> ***复杂图像上的自适应阈值处理——自适应阈值处理的适用范围***

![](img/e230cdbbf2ce8518347cb81311b55f21.png)![](img/5efbeff8079b564504a8a10732893f6a.png)![](img/f9250329f0a799a9d35acee119552ada.png)

> ***复杂图像上的自适应阈值处理——简单阈值处理的工作原理***

![](img/7daf63c0d4df5be41c74f4c84fdb29b0.png)![](img/c5d41f9d0fafcfae191abcae286dfe24.png)

> 大津二值化

适用于双峰图像。直方图中有两个峰值的图像。

![](img/453323fae88194b44923630123772ccd.png)

参考:[维基百科](https://en.wikipedia.org/wiki/Otsu%27s_method#/media/File:Otsu's_Method_Visualization.gif)

> ***实现 Otsu 的二值化***

![](img/c04af16ba29ad2494d89b018694ac469.png)![](img/1504329ffce47da5df0c44aa46ac869f.png)

# 形态学运算

> 侵蚀

*   边界附近的像素将根据内核大小被移除。

> ***执行侵蚀操作***

![](img/b9927699d9001f2b7cee5753b4f365f6.png)

> 开始

*   开放是侵蚀，随后是扩张。它是用来消除噪音的。

> ***使用 opencv*** 打开变形

![](img/2a6b12fe412288730909764210ed21b8.png)

> 关闭

关闭是开放的反义词，扩张之后是侵蚀。

> ***使用 opencv*** 进行形态关闭操作

![](img/927a76efb7ac2d12f94a201a062ebf0d.png)

# Canny 边缘检测

Canny 边缘检测有 5 个不同的步骤:

1.  应用高斯过滤器
2.  找到图像的强度梯度
3.  非最大抑制
4.  双阈值
5.  通过滞后跟踪边缘。

> ***利用 opencv*** 实现 Canny 边缘检测器

![](img/a317d9673c193e4e25285f02432901b6.png)

你可以在 Github 上找到完整的 jupyter 笔记本。如果你喜欢蒙克，给我们 GitHub 回购⭐️。

如有疑问，可联系[阿布舍克](https://www.linkedin.com/in/abhishek-kumar-annamraju/)和[阿卡什](https://www.linkedin.com/in/akashdeepsingh01/)。请随意联系他们。

我对计算机视觉和深度学习充满热情。我是 [Monk](https://github.com/Tessellate-Imaging/Monk_Object_Detection) 库的开源贡献者。

你也可以在以下网址看到我的其他作品:

[](https://medium.com/@akulahemanth) [## 阿库拉·赫曼思·库马尔培养基

### 阅读阿库拉·赫曼思·库马尔在媒介上的作品。计算机视觉爱好者。每天，阿库拉·赫曼思·库马尔和…

medium.com](https://medium.com/@akulahemanth) ![](img/c96ee5cc1232092261fb5f7d84b0ce99.png)

照片由[斯里莱卡](https://www.instagram.com/_fernwehd_._/?hl=en)拍摄