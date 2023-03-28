# 深度学习的线性代数，简单解释

> 原文：<https://pub.towardsai.net/linear-algebra-for-deep-learning-simply-explained-e279998cfad1?source=collection_archive---------5----------------------->

## 了解在深度学习中应用线性代数的 4 个原因，并了解演示应用的 4 个用例

![](img/1d9b44f7bf57ac367dc17bd2632cc9ae.png)

来自 Unsplash 的马塞尔·埃伯勒

今天的用例包含深度学习，因为它在每个行业都有无数的实现。你不会每天都听到带有深度学习的线性代数以同样的方式(围绕人工智能行业)或由团队表达的同样的句子。然而，数学被整合到几乎每一个用于输出设计的机器学习问题中。

## 线性代数是一门研究向量空间和它们之间的线性映射的数学学科[1]。

而且，

## 深度学习是应用神经网络进行数据学习的机器学习的子集。通过使用多个层，深度学习模型可以学习复杂的模式，并对新数据进行预测。

线性代数和深度学习的集成包括两种通用方法:(1)我们使用线性代数来表示和处理数据，以及(2)训练神经网络。此外，在线性代数算法的背景下，它们可以通过减少所需的训练数据量来提高训练的效率[7]，并使优化网络参数变得更容易。举个例子，线性代数如何被用来分析神经网络的输出并理解它们是如何工作的。

![](img/140e2cb9d5078c4cd5e81afd88ba4b44.png)

由[澳大利亚奥古斯特](https://unsplash.com/@austris_a)从 Unsplash

# **线性代数背景下的深度学习**

深度学习是机器学习的一个分支，它使用人工神经网络(ann)在包括分类和回归在内的建模管道领域进行预测建模。神经网络类似于生物神经系统，因为它们由通过突触交换信息的互连处理节点或神经元组成。

深度学习通过增加网络的隐藏层数，让 ann 从数据中学习复杂的模式；这使得它们比在相同数据集上训练的较浅的网络具有更大的深度。因此，深度学习可以被视为使用许多分层非线性变换从原始数据中提取更高级别表示的一种方式。

近年来深度学习的成功[8]可以归因于几个因素，包括高性能计算资源的可用性不断增加，更复杂算法的发展，以及具有许多训练示例的数据集的增加。然而，需要注意的是，并不是所有的机器学习任务都非常适合深度学习；有时更简单的方法，如逻辑回归或支持向量机可能会表现得更好。此外，尽管深度学习在某些应用中表现出了巨大的前景，但它仍然是一个活跃的研究领域，关于如何最好地设计和训练神经网络，还有许多开放的问题。

![](img/4132b5d58c264797a5364b842c0cf977.png)

来自 Unsplash 的 Veri Ivanova

# **在深度学习中应用线性代数的 4 个理由**

首先，BLUF(底线在前面):

1.线性代数可以通过减少需要优化的参数数量来帮助简化深度学习算法。

2.通过提供一种在多个内核或 GPU 之间并行化计算的方法，减少深度学习模型的培训时间。

3.在许多情况下，传授更有效的方法来表示数据，从而从基于此数据训练的深度学习模型中获得更快、更准确的预测。

4.在深度学习用例中，应用线性代数来规范[4]深度学习模型，有助于防止过度拟合并提高这些模型的泛化能力。

![](img/96da57f8e2853ba9109f2b95398320b2.png)

来自 Unsplash 的 dylan nolte

# **通过减少要优化的参数数量来简化深度学习算法。**

在许多深度学习算法中，为了达到良好的性能，需要对参数进行优化。然而，这些参数中的一些可能不是必需的，并且可以完全消除，而不会影响算法的性能。线性代数可以通过删除不需要的参数来帮助简化这些算法。

在深度学习算法线性代数经常需要的高维向量的情况下，我们可以在更低维的空间中拟合这些向量，这可以使优化过程更容易和更高效。因为许多深度学习算法对矩阵或高阶张量进行操作，所以线性代数将允许对这些对象的属性进行分析，以帮助相应地优化它们。

一些深度学习算法需要梯度下降进行优化。这种实现方法可以通过使用线性代数来直接计算梯度而不是使用诸如有限差分的数值方法来实现功效[2]。

![](img/11229da151752078791749a72a84d876.png)

来自 Unsplash 的 Siora 摄影

# **通过提供一种在多个内核或 GPU 之间并行化计算的方式，减少深度学习模型的训练时间。**

通过在几个核心或 GPU 之间分配计算，线性代数可以帮助加快训练过程。具体来说，线性代数方法可以压缩表示深度学习模型的数据矩阵，从而在训练新模型或用现有模型进行预测时，实现更快的矩阵运算和更高的性能。

机器学习(特别是神经网络)中的某些类型的正则化使用线性代数比传统方法(如梯度下降/上升)更自然地表达和求解。因此，采用线性代数技术可以提高训练机器学习模型的准确性和效率。

![](img/b1e11fe29bfedf02eead953ef9993036.png)

来自 Unsplash 的 Elena Mozhvilo

# **传授一种更有效的方式来表示数据，从而导致更快更准确的预测。**

1)线性代数可以通过数据压缩有效地优化求解[2]。例如，如果我们有一个 1000x1000 的数据集，我们希望将其压缩到 100x100，那么线性代数可以通过消除数据中的冗余来解决这个问题，从而为神经网络更快、更准确地处理压缩数据创造条件。

