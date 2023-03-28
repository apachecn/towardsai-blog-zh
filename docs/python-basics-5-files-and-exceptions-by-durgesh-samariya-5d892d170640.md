# Python 基础— 5:文件和异常

> 原文：<https://pub.towardsai.net/python-basics-5-files-and-exceptions-by-durgesh-samariya-5d892d170640?source=collection_archive---------3----------------------->

## [编程](https://towardsai.net/p/category/programming)， [Python](https://towardsai.net/p/category/programming/python)

## 机器学习 100 天的第 5 天

![](img/2a3e21f857f34f828ec319d6f33038da.png)

詹姆斯·哈里森在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

我相信你在关注我之前的所有部分(如果没有，那么你可以在这里找到它们→ [第 1 部分](https://medium.com/the-innovation/python-basics-variables-data-types-and-list-59cea3dfe10f)、[第 2 部分](https://towardsdatascience.com/python-basics-2-working-with-list-tuples-dictionaries-871c6c01bb51)、[第 3 部分](https://medium.com/towards-artificial-intelligence/python-basics-3-97a8e69066e7)和[第 4 部分](https://medium.com/javarevisited/python-basics-4-functions-working-with-functions-classes-working-with-class-inheritance-70e0338c1b2e))。我假设您现在已经掌握了 python 基础知识。在这篇文章中，我们将学习如何处理文件和异常。

# 内容

*   读取文本文件
*   逐行读取文件
*   从数据行创建列表
*   不同模式
*   追加文本
*   例外

# 读取文本文件

这个时代，数据无处不在，读/写数据有利于数据分析。所以让我们来看看如何用 Python 读取文件的代码。首先，让我们看看这个文件是什么样子的。

要在您的系统中运行这段代码，请从这里下载文本，然后将其移动到您的 python 文件所在的目录中。现在让我们来看看 python 代码。

# 逐行读取文件

在 Python 中，您也可以逐行读取文件的数据。让我们来看看代码。

# 从数据行创建列表

在 Python 中，可以根据数据行创建列表。您可以使用`readlines()`方法来完成。让我们来看看。

到目前为止，我们学习了如何从文件中读取内容。现在让我们学习如何在文件中写入数据。创建一个新的空文本文件。

# 不同模式

## r’—读取模式

此模式允许您读取文件

## w’—写入模式

此模式将使您能够编写文件；当文件为空时，最好使用写入模式，因为如果您对包含一些内容的文件使用该模式，旧内容将被删除，新内容将被写入。

## ' a' —附加模式

该模式允许读取和写入。

## r+' —读写模式

这种模式也允许我们读和写。

# 追加文本

如前所述，附加模式允许读和写。让我们假设您想在我们的文本文件“编程语言”中添加模式编程语言。

# 例外

和其他编程语言一样，Python 也有一个例外。异常有利于处理错误。错误可以在“try-catch”块中处理。Try-catch 块允许程序即使在出现错误时也能运行。让我们试着用 0 除 10。如果在 Python 中没有 try-catch 的情况下运行，将会得到一个错误。让我们看看错误。

现在让我们使用 try-catch 块。

今天我们从 [python 速成教程](https://geni.us/ew5ZE7B)一书中(第 10 章)学习了 Python 的基础知识。今天我已经学完了 python 的所有基本概念。我将用几天时间练习所有这些概念，然后我将转向数据科学 python 库。

我参加这个 100 天机器学习挑战的目标是从零开始学习机器学习，并帮助其他想开始机器学习之旅的人。很多概念我都知道，但我是从零开始，帮助机器学习社区的初学者，修正概念。

**感谢阅读！**

如果你喜欢我的工作并想支持我，我会非常感谢你在我的社交媒体频道上关注我:

*   支持我的最好方式就是跟随我上 [**中级**](https://medium.com/@themlphdstudent) 。
*   订阅我的新 [**YouTube 频道**](https://www.youtube.com/c/themlphdstudent) 。
*   在我的 [**邮箱列表**](http://eepurl.com/hampwT) 报名。

如果你错过了我的前一部分系列。

*   第 0 天:[挑战介绍](/@durgeshsamariya/100-days-of-machine-learning-code-a9074e1c42c3)
*   第 1 天: [Python 基础知识— 1](/the-innovation/python-basics-variables-data-types-and-list-59cea3dfe10f)
*   第二天: [Python 基础知识— 2](https://towardsdatascience.com/python-basics-2-working-with-list-tuples-dictionaries-871c6c01bb51)
*   第 3 天: [Python 基础知识— 3](/towards-artificial-intelligence/python-basics-3-97a8e69066e7)
*   第 4 天: [Python 基础— 4](https://medium.com/javarevisited/python-basics-4-functions-working-with-functions-classes-working-with-class-inheritance-70e0338c1b2e)

我希望你会喜欢我的其他文章。

*   [八月月度阅读清单](/@durgeshsamariya/august-2020-monthly-machine-learning-reading-list-by-durgesh-samariya-20028aa1d5cc)
*   [集群资源](/towards-artificial-intelligence/a-curated-list-of-clustering-resources-fe355e0e058e)
*   [离群点检测资源](https://medium.com/dev-genius/curated-list-of-outlier-detection-resources-35ed27d0e46e)
*   [降价备忘单](https://medium.com/dev-genius/markdown-cheatsheet-59d872798107)