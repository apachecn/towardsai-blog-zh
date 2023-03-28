# 监督学习:31 个最重要的模型:5 是必须学习的

> 原文：<https://pub.towardsai.net/supervised-learning-31-of-the-most-important-models-5-are-a-must-learn-9c62444905fa?source=collection_archive---------1----------------------->

## 我概述了 31 个关键的监督学习模型，并揭示了必须学习的前 5 个模型

![](img/53a596cf7e306b4197bc66ca94fb4763.png)

由来自 Pexels 的 [Pixabay](https://www.pexels.com/@pixabay/)

# 机器学习的介绍性定义

简单来说，机器学习是计算系统通过从数据中学习来更好地做事的一种方式。更严格地说，机器学习是一个计算机科学领域，涉及创建可以从数据中学习并对数据进行预测的算法。

# 什么是监督模型？

非定量定义:监督学习是一种通过向机器展示大量例子来教授它们的方法，或者是一种给你一些例子来学习的学习类型。更专业地说，计算系统被给予一组训练数据，其包括输入数据和每个数据的正确输出。系统使用这个特定的训练数据来学习如何为新的输入数据产生正确的结果。

# 监督学习面临的三大挑战

## 简单的 3:

1.找到足够的数据来训练模型

2.确保数据的准确性和高质量

3.防止模型过度拟合，这意味着确保它不会将训练数据记忆得过于紧密，以至于不能很好地推广到新数据[37]

## 更技术性的 3:

1.数据通常是不平衡的，一类样本比另一类样本多。这对于一些假设类是平衡的学习算法来说可能是一个问题。

2.很难标记数据，因为这需要人工操作。

3.一些学习算法需要大量的数据才能很好地工作。

# 何时使用监督学习需要考虑的三种方法

1.分类:这是当计算系统被给定一组数据点时，需要学习将它们分类到不同的组中。例如，假设给某人一组不同动物的图片。在这种情况下，可以给计算系统一个用例，将它们分成不同的类别，例如两栖动物、爬行动物和哺乳动物。

2.回归:基于特定的数据点，计算系统学习预测每个数据点的连续值。例如，一个一年级学生可能会得到一组代表不同人身高的数据点；计算机系统将会根据这些信息来预测一个人的身高。

3.群集:计算系统会将数据分组到不同的群集中。例如，考虑代表不同物体颜色的数据点；计算系统需要学会将它们分成不同的颜色组。

![](img/63f2d8b3a09c4ae04781d7868ffa0828.png)

来自 Pexels 的[皮克斯贝](https://www.pexels.com/@pixabay/)

# 前 31 个监督学习模型

1.线性回归

2.逻辑回归

3.支持向量机[2]

4.决策树[3]

5.随机森林[4]

6.AdaBoost [5]

7.梯度推进[6]

8.k-最近邻[7]

9.随机梯度下降[8]

10.朴素贝叶斯[9]

11.感知器[10]

12.最近质心[10]

13.线性判别分析[11]

14.二次判别分析[12]

![](img/b34ce9093b298609d63b263ba80494a8.png)

来自 pexels 的 https://www . Pexels . com/photo/office-writing-vintage-technology-12199413/

15.手推车[13]

16.卡方自动交互检测[14]

17.隔离森林[15]

18.一级 SVM [16]

19.额外的树分类器[17][18][19]

20.特征集聚[20]

21.多项式 NB [21]

22.被动攻击性分类器[23][24]

23.伯努利 NB [1]

24.脊形分类器〔25〕

25.内核 SVM [2]

26.拉索回归[26]

27.岭回归[27]

28.弹性网络回归[28]

29.最小二乘回归[29]

30.贝叶斯岭回归[30][31][32]

31.胡伯回归量[32]

![](img/e311255b1556bd7e4d9c6bca759473a3.png)

由[米盖尔Á。来自 Pexels 的 padrián](https://www.pexels.com/@padrinan/)

# 五大必学知识的分类

由于他们的绩效结果，这些将会出现无数次，无论是在你早期的学习中，还是在你整个职业生涯中不断进步。它们是:

1.线性回归

2.支持向量机

3.逻辑回归

4.决策树

5.集成方法

线性回归是一种监督学习算法，它基于输入要素的线性组合来预测实值输出。它实现起来更简单，并且可以应用于各种各样的问题领域。例如，如果你曾经在 Zillow 上查看过房价预测，这就是一切开始的地方(通过线性回归)。

支持向量机是另一种公认的用于回归和分类任务的监督学习算法。该算法依赖于找到一个在特征空间中最大地分离数据点的超平面[2]。此外，它被设计为接收和处理噪声[2]，并可以处理非线性，使其成为机器学习任务的通用工具。

逻辑回归是一种监督学习算法，通常用于分类任务。该算法预测实例属于特定类的概率，然后可以实现该算法来预测新的实例。

决策树可用于回归和分类[39]任务。该算法从训练数据中构建一个决策规则树，然后可以用它来预测新的实例。此外，决策树更易于解释和理解，这使得它们在数据挖掘和机器学习应用中易于使用。

集成方法(如 AdaBoost [5])是监督学习算法，它将多个单独模型的预测结合起来，以产生更准确的整体预测。集合方法通常用于精确的情况，目标是在给定的任务上达到最高的可能精度。

![](img/c315afcea7b2f97fa8a52a8aeba97d4a.png)

来自 Pexels 的安吉拉·罗玛

# 逻辑回归和线性回归有什么不同？

1.线性回归用于预测连续结果，而逻辑回归用于预测二元结果[32]。

2.线性回归使用最小二乘法来优化模型，而逻辑回归使用最大似然法[35]。

3.线性回归假设预测值[38]和结果变量之间存在线性关系，而逻辑回归不做这种假设[32]。

4.线性回归不需要将数据转换成虚拟变量，而逻辑回归需要[33]。

5.线性回归会受到异常值的影响，而逻辑回归对异常值不太敏感[34]。

![](img/72cb8eed782542f07754b832f946a856.png)

来自佩克斯的安·H·T3

# 监督学习最佳实践概述

1.数据预处理:数据预处理是任何机器学习管道中的关键步骤。在将数据输入模型之前，对其进行清理和格式化是非常重要的。这包括处理缺失值、异常值和数据规范化。

2.交叉验证:这是一种用于评估机器学习模型准确性的技术。我们将数据分成两组，一组用于训练，另一组用于测试。以这种方式拆分数据有助于避免过度拟合训练数据。

3.选择正确的模型:如此处所示，有许多不同类型的监督学习模型可用。为数据选择合适的模型对于获得良好的结果至关重要。选择模型时需要考虑几个因素，例如数据类型、手头的任务和可用资源。

4.训练/测试分割:训练/测试分割是另一种用于评估机器学习模型准确性的技术。它包括将数据分成两组，在第一组上训练模型，并在第二组上测试它。这种方法有助于避免过度拟合训练数据。

5.参数调整:参数调整是机器学习中必不可少的过程；这是您调整模型的超参数以优化其性能的地方。参数调整有许多不同的方法，如网格搜索和随机搜索[35]。

6.特征工程:特征工程从现有数据创建新特征。这个过程可以通过组合现有元素、转换功能或使用领域知识创建新功能来完成。特征工程是任何机器学习管道中的功能关键步骤。

7.正则化:正则化是一种用于防止机器学习模型过度拟合的技术。它通过在损失函数中增加一个惩罚项来惩罚模型的复杂性。有许多类型的正规化，如 L1 和 L2 [36]。

8.偏差/方差权衡:偏差/方差权衡是机器学习中的一个基本概念。它是指拥有一个过于简单(高偏差)的模型和拥有一个过于复杂(高方差)的模型之间的交换。找到正确的平衡对于获得好的结果至关重要。

9.集成:集成是一种用于组合多个机器学习模型以创建单个更准确的模型的技术。这项技术可以通过在不同的数据子集上训练多个模型，然后对它们的预测进行平均，或者通过在不同版本的数据上引入多个模型来完成。

10 评估指标:选择合适的评估指标对于评估机器学习模型的性能至关重要。有许多不同的评估指标可用，如准确度、精确度、召回率和 F1 分数。

如果您有任何编辑/修改建议或关于进一步扩展此主题的建议，请考虑与我分享您的想法。

# 另外，请考虑订阅我的每周简讯:

[](https://pventures.substack.com/) [## 周日报告#1

### 设计思维与 AI 的共生关系设计思维能向 AI 揭示什么，AI 又能如何拥抱…

pventures.substack.com](https://pventures.substack.com/) 

# **我写了以下与这篇文章相关的内容；他们可能与你有相似的兴趣:**

除了这篇关于监督学习的文章，我之前提到过**半监督学习**:

[](https://medium.com/@AnilTilbe/semi-supervised-learning-guide-3-models-rise-on-top-4b03f86cdd52) [## 半监督学习指南；3 款车型拔得头筹

### 我揭示了半监督学习的挑战，最佳实践，9 项技术，16 个基本模型，以及如何 3…

medium.com](https://medium.com/@AnilTilbe/semi-supervised-learning-guide-3-models-rise-on-top-4b03f86cdd52) 

这是我关于**监督学习的帖子:**

[](/unsupervised-learning-14-of-the-most-important-algorithms-b3e9e07350c9) [## 无监督学习:14 种最重要的算法

### 14 种算法及其使用案例的细分。

pub.towardsai.net](/unsupervised-learning-14-of-the-most-important-algorithms-b3e9e07350c9) 

如果您对 **NLP 指南**感兴趣，您可以在这里找到它:

[](/16-open-source-nlp-models-for-sentiment-analysis-one-rises-on-top-b5867e247116) [## 16 个用于情感分析的开源 NLP 模型；一个在顶端升起

### 介绍 16 款车型，深入了解风格。

pub.towardsai.net](/16-open-source-nlp-models-for-sentiment-analysis-one-rises-on-top-b5867e247116) 

*参考文献:*

*1。*[*https://sci kit-learn . org/stable/modules/generated/sk learn . naive _ Bayes。BernoulliNB.html*](https://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.BernoulliNB.html)

*2。*[](https://scikit-learn.org/stable/modules/svm.html)

**3。*[*https://www . kdnuggets . com/2020/01/decision-tree-algorithm-explained . html*](https://www.kdnuggets.com/2020/01/decision-tree-algorithm-explained.html)*

**4。*[*https://www.ibm.com/cloud/learn/random-forest*](https://www.ibm.com/cloud/learn/random-forest)*

**5。*[【https://www.mygreatlearning.com/blog/adaboost-algorithm/】T21](https://www.mygreatlearning.com/blog/adaboost-algorithm/)*

**6。*[*https://machine-learning . paper space . com/wiki/gradient-boosting*](https://machine-learning.paperspace.com/wiki/gradient-boosting)*

**7。*[*https://www . codecademy . com/learn/introduction-to-supervised-learning-skill-path/modules/k-nearest-neighbors-skill-path/cheat sheet*](https://www.codecademy.com/learn/introduction-to-supervised-learning-skill-path/modules/k-nearest-neighbors-skill-path/cheatsheet)*

**8。*[*https://realpython.com/gradient-descent-algorithm-python/*](https://realpython.com/gradient-descent-algorithm-python/)*

**9。*[*https://highdemandskills.com/naive-bayes-supervised/*](https://highdemandskills.com/naive-bayes-supervised/)*

**10。*[*https://IDC 9 . github . io/stor 390/notes/classification/class ification . html*](https://idc9.github.io/stor390/notes/classification/classification.html)*

**11。*[*https://machine learning mastery . com/linear-discriminal-analysis-for-machine-learning/*](https://machinelearningmastery.com/linear-discriminant-analysis-for-machine-learning/)*

**12。*[*https://scikit-learn.org/stable/modules/lda_qda.html*](https://scikit-learn.org/stable/modules/lda_qda.html)*

*13。[*https://machine learning mastery . com/class ification-and-regression-trees-for-machine-learning/*](https://machinelearningmastery.com/classification-and-regression-trees-for-machine-learning/)*

*14。[*https://select-statistics . co . uk/blog/chaid-chi-square-automatic-interaction-detector/*](https://select-statistics.co.uk/blog/chaid-chi-square-automatic-interaction-detector/)*

**15。*[*https://sci kit-learn . org/stable/modules/generated/sk learn . ensemble . isolation forest . html*](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html)*

**16。*[*https://scikit-learn . org/stable/auto _ examples/SVM/plot _ one class . html*](https://scikit-learn.org/stable/auto_examples/svm/plot_oneclass.html)*

*17。[*https://machine learning mastery . com/extra-trees-ensemble-with-python/*](https://machinelearningmastery.com/extra-trees-ensemble-with-python/)*

*18。[*https://www . geeks forgeeks . org/ml-extra-tree-classifier-for-feature-selection/*](https://www.geeksforgeeks.org/ml-extra-tree-classifier-for-feature-selection/)*

*19。[*https://scikit-learn . org/stable/modules/generated/sk learn . ensemble . extractreesclassifier . html*](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.ExtraTreesClassifier.html)*

**20。*[*https://scikit-learn . org/stable/modules/generated/sk learn . cluster . feature agglomeration . html*](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.FeatureAgglomeration.html)*

**21。*[*https://NLP . Stanford . edu/IR-book/html/html edition/naive-Bayes-text-class ification-1 . html*](https://nlp.stanford.edu/IR-book/html/htmledition/naive-bayes-text-classification-1.html)*

**22。*[*https://arxiv.org/pdf/1904.07496.pdf*](https://arxiv.org/pdf/1904.07496.pdf)*

**23。*[*https://www . geeks forgeeks . org/passive-aggressional-classifiers/*](https://www.geeksforgeeks.org/passive-aggressive-classifiers/)*

**24。*[*https://scikit-learn . org/stable/modules/generated/sk learn . linear _ model。PassiveAggressiveClassifier.html*](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.PassiveAggressiveClassifier.html)*

*25。[*https://scikit-learn . org/stable/modules/linear _ model . html # ridge-regression-and-class ification*](https://scikit-learn.org/stable/modules/linear_model.html#ridge-regression-and-classification)*

**26。*[*https://www.youtube.com/watch?v=Y1EBH1Tv1Gw*](https://www.youtube.com/watch?v=Y1EBH1Tv1Gw)*

**27。*[*https://www . mygreatlearning . com/blog/what-is-ridge-regression/*](https://www.mygreatlearning.com/blog/what-is-ridge-regression/)*

*28。[*https://www . analyticssteps . com/blogs/linear-lasso-ridge-and-elastic-net-regression-overview*](https://www.analyticssteps.com/blogs/linear-lasso-ridge-and-elastic-net-regression-overview)*

**29。*[*https://www.edureka.co/blog/least-square-regression/*](https://www.edureka.co/blog/least-square-regression/)*

*三十。[*https://alpopkes . com/posts/machine _ learning/Bayesian _ linear _ regression/*](https://alpopkes.com/posts/machine_learning/bayesian_linear_regression/)*

**31。*[*https://stats . stack exchange . com/questions/551424/Bayesian-machine-learning-for-supervised-learning*](https://stats.stackexchange.com/questions/551424/bayesian-machine-learning-for-supervised-learning)*

**32。*[*https://scikit-learn-extra . readthedocs . io/en/stable/modules/robust . html*](https://scikit-learn-extra.readthedocs.io/en/stable/modules/robust.html)*

**33。*[*https://www . the analysis factor . com/odds-ratio-categorial-predictor/*](https://www.theanalysisfactor.com/odds-ratio-categorical-predictor/)*

**34。*[*https://stats . stack exchange . com/questions/279010/how-does-outlier-impact-logistic-regression*](https://stats.stackexchange.com/questions/279010/how-does-outlier-impact-logistic-regression)*

*35。[*https://machine learning mastery . com/hyperparameter-optimization-with-random-search-and-grid-search/*](https://machinelearningmastery.com/hyperparameter-optimization-with-random-search-and-grid-search/)*

*36。[*https://Neptune . ai/blog/fighting-over fitting-with-L1-or-L2-正则化*](https://neptune.ai/blog/fighting-overfitting-with-l1-or-l2-regularization)*

**37。什么是机器学习管道，为什么它们很重要？。*[*https://www . akkio . com/post/what-are-machine-learning-pipelines-and-why-are-they-important*](https://www.akkio.com/post/what-are-machine-learning-pipelines-and-why-are-they-important)*

**38。第四章线性回归|动手机器学习与 r .*[*https://bradleyboehmke . github . io/HOML/Linear-Regression . html*](https://bradleyboehmke.github.io/HOML/linear-regression.html)*

*39。11–8 . docx——决策树是一种什么样的树，它可以如何用于…[*https://www.coursehero.com/file/76877217/11-8docx/*](https://www.coursehero.com/file/76877217/11-8docx/)*