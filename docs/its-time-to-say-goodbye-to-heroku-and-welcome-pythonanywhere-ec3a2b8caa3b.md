# 是时候告别 Heroku，迎接 PythonAnywhere 了

> 原文：<https://pub.towardsai.net/its-time-to-say-goodbye-to-heroku-and-welcome-pythonanywhere-ec3a2b8caa3b?source=collection_archive---------0----------------------->

## 将您的应用程序迁移到免费云服务的逐步过程。

![](img/0b7eff86e0aaa056bb586fabe2bfaa86.png)

2022 年 11 月 28 日， [Heroku](https://www.heroku.com/) 停止提供免费的产品计划和免费的数据服务，删除不活动的帐户，以及不活动超过一年的帐户的相关存储。

采取这一决定是为了消除在管理他们的免费层服务上的欺诈和滥用方面投入的巨大努力。从利益相关者的角度来看，这是一个好的决定，但对学生来说却不是。很长一段时间，**的学生**将 Heroku 作为他们部署、测试和展示他们喜爱的项目、任务和作品集的首选。

## 所以问题是，他们应该在哪里部署他们的项目，而且是免费的？

顾名思义，这里是 [PythonAnywhere](https://www.pythonanywhere.com/) 。

PythonAnywhere 是 Heroku 的另一个免费替代品，您可以在其中部署 Django、web2py、Flask 和 Bottle 应用程序。唯一的限制是在一个帐户上只能部署一个应用程序。但是我知道我们很多人都可以克服这个问题(创建多个账户)。

在这篇博客中，我将向你展示如何将你的 flask 应用程序从 Heroku 迁移到 PythonAnywhere，只需稍作调整。

# 部署工作流程

![](img/d5490626082d3d8f4b1a7ee0e949b370.png)

我们将使用 VS 代码来开发/修改应用程序代码库， [Github](https://github.com/) 用于版本控制，PythonAnywhere 作为托管服务。

在付费帐户中，您可以通过 SSH 从本地直接将更改推送到 PythonAnywhere。但在这里，我们的重点是有效利用免费服务。

# 我们将部署什么？

我准备了一个样本代码库，展示了世界十大经济体的土地使用情况。该应用程序使用由世界银行提供的开源数据。

![](img/44f7ad979f524843b096ba1f5354cdc6.png)

仪表板上的样本

现在我们已经消耗了足够的行话来继续。让我们开始吧！

# 设置本地

首先，我们将从这个[存储库](https://github.com/rajatsharma369007/flask-dashboard-heroku)中克隆现有的代码库到您的本地。

[](https://github.com/rajatsharma369007/flask-dashboard-heroku) [## GitHub-rajatsharma 369007/flask-dashboard-heroku

### requirements.txt 文件列出了该项目所需的所有 Python 库，可以安装它们…

github.com](https://github.com/rajatsharma369007/flask-dashboard-heroku) 

我这里用的是 [VScode](https://code.visualstudio.com/) ，你可以用任何其他的 IDE。确保使用基于凭据的 URL 来克隆存储库，否则，在推送更改时，您将面临权限问题。这里有一个例子:`git clone [https://username:token@github.com/username/repository.git](https://username:token@github.com/username/repository.git)`

![](img/81708828555d9171b7b080c49ff961ec.png)

# 代码库的变化

*   第一个变化是从目录中删除 [Procfile](https://devcenter.heroku.com/articles/procfile) 文件。

![](img/56fc514cdbd8d2ca0eaceb94363e1a4f.png)

*   将变更暂存、提交并推送到 Github。

![](img/c4867708f0364ffaaade92c306064f80.png)

复习者

现在，是时候将这个更新的代码库克隆到 PythonAnywhere 了。我希望你已经创建了一个初学者帐户。如果没有，那么[点击这里](https://www.pythonanywhere.com/registration/register/beginner/)。这是您的仪表板的外观。

*   点击 **Bash** 来实例化一个 Bash 会话。

![](img/5d3b6fee9ad775f2d5bad8e80f76dd22.png)

*   **克隆**更新后的代码库。

![](img/a9f2fa249091979b42a13623b03062db.png)

*   现在，转到**文件**。您将在主目录中找到所有项目文件夹。

![](img/41da0f2dd2a56d0b0cdbd78a98ce274c.png)

*   工作还没有结束。我们必须**将代码库中任何地方出现的所有** **相对路径更改为绝对路径**。查找所有路径的聪明方法是搜索最初导入的文件夹或文件名。你只需要把`/home/user_name/repository_name/`加到相对路径上。

![](img/d3bf65b07af973f7a9eab5237f5649c2.png)

*   一旦你完成了这些，执行 staging，提交并把修改推送到 GitHub。
*   然后，您必须在 PythonAnywhere 中进行所有的更改，为此，您必须重新访问 bash 并执行`git pull`命令。确保你在正确的目录中(例如，在 **flask-dashboard-heroku** 中)

# 配置环境

我们刚刚按照 PythonAnywhere 部署更新了代码库。现在，我们将配置环境。

*   你必须首先创建一个虚拟环境。使用`mkvirtualenv environment_name`命令创建一个虚拟环境。(默认情况下，环境将被激活。如果这种情况没有发生，那么使用`workon`命令来激活环境)。

![](img/cb80bc2f688ab80c295cb0fc6f5d9e91.png)

*   安装所有需要的**库**。使用`pip install -r requirements.txt`

![](img/4688d413a52189f0a3ab4a92c6fe07d0.png)

*   创建一个新的 web 应用程序。您将在**网页**部分找到该选项。

![](img/e81578bbfcf5bcfeb6728745063f61d4.png)![](img/f26e54f14ba121dcec3c81f3fdc4db3e.png)![](img/3b81fec333cc5535943431f00fd64a28.png)

*   之后，您将被要求提供 flask 应用程序的路径。继续使用默认路径。

![](img/583d1baf7032607db05cbf1a039863da.png)

*   转到**文件**，删除新生成的文件夹(默认为“ **mysite** ”)。

![](img/49a866212322fef9630abb940324f93d.png)

*   接下来，转到**网站**，更改**源代码**路径。

![](img/1f32acceccc53d40fc1085bde2466439.png)![](img/9ee1b0fb9c965cd6bc424d79ce1c3b77.png)

*   然后，打开 WSGI 文件。

![](img/7ce7cfa70b5e7aff40201207547786b5.png)

*   输入正确的**项目路径**和正确的**烧瓶脚本名称**。完成后，点击右上角的**保存**按钮保存更改。

![](img/9e6833681c1af35b02d2f89b3e41ccb3.png)

*   我们的应用程序已经部署。现在，转到 **Web** 部分，并重新加载部署的应用程序。

![](img/5c621bd60e639fe8fb10e8e813e3e405.png)

经过这一切，我们已经免费部署了我们的应用程序，但只有三个月。三个月后，你必须再次**重新加载**申请**以获得下一个三个月的有效期**。

这是我们部署的应用程序。[http://rsharma369007.pythonanywhere.com/](http://rsharma369007.pythonanywhere.com/)

![](img/2732b28cb7ac720f6d68dc1cf1144f5b.png)

如果你想要最终的代码库，那么[点击这里](https://github.com/rajatsharma369007/flask-dashboard-pythonanywhere)。我为此创建了一个单独的存储库。

[](https://github.com/rajatsharma369007/flask-dashboard-pythonanywhere) [## GitHub-rajatsharma 369007/flask-dashboard-python anywhere

### requirements.txt 文件列出了该项目所需的所有 Python 库，可以安装它们…

github.com](https://github.com/rajatsharma369007/flask-dashboard-pythonanywhere) 

# 免费计划的问题

*   您的应用程序可以在 100%的 CPU 利用率下运行 100 秒。别担心，这只是一个软限制。当您达到 100%时，您的进程仍然运行，但是 CPU 功率较低。24 小时后，已利用的 CPU 资源再次重置为零。
*   512 兆字节的文件存储空间。这看起来很多，但是在这个空间内，您还必须安装您的库和包。因此，您必须只安装必要的库，以避免空间不足。
*   每个帐户只能部署一个应用程序。
*   每隔三个月，你必须再次重新加载申请，以获得下一个三个月的有效期，否则你的申请将被遣散。

# 接下来呢？

*   我正在考虑在基于 Raspberry Pi 的本地基础设施上部署应用程序。这将是学生远程测试和部署几个数据科学和机器学习项目的一次性投资。
*   除此之外，接下来我将在 PythonAnywhere 上部署一个小规模的 NLP 应用程序。我想看看它的局限性。

敬请关注下一篇博客…

![](img/b36d84295dda7f60e06754e8d7a4ccd8.png)

[吉菲](https://medium.com/u/89e606173af3?source=post_page-----ec3a2b8caa3b--------------------------------)