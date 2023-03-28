# 数据科学课程

> 原文：<https://pub.towardsai.net/data-science-curriculum-bf3bb6805576?source=collection_archive---------0----------------------->

## [数据科学](https://towardsai.net/p/category/data-science)

## 初级数据科学自学的推荐课程

![](img/811216294065b858a6cae2bac1b88757.png)

由[凯利·西克玛](https://unsplash.com/@kellysikkema?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

作为一名数据科学教育工作者，许多对数据科学感兴趣的人联系我，寻求如何进入数据科学领域的指导。本文将讨论推荐的主题，人们必须学习这些主题才能掌握数据科学的基本技能。

这里介绍的主题，如果研究透彻，将提供开始从事数据科学所需的最基本的背景知识。该课程也可用于设计数据科学方面的大学入门课程。

*请记住，仅仅从课程中获得的知识不会让你成为数据科学家。课程工作必须伴随着一个顶点项目或实习。Kaggle 竞赛可以用于顶点，因为它们提供了在现实世界的数据科学项目上工作的机会。*

# 数据科学导论的基本主题

## 1.数学基础

**(一)多变量微积分**

大多数机器学习模型是用具有几个特征或预测器的数据集构建的。因此，熟悉多变量微积分对于建立机器学习模型极其重要。以下是您需要熟悉的主题:

*   多元函数
*   导数和梯度
*   阶跃函数、Sigmoid 函数、Logit 函数、ReLU(校正线性单位)函数
*   价值函数
*   功能绘图
*   函数的最小值和最大值

**(二)线性代数**

线性代数是机器学习中最重要的数学技能。数据集被表示为矩阵。线性代数用于数据预处理、数据转换和模型评估。以下是您需要熟悉的主题:

*   向量
*   矩阵
*   矩阵的转置
*   矩阵的逆矩阵
*   矩阵的行列式
*   点积
*   本征值
*   特征向量

**(三)优化方法**

大多数机器学习算法通过最小化目标函数来执行预测建模，从而学习为了获得预测标签而必须应用于测试数据的权重。以下是您需要熟悉的主题:

*   成本函数/目标函数
*   似然函数
*   误差函数
*   梯度下降算法及其变体(例如，随机梯度下降算法)

## 2.编程基础

Python 和 R 被认为是数据科学的顶级编程语言。你可能会决定只专注于一种语言。Python 被行业和学术培训项目广泛采用。作为初学者，建议你只专注于一门语言。

下面是一些需要掌握的 Python 和 R 基础知识主题:

*   基本 R 语法
*   基本的 R 编程概念，如数据类型、矢量算法、索引和数据框架
*   如何在 R 中执行操作，包括排序、使用 dplyr 处理数据以及使用 ggplot2 进行数据可视化
*   r 工作室
*   Python 的面向对象编程方面
*   Jupyter 笔记本
*   能够使用 Python 库，如 NumPy、pylab、seaborn、matplotlib、pandas、scikit-learn、TensorFlow、PyTorch

## 3.数据基础

学习如何操作各种格式的数据，例如 CSV 文件、pdf 文件、文本文件等。了解如何从互联网上清理数据、估算数据、缩放数据、导入和导出数据以及废弃数据。一些感兴趣的包有 pandas、NumPy、pdf tools、stringr 等。此外，R 和 Python 包含几个内置的数据集，可以用于实践。学习数据转换和降维技术，如协方差矩阵图、主成分分析(PCA)和线性判别分析(LDA)。

## 4.概率和统计基础

统计和概率用于特征的可视化、数据预处理、特征转换、数据插补、降维、特征工程、模型评估等。以下是您需要熟悉的主题:

*   平均
*   中位数
*   方式
*   标准偏差/方差
*   相关系数和协方差矩阵
*   概率分布(二项式、泊松、正态)
*   p 值
*   Baye 定理(精确度、召回率、阳性预测值、阴性预测值、混淆矩阵、ROC 曲线)
*   A/B 测试
*   蒙特 卡罗模拟

## 5.数据可视化基础

了解良好的数据可视化的基本组件。一个好的数据可视化由几个组件组成，这些组件必须组合在一起才能产生最终产品:

a) **数据成分**:决定如何可视化数据的第一个重要步骤是了解数据的类型，例如，分类数据、离散数据、连续数据、时间序列数据等。

b) **几何组件:**您可以在这里决定哪种可视化适合您的数据，例如散点图、线形图、条形图、直方图、Q-Q 图、平滑密度、箱线图、配对图、热图等。

c) **映射组件:**这里，你需要决定用什么变量作为你的 x 变量，用什么变量作为你的 y 变量。这一点非常重要，尤其是当数据集是包含多个要素的多维数据集时。

