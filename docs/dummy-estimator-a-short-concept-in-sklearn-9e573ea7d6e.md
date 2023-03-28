# 虚拟估计量:Sklearn 中的一个简短概念

> 原文：<https://pub.towardsai.net/dummy-estimator-a-short-concept-in-sklearn-9e573ea7d6e?source=collection_archive---------3----------------------->

## [数据科学](https://towardsai.net/p/category/data-science)

## 监督学习中的估计量检验

![](img/19d3bbb95a3edd1c3fba57177b180daa.png)

由[咖啡极客](https://unsplash.com/@coffeegeek?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

在本文中，我们将讨论如何创建一个假估计量，只是为了与模型估计量进行比较。我们将讨论监督学习中的两种类型的虚拟模型，即回归和分类。

这个概念来自 sklearn 的度量和评分部分。

## DummyRegressor

它用于根据简单规则进行预测，以了解比较回归变量的简单基线，但不用于实际问题。

**DummyRegressor 中的参数**

主要参数如下所示:

1.  **策略:**用于根据其不同的自变量生成预测。

*   ***均值:*** 用于预测训练集的均值。
*   ***中位数:*** 用于预测训练集的中位数。
*   ***分位数:*** 用于预测训练集的分位数范围。
*   ***常量:*** 是用户定义的预测常量值。

python 的例子

```
#import the libraries
import numpy as np
from sklearn.dummy import DummyRegressor#Assign the value to X and y
X = np.array([1.0, 2.0, 3.0, 4.0])
y = np.array([2.0, 3.0, 5.0, 10.0])# Using the dummy regressor
dummy_regr = DummyRegressor(strategy="mean")
dummy_regr.fit(X, y)dummy_regr.predict(X)#output:
array([5., 5., 5., 5.])
```

[](/part-ii-pre-processing-techniques-in-image-processing-with-python-17fb628453ff) [## 第二部分 Python 图像处理中的预处理技术

### OpenCV 下的图像处理技术

pub.towardsai.net](/part-ii-pre-processing-techniques-in-image-processing-with-python-17fb628453ff) [](/step-by-step-basic-understanding-of-neural-networks-with-keras-in-python-94f4afd026e5) [## 使用 Python 中的 Keras 逐步基本了解神经网络

### 具有定义的神经网络的学习

pub.towardsai.net](/step-by-step-basic-understanding-of-neural-networks-with-keras-in-python-94f4afd026e5) 

## dummy 分类器

它用于对简单规则进行预测，以了解比较分类器的简单基线，但不用于实际问题。

**dummy classifier 中的参数**

主要参数如下所示:

1.  **策略:**用于生成预测。

*   ***分层:*** 用于根据训练集中的类分布生成预测。
*   ***最频繁:*** 用于预测训练集的最频繁标签。
*   ***先验:*** 用于预测类别先验最大化的类别。
*   ***均匀:*** 用于随机均匀地生成预测。
*   ***常量:*** 是用户定义的预测常量标签值。这是非常有用的度量评估时间为非多数阶级。

Python 的例子

```
#import the libraries
import numpy as np
from sklearn.dummy import DummyClassifier#Assign the value to X and y
X = np.array([-1, 1, 1, 1])
y = np.array([0, 1, 1, 1])# Using the dummy classifer
dummy_clf = DummyClassifier(strategy="most_frequent")
dummy_clf.fit(X, y)

dummy_clf.predict(X)#output:
array([1, 1, 1, 1])
```

## 结论:

这篇文章只是一个关于哑估计量的基本概念。

[](/hypothesis-testing-in-statistics-with-examples-844d698d99d5) [## 统计学中的假设检验及实例

### 数据驱动决策的统计学概念

pub.towardsai.net](/hypothesis-testing-in-statistics-with-examples-844d698d99d5) 

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

[1。NLP —零到英雄用 Python](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)
2。 [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)
3。[数据预处理概念同 Python](/data-preprocessing-concepts-with-python-b93c63f14bb6?source=friends_link&sk=5cc4ac66c6c02a6f02077fd43df9681a)
4。[用 Python 进行主成分分析降维](/principal-component-analysis-in-dimensionality-reduction-with-python-1a613006d531?source=friends_link&sk=3ed0671fdc04ba395dd36478bcea8a55)
5。[用 Python 全面讲解 K-means 聚类](https://medium.com/towards-artificial-intelligence/fully-explained-k-means-clustering-with-python-e7caa573176a?source=friends_link&sk=9c5c613ceb10f2d203712634f3b6fb28)
6。[用 Python 充分解释了线性回归](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)
7。[用 Python](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)
充分解释了 Logistic 回归 8。[用 Python 做时间序列的基础知识](https://medium.com/towards-artificial-intelligence/basic-of-time-series-with-python-a2f7cb451a76?source=friends_link&sk=09d77be2d6b8779973e41ab54ebcf6c5)
9。[与 Python 的数据角力—第一部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)10。[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)