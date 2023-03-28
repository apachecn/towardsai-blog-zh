# Python 中的解包是什么

> 原文：<https://pub.towardsai.net/what-is-unpacking-in-python-5bd22954ce4d?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)， [Python](https://towardsai.net/p/category/programming/python)

## 通过示例了解 Python 中的解包

![](img/9d8cce180d06651f6d6f9d8647f00469.png)

由[卡罗琳娜·格拉博斯卡](https://www.pexels.com/@karolina-grabowska)在[像素上拍摄的照片](https://www.pexels.com/photo/cardboard-boxes-on-dark-surface-against-white-wall-4498122/)

在这篇文章中，我们将经历`unpacking`、`extended unpacking`、&、`nested unpacking`。让我们开始吧。

# 拆包

将打包的值拆分成单个元素的过程称为“`unpacking`”。打包的值是`strings, lists, tuples, sets, and dictionaries`。

在拆包过程中，来自`RHS`(右手侧)的元件被拆分到它们在`LHS`(左手侧)上的相对位置。我们将在下面的例子中看到这是如何工作的。

正如我们从下面两个例子中看到的，来自`RHS`的元素根据相对位置被解包到`LHS`的变量中。

## 示例 1:使用列表、元组和字符串

## 示例 2:使用集合与字典

因为`sets` & `dictionaries`是元素的无序集合，所以不保证每次解包都会给出相同的结果，不像字符串、列表和元组是元素的有序集合。注意，对于`dictionary`型，拆包是在键上完成的。

> **提示**:由于集合&字典是一个无序的元素集合，所以不推荐使用它们来解包，因为不能保证结果的顺序。

# 扩展的可迭代解包

扩展的可迭代解包通过操作符 ***和**** 完成。

## *操作员

有时候我们不想拆开所有的元素。我们可能只对解包第一个元素或最后一个元素感兴趣，并将其余元素放入一个变量中。这可以在 ***** 操作员的帮助下实现。

> **注** : *运算符只能在赋值运算符的 LHS 上使用一次，除非用于嵌套解包。

**例 3:使用列表、元组、字符串**

**示例 4:使用集合与字典**

## ****操作员**

从上面的例子中您已经注意到，*操作符遍历字典中的键。如果我们想要遍历`**key-value**`对，那么我们必须使用`**** operator**`。

> **注意** : **运算符不能用在赋值运算符的 LHS 上。

**例 5:使用字典**

# 嵌套拆包

我们刚刚经历的解包和扩展解包的概念也适用于嵌套解包。唯一的区别就是顾名思义，它是嵌套的。让我们看看例子:

**例 6:** **使用列表，元组&字符串**

# 结论

希望你已经理解了 Python 中的解包是什么，以及它是如何工作的。

如果您有兴趣了解更多关于 Python 的知识，这里有一些您可能会喜欢的文章:

1.  [**如何使用 Python 进行 and while 循环**](https://towardsdatascience.com/how-to-use-python-for-and-while-loops-6a6a3325929c)
2.  [**Python 中的优化—实习**](https://towardsdatascience.com/optimization-in-python-interning-805be5e9fd3e)
3.  [**Python 中的优化—窥视孔**](https://towardsdatascience.com/optimization-in-python-peephole-e9dc84cc184d)
4.  [**Python 中的可变性和不变性**](https://towardsdatascience.com/mutability-immutability-in-python-b698bc592cbc)

*阅读更多关于 Python 和数据科学的此类有趣文章，* [***订阅***](https://pythonsimplified.com/) *到我的博客*[***www.pythonsimplified.com***](http://www.pythonsimplified.com/)***。*** 你也可以在 [**LinkedIn**](https://www.linkedin.com/in/chetanambi/) 上联系我。