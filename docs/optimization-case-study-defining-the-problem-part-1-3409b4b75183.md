# 优化案例研究:定义问题—第 1 部分

> 原文：<https://pub.towardsai.net/optimization-case-study-defining-the-problem-part-1-3409b4b75183?source=collection_archive---------0----------------------->

## [优化](https://towardsai.net/p/category/optimization)

## 决定每个品牌有多少部智能手机，以及动态定价是否合理

![](img/906af147ece9a90e40c318dfc413586b.png)

来自 [Unsplash](https://unsplash.com/photos/a_PDPUPuNZ8?utm_source=unsplash&utm_medium=referral&utm_content=creditShareLink)

*这是一个两部分的案例研究，其中* ***我们在第一部分定义了优化问题*** *，而* ***我们使用 Pulp python 库作为工具来解决* [*第二部分*](/optimization-case-study-solving-the-problem-and-deciding-part-2-71c05521be06) 中的业务问题** *。*

## **简介**

优化问题是任何企业的困境。这可以归结为两种决策:要么最大化，要么最小化，无论是利润还是成本。

任何优化问题在解决之前都需要定义三件事

1.  决策变量 s——你能控制什么
2.  目标函数——我们想要达到的目标
3.  约束条件—我们的资源有多有限

典型的优化问题可以用本身就是数学的优化方法来解决。因此，我们需要用数学方法来表示我们上面的组件定义。

> 优化方法的目标是在给定约束的情况下找到目标的最优解。

让我们创造一个场景。

> 假设我们被一家智能手机电子商务公司聘为分析师，该公司销售两大品牌的智能手机:三星和苹果。该公司目前有一个天真的动态定价策略，在一天中不断改变同一款手机的价格。该公司想知道是否决定了一个固定价格，每个品牌需要多少库存，以及坚持他们天真的动态定价是否有意义，即，在给定约束的情况下，它是否使收入最大化？

该公司还不想做 A/B 测试来做这个决定，而是一个优化方法。这能用最优化方法解决吗？大部分情况下，是的。

这里的优化陈述是**每种品牌的手机一天应该卖多少，因为我们一天都有一个固定的价格，我们可以获得最大的收入**。

第二个商业问题是:**这个最优的最大收入是比我们平均一天的收入多还是少？我们是否应该坚持目前的定价策略？**

让我们从阐明我们的三个优化组件开始

*   **决策变量:**我们可以控制每个品牌的库存数量

**数学上，**

```
Our decision variables can be represented as A and Swhere 
A is the number of Apple phone stock 
S is the number of Samsung phone stock
```

*   **目标函数:**我们希望在固定价格的情况下实现收入最大化，并找出 A 和 S 的最佳组合最符合最优解。*(如果这听起来像是线性回归算法的目标，那是因为线性回归算法也被认为是优化算法)。*

**数学上，**

```
Z = P1 * A + P2 * Swhere
Z is the optimal maximum revenueP1 and P2 are the fixed prices of the brands respectively
```

*   **约束条件:**假设我们唯一的约束条件是平均每天可以拥有的手机总量

**数学上，**

```
A + S <= Xwhere
X is the maximum number of phones we can have available. This is should not be confused as the decision variables. Even though we have a maximum capacity constraint, we still have the free will to decide how we want to allocate the quantity available to each of the brands i.e should we have more of apple or less of apple and vice versa
```

很高兴知道优化方法强调的是**最优解决方案**，这意味着业务解决方案可以有三种风格

*   不满足约束的解决方案，即不可行的解决方案
*   满足约束的解决方案，即可行且可接受的解决方案
*   在可接受的解决方案中，有一个最优的最佳解决方案

## **我来给大家介绍一下数据。**

该数据有 4 个基本列:时间戳、日期、品牌和每个手机品牌在不同时间的价格。

由作者在 DataPane 中创建

让我们做一个快速 EDA 来提取我们需要的重要数字，它们是

*   我们想要使用的固定价格
*   容量限制
*   我们目前平均每天的收入

**假设该品牌智能手机在 2020 年的销售价格会有变化**，这取决于一天中的时间。

让我们通过获得每个手机品牌的平均价格分布并将这些价格用作每个品牌在一天中任何时间的固定价格来简化事情。

```
def average_price(data):"""Get the average price per brand by summing the unique variation of prices over time and dividing it by the count of variations"""    brand_price = {} for i in list(data['brand'].unique()): list_price_sum = sum(data[data['brand']==i]['price'].unique()) unique_price_count = data[data['brand']==i]['price'].nunique() avg_price = list_price_sum/unique_price_count brand_price[i] = round(avg_price , 2) return(brand_price)average_price_per_brand = average_price(smartphone_data) >>>> Output{'apple': 788.53, 'samsung': 425.81}
```

从上面的分析中，我们分别得到苹果和三星智能手机的`$788.53`和`$425.81`。因此，我们可以在我们的目标方程中估算这些数字。

```
Z = 788.53A + 425.81S
```

**为了得到容量限制，**让我们简化一下，计算手机总销量，然后除以数据中可用的天数，得到**每天可用的平均手机库存。** *(我们假设每天所有的存货都卖完了)*

```
def average_phone_available(data):"""Get the average daily stock of phones by getting all the phones sold so far and dividing it by the number of days recorded""" inventory_sold = data.shape[0] days_so_far = data['date'].nunique() average_inventory_available = inventory_sold/days_so_far return(round(average_inventory_available,0))average_inventory_available = average_phone_available(smartphone_data)>>> Output694.0
```

从上面的分析中，我们得到了`694.0`平均可用库存。这样，我们可以用数学方法完成约束方程，如下所示

```
A + S <= 694.0
```

谜题的最后一块是知道我们目前每天赚多少钱。*(虽然这不是优化问题直接需要的，但在回答第二个问题陈述(是否坚持我们的动态定价)时会需要)*

对于这个**(同样，为了简化起见)**，我们将得到迄今为止获得的总收入，并用它除以记录的天数，以近似得到**该公司在该时刻的日收入**。

```
def average_revenue(data):"""Get the average revenue made in a day by getting the sum of revenue made so far divided by the number of days recorded""" revenue_so_far = sum(data['price']) days_so_far = data['date'].nunique() average_daily_revenue = revenue_so_far/days_so_far return (round(average_daily_revenue,2))revenue_daily_average = average_revenue(smartphone_data) >>> Output 247963.17
```

我们开始四处走动。这是该公司目前使用简单的动态定价策略平均每天输出的收入。

现在我们已经定义了所有的变量和方程，让我们使用 python 来解决优化问题。

***在下面的文章***[***中了解如何使用 python 库解决这个业务案例问题。***](/optimization-case-study-solving-the-problem-and-deciding-part-2-71c05521be06)

## 常见问题解答

*   **在哪里可以找到使用的原始数据集？** *你可以在* [*中找到数据集*](https://www.kaggle.com/mkechinov/ecommerce-purchase-history-from-electronics-store) *。然而，我使用原始版本的一个干净子集来简化案例研究。你可以在 Github 的* ***上* *这里找到我的清理程序和分析* [*。*](https://github.com/anitaokoh/smartphone-quantity-optimization)**
*   **你为什么用苹果和三星？是因为它们一般都是大众品牌吗？** *很遗憾，没有，我做了一个快速的探索性分析，看到智能手机是原始数据集中需求最多的，苹果和三星也是最受欢迎的品牌。可以说这些数据很好地代表了现实世界。*
*   **优化问题就这么简单？** *Lol，不，不总是。当你需要考虑更多的决策变量和约束时，事情就变得复杂了。*
*   我们真的需要约束吗？ *Lol。好主意。资源永远是无限的吗？*