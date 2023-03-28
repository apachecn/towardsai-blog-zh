# Streamlit Cloud 向所有人开放，您会尝试吗？

> 原文：<https://pub.towardsai.net/streamlit-cloud-is-open-to-everyone-will-you-try-it-cbfc4b03bac0?source=collection_archive---------1----------------------->

## [DevOps](https://towardsai.net/p/category/devops)

## 仍然支持免费使用。但他们的定价计划中是否遗漏了“中产阶级”阶层？

![](img/2c78946e968da72fa2767e299a5c2836.png)

由 [jae bano](https://unsplash.com/@jae462?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

> 免责声明:不存在利益冲突。没有赞助。我只是根据我个人对这个工具的使用体验来介绍一下 Streamlit。

# 介绍

在我上个月发表的一篇文章中，我向您展示了如何通过在 Streamlit Sharing 上托管您的应用程序来免费部署 Streamlit web 应用程序，Streamlit Sharing 是 Streamlit 提供的公共托管服务。然而，在那时，你必须申请一个邀请才能使用共享功能。

[](https://towardsdatascience.com/deploy-a-public-streamlit-web-app-for-free-heres-how-bf56d46b2abe) [## 免费部署一个公共的 Streamlit Web 应用程序—方法如下

### Google Sheets 作为其后端，由 Streamlit Sharing 托管

towardsdatascience.com](https://towardsdatascience.com/deploy-a-public-streamlit-web-app-for-free-heres-how-bf56d46b2abe) 

不再需要邀请了！今天(2021 年 11 月 2 日)，在他们的博客中，他们公布了他们的最新产品——Streamlit Cloud。Streamlit Cloud 将之前的 Streamlit 共享服务扩展为基础层。

[](https://blog.streamlit.io/introducing-streamlit-cloud/) [## ☁️推出 Streamlit 云！☁️

### 数据科学陷入了僵局。曾几何时，数据顺畅地流入结构良好的表中。现在是一片汹涌…

blog.streamlit.io](https://blog.streamlit.io/introducing-streamlit-cloud/) 

# 定价等级

他们提供三个等级的价格。

*   **社区。**免费使用。但是，使用公共存储库最多只能发布 3 个 web 应用程序。此层不支持任何私有应用程序。对于像我们许多人一样的社区来说，好消息是可以使用该应用程序的用户数量没有限制。您可以拥有 1GB 的应用资源，并获得基于电子邮件的支持。
*   **组队。每月 250 美元。您可以使用公共或私有存储库托管多达 10 个 web 应用程序。对于公共应用程序，如社区层，没有用户限制。但是，对于私人应用程序，最多只有 20 个用户可以使用。在这一层，3GB 用于应用程序资源和电子邮件支持，一个工作日响应窗口。**
*   **企业。**它有一个未公开的费用——“联系我们”选项。显然，您可以预期成本会高于团队层级。在这一层，一切都可以商量。因为它旨在为大型企业提供服务，Streamlit 提供了 1 小时响应内的专门支持！

您可以在 [Streamlit 的网站](https://streamlit.io/cloud)上找到有关定价计划的更多详细信息。该链接是为了方便您而提供的。

# 你会尝试它吗？

## 简化框架

首先，我假设如果你正在阅读这篇文章，你知道什么是 Streamlit。本质上，它是一个 web 框架，通过它，你可以构建高度互动和好看的(从程序员的标准，而不是图形设计师的标准)web 应用程序，以展示你的数据科学或机器学习项目。

您所需要做的就是编写一个 Python 脚本并使用 Streamlit 运行它，Streamlit 会将内容显示为 web 应用程序。您可以使用 Streamlit 构建 web 应用程序，显示图像、表格、文本、地图、交互式图形和各种用于数据收集的小部件(例如，文本输入、按钮、单选按钮、多选、下拉选择、滑块)，几乎是您能想到的用于构建数据科学应用程序的所有内容。

值得注意的是，Streamlit 框架是免费和开源的。因此，如果你还没有尝试过，你现在就可以做。在开发阶段，您可以使用它在本地部署 web 应用程序。这意味着你可以在本地网络中运行一个允许多台电脑访问的 web 应用程序。

## 流线云

对于初学者来说，你可以在自己的电脑上玩 Streamlit。当你准备好公开展示你的项目时，你可以从免费社区层开始，它允许你托管 3 个公共应用。

然而，如果你想发布 3 个以上的公共应用程序，你需要决定是否要升级到团队层。就我个人而言，我觉得这两层之间的成本差距(250 美元/月)有点大。对于较小的公司，他们可能会犹豫是否值得升级。毕竟，这些层之间的功能差异似乎并不能证明成本差异的合理性。

因此，为了提供灵活性，我认为如果他们有额外的层级，比如小团队和大团队，前者的价格为每月 100 美元和每月 300 美元或类似的价格，将会吸引更多的潜在用户。当然，他们需要为每一层调整支持的功能。

无论如何，根据博客上显示的内容，Streamlit 已经被许多更大的公司采用，我猜这些企业中的许多将与 Streamlit 谈判一项定制协议。他们不太关心这些成本。

然而，正如你可以从我之前的段落中看出的，我的印象是 Streamlit 似乎并不清楚他们在“团队”层的目标受众。有哪些潜在的团队？

他们的商业模式的另一种选择是模仿 AWS 的现收现付模式，这种模式对较小的用户更有吸引力，可以控制他们的成本。

# 结论

我对 Streamlit 为数据科学社区提供的服务持积极态度，这些服务为我们开发和维护了这样一个令人敬畏的框架。我打赌这个框架会继续变得更好。就他们的云产品而言，我相信当他们听到更多来自最终用户的反馈时，他们也会继续发展。

无论如何，你总是可以开始尝试公共托管的框架和社区层。他们一开始都是免费的。

感谢阅读这篇文章。通过注册我的时事通讯保持联系。还不是中等会员？通过使用我的会员链接[来支持我的写作(对你来说没有额外的费用，但是你的一部分会员费作为奖励被 Medium 重新分配给我)。](https://medium.com/@yong.cui01/membership)