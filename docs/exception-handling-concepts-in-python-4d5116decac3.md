# Python 中的异常处理概念

> 原文：<https://pub.towardsai.net/exception-handling-concepts-in-python-4d5116decac3?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 使用 try、except 和 finally 关键字进行错误处理

![](img/2d2fc544c4cd40a17b9a85c68f3fabbc.png)

由[马库斯·斯皮斯克](https://unsplash.com/@markusspiske?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

在本文中，我们将讨论 python 中的错误处理，用 try、except 和 finally 关键字来处理文件和数据管理。

一般来说，错误分为以下三类:

*   编译时错误:当我们出现一些语法错误时，比如遗漏了什么、拼写错误、使用了未定义的变量等等。这些类型的错误出现在编译时。
*   **逻辑错误:**当程序正常运行或编译，但给出错误或不希望的输出时，就会出现这种错误。所以，这种错误被称为逻辑错误。
*   **运行时错误:**该错误发生在程序执行过程中。例如，被零除、编码、I/O 或逻辑错误。

异常处理是一种非常现实的处理异常的方法，当程序中发生错误时，解释器会停止并引发一个异常，直到它被处理。为了在程序中处理这些类型的异常以继续执行，我们学习异常处理。

[](/python-zero-to-hero-with-examples-c7a5dedb968b) [## Python:从零到英雄(带示例)

### python 初学者手册指南

pub.towardsai.net](/python-zero-to-hero-with-examples-c7a5dedb968b) [](/tips-and-tricks-in-machine-learning-with-python-to-avoid-data-leakage-c3908fa4a0c9) [## 使用 Python 进行机器学习以避免数据泄漏的技巧和诀窍

### 更有效地编写机器学习算法

pub.towardsai.net](/tips-and-tricks-in-machine-learning-with-python-to-avoid-data-leakage-c3908fa4a0c9) 

## python 的例子

```
x = 4
y = 2print(x/y)#output:
2
```

这里，我们得到输出“2 ”,因为执行了 print 语句。我们还可以打印另一条语句来检查整个程序是否正确执行。

```
x = 4
y = 2print(x/y)
print("All Well")#output:
2
All Well
```

程序正确执行。如果我们将变量“y”的值改为“0 ”,会发生什么情况？

```
x = 4
y = 0print(x/y)
print("All Well")#output:ZeroDivisionError : division by zero
```

该程序给出一个错误，并告诉它不是除以零。还有一点需要注意，第二个打印的语句没有打印出来是因为错误出现在第二个打印的语句之前。

因此，要处理这种错误，可以通过 try 和 except 块，如下例所示:

```
x = 4
y = 0#putting the critical statement in a try block
try:
    print(x/y)#handling the critical statement in except block
except Exception:
    print("You can not divide the number by Zero")print("All Well")#output:
You can not divide the number by Zero
All Well
```

上面的例子处理了异常块中的关键语句，程序的执行过程在出错后继续。我们还注意到第二个 print 语句也被执行了。

当没有错误时，将执行 try 块中的 print 语句，但不执行异常块。

如果我们想打印错误语句，如下例所示:

```
x = 4
y = 0#putting the critical statement in a try block
try:
    print(x/y)#handling the critical statement in except block
except Exception as e:
    print("Error:", e)print("All Well")#output:
Error: division by zero 
```

当我们处理文件和数据资源时，关闭它也是非常重要的。下面的例子显示了我们是如何以及在哪个块中关闭文件或资源的。

```
x = 4
y = 0#putting the critical statement in a try block
try:
    print("file opened")   
    print(x/y)
    print("file closed")#handling the critical statement in except block
except Exception as e:
    print("Error:", e)
```

在这种情况下，我们在 try 块中打开并关闭了文件，但是如果我们在两者之间得到一个错误，那么执行跳转到异常块，我们的“file closed”语句不会被处理。

```
#output:
file opened
Error: division by zero
```

出现错误后，我们的文件仍然打开。如果我们将“文件关闭”语句放在异常块中，那么它将关闭文件。但是，如果我们没有得到一个错误，那么 except 块不会执行，瓷砖仍然会打开。

为了使文件或资源有错误或无错误地关闭，我们使用 finally 块。在这个块中，每次执行 try 或 except 块后，这个 finally 块都会执行。因此，我们应该将“文件关闭”语句放在“finally”块中。

示例:

```
x = 4
y = 0#putting critical statement in try block
try:
    print("file opened")   
    print(x/y) #handling the critical statement in except block
except Exception as e:
    print("Error:", e)finally:
    print("file closed")#output:
file opened
Error: division by zero
file closed
```

在异常处理程序中使用这三个块是一个好的实践。

## 结论:

当我们测试程序时，这些概念是很方便的。

[](/fully-explained-birch-clustering-for-outliers-with-python-2ad6243f126b) [## 用 Python 对异常值进行 BIRCH 聚类的完整解释

### 聚类中的无监督学习为数据建立树

pub.towardsai.net](/fully-explained-birch-clustering-for-outliers-with-python-2ad6243f126b) 

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —零到英雄与 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)3 .[数据预处理概念同 Python](/data-preprocessing-concepts-with-python-b93c63f14bb6?source=friends_link&sk=5cc4ac66c6c02a6f02077fd43df9681a)
4。[用 Python 进行主成分分析降维](/principal-component-analysis-in-dimensionality-reduction-with-python-1a613006d531?source=friends_link&sk=3ed0671fdc04ba395dd36478bcea8a55)
5。[用 Python 全面讲解 K-means 聚类](https://medium.com/towards-artificial-intelligence/fully-explained-k-means-clustering-with-python-e7caa573176a?source=friends_link&sk=9c5c613ceb10f2d203712634f3b6fb28)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[用 Python 实现时间序列的基础知识](https://medium.com/towards-artificial-intelligence/basic-of-time-series-with-python-a2f7cb451a76?source=friends_link&sk=09d77be2d6b8779973e41ab54ebcf6c5)
9。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)