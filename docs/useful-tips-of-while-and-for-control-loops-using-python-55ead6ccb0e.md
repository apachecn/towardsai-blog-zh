# 使用 Python 的 While 和 For 控制循环的有用提示

> 原文：<https://pub.towardsai.net/useful-tips-of-while-and-for-control-loops-using-python-55ead6ccb0e?source=collection_archive---------3----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 通过示例对控制回路有基本的了解

![](img/c9716b27b4cbb71d06bc9e3991abe302.png)

由 [Javier Esteban](https://unsplash.com/@javiestebaan?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

**控制流程:**

在编程中，控制流是任何语句或函数执行的顺序。控制流由条件语句、循环和函数组成。当一个程序需要多次执行或根据条件选择语句时，我们使用它们。

**什么是循环&为什么要用？**

在 python 中，循环在程序中反复执行任务。循环连续执行一组语句，直到满足给定的条件。主要有两种类型的循环语句，“for loop”和“while loop”。

一个循环通常由两段组成；主体和控制语句。

控制语句是给定的执行循环的条件，而主体语句是当控制语句为真时我们作为输出接收的语句。现在，让我们深入研究这些循环:

> ***While 循环***

python 中的 while 循环以指定的次数执行一些语句，直到给定的条件变为假。执行总是从一个条件开始。如果条件为真，则执行循环中的语句。如果条件完全不满足，那么程序就停止。

**语法:**

```
while testing_expression:
Body statements
```

**程序:**

```
a = 0
while a<2:
print(“Hello WorLd”)a + = 1**Output:** Hello WorLd
Hello WorLd
```

**解释:**在上面的程序中，我们要求打印“Hello World”，作为输出的两倍。这里，‘a’被初始化为 0；表示在执行程序之前计数值当前为‘0’。现在条件检查完毕。第一个计数值是“0 ”,它满足条件，因此在 while body 中执行。在“while”主体中，语句被打印出来，计数器值增加到 1。重复这个过程，直到条件变为假。

[](/latest-programming-languages-for-ai-5252d39e1c51) [## 最新的人工智能编程语言

### 人工智能未来娱乐它的语言

pub.towardsai.net](/latest-programming-languages-for-ai-5252d39e1c51) [](/python-zero-to-hero-with-examples-c7a5dedb968b) [## Python:从零到英雄(带示例)

### python 初学者手册指南

pub.towardsai.net](/python-zero-to-hero-with-examples-c7a5dedb968b) 

**让我们看看使用数据结构执行 while 循环的不同方法:**

**1。**列表中的

****程序:****

```
Fruits = [“guava”, “orange”, “lemon”]i = 0
while i < len(Fruits):
print(Fruits[i])i = i + 1**Output:** guava
orange
lemon
```

****解释:**上面的程序声明使用“while”循环打印元素列表。这里，我们将计数器值初始化为“0 ”,并将限制值初始化为列表的长度。“循环”一直执行到条件变为假。**

****2。成套****

****程序:****

```
i = 3Fruit = {“guava”, “orange”, “lemon”}
while i:
print(Fruit)i=i-1**Output:** (‘guava’, ‘orange’, ‘lemon’)
(‘guava’, ‘orange’, ‘lemon’)
(‘guava’, ‘orange’, ‘lemon’)
```

****解释:**上面的程序声明使用‘while’循环打印三次‘set’元素。这里，我们将变量“I”初始化为 3，这样每次在 while 循环中计数器的值都会递减，以便根据需要打印输出。**

****3。在字典里****

****程序:****

```
V = {1: ”a”, 2: “b”}i = 0
while i < 3:
print(v[1])i=i+1**Output:** a
a
a
```

****解释:**上面的程序声明使用‘while’循环打印一个字典(键值对)。这里，计数器值被设置为“0”。并且条件是只有当计数器值小于 3 时，才会打印“while”主体语句。每次执行后，计数器值递增到 1。**

> *****为循环*****

**“for”循环重复一组语句，直到对象中没有元素。它可以是字符串、元组、列表或任何其他对象。循环体总是使用表示为“{}”的缩进与程序分开。**

****语法:****

```
for variable in object:
    statement a
    statement b
    .
    .
    statement c
```

****程序:****

```
for a in range(0, 2):
    print(“Hello woRld”)**Output:** Hello woRld
Hello woRld
```

****说明:**在上面的程序中，要求是打印两次“Hello woRld”。这里，“for”表示循环的关键字，“a”指定保存元素序列的变量的名称，“in”表示下一个序列，“range(0，2)”是循环体将执行的次数限制。**

****让我们看看如何使用数据结构执行 for 循环的不同方法:****

****1。**列表中的**

******程序:******

```
**veggies = [“tomato”, “potato”, “onion”]for a in veggies:
    print(a)**Output:** tomato
potato
onion**
```

******解释:**这是一个简单的“for”循环例子，用来打印列表中的所有元素。“for”条件声明，如果元素出现在列表中，则执行“for”主体。因此获得了输出。****

******2。**套内**套内******

******程序:******

```
**veggies = {“tomato”, “potato”, “onion”}for a in veggies:
    print(a)**Output:** onion
potato
tomato**
```

******解释:**这是一个简单的“for”循环例子，用来打印一个集合中的所有元素。“set”中“for 循环”的执行类似于列表。唯一的区别是，在' set '中，元素用花括号括起来，而在 list 中，我们用方括号括起来。并且输出是随机生成的。“集合”中没有索引的概念。****

******3。** **辞书中的******

******程序:******

```
**veggies = {1:“tomato”, 2:“potato”, 3:“onion”}for a in veggies:
    print(veggies[a])**Output:** tomato
potato
onion**
```

******解释:**这是一个简单的“for”循环例子，用来打印字典中的所有元素。字典中“for 循环”的执行类似于集合。唯一的区别是，在字典中，元素是通过索引来迭代的，而在“集合”中，元素是随机生成的。****

> *******结论*******

****嘿读者们！！，我们已经介绍了控制语句的大部分基础知识，如“while loop”和“for loop”。我们还讨论了如何使用所有控制流语句来使用数据结构。我鼓励你通过自己执行程序来探索这个主题，并希望你在阅读本文时感到愉快。****

****我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。****

# ****推荐文章****

****[1。NLP —零到英雄与 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)3 .[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[为什么 LSTM 在深度学习方面比 RNN 更有用？](/deep-learning-88e218b74a14?source=friends_link&sk=540bf9088d31859d50dbddab7524ba35)
5。[神经网络:递归神经网络的兴起](/neural-networks-the-rise-of-recurrent-neural-networks-df740252da88?source=friends_link&sk=6844935e3de14e478ce00f0b22e419eb)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[concat()、merge()和 join()与 Python](/differences-between-concat-merge-and-join-with-python-1a6541abc08d?source=friends_link&sk=3b37b694fb90db16275059ea752fc16a)
的区别 9。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)****