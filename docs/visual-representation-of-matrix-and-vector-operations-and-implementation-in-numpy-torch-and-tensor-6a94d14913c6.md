# 矩阵和向量运算的可视化表示以及在 NumPy、Torch 和 TensorFlow 中的实现。

> 原文：<https://pub.towardsai.net/visual-representation-of-matrix-and-vector-operations-and-implementation-in-numpy-torch-and-tensor-6a94d14913c6?source=collection_archive---------1----------------------->

## [深度学习](https://towardsai.net/p/category/machine-learning/deep-learning)

在深度学习的基本单元上实现从初级到高级的操作。

![](img/c2b5fbace7483921e7dcd11ced48506c.png)

摘录

我习惯于为不同的问题创建新的深度学习架构，但选择哪个框架( **Keras，Pytorch，TensorFlow** )往往更难。

由于其中存在不确定性，所以了解这些框架的基本单元(NumPy、Torch、Tensor)的基本操作是有好处的。

在这篇文章中，我已经在 3 个框架中执行了一些相同的操作，也尝试了大部分框架的可视化。

这是一个适合初学者的帖子，让我们开始吧。

# 1.装置

# 2.版本检查

# 3.数组初始化~一维、二维、三维

## 标量和一维数组

![](img/7f3d231ac4112e31ed2b2b5ac21b262d.png)

标量、一维、二维数组

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

## 二维向量阵列

![](img/1bb1188cf0f18aa45070922c251e985a.png)

二维数组

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 4.生成数据

![](img/35ccb2bfb4a7157d15e57a0d4fa070ba.png)

零和一

![](img/edea6d043b78dac30c7332cf9626eb8c.png)

对角线和相同元素填充

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

## 从正态分布中抽取随机样本

![](img/a0bda3728d8b5f8d7d48c8e1d92f7d84.png)

正态分布钟形曲线

![](img/bbee116c997fb6a4c60cbbb7a3705c85.png)

样本取自正常区

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

## 从均匀分布中抽取样本

![](img/fc9b7564b73e1f95ad36eb26b4a1205d.png)

均匀分布曲线

![](img/70e18dce1717e352addb3ea3156b896f.png)

样品取自制服区

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 6.向量排列

![](img/5130277d91c75676ea8abb94054ccd6e.png)

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 7.数据类型—转换

uint 8/16/32/64←→float 8/16/32/64

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 8.数学运算

![](img/55dc5ec795270013f427475e58a83dae.png)![](img/57d687a55cba84edd65b600a36af875c.png)

加法和减法运算

![](img/d3ec75f7734d6ce0a6b20d037361769a.png)![](img/5efd4cd592701375746f5de9ea84006b.png)

乘法和除法运算

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 9.点积

![](img/c6b00c0acaf74988c674676f1e20351b.png)

点积

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 10.矩阵乘法

![](img/5bc8fd1a0e76f1634aa5ad982ee910ce.png)

矩阵乘法

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 11.索引和切片(二维)

![](img/8c1fa9f4ffe73edc7727c91d57658ad0.png)

索引和切片

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 12.索引和切片(二维矩阵)

![](img/aaa08229811a2cb0748c716ada69e2a2.png)

矩阵切片

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 13.重塑和转置轴

![](img/d7f0222bdc170c5a662ff9b6a4ec0c6c.png)

重塑和移调

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 14.串联

![](img/2c4dabe1ed8ab9c22987a29ead1bbb80.png)

矩阵串联

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 15.跨轴求和

![](img/454394686ce3c987db5a1399af958bda.png)

坐标轴—总和

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 16.跨轴平均值

![](img/73d32d60f125802b4563e998cb6883c1.png)

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 17.尺寸扩展和移动轴。

![](img/32ba1d20997b4a8c468e6f775fdfa7c9.png)

串联和移动轴

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 18.Max (Min)和 Argmax:

![](img/28489b494f234a203eeb849dbdf82bef.png)![](img/99882199415c223b709b986d8242e948.png)![](img/c095ef9e8b458a6fdd561778c400ca40.png)

轴的最大值=0

![](img/edf7bf4ee53bca2e09d56d9401e35d10.png)

轴的最大值=1

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

# 19.切片和索引(三维矩阵)

![](img/474b3969ae06008711686155166927b3.png)![](img/d2195e30fc9d2a13cc644a2a15f486a4.png)

3x3 矩阵及其指数

![](img/359d610a6d6b28e137da7b79b66fe119.png)![](img/a1147265549d9dfa6a0b2f4f79690465.png)

左上和右下

![](img/ffbab2cb1af51aa25e420f2b2582495f.png)![](img/5190f7bc7023ceea302e8b6115164c5b.png)

中间元素&逆中间元素

## Numpy 实现:

## TensorFlow 实现:

## 火炬实施:

由于可视化的限制，我跳过了高维度部分的操作。

我希望我能够对一些基本操作以及您选择的深度学习框架提供一些视觉理解，我将很快添加更多详细的操作。

在 Google Colab 这里查看笔记本→ [***Colab***](https://colab.research.google.com/github/bala-codes/Numpy-Tensor-Torch-Operations-Visualized/blob/master/codes/Numpy_Tensor_Torch_Operations_Visualized.ipynb) 。

(或)

在 Kaggle 这里查看笔记本→[***Kaggle***](https://www.kaggle.com/balakrishcodes/visual-representation-of-matrix-vector-operation)

在那之前，下次见。

**文章作者:**

**BALAKRISHNAKUMAR V**