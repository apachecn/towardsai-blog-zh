# 使用 ARKit 开发基于人工智能的移动应用

> 原文：<https://pub.towardsai.net/using-arkit-to-develop-mobile-apps-powered-by-ai-fa09b9a3cd57?source=collection_archive---------1----------------------->

## 编程；编排

![](img/208d824e0c2dc0442a4211fa7391ad95.png)

移动应用程序的创建和开发是一个庞大且快速发展的行业。在过去的几年里，由于引入了新颖的未来技术，它已经得到了显著的改进。增强现实和人工智能已经存在了相当一段时间，现在是时候将它们应用到移动应用程序的创建中了。

# 什么是 ARKit？

ARKit 是苹果用于创建 AR 应用的开发工具。为了让这项技术发挥作用，苹果使用设备的内置摄像头、处理器和一些传感器来分析环境。该设备自动检测水平表面，并允许用户在其上放置合适的物体。苹果还负责与渲染阴影和移动相机时的所有移动相关的所有计算。

为了实现增强现实，ARkit 使用了一个处理器(在新的 [A11 Bionic](https://en.wikipedia.org/wiki/Apple_A11) 中分配了一个单独的子系统)、一个集成的设备摄像头和一组用于分析周围空间的传感器。

现在，iPhones 和 iPads 将能够使用来自相机、陀螺仪、加速度计和其他传感器的数据集来确定他们在当前情况下的位置，并考虑设备周围的物体。所有这些数据的一个关键应用是找到适合当前任务的平面对象或线条，在其上可以放置信息或虚拟对象。

该平台可以识别周围空间的尺寸，并考虑照明条件，以尽可能可靠地将虚拟对象融入现实生活。

除此之外，苹果现在拥有最快、最经济的移动处理器，ARKit 可以完全获得他们的资源。其他功能集，如 Metal 和 [SceneKit](https://en.wikipedia.org/wiki/SceneKit) ，也可以用来构建场景。ARKit 与大多数现代 iOS 设备的兼容性使其成为用于[移动应用开发](https://swagsoft.com.sg/mobile-app-development/)的最大规模的增强现实平台。

# 使用 ARKit 构建移动应用

苹果 ARKit 的主要功能是向应用开发者提供一套工具，以便他们在移动应用创建的过程中使用增强现实(AR)。无论是计划将创建的应用程序用于娱乐还是实际任务，使用的工具都是相同的:

*   设备摄像机接收视觉图像；
*   麦克风和其他传感器获取声音，读取振动和其他变化的信息；
*   处理器分析输入的数据，并与应用程序直接提交的命令进行协调。

配备了一套工具，AR iPhone 和 iPad 现在可以独立检测水平和垂直表面，确定光源和阴影，区分声音和人脸，等等。最新的处理器将完全应对输入信息的使用，并创建增强现实。

新工具包的可能性包括:

1.  在地图上自由导航，获取世界信息；
2.  测量距离和其他指标；
3.  三维绘图和建模；
4.  乘坐、飞行和其他过程的模拟器；
5.  娱乐和游戏应用程序，以这样或那样的方式基于与现实世界的交互。

例如，我们来看看在 ARKIt 上构建的 AR 应用程序中放置 3D 对象的过程。只需要几个简单的步骤。第一步是设置一个场景，并在 viewWillAppear 方法中运行它:

```
func setupScene() {
    let scene = SCNScene()
    sceneView.scene = scene
}

func setupConfiguration() {
    let configuration = ARWorldTrackingConfiguration()
    sceneView.session.run(configuration)
}
```

接下来，您需要向场景中添加一个 3D 对象(姑且称之为“对象”):

```
class Object: SCNNode {
    func loadModel() {
        guard let virtualObjectScene = SCNScene(named: "Object.scn") else { return }
        let wrapperNode = SCNNode()
        for child in virtualObjectScene.rootNode.childNodes {
            wrapperNode.addChildNode(child)
        }
        addChildNode(wrapperNode)
    }
}
```

一旦我们配置了 SCNNode，让我们开始初始化 object 类的一个对象，并在设置配置后补充它:

```
func addObject() {
    object.loadModel()
    sceneView.scene.rootNode.addChildNode(object)
}
```

## 用 ARKit 结合 AI 和 AR

人工智能一直是许多开发者感兴趣的主题。无论你是在开发一个个人助理，一个计算程序，或者仅仅是一个游戏，将这种新颖的技术引入到你的项目中会使它变得现代，引人入胜，并且绝对受欢迎。[在移动应用程序开发中利用人工智能](https://www.embedded-computing.com/home-page/decentralized-intelligence-how-enterprises-can-leverage-ai-blockchain-in-mobile-app-development)，您还可以提高数据安全性，改善客户服务，并赢得应用程序开发人员之间日益激烈的竞争。

合并 AR 和 AI 设计的最明显的方法是从场景中捕捉图片或声音，在 AI 模型中操作该信息，并利用该结果来施加特定的效果。例如，考虑以下模式:

*   **为场景中的图像添加标签**:你可以通过人工智能模型来处理相机画面，该模型将对图片进行分析/分类。一旦图像被分类，该位置将获得其 AR 标签。
*   **目标曝光**:一个相机画面被转移到一个 AI 模型上，这个模型决定了一个物体的位置和大小。位置数据随后被用于制作 hitboxes，以简化现实和数字对象的交互。
*   **位置评估**:AI 模型确定用于管理 AR 内容的对象的姿态。
*   **文本识别和解释**:人工智能模型可以识别、阅读和翻译内容。然后 AR 可以将其转移到 3D 环境中。
*   **声音识别**:AI 模型听某些催促 AR 效果的词。例如，如果你说“帽子”这个词，一顶虚拟的帽子就会出现在你的头上。

# 一锤定音

正如你所看到的，有了 ARKit 这样的现代工具，构建一个引人入胜的移动应用程序正在变成一件轻松愉快的事情。一个精心选择的开发方向和你对项目的热情的结合无疑会创造出一个成功而独特的产品。