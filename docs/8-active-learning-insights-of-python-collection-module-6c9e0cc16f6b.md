# 8 Python 集合模块的主动学习见解

> 原文：<https://pub.towardsai.net/8-active-learning-insights-of-python-collection-module-6c9e0cc16f6b?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 数据收集容器

![](img/88b3851673ef286b187a969a687cb392.png)

由[穆罕默德·拉赫马尼](https://unsplash.com/@afgprogrammer?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

> ***采集模块***

python 集合模块是一个容器，用于存储许多数据集合，如对象，并提供对这些包含的对象的访问。列表、元组和字典是一些内置的容器。这些模块主要是为了改进这些内置收集容器的功能。让我们看一下集合模块提供的一些特殊类型的容器。

> ***涵盖的主题***

```
1\. Counters
2\. Ordered Dic
3\. Default Dic
4\. Chain Map
5\. Named Tuple
6\. DeQue
7\. User Dic
8\. User List
9\. User String
```

> ***计数器***

计数器是一个字典子类，我们用它来计算可散列对象。

**语法:**类集合。计数器([可迭代或映射])

**例子:**

```
from collections import Counternumbers = [9, 5, 7, 4, 7, 10, 9, 10, 3, 5, 3, 6, 8, 4, 5, 10, 5]
Count = Counter(numbers)print(Count)
print(list(Count.elements()))
print(Count.most_common())sub = {10:1, 9:2}
print(Count.subtract(sub))
print(Count.most_common())**Output:** Counter({5: 4, 10: 3, 9: 2, 7: 2, 4: 2, 3: 2, 6: 1, 8: 1})
[9, 9, 5, 5, 5, 5, 7, 7, 4, 4, 10, 10, 10, 3, 3, 6, 8]
[(5, 4), (10, 3), (9, 2), (7, 2), (4, 2), (3, 2), (6, 1), (8, 1)]
None
[(5, 4), (7, 2), (4, 2), (10, 2), (3, 2), (6, 1), (8, 1), (9, 0)]
```

**解释:**

*   这里，第一个代码片段是查找每个唯一元素的计数。输出以字典的形式返回。输出格式:首先是元素，接着是冒号，然后是它在列表中出现的次数。(5:4)
*   第二段代码显示了一个列表，其中包含每个唯一元素的所有重复元素。
*   第三个代码片段以元组的形式显示每个唯一元素的计数。
*   第四个代码片段是使用 subtract 函数减少特定元素的计数。

上述程序也使用元组、列表、集合和字典来执行。

> **命令*命令*命令**

OrderedDict 也是 dictionary 的子类。它的功能是记住输入的顺序。

**语法:**类集合。OrderDict()

**例如:**

```
from collections import OrderedDictod = OrderedDict()
od[2] = ‘h’
od[5] = ‘e’
od[4] = ‘l’
od[7] = ‘l’
od[9] = ‘o’print(od)
print(od.keys())od[2] = ‘b’
print(od)**Output:** OrderedDict([(2, ‘h’), (5, ‘e’), (4, ‘l’), (7, ‘l’), (9, ‘o’)])
odict_keys([2,5,4,7,9])
OrderedDict([(2, ‘b’), (5, ‘e’), (4, ‘l’), (7, ‘l’), (9, ‘o’)])
```

**解释:**

*   第一个代码片段按照条目的顺序显示存储的元素作为输出。
*   第二个代码片段按照输入的顺序只显示键作为输出。
*   第三个代码片段是将存储在“od[2]”中的元素替换为“b”，作为最终输出。

[](/standardization-in-data-preprocessing-with-python-96ae89d2f658) [## 用 Python 实现数据预处理的标准化

### 机器学习和深度学习算法中的缩放方法

pub.towardsai.net](/standardization-in-data-preprocessing-with-python-96ae89d2f658) [](/a-comprehensive-guide-of-regular-expressions-using-python-6ff8de3d1a67) [## 使用 Python 的正则表达式综合指南

### 文本分析中“重”模块的概念

pub.towardsai.net](/a-comprehensive-guide-of-regular-expressions-using-python-6ff8de3d1a67) 

*DefaultDict 也是一本字典。它的功能是调用工厂函数来提供缺失的值。*

***语法:**class collections . default dict(default _ factory)*

***举例:***

```
*from collections import defaultdictdd = defaultdict(int)
dd[1] = ‘hello’
dd[2] = ‘world’print(dd[3])**Output:** 0*
```

***解说:***

*这里，因为我们在这里使用了 defaultdict()函数，所以在显示第三个字符串(未创建)时，输出显示为“0”而不是“关键字错误”消息。*

> ****链图****

*链表也是类下的字典。它用于创建多个映射的单一视图。*

***语法:**类集合。链式映射(字典 1，字典 2)*

***示例:***

```
*from collections import ChainMapsub1 = {1: ‘Maths’, 2: ‘English’, 3: ‘Science’}
sub2 = {4: ‘Social’, 5: ‘Computer’, 6: ‘Hindi’}
subt = ChainMap(sub1, sub2)print(subt)**Output:** ChainMap({1: ‘Maths’, 2: ‘English’, 3: ‘Science’}, {4: ‘Social’, 5: ‘Computer’, 6: ‘Hindi’})*
```

***解释:**从上面的程序中我们可以看到，在 python 中可以获得多个映射的单个视图。这里创建了两个字典(sub1 & sub2)。在使用 ChianMap 函数时，两个字典显示为一个视图。*

> ****名为****

*namedtuple()返回一个元组，该元组由元组中每个元素的命名值组成。该容器也用于列表存储和访问数据。*

*语法:class collections . named tuple(typename，field_names)*

***例如:***

```
*from collections import namedtupleEmployee = namedtuple(‘Details’, [‘name’, ‘age’, ‘gender’])
a = Employee(‘Ram’, 24, ‘Male’)print(a)
print(a[2])
print(a.age)**Output:** Details(name=‘Ram’, age=24, gender=’Male’)
Male
24*
```

***说明:**这里程序执行将数据存储在一个命名字段下，需要时可以访问。第一步是导入集合库。下一步是声明我们想要存储的数据的类型名和字段名。之后，将数据存储在这些字段中(第 3 行)。我们现在可以看到数据存储在声明的属性中。也可以使用索引来访问数据。*

> ****德奎****

*deque 是一个优化的列表，可以非常容易地执行插入和删除等功能。*

***语法:**类 collections.deque(list)*

***例如:***

```
*from collections import dequejob = [‘e’, ‘l’, ‘e’, ‘c’, ‘t’, ‘r’, ‘i’, ‘c’]b = deque(job)
print(b)b.appendleft(‘mechanics’)
print(b)b.popleft()
print(b)**Output:** deque([‘e’, ‘l’, ‘e’, ‘c’, ‘t’, ‘r’, ‘i’, ‘c’])
deque([‘mechanics’, ‘e’, ‘l’, ‘e’, ‘c’, ‘t’, ‘r’, ‘i’, ‘c’])
deque([‘e’, ‘l’, ‘e’, ‘c’, ‘t’, ‘r’, ‘i’, ‘c’])*
```

***说明:**上面的程序描述了在一个列表中插入和删除。第一步是导入集合库。在这里，我们创建了一个名为“job”的列表主要目的是将字符串“mechanic”插入到创建的列表的最左侧位置。因此我们使用 appendleft()函数。现在，为了删除最左边的元素，我们使用函数 popleft()。*

*[](/image-processing-morphological-operations-with-python-7e0f8d1983eb) [## 图像处理:用 Python 进行形态学运算

### 为了从图像中去除噪声

pub.towardsai.net](/image-processing-morphological-operations-with-python-7e0f8d1983eb) 

> ***UserDict***

UserDict 类充当字典对象的包装器，使字典的子类化更容易。当我们想要创建一个具有一些修改功能或新功能的字典时，这个类是很有用的。最后，这个字典可以通过类的数据属性来访问。

**语法:**类集合。用户字典([初始数据])

**举例:**

```
from collections import UserDictud = {1:’h’, 2:’a’, 3:’i’}usdi = UserDict(ud)
print(usdi.data)usdi = UserDict()
print(usdi.data)**Output:** {1: ‘h’, 2: ‘a’, 3: ‘i’}
{}
```

> ***用户列表***

UserList 类充当列表的包装器，使列表的子类化更容易。当我们想要创建一个包含一些修改过的功能或新功能的列表时，这个类是很有用的。最后，列表可以通过类的数据属性来访问。

**语法:**类集合。用户列表([列表])

**示例:**

```
from collections import UserListul = [‘h’,’e’,’l’,’l’,’o’]usli = UserList(ul)
print(usli.data)usli = UserList()
print(usli.data)**Output:** [‘h’, ‘e’, ‘l’, ‘l’, ‘o’]
[]
```

> ***用户字符串***

UserString 类还充当 String 对象的包装器，使字符串的子类化更容易。当我们想要创建一个包含一些修改过的功能或新功能的列表时，这个类是很有用的。这个类更容易使用，因为底层字符串可以作为属性访问。最后，这个字符串可以被类的数据属性访问。

**语法:**类集合。用户字符串(序列)

**示例:**

```
from collections import UserStringstr = ‘hello’us = UserString(str)
print(us.data)us = UserString(“”)
print(“Empty string is created”,us.data)**Output:** hello
Empty string is created
```

> ***结论***

总之，本文涵盖了 9 个 Python 集合模块的基础知识。我强烈建议阅读更多的文章，因为在每个模块中有许多功能，你可以在这个主题上进行实验。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —零到英雄与 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [NumPy:图像上的线性代数](/numpy-linear-algebra-on-images-ed3180978cdb?source=friends_link&sk=d9afa4a1206971f9b1f64862f6291ac0)3。[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[用 Python 进行主成分分析降维](/principal-component-analysis-in-dimensionality-reduction-with-python-1a613006d531?source=friends_link&sk=3ed0671fdc04ba395dd36478bcea8a55)
5。[用 Python 全面讲解 K-means 聚类](https://medium.com/towards-artificial-intelligence/fully-explained-k-means-clustering-with-python-e7caa573176a?source=friends_link&sk=9c5c613ceb10f2d203712634f3b6fb28)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[concat()、merge()和 join()与 Python](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
的区别 9。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)*