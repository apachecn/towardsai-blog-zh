# 2022 年 12 款语音识别模型；其中一个在 Github 上有 2 万颗星星

> 原文：<https://pub.towardsai.net/12-speech-recognition-models-in-2022-one-of-these-has-20k-stars-on-github-6ed989b24cb5?source=collection_archive---------0----------------------->

## 了解 12 种更重要的语音识别引擎和 API

![](img/4ab9e3d574989669bb5344c1dc6ae744.png)

Pexels 的 Matthew Hintz

在自然语言处理中，语音识别[11]是将口语单词转换成文本的过程。它也被称为自动语音识别或 ASR。

# **语音识别的 3 个高级描述:**

1.语音识别是将口语单词转换成文本的过程。

2.语音识别系统使用声学和语言模型来识别口语单词。声学模型基于口语单词的声音，而语言模型基于语言的语法和结构。

3.语音识别系统可用于听写和转录，也可用于命令和控制。

# **语音识别实施流程中要采取的 3 个一般步骤:**

1.预处理:该步骤清理原始音频信号，并为特征提取做准备。

2.特征提取:该步骤从预处理的音频信号中提取独特的特征，这些特征可用于识别所说的单词。

3.解码:这一步使用提取的特征将语音信号转换成文本。

![](img/09acdd87563d785ed8b96ac34f5a2eec.png)

来自 Pexels 的 Amos Getanda

# **使用语音识别的 8 个用例:**

1.自动语音识别可用于将音频文件转录到文本中；这个用例可以帮助转录会议笔记、讲座或其他音频记录。

2.ASR 可以用来为视频生成字幕。

**3。用于创建录音的可搜索索引，以支持在大型音频文件中查找特定信息的用例。**

4.用于识别录音的说话者。这对取证或其他应用很有帮助。

5.ASR 可用于从一种语言翻译到另一种语言，这种使用案例对于与录音中的人说不同语言的人很有帮助。

6.它可以用来创建一个虚拟助理来支持无数的任务，如设置提醒，发送电子邮件，通过电话系统提供客户服务，或搜索网页。

7.用于控制计算机或其他设备。这对残障人士或免提操作非常有用。

**8。ASR 可用于为智能设备创建声控命令或控制。**

隐马尔可夫模型(HMM)将在这篇文章中被多次提及。简单地说，HMM 是一种统计模型，用于描述一系列观察到的事件和一组隐藏状态之间的关系。

![](img/97bce70dd32c91d03074a21acd8059da.png)

来自 Pexels 的 Werner Pfennig

# **12 语音学习实现:**

1.Python 的语音识别库。它支持多种 API 和算法引擎，全部在线或离线实现[13]。支持的一些 API/引擎包括(1) CMU 斯芬克斯(离线工作)；(2)谷歌云语音 API(3)wit . ai；(4)微软必应语音识别；(5) IBM 语音转文本；以及(6) Snowboy 热门词检测(离线工作)[13]。

2.Eesen:一个端到端的语音识别工具包。Eesen 是一个基于神经网络的语音识别系统(基于训练单个递归神经网络[13])，它使用深度神经网络来模拟语音的声学模式。该系统被设计成端到端的，这意味着它不需要手工制作的功能或语音知识。Eesen 在一个大型语音记录数据集上接受训练，可以学习识别任何声学环境中的语音。该系统还对背景噪声具有鲁棒性，并可用于实时语音识别。

**Eesen 已经被证明在准确性和速度方面优于传统的语音识别系统。**

此外，该系统是可扩展的，可以用于大规模的语音识别任务。

3.TensorFlowASR:几乎是 Tensorflow 2 中最先进的 ASR。TensorFlowASR 是用于语音识别的自然语言处理工具。

**基于深度学习平台 TensorFlow，可用于训练和部署语音识别模型。**

TensorFlowASR 的一些使用方法包括:

> —在大型数据集上训练语音识别模型
> 
> —在边缘设备上部署语音识别模型
> 
> —构建定制的语音识别应用程序
> 
> —针对特定领域微调语音识别模型
> 
> —可视化和调试语音识别模型

4.Vosk:适用于 Android、iOS、Raspberry Pi 以及使用 Python、Java、C#和 Node 的服务器的离线语音识别 API[15]。Vosk 是一个用于语音识别的开源工具包，可用于开发新的语音识别模型。Vosk 可用于为各种平台(包括移动设备)构建语音识别应用程序。它目前支持 20 多种语言的语音识别[15]，其路线图中还计划了更多。Vosk 团队表示，他们模型不仅小(50 Mb) [15]，而且提供“具有流式 API、可重新配置的词汇和说话者识别的零延迟响应”[15]。

![](img/9b90e6309d58c4ef538ea0019fb01790.png)

来自 Pexels 的乔治·米尔顿

5.**deep speech(Github 上差不多 20k 星)**:离线、设备上的语音转文本引擎。DeepSpeech 是一个开源的语音识别引擎，可以用来处理语音并将其转换为文本。**它使用深度神经网络来解析输入语音，并将其转换为文本[16]。【DeepSpeech 可用于处理语音的一些方式包括:**

> —将语音转换为文本:这对于转录语音或创建音频文件的文本转录非常有用。
> 
> —语音识别支持语音转文本、语音识别和语音搜索应用程序。
> 
> —语音搜索:DeepSpeech 可用于启用语音搜索，并支持使用语音而不是打字来搜索信息的用例。
> 
> —用于创建合成语音或文本到语音转换应用程序的语音合成。
> 
> —针对语音识别和语音生物识别等应用的语音识别。

