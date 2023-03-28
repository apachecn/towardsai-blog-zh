# 在 AWS 中逐步创建 EC2 实例，并通过 Putty 和 WinSCP 访问它

> 原文：<https://pub.towardsai.net/step-by-step-creation-of-an-ec2-instance-in-aws-and-access-it-via-putty-winscp-a6c28f2022be?source=collection_archive---------2----------------------->

## [云计算](https://towardsai.net/p/category/cloud-computing)

![](img/f61fe8253d12880a579038b32a720838.png)

一个 **EC2 实例**是亚马逊弹性计算云( **EC2** )中的一个虚拟服务器(就像我们的计算机一样，但是在云中)，用于在亚马逊 Web 服务( **AWS** )基础设施上运行应用程序。

## 让我们开始吧。

1.  在服务下，单击计算部分下的 EC2 present。

![](img/54450c45b245d91e10d1b6936d7c9601.png)

2.单击启动实例

![](img/8e1759f1620c6ee197340b753e684dca.png)

3.搜索基于 ubuntu 的实例，也只单击免费层，以避免产生任何费用，现在我们选择 18.04 版本的 Ubuntu 服务器来运行基于深度学习的应用程序。您也可以选择其他操作系统，如 windows 等。但是这里我们坚持使用基于 ubuntu 的服务器。然后单击选择

![](img/07cedd172e21a1045b70d0b964485f2d.png)

4.选择 t2.micro instance，再次保持在自由层下&它为入门级应用程序提供了良好的性能，然后单击 Next: Configure Instance Details。

![](img/115e36a7cf48d27da3e8abbb947822e1.png)

5.保持默认值不变，如果您希望更改任何参数，请随意更改。

![](img/471a59c3cf4ff871e344816117d2b754.png)

6.接下来，对于存储，我们保留默认的 8 GB 空间，并确保启用“终止时删除”(如果您希望，但不建议禁用它),然后单击“下一步:添加标签”

![](img/548b429b89142f36ff8b51d080905396.png)

7.选择通过创建新的键和值对来添加标记，以便于识别特定的 EC2 实例，以防将来管理更多的 EC2，然后单击下一步:配置安全组

![](img/6cb49168b97c441a30393074ba3b18e7.png)

8.您可以创建新的安全组，也可以使用以前创建的或默认的安全组。在这里，我创建了一个新的安全组，并使用默认端口 SSH — 22，通过 putty 只提供对基于 SSH 的连接的访问。

您可以根据需要打开其他端口，如 HTTP(80) / HTTPS(443)。然后单击查看和启动

![](img/ffd0fb499539341925f75303c180eea1.png)

9.确保您验证了所有字段，然后单击“launch”。

![](img/34366bc6d85c4283ed88befda637cd23.png)

10.现在，弹出窗口打开，现在创建一个新的密钥对，并通过单击按钮 Download Key Pair 下载它。

这将下载一个. pem 文件，该文件用作每次访问我们创建的 EC2 实例的安全措施。如果没有这个密钥对，请小心。pem)文件，您**不能**访问您的服务器，因此请确保该文件的安全。

避免分享你的(。pem)文件，因为任何人都可以使用该文件访问您的服务器。

现在，单击 launch instance，最终启动我们的 EC2。

![](img/2ff2a3e15bcd413a0b45334aa1d43f03.png)![](img/8dd47626bf722b08ebdd677931d2a62d.png)

现在单击“查看实例”。

11.添加一个名称来标识您的实例，在 descriptions 选项卡中，您拥有连接到您的实例的 IPV4 DNS & address。现在让我们使用下载的(。pem)文件，并尝试访问新创建的 EC2 实例。

![](img/9ef6d65375b251c984cb8217c145761a.png)

12.有许多方法可以连接和查看我们的 EC2 实例。在这里，我将演示连接到 EC2 实例的两种方法。

一.使用油灰

![](img/ac42a50e97f9f1080b2288b9aebd2907.png)

在这里下载 putty 软件:[https://www.putty.org/](https://www.putty.org/)

二。使用 WinSCP

![](img/fbaf271d2bf6762085ef50ccefbe1337.png)

二。在这里下载 WinSCP 软件:【https://winscp.net/eng/download.php 

# **使用油灰**

13.现在，在安装了您选择的软件之后，我们必须转换下载的密钥文件(。pem) →(。ppk)来使用上面列出的两个软件访问我们的实例

不过没什么好担心的，可以用我们之前安装的油灰来完成。

![](img/7be5332b5cfb048f188f3c7324d3106f.png)

在 windows“开始”菜单上，键入 putty，然后选择 puTTYgen。

14.现在单击 load 按钮并选择下载的(。pem)文件。

![](img/b5eb1a535ca27b1b94fe2ba7bff3645c.png)

15.加载后，单击 save private key(保存私钥),会出现一个提示，选择 yes(是)保存私钥，不要输入密码，如果您希望输入密码，则选择 no(否)。在我们的例子中，我们选择 YES。

![](img/8b0865f3cd159d4f152f4bad61840769.png)

16.现在给它起一个新名字，并用(.ppk)格式，然后单击确定。

![](img/41ff132815fce974dba5300d4c8c63bc.png)![](img/9f5571b97c95af88756c118fba5d2635.png)

17.现在我们已经成功转换了(。pem)到(。ppk)格式。

18.现在让我们尝试使用 putty 和新的(*)来访问我们的 EC2 实例。ppk)文件已生成。

