# 如何用字符串调用 Python 函数？

> 原文：<https://pub.towardsai.net/python-trick-how-to-call-a-function-by-its-name-f35309469c66?source=collection_archive---------0----------------------->

![](img/5085c07df1f8c35224cafdfe7f289b5e.png)

詹姆斯·哈里森在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

## Methodcaller、Get 属性、名称空间等等

欢迎阅读一系列短文，每篇都有可以帮助你提高游戏水平的 Python 技巧。在这篇博客中，我们将研究如何通过名字调用一个函数。

## 情况

假设你有一个函数`def f(): pass`。

可以只用`"f"`调用函数吗？

## 解决方案 1:本地和全球

在我们深入研究`locals`和`globals`之前，了解一下什么是名称空间是很重要的。在 Python 运行时，所有定义的对象(类、函数、变量等。)被映射并存储在一个字典中，也称为命名空间。

`locals()`返回局部级别的名称空间——比如，函数中定义的局部变量，这些变量将成为函数中局部名称空间的一部分。

`globals()`返回全局级别的名称空间——比如，全局导入的模块或全局定义的对象，它们将成为全局名称空间的一部分，无论它在函数内部还是外部。

假设有一个函数名为`my_function`。

```
def my_function(a, b, c):
  pass
```

使用`locals`和`globals`调用带有`"my_function"`的功能:

```
s = "my_function"# calling the function from local namespace
function = locals()[s]
function(a=1, b=2, c=3)# calling the function from global namespace
function = globals()[s]
function(a=1, b=2, c=3)
```

## 解决方案 2:评估

下一个选项是众所周知的`eval`，这是一个内置的 python 函数，它计算任意字符串表达式/编译后的代码，如果它是一个**合法的** Python 表达式就执行。

```
eval(expression[, globals[, locals]])
```

要使用`eval`，您最多只需要三个参数:

*   Expression:要计算的字符串表达式/编译代码
*   Globals:为`eval`提供全局名称空间的可选字典
*   Locals:为`eval`提供本地名称空间的可选字典

> 当提供全局变量和局部变量时，它们就是`eval`运行所基于的名称空间。否则，`eval`将使用当前代码所基于的全局和局部名称空间。

## 解决方案 3:方法调用方

另一种方法(没有双关语)是在 Python 的一个标准库中— `operator.methodcaller`。与上面的选项不同，`methodcaller`从提供的对象中获取一个可调用的**。因此，以下内容将不起作用:**

```
from operator import methodcaller# This would not work!!
bar = methodcaller("myfunction")
bar()
```

相反，可调用的需要是对象的一部分:

```
from operator import methodcaller
foo = "bar"# upper is a method of a string object
foo_method = methodcaller("upper")
foo_method(foo)>>> 'BAR'
```

`methodcaller`和其他选项的另一个关键区别是，任何论据都需要提前提供。例如:

```
from operator import methodcaller
import random# This doesn't work
foo_method = methodcaller("randint")
foo_method(random)>>> TypeError: randint() missing 2 required positional arguments: 'a' and 'b'# This doesn't work either
foo_method = methodcaller("randint")
foo_method(random, a=1, b=2)>>> TypeError: methodcaller() takes no keyword arguments# This works!
foo_method = methodcaller("randint", a=1, b=2)
foo_method(random)>>> 1
```

因此，要使用`methodcaller`，您首先需要注意:

*   方法的位置(例如，该方法在哪个模块/类下)
*   使用该方法是否需要参数

## 解决方案 4:获取属性

就像`operator.methodcaller`，`getattr`是另一个选项，需要预先知道方法所在的位置。也就是说，两个选项有两个主要区别:
1。`getattr`不限于获取可调用的。使用它时，一定要注意返回的对象是否可调用。
2。`getattr`允许您将参数传递给返回的方法，而`methodcaller`要求您事先提供参数。

```
import randombar = getattr(random, 'randint')
result = bar(1, 2)
>>> 2
```

## 结束语

你能做并不意味着你应该做。

允许脚本的用户使用用户提供的字符串来指定它的行为会导致一些不良的安全漏洞。其他一些臭名昭著的安全漏洞源于将非参数化数据视为代码，包括 XSS 和 SQL 注入。也就是说，Python 本身是一种解释型语言，这意味着可以说，人们可以做出更低级的改变，从而产生更大的漏洞。

简而言之，在本教程中，我们已经走过了使用字符串调用方法的四种方式。作为快速修订，以下表格总结了他们的行为:

这篇博文就讲到这里吧！我希望你已经发现这是有用的。如果你喜欢这本书，别忘了留下一些掌声，甚至使用我的推荐链接加入媒体(不需要额外付费)。

[](https://louis-chan.medium.com/membership) [## 通过我的推荐链接加入灵媒&路易·陈

### 阅读路易·陈的每一个故事(以及媒体上成千上万的其他作家)。您的会员费直接支持…

louis-chan.medium.com](https://louis-chan.medium.com/membership) 

如果你对其他 Python 技巧感兴趣，我为你整理了一份简短博客列表:

*   [Python 技巧:解包 Iterables](/python-tricks-unpacking-iterables-a1acf8a658a6)
*   [Python 技巧:拉平列表](https://towardsdatascience.com/python-tricks-flattening-lists-75aeb1102337)
*   [Python 技巧:如何检查与熊猫的表格合并](https://towardsdatascience.com/python-tricks-how-to-check-table-merging-with-pandas-cae6b9b1d540)
*   [Python 技巧:简化 If 语句&布尔求值](https://towardsdatascience.com/python-tricks-simplifying-if-statements-boolean-evaluation-4e10cc7c1e71)
*   [Python 技巧:对照单个值检查多个变量](https://towardsdatascience.com/python-tricks-check-multiple-variables-against-single-value-18a4d98d79f4)

如果你想了解更多关于如何将机器学习应用于交易和投资的信息，这里有一些你可能感兴趣的帖子:

*   [Python 中用于交易策略优化的遗传算法](/genetic-algorithm-for-trading-strategy-optimization-in-python-614eb660990d)
*   [遗传算法——停止过度拟合交易策略](https://medium.com/towards-artificial-intelligence/genetic-algorithm-stop-overfitting-trading-strategies-5df671d5cde1)
*   [人工神经网络选股推荐系统](/ann-recommendation-system-for-stock-selection-c9751a3a0520)

[](https://www.linkedin.com/in/louis-chan-b55b9287) [## Louis Chan -数据和分析副总监-毕马威英国| LinkedIn

### 雄心勃勃的，好奇的和有创造力的个人，对分支知识和知识之间的相互联系有强烈的信念

www.linkedin.com](https://www.linkedin.com/in/louis-chan-b55b9287)