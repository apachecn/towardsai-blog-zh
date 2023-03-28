# 多类图像分类—使用 Keras 和 TensorFlow 进行实践

> 原文：<https://pub.towardsai.net/multiclass-image-classification-hands-on-with-keras-and-tensoflow-e1cf434f3467?source=collection_archive---------0----------------------->

## [深度学习](https://towardsai.net/p/category/machine-learning/deep-learning)

第 1 部分—例外

图像分类或计算机视觉是人工智能的一个分支，其任务是设计可以基于数字图像识别或分类对象的系统。由于应用的广泛性，它是一个受欢迎的领域-图像分类可用于各种应用，如从照片中识别特定的花或将医学图像分类为正常或疾病。

在本文中，我将介绍如何使用 Keras 创建卷积神经网络来对数据集中的图像进行分类。Keras 是一个使用高级 API 构建模型的简单框架。我假设您至少对 Python 有基本的了解。

使用 Keras 创建用于图像分类的卷积神经网络有两种方式。使用第一种方法(硬方法)，您可以定义使用哪些层以及如何将它们链接在一起，编译您的模型，然后您的模型就可以使用了。第二种方法(简单且有时更有效的方法)是使用迁移学习，并使用预先训练好的模型，这些模型已经被证明对任务足够强大。

Keras 已经为我们提供了 26 个可以应用于我们数据的预训练模型。然而，有了 26 个预先训练好的模型，我们怎么知道哪一个最适合我们的数据呢？

答案是:*我们不知道！我们需要测试它们。*

