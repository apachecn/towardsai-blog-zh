# 如何用 PySpark 训练 XGBoost 模型

> 原文：<https://pub.towardsai.net/how-to-train-xgboost-model-with-pyspark-2c4e219da5e1?source=collection_archive---------1----------------------->

![](img/a81416b859e0e63bad7b77a975662dff.png)

# 为什么选择 XGBoost？

X GBoost ( **极限梯度提升**)是各行各业数据科学家最流行、最广泛使用的 ML 算法之一。此外，该算法在减少计算时间和提供内存资源的最佳使用方面非常有效，另一个重要特征是在训练过程的实现和并行化上处理缺失值。

如今，由于数据集规模迅速增加，分布式训练真的很重要，所以在这篇博客中，我们将探讨有人如何集成 ***XGBoost + PySpark*** 并进行模型训练和评分。

人们可以很容易地在 **pyspark.ml** 或 **MLLib、**中使用可用的 ml 算法，但要以同样的方式使用 XGBoost，我们必须添加一些外部依赖项和 python XGBoost 包装器，另一种方法是直接使用带有 pyspark 的 **XGBoost 本机**框架，最新版本的 [XGBoost](https://pypi.org/project/xgboost/) 不支持该框架(这里唯一的限制是它仅在 python 版本≥3.8 上受支持)，要知道(感谢 dmlc 社区..)

但在这篇博客中，我们主要关注的是如何在 python 版本< 3.8.

**上与 PySpark 集成，在开始集成部分之前，请从这个** [**链接**](https://github.com/divyhshah/xgboost-pyspark) **下载必备文件。**

一旦你下载了所有的 3 个文件，我们就可以把 XGBoost 和 PySpark 集成起来了。

1.  如下面的示例代码所述，在 **PYSPARK_SUBMIT_ARGS** 部分添加 **JAR** 文件(确保添加文件位置的准确路径)
2.  创建您的 Spark 会话。
3.  添加 XGBoost python 包装器代码文件 ***(。zip 文件)*** 在 sparkContext 中。(我们这样做是为了支持 XGBoost 导入，再次确保添加 zip 文件的正确路径)

```
import os
import findspark
import numpy as np

## Add the path of the downloaded jar files
os.environ['PYSPARK_SUBMIT_ARGS'] = '--jars xgboost4j-spark.jar,xgboost4j.jar pyspark-shell'

findspark.init()

spark = SparkSession\
        .builder\
        .appName("XGBoost_PySpark")\
        .master("local[*]")\
        .getOrCreate()

spark.sparkContext.addPyFile("sparkxgb.zip")
```

完成上述步骤后，您可以通过导入 XGBClassifier 或 Regressor 进行交叉检查。

```
from sparkxgb.xgboost import XGBoostClassificationModel, XGBoostClassifier
```

如果你得到一个 JAR 错误，那么可能是由于版本不匹配，在这种情况下，你可以从[这里](https://mvnrepository.com/artifact/ml.dmlc/xgboost-jvm)下载另一个版本的 JAR 文件来检查。

现在，一旦所有的都完成了，让我们试着建立一个简单的模型，按照下面的步骤。

这里，我们采用了一个开源贷款预测数据集，并试图预测贷款是否会获得批准，这里的 **Loan_Status** 是我们的目标变量(因为它是 Y/N 格式，所以我们在 1/0 中进行了转换)。

1.  **添加所需的星火库**

```
from pyspark.ml.feature import StringIndexer, VectorAssembler
from sparkxgb.xgboost import XGBoostClassificationModel, XGBoostClassifier
from pyspark.ml import Pipeline
from pyspark.mllib.evaluation import MulticlassMetrics
from pyspark.sql import functions as F
```

**2。加载数据集并进行所需的预处理**

```
data = spark.read.parquet('train.parquet')
data = data.withColumn('label', F.when(F.col('Loan_Status')=='Y', 1) \
                                            .otherwise(0)
                                  )
data.show(5)
```

```
+--------+------+-------+----------+------------+-------------+---------------+-----------------+----------+----------------+--------------+-------------+-----------+-----+
| Loan_ID|Gender|Married|Dependents|   Education|Self_Employed|ApplicantIncome|CoapplicantIncome|LoanAmount|Loan_Amount_Term|Credit_History|Property_Area|Loan_Status|label|
+--------+------+-------+----------+------------+-------------+---------------+-----------------+----------+----------------+--------------+-------------+-----------+-----+
|LP001002|  Male|     No|         0|    Graduate|           No|           5849|              0.0|      null|           360.0|           1.0|        Urban|          Y|    1|
|LP001003|  Male|    Yes|         1|    Graduate|           No|           4583|           1508.0|     128.0|           360.0|           1.0|        Rural|          N|    0|
|LP001005|  Male|    Yes|         0|    Graduate|          Yes|           3000|              0.0|      66.0|           360.0|           1.0|        Urban|          Y|    1|
|LP001006|  Male|    Yes|         0|Not Graduate|           No|           2583|           2358.0|     120.0|           360.0|           1.0|        Urban|          Y|    1|
|LP001008|  Male|     No|         0|    Graduate|           No|           6000|              0.0|     141.0|           360.0|           1.0|        Urban|          Y|    1|
+--------+------+-------+----------+------------+-------------+---------------+-----------------+----------+----------------+--------------+-------------+-----------+-----+
```

在上面的示例数据中，我们可以看到一些列有分类/字符串值..因此，我们需要在将它们传递到模型之前将其转换为数值，PySpark 提供了**string indexer&OneHotEncoder**用于相同的目的，这里我们将 **StringIndexer。**

```
index1 = StringIndexer().setInputCol("Gender").setOutputCol("GenderIndex").setHandleInvalid("keep")
index2 = StringIndexer().setInputCol("Married").setOutputCol("MarriedIndex").setHandleInvalid("keep")
index3 = StringIndexer().setInputCol("Education").setOutputCol("EducationIndex").setHandleInvalid("keep")
index4 = StringIndexer().setInputCol("Self_Employed").setOutputCol("SelfEmployedIndex").setHandleInvalid("keep")
index5 = StringIndexer().setInputCol("Property_Area").setOutputCol("PropertyAreaIndex").setHandleInvalid("keep")
```

现在，正如我们所看到的，我们有多个 **StringIndexer** 对象，我们需要通过每个索引器进行转换，这是一个漫长的过程，因此为了整合所有的转换、特征矢量化和模型拟合 **PySpark** **ML** 提供了 **ML 管道**的概念，在其中我们可以将几个步骤组合在一起并随时运行，

在创建管道对象之前，我们先定义 **VectorAssembler** 和 **Model** 对象。

```
## define list of your final features
features = ['GenderIndex', 'MarriedIndex', 'EducationIndex', 'SelfEmployedIndex', 'PropertyAreaIndex',
           'ApplicantIncome', 'CoapplicantIncome', 'LoanAmount', 'Loan_Amount_Term', 'Credit_History']

vec_assembler = VectorAssembler(inputCols=features, outputCol='features', handleInvalid='keep')

xgb = XGBoostClassifier(objective="binary:logistic",seed=1712,
                        featuresCol="features",
                        labelCol="label",
                        missing=0.0,
                        )
```

现在让我们创建管道对象并构建最终模型。

**3。创建 ML 管道**

```
# here add all your steps inside setStages

pipeline = Pipeline().setStages([index1, index2, index3, index4, index5, vec_assembler, xgb])

# split the data in train and test
trainDF, testDF = train_data.randomSplit([0.7, 0.3], seed=1712)

model = pipeline.fit(trainDF)

# Generate the prediction on test data

predictions = model.transform(testDF)[['Loan_ID', 'prediction', 'label']]
predictions.show()
```

```
+--------+----------+-----+
| Loan_ID|prediction|label|
+--------+----------+-----+
|LP001005|       1.0|    1|
|LP001013|       1.0|    1|
|LP001018|       1.0|    1|
|LP001027|       1.0|    1|
|LP001032|       1.0|    1|
+--------+----------+-----+
```

哇..最后建立 XGBoost 模型，并用 PySpark 进行测试

**4。检查绩效指标**

```
from pyspark.sql.types import DoubleType

predictionAndLabels = predictions.select(['prediction', 'label']\
                                  ).withColumn('label',F.col('label').cast(DoubleType())).rdd

metrics = MulticlassMetrics(predictionAndLabels)

cm = metrics.confusionMatrix().toArray()

accuracy=(cm[0][0]+cm[1][1])/cm.sum()
precision=(cm[1][1])/(cm[0][1]+cm[1][1])
recall=(cm[1][1])/(cm[1][0]+cm[1][1])

print(accuracy, precision, recall)
```

```
(0.7015706806282722, 0.7517241379310344, 0.8384615384615385)
```

**5。超参数调谐(可选步骤)**

如果你想调整你的 XGBoost 参数，然后按照下面的代码，实际上，这不是可行的方法，因为在大量的数据上，它非常昂贵，因为它在每个参数的组合上建立一个模型，一个更好的方法是使用 python 中的**randomsearccv**并在这里使用该参数，或者你可以在 PySpark 中设计代码，每次使用随机值选择并分配给模型。

```
from pyspark.ml.tuning import ParamGridBuilder, CrossValidator, CrossValidatorModel
from pyspark.ml.evaluation import BinaryClassificationEvaluator, MulticlassClassificationEvaluator

xgbEval = BinaryClassificationEvaluator()

# Define your list of grid search parameters

paramGrid = (ParamGridBuilder()
             .addGrid(xgb.alpha,[1e-5, 1e-2, 0.1])
             .addGrid(xgb.eta, [0.001, 0.01])
             .addGrid(xgb.numRound, [150,160])
             .addGrid(xgb.maxDepth, range(3,7,3))
             .addGrid(xgb.minChildWeight, [3.0, 4.0])
             .addGrid(xgb.gamma, [i/10.0 for i in range(0,2)])
             .addGrid(xgb.colsampleBytree, [i/10.0 for i in range(3,6)])
             .addGrid(xgb.subsample, [0.4,0.6])
             .build())

cv = CrossValidator(estimator=pipeline, estimatorParamMaps=paramGrid, evaluator=xgbEval, numFolds=3)
cvModel = cv.fit(trainDF)
cvPreds = cvModel.transform(testDF)
xgbEval.evaluate(cvPreds)

## Print the tuned params
cvModel.bestModel.extractParamMap()
```

感谢您抽出时间阅读我的博客，希望对您有所帮助。总而言之，我们了解了一些 XGBoost 及其优点。我们还研究了使用外部依赖在 PySpark 中逐步实现 XGBoost。我期待着来自我的读者的各种建议，让我知道你想让我写的下一部是什么。