# 2021 年最佳人工智能突破-综述

> 原文：<https://pub.towardsai.net/the-best-2021-ai-breakthroughs-d92def157d99?source=collection_archive---------0----------------------->

## [技术](https://towardsai.net/p/category/technology)

## 按发布日期排列的人工智能最新突破的精选列表，带有清晰的视频解释、更深入文章的链接和代码。

![](img/16f57054f477109db85edb407e7ba659.png)

由[凯利·西克玛](https://unsplash.com/@kellysikkema?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

虽然世界仍在复苏，但研究并没有放缓其疯狂的步伐，尤其是在人工智能领域。此外，今年还强调了许多重要方面，如道德方面、重要偏见、治理、透明度等等。人工智能和我们对人脑及其与人工智能的联系的理解正在不断发展，显示出在不久的将来改善我们生活质量的有前途的应用。然而，我们应该小心选择应用哪种技术。

> 科学不能告诉我们应该做什么，只能告诉我们能做什么—让-保罗·萨特，《存在与虚无》

这里是今年最有趣的研究论文，以防你错过其中的任何一篇。简而言之，它是人工智能和数据科学领域最新突破的精选列表，按发布日期排列，带有清晰的视频解释、更深入文章的链接和代码(如果适用)。享受阅读吧！

**每篇论文的完整参考资料都列在该存储库的末尾。**

订阅我的[时事通讯](http://eepurl.com/huGLT5)—AI 的最新更新每周都有讲解。

*随时给我发* [*消息*](https://www.louisbouchard.ai/contact/) *我可能错过的任何有趣的论文都可以添加到这个库中。*

*在* ***上给我加标签 Twitter****[*@ Whats _ AI*](https://twitter.com/Whats_AI)*或****LinkedIn****[*@ Louis(什么是 AI) Bouchard*](https://www.linkedin.com/in/whats-ai/) *如果分享一下名单！***

**去年错过了？看看这个: [2020 年:充满令人惊叹的人工智能论文的一年——一篇评论](https://github.com/louisfb01/Best_AI_paper_2020)**

**👀**如果你想支持我的工作**并使用 W & B(免费)来跟踪你的 ML 实验并使你的工作可复制或与团队合作，你可以通过遵循[这个指南](https://colab.research.google.com/github/louisfb01/examples/blob/master/colabs/pytorch/Simple_PyTorch_Integration.ipynb)来尝试一下！由于这里的大部分代码都是基于 PyTorch 的，我们认为分享一个在 PyTorch 上使用 W & B 的[快速入门指南](https://colab.research.google.com/github/louisfb01/examples/blob/master/colabs/pytorch/Simple_PyTorch_Integration.ipynb)会很有趣。**

**👉遵循[这个快速指南](https://colab.research.google.com/github/louisfb01/examples/blob/master/colabs/pytorch/Simple_PyTorch_Integration.ipynb)，在你的代码或下面的任何回复中使用相同的 W & B 行，让你的所有实验在你的 w & b 账户中自动跟踪！它不需要超过 5 分钟的时间来设置，并将改变你的生活，就像我改变你的生活一样！[这里有一个更高级的使用超参数扫描的指南](https://colab.research.google.com/github/louisfb01/examples/blob/master/colabs/pytorch/Organizing_Hyperparameter_Sweeps_in_PyTorch_with_W%26B.ipynb)，如果你有兴趣的话:)**

**🙌感谢[Weights&bias](https://wandb.ai/)赞助这个库和我一直在做的工作，感谢你们中的任何人使用这个链接并尝试 W & B！**

**[访问 GitHub 存储库中的完整列表](https://github.com/louisfb01/best_AI_papers_2021)**

## **在 15 分钟内观看完整的 2021 年倒带**

## **目录**

*   **DALL E:open ai 的零镜头文本到图像生成[1]**
*   **时尚:StyleGAN 插值优化的尝试[2]**
*   **驯服高分辨率图像合成的变压器[3]**
*   **人工智能中的快速思考和慢速思考[4]**
*   **航空图像中漂浮海洋大垃圾的自动检测和量化[5]**
*   **ShaRF:来自单个视图的形状调节辐射场[6]**
*   **生成对抗性变形金刚〔7〕**
*   **我们要求人工智能创建约会档案。你能向右滑动吗？[8]**
*   **Swin 转换器:使用移位窗口的分层视觉转换器[9]**
*   **图像 GANS 满足反向图形和可解释的 3D 神经渲染的可区分渲染[10]**
*   **深网:他们为视觉做过什么？[11]**
*   **无限自然:从单一图像生成自然场景的永久视图[12]**
*   **具有基于深度学习的手指控制的便携式独立神经假体手[13]**
*   **完全重新照明:学习为背景替换重新照明肖像[14]**
*   **LASR:从单目视频学习关节形状重建[15]**
*   **增强照片真实感增强[16]**
*   **DefakeHop:一种轻型高性能 Deepfake 检测器[17]**
*   **实时高分辨率照片真实感图像翻译:拉普拉斯金字塔翻译网络[18]**
*   **理发店:基于 GAN 的图像合成使用分段掩模[19]**
*   **TextStyleBrush:从一个例子看文本美学的转移[20]**
*   **用欧拉运动场制作动画[21]**
*   **CVPR 2021 最佳论文奖:长颈鹿——可控图像生成[22]**
*   **GitHub Copilot & Codex:评估代码训练的大型语言模型[23]**
*   **苹果:通过私人设备上的机器学习识别照片中的人[24]**
*   **用随机微分方程进行图像合成和编辑[25]**
*   **勾画自己的 GAN [26]**
*   **特斯拉的自动驾驶仪解释[27]**
*   **Styleclip:文本驱动的 StyleGAN 图像操作[28]**
*   **TimeLens:基于事件的视频帧插值[29]**
*   **单一视频的多样化生成成为可能[30]**
*   **使用雷达的深度生成模式的巧妙降水临近预报[31]**
*   **鸡尾酒叉问题:现实世界音轨的三干音频分离[32]**
*   **ADOP:近似可微分单像素点渲染[33]**
*   **(Style)CLIPDraw:文本到绘图合成中内容和样式的耦合[34]**
*   **SwinIR:使用 swin transformer 进行图像恢复[35]**
*   **EditGAN:高精度语义图像编辑[36]**
*   **城市 NeRF:在城市尺度上建造 NeRF[37]**
*   **ClipCap:图像字幕的剪辑前缀[38]**
*   **论文参考**

## **DALL E:open ai 的零镜头文本到图像生成[1]**

**OpenAI 成功训练了一个能够从文本字幕生成图像的网络。它与 GPT 3 号和 GPT 图像非常相似，产生了惊人的效果。**

**短视频讲解:**

**简短阅读:**

**[](/openais-dall-e-text-to-image-generation-explained-1f6fb4bb5a0a) [## OpenAI 的 DALL E:解释文本到图像的生成

### OpenAI 刚刚发布了解释 DALL-E 如何工作的论文！它被称为“零镜头文本到图像的生成”。

pub.towardsai.net](/openais-dall-e-text-to-image-generation-explained-1f6fb4bb5a0a) 

*   论文:[零投文本转图像生成](https://arxiv.org/pdf/2102.12092.pdf)
*   代码:[代码&用于 DALL E](https://github.com/openai/DALL-E) 的离散 VAE 的更多信息** 

## **时尚:StyleGAN 插值优化的尝试[2]**

**谷歌使用修改后的 StyleGAN2 架构创建了一个在线试衣间，在这里你可以只使用自己的图像自动试穿任何你想要的裤子或衬衫。**

*   **短视频讲解:**

**简短阅读:**

**[](/the-ai-powered-online-fitting-room-vogue-5f77c599832) [## 人工智能驱动的在线试衣间:VOGUE

### 谷歌使用了一种经过修改的 StyleGAN2 架构来创建一个在线试衣间，在这里你可以自动试穿任何…

pub.towardsai.net](/the-ai-powered-online-fitting-room-vogue-5f77c599832) 

*   论文:[时尚:试戴方式](https://vogue-try-on.github.io/static_files/resources/VOGUE-virtual-try-on.pdf)插值优化** 

## **驯服高分辨率图像合成的变压器[3]**

**TL；DR:他们将 GANs 和卷积方法的效率与 transformers 的表达能力结合起来，为语义指导的高质量图像合成提供了一种强大而省时的方法。**

*   **短视频讲解:**

**简短阅读:**

**[](/combining-the-transformers-expressivity-with-the-cnns-efficiency-for-high-resolution-image-synthesis-31c6767547da) [## 结合变形金刚的表现力和 CNN 的高分辨率图像的效率…

### TL；DR:他们将 GANs 和卷积方法的效率与变压器的表达能力结合起来…

pub.towardsai.net](/combining-the-transformers-expressivity-with-the-cnns-efficiency-for-high-resolution-image-synthesis-31c6767547da) 

*   论文:[驯服高分辨率图像合成的变形金刚](https://compvis.github.io/taming-transformers/)
*   代号:[驯服变形金刚](https://github.com/CompVis/taming-transformers)** 

## **人工智能中的快速思考和慢速思考[4]**

**从人类能力中汲取灵感，走向更通用、更可信的人工智能&给人工智能研究界的 10 个问题。**

*   **短视频讲解:**

**简短阅读:**

**[](/thinking-fast-and-slow-and-the-third-wave-of-ai-79156b5545e8) [## 思维的快慢与第三次人工智能浪潮

### 从人类能力中汲取灵感走向更通用和更可信的人工智能&人工智能的 10 个问题…

pub.towardsai.net](/thinking-fast-and-slow-and-the-third-wave-of-ai-79156b5545e8) 

*   论文:[思考中的快与慢艾](https://arxiv.org/abs/2010.06002)** 

## **航空图像中漂浮海洋大垃圾的自动检测和量化[5]**

**来自巴塞罗纳大学的奥代·加西亚-加林等人开发了一种基于深度学习的算法，能够从航空图像中检测和量化漂浮的垃圾。他们还开发了一个面向网络的应用程序，允许用户在海面图像中识别这些垃圾，称为浮动海洋宏观垃圾，或 FMML。**

*   **短视频讲解:**

**简短阅读:**

**[](/an-ai-software-able-to-detect-and-count-plastic-waste-in-the-ocean-7211aa0baf89) [## 一个人工智能软件能够检测和计算海洋中的塑料垃圾

### 它既聪明又简单，你可以在许多图像分类应用中使用相同的模型。

pub.towardsai.net](/an-ai-software-able-to-detect-and-count-plastic-waste-in-the-ocean-7211aa0baf89) 

*   论文:[航拍图像中漂浮海洋大型垃圾的自动检测和量化:介绍一种新的深度学习方法，连接到 R，环境污染中的 web 应用](https://doi.org/10.1016/j.envpol.2021.116490)
*   [点击此处获取代码](https://github.com/amonleong/MARLIT)** 

## **ShaRF:来自单个视图的形状调节辐射场[6]**

**想象一下，拍一张物体的照片，然后以 3D 形式插入到您正在制作的电影或视频游戏中，或者插入到 3D 场景中作为插图，这将是多么酷的事情。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/sharf-take-a-picture-from-a-real-life-object-and-create-a-3d-model-of-it-c6809806b32) [## ShaRF:从现实生活中的物体上拍一张照片，然后创建一个它的 3D 模型

### 想象一下，拍一张物体的照片，然后用 3D 方式插入到电影或视频中，那该有多酷…

pub.towardsai.net](/sharf-take-a-picture-from-a-real-life-object-and-create-a-3d-model-of-it-c6809806b32) 

*   论文: [ShaRF:来自单一视图的形状调节辐射场](https://arxiv.org/abs/2102.08860)
*   [点击此处获取代码](http://www.krematas.com/sharf/index.html)** 

## **生成对抗性变形金刚〔7〕**

**他们基本上利用了强大的 StyleGAN2 架构中变形金刚的注意力机制，使其更加强大！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/generative-adversarial-transformers-gansformers-explained-bf1fa76ef58d) [## 生成对抗性变形:GANsformers 解释

### 他们基本上利用了强大的 StyleGAN2 架构中变形金刚的注意力机制，使其更加…

pub.towardsai.net](/generative-adversarial-transformers-gansformers-explained-bf1fa76ef58d) 

*   论文:[生成对立的变形金刚](https://arxiv.org/pdf/2103.01209.pdf)
*   [点击此处获取代码](https://github.com/dorarad/gansformer)

> *订阅我的每周* [*时事通讯*](http://eepurl.com/huGLT5) *及时了解 AI 2022 年最新出版物！*** 

## **我们要求人工智能创建约会档案。你能向右滑动吗？[8]**

**你会在人工智能档案上向右滑动吗？你能区分真人和机器吗？这就是这项研究揭示的在约会应用程序上使用人工智能化妆的人。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/would-you-swipe-right-on-an-ai-profile-98dc8a4451ec) [## 你会在人工智能档案上向右滑动吗？

### 你能区分真人和机器吗？这就是这项研究揭示的在约会中使用人工智能制造的人…

pub.towardsai.net](/would-you-swipe-right-on-an-ai-profile-98dc8a4451ec) 

*   论文:[我们让人工智能创建约会档案。你能向右滑动吗？](https://studyonline.unsw.edu.au/blog/ai-generated-dating-profile)
*   [点击此处获取代码](https://colab.research.google.com/drive/1VLG8e7YSEwypxU-noRNhsv5dW4NfTGce#forceEdit=true&sandboxMode=true&scrollTo=aeXshJM-Cuaf)** 

## **Swin 转换器:使用移位窗口的分层视觉转换器[9]**

**变形金刚会取代计算机视觉中的 CNN 吗？在不到 5 分钟的时间内，您将通过一篇名为 Swin transformer 的新论文了解如何将 Transformer 架构应用于计算机视觉。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/will-transformers-replace-cnns-in-computer-vision-55657a196833) [## 变形金刚会取代计算机视觉中的 CNN 吗？

### 几分钟后，您将了解如何通过一种新的方式将 transformer 架构应用于计算机视觉

pub.towardsai.net](/will-transformers-replace-cnns-in-computer-vision-55657a196833) 

*   论文: [Swin Transformer:使用移位窗口的分层视觉转换器](https://arxiv.org/abs/2103.14030v1)
*   [点击此处获取代码](https://github.com/microsoft/Swin-Transformer)** 

## **图像 GANS 满足反向图形和可解释的 3D 神经渲染的可区分渲染[10]**

**这个被称为 GANverse3D 的有前途的模型只需要一个图像就可以创建一个可以定制和动画的 3D 人物！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/create-3d-models-from-images-ai-and-game-development-design-1835785b8563) [## 从图像创建三维模型！人工智能和游戏开发，设计…

### 这个被称为 GANverse3D 的有前途的模型只需要一个图像就可以创建一个可以定制和动画的 3D 人物！

pub.towardsai.net](/create-3d-models-from-images-ai-and-game-development-design-1835785b8563) 

*   论文:[图像 GANS 满足逆向图形的可微分渲染和可解释的 3D 神经渲染](https://arxiv.org/pdf/2010.09125.pdf)** 

## **深网:他们为视觉做过什么？[11]**

**“我将公开分享关于视觉应用深度网络的一切，它们的成功，以及我们必须解决的局限性。”**

*   **短视频讲解:**

*   **简短阅读:**

**[](/what-has-ai-done-for-computer-vision-3748f5958e07) [## AI 为计算机视觉做了什么？

### 关于当前深度网络的一切，他们为视觉应用做了什么。他们的成功和局限。

pub.towardsai.net](/what-has-ai-done-for-computer-vision-3748f5958e07) 

*   论文:[深网:他们为视觉做过什么？](https://arxiv.org/abs/1805.04025)** 

## **无限自然:从单一图像生成自然场景的永久视图[12]**

**视图合成的下一步:永久视图生成，目标是拍摄一幅图像，然后飞进去探索风景！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/infinite-nature-fly-into-an-image-and-explore-it-like-controlling-a-drone-541cab44b8f5) [## 无限自然:飞入一个影像，像控制无人机一样探索它！

### 视图合成的下一步:永久视图生成，其目标是获取一幅图像，然后…

pub.towardsai.net](/infinite-nature-fly-into-an-image-and-explore-it-like-controlling-a-drone-541cab44b8f5) 

*   论文:[无限自然:从单一图像生成自然场景的永久视图](https://arxiv.org/pdf/2012.09855.pdf)
*   [点击此处获取代码](https://github.com/google-research/google-research/tree/master/infinite_nature)
*   [Colab 演示](https://colab.research.google.com/github/google-research/google-research/blob/master/infinite_nature/infinite_nature_demo.ipynb#scrollTo=sCuRX1liUEVM)** 

## **具有基于深度学习的手指控制的便携式独立神经假体手[13]**

**有了这个人工智能驱动的神经接口，截肢者可以像生活一样灵活和直观地控制神经假体手。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/from-amputee-to-cyborg-with-this-ai-powered-hand-bdeb40f9b0d8) [## 用这只人工智能手从截肢者变成机器人！🦾

### 通过这种人工智能驱动的神经接口，截肢者可以像生活一样灵活地控制神经假体手

pub.towardsai.net](/from-amputee-to-cyborg-with-this-ai-powered-hand-bdeb40f9b0d8) 

*   论文:[便携式独立神经修复手，具有基于深度学习的手指控制](https://arxiv.org/abs/2103.13452)** 

## **完全重新照明:学习为背景替换重新照明肖像[14]**

**根据您添加的新背景的照明，正确地重新照亮任何肖像。你是否曾经想改变一张图片的背景，但却让它看起来很真实？如果你已经尝试过，你就会知道这并不简单。你不能在家里给自己拍张照片，然后给海滩换个背景。只是看起来很糟糕，不现实。任何人都会马上说“那是 PS 过的”。对于电影和专业视频，你需要完美的灯光和艺术家来再现高质量的图像，而这是超级昂贵的。你不可能用自己的照片做到这一点。还是可以？**

*   **短视频讲解:**

*   **简短阅读:**

**[](/change-your-portraits-backgrounds-with-realistic-lighting-b6f2ebeb1a85) [## 用真实的灯光改变你的肖像背景

### 根据您添加的新背景的照明，正确地重新照亮任何肖像。

pub.towardsai.net](/change-your-portraits-backgrounds-with-realistic-lighting-b6f2ebeb1a85) 

*   纸张:[整体重新照明:学习为背景替换重新照亮肖像](https://augmentedperception.github.io/total_relighting/total_relighting_paper.pdf)** 

## **LASR:从单目视频学习关节形状重建[15]**

**仅通过短视频作为输入，生成人类或动物运动的 3D 模型。这是一种仅从短视频作为输入来生成人类或动物运动的 3D 模型的新方法。事实上，它知道这是一个奇怪的形状，它可以移动，但仍然需要保持连接，因为这仍然是一个“对象”，而不只是许多对象在一起…**

*   **短视频讲解:**

*   **简短阅读:**

**[](/3d-reconstruction-from-videos-lasr-c29459399aed) [## 视频三维重建:LASR

### 仅通过短视频作为输入，生成人类或动物运动的 3D 模型。

pub.towardsai.net](/3d-reconstruction-from-videos-lasr-c29459399aed) 

*   论文: [LASR:从单目视频学习关节形状重建](https://openaccess.thecvf.com/content/CVPR2021/papers/Yang_LASR_Learning_Articulated_Shape_Reconstruction_From_a_Monocular_Video_CVPR_2021_paper.pdf)
*   [点击此处获取代码](https://github.com/google/lasr)** 

## **增强照片真实感增强[16]**

**这种人工智能可以应用到视频游戏中，并使每一帧看起来更加自然。来自英特尔实验室的研究人员刚刚发表了一篇名为“增强真实感增强”的论文。如果你认为这可能是“另一个甘”，把视频游戏的照片作为输入，并按照自然世界的风格改变它，让我改变你的想法。他们花了两年时间研究这个模型，让它变得非常健壮。它可以现场应用到视频游戏中，并使每一帧看起来更加自然。想象一下这样的可能性，你可以在游戏图形中投入更少的努力，使它超级稳定和完整，然后使用这种模式改进风格…**

*   **短视频讲解:**

*   **简短阅读:**

**[](/the-future-of-video-game-design-234cbeba7ab) [## 电子游戏设计的未来？

### 这种人工智能可以应用到视频游戏中，并使每一帧看起来更加自然。

pub.towardsai.net](/the-future-of-video-game-design-234cbeba7ab) 

*   论文:[增强真实感增强](http://vladlen.info/papers/EPE.pdf)
*   [点击此处获取代码](https://github.com/isl-org/PhotorealismEnhancement)** 

## **DefakeHop:一种轻型高性能 Deepfake 检测器[17]**

**2021 年如何识破深度假？突破性的美国陆军技术使用人工智能寻找 deepfakes。**

**虽然它们似乎一直都在那里，但第一个现实的 deepfake 直到 2017 年才出现。它从有史以来第一个自动生成的相似的假图像发展到今天的带有声音的视频中的一模一样的某人的复制品。**

**事实是，我们再也看不出真正的视频或图片与假的之间的区别了。我们如何区分什么是真实的，什么不是？如果一个人工智能可以完全生成音频文件或视频文件，它们如何在法庭上用作证据？那么，这篇新论文可能会提供这些问题的答案。这里的答案可能再次是人工智能的使用。“当我看到它时我会相信它”这句话可能很快就会变成“当人工智能告诉我相信它时我会相信它…”**

*   **短视频讲解:**

*   **简短阅读:**

**[](/how-to-spot-a-deep-fake-in-2021-3067ebb218fe) [## 2021 年如何识破深度假

### 突破性的美国陆军技术使用人工智能寻找 deepfakes。

pub.towardsai.net](/how-to-spot-a-deep-fake-in-2021-3067ebb218fe) 

*   论文: [DefakeHop:一款轻量级高性能深度打假检测器](https://arxiv.org/abs/2103.06929)** 

## **实时高分辨率照片真实感图像翻译:拉普拉斯金字塔翻译网络[18]**

**使用这种基于机器学习的新方法，实时将任何风格应用到您的 4K 图像中！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/computer-vision-fe47a52e76a5) [## 实时高分辨率真实感图像翻译

### 使用这种基于机器学习的新方法，实时将任何风格应用到您的 4K 图像中！

pub.towardsai.net](/computer-vision-fe47a52e76a5) 

*   论文:[实时高分辨率真实感图像翻译:拉普拉斯金字塔翻译网络](https://arxiv.org/pdf/2105.09188.pdf)
*   [点击此处获取代码](https://github.com/csjliang/LPTN)** 

## **理发店:基于 GAN 的图像合成使用分段掩模[19]**

**这篇文章本身并不是关于一项新技术。相反，它是关于 GANs 的一个令人兴奋的新应用。的确，你看到了标题，它不是 clickbait。这个人工智能可以转移你的头发，看看它会是什么样子，然后再做出改变…**

*   **短视频讲解:**

*   **简短阅读:**

**[](/barbershop-try-different-hairstyles-and-hair-colors-from-pictures-gans-e5138a8ee5f4) [## 理发店:尝试图片中不同的发型和发色

### 这个人工智能可以在改变之前转移你的头发，看看它会是什么样子。

pub.towardsai.net](/barbershop-try-different-hairstyles-and-hair-colors-from-pictures-gans-e5138a8ee5f4) 

*   论文:[理发店:使用分割遮罩的基于 GAN 的图像合成](https://arxiv.org/pdf/2106.01505.pdf)
*   [点击此处获取代码](https://github.com/ZPdesu/Barbershop)** 

## **TextStyleBrush:从一个例子看文本美学的转移[20]**

**这个新的脸书人工智能模型可以用你自己的语言直接翻译或编辑图像中的文本，遵循同样的风格！**

**想象你在另一个你不会说该语言的国家度假。你想试试当地的餐馆，但是他们的菜单用的是你不会说的语言。我认为这不会太难想象，因为我们大多数人已经面临这种情况，无论你看到菜单项或方向，你不能理解写的是什么。嗯，在 2020 年，你会拿出你的手机，谷歌翻译你看到的东西。2021 年你甚至不需要再打开谷歌翻译，试着把你看到的一个一个写下来翻译。相反，你可以简单地使用脸书人工智能的这个新模型，用你自己的语言翻译图像中的每一个文本…**

*   **短视频讲解:**

*   **简短阅读:**

**[](/translate-text-from-images-emulating-the-style-textstylebrush-1b73af3d0ac9) [## 从模拟样式的图像翻译文本:TextStyleBrush

### 这个新的脸书人工智能模型可以用你自己的语言翻译或编辑图像中的每一个文本，遵循相同的…

pub.towardsai.net](/translate-text-from-images-emulating-the-style-textstylebrush-1b73af3d0ac9) 

*   论文: [TextStyleBrush:从单个例子看文本美学的转移](https://arxiv.org/abs/2106.08385)
*   [点击此处获取代码](https://github.com/facebookresearch/IMGUR5K-Handwriting-Dataset?fbclid=IwAR0pRAxhf8Vg-5H3fA0BEaRrMeD21HfoCJ-so8V0qmWK7Ub21dvy_jqgiVo)

> *如果你也想阅读更多的研究论文，我推荐你阅读* [*我的文章*](/how-to-read-more-research-papers-7737e3770d7f) *，在那里我分享了寻找和阅读更多研究论文的最佳技巧。*** 

## **用欧拉运动场制作动画[21]**

**该模型拍摄一张照片，了解哪些粒子应该在移动，并在无限循环中逼真地动画化它们，同时完全保留照片的其余部分，仍然创建像这样看起来令人惊叹的视频…**

*   **短视频讲解:**

*   **简短阅读:**

**[](/create-realistic-animated-looping-videos-from-pictures-58debf6f139) [## 从图片创建逼真的动画循环视频

### 这个模型拍一张照片，了解哪些粒子应该在移动，并逼真地将它们动画化…

pub.towardsai.net](/create-realistic-animated-looping-videos-from-pictures-58debf6f139) 

*   论文:[用欧拉运动场制作图片动画](https://arxiv.org/abs/2011.15128)
*   [点击此处获取代码](https://eulerian.cs.washington.edu/)** 

## **CVPR 2021 最佳论文奖:长颈鹿——可控图像生成[22]**

**使用改进的 GAN 架构，他们可以移动图像中的对象，而不会影响背景或其他对象！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/cvpr-2021-best-paper-award-giraffe-controllable-image-generation-24eac0001ca4) [## CVPR 2021 年最佳论文奖:长颈鹿——可控图像生成

### 使用改良的氮化镓架构，他们甚至可以移动图像中的物体，而不影响背景或…

pub.towardsai.net](/cvpr-2021-best-paper-award-giraffe-controllable-image-generation-24eac0001ca4) 

*   论文:[长颈鹿:将场景表示为合成生成神经特征场](http://www.cvlibs.net/publications/Niemeyer2021CVPR.pdf)
*   [点击此处获取代码](https://github.com/autonomousvision/giraffe)** 

## **GitHub Copilot & Codex:评估代码训练的大型语言模型[23]**

**了解 OpenAI 的这个新模型如何从单词生成代码！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/openais-new-code-generator-github-copilot-and-codex-6031d65e47c1) [## OpenAI 的新代码生成器:GitHub Copilot(和 Codex)

### 了解这个人工智能如何从单词中生成代码

pub.towardsai.net](/openais-new-code-generator-github-copilot-and-codex-6031d65e47c1) 

*   论文:[评估基于代码](https://arxiv.org/pdf/2107.03374.pdf)训练的大型语言模型
*   [点击此处获取代码](https://copilot.github.com/)** 

## **苹果:通过私人设备上的机器学习识别照片中的人[24]**

**使用多种基于机器学习的算法在你的设备上私下运行，苹果允许你在 iOS 15 上准确地管理和组织你的图像和视频。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/how-apple-photos-recognizes-people-in-private-photos-using-machine-learning-8c7f4d60f914) [## Apple Photos 如何使用机器学习识别私人照片中的人

### 使用多种基于机器学习的算法在您的设备上秘密运行，Apple 允许您准确地…

pub.towardsai.net](/how-apple-photos-recognizes-people-in-private-photos-using-machine-learning-8c7f4d60f914) 

*   论文:[通过私有设备上的机器学习识别照片中的人](https://machinelearning.apple.com/research/recognizing-people-photos)** 

## **用随机微分方程进行图像合成和编辑[25]**

**告别复杂的 GAN 和变压器架构，实现图像生成！斯坦福大学和卡耐基梅隆大学的孟等人提出的这种新方法可以从任何基于用户的输入中生成新图像。即使像我这样没有艺术技巧的人，现在也可以从快速草图中生成美丽的图像或修改…**

*   **短视频讲解:**

*   **简短阅读:**

**[](/image-synthesis-and-editing-from-hand-drawn-color-strokes-sdedit-8da8592182cb) [## 手绘彩色笔画的图像合成和编辑。

### 告别复杂的 GAN 和变压器架构，实现图像生成。这种新方法可以生成新的图像…

pub.towardsai.net](/image-synthesis-and-editing-from-hand-drawn-color-strokes-sdedit-8da8592182cb) 

*   论文:[用随机微分方程进行图像合成与编辑](https://arxiv.org/pdf/2108.01073.pdf)
*   [点击此处获取代码](https://github.com/ermongroup/SDEdit)
*   [Colab 演示](https://colab.research.google.com/drive/1KkLS53PndXKQpPlS1iK-k1nRQYmlb4aO?usp=sharing)** 

## **勾画自己的 GAN [26]**

**通过根据草图生成图像，使 GANs 训练对每个人来说都更容易！事实上，有了这种新方法，你可以根据你能提供的最简单的知识类型来控制你的 GAN 的输出:手绘草图。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/make-gans-training-easier-for-everyone-generate-images-following-a-sketch-a2bc4fd6ec8c) [## 让 GANs 训练对每个人都更容易:根据草图生成图像

### 根据你能提供的最简单的知识类型控制 GANs 输出:手绘草图。

pub.towardsai.net](/make-gans-training-easier-for-everyone-generate-images-following-a-sketch-a2bc4fd6ec8c) 

*   论文:[勾画自己的甘](https://arxiv.org/abs/2108.02774)
*   [点击此处获取代码](https://github.com/PeterWang512/GANSketching)** 

## **特斯拉的自动驾驶仪解释[27]**

**如果你想知道特斯拉汽车如何不仅能看到其他车辆，还能在道路上导航，这就是你一直在等待的视频。几天前是第一个特斯拉人工智能日，特斯拉人工智能总监 Andrej Karpathy 和其他人展示了特斯拉的自动驾驶仪如何通过他们的八个摄像头进行图像采集，以及在道路上的导航过程。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/tesla-ai-day-in-10-minute-show-does-teslas-autopilot-work-3990252082dc) [## 特斯拉人工智能日亮点&自动驾驶仪如何工作

### 安德烈·卡帕西(Andrej Karpathy)关于特斯拉自动驾驶仪的演讲在不到 10 分钟的时间里就解释清楚了

pub.towardsai.net](/tesla-ai-day-in-10-minute-show-does-teslas-autopilot-work-3990252082dc)** 

## **风格剪辑:文本驱动的风格处理[28]**

**人工智能可以生成图像，然后，使用大量的脑力和反复试验，研究人员可以按照特定的风格控制结果。现在，有了这个新模型，你可以只用文本就能做到！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/manipulate-real-images-with-text-25b9f583e292) [## 用文本处理真实图像

### 创意艺术家的人工智能！StyleCLIP 解释

pub.towardsai.net](/manipulate-real-images-with-text-25b9f583e292) 

*   Paper: [Styleclip:文本驱动的 StyleGAN 图像操作。](https://arxiv.org/abs/2103.17249)
*   [点击此处获取代码](https://github.com/orpatashnik/StyleCLIP)
*   [Colab 演示](https://colab.research.google.com/github/orpatashnik/StyleCLIP/blob/main/notebooks/StyleCLIP_global.ipynb)** 

## **TimeLens:基于事件的视频帧插值[29]**

**TimeLens 可以理解视频帧之间的粒子运动，以我们肉眼无法看到的速度重建真实发生的事情。事实上，它实现了我们的智能手机和其他型号之前无法达到的效果！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/change-video-into-slow-motion-with-ai-timelens-explained-4281d97c9b9d) [## 用 AI 把视频换成慢动作！TimeLens 解释道

### 时间镜头可以理解视频帧之间的粒子运动，以重建真正的…

pub.towardsai.net](/change-video-into-slow-motion-with-ai-timelens-explained-4281d97c9b9d) 

*   论文: [TimeLens:基于事件的视频帧插值](http://rpg.ifi.uzh.ch/docs/CVPR21_Gehrig.pdf)
*   [点击此处获取代码](https://github.com/uzh-rpg/rpg_timelens)

> *订阅我的每周* [*时事通讯*](http://eepurl.com/huGLT5) *及时了解 AI 2022 年最新出版物！*** 

## **单一视频的多样化生成成为可能[30]**

**你有没有想过剪辑一个视频？删除或添加某人，更改背景，使其持续更长时间，或者更改分辨率以适应特定的纵横比，而不压缩或拉伸它。对于那些已经开展过广告活动的人来说，你肯定希望有不同的视频来进行 AB 测试，看看什么效果最好。Niv Haim 等人的这项新研究可以帮助你在一个高清视频中完成所有这些事情！**

**的确，使用一个简单的视频，你可以在几秒钟或几分钟内完成我刚才提到的任何高质量视频的任务。你基本上可以把它用于任何你想到的视频操作或视频生成应用。它甚至在所有方面都优于 GANs，并且不使用任何深度学习的花哨研究，也不需要庞大而不切实际的数据集！最棒的是，这项技术可以扩展到高分辨率视频。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/diverse-generation-from-a-single-video-made-possible-no-dataset-or-deep-learning-required-f4377c0c56bf) [## 从单个视频生成不同的内容成为可能—不需要数据集或深度学习！

### 这种模式可以做任何视频操作或视频生成应用程序，你记住了！

pub.towardsai.net](/diverse-generation-from-a-single-video-made-possible-no-dataset-or-deep-learning-required-f4377c0c56bf) 

*   论文:[单一视频的多样化生成成为可能](https://arxiv.org/abs/2109.08591)
*   [点击此处获取代码](https://nivha.github.io/vgpnn/)** 

## **使用雷达的深度生成模式的巧妙降水临近预报[31]**

**DeepMind 刚刚发布了一个生成模型，该模型在 89%的情况下能够胜过广泛使用的临近预报方法，其准确性和实用性由 50 多位专家气象学家评估！他们的模型侧重于预测未来 2 小时的降水量，并取得了令人惊讶的好成绩。这是一个生成模型，这意味着它将生成预测，而不是简单地预测它们。它基本上利用过去的雷达数据来创建未来的雷达数据。因此，利用过去的时间和空间成分，他们可以生成它在不久的将来的样子。**

**您可以看到这与 Snapchat 滤镜一样，获取您的面部，并生成一个带有修改的新面部。为了训练这样一个生成模型，你需要来自人脸和你想要生成的人脸类型的大量数据。然后，使用经过许多小时训练的非常相似的模型，你将拥有一个强大的生成模型。这种模型通常使用 GANs 架构进行训练，然后独立使用生成器模型。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/artificial-intelligence-4d7b12727ac4) [## DeepMind 使用人工智能来预测更准确的天气预报

### 50 多名专家气象学家评估 DeepMind 的新模型在 89%的情况下击败了当前的临近预报方法，因为它…

pub.towardsai.net](/artificial-intelligence-4d7b12727ac4) 

*   论文:[巧用雷达深度生成模式进行降水临近预报](https://www.nature.com/articles/s41586-021-03854-z)
*   [点击此处获取代码](https://github.com/deepmind/deepmind-research/tree/master/nowcasting)** 

## **鸡尾酒叉问题:现实世界音轨的三干音频分离[32]**

**你有没有收听过一个视频或电视节目，而演员完全听不见，或者音乐太大声？嗯，这个问题，也叫鸡尾酒会问题，可能再也不会发生了。三菱和印第安纳大学刚刚发布了一个新的模型和一个新的数据集来处理识别正确的配乐的任务。例如，如果我们把刚才播放的同一个音频片段的音乐音量调得太大，你可以简单地调高或调低音轨，让语音比音乐更重要。**

**这里的问题是从复杂的声学场景中分离出任何独立的声源，比如电影场景或 youtube 视频，其中一些声音不平衡。有时你根本听不到一些演员的声音，因为背景中有音乐、爆炸声或其他环境声音。嗯，如果你成功地隔离了一个音轨中的不同类别，这意味着你也可以只调高或调低其中一个类别，就像把音乐调低一点，以便正确地听到所有其他演员的声音。这正是研究人员所取得的成果。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/separate-voice-music-and-sound-effects-with-ai-9a652f4f9cfc) [## 用人工智能分离语音、音乐和音效

### 如果我们在播放音乐的时候声音太大，你只需要调高音量，调低音乐就可以了！

pub.towardsai.net](/separate-voice-music-and-sound-effects-with-ai-9a652f4f9cfc) 

*   论文:[鸡尾酒叉问题:现实世界配乐的三茎音频分离](https://arxiv.org/pdf/2110.09958.pdf)
*   [点击此处获取代码](https://cocktail-fork.github.io/)** 

## **ADOP:近似可微分单像素点渲染[33]**

**想象一下，你想从你拍的一堆照片中生成一个 3D 模型或者简单的一个流畅的视频。嗯，现在有可能了！我不想给出太多，但结果简直是惊人的，你需要自己检查一下！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/ai-synthesizes-smooth-videos-from-a-couple-of-images-aeb288493b3d) [## 人工智能从一对夫妇的图像合成流畅的视频！

### 让我们从几张照片中构建 3D 模型…

pub.towardsai.net](/ai-synthesizes-smooth-videos-from-a-couple-of-images-aeb288493b3d) 

*   论文: [ADOP:近似可微单像素点渲染](https://arxiv.org/pdf/2110.06635.pdf)
*   [点击此处获取代码](https://github.com/darglein/ADOP)** 

## **(Style)CLIPDraw:文本到绘图合成中内容和样式的耦合[34]**

**你有没有梦想过采用图片的风格，比如左边这个很酷的抖音绘画风格，并将其应用到你选择的新图片中？是的，我做到了，而且从来没有这么容易做到。事实上，你甚至可以只通过文本来实现，现在就可以用这种新方法和他们为每个人提供的 Google Colab 笔记本来尝试。只需拍下你想要复制的样式的图片，输入你想要生成的文本，这个算法就会从中生成一张新的图片！回头看看上面的结果就知道了，这么大的进步！结果非常令人印象深刻，尤其是如果您考虑到它们是由单行文本构成的！**

*   **短视频讲解:**

*   **简短阅读:**

**[](/text-to-drawing-synthesis-with-artistic-control-clipdraw-styleclipdraw-dd56fa208bea) [## 具有艺术控制的文本到绘图合成| CLIPDraw & StyleCLIPDraw

### 给你想要复制的风格拍张照，输入文字，算法会从中生成一张新的图片！

pub.towardsai.net](/text-to-drawing-synthesis-with-artistic-control-clipdraw-styleclipdraw-dd56fa208bea) 

*   Paper (CLIPDraw): [CLIPDraw:通过语言图像编码器探索文本到绘图的合成](https://arxiv.org/abs/2106.14843)
*   paper(StyleCLIPDraw):[StyleCLIPDraw:文本到绘图合成中内容和样式的耦合](https://arxiv.org/abs/2111.03133)
*   [CLIPDraw Colab 演示](https://colab.research.google.com/github/kvfrans/clipdraw/blob/main/clipdraw.ipynb)
*   [StyleCLIPDraw Colab 演示](https://colab.research.google.com/github/pschaldenbrand/StyleCLIPDraw/blob/master/Style_ClipDraw.ipynb)** 

## **SwinIR:使用 swin transformer 进行图像恢复[35]**

**你是否曾经有过一个你非常喜欢的图片，但只能找到一个小版本，看起来像下面左边的这张图片？如果你能把这张图片放大两倍，那该有多酷？这很棒，但是如果你能把它的清晰度提高四到八倍呢？现在我们在谈话，看看那个。**

**在这里，我们将图像的分辨率提高了四倍，这意味着我们有四倍多的高度和宽度像素来获得更多的细节，使它看起来更加平滑。最棒的是，这是在几秒钟内完成的，完全自动，几乎可以处理任何图像。哦，你甚至可以通过他们提供的演示自己使用它…**

*   **短视频讲解:**

*   **简短阅读:**

**[](/this-ai-makes-blurry-faces-look-8-times-sharper-swinir-photo-upsampling-b41d394b41e9) [## 这个人工智能使模糊的脸看起来清晰 8 倍！SwinIR:照片上采样

### 用 AI 把你的小 512 像素大图转换成 4k！

pub.towardsai.net](/this-ai-makes-blurry-faces-look-8-times-sharper-swinir-photo-upsampling-b41d394b41e9) 

*   论文: [SwinIR:使用 swin transformer 进行图像恢复](https://arxiv.org/abs/2108.10257)
*   [点击此处获取代码](https://github.com/JingyunLiang/SwinIR)
*   [演示](https://replicate.ai/jingyunliang/swinir)** 

## **EditGAN:高精度语义图像编辑[36]**

**控制快速草稿中的任何功能，它将只编辑你想要的，保持图像的其余部分不变！NVIDIA，MIT 和 UofT 基于 GANs 的草图模型的 SOTA 图像编辑。**

*   **短视频讲解:**

*   **简短阅读:**

**[](/image-editing-from-sketches-editgan-4cacca609e2d) [## 从草图编辑图像:EditGAN

### 控制快速草稿中的任何功能，它将只编辑你想要的，保持图像的其余部分不变！SOTA…

pub.towardsai.net](/image-editing-from-sketches-editgan-4cacca609e2d) 

*   论文: [EditGAN:高精度语义图像编辑](https://arxiv.org/abs/2111.03186)
*   [点击此处获取代码(即将发布)](https://nv-tlabs.github.io/editGAN/)** 

## **城市 NeRF:在城市尺度上建造 NeRF[37]**

**这个模型被称为 CityNeRF，它是从 NeRF 发展而来的，我之前在我的频道中介绍过。NeRF 是首批使用辐射场和机器学习从图像中构建 3D 模型的模型之一。但是 NeRF 并不是那么有效，而且只适用于单一规模。在这里，CityNeRF 同时应用于卫星和地面图像，为任何视点生成各种 3D 模型比例。简而言之，他们将 NeRF 带到了城市规模。但是怎么做呢？**

*   **短视频讲解:**

*   **简短阅读:**

**[](/technology-fcb0fbfa9c00) [## CityNeRF:城市比例的 3D 渲染！

### 以任何比例生成具有高质量细节的城市级 3D 场景！

pub.towardsai.net](/technology-fcb0fbfa9c00) 

*   论文:[城市 NeRF:城市规模的建筑 NeRF](https://arxiv.org/pdf/2112.05504.pdf)
*   [点击此处获取代码(即将发布)](https://city-super.github.io/citynerf/)** 

## **ClipCap:图像字幕的剪辑前缀[38]**

**我们已经看到人工智能使用 GANs 从其他图像生成图像。然后，有模型能够使用文本生成有问题的图像。2021 年初，DALL-E 发表，击败了之前所有使用 CLIP 从文本输入中生成图像的尝试，CLIP 是一种将图像与文本链接起来的模型。一个非常相似的任务叫做图像字幕，听起来可能很简单，但实际上也很复杂。它是机器生成图像的自然描述的能力。简单地标记你在图像中看到的物体是很容易的，但要理解在一张二维图像中发生了什么却是另一个挑战，这个新模型做得非常好…**

*   **短视频讲解:**

*   **简短阅读:**

**[](/image-captioning-with-clip-and-gpt-d0cb3f3fddda) [## 带剪辑和 GPT 的图像字幕

### 使用剪辑和 GPT 模型轻松生成图像的文本描述！

pub.towardsai.net](/image-captioning-with-clip-and-gpt-d0cb3f3fddda) 

*   Paper: [ClipCap:图像字幕的剪辑前缀](https://arxiv.org/abs/2111.09734)
*   [点击此处获取代码](https://github.com/rmokady/CLIP_prefix_caption)
*   [点击这里观看 Colab 演示](https://colab.research.google.com/drive/1tuoAC5F4sC7qid56Z0ap-stR3rwdk0ZV?usp=sharing)** 

> ***如果你想阅读更多的论文并有更广阔的视野，这里有另一个涵盖 2020 年的伟大知识库:* [*2020:充满令人惊叹的人工智能论文的一年——回顾*](https://github.com/louisfb01/Best_AI_paper_2020) *，并随时订阅我的每周* [*时事通讯*](http://eepurl.com/huGLT5) *，了解 2022 年人工智能的最新出版物！***

***在* ***上给我加标签推特****[*@ Whats _ AI*](https://twitter.com/Whats_AI)*或****LinkedIn****[*@ Louis(什么是 AI) Bouchard*](https://www.linkedin.com/in/whats-ai/) *如果分享名单！*****

## **论文参考**

**[1] A. Ramesh 等，零拍文本到图像的生成，2021。arXiv:2102.12092**

**[2] Lewis，Kathleen M 等人，(2021)，《时尚:通过 StyleGAN 插值优化试穿》。**

**[3]驯服高分辨率图像合成的变压器，Esser 等人，2020 年。**

**[4]《思考的快与慢》载艾、布奇等人，(2020)，。**

**[5]https://doi.org/10.1016/j.envpol.2021.116490 奥代·加西亚-加林等，航拍图像中漂浮海洋大型垃圾的自动检测和量化:介绍一种连接到网络应用的新型深度学习方法，载于 R，环境污染，[。](https://doi.org/10.1016/j.envpol.2021.116490)**

**[6] Rematas，k .，Martin-Brualla，r .，和 Ferrari，v .，“ShaRF:来自单一视图的形状调节辐射场”，(2021)，【https://arxiv.org/abs/2102.08860**

**[7]德鲁·a·哈德森和 c·劳伦斯·兹尼克，《生成性对抗性变形金刚》，(2021)**

**[8]桑德拉·布莱恩特(Sandra Bryant)等人，“我们要求人工智能创建约会档案。你会向右滑动吗？”，(2021)，UNSW 悉尼博客。**

**[9]刘，z .等，2021，“Swin 变压器:使用移位窗口的分层视觉变压器”，arXiv 预印本【https://arxiv.org/abs/2103.14030v1】**

**[10]张，y，陈，w，凌，h，高，j，张，y，Torralba，a .和 Fidler，s .，2020。图像甘满足逆向图形和可解释的 3d 神经渲染的可区分渲染。arXiv 预印本 arXiv:2010.09125**

**[11]尤耶和刘，2021 年。深网:他们为视觉做过什么？。《国际计算机视觉杂志》，129(3)，第 781–802 页，[https://arxiv.org/abs/1805.04025](https://arxiv.org/abs/1805.04025)。**

**[12]刘，a .，塔克，r .，贾帕尼，v .，马卡迪亚，a .，斯内夫利，n .，金泽，a .，2020 年。无限自然:从单一图像生成自然场景的永久视图，[https://arxiv.org/pdf/2012.09855.pdf](https://arxiv.org/pdf/2012.09855.pdf)**

**[13] Nguyen & Drealan 等人(2021)一种具有基于深度学习的手指控制的便携式独立神经假体手:[https://arxiv.org/abs/2103.13452](https://arxiv.org/abs/2103.13452)**

**[14] Pandey 等人，2021，Total Relighting:学习为背景替换重新照亮人像，doi: 10.1145/3450626.3459872，[https://augmented perception . github . io/Total _ re lighting/Total _ re lighting _ paper . pdf](https://augmentedperception.github.io/total_relighting/total_relighting_paper.pdf)。**

**[15]耿山阳等，(2021)，:从单目视频学习关节形状重建，，。**

**[16]里克特，阿布·阿尔海贾，科尔敦，(2021)，“增强照片真实感增强”，[https://intel-isl.github.io/PhotorealismEnhancement/](https://intel-isl.github.io/PhotorealismEnhancement/)。**

**[17] DeepFakeHop:陈，洪硕，等，(2021)，“DeepFakeHop:一种轻量级高性能 Deepfake 检测器。”ArXiv abs/2103.06929。**

**[18]梁，解，曾，惠，张，雷，(2021)，“高分辨率真实感图像实时翻译:拉普拉斯金字塔翻译网络”，【https://export.arxiv.org/pdf/2105.09188.pdf】。**

**[19]朱佩豪等，(2021)，理发店，【https://arxiv.org/pdf/2106.01505.pdf】。**

**[20] Praveen Krishnan，Rama Kovvuri，Guan Pang，Boris Vassilev，and Tal Hassner，脸书·艾(2021)，“文本风格刷:从单个例子转移文本美学”。**

**Holynski，Aleksander 等人，“用欧拉运动场制作动画”IEEE/CVF 计算机视觉和模式识别会议录。2021.**

**[22] Michael Niemeyer 和 Andreas Geiger，(2021)，“长颈鹿:将场景表示为合成生成神经特征场”，发表于 CVPR 2021 年。**

**[23] Chen，m .，Tworek，j .，Jun，h .，Yuan，q .，Pinto，H.P.D.O .，Kaplan，j .，Edwards，h .，y .，Joseph，n .，Brockman，g .和 Ray，a .，2021 年。评估基于代码训练的大型语言模型。arXiv 预印本 arXiv:2107.03374。**

**[24]苹果，“通过私人设备上的机器学习识别照片中的人”，(2021 年)，[https://Machine Learning . Apple . com/research/recognized-People-Photos](https://machinelearning.apple.com/research/recognizing-people-photos)**

**[25]孟，c，宋，杨，宋，吴，朱，朱和埃蒙，s，2021。Sdedit:用随机微分方程进行图像合成和编辑。arXiv 预印本 arXiv:2108.01073。**

**[26]王士友、鲍、朱，2021。画出你自己的 GAN。IEEE/CVF 国际计算机视觉会议论文集(第 14050-14060 页)。**

**[27]“特斯拉 AI 日”，特斯拉，2021 年 8 月 19 日，[https://youtu.be/j0z4FweCy4M](https://youtu.be/j0z4FweCy4M)**

**[28] Patashnik，Or 等人(2021)，“样式剪辑:样式图像的文本驱动操作。”，[https://arxiv.org/abs/2103.17249](https://arxiv.org/abs/2103.17249)**

**[29]斯捷潘·图利亚科夫*、丹尼尔·格赫里希*、斯塔马蒂亚斯·乔戈里斯、朱利叶斯·埃尔巴赫、马蒂亚斯·格赫里希、元佑·李、大卫·斯卡拉穆扎，TimeLens:基于事件的视频帧内插，IEEE 计算机视觉和模式识别会议(CVPR)，纳什维尔，2021 年，[http://rpg.ifi.uzh.ch/docs/CVPR21_Gehrig.pdf](http://rpg.ifi.uzh.ch/docs/CVPR21_Gehrig.pdf)**

**[30]哈伊姆、范斯坦、格拉诺特、肖彻、巴贡、戴克尔和伊拉尼(2021 年)。多样化的一代从一个单一的视频成为可能，【https://arxiv.org/abs/2109.08591】T2。**

**[31]拉武里、伦克、王绍博、坎金、拉姆、米罗夫斯基、菲茨西蒙斯、阿萨纳夏杜、卡舍姆、马奇和普鲁登，2021 年。使用雷达深度生成模式的巧用降水临近预报，【https://www.nature.com/articles/s41586-021-03854-z **

**[32]彼得曼、威彻恩、王和鲁(2021 年)。鸡尾酒叉问题:现实世界音轨的三干音频分离。[https://arxiv.org/pdf/2110.09958.pdf](https://arxiv.org/pdf/2110.09958.pdf)。**

**[33]吕克特博士、弗兰克博士和斯塔明格博士，2021 年。https://arxiv.org/pdf/2110.06635.pdf[ADOP:近似可微分单像素点绘制。](https://arxiv.org/pdf/2110.06635.pdf)**

**[34] a) CLIPDraw:通过语言-图像编码器探索文本到绘图的合成。StyleCLIPDraw:文本到绘图合成中内容和样式的耦合。**

**[35]梁军、曹军、孙、张、范古尔和，2021 年。SwinIR:使用 swin transformer 进行图像恢复。IEEE/CVF 国际计算机视觉会议论文集(第 1833-1844 页)。**

**[36] Ling，h .，Kreis，k .，Li，d .，Kim，S.W .，Torralba，a .和 Fidler，s .，2021 年 5 月。EditGAN:高精度语义图像编辑。在第三十五届神经信息处理系统会议上。**

**[37]杨，，徐，李，潘，x，赵，n，饶，a，西奥多，c，戴，b 和林，2021。城市 NeRF:在城市尺度上建造 NeRF。**

**[38]莫凯迪、赫兹和伯尔曼诺，2021 年。ClipCap:图像字幕的剪辑前缀。[https://arxiv.org/abs/2111.09734](https://arxiv.org/abs/2111.09734)**