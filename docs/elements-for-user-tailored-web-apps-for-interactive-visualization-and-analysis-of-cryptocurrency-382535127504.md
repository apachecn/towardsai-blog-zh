# 用于加密货币数据的交互式可视化和分析的用户定制 Web 应用的元素

> 原文：<https://pub.towardsai.net/elements-for-user-tailored-web-apps-for-interactive-visualization-and-analysis-of-cryptocurrency-382535127504?source=collection_archive---------5----------------------->

## [数据分析](https://towardsai.net/p/category/data-analysis)

## 通过 API 和丰富的 web 编程工具，现在可以为个性化目标定制令人惊叹的完整 web 应用程序。发现一个具有丰富特性的示例 web 应用程序及其背后的主要元素和代码片段。

*免责声明:你可以在这里找到代码和一个可用的 web 应用程序，欢迎你使用，但这些都不构成财务建议，我对你可能在中遭受的任何误用或损失不承担任何责任。我不是密码和相关东西的专家。也就是说，玩得开心，如果有问题和工作建议，一定要联系我们！*

可视化是有效探索复杂数据集的关键。我特别支持**的交互图**，用户可以动态地改变显示的内容以及显示的数据是如何处理的。我也提倡尽可能多的网络编程，如果你关注我，你就会知道。Web 应用程序具有易于部署和可用性的巨大优势，加上跨设备和操作系统的无缝兼容性；此外，它们不需要安装和更新。

## 交互式数据可视化的 web 应用系列

在我从本文开始的一个简短系列中，我将介绍处理与各种主题相关的数据可视化和数据分析的编码元素，甚至完整的 web 应用程序。

我从一个 **web 应用程序开始，在基本数据分析的帮助下，一次显示最多两个硬币的历史加密货币数据，以便于快速探索各种硬币和即时比较。**在本系列文章的下一个版本中，我将展示为结构生物学和结构生物信息学的各种主题的数据导航和显示而定制的 web 应用程序:

