# 使用 Prophet 预测 2021 年比特币价格

> 原文：<https://pub.towardsai.net/using-prophet-to-predict-bitcoin-prices-for-2021-1dd65c86c858?source=collection_archive---------3----------------------->

## [数据可视化](https://towardsai.net/p/category/data-visualization)

## 完整的代码可在我的回购的

[**点击这里了解我，我的项目，我的最新文章。**](http://www.michelangiolo.best/)

Prophet library 是一个开源的加法回归模型，由脸书提供，用于时间序列预测。虽然有一个使用神经网络的更高级版本的 prophet，NeuralProphet，但我将使用这个使用机器学习技术(回归模型)来估计未来价格的简化版本。

## 先知的局限性

你能在什么上面使用先知图书馆？这个工具最大的局限性就是局限于单变量模型。这意味着只能对一个变量起作用。例如，如果我们真的想建立一个现实的模型，我们会考虑其他变量来预测资产的价格。经济怎么样了？新冠肺炎是如何扩张的？有没有可能让比特币变得不那么重要的竞争对手？政府干预让比特币变得更相关还是更不相关？通过量化所有这些其他变量并将其输入到我们的模型中，我们可以创建一个更可靠的回归模型，该模型考虑了所有这些因素来预测价格。

通过使用具有单变量限制的 prophet，我们假设所有其他变量都不存在，因为它们根本不适合我们的模型。最终，我们假设比特币本身的价格将足以让我们对其未来趋势有所了解:这是否足以创造一个可行的模型？

# 步伐

1.  下载 BTC 数据
2.  导入库
3.  导入数据
4.  拟合模型
5.  做预测
6.  图形和最终结果

## 1.下载 BTC 数据

下载加密货币数据有多种选择。对于大量的分析和数据(例如同时下载 10 种不同的加密货币)，我更喜欢使用代码。然而，对于这个实验，我很乐意手动下载数据集。数据集也可以在我的回购，但这里是程序，如果你想下载最新的:[https://finance.yahoo.com/quote/BTC-USD/history/](https://finance.yahoo.com/quote/BTC-USD/history/)

![](img/11c0099b416d3b7b911c2844f40d5f6b.png)

按照以下步骤下载 5 年的 BTC 历史

## 2.导入库

要运行这段代码，我需要安装并导入以下库:

```
!pip install pystan
!pip install fbprophetimport pandas as pd
from fbprophet import Prophet
```

## 3.导入数据集

根据您用来运行代码的 IDE，您需要指定。csv 定位，然后用熊猫导入。Prophet 只处理名为“ds”的列中包含字符串时间序列格式的数据和名为“y”的列中包含连续值的数据。我必须相应地创建数据集。

```
df = pd.read_csv('BTC-USD.csv')
df = df[['Date', 'Close']]
df.columns = ['ds', 'y']
df
```

## 4.拟合模型

先知库遵循 sklearn 文档。我需要将模型与数据进行拟合。

```
m = Prophet()
m.fit(df)
```

## 5.做预测

现在，我将告诉模型我想要一个未来 365 天的预测:

```
#estabilish prediction period
future = m.make_future_dataframe(periods=365)
future#make forecast
forecast = m.predict(future)
forecast[['ds', 'yhat', 'yhat_lower', 'yhat_upper']].tail()
```

该模型将输出关于**预测**数据帧的预测。

## 6.图形和最终结果

通过绘制结果，这是我最后得到的结果:

```
#graphing
from fbprophet.plot import plot
fig1 = m.plot(forecast, figsize=(20, 9))
```

![](img/62522a44a7af64b115388251b6a6b9c7.png)

# 结论

对 Prophet 计算的预测有几种解释:比特币价格目前的势头已经飙升，我们很可能会看到非常快速的下跌。到目前为止，比特币的表现就像一个周期性的泡沫，因此空气会猛烈地冲出泡沫是有道理的。