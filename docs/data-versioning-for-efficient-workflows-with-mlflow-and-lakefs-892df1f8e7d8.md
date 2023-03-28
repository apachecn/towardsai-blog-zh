# 使用 MLFlow 和 LakeFS 实现高效工作流的数据版本控制

> 原文：<https://pub.towardsai.net/data-versioning-for-efficient-workflows-with-mlflow-and-lakefs-892df1f8e7d8?source=collection_archive---------1----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)，[软件工程](https://towardsai.net/p/category/software-engineering)

## 构建弹性、原子和版本化的数据湖操作

![](img/821a565bca001193a495f59ca6aff2a4.png)

照片由[汉尼斯·艾格勒](https://unsplash.com/@egla)在 [Unsplash](https://unsplash.com/photos/nT4k2JDtwTQ) 上拍摄

## 介绍

版本控制系统，比如 Git，是对源代码进行版本控制和归档的重要工具。版本控制帮助您跟踪代码中的更改。当进行更改时，也可能引入错误，但是使用源代码控制工具，开发人员可以回滚到工作状态，并将其与非工作代码进行比较。这最大限度地减少了对可能正在处理代码的其他团队成员的干扰，并帮助他们有效地协作。

> 除了代码，数据也会改变。

通常，数据科学家需要访问一系列数据集来完成特定任务。从特征工程到模型训练或选择和超参数优化，数据也会得到处理和改变。除此之外，实验和结果观察也是数据科学家日常工作中的一项普遍任务，这意味着他们需要来回切换特定的数据格式或版本。可以想象，这使得整个过程既耗时又容易出错。

在本文中，我们将探索***lakeFS***——一个帮助团队**像管理代码**一样管理数据的强大工具。我们将讨论它如何处理数据版本，以及它如何潜在地帮助数据团队构建更高效的工作流，并且更不容易出错。此外，我们将看到它如何与`[mlflow](https://mlflow.org)`一起使用，以建立一个工作流，对数据和经过训练的机器学习模型进行版本化。

## 什么是 lakeFS

![](img/378aed7b1df01c9fb20d61b59321ab81.png)

LakeFS 是一个开源平台，提供了一个类似 Git 的模型来帮助团队版本化和管理数据。从复杂的 ETL 任务到数据科学和分析，LakeFS 为您的数据湖提供了弹性、原子性和可管理性。它可以与所有现代数据框架无缝协作，如 Apache Kafka、Apache Spark 等。同时，它还支持最广泛使用的云存储，如 AWS S3、谷歌云存储和 Azure Blob 存储。

使用 lakeFS，您可以为数据创建一个**开发环境**,就像您为源代码所做的一样。这样的环境将帮助您在不会影响您的生产环境的[数据湖](https://lakefs.io/data-lakes/)的隔离快照中试验工具和代码更改。得益于其分支和提交模型，lakeFS 为您提供了在任何时候回滚到数据湖本身的特定版本所需的所有工具。

此外，该平台允许您通过实施模式兼容性、格式实施和命名约定等最佳实践的机制来构建防弹的**连续数据集成和部署**工作流。您甚至可以配置您的工作流，将数据接收到非生产分支，以便防止重大更改进入您的生产环境，从而最大限度地减少中断。

在本文接下来的部分中，我们将探讨如何在数据版本化的上下文中使用 lakeFS。我们将展示如何在一瞬间启动并运行它，并使用它来构建易于管理且高效的数据工作流。

## LakeFS 入门

首先，让我们从使用 Docker Compose 运行 lakeFS 的本地实例开始。如果您的机器上没有安装 Docker 和 Docker Compose，请确保按照 Docker 文档中的[官方指南进行安装。确保合成版本为 1.25.04 或更高版本也很重要。](https://docs.docker.com/get-docker/)

一旦您确认 Docker 已经成功安装在您的机器上，您就可以打开您的终端并运行下面的命令来启动 lakeFS 实例。

```
curl https://compose.lakefs.io | docker-compose -f - up
```

如果一切按计划进行，您现在应该会看到类似于下面所示的输出。

![](img/d9f1cd86e2ae527368d15e59d21c6b51.png)

跑步湖

现在，让我们通过在您首选的 web 浏览器中打开[http://127 . 0 . 0 . 1:8000/setup](http://127.0.0.1:8000/setup)来检查我们的安装。如果安装成功，您应该能够看到初始设置页面，要求您输入管理员用户名。

![](img/8fe136c553ceb09eff758f7deaf33127.png)

LakeFS 初始设置页面

添加您的首选用户名，然后单击设置。在下一页，您将获得身份验证凭据—访问密钥 ID 和秘密访问密钥。请确保将它们安全地存放在某个地方，因为一路上你会用到它们。现在转到登录屏幕，使用上一步生成的凭证登录。如果凭据正确，通常会显示以下屏幕:

![](img/ef0fa31eb5ace4b76bfe26fa33af512b.png)

LakeFS 主页

在此页面上，您将能够看到您的数据存储库和访问管理实用程序(如访问控制),并与之进行交互。

`lakeFS`还自带名为`**lakectl**`的原生命令行界面(CLI)。CLI 可用于 Linux、OSX 和 Windows，并作为一个没有外部依赖性的二进制文件分发。

为了下载并安装`lakectl`,只需遵循以下步骤:

1.  访问 `[lakeFS](https://docs.lakefs.io/downloads.html)` [文档](https://docs.lakefs.io/downloads.html)中的[下载部分](https://docs.lakefs.io/downloads.html)
2.  点击“二进制版本”
3.  上一步将引导您到 lakeFS GitHub 存储库上的发布——向下滚动到“Assets”部分

![](img/be942cea2b6a1dc0f595dfdea509ba15.png)

GitHub 上的 LakeFS 二进制文件

4.点击下载符合您机器规格的`.tar.gz`文件

5.现在提取下载的`tar.gz`的内容。举个例子，

```
tar -xzvf lakeFS_0.40.0_Darwin_x86_64.tar.gz
```

上面的命令应该提取 3 个文件:`README.md`、`lakefs`和`lakectl`。

6.将`lakectl`移到`PATH`中—这取决于操作系统，对于*nix 系统，这通常是`/usr/local/bin`:

```
mv lakectl /usr/local/bin
```

您可以通过运行 help 命令来确保一切正常。

```
$ lakectl -h 
```

如果一切按计划进行，您现在应该能够检查上述命令的输出，并了解如何使用`lakeFS` CLI。

**OSX 注意:**如果由于任何原因操作系统不允许你运行`lakectl`因为开发者不被认可，你可能需要运行`sudo spctl --master-disable`。

7.一旦您确认安装了`lakectl`，现在您需要配置 CLI 以使用您之前创建的凭证。为此，只需运行

```
$ lakectl config
```

并填写访问密钥 ID、秘密访问密钥和服务器端点 URL。

```
192:lakefs-demo gmyrianthous$ lakectl config
Config file /Users/gmyrianthous/.lakectl.yaml will be used
Access key ID: AKIAJKTJORSSALEG7RQQ
Secret access key: **************************
Server endpoint URL: http://127.0.0.1:8000
```

最后，让我们通过运行一个示例命令来验证配置:

```
$ lakectl branch list lakefs://example
+--------+-----------+
| BRANCH | COMMIT ID |
+--------+-----------+
+--------+-----------+
```

如果您在输出中看不到分支，请不要担心——这是我们所期望的，因为我们还没有创建任何分支。

## 使用 LakeFS 进行数据版本控制

现在我们已经启动并运行了 LakeFS，还安装了它的本机 CLI，是时候演示如何使用它来版本化特定的数据集了。

显然，我们首先需要创建一个存储库，在那里我们将能够存储和版本化我们的数据。为此，只需返回到`lakeFS`用户界面，点击“存储库”选项卡，然后点击“创建存储库”。您可以为您的存储库 id 选择一个任意的名称，但是如果您在本地机器上运行 lakeFS，请确保使用普通的`local://`存储名称空间。最后点击“创建存储库”。

![](img/febcdc7490ee2d7b405828a2904f6548.png)

创建我们的第一个 LakeFS 存储库

现在，您应该会被重定向到新创建的存储库。

![](img/94dba9886d1206ab1bec4b0ace9572ad.png)

现在我们已经创建了我们的存储库，是时候进行我们的第一次提交了。出于演示的目的，我计划使用 [UCI 虹膜数据集](https://archive.ics.uci.edu/ml/datasets/iris)。让我们回到终端，将初始数据集上传到我们新创建的存储库的主分支。为此，我们需要做的就是运行`[lakectl fs upload](https://docs.lakefs.io/reference/commands.html#lakectl-fs-upload)`命令:

```
lakectl fs upload -s iris.data lakefs://lakefs-demo/master/iris.data
```

答案应该是:

```
Path: iris.data
Modified Time: 2021-04-20 18:40:23 +0100 BST
Size: 3151 bytes
Human Size: 3.2 kB
Physical Address: local://daad0433311a48d3a02c87bd4fcbbe44
Checksum: 749c76812c8c96999282e757b344d473
```

最后，让我们提交刚才所做的更改。如果您想观察将要提交的更改，只需运行`lakectl diff repo-uri`:

```
$ lakectl diff lakefs://lakefs-demo/masterRef: lakefs://lakefs-demo/master
+ added iris.data
```

现在，您可以使用

```
$ lakectl commit lakefs://lakefs-demo/master \
  --message "Initial dataset"
```

这通常会返回一个成功的响应，如下所示:

```
Branch: lakefs://lakefs-demo/master
Commit for branch "master" completed.
ID: de34534cde4cfed0b333dfd977da551de6c0b97cfacb6e35a7833baa4e22c6b6
Message: Initial dataset
Timestamp: 2021-04-21 09:55:32 +0100 BST
Parents: c7b2e167d9c807e5f4d1995de4a659ff40f8994926aad675fe967a19ef0
```

现在，您可以通过用户界面验证初始数据是否已添加到我们的主分支中。

![](img/6b772ef5eba07718a0e816d083432c95.png)

lakefs 仓库主分支中的数据文件

既然我们已经将初始数据集添加到了我们的`lakeFS`存储库的主分支中，那么是时候展示如何创建其他特性或开发分支，并独立地处理它们了。

为此，我们需要运行命令`lakectl branch create`并提供新的目标分支和源分支。我们将调用新分支`feature-branch`并从`master`分支中创建它。

```
lakectl branch create lakefs://lakefs-demo/feature-branch --source lakefs://lakefs-demo/master
```

现在，新的分支也应该在用户界面上可见，如下所示。请注意，您也可以直接从 UI 创建分支。

![](img/5a8953fc6555b708e6f14da536d27d47.png)

LakeFS 存储库中的分支列表

为了这个例子，我们将应用一个非常基本的变换。下面提供的代码片段只是将数据集的第一列乘以标量`-1`:

既然已经修改了`iris.data`文件，我们可以将更新后的文件上传到我们在上一步中创建的分支中，名为`feature-branch`:

```
lakectl fs upload -s iris.data lakefs://lakefs-demo/feature-branch/iris.dataPath: iris.data
Modified Time: 2021-04-21 14:24:14 +0100 BST
Size: 3250 bytes
Human Size: 3.2 kB
Physical Address: local://fed67112d77f483798f441307c05ab36
Checksum: ca0adaa9d6b38a9901442a0432f4c8eb
```

最后，我们提交变更:

```
$ lakectl commit lakefs://lakefs-demo/feature-branch --message "Transformed the first column"Branch: lakefs://lakefs-demo/feature-branch
Commit for branch "feature-branch" completed.
ID: b9879d3219c4e39ac08613ed94d234cd86478af133464c76ae8e8de7b8f46770
Message: Transformed the first column
Timestamp: 2021-04-21 14:26:54 +0100 BST
Parents: de34534cde4cfed0b333dfd977da551de6c0b97cfacb6e35a7833baa4e2
```

我们还可以使用`lakectl diff`命令来观察`master`和`feature-branch`分支之间的区别。

```
lakectl diff lakefs://lakefs-demo/feature-branch lakefs://lakefs-demo/masterLeft ref: lakefs://lakefs-demo/feature-branch
Right ref: lakefs://lakefs-demo/master
~ modified iris.data
```

最后，一旦我们对这些变化感到满意，我们就可以将`feature-branch`合并成`master`:

```
lakectl merge lakefs://lakefs-demo/feature-branch  lakefs://lakefs-demo/masterSource: lakefs://lakefs-demo/feature-branch
Destination: lakefs://lakefs-demo/master
Merged "feature-branch" into "master" to get "5cde9f05823aaf3b0481011e4a143477cf767df7f2ac87ecf164b1a2d593f485".
Added: 0
Changed: 1
Removed: 0
```

更改现在在`master`分支上，提交也应该在`lakeFS`用户界面的“提交”选项卡下可见。

![](img/710fab68dc6bed7d7ccba141eadbe96b.png)

将特征分支合并到主分支

在这个快速演示中，我们展示了如何使用`lakeFS`来管理和版本化数据，就像处理源代码一样。您可以创建开发环境，在这里您可以围绕数据本身构建工具和转换，并最终将转换后的数据合并回主分支。

如果出现任何问题，您可以使用`lakectl` CLI 或`lakeFS` UI 来观察各个分支之间的差异。此外，如果需要，该平台允许您回滚到以前的版本。

## 使用 LakeFS 和 MLFlow 进行模型和数据版本控制

尽管 lakeFS 可以单独使用，但它也可以与其他广泛使用的 MLOps 工具结合使用，以帮助数据团队设计高效的工作流并完成特定任务。

数据科学家通常希望试验各种模型和功能。这意味着他们最终可能会得到一个不同数据集和模型的池，然后对其进行进一步分析。因此，需要将模型和用于训练它们的数据集绑定在一起。

为此，我们可以将`lakeFS`和`mlflow`结合起来负责数据版本控制，而后者将负责模型训练。

MLFlow 附带了一个名为**模型注册中心**的组件，它是一个集中的存储库，用于存储丰富了 API 和用户界面的模型。它可以用于模型版本化和阶段转换(例如，当将模型从开发环境带到生产环境时)。

通常，我们需要执行一些预处理步骤和特征工程，然后用训练数据集训练模型。在本文的剩余部分，我们可以探索如何使用`lakeFS`和`mlflow`来准备数据集和训练模型，同时我们也对结果数据集和训练模型进行版本化。

让我们假设，在第一轮中，我们对我们在前面几节中讨论的初始数据集执行一些预处理和转换步骤。我们现在可以使用`[lakeFS](https://docs.lakefs.io/using/python.html)` [Python API 客户端](https://docs.lakefs.io/using/python.html)来创建一个新的分支，并将我们创建的数据集提交给存储库。为此，我们首先需要使用`pip`安装客户端:

```
$ pip install 'lakefs_client==<lakeFS version>'
```

并使用下面的代码片段创建一个新的分支，该分支将用于跨我们希望执行的实验对数据集进行版本控制。

请注意，在下面的例子中，我们不会将 df 分成测试集和训练集，但是通常情况下，您需要这样做并将两个结果数据文件存储到存储库中。

既然我们已经处理了数据集，现在我们可以继续进行模型训练和版本控制。为此，我们将使用`mlflow`工作流 API 来记录模型并将其版本化到模型存储中:

使用`mlflow.log_param`将`lakefs`存储库名称记录到模型中是很重要的，这样您就可以在加载回模型时推断出这条信息。

在上面的例子中，我们已经看到了如何创建不同版本的建模数据集，这些数据集随后将用于训练模型。使用`lakeFS`和`mlflow`，我们可以将建模数据集和训练模型版本化，并将它们绑定在一起。这样，您可以很容易地推断出与特定模型版本相关联的数据集版本，反之亦然。您可以使用`lakeFS`和`mlflow`的其他组件，比如 [MLFlow Tracking](https://mlflow.org/docs/latest/tracking.html) ，它们有可能帮助您将代码与数据关联起来。

虽然 **MLFlow** 可以帮助你管理机器学习生命周期，包括中央模型注册和部署，但 **lakeFS** 使你能够以类似 Git 的方式控制数据集。结合`mlflow`和`lakeFS`提供的工具，您可以创建高效、自动化的工作流程，促进实验并提高可重复性。

## 最后一句话

数据版本化最近开始受到关注，因为它可以作为现代数据工作流中的一个关键组件。 **LakeFS** 是一个强大的平台，旨在为数据湖提供弹性和可管理性。在本文中，我们展示了如何安装和使用该平台及其本机 CLI `lakectl`。此外，我们探索了如何将`lakeFS`与其他常用的 MLOps 工具(如`mlflow`)一起使用，以执行特定的任务，如数据和模型版本控制。

您可以在[官方文档](https://docs.lakefs.io/)和 [GitHub 资源库](https://github.com/treeverse/lakeFS)中了解更多关于 lakeFS 及其功能的信息。