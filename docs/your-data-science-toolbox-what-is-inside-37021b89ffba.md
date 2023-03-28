# 您的数据科学工具箱—里面有什么？

> 原文：<https://pub.towardsai.net/your-data-science-toolbox-what-is-inside-37021b89ffba?source=collection_archive---------0----------------------->

![](img/72265f2e83e9314fa557482ce3f0a380.png)

由[谷仓图片](https://unsplash.com/@barnimages?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

## [数据科学](https://towardsai.net/p/category/data-science)

## 作为一名数据科学家，您只能执行拥有合适工具的任务

# 一.导言

数据科学是一个非常广泛的多学科领域，包括几个细分领域，如数据可视化、机器学习和人工智能。由于该领域的广泛性，并且由于技术创新和新算法的发展，数据科学在不断变化，因此一名成功的数据科学家必须始终保持一个庞大且最新的工具箱。请记住，作为一名数据科学家，您只能执行拥有合适工具的任务。本文将讨论可以包含在数据科学工具箱中的几种工具。

# 二。基于知识的工具

基于知识的工具可以根据所涉及的数据科学任务的级别分为三个主要类别:**级别 1** (基础级别)；**二级**(中级)；以及 l**level 3**(高级水平)。

![](img/41f77754e9c9502d7b3f3f815e5fcdfc.png)

数据科学的三个层次。Benjamin O. Tayo 的图片

## 1 基本工具

基本工具是使人能够执行 1 级任务的工具。在第一级，数据科学的追求者应该能够处理通常以逗号分隔值(CSV)文件格式呈现的数据集。他们应该掌握数据基础知识；数据可视化；和线性回归。

## 1.1 数据基础

能够操作、清理、构建、缩放和设计数据。他们应该熟练使用熊猫和 NumPy 库。应具备以下能力:

*   知道如何导入和导出以 CSV 文件格式存储的数据
*   能够清理、辩论和组织数据，以便进一步分析或建模
*   能够处理数据集中缺失的值
*   理解并能够应用数据插补技术，如均值或中位数插补
*   能够处理分类数据
*   知道如何将数据集划分为训练集和测试集
*   能够使用标准化和规范化等缩放技术缩放数据
*   能够通过主成分分析(PC)等降维技术压缩数据

## 1.2 数据可视化

能够理解良好的数据可视化的基本组成部分。能够使用包括 Python 的 matplotlib 和 seaborn 包在内的数据可视化工具；以及 R 的 ggplot2 包。应该了解良好的数据可视化的基本组件:

*   **数据成分**:决定如何可视化数据的第一个重要步骤是了解数据的类型，如分类数据、离散数据、连续数据、时间序列数据等。
*   **几何组件:**您可以在这里决定哪种可视化适合您的数据，例如散点图、线形图、条形图、直方图、Q-Q 图、平滑密度、箱线图、配对图、热图等。
*   **映射组件:**在这里，你需要决定用什么变量作为你的 *x 变量*，用什么作为你的 *y 变量*。这一点非常重要，尤其是当数据集是包含多个要素的多维数据集时。
*   **秤组件:**在这里，您可以决定使用哪种秤，例如线性秤、对数秤等。
*   **标签组件:**包括轴标签、标题、图例、使用的字体大小等。
*   **道德成分**:在这里，你要确保你的可视化讲述真实的故事。在清理、汇总、操作和生成数据可视化时，您需要意识到您的行为，并确保您没有使用您的可视化来误导或操纵您的受众。

## 1.3 监督学习(预测连续目标变量)

熟悉线性回归和其他高级回归方法。能够熟练使用 scikit-learn 和 caret 等软件包进行线性回归建模。具备以下能力:

*   能够使用 NumPy 或 Pylab 进行简单的回归分析
*   能够使用 scikit-learn 进行多元回归分析
*   了解正则化回归方法，如套索法、岭法和弹性网法
*   了解其他非参数回归方法，如 KNeighbors 回归(KNR)和支持向量回归(SVR)
*   了解评估回归模型的各种指标，如 MSE(均方误差)、MAE(平均绝对误差)和 R2 分数
*   能够比较不同的回归模型

## 2 个中间工具

除了基本工具箱中的技能和能力外，还应具备以下能力:

## 2.1 监督学习(预测连续目标变量)

熟悉二进制分类算法，例如:

*   感知器分类器
*   逻辑回归分类器
*   支持向量机(SVM)
*   能够使用核 SVM 解决非线性分类问题
*   决策树分类器
*   k-最近分类器
*   朴素贝叶斯分类器
*   了解评估分类算法质量的几个指标，如准确度、精密度、灵敏度、特异性、召回率、f-l 分数、混淆矩阵、ROC 曲线。
*   能够使用 scikit-learn 建立模型

## 2.2 模型评估和超参数调整

*   能够在一个管道中结合变压器和估值器
*   能够使用 k-fold 交叉验证来评估模型性能
*   知道如何用学习和验证曲线调试分类算法
*   能够通过学习曲线诊断偏差和方差问题
*   能够解决验证曲线的过度拟合和欠拟合问题
*   知道如何通过网格搜索微调机器学习模型
*   了解如何通过网格搜索调整超参数
*   能够阅读和解释混淆矩阵
*   能够绘制和解释受试者工作特性(ROC)曲线

## 2.3 结合不同模型进行集成学习

*   能够使用不同分类器的集成方法
*   能够结合不同的算法进行分类
*   知道如何评估和调整集成分类器

## 3.高级工具

能够处理高级数据集，如文本、图像、语音和视频。除基本技能和中级技能外，还应具备以下能力:

*   聚类算法(无监督学习)
*   k 均值
*   深度学习
*   神经网络
*   克拉斯
*   张量流
*   Theano
*   云系统(AWS、Azure)

# 三。生产力工具

这些工具将帮助您处理大规模数据科学项目，并帮助您将模型部署到生产级别。他们还将帮助您展示您的数据科学技能，并与其他数据科学专业人士建立联系。

## 1.大型项目的工具

在现实世界的数据科学项目中，数据集可能非常复杂，要执行的任务可能涉及计算密集型问题，例如图像处理、语音分析，或者使用具有数百个特征和数千个观察值的复杂数据集构建深度学习模型。这类问题需要先进的生产力工具。

## 1.1.高性能计算

高度密集的数据科学项目可以使用高性能计算(HPC)设施来执行。HPC 是包含多个节点的计算机集群。HPC 可以串行或并行模式执行计算。为了使用 HPC 资源，数据科学家必须掌握以下技能:

**a)命令行或类似 UNIX 的界面(Linux)** :这是与计算机服务器交互所需要的。有几种基于 UNIX 的操作系统可用于 HPC。我最喜欢的是 [Ubuntu](https://ubuntu.com/) 。Ubuntu 提供了一个类似 windows 的 UNIX 系统，非常容易使用，特别是对于不熟悉命令行的个人。

下面给出了 HPC 所必需的一些基本 UNIX 命令:

```
**# make a new director**
$ mkdir**# what is my current directory**
$ pwd**# change director**
$ cd**# lists your files in current working directory**
$ ls**# copy file1 and save as file2**
$ cp file1 file2**# delete a file1**
$ rm file1**# search the string "r2 score" in file1**
$ grep "r2 score" file1**# launch an editor that lets you create and edit a file
$** emacs file1
```

关于基本 UNIX 命令的更多信息可以在这里找到:【http://mally.stanford.edu/~sr/computing/basic-unix.html 

**b)关于批处理调度器的知识:**这是在 HPC 集群上以非交互方式运行作业所需要的。假设我们想要在 HPC 计算机上运行一个机器学习模型，该模型允许 MPI(节点间通信)进行消息传递。假设我们模型的 python 代码存储在一个名为“ *my_script.py* 的文件中要在 HPC 集群上运行它，我们可以在与 Python 脚本相同的目录中创建以下批处理脚本，我们称之为“ *myjob.sh* ”，如下所示:

