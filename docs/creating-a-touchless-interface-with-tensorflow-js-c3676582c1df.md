# 用 Tensorflow.js 创建无触摸界面

> 原文：<https://pub.towardsai.net/creating-a-touchless-interface-with-tensorflow-js-c3676582c1df?source=collection_archive---------3----------------------->

## [深度学习](https://towardsai.net/p/category/machine-learning/deep-learning)

触摸屏是革命性的。然而，随着无线技术的出现和在表面上传播的高度传染性疾病，需要一种与应用程序交互的精细方式。引入无触摸界面。

![](img/8e5a05448ccebff5b8ebf83e466cd73a.png)

来源:来自 pexels.com[的](https://www.pexels.com/photo/photo-of-woman-wearing-turtleneck-top-2777898/)[阿里·帕扎尼](https://www.pexels.com/@alipazani)

# 介绍

无触摸界面在大量设备上运行良好，为许多平台上的现实世界实施打开了大门——从无触摸亭到 VR 游戏集成。

这篇文章将介绍一个基于 web 的无触摸界面的代码，在这个界面中，来自任何平台的用户都可以通过手的移动与虚拟块进行交互。

## 有用的链接:

*   [无触摸界面](https://touchlessinterface.netlify.app/)(网站)
*   [无接触界面 GitHub 库](https://github.com/Hammaad-M/touchless-interface)
*   [isHandOpen GitHub 库](https://github.com/Hammaad-M/isHandOpen)(稍后讨论)

# 设置

在数据可以开始通过深度学习模型推送之前，有几项任务需要首先完成。

1.  正在加载 Tensorflow.js
2.  加载手选模型
3.  设置网络摄像头
4.  创建随机生成的块

只需通过 index.html 文件中的 cdn 加载 Tensorflow.js。Tensorflow.js 的脚本标记放在本地 JavaScript 标记之前和所有 UI 元素之后，以允许 UI 首先加载 Tensorflow.js，然后加载本地 JavaScript。

出于与上述相同的原因，HandPose 模型也是在 Tensorflow.js 之后通过 cdn 加载的。但是，加载 HandPose 模型还需要执行下面的异步命令:`handpose.load()`。在无接触界面的代码中，步骤 1-3 被包装在对 attempt()函数的调用中。下面是加载 HandPose 模型的 attempt()函数:

```
// Load the MediaPipe handpose model.
  const model = await attempt(
    async () => await handpose.load(), 
    () => statusDisplay.textContent = "Setting up Webcam", 
    () => fail("Failed to Load Model"),
  );
```

attempt()函数接受 3 个函数参数。传递的第一个函数是要执行的函数。如果第一个函数没有任何错误地完成，则执行第二个函数。如果第一个函数出错，将执行最后一个函数。在这种情况下，如果`await handpose.load()`运行没有任何错误，屏幕状态将更新到下一步，否则将执行失败回调以中止设置。

下一个任务是设置网络摄像头，它被提取到异步函数`setupWebcam`中，并被打包到一个`attempt()`调用中。`setupWebcam`功能访问用户的网络摄像头，并将其设置为屏幕视频元素的来源。它还为摄像头的大小设置了全局变量，这对于从视频馈送中解密手的偏移是必不可少的。该函数还为视频元素设置了`plays-inline`属性`true`，以确保 safari 兼容性。

最后一个设置任务是随机生成供用户交互的彩色块。这是在`createObjects`函数中通过使用`document.createElement`函数创建 HTML 元素来完成的，这些元素随后被随机应用到样式预设中。

# 跟踪手

完成初始设置后，剩下的代码将在应用程序的主循环中执行。跟踪用户手部的第一步是调用异步函数`model.estimateHands(videoRef)`，该函数使用 HandPose 模型从视频元素预测手部，该视频元素正在传输用户的网络摄像头馈送。`estimateHands`函数返回一个预测数组，其中第一个是最相关的。预测对象有很多重要的信息，比如手掌根部和每个手指上的关键点的坐标(x，y，z)。

第一个任务是根据手在摄像头中的位置移动屏幕上的目标元素。`getHandCoords`函数接受`prediction.annotations`作为输入，并使用它来检索手掌底部的 x 和 y 坐标。然后，它发回以下表达式的结果:

```
return [
  ( palmX / webcamWidth ) * 100, 
  ( palmY / webcamHeight ) * 100
];
```

手在视口中的位置被转换为百分比偏移，然后用于设置屏幕目标的`right`和`top`样式属性，以匹配手的位置。

# 与用户界面交互

最后一步，也可能是最具挑战性的一步，是允许用户拾取、移动和丢弃随机生成的块。以下是对该概念的简要解释:

> *当用户伸出手指，手掌平放在摄像机上时，屏幕上的目标应在不改变位置的情况下越过任何方块，并放下任何被按住的方块。*
> 
> *相比之下，当用户的手指卷曲，或者他们的手握拳时，任何被握住的块应该继续被移动。如果没有块被保持，用一只握紧的手经过一个块时，应该会拿起它，并沿着屏幕上的光标拖动它。*

## isHandOpen 库简介

上述伪代码的实现依赖于准确地确定用户的手是否张开。为了有效地将这个组件提取到一个可重用的组件中，我编译了一个纯 JavaScript 库，它使用`predictions.annotations`对象来返回一个`true`或`false`值，以表示用户的手是否张开。这里有一个[链接](https://github.com/Hammaad-M/isHandOpen)到存储库。值得注意的是，无接触界面存储库附带了 isHandOpen。如果没有使用无接触界面的存储库，下载简化的 isHandOpen JavaScript 文件，并在任何本地 JavaScript 标签上方引用它`<script src="isHandOpen.min.js"></script>`。这将定义带有两个参数的`isHandOpen`函数:对象`predictions.annotations`和可选的`HAND_OPEN_BUFFER`。第二个参数控制在`isHandOpen`函数返回`true`之前，手在一行中应被检测为张开的次数。默认情况下，`HAND_OPEN_BUFFER`是`null`，这意味着函数每次都会准确地返回它所预测的结果。我在这种方法中发现的一个反复出现的错误是，当用户的手合拢时，应用程序会抛出阻塞。`HAND_OPEN_BUFFER`有效地消除了误报的问题，代价是稍后`HAND_OPEN_BUFFER`调用`isHandOpen`时会丢失项目——在这种情况下只有几毫秒。

## 拖动项目

用`predictions.annotations`对象和为 2 的`HAND_OPEN_BUFFER`对`isHandOpen`的简单调用返回一个布尔值，表示用户的手是否张开。下一步是允许用户移动屏幕上的块。为了拿起一个方块，用户的手必须合拢，光标或目标必须靠近该方块。如果手闭合并且当前没有拿着任何物品，则执行`canGrabItem`功能，将目标的`top`和`right`样式值与屏幕上的每个物品进行比较，并找到可以拿起的最近的物体。如果该项足够接近，那么它会将其设置为当前持有项的全局变量的值。然后，在主循环的后续迭代中读取该值，主循环将其与目标光标一起移动—随着用户的手一起移动。

# 摘要

无触摸界面利用 Tensorflow.js 的 HandPose 模型从网络摄像头定位用户的手，并将其位置投影到屏幕光标上。然后它集成 isHandOpen 库来解密用户的手是否张开。这些信息然后被用来允许用户在他们的手指和手上抓取、移动和放下屏幕上的小部件。

## 含义

浏览器中的无接触界面代表了这种技术的广泛应用。从公共区域的无触摸解决方案到新水平的软件沉浸，无触摸界面有能力彻底改变人类与计算机的交互方式。