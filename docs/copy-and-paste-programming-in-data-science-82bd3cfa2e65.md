# 数据科学中的复制和粘贴编程

> 原文：<https://pub.towardsai.net/copy-and-paste-programming-in-data-science-82bd3cfa2e65?source=collection_archive---------1----------------------->

![](img/7978a5d838c398ee601559a09a6c4491.png)

戈兰·艾沃斯在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

## 数据科学

## 如何使用 GitHub 和 Medium 来提高数据科学项目的生产力和效率

## 一.导言

数据科学项目需要良好的编程背景。然而，在从事数据科学项目时，您不必总是从头开始编写代码。作为一名数据科学的追求者，你的目标应该是最大限度地减少花在代码开发上的时间，这样你就可以将精力集中在最重要的事情上，即开发可以推动组织决策的模型。感谢像 GitHub 和 Medium 这样的平台，人们可以通过利用一种叫做 ***复制和粘贴编程*** 的方法，在项目工作时利用这些平台来提高生产率和效率。

***复制粘贴编程*** 是指利用现有代码解决新的数据科学和机器学习问题。GitHub 和 Medium 等平台上有大量关于各种数据科学问题的资源，包括数据可视化、线性回归、分类问题、深度学习、神经网络、AI 等。利用复制粘贴编程的最佳方式是在 GitHub 和 Medium 上维护您已完成项目的记录。然后，每当您必须处理一个新项目时，您可以简单地复制现有的代码，只做一些修改。

## 二。案例研究:建立线性回归模型

在这一节中，我将说明如何在数据科学中使用复制和粘贴编程。假设我们有一个给定的数据集，任务是建立一个线性回归模型。在我们的模型中，我们希望执行以下步骤:

*1。读取数据文件并显示列。*

*2。计算数据的基本统计数据(计数、平均值、标准差等)并分析数据。*

*3。选择与预测变量最相关的列。*

*4。将数据划分为训练集和测试集。*

*5。建立一个机器学习模型来预测目标变量。*

6。通过计算训练和测试数据集的皮尔逊相关系数来评估模型。

7。微调模型中的超参数，以获得性能最优的模型。

8。通过执行 k 倍交叉验证来评估随机误差。

9。应用高级回归技术，如套索和弹性网正则化。

10。实施不同的回归模型，如 KNeighbors 回归(KNR)和支持向量回归(SVR)。

*11。选择具有最佳性能的最终型号。*

要解决这个问题，我可以简单地导航到我的 GitHub 帐户，搜索所有关于线性回归的已完成项目，然后选择最适合给定问题的项目。

通过搜索我的 GitHub 帐户，我找到了以下 3 个可以提供帮助的存储库:

