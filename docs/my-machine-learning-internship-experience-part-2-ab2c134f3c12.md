# 我的机器学习实习经历——第二部分

> 原文：<https://pub.towardsai.net/my-machine-learning-internship-experience-part-2-ab2c134f3c12?source=collection_archive---------3----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

## 我参与的项目，我使用的免费宝贵资源，以及我现在在做什么。如果你即将踏上机器学习之旅，请阅读这篇文章。

![](img/8030d360f508b61846e09f1108886355.png)

[夏嫣·胡伊津加](https://unsplash.com/@iam_anih?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

在我之前的帖子中，我谈到了:
[第 0 部分](https://anglinabhambra.medium.com/how-i-became-an-intern-machine-learning-engineer-b85b5649e280)——我实习前的经历。第一部分——我的第一周以及之后的一些挑战。

# TL；速度三角形定位法(dead reckoning)

*   你不需要成为任何一个主题的专家，尤其是在处理多个项目的时候。建立好的系统来填补你的知识空白。
*   这里有一个简短的总结，是我得到一个好的系统的最重要的提示:
    →每天花时间学习(查看下面的“有价值的资源”)。
    →巩固获得任何主题基本理解的方法。
    →使用可以迭代的架构图来处理项目。

# 项目📝

我主要参与了两个项目的第一阶段。一个是地平线 2020 (H2020)项目，另一个是创新英国项目。H2020 是欧盟有史以来最大的研究和创新项目。 [Innovate UK](https://www.gov.uk/government/organisations/innovate-uk/about) 隶属于英国研究与创新机构，这是一个由英国政府资助的非部门公共机构。

## H2020 —蜂鸟

《蜂鸟》(仍在进行中)的目标是更好地理解不断变化的移民流。我公司的贡献分成 4 个子产品，我团队的子产品是非洲之角的干旱绘图系统。我所做的工作和研究，促成了这个子产品的第一次迭代。

我要做的第一件事是有效地理解如何使用卫星数据来绘制特定地区的干旱地图。这是一项艰巨的任务，因为我阅读学术论文的经验非常少。令人尴尬的是，我直面自己的恐惧，寻求帮助。我的经理向我介绍了一些基础知识，然后分享了这篇[关于“你应该如何阅读研究论文”的精彩文章](https://towardsdatascience.com/how-you-should-read-research-papers-according-to-andrew-ng-stanford-deep-learning-lectures-98ecbd3ccfb3)。

我的同事开始构建管道来实现我们提出的一些想法，所以我尝试用 PyTests 对管道进行**测试。我肯定应该首先尝试单元测试，但是我在 Twitch 上看到了一个很棒的教程(在下面的“有价值的资源”中提到)，它以一种容易理解的方式解释了如何使用 PyTests。**

我还**使用 streamlit** 创建了一个内部应用程序，让所有团队(子产品)保持在同一页面上。我的一个同事在应用程序中添加了一个超级翔实和简洁的文献综述，这让每个人都对项目和有用的背景信息有了高层次的了解。

我还学会了如何用 [QGIS](https://qgis.org/en/site/) 、 [SNAP](https://step.esa.int/main/toolboxes/snap/) 和[气流](http://airflow.apache.org/)对卫星数据进行**标记和预处理。尽管我使用这些工具的时间有限，但接触到它们的工作感觉很棒。我还帮助我的同事录制了内部“操作”视频，以帮助我的一些同事也使用这些工具。**

## 创新英国— SBRI

简而言之，这个项目是关于铁路结构测量的自动化测量处理。要了解更多关于这个项目和 SBRI 的信息，请点击以下链接:

*   [https://www . gov . uk/government/collections/sbri-the-small-business-research-initiative](https://www.gov.uk/government/collections/sbri-the-small-business-research-initiative)
*   [网络铁路&创新英国铁路 SBRI](https://www.youtube.com/watch?v=5GUmVRWKZ2w)

在我工作的前几周，我的同事和经理写了这份提案的大部分内容。我对什么是[点云](https://info.vercator.com/blog/what-are-point-clouds-5-easy-facts-that-explain-point-clouds)只有皮毛的了解，所以当我被要求**参与提案**时，我感觉自己像个大骗子。我还被要求整理一张**高层架构图**，老实说，如果你看到我整理的东西，那会很滑稽。这绝对是我提高的一项技能。经过长时间的延迟，我们发现我们成功进入了第一阶段。

第一阶段发生在我实习的最后三个月。为了让自己更好地理解项目和数据的范围，我的经理建议我阅读这个主题并**找到开源数据集来练习**。通过参与代码评审，我也从我的同事那里学到了很多。例如，**用我自己的话重复一项任务**以确保我完全理解我应该做什么。

我**使用 streamlit** 创建了一个标签应用程序，在 ML 算法循环中支持人类反馈。我处理杂乱的点云遗留数据，我同事的代码，并将 [PyDeck](https://deckgl.readthedocs.io/en/latest/) 集成到应用程序中。使用 [streamlit gallery](https://awesome-streamlit.org/) 我也可以制作一些 HTML 和 CSS。

# 宝贵的资源📚

我最喜欢的部分！在规划你的学习路径时，很容易信息过载，或者感觉你什么也没学到，因为一种资源对你不起作用。下面列出的 MOOCs、YouTube 频道、Twitch 频道和 Meetup 群组是最适合我的，也是我仍在继续使用的。

**慕课。我可以推荐 3 门对我最有帮助的 MOOCS。**

1.  哥白尼是欧盟的地球观测项目，提供从卫星数据中提取的信息服务。
2.  Jovian.ai 的 toGANS 这无疑是我遇到的最好的深度学习入门课程。实际上，实习结束后，我又重新上了这门课。
3.  [Fast.ai](http://fast.ai) 。我学习了网络抓取，甚至还建造了一个[图像分类器](https://github.com/AnglinaBhambra/fastai-v3/blob/master/lesson1-hw/lesson1-hw-birdclassifier.ipynb)。虽然 [fast.ai](http://fast.ai) 欢迎初学者，但 0toGANS 对我来说是更好的入门资源。

**YOUTUBE** 。我可以推荐更多的频道，但我会坚持我在实习期间看得最多的 3 个。

1.  [Abhishek tha kur](https://www.youtube.com/c/AbhishekThakurAbhi/featured)——我发现 Abhishek 的 [*在完成 0toGANS 后，使用 PyTorch*](https://www.youtube.com/watch?v=u1loyDCoGbE) 视频从零开始实现原始 U-Net。
2.  [Ken Jee](https://www.youtube.com/channel/UCiT9RITQ9PW6BhXK0y2jaeg) - Ken 的视频教会了我很多关于数据可以带来的商业价值。他有关于他如何通过 Kaggle 和许多 [*简历评论视频*](https://www.youtube.com/watch?v=QBIe4nbmZfA&list=PL2zq7klxX5ARdms3L99sE8DTEsJ4_jCHP&index=23) 学习的视频。肯还发起了一个数据挑战，你可以在任何社交媒体平台上分享你的进步。
3.  丹尼尔·伯克(Daniel Bourke)—丹尼尔给数据带来了如此多的惊喜！我最喜欢的系列是 [*复制 Airbnb 的舒适度检测*](https://www.youtube.com/watch?v=C_lIenSJb3c&list=PL6vjgQ2-qJFeMrZ0sBjmnUBZNX9xaqKuM) 和 [*机器学习月刊*](https://www.youtube.com/watch?v=DBbBRwpneLs&list=PL6vjgQ2-qJFdEjZjYFrwVZYlroGs5trip) 。

**抽动**。我没想到我会使用 Twitch，尤其是当我已经对自己策划的内容饮食感到满意(可能有点超载)的时候。话虽如此，当你找到一个制作高质量内容和易于跟随的教程的频道时，把它们记下来总是好的，所以我可以推荐→ [*卓氏抽动流*](https://www.twitch.tv/cheukting_ho) 。我最喜欢的是 *Python 零到英雄*和*数据的传说*系列。

**聚会**。这些对保持现状和结识与你有相似兴趣的人很有帮助。你也可能有机会发表演讲。我选择参加的聚会通常以 Python 或数据科学为主题，并混合了讲座和教程。一些寻找聚会和活动的好地方是 meetup.com 和 eventbrite.co.uk。

![](img/ba6cbbb7ca6d5109f40168deb82ec6d9.png)

照片由[蒂姆·莫斯霍尔德](https://unsplash.com/@timmossholder?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

不用说，每天学习很重要。当每个人都在疫情开始时被送回家，我开始了**# 100 daysofcode**[Twitter 挑战](https://twitter.com/_AnglinaB/status/1242181828120907784)。这对我非常有帮助，因为它给了我责任感。在社交媒体上宣布我正在学习的东西迫使我组织我的学习，并推动我完成我开始的事情。

# 我现在在做什么👩🏽‍⚕️

完成这次实习为我打开了许多大门。我现在在[铁路银行](https://www.railsbank.com/)担任**数据分析师**，并将于今年 9 月开始在**兼职攻读数据科学硕士**。我还开始了与一个很棒的人合作的项目，他是我通过推特认识的。正如我的经理几次提到的**为开源项目做贡献**，我通过 [PyLadies Meetup Group](https://www.meetup.com/PyLadiesLondon/) 找到了做这件事的绝佳机会，并且已经能够为 [Pandas](https://pandas.pydata.org/docs/) 做贡献。

# 结论

我要感谢 GMV·NSL 对我的欢迎。我的实习是我有幸遇到的最艰难的学习经历之一。挺俗气的，但是这次旅程教会了我一切皆有可能。我从最少的 python 经验到做机器学习和软件工程，使用地理空间数据和点云数据。

我希望这一系列的帖子能鼓励你找到最适合你的学习途径，在这里我推荐的一些资源会有用。记住，外面有那么多资源，它们都不会引起你的共鸣，所以不要气馁，继续尝试。如果可以的话，每天花一点时间学习。

# 我希望这篇文章对你有用。

要联系我或找到更多类似本文的内容，请执行以下操作:

1.  跟我上 [**中**](https://anglinabhambra.medium.com/)
2.  在 [**LinkedIn**](https://www.linkedin.com/in/anglina-bhambra/) 和 [**Twitter**](https://twitter.com/_AnglinaB) 上连接并联系我
3.  通过我的 [**博客**](https://anglinabhambra.github.io/) 继续我的旅程

[](https://anglinabhambra.medium.com/how-i-became-an-intern-machine-learning-engineer-b85b5649e280) [## 我如何成为一名实习机器学习工程师

### 这篇文章概述了我是如何转行的，以及我的入门之旅。我学的是机械工程…

anglinabhambra.medium.com](https://anglinabhambra.medium.com/how-i-became-an-intern-machine-learning-engineer-b85b5649e280) [](/my-machine-learning-internship-experience-part-1-c6597fccbce6) [## 我的机器学习实习经历——第一部分

### 去年这个时候，我的机器学习实习已经进行了几个月。我讲述了我在…之前的经历

pub.towardsai.net](/my-machine-learning-internship-experience-part-1-c6597fccbce6)