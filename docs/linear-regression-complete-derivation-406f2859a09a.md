# 线性回归完全推导和数学解释！

> 原文：<https://pub.towardsai.net/linear-regression-complete-derivation-406f2859a09a?source=collection_archive---------0----------------------->

## 机器学习

## 线性回归中的 3/5 部分

第一部分:[从零开始线性回归](https://medium.com/@shuklapratik22/linear-regression-from-scratch-a3d21eff4e7c)。

第二部分:[通过暴力破解直线回归线](https://medium.com/@shuklapratik22/linear-regression-line-through-brute-force-1bb6d8514712)。

第三部分:[线性回归完全推导](https://medium.com/@shuklapratik22/linear-regression-complete-derivation-406f2859a09a)。

第四部分:[从零开始简单线性回归实现](https://medium.com/@shuklapratik22/simple-linear-regression-implementation-from-scratch-cb4a478c42bc)。

第 5 部分:[使用 Scikit-Learn](https://medium.com/@shuklapratik22/simple-linear-regression-implementation-2fa88cd03e67) 实现简单的线性回归。

在上一篇文章中，我们看到了如何使用暴力找到回归线。但对于我们通常以百万计的数据来说，这并不是很有成效。所以为了处理这样的数据集，我们使用 python 库，但是这样的库是建立在一些逻辑理论之上的，对吗？因此，让我们找出一些令人毛骨悚然的公式背后的逻辑。相信我，背后的数学更性感！

![](img/4ad95b5af6987599e4082f3094d44e15.png)

在我们开始之前，以下主题的知识可能会有所帮助！

*   偏导数
*   总和

## 找到最适合的线，你兴奋吗？

![](img/d8e556fec6cf8020bce209cccb4a0065.png)

让我们从定义一些东西开始

1)给定 n 个输入和输出。

![](img/be11f2c23603f6967f5279b5cf1c27ee.png)

2)我们将最佳拟合线定义为:

![](img/bbcda25a9f6890e33d5bce2f3e29c105.png)

3)现在我们需要最小化我们命名为 S 的误差函数

![](img/69d4ead9ef78984c645194ba0aa223ee.png)

4)将等式 2 的值代入等式 3。

![](img/5a6a349f5cc592fdcbdcf15d80cdd45f.png)

为了最小化我们的误差函数 S，我们必须找到 S 的一阶导数在哪里等于 0，关于 a 和 b，a 和 b 越接近 0，每个点的总误差越小。让我们先求出 a 的偏导数。

# 查找 a:

1)求 S 关于 a 的导数。

![](img/81b5c816e59591248c269251b54b2ec2.png)

2)使用链式法则，比方说

![](img/7fdcac24428dd7dabafeba3b47bcfc1f.png)

3)使用偏导数

![](img/b09287d006e1c7ae7f93a3f97f8b1b02.png)

4)扩展

![](img/ab5c41b0441d0e90f4b745ca93fd5c2e.png)

5)简化

![](img/381b79c08fa6777577944dafeb1fec35.png)

6)为了找到极值，我们把它置为零

![](img/985bb53f946149ba5da54b0d13565846.png)

7)用-2 除左边

![](img/a7fe3a78141e28813cad266c6ff792e5.png)

8)现在让我们将总和分成 3 部分

![](img/e2c8ba570f757fc9fd088a02f0151330.png)

9)现在 a 的总和是

![](img/cb061ecc730775a859830a66ecb952d7.png)

10)将其代入等式

![](img/2780dbaab2088aecb2bf22453a727da5.png)

11)现在我们需要求解一个

![](img/aaa02779301bc0fb5736b3715dd36d0d.png)

12)Y 和 x 的总和除以 n，就是它的平均值

![](img/79266684cda274e01a29d45af6aac8a7.png)

我们已经最小化了关于 x 的成本函数，现在让我们找到关于 b 的最后一部分。

# 调查结果 B:

1)与我们对 a 所做的相同

![](img/9750e711f0f311c50a571f671468ce04.png)

2)求偏导数

![](img/e005777e2523a00a1a5ad6c861defc07.png)

3)稍微扩展一下

![](img/d93142d6f0369dc9f8e72778b096c389.png)

4)将它放回等式中

![](img/dd9f47fd6c27e179f4cf8dc5a2d99c50.png)

5)让我们将两边除以-2

![](img/3e8365f4bce81daf399f3a224cae2f10.png)

6)为了便于查看，让我们分布 x

![](img/3e3af73acdb6016191bb138665497dff.png)

现在让我们做些有趣的事情吧！记住，我们在本文前面已经找到了。我们为什么不用它来代替呢？好吧，让我们看看会发生什么。

7)代入 a 的值

![](img/02d863ad275b3a6ad44561c86d815ffa.png)![](img/1d93e30de80e02d6f199ae818036abfc.png)

8)让我们分配负号和 x

![](img/7aac0b60e7f6da2145317d092b70f4aa.png)

你不喜欢吗？让我们把总数分成两笔

9)分割总和

![](img/155521cfb89fbd5880bece986c23db7a.png)

10)简化

![](img/9e4d4e74c8ee662323985c22ac458427.png)

11)从中找出 B

![](img/4463ad16175518a675b5f2d5425668a4.png)

太好了。我们做到了。我们以 x 和 y 的形式分离出了 a 和 b，这并不难，对吧？

我还有一些精力，想去探索一下！

12)简化公式

![](img/cc61c8b07a905fb14888f1e83be866cf.png)![](img/5117b2d4dfecbcea1024923261954943.png)

13)将等式 11 中的分子和分母乘以 n

![](img/74443e697fb8d9dd25eca9c434c5c094.png)

14)现在，如果我们使用等式 13 简化 a 的值，我们得到

![](img/37e909d054d7e38625207528d2e3686e.png)

## 摘要:)

如果你有一个有一个独立变量的数据集，那么你可以通过计算 b 找到最适合的线。

![](img/a4ef531bd5e21364a1f3ced698d1bb02.png)

然后将 B 代入 a

![](img/3d3b81fda9dcebf219741230521c6d0e.png)

最后将 B 和 a 代入最佳拟合线

![](img/61705bc65712a353b9419abeec463313.png)

# 向前看，

在下一篇文章中，我们将看到如何用 Python 从头开始实现简单的线性回归(没有 sklearn)。

请让我知道你是否喜欢这篇文章！我打赌你喜欢它。

要找到更多这样的详细解释，请访问我的博客:[**【patrickstar0110.blogspot.com】**](http://patrickstar0110.blogspot.com)

**(1)** [**简单线性回归用其导数**](https://youtu.be/1M2-Fq6wl4M) **解释。**

**(2)** [**如何从零开始计算线性回归中模型的精度**](https://youtu.be/bM3KmaghclY) **。**

**(3)** [**简单线性回归使用 Sklearn**](https://youtu.be/_VGjHF1X9oU) **。** 你可以在 [Google Drive](https://drive.google.com/open?id=1_stSoY4JaKjiSZqDdVyW8VupATdcVr67) 上下载推导的代码和一些手写笔记。

如果您有任何其他问题，请随时联系我:[shuklapratik22@gmail.com](mailto:shuklapratik22@gmail.com)。

![](img/d68105c04494298f4fd4526bc93f1cee.png)