![](img/9dbddda12676e1206d4c44d9d5ac9fea.png)

19.从开始菜单中选择 putty。

20.现在返回 AWS EC2 实例控制台，复制公共 IP 地址并将其粘贴到 putty 配置窗口中。

![](img/636d47267b39090e4b522bbb01d9cb81.png)

21.现在，粘贴 IP 地址后，导航到 putty 中的 ssh 类别，并单击 Auth。现在单击选项卡中的浏览按钮，现在选择(*。ppk 文件)我们已经转换并打开它。

![](img/87f8b16cc5fad310beb2fb03924db2bd.png)![](img/4c5f4d690a0e1fd4dc4d7f0cdccb2e34.png)![](img/414081bf97eb9f90bd3de634ac637323.png)

22.现在将打开一个新的命令行界面，在提示窗口中，单击 yes(因为我们信任这个网络)

![](img/00d4a5f865b1f0ddc61ccfdf5610ef4d.png)

23.现在它要求用户名，所以对于我们的 ubuntu 实例，用户名是 ubuntu。键入并按回车键。现在，我们已经成功登录到我们的实例中。

![](img/8b2bde20532d069b88c2708e7e6668c1.png)![](img/093942fac5d1b7f8f6ecb687c2751782.png)![](img/219949865ac604030a3bf151f000166b.png)

第一次运行命令:" **sudo apt-get update** "更新 ubuntu 包的安全措施和新的更新。偶尔运行此命令来更新您的系统。

由于 AWS EC2 提供了一个虚拟服务器，我们可以通过命令行与它进行交互。第一次会有点吓人，因为我们大多数人都在使用基于 GUI 的界面。

但请相信我，这将是令人敬畏的，而且非常快。

# 使用 WinSCP

24.通过 WinSCP 软件连接是连接到我们实例的另一种方式，该选项为我们提供了一个基于 GUI 的界面，因此我们感觉像是我们已经习惯的基于 windows 的选项。

现在从开始菜单打开 WinSCP。

现在单击 New session 选项卡，然后在弹出窗口中单击 New Site，然后填充字段 Host name:(您的 EC2 IP 地址)和 username: ubuntu(如果是基于 ubuntu 的实例)。

然后单击菜单中的高级按钮

![](img/473e2dcf06c679752f8a0b045b6b2768.png)

25.单击“Advanced”按钮后，会打开一个新的弹出窗口，现在选择 SSH 选项卡，并选择其下的 Authentication 选项卡。

在此添加您的(*。ppk)文件，最后单击 OK。

![](img/391b8ca2d65343b07ec216bb8e25056c.png)![](img/25de3728401337f42e569795c0e574a2.png)

现在点击登录按钮。

![](img/1763289be803f22ab823eb7d79f672bc.png)

单击“是”(因为我们信任此网络)。

26.成功，现在我们可以通过 WinSCP 使用自定义 GUI 界面访问 EC2 实例。

我们的主目录是/home/ubuntu/因此，让我们在其中添加一些文件，然后通过我们的 putty 访问它。

![](img/13f52e8b6d3af0e767c174840f11a1aa.png)

现在，我在本地计算机上创建了一个. txt 文件，并将其移动到我们的 EC2 实例中。

![](img/e4421ac796fe850681f23b96aeda17e2.png)

让我们做一个简单的复制和粘贴。

![](img/5d2ec2f7733960a1ec97277a11ea6421.png)![](img/d63ee8d4adf3780e42a74bc6b89e1944.png)![](img/6b56c26ffe28efe6e44547cee419228b.png)![](img/a8c6e8e758fe6e0d1731102f3cdab295.png)

27.现在让我们通过 putty 访问这个文件。

![](img/50a80dc6e176e6bbba0cc17f4e5c95dd.png)![](img/d39eee05eb4e8cabbb674d5c3ef420f2.png)

就这样，我们只是将一个文件移入 EC2 并打开它。要退出编辑器，请遵循命令 Insert -> Esc -> **type** :q！- >回车。

28.键入 Exit，安全地移出我们的实例。

![](img/54d52b446f842113a09e48394436d73d.png)

29.最后，为了避免任何额外的费用，您可以在不使用 EC2 实例时停止它，稍后再启动。

不要终止实例，因为它会从控制台中删除。如果您希望不再需要它，可以终止它。所有存储卷将被一起删除。

![](img/32fcae6e4e09bf28c029997a742496e2.png)![](img/0a3dfdbb350e722e4d6a694f6295d458.png)![](img/b2633cfb3533f6634c6a2ef9df60c449.png)

由[多兰·埃里克森](https://unsplash.com/@doran_erickson?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

30.太酷了，你坚持到了最后，这就是我们如何在 AWS 中创建 EC2 实例。如果中途遇到任何问题，请不要发表评论。

如果你想玩不同的游戏，最好检查 EC2 实例的价格:[https://aws.amazon.com/ec2/pricing/](https://aws.amazon.com/ec2/pricing/)

我将发布与机器和深度学习相关的文章，以及它们与 AWS 服务的交集。

在那之前，下次见。

**文章作者:**

**BALAKRISHNAKUMAR V**