6.CMUSphinx: CMUSphinx 是一个用于移动和嵌入式设备的语音识别系统，可以快速适应新的语言和领域。它体积小，计算效率高，非常适合资源受限的环境。CMUSphinx 使用各种声学和语言模型来实现高精度。CMUSphinx 的工作原理是首先将音频信号翻译成声谱图，然后对声谱图运行隐马尔可夫模型(HMM) [2]来识别语言单元，最后将语言单元翻译成文本。CMUSphinx 使用隐马尔可夫模型(HMM)从语音信号中识别单词，而软件首先从语音信号中识别音素[3]，然后将它们与 HMM 中的单词进行匹配。

![](img/d7af9d456caa5e8e2fd7a45e59dc67ed.png)

由佩克斯的[摄影师](https://www.pexels.com/@skitterphoto/)拍摄

7.卡耐基梅隆大学的语音识别系统。这是 CMUSphinx 的移动路径。Github 上宣布不再对其进行进一步开发。在虚拟环境中安装 Python 模块的说明可以在这里找到[4]。

8.KoNLPy，或“Python 中的朝鲜语 NLP”[5]:朝鲜语的自然语言处理 Python 包。

**对韩语的独家关注使 KoNLPy 在各种用例中独树一帜，如语料库分析、文本分析、寻找搭配[6]、分块和随机文本生成(实验以告知关于后者的其他用例)。**

9.Madmom:音频信号处理库[8]用 Python 编码，专门研究音乐信息检索(MIR)用例，其根源是约翰尼斯·开普勒大学(奥地利林茨)和奥地利人工智能研究所(奥地利维也纳 OFAI)。

10.Julius:一个大词汇量连续语音识别(LVCSR)解码器软件[9]，用于语音识别的研究和开发。在算法上，它基于隐马尔可夫模型[9]，并使用维特比算法进行解码。

11.HTK(隐马尔可夫模型工具包)是一个软件工具包，用于构建和部署基于隐马尔可夫模型的语音识别系统。它主要用于语音识别的研究[10]。

HTK 是用 C 编程语言编写的，可以在多种平台上运行，包括 Windows、Linux 和 Unix。HTK 使用隐马尔可夫模型(HMM)来模拟语音的声学和语言特征。

12.Pysptk: Python 语音工具包。Pysptk 是一个用于处理语音的 Python 库，是由 CMU Sphinx 团队开发的一套语音处理工具包。它是用 Python 编写的，可以在各种平台上工作，包括 Windows、macOS 和 Linux。它提供了一套语音分析和合成工具，包括语音转换、重新合成、语音识别器、说话人确认系统和文本到语音合成器[12]。Pysptk 还提供了一个处理声学模型的工具包，比如训练和测试。

如果您有任何编辑/修改建议或关于进一步扩展此主题的建议，请考虑与我分享您的想法。

# **另外，请考虑订阅我的每周简讯:**

[](https://pventures.substack.com/) [## 周日报告#1

### 设计思维与 AI 的共生关系设计思维能向 AI 揭示什么，AI 又能如何拥抱…

pventures.substack.com](https://pventures.substack.com/) 

*参考文献:*

*【1】。CMUSphinx:*[*https://cmusphinx.github.io/wiki/about/*](https://cmusphinx.github.io/wiki/about/)

*【2】。界面嗯。*[*https://cmusphinx . github . io/doc/sphinx 4/javadoc/edu/CMU/sphinx/语言学家/acoustic/HMM.html*](https://cmusphinx.github.io/doc/sphinx4/javadoc/edu/cmu/sphinx/linguist/acoustic/HMM.html)

*【3】。音素识别(CMUSphinx)。*[【https://cmusphinx.github.io/wiki/phonemerecognition/】T21](https://cmusphinx.github.io/wiki/phonemerecognition/)

*【4】。pocket sphinx Github:*[*https://github.com/cmusphinx/pocketsphinx*](https://github.com/cmusphinx/pocketsphinx)

*【5】。康皮。*[*https://konlpy.org/en/latest/*](https://konlpy.org/en/latest/)

*【6】。KoNLPy 示例任务。*[](https://konlpy.org/en/latest/examples/#contents)

**【7】。妈妈。*[*https://www.findbestopensource.com/product/cpjku-madmom*](https://www.findbestopensource.com/product/cpjku-madmom)*

**【8】。Github 上的 Madmom。*[*https://github.com/CPJKU/madmom*](https://github.com/CPJKU/madmom)*

**【9】。Github 上的 Julius。*[【https://github.com/julius-speech/julius】T21](https://github.com/julius-speech/julius)*

**【10】。HTK 语音识别工具包。*[*https://htk . eng . cam . AC . uk*](https://htk.eng.cam.ac.uk/)*

**【11】。Github 上的自动语音识别主题。*[*https://github.com/topics/automatic-speech-recognition*](https://github.com/topics/automatic-speech-recognition)*

**【12】。Github 上的 Pysptk。*[*https://github.com/r9y9/pysptk*](https://github.com/r9y9/pysptk)*

**【13】。演讲认知。*[*https://pypi.org/project/SpeechRecognition/*](https://pypi.org/project/SpeechRecognition/)*

**【14】。Github 上的 Eesen。*[*https://github.com/srvk/eesen/*](https://github.com/srvk/eesen/)*

**【15】。Github 上的 Vosk。*[*https://github.com/alphacep/vosk-api*](https://github.com/alphacep/vosk-api)*

**【16】。Github 上的 DeepSpeech。*[*https://github.com/mozilla/DeepSpeech*](https://github.com/mozilla/DeepSpeech)*