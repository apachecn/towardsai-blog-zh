# Python:从零到英雄(带示例)

> 原文：<https://pub.towardsai.net/python-zero-to-hero-with-examples-c7a5dedb968b?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## python 初学者手册指南

![](img/399b0166d03df87c3a20be26180179b1.png)

由 [Fernando Hernandez](https://unsplash.com/@_ferh97?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

这篇文章将帮助许多对从哪里开始感到困惑的 python 学习者——来自 basic 的 python 概念和例子将消除每个初学者的疑虑。

## 这篇长文涉及的主题如下所示:

**第一节:**变量和字符串的基础知识

**第二节:**列表，元组，集合，字典，范围

**第 3 节:**操作符和导入库

**第四节:** If-else 和循环

**第五节:** Break，Continue，Pass 关键字。

**第六节:**数组和矩阵

**第 7 节:**功能、范围和自变量

**第 8 节:**带滤镜、贴图、还原的 Lambda 函数

我希望这篇长文不会让你厌倦学习，让乐趣开始吧。

[](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e) [## NLP——使用 Python 从零到英雄

### 学习自然语言处理基本概念的手册

medium.com](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e) 

# 第一节:

## 变量和字符串的基础知识

我认为没有必要介绍 python 语言是什么，以及它在从 web 开发到人工智能的各种应用程序中有多有用——涵盖所有领域。

*什么是变量？*

它是一个名称和存储容器，我们在其中以 int 或 string 的形式分配一些值。

*什么是字符串？*

它是字节数组形式的 Unicode 字符。

酷！我们有了变量和字符串定义的概念。现在来看一些如下所示的实际例子:

在 python 中，创建变量毫不费力。写一个用户友好的名字就行了，这样将来其他程序员也能明白它在程序中是做什么用的。

```
#creating a variable namea = 10
char = "Happy"
float_number = 12.5#How to check the length of the string
print(len(char))              #output : 5#how to add the other string to the existing string
print(char + 'World')        #output : Happy World#we cannot change the character of the string by indexchar[1] = 'i'
print(char[1])#output : error, 'str' object does not support item assignment
```

在上面的例子中，(a，char，float_number)这些是通过给(=)赋值这个符号而赋予 integer、string 和 float 值的变量名。

# 第二节:

## 目录

*   它是可变的
*   它使用[]括号
*   该列表用于在单个括号[]中对若干事物进行分组。

示例:

我们可以使用带变量的方括号来创建一个列表。这里，“list1”是一个变量名，五个整数值分配给它。

```
list1 = [1,2,3,4,5]
print(list1)             #output : [1,2,3,4,5]#accessing values by indexing
print(list1[0])          #output : 1
print(list1[4])          #output : 5
print(list1[2:])         #output : [3,4,5]
print(list1[-1])         #output : 5
print(list1[-5])         #output : 1
```

列表是 python 中的一种工具数据结构。我们可以将多种数据类型放在一个列表中。列表中可以有浮点值、整数值和字符串值。

```
list2 = [ 5.5, 4, 'Amit']
```

我们也可以将多个列表放在一个列表中。

```
list3 = [list1, list2] 
```

我们也可以在列表上做操作，比如追加、插入、删除等等。

```
list1 = [1,2,3,4,5]
list1.append(6)
print(list1)                     #output : [1,2,3,4,5,6]#if we remove any values from the list
list1.remove(2)
print(list1)                     #output : [1,3,4,5,6]#if we insert any values from the list by indexing
list1.insert(2,30)
print(list1)                     #output : [1,3,30,4,5,6]#deleting values from the list
del list1[3:]
print(list1)                     #output : [1,3,30]
```

列表中有各种操作，为了更加清晰，尽量都做。

## 元组

*   它是不可改变的。
*   它与列表几乎相同，但是元组使用了圆括号()。

不可变意味着我们不能改变元组的值。

示例:

```
tup1 = (20,30,40,50)print(tup1[2])                         #output : 40#what if we change the values
tup1[2] = 44
print(tup1) #output : error, 'str' object does not support item assignment
```

我们使用元组

*   它就像一个列表。我们不想改变它的价值。在某些项目中，我们有一个不需要改变值的需求。我们去找一个元组。
*   元组中的迭代比链表更快，提高了执行的速度。

## 一组

*   也是元素的集合。
*   集合用花括号{}区分。
*   集合从不遵循顺序。

示例:

```
set1 = {21,32,55,46}
print(set1)                 #output : {32,46,55,21}
```

在这里，我们看到设置值序列的输出并不完全相同。我们能通过索引得到集合中的值吗？让我们检查一下。

```
print(set1[2])                   #output : error
```

在集合中，没有任何顺序，所以我们不能通过索引来访问值。

## 词典

*   在字典中，我们给所有的值分配键。
*   它使用带键值对的花括号{}。

示例:

```
dic = {1:'Apple', 2:'Orange', 3:'Banana'}
print(dic)#output:
{1:'Apple', 2:'Orange', 3:'Banana'}
```

在字典中，我们也可以分别访问键和值。

```
print(dic.keys())
print(dic.values())#output:
dict_keys([1,2,3])
dict_values(['Apple','Orange','Banana'])
```

我们也可以使用键来获取值。

```
print(dic[2])               #output : 'Orange'
```

## 范围

*   范围用于获得从起点到终点的范围，即固定的间隔。

示例:

```
range(10)
print(range(10)                 #output: range(0,10)print(list(range(10))      #output : [0,1,2,3,4,5,6,7,8,9]#starting point, end point, difference between them
print(list(range(2,10,2)))   #output : [2,4,6,8]
```

# 第三节:

## 经营者

python 中的操作符有各种类型，用于执行算术和计算过程。操作员的类型如下所示:

*   **算术运算符**

示例:

```
x,y = 2,3
print(x+y)                         #output : 5
print(x-y)                         #output : -1
print(x*y)                         #output : 6
print(x/y)                         #output : 0.6666
```

*   **赋值操作符**

示例:

```
x = 8
x = x+2
print(x)            #output : 10x += 2
print(x)            #output : 12x *= 2
print(x)            #output : 24#assigning multiple values in one line 
x,y = 2,3
```

*   **关系运算符**

示例:

```
x,y = 5,6
print(x<y)           #output : True
print(x>y)           #output : Falsefor comparison we use double equal sign '=='print(x=y)          #output : Falseprint(x<=y)         #output : True
print(x>=y)         #output : True
print(x!=y)         #output : True
```

*   **一元运算符**

示例:

```
x = 3
print(x)              #output : 3
print(-x)             #output : -3x = -x
print(x)              #output : -3
```

*   **逻辑运算符**

示例:

```
# 'and' - condition 
x,y = 5,4
print(x<8 and y<5)             #output : True
print(x<8 and y<2)             #output : False# 'or' - condition
print((x<8 or y<2))            #output : True# 'not'
x = True
print(x)                       #output : True
print( not x)                  #output : False
```

*   **按位运算符**

按位运算符用于对整数进行按位计算。

示例:

```
# Compliment ( ~ ) operator
print(~12)                        #output : -13#Bitwise And ( & ) operator
print(12&13)                      #output : 12#Bitwise Or ( | ) operator
print(12|13)                      #output : 13# Xor ( ^ ) operator 
print(12^13)                      #output : 1# Left shift ( << ) operator
print(10<<2)                      #output : 40# Right shift ( >> ) operator
print(10>>2)                      #output : 2
```

## 导入库

*   有时 python 本身并没有所有的函数，我们需要从库中导入它们，这样我们就可以在我们的算法和程序中使用它们。

示例:

```
#finding the square root 
a = sqrt(36)
print(a)               #output : error, name sqrt is not defined
```

因此，我们需要导入一个数学库来使用 sqrt 函数

```
import math
a = math.sqrt(36)
print(x)                 #output : 6.0a = math.sqrt(15)
print(x)                 #output : 3.8729
```

当我们有一些小数值时，为了得到整数值，我们使用两个函数，即 floor 和 ceil

*****Ceil*** —无论 Ceil 函数中出现什么值，它都会四舍五入到最大值。即使 2.1，也会显示 3。**

**示例:**

```
print(math.floor(2.9))           #output : 2
print(math.ceil(2.2))            #output : 3
```

**如果在导入时不使用数学单词，而只使用“m ”,我们必须称它为别名**

```
import math as m
print(m.sqrt(36))   #output : 6.0
```

# **第四节:**

## **如果-否则**

*   **控制语句用于根据给定的条件执行语句。如果条件为真，那么它将执行 If 部分，否则不执行。**

**示例:**

```
# if if True:
    print("This statement is True")#output : This statement is True
```

**如果的条件为真，那么该语句将执行。**

**在这里，我们遇到了两个新事物——条件后的冒号和下一行中的空格。冒号表示某个块开始，在该块中，我们给出缩进(空格)，这样，该语句只属于该块。**

```
x = 6
remainder = x%2
if remainder == 0:
    print("Even")
else:
    print("odd")print("loop works")#output:even
loop works
```

## **While 循环**

*   **循环在编程中用于重复迭代。**

**示例:**

```
a = 1
while a<=3:
    print("It is working")
    a = a+1#output:
It is working
It is working
It is working
It is working
```

## **For 循环**

*   **它用于序列。**

**示例:**

```
a = [1, 2, ‘Amit’]
print(a)               #output:[1, 2, ‘Amit’]
```

**如果我们想让列表中的值一个接一个地迭代呢？**

```
a = [1, 2, ‘Amit’]
for i in a:
    print(i)#output:1
2
Amitb =  'AMIT'
for i in b:
    print(i)#output:A
M
I
T
```

# **第五节:**

**在某些情况下，我们使用这些关键字来中断、继续和传递，以使代码更有用。**

## **Break 关键字**

*   **如果条件不为真，则从循环中出来。**

**示例:**

```
x = 4
a = int(input('Enter the number:'))
b = 1
while b<=a:
    if b>=x:
        break
    print("Hello")
    b+=1
print("Done")#output:Enter the number: 5
Hello
Hello
Hello
Hello
Done
```

## **继续关键字**

*   **continue 关键字用于跳过 true 语句并继续打印其他语句。**

```
for i in range(1, 10):
    if i%3==0 or i%5==0:
        continue
    print(i)
print("Done")#output:
1
2
4
6
7
8 
```

## **传递关键字**

*   **pass 关键字用于跳过 true 语句并继续打印其他语句。**

```
for i in range(1, 11)
    if(i%2!=0):
        pass
    else:
        print(i)
print("Done")#output:
2
4
6
8
10
```

# **第六节:**

## **排列**

*   **数组对于保存许多值的变量来说很方便。**
*   **数组没有固定的大小。扩大它，缩小它。**
*   **我们必须导入一个数组来在程序中使用它们。**

```
import array import *
num = array()
```

*   **星号*用于从数组导入所有函数。**

**示例:**

```
import array import *
num = array('i', [1,2,3,4,5])
print(num)#output: array('i',[1,2,3,4,5])
```

*   **在数组值中，代码“I”仅代表列表中的整数值。**
*   **如何检查缓冲区(地址和类型代码)。**

```
import array import *
num = array('i', [1,2,3,4,5])
print(num.buffer_info())
print(num.typecode)#output:(85049343, 5)
i
```

*   **缓冲区给出了数组的地址和大小。**
*   **我们也可以使用字符类型码来处理字符。**

```
import array import *
num = array('i', ['a','b','c'])
for i in num:
    print(i)#output:a
b
c
```

*   **获取数组中值的索引号。**

```
import array import *
num = array('i', [1,2,3,4,5])
num1 = int(input("value for search: ")
print(num.index(num1))#output:value for search: 3
2      #it is index number
```

****创建数组的方式****

*   **数组()**

```
import array import *
num = array([1,2])
print(num)
print(num.dtype)#output:[1,2]
int32
```

*   **linspace()**

```
num = linspace(1,5,6)
print(num)#here 6 means breaking range 1 to 5 into 6 parts
#output: [0., 1., 2., 3., 4., 5.]
```

*   **阿兰格()**

```
num = arange(1, 10, 3)
print(num)#output: [1 4 7 10]
```

**还有许多其他功能。**

****增加两个数组****

```
ar1 = array([1,2,3])
ar2 = array([4,5,6])
ar3 = ar1 + ar2
print(ar3)#output: [5 7 9]
```

****连接两个数组****

```
ar1 = array([1,2,3])
ar2 = array([4,5,6])
print(concatenate([ar1, ar2])#output: [1 2 3 4 5 6]
```

****浅层和深层复制****

***浅拷贝*:两个数组仍然相互依赖**

**示例:**

```
ar1 = array([1,2,3])
ar2 = ar1.view()
ar1[0] = 5
print(ar1)
print(ar2)#output:[5 2 3]
[5 2 3]
```

**当我们使用浅拷贝时，它也改变了第二个数组中的值。**

***深度复制*:两个没有任何关联的数组使用函数 copy()代替 if viewe()。**

```
ar1 = array([1,2,3])
ar2 = ar1.copy()
ar1[0] = 5
print(ar1)
print(ar2)#output:[5 2 3]
[1 2 3]
```

## **[数]矩阵**

*   **矩阵是数据结构中的一种特殊数据类型，在这种数据结构中，数据以多维数组的形式排列。**
*   **数组不支持多维数组，这就是使用第三个包 NumPy 的原因。**

**示例:**

```
from numpy import *
ar1 = array([
             []
             []
            ])
print(ar1)
print(ar1.dtype)#output:[[1 2 3]
 [4 5 6]]int32
```

**要知道数组的维数，请使用(ndim)。**

```
print(ar1.ndim)
print(ar1.shape)#output:2
(2,3)     # row and columnprint(ar1.size)#output:  6
```

****三维阵列****

```
ar1 = array([
             [1,2,3,4,5,6], 
             [2,5,2,7,9,10]
           ])
ar2 = ar1.flatten()
ar3 = ar2.reshape(3,4)
print(ar3)#output:[[1 2 3 4]
 [5 6 2 5]
 [2 7 9 10]]
```

# **第 7 节:**

## **功能**

*   **当我们在做一个大项目时，我们可以分解成更小的任务，然后使用函数。**
*   **我们必须知道两件主要的事情。**

1.  **定义函数**
2.  **调用函数**

*****语法*****

```
def function_name():
```

**我们使用一个 *def* 字来定义一个函数。**

**示例:**

```
def hello():                         # Defining a function
    print("This is the first statement")
hello()                              # Calling a function
```

*   **我们可以将一项任务分配给一个功能。**
*   **我们可以多次调用这个函数。**

```
#adding two numbers
def add(a,b)
    x = a+b
    print(x)add(2,3)     # passing two arguments when we call a function#output: 5
```

## ****争论的类型****

*   **形式参数:在函数中定义的。**
*   **实际参数:在调用函数中定义。**

**在实际的争论中，有四种类型:**

1.  **位置**

**示例:**

```
def person(name, age):
    print(name)
    print(age)
person('Amit', 25)#output:
Amit
25
```

**在位置论证中，我们怎么知道阿米特去名，25 去龄？这就是位置发挥作用的地方。**

**2.关键词**

*   **如果我们不知道序列，我们使用关键字。**

```
person(age = 25, name = 'Amit')
```

**3.默认**

**一个参数已经在一个形式参数中定义了，只需要传递一个参数。**

```
def person(name, age = 25):
    print(name)
    print(age)
person('Amit')
```

**4.可变长度变元**

*   **这种类型的参数用于传递多个值。**

**示例:**

```
def sum(x, *y)
    a = x+y
    print(a)
sum(5,6,7,2)
```

*   **这里的提示是，当我们传递多个值时，第一个值传递给第一个形参，与第二个形参一起使用的星号是接受其中的所有其他值。**
*   **x 得到 5，而*y 得到(6，7，2)**

## **范围**

*   **它基于函数中的全局和局部变量。**

```
x = 5                #this is Global Variable
def hello():
    x = 10           #this is Local Variable
    print(x)
hello(x)
```

**如果我们想把一个局部变量变成一个全局变量，我们需要显式地写 global。**

```
x = 5                #this is Global Variable
def hello():
    global x
    x = 10           #this is Local Variable
    print(x)
hello(x)
```

# ****第八节:****

## **具有过滤、映射和减少的 Lambda 函数**

**Lambda 是一个函数，在这个函数中，我们在一条语句中完成所有的函数任务。有时，我们会处理大数据，并将其分成小块，我们会过滤数据，绘制数据图，并减少数据。**

**示例:**

```
func = lambda x:x*x
result = func(x)
print(result)#output:
25
```

****过滤功能****

**句法**

```
filter(function, iterable)
```

**该功能是自定义功能。它只返回一个值。在这种情况下，使用 lambda。**

```
def is_even(x):
    return x%2 == 0
num = [2,6,7,4,9,10]even = list(filter(lambda x:x%2==0, num)
print(even)#output:
[2,6,4,10]
```

****地图功能****

**句法**

```
map(function, iteration)
```

**过滤后，我们需要映射数据。**

```
num = [2,6,7,4,9,10]even = list(filter(lambda x:x%2==0, num)
add = list(map(lambda x: x+2, even))print(add)#output:
[4,12,8,20]
```

****减少功能****

*   **Reduce 函数属于一个名为 *functools 的模块。***

```
from functools import reducenum = [2,6,7,4,9,10]
even = list(filter(lambda x:x%2==0, num)
add = list(map(lambda x: x+2, even))
sum = reduce(lambda a,b: a+b, add)print(sum)#output:
44
```

**[](https://medium.com/towards-artificial-intelligence/inheritance-and-its-type-with-python-f35b993d712e) [## Python 中的继承及其类型

### 单一、多级和多重继承方法的概念

medium.com](https://medium.com/towards-artificial-intelligence/inheritance-and-its-type-with-python-f35b993d712e) 

## 结论

几乎每个领域都在用 python 进行业务开发。本文为新手提供了一些 python 的基本概念。我希望你坚持到最后。如果你忘了什么，再上去读。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

1.[Python 最有用的 15 种 NumPy 方法](/15-most-usable-numpy-methods-with-python-4d20eb93e149?sk=911d2bebf042b148be8f366b907af158)
2。 [NumPy:图像上的线性代数](/numpy-linear-algebra-on-images-ed3180978cdb?source=friends_link&sk=d9afa4a1206971f9b1f64862f6291ac0)3。[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[熊猫:处理分类数据](/pandas-dealing-with-categorical-data-7547305582ff?source=friends_link&sk=11c6809f6623dd4f6dd74d43727297cf)
5。[超参数:机器学习中的 RandomSeachCV 和 GridSearchCV](/hyper-parameters-randomseachcv-and-gridsearchcv-in-machine-learning-b7d091cf56f4?source=friends_link&sk=cab337083fb09601114a6e466ec59689)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[数据分发使用 Numpy 与 Python](/data-distribution-using-numpy-with-python-3b64aae6f9d6?source=friends_link&sk=809e75802cbd25ddceb5f0f6496c9803)
9。 [40 种 Python 中最疯狂可用的方法](https://medium.com/pythoneers/40-most-insanely-usable-methods-in-python-a983c78f5bfd?sk=07df9058ea3e8c2fce4318a73cd8fce9)
10。[Python 中最常用的 20 种熊猫快捷方式](https://medium.com/pythoneers/20-most-usable-pandas-shortcut-methods-in-python-c9bc065ce11e?sk=1faf673d0cdfb46234975cbdeed12beb)**