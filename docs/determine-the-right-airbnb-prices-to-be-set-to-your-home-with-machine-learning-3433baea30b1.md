# 通过机器学习确定适合你家的 Airbnb 价格

> 原文：<https://pub.towardsai.net/determine-the-right-airbnb-prices-to-be-set-to-your-home-with-machine-learning-3433baea30b1?source=collection_archive---------1----------------------->

## 在人工智能和机器学习的帮助下，可以根据位置、房间类型和评论来预测 Airbnb 房价。

![](img/23e75f3cfd0ae1b70c27010ccf3174fe.png)

Andrea Davis 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

**Airbnb** 是一家可靠的公司，它允许用户为客人预订房间，还允许他们通过了解在该地点住过的人之前的评论来了解条件。如果你是一个使用 Airbnb 为各种旅行者和有兴趣探索城市并寻找临时住宿的人提供房间的人，如果你能在机器学习和数据科学的帮助下了解正确的价格，这将是有价值的。在这篇文章中，我们将探索如何使用 Airbnb 的数据，并根据你的位置和你的邻居来决定你房子的合适价格。让我们现在开始吧。

数据集可以在这个**网站**上找到。随意点击高亮显示的文字查看并下载数据:[纽约市 Airbnb 开放数据| Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)

数据包含列表的名称、主机 id、主机名、邻居、纬度、经度、房间类型和许多其他特性。我们将使用这些功能来预测价格，我们应该根据我们所拥有的关于我们的房子和我们想要出租的房间的信息来设定价格。

同样重要的是要考虑到我们所掌握的数据和房价只是在纽约州。因此，应该考虑到价格反映了我们可以从纽约州**和其他州**得到的价格。如果您在其他州，我们可能无法从我们的模型中获得最佳结果或预测，因为我们已经用纽约州的数据对它们进行了训练。如果你对其他州也感兴趣，请随意下载 Kaggle 中的相关数据，这样你就可以分别确定你的房子的正确价格。好了，事不宜迟，让我们从代码和读取数据开始。

## 导入库

我们导入了 **NumPy** 库，用于高效计算我们在机器学习领域经常处理的矩阵。

我们使用 **seaborn** 来很好地可视化我们的数据和各种相关性。

**Pandas** 基本上是用来读取数据和创建在 Python 中非常有用的数据帧。

**Matplotlib** 类似于用于可视化的 Seaborn 库。

**警告**库的导入只是为了过滤掉运行代码时可能会出现的警告。

当将数据分为训练数据和交叉验证时，我们对交叉验证数据执行**超参数调整**，以产生测试数据的最佳结果。库**‘cross _ val _ score’**为我们提供了测试集上的模型性能。

## 读取数据

我们将**读取**实际数据，并将其存储在变量**‘df’**中，以便执行进一步的分析和机器学习预测。请注意，我刚刚从当前目录中读取了数据。但是，如果数据存在于其他位置，您必须在读取之前指定数据存在的**路径**。

也可能有多个我们想要导入的 CSV 文件，并在需要时**连接**。在我们的例子中，我们只得到一个包含纽约 Airbnb T21 价格列表和有用信息的数据文件。

## 定义有用的功能

虽然上面的函数看起来有点复杂，但我们实际上只是将日期列分别转换为年、月和日。这样做是因为 ML 模型不能直接处理**【对象】**类别或**【日期】**特征。在一天结束时，我们总是以数字的形式给模型输入信息，让它们做出预测。

如果数据中存在任何**缺失的**值，以及我们试图填充这些值的方式，定义该函数会很有帮助。在现实生活中，数据并不总是完美的，异常值**或缺失值**也是如此。处理它们是作为数据科学家或机器学习工程师的艺术。在我们的例子中，我们将使用数据中的平均值**或中位数**来估算缺失值。****

正如上一段前面所说，现实世界的数据中可能存在离群值，必须在训练我们的机器学习模型之前处理这些离群值。离群值的存在会导致我们的模型对训练数据做出**错误的假设**，并导致它们**过度拟合**训练数据。因此，在上述函数的帮助下，我们将从数据中移除这些异常值。

在上述函数的帮助下，我们移除了那些高于值的第 99 百分位的**的点。打印剔除的异常值的总数也很有用，这是在函数中完成的。最后，去除了异常值的数据作为输出返回**。

## 超参数调谐

这是机器学习的重要部分，其中影响模型结果的超参数被修改或调整，以便在交叉验证数据上达到最佳结果。在机器学习中，我们基本上把数据分成**三部分，**即训练数据、交叉验证数据和测试数据。我们首先用训练数据训练模型，然后**调整**交叉验证数据上的超参数，最后，我们看到模型在测试数据上的实际表现如何。如果他们在测试数据上表现良好，我们假设真实世界的数据也遵循与测试数据相同的分布，并且**性能**必须相同。

## 决策树回归器

