# 优化案例研究:解决问题和决策—第二部分

> 原文：<https://pub.towardsai.net/optimization-case-study-solving-the-problem-and-deciding-part-2-71c05521be06?source=collection_archive---------3----------------------->

## [优化](https://towardsai.net/p/category/optimization)

## 如何使用 Pulp python 库作为优化方法来决定动态定价是否有意义

![](img/a67b1be9caef2102c5855acd8147ab7e.png)

来自 [Unsplash](https://unsplash.com/photos/LPckxbrqE5w?utm_source=unsplash&utm_medium=referral&utm_content=creditShareLink)

*这是一个两部分的案例研究，其中* ***我们在* [*第一部分*](/optimization-case-study-defining-the-problem-part-1-3409b4b75183)****中定义了优化问题*** *，在第二部分*中我们使用 Pulp python 库作为工具来解决业务问题*** **。**

## ***简介***

*从[之前的文章](https://medium.com/@anitaokoh/optimization-case-study-defining-the-problem-part-1-3409b4b75183)中，我们能够定义决策变量、目标函数和约束条件。让我们快速复习一下数学。*

*   ***决策变量***

```
*Our decision variables can be represented as A and Swhere 
A is the number of Apple phone stock 
S is the number of Samsung phone stock*
```

*   ***目标函数***

```
*Z = 788.53A + 425.81Swhere 
Z is the optimal maximum revenue
788.53 and 425.81 are the fixed prices of the brands respectively*
```

*   ***约束***

```
*A + S <= 694.0where
X is the maximum number of phones we can have available.*
```

*要添加的其他简单约束**有***

```
*A >= 0
S >= 0i.e the number of each brand phones available can’t be negative*
```

**请注意，根据您的业务问题，需要考虑的约束可能不止一个**

*优化语句通常是这样写的*

```
*The Objective is to maximize revenue
Z = 788.53A + 425.81SSubject to:
A >= 0
S >= 0
A + S <= 694.0*
```

*知道我们的决策变量本质上是整数而不是连续的也很好，也就是说，一个电话不可能是两半的。*(这些信息在应用于 python 时会很有用)**

## *一头扎进解决方案*

*正如上一篇文章中提到的，我们将使用 python 来解决这个优化问题，这要归功于一个叫做 Pulp 的 python 库。*

> *Pulp 是一个用 python 编写的线性和整数编程问题的建模框架。*

*对于像我这样懒惰的程序员，我更喜欢**简单易用的**库，使用 Pulp 解决优化问题非常简单。*

**(然而，代码可能会变得复杂。同样，这只会是因为你的优化变量变得复杂)**

*纸浆建模过程分为 5 个步骤*

1.  *初始化模型(很明显)*
2.  *定义决策变量*
3.  *定义目标函数*
4.  *定义约束*
5.  *求解模型*

***让我们从安装包和导入库**开始*

```
*!pip install pulpfrom pulp import **
```

**关于纸浆的更多信息，这里的*[](https://www.coin-or.org/PuLP/pulp.html)**是足够好的文档***

**我们**通过命名问题来初始化模型**。*(这可以是任何名称。良好的做法是描述清楚)*然后指定目标:是**最小化**还是**最大化****

```
**Model = LpProblem(name=’Find the optimal brand smartphone quantity’, sense= LpMaximize)**
```

**我们通过在库中指定四个主要参数来定义决策变量**

*   **`name` —变量的名称，即苹果或三星*(也可以表示为 A 和 S)。***
*   **`lowbound` / `upbound` —即什么是可接受的最低/最高数量的决策变量。在这种情况下，我们可以有零个电话号码，但不能低于。**
*   **`cat` —变量类型*(整数、二进制或连续)*。在这种情况下，它是一个整数变量，因为我们不能卖半部手机。**

**注意，`lowbound`和`upbound`参数的默认值是`None`，即如果没有指定，则默认为`None`。这同样适用于默认为`continuous`的`cat`a 参数**

**在 Pulp 中，我们这样定义每个决策变量**

```
**A = LpVariable('Apple', lowBound=0, cat='Integer')S = LpVariable('Samsung', lowBound=0, cat='Integer')**
```

**通过使用名为 **model** 的初始化模型变量和名为 **A** 和 **S.** 的决策变量，在模型中定义目标函数相当简单**

```
**model += average_price_per_brand['apple'] * A + average_price_per_brand['samsung'] * S**
```

***注意，我们只是复制了模型*中的目标方程**

**在模型中定义约束的**也是如此****

```
**model += 1* A + 1 * S <= average_inventory_available**
```

**最后，我们**求解模型****

```
**model.solve()**
```

**让我们来看看一天中收入最大化的品牌手机的最佳数量**

```
**print("Stock {} Apple ".format(A.varValue))print("Stock {} Samsung".format(S.varValue))>>> OutputStock 694.0 Apple Phones
Stock 0.0 Samsung Phones**
```

**这是整个优化代码的样子**

**由作者创建**

**使用这些数字，让我们来计算我们可以获得的最大收益。**

```
**maximum_revenue = average_price_per_brand['apple'] * A.varValue + average_price_per_brand['samsung'] * S.varValueprint('$' + str(maximum_revenue))>>> Output
$547239.82**
```

**根据我们当前的定价策略，通过快速比较新的最大化收入与当前日均收入，我们可以看到，如果我们将每部品牌手机的价格固定在 **120.69%** 之前，我们会赚更多的钱。(*参见下面的代码。还要记住，当前的日平均收入是* `*247963.17)*`**

```
**print(str(round(((maximum_revenue - current_revenue)/ current_revenue) * 100.0,2)) + '%')>>> Output 
120.69%**
```

**你可以在 Github 的中找到完整的代码**

> **对该公司的建议是转向固定定价策略。**

*****免责声明:这是一个简单的解决方案，因为还可以考虑其他因素，如需求的季节性、每个品牌的手机类型、定价对客户流失或客户行为的影响等。，这会影响定价策略的使用。*****

## **让我们以一个常见问题来结束。**

*   ****除了 python，还有其他解决优化问题的方法吗？** *有，有。事实上，不使用库也可以用图形解决上面的简单问题。这取决于问题的复杂程度和你喜欢使用的工具/程序/求解器。为 3 个基本组成部分(决策变量、目标函数和约束)建立正确的定义是关键。***
*   ****优化问题是不是只存在于业务问题中？** *绝对不行。也可以识别日常生活中的优化问题。例如，考虑到你有限的资源，决定是否现在就辞职，去追求你梦想中的工作，同时考虑年龄和收入限制，或者决定投资什么样的投资组合。* [*这里的*](https://www.youtube.com/watch?v=7yZ5xxdkTb8) *是一个 youtube 视频，讲述了使用纸浆应用优化程序的其他令人兴奋的方法。***