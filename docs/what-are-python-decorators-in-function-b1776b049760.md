# Python Decorators 在功能上是什么？

> 原文：<https://pub.towardsai.net/what-are-python-decorators-in-function-b1776b049760?source=collection_archive---------1----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 向程序添加新功能

![](img/94dc6dcc527b1791b269a25992861264.png)

由[沙哈达特拉赫曼](https://unsplash.com/@hishahadat?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

> ***Python 装饰者***

在真正理解 decorators 之前，有必要了解一下一级对象及其属性。

## **一等品**

一级对象不过是函数。这意味着它们可以作为参数使用或传递。让我们来看看这些函数的一些主要性质。

## **一级函数的性质:**

*   一个函数可以以参数的形式传递给另一个函数。
*   用户定义的函数可以在另一个用户定义的函数中定义。
*   在变量中存储一个函数是可能的。
*   这些函数也可以存储在类似哈希表、列表、元组等数据结构中。

现在让我们看几个基于这些特征的例子。

## **将函数作为对象进行处理**

**程序**

```
2,6→ def begin(prog):
3,7→     return prog.upper()1→   print(begin(‘Python Program’))
4→   end = begin
5,8→ print(end(‘Welcome’))**Output:** PYTHON PROGRAM
WELCOME
```

## **说明:**

在第四行中，我们看到函数“begin”被赋给了一个变量。这个变量不会调用函数。它使用“begin”引用的函数对象来创建另一个名称“end”在第五行中，我们可以观察到被引用的对象被调用并执行与之前相同的操作。让我们来详细看看这个程序的工作原理。

```
1→ The program starts from here, where the function gets called.2→ The parameter “Python Program” is passed as the argument in the function.3→ This line converts the stated argument to uppercase letters, returns the value to the called function, and prints as the output.4→ Here, we have referenced the function ‘begin’ to a variable named ‘end.’5→ In this line, we can observe that the referenced object is called and performs the same operation as before.
```

## **将函数作为参数传递**

**程序:**

```
4→ def begin(prog):
5→     return prog.lower()10→ def start(prog):
11→     return prog.upper()2,8→  def end(func):
3,9→      ending = func(“Passing functions as an argument”)
6,12→     print(ending)1→ end(begin)
7→ end(start)**Output:** passing functions as an argument
PASSING FUNCTIONS AS AN ARGUMENT
```

## **解释:**

上面的例子说明了调用函数“end”将另一个函数作为参数；开始喊。作为参数传递的“begin”函数稍后在函数内部调用:“end。”让我们详细看看程序的工作原理:

```
1→ The function, ‘end’ is called.2→ The begin function is passed as an argument.3→ Now, the begin function is called inside the function ‘end’. This function is inside a variable named ‘ending’.4→ The ‘begin’ function’s parameter is passed as the argument here.5→ This line converts the stated argument to lowercase letters and returns the output to the called function.6→ In this line, the result is printed.7→ The above process is repeated for the following function call.
```

[](/data-preprocessing-concepts-with-python-b93c63f14bb6) [## Python 中的数据预处理概念

### 一种为机器学习估值器准备数据的稳健方法

pub.towardsai.net](/data-preprocessing-concepts-with-python-b93c63f14bb6) 

## **函数返回另一个函数**

**程序:**

```
2→ def begin(prog):
3→     print(“Beginning of program”)
4→     return prog7→ def end():
8→     return “End of program”1,5→ calling = begin(end)
6,9→ print(calling())**Output:** Beginning of program
End of program
```

## **说明:**

为了避免混淆，让我们详细地看一下这个程序的工作原理。

```
1→ The ‘begin’ function is called. (The function is stored in a variable ‘calling’, which will be called later in step 6).2→ Here, the ‘end’ function is passed as an argument.3→ Inside this function lies a statement that prints the output.4→ This step returns a reference of the argument ‘end’ to the called function.5→ The returned argument is referenced to the variable, “calling”.6→ Now, the function “calling”(referenced as ‘end’) is called.7&8→ The end function is implemented and returns the statement to the called function.9→ The returned statement is printed.
```

**以上三个概念是理解装修工概念必不可少的。让我们更深入地探讨这个话题。**

[](/8-active-learning-insights-of-python-collection-module-6c9e0cc16f6b) [## 8 Python 集合模块的主动学习见解

### 数据收集容器

pub.towardsai.net](/8-active-learning-insights-of-python-collection-module-6c9e0cc16f6b) [](/pandas-dealing-with-categorical-data-7547305582ff) [## 熊猫:处理分类数据

### 用 python 创建系列和数据帧

pub.towardsai.net](/pandas-dealing-with-categorical-data-7547305582ff) 

> ***Python 中的 Decorators 是什么？***

装饰者的概念很简单。python 中的装饰器允许我们在不改变现有功能的情况下给程序添加新的功能。

**语法:**

```
@decorator
def func_name():
    ‘’’Function Implementation’’’
```

**上面的语法也等同于:**

```
def func_name():
    ‘’’Function Implementation’’’
func_name = decorator(func_name)
```

**程序:**

```
#without decoratordef str_upr(fun):
    def inn():
        str1 = fun()
        return str1.upper()
    return inndef str():
    return “Welcome to Python Programming”
d = str_upr(str)
print(d())#with decorator3→ def str_upr(fun):
6→     def inn():
7→         str1 = fun()
8→         return str1.upper()
4→     return inn2,5→@str_upr
    def str():
        return “Welcome to Python Programming”
1→  print(str())**Output:** WELCOME TO PYTHON PROGRAMMING
```

## **说明:**

以上两个程序是理解装饰者概念的简单例子。第一个是使用函数概念的简单程序。

我们知道第一类程序的工作原理。让我们来看看第二种工作方式。

```
1→ This is where the program starts; we are calling the function.2→ This means that the ‘str_upr’ function decorates the ‘str’ function.3→ Here, the ‘str_upr’ function is executed with ‘str’ as the argument.4→ To execute the function ‘inn’, we have to call it. Hence, we return the name of the function, i.e. inn.5→ This step would call the ‘inn’ function that was returned in the previous step.6→ The ‘inn’ function is executed.7→ **Note**: The inner function can access the arguments of the outer function. Hence the function ‘str’ is called and stored in variable ‘str1’.8→ This step converts the string to the upper case and returns the output to the function call(Step 1). Finally, the result gets printed as above.
```

## **Python 中带参数的装饰器**

**语法:**

```
@decorator(parameter)
def func_name():
    ‘’’ Function Implementation ‘’’
```

**程序:**

```
3,11→ def add_decor(func):
5,13→     def inn(x,y):
6,14→         if y==2:
7,15→             return “The number to be added is 2”
16→           return func(x,y)
4,12→     return inn2,10→ @add_decor
17→   def add(a,b):
18→       return a+b1,8→  print(add(4,2))
9,19→ print(add(2,4))**Output:** The number to be added is 2
6
```

## **说明:**

```
1→ First, we are calling the ‘add’ function that contains two parameters (4,2).2→ This means that the ‘add_decor’ function decorates the ‘add’ function.3→ Hence, the ‘add_decor’ function is executed.4→ The inner function ‘inn’ will not be executed as it is not called. Hence, it jumps to returns the function name ‘inn’ to the function call(line 1).5→ Now, the function ‘inn’ is executed, with arguments as ‘2’ and ‘4’.6,7,8→ Here, there is an ‘if’ condition to check whether the value of y is equal to ‘2’. Since the condition is true, (line 7) ‘return statement is printed. And the function execution comes to a stop.9→ In the second function call, the program executes the same way till the ‘inn’ function.14→ Inside the ‘inn’ function, since the condition is not satisfied, the else statement is executed (line 16).16,17,18→ **Note**: The inner function can access the arguments of the outer function. Hence the function ‘add’ is executed.19→ Finally, the output is printed.
```

> ***连锁装修工***

我们知道装饰器在不改变现有功能的情况下给程序增加了新的功能。链接装饰器只不过是给程序增加了更多的功能。这些类型的装饰器很有用，因为新的功能是以块的形式添加的，这些块执行不同的任务，但使程序看起来更整洁和条块化。这些也被称为嵌套装饰器。

**语法:**

```
@decorator1
@decorator2
def state():
    statements(st)
```

**程序:**

```
def upper_dec(fun):
    def inn():
        x = fun()
        return 40+x
    return inndef lower_dec(fun):
    def inn():
        x = fun()
        return 25-x
    return inn@lower_dec
@upper_dec
def num():
    return 20
print(num())**Output:** -35
```

## **解释:**

上面的程序类似于前面讨论的程序。唯一的区别是这次有两个装饰者，而不是一个。

多个装饰器的执行很简单。

*   装饰者总是从室内开始执行。
*   因此，这里首先执行“upper_dec ”,只有在完成这个装饰函数的执行之后，才会执行“lower_dec”装饰函数。

[](/why-map-filter-and-reduce-functions-are-so-famous-4c8e42fd0755) [## 为什么 Map()、Filter()和 Reduce()函数这么出名？

### python 中避免循环和分支的函数式编程

pub.towardsai.net](/why-map-filter-and-reduce-functions-are-so-famous-4c8e42fd0755) 

> ***在 Python 中使用装饰器进行记忆***

我们知道递归的编程概念是反复调用函数，直到结束条件为真。一些使用递归的程序有阶乘、斐波那契等。但是，这些程序中的问题是，已经解决的子问题可能会被重复解决。这导致最终输出的执行延迟。这些程序使用记忆优化。

记忆化只不过是一种记录中间结果的编程技术。并优化程序的运行。这个概念也可以使用函数装饰器来实现。

**程序:**

```
#Simple Factorial program without decorators
def fact(n):
    if n == 1:
        return 1
    else:
        return n * fact(n-1)
print(fact(6))#Factorial program with memoization using decorators
def store_fact(f):
    storage = {}
    def inn(n):
        if n not in storage:
            storage[n] = f(n)
        return storage[n]
    return inn@store_fact
def fact(n):
    if n == 1:
        return 1
    else:
        return n * fact(n-1)
print(fact(6))**Output:** 720
```

## **解释:**

上面的程序类似于其他讨论过的程序。记忆的唯一区别是递归操作甚至在结果存储在“存储器”中之后才发生。这意味着每次需要执行计算时，它首先检查结果是否存储在“存储器”中。如果它被存储，则该值被用作输出，否则该值被计算然后存储在存储器中。

**结论:**

总之，本文涵盖了装饰函数的所有基础知识。我强烈建议阅读更多的文章，并使用 python 程序应用这些概念，因为在这个主题上有许多程序可供您试验。

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