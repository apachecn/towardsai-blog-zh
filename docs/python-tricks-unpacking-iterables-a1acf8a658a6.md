# Python 技巧:解包 Iterables

> 原文：<https://pub.towardsai.net/python-tricks-unpacking-iterables-a1acf8a658a6?source=collection_archive---------2----------------------->

![](img/ffa8b9cf515d15ef09b7f3e8ce290927.png)

克劳迪奥·施瓦茨在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

## [编程](https://towardsai.net/p/category/programming)

## 你并不总是需要指数

欢迎阅读一系列短文，每篇短文都有方便的 Python 技巧，可以帮助你成为更好的 Python 程序员。在这篇博客中，我们将探讨如何解包 iterables。

## 你不需要指数。

假设你有一个元组`("a", "b", "c")`。

如果您想将第一个元素分配给`a`，将第二个元素分配给`b`，将第三个元素分配给`c`，您实际上不需要使用索引:

```
# Don't do this
t = ("a", "b", "c")
a = t[0]
b = t[1]
c = t[2]# Do this instead
t = ("a", "b", "c")
a, b, c = t
```

事实上，这不仅仅适用于元组:

```
a, b, c = [0, 1, 2]              # List
a, b, c = "abc"                  # String
a, b, c = range(3)               # Range
a, b, c = (i for i in range(3))  # Generator
a, b, c = iter([0, 1, 2])        # Iterator
a, b, c = {0, 1, 2}              # Set
a, b, c = {0: 0, 1: 1, 2: 2}     # Dictionary
```

在上述各项中，集合和字典的行为略有不同:

1.  Sets:解包的顺序可能不会被保留，并且会相对于元素的散列(尝试`a, b, c = {3, 2, 1}`来测试自己)
2.  字典:被解包的是键，而不是值，键的顺序和它被创建时一样

## 解包时跳过值并对其分组

上面所有的例子都有需要解包的元素的确切数目(例如`[0, 1, 2]`有 3 个元素需要解包到 3 个变量`a, b, c`)。如果列表是`[0, 1, 2, 3, 4, 5, 6]`，但是我们只需要值`0`、`1`和`6`怎么办？

我们仍然可以使用拆包:

```
a, b, *_, c = [0, 1, 2, 3, 4, 5, 6]
```

在这个例子中，有两个重要的要点:

1.  `_`习惯用作废弃变量/虚拟变量
2.  `*`是一个运算符，用于解包所有尚未赋值的值。这意味着在确定给`*`(本例中为`_`)后面的变量分配多少个值之前，会优先分配其他变量

但是坚持住。如果我们的列表只有三个元素呢？

```
a, b, *_, c = [0, 1, 2]a # 0
b # 1
c # 2
_ # []
```

因为在我们的例子中，值将被优先分配给`a`、`b`和`c`，所以它们中的每一个都将获得一个值，这样就不会留下任何值分配给`_`。默认情况下，`_`它将成为一个空列表。

## 开箱限制

虽然拆包看起来很整洁，但它也有一些关键的限制:

1.  iterable 的长度≥非星号变量的数量。否则你会得到`ValueError: not enough value to unpack`
2.  只能有 1 个`*`变量。否则你会得到`SyntaxError: multiple starred expression in assignment`

这篇博文就讲到这里吧！我希望你已经发现这是有用的。如果你对其他 Python 技巧感兴趣，我为你整理了一份简短博客列表:

*   [Python 技巧:拉平列表](https://towardsdatascience.com/python-tricks-flattening-lists-75aeb1102337)
*   [Python 技巧:如何检查与熊猫的表格合并](https://towardsdatascience.com/python-tricks-how-to-check-table-merging-with-pandas-cae6b9b1d540)
*   [Python 技巧:简化 If 语句&布尔求值](https://towardsdatascience.com/python-tricks-simplifying-if-statements-boolean-evaluation-4e10cc7c1e71)
*   [Python 技巧:对照单个值检查多个变量](https://towardsdatascience.com/python-tricks-check-multiple-variables-against-single-value-18a4d98d79f4)

如果你想了解更多关于 Python、数据科学或机器学习的知识，你可能想看看这些帖子:

*   [改进数据科学工作流程的 7 种简单方法](https://towardsdatascience.com/7-easy-ways-for-improving-your-data-science-workflow-b2da81ea3b2)
*   [熊猫数据帧上的高效条件逻辑](https://towardsdatascience.com/efficient-implementation-of-conditional-logic-on-pandas-dataframes-4afa61eb7fce)
*   [常见 Python 数据结构的内存效率](https://towardsdatascience.com/memory-efficiency-of-common-python-data-structures-88f0f720421)
*   [Python 的并行性](https://towardsdatascience.com/parallelism-with-python-part-1-196f0458ca14)
*   [数据科学的基本 Jupyter 扩展设置](https://towardsdatascience.com/cookiecutter-plugin-for-jupyter-easily-organise-your-data-science-environment-a56f83140f72)
*   [Python 中高效的根搜索算法](https://towardsdatascience.com/mastering-root-searching-algorithms-in-python-7120c335a2a8)

如果你想了解更多关于如何将机器学习应用于交易和投资的信息，这里有一些你可能感兴趣的帖子:

*   [Python 中用于交易策略优化的遗传算法](/genetic-algorithm-for-trading-strategy-optimization-in-python-614eb660990d)
*   [遗传算法——停止过度拟合交易策略](https://medium.com/towards-artificial-intelligence/genetic-algorithm-stop-overfitting-trading-strategies-5df671d5cde1)
*   [人工神经网络选股推荐系统](/ann-recommendation-system-for-stock-selection-c9751a3a0520)

[](https://www.linkedin.com/in/louis-chan-b55b9287) [## Louis Chan—FTI Consulting | LinkedIn 数据科学总监

### 雄心勃勃的，好奇的和有创造力的个人，对分支知识和知识之间的相互联系有强烈的信念

www.linkedin.com](https://www.linkedin.com/in/louis-chan-b55b9287)