# 无分支编程如何提高 Excel 的速度

> 原文：<https://pub.towardsai.net/an-example-of-branchless-logic-using-excel-c6afc6eef75e?source=collection_archive---------5----------------------->

![](img/f062800fc3f1fd90098c02c23901ebb7.png)

来源: [Unsplash](https://unsplash.com)

## [数据科学](https://towardsai.net/p/category/data-science)

## 使用 Excel 进行分类的无分支逻辑示例

本文以 IRIS flowers 数据集和[几何平均分类器](https://medium.com/towards-artificial-intelligence/geometric-mean-classifier-for-iris-dataset-ed83209f54f3)为例，介绍了 excel 中无分支逻辑的应用。(参见下面的视频，了解更多相关信息)

无分支编程—[https://www.youtube.com/watch?v=bVJ-mWWL7cE](https://www.youtube.com/watch?v=bVJ-mWWL7cE)

## 用例概述

这个例子将带你浏览一个例子，将一个嵌套的 **if 语句用例转换成一个没有任何 if 语句**的更快的计算。这提高了大型 excel 工作簿的性能，也大大缩短了代码。

假设您正试图根据下面显示的高低范围对来自[虹膜数据集](https://en.wikipedia.org/wiki/Iris_flower_data_set)的三种花进行分类。对这个逻辑进行编程的最简单的方法是使用一个标准的 IF 语句来测试一个测试数据实例的几何平均值是否落在下限和上限之间。然而，随着测试数据集变得越来越大，嵌套的 if 语句会破坏工作簿的速度。

![](img/1c53c82ddaf4ce93dde62ab6f3b54e69.png)

分类器的虹膜数据高-低范围

## 如何用 If 语句写出分类问题

首先，让我们看看如何用一个 If 语句结合一个 AND 语句来写这个。这是 excel 中 if 语句的格式:

```
=if(condition, output if the condition is true, output if the condition is false)
```

“And”语句看起来是这样的:

```
=AND(condition 1, condition 2,…condition n). An AND statement returns TRUE in a cell if the condition is met.
```

例如:

```
=AND(1=1,2=2) will return TRUE//=AND(1=1,2=1) will return FALSE because 2 is NOT equal to 1.
```

为了编写 IF(AND)语句，可以使用以下语法:

```
=If(AND(condition 1, condition 2… , condition n), output if ALL conditions return TRUE, output if all conditions return FALSE)
```

现在，让我们看看，在给定一个测试数据集实例的情况下，我们将如何从上面的语句中为 Versicolor 编写这个。

想象一下，你的测试数据有一个 2.75 的几何平均值，这意味着你将把这个实例归类到 Versicolor 中，那么这是如何编码的呢？

嗯，这里有两个你必须满足的条件:

> 几何平均值是否大于上面查找表中的杂色范围的下限？
> 
> 几何平均值是否小于上面查找表中的杂色范围的高端？

如果符合范围，此代码将返回 TRUE，如果不符合范围，则返回 FALSE:

```
=AND(geomean>=low of versicolor, geomean<=high of versicolor)
```

现在我们要做的就是用 if 语句包装它:

```
=If(AND(geomean>=low of versicolor, geomean<=high of versicolor),”versicolor”, “not versicolor”)
```

然而，这仍然不能给你所有的三朵花。为了实现这一点，您必须嵌套一个 IF 语句:

```
=If(AND(geomean>=low of versicolor, geomean<=high of versicolor),”versicolor”, If(AND(geomean>=low of setosa, geomean<=high of setosa),”setosa”, If(AND(geomean>=low of virginica, geomean<=high of virginica),”virginica”……)
```

> 这是一个很长的 if 语句，它必须一遍又一遍地计算嵌套的 IF 才能得到正确的花类。

我们如何避免这种情况？有没有一种方法可以大大缩短这段代码，并把它变成一些简单的算法？有，这是我们可以引入无分支编程的地方。

## Excel 中的无分支编程

让我们先看看我们之前为 Versicolor 编写的 AND 语句。

```
AND(geomean>=low of Versicolor, geomean<=high of Versicolor)
```

注意，在布尔语句中，真等于 1，假等于 0。

现在，让我们试着理解如何用这个来代替 IF 逻辑。本质上，当条件评估为真或 1 时，我们希望重复花名(文本)1 次，当它为假或 0 时，我们希望重复 0 次，即显示空白。

让我们把它写出来:

![](img/1c53c82ddaf4ce93dde62ab6f3b54e69.png)

细胞:物种名称在 I4、I5 和 I6 中。低的是 L 列，高的是 m 列。下面是公式如何从测试数据集中查找您想要分类的花:

```
=REPT(I4,AND(geomeangiven>=L4, geomeangiven <=M4)) → versicolor=REPT(I5,AND(geomeangiven >=L5, geomeangiven <=M5)) → setosa=REPT(I6,AND(geomeangiven >=L6, geomeangiven <=M6)) → virginica
```

将这两者结合起来，可以替代上面的嵌套 if 语句:

```
= REPT(I4,AND(geomeangiven>=L4, geomeangiven <=M4))&REPT(I5,AND(geomeangiven >=L5, geomeangiven <=M5))&REPT(I6,AND(geomeangiven >=L6, geomeangiven <=M6))
```

本质上，不是***慢慢地…计算*** ***3 个 if 语句在对方*** 内，你只是串联了三个不同的简单算术公式，其中两个将计算为空白，一个将是花的名字。

参考资料:

1.  无分支编程:为什么“如果”很慢...以及我们能做些什么！—[https://www.youtube.com/watch?v=bVJ-mWWL7cE](https://www.youtube.com/watch?v=bVJ-mWWL7cE)