```
#!/bin/bash#SBATCH --nodes = 3#SBATCH --tasks-per-node = 32#SBATCH --time = 02:00:00#SBATCH --job-name = my_script.pymodule load pythonsrun -n 96 python my_script.py
```

为了在 HPC 上以批处理模式运行" *my_script.py* ，我们使用 sbatch 命令从命令行提交批处理脚本，并等待它运行完成:

```
% sbatch myjob.sh
```

执行作业时，会在服务器上的当前工作目录中创建一个输出文件。然后，输出文件可用于后处理和分析。一些服务器配备了软件，能够通过图形用户界面进行事后分析和结果可视化。如果这不可用，那么可以将输出文件传输到本地桌面进行后期分析。有许多软件应用程序可用于在本地目录和服务器上的目录之间传输文件。一个例子是 PuTTY，它是一个免费的开源终端仿真器、串行控制台和网络文件传输应用程序。它支持多种网络协议，包括安全拷贝(SCP)和安全外壳(SSH):[https://www.putty.org/](https://www.putty.org/)。

## 1.2.云服务

对于小公司来说，构建 HPC 计算平台可能非常昂贵。它还需要一个 HPC 技术人员团队来操作和维护该设施，并为数据科学家提供技术支持和培训。因为大多数公司无法维护这些设施，所以他们更倾向于云服务，将其作为大规模数据科学和机器学习项目的生产力工具。

在云计算领域，三大主要提供商是亚马逊、微软和 IBM。云平台提供内置算法，允许您构建、测试和部署机器学习模型。AWS 和 Azure 是最流行的构建和部署机器学习模型的云平台。数据科学家应该学会如何使用云服务。

## 2.投资组合构建工具

数据科学是一个实用的领域。实践技能非常重要，尤其是当你有兴趣作为一名实践数据科学家在学术界之外工作时。展示你已完成项目的一个方法是建立一个非常棒的作品集。有兴趣雇用你的公司肯定会向你索要投资组合，因为这证明了你在基础数据科学概念方面的优势。有几个平台可用于投资组合构建和联网，例如:

*   开源代码库
*   商务化人际关系网
*   中等
*   卡格尔

有关投资组合构建的更多信息，请参见以下文章:[数据科学投资组合比简历更有价值](https://towardsdatascience.com/a-data-science-portfolio-is-more-valuable-than-a-resume-2d031d6ce518)。

# 四。摘要

总之，我们已经讨论了在您的数据科学工具箱中需要维护的几个工具。根据您工作或预期工作的组织，您的工作角色可能不要求您使用本文中列出的所有工具。然而，要想被认为是一名成功的数据科学家，你必须时刻保持一个大而更新的工具箱。请记住，作为一名数据科学家，您只能执行拥有合适工具的任务。所以，为什么不把你所有的工具都准备好，为将来的工作角色做准备呢？

# 其他数据科学/机器学习资源

[数据科学需要多少数学知识？](https://medium.com/towards-artificial-intelligence/how-much-math-do-i-need-in-data-science-d05d83f8cb19)

[数据科学课程](https://medium.com/towards-artificial-intelligence/data-science-curriculum-bf3bb6805576)

[进入数据科学的 5 个最佳学位](https://towardsdatascience.com/5-best-degrees-for-getting-into-data-science-c3eb067883b1)

[数据科学的理论基础——我应该关心还是仅仅关注实践技能？](https://towardsdatascience.com/theoretical-foundations-of-data-science-should-i-care-or-simply-focus-on-hands-on-skills-c53fb0caba66)

[机器学习项目规划](https://towardsdatascience.com/machine-learning-project-planning-71bdb3a44349)

[如何组织你的数据科学项目](https://towardsdatascience.com/how-to-organize-your-data-science-project-dd6599cf000a)

[大型数据科学项目的生产力工具](https://medium.com/towards-artificial-intelligence/productivity-tools-for-large-scale-data-science-projects-64810dfbb971)

[数据科学作品集比简历更有价值](https://towardsdatascience.com/a-data-science-portfolio-is-more-valuable-than-a-resume-2d031d6ce518)

***如有疑问和咨询，请发邮件给我*【benjaminobi@gmail.com :**