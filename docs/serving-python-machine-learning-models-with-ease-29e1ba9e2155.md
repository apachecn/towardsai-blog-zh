# 轻松服务于 Python 机器学习模型

> 原文：<https://pub.towardsai.net/serving-python-machine-learning-models-with-ease-29e1ba9e2155?source=collection_archive---------0----------------------->

![](img/360da4e3eb1f61ff0304f905e4021828.png)

照片由 [Marius Masalar](https://unsplash.com/@marius?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

有没有训练过一个新模型，并且只想通过 API 直接使用它？有时候你不想写 Flask 代码，或者把你的模型打包并在 Docker 中运行。如果这听起来像你，你肯定想看看 [MLServer](https://github.com/seldonio/mlserver) 。这是一个基于 python 的推理服务器，最近正式上市，它真正出色的地方在于它也是一个为生产环境设计的高性能服务器。这意味着，通过在本地为模型提供服务，您可以在与它们进入生产环境时完全相同的环境中运行。

这篇博客以几个图像模型为例，带您了解如何使用 MLServer

# 资料组

我们将要使用的数据集是[时尚 MNIST 数据集](https://www.kaggle.com/zalando-research/fashionmnist)。它包含 70，000 幅灰度为 28x28 像素的服装图像，分为 10 个不同的类别(上衣、连衣裙、外套、裤子等)。

*如果你想复制这篇博客中的代码，确保你下载了文件，并把它们解压到一个名为* `*data*` *的文件夹中。GitHub repo 中省略了它们，因为它们非常大。*

# 培训 Scikit-learn 模型

首先，我们将使用 scikit-learn 框架训练一个支持向量机(SVM)模型。然后，我们将模型保存到一个名为`Fashion-MNIST.joblib`的文件中。

```
import pandas as pd
from sklearn import svm
import time
import joblib#Load Training Data
train = pd.read_csv('../../data/fashion-mnist_train.csv', header=0)
y_train = train['label']
X_train = train.drop(['label'], axis=1)
classifier = svm.SVC(kernel="poly", degree=4, gamma=0.1)#Train Model
start = time.time()
classifier.fit(X_train.values, y_train.values)
end = time.time()
exec_time = end-start
print(f'Execution time: {exec_time} seconds')#Save Model
joblib.dump(classifier, "Fashion-MNIST.joblib")
```

注意:SVM 算法不是特别适合大型数据集，因为它的二次性质。本例中的模型将取决于您的硬件，需要几分钟来训练。

# 服务于 Scikit-learn 模型

好了，我们现在已经有了一个保存的模型文件`Fashion-MNIST.joblib`。让我们来看看如何使用 MLServer 实现这一点...

首先，我们需要安装 MLServer。

`pip install mlserver`

额外的运行时是可选的，但是当服务模型时，我们将安装 Scikit-Learn 和 XGBoost

`pip install mlserver-sklearn mlserver-xgboost`

*你可以在这里* 找到所有推理运行时 [*的细节*](https://mlserver.readthedocs.io/en/latest/runtimes/index.html#included-inference-runtimes)

完成后，我们需要做的就是添加两个配置文件:

*   `settings.json` -包含服务器本身的配置。
*   `model-settings.json`——顾名思义，这个文件包含了我们想要运行的模型的配置。

对于我们的`settings.json`文件，只定义一个参数就足够了:

```
{
    "debug": "true"
}
```

`model-settings.json`文件需要更多的信息，因为它需要了解我们试图服务的模型:

```
{
    "name": "fashion-sklearn",
    "implementation": "mlserver_sklearn.SKLearnModel",
    "parameters": {
        "uri": "./Fashion_MNIST.joblib",
        "version": "v1"
    }
}
```

这个`name`参数应该是不言自明的。它为 MLServer 提供了一个惟一的标识符，这在服务多个模型时特别有用(我们稍后会谈到这一点)。`implementation`定义使用哪个预建服务器(如果有的话)。它与用于训练模型的机器学习框架紧密耦合。在我们的例子中，我们使用 scikit-learn 训练模型，因此我们将使用 MLServer 的 scikit-learn 实现。对于 model，`parameters`我们只需要提供模型文件的位置以及版本号。

就这样，两个小的配置文件，我们准备好使用命令来服务我们的模型:

`mlserver start .`

嘣，我们现在已经让我们的模型在本地生产就绪的服务器上运行了。现在已经准备好通过 HTTP 和 gRPC 接受请求了(分别是默认端口`8080`和`8081`)。

# 测试模型

既然我们的模型已经建立并运行了。让我们发送一些请求来看看它的运行情况。

为了对我们的模型进行预测，我们需要向以下 URL 发送一个 POST 请求:

`http://localhost:8080/v2/models/<MODEL_NAME>/versions/<VERSION>/infer`

这意味着要访问我们之前培训的 scikit-learn 模型，我们需要用`fashion-sklearn`替换`MODEL_NAME`，用`v1`替换`VERSION`。

下面的代码显示了如何导入测试数据，向模型服务器发出请求，然后将结果与实际标签进行比较:

```
import pandas as pd
import requests#Import test data, grab the first row and corresponding label
test = pd.read_csv('../../data/fashion-mnist_test.csv', header=0)
y_test = test['label'][0:1]
X_test = test.drop(['label'],axis=1)[0:1]#Prediction request parameters
inference_request = {
    "inputs": [
        {
          "name": "predict",
          "shape": X_test.shape,
          "datatype": "FP64",
          "data": X_test.values.tolist()
        }
    ]
}
endpoint = "http://localhost:8080/v2/models/fashion-sklearn/versions/v1/infer"#Make request and print response
response = requests.post(endpoint, json=inference_request)
print(response.text)
print(y_test.values)
```

当运行上面的`test.py`代码时，我们从 MLServer 得到以下响应:

```
{
  "model_name": "fashion-sklearn",
  "model_version": "v1",
  "id": "31c3fa70-2e56-49b1-bcec-294452dbe73c",
  "parameters": null,
  "outputs": [
    {
      "name": "predict",
      "shape": [
        1
      ],
      "datatype": "INT64",
      "parameters": null,
      "data": [
        0
      ]
    }
  ]
}
```

您会注意到 MLServer 已经生成了一个请求 id，并自动添加了用于服务我们请求的模型和版本的元数据。一旦我们的模型进入生产阶段，获取这种元数据是非常重要的；它允许我们记录每个请求，以便进行审计和故障排除。

您可能还注意到 MLServer 已经为`outputs`返回了一个数组。在我们的请求中，我们只发送了一行数据，但是 MLServer 也处理批量请求并将它们一起返回。您甚至可以使用一种叫做[自适应批处理](https://mlserver.readthedocs.io/en/latest/user-guide/adaptive-batching.html)的技术来优化在生产环境中处理多个请求的方式。

在我们上面的例子中，模型的预测可以在`outputs[0].data`中找到，这表明模型已经用类别`0`标记了这个样本(值 0 对应于类别`t-shirt/top`)。那个样本的真实标签也是一个`0`，所以这个模型的预测是正确的！

# 为 XGBoost 模型定型

现在我们已经看到了如何使用 MLServer 创建和服务单个模型，让我们看看如何处理在不同框架中训练的多个模型。

我们将使用相同的时尚 MNIST 数据集，但这一次，我们将训练一个 [XGBoost](https://xgboost.readthedocs.io/en/stable/) 模型。

```
import pandas as pd
import xgboost as xgb
import time#Load Training Data
train = pd.read_csv('../../data/fashion-mnist_train.csv', header=0)
y_train = train['label']
X_train = train.drop(['label'], axis=1)
dtrain = xgb.DMatrix(X_train.values, label=y_train.values)#Train Model
params = {
    'max_depth': 5,
    'eta': 0.3,
    'verbosity': 1,
    'objective': 'multi:softmax',
    'num_class' : 10
}
num_round = 50start = time.time()
bstmodel = xgb.train(params, dtrain, num_round, evals=[(dtrain, 'label')], verbose_eval=10)
end = time.time()
exec_time = end-start
print(f'Execution time: {exec_time} seconds')#Save Model
bstmodel.save_model('Fashion_MNIST.json')
```

上面用来训练 XGBoost 模型的代码类似于我们之前用来训练 scikit-learn 模型的代码，但是这一次我们的模型以 XGBoost 兼容的格式保存为`Fashion_MNIST.json`。

# 服务多个模型

MLServer 很酷的一点是它支持[多模型服务](https://mlserver.readthedocs.io/en/latest/examples/mms/README.html)。这意味着您不必为您想要部署的每个 ML 模型创建或运行一个新的服务器。使用我们在上面构建的模型，我们将使用这个特性同时为它们服务。

当 MLServer 启动时，它将在目录(以及任何子目录)中搜索`model-settings.json`文件。如果你有多个`model-settings.json`文件，那么它会自动为它们服务。

*注意:您仍然只需要根目录*中的一个 `*settings.json*` *(服务器配置)文件*

下面是我的目录结构的细目分类，供参考:

```
.
├── data
│   ├── fashion-mnist_test.csv
│   └── fashion-mnist_train.csv
├── models
│   ├── sklearn
│   │   ├── Fashion_MNIST.joblib
│   │   ├── model-settings.json
│   │   ├── test.py
│   │   └── train.py
│   └── xgboost
│       ├── Fashion_MNIST.json
│       ├── model-settings.json
│       ├── test.py
│       └── train.py
├── README.md
├── settings.json
└── test_models.py
```

注意有两个`model-settings.json`文件——一个用于 scikit-learn 模型，一个用于 XGBoost 模型。

我们现在可以运行`mlserver start .`，它将开始处理两个模型的请求。

```
[mlserver] INFO - Loaded model 'fashion-sklearn' succesfully.
[mlserver] INFO - Loaded model 'fashion-xgboost' succesfully.
```

# 测试多个模型的准确性

现在这两个模型都已经在 MLServer 上运行了，我们可以使用测试集中的样本来验证我们的每个模型有多准确。

以下代码向每个模型发送一个批处理请求(包含完整的测试集),然后将收到的预测与真实标签进行比较。在整个测试集上这样做给了我们一个相当好的方法来衡量每个模型的准确性，并在最后打印出来。

```
import pandas as pd
import requests
import json#Import the test data and split the data from the labels
test = pd.read_csv('./data/fashion-mnist_test.csv', header=0)
y_test = test['label']
X_test = test.drop(['label'],axis=1)#Build the inference request
inference_request = {
    "inputs": [
        {
          "name": "predict",
          "shape": X_test.shape,
          "datatype": "FP64",
          "data": X_test.values.tolist()
        }
    ]
}#Send the prediction request to the relevant model, compare responses to training labels and calculate accuracy
def infer(model_name, version):
    endpoint = f"http://localhost:8080/v2/models/{model_name}/versions/{version}/infer"
    response = requests.post(endpoint, json=inference_request) #calculate accuracy
    correct = 0
    for i, prediction in enumerate(json.loads(response.text)['outputs'][0]['data']):
        if y_test[i] == prediction:
            correct += 1
    accuracy = correct / len(y_test)
    print(f'Model Accuracy for {model_name}: {accuracy}')infer("fashion-xgboost", "v1")
infer("fashion-sklearn", "v1")
```

结果显示，XGBoost 模型略微优于 SVM scikit-learn 模型:

```
Model Accuracy for fashion-xgboost: 0.8953
Model Accuracy for fashion-sklearn: 0.864
```

# 摘要

希望到现在为止，您已经理解了使用 [MLServer](https://mlserver.readthedocs.io/en/latest/index.html) 为模型提供服务是多么容易。要了解更多信息，值得阅读一下[文档](https://mlserver.readthedocs.io/en/latest/index.html)，看看不同框架的[示例。](https://mlserver.readthedocs.io/en/latest/examples/index.html)

这个例子中的所有代码都可以在[这里](https://github.com/edshee/mlserver-example)找到。