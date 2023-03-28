# 如何使用 T5 变压器生成有意义的句子？

> 原文：<https://pub.towardsai.net/how-to-generate-meaningful-sentences-using-a-t5-transformer-b755bee64882?source=collection_archive---------2----------------------->

## [自然语言处理](https://towardsai.net/p/category/nlp)

## 开发一个文本生成 API

![](img/be447db577aea8c75da2477617463199.png)

科技日报在 [Unsplash](https://unsplash.com/s/photos/streaming?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄的照片

在博客 [**使用 T5 转换器生成故事情节**](/generating-cool-storylines-using-a-t5-transformer-and-having-fun-4a79f6ab8adb) 中，我们看到了如何通过提供类型、导演、演员和种族等输入来微调 Sequence2Sequence(文本到文本)转换器(T5)以生成故事情节/情节。在这篇博客中，我们将看看如何使用训练过的 T5 模型进行推理。稍后，我们还将看到如何使用`gunicorn`和`flask`来部署它。

# 如何做模型推断？

*   *让我们用导入设置脚本*

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
import torch
import torch.nn.functional as F
from transformers import T5Tokenizer, T5ForConditionalGeneration
```

*   *设置* `*SEED*` *值，加载模型和分词器*

```
torch.manual_seed(3007)model = T5ForConditionalGeneration.from_pretrained('./outputs/model_files')
tokenizer = T5Tokenizer.from_pretrained('./outputs/model_files')
```

*   *使用* `*model.generate*` *功能生成序列*

```
text = "generate plot for genre: horror"
input_ids = tokenizer.encode(text, return_tensors="pt")
greedyOp = model.generate(input_ids, max_length=100)
tokenizer.decode(greedyOp[0], skip_special_tokens=True)
```

*注:阅读* [*这篇*](https://huggingface.co/blog/how-to-generate) *关于如何使用变形金刚使用不同解码策略生成文本的惊人拥抱脸博客*

*   *让我们把它放在一个函数里*

```
def generateStoryLine(text, seq_len, seq_num):
				'''
				args:
					text: input text eg. generate plot for: {genre} or generate plot for: {director}
					seq_len: Max sequence length for the generated text
					seq_num: Number of sequences to generate
				'''
        outputDict = dict()
        outputDict["plots"] = {}
        input_ids = tokenizer.encode(text, return_tensors = "pt")
        beamOp = model.generate(
            input_ids,
            max_length = seq_len,
            do_sample = True,
            top_k = 100,
            top_p = 0.95,
            num_return_sequences = seq_num
        ) for ix, sample_op in enumerate(beamOp):
            outputDict["plots"][ix] = self.tokenizer.decode(sample_op, skip_special_tokens = True)

        return outputDict
```

# 如何用 Flask 部署这个？

用户可以通过多种方式提供输入，并且模型可能需要生成图。用户可以只提供类型，或者他们可以提供类型和演员，或者他们甚至可以提供所有四个，即类型、导演、演员和种族。但是为了这个实现的目的，我强制要求至少提供一个流派。

你可以查看下面的链接，看看这个 API 是如何工作的。

 [## 电影情节生成器

### 我在网上生成模糊的电影情节(但有时很好)。但我可以向你保证，它将永远是…

电影-情节-生成器. vercel.app](https://movie-plot-generator.vercel.app/) 

*让我们开发一个后端来实现用于上面*链接的 API 调用

# 安装需求

```
pip install flask flask_cors tqdm rich gunicorn
```

# 创建 app.py 文件

*   *进口*

```
# app.pyfrom flask import Flask, request, jsonify
import json
from flask_cors import CORS
import uuidfrom predict import PredictionModelObjectapp = Flask(__name__)
CORS(app)print("Loading Model Object")
predictionObject = PredictionModelObject()
print("Loaded Model Object")
```

*   *添加一个 API 路径*

```
@app.route('/api/generatePlot', methods=['POST'])
def gen_plot(): req = request.get_json()
    genre = req['genre']
    director = req['director'] if 'director' in req else None
    cast = req['cast'] if 'cast' in req else None
    ethnicity = req['ethnicity'] if 'ethnicity' in req else None
    num_plots = req['num_plots'] if 'num_plots' in req else 1
    seq_len = req['seq_len'] if 'seq_len' in req else 200 if not isinstance(num_plots, int) or not isinstance(seq_len, int):
        return jsonify({
            "message": "Number of words in plot and Number of plots must be integers",
            "status": "Fail"
        })

    try:
        plot, status = predictionObject.returnPlot(
            genre = genre, 
            director = director,
            cast = cast,
            ethnicity = ethnicity,
            seq_len = seq_len,
            seq_num = num_plots
        ) if status == 'Pass':

            plot["message"] = "Success!"
            plot["status"] = "Pass"
            return jsonify(plot)

        else: return jsonify({"message": plot, "status": status})

    except Exception as e: return jsonify({"message": "Error getting plot for the given input", "status": "Fail"})
```

*   *主程序块运行* `*flask*` *app*

```
if __name__ == "__main__":
    app.run(debug=True, port = 5000)
```

这个脚本还不行。由于我们还没有用 `***PredictionModelObject***`创建 `*predict.py*` *脚本，因此在此时执行脚本时，您可能会收到一个导入错误*

# 创造了`PredictionModelObject`

*   *创建一个* `*predict.py*` *文件，导入下面的*

```
# predict.py
import os
import re
import random
import torch
import torch.nn as nn
from rich.console import Console
from transformers import T5Tokenizer, T5ForConditionalGeneration
from collections import defaultdictconsole = Console(record = True)torch.cuda.manual_seed(3007)
torch.manual_seed(3007)
```

*   *创建* `*PredictionModelObject*` *类*

```
# predict.py
class PredictionModelObject(object): def __init__(self):console.log("Model Loading")
        self.model = T5ForConditionalGeneration.from_pretrained('./outputs/model_files')
        self.tokenizer = T5Tokenizer.from_pretrained('./outputs/model_files')
        console.log("Model Loaded")

    def beamSearch(self, text, seq_len, seq_num): outputDict = dict()
        outputDict["plots"] = {}
        input_ids = self.tokenizer.encode(text, return_tensors = "pt")
        beamOp = self.model.generate(
            input_ids,
            max_length = seq_len,
            do_sample = True,
            top_k = 100,
            top_p = 0.95,
            num_return_sequences = seq_num
        ) for ix, sample_op in enumerate(beamOp):
            outputDict["plots"][ix] = self.tokenizer.decode(sample_op, skip_special_tokens = True)

        return outputDict def genreToPlot(self, genre, seq_len, seq_num): text = f"generate plot for genre: {genre}" return self.beamSearch(text, seq_len, seq_num) def genreDirectorToPlot(self, genre, director, seq_len, seq_num): text = f"generate plot for genre: {genre} and director: {director}"

        return self.beamSearch(text, seq_len, seq_num) def genreDirectorCastToPlot(self, genre, director, cast, seq_len, seq_num): text = f"generate plot for genre: {genre} director: {director} cast: {cast}" return self.beamSearch(text, seq_len, seq_num) def genreDirectorCastEthnicityToPlot(self, genre, director, cast, ethnicity, seq_len, seq_num): text = f"generate plot for genre: {genre} director: {director} cast: {cast} and ethnicity: {ethnicity}" return self.beamSearch(text, seq_len, seq_num)

    def genreCastToPlot(self, genre, cast, seq_len, seq_num): text = f"genreate plot for genre: {genre} and cast: {cast}" return self.beamSearch(text, seq_len, seq_num) def genreEthnicityToPlot(self, genre, ethnicity, seq_len, seq_num): text = f"generate plot for genre: {genre} and ethnicity: {ethnicity}" return self.beamSearch(text, seq_len, seq_num) def returnPlot(self, genre, director, cast, ethnicity, seq_len, seq_num):
        console.log('Got genre: ', genre, 'director: ', director, 'cast: ', cast, 'seq_len: ', seq_len, 'seq_num: ', seq_num, 'ethnicity: ',ethnicity)

        seq_len = 200 if not seq_len else int(seq_len)

        seq_num = 1 if not seq_num else int(seq_num)

        if not director and not cast and not ethnicity: return self.genreToPlot(genre, seq_len, seq_num), "Pass"

        elif genre and director and not cast and not ethnicity: return self.genreDirectorToPlot(genre, director, seq_len, seq_num), "Pass" elif genre and director and cast and not ethnicity: return self.genreDirectorCastToPlot(genre, director, cast, seq_len, seq_num), "Pass" elif genre and director and cast and ethnicity: return self.genreDirectorCastEthnicityToPlot(genre, director, cast, ethnicity, seq_len, seq_num), "Pass" elif genre and cast and not director and not ethnicity: return self.genreCastToPlot(genre, cast, seq_len, seq_num), "Pass"

        elif genre and ethnicity and not director and not cast: return self.genreEthnicityToPlot(genre, ethnicity, seq_len, seq_num), "Pass" else: return "Genre cannot be empty", "Fail"
```

保存`predict.py`文件，然后在调试模式下运行`app.py`文件，

```
python app.py
```

# 测试您的 API

*   *创建一个* `*test_api.py*` *文件并执行*

```
# test_api.py
import requests
import osurl = "<http://localhost:5000/api/generatePlot>"
json = {
    "genre": str(input("Genre: ")),
    "director": str(input("Director: ")),
    "cast": str(input("Cast: ")),
    "ethnicity": str(input("Ethnicity: ")),
    "num_plots": int(input("Num Plots: ")),
    "seq_len": int(input("Sequence Length: ")),
}r = requests.post(url, json = json)
print(r.json())
```

# 如何用`gunicorn`跑步？

使用`gunicorn`和`flask`非常简单。在开始安装需求时，我们已经安装了`gunicorn`命令，现在我们需要转到`app.py`文件所在的文件夹。终端，并运行以下命令

```
gunicorn -k gthread -w 2 -t 40000 --threads 3 -b:5000 app:app
```

我们上面使用的格式和标志表示以下内容

*   *k: kind(工人类型)——*`*gthread*`*`*gevent*`*等...**
*   **w:工人数量**
*   **t:超时时间**
*   **线程:每个工作线程的数量**
*   **b:绑定端口号**

**如果你的文件名是* `*server.py*` *或*`*flask_app.py*`*`*app:app*`*部分会变成* `*server:app*` *或* `*flask_app:app*`**

# **概括起来**

**在这篇博客中，我们看到了如何使用我们之前训练过的 T5 变压器来生成故事情节，并使用`flask`和`gunicorn`来部署它。这个博客很容易被关注，所以你不用浪费时间去不同的平台查看问题。希望你能享受阅读和实现这个的乐趣。**