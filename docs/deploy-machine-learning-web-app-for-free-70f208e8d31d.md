# 免费部署机器学习网络应用

> 原文：<https://pub.towardsai.net/deploy-machine-learning-web-app-for-free-70f208e8d31d?source=collection_archive---------6----------------------->

## [机器学习](https://towardsai.net/p/category/machine-learning)，[编程](https://towardsai.net/p/category/programming)

## 在本教程中，我将解释如何在 Heroku cloud 上部署任何 Python web app。

![](img/9a1f278d3beb7a11547b73cf7780c24b.png)

由[凯文·Ku](https://unsplash.com/@ikukevk?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

由于需要大的内存和强大的计算能力，部署机器学习模型是一项困难的任务。本教程重点介绍一种简单的部署技术，可以用来免费部署任何 Python web 应用程序。

阅读我以前的文章，了解如何构建一个 [**“使用 FastAPI 和 Tensorflow 的图像分类 web 应用程序”**](https://towardsdatascience.com/image-classification-api-with-tensorflow-and-fastapi-fc85dc6d39e8?source=friends_link&sk=3f05ddb711a160fa4e350c150aa74a5d)

> 我还在 YouTube 上创建了一个关于在 Heroku 上部署 Python 应用程序的教程

首先，你需要一个 [**Heroku**](http://heroku.com) id，所以现在就去注册一个免费账号吧。

为了在 Heroku 上部署任何 Python 应用程序，我们需要三个文件——requirements . txt、runtime.txt 和 Procfile。

*   ***requirements . txt***是一个普通的文本文件，包含运行 app 所需的 Python 包。
*   ***runtime.txt*** 是一个文本文件，将包含您希望应用程序运行的 Python 版本。
*   ***Procfile*** 是将包含启动你的 web app 的命令。例如，您可以使用

```
# method 1
python application/server/main.py# or uvicorn if you are deploying a uvicorn server
uvicorn application.server.main:app
```

进入你的 Heroku [**仪表盘**](https://dashboard.heroku.com/apps) 然后点击**新建**和**创建一个新应用**

![](img/bd37e76ba5a5c5273eebf0994cd936ab.png)

输入您的**应用名称**并选择离您最近的服务器区域，然后点击**创建应用**

![](img/b8e81ba01b6756a100732ba77ab6d01b.png)

创建应用程序后，您将看到部署方法——Heroku Git、GitHub 和容器注册表。我将使用 GitHub 方法。为此，只需将您的代码库推送到您的 GitHub 帐户，然后连接到 Heroku 上的 GitHub。

![](img/40f062c2239d76edf4db00048ce9f754.png)

然后搜索存储库并将其连接到您的 Heroku 应用程序。

![](img/4f7329e448d8a5d14669a9a07baf9bf8.png)

之后，您会看到一个 deploy 按钮，选择您想要部署的 Git 存储库的分支，然后点击 **deploy** 。

然后 Heroku 会自动开始你的部署🎉🎉部署后，您可以从任何网络浏览器访问您的应用🔥

希望这篇文章能帮助你部署你的 web 应用。如果你有一些反馈或建议，请在评论区告诉我。

> 在 https://twitter.com/aniketmaurya 的推特上关注我
> 
> 订阅我的 **YouTube 频道:【https://www.youtube.com/channel/UCRuFsj94hWecPkuEr4f5Xww **