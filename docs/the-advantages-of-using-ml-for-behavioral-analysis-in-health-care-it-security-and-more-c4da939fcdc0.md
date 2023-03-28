# 在医疗保健、IT 安全等领域使用 ML 进行行为分析的优势

> 原文：<https://pub.towardsai.net/the-advantages-of-using-ml-for-behavioral-analysis-in-health-care-it-security-and-more-c4da939fcdc0?source=collection_archive---------2----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)

在 2019 年，Yan 等人发表了一项[研究](https://www.emerald.com/insight/content/doi/10.1108/AAOUJ-08-2019-0029/full/html)，探索机器学习分析在线学习行为预测学生表现的适用性。

作者认为，由于最近学习相关数据的激增，进行这种研究的时机已经成熟。数据增长的部分原因是由于 [MOOC](https://www.mooc.org/) 和类似平台的流行(事实上，由于疫情而增加的[在线学习的受欢迎程度](https://www.cnbc.com/2021/03/26/online-learning-boomed-during-the-pandemic-but-soon-students-return-to-school.html)无疑将推动这方面的进一步研究)。

研究作者通过人工神经网络(ANN)运行了从在线学习平台的 192 名学生记录中收集的数据。作者包括数据点，如学生年龄、性别、连接时间、点击数和访问天数。由此，研究人员接下来能够通过分析学生的在线行为来帮助教师粗略预测表现，发现访问天数与学生表现最相关。

![](img/29103ad7c553cf86dcde273c0a9f9f7a.png)

尽管使用了相对较小的数据集——作者自己将其描述为“有限的”——他们也可以基于这种行为分析为教师提供现实世界的建议。“如果老师发现一些学生的访问天数和点击数远低于学习平台上的平均数字，”他们写道，“他或她可以适当关注他们，并给予他们有效的学习支持，以防止他们考试不及格。”

上述实验只是机器学习(ML)和其他形式的人工智能(AI)如何分析和帮助解决我们生活中各方面问题的又一个例子。从市政当局使用 ML 模型设计更智能的城市，到医疗保健专业人员分析大数据以个性化医疗，到研究人员使用自然语言处理发现新药，ML 突然无处不在。

其中一个领域是行为分析(甚至是通过这种分析的行为修正)。但是在我们探索 ML 如何实现这一点之前，首先有必要看一下什么是行为。

## 行为到底是什么？

[行为](https://en.wikipedia.org/wiki/Behavior)是动物和人类关于他们的环境和他们自己的一系列行为或习惯——无论是工作面试前紧张出汗，还是受到惊吓后跳起来。行为也适用于系统和人工网络。行为可以是自愿的，也可以是不自愿的(进一步说，可以是有意识的，也可以是潜意识的)，本质上是有机体对任何数量刺激的反应。

因为行为[由](http://www.sdp.org/publications/papers/WhatIsBehavior.pdf)组成，“生物体的任何可观察到的明显运动，通常包括言语行为和身体运动”，它本质上是一种可观察到的身体活动。

## ML 如何分析(甚至帮助修改)行为？

[机器学习](https://en.wikipedia.org/wiki/Machine_learning)涉及行为相关数据的自动分析——在大多数情况下，使用传统方法分析太多或太复杂的数据——并采取多种形式，包括监督学习、非监督学习和强化学习。ML 模型从数据中学习(并从使用相关数据集的[训练](https://www.capestart.com/solutions/big-datasets-for-machine-learning/)中提高其有效性)。一旦训练到足够的水平，它就能发现模式或自主做出决定——通常具有与人类相当的准确度。

行为经济学和消费者心理学研究员 Ahmad Tanehkar [引用](https://towardsdatascience.com/lets-apply-machine-learning-in-behavioral-economics-eb952d0f2300)丹尼尔·卡内曼的话说，“我们(人类)是模式寻求者”，同样的事情也适用于 ML 模型。ML 模型自动识别数据中的模式，然后使用这些模式来预测未来的行动或行为。

特定用例的 ML 模型使用各种数据集类型进行训练，包括健康数据、金融数据、社交媒体数据或由物联网(IoT)设备和其他传感器捕获的数据。

## 传感器对行为分析的重要性

总部位于挪威的 SINTEF 数字公司的研究员 Enrique Garcia-Ceja 说,[对于观察和分析生物体(如人或动物)的物理行为的人工智能模型来说，它们需要合适的工具。人类和动物有他们的感官来为他们做这件事。缺少眼睛、耳朵和鼻子的机器学习模型必须依赖人工传感器，如麦克风、热和 RGB 相机、温度传感器、视觉和成像传感器或振动传感器。](https://enriquegit.github.io/behavior-free/intro.html)

对 ML 的研究人员来说幸运的是，传感器技术的进步带来了各种配备传感器的可穿戴技术。智能手表和健身追踪器就是一个例子，但柔性和混合电子产品的发展也导致了各种其他类型的可穿戴设备，包括生命体征测量衬衫和自加热智能 T2 夹克。

所有这些类型的产品都是用于行为分析的 ML 模型的新耳目。

## ML 在行为分析中的应用

我们在这篇博客中谈到了使用 ML 来分析在线学习数据并从中得出结论，但这并不是通过 ML 模型改进的唯一行为分析应用程序。

***医疗保健、身体健康和个性化医疗***

我们前面提到的可穿戴技术每天都被个人用来分析他们的行为——如果有必要，做出改变以有益于他们的健康。Handel 等人[表示](https://eml.berkeley.edu/~bhandel/wp/Wearables.pdf)可穿戴设备——包括从[智能健身追踪器](https://mixpanel.com/blog/fitbit-machine-learning/)，到配备传感器的[瑜伽裤](https://money.cnn.com/2017/06/09/technology/gadgets/nadix-wearable-yoga-pants/index.html)，再到[智能头盔](https://www.sciencedirect.com/science/article/pii/S016502702100008X)——可以被个人用来“了解并制定个人计划来改变他们的健康行为(例如，锻炼、饮食、睡眠)。”

反过来，将 AI 和 ML 算法应用于可穿戴设备数据，可以提供实时见解，以理解所有这些数据，并帮助改善用户的健康和体能。

ML 在[医疗保健方面](https://emerj.com/ai-sector-overviews/machine-learning-in-pharma-medicine/)提供了类似的行为分析优势。医疗保健专业人员越来越依赖医疗级可穿戴设备[,如心电监护仪、血压监护仪和生物传感器——所有这些设备都有助于从业人员远程监控患者健康并建立基线，这是新冠肺炎疫情期间的一大亮点。](https://www.businessinsider.com/wearable-technology-healthcare-medical-devices)

医疗保健应用还包括个性化医疗中的 ML 算法，使用预测分析根据患者的独特数据设计超精细的治疗方案。该领域的大多数 ML 模型都涉及监督学习，可用于治疗特别有害的行为，如成瘾，或[监测](https://somatix.com/covid-19/)新冠肺炎患者机器学习基线中潜在的威胁生命的状况变化。

***IT 安全***

ML 还可以对组织的企业系统中潜在的[内部威胁](https://itsecuritycentral.teramind.co/2019/11/01/using-machine-learning-for-behavioral-analysis-to-detect-insider-threats/)(员工、承包商或第三方供应商之间)的行为分析产生重大影响。内部威胁尤其阴险，因为使用传统的安全措施(如防火墙和入侵检测)很难检测到它们。这是零信任架构兴起的原因，通过将[ML 模型应用于组织的安全态势，零信任架构的有效性得到了指数级的帮助。](https://www.forbes.com/sites/louiscolumbus/2018/05/11/three-ways-machine-learning-is-revolutionizing-zero-trust-security/?sh=4112860781ed)

事实上，随着内部威胁[的增长，通过用户活动监控(UAM)、用户/实体行为分析(UEBA)、数据丢失预防(DLP)和其他技术来监控用户活动以识别行为异常已经变得越来越常见。这些技术是非常必要的，因为随着企业内数据量的增长，涉及的规模非常大。“即使你知道要寻找什么，从大量的活动中发现异常行为，然后将这些点连接起来以形成完整的画面，这对于人类来说可能是不可能的，”](https://securityboulevard.com/2021/01/insider-threats-are-on-the-rise-and-growing-more-costly-you-need-the-right-tools-to-detect-them/)[IT 安全中心的](https://itsecuritycentral.teramind.co/2019/11/01/using-machine-learning-for-behavioral-analysis-to-detect-insider-threats/) *，*说，“特别是如果你有一个大的用户群。”

***行为经济学***

ML 模型也有助于理解经济领域的行为科学。我们之前提到的丹尼尔·卡内曼和理查德·塞勒等研究人员已经表明，理解一个人决策过程的背景可以帮助模型理解人类的动机。人工智能模型可以使用分析来学习员工的行为，并发送技术诱导的“轻推”，这本质上是旨在激励个人取得更好绩效的及时刺激——一种被称为“人工智能辅助轻推管理”的应用[。](https://behavioralscientist.org/scaling-nudges-machine-learning/)

“机器学习和行为经济学之间的互动可能是互利的，”[写道](https://towardsdatascience.com/lets-apply-machine-learning-in-behavioral-economics-eb952d0f2300)前面提到的行为经济学研究员 Tanehkar。“一方面，ML 可用于挖掘大量数据，并找到促成不同行为出现的行为类型变量。另一方面，嵌入用于识别偏差和错误假设的 ML 算法将达到更高的性能。”

## CapeStart 如何提供帮助

[CapeStart](https://www.capestart.com/) 提供数据注释服务、预训练数据集、预构建的 ML 模型和 AI/ML 模型开发，用于各种行业和应用的行为分析，包括医疗保健、IT 安全、金融和法律。我们由数据科学家和 ML 工程师组成的综合团队每天都与大型组织合作，改进和微调 MLl 建模和有效性，为我们的客户提高效率和取得更好的业务成果。