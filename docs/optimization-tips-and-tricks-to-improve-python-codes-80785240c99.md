# 改进 Python 代码的优化技巧和诀窍

> 原文：<https://pub.towardsai.net/optimization-tips-and-tricks-to-improve-python-codes-80785240c99?source=collection_archive---------1----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 提高 python 程序的速度和性能

![](img/15ad0aa4ae8f108db4603cfe6e239a4f.png)

照片由[埃米尔·佩龙](https://unsplash.com/@emilep?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

在本文中，我们将看到一些 python 示例，以获得 python 代码的帮助，使程序在速度和性能方面更加优化。

运行时间长的冗长程序你不烦吗？没有问题的读者，因为这篇文章将帮助你指导如何有效地编写你的 python 代码而不影响它的性能。

优化您的 Python 代码是绝对必要的，这将使您的程序更加高效，节省系统内存并更快地获得结果。优化代码的一些方法；列表理解、内置函数和库等。

作为编程的初学者，人们选择 Python 作为他们的第一语言，因为这种语言简单易学，并且已经在多个应用程序中使用。

让我们看看一些特性，通过它们我们可以使 python 程序变得更快一点。

> ***使用内置函数和库***

内置函数不过是 Python 中预定义的函数。这些函数的使用减少了你的程序的大小，并使它更加有效。这样，当一个简单的内置函数可以修复它时，就不需要实现复杂的循环。

让我们考虑一个简单的例子，要求打印给定列表中最大的数字。

## **程序 1**

```
Numbers = [4, 5, 7, 9, 10]
max_number = 0for i in Numbers:
    while i > max_number:
        max_number = iprint(max_number)
```

## **程序 2**

```
list = [4, 5, 7, 9, 10]
print(max(list))
```

## **输出:**

```
10
```

## **说明:**

从上面的程序中，我们可以了解到，像' max()'这样简单的内置函数消除了第一个程序中繁琐的代码行的使用。这些函数有助于你的程序得到优化。当您运行大量代码时，内置函数非常友好。

> ***使用排序函数中的关键参数***

“排序”函数返回列表或元组中已排序元素的列表，而不改变原始序列。在“排序”函数中，使用 key 参数是优化代码的另一种方式。让我们看一个例子。这里的要求是根据列表中元素的长度对列表进行排序:

## **程序:**

```
list = [‘aaaaaa’, ‘bb’, ‘ccc’, ‘d’]
print(sorted(list, key=len))
```

## **输出:**

```
[‘d’, ‘bb’, ‘ccc’, ‘aaaaaa’]
```

## **解释:**

上述程序的概念很简单。这里，在 print 语句中，要求程序对列表进行排序；根据键值显示。在这种情况下，键值是' len '；意味着列表将根据元素的长度进行排序。使用键是一种非常简单的编写程序的方式，而且执行起来花费的时间也少得多；优化代码。

[](https://medium.com/pythoneers/forget-html-and-flask-start-using-streamlit-1b394cfe4595) [## 忘记 HTML 和 Flask，开始使用 Streamlit

### 数据科学和机器学习的 WebApp 框架

medium.com](https://medium.com/pythoneers/forget-html-and-flask-start-using-streamlit-1b394cfe4595) 

> ***优化循环***

我们知道我们使用循环来执行重复的任务。但是循环语句通常需要时间来执行。为了优化这个过程，我们使用字符串连接。字符串连接提供了比 Python 中任何其他实现都要快得多的结果。让我们看一个例子，其中的要求是将字符串中的所有小写字母转换成大写字母。

## **节目一**

```
s = ‘welcome’
sl = ‘ ’for i in s:
    sl = sl + i
print (sl.upper())
```

## **输出**

```
WELCOME
```

## **程序 2**

```
s = ‘welcome’sl = ‘’.join([i for i in s])print (sl.upper())
```

## **输出**

```
WELCOME
```

## **说明:**

从上面两个程序可以看出，得到的输出是一样的。但是正如你所观察到的，这两个程序有一些不同之处。在 program1 中，创建了两个变量，其中一个存储字符串 welcome，另一个为空。在此之后,“for”循环执行，将字符串中的每个字母转换为大写。而在 program2 中，变量初始化和“for”循环是在一个步骤中编写的；优化代码。这也是在处理冗长项目时简化代码的另一种方式。

> ***用 range()代替 xrange()函数***

优化代码的另一种方法是使用 range()函数，而不是 xrange()函数。下面给出了两个显示 1 到 7 之间数字的例子。

**注意:**以下代码在 Python 解释器中执行。

## **节目一**

```
>> xrange(1,7)
xrange(1,7)>> for i in xrange(1,7):
print i1
2
3
4
5
6
```

## **程序二**

```
>> range(1,7)
[1, 2, 3, 4, 5, 6]
```

## **解释:**

xrange()函数总是返回生成器对象，并且只通过循环显示数字，而 range 函数只在一行中显示输出。因此，我们可以理解，range()函数比 xrange()函数更有助于节省系统内存。

> ***限制循环的使用***

可以使用 range()来限制循环的使用。range 函数打印从零开始的数字序列，默认情况下，以 1 为增量。这个函数比使用任何循环都要好。下面两个程序展示了使用和不使用 range 函数的区别。

要求是打印范围从奇数到 10 的数字。

## **程序 1**

```
i=0
while i <= 10:
    if ( i % 3==0):
        print (i, end=’, ‘)
    i+=1
```

## **程序 2**

```
odd = [ i for i in range(10) if i%3 == 0]
print (odd)
```

## **输出**

```
[0, 3, 6, 9]
```

## **解释:**

在程序 1 中，你可以看到我们使用了一个 while 循环来执行这个程序。而在 program2 中，使用 range 函数和列表理解的概念减少了代码行数；这种方法所用的时间比程序 1 少得多。

[](/why-data-science-is-booming-e240b1a64645) [## 数据科学为何蓬勃发展？

### 对他们的企业和整个社会的宝贵贡献

pub.towardsai.net](/why-data-science-is-booming-e240b1a64645) [](/network-programming-of-sockets-server-sockets-client-sockets-with-python-5ce556276b0b) [## 用 Python 对套接字、服务器套接字、客户端套接字进行网络编程

### 低级和高级接入网内编程

pub.towardsai.net](/network-programming-of-sockets-server-sockets-client-sockets-with-python-5ce556276b0b) 

> ***采用多种编码方式***

在 python 程序中，有不同的方法可以编写代码，其中一些方法可能长或短。从长远来看，一个高效的程序员总是遵循捷径；以使程序优化并易于阅读。下面是一个例子，有两种方法来存储字典中每个字母的计数。

## **节目一**

```
wd = {}
word = ‘thanksthanking’for i in word:
    if i not in wd:
        wd[i] = 0
    wd[i] += 1print(wd)
```

## **程序 2**

```
wd = {}
word = ‘thanksthanking’for i in word:
    try:
        wd[i] += 1
    except KeyError:
        wd[i] = 1print (wd)
```

## **输出**

```
{‘t’: 2, ‘h’: 2, ‘a’: 2, ’n’: 3, ‘k’: 2, ‘s’: 1, ‘i’: 1, ‘g’: 1}
```

## **说明:**

在 program1 中，您可以看到我们在“for”循环中使用 if-else 子句来初始化字典元素。而在 program2 中，一个简单的 try-except 方法是执行相同的过程。这两个程序的区别在于，在 program1 中，编译器每次检查单词中的字母时都必须检查 if-else 语句，这使得 program1 比 program2 运行的时间更长。因此，使用 try-except 方法是一种更加高效和优化的代码编写方式。

> ***简化变量交换***

在 python 中优化代码的另一种方法是通过简化代码来交换变量。下图显示了该计划的两种不同方法。

## **程序 1**

```
a = 2
b = 6temp = a
a = b
b = tempprint (a,b)
```

## **程序 2**

```
a,b = 2,6a,b = b,aprint (a,b)
```

## **输出**

```
6 2
```

## **解释:**

在程序 1 中，你可以看到‘a’和‘b’的值存储在另一个变量中；命名为“temp”来交换变量。但是在 program2 中，这个过程以一种非常简化的方式陈述(a，b = b，a)；节省系统内存。因此，program2 是一种更有效的交换变量的方式。

> ***使用局部变量而不是全局变量***

练习使用局部变量而不是全局变量是优化代码的另一个技巧。下面给出的是分别使用全局变量和局部变量的编程例子。

## **程序 1:全局变量**

```
def f():
    print(“Inside Func: “, s)# Global scope
s = “welcome to programming”
f()
```

## **输出**

```
Inside Func: welcome to programming
```

## **程序 2:局部变量**

```
def f():
    # local variable
    s = “welcome to programming”
    print(s)
f()
```

## **输出**

```
welcome to programming
```

## **解释:**

在这个程序 1 中，函数 f()被调用。但是在函数中，当 Python 搜索变量‘s’时。因为变量不在函数中，所以它从函数中出来，取值为“s”。由于这个搜索，这个程序的执行变得很慢。

但是在 program2 中，存储字符串的变量存在于函数内部；不需要用 Python 来搜索。因此，这个程序的执行时间比程序 1 少得多。

> ***结论:***

总之，本文介绍了一些优化 Python 代码的基本技巧。我强烈建议阅读更多的文章并应用这些概念，因为有许多方法可以让你尝试这个话题。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

1.[8 Python 的主动学习见解收集模块](/8-active-learning-insights-of-python-collection-module-6c9e0cc16f6b?source=friends_link&sk=4a5c9f9ad552005636ae720a658281b1)
2。 [NumPy:图像上的线性代数](/numpy-linear-algebra-on-images-ed3180978cdb?source=friends_link&sk=d9afa4a1206971f9b1f64862f6291ac0)3。[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[熊猫:处理分类数据](/pandas-dealing-with-categorical-data-7547305582ff?source=friends_link&sk=11c6809f6623dd4f6dd74d43727297cf)
5。[超参数:机器学习中的 RandomSeachCV 和 GridSearchCV](/hyper-parameters-randomseachcv-and-gridsearchcv-in-machine-learning-b7d091cf56f4?source=friends_link&sk=cab337083fb09601114a6e466ec59689)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[数据分发使用 Numpy 与 Python](/data-distribution-using-numpy-with-python-3b64aae6f9d6?source=friends_link&sk=809e75802cbd25ddceb5f0f6496c9803)
9。[机器学习中的决策树 vs 随机森林](/decision-trees-vs-random-forests-in-machine-learning-be56c093b0f?source=friends_link&sk=91377248a43b62fe7aeb89a69e590860)
10。[用 Python 实现数据预处理的标准化](/standardization-in-data-preprocessing-with-python-96ae89d2f658?source=friends_link&sk=f348435582e8fbb47407e9b359787e41)