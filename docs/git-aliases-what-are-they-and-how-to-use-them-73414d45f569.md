# Git 别名——它们是什么以及如何使用它们？

> 原文：<https://pub.towardsai.net/git-aliases-what-are-they-and-how-to-use-them-73414d45f569?source=collection_archive---------6----------------------->

## [编程](https://towardsai.net/p/category/programming)

![](img/0f36091026b152709eb337c19abfa372.png)

[Yancy Min](https://unsplash.com/@yancymin?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍照

作为一名开发人员，我们使用 Git 做了很多工作。我们倾向于在一天中无数次地编写相同的命令。因此，一遍又一遍地重复同样长的 Git 命令会成为一项乏味的任务。

因此，在本文中，您将看到如何为您想要的任何 Git 命令设置 Git 别名。别名将极大地改善您的体验，同时也将节省您的时间。

# 什么是 Git 别名

Git 别名是映射到较长命令的较短命令。简单地说，它们是一条捷径。例如，不要每次想要提交一些更改时都键入`git commit -m "message here"`，而是可以使用一个别名，比如`git cm "message"`。

乍一看，这似乎不是一个显著的改进，但是一旦你重复同样的命令十几次，你就会看到好处。此外，当您推动更改和使用各种命令时，它可以节省您大量的时间。

因此，让我们看看如何设置 Git 别名。

# 如何设置别名

要为命令设置别名，您需要在终端中运行一行配置。所有的命令都以`git config --global alias.`开头，在点之后添加别名和 Git 命令。例如，要为`git status`创建一个别名，我们可以在终端`git config --global alias.st status`中运行下面的命令。

添加别名的模板如下`git config --global alias.[insertYourShortcut] [gitCommand]`。下面，你可以看到我使用的 Git 别名作为指导:

```
git config --global alias.c checkout
git config --global alias.st status
git config --global alias.cm 'checkout master'
git config --global alias.b branch
git config --global alias.c checkout
git config --global alias.cmm 'commit -m'
git config --global alias.p pull
git config --global alias.cb 'checkout -b'
git config --global alias.sc 'switch -c'
```

但是，你可以按照你喜欢的任何方式进行修改。除此之外，您还可以添加新的、更复杂的命令。

# 如何运行命令

您可以像运行任何其他 Git 命令一样运行这些命令。例如，如果您想签出 master，您可以运行`git cm`而不是`git checkout master`。

我建议为您的命令使用描述性别名。否则，你会感到困惑。比如看`git.st`或者`git.cm`，更容易理解他们的目的是什么。另一方面，对`git rebase <base>`使用类似`git cm`的东西，会让你感到困惑。

# 警告

为了方便地显示您的 git 别名，在您的终端中运行下面的命令`git config --global alias.alias "! git config --get-regexp ^alias\. | sed -e s/^alias\.// -e s/\ /\ =\ /"`。

现在您可以使用`git alias`列出您创建的所有别名。

# 结论

总之，使用别名后，你会喜欢它们的。它们帮助你节省时间，减少错误，并且加速开发。

如果有其他别名，可以在评论里回复。我很想看看它们！

*如果你对 JavaScript 教程感兴趣，我推荐* [*前端高手*](https://catalins.tech/frontend-masters-membership-is-it-worth-it) *！*

*如果你想用技术写作赚钱，就去查查* [*那些付钱让你写*](https://catalins.tech/websites-that-pay-you-to-write-technical-articles) *技术文章的网站吧！*

*如果你想学习 JavaScript，我推荐这些* [*5 资源作为初学者学习 JavaScript*](https://catalins.tech/5-best-resources-to-learn-javascript-as-a-beginner)*！*

*谈判你的工资是必不可少的——学习* [*作为一名开发者如何谈判你的工资*](https://catalins.tech/how-to-negotiate-your-salary-as-a-developer) *！*

*用* [*Git 别名*](https://catalins.tech/git-aliases-what-are-they-and-how-to-use-them) *加速你的开发。*

*如果你想以开发者的身份* [*开博客*](https://catalins.tech/how-to-start-your-blog-as-a-developer) *，我推荐你阅读《* [*如何以开发者的身份开博客*](https://catalins.tech/how-to-start-your-blog-as-a-developer) *》一文！*

你是否很难跟上科技领域的最新消息？参见 [*作为开发者保持最新状态的一种方法*](https://catalins.tech/one-way-to-stay-up-to-date-as-developer) *！*

*学习* [*如何在 JavaScript*](https://catalins.tech/how-to-use-asyncawait-in-javascript) *中使用 Async/Await！*

GitHub 简介目前风靡一时。了解 [*如何创建 GitHub 个人资料页面*](https://catalins.tech/how-to-create-a-kickass-github-profile-page) *！*

*看看这 7 个* [*资源，帮你通过求职面试*](https://catalins.tech/7-github-repositories-to-help-you-crush-your-job-interviews) *！*

*查看*[*JavaScript ECMAScript 2021 es 2021*](https://catalins.tech/javascript-es2021-you-need-to-see-these-ecmascript-2021-features)即将推出的新功能！

你是初学程序员吗？查看这些 [*编程项目思路适合初学者*](https://catalins.tech/10-programming-project-ideas-for-beginners) *！*

你是在学习编码还是打算做编码？查看 [*免费学习编程的最佳地点*](https://catalins.tech/20-best-places-to-learn-programming-for-free) *！*

[*用这 9 个浏览器扩展提高你的开发者生产力*](https://catalins.tech/my-9-must-have-browser-extensions-for-increased-developer-productivity) *！*

*如果你是 Node.js 的开发者，我建议你查看 Node.js* *中的这些* [*4 种创造性的设计模式！*](https://catalins.tech/the-4-creational-design-patterns-in-nodejs-you-should-know)

*查看这些惊人的*[*JavaScript ECMAScript 2020 特性*](https://catalins.tech/javascript-es2020-the-features-you-should-know) *！*