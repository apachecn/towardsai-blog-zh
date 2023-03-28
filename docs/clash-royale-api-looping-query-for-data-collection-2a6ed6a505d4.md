# Clash Royale API:循环查询数据收集

> 原文：<https://pub.towardsai.net/clash-royale-api-looping-query-for-data-collection-2a6ed6a505d4?source=collection_archive---------1----------------------->

## 数据科学

几天前，我有了一个想法，将因子分析应用于皇家冲突的玩家，以便将他们分成不同的等级。不幸的是，我意识到我无法在网上找到任何相关的数据，并且我找到的开源数据集都没有我正在搜索的信息:因此，我决定使用 API 从源下载原始数据。

您可以使用本教程作为指南，指导您使用 API 和从在线数据库收集数据。在下一篇教程中，我将对结果进行因子分析，以识别收集到的数据中的层次结构。

> 我的 GitHub repo 上有完整的代码。

# 下载 JSON 文件中的 Clash Royale 匹配

![](img/769ae99b21b1e0efd58b9e48daf8afc1.png)

图片来自壁纸洞穴

Clash Royale 是一款智能手机游戏，允许每个玩家建立一套 8 张不同的卡片来与其他玩家战斗。通过 https://developer.clashroyale.com/#/[网站，我可以看到一名球员最近 25 场比赛的信息。我想收集并存储顶级玩家在最近 25 场战斗中打出的每副牌的数据，以便我以后可以使用这些数据来训练一个 AI。为此，我需要:](https://developer.clashroyale.com/#/)

