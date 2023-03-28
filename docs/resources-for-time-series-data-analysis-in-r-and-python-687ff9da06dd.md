# R 和 Python 中的时序数据分析资源

> 原文：<https://pub.towardsai.net/resources-for-time-series-data-analysis-in-r-and-python-687ff9da06dd?source=collection_archive---------2----------------------->

## 数据可视化

## 节省您在数据争论、可视化和预测方面的时间

![](img/3bbad4cf212abc9418f496783b88c653.png)

凯勒·琼斯在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

那些想要进入时间序列分析或者只是提升技能的人，寻找合适的工具和资源可能会令人沮丧和耗时。但是你会惊讶地发现，只有很少的资源能够满足你 95%的分析需求。

> 有 Python，有 R，有 ggplot，matplotlib，seaborn，tidyverse ……你迷路了！！

我曾经有过这样的经历，所以我知道如果在需要的时候，正确的信息就在手边，我可以节省多少时间。这篇文章试图把我学到的教训还给大家。

Python 和 R 都是大多数数据科学家的热门切入点，我们每个人对这些语言都有不同的熟悉程度。因此，我将尝试在这里列出两个阵营的一些资源。

# **数据来源**

首先，我将列出一些您可以在实践中立即访问的数据源。前两个是玩具数据集，不需要处理，非常节省时间。接下来的两个需要一些清理，但伟大的数据集来探索，看看现实世界的数据是什么样子，他们可以讲述什么故事。

*   [已清理，玩具数据(单变量)](https://www.kaggle.com/chirag19/air-passengers)；
*   [清洗过的，玩具数据(多元)](https://raw.githubusercontent.com/jenfly/opsd/master/opsd_germany_daily.csv)；
*   [真实世界数据(单变量)](https://www.census.gov/econ/currentdata/dbsearch?program=RESSALES&startYear=1963&endYear=2020&categories=ASOLD&dataType=TOTAL&geoLevel=US&adjusted=1&notAdjusted=0&errorData=0)；
*   [现实世界(多元)](https://www.kaggle.com/rohanrao/air-quality-data-in-india)。

我认为你应该从第一个开始，随着时间序列分析的进展，按这个顺序进行。

# **数据角力**

当您准备好数据时，真正的乐趣就开始了。但是在你到达那里之前，你需要经历不可避免的数据争论过程。

> 有人说 80%的数据科学工作其实就是数据角力。

导入数据后，您必须经历处理缺失值、命名和重命名列、根据需要对数据进行切片和切块的整个过程。

在 Python 中，`pandas`和`numpy`是你处理所有数据争论工作的最好朋友。在 R 中，如果不安装`tidyverse`和`dplyr`包，你去不了任何地方。

需要记住的一点是，您正在处理的时间序列数据中会有一个日期列。通常这个日期列存储为一个*字符串*，而不是一个日期时间对象。所以您需要将它转换成 datetime 对象。这种简单的转换将释放出分析、可视化和预测时间序列的巨大潜力。

例如，在 python 中，您可以通过以下方式进行转换:

# **2。数据可视化**

老实说，你在互联网上任何地方遇到的超过 70%的时间序列数据分析实际上是视觉叙事。事实上，正是视觉方面赋予了时间序列数据最大的力量。

在 Python 中，如果你只想尝试一个可视化库，那应该是`seaborn`。它建立在`matplotlib`之上，因此只需几行代码，您就可以创建漂亮的图形:

对于交互式可视化，你可能想看看`plotly`，它改变了我们在网络上查看数据和与数据交互的方式。

在 R 环境中，`ggplot2`是大多数数据科学家创建强大、优雅的可视化的*和*首选库。

# **3。预测**

预测是跨行业商业决策的重要组成部分。预测未来可以简单到外推历史观察的趋势，应用复杂的算法。

在 Python 世界中，`statsmodels`可以处理您需要的最有用的预测技术。我最喜欢这个库的是它所谓的“状态空间”模型，比如 SARIMAX，VARMAX。

你也可以试试脸书的`prophet`套餐。这是一个易于使用和直观的预测包。

对于 LSTM 等技术的深度学习，你需要去别处看看。`Tensorflow`包含所有可用的代码[以及单变量和多变量预测的示例](https://www.tensorflow.org/tutorials/structured_data/time_series)。但需要注意的是，理解 LSTM 过程及其参数化可能会导致你的大量眼泪、汗水和沮丧，所以要为上山做好准备。

关于 Python 的所有优点，如果您主要是一个 R 用户，那么您很幸运！是所有预测软件中最容易使用和学习的。它附带了一本名为“[预测原则和实践](https://otexts.com/fpp2/)的相关开放书籍，里面有所有的理论、代码和例子。老实说，我认为这是所有预测解决方案的“一站式商店”，尤其是对初学者而言。

我不想插一句，但是我写了几篇关于[单变量](https://towardsdatascience.com/7-forecasting-techniques-youll-never-use-but-should-know-them-anyway-c9ba645c8ba0?source=your_stories_page---------------------------)和[多变量](https://towardsdatascience.com/multivariate-time-series-forecasting-653372b3db36)预测技术的文章，如果你想看看的话。

![](img/503a4acc4a0fbffce30cfc5b7934833b.png)

图:GDP 的多元预测(来源:作者)

# 最终想法:Python 还是 R？

老生常谈，但真的“视情况而定”。

我不打算在这里重新提起**“Python vs R”**之战，但实际上它确实值得一些讨论。和很多数据科学家一样，我开始用 R 编程，然后过渡到 Python。从那以后，为了各种各样的需要，我在这两者之间来回奔波。我从来不觉得有义务坚持使用其中的一个，因为我总是优先考虑处理手头问题的最佳工具。从我的经验来看，我发现对于初学者来说，R 更容易一些。如果你只是安装了`forecast`和`ffp2`包，你可以马上开始做你的分析和可视化。

但是当你转向更高级的算法，如 LSTM 等。，您可能已经超越了 R，应该转而使用 Python 来利用深度学习平台，比如`Tensorflow`。

但是我会让你决定什么是你最舒服的。