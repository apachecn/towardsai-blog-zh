# 分析 SAS 中的非正态数据-日志数据、死亡率、产仔数和偏好得分。

> 原文：<https://pub.towardsai.net/using-proc-glimmix-in-sas-examples-ef311aa08717?source=collection_archive---------2----------------------->

本文是展示 PROC GLIMMIX 潜力的系列文章中的最后一篇，它是使用广义线性混合模型的实际工具。在[的介绍文章](https://medium.com/@marc.jacobs012/generalized-linear-mixed-models-in-sas-distributions-link-functions-scales-overdisperion-and-4b1c767bb89a)和展示了使用[多项式](https://medium.com/@marc.jacobs012/analyzing-ordinal-data-in-sas-fe9d9d35a449)、[二元、二项式、贝塔](https://medium.com/@marc.jacobs012/analyzing-ordinal-data-in-sas-using-the-binary-binomial-and-beta-distribution-8efe5fe5af66)、[泊松和负二项式](https://medium.com/@marc.jacobs012/analyzing-ordinal-data-in-sas-poisson-and-negative-binomial-distribution-5f46b039aaeb)的例子之后，现在是时候深入分析动物科学中经常遇到的情况了。更准确地说，我将展示细菌计数、产仔数、死亡率和偏好数的例子。尽情享受吧！

F 首先，细菌计数以及如何在对数标度上分析数据。分布如此之广以至于需要使用对数标度进行分析的数据在 GLIMMIX 模型中建模会非常困难，尤其是在使用对数函数时。稍后我会告诉你我的意思。

下面你可以看到在[随机完全区组设计](https://medium.com/@marc.jacobs012/building-and-optimizing-randomized-complete-block-designs-using-sas-c973d127d862)中两个点——第五个点和第十五个点——的肠道数据。

![](img/0d53a54aee6457184423bb4b98185f97.png)![](img/9b3e3cd437a7214c70d0f3450c8d54ac.png)

原始刻度(左)和对数刻度(右)上的肠道数据。

下面你可以看到使用的数据集。这是一个嵌套设计，包含跨部门、块和笔的数据。

![](img/9c44ac9d0e5ae271d97150538f609dec.png)

大肠杆菌、肠杆菌、梭状芽孢杆菌和乳酸杆菌的数值都非常大，这表明需要对数标度。如何应用对数标度取决于您(数据与模型)。

![](img/4287a583b5290ba89637ac618df6e209.png)

幻灯片输出显示了对四种结果及其比率进行建模时所做的选择。尤其是那些利率可能很难管理。

![](img/5a76fa923ab305421ecd529c5a6127cf.png)

细菌计数—乳/乳球菌。这个比率可以使用 PROC MIXED 进行分析，并且非常好地遵循正态分布。即使有两个额外的随机成分(方差和非结构化)，数据运行也非常平稳。结果是可信的。

![](img/a75a3fdddb2e21e876e4f8241d83eae9.png)

每次治疗和每天的费用估算

![](img/0fcfe9de133fab050dce08626f99c89f.png)![](img/69537ed9999d4398668261bebda5a9f0.png)

跨天比较。

上面看起来很简单。当你分析大肠杆菌/肠道病毒比率时，就会唱出另一首歌。下面两条简单的曲线很容易表明，你正在处理一个在空间边界运动的速率。

![](img/64b9dc55badb295c8d01f52b86169319.png)![](img/7560d5544a58b04f0694ec31c28649cc.png)![](img/a2bc98488d3456341044e21d80f483d3.png)![](img/937adf58e278b89650abf8f263dc4d31.png)

贝塔分布不知道如何处理它。至少，你期望 Beta 更趋向于正态分布，尽管它有 0 和 1 的正态极限。

![](img/59f8a8573b1596fd7f3c086e3fbee29b.png)![](img/d32489e1181167aaba3e1c9e227460c1.png)

负二项式并不比贝塔做得更好。

这个例子的问题不在于分布，而在于数据。数据设置的方式产生了一个奇怪的比率，这是大多数已知分布无法模拟的。当然，可以使用混合分布，但是改变速率会怎么样呢？

所以，这就是我所做的。我用原始数据而不是对数标度改变了速率。如果你画出这个比率，它看起来更正常。因此，负二项式对其建模没有任何问题。

![](img/a7c33ddf9a845f35f533add4badd084a.png)![](img/912da11572cb5778799d57bc9db9029a.png)![](img/eeaab0993492640cda92270514d1b308.png)

以不同的方式设置比率，即使用原始分数而不是经过对数变换的分数。

![](img/4c9ff1c56fc42f0b9af238fdc6173fed.png)![](img/c6c64a7512dd1bc04e02f84afc26fd6f.png)![](img/676b9d80b7c1c0c36c2145996093c892.png)

从协方差估计可以看出，负二项式现在可以更好地模拟数据。这是因为我在模型中对原始速率应用了对数转换。然而，缺少标准误差仍然是一个问题。现在，我们把它留下。

![](img/ae2023ce95237beba9b6ef681b613a27.png)![](img/057b1a161ef799bb28d7f53b0aca8195.png)

比较均值和 ls 均值。我觉得可以接受。

![](img/c37bd7f1e471bc46b9275fc6ef3e7ab4.png)![](img/11f0b6cacc57d4925885a25c520d4c36.png)

比较处理-对数转换分数

总之，我展示了对四个不同变量的对数分析，然后我们将其合并为两个新变量:

1.  大肠杆菌和肠杆菌科的比例
2.  梭菌和乳酸杆菌的比率

可以像 **PROC Mixed 中的 FCR 一样分析乳酸杆菌/梭菌的比例。**log(大肠杆菌)/ log(肠杆菌科)的比率提出了更难克服的问题——分布难以建模。最好使用大肠杆菌/肠杆菌科作为原始变量，并使用**负二项分布**在模型中应用**对数变换**

下面进行生命和死胎的分析。在之前的帖子中，我已经向你展示了如何[使用 Beta-Binomial 来模拟这些结果的样本大小](https://medium.com/@marc.jacobs012/sample-size-calculation-using-the-beta-binomial-distribution-7adca91035a9)。在这里，我将向您展示负二项分布的可用性。

数据集看起来像这样，其中有出生总数、活产、死产和木乃伊的列。我们有每个 sow 和每个周期的数据。

![](img/1b0cf5d599dc86e04edf947d3994ac19.png)

TG =总产，LG =活产，DG =死产，MM =木乃伊

![](img/4f9d9361144098d658ae1d4507656615.png)![](img/5e03d37d8c04d5ebb1face3089d58248.png)![](img/418513fb627dbaaa5890e8cdf1c0e331.png)

以及它们各自的分布。死产显然看起来像泊松分布，而总产和活产看起来像正态分布。

![](img/f79607bd3f620ca91354ac4b34f8124e.png)![](img/ad0f0cd1d91af77b8f1fd1279c4dc062.png)

总出生分布。正态分布看起来很适合，但是数据是离散的

![](img/364463adf245a8f6fa9967d015b77c7c.png)![](img/1d7f0450b1b75a1a5b0d71496a4bdabc.png)

生命出生分布。正态分布看起来很适合，但是数据是离散的

让我们使用 **PROC MIXED** 和 **PROC GLIMMIX** 来分析数据。

![](img/341c17c54ec0f96b87d3df63606843e8.png)![](img/89602c72179549e0e9e6be790ed1c7bb.png)

使用总出生/生命出生的正态分布。看起来非常适合，但对离散数据应用连续分布也非常奇怪。

![](img/e5ad6e76e257c87bdaa6b6b1ed6b7687.png)![](img/1057c8a857c4517f6f66059fb79c6b7a.png)

如果包括治疗呢？现在，它看起来好多了，但不要让情节愚弄你。它仍然是离散数据，对离散数据应用连续分布通常意味着模型会低估标准误差。

![](img/8ce271a52e1fd4177286524885cbeece.png)

一次处理(3)如何平均产出 15 头小猪和 1/3 头小猪？

对离散数据使用连续分布的问题是，结果将呈现在连续体**上，这将导致估计小猪**的部分。

![](img/9d54b7441cd3aed4cc87f5299b3d948b.png)![](img/adf5c81a59c359f680c61f88ad1fd01f.png)![](img/ad2e1b48bcbc215055950eb5d90620d1.png)

活着出生，使用正态分布。

![](img/5a5c2757dd41094c14833c512f21214f.png)![](img/4067e72c4ecab78c38abb6e445f91331.png)![](img/c664f6930ef6cace6e532c4df2917ad5.png)

生命出生的正态分布与负二项分布。你不能比较 AIC 分数，因为链接函数是不一样的。然而，当使用离散数据时，我会选择负二项式而不是正态分布。除非，也许，如果你包括[一个三明治估计](https://www.stat.berkeley.edu/~census/mlesan.pdf)。

下面，您将看到通过正态分布和负二项分布提供的估计值。当然，正常在这里毫无意义。

![](img/452f5d6d123ae3f8b7e24a10e88ac120.png)![](img/88f93a688b56846be15cbc12a31462de.png)![](img/a3eae2d5dd73dceededa69a1df9c3b50.png)![](img/db4182cc3b00470a489e7c15304fdbd7.png)

LB 的正态与负二项分布。对于负二项式，结果将是预测的比例，您必须乘以总数才能得到预测的整数。

![](img/9653dc5eefd6b6c58011a63d309aadac.png)![](img/45c5c191fd498b4fc1fb0063bd4098fc.png)

差异没有数据尺度。你需要回到优势比

因此，以正确的方式分析总的、静止的和生命的出生并不容易，尽管它看起来很容易。总出生数和活产数似乎遵循正态分布，但不能如此分析——如何解释 1/5 仔猪的治疗增益？

因此，对于总出生和生命出生，一个**负二项式**模型将在处理方差对均值的偏斜度时，以离散方式(计数)保存数据。结果将是预测的比例，你必须乘以总数才能得到预测的整数。使用负二项式模型将**通过使用正确的模型增加 LS 均值和 LS 差异的标准误差**。

**让我们**继续研究变异极低的数据，如死亡率或足垫损伤。动物科学中的死亡率数据通常很难建模，因为它们在规模的下限运行——幸运的是。

在处理比例时，当值完全或准完全分离时，您可能会遇到问题。一个例子是，当你有极端的类别，其中治疗 1 显示 99%的“是”，而治疗 2 显示 99%的“否”。这样一来，治疗就完全把分数分开了。

这在二元/二项式数据中比较常见:

1.  在给定水平的 Trt 因子中，响应变量的每个值都是 0 →概率(成功| Trt) = 0%
2.  在给定水平的 Trt 因子中，响应变量的每个值都是 1 →概率(成功| Trt) = 100%

模型将无法收敛→如果收敛，则估计不可信，推断无效。而且，最大似然估计会趋于无穷大。

下面是一个 2*2 的表格，显示了两组的两个结果。可以通过比值比、相对风险、绝对风险和风险差异来比较这些组。

![](img/32e27c2bd848a53afaf6fc9eeea89f3b.png)

死亡率得分的直接分析。有时候，一个模型并不需要更多。

要使用 2*2 表分析死亡率数据，我们需要转换数据。

![](img/72a9eba45e380d7756cd55db38b637f6.png)![](img/00f177eddcf0fd666061b9f54f342fe6.png)![](img/da7d096a38c41909262cc72a19c872a4.png)

从原始形式到摘要数据适合使用 **PROC FREQ** 进行分析。

![](img/8a665e79228bb1368f48dbc44abb2b89.png)![](img/d28852b4be8e36e2fb4249a1f53264bb.png)![](img/bd72398985a83493caa49023b4b31d15.png)

在这里，我要求的是优势比，相对风险，风险差异，以及确切的测试。我想看看统计数据会有多大帮助。然而，通过看这个图，我已经知道统计数据在这里毫无用处。

![](img/ec88b67d5febe1c707a46004d0f39e70.png)![](img/d482f251646304fb22f63cf870b355ed.png)

使用 **PROC GLIMMIX** 分析死亡率作为事件数据。

![](img/141429165b7cb89e77dc143f0bd304e4.png)![](img/acde2d19e33b33a66625f0412494e8c3.png)

以及 LSMEANS 和 differences。这就是边界测试的样子。

![](img/7be36bfc3884a6336c5383ac1d15ccc1.png)![](img/44f72f8314219a4b8901d01930b18dab.png)

我也在不同的数据集里加入了日期。

![](img/54dafa92fea0e71e0f8bfe738734b684.png)![](img/292eafacd0a8ec4b2bc7e89a4af15733.png)

足垫损伤的β模型。从失败的评估中可以看出，没有收敛。

![](img/2bc602e4e7bff402f01aab602642044c.png)

以及它未能传达的明确信息。

![](img/748eb0f300b0dc88d3dcdf6019e430ac.png)![](img/519cf8fc5088d1b3e1e933a434ef6314.png)

不同的数据不同的分析。我正在用科克伦-曼特尔-海恩斯泽尔统计来观察一天的影响，这种统计着眼于变化。不重要。看一看情节就会发现同样的情况。

![](img/91b31976bf7497edc1d18189796699e1.png)![](img/9443bac939c7768d610ccaab1061733d.png)![](img/f4c02a7989e67994ed6f099f6587b4c7.png)

Footpad —显示 CMH 统计数据的列联表。左边你可以看到这些情节。

![](img/d91fbe455e8c90b79640fc5d8a9bb5f2.png)![](img/0f97ec3a1caad4d114e6cd9e35ef12d5.png)

和 **PROC GLIMMIX** 分析。查看总数，您已经可以看到，您再次在边界处进行测试。

![](img/de649e3b6de712f8332ad22684cc2af0.png)

使用带有二项式分布的 GLIMMIX 模型，其值位于空间边界，这是一个非常好的不收敛真正无用的估计值的方法。

让我们看看是否可以使用另一个数据集使用 Beta 分布来模拟死亡率数据。

![](img/a8f45284095015a81d891720c659f19b.png)![](img/26bbc085c344c4463a5330d84fd8019c.png)![](img/b1e8ee721fca31fc2d6ca372d5859a7b.png)

创建不为 0 或 1 的新变量，因为 Beta 分布不允许值为 0 或 1。这里，你可以看到 35 天的总死亡率。尽管一种处理显示出非常奇怪的行为，但传播足以开始建模。

![](img/7a725ebaf22032d53e50a6cc6b173bd1.png)![](img/6f95fd8c62d5445783dd3b7f13f1714f.png)

这个模型并不完美，但是可以接受。

![](img/7c2d5c9e7b6ff73f86dc5090fbff5dac.png)

平均值以比例显示，因此*100 将给出死亡率的%。

让我们看看是否可以分析每周的死亡率数据。

![](img/fc7a6a06617e49d6b69b5adfc2758c9b.png)![](img/1aca86cca57210cb7f8bdc40e069d10a.png)![](img/9c9638314efb232dcf15f5d9fd0a095c.png)![](img/0ff9a6617640c4a43c602306df6e88ef.png)![](img/7a70ff332fcf7336ffaf4706d4cdea43.png)

肉鸡死亡率——使用贝塔分布按时间建模。我们再一次在空间的边界建模。

总之，死亡率和足垫损伤的数据因没有足够的变化来分析而臭名昭著。这是因为没有动物死亡，结果是每只围栏中的每只动物都得到了相同的分数。因此，在某些情况下，最好只使用列联表来分析事件。此外，创建二元类并按比例分析它们有助于获得一个模型，从中可以做出推断。然而，当确实没有足够的变化时，最好只报告观察到的事件数量。没有统计！

最后，但同样重要的是，让我们深入研究偏好。偏好研究分析起来很有趣，因为它们测量动物吃的食物量，并通过治疗来分割。因此，你会得到每只动物的进食量，这个量可以通过把它们可以选择的饲料数量加起来作为一个整体来总结。更具体地说，如果你看下面的数据集，你可以看到吃的总量是一个复制的数字，每行的摄入比例是实际感兴趣的数字。然而，由于我们只有两种治疗方法，我们面对的是一个零和游戏。如果你知道第一次治疗吃了多少，你也知道其他的。

![](img/0104ec8fd01f79c08d58c1aadb860157.png)

相互依赖的数据。

如你所见，每周&每只动物，两种产品的总饲料摄入量被测量。该实验的设计及其数据的聚集使得数据是相关的:

1.  总数= 842
2.  IB = 642
3.  所以肯定有 200

![](img/cd440d3636d3189ce3220cb4d2732753.png)![](img/0555330a3249123514d04ebc7d893e29.png)

在这里，你可以看到一段时间内的意大利面图形式的数据。

![](img/9b594f74ffaf95c11f315d4e965953a5.png)

和箱线图形式的数据。

![](img/c3f9820c0641fe2d0714b92e5804e179.png)![](img/ade5d9f818715a4f9a9a882cda607dce.png)

和使用贝塔分布的分析。分析这类数据的诀窍在于使用协方差结构中的组函数。这样，我要求模型建立两个协方差结构，它们是镜像。这样，我就可以估算出完整的数据集，尽管这是一个零和游戏。

随机周 *type=un group=type* 意味着我为 IB 和 SB 组指定了一个单独的非结构化协方差矩阵。由于数据是互斥的，这非常有意义，并且允许您使用所有的数据。

![](img/81d21b6f54a8f194793b0b6305775fea.png)![](img/a794d2640df6dc76b12e73d6b6396abe.png)

这里你可以看到我是如何使用 **group=** 函数模拟协方差结构的。

![](img/cbd0a6dcdb90a3a560d429f4942c39bd.png)![](img/02bffc5b54c43c31c48bdc0803479f74.png)

和观察值的比较。

总之，偏好数据根据定义是依赖数据。如果你知道 A 量吃，你也知道 B，如果你有两个治疗。因此，它们就像虚拟变量一样工作。这种依赖需要包含在混合模型中才能运行— *随机周/剩余 subject = animal NR type = un group = type。*该语句实际上会对数据进行双重分析，因此您必须将原始数据的结果与 LSMEANS 进行比较，以确保您没有出错。由于数据的相关性，很容易出错

这篇文章标志着 PROC GLIMMIX 系列的结束。下面你可以找到最后一个提示表，它显示了每个特定发行版的需求！

![](img/dbc0eded9d6233e8b9c72d75d771c9f7.png)