1.在 developer.clashroyale.com[注册并获得一个 API 令牌](https://developer.clashroyale.com/#/)

2.通过 API 建立到数据集的连接

3.下载一组特定的数据(我不能下载所有的数据，我需要明确我想要收集的数据)

4.遍历每一个。json，从。json 文件并存储它们

5.将所有存储的数据做成相同的形状，然后创建一个数据帧

6.导出数据帧

# 实际问题

实际上，当使用 API 下载数据时，我们会遇到很多限制:

*   有时间限制:我们可以下载与时间相关的小批量数据

这个问题使得使用这个数据库非常具有挑战性。我知道对于我的 AI 来说，我需要成千上万的匹配来执行任何类型的分析，然而，我可以每 4 分钟下载多达 25 个匹配，其中 15 个可能是有效的(我只想存储‘梯子’游戏，丢弃所有其他的):这设置了每小时 225 个匹配的下载限制，假设算法完全运行并且每个请求都是有效的(即使在执行有效的请求时，你也不会相信会发生多少问题)。

通过这篇文章，我将指导你构建一个算法，它能够**周期性地**连接到一个在线数据库来提取信息，将它们收集到一个数据帧中，你可以将它导出为一个. csv 文件。

*   我们需要知道要搜索什么数据

在这个特定的例子中，我需要输入参加过我想要收集数据的比赛的球员的标签。我将选择 7 个玩 X 弓原型的顶级玩家(使用这个原型的顶级玩家被称为柠檬树 68，他的名字将会在时间中回响…)。如前所述，我只想保存在“天梯”中玩的游戏，所以我需要删除所有其他游戏:在 25 个原始游戏中，我可能只能存储 15 个。

*   我们需要处理。json 文件

API 将为我们提供一个字典列表，每个字典代表一个匹配。然而，我们不能仅仅将它转换成. csv:我们需要确定我们想要保存的特性，然后将它们存储到一个列表中。我们下载的 json 字典:我们需要为此创建一个个性化的算法。

如果你的目标是更专业的数据科学方法，你将需要习惯于使用 API 直接从特定网站下载数据，而不是在一些开源存储库中找到已经结构化的数据。

# 连接到数据库

让我们开始浏览步骤列表:首先，我已经在上面的网站中注册，并请求与我的 IP 地址相关联的开发者密钥:

![](img/a372684f8f1411e563b4226caba8b34a.png)

在[https://developer.clashroyale.com/#/](https://developer.clashroyale.com/#/)创建的密钥

当我在我的代码中使用这个密钥时，如果查询(请求)是正确的并且 IP 地址是对应的，数据库将授权我，并允许我下载数据。现在，我将建立一个与数据库的连接:

```
import requests
import json
from urllib.parse import quote
import timeheaders = {
'Accept': 'application/json',
'authorization': 'Bearer <eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiIsImtpZCI6IjI4YTMxOGY3LTAwMDAtYTFlYi03ZmExLTJjNzQzM2M2Y2NhNSJ9.eyJpc3MiOiJzdXBlcmNlbGwiLCJhdWQiOiJzdXBlcmNlbGw6Z2FtZWFwaSIsImp0aSI6ImFkODhlY2NjLTM2YjUtNDUwZi1hODI0LTY3ZWIyZjc0MzY5YSIsImlhdCI6MTU4OTQ4MzUyMiwic3ViIjoiZGV2ZWxvcGVyLzJkZGRhOGI4LTEyY2YtMzQzNy05N2FjLTQxNTBhMTMzNGI1MiIsInNjb3BlcyI6WyJyb3lhbGUiXSwibGltaXRzIjpbeyJ0aWVyIjoiZGV2ZWxvcGVyL3NpbHZlciIsInR5cGUiOiJ0aHJvdHRsaW5nIn0seyJjaWRycyI6WyIxMDQuMTU1LjIxOC4xNzgiXSwidHlwZSI6ImNsaWVudCJ9XX0.PdB9ycHIcIkKRs246zKLNdRJleUiXV9u-szeMj9qm02Rz-wS4OkkfOaafWRMXos_LVLmZe1VeUBCpr6fIiMvRw>'
}
```

# 准备请求

如前所述，我需要非常具体地说明我要下载哪些数据。我将下载世界上 7 个顶级 X-bow 玩家最近的比赛(每个玩家 25 场比赛)。因此，我将存储以下标签。

```
#has to be run only once, otherwise the dataset we are going to create will reset
battles_list = list()tag_list = [
'#929URQCL8', '#RC2JGVVG', '#R9QC0QUQ', 
'#9JPL980Y2', '#YU8R0VPP', '#RPURG9GR', 
'#2GYRQJRR8']tag_list_scavenged = list()
columns = [
'gamemode', 'battletime',
'p1.name', 'p2.name',
'p1.crowns', 'p2.crowns',
'p1.card_1', 'p1.card_2', 'p1.card_3', 'p1.card_4', 
'p1.card_5','p1.card_6', 'p1.card_7', 'p1.card_8',
'p2.card_1', 'p2.card_2', 'p2.card_3', 'p2.card_4', 
'p2.card_5', 'p2.card_6', 'p2.card_7', 'p2.card_8'
]
```

因为我已经查看了数据，所以我还将保存我希望应用到最新版本的。我们将要创建的 csv 数据集:基本上是游戏模式(我们将使用这些信息来丢弃所有未在‘天梯’中玩的游戏)、战斗时间和两个玩家的姓名(为了丢弃重复的游戏)、计算谁赢了这场比赛的冠数，以及每个玩家选择的牌组。

# 为每个标签转发一个查询

现在，我将创建一个允许我对数据库执行 GET 请求的函数:对于每个玩家标记，我将下载一个. json 文件，进行适当的修改，最后得到一个包含 25 个元素的列表:每个元素只包含我想要作为战斗摘要的数据。

```
import pandas as pd
from pandas.io.json import json_normalizedef p1_dataset(player_tag):
  df_list_complete = list() #downloading json
  r =   requests.get('https://api.clashroyale.com/v1/players/'+player_tag+'/battlelog', headers=headers)
  #a contains 25 dicts in a list
  try:
  a = r.json() ###IN CASE OF UNRESOLVED ERROR: EXIT
  except Exception as e:
    return 1 ###IN CASE OF FAILED REQUEST: EXIT
  if a == {'reason': 'accessDenied', 'message': 'Invalid authorization'}:
    return 0
```

如果数据集返回错误，函数将退出并返回 0 或 1。

# 将每个 JSON 构造成一个数据帧

```
 #for each of the 25 dicts in the list
  for n in a:
```

## 将所有数据下载到变量

到目前为止，最大的问题是构造每个. json。正如你从我下载的内容中看到的，它是一组字典中的字典。我要做的是使用 pandas.io.json.json_normalize，这个工具允许我将一个单元格中包含的字典转换成另一个数据帧。

![](img/a6738c3bf721e61db4d8b7e4421abdb2.png)

怎么会。json 看起来会像

本质上，我将处理几个嵌套的字典:

![](img/663ee5bb8d85afdad83fe4a00340ed38.png)

DataFrame 的. json 将会是什么样子

![](img/676df4f92d4db44b91ddf1246357677b.png)

```
 df1 = json_normalize(n)
    df_opponent = json_normalize(df1['opponent'][0]) df_opponent_name = df_opponent['name'][0]
    df_opponent_crowns = df_opponent['crowns'][0]
    df_opponent_cards = json_normalize(df_opponent['cards'][0])
    df_opponent_cards = df_opponent_cards['name'].tolist() df_team = json_normalize(df1['team'][0])
    df_team_name = df_team['name'][0]
    df_team_crowns = df_team['crowns'][0]
    df_team_cards = json_normalize(df_team['cards'][0])
    df_team_cards = df_team_cards['name'].tolist() battletime = df1['battleTime'][0]
    gamemode = df1['gameMode.name'][0]
```

## 将所有变量放在一个列表中

我将把数据帧的每个元素存储在一个变量中，同时我需要扩展嵌套的字典来找出它们还包含哪些变量。最后，我会给出一个变量列表。

![](img/d0f453a0b2bea3b21f5adf5b0754ff08.png)

在将所有嵌套数据存储到单个列表中之后

```
 df_list = list()
    #append individual variables
    df_list = [
               gamemode, 
               battletime,
               df_team_name, 
               df_opponent_name,
               df_team_crowns, 
               df_opponent_crowns
              ]
    #append lists
    for team_card_n in df_team_cards:
      df_list.append(team_card_n)
    for opponent_card_n in df_opponent_cards:
      df_list.append(opponent_card_n)
```

## 将列表附加到我们的数据框架中

```
 df_list_complete.append(df_list)
    return df_list_complete
```

# 循环查询

我们已经创建了一个功能，让我们下载和正确存储每个球员标签 25 场比赛。现在我们必须以某种方式激活它，给定 7 个玩家标签的列表，算法不会停止，直到它下载了所有的数据(175 行)。为了做到这一点，我们将让它循环，直到它完成它的任务:

```
first_round = True
#looping through queries until all our requests are filled
while len(tag_list_scavenged) < len(tag_list):
  #we cannot substitute existing tags
  for m in tag_list:
    if m in tag_list_scavenged:
      print(‘Tag already in list:’, m)
    else:
      #the first round skip the waiting
      if first_round == True:
        first_round = False
      else:
        #wait 240 seconds
        time.sleep(240)
      print('timer_ended') #GET request
      csv = p1_dataset(quote(m))#manage errors
    if csv == 0 or csv == []:
      print('unable to download:', m)
      pass
    elif csv == 1:
      print('unable to download due error:', m)
      pass
    else:
      print(‘scavenged:’, m)
      csv = pd.DataFrame(csv)
      #we won't ne editing the columns until the end, here is only a reference
      #csv.columns = columns
      #we add the csv to the dataset
      battles_list.append(csv)
      #we save the tag so that the algorithm will not repeat the request for this tag
      tag_list_scavenged.append(m)
```

# 处理错误

我们算法运行的最大风险是错误，因为它们迫使算法停止，需要手动重新激活。为了防止这种情况发生，在出现错误或空数据集(这种情况可能导致错误)时，我将返回一个条件(0 或 1)，算法将忽略该条件以继续循环。你可以用许多其他的方法来做这件事，我选择这件是因为我发现它是最舒适的。常见错误:

*   下载的文件为空，结果为[]，导致 JSONDecodeError
*   { '原因':'拒绝访问'，'消息':'无效授权' }

# …28 分钟后

```
timer_ended
scavenged: #RPURG9GR
timer_ended
scavenged: #2GYRQJRR8
...
```

如果出现错误，算法会发出信号，但会继续工作并执行请求。如果我们检查 tag_list_scavenged:

```
tag_list_scavenged
[‘#929URQCL8’, 
‘#RC2JGVVG’, 
‘#R9QC0QUQ’, 
‘#9JPL980Y2’, 
‘#YU8R0VPP’, 
‘#RPURG9GR’, 
‘#2GYRQJRR8’]
```

上面，我们已经创建了一个数据集，其中包含了带有上述标签的所有玩家的战斗，使用了一个算法而不是几个手动请求。所有的匹配都被保存在战斗列表中。

```
#before editing further, we make a copy
q = battles_list.copy()
```

* * *如果由于任何原因算法会停止，因为在 Jupiter 笔记本上操作，变量将被临时存储:任何成功的请求都不会丢失

# 编辑战斗数据帧

我们现在必须放弃所有未被归类为“天梯”的游戏:

```
#we only conserve ladder plays
for i in range(0, len(q)):
  #lista con i nomi delle colonne exra che volgiamo eliminare
  list1 = [22 + x for x in range(0, q[i].shape[1]-22)]
  print(list1)
  #only maintain ladder games
  q[i] = q[i].loc[q[i][0] == ‘Ladder’]
```

![](img/a3d4eaf62618e23272aec155d9f48917.png)

我们唯一想保留的游戏模式(第 0 列)是天梯

现在有另一个问题:我们存储的列表长度不相等:因为有可能玩一个允许 18 副牌的游戏模式，所以一些列表比其他的要长。因为我们一直将它们存储为唯一的数据帧，所以我们需要删除所有额外的列:

```
 #deleting all the extra columns
  if q[i].shape[1] > 22:
  #if there are no extra columns, do not even bother, otherwise error
    q[i] = q[i].drop(list1, axis=1)
```

# 编辑最终数据帧

```
CRL = pd.DataFrame()
CRL = pd.concat(q[0:len(q)], axis=0)
#rinominiamo l’intero dataset alla fine
CRL.columns = columns
CRL
```

![](img/a224b09d32538b9181f8b6c1ac5d817a.png)

最终数据集的屏幕截图

# 导出到 CSV

```
CRL.to_csv(‘CRL.csv’)
```