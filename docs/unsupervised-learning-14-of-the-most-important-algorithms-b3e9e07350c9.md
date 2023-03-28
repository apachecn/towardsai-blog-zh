# 无监督学习:14 种最重要的算法

> 原文：<https://pub.towardsai.net/unsupervised-learning-14-of-the-most-important-algorithms-b3e9e07350c9?source=collection_archive---------1----------------------->

## 14 种算法及其使用案例的细分。

![](img/8447679c001c0080aeb9a3ee3d4a6a8a.png)

由 Pexels 的[this is 工程](https://www.pexels.com/@thisisengineering/)

有几种类型的无监督学习算法，下面是 14 种最重要的算法:

1.聚类算法根据相似性将数据点组合成聚类。例如，k-means 聚类是一种流行的聚类算法，它将数据划分为 k 个组。

## 2.降维算法降低了数据的维数，使其更易于可视化和处理。

例如，主成分分析(PCA)是一种将数据投影到低维空间的降维算法(PCA 可用于将数据缩减到其最重要的特征。)

3.异常检测算法识别异常值或异常数据点。支持向量机可以用于异常检测(一个例子)[26]。异常检测算法用于检测数据集中的异常值，有许多不同的异常检测方法，但大多数都可以分为有监督的和无监督的。监督方法需要有标签的数据集，而非监督方法则不需要。

# 无监督异常检测算法通常基于密度估计[20]，它们试图找到数据空间中异常密集的区域。

例如，一种简单的方法可以计算每个点到其 k 个最近邻点的平均距离。离它们的邻居非常远的点很可能是异常点。

![](img/51b531c59534ad2ebd6ee2b015fd5e8c.png)

来自 Pexels 的 Markus Spiske

存在许多其他基于密度的异常检测算法，包括局部离群因子(LOF)和支持向量数据描述(SVDD)。这些算法比简单的 k-最近邻方法更复杂，通常可以检测到更微妙的异常[21]。大多数异常检测算法都需要调整，因此您需要指定一个参数来控制算法对异常的敏感度。如果参数太低，算法可能会遗漏一些异常。如果设置得太高，该算法可能会产生假阳性(例如，它可能会将正常点识别为异常点。)

4.分割算法将数据分割成段或组[12]。例如，分割算法可以将图像分割成前景和背景。

# 这些算法可用于自动将数据集分成有意义的组，而无需人工监督。

在这个领域中，最著名的算法之一是 k-means 算法。该算法通过最小化组内距离平方和将数据点分成 k 个组。

另一种流行的分割算法是均值漂移算法。该算法的工作原理是将每个数据点向其局部邻域的中心反复移动。均值漂移对异常值相对稳健，可以处理密度不均匀的数据集。然而，在大型数据集上运行计算开销很大。最后，高斯混合模型(GMM)是可以用于分割的概率模型。GMM 传统上需要大量的计算来训练，但最近的进展使它们变得更快。GMM 非常灵活，可以用于任何类型的数据。然而，它们可能很难解释，并且不一定总能产生最佳结果。一般来说，k-means 是简单数据集的好选择，而 GMM 更适合复杂数据集。这两种情况下都可以使用均值漂移，但在大型数据集上可能计算量很大。

![](img/08020295eba1e7d3ac2fec357e34c7c3.png)

来自 Pexels 的 Kaushal Moradiya

5.去噪算法减少或消除数据中的噪声。例如，小波变换可以用于图像去噪。但是，各种来源都会产生噪声，包括数据损坏、丢失值和异常值。

# 去噪算法可以通过减少数据中的噪声量来提高无监督学习模型的准确性[10]。

有多种去噪算法可用，包括主成分分析(PCA)、独立成分分析(ICA)和非负矩阵分解(NMF) [11]。

6.链接预测算法预测数据点之间的未来连接(例如，网络中两个节点之间的未来交互)；例如，链接预测可以用来预测哪些人将成为社交网络中的朋友。更常用的链路预测算法之一是优先连接算法[15]，该算法预测两个节点如果具有许多现有连接，则更有可能被连接。

![](img/9cb88fa46938284cad845cb26ae8024c.png)

来自 Pexels 的 Pixabay

另一种流行的链路预测算法是本地路径算法，该算法预测两个节点如果共享一个共同的邻居，则它们更有可能相关联[27]。这种算法通常用于生物网络，因为它可以捕捉“结构等价”的概念[16]。

## 最后，带重启的随机行走算法是一种链路预测算法，它模拟网络上的随机行走器，并在随机节点重启行走器[17]。然后，遍历器将到达特定节点的概率被用于测量两个节点之间存在连接的可能性。

7.强化学习算法通过反复试验来学习。Q-learning 是基于值的学习算法的一个例子[1]；从我的经验来看，我发现它对于用例实现来说既简单又通用。然而，Q-learning 有时会收敛到次优解[18]。另一个例子是 TD 学习，它在计算上比 Q 学习要求更高，但通常可以找到更好的解决方案[19]。

8.生成模型:这些算法生成新的数据点，如训练数据。例如，自动编码器是生成模型，可用于从图像数据集创建独特的图像。在机器学习中，生成模型是捕获一组数据的统计属性的模型。这些模型可以用来生成新的数据，就像它们被训练的数据一样。

# 生成模型用于各种任务，如无监督学习、数据压缩和去噪[22]。

有各种各样的生成模型，如隐马尔可夫模型和玻尔兹曼机器[22]。每个模型都有其优点和缺点，适合不同的任务。例如，隐马尔可夫模型擅长对序列数据建模，而玻尔兹曼机器更擅长对高维数据建模[22]。通过在未标记的数据上训练它们，生成模型可以用于无监督学习。一旦模型经过训练，就可以用来生成新数据。然后，这种生成的数据可以由人类或另一种机器学习算法来标记。此过程可重复进行，直到创成式模型学会生成类似所需输出的数据。

![](img/ac9f51ec6488b738868898e0070c7bb1.png)

来自 Pexels 的 Oladimeji Ajegbile

# 另外:

9.提升包括使用梯度下降框架来构建数据集的梯度加权分位数草图的算法。因为它是高度可扩展和高效的，所以升压在许多情况下都是非常有效的。

10.随机森林是一种机器学习算法，用于监督和非监督学习[9]。

# 对于无监督学习，随机森林可以找到相似项目的组，识别离群值，并压缩数据[9]。

对于监督和非监督任务，随机森林已经被证明优于其他流行的机器学习算法，例如支持向量机[9]。随机森林是无监督学习的强大工具，因为它们可以处理具有许多特征的高维数据。他们也抵制过度拟合，这意味着他们可以很好地推广新数据。

## 11.DBSCAN: DBSCAN 是一种基于密度的聚类算法，可用于无监督学习。

它基于密度，即每个区域的点数。如果 DBSCAN 组距离较近，则它们会指向一起，而忽略相距较远的点。与其他聚类算法相比，DBSCAN 有几个优点。它可以发现不同大小和形状的簇，并且不需要用户预先指定簇的数量[23][28]。此外，DBSCAN 对异常值不敏感，这意味着它可以用来查找数据集的其余部分不能很好地表示的数据。然而，DBSCAN 也有一些缺点。例如，它可能很难在有大量噪声的数据集中找到聚类。此外，DBSCAN 需要一个密度阈值，这可能不适合所有数据集[23]。

![](img/6d718c8cb936891ded1dc90e581bd893.png)

来自 Pexels 的 Andrea Piacquadio

12.Apriori 算法用于发现关联、频繁项目集和序列模式[24]。

# Apriori 算法的工作原理是首先找到数据中的所有频繁项集，然后利用这些项集生成规则。

Apriori 算法有多种实现方式，可以针对不同的需求进行定制。例如，可以控制支持度和置信度阈值来找到不同类型的规则[24]。

## 13.Eclat 算法从事务数据库中挖掘频繁项集，可用于购物篮分析、入侵检测和文本挖掘[25]。

14.Bagging 是梯度推进决策树的一种实现。它使用梯度提升决策树作为构建的基础，然后将先前决策树的特征权重添加到各个决策树的加权和中。这增加了最终决策树的方差，并使其更有可能给出最优解。

如果您有任何编辑/修改建议或关于进一步扩展此主题的建议，请考虑与我分享您的想法。

# **另外，请考虑订阅我的每周简讯:**

[](https://pventures.substack.com/) [## 周日报告#1

### 设计思维与 AI 的共生关系设计思维能向 AI 揭示什么，AI 又能如何拥抱…

pventures.substack.com](https://pventures.substack.com/) 

*参考文献:*

*1。Q-Learning 入门:强化学习:*[*https://www . freecodecamp . org/news/an-introduction-to-Q-Learning-reinforcement-Learning-14 ac0 b 4493 cc/*](https://www.freecodecamp.org/news/an-introduction-to-q-learning-reinforcement-learning-14ac0b4493cc/)

*2。q-学习视频演练:*[*https://www.youtube.com/watch?v=4dcgjcuR-1o*](https://www.youtube.com/watch?v=4dcgjcuR-1o)

*3。无监督学习:用 DBSCAN 聚类:*[*https://web . cs . dal . ca/~ kall ada/stat 2450/lectures/lectures 15 . pdf*](https://web.cs.dal.ca/~kallada/stat2450/lectures/Lecture15.pdf)

*4。机器学习中的 DBSCAN 聚类算法:*[*https://www . kdnugges . com/2020/04/DBS can-clustering-algorithm-machine-learning . html*](https://www.kdnuggets.com/2020/04/dbscan-clustering-algorithm-machine-learning.html)

*5。深度生成模型中全局因素的无监督学习。arXiv:2012.08234*

*6。Harshvardhan GM，摩哂陀·库马尔·古利萨里亚，文殊莎·潘迪，西达尔特·斯瓦鲁普·劳塔雷，《机器学习中生成模型的综合调查与分析》，《计算机科学评论》，第 38 卷，2020，100285，ISSN 1574–0137，*[*https://doi.org/10.1016/j.cosrev.2020.100285.*](https://doi.org/10.1016/j.cosrev.2020.100285.)

7。助推:【https://aws.amazon.com/what-is/boosting/】[](https://aws.amazon.com/what-is/boosting/)

*8。装袋:[*https://www.ibm.com/cloud/learn/bagging*](https://www.ibm.com/cloud/learn/bagging)*

**9。Breiman，L. (2001 年)。随机森林。机器学习，45(1)，5–32 页。**

**10。Hastie，Tibshirani，r .，& Friedman，J. (2009 年)。统计学习的要素:数据挖掘、推理和预测(第二版。).施普林格科学&商业媒体。**

**11。主教，C. M. (2006 年)。模式识别和机器学习。斯普林格。**

**12。用于功能材料断层图像数据分割的机器学习技术。*[*https://www . frontier sin . org/articles/10.3389/fmats . 2019.00145/full*](https://www.frontiersin.org/articles/10.3389/fmats.2019.00145/full)*

**13。复杂网络中的链路预测:综述。*[*https://arxiv.org/pdf/1010.0725.pdf*](https://arxiv.org/pdf/1010.0725.pdf)*

**14。链接预测。*[*https://neo4j . com/developer/graph-data-science/link-prediction/*](https://neo4j.com/developer/graph-data-science/link-prediction/)*

*15。在线网络中的优先依恋:测量与解释。[](https://arxiv.org/pdf/1303.6271.pdf)*

**16。一种新的挖掘长路径网络缺失链接的相似性度量。[*https://arxiv.org/pdf/2110.05008.pdf*](https://arxiv.org/pdf/2110.05008.pdf)**

***17。重启的快速随机游走及其应用。*[*https://www . cs . CMU . edu/~ christos/PUBLICATIONS/icdm 06-rwr . pdf*](https://www.cs.cmu.edu/~christos/PUBLICATIONS/icdm06-rwr.pdf)**

***18。Q-Learning:教程和扩展。*[*https://link . springer . com/chapter/10.1007/978-1-4615-6099-9 _ 3*](https://link.springer.com/chapter/10.1007/978-1-4615-6099-9_3)**

**19。时差学习:[*https://web . Stanford . edu/group/PDP lab/pdphandbook/handbook ch 10 . html*](https://web.stanford.edu/group/pdplab/pdphandbook/handbookch10.html)**

**20。异常检测的机器学习技术:综述。[*https://www . research gate . net/profile/Salima-Benqdara/publication/325049804 _ Machine _ Learning _ Techniques _ for _ Anomaly _ Detection _ An _ Overview/links/5af 3569 b 4585157136 c 919d 8/Machine-Learning-Techniques-for-Anomaly-Detection-An-Overview . pdf*](https://www.researchgate.net/profile/Salima-Benqdara/publication/325049804_Machine_Learning_Techniques_for_Anomaly_Detection_An_Overview/links/5af3569b4585157136c919d8/Machine-Learning-Techniques-for-Anomaly-Detection-An-Overview.pdf)**

***21。网络异常检测的机器学习方法。*[*https://www . usenix . org/legacy/event/sysml 07/tech/full _ papers/Ahmed/Ahmed . pdf？ref = driver layer . com/web*](https://www.usenix.org/legacy/event/sysml07/tech/full_papers/ahmed/ahmed.pdf?ref=driverlayer.com/web)**

***22。墨菲，K. P. (2012 年)。机器学习:概率观点(第 1 版。).麻省理工出版社。***

***23。一种基于密度的大空间聚类发现算法。*[*https://www.osti.gov/biblio/421283.*](https://www.osti.gov/biblio/421283.)**

***24。拉克什、阿格拉瓦尔和拉玛克里希南·斯里坎特。"挖掘关联规则的快速算法."*[*https://www . researchgate . net/publication/2460430 _ Fast _ Algorithms _ for _ Mining _ Association _ Rules*](https://www.researchgate.net/publication/2460430_Fast_Algorithms_for_Mining_Association_Rules)**

**25。帕克尔伊克巴尔。算法、现实世界应用和研究方向。[*https://link . springer . com/article/10.1007/s 42979-021-00592-x*](https://link.springer.com/article/10.1007/s42979-021-00592-x)**

***26。使用多代理系统的异常检测。*[*https://users . encs . Concordia . ca/~ abdelw/papers/Khosravifar _ MSc _ s 2018 . pdf*](https://users.encs.concordia.ca/~abdelw/papers/Khosravifar_MSc_S2018.pdf)**

***27。用于图形生成的深度生成模型的系统调查。*[*https://deepai . org/publication/a-systematic-survey-on-deep-generated-models-for-graph-generation*](https://deepai.org/publication/a-systematic-survey-on-deep-generative-models-for-graph-generation)**

**28。分层 K 均值聚类:优化聚类。[*https://www . data novia . com/en/lessons/hierarchical-k-means-clustering-optimize-clusters/*](https://www.datanovia.com/en/lessons/hierarchical-k-means-clustering-optimize-clusters/)**