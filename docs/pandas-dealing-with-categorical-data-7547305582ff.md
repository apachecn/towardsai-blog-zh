# 熊猫:处理分类数据

> 原文：<https://pub.towardsai.net/pandas-dealing-with-categorical-data-7547305582ff?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## 用 python 创建系列和数据帧

![](img/18f4c16318f4fc66a2495ceb853f6884.png)

由[马库斯·斯皮斯克](https://unsplash.com/@markusspiske?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

在本文中，我们将使用 python 示例处理 pandas 中的分类数据分析。

类别数据是作为信息一部分的不同变量的群集。数据收集对于了解产品特定分析的统计数据非常重要。

类别数据可分为两组，如下所示:

*   **名义类别:**处理有不同类别的数据。类别可以是字符串或数字形式，但我们不能对这些类型的数据进行数学运算。

例如任何二进制值、邮政编码、性别等。

*   **顺序类别:**这种类型的类别处理顺序或等级类型的数据，这些数据按照比例的顺序定义某些东西。这个数据也不适合数学运算。

例如产品质量、等级、级别等。

涵盖的主题:

```
1\. Creation of series and dataframe in pandas
2\. Working with categories
3\. Order, sorting, and comparisons
4\. Operations and data munging
5\. Memory usage in data types
```

> ***在熊猫*** 中创建系列和数据帧

*   **系列:**这是一个单列，包含用于分析的数据。
*   **Dataframe:** 它是一个以上系列的集合，指一个矩阵形式的多个列，用于数据分析。

## 系列的创建

用于创建系列的函数是 *series()* 带参数: ***数据******指标******d type******name******copy***。

示例:

```
Import pandas as pda = pd.Series(["w", "x", "y", "w"])
a**#output:**
0    w
1    x
2    y
3    w
dtype: object--------------------------------------------------------------
s = pd.Series(["w", "x", "y", "w"], dtype="category")
s**#output:**
0    w
1    x
2    y
3    w
dtype: category
Categories (3, object): ['w', 'x', 'y']
```

在上面的示例中，两个系列的输出相同，但数据类型不同。与对象或字符串类型相比，类别类型在内存使用和速度方面更有优势。

## 数据帧的创建

数据框是数据框中一列或多列的集合。让我们创建一个空数据框。

示例:

```
import pandas as pd

df = pd.DataFrame()
print(df)**#output:**
Empty DataFrame
Columns: []
Index: []
```

从上面的例子来看，空数据框至少需要两个东西，即列和索引。默认情况下，列将作为数据给出，索引将自动添加。

示例:

```
import pandas as pdlist1 = ["w", "x", "y", "w"]
df = pd.DataFrame(list1)
print(df)**#output:**
   0
0  w
1  x
2  y
3  w
```

代码的输出是创建一个包含一列的数据框，该列的索引值或名称为“0”。我们还可以通过在 dataframe 方法中指定列名来给出列名。

示例:

```
import pandas as pdlist1 = ["w", "x", "y", "w"]df = pd.DataFrame(list1, columns=['c'])
print(df)**#output:**
   c
0  w
1  x
2  y
3  w
```

[](/understand-list-with-python-example-5e02a5566ca0) [## 通过 Python 示例了解 List[]

### python 中数据结构的便捷概念

pub.towardsai.net](/understand-list-with-python-example-5e02a5566ca0) [](/class-and-objects-in-python-with-examples-591c6ca95ee6) [## Python 中的类和对象及其示例

### 软件开发程序的便捷概念

pub.towardsai.net](/class-and-objects-in-python-with-examples-591c6ca95ee6) 

> ***处理类别***

我们可以用任何方式对类别进行操作，以在数据框中进行更改。

数据具有类似 category 和 ordered 的属性，可以通过 cat.categories 和 cat.ordered 方法进行检查。

示例:

```
import pandas as pds = pd.Series(["w", "x", "y", "w"], dtype="category")
s.cat.categories**#output:**
Index(['w', 'x', 'y'], dtype='object')
---------------------------------------------------------
s.cat.ordered**#output:**
False
```

*   **重命名类别**

此方法将重命名列中类别的名称。

示例:

```
s = pd.Series(["w", "x", "y", "w"], dtype="category")s.cat.categories = ["Group %s" % a for a in s.cat.categories]
s#output:
0    Group w
1    Group x
2    Group y
3    Group w
dtype: category
Categories (3, object): ['Group w', 'Group x', 'Group y']
```

*   **添加新类别**

我们还可以借助 cat.add_categories 方法在列中添加一个新的类别。

示例:

```
import pandas as pds = pd.Series(["w", "x", "y", "w"], dtype="category")
s = s.cat.add_categories([4])s.cat.categories**#output:**
Index(['w', 'x', 'y', 4], dtype='object')
```

> ***排序、排序和比较***

有时候我们看到品类有一些顺序就知道产品的质量了。因此，我们试图通过一个 python 例子来了解类别的顺序。

示例:

```
import pandas as pd
from pandas.api.types import CategoricalDtypes = pd.Series(["w", "x", "y",
                     "w"]).astype(CategoricalDtype(ordered=True))
s.sort_values(inplace=True)
s**#output:**
0    w
3    w
1    x
2    y
dtype: category
Categories (3, object): ['w' < 'x' < 'y']
```

我们还可以在下面的示例中获得类别的最低和最高级别:

```
s.min(), s.max()**#output:**
('a', 'c')
```

**排序**也是订单类别的一部分。

示例:

```
import pandas as pds = pd.Series([3,4,5,3], dtype="category")
s = s.cat.set_categories([3,4,5], ordered=True)
s.sort_values(inplace=True)
s#output:
0    3
3    3
1    4
2    5
dtype: category
Categories (3, int64): [3 < 4 < 5]
```

**比较:**用于将数据上的序列或列表与布尔输出中的其他序列或列表进行比较，如下例所示:

```
import pandas as pda = pd.Series([1,2,3,4])
b = pd.Series([1,1,3,2])
c = pd.Series([4,1,3,2])------------------------------------------
a > b**#output:**
0    False
1     True
2    False
3     True
dtype: bool
------------------------------------------
b == c**#output:**
0    False
1     True
2     True
3    False
dtype: bool
```

> ***操作和数据管理***

对数据的操作对于查找计数、某些类别和数字数据非常有用，如下例所示:

```
import pandas as pda = pd.Series([4,1,3,3])
a.value_counts()**#output:**
3    2
1    1
4    1
dtype: int64
---------------------------
s = pd.Series(["w", "x", "y", "w"])
s.value_counts()**#output:**
w    2
y    1
x    1
dtype: int64
---------------------------
op = pd.Categorical(["w", "y", "z", "s", "w", "y", "y"],
                                 categories=["x", "y", "z", "s"])
df = pd.DataFrame({"op": op, "values": [3,2,5,6,5,6,3]})
df.groupby("op").mean()**#output:**
op   values
x     NaN
y    3.666667
z    5.000000
s    6.000000
```

**数据管理:**用于操作数据，借助 loc、iloc、at、iat 方法从整个数据帧中选择部分数据。

示例:

```
import pandas as pdlist1 = ["w", "x", "y", "w"]

values = [1, 2, 3, 4]
df = pd.DataFrame({"list1": list1, "values": values})
print(df)**#output:**
  list1  values
0     w       1
1     x       2
2     y       3
3     w       4
---------------------------------------
df.iloc[1:3, :]**#output:**
     list1    values
1     x         2
2     y         3
---------------------------------------
df.loc[1:3, "list1"]**#output:**
1    x
2    y
3    w
Name: list1, dtype: object
---------------------------------------
df.iat[0, 0]**#output:**
'w'
---------------------------------------
```

> ***数据类型中的内存使用量***

当我们讨论数据的内存使用时，对象比类别类型占用更多的内存，如下例所示:

```
s = pd.Series(["happy"] * 1000)#as object 
s.nbytes**#output:**
8000
---------------------
#as category
s.astype("category").nbytes**#output:**
1008
```

> ***结论***

类别和对象是数据框的数据类型，pandas 是帮助处理这些数据类型的库。

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
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)