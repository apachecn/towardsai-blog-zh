# 数据科学如何依赖熊猫和 Numpy？

> 原文：<https://pub.towardsai.net/how-data-science-depends-on-pandas-and-numpy-377eb9c4b673?source=collection_archive---------1----------------------->

## 熊猫和 Numpy 在数据科学和机器学习中发挥着至关重要的作用

![](img/56122ff86c59cbe9f381d144e316bdf5.png)

亚历克斯·丘马克在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

**简介**

当你从网上提取数据时，获得的数据不一定总是干净的或结构化的，对吗？Python 为我们提供了一个特性，使用 Pandas data frames(Python 中的一个包)来构造这些杂乱的数据。

在讨论熊猫数据框之前，让我们先了解一下什么是数据框。数据帧以二维结构的形式存储数据；以由行和列组成的表格的形式。这意味着表中的每一行都可以是任何数据类型:数值、字符、空或非空。

熊猫数据框与普通数据框相似，唯一的区别是列可以是不同的类型。一般来说，Pandas 数据框架由三个主要部分组成:索引、列和数据。

让我们通过熊猫数据框架来看几个实际例子。

**注意:**确保在使用 Pandas 数据框时导入以下库:

```
import numpy as np
Import pandas as  pd
```

## 涵盖的主题

```
**1\. Creating an Empty data frame
2\. Dates in Pandas dataframe while importing data
3\. Reshaping a dataframe
4\. Iterating a dataframe
5\. Writing a dataframe to a file**
```

> ***创建空数据帧***

使用 Pandas 开发一个空数据框；来获取我们将来要添加的数据的结构。

在 Pandas 中，数据框是通过使用' data frame()'函数和传递值来创建的:数据、列和索引。

让我们看看它是如何工作的:

**程序:**

**#1**

```
import numpy as np
import pandas as pddF = pd.DataFrame(np.nan, index=[0,1,2,3], columns=[‘Column1’])
print(dF)
```

**#2**

```
import numpy as np
import pandas as pddF=pd.DataFrame(index=range(0,5),columns=['Column1'], dtype=’str’)print(dF)
```

**输出:**

```
Column10 NaN
1 NaN
2 NaN
3 NaN
```

**解释:**

在第一个程序中，你可以看到我们正在使用' DataFrame()'函数。在函数内部，我们将值作为“np.nan”进行传递，用 nan 值初始化您的数据框。接下来，我们初始化索引值，并为包含 NaN 值的列提供一个名称。当程序运行时，您将得到一个由 nan 组成的数据框，输入列名和索引。

**注意:'** np.nan '默认为' float '数据类型。

第二个程序与第一个程序有一点不同。在某些情况下，您可能需要数据框具有特定的数据类型。在这种情况下，我们使用这种方法。这里，我们只是初始化数据框的索引、列名和数据类型。获得的输出将与第一个程序的输出相同。

> ***导入数据时熊猫数据框中的日期***

熊猫在导入数据时发现很难识别日期。但是有一种方法可以让它识别，那就是传递“parse_dates”参数。

**例如:从 CSV 文件中读取数据**

```
import pandas as pdpd.read_csv(‘filename’, parse_dates=True)
```

#或此选项:

```
pd.read_csv(‘filename’, parse_dates=[‘C_name’])
```

上面的程序是为了帮助熊猫识别日期列。

但是有时候，即使传递了这个参数，解析器也会抛出一个错误。这主要是由于格式问题。下面的程序将告诉你解决这个问题的方法。

**节目:**

```
import pandas as pdparser = lambda x: pd.datetime.strptime(x, ‘%Y-%m-%d %H:%M:%S’)# read command:
pd.read_csv(infile, parse_dates=[‘Column1’], date_parser=parser)# Or combine two columns to one DateTime column
pd.read_csv(infile, parse_dates={‘datetime’: [‘date’, ‘time’]}, date_parser=parser)
```

**解说:**

当您在 Pandas 中处理日期时，检查格式是很重要的。这是因为熊猫遵循特定的格式，当我们试图读取包含日期列的 CSV 或 excel 文件时，它可能会抛出错误。但是我们可以通过创建自己的解析器来解决这个问题，也就是说，通过使用 lambda 函数。这里，我们创建了一个 lambda 函数，它将获取日期时间并使用字符串格式控制它。

> ***重塑一个数据帧***

对数据框进行整形，使生成的结构更易于理解，以便分析获得的数据。这一步在数据分析领域非常关键。重塑不仅仅意味着格式化；也改变了我们看待或处理数据的方式。

让我们看看一些重塑技术:

*   **旋转数据框**

使用 pivot()函数旋转数据框。此函数以一种由于大量值而导致多个索引列的方式重塑数据框。

**注意:** pivot()函数不支持数据聚合

pivot()函数基本上有 3 个参数:

1.  **值:**您可以指定希望在数据透视表中看到的原始数据框中的值。
2.  **列:**这将是结果表中的列。
3.  **索引:**这将是最终表格中的索引。

**程序:**

