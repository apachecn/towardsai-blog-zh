# 为什么 Map()、Filter()和 Reduce()函数这么出名？

> 原文：<https://pub.towardsai.net/why-map-filter-and-reduce-functions-are-so-famous-4c8e42fd0755?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## python 中避免循环和分支的函数式编程

![](img/b5887367b2e9b8aa4402bce2d8e8f8cb.png)

照片由[丹尼尔·伊德里](https://unsplash.com/@ricaros?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

在 python 中，许多内置函数允许用户编写简单明了的代码，而不用担心循环和分支。这些函数中的一个被称为λ函数。

> ***什么是λ函数？***

Lambda 函数是没有名称的单行函数，可以有任意数量的参数，但只能包含一个表达式。Lambda 函数类似于 python def 函数。“def”被定义为匿名函数，而 lambda 被认为是一次性函数。

**语法:** (lambda 参数:表达式)

> ***我们为什么要使用 lambda 函数？***

在 python 中，编写函数是一项简单的任务。但是将这些功能结合在一个应用程序中是它变得如此沉重的地方。

在应用程序中使用函数时，它们会很长，因此编译器也会花费额外的时间来执行每一行代码，尽管 python 简单易读。

但是，如果有一种方法可以让这些函数变得易读和简短呢？这就是 lambda 函数发挥作用的地方。Lambda 减小了程序的大小，使得执行程序的效率大大提高。

> ***如何使用 python 使用 lambda 函数？***

lambda 函数由 3 部分组成:

1.  **关键词:**λ
2.  **绑定变量:**这个绑定变量是 lambda 函数的一个参数。
3.  **表达式:**该部分包含我们需要执行的约束。

以下示例显示了该函数的三个部分:

**例**:**λa:a+1**

**让我们通过一个例子来看看普通函数和 lambda 函数之间的区别:**

1.  ****使用“匿名函数”和“lambda 函数”打印奇数列表****

*   ****匿名函数(不使用 lambda 的函数):****

```
def odd(n):
    return n%3 ==0Numbers = [23,22,16,28,14,36,12,99]
even = list(filter(odd, Numbers))
print(odd)
```

*   ****λ函数:****

```
Numbers = [23,22,16,28,14,36,12,99]
odd = list(filter(lambda n : n%3 == 0, Numbers))
print(odd)**Output :** [23,15,13,37,99]
```

## ****解释:****

**在程序的第一步，我们声明一个数字列表作为输入。在下一步中，我们使用 lambda 函数来查找偶数列表。这个函数是根据语法写的。**

**函数的第一部分包含关键字。第二部分提到参数，最后是表达式。这里正常函数和 lambda 函数的区别是:**

1.  **lambda 函数计算单个表达式并产生一个函数对象，而“标准函数”可以计算多个表达式。**
2.  **lambda 函数不包含 return 语句。默认情况下，它总是返回表达式的输出，而标准函数则由 return 语句组成。**

**从这两个程序中，我们可以得出结论，lambda 函数使得程序更加高效和易读。**

**[](/understand-list-as-big-o-and-comprehension-with-python-examples-cbea610c9e43) [## 将 List 理解为 Big O 并理解 Python 示例

### 列表是 python 数据结构的一部分

pub.towardsai.net](/understand-list-as-big-o-and-comprehension-with-python-examples-cbea610c9e43) [](/oops-concept-in-python-b5f5833d57db) [## Python 中的 OOPs 概念

### OOPs 是编写程序的一种高效方式

pub.towardsai.net](/oops-concept-in-python-b5f5833d57db) 

> ***内置函数使用λ***

我们现在知道λ函数使

有许多使用 lambda 的内置函数。这里，我们将只讨论 3 个函数:map()、filter()和 reduce()。这三个函数为 python 带来了函数式编程的一小部分，为一些问题提供了更优雅和简便的方法。

1.  **滤镜()**

顾名思义，filter()创建了一个新的列表，其中只包含满足我们提供的条件**的元素。**

**语法:** filter(函数，iterable(s))

**程序:**

让我们用同一个例子来比较标准函数和 lambda 函数。

*   **只打印奇数的列表，有和没有 lambda 函数。**
*   **匿名函数(不使用 lambda 的函数):**

```
def odd(n):
    return n%3 == 0Numbers = [23,22,19,26,33,55,64,67]
odd = list(filter(odd, Number))
print(odd)
```

*   **使用λ的过滤功能:**

```
Numbers = [23,22,19,26,33,55,64,67]
odd = list(filter(lambda n : n%3 == 0, Numbers))
print(odd)**Output :** [23,19,33,55,67]
```

## **说明:**

在匿名函数中，我们将函数命名为“odd ”,并添加了我们想要的约束作为输出。这个函数在程序的第四行被调用。然而，在使用 lambda 时，我们不会面临这么多的复杂问题。lambda 函数及其操作在主体内执行。我们可以看到 lambda 函数是如何使它变得更加简单的。

**2。地图()**

map 函数遍历给定 iterable 中的所有元素，并通过我们传递的参数执行函数。

**语法:** map(函数，iterable(s))

**程序:**

让我们用同一个例子来比较标准函数和 lambda 函数。

*   **打印一个只有奇数的双数列表，有和没有 lambda 函数。**
*   **匿名函数(不使用 lambda 的映射函数):**

```
def update(n):
    return n*2Numbers = [23,22,19,26,33,55,64,67]
odd = list(filter(lambda n : n%3 == 0, nums))
doubles = list(map(update, odd))print(doubles)
```

*   **使用 lambda 映射功能:**

```
Numbers = [23,22,19,26,33,55,64,67]
odd = list(filter(lambda n : n%3 == 0, nums))
doubles = list(map(lambda n : n*2, odd))print(doubles)**Output :** [46,38,66,110,134]
```

## **解释:**

与上面的过滤器示例一样，匿名函数和 lambda 函数遵循相同的原则。映射是一个概念，它根据规定的可重复项来映射值。所以这里只把奇数乘以“2”，以列表的形式返回作为输出。

**3。Reduce()**

Reduce 函数不同于 map()和 filter()。根据我们传递的函数和 iterables，它只返回一个值。

**语法:** reduce(函数，序列[，初始])

**程序:**

让我们用同一个例子来比较标准函数和 lambda 函数。

*   **打印包含和不包含 lambda 函数的列表中所有奇数的和。**
*   **匿名函数(不使用 lambda 的函数):**

```
def add_all(x,y):
    return x+yNumbers = [23,22,19,26,33,55,64,67]
odd = list(filter(lambda n : n%3 == 0, nums))
sum = reduce(add_all, odd)print(sum)
```

*   **使用 lambda 减少功能:**

```
from functools import reduceNumbers = [23,22,19,26,33,55,64,67]
odd = list(filter(lambda n : n%3 == 0, nums))print(odd)sum = reduce(lambda a,b : a+b, odd)
print(sum)**Output :** [23,19,33,55,67]
203
```

## **说明:**

众所周知，reduce 函数总是返回一个值。所以，这个程序首先打印一个奇数列表。在这个列表中，从左端取两个值，并不断相加，直到没有剩余的值。

```
[**23,19**,33,55,67]
⇒ **42,33**,55,67
⇒ **75,55**,67
⇒ **130,67**
⇒ 197
```

> ***结论***

总之，我们可以说 lambda 函数在编写程序时起着重要的作用。它们是为了我们的方便而使用的，因此我们的程序被压缩并显示相同的输出，而不是编写冗长乏味的代码。

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
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)**