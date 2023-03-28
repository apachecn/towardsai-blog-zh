# 2022 年的 12 种基本数据科学工具及其最佳实践

> 原文：<https://pub.towardsai.net/12-essential-data-science-tools-in-2022-along-with-their-best-practices-ffae0b9f865f?source=collection_archive---------5----------------------->

## 考虑建立一个工具包，无论是新手还是高级专业人员，包括这 12 个日常使用的工具

![](img/761fd56f45240967652f7c49b5db2099.png)

来自 Pixabay 的 RyanMcGuire

数据科学工具是帮助数据科学家完成工作的任何专门构建的功能。这本身可以是任何东西，从自动化任务的网站到更复杂的软件程序。

1.r:一种用于统计计算和图形的开源编程语言和软件环境。它被统计学家和数据科学家广泛用于开发统计软件和数据分析。r 是有效的，因为:

*—一个强大的数据分析工具，具有许多内置的统计和机器学习功能。*

*—一种解释型语言，意味着代码可以在不编译的情况下运行，总体上使测试新想法和快速原型化解决方案变得切实可行。*

*—拥有一个庞大而活跃的社区，其中有许多有用的在线资源。*

## *— R 的绘图和可视化功能非常有效，可以轻松生成复杂的图表和图形。我还没有遇到一个人声称 Python 比 r 有更好的图表和可视化能力*

![](img/6d9481edb16372bd55800239d71b6ef5.png)

来自普里皮克的 https://www.freepik.com/photos/sports-equipment

2.Python: Python 是一种广泛使用的高级解释语言，以其易用性和可读性而闻名。它是数据科学家中用于数据争论、机器学习和深度学习的流行语言。

3.Jupyter Notebook:一个基于网络的交互式计算环境，用于创建 Jupyter 笔记本。Jupyter 笔记本是结合了实时代码、方程式、可视化和叙述性文本的文档。数据科学家使用它们进行数据清理、探索、可视化和建模。

4.Pandas:用于数据分析的 Python 库，提供了高性能、易于使用的数据结构和数据分析工具。它被数据科学家广泛用于数据争论、探索性数据分析和构建机器学习模型。

5.NumPy:用于科学计算的 Python 库，提供了强大的对象数组和广泛的数学函数。它被数据科学家广泛用于数值计算和处理大型数据集。

![](img/02730156fb0bc120cd62467400adae39.png)

