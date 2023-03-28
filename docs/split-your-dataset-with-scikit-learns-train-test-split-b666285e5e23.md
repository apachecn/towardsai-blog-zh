# 使用 scikit-learn 的 train_test_split()拆分数据集

> 原文：<https://pub.towardsai.net/split-your-dataset-with-scikit-learns-train-test-split-b666285e5e23?source=collection_archive---------4----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

![](img/6650fe7268bc9114f161252f9ecf024c.png)

由[艾萨克·史密斯](https://unsplash.com/@isaacmsmith?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

模型评估和验证是监督机器学习的重要组成部分。它有助于选择最佳模型来表示我们的数据，以及预测该模型在未来的表现如何。

为了预测这个模型，我们需要将这个模型数据集分成训练和测试数据。手动拆分这些数据非常困难，因为数据集的大小很大，并且需要对数据进行混洗。

为了使这项任务更容易，我们将使用 Scikit-learn 的 train_test_split()模块，该模块将我们的数据分成训练集和测试集。

# Scikit-Learn 的安装

![](img/11c0ee47cc72a713eaed9aa167c0b6a1.png)

沃洛季米尔·赫里先科在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

**安装 Scikit-使用 pip 学习:**

```
$ pip install -U scikit-learn
```

**安装 sci kit-使用 conda 学习:**

```
$ conda install -c anaconda scikit-learn=0.24
```

# 正在导入库—

```
>>> from **sklearn.model_selection** import **train_test_split**
```

# 开始——

![](img/3866687616f665f1f15c139d6fe15659.png)

照片由[戴恩·托普金](https://unsplash.com/@dtopkin1?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

## 语法-

```
*train_test_split(*arrays, test_size=None, train_size=None, random_state=None, shuffle=True, stratify=None)*
```

## **参数-**

![](img/7fa11adff549abf556cfc5ad6e0e445b.png)

Artem Sapegin 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

**数组**——你想要分割的数据保存在一系列列表、NumPy 数组、pandas 数据帧或其他类似数组的对象中，这些对象称为数组。数据集由所有这些对象组成，它们的长度必须相同。

**train_size -** 训练数据集的大小由该选项决定。无，这是默认值。需要精确样本数的 Int 和从 0.1 到 1.0 的 float 是三种选择。

**test_size -** 该参数指定测试数据集的大小。如果训练尺寸被设置为默认值，则**测试尺寸**将被设置为 **0.25** 。

**random_state -** 该参数使用`np.random`或 int 指定数据的随机分割。

**shuffle -** Shuffle 有布尔值(*默认=真*)。这决定了数据是否应该被打乱。

**分层-** 是一个类似数组的对象(*默认=无*)。如果分层不是任何，那么它确定如何使用分层数据分割。

现在是时候测试您的数据分割技能了！首先，您需要创建一个简单的数据集来使用。输入将位于二维数组 **X** 中，而输出将位于数据集中的一维数组 **y** 中。

我们使用 NumPy 库来生成数据集。arange()将返回指定间隔内的等间距值。shape()将改变数组的形状而不改变其数据。

[](https://medium.com/@yashpnagare/a-complete-guide-on-numpy-for-machine-learning-fd4ec1f168b7) [## 机器学习的 NumPy 完全指南

### 什么是 NumPy？如何安装 NumPy？Numpy 线性代数

medium.com](https://medium.com/@yashpnagare/a-complete-guide-on-numpy-for-machine-learning-fd4ec1f168b7) 

通过一次函数调用，您可以分割输入和输出数据集。

train_test_split()执行数据拆分，并按以下顺序返回 NumPy 数组的四个序列:

1.  X _ train-X 序列的训练部分
2.  y _ train-y 序列的训练部分
3.  X _ test-X 序列的测试部分
4.  y _ test-y 序列的测试部分

```
**>>>** train_test_split(y, shuffle=True)
[[4, 0, 6, 2, 5, 9, 3], [1, 7, 8]]
**>>>**
```

数据集的样本被随机打乱，然后将数据分成训练集和测试集。

![](img/13685c859ec54fb541be86ed76de6755.png)

照片由 [Alex](https://unsplash.com/@alx_andru?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

# 结论

现在您已经了解了为什么以及如何使用 sklearn 的 train_test_split()函数以及其中使用的各种参数。现在，您可以使用您的数据来训练、验证和测试任意数量的机器学习模型。

# 在你走之前

我欢迎你加入我的旅程！关注此[媒体](https://medium.com/@yashpnagare)页面，了解更多令人兴奋的数据科学/Python 内容。