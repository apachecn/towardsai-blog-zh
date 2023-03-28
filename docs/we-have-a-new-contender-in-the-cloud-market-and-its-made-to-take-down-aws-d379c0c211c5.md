# 这家新的创业公司旨在拿下 AWS 和 DevOps 的工作

> 原文：<https://pub.towardsai.net/we-have-a-new-contender-in-the-cloud-market-and-its-made-to-take-down-aws-d379c0c211c5?source=collection_archive---------4----------------------->

## [云计算](https://towardsai.net/p/category/cloud-computing)、 [DevOps](https://towardsai.net/p/category/devops) 、[意见](https://towardsai.net/p/category/opinion)

## Render 能代替 DevOps 工程师，拿下 AWS 吗？

![](img/b58865e880b6f9cb8b96f6bffeed6468.png)

照片由[陶黎黄](https://unsplash.com/@h4x0r3?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄

答你是云的创始人还是在云上经营你的企业？您是否对经常性的云维护、开发人员工资和云成本感到沮丧？

Render 是一家新成立的公司，声称比 AWS、Heroku、GCP 和其他公司更好、更快、更容易维护。与 Heroku 和 AWS 不同，在 Heroku 和 AWS 中，您需要有一个单独的开发-运营团队来维护您在云中运行的应用程序，Render 使它成为一个一键式过程。

是啊！Render 是一个完全自动化的云提供商。它可以托管 Web 应用程序、API、Docker 文件、Cron 作业等等，不需要您进行任何维护。这意味着您的初创公司可以更加专注于他们的产品，而不必维护单独的开发-运营团队和关心云维护。 [Render 甚至获得了 Tech Crunch SF Disrupt 2019。](https://search.techcrunch.com/click/_ylt=Awr9DuGpaC1fFCcA.12nBWVH;_ylu=X3oDMTByNWU4cGh1BGNvbG8DZ3ExBHBvcwMxBHZ0aWQDBHNlYwNzYw--/RV=2/RE=1596840233/RO=10/RU=https%3a%2f%2ftechcrunch.com%2f2019%2f10%2f07%2fdaily-crunch-render-wins-the-startup-battlefield%2f/RK=2/RS=Iagb8_XYpbZONM9NhEngeKFtaRw-)

如果你是 DevOps 工程师，这是个坏消息。

我要讲的是—

*   **为什么渲染存在**
*   **渲染能做什么**
*   **什么渲染不能做**
*   它能取代 DevOps 工程师、AWS、GCP 和其他云提供商吗？

平均而言，美国 DevOps 的薪水是 104，000 美元，DevOps 团队的理想规模是 5 名工程师。美国有超过 660，000 名 DevOps 工程师。这意味着公司每年花费超过 680 亿美元用于云维护和开发人员工资。

Heroku 等托管云服务每月花费 250 美元，只需 2 GB 内存，不含固态硬盘和专用网络。Render 同样只需 25 美元，它提供固态硬盘和私人网络。

对于小企业、初创公司和爱好者来说，这些成本可能是一个大问题。[初创企业失败的第二大原因是资金。](https://www.cbinsights.com/research/startup-failure-reasons-top/)他们现金不足，无法跟上成本，无法生产高质量的产品，也无法根据市场进行调整。Render 为初创公司提供了自动化云，为他们节省了数十万美元的工资成本和大量的云维护时间。

> 2019 年 9 月，增强现实初创公司[dakri](https://www.cbinsights.com/research/startup-failure-post-mortem/#2019update3)在耗尽超过 2.5 亿美元的资金且未能从投资者那里筹集到新一轮资金后关闭——T4 CBinsights

# **渲染可以做什么**

1.  渲染是自动的，所以它可以管理你在云中运行的所有应用程序，而不需要你的参与。
2.  Render 让您可以部署任何东西，从简单的静态网站到复杂的应用程序集群。它可以处理 API、网络应用程序、Docker 文件等等。
3.  它可以构建代码并将其部署到云中，处理安全更新，自动扩展，负载平衡资源，并在出现任何问题时监视和提醒用户。只需单击“部署到渲染”按钮，所有这些任务都可以自动化。
4.  每个渲染服务都获得服务发现、专用网络和负载平衡。
5.  Render 为固态硬盘提供自动备份和一键式恢复功能。
6.  Render 开发了一个称为“基础设施即代码”的概念。这允许开发人员在 YAML 文件中定义他们的基础设施需求。只需更改该文件并将其推送到 g it，就可以更新当前的基础设施。
7.  渲染使您能够在云中加速自动对象存储。亚马逊 S3 和其他云存储选项要求您在云中使用虚拟机，连接存储，管理备份，并永远负责所有的处理和管理任务。渲染使用渲染磁盘使其自动化。
8.  渲染让您可以灵活地在不同区域的 AWS 和 GCP 上同时运行工作负载，只需一个剪辑。AWS 或 GCP 未提供此类方案。
9.  Render 为您提供了一个插件市场，通过这个市场您可以集成其他服务，例如 L [ogDNA](https://logdna.com/) 、scout 和其他服务。

# 什么渲染不能做

1.  渲染不能与云上的深度学习和 Ml 模型一起使用。这对于基于 GPU 的工作负载来说并不好。
2.  他们没有自己的底层基础设施。Render 使用 GCP 和 AWS 来存储所有数据，并使维护的云成为可能。但他们计划在未来转向裸机集群
3.  就基础设施成本而言，Render 不是最佳解决方案，因为它使用 GCP 和 AWS 来运行，因此会比它们昂贵。Render 旨在通过自动化传统上需要开发运营团队完成的云维护任务，最大限度地降低初创公司和小公司的运营成本。
4.  Render 不是为大型企业设计的，目前它不能同时处理数千台机器。他们的目标是那些没有资源雇佣独立开发运营团队的创业公司、个人和企业。

通过自动化云需求和所有云工作流，ender 肯定可以取代初创公司、独家开发商和公司的开发运营需求，但它不能取代大型企业和老牌公司的这一需求。

对于需要处理大量数据并快速增长的初创公司来说，这也不是一个可行的解决方案，因为如果 Render 不能以同样的速度增长，他们将不可避免地转向 AWS 或其他提供商来满足他们的要求。Render 计划长期满足这些要求，但目前不提供此解决方案。

这意味着大型组织和成长型创业公司仍然需要 DevOps 工程师。因此，如果你是一名开发运营工程师，你可以松一口气了。

由于 Render 依赖于 AWS 和 GCP，目前这些云提供商是无害的。但 Render 的目标是转向裸机，并为初创公司和企业提供特定的利基市场。它将从 AWS、GCP 或任何其他平台夺走这一细分市场。