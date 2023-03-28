# 了解熊猫融化— pd.melt()

> 原文：<https://pub.towardsai.net/understanding-pandas-melt-pd-melt-362954f8c125?source=collection_archive---------0----------------------->

![](img/2e77211d1d1a3a6d0ac665fdda2181e3.png)

Pandas.melt()函数示例|图片由作者提供|除非另有说明，所有图片均来自作者。

## [数据科学](https://towardsai.net/p/category/data-science)、[编辑](https://towardsai.net/p/category/editorial)、[编程](https://towardsai.net/p/category/programming)

## 了解重塑 Pandas 数据框的最有效和最灵活的函数

**作者:** [普拉蒂克·舒克拉](https://www.linkedin.com/in/pratik-shukla28/)，[罗伯特·伊里翁多](https://mktg.best/vguzs)

[](https://members.towardsai.net/) [## 加入我们吧↓ |面向人工智能成员|数据驱动的社区

### 向着 AI 加入。通过成为会员，你不仅将支持人工智能，但你将有机会…

members.towardsai.net](https://members.towardsai.net/) 

他的教程将更深入地探究 Pandas 的函数，理解它的图形核心功能及其在 Python 中的实现。我们将首先看到这个方法的语法和参数。那么我们就举几个例子来了解所有的`pd.melt()`函数参数。本教程的配套资源可以在 [**Google Colab**](https://colab.research.google.com/drive/1Anc3ydboAyrxxVycP0wtMYbDCvSWDSpN?usp=sharing) 或 [**Github**](https://github.com/towardsai/tutorials/tree/master/pandas/pd-melt.py) 上找到。

## 什么是 PD 熔体？

**Pandas melt()** 函数是用于将 Pandas 数据帧从宽格式重塑为长格式的许多其他方法中的一种，这在 [**数据科学**](https://mld.ai/mldcmu) 中特别有用。然而，`pd.melt()`功能是**中最高效、最灵活的**。`pd.melt()`功能将熊猫数据帧从宽格式解旋转/融化为长格式。

![](img/692b8eadbadaeedc0b22b6b6a8d7c287.png)

图 pd.melt()函数的语法。

## 宽与长数据帧:

在将我们的**宽数据帧**转换为**长数据帧**之前，让我们先直观地看看它们之间的区别。下面是一个数据帧的例子。

![](img/e10620b2b21d04a8e2a6738781890fd4.png)

图 2:宽格式的数据帧。

现在，下图显示了一个 DataFrame，它包含相同的数据，但格式较长。

![](img/7ad8102bfa2988aeadbe296a802cd524.png)

图 3:长格式的数据帧。

在深入研究之前，让我们首先使用`pd.DataFrame()`创建一个宽数据帧。

## A.创建宽数据框架:

![](img/e10620b2b21d04a8e2a6738781890fd4.png)

图 4:创建主数据帧。

![](img/014db2a92a22467b72add903c5718976.png)

图 5: Python 代码。

![](img/873b554d1f25216d5eb4524c87b533a0.png)

图 6: Python 代码输出。

## B.示例 1:

**使用的参数:**

> 没有使用参数

**在使用`pd.melt()`方法时，如果我们不指定任何参数**，它将熔化所有列及其相应的值。

![](img/7dbff5960989a31d8968fc39dbfbbca1.png)

图 7:主数据帧。

![](img/920136f2f67235234356a7808e40d180.png)

图 8:使用 pd.melt()函数。

![](img/10ef25cd8b9fcfef1cd1e5b7a16496c6.png)

图 9:输出。

![](img/c58117e3870791da56e1cd3cca4012f2.png)

图 10:输出。

## Python 实现:

![](img/80cec262529f15544420f1eba7a44cc1.png)

图 11: Python 代码。

![](img/d7c60f283d2411ed0d8d09306d2b9afc.png)

图 12: Python 代码输出。

## C.示例 2:

**使用的参数:**

> id_vars:人，房子

在本例中，我们将通过仅指定`id_vars`参数来融合我们的`data_wide`数据帧。在`id_vars`(人，房子)中使用的列被称为标识符变量，这些列不会被融化。由于我们没有指定任何其他参数，所有其他列(年龄、书籍、电影)将被融合成一个单独的列。

在输出中，我们有两个新列:变量和值。变量列存储融合列的名称，值列存储融合列的实际值。我们可以使用`var_name`和`value_name`参数更改输出列名。

这里需要注意的关键点是，在`id_vars`中指定列名之后，不指定要融合的列将会融合所有剩余的列。

![](img/4e7241c16c2e02cdc2b69e48aa55a813.png)

图 13:主数据帧。

![](img/506360e2af37174c0105ded65169aaa4.png)

图 14:使用 pd.melt()函数。

![](img/fb8f6a1f84bdcb4319ec482bc10117c7.png)

图 15:输出。

## Python 实现:

![](img/bfe0dfe45fc784722d0f1a4a922cfa3e.png)

图 16: Python 代码。

![](img/29bb316351a129d7c4a9aa94cef346d1.png)

图 17: Python 代码输出。

## D.示例 3:

**使用的参数:**

> id_vars:人，房子
> 
> value_vars:年龄、书籍、电影

在这个例子中，我们指定`id_vars`来指定我们不希望融合的列名(Person，House)。除此之外，我们使用`value_vars`参数来指定我们想要融合的列名(年龄、书籍、电影)。

![](img/4e7241c16c2e02cdc2b69e48aa55a813.png)

图 18:主数据帧。

![](img/b6c8329fc4e0457c80599a6f8fbc760d.png)

图 19:使用 pd.melt()函数。

![](img/fb8f6a1f84bdcb4319ec482bc10117c7.png)

图 20:输出。

## Python 实现:

![](img/658f987ecca18e8d807adf2037cbc79d.png)

图 21: Python 代码。

![](img/ee3be0bc50d6b7f96b6f0017df91d610.png)

图 22: Python 代码输出。

## E.示例 4:

**使用的参数:**

> id_vars:人员
> 
> value_vars:书籍、电影

下面的例子显示了我们可以为参数`id_vars`和`value_vars.`使用任意多的列

![](img/4e7241c16c2e02cdc2b69e48aa55a813.png)

图 23:主数据帧。

![](img/b982566b23c99a03c18bbb677a48a1b9.png)

图 24:使用 pd.melt()函数。

![](img/efc8bf23a19a37e3b71886090b4c35b9.png)

图 25:输出。

## Python 实现:

![](img/bb9621f1e9682a4a263fc5b804e569b4.png)

图 26: Python 代码。

![](img/d6e9839c84f866f4584bc488d92dd649.png)

图 27: Python 代码输出。

## F.示例— 5:

**使用的参数:**

> id_vars:人，房子
> 
> value_vars:年龄、书籍、电影
> 
> var_name:信息
> 
> 数值名称:数字

下面的例子展示了我们如何使用`var_name`和`value_name`参数来改变输出列的名称。

![](img/5c58b1b815d586800333b53a6e82dcf5.png)

图 28:主数据帧。

![](img/aa393d930bc7d47edb890082c8240bdc.png)

图 29:使用 pd.melt()函数

![](img/587796fdf7b3778135763ecc02e85fb4.png)

图 30:输出。

## Python 实现:

![](img/5e5e0535c01e5940e0f5a35a81cde6a8.png)

图 31: Python 代码。

![](img/1d8fedeb3724ce1a31767f6fc3317567.png)

图 32: Python 代码输出。

## G.示例— 6:

**使用的参数:**

> id_vars:人员
> 
> value_vars:书籍、电影
> 
> var_name:信息
> 
> 数值名称:数字

以下示例使用选定的列作为`id_vars`和`value_vars`参数。除此之外，我们还使用 `var_name`和`value_name`参数改变输出数据帧的列名。

![](img/5c58b1b815d586800333b53a6e82dcf5.png)

图 33:主数据帧。

![](img/138e5e7d6628ef5a9ba8e0e1bf4e83ef.png)

图 34:使用 pd.melt()函数。

![](img/36b0271a103e089520a2b06813049ea8.png)

图 35:输出。

## Python 实现:

![](img/496a7d8b74942e5ea8808b5ec38361e8.png)

图 36: Python 代码。

![](img/4b369ec7af108389033689dd90e1a059.png)

图 37: Python 代码输出。

## H.示例— 7:

**使用的参数:**

> id_vars:人，房子
> 
> value_vars:年龄、书籍、电影
> 
> var_name:信息
> 
> 数值名称:数字
> 
> Ignore _ 索引:False

下面的例子显示了使用`ignore_index`参数来忽略或保留原始索引。如果我们将`ignore_index`设置为`False`，那么原始索引将被保留。如果我们将`ignore_index`设置为`True`，它将忽略原始索引，并为该索引分配连续值。

![](img/5c58b1b815d586800333b53a6e82dcf5.png)

图 38:主数据帧。

![](img/1066f1113ba7c3e9a7d56c2265255bda.png)

图 39:使用 pd.melt()函数。

![](img/814f74825482d41228c7900976d525d1.png)

图 40:输出。

## Python 实现:

![](img/8fa0645e85bda968c96744694a74e1db.png)

图 41: Python 代码。

![](img/5a6aa2ab11389380ced59ca46ef63b50.png)

图 42: Python 代码输出。

## I .创建具有多个索引的数据帧:

在某些情况下，列会有多个名称。在这种情况下，我们可以使用`col_level`参数来指定在熔化数据帧时使用哪个级别。

![](img/6a497634ed20a2926126b76cf03e14ae.png)

图 43:带有多个索引的主数据帧。

![](img/34408a0d6c095d13d3898120efcf8d94.png)

图 44: Python 代码。

![](img/a3b66688b5a28064141022932a00b47b.png)

图 45: Python 代码输出。

## J.示例— 8:

**使用的参数:**

> id_vars:人，房子
> 
> value_vars:年龄、书籍、电影
> 
> var_name:信息
> 
> 数值名称:数字
> 
> 列级别:0

以下示例演示了如何使用第 0 个列级索引，使用`col_level`参数来融合数据帧。

![](img/6a497634ed20a2926126b76cf03e14ae.png)

图 46:带有多个索引的主数据帧。

![](img/1b2faab9a006d1714094b4dc020d6ef0.png)

图 47:使用 pd.melt()函数。

![](img/5b8977a89e286cec63c1e22e6feb83f2.png)

图 48:输出。

## Python 实现:

![](img/12d26a0de09eaab439592c67b695b82b.png)

图 49: Python 代码。

![](img/a43e8439221b7bee08e704ce6e32d781.png)

图 50: Python 代码输出。

## K.示例— 9:

**使用的参数:**

> id_vars:人，房子
> 
> value_vars:年龄、书籍、电影
> 
> var_name:信息
> 
> 数值名称:数字
> 
> 列级别:1

下面的例子演示了如何使用列级的第一个索引，使用参数`col_level`来融合数据帧。

![](img/6a497634ed20a2926126b76cf03e14ae.png)

图 51:带有多个索引的主数据框。

![](img/35331ded83ebc1dfcc064754695eaa22.png)

图 52:使用 pd.melt()函数。

![](img/fdfb462865d54bcfbfe7ca1ec03322ce.png)

图 53:输出。

## Python 实现:

![](img/3c5f8c3dd3e96ff97a916e8dc3f8c59c.png)

图 54: Python 代码。

![](img/173e8430b950c52763c40c47b9e61f52.png)

图 55: Python 代码输出。

## 长度示例— 10:

**使用的参数:**

> id_vars:人，房子
> 
> value_vars:年龄、书籍、电影
> 
> var_name:信息
> 
> 数值名称:数字
> 
> Ignore _ 索引:False
> 
> 列级别:1

在下面的例子中，我们将使用所有的`pd.melt()`函数参数。

![](img/6a497634ed20a2926126b76cf03e14ae.png)

图 56:带有多个索引的主数据帧。

![](img/d702636e4d0c5084fa2d55c6e1c6e8ca.png)

图 57:使用带有所有参数的 pd.melt()函数。

![](img/479fe5b481c96f92279ccb586d362c97.png)

图 58:输出。

## Python 实现:

![](img/0e52d0666ae9df5c017965b143cbd352.png)

图 59: Python 代码。

![](img/06f8f320d6608349bccdc9e1124cc179.png)

图 60: Python 代码输出。

## 结束语:

我们希望你喜欢阅读这篇文章，并了解到一些关于`pd.melt()`函数**的新东西，它允许我们重新塑造数据帧**。一如既往，请随时让我们知道你的想法。感谢您的阅读！

[![](img/7ba4f2d6d12c187d5442ad1a88605fe8.png)](https://www.buymeacoffee.com/pratu)

给普拉蒂克买杯咖啡！

**免责声明:**本文所表达的观点仅代表作者个人观点，不代表与作者(直接或间接)相关的任何公司的观点。这项工作并不打算成为最终产品，而是当前思想的反映，同时也是讨论和改进的催化剂。

**除非另有说明，所有图片均来自作者。**

通过 [**向 AI**](https://towardsai.net/) 发布

## 参考资料和资源:

[](https://colab.research.google.com/drive/1Anc3ydboAyrxxVycP0wtMYbDCvSWDSpN?usp=sharing) [## 了解熊猫融化——谷歌合作实验室

colab.research.google.com](https://colab.research.google.com/drive/1Anc3ydboAyrxxVycP0wtMYbDCvSWDSpN?usp=sharing) 

[**Github 资源库**](https://github.com/towardsai/tutorials/blob/master/pandas/pd-melt.py) 。

[**熊猫文献—熊猫融化**](https://pandas.pydata.org/docs/reference/api/pandas.melt.html)

[](https://ws.towardsai.net/shop) [## 店铺↓ |走向 AI

### 发布最好的技术、科学和工程|社论→https://towardsai.net/p/editorial |订阅→…

ws.towardsai.net](https://ws.towardsai.net/shop) [](https://members.towardsai.net/) [## 加入我们吧↓ |面向人工智能成员|数据驱动的社区

### 加入人工智能，成为会员，你将不仅支持人工智能，但你将有机会…

members.towardsai.net](https://members.towardsai.net/) [](https://sponsors.towardsai.net/) [## 赞助商|了解如何成为《走向人工智能》的赞助商

### 无论你是想以一种吸引读者的方式突出你的产品，吸引高度相关的利基受众，还是…

sponsors.towardsai.net](https://sponsors.towardsai.net/)