d) **秤组件:**在这里，您决定使用哪种秤，例如线性秤、对数秤等。

e) **标签组件:**这包括轴标签、标题、图例、使用的字体大小等。

f) **伦理成分**:在这里，你要确保你的可视化讲述真实的故事。在清理、汇总、操作和生成数据可视化时，您需要意识到您的行为，并确保您没有使用您的可视化来误导或操纵您的受众。

重要的数据可视化工具有 Python 的 matplotlib 和 seaborn 包，R 的 ggplot2 包。

## 6.线性回归基础

学习简单和多元线性回归分析的基础。线性回归用于具有连续结果的监督学习。下面给出了一些执行线性回归的工具:

Python: NumPy，pylab，sci-kit-learn

r:插入符号包

## 7.机器学习基础

**a)监督学习(连续变量预测)**

*   基本回归
*   多元回归分析
*   正则回归

**b)监督学习(离散变量预测)**

*   逻辑回归分类器
*   支持向量机(SVM)分类器
*   k 近邻(KNN)分类器
*   决策树分类器
*   随机森林分类器
*   朴素贝叶斯

**c)无监督学习**

*   Kmeans 聚类算法

用于机器学习的 Python 工具:Scikit-learn，Pytorch，TensorFlow。

## 8.时间序列分析基础

在结果依赖于时间的情况下，用于预测模型，例如预测股票价格。有 3 种分析时间序列数据的基本方法:

*   指数平滑法
*   ARIMA(自回归综合移动平均)，它是指数平滑的推广
*   GARCH(广义自回归条件异方差)，这是一个分析方差的类 ARIMA 模型。

这 3 种技术可以用 Python 和 r 实现。

## 9.生产力工具基础

了解如何使用基本的生产力工具，如 R studio、Jupyter notebook 和 GitHub，是必不可少的。对于 Python 来说，Anaconda Python 是最好安装的生产力工具。AWS、Azure 等先进的生产力工具也是需要学习的重要工具。

## 10.数据科学项目规划基础

学习如何规划项目的基础知识。在建立任何机器学习模型之前，认真坐下来计划你希望你的模型完成什么是很重要的。在深入研究编写代码之前，了解要解决的问题、数据集的性质、要构建的模型的类型以及如何训练、测试和评估模型是非常重要的。在从事数据科学项目时，项目规划和项目组织对于提高工作效率至关重要。下面提供了一些用于项目规划和组织的资源。

## 数据科学自学的有用资源

[机器学习的基本数学技能](https://medium.com/towards-artificial-intelligence/4-math-skills-for-machine-learning-12bfbc959c92)

[3 个最佳数据科学 MOOC 专业](https://medium.com/towards-artificial-intelligence/3-best-data-science-mooc-specializations-d58da382f628)

[进入数据科学的 5 个最佳学位](https://towardsdatascience.com/5-best-degrees-for-getting-into-data-science-c3eb067883b1)

[2020 年开始数据科学之旅的 5 个理由](https://towardsdatascience.com/5-reasons-why-you-should-begin-your-data-science-journey-in-2020-2b4a0a5e4239)

[数据科学的理论基础——我应该关心还是仅仅关注实践技能？](https://towardsdatascience.com/theoretical-foundations-of-data-science-should-i-care-or-simply-focus-on-hands-on-skills-c53fb0caba66)

[机器学习项目规划](https://towardsdatascience.com/machine-learning-project-planning-71bdb3a44349)

[如何组织您的数据科学项目](https://towardsdatascience.com/how-to-organize-your-data-science-project-dd6599cf000a)

[大型数据科学项目的生产力工具](https://medium.com/towards-artificial-intelligence/productivity-tools-for-large-scale-data-science-projects-64810dfbb971)

[数据可视化的艺术——使用 Matplotlib 和 Ggplot2 进行天气数据可视化](https://medium.com/p/4d4b48b5b7c4?source=post_stats_page---------------------------)

[使用协方差矩阵图进行特征选择和降维](https://medium.com/towards-artificial-intelligence/feature-selection-and-dimensionality-reduction-using-covariance-matrix-plot-b4c7498abd07)

[数据科学 101 —包含 R 和 Python 代码的中型平台短期课程](https://medium.com/towards-artificial-intelligence/data-science-101-a-short-course-on-medium-platform-with-r-and-python-code-included-3cdc9d489c6d)

更多资源请点击此处:

[](https://medium.com/@benjaminobi) [## 本杰明·奥比·塔约博士——中等

### 阅读 Benjamin Obi Tayo 博士在媒体上的文章。物理学家，数据科学教育家，作家。兴趣:数据科学…

medium.com](https://medium.com/@benjaminobi) 

如有疑问，请发电子邮件给我:benjaminobi@gmail.com