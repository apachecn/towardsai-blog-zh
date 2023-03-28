# 数据科学家编码练习

> 原文：<https://pub.towardsai.net/data-scientist-coding-exercise-e62f4de7df9e?source=collection_archive---------0----------------------->

![](img/fc8c0f89303c8c9114d425164587d3c2.png)

资料来源:Pexels

## [数据科学](https://towardsai.net/p/category/data-science)

## 比较两个行业的带回家的编码挑战问题。它们的范围和难度各不相同。提供了建议的解决方案。

A 你是一名数据科学家吗？你目前在申请数据科学家的职位吗？你最近有数据科学家的面试吗？你担心带回家的编码练习吗？

如果你有以上任何一个问题，那么你来对地方了。本文将帮助您回答一些关于数据科学家编码练习的问题。

在经历了几次数据科学家面试过程后，我想与有抱负的数据科学家分享我的编码经验。希望他们能从我的经历中学到一些东西，帮助他们更好地准备面试过程中的这个重要阶段。

本文将重点描述带回家的编码练习。关于如何为一个带回家的挑战问题写一份正式的项目报告的更多信息，请参见以下文章: [**数据科学编码练习项目报告**](https://towardsdatascience.com/project-report-for-data-science-coding-exercise-9a9c76a09be8) 。

# 带回家的挑战问题(编码练习)

那么，你已经成功地通过了面试过程的初步筛选阶段。现在是面试过程中最重要的一步，即**带回家的编码挑战**。这通常是一个数据科学问题，例如机器学习模型、线性回归、分类问题、时间序列分析等。一般来说，面试团队会给你提供项目方向和数据集。如果幸运的话，他们可能会提供一个干净的小型数据集，并以逗号分隔值(CSV)文件格式存储。这样，您就不必担心挖掘数据并将其转换成适合分析的形式。在我的几次采访中，我使用了两种类型的数据集，一种有 160 个观察值(行),另一种有 50，000 个观察值。如下所述，不同公司的带回家的编码工作是不同的。

# 示例 1: ***数据科学家职位编码练习(带回家)***

**指令**

*这个编码练习应该用 python 来执行(python 是团队使用的编程语言)。你可以自由使用互联网和任何其他图书馆。请将您的作品保存在 Jupyter 笔记本中，并通过电子邮件发送给我们进行审核。*

*数据文件:cruise_ship_info.csv(该文件将通过电子邮件发送给您)*

***目标:*** *建立一个回归器，为潜在的船舶购买者推荐“船员”规模。请执行以下步骤(提示:使用 numpy、scipy、pandas、sklearn 和 matplotlib)*

*1。读取文件并显示列。*

*2。计算数据的基本统计数据(计数、平均值、标准差等)，检查数据并陈述你的观察结果。*

*3。选择对预测“团队”规模可能很重要的列。*

*4。如果您删除了列，请解释为什么要删除这些列。*

*5。对分类特征使用一次性编码。*

*6。创建训练集和测试集(将 60%的数据用于训练，其余用于测试)。*

*7。建立一个机器学习模型来预测“船员”的规模。*

8。计算训练集和测试数据集的皮尔逊相关系数。

9。描述模型中的超参数，以及如何更改它们来提高模型的性能。

10。什么是正规化？你的模型中的正则化参数是什么？

*为测试和训练集绘制正则化参数值与皮尔逊相关性的曲线图，并查看您的模型是否有偏差问题或方差问题。*

**评论和备注:**这是一个很直白的问题的例子。数据集干净小巧(160 行 9 列)，指令非常清晰。因此，您所需要做的就是遵循指令并生成您的代码。还要注意，指令明确指定 python 作为建模的编程语言。完成这项编码任务的时间是 3 天。只需提交最终的 Jupyter 笔记本，不需要正式的项目报告。

# **示例 2:数据科学带回家挑战**

**指令**

在这个问题中，你将预测贷款组合的结果。每笔贷款计划在 3 年内偿还，结构如下:

*   首先，借款人收到资金。这个事件被称为起源。
*   *然后，借款人定期还款，直到发生以下情况之一:*

*(i)借款人在 3 年期限结束前停止付款，通常是由于财务困难。这一事件被称为销账，然后贷款被称为已销账。*

*(ii)借款人持续还款，直至贷款发放日之后 3 年。至此，债务已全部还清。*

*在附加的 CSV 中，每行对应一笔贷款，列的定义如下:*

*   *标题为“自发起以来的天数”的列表示从发起到收集数据的日期之间经过的天数。*
*   *对于在收集数据之前已注销的贷款，标题为“从发起到注销的天数”的列表示发起和注销之间经过的天数。对于所有其他贷款，此栏为空白。*

***目标*** *:我们希望您估计一下，在这些贷款的 3 年期限全部结束时，将会有多少比例的贷款被冲销。请包括你如何得到你的答案的一个严格的解释，并且包括你使用的任何代码。你可以做出简化的假设，但是请明确地陈述这些假设。请随意以您喜欢的任何形式提出您的答案；特别是 PDF 和 Jupyter 笔记本都可以。此外，我们希望这个项目不会占用您超过 3-6 个小时的时间。*

**评论和备注:**这里的数据集比较复杂(有 50000 行，2 列；和许多丢失的值)，问题不是很简单。你必须严格检查数据集，然后决定使用什么模型。这个问题将在一周内解决。它还规定提交一份正式的项目报告和一份 R 脚本或 Jupyter 笔记本文件。

# 带回家挑战练习的建议解决方案

有关数据集和建议的解决方案，请参见以下链接:

[*样品 1 推荐溶液*](https://github.com/bot13956/ML_Model_for_Predicting_Ships_Crew_Size)

[*样品 2 推荐溶液*](https://github.com/bot13956/Monte_Carlo_Simulation_Loan_Status)

**注**:上述解决方案仅为推荐方案。请记住，数据科学或机器学习项目的解决方案不是唯一的。在查看示例解决方案之前，我建议您自己解决这些问题。

# 结束语

带回家的编码练习为您提供了一个展示数据科学项目工作能力的绝佳机会。你需要在这里展示出非凡的能力。例如，如果要求您构建多元回归模型，请确保您能够充分理解以下高级概念:

(一)特征标准化

(二)超参数调谐

㈢交叉验证

(四)降维技术，如 PCA(主成分分析)和 Lasso 回归

(五)泛化误差

㈥不确定性量化

(vii)展示使用先进的数据科学技术的能力，例如 scikit-learn 的管道工具来建立模型

(viii)能够从实际应用的角度解释你的模型

如果您对问题的某些方面不了解，请随时联系数据科学面试团队。他们可能会提供一些提示或线索。

# 摘要

总之，我们已经讨论了来自两个不同行业的两个带回家的示例编码练习。编码练习的范围和复杂程度各不相同，这取决于你申请的公司。带回家的编码练习为您提供了一个展示数据科学项目工作能力的绝佳机会。你需要利用这个机会展示你在理解数据科学和机器学习概念方面的非凡能力。如果您对问题的某些方面不了解，请随时联系数据科学面试团队。他们可能会提供一些提示或线索。

# 其他数据科学/机器学习资源

[数据科学课程](https://medium.com/towards-artificial-intelligence/data-science-curriculum-bf3bb6805576)

[机器学习的基本数学技能](https://medium.com/towards-artificial-intelligence/4-math-skills-for-machine-learning-12bfbc959c92)

[3 个最佳数据科学 MOOC 专业](https://medium.com/towards-artificial-intelligence/3-best-data-science-mooc-specializations-d58da382f628)

[进入数据科学的 5 个最佳学位](https://towardsdatascience.com/5-best-degrees-for-getting-into-data-science-c3eb067883b1)

[2020 年开始数据科学之旅的 5 个理由](https://towardsdatascience.com/5-reasons-why-you-should-begin-your-data-science-journey-in-2020-2b4a0a5e4239)

[数据科学的理论基础——我应该关心还是仅仅关注实践技能？](https://towardsdatascience.com/theoretical-foundations-of-data-science-should-i-care-or-simply-focus-on-hands-on-skills-c53fb0caba66)

[机器学习项目规划](https://towardsdatascience.com/machine-learning-project-planning-71bdb3a44349)

[如何组织你的数据科学项目](https://towardsdatascience.com/how-to-organize-your-data-science-project-dd6599cf000a)

[大型数据科学项目的生产力工具](https://medium.com/towards-artificial-intelligence/productivity-tools-for-large-scale-data-science-projects-64810dfbb971)

[数据科学作品集比简历更有价值](https://towardsdatascience.com/a-data-science-portfolio-is-more-valuable-than-a-resume-2d031d6ce518)

[使用协方差矩阵图进行特征选择和降维](https://medium.com/towards-artificial-intelligence/feature-selection-and-dimensionality-reduction-using-covariance-matrix-plot-b4c7498abd07)

[数据科学 101 —包含 R 和 Python 代码的中型平台短期课程](https://medium.com/towards-artificial-intelligence/data-science-101-a-short-course-on-medium-platform-with-r-and-python-code-included-3cdc9d489c6d)

如有问题和疑问，请发邮件给我:benjaminobi@gmail.com