[](https://github.com/bot13956/ML_Model_for_Predicting_Ships_Crew_Size) [## bot 13956/ML _ Model _ for _ Predicting _ Ships _ Crew _ Size

### 作者:Benjamin O. Tayo 日期:2019 年 4 月 8 日我们使用 cruise_ship_info.csv 数据集构建了一个简单的模型来预测…

github.com](https://github.com/bot13956/ML_Model_for_Predicting_Ships_Crew_Size) [](https://github.com/bot13956/Linear_vs_KNN_Regression) [## bot 13956/线性 _ vs _ KNN _ 回归

### 在 GitHub 上创建一个帐户，为 bot 13956/Linear _ vs _ KNN _ 回归开发做贡献。

github.com](https://github.com/bot13956/Linear_vs_KNN_Regression) [](https://github.com/bot13956/Machine_Learning_Process_Tutorial) [## bot 13956/机器学习过程教程

### 使用游轮数据集说明机器学习过程的广泛教程。

github.com](https://github.com/bot13956/Machine_Learning_Process_Tutorial) 

通过综合上述项目中的现有代码，我可以生成一个代码来解决给定的问题。这是一个极其省时的方法。人们可以简单地利用现有代码的可用性，而不是浪费太多时间去开发新代码。这将有助于提高生产率和效率。

如果您没有 GitHub 帐户，我鼓励您创建一个。

## 三。创建 GitHub 帐户和存储库的技巧

Github 是一个非常有用的平台，用于存储您完成的数据科学项目。这个平台使您能够与其他数据科学家或数据科学爱好者共享您的代码。有兴趣雇佣你的雇主会检查你的 GitHub 作品集，评估你完成的一些项目。所以在 GitHub 上建立一个非常强大和专业的投资组合对你来说很重要。

要建立 GitHub 投资组合，首先要做的就是创建一个 GitHub 账户。创建帐户后，您可以继续编辑您的个人资料。在编辑您的个人资料时，添加简短的个人简介和专业的个人资料图片是一个不错的主意。你可以在这里找到一个 GitHub 概要的例子:【https://github.com/bot13956】**。**

**现在让我们假设您已经完成了一个重要的数据科学项目，并且您想要为您的项目创建一个 GitHub 存储库。确保为您的存储库选择合适的标题。然后附上一个自述文件，提供项目的概要。然后，您可以上传您的项目文件，包括数据集、jupyter 笔记本和样本输出。**

**下面是一个机器学习项目的 GitHub 知识库的例子:**

****储存库名称**:bot 13956/ML _ Model _ for _ Predicting _ Ships _ Crew _ Size**

****资源库网址**:[https://github . com/bot 13956/ML _ Model _ for _ Predicting _ Ships _ Crew _ Size](https://github.com/bot13956/ML_Model_for_Predicting_Ships_Crew_Size)**

****自述文件:****

```
**ML_Model_for_Predicting_Ships_Crew_Size**Author: Benjamin O. TayoDate: 4/8/2019We build a simple model using the cruise_ship_info.csv data set for predicting a ship's crew size. This project is organized as follows: (a) data proprocessing and variable selection; (b) basic regression model; (c) hyper-parameters tuning; and (d) techniques for dimensionality reduction.**cruise_ship_info.csv**: dataset used for model building.**Ship_Crew_Size_ML_Model.ipynb**: the jupyter notebook containing code.
```

**一个组织良好的 GitHub 组合是非常重要的，因为它可以让你快速找到重要的资源，尤其是当你必须使用现有的代码和资源来解决新问题的时候。**

## **四。使用介质**

**[Medium](https://medium.com/) 现在被认为是投资组合构建和网络发展最快的平台之一。在一个媒介中，人们可以找到大量关于不同主题的教育资源，如数据可视化、机器学习、深度学习、人工智能等。大多数与数据科学相关的文章都是教程，提供逐步指导，并包含各种数据科学主题的代码。使用搜索工具，您可以发现无限量的资源，这些资源可以用作构建和开发您自己的代码的基础。在某些情况下，您可以简单地从介质中复制和粘贴现有代码，然后根据解决一个新的数据科学项目来修改代码。**

**如果你对探索 Medium 上的大量教育资源感兴趣，你必须创建一个[会员账户](https://medium.com/membership)。会员账户需要 5 美元或 50 美元/年的月订阅费。一些专注于数据科学和机器学习的顶级媒体出版物包括:**

**[走向数据科学](https://towardsdatascience.com/)**

**[走向艾](https://towardsai.net/)**

**[数据驱动型投资者](https://medium.com/datadriveninvestor)**

**[分析 Vidhya](https://medium.com/analytics-vidhya)**

## **动词 （verb 的缩写）总结和结论**

**总之，我们已经讨论了一种为名为 ***复制粘贴编程*** 的数据科学项目开发代码的新方法。复制粘贴编程允许您利用 GitHub 存储库或媒体上大量教育资源中的现有代码，而不是花费大量时间为您的数据科学代码开发新代码。**

# **其他数据科学/机器学习资源**

**[数据科学最低要求:开始从事数据科学工作需要知道的 10 项基本技能](https://towardsdatascience.com/data-science-minimum-10-essential-skills-you-need-to-know-to-start-doing-data-science-e5a5a9be5991)**

**[数据科学课程](https://medium.com/towards-artificial-intelligence/data-science-curriculum-bf3bb6805576)**

**[机器学习的基本数学技能](https://medium.com/towards-artificial-intelligence/4-math-skills-for-machine-learning-12bfbc959c92)**

**[进入数据科学的 5 个最佳学位](https://towardsdatascience.com/5-best-degrees-for-getting-into-data-science-c3eb067883b1)**

**[数据科学的理论基础——我应该关心还是仅仅关注实践技能？](https://towardsdatascience.com/theoretical-foundations-of-data-science-should-i-care-or-simply-focus-on-hands-on-skills-c53fb0caba66)**

**[机器学习项目规划](https://towardsdatascience.com/machine-learning-project-planning-71bdb3a44349)**

**[如何组织你的数据科学项目](https://towardsdatascience.com/how-to-organize-your-data-science-project-dd6599cf000a)**

**[大型数据科学项目的生产力工具](https://medium.com/towards-artificial-intelligence/productivity-tools-for-large-scale-data-science-projects-64810dfbb971)**

**[数据科学作品集比简历更有价值](https://towardsdatascience.com/a-data-science-portfolio-is-more-valuable-than-a-resume-2d031d6ce518)**

*****如有疑问，请发邮件给我***:benjaminobi@gmail.com**