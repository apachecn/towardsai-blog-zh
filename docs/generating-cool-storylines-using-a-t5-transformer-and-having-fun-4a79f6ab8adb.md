# 使用 T5 变压器生成酷炫的故事情节，享受乐趣

> 原文：<https://pub.towardsai.net/generating-cool-storylines-using-a-t5-transformer-and-having-fun-4a79f6ab8adb?source=collection_archive---------0----------------------->

## [自然语言处理](https://towardsai.net/p/category/nlp)

## t5——一个穷人的 GPT 3

![](img/be447db577aea8c75da2477617463199.png)

[科技日报](https://unsplash.com/@techdailyca?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/streaming?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄的照片

# T5 变压器简介

Google AI 的人发表了一篇论文“探索使用统一的文本到文本转换器进行迁移学习的限制”，并介绍了一项关于什么类型的预训练方法或迁移学习技术最有效的实证研究，然后使用该研究创建了一个新的模型，即文本到文本转换器(T5)。这个 transformer 模型是在一个更干净的普通爬行语料库上进行预训练的，谷歌将其命名为巨大的干净爬行语料库(C4)。听起来很酷吧😎。当您检查该模型的能力和灵活性，以便用很少到中等的数据对大量的下游 NLP 问题进行微调时，它的效果也很好。

# 现在你可能会想，T5 和其他型号的变形金刚有什么不同？

要回答这个问题，我们需要看看其他转换器，如伯特、GPT 等。所有这些转换器都针对大量数据进行了预训练，但为了对分类等下游任务进行微调，会添加一个分类层并输出一个分类标签，或者为 NER 输出一个输入范围。但是在 T5，一切都是有序的，就像他们说的“文本到文本”。因此，对于分类，它将是字符串输出，对于 NER，它将是字符串，甚至对于回归，它也是字符串。不信我看报纸。在某种程度上，该模型不受一定数量的类的限制，您可以轻松地处理多个文本分类数据并训练单个模型，而无需担心标签的处理。因为你给它的一切都只是一个序列。这确实为模型提供了很多表达能力，但在某些情况下，它可能会预测标签空间之外的一些东西。我没有看到任何人报告这一点或有这个问题，所以它应该工作良好。

![](img/783a9f227591d7fa91226e177255914f.png)

来源:谷歌人工智能博客

这是很多关于变形金刚及其背后的想法的讨论，如果你想阅读更多，请查看论文和谷歌官方人工智能博客。

*   [用统一的文本到文本转换器探索迁移学习的极限](https://arxiv.org/pdf/1910.10683.pdf)
*   [谷歌人工智能博客](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html)

现在让我们深入代码，构建一些非常有趣的东西。

# 我们今天在建造什么？

正如博客的标题所暗示的，我们将建立一个故事情节生成器。但是对于我们将用来输出故事情节/情节的输入有一点小小的变化。由于 transformer 是 Sequence2Sequence 或谷歌所说的“文本到文本”,我们将通过输入类型、演员、导演、种族和故事线/情节的训练作为输出来微调这个模型。这样做有助于我们看到建议的 Sequence2Sequence(“文本到文本”)转换器的表达能力。

要了解本教程的效果如何，你可以点击这个[链接](https://movie-plot-generator.vercel.app/)去未来看看这个模型如何运行，然后回到这里为你自己建造它😂。

 [## 电影情节生成器

### 我在网上生成模糊的电影情节(但有时很好)。但我可以向你保证，它将永远是…

电影-情节-生成器. vercel.app](https://movie-plot-generator.vercel.app/) 

# 我们将使用哪些数据？

我们将使用的数据集是[维基百科电影情节](https://www.kaggle.com/jrobischon/wikipedia-movie-plots)数据集。它有关于发行年份、标题、种族、导演、演员、情节、流派、维基页面和情节的数据。我们将只使用类型，导演，演员，种族和情节来建立我们的模型。您可以随意尝试任何其他额外的列或任何其他数据集。

# 如何准备资料？

这是建模最重要的步骤之一。因此，请从上面的链接下载数据，并按照下面的步骤操作。

*   *一些正规进口*

```
import os
import re
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from tqdm import tqdm_notebook, tnrange
from sklearn.utils import shuffle
import pickle
```

*   *一些保存数据的功能*

```
def save_pickle(path, obj):
  with open(path, 'wb') as fp:
    pickle.dump(obj, fp)def load_pickle(path):
  with open(path, 'rb') as fp:
    return pickle.load(fp)
```

*   *解压数据，加载熊猫*🐼 🐼 🐼

```
movieDf = pd.read_csv('drive/MyDrive/MoviePlotsModels/data/wiki_movie_plots_deduped.csv')
```

*   *收集训练我们的模型所需的任何东西*

```
outputs = []with tqdm_notebook(total = len(movieDf)) as pbar:
  for ix, row in movieDf.iterrows():
        genre_to_plot_input = f'generate plot for genre: {row.Genre}'
    genre_to_plot_output = row.Plot
    outputs.append({
        "source": genre_to_plot_input,
        "target": genre_to_plot_output
    }) genre_director_to_plot_input = f'generate plot for: genre {row.Genre} and director: {row.Director}'
    genre_director_to_plot_output = row.Plot
    outputs.append({
        "source": genre_director_to_plot_input,
        "target": genre_director_to_plot_output
    }) genre_director_ethinicity_to_plot_input = f'generate plot for: genre {row.Genre} director: {row.Director} and ethinicity {row["Origin/Ethnicity"]}'
    genre_director_ethinicity_to_plot_output = row.Plot
    outputs.append({
        "source": genre_director_ethinicity_to_plot_input,
        "target": genre_director_ethinicity_to_plot_output
    }) if not pd.isna(row.Cast):

      genre_director_cast_to_plot_input = f'generate plot for: genre {row.Genre} director: {row.Director} and cast: {row.Cast}'
      genre_director_cast_to_plot_output = row.Plot outputs.append({
          "source": genre_director_cast_to_plot_input,
          "target": genre_director_cast_to_plot_output
      }) pbar.update(1)
```

*   *让我们保存数据*

```
save_pickle('t5-source-target-data.pkl', outputs)
```

# 让我们训练(微调😅)我们的“文本到文本”转换器

从上面的标题你可能已经明白，我们将使用一个来自 **HuggingFace 的预训练模型。是的，我们确实要使用`**transformers**`库。所以让我们开始训练代码。在开始编码之前，安装下面的包，重启你的 Colab 并开始训练。如果你不重启，你可能会在初始化模型和令牌化器的时候遇到一些错误，当你在 Stackoverflow 和 Github 上搜索了一个小时之后，你可能会找到解决方法，那就是在安装完包之后重启 Colab 笔记本。因此，只需按照安装后重新启动 Colab 笔记本的步骤操作，它将为您节省时间。**

*   *安装这些包(你会看到它们的重要性)*

```
!pip install sentencepiece
!pip install transformers
!pip install torch
!pip install rich[jupyter]
```

***顺便说一句，我们将使用 PyTorch，所以如果你一直认为这是 TensorFlow，我很抱歉让你失望了。我猜*** 你可能想改变你的框架🤣

*   *再次常规进口*

```
import os
import re
import random
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from tqdm import tqdm_notebook, tnrange
from sklearn.utils import shuffle
import pickle
import math
## use if working on jupyter notebook or colab
from IPython.display import clear_output
```

*   *一些保存和加载数据的功能*

```
def save_pickle(path, obj):
  with open(path, 'wb') as fp:
    pickle.dump(obj, fp)def load_pickle(path):
  with open(path, 'rb') as fp:
    return pickle.load(fp)
```

D *如果你用的是同一个 Colab 笔记本*就不要再复制粘贴了

*   *型号相关进口*

```
import numpy as np
import torch
import torch.nn.functional as F
from torch.utils.data import Dataset, DataLoader
from transformers import T5Tokenizer, T5ForConditionalGeneration
from rich.table import Column, Table
from rich import box
from rich.console import Consolefrom torch import cuda
device = 'cuda' if cuda.is_available() else 'cpu'
```

*   *设置丰富的控制台，以更好的方式显示分数*

```
console = Console(record=True)training_logger = Table(
    Column("Random Selection", justify = "center"),
    Column("Epoch", justify="center"),
    Column("Loss", justify="center"),
    title="Training Status",
    pad_edge=False,
    box=box.ASCII,
)valid_loggger = Table(
    Column("Random Selection", justify = "center"),
    Column("Loss", justify = "center"),
    title="Validation Status",
    pad_edge=False,
    box=box.ASCII,
)
```

*   *加载预处理数据*

```
data = load_pickle('/content/drive/MyDrive/T5MovieWikiTraining2_0/t5-source-target-data-2.pkl')
```

*   *PyTorch* `*Dataset*` *物体*

初始化此对象时传递标记化器实例

```
class T5Dataset(Dataset): def __init__(self, tokenizer, data, source_len, target_len): super(T5Dataset, self).__init__()
    self.tokenizer = tokenizer
    self.source_len = source_len
    self.target_len = target_len
    self.data = data def __len__(self): return len(self.data) def __getitem__(self, index): source_seq = self.data[index]['source']
    target_seq = self.data[index]['target'] source = self.tokenizer.batch_encode_plus(
        [source_seq],
        max_length = self.source_len,
        pad_to_max_length = True,
        truncation = True,
        padding = "max_length",
        return_tensors = "pt"
    ) target = self.tokenizer.batch_encode_plus(
        [target_seq],
        max_length = self.target_len,
        pad_to_max_length = True,
        truncation = True,
        padding = "max_length",
        return_tensors = "pt"
    ) source_ids = source["input_ids"].squeeze()
    source_mask = source["attention_mask"].squeeze()
    target_ids = target["input_ids"].squeeze()
    target_mask = target["attention_mask"].squeeze() return {
        "source_ids": source_ids,
        "source_mask": source_mask,
        "target_ids": target_ids,
        "target_mask": target_mask
    }
```

*   *训练功能*

```
def train(epoch, tokenizer, model, device, loader, optimizer): model.train() total_loss = 0
    total_counts = 0 for _, data in enumerate(tqdm_notebook(loader, desc = "Train DL")): y = data["target_ids"].to(device, dtype = torch.long)
        y_ids = y[:, :-1].contiguous()
        lm_labels = y[:, 1:].clone().detach()
        lm_labels[y[:, 1:] == tokenizer.pad_token_id] = -100
        ids = data["source_ids"].to(device, dtype = torch.long)
        mask = data["source_mask"].to(device, dtype = torch.long) optimizer.zero_grad() outputs = model(
            input_ids = ids, attention_mask = mask, decoder_input_ids = y_ids, labels = lm_labels
        ) loss = outputs[0] total_counts += 1
        total_loss += loss.item() loss.backward()
        optimizer.step() return total_loss/total_counts
```

*   *验证功能*

```
def validate(epoch, tokenizer, model, device, loader): model.eval()
    total_loss = 0
    total_counts = 0 with torch.no_grad(): for _, data in enumerate(tqdm_notebook(loader, desc = "Valid DL")): y = data["target_ids"].to(device, dtype = torch.long)
            y_ids = y[:, :-1].contiguous()
            lm_labels = y[:, 1:].clone().detach()
            lm_labels[y[:, 1:] == tokenizer.pad_token_id] = -100
            ids = data["source_ids"].to(device, dtype = torch.long)
            mask = data["source_mask"].to(device, dtype = torch.long) outputs = model(
            input_ids = ids, attention_mask = mask, decoder_input_ids = y_ids, labels = lm_labels
            ) loss = outputs[0] total_loss += loss.item()
            total_counts += 1 return total_loss / total_counts
```

*   让我们把它们放在一起

```
def trainer(
    data, model_params, output_dir = "./outputs/"
): torch.manual_seed(model_params["SEED"])
    torch.cuda.manual_seed(model_params["SEED"])
    np.random.seed(model_params["SEED"])
    torch.backends.cudnn.deterministic = True    console.log(f'''Model: Loading {model_params['MODEL']}.....''') tokenizer = T5Tokenizer.from_pretrained(model_params["MODEL"]) model = T5ForConditionalGeneration.from_pretrained(model_params["MODEL"]) model = model.to(device) console.log(f"[DATA]: READING DATA.......") optimizer = torch.optim.Adam(
        params=model.parameters(), lr=model_params["LEARNING_RATE"]
    ) # Training loop
    console.log(f"[Initiating Fine Tuning]...\\n") ## model save path path = os.path.join(output_dir, "model_files") console.log("Starting with Random Selection")
    ## random selection
    prev_loss = []
    for randomSelection in tnrange(model_params["RANDOM_TRAIN_STEPS"], desc = 'Random Selection'):

        copyData = data.copy()
        copyData = shuffle(copyData)        train_size = 0.75
        random_permuts = np.random.permutation(len(copyData))
        train_nums = round(len(random_permuts) * train_size)
        train_dataset = [copyData[i] for i in random_permuts[:train_nums]]
        valid_dataset = [copyData[i] for i in random_permuts[train_nums:]]         training_set = T5Dataset(
            tokenizer, train_dataset, model_params["MAX_SOURCE_TEXT_LENGTH"], model_params["MAX_TARGET_TEXT_LENGTH"]
        ) val_set = T5Dataset(
            tokenizer, valid_dataset, model_params["MAX_SOURCE_TEXT_LENGTH"], model_params["MAX_TARGET_TEXT_LENGTH"]
        ) train_params = {
            "batch_size": model_params["TRAIN_BATCH_SIZE"],
            "shuffle": True,
            "num_workers": 0
        } val_params = {
            "batch_size": model_params["VALID_BATCH_SIZE"],
            "shuffle": False,
            "num_workers": 0
        }

        train_dl = DataLoader(training_set, **train_params)        ## training 
        console.log(f'[MODEL TRAINING]')
        clear_output(wait = True)
        for epoch in tnrange(model_params["TRAIN_EPOCHS"], desc = "Training"):

            total_loss = train(epoch, tokenizer, model, device, train_dl, optimizer) training_logger.add_row(str(randomSelection), str(epoch), str(total_loss))
            console.log(training_logger)
            if epoch == 0:
              console.log(f"Saving Model at epoch: {epoch} with total loss: {total_loss}")
              model.save_pretrained(os.path.join(output_dir, "model_files_initial"))
              tokenizer.save_pretrained(os.path.join(output_dir, "model_files_initial")) if epoch > 0: if min(prev_loss) > total_loss:
                    console.log(f"Saving Model at epoch: {epoch} with total loss: {total_loss}")
                    model.save_pretrained(path)
                    tokenizer.save_pretrained(path) prev_loss.append(total_loss)
        del train_dl, training_set
        ## validation
        valid_dl = DataLoader(val_set, **val_params)
        console.log(f'[MODEL VALIDATION]')
        for epoch in tnrange(model_params["VAL_EPOCHS"], desc = "Validation"): val_loss = validate(epoch, tokenizer, model, device, valid_dl)

            valid_loggger.add_row(str(randomSelection), str(val_loss))
            console.log(valid_loggger)
        console.save_text(os.path.join(output_dir, f"logs-random-{randomSelection}.txt")) console.log(f"[VALIDATAION DONE]")     
        del valid_dl, val_set
```

您可以使用随机选择策略对每 N 个时期的小数据块进行训练，然后在 N 个时期后随机采样另一个数据块，并再次对新采样的数据块进行训练。这种方法可以帮助您更快地进行微调，并且模型也可以看到所有数据。但是建议仅在使用预先训练的模型进行微调时使用。

*   *模型参数*

```
model_params = {  
    "MODEL": "t5-base", # if you have a bigger machine you can use t5-large
    "TRAIN_BATCH_SIZE": 2,
    "VALID_BATCH_SIZE": 2,
    "TRAIN_EPOCHS": 10,
    "VAL_EPOCHS": 1,
    "LEARNING_RATE": 1e-4,
    "MAX_SOURCE_TEXT_LENGTH": 128,
    "MAX_TARGET_TEXT_LENGTH": 786,
    "SEED": 3007,
    "RANDOM_TRAIN_STEPS": 50
}
```

*   让我们训练这只野兽🐻

```
trainer(
    data = data,
    model_params = model_params,
    output_dir = "./outputs"
)
```

这将开始训练您的模型，并且在每 N 个训练时期后，您也将收到一个验证分数。

# 概括起来

在这篇博客中，我们看到了 Sequence2Sequence Transformer 背后的方法，或者谷歌喜欢称之为“文本到文本”转换器(T5)。我们还快速运行了数据准备流程和培训流程，以便轻松快速地对预培训的 T5 转换器进行文本生成下游任务的微调。希望你在建造这个的过程中得到一些乐趣。稍后我们将看到如何进行推理和部署这个模型。

***Colab 笔记本:***

*   [数据准备](https://colab.research.google.com/drive/1Wgcqn_hFDyUIi5-IDUiJz3feeidjzI60?usp=sharing)
*   [培训](https://colab.research.google.com/drive/1tVYHhqYbcNnF12309p2vvF2bDMvmWVa6?usp=sharing)