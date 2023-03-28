# fast.ai 的计算机视觉

> 原文：<https://pub.towardsai.net/computer-vision-with-fast-ai-eea12918438d?source=collection_archive---------1----------------------->

## 建立并向 AI 部署图像分类器|

## 使用 fast.ai 和 Render 构建和部署图像分类器

![](img/8dffcbabe7d763ffa5cd5652b23a5b15.png)

计算机视觉无处不在，它在现实生活中有大量的应用，如物体检测、人脸识别、人脸验证、图像分类等。如果你对学习这些概念感兴趣，但是不知道从哪里开始，那么不要担心，有很多人面临着同样的问题。在这篇文章中，我将通过教你如何从头开始构建一个图像分类器来帮你一点忙。

我们将使用 fast.ai，这是一个构建在 PyTorch 之上的库。Fast.ai 有许多方便的功能，通过显著减少代码行使我们的生活变得更容易。

> 唯一的先决条件是 Python 的基础知识。

我们将从零开始构建这个计算机视觉应用程序，我所说的零是指我们在开始时什么都没有，没有数据集，没有模型文件，什么都没有。我不希望你使用相同的蹩脚的狗，猫数据集来建立一个图像分类器，相反，我希望你建立一些原创的东西。

这个项目的完整代码可以在 [GitHub](https://github.com/Dhairya10/cars-classifier) 上找到。

# 目录

*   数据收集
*   构建图像分类器
*   部署模型

# 数据收集

正如我在介绍中所说，我们不会使用相同的旧猫，狗数据集，所以现在的问题是，我们将使用哪个数据集，嗯，猜猜是什么，我不会回答这个问题，而是你必须自己找出答案。我的意思是，你应该从头开始建立你的数据集，而不是从 Kaggle 或 UCI 或任何其他来源下载。

这背后的基本原理是，如果你正在创造对你真正重要的东西，而不是对狗和猫进行分类，你将更有动力完成这个项目。我给你举几个例子，帮你入门。

我喜欢汽车，因此我刚刚从谷歌上下载了 500 张特斯拉、宝马、奔驰、丰田和福特汽车的图片。(我将在本文后面解释如何创建数据集)

你也可以这样做，只是寻找一些让你兴奋的事情。如果你是一个口袋妖怪粉丝，下载各种口袋妖怪的图像并建立一个分类器，如果你是一个 GOT 粉丝(或至少在第八季之前)，然后下载各种 GOT 角色的图像并围绕它建立一个图像分类器，重点是你应该寻找一些让你兴奋的东西，因为它将为你提供内在的动力来完成这个项目，甚至超越和学习新的东西。

## 如何构建数据集

动力够了，现在来看编码部分。从头开始构建数据集实际上非常容易。我们将逐步完成数据收集过程。

第一步——在谷歌图片中输入你的搜索查询。尽量具体，因为这样会得到更好的搜索结果。例如，在搜索汽车时，我输入“特斯拉汽车”，而不是只输入特斯拉，因为只输入特斯拉可能会导致模糊的搜索结果。所以尽量具体一点。向下滚动，直到看到“显示更多结果”。

步骤 2 —在浏览器中键入一些 javascript 代码来下载文件。在 Windows/Linux 上按 CTRL + SHIFT + J，或者在 Mac 上按 COMMAND + OPTION + J。将出现一个 javascript 控制台，在该控制台中键入以下代码。

> 注意—在运行此代码片段之前禁用 AdBlock

```
urls = Array.from(document.querySelectorAll('.rg_di.rg_meta')).
map(el**=>**JSON.parse(el.textContent).ou);
window.open('data:text/csv;charset=utf-8,' **+** escape(urls.join('\n')));
```

它将生成一个包含所有 URL 的 downloads.csv 文件。

步骤 3 —使用以下代码片段下载图像。

```
**## Define your classes as a list**
classes = ['Tesla' , 'Mercedes' ,  'BMW' , 'Toyota' , 'Ford']for folder in classes:
    file = 'download_' + folder + '.csv'
    path = Path('data/cars')
    dest = path/folder
    dest.mkdir(parents = True, exist_ok = True)
    download_images(path/file, dest, max_pics = 500)
```

项目结构如下—

```
|-- data
  |-- cars
    |-- Tesla
    |-- Mercedes
    |-- BMW
    |-- Toyota
    |-- Ford
    |-- download_Tesla.csv
    |-- download_Mercedes.csv
    |-- download_BMW.csv
    |-- download_Toyota.csv
    |-- download_Ford.csv
```

> 注意—如果您选择不同的数据集，项目结构会有所不同，但是我建议您遵循存储文件的分层结构。

# 构建图像分类器

收集完所需的数据后，我们现在将重点放在构建分类器上。第一步是从我们的数据集中删除损坏的图像。Google 只显示一些损坏的无法打开的图片，为了保持数据集的完整性，有必要删除这些图片。

```
**## Deleting corrupted images**
for c in classes:
    print(c)
    verify_images(path/c, delete = True, max_size = 500)
```

verify_images 函数将检查每一个图像，因为我们已经设置 delete = True 因此，它会删除损坏或无法打开的图像。是 fast.ai 库提供的内置函数。

我将逐行解释代码的其余部分。

```
**## Viewing the dataset**
np.random.seed(10)data = ImageDataBunch.from_folder(path,train='.',valid_pct=0.2, ds_tfms = get_transforms() , size = 224, num_workers = 4).normalize(imagenet_stats)data.classes 
data.show_batch(rows = 3 ,figsize = (7,8)) **## Training**
learn = cnn_learner(data,models.resnet34, metrics = error_rate)
learn.fit_one_cycle(50)**## Saving our model**
learn.save('stage-1')**## Unfreezing our model**
learn.unfreeze()**## Finding the best learning rate and training the model again**
learn.lr_find()
learn.recorder.plot()
learn.fit_one_cycle(10, max_lr=slice(1e-6,1e-4))**## Saving and loading the updated model**
learn.save('stage-2')
learn.load('stage-2');**## Evaluation**
interp = ClassificationInterpretation.from_learner(learn)
interp.plot_confusion_matrix()
interp.most_confused(min_val=2)**## Exporting the model** 
learn.export()
```

## 查看数据集

为了查看我们的数据集，我们需要首先创建一个 **ImageDataBunch** 。如果你曾经从 Kaggle 或任何其他网站下载过数据集，那么你可能会注意到数据集包含像 train、test 等文件夹。但是在我们的例子中，我们只是从 Google 下载了这些图片，因此我们没有任何子目录。由于我们没有任何 train 文件夹，所以我们已经通过了“.”对于训练参数，这意味着将当前目录视为训练目录，valid_pct = 0.2 意味着将保留 20%的数据用于验证。

我们在上面一行中使用 **np.random.seed(10)** 的原因是为了确保我们总是获得相同的验证集，因为每次运行单元时获得不同的验证集会导致问题，如果我们的验证集不断变化，我们可能无法正确调整超参数。

## 培养

训练过程非常简单，我们只需要创建我们的学习者对象，在本例中，我们使用的是 cnn_learner。我们将传入 ImageDataBunch 对象以及我们想要使用的模型和用于评估的度量。这里需要注意的关键是，我们使用的是预先训练的 resnet34 模型，因为从头开始训练模型非常耗时。这个使用已经训练好的模型的过程叫做**迁移学习**。

## 保存我们的模型

我们将使用保存功能来保存我们的模型。通过保存我们的模型，我们将确保我们的模型在训练过程中学习的所有权重和参数都被正确保存，以便我们可以在将来使用它们，而不是再次训练模型。

## 解冻我们的模型

这是一个有点棘手的概念。如果你熟悉 CNN 的基本结构，那么你一定知道它包含许多层，因为我们在这里使用迁移学习；因此，我们所做的只是在最后添加了一些额外的层，并且只训练这些层，而不是训练整个模型。

这种方法听起来可能令人惊讶，但当我们试图对汽车、猫、狗等普通图像进行分类时，它相当有效。通过使用 unfreeze 函数，我们现在可以训练整个模型，而不仅仅是训练最后几层。

## 寻找最佳的学习速度

现在我们已经决定训练整个模型，我们需要找到最佳的学习率来训练我们的模型。解冻模型后我们面临的主要问题是，如果我们只是解冻模型，然后再次训练它，那么我们将获得更高的错误率。错误率较高的主要原因是所有的层将使用相同的学习率来训练，这不是最好的方法。我们在这里做的是提供一个学习率范围，即 1e-6 到 1e-4。第一层将用学习率 1e-6 来训练，最后一层用 1e-4 来训练，其余层的学习率将在这两个值之间。

## 估价

我们将在从一开始就保持分离的验证数据集上评估我们的模型。我们将使用混淆矩阵来检查我们的结果。

我们还使用了一个特殊的函数 most_confused()来检查最常见的不匹配类。

## 导出模型

导出函数将生成一个. pkl 文件，我们将使用它来使用 Render 部署模型。

# 部署模型

我们将使用渲染来部署这个模型。您只需要分叉[这个](https://github.com/render-examples/fastai-v3)库，并根据您的项目进行必要的更改。完整的安装指南可在[这里](https://course.fast.ai/deployment_render.html#create-a-render-account)找到。

[](https://course.fast.ai/deployment_render.html#create-a-render-account) [## 在 Render | fast.ai 课程 v3 上部署

### 如果你只是想在 Render 上测试初始部署，starter repo 设置为使用 Jeremy 的 bear 分类…

course.fast.ai](https://course.fast.ai/deployment_render.html#create-a-render-account) 

# 进一步的学习资源

我强烈建议你去看看 fast.ai 深度学习课程。

[](https://course.fast.ai/index.html) [## 程序员实用深度学习，v3 | fast.ai 课程 v3

### 要完成本课程中的几乎所有内容，您需要使用一台配有 NVIDIA GPU 的计算机(不幸的是，其他品牌…

course.fast.ai](https://course.fast.ai/index.html) 

如果你想学习更多关于 CNN 的知识，我会建议你选修吴恩达的这门课。

[](https://www.coursera.org/learn/convolutional-neural-networks/home/welcome) [## Coursera |顶尖大学的在线课程。免费加入

### 斯坦福和耶鲁等学校的 1000 多门课程——无需申请。培养数据科学方面的职业技能…

www.coursera.org](https://www.coursera.org/learn/convolutional-neural-networks/home/welcome) 

> 你可以在这里找到这个项目的完整代码。

这就把我们带到了本文的结尾。非常感谢你的阅读。

我的[推特](https://twitter.com/DhairyaKumar16)和 [LinkedIn](https://www.linkedin.com/in/dhairya-kumar-873a9615b/) 。