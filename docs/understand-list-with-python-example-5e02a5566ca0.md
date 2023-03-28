# 通过 Python 示例了解 List[]

> 原文：<https://pub.towardsai.net/understand-list-with-python-example-5e02a5566ca0?source=collection_archive---------1----------------------->

## [编程](https://towardsai.net/p/category/programming)

## python 中数据结构的便捷概念

![](img/7f01e1c86595c72b406e74d3fac690a2.png)

在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上[的照片](https://unsplash.com/@ffstop?utm_source=medium&utm_medium=referral)

列表是元素的有序集合。它在一个变量中存储多个值。列表可以包含任何数据类型的元素，如字符串和整数等。列表中的元素放在方括号([])中。列表可以包含相同类型、不同类型或重复的元素。

**关于如何使用列表有不同的方法，让我们来看几个:**

> ***创建列表***

创建列表非常简单。在一个列表中，我们必须总是提到一个变量来存储元素。让我们看看创建列表的一些类型:

```
**1\. Creating empty list**a = []**2\. Creating an integer/ string list**a = [1, 2, 3, 4]**3.Creating a mixed list**a = [5, “hello”, 65, “welcome”]**4\. Creating a nested list**a = [5, 8 , 3, [“hello”, “hi”], 45]
```

**解释:**上面的例子陈述了一个简单列表的例子，其中所有的元素都存储在变量“a”中。

> ***访问列表***

我们已经创建了一个列表。但是现在我们希望只显示或打印所需的内容作为输出。索引是做到这一点的方法。列表中的每个元素都有一个索引值，使用该值可以访问列表中的元素。有两种类型的索引，积极和消极的。让我们深入探讨每一个问题。

1.  **正向分度**

正索引意味着从左到右访问列表中的元素。这里，索引从“0”开始。让我们用一个简单的例子来探讨这个概念:

```
a = [1, 3, 5, 8, “Hello”]
     **↑  ↑  ↑  ↑     ↑
     0  1  2  3     4**print(a[0])
print(a[4])**Output:** 1
Hello
```

**解释:**在上面列举的“一”中，有五个元素。这里，索引值从“0”(从左到右)开始，以“4”结束。

*   在第一个 print 语句中，输出将显示为 1，因为“a[0]”意味着我们正在访问一个索引值为“0”的元素。同样的过程也适用于第二个语句。

**2。负步进**

负索引意味着列表中的元素是从右向左访问的。这里，索引从“-1”开始。让我们用一个简单的例子来探讨这个概念:

```
a = [1, 2, 5, 4, “welcome”]
    ** ↑  ↑  ↑  ↑      ↑
   -5  -4  -3 -2    -1**print(a[-1])
print(a[-3])**Output:** welcome
5
```

**解释:**

这里我们可以看到一个列表也可以从右向左访问。在第一个 print 语句中，输出将显示为“welcome”，因为“a[-1]”意味着我们正在访问索引值为“-1”的元素。这也适用于第二个打印声明。

**3。嵌套索引**

嵌套索引与上面的概念相似。让我们看一个例子:

```
a = [“atom”, “cell”, [1, 2, 3]]
       ↑       ↑         ↑
       0       1         2print(a[0][3])
print([2][0])**Output:** m
1
```

**解释:**

在第一个 print 语句中，“a[0][3]”意味着我们正在访问分配在第 0 个位置的元素，即“atom”换句话说，我们正在访问一个索引为“3”的元素，它是字母“m ”,这同样适用于第二条语句。

**4。切片列表**

列表被分割以访问一系列元素。“:”符号在这里用于指定必须被访问的元素的范围。让我们用一个简单的例子来探讨这个概念:

```
a = [“toy”, “lock”, 23, 65, 89]print(a[0:2])
print(a[:-2])
print(a[2:])
print(a[:])**Output:** [‘toy’, ‘lock’, 23]
[‘toy’, ‘lock’, 23]
[23, 65, 89]
[“toy”, “lock”, 23, 65, 89]
```

**解说:**

上面的程序展示了从一个列表中访问一系列元素的不同方法。

*   第一个 print 语句从索引位置 0–2 打印列表。
*   第二个 print 语句打印列表中除最后两个元素之外的所有元素。
*   第三个 print 语句从位置 2 开始打印列表中的所有元素。
*   第四个 print 语句打印列表中的所有元素。

[](/python-zero-to-hero-with-examples-c7a5dedb968b) [## Python:从零到英雄(带示例)

### python 初学者手册指南

pub.towardsai.net](/python-zero-to-hero-with-examples-c7a5dedb968b) 

> ***添加/修改列表***

在一个列表中，如果需要添加一个元素，没有必要手工添加。可以使用 python 程序将元素添加到列表中。让我们了解如何:

```
a = [56, 78, 99]
a[1] = “hello”
print(a)a.append(4)
print(a)a.extend([5, 6, 77])
print(a)**Output:** [56, “hello”, 99]
[56, “hello”, 99, 4]
[56, “hello”, 99, 5, 5, 6, 77]
```

**解释:**

在第一段代码中，单词“hello”被索引值 1 中的 78 替换。对于这个列表，值“4”被添加到列表的末尾(第二段代码)。接下来，列表“[5，6，7]”被添加到代码片段中列表的末尾。

> ***删除或移除列表项***

如果需要删除列表中的元素，就没有必要手动执行。列表中不需要的元素可以使用 python 程序移除。让我们用一个例子来理解:

```
a = [45, 89, 67, 88, 65,45]del a[2]
print(a)del a[2:4]
print(a)del a
print (a)**Output:** [45, 89, 88, 65, 45]
[45, 89]Traceback (most recent call last):
   File “<string>”, line 9, in <module>
NameError: name ‘a’ is not defined
```

**说明:**

在第一个程序中，索引值为“2”的元素将被删除。现在从这个删除列表中，索引位置 2 到 4 的元素将被删除。现在，最后一段代码删除了列表中剩下的所有元素。

> ***列出方法***

python 中使用的列表方法有 append()、extend()、clear()等。这些方法也使得程序更容易理解。让我们用几个例子来看看这些方法:

1.  append():append()方法将一个元素添加到列表的末尾

**程序:**

```
a = [‘e’, ‘l’, ‘i’, ’n’, ‘o’, ‘s’, ‘u’]a.append([‘k’, ‘i’, ’n’, ‘g’])
print(a)**Output:** [‘e’, ‘l’, ‘i’, ’n’, ‘o’, ‘s’, ‘u’, [‘k’, ‘i’, ’n’, ‘g’]]
```

**2。extend():**extend()方法将任意数量的指定元素列表添加到列表的末尾。

**程序:**

```
a = [‘p’, ‘l’, ‘a’, ’n’, ‘t’, ‘s’, ‘s’]a.extend([‘k’, ‘i’, ’n’, ‘g’])
print(a)**Output:** [‘p’, ‘l’, ‘a’, ’n’, ‘t’, ‘s’, ‘s’, ‘k’, ‘i’, ’n’, ‘g’]
```

**3。clear():**clear()方法删除列表中的所有元素。

**程序:**

```
a = [‘t’, ‘o’, ‘y’]
a.clear()**Output:** []
```

**4。remove():**remove()方法从列表中删除一个元素/项目。

**程序:**

```
a = [‘t’, ‘o’, ‘y’]
a.remove(‘y’)print(a)**Output:** [‘t’, ‘o’]
```

**5。pop():**pop()方法从列表或给定的索引值中移除并返回最后一个值。

**节目:**

```
a = [‘t’, ‘o’, ‘y’, ‘s’]print(a.pop(3))**Output:** s
```

**6。insert():**insert()方法在定义的索引处插入一个元素。

**程序:**

```
num = [34, 35, 37]num.insert(2, 36)
print(num)**Output:** [34, 35, 36, 37]
```

**7。index():**index()方法返回列表中第一个匹配的元素。

**程序:**

```
num = [34, 35, 38]print(num.index(38))**Output:** 2
```

**8。count():**count()方法返回作为参数传递的元素数量。

**程序:**

```
d = [1,2,3,4,3,5,3]print(d.count(3))**Output:** 3
```

**9。sort():**sort()方法按升序对列表进行排序。

**程序:**

```
r = [5,66,3,8,1]r.sort()
print(r)**Output:** [1, 3, 5, 8, 66]
```

10。reverse():reverse()方法颠倒列表中元素的顺序。

**程序:**

```
e = [1, 3, 5, 8, 66]e.reverse()
print(e)**Output:** [66, 8, 5, 3, 1]
```

> ***列表会员测试***

列表成员测试是检查定义的元素是否存在于列表中的测试。

**程序:**

```
animal = [ ‘a’, ’n’, ‘i’, ‘t’, ‘a’, ‘l’, ‘y’]print(‘a’ in animal)
print(‘b’ in animal)**Output** True
False
```

**说明:**

在上面的程序中，第一条语句检查元素“a”是否出现在列表中。因为在列表中找到了' a ',所以它将输出返回为 True。类似的过程也适用于第二个语句。

[](/become-a-data-scientist-in-2021-with-these-following-steps-5bf70a0fe0a1) [## 按照以下步骤，在 2021 年成为一名数据科学家

### 走上数据科学家之路需要具备的基本点

pub.towardsai.net](/become-a-data-scientist-in-2021-with-these-following-steps-5bf70a0fe0a1) 

> ***迭代使用列表***

使用列表的迭代意味着使用“for”循环。for 循环有助于多次打印语句。让我们用一个简单的例子来探讨这个概念:

```
for animal in ["Tiger", "Lion", "Hyena", "Zebra"]:
    print(animal, “is an animal”)**Output:** Tiger is an animal
Lion is an animal
Hyena is an animal
Zebra is an animal
```

**说明:**以上程序是循环程序(使用 for 循环)。在这里，程序打印输出，直到它到达列表的末尾。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —零到英雄与 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)3 .[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[为什么 LSTM 在深度学习方面比 RNN 更有用？](/deep-learning-88e218b74a14?source=friends_link&sk=540bf9088d31859d50dbddab7524ba35)
5。[神经网络:递归神经网络的兴起](/neural-networks-the-rise-of-recurrent-neural-networks-df740252da88?source=friends_link&sk=6844935e3de14e478ce00f0b22e419eb)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[concat()、merge()和 join()与 Python](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
的区别 9。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)