# R 的离散概率分布

> 原文：<https://pub.towardsai.net/discrete-probability-distributions-with-r-2ab00ce39cfe?source=collection_archive---------2----------------------->

## [统计数据](https://towardsai.net/p/category/statistics)

## 概率分布描述了事件的随机过程

![](img/8846b108107b670c66123412b2e6143f.png)

由[穆罕默德·拉赫马尼](https://unsplash.com/@afgprogrammer?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

> ***离散概率分布***

在详细进入正题之前，我们必须知道概率分布到底是什么意思？

更简单地说，概率分布用概率来描述随机过程(任何现象)。

## 随机过程到底是什么？

随机事件是一个随机过程，我们永远无法找到它的精确值或精确概率。唯一的方法就是预测它。

例如，我们可以说，

*   抛硬币(我们不知道结果；可以是头也可以是尾)。
*   从一副牌中抽出一张牌(可以是 52 张牌中的任何一张)。
*   用概率来描述任何事件都是概率分布

概率分布有两种类型

1.  分离的
2.  连续的

> ***解释—离散概率分布***

在这里，我们将讨论一些离散分布以及如何使用它们。但是首先，让我们来看看离散分布的确切含义。

当任何随机事件的结果是可数的、有限的、非负整数的离散类型，以及具有无限小数的任何数字时，则概率在离散分布的帮助下被投影或建模。

掷骰子的基本例子

```
X represents the value of a discrete random variableP(X) represents the associated probability
```

现在新出现的是随机变量。这是任何结果都可能达到的量化值。在这里，X 可以取值 1，2，3，4，5，6，因为当你掷骰子时，只有这些值会出现。

因此，在工作时，我们需要注意两点。

任何随机变量可以取的值和它们相关的概率。

## ***一个概率分布的条件***

*   对于 X 的每个值，P(X)总是大于 0
*   在任何情况下，X 的每个值的所有相关概率的总和都等于 1。

(原因很简单，因为概率总是在 0 到 1 之间&它永远不会大于 1)

**P(X)** 用专业术语来说叫做概率质量函数(pmf)。

分析上面讨论的例子的条件，我们看到

```
X = 1, here P(X) = 1/6 (approx. 0.167)
X = 2, here P(X) = 1/6
X = 3, here P(X) = 1/6
X = 4, here P(X) = 1/6
X = 5, here P(X) = 1/6
X = 6, here P(X) = 1/6
```

这里满足了条件(1 )&对于条件(2 ),总概率加起来是 1。

**考虑一些离散的概率分布函数以及在 R 中寻找相关概率的方法**

[](/in-depth-introduction-of-analysis-of-variance-anova-with-r-examples-47c2805d9524) [## 用 R 个例子深入介绍方差分析(ANOVA)

### 特征关系分析的统计工具

pub.towardsai.net](/in-depth-introduction-of-analysis-of-variance-anova-with-r-examples-47c2805d9524) [](/hypothesis-testing-for-known-and-unkown-population-with-t-test-and-anova-8a00b457c48f) [## 用 T 检验和方差分析对已知和未知总体进行假设检验

### 两个及两个以上独立样本，具有标准偏差

pub.towardsai.net](/hypothesis-testing-for-known-and-unkown-population-with-t-test-and-anova-8a00b457c48f) 

> ***均匀离散分布***

当每个事件发生的概率相等时，存在均匀离散分布。我们讨论的掷骰子的例子是一个均匀离散分布的例子。X 取任意值的概率(几率)是 1/6。

***求骰子显示的概率 2***

```
Here, we find P(X=2)
```

**R 中的实现**

```
#Storing the possible values of X (1 to 6)
X<-1:6>length(X[X=2])/length(X)#output:
[1] 0.1666667
```

***求骰子显示的概率 6***

在这里，我们发现 P(X=6)

```
>length(X[X=6])/length(X)#output:
[1] 0.1666667
```

类似地，我们也可以对其他值做同样的事情。

同样，如果我们 ***想求出 P(X < =3)***

我们手动得到= P(X = 1)+P(X = 2)+P(X = 3)= 1/6+1/6+1/6 = 1/2

**换 R**

```
>length(X[X<=3])/length(X)#output
[1] 0.5
```

> ***二项分布***

当我们的结果只有两种可能性，要么成功，要么失败时，就会出现这种情况。

这个分布求解 n 次试验的成功次数。

在应用这个分布的时候，我们需要知道一些函数。

```
dbinom() :
```

计算某个固定值 P(X=3)的概率

```
pbinom() :
```

计算累积概率为，P(X <=3)

## Consider an example

A group that consists of ten children, each of them been independently infected by some severe disease. The survival probability of the disease is 70%.

(It simple means we have n=10 and p= probability of surviving is 0.70 and q = 1-p = 0.30)

**找出恰好五个孩子存活的概率**

它仅仅意味着我们必须找到 P(X=5)

所以，

**使用 R 实现**

```
#USING dbinom(x,n,p)>dbinom(5,10,0.70)#output:
[1] 0.1029193
```

**找出少于 5 名儿童存活的概率**

这里我们必须找到 P(X <5) means P(X<=4)

So,

```
#USING pbinom(x,n,p)>pbinom(4,10,0.70)#output:
[1] 0.04734899
```

**找到至少 7 个孩子存活的概率**(意味着存活的孩子是 7、8、9 或 10)

这里我们必须找到 P(X>=7)，即 P(X=7) + P(X=8) + P(x=9) + P(X=10)

或者，

1-P(X <=7) makes our process much simpler.

```
#USING pbinom(x,n,p)>1-pbinom(7,10,0.70)#output:
[1] 0.3827828
```

> ***几何分布***

这种分布与二项式分布相同，但主要区别是，在二项式分布中，我们有固定数量的观察值，而在几何分布中，我们不断迭代或重复这一过程，直到观察到第一次成功。

考虑一个投掷硬币十次的场景。

在这里，根据二项式，找出头部恰好出现六次的概率。

但是，如果我们反复投掷硬币，直到第一个头像出现，那么我们遵循几何分布。

## 例子

独立假设生女孩的概率为 0.51。

**找出一个女人的第三个孩子是她第一个女儿的概率**

这里 X=3

```
#using dgeom(X-1,p)>dgeom(2,0.51)#output:
[1] 0.122451
```

**找出一个女人在生第一个女儿之前最多生 4 个儿子的概率**

这里，我们必须找到 P(X <=4)

So,

```
#using pgeom(X,p)
>pgeom(4,0.51)#output:
[1] 0.9717525
```

**,找到这个女人在生第一个女儿**之前有 2 个以上儿子的概率

这里，P(X>2)表示 1-P(X <=2)

So,

```
#using pgeom()
>1-pgeom(2,0.51)#output:
[1] 0.117649
```

> ***泊松分布***

泊松与成功和失败无关。在这里，我们不知道试验的数量，但是知道在某个时间间隔内发生的事件的平均数量。

当给定事件发生的平均速率时，它用于计算事件发生的可能性。

考虑一个保险公司的例子，该公司每月收到 2 起索赔

***求公司一个月收到 5 次索赔的概率***

```
#using dpois(x,m=rate)
>dpois(5,2)#output:
[1] 0.03608941
```

**找出公司在一个月内收到至少 4 份索赔的概率**

这里，我们必须找到 P(X>=4)

或者说，1-P(X<=3)

```
#Using ppois(x,m)
>1-ppois(3,2)#output:
[1] 0.1428765
```

> **结论 **

本文用 R 语言的例子解释了概率分布。

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