来自 Pixabay 的 [bodobe](https://pixabay.com/users/bodobe-1222375/)

6.Matplotlib:一个 Python 绘图库，可以生成出版物质量的图形。数据科学家经常使用它来创建数据分析的可视化。三个最佳实践包括:

*—在同一图形中绘制多条线时，最好对所有的线使用线绘制功能；这种方法将确保地块线具有相同的格式，并且不会无意中出现差异。*

*——为了让数字更具可读性，使用白色背景可能更好:这将与大多数配色方案形成良好的对比，并使情节主线更容易看到。*

## *—当使用 Matplotlib 创建散点图时，请考虑使用散点图函数来确保数据点间隔均匀，并且不存在无意的聚集。*

![](img/ac3ff167abfbb61ae80ef0b401bf221a.png)

由来自 Pexels 的 [Pixabay](https://www.pexels.com/@pixabay/)

7.Seaborn:基于 Matplotlib 的 Python 可视化库，提供美观的统计图形。数据科学家经常使用它来创建信息丰富且有吸引力的数据分析可视化。根据我的经验，三个最佳实践可能包括:

—在白色背景上绘图；

—使用颜色创建易于理解的可视化效果；和

—使用网格线帮助用户在可视化中确定自己的方向。

8.Scikit-learn:一个 Python 机器学习库，为数据挖掘和数据分析提供了简单高效的工具。它被希望快速高效地建立机器学习模型的数据科学家广泛使用。我认为以下是几个基本的最佳实践:

-特征选择:考虑选择将用于构建模型的特征。对此有许多方法；尽管如此，该过程可以手动完成，或者使用特征选择算法来完成。

—要素缩放:这是通过使用标准化或规范化将要素提升到相同的比例。

—交叉验证:要评估 Scikit-learn 模型的性能，使用交叉验证是关键。这种技术将数据拆分为多个折叠，然后使用每个折叠来训练和测试模型。

# —超参数优化:为了充分利用 Scikit-learn 模型，调整超参数非常重要。您可以通过执行网格搜索或随机搜索来实现这一点。

—管道:管道是一种工具，可用于将 Scikit-learn 中的[5]多个操作链接在一起(例如，在特征选择、特征缩放和建模的情况下)。

—模型集成:集成是组合多个模型以创建更具体的模型的方法。这种组合实现可以通过投票、平均或堆叠来实现[4]。

—保存和加载模型:保存已训练的模型通常很有帮助，以便以后使用。Scikit-learn 提供了一种通过 pickle 模块实现这一点的方法[3]。

![](img/3b07cb5c1fd74e1fa20a6b265303a556.png)

来自 Pexels 的 Engin Akyurt

9.xboost[1]:是一个梯度增强库，提供了各种机器学习算法的高效实现。希望在分类和回归等预测建模任务中获得最先进结果的数据科学家经常使用它。以下是三个最佳实践:

—使用多个提前停止轮次帮助模型找到最佳训练轮次数，并防止过度拟合。

—尝试不同的学习率值。较低的学习速率可以帮助模型收敛，而较高的学习速率可以帮助模型学习得更快。

—使用足够大的 max_depth 值[6]，以帮助模型更好地了解数据结构并防止过度拟合。

10.Keras [2]:是一个高级神经网络 API，允许简单快速地对深度学习模型进行原型开发。这在数据科学家中很受欢迎，他们希望尝试不同的深度学习架构，而不必快速担心实现的潜在细节[10]。Keras 的三个最佳实践:

—使用 Keras Functional API [7]构建具有多个输入和输出的模型。

—使用 Keras 子类化[8]创建自定义图层和模型。

—使用 Keras 回调 API [9]编写自定义回调，以在培训期间监控培训和验证指标。

11.Plotly:一项网络服务，允许您使用 Python 编程语言创建和共享交互式在线绘图。

12.Bokeh:一个免费的开源 Python 库，提供了像 D3.js 这样的 JavaScript 库中的交互式可视化功能。

如果您对进一步扩展此主题有任何编辑/修订建议或建议，请考虑与我分享您的想法。

# **另外，请考虑订阅我的每周时事通讯:**

[](https://pventures.substack.com/) [## 周日报告#1

### 设计思维与人工智能的共生关系设计思维能向人工智能揭示什么，以及人工智能如何拥抱……

pventures.substack.com](https://pventures.substack.com/) 

# **关于这篇文章，我写了以下一些东西:您可能对它们感兴趣:**

## 进一步阅读 R，我将在这里介绍它的最佳实践:

[](/i-code-in-python-for-ml-and-nlp-but-you-should-learn-r-before-2023-747474293c23) [## 我用 Python 为 ML 和 NLP 编写代码，但是你应该在 2023 年之前学会 R

### 您应该学习 R 的 6 个原因，什么使 R 有效，R 在哪里闪耀，以及 R 的最佳实践。

pub.towardsai.net](/i-code-in-python-for-ml-and-nlp-but-you-should-learn-r-before-2023-747474293c23) 

## 我在这里会更多地谈论 XGBoost:

[](/xgboost-its-present-day-powers-and-use-cases-b4cac3d6e1d5) [## XGBoost:机器学习的当代力量和用例

### 基于当今实现的 XGBoost 深度挖掘

pub.towardsai.net](/xgboost-its-present-day-powers-and-use-cases-b4cac3d6e1d5) 

如果您对进一步扩展此主题有任何编辑/修订建议或建议，请与我分享您的想法。

*参考文献:*

*1。xboost 文档—xboost 1 . 6 . 1 文档。(n.d .)。检索日期 2022 年 7 月 18 日，来自*[*https://xgboost.readthedocs.io/en/stable/*](https://xgboost.readthedocs.io/en/stable/)

*2。小组，k .(未注明)。keras:Python 深度学习 API。检索 2022 年 7 月 18 日，来自*[*https://keras . io*](https://keras.io/)

*3。Pickle — Python 对象序列化— Python 3.10.5 文档。(未注明)。检索 2022 年 7 月 18 日，来自*[](https://docs.python.org/3/library/pickle.html)

**4。sk learn . ensemble . voting classifier .(未标明)。sci kit-学习。2022 年 7 月 18 日检索，来自*[*https://sci kit-learn . org/stable/modules/generated/sk learn . ensemble . voting classifier . html*](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.VotingClassifier.html)*

**5。Sklearn.pipeline.Pipeline .(未标明)。sci kit-学习。2022 年 7 月 18 日检索，来自*[*https://sci kit-learn . org/stable/modules/generated/sk learn . pipeline . pipeline . html*](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html)*

**6。XGBoost 参数— xgboost 1.6.1 文档。(未注明)。检索到 2022 年 7 月 18 日，来自*[*https://xgboost.readthedocs.io/en/stable/parameter.html*](https://xgboost.readthedocs.io/en/stable/parameter.html)*

**7。小组，k .(未注明)。Keras 文档:函数式 API。检索 2022 年 7 月 18 日，转自*[*https://keras.io/guides/functional_api/*](https://keras.io/guides/functional_api/)*

**8。小组，k .(未注明)。Keras 文档:通过子类化创建新的层和模型。2022 年 7 月 18 日检索，来自*[*https://keras . io/guides/making _ new _ layers _ and _ models _ via _ subclass ing/*](https://keras.io/guides/making_new_layers_and_models_via_subclassing/)*

**9。小组，k .(未注明)。Keras 文档:回调 API。检索 2022 年 7 月 18 日，转自*[*https://keras.io/api/callbacks/*](https://keras.io/api/callbacks/)*

**10。科尔河(未标明)。用实体框架实现知识库模式——rycole.com。2022 年 7 月 18 日检索，来自*[*http://ry cole . com/2014/01/25/entity-framework-repository-pattern . html*](http://rycole.com/2014/01/25/entity-framework-repository-pattern.html)*