```
import pandas as pd# Creating your DataFrameproducts = pd.DataFrame({‘category’: [‘Red’, ‘Red’, ‘Blue’, ‘Blue’, ‘White’, ‘White’],
‘Shade’: [‘Dark’, ‘Light’, ‘Dark’, ‘Medium’, ‘Light’,’Dark’],
‘Cost’:[11.42, 23.50, 19.99, 15.95, 55.75, 111.55]
})pivot_products = products.pivot(index=’category’, columns=’Shade’, values=’Cost’)print(pivot_products)
```

**输出:**

```
Shade        Dark     Light     Medium
categoryBlue          19.99    NaN       15.95Red           11.42    23.50      NaNWhite         111.55   55.75      NaN
```

**解释:**

这里，我们首先传递所有三个参数来形成数据框。然后我们使用 pivot()函数，它最终将整形后的数据显示为输出。

注意:需要注意的是，你的数据不能包含重复的列值，否则你会得到一个错误信息。如果您的数据不是唯一的，那么尝试 pivot_table()方法。

*   **使用 Melt()重塑数据帧**

当您的数据中有多个列是标识符变量时，可以使用 melting 方法。

**程序:**

```
# The DataFramepeople = pd.DataFrame({‘First Name’ : [‘Mary’, ‘Peter’],‘Last Name’ : [‘Tony’, ‘Pepper’],‘Subject’ : [‘English’, ‘Math’],‘Marks’ : [90, 84]})
```

**使用熔化()数据帧**

```
print(pd.melt(people, id_vars=[‘First Name’, ‘Last Name’], var_name=’Categories’))
```

**输出:**

```
 First Name      Last Name     Categories    value0    Mary           Tony           Subject     English1    Peter          Pepper         Subject      Math2    Mary           Tony           Marks        903    Peter          Pepper         Marks        84
```

**解释:**

首先，创建数据框。接下来，我们将使用“melt”函数，其中我们将第一个参数作为“people”(创建的数据框)传递。然后是标识符变量(名、姓)，最后是所有测量值(主题、标记将在“类别”列名下)。

> ***迭代数据帧***

**程序:**

```
import numpy as npdf = pd.DataFrame(data=np.array([[10, 11, 12], [13, 14, 15], [16, 17, 18]]), columns=[‘col1’, ‘col2’, ‘col3’])for index, row in df.iterrows() :
    print(row[‘col1’], row[‘col2’], row[‘col3’])
```

**输出:**

```
10 11 12
13 14 15
16 17 18
```

**解释:**

上面的程序使用一个 for 循环和一个 itterrows()函数的组合来迭代一系列数据。首先，我们创建了一个数据框。接下来，当调用 print 函数时，它首先显示“col1”中的所有值。当循环结束时，它移动到下一行，并继续打印下一列的值，直到循环结束。

> ***将数据帧写入文件***

**程序:**

```
**#1**import pandas as pd
df.to_csv(‘filename.csv’)**#2 — delimiting by a tab**import pandas as pd
df.to_csv(‘filename.csv’, sep=’\t’)**#3 — writing a dataframe to excel**import pandas as pdwriter = pd.ExcelWriter(‘filename.xlsx’)
df.to_excel(writer, ‘DataFrame’)
writer.save()
```

**说明:**

第一个程序向我们展示了将 pandas 数据帧写入 CSV 文件的语法。但是现在，你的数据是用 CSV 格式写的，没有任何分隔符。所以，如果你想添加一个分隔符，使用' sep '参数，如第二个程序所示。第三个程序是将数据框写入并保存到 excel 文件中。

> ***结论***

总之，本文涵盖了 Pandas 数据框架中的一些重要主题。我强烈建议阅读更多的文章，并使用 python 程序应用这些概念。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [Twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

1.[8 Python 的主动学习见解收集模块](/8-active-learning-insights-of-python-collection-module-6c9e0cc16f6b)
2。 [NumPy:图像上的线性代数](/numpy-linear-algebra-on-images-ed3180978cdb?source=friends_link&sk=d9afa4a1206971f9b1f64862f6291ac0)3。[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[熊猫:处理分类数据](/pandas-dealing-with-categorical-data-7547305582ff?source=friends_link&sk=11c6809f6623dd4f6dd74d43727297cf)
5。[超参数:机器学习中的 RandomSeachCV 和 GridSearchCV](/hyper-parameters-randomseachcv-and-gridsearchcv-in-machine-learning-b7d091cf56f4?source=friends_link&sk=cab337083fb09601114a6e466ec59689)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[数据分发使用 Numpy 与 Python](/data-distribution-using-numpy-with-python-3b64aae6f9d6?source=friends_link&sk=809e75802cbd25ddceb5f0f6496c9803)
9。[机器学习中的决策树 vs 随机森林](/decision-trees-vs-random-forests-in-machine-learning-be56c093b0f?source=friends_link&sk=91377248a43b62fe7aeb89a69e590860)
10。[用 Python 实现数据预处理的标准化](/standardization-in-data-preprocessing-with-python-96ae89d2f658?source=friends_link&sk=f348435582e8fbb47407e9b359787e41)