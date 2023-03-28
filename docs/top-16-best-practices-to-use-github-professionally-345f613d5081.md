# 专业使用 Github 的 16 大最佳实践

> 原文：<https://pub.towardsai.net/top-16-best-practices-to-use-github-professionally-345f613d5081?source=collection_archive---------0----------------------->

## Git 和 Github 之间的 10 个区别，以及 16 个 Github 最佳实践，让您的项目保持安全、有效和专业的维护

![](img/ca67afb8b96b4bc131d86d4a31254485.png)

由 Pexels 的 [RODNAE Productions](https://www.pexels.com/@rodnae-prod/) 制作

Git hub 是一个用于版本控制和协作的代码托管平台。

我将涉及两个方面:(Git 和 Github 之间的十个不同之处，以及(2)Github 的 16 个最佳实践。

# Git 和 Github 的 10 个区别

1.Git 是一个版本控制系统，而 GitHub 是一个基于 web 的托管服务，使用 Git 进行版本控制。

2.使用 Git，开发人员可以在本地管理和跟踪源代码的更改，而 GitHub 创建了一个中央存储库，允许开发人员之间轻松协作。

3.Git 是免费和开源的，而 GitHub 为私有存储库和一些功能支付了费用。

4.Git 使用命令行界面，而 GitHub 有一个 UI 和许多带有图形用户界面的客户端。

5.在 Git 中，每个开发人员都有整个项目历史的完整本地副本，而在 GitHub 中，默认下载项目的最新版本。

6.Git 可以离线使用，而 GitHub 需要互联网连接。

7.在 Git 中，对文件大小和存储库数量没有限制，而 GitHub 根据用户选择的方案施加了某些存储限制。

8.Git 比 GitHub 快，因为它不必为每个操作都与服务器通信。

![](img/634db049ec2e080e2263d79c66b0b3bb.png)

来自 Pexels 的简·kopřiva

# 16 个 Github 最佳实践

1.保持你的代码简洁明了

以干净、一致的风格编写，使你的代码可读性更好。它应该足够简洁，这样你就可以理解正在发生的事情，而不用费力地去读很多不必要的废话。当你的代码易于阅读时，它就更容易维护。当它更容易维护时，人们就更有可能在你的代码中工作(如果你被设置为与其他人共同贡献)。

2.写清楚提交消息

这个看似显而易见，但无论如何还是值得一提。当您将代码提交到您的存储库时，编写清晰、简洁的提交消息，解释什么发生了变化以及原因。这种方法有助于您和您的合作者了解项目历史，在需要时更容易找到具体的变更。

3.不要提交不必要的文件

在提交代码之前，请查看已更改文件的列表，以确保您没有意外地提交您不想提交的内容。在提交之前很容易忘记删除临时文件或生成的文件，但是这样做会使您的存储库变得混乱，并使以后更难找到重要的内容。

![](img/d1d1942694fb98a38e16b144a3f03dbf.png)

由来自 Unsplash 的[蒂姆·周](https://unsplash.com/@timchowstudio)

4.让您的分支保持最新

如果你和其他人一起工作，保持你的分支与主分支的最新变化同步是很重要的。这样，当您提交一个 pull 请求时，将不会有任何合并冲突，并且您的更改将更有可能被接受。当然，您不应该盲目地接受主分支的每一个变更——如果有您不同意的变更，在将它们合并到您自己的分支之前，与您的团队进行讨论。

5.将相关提交分组在一起

如果您对代码库进行了几个相关的更改(例如，添加一个新特性和修复几个错误)，请尝试将这些更改组合到一个提交中。这样，当其他人审查您的代码时，他们可以在一个地方看到所有相关的更改，而不是在提交之间来回跳转。

6.对新特征使用特征分支

如果你正在为你的项目开发一个新的特性，为它创建一个单独的分支，而不是直接在主分支中工作[7]。这样，如果你的特性还没有准备好，你可以把它放在主分支之外，直到它准备好被合并进来。

7.为您的代码编写测试

如果你的项目有一个自动化测试套件[1](它应该有)，确保在提交之前为你的新代码编写测试。这样，您就可以确信您的代码正在做它应该做的事情，并且在合并到主分支时不会破坏任何东西。

![](img/f3bb0ad23de16c1dcc1f4d4ed0643d81.png)

来自 Unsplash 的 JESHOOTS.COM

8.在提交之前，确保您的测试通过

说到测试，在提交代码之前要确保所有的测试都通过了！否则，您可能会在代码库中引入本来可以轻松避免的错误。如果可能的话，设置持续集成，这样无论何时提交代码，测试都会自动运行。

9.遵循风格指南

如果您的项目有一个样式指南，请确保您的新代码在提交之前遵循它。这不仅会使您的代码与项目的其余部分更加一致，而且还会使其他人更容易阅读和理解。风格指南不是草率代码的借口——如果有的话，它应该改进您的代码！

10.使用好的变量名

选择好的变量名[2]是编写可读代码的重要部分。毕竟，如果有人不能理解一个变量应该代表什么，他们就不能理解使用它的代码。所以，花些时间选择描述性的变量名，使你的代码更容易阅读和维护。

11.不要重复不必要的代码

复制代码通常被认为是一个坏主意，因为它会导致错误和不一致。如果你发现自己在项目中复制粘贴代码，后退一步，看看是否有更好的方法来组织事情，这样你就不必复制那么多代码。

![](img/fa42ce8f6b4d67b6c851c572f461e53f.png)

来自 Unsplash 的 Maksym Ivashchenko

12.保持干燥

与上一点相关的是，“不要重复自己”(DRY) [3]是软件开发的一个原则，它指出只要有可能就应该避免重复。有很多方法可以确保你的代码是干巴巴的。例如，探索如何使用函数或模块。

13.不要提交损坏的代码

就像警告一样，破损的代码也告诉你有问题。所以，不要犯！相反，在提交之前修复代码中的任何错误；否则，您将冒着在开发过程中破坏某些东西的风险。

14.标记版本

在您推出软件的新版本后，用版本号标记提交，以便以后更容易地发现它。

15.正确忽略文件

确保将文件添加到您的。gitignore [4]不需要 Git 跟踪的文件(例如编译后的二进制文件)。

16.使用 GitHub 问题

使用 GitHub Issues [5]跟踪 bug、特性和任务，并在提交中引用问题以将它们链接在一起。

如果您有任何编辑/修改建议或关于进一步扩展此主题的建议，请考虑与我分享您的想法。

# 另外，请考虑订阅我的每周简讯:

[](https://pventures.substack.com/) [## 周日报告#1

### 设计思维与 AI 的共生关系设计思维能向 AI 揭示什么，AI 又能如何拥抱…

pventures.substack.com](https://pventures.substack.com/) 

*参考文献:*

*1。*[*https://github.com/dvsa/mot-automated-testsuite*](https://github.com/dvsa/mot-automated-testsuite)

*2。*[*https://docs . github . com/en/actions/learn-github-actions/环境-变量*](https://docs.github.com/en/actions/learn-github-actions/environment-variables)

*3。*[*https://deviq.com/principles/dont-repeat-yourself*](https://deviq.com/principles/dont-repeat-yourself)

*4。*[*https://git-scm.com/docs/gitignore*](https://git-scm.com/docs/gitignore)

*5。*[*https://docs.github.com/en/issues*](https://docs.github.com/en/issues)

*6。将您的更改同步到远程 Git repo — Azure Repos。*[*https://docs . Microsoft . com/en-us/azure/devo PS/repos/git/pushing*](https://docs.microsoft.com/en-us/azure/devops/repos/git/pushing)

*7。GitHub—vtraag/intro-Python:Python 简介。*【https://github.com/vtraag/intro-python】

**8。Visual Studio 2010:复制类的最简单方法？。*[*https://stack overflow . com/questions/5008893/visual-studio-2010-最容易复制一个类*](https://stackoverflow.com/questions/5008893/visual-studio-2010-easiest-way-to-duplicate-a-class)*