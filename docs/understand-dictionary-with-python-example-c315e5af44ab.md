# 用 Python 例子理解字典{}

> 原文：<https://pub.towardsai.net/understand-dictionary-with-python-example-c315e5af44ab?source=collection_archive---------2----------------------->

## [编程](https://towardsai.net/p/category/programming)

## python 中数据结构的便捷概念

![](img/33c008cded7f0903d156a63b106e8844.png)

由[阿尔瓦罗·雷耶斯](https://unsplash.com/@alvarordesign?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

字典是由逗号分隔在大括号“{}”内的项目的无序集合。字典中的条目总是以键值对的形式出现。字典中的值使用各自的键显示。字典中的值可以重复，并且可以是任何数据类型。但是，一把钥匙永远不会重现。(它必须有唯一的值)。

> ***创建字典***

1.  **创建空字典**

```
Dictionary = {}print(Dictionary)**Output:** {}
```

**2。使用整数键创建字典**

```
D = {1: ‘lion’, 2: ‘tiger’, 3: ‘zebra’}print(D)**Output:** {1: ‘lion’, 2: ‘tiger’, 3: ‘zebra’}
```

**3。使用组合键创建字典**

```
D = {‘animal’: ‘tiger’, 4: [1, 2, 3]}print(D)**Output:** {‘animal’: ‘tiger’, 4: [1, 2, 3]}
```

**4。使用 Dict()函数创建字典**

```
D = dict({1: ‘lion’, 2: ‘tiger’, 3: ‘zebra’})print(D)**Output:** {1: ‘lion’, 2: ‘tiger’, 3: ‘zebra’}
```

> ***查阅字典***

1.  **使用[]** 访问字典

```
d = {‘animal’: ‘tiger’, ‘ani’: ‘zebra’}print(d[‘animal’])**Output:** tiger
```

**解释:**

这里的'[]'是定义要访问的键。在上面的程序中，我们已经定义了‘animal’来从字典中访问。该键的值就是输出(tiger)。

**2。使用 get()** 访问字典

```
p = {‘animal’: ‘tiger’, ‘ani’: ‘zebra’}print(p.get(‘ani’))**Output:** Zebra
```

**解释:**

get()函数执行与“[]”相同的功能。唯一的区别是书写的方式。

> ***修改/添加字典元素***

1.  **更新字典**

```
S = {‘color1’: ‘pink’, ‘color2’: ‘red’}S[‘color1’] = ‘green’**Output:** {‘color1’: ‘green’, ‘color2’: ‘red’}
```

**解释:**

这里，程序将把字典中的颜色“粉色”更新为“绿色”。因此，我们将“颜色 1”指定为绿色。输出显示了所做的更新。

**2。向词典添加条目:**

```
S = {‘color1’: ‘green’, ‘color2’: ‘red’}S[‘color3’] = ‘yellow’**Output:** {‘color1’: ‘green’, ‘color2’: ‘red’, ‘color3’: ‘yellow’}
```

**说明:**

这里，程序将向字典中添加另一个键值对。因此，我们为新键“color3”分配一个新值“yellow”。输出显示了添加的键值对。

[](/python-zero-to-hero-with-examples-c7a5dedb968b) [## Python:从零到英雄(带示例)

### python 初学者手册指南

pub.towardsai.net](/python-zero-to-hero-with-examples-c7a5dedb968b) [](/become-a-data-scientist-in-2021-with-these-following-steps-5bf70a0fe0a1) [## 按照以下步骤，在 2021 年成为一名数据科学家

### 走上数据科学家之路需要具备的基本点

pub.towardsai.net](/become-a-data-scientist-in-2021-with-these-following-steps-5bf70a0fe0a1) 

> ***删除字典元素***

1.  **pop():**pop()函数返回指定要从字典中删除的值。pop 功能一次只允许删除一个项目。

**程序:**

```
R = {1: ’n’, 2: ‘f’, 3: ‘w’, 4: ‘y’, 5: ‘i’}print(R.pop(3))
print(R)**Output:** w
{1: ’n’, 2: ‘f’, 4: ‘y’, 5: ‘i’}
```

**2。pop item():**pop item()方法返回字典中的最后一个值。

**节目:**

```
R = {1: ’n’, 2: ‘f’, 4: ‘y’, 5: ‘i’}print(R.popitem())
print(R)**Output:** (5, ‘i’)
{1: ’n’, 2: ‘f’, 4: ‘y’}
```

**3。clear():**clear()函数从字典中删除所有的条目，使它们为空。

**程序:**

```
R = {1: ’n’, 2: ‘f’, 4: ‘y’}print.clear()**Output:** {}
9
```

**4。del**:‘del’删除整个字典。

**程序:**

```
R = {1: ’n’, 2: ‘f’}del Rprint(R)**Output:** Traceback (most recent call last):
    File “<string>”, line3, in <module>
       print(R)
NameError: name ‘R’ is not defined
```

> ***字典方法***

字典中有几种方法，其中一些已经被详细研究过了。以下是探索的一些方法:

1.  **items():**items()方法以键值格式返回字典中存在的条目的新对象。

**程序:**

```
P = {0:’tiger’, 1:’lion’, 2:’zebra’}for i in P.items():
    print(i)**Output:** (0, ‘tiger’)
(1, ‘lion’)
(2, ‘zebra’)
```

**2。keys():**keys()方法，返回字典中存在的所有字典键。

**程序:**

```
Y = {‘tiger’: ‘a’, ‘lion’: ‘b’, ‘zebra’: ‘c’}print(Y.keys())**Output:** dict_keys([‘tiger’, ‘lion’, ‘zebra’])
```

> ***字典成员测试***

字典中使用的成员测试类似于其他数据结构。它检查定义的元素是否存在于集合中。如果元素出现在集合中，它将输出返回 true，否则将输出返回 false。

**注意**成员测试只针对键，不针对值。

**程序:**

```
Test = {1: 34, 2: 23, 3: 56, 4: 99, 5: 55}print(1 in Test)
print(3 not in Test)
print(7 in Test)**Output:** True
False
False
```

**解释:**

*   在第一个 print 语句中，要求检查字典中是否存在键“1”。由于密钥存在，它将输出返回 true。
*   在第二个 print 语句中，要求检查字典中是否不存在键“3”。我们可以观察到定义的键出现在字典中。因此，输出被返回为 false。
*   在第三条语句中，要求检查字典中是否存在键“7”。因为键不存在，所以它将输出返回 false。

> ***迭代使用字典***

**程序:**

```
R = {1: ’n’, 2: ‘f’, 4: ‘y’, 5: ‘i’}for d in R:
    print(R[d])**Output:** n
f
y
i
```

**说明:**

在上面的例子中，打印了字典的每个键值。即,“for”循环一直执行程序，直到没有元素剩下为止。

> ***一些内置函数使用字典***

1.  **all():** 只有当一个字典的所有键都为真时，all()函数才返回输出。如果字典为空，它也返回 true。

**程序:**

```
P = {1: ’n’, 2: ‘f’, 4: ‘y’, 5: ‘i’}print(all(P))**Output:** True
```

**2。any():** 如果字典中的任意键为真，any()函数返回值为真。此外，如果字典为空，它将返回值 false。

**程序:**

```
P = {}print(any(P))**Output:** False
```

**3。sorted():**sorted()函数以排序的形式返回字典中的值。

**程序:**

```
P = {1: 34, 2: 23, 3: 56, 4: 99, 5: 55}print(sorted(squares))**Output:** [23, 34, 55, 56, 99]
```

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —用 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2 从零到英雄。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)
3 .[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[为什么 LSTM 在深度学习方面比 RNN 更有用？](/deep-learning-88e218b74a14?source=friends_link&sk=540bf9088d31859d50dbddab7524ba35)
5。[神经网络:递归神经网络的兴起](/neural-networks-the-rise-of-recurrent-neural-networks-df740252da88?source=friends_link&sk=6844935e3de14e478ce00f0b22e419eb)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
充分解释了线性回归 7。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
8 完整解释了 Logistic 回归。[concat()、merge()和 join()与 Python](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
9 的区别。[与 Python 的数据角力—第 1 部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)