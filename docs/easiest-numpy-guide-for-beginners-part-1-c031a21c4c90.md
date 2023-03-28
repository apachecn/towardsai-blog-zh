# 初学者最简单的数字指南第 1 部分

> 原文：<https://pub.towardsai.net/easiest-numpy-guide-for-beginners-part-1-c031a21c4c90?source=collection_archive---------4----------------------->

## [编程](https://towardsai.net/p/category/programming)

![](img/25d268f973ade3577d6c27abfae7c87c.png)

来源:[全栈 Python](https://www.fullstackpython.com/scipy-numpy.html)

## 什么是 Numpy？

Numpy 是一个 python 库，用于执行与线性代数、矩阵相关的数学运算。Numpy 实际上代表*数字 python* ，它在处理数字时比其他任何数据类型都要快得多。

## 使用 NumPy 库我们可以执行哪些操作？

1.  创建数组

```
**Input:**
import numpy as np
l=[10,20,30]
np1=np.array(l)
type(np1)**Output:** [10 20 30]
numpy.ndarray**Input:** l=[[1,2],[5,6],[7,8]]
np2=np.array(l)
print(np2)**Output:** [[1 2]
 [5 6]
 [7 8]]
```

在上面的代码中，我通过使用一个列表或列表的列表创建了一个 NumPy 数组，我们也可以通过使用一个 ***元组或简单地传递一个数字来创建一个数组。***

2.更改 NumPy 数组中元素的类型

```
**Input:**
np2_float= np.array(l,dtype=’float’)
print(np2_float)**Output:** [[1\. 2.]
 [5\. 6.]
 [7\. 8.]]**Input:**
print(np2.astype('float'))     #np2 is name of the array declared**Output:** [[1\. 2.]
 [5\. 6.]
 [7\. 8.]]
```

NumPy 数组中的数字类型可以通过使用 dtype 关键字或使用 astype()函数来更改。该类型可以更改为 float64、str、int32 和 complex128 数据类型。

3.知道 NumPy 数组的维数

ndmin 代表 n 维，用于通过简单地使用关键字 ndimn 来创建多维数组

```
**Input:**
x=np.array(10)
y=np.array([10,20])
z=np.array([[10,20],[30,40]])
print(x.ndim)
print(y.ndim)
print(z.ndim)**Output:** 0
1
2***Creating a multidiamensional numpy array***
**Input:** arr = np.array([10, 20, 30, 40], ndmin=5)
print(arr)**Output:**
[[[[[10 20 30 40]]]]]
```

4.使用 Nan 和 Inf

Nan 代表非数字，Inf 代表无穷大。有时，数据集中存在未定义的值，这会对数学计算产生不利影响，并导致计算中出现问题，该问题可以通过使用 Nan 来解决。这些 Nan 值也可以通过使用列的平均值、众数和中值计算出的合适值来替换。

```
**Input:**
np2_float= np.array(l,dtype=’float’)
print(np2_float)np2_float[0][0]=np.nan
np2_float[1][1]=np.infprint(np.isnan(np2_float))
print(np.isinf(np2_float))**Output:** [[1\. 2.]
 [5\. 6.]
 [7\. 8.]][[ True False]
 [False False]
 [False False]][[False False]
 [False  True]
 [False False]]
```

isnan()和 isinf()函数返回一个布尔数组，如果值不是数字和无穷大，则分别在该数组中赋值 True。

5.使用 Numpy 的统计操作

NumPy 库的主要特点是它提供了用于执行统计计算的内置函数，如平均值、方差、标准偏差、中值、最大值、最小值。

```
**Input:**
import numpy as np
arr1=np.array([[0.,2.],[3.,0.],[3.,4.]])
print(arr1.mean())
print(arr1.max())
print(arr1.min())
print(arr1.std())
print(arr1.var())
print(np.median(arr1))**Output:** 2.0                               #Mean
4.0                               #Maximum Value
0.0                               #Minimum Value
1.5275252316519468                #Standard Deviation
2.3333333333333335                #Variance
2.5                               #Median
```

6.重塑 Numpy 数组

数组的整形是通过使用 shape、shape()、ravel()和 flatten()方法来完成的。

1.  shape-用于知道 Numpy 数组的形状。
2.  shape()-用于整形 Numpy 数组
3.  ravel()-将多维数组转换成一维数组
4.  flatten()-将数组展平为一维数组，返回数组的副本，而不是原始数组。

```
**1.Input:**
print(arr1.shape) **Output:** (3, 2)**2.Input:** print(arr1.reshape(2,3))**Output:** [[0\. 2\. 3.]
 [0\. 3\. 4.]]           #Return an array having 2 rows and 3 columns**3.Input:** print(arr1.reshape(3,4))**Output:
---------------------------------------------------------------------------**
**ValueError**                                Traceback (most recent call last)
**<ipython-input-9-473a5b5a1916>** in <module>
**----> 1** print**(**arr1**.**reshape**(3,4))**

**ValueError**: cannot reshape array of size 6 into shape (3,4)
```

在示例 2 中，我们能够将数组转换为(2，3)，那么示例 3 有什么问题呢？

当我们对一个数组进行整形时，我们要记住的第一件事是，整形前后数组所有维度的乘积应该是相同的。即

```
3*2 = 6  Original array shape
2*3 = 6  6 obtained this time hence reshaping is possible here
3*4 = 12  6 != 12 and hence it can't be reshaped into(3,4)array
1*6 = 6   Possible**Input:**
print(arr1.reshape(1,6))**Output:** [[0\. 2\. 3\. 0\. 3\. 4.]]**Input:** print(arr1.ravel())**Output:** [0\. 2\. 3\. 0\. 3\. 4.]         #Returns a view of original array**Input:** print(arr1.flatten())**Output:** [0\. 2\. 3\. 0\. 3\. 4.]         #Returns a copy after applying changes
```

7.Numpy 中的序列和重复

1.  arange()- arange 函数用于获取特定范围内的值。arange 函数总是不包括最终值。

```
arange(start_value,end_value,step) The default value of step is 1**Input:** np.arange(1,5,dtype='float64')  #Excludes the last value from range**Output:** array([1., 2., 3., 4.])**Input:** np.arange(1,15,5)        #Third value is step value **Output:** array([ 1,  6, 11])
```

2.linspace()和 logspace()

linspace() —值之间有线性空格

log space()-值之间有对数刻度空间

```
**Input:**
np.linspace(1,20,3)   #This gives 3 values which are linearly spaced**Output:** array([ 1\. , 10.5, 20\. ])**Input:** np.logspace(1,20,5)**Output:** array([1.00000000e+01, 5.62341325e+05, 3.16227766e+10, 1.77827941e+15,1.00000000e+20])
```

3.零和一

zeros——NumPy 中的这个方法用于获取特定维数的零数组。有人会想到一个问题，0 的数组有什么用呢？这个问题的答案是，它专门用于计算机视觉或张量流运算，来创建一个 0 和 1 的变量

```
**Input:**
np.zeros([1,5])             #1 is no.of rows 5 is no. of columns**Output:** array([[0., 0., 0., 0., 0.]])**Input:** np.zeros([1,2,3])        # 1=no_of_rows,2=no_of_columns,3=diamension**Output:** array([[[0., 0., 0.],
        [0., 0., 0.]]])
```

这创建了一个由 1 组成的特定维度的数组。

```
**Input:**
np.ones([1,2])**Output:** array([[1., 1.]])
```

8.Numpy 数组中的重复

数组中元素的重复是通过使用 NumPy 中的平铺和重复方法来执行的。

```
**Input:**
np.tile([5,6],3)                  #Tile method**Output:** array([5, 6, 5, 6, 5, 6])**Input:** np.repeat([5,6],3)               # Repeat Method**Output:** array([5, 5, 5, 6, 6, 6])
```

9.Numpy 中的随机数

1.  rand():该方法用于创建指定大小的 0 到 1 范围内的随机数。

```
**Input:**
np.random.rand(3,3) **Output:                               # Range of values 0-1** array([[0.40789767, 0.09907005, 0.61824239],
       [0.1407942 , 0.00401495, 0.6172148 ],
       [0.71200448, 0.72108788, 0.70333744]])
```

2.random.randint():创建一个具有特定维数和指定值范围的整数数组。

```
**# np.random.randint(start_value,end_value,diamension)
Input:**
np.random.randint(1,100,[3,3]) **Output:** array([[63, 45, 50],
       [18, 10, 48],
       [62,  6, 48]])
```

每次当我们运行上面的命令时，我们都会得到不同的值。如果我们想用 random 得到相同的数组。randint()我们需要使用种子函数来固定 randint 函数的初始值，因此我们总是得到相同的数组值。

```
**Input:**
np.random.seed(34)
np.random.randint(1,100,[3,3])**Output:** array([[34, 86, 69],
       [36, 70, 12],
       [79, 30, 19]])
```

10.Numpy 数组中的唯一值

Unique 方法用于从 NumPy 数组中查找唯一的数字。

```
**Input:**
arr_2=np.array([[0,2],[3,0],[3,4]],dtype=’float64')
print(arr_2)
print(np.unique(arr_2))**Output:** [[0\. 2.]
 [3\. 0.]
 [3\. 4.]]
[0\. 2\. 3\. 4.]
```

唯一数字的计数也可以通过使用简单的关键字 *return_counts 来计算。*

```
**Input:**
np.unique(arr_2,return_counts=True)**Output:** (array([0., 2., 3., 4.]), array([2, 1, 2, 1], dtype=int64))
```

输出中的第二项显示了每个唯一值的计数。

如果你真的喜欢这个博客，请鼓掌并关注。我将很快发布初学者最简单的 Numpy 指南的第 2 部分…

谢谢你。