在下面的代码单元中，我们为**决策树回归器**执行超参数调整，该回归器可以从 **Scikit-Learn** 库中导入。

在决策树回归器中，超参数之一是树的**最大深度**，在这里我们迭代值列表，直到我们在交叉验证数据上得到完美的一个。

## 随机森林回归量

类似地，我们还将对**随机森林模型**执行超参数调整，该模型比决策树复杂得多，包含多个这样的树以及**引导聚合**。让我们看看下面的代码单元，在这里完成了超参数的调整。

我们有一个超参数，它只不过是我们在训练模型时应该定义的估计量或树的总数。如果我们在训练模型时有树的话，有更多的树可以减少**方差**。因此，不同的数据集可能有不同的结果，这取决于我们如何初始化超参数。

最后，我们保存**随机森林模型**的每个超参数值的**均方误差**，以找到表现最好的一个。

## 梯度推进决策树

最后但同样重要的是，我们还将通过定义估计器的数量或用于预测的树的数量，为**梯度增强决策树(GBDT)** 执行超参数调整。请查看下面的代码单元，了解实际是如何做到的。

我们也遵循类似的过程，迭代所有超参数的列表，以找到在**交叉验证数据**上表现最好的一个。如果您正在解决的问题是**时间序列预测**，那么将数据分成 **k 倍**并不是最好的方法，因为在时间序列中，我们总是对使用过去的值来预测未来的值感兴趣。在 k-fold 交叉验证中，我们选择一个 fold 作为交叉验证数据，其余的作为训练数据。通过考虑不同的折叠，我们将这个步骤**进行 k 次**。然而，如果我们使用第一个折叠作为交叉验证，其余的折叠作为测试数据，这将没有意义。在这种情况下，我们只是**泄露**关于**未来**的信息来预测**过去(k 折交叉验证的第一折)**。因此，在时间序列问题中，我们应该使用替代方法来执行时间序列预测和交叉验证。

## 测试预测

对模型进行了训练，并且我们对交叉验证数据进行了超参数调整，以获得最佳结果。一旦我们看到哪个模型在所考虑的指标方面表现最好，例如均方误差，现在是时候检查该模型是否继续在测试数据上表现非常相似。我们只是用下面的代码来评估它在**测试数据**上的表现。

在我们得到测试集上的预测后，我们看到模型相对于实际测试数据的表现如何。最后，我们选择在**测试数据**上表现最好的模型作为我们的最终模型。一旦我们准备好了最终的模型，我们现在就要输入我们将要出租的房间的信息，并确定最好的价格，以便吸引来自不同地区的人。

## 我们的房价即将确定

我们已经执行了超参数调整，并评估了测试集上的模型性能，以最终决定我们将在实际预测中使用哪个模型。现在是时候我们以**特征**的形式定义一些信息，并将它们提供给模型，以便它可以根据训练数据的训练方式做出最佳预测。在下面的代码单元格中，我只需输入一个**邻域**和一些我们在训练中考虑过的其他特征，就可以看到模型给出的总价格。

我刚刚给出了一个数据示例，但是您可以添加您的房屋详细信息，然后根据我们在此过程中使用的训练数据来确定您房屋的正确价格。

## 部署

需要注意的一点是，我们使用 **Jupyter Notebook** 作为各种模型的实验来源，然后选择最佳模型，然后让用户选择房屋类型。然而，对于使用我们的应用程序来预测正确的房价的用户来说，这个过程并不直观。在这种情况下，解决这个问题的最好方法是创建一个 **UI(用户界面)**，以便它是用户友好的，并且他们可以理解他们正在输入的值。此外，该模型将在幕后运行，以给出我们已经在 jupyter 笔记本中试验过的最佳预测。最后，基于在用户界面中输入的信息，向用户给出要为房子设定的正确价格的预测。输出以用户友好的格式显示，以便他们最终可以采取正确的步骤来确定房价。

## 结论

读完这篇文章后，你会对如何使用机器学习和数据科学从数据中提取洞察力并做出有价值的预测有一个清晰的了解，这样他们就可以在各种机器学习模型的帮助下产生最好的收入。我希望这篇文章对你有所帮助。欢迎分享您的反馈和意见。

如果你想获得更多关于我的最新文章的更新，并且每月只需 **5 美元**就可以无限制地访问中型文章，请随时使用下面的**链接**来添加你对我工作的支持。谢了。

[https://suhas-maddali007.medium.com/membership](https://suhas-maddali007.medium.com/membership)

以下是您联系我或查看我作品的方式。

**GitHub:** [苏哈斯·马达利(Suhas Maddali)(github.com)](https://github.com/suhasmaddali)

**LinkedIn:** [(1)苏哈斯·马达利，东北大学，数据科学| LinkedIn](https://www.linkedin.com/in/suhas-maddali/)

**中等:** [苏哈斯·马达利——中等](https://suhas-maddali007.medium.com/)