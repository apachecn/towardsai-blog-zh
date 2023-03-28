# 使用 Wav2Vec 2.0 进行语音转文本

> 原文：<https://pub.towardsai.net/speech-to-text-with-wav2vec-2-0-b21c1e1ad701?source=collection_archive---------1----------------------->

![](img/99d0420c25f6f347e3023363a78fc065.png)

图片由 [Harmony Lawrence](https://pixabay.com/users/temperatesage-13030917/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=4335953) 来自 [Pixabay](https://pixabay.com/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=4335953)

## [自然语言处理](https://towardsai.net/p/category/nlp)

## 语音转文本

在我之前的博客中，我解释了如何在谷歌语音识别 API 的帮助下，使用语音识别库将语音转换为文本。在这篇博客中，我们看到了如何使用脸书 Wav2Vec 2.0 模型将语音转换成文本。

[脸书](https://ai.facebook.com/blog/wav2vec-20-learning-the-structure-of-speech-from-raw-audio)最近推出并[开源了他们的新框架](https://ai.facebook.com/blog/wav2vec-20-learning-the-structure-of-speech-from-raw-audio)，用于从原始音频数据进行自我监督学习，称为 Wav2vec 2.0。脸书的研究人员声称，这个框架只需要 10 分钟的转录语音数据就可以实现自动语音识别模型。

众所周知，变形金刚在自然语言处理中起着主要作用。拥抱脸变形金刚的最新版本是 4.30 版本，它带有 Wav2Vec 2.0。这是变形金刚中包含的第一个自动语音识别语音模型。

模型架构超出了这篇博客的范围。详细的 Wav2Vec 模型架构，请查看[此处](https://ai.facebook.com/blog/wav2vec-20-learning-the-structure-of-speech-from-raw-audio/)。

让我们看看如何通过一行简单的代码使用拥抱面部变形器将音频文件转换成文本。

# 安装转换器库

# 导入必要的库

Wav2Vec2 是一种语音模型，它接受与语音信号的原始波形相对应的浮点数组。Wav2Vec2 模型使用连接主义时间分类(CTC)进行训练，因此模型输出必须使用 wav2 vec 2 tokenizer([Ref:Hugging Face)](https://huggingface.co/transformers/model_doc/wav2vec2.html)进行解码

# 读取音频文件

在这个例子中，我使用了连姆·尼森著名的电影《捉迷藏》中的对话音频片段，它说*“我会去找你，我会找到你，我会杀了你”*

请注意，Wav2Vec 模型是在 16 kHz 频率上预先训练的，因此我们确保我们的原始音频文件也以 16 kHz 的采样率重新采样。我已经使用在线[音频工具转换](https://audio.online-convert.com/convert-to-wav)将“拍摄”的音频剪辑重新采样为 16kHz。

使用 librosa 库加载音频文件，并提及我的音频剪辑大小为 16000 Hz。它将音频剪辑转换成一个数组，并存储在“音频”变量中。

# 导入预训练的 Wav2Vec 模型

下一步是获取输入值。将音频(数组)传递给 tokenizer，我们希望张量转换成 PyTorch 格式，而不是 python 整数。提到的 return_tensors = "pt "无非就是 PyTorch 格式。

获取 logit 值(非标准化值)

将 logit 值传递给 softmax 以获得预测值

# 将音频转换为文本

最后一步是将预测传递给记号赋予器解码以获得转录

它能准确读出我们的音频片段。

在这篇博客中，我们看到了如何使用 Wav2Vec pretraining model 使用 transformers 将语音转换为文本。这对 NLP 项目非常有帮助，尤其是处理音频文本数据。如果你有什么要补充的，欢迎随时留言评论！

你可以在我的 [GitHub repo 中找到完整的代码和数据。](https://github.com/sdhilip200/speech-to-text)

感谢阅读。请继续学习，并关注更多内容！

# 参考

1.  [https://huggingface.co/transformers/model_doc/wav2vec2.html](https://huggingface.co/transformers/model_doc/wav2vec2.html)
2.  [https://ai . Facebook . com/blog/wav2 vec-20-从原始音频中学习语音结构/](https://ai.facebook.com/blog/wav2vec-20-learning-the-structure-of-speech-from-raw-audio/)