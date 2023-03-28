# Python 基础— 3: If 语句、用户输入、While 循环

> 原文：<https://pub.towardsai.net/python-basics-3-97a8e69066e7?source=collection_archive---------2----------------------->

## [编程](https://towardsai.net/p/category/programming)， [Python](https://towardsai.net/p/category/programming/python)

## 机器学习 100 天的第 3 天

![](img/0e8e3937b42c750eae4ea758f6fbebc5.png)

照片由 [Pakata Goh](https://unsplash.com/@pakata?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

# 内容

*   如果语句
*   条件测试
*   If-Elif-Else 语句
*   用户输入
*   While 循环
*   在循环中中断并继续

# 如果语句

If 语句用于检查条件。让我们来看看语法。

```
. . .
. . .if condition:
 . . . .
 do_something
 . . . .else:
 . . . .
 do_something
 . . . .. . . .
. . . .
```

上面给出的语法只是简单的 if-else 语法。在 python 中，可以创建更复杂的 if-else 系列。首先，我们来看一个非常基本的 if 语句例子。

# 条件测试

一个`if`语句总是需要一个条件来回答真或假。如果条件返回 True，那么 python 将运行 If 语句块。如果条件返回 False，那么 python 会跳过 If 语句。

在 python 中，可以用不同的方式比较条件，比如相等、不相等、数字比较、多个条件、值是否在列表中以及布尔表达式。让我们看看下面每个条件的代码示例。

# If-Elif-Else 语句

在很多现实生活的例子中，你需要检查多个条件。Python 允许 if-elif-else 链，其中它只运行一个代码块。假设您要建立一个评分系统，如果百分比小于 35，则打印失败，如果百分比大于或等于 35 且小于 70，则打印合格，如果百分比大于 70，则打印您通过的一等品。让我们看看如何使用 if-elif-else 链在 python 中实现这一点。

在 python 中，可以使用多个 elif 块，如果愿意，可以省略/忽略 else 块。让我们来看看代码。

# 用户输入

许多应用程序需要来自用户的信息。在 python 中，要做到这一点，我们需要`input()`函数。让我们来看看代码。

您也可以接受整数值和浮点值。你只需要把它们从 string 转换成 int 或者 float。

# While 循环

当给定条件为真时，While 循环运行代码块。

# 在循环中中断并继续

在 python 中，可以使用 break 语句立即退出循环，而无需在循环中运行完整的代码。让我们看一下代码。

您可以使用 continue 语句返回到循环的开头，而不是中断整个循环。

今天我们从 python 速成教材(第 5 章和第 7 章)中学到了 Python 的基础知识。我参加这个 100 天机器学习挑战的目标是从零开始学习机器学习，并帮助其他想开始机器学习之旅的人。很多概念我都知道，但我是从零开始，帮助机器学习社区的初学者，修正概念。

**感谢阅读。**

如果你喜欢我的工作并想支持我，我会非常感谢你在我的社交媒体频道上关注我:

*   支持我的最好方式就是跟随我上[](/@durgeshsamariya)**。**
*   **订阅我的新 [**YouTube 频道**](https://www.youtube.com/c/themlphdstudent) 。**
*   **在我的 [**邮箱列表**](https://tinyletter.com/themlphdstudent) 报名。**

**如果你错过了我的前一部分系列。**

*   **第 0 天:[挑战介绍](https://medium.com/@durgeshsamariya/100-days-of-machine-learning-code-a9074e1c42c3)**
*   **第 1 天: [Python 基础— 1](https://medium.com/the-innovation/python-basics-variables-data-types-and-list-59cea3dfe10f)**
*   **第 2 天: [Python 基础知识— 2](https://towardsdatascience.com/python-basics-2-working-with-list-tuples-dictionaries-871c6c01bb51)**
*   **第三天: [Python 基础知识— 3](https://medium.com/towards-artificial-intelligence/python-basics-3-97a8e69066e7)**

**我希望你会喜欢我的其他文章。**

*   **[八月月度阅读清单](https://medium.com/@durgeshsamariya/august-2020-monthly-machine-learning-reading-list-by-durgesh-samariya-20028aa1d5cc)**
*   **[集群资源](https://medium.com/towards-artificial-intelligence/a-curated-list-of-clustering-resources-fe355e0e058e)**