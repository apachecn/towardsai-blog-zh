# Python 中的字符串方法有助于文本处理

> 原文：<https://pub.towardsai.net/programming-14b6b5c43a5d?source=collection_archive---------1----------------------->

## [编程](https://towardsai.net/p/category/programming)

## string 类提供了各种与文本相关的内置方法

![](img/ef52817d63e9ab1027bed7a4046cb1b9.png)

由[蒂姆·莫斯霍尔德](https://unsplash.com/@timmossholder?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

本文将带您深入了解在机器学习项目的各种文本处理任务中使用的内置字符串方法。

字符串方法有助于在这些方法的帮助下实现序列操作。

让我们看看 python 的 string 类中使用的所有 string 方法。

首先，将一个字符串赋给一个变量，该变量将是 string 类的一个实例或对象。

```
a = 'happyworld'#check the type of object 'a'
print(type(a))**#output:**
<class 'str'>
```

*   **大写**

在这个方法中，字符串以首字母大写返回。

```
a.capitalize()**#output:**
'Happyworld'
```

*   **文件夹**

这种方法将使字符串小写，但在一个非常强大的方式。如果我们举一个例子，所有单词的第一个字母都有一个大写字母，这将使它们变成小写字母。

```
text = "Amit Is Happy"
a = text.casefold()
print(a)**#output:**
amit is happy
```

*   **居中**

此方法将在文本前后添加填充。例如，如果我们给定填充为“10 ”,单词的长度为“4 ”,那么它将在文本前添加“3”个空格，在文本后添加“3”个空格。

```
text = "Ball"
a = text.center(10)
print(a)**#output:**
   Ball#The second argument to fill the padding with specific charactertext = "Ball"
a = text.center(10, '-')
print(a)**#output:**
---Ball---
```

[](/class-and-objects-in-python-with-examples-591c6ca95ee6) [## Python 中的类和对象及其示例

### 软件开发程序的便捷概念

pub.towardsai.net](/class-and-objects-in-python-with-examples-591c6ca95ee6) [](/why-map-filter-and-reduce-functions-are-so-famous-4c8e42fd0755) [## 为什么 Map()、Filter()和 Reduce()函数这么出名？

### python 中避免循环和分支的函数式编程

pub.towardsai.net](/why-map-filter-and-reduce-functions-are-so-famous-4c8e42fd0755) 

*   **计数**

它将计算我们在 count 方法中作为参数给出的字母或单词。

```
text = "Amit is Happy"
a = text.count("i")
print(a)**#output:**
2#Counting "i" between the given lengthtext = "Amit is Happy"
a = text.count("i", 0, 10)
print(a)**#output:**
2
```

*   **编码**

此方法将对文本中的特殊字符进行编码。我们将观察到“A”符号是不同的，并且该方法在输出中给出了编码的“A”。

```
text = " Άmit "
a = text.encode()
print(a)**#output:**
b' \xce\x86mit '
```

*   **结束于**

这个方法将给定的文本与带或不带结尾的字符串进行比较。我们在下面的代码中看到字符串以“.”结尾方法中给出的要比较的。

```
text = "Amit is Happy."
a = text.endswith(".")
print(a)**#output:**
True#To check with given index locationstext = "Amit is Happy."
a = text.endswith("Happy.", 4, 10)
print(a)**#output:**
False
```

*   **找到**

此方法用于在字符串中查找字母或单词。下面的代码将给出字母“I”在字符串中第一次出现的索引位置。

```
text = "Amit is Happy."
a = text.find("i")
print(a)**#output:**
2           #means the first 'i' at position '2'.#What if the letter is not in the string. It will return '-1'text = "Amit is Happy."
a = text.find("z")
print(a)**#output:**
-1
```

*   **加入**

这用于在字符串之间插入一些符号。

```
lst = ["Amit", "is", "Happy"]
a = "-".join(lst)
print(a)**#output:**
Amit-is-Happy
```

*   **lstrip**

此方法用于去除或移除字符串左侧的所有字符或符号。在下面的代码中，可以清楚地看到 lstrip 方法删除了'**、**、 **@** 、 **#** 、'**。**符号。

```
text = ",,,,,@###@.....Amit"
a = text.lstrip(", . @ #")
print(a)#output:
Amit
```

*   **rsplit**

这是用来分隔带有特定符号的单词并返回一个列表。

```
text = "Amit, is, Happy"
a = text.rsplit(",")
print(a)**#output:**
['Amit', 'is', 'Happy']#to get a list with specific elements
text = "Amit, is, Happy"
a = text.rsplit(",", 0)
print(a)**#output:**#with value 0, it return one element in the list
['Amit, is, Happy']#with value 1, it return two elements in the list
['Amit, is', ' Happy']
```

## 结论

这些是最常用的基本字符串方法，请尝试找到更多的字符串方法来练习。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —零到英雄用 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)
3。[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[为什么 LSTM 在深度学习方面比 RNN 更有用？](/deep-learning-88e218b74a14?source=friends_link&sk=540bf9088d31859d50dbddab7524ba35)
5。[神经网络:递归神经网络的兴起](/neural-networks-the-rise-of-recurrent-neural-networks-df740252da88?source=friends_link&sk=6844935e3de14e478ce00f0b22e419eb)
6。[用 Python 充分解释了线性回归](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[concat()、merge()和 join()与 Python](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
9 的区别。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)