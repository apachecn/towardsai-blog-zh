# 带示例的 Python 标准库之旅

> 原文：<https://pub.towardsai.net/a-walk-to-the-standard-library-of-python-with-examples-c5140a8ef1a7?source=collection_archive---------0----------------------->

## [编程](https://towardsai.net/p/category/programming)

## python 中提供的一个方便有用的脚本模块

![](img/ba782b2f2a9d0b310e997c5a8516b23e.png)

照片由[克里斯里德](https://unsplash.com/@cdr6934?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

在本文中，我们将讨论 python 中的标准库。它们是 python 中作为库可用的代码片段。程序员可以在他们的代码中使用它们来优化程序或算法。

## 涵盖的图书馆:

```
1\. Math
2\. OS interface
3\. Wildcards
4\. Command line arguments
5\. String pattern matching
6\. Dates and Times
7\. Data compression
8\. Quality control
```

> ***数学库***

数学库允许我们使用 python 中的大多数数学公式。最常见的方法有算术、三角学等。

python 的例子:

```
#import the math library
import math------------------------------------------------------
#The CEIL functionprint(math.ceil(2.9))
print(math.ceil(2.2))**#output:**
3
3
------------------------------------------------------
#The FLOOR functionprint(math.floor(6.1))
print(math.floor(6.9))**#output:**
6
6
------------------------------------------------------
#The SIN functionprint (math.sin(0.00))
print (math.sin(90.00))**#output:**
0.0
0.8939966636005579
------------------------------------------------------
#The Power functionprint(math.pow(2, 4))**#output:**
16.0
------------------------------------------------------
#The RADIAN functionprint(math.radians(90))
print(math.radians(-60))**#output:**
1.5707963267948966
-1.0471975511965976
```

> ***OS 接口库***

它用于访问操作系统功能，以读取、写入、操作、访问目录等。

python 的例子:

```
#importing the OS library
import os------------------------------------------------------
#Working directoryos.getcwd()#output:
'C:\\Users\\Amit'
------------------------------------------------------
#List of function in OSdir(os)**#output:**
['DirEntry',
 'F_OK',
 'MutableMapping',
 'O_APPEND',
 'O_BINARY',
 'O_CREAT',
      |
      |
      |
'walk',
'write']
------------------------------------------------------
#List of files in the directorypath = 'C:\\Users\\Amit'
dirs = os.listdir( path )
for file in dirs:
    print(file)**#output:**
Case_study.html
case_study.xlsx
Contacts
Cookies
cross_validation.ipynb
Customers.csv
Data Frame.ipynb
Data.csv
data.json
data1.json
dataframe practice.ipynb
dataset.csv
Data_Preprocessing.ipynb
```

操作系统模块中有大量的功能。你可以试试别人，做做练习。

[](/understand-time-series-components-with-python-4bc3e2ba1189) [## 用 Python 理解时间序列组件

### 机器学习中预测模型的基本概念及实例

pub.towardsai.net](/understand-time-series-components-with-python-4bc3e2ba1189) [](/data-preprocessing-concepts-with-python-b93c63f14bb6) [## Python 中的数据预处理概念

### 一种为机器学习估值器准备数据的稳健方法

pub.towardsai.net](/data-preprocessing-concepts-with-python-b93c63f14bb6) 

> ***通配符***

它们与正则表达式相关联，用于搜索或改变程序或操作系统中的字符。有些通配符符号是点(。)，星号(*)，问号(？)，等等。

python 的例子:

```
# Regular expression library
import re#List of words
list1 = ["dark", "red", "darker", "blue",
            "darkiest", "orange"]for word in list1:
        #Find all words with dark word
        if re.search('dark*', word) : 
                print (word)**#output:**
dark
darker
darkiest
```

> ***命令行参数***

命令行参数一般存储在 sys 模块中，需要 argv 来获取列表。这些在解释器中使用并由解释器维护。

python 的例子:

```
#Importing library and getting first element of argv list
import sys
print(sys.argv[0])**#output:**
C:\Users\Amit\Anaconda3\lib\site-packages\ipykernel_launcher.py
```

> ***字符串模式匹配***

正则表达式 re 模块提供了字符串处理和搜索模式。

python 的例子:

```
#import the library
import re#Finding a list occurrence of "it" character
str = "Sumit knows Amit"
find = re.findall("it", str)
print(find)**#output:**
['it', 'it']
```

上面的代码在句子中发现了两次“it”字符。搜索功能可以搜索句子中的单词。

```
import restr = "The search function can search the word in the sentence"
a = re.search("can", str)
print(a)**#output:**
<re.Match object; span=(20, 23), match='can'>
```

上面的单词“can”出现在句子的第 20 个位置。

[](https://medium.com/analytics-vidhya/matplotlib-and-seaborn-visualization-with-python-2d51981a1c5a) [## 用 Python 实现 Matplotlib 和 Seaborn 可视化

### 使用两个 python 库可视化医疗保健数据

medium.com](https://medium.com/analytics-vidhya/matplotlib-and-seaborn-visualization-with-python-2d51981a1c5a) 

> ***日期和时间***

这个库可以在日期和时间数据中做有用的操作和提取有用的信息。

python 的例子:

```
#impport the library
from datetime import datetoday_date = date.today()
print(today_date)**#output:**
2021-04-22
------------------------------------------------------
#to find the number of days from birthday datebirthday = date(1998, 7, 31)
age = today_date - birthday
age.days**#output:**
8301
```

> ***数据压缩***

这个库用于将数据压缩和解压缩到比原始数据更少的内存中。常见的函数有 zlib、tarfile、zipfile 等。

python 的例子:

```
#import the library
import zlibstr1 = b'The search function can search the word in the sentence'
len(str1)#output:
55#To compress the data we need compress method
com_str = zlib.compress(str1)
len(com_str)#output:
52
```

> ***质量控制***

这个库用于测试程序的工作状态。doctest 模块测试所有程序，并验证程序是否工作。

python 的例子:

```
def average(nums):
    """Computing average of the numbers print(average([3,4,5,6,7,8]))
    5.5
    """
    return sum(nums) / len(nums)print(average([3,4,5,6,7,8]))
```

doctest 将检查 docstring 和程序的输出是否工作。

```
**#By typing -v in the command**
$ python average.py -v**#it will print the following**Trying:
    average([3,4,5,6,7,8])
Expecting:
    5.5
ok
Trying:
    sum(nums) / len(nums)
Expecting:
    5.5
ok
```

> ***结论:***

在本文中，我们只是概述了 python 中的标准库，但是相信我，还有更多库和属性需要学习。

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —零到英雄与 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)3 .[Python 中的异常处理概念](/exception-handling-concepts-in-python-4d5116decac3?source=friends_link&sk=a0ed49d9fdeaa67925eac34ecb55ea30)
4。[用 Python 进行主成分分析降维](/principal-component-analysis-in-dimensionality-reduction-with-python-1a613006d531?source=friends_link&sk=3ed0671fdc04ba395dd36478bcea8a55)
5。[用 Python 全面讲解 K-means 聚类](https://medium.com/towards-artificial-intelligence/fully-explained-k-means-clustering-with-python-e7caa573176a?source=friends_link&sk=9c5c613ceb10f2d203712634f3b6fb28)
6。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7 全面讲解了线性回归。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[用 Python 实现时间序列的基础知识](https://medium.com/towards-artificial-intelligence/basic-of-time-series-with-python-a2f7cb451a76?source=friends_link&sk=09d77be2d6b8779973e41ab54ebcf6c5)
9。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)
10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)