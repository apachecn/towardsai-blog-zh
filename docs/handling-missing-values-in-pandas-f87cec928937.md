# 处理熊猫中缺失的值

> 原文：<https://pub.towardsai.net/handling-missing-values-in-pandas-f87cec928937?source=collection_archive---------0----------------------->

![](img/7c3efc98eea5932cb3ba10d08d3dab3b.png)

图片由作者| **除非另有说明，所有图片均来自作者。**

## [数据科学](https://towardsai.net/p/category/data-science)，[编辑](https://towardsai.net/p/category/editorial)，[编程](https://towardsai.net/p/category/programming)

## 一个关于如何检测和处理熊猫丢失数据的实践视频教程

**作者:** [普拉蒂克·舒克拉](https://www.linkedin.com/in/pratik-shukla28/)，[罗伯特·伊里翁多](https://mktg.best/vguzs)

[](https://members.towardsai.net/) [## 加入我们吧↓ |面向人工智能成员|数据驱动的社区

### 加入人工智能，成为会员，你将不仅支持人工智能，但你将有机会…

members.towardsai.net](https://members.towardsai.net/) 

任何数据科学项目中最关键和最耗时的部分是数据清理和准备。幸运的是，有许多强大的工具可以帮助我们加快这个过程。

pandas 库是 python 中广泛使用的数据分析库之一。在使用我们的模型对我们的数据执行数据分析之前，找到任何可能影响我们输出的缺失值是至关重要的。

**当接受调查的用户不共享他们的数据时，就会出现数据缺失**。本教程将深入探讨一些方法，这些方法将帮助我们在 pandas 的帮助下识别和删除这些丢失的数据。

本教程的配套资料可以在我们的 [**资源部分**](#62a4) 中找到。

## 目录:

1.  [pd.isna()](#bc93)
2.  [pd.notna()](#f659)
3.  [pd.isnull()](#092d)
4.  [pd.notnull()](#092d)
5.  [pd.dropna()](#613c)
6.  [pd.fillna()](#65aa)
7.  [pd.bfill()](#329d)
8.  [pd .回填()](#7cda)
9.  [pd.ffill()](#1352)
10.  [pd.pad()](#4ebe)
11.  [结束语](#b758)
12.  [资源](#62a4)
13.  [参考文献](#62a4)

# pd.isna():

我们使用 pandas 库的`pd.isna()`函数来检测一个类似数组的对象的缺失值。我们先来看看`pd.isna()`的语法，用例子来理解。

![](img/de62535f4c238a85febf0ae1bf136646.png)

pandas.isna()函数的语法和参数说明

在我们继续理解`pd.isna()`函数如何工作之前，让我们先导入一些必需的库。

![](img/54ad9ebaf0c5bf28194edbd245efa853.png)

导入所需的库

## A.示例 1:

![](img/9caa187181023949dcf82e8a376911ab.png)

标量参数(数字)

## B.示例 2:

![](img/bf637370a7cdace1455ecd2b7375e987.png)

标量参数(字符串)

## C.示例 3:

请注意，空字符串不被视为 NA 值。这就是为什么`pd.isna(“ ”)`的输出会是假的。

![](img/f8d1a167e7b0a378988dafccd0a3d6b1.png)

空字符串

## D.示例 4:

![](img/a225525658c636ccf8dec32bf60cb0f6.png)

NaN —不是一个数字

## E.示例— 5:

![](img/55c065beb139c6c73ca801f6aa0be4f6.png)

inf —无穷大

## F.示例— 6:

![](img/8f54a635560a4d73011ebd61363c5dad.png)

没有人

## G.示例— 7:

![](img/5e1894c0a5455dccd6919f8ddb607385.png)

不适用—不可用

## H.示例— 8:

![](img/299f58aedc9ad088e75d6716af886510.png)

NaT —不是时间戳

## n 维数组:

## 一.示例— 9:

![](img/5dc3a709b7c8abda1f24e8bacfc1b223.png)

一维数组

## J.示例— 10:

![](img/3bc24692ac856034b3d09bbb6deeab83.png)

二维数组

## 索引值:

## K.示例— 11:

![](img/418db8622b6ce4c55cd034524c151728.png)

索引值(一维)

## 长度示例— 11:

![](img/8afb331c1e6bd10d9cbb6d57468bed29.png)

时间戳值(一维)

## 熊猫系列:

## 米（meter 的缩写））示例— 13:

![](img/a87728b98a494e2adf17544539e34701.png)

熊猫系列

## 熊猫数据帧:

## 名词（noun 的缩写）示例— 14:

![](img/e281221d92514ffa9138094aad4256cf.png)

熊猫数据框

# pd.notna():

pandas 库的`pd.notna()`函数用于检测一个类似数组的对象的非缺失值或有效值。请注意`pd.notna()`是熊猫库`pd.isna()`函数的布尔逆。我们先来看看`pd.isna()`的语法，用例子来理解。

![](img/28bd64eac2a49c8387ebf82cc5cbc86f.png)

pandas.notna()函数的语法和参数说明

在我们继续理解`pd.isna()`函数如何工作之前，让我们首先导入一些必需的库。

![](img/0710f4c4f76c0a3c322bc28c95ec03f2.png)

导入所需的库

## A.示例 1:

![](img/7fbe6f5c40c6065a130e1408067ad957.png)

标量参数(数字)

## B.示例 2:

![](img/2def0ab8799abc65beb907aff837809e.png)

标量参数(字符串)

## C.示例 3:

![](img/068e8cbf2501e6c894d70b83c2ff4d7e.png)

空字符串

## D.示例 4:

![](img/1aa6a4e19aa0d7a2700c3be199a9d64d.png)

inf —无穷大

## E.示例— 5:

![](img/319acb8ff16d4783872f697ae81afddb.png)

NaN —不是一个数字

## F.示例— 6:

![](img/52df7a0f0c27c8bb64a1066aeed5301f.png)

没有人

## G.示例— 7:

![](img/f933bda59768386d42f8300c7a27a014.png)

不适用—不可用

## H.示例— 8:

![](img/2b325a750930641d11fd1ffd2be9928c.png)

NaT —不是时间戳

## 一.示例— 9:

![](img/53ec303ee5b2813c6fed10e9bae5f241.png)

一维数组

## J.示例— 10:

![](img/74cc459889eb240128f8e8524b847634.png)

二维数组

## K.示例— 11:

![](img/34bdc534fea5ddf2aa9742bd29723495.png)

索引值

## 长度示例— 12:

![](img/8187b1a03d147fcb58e9b73480d2f3a0.png)

时间戳值

## 米（meter 的缩写））示例— 13:

![](img/2f439b5b63c1c33df8d86c7d65682c09.png)

熊猫系列

## 名词（noun 的缩写）示例— 14:

![](img/b581e3a2f57c120b148016dc5d2f7552.png)

熊猫数据框

# 重要提示:

1.  `pd.isnull()`函数是`pd.isna()`函数的别名。它会给我们完全相同的结果。建议使用`pd.isna()`功能，而不是`pd.isnull()`功能。

![](img/9c7d3311c1062829bdcf1799b821d452.png)

pd.isnull()函数

2.`pd.notnull()`函数是`pdnotna()`函数的别名。它会给我们同样的结果。建议使用`pd.notna()` 功能，而不是`pd.notnull()`功能。

![](img/76c3d9f7c78d5af84a909f37604e55dd.png)

pd.notnull()函数

要复制本教程，请运行 Google Colab 笔记本。

# pd.dropna():

我们使用熊猫图书馆的`pd.dropna()`功能来删除丢失的值。让我们先看看它的语法和参数，以便更好地了解它的功能。

![](img/042cafdb171a9ca9335a500d4e28c2a1.png)

pandas.dropna()函数的语法和参数说明

下面举几个例子来了解一下`pd.dropna()`函数的参数到底是如何影响输出的。

在深入研究`pd.dropna()`函数之前，让我们首先创建一个数据帧。

## A.创建数据框架:

![](img/606ff9e214019fd55c954ff5482f6967.png)

主数据框

## Python 实现:

![](img/74e6708b48c381bc4fd331c4820163ee.png)

Python 代码

![](img/617dd29bd07bb7223452221596e63d65.png)

输出

## B.示例 1:

如果我们没有为`pd.dropna()`函数指定任何参数，它将删除所有至少缺少一个元素的行。

## 使用的参数:

> 没有人

![](img/fefd79e4e01f5041fa2c1605c5fa4ad1.png)

不带任何参数的 pd.dropna()

## Python 实现:

![](img/b64ff80cdb53fcb9801262ca5c4f3a02.png)

Python 代码

## C.示例 2:

如果我们指定参数`axis=0`，它将删除所有至少缺少一个元素的行。这种删除是默认行为。

## 使用的参数:

> 轴= 0

![](img/1749598b6c5b9cc348e9e600af9f4ef3.png)

轴=0 的 pd.dropna()

## Python 实现:

![](img/7c3dc0741c5927931c8ae1b2710c6365.png)

Python 代码

## D.示例 3:

不指定`axis=0`，我们也可以指定`axis="row”`作为参数。它会以同样的方式工作。

## 使用的参数:

> axis = "行"

![](img/1e72408e171d35c02746ae57bedd3e58.png)

轴=行的 pd.dropna()

## Python 实现:

![](img/9348478b86f97d458841538b37c65176.png)

Python 代码

## E.示例 4:

如果我们指定参数`axis=1`，它将删除所有至少缺少一个元素的列。

## 使用的参数:

> 轴= 1

![](img/6ddfc50c97decf954e6949012a9fd030.png)

轴=1 的 pd.dropna()

## Python 实现:

![](img/48c0a0af625a04e1b144a23750d9ca69.png)

Python 代码

## F.示例— 5:

除了指定`axis=1`，我们还可以指定`axis=“columns”`作为参数。它会以同样的方式工作。

## 使用的参数:

> axis = "列"

![](img/3eead7999ab0a7c9943625f7f3d0a0a8.png)

带有轴=列的 pd.dropna()

## Python 实现:

![](img/2b5f8af389e8dae5b5eea777d7805b41.png)

Python 代码

## G.示例— 6:

如果我们将 `how="any”`指定为参数，它将删除至少有一个缺失元素的行。简而言之，如果它有`any`缺失的元素，它将删除这些行。如果我们想在列上执行这个操作，我们必须使用轴参数。

## 使用的参数:

> how = "any "

![](img/a41b0735c7a56e4541b88cad29d55fc3.png)

pd.dropna( ) with how="any "

## Python 实现:

![](img/9bd5f22ebaff9832c7a3c503b1700b8b.png)

Python 代码

## H.创建数据帧:

![](img/a35bcf29650b16dbc2ae9ebf2544b279.png)

创建新的数据帧

## Python 实现:

![](img/b349f8c441d6e64326222649581064e1.png)

Python 代码

![](img/527daf0e38369063976c325e02265594.png)

输出

## 一.示例— 7:

如果我们指定 `how="all”`作为参数，它将删除所有元素都丢失的行。简而言之，如果它有`all`个缺失元素，它将删除这些行。如果我们想在列上执行这个操作，我们必须使用轴参数。

## 使用的参数:

> how = "all "

![](img/5ad3e8d7ba2a6cae7316929595ee8c9a.png)

pd.dropna( ) with how="all "

## Python 实现:

![](img/81638a3114554b00a851c5d51611d84e.png)

Python 代码

## J.示例— 8:

如果我们指定了`thresh`参数，它将只保留那些至少具有由`thresh`参数指定的数量的非缺失元素的行。在下面的例子中，我们可以看到我们已经指定了`thresh=5`，这意味着它将只保留那些有 5 个非缺失元素的行。

## 使用的参数:

> 阈值= 5

![](img/89635897c0c3a235424b82b3c239ad47.png)

thresh=5 的 pd.dropna()

## Python 实现:

![](img/857109237a485c8ab6b8cf81e9c6ebfc.png)

Python 代码

## K.创建数据框架:

![](img/d837ccfbbd244108c3ad6bf4aae0c827.png)

创建新的数据帧

## Python 实现:

![](img/cfc21f9e401f7dda34860624798d311a.png)

Python 代码

![](img/ec7cc4c500e36e5776e3bca66f1e60e2.png)

输出

## 长度示例— 9:

如果我们只想考虑一个列的子集来查找并删除缺失的元素，我们可以使用`subset`参数来指定我们想要在其中查找缺失元素的列名。在下面的例子中，它将只在`“Person”, “Degree”, “Country”`列中查找丢失的值。其他列中缺少的值不会影响最终输出。

## 使用的参数:

> 子集= ["人"，"度"，"国"]

![](img/04a74e33d1bfb8057261e17f90bb3d88.png)

pd.dropna()，子集=["人"，"度"，"国"]

## Python 实现:

![](img/61258ac79b052842c1739c24ef8dea31.png)

Python 代码

## 米（meter 的缩写））创建数据框架:

![](img/7fe2b2a8ee69eb347f8105fa3374f615.png)

创建新的数据框架

## Python 实现:

![](img/87c42f396abb795627dbad2a44e184a5.png)

Python 代码

![](img/4fc5462a7b5695ea15fd71e08ab1ddff.png)

输出

## 名词（noun 的缩写）示例— 10:

如果我们希望改变发生在我们的原始数据帧中，我们必须指定`inplace=True`作为参数。请注意，它不会返回任何内容。执行后，原始数据帧将被`pd.dropna()`函数的结果修改。

## 使用的参数:

> 原地=真

![](img/9e412e6840919442b995d06dcb8bab76.png)

pd.dropna( ) with inplace=True

## Python 实现:

![](img/0ad0b6ee56c510086cb31e8f29ea0f56.png)

Python 代码

# pd.fillna():

pandas 库的`pd.fillna()`函数用于使用特定的方法填充缺失的值。让我们先看看它的语法和参数，以便更好地理解它。

![](img/b783dba451b030cf65f2fd6a708bac7c.png)

pandas.fillna()函数的语法和参数说明

让我们举几个例子来理解参数值是如何影响输出的。

在我们深入研究`pd.fillna()`函数之前，让我们首先创建一个数据帧。

## A.创建数据框架:

![](img/5b9b0c22eb7d6e32433eb3b130ebc10f.png)

创建数据框架

## Python 实现:

![](img/c8e402c98aab9b941ac3bb9610f374b9.png)

Python 代码

![](img/21f596a10251a3f8d26e61880e1b53f0.png)

输出

## B.示例 1:

我们可以使用`value`参数来指定用哪个值来填充缺失的元素。在下面的例子中，我们指定了`value=0`,所以它会用 0 填充所有缺少的元素。

## 使用的参数:

> 值= 0

![](img/416e5ca3cba7307be3e377f24cd78421.png)

值=0 的 pd.fillna()

## Python 实现:

![](img/e0f6b287eca90d33a1e1bb644b4616e3.png)

Python 代码

![](img/3617d63a6f0b4484aa835b4a07a9afed.png)

输出

## C.示例 2:

我们还可以使用`value`参数指定不同的值来填充不同列中缺少的元素。下面的例子演示了我们如何执行这个操作。

## 使用的参数:

> 值=字典

![](img/da6e138c03c6109547fa87c7c4d65f5a.png)

pd.fillna()和一个值字典

## Python 实现:

![](img/058ac174315de975bb740fb75a0f6d8d.png)

Python 代码

![](img/3446a23d190c379cd3ed2de261d64a67.png)

输出

## D.示例 3:

为了填充缺失的元素，我们可以使用`method`参数。如果我们指定`method=”ffill”`，它将使用最后一个有效的观察值来填补空白。如果我们不指定轴的值，它将按行执行操作或轴=0。请注意，没有限制传播最后一个有效的观察值来填充间隙。如果有多个连续的缺失元素，它们将由最后一个有效的观察来填充。

## 重要提示:

如果我们指定了`method=”ffill”`和`axis=0`，并且如果第一行中的元素丢失了，它们将永远不会被填充。

## 使用的参数:

> method = "ffill "

![](img/2edc6580a23c57ae90b57999dbd046c8.png)

data.fillna( ) with method="ffill "

## Python 实现:

![](img/82c1f43d157ff476aff9356ccf760c27.png)

Python 代码

![](img/c464f0d22f9f6aa92da8f9040554b7c3.png)

输出

## E.示例 4:

如果我们指定`method=”pad”`，它的工作方式与`method=”ffill”`相同。

## 使用的参数:

> method = "pad "

![](img/92a4e8fe2b20948434c8b950a0a6f39a.png)

pd.fillna( ) with method="pad "

## Python 实现:

![](img/5ce8bba1d8d0e4f37cd783a8989abc9b.png)

Python 代码

![](img/0255c98d1876385d16f403d9efac7789.png)

输出

## F.示例— 5:

默认情况下，缺少的元素将按行填充，或者用 axis=0 填充。

## 重要提示:

如果我们指定了`method=”ffill”`和`axis=0`，那么如果第一行中的元素丢失，它们将永远不会被填充。

## 使用的参数:

> method = "ffill "
> 
> 轴= 0

![](img/639a20c6ffc47d9ba9f44f64751a2b43.png)

pd.fillna()，method="ffill "且 axis=0

## Python 实现:

![](img/9c76126ab417e9981d03708d56850937.png)

Python 代码

![](img/a21249751fb34aed908fac235697cdc0.png)

输出

## G.示例— 6:

在某些情况下，如果我们想要按列填充缺失的元素，我们可以指定`axis`参数并设置`axis=1`。

## 重要提示:

如果我们指定了`method=”ffill”`和`axis=1`，那么如果第一列中的元素丢失，它们将永远不会被填充。

## 使用的参数:

> method = "ffill "
> 
> 轴= 1

![](img/2a3ede9a78e7bec615d34ec180d89b6f.png)

pd.fillna()，method="ffill "且 axis=1

## Python 实现:

![](img/0d661734df65cbaa62e4d8600c3b89e8.png)

Python 代码

![](img/0fcc1d818c45811b508af6ed43a2cdbf.png)

输出

## H.示例— 7:

为了填充缺失的元素，我们可以使用`method`参数。如果我们指定`method=”bfill”`，它将使用下一个有效的观察值来填补空白。如果我们不指定轴的值，它将按行执行操作或轴=0。请注意，没有限制传播下一个有效的观察来填充间隙。如果有多个连续的缺失元素，它们将被下一个有效的观察填充。

## 重要提示:

如果我们指定了`method=”bfill”`和`axis=0`，那么如果最后一行中的元素丢失了，它们将永远不会被填充。

## 使用的参数:

> method = "bfill "
> 
> 轴= 0

![](img/d9879d79afb1a6ceecb62b9664afde5a.png)

pd.fillna( ) with method="bfill "

## Python 实现:

![](img/532aaba65c04d4c2c992826b93b45960.png)

Python 代码

![](img/f194fbe3845332f6c38692bb7ad276f0.png)

输出

## 一.示例— 8:

如果我们指定`method=”backfill”`，它的工作方式与`method=”bfill”`相同。

## 使用的参数:

> method = "回填"

![](img/c622c810245e183e96682744f351bcdf.png)

pd.fillna( ) with method= "回填"

## Python 实现:

![](img/6c0daceffe4e7a7894a921172c88be8f.png)

Python 代码

![](img/6133b4b12930aeee54ab764f786e7a9e.png)

输出

## J.示例— 9:

默认情况下，缺少的元素将按行填充，或者用 axis=0 填充。

## 重要提示:

如果我们指定了`method=”bfill”`和`axis=0`，那么如果最后一行中的元素丢失了，它们将永远不会被填充。

## 使用的参数:

> method = "bfill "
> 
> 轴= 0

![](img/85cbdb0a4b1a7b81111bef7144bb8ba0.png)

pd.fillna()，method="bfill "且 axis=0

## Python 实现:

![](img/38a2a270c3f107c60f5e8b0c9aed77df.png)

Python 代码

![](img/278afee29672d692477ba283b8029660.png)

输出

## K.示例— 10:

在某些情况下，如果我们想要按列填充缺失的元素，我们可以指定`axis`参数并设置`axis=1`。

## 重要提示:

如果我们指定了`method=”bfill”`和`axis=1`，那么如果最后一列中的元素丢失，它们将永远不会被填充。

## 使用的参数:

> method = "ffill "
> 
> 轴= 1

![](img/d62dfbc81c0e7baea603affd774947e1.png)

pd.fillna()，method="bfill "且 axis=1

## Python 实现:

![](img/98968c321bb6f1f06ec4d164fa297892.png)

Python 代码

![](img/c54d24a1d924eec601acc33d0051d4ef.png)

输出

## 长度示例— 11:

如果我们指定`limit`参数，它将限制向前或向后填充方法中要填充的连续缺失值的最大数量。我们可以说，如果连续缺失元素的间隙大于`limit`参数指定的数量，它将仅被部分填充。这里我们使用向前填充方法，轴=0，限制为 1 个元素。

## 使用的参数:

> method = "ffill "
> 
> 轴= 0
> 
> 极限= 1

![](img/0abb1e0963553673c4098aece5ec5764.png)

pd.fillna()，method="ffill "且 axis=0，limit=1

## Python 实现:

![](img/5eba69db0f4ba56fabf7ba01341c0d5d.png)

Python 代码

![](img/9bb9e27145aeca44af729b796d529abe.png)

输出

## 米（meter 的缩写））示例— 12:

在本例中，我们将使用向前填充方法，轴=1，限制为 1 个元素。

## 使用的参数:

> method = "ffill "
> 
> 轴= 1
> 
> 极限= 1

![](img/687cee9af87c45751520250803c7c2fd.png)

pd.fillna()，method="ffill "且 axis=1，limit=1

## Python 实现:

![](img/6640ceed42da124b762dcf18372d6458.png)

Python 代码

![](img/0f5585885d29c01ef4a3bf1803778f79.png)

输出

## 名词（noun 的缩写）示例— 13:

在本例中，我们将使用反向填充方法，轴=0，限制为 1 个元素。

## 使用的参数:

> method = "bfill "
> 
> 轴= 0
> 
> 极限= 1

![](img/3ad480349ab912078dac6f8a6bfbcb43.png)

pd.fillna()，method="bfill "且 axis=0，limit=1

## Python 实现:

![](img/5ef4526d6f83e2b699d14b505ae0bc81.png)

Python 代码

![](img/c8b3c7ff87e0419c9b289948e9d64b24.png)

输出

## O.示例— 12:

在本例中，我们将使用反向填充方法，轴=1，限制为 1 个元素。

## 使用的参数:

> method = "bfill "
> 
> 轴= 1
> 
> 极限= 1

![](img/87ef95818d3c830aaefd35ca1028f4ee.png)

pd.fillna()，method="bfill "且 axis=1，limit=1

## Python 实现:

![](img/e12379952f0a946601a7553ef69cd80a.png)

Python 代码

![](img/899efebd208d1975aaaef13d10568c3e.png)

输出

## 页（page 的缩写）创建数据帧:

![](img/45b78062d7ac9e9d9c941d4a70a0ccc3.png)

创建新的数据帧

## Python 实现:

![](img/2c506e6485623e8b9bca78a7dc33f750.png)

Python 代码

![](img/82bb95221f8c906d5a2da8a3833efd3a.png)

输出

![](img/2ea3cea1504ca82b3d13f771137c8809.png)

数据类型

## 问题示例— 13:

如果可能的话，我们可以使用`downcast`参数来向下转换数据类型。字符串值 `“infer”`将尝试向下转换为适当的相等类型。比如 float64 到 int64。

## 使用的参数:

> 向下转换=推断

![](img/0b797a0cdd4ab875130309eb772188e7.png)

pd.fillna()，值=0，downcast="infer "

## Python 实现:

![](img/1b0631b0f08132474dfde1791d2cf636.png)

Python 代码

## R.示例— 14:

如果我们希望改变发生在我们的原始数据帧中，那么我们必须指定`inplace=True`作为参数。请注意，它不会返回任何内容。执行后，原始数据帧将被`pd.dropna()`函数的结果修改。

## 使用的参数:

> 原地=真

![](img/09eb81875ecb317591494ef74f52cbf7.png)

pd.fillna()，值=0 且 inplace=True

## Python 实现:

![](img/84056c8f9fbe2ddf63287a7aed9caebd.png)

Python 代码

![](img/3f75eb2b33023c7127abc1f4faa7cf5e.png)

输出

# 警察。DataFrame.bfill():

`pd.DataFrame.bfill()`函数的工作方式与`pd.fillna()`函数使用参数`method=”bfill”.`完全相同

![](img/89128747e8a34c84be4d170382c8423f.png)

让我们举个例子来理解一下。

## A.创建数据框架:

![](img/5afd984b066b509702127bb71b69cb4d.png)

创建数据框架

## Python 实现:

![](img/199d698e134654f0b4bd3d3cac17ae4c.png)

Python 代码

![](img/1d876cdfcab641ddcc63320a64ae535e.png)

输出

## B.示例 1:

## 使用的参数:

> 没有人

![](img/6df5ba81d32e66a2d5bd096569ea081c.png)

pd.bfill()

## Python 实现:

![](img/3e57e5d5968421e1de16d9982a823ed2.png)

Python 代码

![](img/fbce99bdd7d85eebc22717839abb7a56.png)

输出

# 警察。DataFrame .回填( ):

`pd.DataFrame.backfill()`功能的工作方式与`pd.fillna()`功能使用参数`method=”backfill”.`的工作方式相同

![](img/c4496f3e1425e9508b8fa45741ede093.png)

pd 的语法和参数说明。DataFrame .回填( )函数

让我们举个例子来理解它是如何工作的。

## A.创建数据框架:

![](img/5afd984b066b509702127bb71b69cb4d.png)

创建数据框架

## Python 实现:

![](img/199d698e134654f0b4bd3d3cac17ae4c.png)

Python 代码

![](img/1d876cdfcab641ddcc63320a64ae535e.png)

输出

## B.示例 1:

## 使用的参数:

> 没有人

![](img/2e0c810afd33c073738865a25cd41b86.png)

pd .回填( )

## Python 实现:

![](img/d49fe19f0053abc1f395dea5760cd00f.png)

Python 代码

![](img/892241bd56b0317ad96a05faf34ede06.png)

输出

# 警察。DataFrame.ffill():

`pd.DataFrame.ffill()`函数的工作方式与`pd.fillna()`函数使用参数`method=”ffill”.`完全相同

![](img/11d62a6cd5a8842fcbfda15b794199eb.png)

pd 的语法和参数说明。DataFrame.ffill()函数

让我们举个例子来更好地理解它。

## A.创建数据框架:

![](img/5afd984b066b509702127bb71b69cb4d.png)

创建数据框架

## Python 实现:

![](img/199d698e134654f0b4bd3d3cac17ae4c.png)

Python 代码

![](img/1d876cdfcab641ddcc63320a64ae535e.png)

输出

## B.示例 1:

## 使用的参数:

> 没有人

![](img/82ccc425b0a89fe29de9c419ffa765af.png)

pd.ffill()函数

## Python 实现:

![](img/7a7da3d9097c7443f1506e3d9b5a8c25.png)

Python 代码

![](img/cd0264350cc168b9ec89d959b0164943.png)

输出

# 警察。DataFrame.pad():

`pd.DataFrame.pad()`函数的工作方式与`pd.fillna()`函数使用参数`method=”pad”.`的工作方式相同

![](img/4ee025e94d0f79f5751ae82197a95215.png)

pd 的语法和参数说明。DataFrame.pad()函数

让我们举个例子来更好地理解它。

## A.创建数据框架:

![](img/5afd984b066b509702127bb71b69cb4d.png)

创建数据框架

## Python 实现:

![](img/199d698e134654f0b4bd3d3cac17ae4c.png)

Python 代码

![](img/1d876cdfcab641ddcc63320a64ae535e.png)

输出

## B.示例 1:

## 使用的参数:

> 没有人

![](img/686026f5b0bf2ea0e2250c5eac2a554d.png)

pd.pad()函数

## Python 实现:

![](img/bd9c40a56414d722250167c44be76352.png)

Python 代码

![](img/c76f852f35ef10a37f76624a4b645a06.png)

输出

## 结束语:

我们希望您喜欢阅读这篇文章，并学到一些关于处理丢失数据的新知识。

[![](img/7ba4f2d6d12c187d5442ad1a88605fe8.png)](https://www.buymeacoffee.com/pratu)

给普拉蒂克买杯咖啡！

**免责声明:**本文中表达的观点仅代表作者个人观点，不代表与作者(直接或间接)相关的任何公司的观点。这项工作并不打算成为最终产品，而是当前思想的反映，同时也是讨论和改进的催化剂。

**除非另有说明，所有图片均来自作者。**

经由[发布**走向 AI** 发布](https://towardsai.net/)

## 资源

[](https://github.com/towardsai/tutorials/tree/master/pandas) [## 熊猫——走向世界/教程

### AI 相关教程。免费访问其中任何一个→https://towardsai.net/editorial-toward sai/教程

github.com](https://github.com/towardsai/tutorials/tree/master/pandas) [](https://colab.research.google.com/drive/13oVoXxD1rGtcy6tuHp4fuwIb4GgtQol-) [## Google 联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/13oVoXxD1rGtcy6tuHp4fuwIb4GgtQol-) [](https://colab.research.google.com/drive/1SNoC76YZRFl56v4eZfetJoztpo4MUP7C?usp=sharing) [## pd.notna() | Google 联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1SNoC76YZRFl56v4eZfetJoztpo4MUP7C?usp=sharing) [](https://colab.research.google.com/drive/1DrXxT69xNJKGHpLEeZCdTrX93s8wtvhC?usp=sharing) [## pd.isnull() | Google 联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1DrXxT69xNJKGHpLEeZCdTrX93s8wtvhC?usp=sharing) [](https://colab.research.google.com/drive/1INZxS5zMMW6o_yXIDFzxQQzECjY8r2pw?usp=sharing) [## pd.notnull() | Google 联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1INZxS5zMMW6o_yXIDFzxQQzECjY8r2pw?usp=sharing) [](https://colab.research.google.com/drive/1XMpkcE2jYYSPp5Nt47_meRiJzCF9houl?usp=sharing) [## pd.dropna() | Google 联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/1XMpkcE2jYYSPp5Nt47_meRiJzCF9houl?usp=sharing) [](https://colab.research.google.com/drive/175N50wGQc5tJwY09s1HdjAQdsOteXpcN?usp=sharing) [## pd.fillna() | Google 联合实验室

### 编辑描述

colab.research.google.com](https://colab.research.google.com/drive/175N50wGQc5tJwY09s1HdjAQdsOteXpcN?usp=sharing) [](https://ws.towardsai.net/shop) [## 店铺↓ |走向 AI

### 发布最好的技术、科学和工程|社论→https://towardsai.net/p/editorial |订阅→…

ws.towardsai.net](https://ws.towardsai.net/shop) [](https://members.towardsai.net/) [## 加入我们吧↓ |面向人工智能成员|数据驱动的社区

### 加入人工智能，成为会员，你将不仅支持人工智能，但你将有机会…

members.towardsai.net](https://members.towardsai.net/) [](https://sponsors.towardsai.net/) [## 赞助商|了解如何成为《走向人工智能》的赞助商

### 无论你是想以一种吸引读者的方式突出你的产品，吸引高度相关的利基受众，还是…

sponsors.towardsai.net](https://sponsors.towardsai.net/) 

## 参考

1.  “熊猫。数据框架.回填-Pandas 1 . 2 . 4 文件”。2021.Pandas.Pydata.Org。[https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.backfill.html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.backfill.html)。
2.  “熊猫。data frame . drop na-Pandas 1 . 2 . 4 文档”。2021.Pandas.Pydata.Org。[https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.dropna.html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.dropna.html)。
3.  “熊猫。data frame . Pad-Pandas 1 . 2 . 4 文档”。2021.Pandas.Pydata.Org。【https://pandas.pydata.org/docs/reference/api/pandas. DataFrame.pad.html。
4.  “熊猫。Dataframe.Notnull — Pandas 1.2.4 文档”。2021.Pandas.Pydata.Org。【https://pandas.pydata.org/docs/reference/api/pandas. DataFrame.notnull.html。
5.  “熊猫。Dataframe.Notna — Pandas 1.2.4 文档”。2021.Pandas.Pydata.Org。[https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.notna.html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.notna.html)。
6.  “熊猫。Dataframe.Isnull — Pandas 1.2.4 文档”。2021.Pandas.Pydata.Org。[https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.isnull.html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.isnull.html)。
7.  “熊猫。data frame . Isna-Pandas 1 . 2 . 4 文档”。2021.Pandas.Pydata.Org。[https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.isna.html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.isna.html)。
8.  “熊猫。data frame . fill na-Pandas 1 . 2 . 4 文档”。2021.Pandas.Pydata.Org。[https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.fillna.html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.fillna.html)。
9.  “熊猫。Dataframe.Ffill — Pandas 1.2.4 文档”。2021.Pandas.Pydata.Org。[https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.ffill.html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.ffill.html)。
10.  “熊猫。data frame . drop na-Pandas 1 . 2 . 4 文档”。2021.Pandas.Pydata.Org。[https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.dropna.html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.dropna.html)。