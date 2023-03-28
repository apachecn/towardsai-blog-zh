# 将分类算法应用于过去的贷款数据

> 原文：<https://pub.towardsai.net/past-loan-data-75710e4552ed?source=collection_archive---------0----------------------->

## KNN，决策树，支持向量机，逻辑回归

![](img/ef92bc7d9a9637a1c6267f104ab214fe.png)

作者图片

在这个数据集中，我将对过去的贷款数据进行分类机器学习分析，这些数据是；

*   k 最近邻(KNN)
*   决策图表
*   支持向量机
*   逻辑回归

```
Content Table· [Data Visualization](#7f67)
· [One hot encoding](#5891)
· [Feature Selection](#d45a)
· [Normalize Data](#c4ed)
· [Classification](#71cd)
 ∘ [K Nearest Neighbor](#b540)
 ∘ [Evaluation Metrics of KNN](#8b51)
 ∘ [Decision Tree](#8300)
 ∘ [Evaluation Metrics of Decision Tree](#5730)
 ∘ [Support Vector Machine](#83d7)
 ∘ [Evaluation Metrics of SVM](#5cc6)
 ∘ [Logistic Regression](#bf84)
 ∘ [Evaluation Metrics of Logistic Regression](#5f5d)
 ∘ [Model Evaluation using a Test set](#1eb5)
 ∘ [Jaccard Scores](#edfa)
 ∘ [F1 Scores](#8648)
 ∘ [Final Evaluation](#dd7e)
```

让我们加载必要的库；

![](img/81ceb9f89bb8fe6eb718727a2a777f25.png)

作者图片

**Loan_train.csv** 数据集包括 346 名贷款已经还清或违约的客户的详细信息。

![](img/b825d3b3fa156ef7ac189deba4cae1c5.png)

作者图片

让我们加载数据；

![](img/995d9ee790a40df85183a514abe8dca6.png)

作者图片

看数据的形状，看全局总是有效的。

![](img/df8a5fc21bb01eb22f310e9a0f2b51fb.png)

作者图片

现在，让我们修复数据框列类型。

![](img/6282d87f98a7390437bd9fcb5d45763a.png)

作者图片

# 数据可视化

让我们看看每个类在我们的数据集中有多少

![](img/8ba67bfe9a63725fe597a6861e566205.png)

作者图片

让我们绘制一些列来更好地理解

![](img/4011c5982c77a3215d0e4eb878e74dc1.png)

作者图片

![](img/fe6700c791ce8259467bbad2de525d75.png)

作者图片

让我们看看人们在一周的哪一天得到贷款

![](img/934bd45729637a40a156ebe451308fa6.png)

作者图片

我们看到在周末获得贷款的人没有还清贷款，所以让我们使用特征二值化来设置小于第 4 天的阈值

![](img/c5cf35a215d8789555626c8983786e38.png)

作者图片

现在是时候将分类特征改为数字特征了，因为我们将使用机器学习算法。

![](img/2c039cafe296ccafc42bc54d6f798267.png)

作者图片

86 %的女性偿还贷款，而只有 73 %的男性偿还贷款

让我们将男性转换为 0，女性转换为 1:

![](img/290d815b7bdffe40fab3a74e4f24bb32.png)

作者图片

# 一个热编码

现在让我们看看教育专栏。

![](img/e78e6cee7fefd40f9f7d94a3e5d52c7e.png)

作者图片

![](img/f4379e1aa4cf0a3581e0703e17e9470d.png)

作者图片——这些是我们在预测中要用到的特征。

我们用假人将教育从分类转变为数字。

![](img/cdb7ba767e3e77c69f74b863687e4f97.png)

作者图片

# **功能选择**

让我们定义特征；

![](img/4b93cdf409d754751d8884d58c4b1fcf.png)

作者图片

现在是时候定义我们的标签了；

![](img/6a8caddc3ff5b6d519861a2dd0a2224c.png)

作者图片

# 标准化数据

![](img/2e09f929372c6737f335502c90bc98ef.png)

作者图片

# 分类

这些是我将在这个数据集中使用的分类技术。

