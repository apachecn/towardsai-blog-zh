# 释放 WebSockets 的力量进行实时模型推理

> 原文：<https://pub.towardsai.net/unleashing-the-power-of-websockets-for-real-time-model-inference-e100d597c7a2?source=collection_archive---------3----------------------->

## 使用套接字进行模型推理的实践指南

![](img/c481ebd87b797684ad2c191b7fe5aff8.png)

作者 GIF

一个*套接字*指定了一个网络地址和端口，应用程序可以通过它与网络上的进程进行通信。套接字是低级编程接口，通常用于开发应用程序之间的实时双向通信。

# 套接字与 REST APIs 有什么不同？

*   ***REST*** 和 ***Sockets*** 都是用来创建网络应用的。 **REST** ( *表述性状态转移*)是一种*软件架构*风格，它定义了一组用于创建 web 服务的约束和属性
*   ***REST*** 使用*无状态请求-响应模型*，其中服务器响应请求，而不保持先前的状态或先前请求中交换的数据
*   ***插座*** 使用一个*双向全双工通信通道*，这意味着可以同时发送和接收数据。

*如果太复杂理解不了，我也有 ChatGPT 的回答。*我请 ***ChatGPT*** 给一个孩子解释一下 *REST API 和 Socket 的区别；下面的*是它生成的响应，

> “REST 和 sockets 是计算机通过互联网相互对话的两种不同方式。休息就像打电话，一台电脑打电话给另一台电脑，询问一些信息。另一台计算机监听，然后给第一台计算机它所要求的信息。插座就像一个对讲机，两台电脑可以同时通话和听对方说话。”
> 
> “REST 是计算机共享信息的一种简单方式，但只能用于单向通信。套接字稍微复杂一点，但是它们允许计算机进行双向对话。这对于视频游戏或聊天应用来说非常有用，在这些应用中，电脑需要能够实时地来回发送信息。”

*既然我们知道了* ***套接字*** *背后的基本理论，以及它们与****REST API 的不同之处，*** *让我们继续用套接字*构建一些更酷的东西

# 在本教程中，

*   我们将看到如何使用 **FastAPI** 构建 *Socket* 服务器，并通过 *WebSockets* 提供**模型推理**。
*   作为*模型推理的一部分，*我们将部署一个 *NER* 模型，它将检测并标记给定句子中的不同实体。

*所以让我们来建造*

# FastAPI WebSockets 入门

*   安装 *FastAPI 和 uvicon*python 包，

```
pip install fastapi uvicorn
```

*   创建一个`server.py`文件并创建一个*套接字*端点

```
import os

from typing import List, Dict, Union

from fastapi import FastAPI, Header, WebSocket, WebSocketDisconnect

import uvicorn

class ConnectionManager:

 def __init__(self):

  self.active_connections: List[WebSocket] = []

  async def connect(self, websocket: WebSocket):

  await websocket.accept()

  self.active_connections.append(websocket)

 def disconnect(self, websocket: WebSocket):

  self.active_connections.remove(websocket)

 async def send_personal_message(self, data: Union[List[Dict], Dict, List],
 websocket: WebSocket):

  await websocket.send_json(data)

manager = ConnectionManager()

# healthcheck path
@app.get("/health")
async def health():
 return {"ok": True}

@app.websocket("/ws/socket-endpoint")
async def ws_get_entities(websocket: WebSocket):
 await manager.connect(websocket)

 try:

  while True:

   data = await websocket.receive_text()

   await manager.send_personal_message({"ok": True, "message": "Received"}, websocket)

 except WebSocketDisconnect:

  manager.disconnect(websocket)

if __name__ == "__main__":
 uvicorn.run(app, port=5010, host="0.0.0.0")
```

*   `ConnectionManager`帮助跟踪活动的 *WebSocket* 连接，如果这些连接从客户端断开，则可以删除/移除连接。
*   我们创建了一个 API `/health`来检查服务器启动后是否启动

目前，`/ws/socket-endpoint`什么也不做。它返回一个带有两个键`ok`和`message`的 JSON 对象

您可以在终端中运行以下命令来启动 WebSocket

```
python server.py
```

# 模型推理

让我们从 *HuggingFace* 空间中选取一个预先训练好的 NER 模型，并编写一个函数来返回给定文本中的实体。

在使用 HuggingFace 空间中的任何模型之前，我们需要安装以下软件包

```
pip install transformers torch sentencepiece
```

一旦软件包安装完毕，我们就可以继续下一步了。

