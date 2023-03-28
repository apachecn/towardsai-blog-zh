# 机器学习面试问题-1

> 原文：<https://pub.towardsai.net/16-interview-questions-every-machine-learning-enthusiast-should-know-a4142d5e00cc?source=collection_archive---------1----------------------->

## [职业](https://towardsai.net/p/category/careers)，[机器学习](https://towardsai.net/p/category/machine-learning)

![](img/703a4d0e6fde67a6928cd8de41c2c860.png)

JESHOOTS.COM 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上[拍照](https://unsplash.com/@jeshoots?utm_source=medium&utm_medium=referral)

> 一个机器学习工程师必须涵盖 ML、DL、概率、统计和编码的广度概念，并具有良好的理解深度。机器学习工程师面试不是关于'**什么'**我们总是认为对于**为什么**和**如何**所以我在这次讨论中只限于 2–3**什么**问题，并重点讨论**为什么和如何的问题。**

1.  **如何使用 k-NN 进行分类回归？**

a)对于分类，应用邻居的多数投票，对于回归，我们使用所有 k 个邻居的平均值或中值。

为什么我们在逻辑回归中使用“回归”这个词，即使我们用它来分类？

a)在模型预测(0–1)之间的连续输出后，我们使用逻辑回归进行分类，我们可以将其解释为属于该类的点的概率。

*   如 sigmoid(W.Xq)> 0.5，我们将其标记为正，否则为负。

解释助推背后的直觉

a)用训练数据训练非常基础的模型 h(0 ),因为我们拟合的模型该训练数据被设置为具有高偏差，这使得更多数量的训练错误。

*   然后存储错误
*   根据前一个模型中得到的误差训练下一个模型
*   如果我们继续这样做..…每次我们获得残差并试图在下一个模型中预测它们时，我们的**最终模型=Fi(x) = a0 h0(x) + a1 h1(x)…。+ai hi(x)**

**4)模型的精度等于 0 是什么意思有没有可能精度等于 0。**

a)精度表示在所有预测的阳性中有多少实际上是阳性的。

> 精度=(真阳性)/(真阳性+假阳性)

*   如果模型预测的每个点都是假阳性，则精度等于 0。

为什么我们需要校准？

*   如果需要概率分类标签作为输出，校准是必须的
*   如果度量是对数损耗，并且需要 P(Y_i|X_i)值，则必须进行校准。
*   由诸如 LR、朴素贝叶斯等模型输出的概率通常没有被很好地校准，这可以通过绘制校准图来观察。因此，我们使用校准作为后处理步骤，以确保最终的类别概率得到很好的校准。

**6)深度学习中的参数共享在哪里看到的？**

a)参数共享是特定特征图中所有神经元共享权重。CNN 使用相同的权重向量来执行卷积运算，并且 RNN 在每个时间戳处具有相同的权重。

**7)我们在 LSTM 有多少参数？**

A) 4(mn+m +m)。为衍生检查以下博客。

[](https://medium.com/scavs-ai/summing-up-dl-1-lstm-parameters-9ab64515e705) [## 总结 DL -1: LSTM 参数

### 为什么是 4(nm+n^2+n)？

medium.com](https://medium.com/scavs-ai/summing-up-dl-1-lstm-parameters-9ab64515e705) 

**8)什么是 box cox 变换？什么时候可以用？**

*   Box-Cox 变换帮助我们将非高斯分布变量转化为高斯分布变量。
*   如果您的模型需要高斯分布的要素(高斯朴素贝叶斯),则最好执行此操作。

**9)如何用 K-S 检验找出两个随机变量 X1 和 X2 服从同一分布？**

*   绘制两个随机变量的 CDF
*   假设零假设:两个随机变量来自同一个分布；
*   在整个 CDF 范围内取测试统计量 D =上确界(CDF(X1)-CDF(X2))
*   当 D > c(α) * sqrt( (n+m)/nm ) 时，零假设被拒绝
*   **其中 m 和 n 分别是 CDF1 和 CDF2 中的观测值数量。**

****10)解释脱落层中的反向传播机制？****

*   **当训练具有丢弃的神经网络时，计算输出时不考虑被选择丢弃的所选神经元的那些权重，并且它们具有与它们在先前迭代中相同的值。并且在反向传播时权重不更新。**
*   **注意权重不会变为零，它们只是在迭代中被忽略了。**

