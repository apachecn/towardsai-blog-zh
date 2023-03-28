# 使用 Python 进行机器学习以避免数据泄漏的技巧和诀窍

> 原文：<https://pub.towardsai.net/tips-and-tricks-in-machine-learning-with-python-to-avoid-data-leakage-c3908fa4a0c9?source=collection_archive---------5----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

## 更有效地编写机器学习算法

![](img/9506cfe9a46617ef04fcc89122689132.png)

[absolute vision](https://unsplash.com/@freegraphictoday?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 拍摄的照片

这篇文章将成为非常有趣的一篇，我们将谈论机器学习中使用的技巧和窍门，以避免数据泄漏。很多初学者学习机器学习算法只是通过拆分数据，将训练数据馈送给分类器。哦！等等，这对初学者来说看起来简单多了，但是在我们建模之前，要弄清楚更多的事情是很难的。

在机器学习中， ***数据泄露*** 是训练过程中与目标特征相关的共享信息或数据，即与目标特征高度相关的独立特征导致泄露。

它会降低真实世界数据的准确性。为了改善机器学习中的泄漏问题，有如下一些提示:

*   在对数据进行训练测试分割之前，不要进行数据预处理。
*   切勿使用 fit_transform 来测试集合。
*   我们应该在训练集和测试集上都使用转换。训练集的 fit_transform 和测试集的 transform。
*   我们应该使用 sklearn 的管道，它在参数调整和交叉验证方面使用得很好。

[](/fully-explained-dbscan-clustering-algorithm-with-python-a568139ebff5) [## 用 Python 全面解释 DBScan 聚类算法

### 基于密度聚类的机器学习中的无监督学习

pub.towardsai.net](/fully-explained-dbscan-clustering-algorithm-with-python-a568139ebff5) 

**python 的例子**

在训练-测试分割之后，我们应该使用标准缩放。

```
X_train, X_test, y_train, y_test = train_test_split(
                     X, y, test_size=0.4, random_state=random_state)
```

现在是使用标准缩放的时候了

```
scaler = StandardScaler()
X_train_transformed = scaler.fit_transform(X_train)
model = LinearRegression().fit(X_train_transformed, y_train)
mean_squared_error(y_test, model.predict(X_test))
```

在上面的例子中，我们注意到测试数据没有被转换，这可能会影响准确性。

```
X_test_transformed = scaler.transform(X_test)
mean_squared_error(y_test, model.predict(X_test_transformed))
```

分割后的训练集和测试集的分类数据也是如此。

```
one_hot_en = OneHotEncoder(handle_unknown='ignore', sparse=False)
one_hot_cols_train = pd.DataFrame(one_hot_en.fit_transform(X_train[cat_cols]))
one_hot_cols_test = pd.DataFrame(one_hot_en.transform(X_test[cat_cols]))

# One-hot encoding removed index; put it back
one_hot_cols_train.index = X_train.index
one_hot_cols_test.index = X_test.index
```

在机器学习中使用流水线方法，以减少在转换中跳过某些步骤的机会。

```
from sklearn.pipeline import make_pipeline

model = make_pipeline(StandardScaler(), LinearRegression())----------------------------------------------------------------
model.fit(X_train, y_train)
#output:
Pipeline(steps=[('standardscaler', StandardScaler()),
                ('linearregression', LinearRegression())])----------------------------------------------------------------
mean_squared_error(y_test, model.predict(X_test))
```

[](/fully-explained-gradient-boosting-technique-in-supervised-learning-d3e293ca70e1) [## 监督学习中的梯度推进技术

### 机器学习中的回归和分类方法

pub.towardsai.net](/fully-explained-gradient-boosting-technique-in-supervised-learning-d3e293ca70e1) 

**更多提示**

*   当我们保存模型时，我们使用 pickle，但是当对象是一个非常大的 numpy 数组时，在某些情况下使用 joblib 方法。
*   当我们处理分类数据时，我们应该在不同的情况下使用 MAE 得分来检查哪个情况得分更低，以获得更有效的算法。
*   热点图还显示了高度相关的要素，这些要素可能会导致渗漏问题。

## 支持向量机技巧

*   为了避免复制大量密集的输入数据，建议使用`SGDClassifier`。
*   增加内核缓存的大小是一个很好的做法。
*   建议设置正则化参数。
*   SVM 的不变性建议在建模前缩放数据。
*   为了缩短训练时间，我们应该使用收缩参数。

## K-最近邻中的提示

*   选择一个好的搜索技巧。
*   选择距离度量，以便更好、更快地进行搜索。

## K 均值中的提示

*   数据点应该基于相似性。
*   用肘法选择合适的 k 值。

[](https://amitprius.medium.com/how-my-single-thought-made-me-a-writer-on-medium-430061ff0803) [## 我的单一想法如何让我成为一个媒体作家

### 作为一个作家，我们应该一直努力的事情

amitprius.medium.com](https://amitprius.medium.com/how-my-single-thought-made-me-a-writer-on-medium-430061ff0803) 

我希望你喜欢这篇文章。通过我的 [LinkedIn](https://www.linkedin.com/in/data-scientist-95040a1ab/) 和 [twitter](https://twitter.com/amitprius) 联系我。

# 推荐文章

1.  [NLP——用 Python 零到英雄](https://medium.com/towards-artificial-intelligence/nlp-zero-to-hero-with-python-2df6fcebff6e?sk=2231d868766e96b13d1e9d7db6064df1)

2. [Python 数据结构数据类型和对象](https://medium.com/towards-artificial-intelligence/python-data-structures-data-types-and-objects-244d0a86c3cf?sk=42f4b462499f3fc3a160b21e2c94dba6)

3.[使用 Python 的数据预处理概念](/data-preprocessing-concepts-with-python-b93c63f14bb6?source=friends_link&sk=5cc4ac66c6c02a6f02077fd43df9681a)

4.[用 Python 进行主成分分析降维](/principal-component-analysis-in-dimensionality-reduction-with-python-1a613006d531?source=friends_link&sk=3ed0671fdc04ba395dd36478bcea8a55)

5.[用 Python 全面解释 K-means 聚类](https://medium.com/towards-artificial-intelligence/fully-explained-k-means-clustering-with-python-e7caa573176a?source=friends_link&sk=9c5c613ceb10f2d203712634f3b6fb28)

6.[用 Python 全面解释线性回归](https://medium.com/towards-artificial-intelligence/fully-explained-linear-regression-with-python-fe2b313f32f3?source=friends_link&sk=53c91a2a51347ec2d93f8222c0e06402)

7.[用 Python 全面解释逻辑回归](https://medium.com/towards-artificial-intelligence/fully-explained-logistic-regression-with-python-f4a16413ddcd?source=friends_link&sk=528181f15a44e48ea38fdd9579241a78)

8.[Python 时间序列基础](https://medium.com/towards-artificial-intelligence/basic-of-time-series-with-python-a2f7cb451a76?source=friends_link&sk=09d77be2d6b8779973e41ab54ebcf6c5)

9.[与 Python 的数据争论—第 1 部分](/data-wrangling-with-python-part-1-969e3cc81d69?source=friends_link&sk=9c3649cf20f31a5c9ead51c50c89ba0b)

10.[机器学习中的混淆矩阵](https://medium.com/analytics-vidhya/confusion-matrix-in-machine-learning-91b6e2b3f9af?source=friends_link&sk=11c6531da0bab7b504d518d02746d4cc)