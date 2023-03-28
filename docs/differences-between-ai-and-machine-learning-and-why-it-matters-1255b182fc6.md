# 机器学习(ML)与人工智能(AI)——关键区别

> 原文：<https://pub.towardsai.net/differences-between-ai-and-machine-learning-and-why-it-matters-1255b182fc6?source=collection_archive---------0----------------------->

![](img/7495f3dbb7ed160495e5c0cd57cc777b.png)

机器学习开放许可—图片鸣谢:[物联网世界今日](https://www.iotworldtoday.com)

## [人工智能](https://towardsai.net/p/category/artificial-intelligence)，[机器学习](https://towardsai.net/p/category/machine-learning)

## 不幸的是，一些科技组织正在欺骗客户，他们声称将在他们的技术上使用机器学习(ML)和人工智能(AI)，而不清楚他们产品的限制。

2018 年 10 月 15 日，作者[罗伯托·伊里翁多](https://mktg.best/vguzs) —最后更新:2021 年 10 月 31 日

[](https://sponsors.towardsai.net/) [## 帮助将人工智能和技术初创公司扩展到企业|走向人工智能

### 《走向人工智能》每月通过我们的定制软件为数百万科技读者提供服务。我们拥有成千上万的人工智能和…

sponsors.towardsai.net](https://sponsors.towardsai.net/) 

最近，发布了一份关于声称在其产品和服务中使用人工智能的公司滥用人工智能的报告。据[the Verge](https://www.theverge.com)[[29](https://www.theverge.com/2019/3/5/18251326/ai-startups-europe-fake-40-percent-mmc-report)]报道，声称使用 AI 的欧洲创业公司中，有 40%并没有使用该技术。去年， [TechTalks](https://bdtechtalks.com) 也偶然发现了一些公司的这种滥用，这些公司声称使用机器学习和先进的人工智能来收集和检查数以千计的用户数据，以增强用户对他们产品和服务的体验。

不幸的是，关于什么是真正的人工智能，什么是机器学习，公众和媒体仍然很混乱[[44](https://www.theguardian.com/technology/2018/jul/25/ai-artificial-intelligence-social-media-bots-wrong)]。这些术语经常被用作同义词。在其他情况下，这些被用作离散、平行的进步，而其他人则利用这一趋势来制造宣传和刺激，以增加销售和收入[[2](https://bdtechtalks.com/2018/10/08/artificial-intelligence-vs-machine-learning/)][[31](https://www.businesswire.com/news/home/20190129005560/en/Top-Sales-Marketing-Priorities-2019-AI-Big)][[32](https://www.forbes.com/sites/jonmarkman/2019/02/26/artificial-intelligence-beats-the-hype-with-stunning-growth/#2741e2d51f15)][[45](https://ixtenso.com/technology/retailers-moved-from-ai-hype-to-reality-in-2018.html)]。

> 📚查看我们对[最佳机器学习书籍](https://towardsai.net/p/machine-learning/best-machine-learning-books-free-and-paid-ml-book-recommendations-40c9ab30b0c)的编辑推荐。📚

下面我们来看看人工智能和机器学习之间的一些主要区别。

# 什么是机器学习？

![](img/2679ef7061021bf1bc5431697be5a3ce.png)

什么是机器学习|汤姆·m·米切尔，机器学习，麦格劳·希尔，1997 [ [18](http://www.cs.cmu.edu/afs/cs.cmu.edu/user/mitchell/ftp/mlbook.html) ]

引用 CMU 计算机科学学院临时院长、卡耐基梅隆大学机器学习系教授兼前系主任 Tom M. Mitchell 的话[:](http://www.cs.cmu.edu/~tom/)

> 一个科学领域最好由它所研究的中心问题来定义。机器学习领域试图回答这个问题:
> 
> “我们怎样才能建立能够随着经验自动改进的计算机系统，支配所有学习过程的基本法则是什么？[ [1](http://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf) ]"

[机器学习](https://mld.ai/mldcmu) (ML)是人工智能的一个分支，正如计算机科学家和机器学习先驱[[19](https://www.nae.edu/30398.aspx)Tom m . Mitchell 所定义的:“**机器学习是研究计算机算法，让计算机程序通过经验自动改进。**"[[18](http://www.cs.cmu.edu/afs/cs.cmu.edu/user/mitchell/ftp/mlbook.html)——ML 是我们期望实现 AI 的方式之一。机器学习依赖于通过检查和比较数据来处理从小到大的数据集，以找到共同的模式并探索细微差别。

[](https://contribute.towardsai.net/) [## 为迈向人工智能做出贡献

### 感谢您对发布《走向人工智能》感兴趣。请填写以下表格，我们会尽快回复…

contribute.towardsai.net](https://contribute.towardsai.net/) 

例如，如果你为一个机器学习模型提供许多你喜欢的歌曲，以及它们相应的音频统计数据(舞蹈能力、工具性、节奏或流派)。然后，它应该能够自动化(取决于所使用的监督机器学习模型)并生成一个推荐系统[ [43](https://en.wikipedia.org/wiki/Recommender_system) ]，以便向你推荐你将来会喜欢的音乐(有很高的概率)，就像网飞、Spotify 和其他公司所做的那样[[20](https://towardsdatascience.com/spotifys-this-is-playlists-the-ultimate-song-analysis-for-50-mainstream-artists-c569e41f8118)][[21](https://en.wikipedia.org/wiki/Recommender_system)][[22](https://medium.com/the-graph/how-recommender-systems-make-their-suggestions-da6658029b76)]。

举个简单的例子，如果你加载一个机器学习程序，它有一个相当大的 x 射线照片数据集以及它们的描述(症状、要考虑的项目等)，它应该有能力在以后帮助(或者自动化)x 射线照片的数据分析。机器学习模型查看不同数据集中的每张图片，并找到在带有可比较指示的标签的图片中找到的共同模式。此外，(假设我们对图像使用可接受的 ML 算法)，当您用新图片加载模型时，它会将其参数与之前收集的示例进行比较，以揭示图片包含之前分析过的任何指示的可能性。

![](img/a26c8d2158903a368a789906c37cc581.png)

监督学习(分类/回归)|非监督学习(聚类)|学分:西部数据[【13】](https://blog.westerndigital.com/machine-learning-pipeline-object-storage/)

我们之前的例子中的机器学习类型，称为“**监督学习**”，监督学习算法试图对目标预测输出和输入特征之间的关系和依赖关系进行建模，以便我们可以根据这些关系预测新数据的输出值，这些关系是从以前的数据集[【15】](https://medium.com/datadriveninvestor/the-50-best-public-datasets-for-machine-learning-d80e9f030279)中学习的。

**无监督学习**，另一种类型的机器学习，是机器学习算法家族，主要用于模式检测和描述性建模。这些算法在数据上没有输出类别或标签(模型使用未标记的数据进行训练)。

![](img/6673baafb62bc05c194ebc4850eac85b.png)

强化学习|学分:[你应该知道的 ML 算法类型作者:David Fumo【3】](https://towardsdatascience.com/types-of-machine-learning-algorithms-you-should-know-953a08248861)

**强化学习**，第三种流行的机器学习类型，旨在使用从与其环境的交互中收集的观察结果来采取行动，以最大化回报或最小化风险。在这种情况下，强化学习算法(称为代理)使用迭代不断地从其环境中学习。强化学习的一个很好的例子就是计算机达到了超人的状态，在电脑游戏上打败了人类[【3】](https://openai.com/five/)。

机器学习可能会令人眼花缭乱，尤其是它的高级子分支，即深度学习和各种类型的神经网络。无论如何，它是“神奇的”(计算学习理论)[【16】](http://www.learningtheory.org/)，不管公众是否有时在观察其内部工作时有问题。虽然有些人倾向于将深度学习和神经网络与人类大脑的工作方式进行比较，但这两者之间有着本质的区别[[2](https://bdtechtalks.com/2018/10/08/artificial-intelligence-vs-machine-learning/)][【4】](https://www.quora.com/What-is-the-difference-between-Neural-Networks-and-Deep-Learning)[[46](https://www.imaginea.com/sites/deep-learning-human-brain-inspiration-not-imitation/)]。

# 什么是人工智能(AI)？

![](img/ded1c4966ec7421b146c876d3014091a.png)

人工智能堆栈，由卡内基梅隆大学计算机科学学院教授兼院长安德鲁·摩尔解释| Youtube[【14】](https://youtu.be/r-zXI-DltT8)

另一方面，人工智能的范围很广。卡耐基梅隆大学计算机科学学院前院长安德鲁·摩尔(Andrew Moore)说:“人工智能是一门科学和工程，它让计算机以我们认为需要人类智能的方式运行，直到最近。”

这是用一句话来定义人工智能的好方法；然而，它仍然显示了这个领域是多么广阔和模糊。五十年前，国际象棋程序被认为是人工智能的一种形式，因为博弈论和游戏策略是只有人脑才能完成的能力。如今，国际象棋游戏已经变得无趣和过时，因为它是几乎每台电脑操作系统的一部分。所以“直到最近”是随时间而进步的东西[ [36](https://www.youtube.com/watch?v=HH-FPH0vpVE) ]。

CMU 大学助理教授兼研究员扎卡里·利普顿(Zachary Lipton)澄清了大约正确的说法[【7】](http://approximatelycorrect.com/2018/06/05/ai-ml-ai-swirling-nomenclature-slurried-thought/)，人工智能这个术语“是有抱负的，是一个基于人类拥有而机器没有的能力的移动目标。”人工智能还包括我们所知道的相当多的技术进步。机器学习只是其中之一。人工智能以前的工作利用了不同的技术。例如，1997 年击败世界国际象棋冠军的人工智能“深蓝”使用了一种叫做“树搜索算法”[【8】](http://how2examples.com/artificial-intelligence/tree-search)的方法来评估每一轮的数百万步棋[2](https://bdtechtalks.com/2018/10/08/artificial-intelligence-vs-machine-learning/)[37](https://pdfs.semanticscholar.org/211d/7268093b4dfce8201e8da321201c6cd349ef.pdf)[52](https://www.nytimes.com/2017/10/22/technology/artificial-intelligence-experts-salaries.html)[53](http://stanford.edu/~cpiech/cs221/apps/deepBlue.html)。

![](img/1915173594d8df360ace2bd0bf5c117e.png)

[使用深度优先搜索解决八皇后难题的示例|人工智能简介|。how 2 示例](http://how2examples.com/artificial-intelligence/tree-search)

正如我们今天所知，人工智能的象征是 Google Home、Siri 和 Alexa 的人机交互小工具，以及支持网飞、亚马逊和 YouTube 的机器学习视频预测系统。这些技术进步逐渐成为我们日常生活中必不可少的东西。他们是聪明的助手，增强了我们作为人类和专业人士的能力——让我们更有效率。

与机器学习相反，AI 是一个移动的目标[ [51](https://www.nytimes.com/2017/10/22/technology/artificial-intelligence-experts-salaries.html) ]，随着其相关技术进步的进一步发展，其定义也随之变化[【7】](http://approximatelycorrect.com/2018/06/05/ai-ml-ai-swirling-nomenclature-slurried-thought/)。可能，在几十年内，今天的创新人工智能进步应该被认为是乏味的，就像翻盖手机现在对我们来说一样。

# 为什么科技公司倾向于交替使用 AI 和 ML？

![](img/f89962b13e05d6d03416fcbf67b898b1.png)

“…我们想要的是一台能够从经验中学习的机器。”~艾伦·图灵

“人工智能”这个术语是在 1956 年由一群研究人员创造的，其中包括艾伦·纽厄尔和司马贺。此后，艾所在的行业经历了多次波动。在最初的几十年里，围绕这个行业有很多炒作，许多科学家一致认为人类级别的人工智能指日可待。然而，未交付的断言导致了公众对该行业的普遍觉醒，并导致了人工智能的冬天，这一时期对该领域的资金和兴趣大幅下降[[2](https://bdtechtalks.com/2018/10/08/artificial-intelligence-vs-machine-learning/)[[38](https://pha.berkeley.edu/2018/12/01/is-winter-coming-artificial-intelligence-in-healthcare/)][[39](https://en.wikipedia.org/wiki/AI_winter)][[48](https://www.actuaries.digital/2018/09/05/history-of-ai-winters/)]。

后来，一些组织试图将自己与人工智能这个术语区分开来，人工智能已经成为未经证实的炒作的同义词，并使用不同的名称来指代他们的工作。例如，IBM 将深蓝描述为一台超级计算机，并明确表示它没有使用人工智能[【10】](https://www.aaai.org/Papers/Workshops/1997/WS-97-04/WS97-04-001.pdf)，而它使用了[ [23](https://pdf.sciencedirectassets.com/271585/1-s2.0-S0004370200X00847/1-s2.0-S0004370201001291/main.pdf?x-amz-security-token=AgoJb3JpZ2luX2VjELP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJIMEYCIQDjIMRRlF2Bg0%2FbXb2EuHf1uPveE7JXPGvgiF8jy9v1pgIhAI8%2F7rm5Fduk3s%2FwFcVIzNZ2XlrsnMDuFVegomU%2FlAIwKtoDCHsQAhoMMDU5MDAzNTQ2ODY1IgxBjbK0o0E%2BZAf%2FIBcqtwMYutwXd4VWV3vhNw7bjj%2B6%2FTgAUuDmVO%2BjdJO4DTX4lgr7BsV%2BPlwWHw8Fg0lSjWblQvF9pkHUxpDcviPKFpnLCa%2BK0Q%2FHmVxyJtyMuQhOzyKn47clMW410GwMFgqemOFNqqB%2FbyQhcsJKtzAs%2BSu9Qpcq%2BvcF%2FIB%2FrEgPcbCxZ9alqrr59CTVx%2Bgcvg%2FUgXiwTTU%2BniZyXIYI7w093%2FwuaAZiN14e5wDiiuJJn53WNNb9xjNaBTRw5NqEOwsRP9lyPJyKlBMD%2BpwPAtrWSfYHsaR32efxiZoPh%2BsTQV6Rp%2Fgus8WfTHAo8Ps5vbEcnFXyYaCQS5hQtne53W8%2BTM1QbdEPLnC2SWh%2Bnbe%2FDBUc8uzvh2efc4daxUnxUJnuBp0LDPrkbCIoDqoVg4gvdZHl8Phbi9kKDRR6%2FzeQx2JybPlSRDN0OXoso5KFA2Wy1zskQYnSitJyt2Qnyj9pf3PHGEpbE1Kxwi2EYy0dyOXgucQ6gxst1BD4sxcBqmL%2Fqvh5sXqo8TCdF9etAWGfmXtKIle78Ydj76H08hooLHaGMSsiQUdwOlIHKPufDWezEC4z302EGoVCMITiuOUFOrMBD4NvZT2jbWJVbp6R57pHefR%2Fgxq8WSD83yQE3tdOq%2FKpD2FycKfw4efHjgMA5erHLJPEMP%2FRLXXZXNKyvszdZYK%2BLQH%2FKJfG37qnMwhDUDqDJZyj5B1EWrmrVdQaBseoLzmRgiKZ8JYUfYdGZ3oNrLZC2dTVbGOMhWQs7s6PnHiNzeYaTzGjU%2BkKzqlodPh7FqhQl93elTBm0GiL8tYSzp%2B05AlO%2Bz%2B43bPQhWkMsnQYjuc%3D&AWSAccessKeyId=ASIAQ3PHCVTYQ3OLEJVC&Expires=1554924164&Signature=hgxYChbxK6csUJxhR2mhaVFuF%2Bc%3D&hash=cf558464aa73462a97282dcc3bb0d452ea06e874cf5a74df43072e76f9ead2f9&host=68042c943591013ac2b2430a89b270f6af2c76d8dfd086a07176afe7c76c2c61&pii=S0004370201001291&tid=spdf-3b77c30a-7c01-4278-b018-904f0d0dd14f&sid=878a392e5f5cc946869a7813eb9cff35c2e4gxrqa&type=client) 。

在此期间，各种其他术语，如大数据、预测分析和机器学习，开始获得关注和流行[ [40](https://www.forbes.com/sites/gilpress/2013/05/28/a-very-short-history-of-data-science/#3c828f2055cf) ]。2012 年，机器学习、深度学习和神经网络取得了巨大进步，并在越来越多的领域得到了应用。组织突然开始使用“机器学习”和“深度学习”等术语来宣传他们的产品。

深度学习开始执行经典的基于规则的编程不可能完成的任务。处于早期阶段的语音和人脸识别、图像分类和自然语言处理等领域突然取得了巨大的飞跃[[2](https://bdtechtalks.com/2018/10/08/artificial-intelligence-vs-machine-learning/)][[24](https://www.infoworld.com/article/3017250/4-great-leaps-machine-learning-made-in-2015.html)][[49](https://arxiv.org/pdf/1807.08169.pdf)]，2019 年 3 月，三位最受认可的深度学习先驱获得了图灵奖，这要归功于他们的贡献和突破，这些贡献和突破使深度神经网络成为了当今计算的关键组成部分[ [42](https://amturing.acm.org/byyear.cfm) 。

因此，对于动量，我们看到一个变速杆回到人工智能。对于那些习惯了老式软件限制的人来说，深度学习的效果几乎看起来像是“魔术”[【16】](http://www.learningtheory.org/)。尤其是因为神经网络和深度学习正在进入的领域中有一小部分被认为是计算机的禁区，而如今，机器学习和深度学习工程师正在赚取高水平的薪水，即使他们在非营利组织工作，这也说明了该领域有多热。

![](img/0f63322520fc8ef4312d78a09b8eb907.png)

来源:[推特](https://twitter.com/ai_memes) | [GPT-2 更好的语言模型及其含义，](https://openai.com/blog/better-language-models/)开放 AI

可悲的是，这是媒体公司经常在没有深刻审查的情况下报道的事情，并经常与人工智能文章一起使用水晶球和其他超自然描绘的图片。这种欺骗帮助这些公司围绕他们的产品大肆宣传。然而，随着时间的推移，由于无法满足预期，这些组织被迫雇用人类来弥补他们所谓的人工智能[【12】](https://www.theguardian.com/technology/2018/jul/06/artificial-intelligence-ai-humans-bots-tech-companies)。最终，为了短期利益，他们可能会导致该领域的不信任，引发另一个人工智能冬天[ [2](https://bdtechtalks.com/2018/10/08/artificial-intelligence-vs-machine-learning/) ] [ [28](http://jeffreybigham.com/blog/2019/the-coming-ai-autumnn.html) ]。

> 我总是乐于接受反馈，如果你看到一些可能需要重新审视的东西，请在评论中分享。感谢您的阅读！

## 致谢:

作者非常感谢软件工程师和技术博客作者 Ben Dickson，感谢他的好意，允许我依靠他的专业知识和故事，以及 AI 社区的几个成员，感谢他们在准备本文时给予的巨大支持和建设性的批评。

**免责声明:**本文表达的观点仅代表作者个人观点，不代表卡内基梅隆大学或其他(直接或间接)与作者相关的公司的观点。这些文章并不打算成为最终产品，而是当前思想的反映，是讨论和改进的催化剂。

你可以在[我的网站](https://www.robertoiriondo.com)、[中](https://medium.com/@robiriondo)、 [Instagram](https://www.instagram.com/robiriondo) 、 [Twitter](https://twitter.com/robiriondo) 、[脸书](https://www.facebook.com/robiriondo)、 [LinkedIn](https://www.linkedin.com/in/robiriondo) 上找到我。

## 资源

机器学习导论| [马特·葛姆雷](https://www.cs.cmu.edu/~mgormley/) | [计算机科学学院](https://cs.cmu.edu/)，卡耐基·梅隆大学|[http://www.cs.cmu.edu/~mgormley/courses/10601/](https://www.cs.cmu.edu/~mgormley/courses/10601/)

AI for Everyone |吴恩达| Coursera |[https://www.coursera.org/learn/ai-for-everyone](https://mktg.best/dxh4u)

机器学习课程| Google |[https://developers . Google . com/machine-Learning/crash-Course/](https://mktg.best/2rq0b)

机器学习简介| uda city |[https://www . uda city . com/course/intro-to-Machine-Learning–ud 120](https://mktg.best/udacity-school-ai)

机器学习培训|亚马逊网络服务|[https://AWS . Amazon . com/Training/Learning-paths/machine-Learning/](https://mktg.best/0hnh5)

机器学习入门| Coursera |[https://www.coursera.org/learn/machine-learning](https://mktg.best/40ebo)

## 参考资料:

[1]机器学习的学科|汤姆·米契尔|[http://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf](http://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf)

【2】为什么 AI 和机器学习的区别很重要| Ben Dickson | tech talks |[https://bdtechtalks . com/2018/10/08/artificial-intelligence-vs-machine-learning/](https://bdtechtalks.com/2018/10/08/artificial-intelligence-vs-machine-learning/)

[3]你应该知道的机器学习算法类型| David Fumo |走向数据科学|[https://towardsdatascience . com/Types-of-Machine-Learning-Algorithms-You-Should-Know-953 a 08248861](https://towardsdatascience.com/types-of-machine-learning-algorithms-you-should-know-953a08248861)

[4]观看我们的人工智能系统与五位世界顶级 Dota 2 职业选手的比赛|开放人工智能|[https://openai.com/five/](https://openai.com/five/)

[5]神经网络和深度学习的区别| Quora |[https://www . Quora . com/What-is-the-difference-between-Neural-Networks-and-Deep-Learning](https://www.quora.com/What-is-the-difference-between-Neural-Networks-and-Deep-Learning)

[6]机器学习能做什么，不能做什么| WSJ |[https://blogs . WSJ . com/CIO/2018/07/27/What-Machine-Learning-Can-and-Cannot-Do/](https://blogs.wsj.com/cio/2018/07/27/what-machine-learning-can-and-cannot-do/)

[7]卡耐基梅隆大学计算机科学学院院长谈人工智能的未来|福布斯|[https://www . Forbes . com/sites/Peter high/2017/10/30/卡耐基梅隆大学计算机科学学院院长谈人工智能的未来](https://www.forbes.com/sites/peterhigh/2017/10/30/carnegie-mellon-dean-of-computer-science-on-the-future-of-ai)

[8]从 AI 到 Ml 再到 AI:论漩涡命名法&模糊化思维|扎卡里·c·利普顿|近似正确|[http://Approximately Correct . com/2018/06/05/AI-Ml-AI-漩涡命名法-模糊化思维/](http://approximatelycorrect.com/2018/06/05/ai-ml-ai-swirling-nomenclature-slurried-thought/)

[9]树搜索算法|人工智能简介|[http://how2examples.com/artificial-intelligence/tree-search](http://how2examples.com/artificial-intelligence/tree-search)

[10]根据 1955 年以来的数据和有效措施重塑教育|卡耐基梅隆大学|[https://www.cmu.edu/simon/what-is-simon/history.html](https://www.cmu.edu/simon/what-is-simon/history.html)

【11】深蓝用 AI 吗？|理查德·e·科尔夫|加州大学|[https://www . aaai . org/Papers/workshop/1997/WS-97-04/WS97-04-001 . pdf](https://www.aaai.org/Papers/Workshops/1997/WS-97-04/WS97-04-001.pdf)

[12]人工智能:薪水飙升| Stacy Stanford |机器学习回忆录|[https://medium . com/ml memories/Artificial-Intelligence-salary-Heading-Skyward-e 41 b 2 a 7 bb a7d](https://medium.com/mlmemoirs/artificial-intelligence-salaries-heading-skyward-e41b2a7bba7d)

[13]“伪人工智能”的兴起:科技公司如何悄悄使用人类来做机器人的工作|卫报|[https://www . The Guardian . com/technology/2018/jul/06/artificial-intelligence-AI-humans-bots-tech-companies](https://www.theguardian.com/technology/2018/jul/06/artificial-intelligence-ai-humans-bots-tech-companies)

[14]使用对象存储简化机器学习管道分析| Western Digital |[https://blog . Western Digital . com/Machine-Learning-Pipeline-Object-Storage/](https://blog.westerndigital.com/machine-learning-pipeline-object-storage/)

[15]Andrew Moore 博士致开幕词|人工智能和全球安全倡议|[https://youtu.be/r-zXI-DltT8](https://youtu.be/r-zXI-DltT8)

[16]机器学习的 50 个最佳公共数据集| Stacy Stanford |[https://medium . com/datadriveninvestor/The-50-Best-Public-Datasets-for-Machine-Learning-d 80 e 9 f 030279](https://medium.com/datadriveninvestor/the-50-best-public-datasets-for-machine-learning-d80e9f030279)

[17]计算学习理论| ACL | http://www.learningtheory.org/

[18]机器学习定义|汤姆·m·米切尔|麦格劳-希尔科学/工程/数学；(1997 年 3 月 1 日)第 1 页| h[TTP://www . cs . CMU . edu/AFS/cs . CMU . edu/user/Mitchell/FTP/ml book . html](http://www.cs.cmu.edu/afs/cs.cmu.edu/user/mitchell/ftp/mlbook.html)

[19]在机器学习的方法和应用方面的开创性贡献和领导地位。汤姆·米切尔教授。[美国国家工程院](https://en.wikipedia.org/wiki/National_Academy_of_Engineering)。检索于 2011 年 10 月 2 日。

[20]推荐系统|维基百科|[https://en.wikipedia.org/wiki/Recommender_system](https://en.wikipedia.org/wiki/Recommender_system)

[21] Spotify 的“这是”播放列表:50 位主流艺术家的终极歌曲分析| James Le |[https://towardsdatascience . com/spotifys-This-Is-playlists-the-ultimate-song-analysis-for-50-mainstream-artists-c 569 e 41 f 8118](https://towardsdatascience.com/spotifys-this-is-playlists-the-ultimate-song-analysis-for-50-mainstream-artists-c569e41f8118)

[22]推荐系统如何提出建议| Bibblio |[https://medium . com/the-graph/How-recommender-systems-make-thes-suggestions-da 6658029 b 76](https://medium.com/the-graph/how-recommender-systems-make-their-suggestions-da6658029b76)

[23]深蓝|科学直接资产|[https://www . Science Direct . com/Science/article/pii/s 0004370201001291](https://www.sciencedirect.com/science/article/pii/S0004370201001291)

[24]4 great-leaps 机器学习 2015 年制造| Sergar Yegulalp |[https://www . infoworld . com/article/3017250/4-great-leaps-machine-leaps-learning-made-in-2015 . html](https://www.infoworld.com/article/3017250/4-great-leaps-machine-learning-made-in-2015.html)

[25]深度学习在人工智能研究中的局限性|罗伯特·伊里翁多|走向数据科学|[https://Towards Data Science . com/limits-of-Deep-Learning-in-AI-Research-5eed 166 a 4205](https://towardsdatascience.com/limitations-of-deep-learning-in-ai-research-5eed166a4205)

[26]欧洲 40%的“人工智能初创公司”不使用人工智能，声称报告| The Verge |[https://www . The Verge . com/2019/3/5/18251326/AI-startups-Europe-fake-40-percent-MMC-report](https://www.theverge.com/2019/3/5/18251326/ai-startups-europe-fake-40-percent-mmc-report)

[27]这款智能牙刷声称拥有自己的“嵌入式人工智能”| The Verge | h[ttps://www . The Verge . com/circuit breaker/2017/1/4/14164206/smart-brush-ara-AI-koli Bree](https://www.theverge.com/circuitbreaker/2017/1/4/14164206/smart-toothbrush-ara-ai-kolibree)

[28]即将到来的 AI 秋天| Jeffrey p . big ham |[http://Jeffrey big ham . com/blog/2019/The-Coming-AI-autumnn . html](http://jeffreybigham.com/blog/2019/the-coming-ai-autumnn.html)

[29]欧洲 40%的“人工智能初创公司”不使用人工智能，声称报告| The Verge |[https://www . The Verge . com/2019/3/5/18251326/AI-startups-Europe-fake-40-percent-MMC-report](https://www.theverge.com/2019/3/5/18251326/ai-startups-europe-fake-40-percent-mmc-report)

[30]AI 的状态:Divergence | MMC Ventures |[https://www . MMC Ventures . com/WP-content/uploads/2019/02/The-State-of-AI-2019-Divergence . pdf](https://www.mmcventures.com/wp-content/uploads/2019/02/The-State-of-AI-2019-Divergence.pdf)

[31]2019 年销售和营销的首要任务:人工智能和大数据，通过对 600 多名销售专业人士的调查揭示| Business Wire |[https://www . Business Wire . com/news/home/20190129005560/en/Top-Sales-Marketing-Priorities-2019-AI-Big](https://www.businesswire.com/news/home/20190129005560/en/Top-Sales-Marketing-Priorities-2019-AI-Big)

[32]人工智能以惊人的增长击败炒作|福布斯|[https://www . Forbes . com/sites/Jon markman/2019/02/26/人工智能以惊人的增长击败炒作/#4e8507391f15](https://www.forbes.com/sites/jonmarkman/2019/02/26/artificial-intelligence-beats-the-hype-with-stunning-growth/#4e8507391f15)

[33]滥用人工智能会破坏客户忠诚度:以下是如何正确处理的方法|比较云|[https://www . Compare Cloud . net/articles/Misuse-of-AI-can-destroy-customer-loyalty-heres-how-to-get-it-right/](https://www.comparethecloud.net/articles/misuse-of-ai-can-destroy-customer-loyalty-heres-how-to-get-it-right/)

[34]人工智能时间轴|维基百科|[https://en . Wikipedia . org/wiki/Timeline _ of _ Artificial _ Intelligence # 20 世纪 50 年代](https://en.wikipedia.org/wiki/Timeline_of_artificial_intelligence#1950s)

[35]电脑象棋|维基百科| https://en.wikipedia.org/wiki/Computer_chess

[36]卡内基梅隆大学人工智能|卡内基梅隆大学机器学习系|[https://www.youtube.com/watch?v=HH-FPH0vpVE](https://www.youtube.com/watch?v=HH-FPH0vpVE)

[37]深蓝|语义学者|[https://pdfs . Semantic Scholar . org/211d/7268093 B4 dfce 8201 E8 da 321201 C6 CD 349 ef . pdf](https://pdfs.semanticscholar.org/211d/7268093b4dfce8201e8da321201c6cd349ef.pdf)

[38]冬天来了吗？|加州大学伯克利分校|[https://PHA . Berkeley . edu/2018/12/01/is-winter-coming-artificial-intelligence-in-health care/](https://pha.berkeley.edu/2018/12/01/is-winter-coming-artificial-intelligence-in-healthcare/)

[39]艾冬天|维基百科|[https://en.wikipedia.org/wiki/AI_winter](https://en.wikipedia.org/wiki/AI_winter)

[40]数据科学简史|福布斯|[https://www . Forbes . com/sites/Gil press/2013/05/28/A-Very-Short-History-of-Data-Science/# 3c 828 f 2055 cf](https://www.forbes.com/sites/gilpress/2013/05/28/a-very-short-history-of-data-science/#3c828f2055cf)

[41]深度学习革命|维基百科|[https://en . Wikipedia . org/wiki/Deep _ Learning # Deep _ Learning _ Revolution](https://en.wikipedia.org/wiki/Deep_learning#Deep_learning_revolution)

[42]图灵奖获奖者 2018 | ACM |[https://amturing.acm.org/byyear.cfm](https://amturing.acm.org/byyear.cfm)

[43]推荐系统|维基百科|[https://en.wikipedia.org/wiki/Recommender_system](https://en.wikipedia.org/wiki/Recommender_system)

[44]话语精神错乱:媒体如何让 AI 犯下惊人的错误|卫报|[https://www . The Guardian . com/technology/2018/jul/25/AI-人工智能-社交媒体-机器人-错误](https://www.theguardian.com/technology/2018/jul/25/ai-artificial-intelligence-social-media-bots-wrong)

[45]2018 年零售商从 AI 炒作走向现实| iXtenso |[https://iXtenso . com/technology/Retailers-moved-from-AI-hype-to-reality-in-2018 . html](https://ixtenso.com/technology/retailers-moved-from-ai-hype-to-reality-in-2018.html)

[46]深度学习&人脑，灵感不模仿| Imaginea |[https://www . Imaginea . com/sites/Deep-Learning-Human-Brain-Inspiration-not-simulation/](https://www.imaginea.com/sites/deep-learning-human-brain-inspiration-not-imitation/)

[47]卡内基梅隆大学计算机科学学院院长谈人工智能的未来|福布斯|[https://www . Forbes . com/sites/Peter high/2017/10/30/卡内基梅隆大学计算机科学学院院长谈人工智能的未来/#164487aa2197](https://www.forbes.com/sites/peterhigh/2017/10/30/carnegie-mellon-dean-of-computer-science-on-the-future-of-ai/#164487aa2197)

[48]艾温特斯历史|精算师数字| [https://www .精算师. Digital/2018/09/05/History-of-AI-Winters/](https://www.actuaries.digital/2018/09/05/history-of-ai-winters/)

[49]深度学习的最新进展:概述| Arxiv |[https://arxiv.org/pdf/1807.08169.pdf](https://arxiv.org/pdf/1807.08169.pdf)

[50]科技巨头正在为稀缺的人工智能人才支付巨额薪酬|纽约时报|[https://www . nytimes . com/2017/10/22/technology/artificial-intelligence-experts-Salaries . html](https://www.nytimes.com/2017/10/22/technology/artificial-intelligence-experts-salaries.html)

[51]人工智能是一个移动的目标| answer rocket |[https://www . nytimes . com/2017/10/22/technology/Artificial-Intelligence-experts-salaries . html](https://www.nytimes.com/2017/10/22/technology/artificial-intelligence-experts-salaries.html)

[52]深蓝|语义学者|中的搜索控制方法[https://www . nytimes . com/2017/10/22/technology/artificial-intelligence-experts-salaries . html](https://www.nytimes.com/2017/10/22/technology/artificial-intelligence-experts-salaries.html)

[53]深蓝上的搜索树算法|斯坦福大学|[http://stanford.edu/~cpiech/cs221/apps/deepBlue.html](http://stanford.edu/~cpiech/cs221/apps/deepBlue.html)DDI