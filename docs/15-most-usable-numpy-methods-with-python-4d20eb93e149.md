# Python 最有用的 15 种 NumPy 方法

> 原文：<https://pub.towardsai.net/15-most-usable-numpy-methods-with-python-4d20eb93e149?source=collection_archive---------1----------------------->

## 适用于所有数据科学和机器学习项目的便捷概念

![](img/8f54e50b31bcd970f84af8dec808971a.png)

Emile Perron 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

本文将更新数据科学项目分析中使用的 NumPy 方法的概念。

涵盖的主题:

```
1\. Array Creation
2\. Matrix creation routines
3\. Generating linear array
4\. Arange method
5\. Reshape method
6\. Matrix multiplication
7\. Ravel method
8\. Flatten method
9\. Stack method
10\. Horizontal stack method
11\. Bitwise operations
12\. Statistics operations with numpy
13\. Transpose method
14\. Linspace method
15\. Indexing and Slicing
```

1.  **阵列创建**

在 NumPy 方法的帮助下，有许多方法可以创建数组。

```
import numpy as nparray1 = np.array([20,30,40])
array1#output:
array([20, 30, 40])#create null array
np.zeros((2,2))#output:
array([[0., 0.],
       [0., 0.]])
```

**2。矩阵创建例程**

这些方法用于创建上下矩阵。

```
#creating lower triangle i.e. below diagonal line
a = np.tri(3, 3, k=-1, dtype = np.uint16)
print(a)#output:
[[0 0 0]
 [1 0 0]
 [1 1 0]]#change the value to k=0
a = np.tri(3, 3, k=0, dtype = np.uint16)
print(a)#output:
[[1 0 0]
 [1 1 0]
 [1 1 1]]#creating upper triangular matrix
b = np.ones((3, 3), dtype = np.uint8)
c = np.triu(b, k=0)
print(c)#output:
[[1 1 1]
 [0 1 1]
 [0 0 1]]
```

**3。生成线性数组**

具有下限和上限参数的随机方法将生成线性数组，如下所示:

```
a = np.random.randint(low=0, high=9, size=10)
print(a)#output:
[5 4 2 1 5 3 8 2 3 3]
```

**4。排列方法**

它还用于通过 arange 方法创建数组。

```
np.arange( 1, 10, 2 )#output:
array([1, 3, 5, 7, 9])
```

**5。整形方法**

此方法用于创建具有方法中提到的指定行数和列数的矩阵。

```
matrix1 = np.arange(9).reshape(3,3)
print(matrix1)#output:
[[0 1 2]
 [3 4 5]
 [6 7 8]]
```

**6。矩阵乘法**

在此方法中，数组和矩阵可用于算术运算，如下所示:

```
x = np.array( [4,6,8,10] )
y = np.arange( 4 )z = x-y#output:
array([4, 5, 6, 7])#matrix multiplication
x = np.array( [[2,2], [2,0]] )
y = np.array( [[1,3], [1,1]] )# using @ for matrix multiplication
x@y#output:
array([[4, 8],
       [2, 6]])
```

**7。拆纱方法**

它用于展平矩阵。

```
flatten_matrix = np.ravel(matrix1)
flatten_matrix#output:
array([0, 1, 2, 3, 4, 5])
```

**8。展平方法**

它也用于展平矩阵

```
flatten_matrix = matrix1.flatten()
flatten_matrix#output:
array([0, 1, 2, 3, 4, 5])
```

9。堆叠法

它用于连接阵列以形成 2D 矩阵。

```
x = np.array( [4,6,8,10] )
y = np.arange( 4 )stack_matrix = np.stack((x,y))
print(stack_matrix)#output:
[[ 4  6  8 10]
 [ 0  1  2  3]]
```

[](https://medium.com/pythoneers/20-most-usable-pandas-shortcut-methods-in-python-c9bc065ce11e) [## Python 中 20 个最有用的熊猫快捷方式

### 数据科学和机器学习的有用概念

medium.com](https://medium.com/pythoneers/20-most-usable-pandas-shortcut-methods-in-python-c9bc065ce11e) [](https://medium.com/pythoneers/io-basics-and-open-read-and-write-methods-in-python-5ceda9d658e) [## Python IO 基础和 Open()、Read()和 write()方法

### 理解操作文件的基本概念

medium.com](https://medium.com/pythoneers/io-basics-and-open-read-and-write-methods-in-python-5ceda9d658e) 

10。水平叠加法

它用于将一个数组追加到另一个数组中。

```
x = np.array( [7,2,3] )
y = np.arange( 3 )hstack_matrix = np.hstack((x,y))
print(hstack_matrix)#output:
[7 2 3 0 1 2]
```

11。位运算

我们使用 NumPy 数组进行位运算。

```
x = np.array( [4,6,8,10] )
y = np.array( [6,6,2,14] )print(np.bitwise_and(x,y))
print(np.bitwise_or(x,y))
print(np.bitwise_xor(x,y))#output:
[ 4  6  0 10]
[ 6  6 10 14]
[ 2  0 10  4]
```

12。用 NumPy 进行统计操作

NumPy 库也可用于查找数组中的中心度量值和其他参数。

```
x = np.array( [1, 1, 3, 5, 6, 8, 3, 4, 7, 1] )print(np.median(x))
print(np.mean(x))
print(np.std(x))
print(np.var(x))#output:
3.5
3.9
2.4269322199023193
5.889999999999999
```

13。转置方法

transpose 方法用于更改行和列的值。

```
x = np.array( [[2,3], [4,5]] )
x#output:
array([[2, 3],
       [4, 5]])#doing transpose of x
x.transpose()#output:
array([[2, 4],
       [3, 5]])
```

**14。林空间方法**

它还用于创建一个线性可分数组，如下所示。

```
np.linspace(0, 20, num=5)#output:
array([ 0.,  5., 10., 15., 20.])
```

15。步进和切片

我们可以使用索引和切片从数组中获取部分数据。

```
x = np.array( [1, 1, 3, 5, 6, 8, 3, 4, 7, 1] )x[2]
#Output:
3-----------------------------------x[6:]
#output:
array([3, 4, 7, 1])
```

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