在这个动手系列中，我将在 Keras 上测试一些免费的预训练模型，并在[英特尔图像分类数据集](https://www.kaggle.com/puneet6060/intel-image-classification)上评估它们的性能。该数据集包含 6 类图像:建筑物、森林、冰川、山脉、海洋和街道。这意味着我们将在分类数据集中尝试模型。也可以使用二进制数据集，我将把它留给另一篇文章。

您可以在 Github 上找到本文中使用的代码。

我强烈建议您在启用 GPU 的情况下在 Google Colab 上运行代码(除非您在笔记本电脑上为 ML 任务配置了强大的 GPU)。要启用 GPU，请转到“编辑”>“笔记本设置”,然后选择 GPU，默认值为“无”。保存您的设置。

![](img/43b0e845b3d8132c6651be5113d17092.png)

如何启用谷歌 GPU？图片来自作者。

让我们跳进教程吧！

在我们开始预训练模型之前，我们需要对所有模型执行一些通用步骤，包括数据库下载、数据预处理和数据分割。

# **数据预处理**

这一步对于所有的模型都是相似的，所以我不会在本系列的下一篇文章中重复。

我们需要做的第一件事是从 Python 库中导入必要的包:

```
import pandas as pd
import matplotlib as mat
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
import random
import os
from numpy.random import seed
from sklearn.model_selection import train_test_split
from sklearn import metrics
from sklearn.metrics import accuracy_score
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers
from tensorflow.keras import callbacks
from tensorflow.keras.models import Model
from tensorflow.keras.preprocessing.image import ImageDataGenerator
import glob
import cv2
from tensorflow.random import set_seed
import warnings
from sklearn.preprocessing import OneHotEncoder
from sklearn.model_selection import train_test_split
from tensorflow.keras.models import Sequential, Model
from tensorflow.keras.layers import Dense, Flatten, Conv2D, MaxPool2D, GlobalAveragePooling2D, Dropout
from tensorflow.keras.applications.xception import Xception
from tensorflow.keras.optimizers import Adam
from sklearn.metrics import classification_report, confusion_matrix
```

我们还需要定义一些常量和设置:

```
pd.options.display.max_colwidth = 100
seed(42)
random.seed(42)
os.environ['PYTHONHASHSEED'] = str(42)
os.environ['TF_DETERMINISTIC_OPS'] = '1'
set_seed(42)
warnings.filterwarnings('ignore')IMG_SIZE = 150
SEED = 42
```

从 Kaggle 下载数据集后，我将它上传到我的 Google Drive，这样我就可以从 Google Colab 访问文件，而无需在每次开始新会话时上传数据集。为了从所有目录导入图像文件，我使用了以下代码:

```
main_path = "/content/drive/MyDrive/ic_project"train_path = os.path.join(main_path,"train")train_buildings = glob.glob(train_path+"/buildings/*.jpg")
train_forest = glob.glob(train_path+"/forest/*.jpg")
train_glacier = glob.glob(train_path+"/glacier/*.jpg")
train_mountain = glob.glob(train_path+"/mountain/*.jpg")
train_sea = glob.glob(train_path+"/sea/*.jpg")
train_street = glob.glob(train_path+"/street/*.jpg")
```

然后，我们将把来自不同目录的所有图片放在一个列表中。事实上，列表、测试和训练数据帧。

```
#Train list:train_list = [x for x in train_buildings]
train_list.extend([x for x in train_forest])
train_list.extend([x for x in train_glacier])
train_list.extend([x for x in train_mountain])
train_list.extend([x for x in train_sea])
train_list.extend([x for x in train_street])df_train = pd.DataFrame(np.concatenate([
                       ['0']*len(train_buildings),
                       ['1']*len(train_forest),
                       ['2']*len(train_glacier),
                       ['3']*len(train_mountain),
                       ['4']*len(train_sea),
                       ['5']*len(train_street)]),
                  columns = ['label'])df_train['image'] = [x for x in train_list]
```

您可以检查获得的列表:

```
df_train
```

![](img/7fc398879f75b34b532311fbace68b92.png)

在图像中可以看到，我们的列车数据帧中有 6737 幅图像。我们还有从 0 到 5 的 6 个编码类别。第一列是图像标签，第二列是图像路径。

我们还可以检查图像在六个类别中是如何分布的，以及是否有任何类别(或多个类别)未被充分代表。

```
sns.countplot(df_train['label'])
plt.title('Category distribution')
plt.xlabel('Categories')
plt.ylabel('Counts of Observations');
```

![](img/5060c94c8b0ce1b5b11a4bbabeaa9cad.png)

目测之后，可以看到数据集中的所有类别都是平衡的。因此，现在应该导入所有图像，并将它们的数据转换成适合进入模型的格式，即 NumPy 数组。我们将图像从数据框“导入”到一个张量(或 NumPy 数组)，然后将标签导入到另一个张量。首先，我们将创建 images 变量:

```
path = '/content/drive/MyDrive/ic_project/train'#List of image:
img_list = list(df_train['image'])
data_img = []for each in img_list:
               #Each image path:
               each_path = os.path.join(path, each)
               #Read each image:
               each_img = cv2.imread(each_path)
               #OpenCv default color is BGR. Convert it to RGB:
               each_img = cv2.cvtColor(each_img, cv2.COLOR_BGR2RGB)
               #Resize the images:
               each_img_resized = cv2.resize(each_img, (128,128))
               #Save arrays to a list:
               data_img.append(each_img_resized)# Converting list to numpy array
X = np.array(data_img)
```

我必须告诉你这一步很费时间。我用 CPU 花了 39 分钟完成这个代码片段的执行，用 TPU 花了 14 分钟。出于这个原因，并且因为训练数据集足够大，所以我将只使用训练数据集，并且在下一步中我将把它分成测试和验证子集。如果您愿意，您也可以导入和转换测试图像，只需使用相同的代码，并将“train”改为“test”。要确认阵列的形状:

```
print('Shape of X: ', X.shape)
```

![](img/f6555c6bfdf899337172c1d7a2026cc6.png)

我们的数组有 6737 个图像，大小为 128x128，采用 RGB 配色方案。如果你不知道它的确切含义，你可以找到我的另一篇文章，在那里我解释了张量数据结构并解释了这些值。

要创建带标签的张量:

```
y = OneHotEncoder(dtype='int8', sparse=False).fit_transform(df_train['label'].values.reshape(-1,1))
```

我们可以再次检查格式:

```
print('Shape of y: ', y.shape)
```

![](img/8f56cfe59d36a25f769918694b3a7fc7.png)

我们有 6737 张图片，分为六类。我们可以从我们的数据和它们的标签中看到一些随机图像:

```
indices = np.random.randint(0,6737,8)
i = 1
plt.figure(figsize=(14,7))
for each in indices:
    plt.subplot(2,4,i)
    plt.imshow(X[each])
    plt.title(df_train['label'].loc[each])
    plt.xticks([])
    plt.yticks([])
    i += 1
```

![](img/0b0fc5a2df2e6e4b7fafc572f93653fa.png)

快好了！再走两步。第一步是数据分割(正如我在本文前面所解释的)。我们仍然需要测试和验证数据，因此我们将拆分训练数据。

```
X_data, X_test, y_data, y_test = train_test_split(X, y, test_size=0.15, random_state=42)X_train, X_val, y_train, y_val = train_test_split(X_data, y_data, test_size=0.2, random_state=42)print('X_train shape: ', X_train.shape)
print('y_train shape: ', y_train.shape)
print('X_val shape  : ', X_val.shape)
print('y_val shape  : ', y_val.shape)
print('X_test shape : ', X_test.shape)
print('y_test shape : ', y_test.shape)
```

![](img/8d8b49ae16e98eb3e3c3aa117007976b.png)

这里我们有六个 NumPy 数组。

另一个技巧是，如果数据集不够大，可以通过对图像应用随机变换来增加数据集，如旋转、放大和一些扭曲。这只对小数据集是必要的，但我将向您展示如何做:

```
train_gen = ImageDataGenerator(horizontal_flip=True,
                               rotation_range = 45,
                               zoom_range=0.2,
                               height_shift_range = 0.5,
                               width_shift_range = 0.5)validation_gen = ImageDataGenerator(horizontal_flip=True,
                                    rotation_range = 45,
                                    zoom_range=0.2,
                                    height_shift_range = 0.5,
                                    width_shift_range = 0.5)train_gen.fit(X_train)
validation_gen.fit(X_val)
```

我们到此为止。

准备好使用 Xception 构建我们的第一个图像分类项目吧！

# **异常**

我们将尝试的第一个预训练模型是[exception](https://keras.io/api/applications/)。这个模型在精确性方面是第一位的，但是如果你需要最大化性能，它不是最好的。它是由 Google 开发的，其特点是有入口流、中间流和出口流。

![](img/9ad11f792dd4824c0eb6562591a39f18.png)

例外模型架构。

该模型有各种参数，但是，我们不需要设置它们。在下图中可以看到异常模型的所有参数列表:

![](img/5fc85e2b6f832282d02fb66685b96576.png)

为了构建我们的模型，我们首先定义我们的批次和时期大小:

```
#Note that you can decrease batch size and increase number of epochs if you want to maximise your model accuracy:batch_size = 64
epochs = 10
```

现在我们定义例外，我们的预训练模型:

```
base = Xception(include_top=False, 
                weights='imagenet', 
                input_shape=(128,128,3))x = base.output
x = GlobalAveragePooling2D()(x)
```

我们还定义了模型的入口(或头部),并将底部和头部结合起来:

```
#We use 6, because we have 6 categories:
head = Dense(6, activation='softmax')(x)model = Model(inputs=base.input, outputs=head)
```

我们使用以下参数编译模型(注意，您可以在函数中使用更多参数，只需在此处勾选):

```
model.compile(optimizer=Adam(lr=0.0001),
              loss = 'categorical_crossentropy',
              metrics=['accuracy'], run_eagerly=True)
```

如果您想要查看模型概要，或者甚至绘制一个模型模式，您可以使用下面介绍的函数。

```
model.summary()
```

![](img/29e282e09d97d37d7e2d05e35ce483c5.png)

….

![](img/7fd16b7e34f27acf25f056aa07d53169.png)

```
tf.keras.utils.plot_model(
            model,
            to_file="model.png",
            show_shapes=False,
            show_dtype=False,
            show_layer_names=True,
            rankdir="TB",
            expand_nested=False,
            dpi=96,
            layer_range=None,
)
```

![](img/3f3b9826dc28dfb5b64d32234d903c3f.png)

最后，是时候适应我们的模型了，这意味着，指导机器学习！

```
history = model.fit_generator(
               train_gen.flow(X_train, y_train,
               batch_size=batch_size),
               epochs = epochs,
               validation_data = validation_gen.flow(X_val, y_val)
)
```

![](img/890bd1c4f0e6c50aa65568382bcdc629.png)

让我告诉你，这个模型，因为它是工程，将需要大约 4 小时来完成免费的谷歌 Colab 帐户。增加批处理大小可能会因为内存不足而导致会话崩溃。增加历元数会使模型花费更长时间。

完成后，我们可以用图形分析结果:

```
history_df = pd.DataFrame(history.history)plt.figure(figsize=(12,4))
plt.subplot(1,2,1)
plt.plot(history_df['loss'], label='training loss')
plt.plot(history_df['val_loss'], label='validation loss')
plt.title('Model Loss Function')
plt.legend()
plt.subplot(1,2,2)
plt.plot(history_df['accuracy'], label='training accuracy')
plt.plot(history_df['val_accuracy'], label='validation accuracy')
plt.title('Model Accuracy')
plt.legend();
```

![](img/849a9311eb09fd1a8b3620d993ca1437.png)

正如我们所看到的，结果不是很好，但对于 10 个时期的模型来说，对 6 个类别进行分类是相当好的。我们还可以构建一个混淆矩阵，检查我们的模型在哪里失败，在哪里表现良好:

```
# Predicting labels from X_test data
y_pred = model.predict(X_test)# Converting prediction classes from one hot encoding to list
# Argmax returns the position of the largest value
y_pred_classes = np.argmax(y_pred, axis = 1)# Convert test labels from one hot encoding to list
y_test_classes = np.argmax(y_test, axis = 1)# Create the confusion matrix
confmx = confusion_matrix(y_test_classes, y_pred_classes)
f, ax = plt.subplots(figsize = (8,8))
sns.heatmap(confmx, annot=True, fmt='.1f', ax = ax)
plt.xlabel('Predicted Labels')
plt.ylabel('True Labels')
plt.title('Confusion Matrix')
plt.show();
```

![](img/f65c4a9ec8a6ead3160195cfd775c9b2.png)

现在我们知道，我们的模型在识别海洋方面存在问题，通常会将海洋图像归类为冰川。所有其他类别在性能方面似乎都很平衡。但是我们可以仔细观察并打印模型分数:

```
print(classification_report(y_test_classes, y_pred_classes))
```

![](img/0ecd40ab462f93e6f6e3c24d1021930f.png)

正如我们所见，海洋和冰川图像的精度较低。

最后，我们可以评估我们的模型是欠拟合还是过拟合。如果欠拟合，那么如果我们将我们的模型应用于测试图像，我们将具有比在测试图像的训练中获得的更高的准确度。如果过度配合，我们将观察对手。如果我们的验证数据与测试数据有相似的结果，我们可以验证模型的准确性。

```
test_loss = model.evaluate(X_test, y_test)
```

![](img/c05ee478e0fab170c030ccbfe2f060a5.png)

一旦在这里获得的精度高于在训练阶段获得的精度，我们的模型就稍显不足。

```
test_loss = model.evaluate(X_val, y_val)
```

![](img/97b364a914bcb71d347d76eab63575d0.png)

当将模型应用于验证数据时，我们可以以大约 74%的准确度来验证我们的模型。

我希望你喜欢这个笔记本，如果你想让我写更多的东西，请告诉我。在我的下一篇文章中，我将讨论并实现另一个模型，并解释 Keras 的另一个函数。

**如果:**你喜欢这篇文章，别忘了关注我，这样你就能收到关于新出版物的所有更新。

如果你想了解更多，你可以通过[我的推荐链接](https://cdanielaam.medium.com/membership)订阅媒体会员。它不会花你更多的钱，但会支付我一杯咖啡。

**其他:**谢谢！