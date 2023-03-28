# 图像强度处理

> 原文：<https://pub.towardsai.net/image-intensity-manipulation-27c126a72d06?source=collection_archive---------2----------------------->

## [计算机视觉](https://towardsai.net/p/category/computer-vision)

![](img/8d86a6b87e73759f8f2c316f3f1479ef.png)

照片由[乔纳森·鲍尔斯](https://unsplash.com/@jbowersphotography?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/dark-image?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄

# 什么算强度操纵

*   任何通道中像素值的显式更改。
*   对图像的数学运算。
*   亮度变化。
*   对比度变化。
*   伽玛操控。
*   直方图均衡
*   高级操作-过滤、增强等。

> 使用 OpenCV 加载图像

```
import numpy as np
import cv2
from matplotlib import pyplot as plt
img = cv2.imread(folder_path + "imgs/chapter3/man.jpg", 0);
plt.imshow(img, cmap = "gray");
plt.show()
```

![](img/52916020d46bf7890666d70c94e2fbf1.png)

> 使用 Opencv 向输入图像添加常数值

```
img = cv2.imread(folder_path + "imgs/chapter3/man.jpg", 0);##########################FOCUS############################
img = cv2.add(img, 120);
###########################################################plt.imshow(img, cmap = "gray");
plt.show()
```

![](img/71004134b208435bd3bfa480841b1486.png)

> 使用 Opencv 从输入图像中减去一个常数值

```
img = cv2.imread(folder_path + "imgs/chapter3/man.jpg", 0);##########################FOCUS############################
img = cv2.subtract(img, 120);
####################################################################plt.imshow(img, cmap = "gray");
plt.show()
```

![](img/0a9903f8c9bf67a3c2bed31f631265e7.png)

# 从图像中平均减去

> 方法 1

*   将图像分割成通道。
*   对于每个通道，计算其平均值。
*   从该通道的每个像素中减去该平均值

> 方法 2(用于深度学习)

*   将所有图像拆分到各自的通道中

> 对于所有图像的每个通道。

*   找出每个图像通道的含义。
*   求所有计算平均值的平均值。

> 应用程序

*   批处理规范化的一部分。

![](img/0a0313b4c442518a6b69c3306e6269df.png)

# 负面形象

> 灰度负片

![](img/7eeced90f38ae40dbe8bddb9abe312ac.png)

> RGB 图像的负片

![](img/fe619311ff2d2782f30900a67f918f25.png)

# 添加两幅图像

> 直接添加

![](img/38b1d12d55886c802cc3ec777a874d91.png)

> 加权加法

![](img/300e194c384036e47a1b9a0cfcd07e4e.png)

# 减去两幅图像

![](img/9e1ccd8a1ea4235b9517c5808a591517.png)

# 聪明

*   发出或反射光的性质或状态。
*   亮度是一个相对的术语。这取决于你的视觉感知。
*   亮度可以定义为一个光源相对于我们与之比较的光源所输出的能量。

![](img/ad49fef6656a5a2a586566b66024a7e2.png)

# 对比

*   对比度是使对象(或其在图像或显示器中的表示)可区分的亮度或颜色的差异。
*   可视化为图像中最大和最小像素强度之间的差异。
*   对比度是由同一视野内物体的颜色和亮度差异决定的。

> 操纵图像中的对比度

![](img/40b6b7bf354b73471fe44df243bbfaac.png)![](img/edf4a420051cb49ac9d4b138ad8e2fa2.png)

# 微克

*   伽马校正，或通常简称为伽马，是用于编码和解码亮度的非线性操作。
*   所有彩色和灰度数字图像文件都包含伽玛数据。
*   Gamma 是关于数字敏感度和人眼敏感度之间的转换，一方面提供了许多优势，但另一方面增加了复杂性。
*   伽玛优化了中间色调的对比度和亮度。

> 使用 Opencv 操作 gamma

![](img/6b7783bf83837882aeaadc530a15e305.png)![](img/096dee25e0e688ce87f029e2b9ac7a5f.png)

# 直方图均衡

> 柱状图

*   直方图是一种图表。显示任何事物频率的图表。
*   图像像素直方图表示具有特定强度值的像素的频率。

![](img/fb243d7be552d63a503eed4b30f6d558.png)

> 直方图均衡

*   直方图均衡化用于增强对比度。
*   这种方法增加了图像的整体对比度。

![](img/0afea5e71d50f545ff338c83c314c7c4.png)

> 使用 Numpy 的直方图可视化

![](img/449ab727664b3e364688df29a1d4fef3.png)

> 使用 OpenCV 进行直方图均衡

![](img/c204bd44c3502a44d5295ac2fd210a19.png)

你可以在这里找到完整的 jupyter 笔记本。

如果你有任何问题，你可以联系[阿布舍克](https://www.linkedin.com/in/abhishek-kumar-annamraju/)。请随意联系他。

我对计算机视觉和深度学习充满热情。我是[和尚](https://github.com/Tessellate-Imaging/Monk_Object_Detection)图书馆的开源贡献者。

你也可以在以下网址看到我的其他作品:

[](https://medium.com/@akulahemanth) [## 阿库拉·赫曼思·库马尔培养基

### 约翰·沃尔夫冈的《色彩理论》一书中的色彩模型。证明为什么 RYB 被认为是主要的…

medium.com](https://medium.com/@akulahemanth)