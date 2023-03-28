# 用机器学习预测股票价格的初学者指南

> 原文：<https://pub.towardsai.net/a-beginners-guide-to-predicting-stock-prices-with-machine-learning-f5a870f6b846?source=collection_archive---------2----------------------->

![](img/1dd9b9d95155f60b11da21f9f122c3e0.png)

# 介绍

预测股票价格是金融领域的一项热门任务。它包括根据过去的数据和市场趋势预测公司股票的未来价值。许多投资者利用股票价格预测来做出明智的决定，决定是否买入、卖出或持有某一特定股票。

在本教程中，我们将使用机器学习算法来预测股票的未来价格。机器学习是一种人工智能，涉及训练计算机学习数据模式，并基于这些模式进行预测。有许多不同类型的机器学习算法，我们将使用一种称为“回归算法”的特定类型来进行股票价格预测。

我们将使用`yahoo_fin`库从雅虎财经中抓取股票数据，使用`pandas`和`sklearn`库对数据进行预处理和分析。

# 步骤 1:收集数据

创建机器学习模型的第一步是收集数据。在这种情况下，我们需要收集我们想要预测的股票的过去价格的数据。这些数据可以从股票市场数据库或提供历史股票价格信息的金融网站获得。

重要的是收集尽可能多的数据，以使我们的模型有最好的机会准确预测未来的股票价格。然而，确保数据干净无误也很重要。

下面是一个例子，说明我们如何使用 Python 中的`yahoo_fin`和`pandas`库来收集股票过去价格的数据:

```
from yahoo_fin import stock_info as si
import pandas as pd

# Scrape stock data from Yahoo Finance
stock_data = si.get_data("AAPL")

# Print the first few rows of the data
print(stock_data.head())
```

这段代码使用`yahoo_fin`库中的`get_data()`函数来抓取指定股票代码(在本例中，苹果公司的“AAPL”)的股票数据，并将其存储在`pandas` DataFrame 中。DataFrame 是包含行和列的二维数据表。我们可以使用`head()`方法打印数据帧的前几行，这将允许我们看到数据的结构。

# 步骤 2:预处理数据

一旦我们收集了数据，下一步就是对其进行预处理。预处理包括清理和格式化数据，以便它可以用于训练我们的机器学习模型。

这可能涉及以下任务:

*   删除任何缺失或不完整的数据点
*   标准化数据(将其缩放到一致的范围)
*   将数据分成训练集和测试集(下一步将详细介绍)

下面是一个例子，说明我们如何使用 Python 中的`pandas`和`sklearn`库预处理股票价格数据:

```
import pandas as pd
from sklearn.preprocessing import MinMaxScaler

# Read in stock price data from a CSV file
stock_data = pd.read_csv("stock_prices.csv")

# Drop any rows with missing data
stock_data.dropna(inplace=True)

# Normalize the data using the MinMaxScaler
scaler = MinMaxScaler()
stock_data_scaled = scaler.fit_transform(stock_data)

# Split the data into training and testing sets
training_data = stock_data_scaled[:int(len(stock_data_scaled) * 0.8)]
testing_data = stock_data_scaled[int(len(stock_data_scaled) * 0.8):]
```

在这段代码中，我们使用`dropna()`方法从 DataFrame 中删除任何缺少数据的行。然后，我们从`sklearn`库中创建了一个`MinMaxScaler`类的实例，并使用它通过将数据缩放到 0 和 1 之间的一致范围来规范化数据。这有助于提高机器学习模型的性能。

最后，我们使用索引将规范化的数据分成训练集和测试集。训练集将用于训练模型，测试集将用于评估模型的性能。

# 第三步:训练模型

既然我们已经预处理了数据，我们就可以开始训练我们的机器学习模型了。这包括将数据输入到模型中，并调整模型的内部参数以优化其性能。

为了训练机器学习模型，我们通常将数据分成两组:训练集和测试集。训练集用于训练模型，测试集用于评估模型的性能。

在这种情况下，我们将使用回归算法来预测股票价格。回归算法用于预测连续值，如股票价格。有许多不同类型的回归算法，包括线性回归、岭回归和套索回归。

下面是我们如何使用 Python 中的`sklearn`库训练线性回归模型的例子:

```
from sklearn.linear_model import LinearRegression

# Create a linear regression model
model = LinearRegression()

# Train the model on the training data
model.fit(training_data, training_targets)
```

在这段代码中，我们创建了一个`LinearRegression`类的实例，并使用`fit()`方法根据训练数据训练模型。训练数据由过去的股票价格组成，训练目标是我们要预测的未来股票价格。

# 步骤 4:测试模型

一旦模型被训练，我们可以使用测试集来评估它的性能。这包括将测试集输入到模型中，并将模型的预测与实际股票价格进行比较。

我们可以使用几个指标来评估模型的性能，例如平均绝对误差和均方根误差。这些指标告诉我们模型的预测有多准确，我们可以使用它们来微调模型并提高其性能。

下面是一个例子，说明我们如何使用 Python 中的`sklearn`库来评估线性回归模型的性能:

```
from sklearn.metrics import mean_absolute_error, mean_squared_error

# Make predictions on the testing data
predictions = model.predict(testing_data)

# Calculate the mean absolute error and mean squared error
mae = mean_absolute_error(testing_targets, predictions)
mse = mean_squared_error(testing_targets, predictions)

# Print the results
print(f"Mean Absolute Error: {mae:.2f}")
print(f"Mean Squared Error: {mse:.2f}")
```

在这段代码中，我们使用`predict()`方法对测试数据进行预测，使用`sklearn`库中的`mean_absolute_error()`和`mean_squared_error()`函数计算模型的平均绝对误差(MAE)和均方误差(MSE)。

MAE 是模型预测中误差的平均大小的度量，而 MSE 是误差的平均平方大小的度量。这两个指标对于评估回归模型的性能都很有用。

# 第五步:做预测

在我们训练和测试了我们的模型之后，我们可以用它来对新数据进行预测。这可能包括输入当前股票价格，并使用模型预测未来价格。

重要的是要记住，股票价格预测并不总是准确的，有许多因素可以影响股票的价格。因此，在使用机器学习模型进行投资决策时，谨慎使用非常重要。

以下是我们如何使用训练好的线性回归模型对新数据进行预测的示例:

```
# Make predictions on new data
new_data = [[100, 200, 300]]
predictions = model.predict(new_data)

# Print the predictions
print(predictions)
```

在这段代码中，我们使用`predict()`方法对包含过去股票价格的新数据集进行预测。该模型将使用它在训练中学习的模式来预测未来的股票价格。

# 结论

在本教程中，我们介绍了使用机器学习算法预测股票价格的步骤。我们收集数据，对其进行预处理，训练线性回归模型，测试该模型，并使用该模型进行预测。虽然机器学习可以成为预测股价的强大工具，但重要的是要记住，有许多因素可以影响股票的价格，没有模型是完美的。

作为最后一点，重要的是要记住，本教程只是使用机器学习算法预测股票价格的过程的概述。在建立和使用机器学习模型时，需要更多的细节和考虑，在做出投资决定之前，做进一步的研究和寻求专家的建议总是一个好主意。