*   k 最近邻(KNN)
*   决策图表
*   支持向量机
*   逻辑回归

## k 最近邻

现在是时候分割训练和测试数据了，通常是 0.2-0.8 份。

![](img/feebe1c7daee5c3fd072fe25caf87142.png)

作者图片

![](img/132c374254bd77461e5e57e35e7b6a05.png)

作者图片

![](img/c00c40bfdf078a852654421c428ccfc2.png)

作者图片

现在是时候调查测试和训练数据的准确性了。

![](img/a96779bfce20ab0263e9fe18abd55e21.png)

作者图片

定义最佳 K；

![](img/49557d0a930fb43383bea4eb56cadc8e.png)

作者图片

如我们所见，结果 7 是我们数据的最佳 K。

![](img/205cb008808a70330a39f1cd6bf800cf.png)

作者图片

![](img/6af3a54ccf0c7526981122d47eaa79eb.png)

作者图片

![](img/010416c8054c04f927dbd3dd2c12bc63.png)

作者图片-适合模型

## KNN 的评价指标

![](img/e7c6df0662966c2ddf5da87f5039a289.png)

作者图片

## 决策图表

现在让我们尝试使用决策树算法。

![](img/24e705993185244fcaa43fd18e6a1b02.png)

作者图片

![](img/acc21d2b0e5d5fb0c998b05e16365bb5.png)

作者图片

确定最佳深度；

![](img/638fbc926b89d0b7b0457faedb9e7506.png)

作者图片

根据准确度分数，5 是最佳深度分数。

![](img/2c5591989bc01e41fb3d06b44c2d6429.png)

作者图片

让我们进行我们的算法，然后评估；

## 决策树的评价指标

![](img/51d9fe7c2a714c3a43025425e9f0e026.png)

作者图片

## 支持向量机

现在让我们用 SVM。

![](img/b8d2233ff895d03da5c592878233fabe.png)

作者图片

找出 SVM 最好的模特；

![](img/62e504f86f3d3405cda00e5f1a401b09.png)

作者图片

![](img/e1cee04d0b68df1316cce8c46f91f36d.png)

作者图片

![](img/163b47cc591cf5c888255ce6da757683.png)

作者图片

## SVM 的评价指标

![](img/bc9e93ed52fcf9e269a3dc304a886859.png)

作者图片

## 逻辑回归

现在是使用逻辑回归的时候了。

让我们锁定和加载；

![](img/cff589363335fc37d77dcfeab0708cbb.png)

作者图片

列车-测试分离；

![](img/0fb7ba40f0a739254a4ed315bb2e3b06.png)

作者图片

找到最佳解算器；

![](img/3d867ed624127cc1cd8c118f13bf1441.png)

作者图片

![](img/cc98bd041713e4a0b9850ba1b96b5105.png)

作者图片

## 逻辑回归的评价指标

![](img/2f14a0dd8393491a30ff7b2101258991.png)

作者图片

## 使用测试集的模型评估

![](img/1c355eaca4a40fdce4e4c8fc2d348cfe.png)

作者图片

![](img/f43343469ae1906753bdb00b40ee1364.png)

作者图片

数据处理；

![](img/bad40a6be1dbe06ec252c0ccb1003d7f.png)

作者图片

## Jaccard 分数

![](img/b801d0c313d33b86304216379668d9fa.png)

作者图片

![](img/624b9c34732e57af7bdcfc14ba646184.png)

作者图片

![](img/7e8317a6a063ab2736f491c1daccf57a.png)

作者图片

![](img/8d8b2af45c8a552672a13dafd4737990.png)

作者图片

## F1 分数

![](img/ba9474e54cf68a4f6710c6d98325e287.png)

作者图片

![](img/ef217dbc2ec0bdebcfba775875559ae1.png)

作者图片

![](img/55d2232d9beed2f15747016b2063454d.png)

作者图片

![](img/2ee19aeae14c186357af4e381a189849.png)

作者图片

## 最终评估

![](img/47e3f5861fc5d44f811c67e1311bab28.png)

作者图片

感谢 IBM 的机器学习教程，它让我到达了那里。