我们将使用一个预训练的模型，该模型由 [*David S. Lim*](https://huggingface.co/dslim) 训练，并且在[](https://huggingface.co/)**上的[*Bert-base-NER*](https://huggingface.co/dslim/bert-base-NER)下可用。**

**我们可以使用下面这段代码来初始化模型，并处理句子或文本进行推理。创建一个`predict.py`文件，并将以下代码添加到该文件中**

```
import os
import re
import json
from typing import List, Dict, Union, Tuple
from transformers import AutoTokenizer, AutoModelForTokenClassification, pipeline

class NERPredictor:
    """NER Predictor Instance
    """
    def __init__(self, model_path: str):
        """Initializes the NER Predictor
        Args:
            model_path (str): Path To Model Files
        """
        self.model_path = model_path
        print(f"LOADING TOKENIZER")
        self.tokenizer = AutoTokenizer.from_pretrained(self.model_path,
                                                       local_files_only=True)
        print(f"LOADED TOKENIZER")
        print(f"LOADING MODEL")
        self.model = AutoModelForTokenClassification.from_pretrained(
            self.model_path, local_files_only=True)
        print(f"LOADED MODEL")
        self.nlp_pipeline = pipeline("ner",
                                     model=self.model,
                                     tokenizer=self.tokenizer)
    def __combine_start_end__(self, text: str,
                              results: List[Dict]) -> List[Dict]:
        """Combines consecutive same entity types into one
        Args:
            text (str): Input Text
            results (List[Dict]): NER Result from the pipeline
        Returns:
            List[Dict]: Combined NER Result
        """
        index = 0
        current = None
        output = []
        while index < len(results):
            current = results[index].get("entity")
            start = results[index].get("start")
            end = results[index].get("end")
            index += 1
            while index < len(results) and results[index].get(
                    "entity") == current:
                end = results[index].get("end")
                index += 1
            output.append({
                "entity": current,
                "start": start,
                "end": end,
                "text": text[start:end]
            })
        return output
    def __clean_entity__(self, result: List[Dict]) -> List[Dict]:
        """Remove the B, I in entity
        Args:
            result (List[Dict]): NER Results
        Returns:
            List[Dict]: NER Results
        """
        [e.update({"entity": e.get("entity").split("-")[-1]}) for e in result]
        return result
    def __tag_input_text__(self, text: str,
                           formatted_result: List[Dict]) -> List[Dict]:
        """Tagging parts of the sentences
        Args:
            text (str): Input Text
            formatted_result (List[Dict]): NER Result
        Returns:
            List[Dict]: Tagged Parts of Sentences
        """
        start_end = list(
            map(lambda r: (r.get("start"), r.get("end")), formatted_result))
        start_end = sorted(start_end, key=lambda se: se[0])
        index = 0
        op = []
        while index < len(text):
            if not index in list(map(lambda se: se[0], start_end)):
                lst = []
                start = index
                while not index in list(map(lambda se: se[0],
                                            start_end)) and index < len(text):
                    lst.append({"entity": "other", "char": text[index]})
                    index += 1
                op.append({
                    "entity":
                    "other",
                    "text":
                    "".join(list(map(lambda char: char.get("char"), lst))),
                    "start":
                    start,
                    "end":
                    index
                })
            else:
                rng = list(filter(lambda se: se[0] == index, start_end))[0]
                en = rng[-1]
                res = list(
                    filter(
                        lambda re: re.get("start") == index and re.get("end")
                        == en, formatted_result))[0]
                op.append({
                    "entity": res.get("entity"),
                    "text": text[index:en],
                    "start": index,
                    "end": en
                })
                index = en
        return op
    def predict_result(self, text: str) -> List[Dict]:
        """Given the text predicts the NER Result
        Args:
            text (str): Input Text
        Returns:
            List[Dict]: NER Result with Start and End index and entity types
        """
        ner_results = self.nlp_pipeline(text)
        ner_results = self.__clean_entity__(ner_results)
        results = self.__tag_input_text__(text, ner_results)
        results = list(
            filter(lambda rs: len(rs.get("text").rstrip().lstrip()) > 0,
                   results))
        return self.__combine_start_end__(text, results)
```

# **将模型推理与 WebSocket 集成**

*   **在`server.py`文件中导入`NERPredictor`**

```
# --- #
from predict import NERPredictor
# --- #
```

*   **初始化顶部的`NERPredictor`**

```
# --- #
manager = ConnectionManager() 
pred_obj = NERPredictor("dslim/bert-base-NER")
# --- #
```

*   **添加一个新的 WebSocket 端点`/ws/get-entities`并监听连接和文本数据**

```
# --- #

@app.websocket("/ws/get-entities")
async def ws_get_entities(websocket: WebSocket):

 await manager.connect(websocket)

 try:

  while True:

  data = await websocket.receive_text()

  # print(f"RECEIVED: {data}")

  result = pred_obj.predict_result(data)

  # print(f"RESULT: {result}")

  await manager.send_personal_message(result, websocket)

 except WebSocketDisconnect:

  manager.disconnect(websocket)

# --- #
```

```
@app.websocket("/ws/get-entities")
async def ws_get_entities(websocket: WebSocket): await manager.connect(websocket) try: while True: data = await websocket.receive_text() # print(f"RECEIVED: {data}") result = pred_obj.predict_result(data) # print(f"RESULT: {result}") await manager.send_personal_message(result, websocket) except WebSocketDisconnect: manager.disconnect(websocket)# --- #
```

**您的服务器端套接字已经准备好了。现在让我们构建客户端应用程序**

**让我们使用 ***Javascript*** 与服务器端代码进行交互**

# **与 WebSocket 交互**

**用 javascript 安装用于 WebSocket 支持的`ws`模块**

```
npm install -g ws
```

**创建一个`test_ws.js`文件并添加以下代码**

```
const ws = new WebSocket("ws://localhost:5010/ws/get-entities")

const readline = require("readline").createInterface({
    input: process.stdin,
    output: process.stdout
})

let is_read = true;

const send_message = (ws) => {
    console.log("\nSEND TEXT")
    readline.question("\nEnter your Text: ,", (msg) => {
        ws.send(msg);
    })
    ws.on("message", (data) => {
        console.log(data.toString())
        send_message(ws)
    })
}

ws.on("open", () => {
    if (is_read) {
        send_message(ws)
    } 
}) 
```

**使用以下命令运行脚本，并尝试一些句子**

```
node test_ws.js
```

**上述实现的代码可从 [SocketNER](https://github.com/vatsalsaglani/SocketNER/tree/main/server) 获得**

# **结论**

**在这篇博客中，我们讨论了如何使用 WebSockets，通过 FastAPI 实现超快的实时模型推理。您可以查看客户端连接器的 [SocketNER](https://github.com/vatsalsaglani/SocketNER.git) 存储库，以连接到服务器端 WebSocket。用户界面是使用 *SvelteKit* 构建的。**