对于解决优化问题，如果我们想要找到使一些成本函数最小化的函数的参数，线性代数可以求解这些参数，潜在地从基于这些数据训练的深度学习模型中获得更快更准确的预测。

线性代数可以用有益的结果来指导特征工程。也就是说，如果我们有一个图像数据集，并且我们想要提取边缘或角点等特征，线性代数可以处理图像并自动提取这些特征。

文本分类或机器翻译等序列建模任务可以充分利用线性代数。在这些情况下，单词的矢量表示(称为单词嵌入)是使用来自线性代数的矩阵分解技术(例如奇异值分解[3])来学习的。这些单词嵌入可以作为深度学习模型的输入特征，与传统的单词袋方法相比，可能会产生性能更好的结果。

![](img/6d49de53a5390c6d53b5451bd75ec639.png)

由来自 Unsplash 的[克里斯·利维拉尼](https://unsplash.com/@chrisliverani)

# **深度学习的 4 个用例线性代数**

—预测建模:例如，分析和预测财务数据，以了解股票价格或住房市场趋势。

—用于图像识别，这可能是在数字图像中识别对象的过程。使用线性代数方法优化的深度学习算法可以被训练来识别图片或视频中的对象。

—对于推荐系统，这是一种人工智能技术，根据用户过去的行为向他们提供建议。网飞使用线性代数根据用户过去看过的电影来推荐电影。

—语音识别。例如，谷歌的语音搜索由深度学习算法驱动，将语音转换为文本[6]。

# **结论**

总之，线性代数是一种强大的工具，可用于深度学习来表示数据，训练神经网络，并分析这些网络的输出。虽然深度学习在某些应用方面显示出巨大的前景，但它仍然是一个充满许多开放问题的活跃研究领域。

如果您有任何编辑/修改建议或关于进一步扩展此主题的建议，请考虑与我分享您的想法。

# **另外，请考虑订阅我的每周简讯:**

[](https://pventures.substack.com/) [## 周日报告#1

### 设计思维与 AI 的共生关系设计思维能向 AI 揭示什么，AI 又能如何拥抱…

pventures.substack.com](https://pventures.substack.com/) 

# **我写了以下与这篇文章相关的内容；您可能对它们感兴趣:**

[](/16-open-source-nlp-models-for-sentiment-analysis-one-rises-on-top-b5867e247116) [## 16 个用于情感分析的开源 NLP 模型；一个在顶端升起

### 介绍 16 款车型，深入了解风格。

pub.towardsai.net](/16-open-source-nlp-models-for-sentiment-analysis-one-rises-on-top-b5867e247116) [](https://medium.com/@AnilTilbe/linear-algebra-for-ai-nlp-and-ml-use-cases-simply-explained-c0bac7159a7f) [## 人工智能的线性代数:简单解释 NLP 和 ML 用例

### 5 个 NLP 用例，5 个 ML 用例，以及在人工智能问题中应用线性代数的理由

medium.com](https://medium.com/@AnilTilbe/linear-algebra-for-ai-nlp-and-ml-use-cases-simply-explained-c0bac7159a7f) [](https://medium.com/@AnilTilbe/top-20-data-engineering-tools-and-5-stand-out-a71714b12f3c) [## 20 大数据工程工具，其中 5 款脱颖而出

### 20 大开源数据工程工具，以及 5 个脱颖而出的工具，用于在您的数据生命周期中部署…

medium.com](https://medium.com/@AnilTilbe/top-20-data-engineering-tools-and-5-stand-out-a71714b12f3c) [](/bayesian-inference-the-best-5-models-and-10-best-practices-for-machine-learning-11238a43929e) [## 贝叶斯推理:机器学习的 5 个最佳模型和 10 个最佳实践

### 将贝叶斯推理应用于机器学习问题的优势、5 大模型和 10 大最佳实践

pub.towardsai.net](/bayesian-inference-the-best-5-models-and-10-best-practices-for-machine-learning-11238a43929e) 

*参考文献。*

***1。*** *应用线性代数导论。(未注明)。检索 2022 年 7 月 21 日，来自*[*https://books.google.com/books?hl=en&# 38；lr =&# 38；id = IApaDwAAQBAJ&# 38；oi = fnd&# 38；pg = PR11&# 38；dq =线性+代数+人工+智能&# 38；ots = szo 9d 3 dwrm&# 38；SIG = qw 5 pvqjbtjf 3 tx-bYybn-dMasRw # v = one page&# 38；q =线性% 20 代数% 20 人工% 20 智能&# 38；f=false*](https://books.google.com/books?hl=en&#38;lr=&#38;id=IApaDwAAQBAJ&#38;oi=fnd&#38;pg=PR11&#38;dq=linear+algebra+artificial+intelligence&#38;ots=szO9d3dwRM&#38;sig=qw5PVQjBTJf3tx-bYybn-dMasRw#v=onepage&#38;q=linear%20algebra%20artificial%20intelligence&#38;f=false)

***2。*** *任意不规则网格下的有限差分法及其在应用力学中的应用。(未注明)。电脑&# 38；结构，11(1–2)，83–95。*[*https://doi . org/10.1016/0045-7949(80)90149-2*](https://doi.org/10.1016/0045-7949(80)90149-2)

***3。*** *(未注明)。*[*https://www . research gate . net/profile/Alexander-Gray-2/publication/228820785 _ Fast _ SVD _ for _ large-scale _ matrices/links/5739d 24 a 08 AEA 45 ee 83 f 6 fad/Fast-SVD-for-large-scale-matrices . pdf*](https://www.researchgate.net/profile/Alexander-Gray-2/publication/228820785_Fast_SVD_for_large-scale_matrices/links/5739d24a08aea45ee83f6fad/Fast-SVD-for-large-scale-matrices.pdf)

***4。*** *里夫金，&# 38；Lippert，R. A. (2007 年 5 月 1 日)。关于正则化最小二乘的注记。*[*https://dspace.mit.edu/handle/1721.1/37318*](https://dspace.mit.edu/handle/1721.1/37318)

***5。*** *矩阵，音乐，网飞推荐。伯克利讲座。*[*https://math . Berkeley . edu/~ sander/fall 2016 decal/reading 10 . pdf*](https://math.berkeley.edu/~sander/fall2016decal/reading10.pdf)

**6*。*** *老安德鲁、赵永明、杰森·韦斯顿。学习改进的线性变换用于语音识别。*[*https://static . Google user content . com/media/research . Google . com/en//pubs/archive/36901 . pdf*](https://static.googleusercontent.com/media/research.google.com/en/pubs/archive/36901.pdf)

*7。建造像人一样学习和思考的机器。*[*https://www . Cambridge . org/core/journals/behavioral-and-brain-sciences/article/building-machines-that-learn-and-think-like-persons/a 9535 B1 d 745 a 0377 e 16 c 590 e 14 b 94993*](https://www.cambridge.org/core/journals/behavioral-and-brain-sciences/article/building-machines-that-learn-and-think-like-people/A9535B1D745A0377E16C590E14B94993)

*8。使用多尺度的高效、高性能语义分割。*[*https://journals.plos.org/plosone/article?id = 10.1371/journal . pone . 0255397*](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0255397)