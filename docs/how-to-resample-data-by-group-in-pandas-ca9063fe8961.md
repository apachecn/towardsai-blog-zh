# 如何在 Pandas 中按组重采样数据

> 原文：<https://pub.towardsai.net/how-to-resample-data-by-group-in-pandas-ca9063fe8961?source=collection_archive---------2----------------------->

## [数据科学](https://towardsai.net/p/category/data-science)

## 一个伟大的工具来消除一个因素的影响

![](img/2a32b868ad011dd51ea01c94a28f155d.png)

有时候，当我们在进行机器学习项目时，有一些因素会对性能产生巨大的影响，并且它们是不可管理或结构化的。一个解决方案是通过基于我们想要标准化的因子进行采样来消除它们在我们的数据中的影响。

让我们为我们的数据创建数据:

假设我们有一个名为“活动”的因素，包含以下几个组:

*   活动 1: **智能手机**相关
*   战役二:**摄像机**相关
*   战役 3: **电脑**相关

```
import pandas as pd
import numpy as np
import statsmodels.formula.api as smf
import plotly.express as px

Smartphone = pd.DataFrame(
    {
        "Gender": np.random.choice(["m", "f"], 200, p=[0.6, 0.4]),
        "Age": np.random.choice(["[<30]", "[30-65]", "[65 ]"], 200, p=[0.3, 0.6, 0.1]),
        "Add_Color": np.random.choice(["Blue", "Red"], 200, p=[0.6, 0.4]),
        "Campaign": ["Smartphone"] * 200,
        "Click": np.random.binomial(1, size=200, p=0.6),
    }
)

Camera = pd.DataFrame(
    {
        "Gender": np.random.choice(["m", "f"], 200, p=[0.6, 0.4]),
        "Age": np.random.choice(["[<30]", "[30-65]", "[65 ]"], 200, p=[0.3, 0.6, 0.1]),
        "Add_Color": np.random.choice(["Blue", "Red"], 200, p=[0.3, 0.7]),
        "Campaign": ["Camera"] * 200,
        "Click": np.random.binomial(1, size=200, p=0.2),
    }
)

Computer = pd.DataFrame(
    {
        "Gender": np.random.choice(["m", "f"], 200, p=[0.6, 0.4]),
        "Age": np.random.choice(["[<30]", "[30-65]", "[65 ]"], 200, p=[0.3, 0.6, 0.1]),
        "Add_Color": np.random.choice(["Blue", "Red"], 200, p=[0.25, 0.75]),
        "Campaign": ["Computer"] * 200,
        "Click": np.random.binomial(1, size=200, p=0.25),
    }
)

df=pd.concat([Smartphone,Camera,Computer])

df.sample(10)Gender      Age Add_Color    Campaign  Click
115      m    [<30]       Red  Smartphone      1
12       m  [30-65]       Red    Computer      0
112      m  [30-65]       Red    Computer      0
148      m    [<30]       Red    Computer      1
127      m    [<30]      Blue    Computer      0
83       f    [<30]       Red  Smartphone      1
168      f  [30-65]       Red    Computer      0
80       f  [30-65]       Red    Computer      0
25       m    [<30]       Red      Camera      0
11       f  [30-65]       Red  Smartphone      0
```

下面我们可以看到，每个组都有不同的点击率。如果我们想在我们的模型中使用这个特性，这是可以的。然而，如果我们不能使用它(也许因为将来我们可能会有不同的活动，我们想建立一个通用的模型)，我们必须以某种方式消除这种影响，否则我们将得到一个有偏见的模型。

```
print(df.groupby('Campaign').mean())Click
Campaign         
Camera       0.21
Computer     0.22
Smartphone   0.59
```

我们想要实现的是对每个组进行重新采样，以获得相等的点击率。

# 按组重新采样数据

在我们的例子中，我们正在处理点击。所以，我们有两个类， **0** 和 **1** 。我们想要实现的是每一个活动都有相同的数量，所以点击率将是 0.5。我们将使用熊猫函数**示例**。基本上，它所做的是给定一个数据帧和一个数字，它用这个数字得到等量的随机行，没有**替换。**

这里棘手的部分是，我们必须为每个活动定义少数群体和多数群体类别，因为正如我们所见，智能手机活动的少数群体类别是类别 **0** 而电脑和相机的少数群体是 **1** 。

```
#get the unique campaigns
campaigns=df.Campaign.unique()

sampled=pd.DataFrame()
for i in campaigns:
    print(i)
    #keep the campaign we want to sample
    z=df.query(f'Campaign=="{i}"')

    A=z[z['Click']==0][['Click']]
    B=z[z['Click']==1][['Click']]

    #find out which is the Minority and Majority
    if len(A)>len(B):
        majority=A
        minority=B
    else:
        majority=B
        minority=A

    #Sampling
    indexes=majority.sample(len(minority),random_state=7).index
    #what we did here is to get the indexes that are NOT in the sampling above
    #so we can remove them in the following steps from our dataframe z
    indexes=majority.loc[~majority.index.isin(indexes)].index

    z=z.loc[~z.index.isin(indexes)]
    sampled=pd.concat([sampled,z])

sampled.groupby('Campaign').mean()Click
Campaign         
Camera        0.5
Computer      0.5
Smartphone    0.5
```

# 结束语

我们丢失了一些数据，但我们正在生成更有意义的数据用于我们的模型。这不是处理此类问题的唯一方法，而是我们正在使用的一种简单解决方案。有偏差的数据是机器学习中最常见的问题之一，可能会导致重大问题，所以这是一个添加到您的工具集中的好工具。

*原载于【https://predictivehacks.com】[](https://predictivehacks.com/how-to-resample-data-by-group-in-pandas/)**。***