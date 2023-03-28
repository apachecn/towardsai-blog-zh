# 机器学习中的特征选择和去除

> 原文：<https://pub.towardsai.net/feature-selection-and-removing-in-machine-learning-dd3726f5865c?source=collection_archive---------1----------------------->

## [预测分析](https://towardsai.net/p/category/predictive-analytics)

## 高维数据模型及其精度的改进

![](img/eebfb6a3c71e6f02adf2ddac96c25cd8.png)

由[弗兰基·查马基](https://unsplash.com/@franki?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

众所周知，特征在机器学习算法中的重要性，在任何领域的预测分析中都起着非常关键的作用。

当数据要素变得非常复杂时，出现多重共线性情况或两个或更多要素之间高度相关的可能性非常高。这种情况严重影响了数据的训练，可能会使数据过拟合或欠拟合。

有一些选择和移除特征的方法，如下所示:

```
**Feature Selection Methods**
1\. Uni-variate Selection
2\. Selecting from Model**Feature removing Methods**
1\. Low variance method
2\. Recursive method
```

> ***单变量选择***

单变量方法是一组检查特征关系强度的方法。我们可以用任何方法来理解单个特征到目标特征。

单变量特征选择方法

*   选择 K 最佳
*   选择百分点
*   通用单变量选择
*   皮尔逊相关

## k 最佳方法

在这种方法中，我们基于特征的最高分数和 p 值来选择要选择的特征的数量。

使用 python 的此方法的示例如下所示:

```
from sklearn.datasets import load_iris
from sklearn.feature_selection import SelectKBest
from sklearn.feature_selection import chi2feature, target= load_iris(return_X_y=True)
feature.shape#output:
(150, 4)feature_new = SelectKBest(chi2, k=2).fit_transform(feature, target)
feature_new.shape#output:
(150, 2)
```

我们在这里注意到的一件事是，我们使用 chi2 特性，因为它用于查找一个特性如何依赖于目标特性的统计数据。

## 选择百分点

在这种方法中，我们基于特征的最高百分位分数来选择特征的数量。

使用 python 的此方法的示例如下所示:

```
from sklearn.datasets import load_iris
from sklearn.feature_selection import SelectPercentile
from sklearn.feature_selection import chi2feature, target= load_iris(return_X_y=True)
feature.shape#output:
(1797, 64)feature_new = SelectPercentile(chi2,
                       percentile=10).fit_transform(feature, target)
feature_new.shape#output:
(1797, 7)
```

我们可以选择百分位数，如上面的代码所示，我们还可以看到，从 64 个特性中选择的特性数量现在只有 7 个。

## 通用单变量选择

在这种方法中，我们选择模式的类型来选择特征的数量。

使用 python 的此方法的示例如下所示:

```
from sklearn.datasets import load_breast_cancer
from sklearn.feature_selection import GenericUnivariateSelect
from sklearn.feature_selection import chi2feature, target= load_iris(return_X_y=True)
feature.shape#output:
(569, 30)transformer = GenericUnivariateSelect(chi2, mode='k_best', param=20)feature_new = transformer.fit_transform(feature, target)
feature_new.shape#output:
(569, 20)
```

## 皮尔逊相关

这种方法很容易知道输入特征和目标特征之间的特征相关性。我们得到的分数在[-1 到 1]的范围内，即负相关到强正相关。

使用 python 的此方法的示例如下所示:

```
import numpy as np
from scipy.stats import pearsonrnp.random.seed(0)count = 300
x = np.random.normal(0, 1, count)print("Less random data",pearsonr(x, x + np.random.normal(0, 1,
                         size)))print("More random data", pearsonr(x, x + np.random.normal(0, 10,
                         size)))#output:
Less random data (0.618, 4.743e-49)
More random data (0.078, 0.23)
```

这种方法的一个主要缺点是它对特征的线性关系起作用。

[](/python-examples-to-make-algorithm-more-robust-with-exception-handling-6bff7a127786) [## Python 示例通过异常处理使算法更加健壮

### 程序正常流程中的错误中断

pub.towardsai.net](/python-examples-to-make-algorithm-more-robust-with-exception-handling-6bff7a127786) [](https://medium.com/pythoneers/forget-html-and-flask-start-using-streamlit-1b394cfe4595) [## 忘记 HTML 和 Flask，开始使用 Streamlit

### 数据科学和机器学习的 WebApp 框架

medium.com](https://medium.com/pythoneers/forget-html-and-flask-start-using-streamlit-1b394cfe4595) 

> ***从*** 型号中选择

该方法用于在拟合模型后发现重要特征。它就像是模型的一个附件，根据某个阈值来选择重要的特性。

使用 python 的此方法的示例如下所示:

```
from sklearn.feature_selection import SelectFromModel
from sklearn.linear_model import LogisticRegressionX = [[ 0.27, -2.34,  0.31 ],
    [-2.79, -0.09, -0.85 ],
    [-0.34, 1.34, -2.55 ],
    [ 1.77,  1.28,  0.54 ]]y = [1, 0, 1, 0]selector = SelectFromModel(estimator=LogisticRegression()).fit(X, y)
selector.estimator_.coef_output:
array([[ 0.35531238, -0.56881882, -0.70144451]])-------------------------------------------------------------selector.threshold_output:
0.5524527319086916-------------------------------------------------------------selector.get_support()output:
array([False,  True, False])
```

> ***低方差法***

该方法基于对特征的方差方法，以满足给定的某个阈值，从而找到数据中的重要重要性。

阈值的一般公式如下所示:

```
.8 * (1 - .8)
```

使用 python 的此方法的示例如下所示:

```
from sklearn.feature_selection import VarianceThresholdX = [[1,0,1], [1, 0, 0], [0, 1, 1], [0, 1, 0], [0, 1, 0], [0, 1, 1]]sel = VarianceThreshold(threshold=(.5 * (1 - .5)))
sel.fit_transform(X)#output:
No feature in X meets the variance threshold 0.25000-------------------------------------------------------------sel = VarianceThreshold(threshold=(.6 * (1 - .6)))
sel.fit_transform(X)#output:
array([[1],
       [0],
       [1],
       [0],
       [0],
       [1]])
```

这里，如果我们给定一个低阈值，那么这些特征就不会被选择。但是如果我们给某个点一个阈值，那么它会从数据中删除一些列。

> ***递归法***

在这种方法中，特征的排序是基于权重的。该方法将特征分成更小的特征集，然后从更小的特征集到更大的特征集进行训练。

使用 python 的此方法的示例如下所示:

```
from sklearn.datasets import make_friedman1
from sklearn.feature_selection import RFE
from sklearn.svm import SVRfeature, target = make_friedman1(n_samples=30, n_features=8, 
                                                 random_state=0)estimator = SVR(kernel="linear")
selector = RFE(estimator, n_features_to_select=5, step=1)
selector = selector.fit(feature, target)selector.ranking_#output:
array([1, 2, 3, 1, 1, 1, 1, 4])
```

从上面的例子中，我们可以看到在 n_features 参数中给出的 8 个特性上有一个排名。

> ***结论***

本文讨论了机器学习中的一些特征选择方法。特性选择是每个项目中的一项重要任务。

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