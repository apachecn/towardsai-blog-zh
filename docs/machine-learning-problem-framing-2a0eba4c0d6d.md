# 机器学习问题框架

> 原文：<https://pub.towardsai.net/machine-learning-problem-framing-2a0eba4c0d6d?source=collection_archive---------0----------------------->

## [云计算](https://towardsai.net/p/category/cloud-computing)，[机器学习](https://towardsai.net/p/category/machine-learning)

## 本文将围绕 GCP 专业机器学习工程师认证[第一节:ML 问题框架](https://cloud.google.com/certification/guides/machine-learning-engineer)。

![](img/d5d291408339bf2f40c3335d7d66a6f5.png)

由 [Unsplash](https://unsplash.com/s/photos/problem?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上的[滑块](https://unsplash.com/@slidebean?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)拍照

如果你打算参加认证，这将是一个很好的起点。如果你没有，那么这将帮助你开发在快速发展的机器学习生态系统中取得成功所需的基本知识。

**这不是认证学习指南。**

本文的目的是对复杂的想法提供一个简单的解释，并给出主题的一个广泛的观点。大纲模仿 [GCP 专业机器学习工程师认证](https://cloud.google.com/certification/guides/machine-learning-engineer)指南。

如果你愿意的话，我已经嵌入了好的阅读材料的链接。

# 将业务挑战转化为 ML 用例

每个用例都是不同的。一刀切的方法是行不通的。理解业务问题、期望的结果以及组织资产的优势和劣势的能力是关键。基本上，你需要理解硬币的两面，期望和能力。有了这些知识，你就可以着手设计解决方案，它可能包括也可能不包括 ML，不管怎样都可以。

*   **定义业务问题:**一个组织是为一个目的而建立的。组织内的业务单位专注于独立但相关的活动，以交付共同的预期结果。业务问题需要以可量化的方式来定义。可测量的度量标准必须在项目的早期定义。这有助于团队专注于几个切实可行的目标。
*   **识别非 ML 解决方案:**不是所有的业务问题都需要 ML 解决方案。即使 ML 解决方案是合适的，但是您没有构建它所需的必要支持结构，您可能需要重新考虑您的策略，从非 ML 解决方案开始，然后在稍后的日期回到 ML 解决方案。
*   **定义输出用途:**项目的输出不一定是最终产品。你必须意识到大局，以及你的努力如何融入整体。例如，您的输出可以给出一个信用评级，该信用评级可以与申请人的其他属性一起用于决策过程。
*   **管理不正确的结果:**失败管理是项目交付的关键组成部分。解决混淆矩阵的计划，尤其是在涉及分类模型的 ML 解决方案中，可能是成功与失败的区别。混淆矩阵是一个简单的概念:如果你的预测与实际相符，无论是正面还是负面，你就是好的。当你预测是积极的，但实际是消极的，或者反之亦然时，混乱就出现了。考虑一下新冠肺炎测试的场景，基于某些属性的测试结果可能是负面的，但你实际上可能是正面的，也可能不是。您的预测和实际情况之间的差异程度以及您对此采取的措施，尤其是所做决策的关键程度，将是您项目的决定性因素。

[](https://towardsdatascience.com/understanding-confusion-matrix-a9ad42dcfd62) [## 理解混淆矩阵

### 当我们得到数据后，经过数据清理、预处理和争论，我们做的第一步是把它提供给一个…

towardsdatascience.com](https://towardsdatascience.com/understanding-confusion-matrix-a9ad42dcfd62) 

*   **识别数据源:**ML 解决方案的基础是数据，无论大小。数据的真实性、可追溯性和质量将直接影响对您的解决方案的信任。因此，当您确定一个数据源时，重要的是您要知道它的谱系，并在将来有明确的所有权定义。数据的任何质量问题都会严重损害解决方案的可信度。

# 定义 ML 问题

理解你的问题领域对于选择正确的 ML 模型是至关重要的。支持未来发展的数据的可用性、质量和可靠性将在模型决策中发挥至关重要的作用。选择一个或多个模型不是技术团队的工作。因此，每个相关人员都必须了解各种类型、结果和基本的输入输出格式。

数据可以结构化。想象一个 excel 类型的表格或者像文本这样的非结构化表格。非结构化数据必须重新格式化为表格和可计算的结构，以便进一步进行有意义的分析。

数据集将具有要素(也称为属性)。让我们考虑一个有 100 行名为 **Person** 的数据集，其特征包括:姓名、性别、出生日期、资格、地址、城市、州、邮政编码、工资。

(清理之后)我们要做的第一件事是获得额外的特征，如年龄、年龄组、工资级别。这被称为**特征工程**。

如果您的挑战是:

1.  根据年龄识别数据集中的聚类。然后**无监督学习**模型可以帮忙。根据识别的聚类，您可以标记行，然后使用此标记的数据集来应用监督学习模型。
2.  根据其他类似特征，确定新员工的薪金或薪金级别。您将使用一个**监督学习**模型，该模型可以预测一个工资级别( ***类别*** )或工资( ***回归*** )。

[](https://medium.com/@randylaosat/a-beginners-guide-to-machine-learning-dfadc19f6caf) [## 机器学习初学者指南

### 我应该现在学…还是以后学？学习是一种普遍的技能/特性，是任何生物在这方面获得的…

medium.com](https://medium.com/@randylaosat/a-beginners-guide-to-machine-learning-dfadc19f6caf) 

# 定义业务成功标准。

任何努力的成功都很大程度上依赖于测试做得如何。在 ML 项目中，如何将数据集分成训练和测试是很重要的。以多种方式分割数据集，然后训练模型以确定模型的准确性，这将增强您对解决方案的信心。

所需的准确度将取决于你的问题的性质。如果你只是简单地寻找购买行为，那么任何产出都是好的，但你是为了目标营销而寻找购买行为，这将需要资金，那么就需要高度的信心。

# 识别 ML 解决方案的可行性和实施的风险。

*   **评估和传达业务影响:**如果您的解决方案将影响应用程序的行为或最终用户体验，那么提前传达变更是非常重要的。比方说，如果您的 ML 解决方案嵌入在呼叫中心应用程序中，那么对于每一个打入的销售电话，您都知道在呼叫发起区域完成的销售额或呼叫者的邮政编码。呼叫中心代理必须经过培训，才能在呼叫脚本中使用这些信息。
*   **评估 ML 解决方案准备情况:**开发解决方案不是最终目标。用法是。您的 ML 解决方案必须通过可用的 API 接口融入您的生态系统，以使其变得有用。
*   **评估数据准备程度:**“学习”部分是 ML 与标准的基于规则的应用程序设计的真正区别。为了主动学习，ML 模型使用的数据集应该是新的，以便解决方案可以适应实时数据捕捉到的不断变化的行为。

[](https://www.mckinsey.com/business-functions/mckinsey-analytics/our-insights/confronting-the-risks-of-artificial-intelligence#) [## 直面人工智能的风险

### 人工智能(AI)被证明是一把双刃剑。虽然大多数新技术都是如此…

www.mckinsey.com](https://www.mckinsey.com/business-functions/mckinsey-analytics/our-insights/confronting-the-risks-of-artificial-intelligence#)