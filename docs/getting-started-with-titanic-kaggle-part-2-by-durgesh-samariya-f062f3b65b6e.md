# 泰坦尼克号起航|第二部分

> 原文：<https://pub.towardsai.net/getting-started-with-titanic-kaggle-part-2-by-durgesh-samariya-f062f3b65b6e?source=collection_archive---------2----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

## 让我们开发一个模型来预测泰坦尼克号对 Kaggle 的挑战

![](img/333a00e553e53a485599bd7522ebae02.png)

来源:[国家地理](https://www.nationalgeographic.org/media/sinking-of-the-titanic/)

在上一篇文章中，我们开始着手泰坦尼克号卡格尔比赛。如果你还没有读过，你可以在这里阅读。所以在这篇文章中，我们将使用机器学习来开发预测模型。

如果您已经关注了我的上一篇文章，那么现在我们的数据已经准备好了，可以准备模型了。有大量的预测算法可供尝试。然而，我们的问题是分类问题，因此我将尝试以下分类/回归算法。

*   支持向量机
*   k-最近邻
*   线性 SVC
*   决策图表
*   随机森林

# 首先要做的事。

# 导入所有必需的机器学习库

为了开发一个机器学习模型，我们需要导入 [Scikit-learn](https://scikit-learn.org/stable/) 库。

> Scikit-Learn 是一个开源的机器学习库，支持监督和非监督学习。它还提供了用于模型拟合、数据预处理、模型选择和评估的各种工具，以及许多其他实用工具。— [Scikit-Learn](https://scikit-learn.org/stable/getting_started.html)

让我们从 Scikit-Learn 导入所有需要的算法。

```
*# machine learning*
from sklearn.svm import SVC, LinearSVC
from sklearn.ensemble import RandomForestClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.tree import DecisionTreeClassifier
```

每种机器学习分类算法都需要训练和测试数据来训练和测试模型。

```
# dropping Name, Survived and PassengerId column
X_train = train_data.drop(["Name", "Survived", "PassengerId"], axis=1)
Y_train = train_data["Survived"]
X_test  = test_data.drop(['Name',"PassengerId"], axis=1).copy()
X_train.shape, Y_train.shape, X_test.shape
```

# 支持向量机

> 支持向量机在高维或无限维空间中构造一个超平面或一组超平面，可用于分类、回归或其他任务，如异常值检测。— [维基百科](https://en.wikipedia.org/wiki/Support_vector_machine)

```
*# Support Vector Machine*
svc = SVC()
svc.fit(X_train, Y_train)
svm_Y_pred = svc.predict(X_test)
svc_accuracy = svc.score(X_train, Y_train)
svc_accuracy# output
0.6823793490460157
```

# k-最近邻

> 在 K *-NN 分类*中，输出的是一个类成员关系。一个对象通过其邻居的多数投票来分类，其中该对象被分配到其 *k* 个最近邻居中最常见的类别— [维基百科](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm)

```
*# k-nearest neighbor*
knn = KNeighborsClassifier(n_neighbors = 3)
knn.fit(X_train, Y_train)
knn_Y_pred = knn.predict(X_test)
knn_accuracy = knn.score(X_train, Y_train)
knn_accuracy# output
0.8406285072951739
```

# 线性支持向量分类

> 类似于带有参数 kernel='linear '的 SVC，但它是根据 liblinear 而不是 libsvm 实现的，因此它在选择惩罚和损失函数方面具有更大的灵活性，并且应该可以更好地扩展到大量样本。— [来源](https://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html)

```
*# Linear SVC*

linear_svc = LinearSVC()
linear_svc.fit(X_train, Y_train)
linear_svc_Y_pred = linear_svc.predict(X_test)
linear_svc_accuracy = linear_svc.score(X_train, Y_train)
linear_svc_accuracy# output
0.792368125701459
```

# 决策树

> 决策树学习是数据挖掘中常用的一种方法。目标是创建一个模型，根据几个输入变量预测目标变量的值。
> 
> 决策树是对例子进行分类的简单表示。对于本节，假设所有输入要素都有有限的离散域，并且有一个称为“分类”的目标要素。分类领域的每个元素被称为一个*类*。— [维基百科](https://en.wikipedia.org/wiki/Decision_tree_learning)

```
*# Decision Tree*

decision_tree = DecisionTreeClassifier()
decision_tree.fit(X_train, Y_train)
decision_tree_Y_pred = decision_tree.predict(X_test)
decision_tree_accuracy = decision_tree.score(X_train, Y_train)
decision_tree_accuracy# output
0.9797979797979798
```

# 随机森林

> 随机森林或随机决策森林是一种用于分类、回归和其他任务的集成学习方法，其通过在训练时构建大量决策树并输出作为个体树的类(分类)或均值预测(回归)的模式的类来操作。— [维基百科](https://en.wikipedia.org/wiki/Random_forest)

```
*# Random Forest*

random_forest = RandomForestClassifier(n_estimators=100)
random_forest.fit(X_train, Y_train
random_forest_Y_pred = random_forest.predict(X_test)
random_forest.score(X_train, Y_train)
random_forest_accuracy = random_forest.score(X_train, Y_train)
random_forest_accuracy# output
0.9797979797979798
```

# 每个模型的提交文件

现在，我们使用不同的模型对每个测试数据进行预测。是时候为竞赛创建一个提交文件了。我们必须创建一个像这样的提交文件。

提交文件包含两列。

*   从 892 到 1148 的乘客 id(在 test.csv 中可用)
*   幸存——这是我们用不同的模型预测的。

让我们看看如何做到这一点。

```
*# submission file from each model*
svm_submission = pd.DataFrame({"PassengerId": test_data["PassengerId"], "Survived": svm_Y_pred})
svm_submission.to_csv('svm_submission.csv', index=False)

knn_submission = pd.DataFrame({"PassengerId": test_data["PassengerId"], "Survived": knn_Y_pred})
knn_submission.to_csv('knn_submission.csv', index=False)

linear_svc_submission = pd.DataFrame({"PassengerId": test_data["PassengerId"], "Survived": linear_svc_Y_pred})
linear_svc_submission.to_csv('linear_svc_submission.csv', index=False)

decision_tree_submission = pd.DataFrame({"PassengerId": test_data["PassengerId"], "Survived": decision_tree_Y_pred})
decision_tree_submission.to_csv('decision_tree_submission.csv', index=False)

random_forest_submission = pd.DataFrame({"PassengerId": test_data["PassengerId"], "Survived": random_forest_Y_pred})
random_forest_submission.to_csv('random_forest_submission.csv', index=False)
```

现在我们有五个不同的提交文件。你甚至可以尝试不同的算法来寻找更好的解决方案。这是帖子的结尾。你可以在这里找到完整的 kaggle 内核。

**感谢阅读！快乐的机器学习。**

如果你喜欢我的工作并想支持我，我会非常感谢你在我的社交媒体频道上关注我:

*   支持我的最好方式就是在[](https://medium.com/@themlphdstudent)**媒体上关注我。**
*   **订阅我的新 [**YouTube 频道**](https://www.youtube.com/c/themlphdstudent) 。**
*   **在我的 [**邮箱列表**](http://eepurl.com/hampwT) 报名。**

****万一你错过了上一篇文章****

**[泰坦尼克号起航|第一部](https://medium.com/towards-artificial-intelligence/getting-started-with-titanic-kaggle-447a309f2d19)**

****如果你错过了我的 python 系列。****

*   **第 0 天:[挑战介绍](/@durgeshsamariya/100-days-of-machine-learning-code-a9074e1c42c3)**
*   **第 1 天: [Python 基础知识— 1](/the-innovation/python-basics-variables-data-types-and-list-59cea3dfe10f)**
*   **第 2 天: [Python 基础知识— 2](https://towardsdatascience.com/python-basics-2-working-with-list-tuples-dictionaries-871c6c01bb51)**
*   **第 3 天: [Python 基础知识— 3](/towards-artificial-intelligence/python-basics-3-97a8e69066e7)**
*   **第 4 天: [Python 基础— 4](/javarevisited/python-basics-4-functions-working-with-functions-classes-working-with-class-inheritance-70e0338c1b2e)**
*   **第 5 天: [Python 基础— 5](/towards-artificial-intelligence/python-basics-5-files-and-exceptions-by-durgesh-samariya-5d892d170640)**

**我希望你会喜欢我的其他文章。**

*   **给初学者的 Git**
*   **[八月月度阅读清单](/@durgeshsamariya/august-2020-monthly-machine-learning-reading-list-by-durgesh-samariya-20028aa1d5cc)**
*   **[集群资源](/towards-artificial-intelligence/a-curated-list-of-clustering-resources-fe355e0e058e)**
*   **[离群点检测资源](/dev-genius/curated-list-of-outlier-detection-resources-35ed27d0e46e)**