*   我的全客户端精神变态服务器。
*   用于蛋白质模型和分数的图形分析的网络应用程序被用于[结构预测的关键评估](https://lucianosphere.medium.com/the-critical-assessment-of-structure-prediction-casp-over-a-quarter-century-tracking-the-state-bde0a92b3680) 13，其中 [AlphaFold](https://lucianosphere.medium.com/here-are-all-my-peer-reviewed-and-blog-articles-on-protein-modeling-casp-and-alphafold-2-d78f0a9feb61) 进入了该领域。
*   一个交互式浏览蛋白质热稳定性数据和 3D 结构的网站。
*   执行蛋白质圆二色数据拟合和模拟的网络工具。

可能还有其他一些包含有趣元素的小项目。

因此，敬请关注所有这些即将到来的文章！

如果你现在想看我的两篇报道在线数据可视化和分析的 web 工具的文章，这里有:

[](https://towardsdatascience.com/a-free-online-tool-for-principal-components-analysis-with-full-graphical-output-c9b3725b4f98) [## 一个免费的在线主成分分析工具，提供完整的图形输出

### 完全在您的浏览器上运行，您不需要下载或安装任何东西，您的数据将保留在您的…

towardsdatascience.com](https://towardsdatascience.com/a-free-online-tool-for-principal-components-analysis-with-full-graphical-output-c9b3725b4f98) [](https://towardsdatascience.com/websites-for-statistics-and-data-analysis-on-every-device-ebf92bec3e53) [## 在每台设备上进行统计和数据分析的网站

### 我对网络浏览器中数据分析在线工具的选择。

towardsdatascience.com](https://towardsdatascience.com/websites-for-statistics-and-data-analysis-on-every-device-ebf92bec3e53) 

# 一个不断发展的 web 应用程序，用于历史加密货币数据的交互式可视化、分析和比较

我想开发一个 web 应用程序，通过它我可以以不同的方式可视化加密货币的数据。例如，考虑价格轴中的对数标度，或者可视化每日变化而不是绝对价格；此外，我希望对显示的日期范围有精确的控制；理想情况下，我希望能够比较成对的加密货币。我想我已经实现了所有这些，或者我也很接近了！我继续开发这个网络应用程序，探索人们可以进行的不同类型的分析。

例如，在下一张图中，我比较了比特币和[基本注意力令牌](https://medium.com/technology-hits/thanks-brave-browser-i-was-sick-of-youtubes-ads-fe3625f36296)在特定日期范围内的每日价格差异，平均超过 13 天(2*6+1)。使用鼠标，我可以看到每个确切的时间点，信息面板显示了图的相关系数。

![](img/4dd3bac23c258e90e76f0c9745937807.png)

我正在开发的 web 应用程序的截图，在笔记本电脑上的谷歌 Chrome 中运行。下面的“就是它，功能丰富的网络应用”中提供了链接。本文中的这张图和所有其他图都是由作者卢西亚诺·阿布利亚塔制作的。

## web 应用程序等元素必须具备

第一点是根据期望的功能和所需的代码，确定我需要什么元素。以下是我认为对这个加密 web 应用程序至关重要的主要元素:

*   加密数据的来源
*   绘制这些数据的方法
*   用户界面的控件
*   处理日期的函数
*   用于执行数值分析的功能

对于其中的一些点，特别是对于数字分析和数据显示本身，您可能会从*特设的*库中受益。或者，您可以采取强硬的方式，编写自己的自定义函数。对于这个项目，我更喜欢**硬编码一切，包括数据绘制，因为这给了我对 web 应用程序计算和显示内容的最大控制权**。耶！

现在让我们逐一分析以上各项，稍后让我们看看一个 web 应用程序的工作示例(您在上面有一个预览)，您可以使用它来直观地比较加密货币并实现一些基本计算。再次声明:不构成任何形式的财务建议。

## 加密数据的来源

许多数据提供者提供了 API(应用程序编程接口),您可以用它来以编程方式获取数据。这些 API 中有许多都包含免费版本，以我的经验来看，对于个人需要的各种任务来说已经足够了。我在最近的文章中讨论了其中的两个 API。第一个 CryptoCompare 的 API 在这里:

[](https://towardsdatascience.com/obtaining-historical-and-real-time-crypto-data-with-very-simple-web-programming-7b481f153630) [## 通过非常简单的 web 编程获得历史和实时加密数据

### 在学习加密货币的过程中，我迫切需要数据来操纵我自己去做我自己的阴谋和…

towardsdatascience.com](https://towardsdatascience.com/obtaining-historical-and-real-time-crypto-data-with-very-simple-web-programming-7b481f153630) 

然后是 CoinGecko 的 API，和 CryptoCompare 的相比有一些优缺点:

[](https://towardsdatascience.com/obtain-unlimited-historical-crypto-data-through-simple-api-calls-without-keys-8a6f5ed55b43) [## 通过简单的 Web 代码获得无限的历史加密数据-没有 API 密钥

### 从基于网络的代码中调用 CoinGecko 的免费 API 来获取价格、交易量和市值，您可以调整…

towardsdatascience.com](https://towardsdatascience.com/obtain-unlimited-historical-crypto-data-through-simple-api-calls-without-keys-8a6f5ed55b43) 

## 绘制数据和其他图形

图形界面可以变得像你想要的那样复杂，甚至是疯狂的未来主义；例如，我在这里使用虚拟现实显示器来实时查看比特币价格，就好像你正身处一个加密版的股票交易中心:

[](https://towardsdatascience.com/live-display-of-cryptocurrency-data-in-a-vr-environment-on-the-web-af476376d018) [## 网上虚拟现实环境中加密货币数据的实时显示

### 一种“虚拟股票交易中心”

towardsdatascience.com](https://towardsdatascience.com/live-display-of-cryptocurrency-data-in-a-vr-environment-on-the-web-af476376d018) 

但是当然，对于一个实用的 web 应用程序，我更喜欢一些简单的图形来有效和简单地传达信息。虚拟现实只是为了好玩！

您可能还需要决定是否希望绘图仅在计算机、智能手机或两者上显示良好。

Google Charts 是一个易于使用的 JavaScript 图形库，事实上我在上一篇文章中使用过它:

[](https://towardsdatascience.com/obtain-unlimited-historical-crypto-data-through-simple-api-calls-without-keys-8a6f5ed55b43) [## 通过简单的 Web 代码获得无限的历史加密数据-没有 API 密钥

### 从基于网络的代码中调用 CoinGecko 的免费 API 来获取价格、交易量和市值，您可以调整…

towardsdatascience.com](https://towardsdatascience.com/obtain-unlimited-historical-crypto-data-through-simple-api-calls-without-keys-8a6f5ed55b43) 

现在，对于我在这里展示的应用程序，我需要对可视化有详细的控制…当然比谷歌图表提供的更多。因此，我不得不硬编码所有的绘图功能。

为了简单起见，我选择了 HTML 画布。是的，它的图形质量很低；然而，我需要高效快速的东西。对于花哨的图形，你可以访问任何常规网站(代价是对你看到的内容的有限控制！).

关于在 HTML 画布上绘制数据的一些提示:

*   在更新绘图之前，使用 clearRect(0，0，canvas.width，canvas.height)清除画布。
*   使用 beginPath()和 stroke()绘制所有图形。
*   使用简单的颜色。这里我用绿色条显示价格或市值的积极变化，红色表示消极变化；简单的白色背景，组成轴的线条和文本为黑色。
*   我用跟随鼠标的垂直和水平线条来完成绘图，作为眼睛的向导。

## 用户界面的控件

在我的 web 应用程序中，我需要控件来选择密码，在各种数据处理选项之间切换，以及选择数据范围。在我的示例应用中，我使用了:

*   **选择和选项**，用户可以选择要比较的加密货币对。
*   小的**文本框**，用户可以在其中输入日期范围和其他参数。
*   **复选框**供用户指示是否查看正常或对数标度的数据、窗口平均值等。
*   一对**单选按钮**，用户可以选择是否查看价格或市值。
*   两张**画布**用于绘图。
*   两个**div**在鼠标移动时跟随鼠标位置，模拟图中眼睛的一对引导线。

你可以使用一个漂亮的库来更好地控制控件的布局，尤其是在像智能手机这样的小屏幕上，但是我没有。我把所有的元素都放在 HTML 和 CSS 级别，这很难。[一般来说，我尽量避免使用库，除非为了保持代码简单而绝对有必要，或者因为我不知道或者没有时间自己实现它的功能。]

无论如何，关于控件布局，这些 web 应用程序是为在计算机上使用而设计的，在计算机上你有空间展开组成页面的不同对象。这就是为什么我刚刚放弃了一个奇特的图形用户界面。(无论如何，我在这里展示的 web 应用程序在平板电脑和大屏幕智能手机上显示得相当好。)

## 转换日期

用于加密数据的 API 以串行格式返回日期，该格式由一个整数组成，用于测量自 1970 年 1 月 1 日以来经过的毫秒数。

该日期格式可能看起来像例如 1644532457000。这实际上是针对 2022 年 2 月 10 日星期四 23:34:19 GMT+0100(中欧标准时间)。

使用下面的函数，您可以在 JavaScript 中将以毫秒为单位的日期转换为人类可读的时间:

```
function serialDateToNiceDate(dateinserialformat){
 return new Date(dateinserialformat)
}
```

您可能还需要相反的东西，即将给定的日期从 nice 格式转换为 serial 格式。这很简单，因为它是由一个本地 JavaScript 对象处理的:

```
Date.parse(dateinhumanreadableformat)
```

## 数值分析

有几个用于数值分析的库，您可以在 web 应用程序中使用它们。我已经在以前的文章中讨论过 Lalolib，例如:

[](https://towardsdatascience.com/websites-for-statistics-and-data-analysis-on-every-device-ebf92bec3e53) [## 在每台设备上进行统计和数据分析的网站

### 我对网络浏览器中数据分析在线工具的选择。

towardsdatascience.com](https://towardsdatascience.com/websites-for-statistics-and-data-analysis-on-every-device-ebf92bec3e53) 

但是还有更多的库，比如 [statistics.js](https://thisancog.github.io/statistics.js/index.html) 、 [simplestatistics](https://simplestatistics.org/) 和 [jstat](https://github.com/jstat/jstat) 等等。

但是这里我没有使用任何库来进行数值分析。为什么？

嗯，因为我的网络应用程序正在计算相当简单的东西，比如平均值和皮尔逊相关系数。因此，我只是自己实现了这些功能；例如，这是计算皮尔逊相关性的函数:

```
function pearsonCorrelation(v1, v2) {
 var sum1 = 0, sum2 = 0
 for (var i = 0; i < v1.length; i++) {
   sum1 += v1[i]
   sum2 += v2[i]
 }var sum1sq = 0, sum2sq = 0
 for (var i = 0; i < v1.length; i++) {
   sum1sq += v1[i] * v1[i]
   sum2sq += v2[i] * v2[i]
 }var tmp = 0
for (var i = 0; i < v1.length; i++) {
  tmp += v1[i] * v2[i]
}var above = tmp — (sum1 * sum2 / v1.length);

var below = Math.sqrt((sum1sq — sum1*sum1 / v1.length) * (sum2sq — sum2*sum2 / v1.length));if (down == 0) return 0;return above / below;
}
```

# 这就是功能丰富的网络应用

有了上面的所有元素，我做了一个 web 应用程序(实际上我一直在开发它),在那里我可以:

*   选择一对加密货币，从 CoinGecko 获取它们的历史价格和市值。
*   当时间范围小于 1 个月时，以每天或每小时为基础，在我想要的任何确切时间范围内绘制数据。
*   以线性或对数标度显示价格/市值数据。有时一个比另一个更方便。
*   显示原始数据或每日/每小时的差异。
*   可选地平均加班点，这突出了价格增长和衰减期。
*   以及计算两个硬币显示的数据的皮尔逊相关性。尼古拉斯·雷森德兹(Nicholas Resendez)在这里讨论了相关性，我总是很好奇不同硬币之间的相关性有多大——剧透一下，你可以使用我的应用程序来检查自己:所有硬币都非常相关，但在特定时期内相关性会暂时消失。

作为该应用程序提供的一个例子，请参见上图或下图，我绘制了 2021 年 7 月 22 日至 2022 年 2 月 18 日期间比特币和以太坊的价格。自己看看它们的价格如何遵循非常相似的趋势，相关系数为 0.887，同时达到峰值:

![](img/e7b311f0a400302ce80fd8761270fadd.png)

我喜欢我正在制作的这个应用程序的一个特别重要的点是，我可以很好地控制显示的确切时间范围。大多数应用程序和网站会给你过去一小时、一天、一周、一月、一年或年初至今的数据…但是你不能选择准确的范围！有了这个网络应用，你可以！

还有一点很重要，一些密码变化太大，标准价格轴通常不好，对数标度更方便。这在标准应用程序中并不常见，但在这里，通过完全控制数据和绘图过程，我可以无缝地添加该功能。例如，比较上面的线性标度和下面的对数标度显示的比特币:

![](img/b9afb0ceca5231ac3c9cb50db249bdca.png)

你可以[在这里以演示模式](https://lucianoabriata.altervista.org/cryptotests/tdsarticlefeb2022/tdsarticlefeb2022_login.html)免费使用这个网络应用。请随时[联系我](https://lucianoabriata.altervista.org/office/contact.html)要求定制这个应用程序的变化，未来的版本，我一直在开发，包括更多的硬币和更多的分析，或任何其他类型的程序，以满足您的需求。

我希望您喜欢这篇文章的精神，这篇文章介绍了一些模块和建议，用于将相对简单的 web 应用程序放在一起，以适应特定的需求。并且向你证明客户端 web 编程是非常强大的。

这一系列文章将继续介绍在 web 应用程序中进行更多数学运算的工具，在页面中插入 3D 数据视图的模块，包括分子结构等等。敬请期待！

www.lucianoabriata.com*[***我写作并拍摄我广泛兴趣范围内的一切事物:自然、科学、技术、编程等等。***](https://www.lucianoabriata.com/) **[***成为媒介会员***](https://lucianosphere.medium.com/membership) *访问其所有故事(我为其获得小额收入的平台的附属链接无需您付费)和* [***订阅获取我的新故事***](https://lucianosphere.medium.com/subscribe) ***通过电子邮件*** *。到* ***咨询关于小职位*** *查看我的* [***服务页面这里***](https://lucianoabriata.altervista.org/services/index.html) *。你可以* [***这里联系我***](https://lucianoabriata.altervista.org/office/contact.html) ***。******