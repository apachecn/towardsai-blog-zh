# 为什么这位人工智能专家说 Python 不是人工智能的未来

> 原文：<https://pub.towardsai.net/why-this-ai-expert-says-python-isnt-the-future-of-ai-97fbcb4f6796?source=collection_archive---------0----------------------->

## [新闻](https://towardsai.net/p/category/news)、[观点](https://towardsai.net/p/category/opinion)、[科技](https://towardsai.net/p/category/technology)

## 什么是？

![](img/c408062bd7e3a8befa8382e80eb9a732.png)

[“2014 年世界经济论坛杰瑞米·霍华德-IT 战略转变”](https://www.flickr.com/photos/15237218@N00/15171960486)作者 [WEF](https://www.flickr.com/photos/15237218@N00) 经 [CC BY-NC-SA 2.0](https://creativecommons.org/licenses/by-nc-sa/2.0/?ref=ccsearch&atype=rich) 授权

人工智能专家、世界上最大的数据科学社区 Kaggle 的前总裁杰瑞米·霍华德说:“Python 不是机器学习的未来。不可能的。”

这里有两个主要原因。

# #1.很慢。

默认情况下，Python 是一种非常慢的语言。正如霍华德所说，“除非你调用一些外部代码，否则你不能并行运行任何东西。”

的确，Julia 和 Python 之间的 [**速度对比**](https://theiotmagazine.com/julia-vs-python-will-it-unseat-the-king-of-programming-8220e4cd2e0a#:~:text=Julia%2C%20an%20excellent%20choice%20for,become%20easier%20to%20speed%20up.) 表明，Julia 无疑是赢家，要让 Python 更快还需要做额外的工作，比如通过使用 Cython，使用 PyPy 或 Numba 之类的加速应用，尽可能保持代码轻量，避免循环等等。

# #2.开销太大了。

由于 Python 的速度限制，在“让它足够快地工作”方面有很多精神负担。

Python 中的人工智能开发人员不得不额外关注每一步的速度和效率，而不是专注于实际的模型构建。

# 那么，还有什么选择呢？

Howard 说，“我真的希望 Julia 真的成功，”因为除了速度之外，它还有几个优于 Python 的优点:

*   一个精心设计的类型系统
*   精心设计的调度系统

在一行程序中，Julia 是“MATLAB 遇上 Python”Julia 是一种具有丰富类型系统的编译语言。

霍华德的观点是，Julia 还没有起飞，因为“它还没有得到企业的认可”，所以它依赖于其核心开发人员来维持。

核心开发者现在运营着 Julia Computing，霍华德说，除了从风投那里获得资金，它似乎没有太多可持续的商业模式。

# 第三种选择

Python 和 Julia 之间的战争的想法实际上有点误导，因为它暗示首先需要编码来进行机器学习。

事实上，你不需要任何编码语言来构建模型，而且有一个更大的趋势是走向无代码人工智能工具，从谷歌的 AutoML 和微软的 Azure AI 这样的巨头到像 [**这样的初创公司。艾**](http://obviously.ai) 。

这种“第三种选择”越来越受欢迎，许多巨头都选择 AutoML。虽然数据科学家总是需要“从零开始”构建，例如新的最先进的模型，甚至是人工智能的大型企业部署，但 AutoML 是一个令人惊叹的解决方案，它为我们其他人民主化了机器学习。

# 摘要

Python 面临着几个挑战，限制了它在大规模深度学习应用程序中的可用性——主要是它速度慢，开销大。虽然额外的软件包可以帮助解决这个问题，但是其他语言可能是更好的选择，比如 Julia。

也就是说，这些速度上的小差异对大多数公司来说并不重要，它们越来越多地选择简单的 AutoML 解决方案。