****11)找到以下操作后的输出形状和参数？****

> **(7，7，512)平面密集(512)**
> 
> **(7，7，512)conv(512，(7，7))**

*   ****for (7，7，512)flat ern Dense(512)**可训练参数= (7*7*512)*512=12845056，输出形状=512**
*   ****For (7，7，512)conv(512，(7，7))** 可训练参数= (7*7*512)*512=12845056，输出形状=1，1512**

****12)在 x 是连续随机变量的情况下，你将如何计算 P(x/y=0)？****

**a)如果 x 是一个数字特征，那么假设该特征遵循正态分布。然后，我们可以从(PDF)密度函数中获得似然概率，而任何连续变量的绝对似然值为零。**

****13)解释相关性和协方差？****

**a)协方差显示变量之间的线性关系，我们无法解释它们之间的相关性有多强，而相关性给出了两个变量的线性关系强度和方向。**

****14)乙状结肠在反传过程中有什么问题？****

**Sigmoid 函数的导数位于 0 和 0.25 之间。在梯度的链式法则乘法期间，它将趋向于零，这导致消失梯度问题，并且影响权重更新。**

****15)多类分类的微观平均 F1 和宏观平均 F1 之间的差异？****

*   **F1 得分= 2 *精度*召回率/(精度+召回率)**
*   **对于每个类别的 3 个类别分类，将有各自的真阳性、假阳性、真阴性、假阴性**

****a)微平均值 F1****

*   ****微平均精度=**TP1+TP2+TP3/(TP1+TP2+TP3+FP1+FP2+FP3)**
*   ****微平均回忆=**TP1+TP2+TP3/(TP1+TP2+TP3+FN1+FN2+FN3)**
*   ****微平均 F1 =**2 *精度*召回/(精度+召回)**

****b)宏观平均法****

*   ****精度的宏观平均值=P1+P2+P3/3****
*   ****回忆的宏观平均值=R1+R2+R3/3****
*   **其中 P1=TP1/(TP1+FP1)，R1=TP1/(TP1+FN1)，P3 P2 也是如此**
*   ****宏平均值 F1 =**2 *精度*召回/(精度+召回)**

**为什么图像增强有助于图像分类？**

**a)图像数据扩充，用于通过从变化的输入图像中人工生成新图像来创建或扩展数据，例如平移、缩放、镜像、转向、缩放等。使得我们可以使我们的模型对输入图像变化具有鲁棒性。**

# ****延伸阅读:****

**[](https://medium.com/towards-artificial-intelligence/16-interview-questions-that-test-your-machine-learning-skills-part-2-386bf3ca0caf) [## 测试你机器学习技能的 16 个面试问题(下)

### 赢得机器学习面试

medium.com](https://medium.com/towards-artificial-intelligence/16-interview-questions-that-test-your-machine-learning-skills-part-2-386bf3ca0caf) [](https://medium.com/towards-artificial-intelligence/16-interview-questions-that-test-your-machine-learning-skills-part-1-52cd58b64fbb) [## 测试你机器学习技能的 16 个面试问题(第一部分)

### 赢得机器学习面试

medium.com](https://medium.com/towards-artificial-intelligence/16-interview-questions-that-test-your-machine-learning-skills-part-1-52cd58b64fbb) [](https://medium.com/towards-artificial-intelligence/ace-your-machine-learning-interview-with-how-and-why-questions-a0f028a8439e) [## 用“如何”和“为什么”的问题赢得你的机器学习面试。

### 这都是关于如何和为什么？

medium.com](https://medium.com/towards-artificial-intelligence/ace-your-machine-learning-interview-with-how-and-why-questions-a0f028a8439e) [](https://medium.com/towards-artificial-intelligence/best-and-worst-cases-of-machine-learning-models-part-1-36cdb9296611) [## 机器学习模型的最佳和最差情况—第一部分

### 用什么？

medium.com](https://medium.com/towards-artificial-intelligence/best-and-worst-cases-of-machine-learning-models-part-1-36cdb9296611) 

# **参考文献:**

[www.appliedaicourse.com](http://www.appliedaicourse.com)**