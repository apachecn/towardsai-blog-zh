# 通过人口统计评估行为的 KDTree

> 原文：<https://pub.towardsai.net/kdtree-to-evaluate-behavior-by-demographics-394752a80d78?source=collection_archive---------0----------------------->

## 有没有考虑过定位的角度进行客户行为分析？

![](img/fb952455f67c786b322be8d3f87c8d04.png)

来源:Pixabay

## **摘要:**

行为分析是对学习和行为原则的科学研究。这个科学领域涉及描述、理解、预测和改变行为。他们通过观察生物和环境因素来寻找答案，尽管他们主要对环境在行为改变中的作用感兴趣。

在数据科学中，行为分析充分利用大数据和人工智能在用户行为数据上的结合，以识别模式、趋势、违规行为和其他有用的见解，从而采取适当的行动。根据使用案例，行为分析被用于许多行业和应用，包括电子商务、医疗保健、银行、保险和网络安全。

常见的数据科学挑战之一是根据人口统计信息分析行为和评分。目标通常是根据几个参数对实体(个人/公司)进行评分，如:

**以往购买**

**购买间隔时间**

**购买数量和价值**

**个人/公司之间的距离**

**数据内部的可变性和其他外部影响因素**

最有趣的领域之一是查看彼此之间的客户距离，以了解是否存在因两个客户之间的距离而产生的行为模式？这个问题通常困扰着每个组织。

## **场景:**

> 在开始“解决方案”之前，可以使用实体之间的距离来解决一些场景:

**1。基于两个地址之间的信息和距离的匹配来合并实体/客户:**如果有两个地址相似且非常接近的客户记录，可以将它们合并为一个。

**2。了解与影响者的距离是否会对购买行为产生影响:**在行为分析的空间中，考察影响者/推广者之间的距离是否会对当地产生影响。

**3。超市/商店影响顾客的合理距离是多少？:**帮助确定一家商店与其自身和竞争对手之间的距离。

**4。一群“推动者”如何影响当地的“潜力”？:**当有一群促销员的时候，他们在当地会有什么影响？

当组织处于吸引、吸引和留住客户的征服模式时，许多这样的问题将是至关重要的。在每一个这样的场景中，位置都扮演着重要的角色。这可能会泄露许多关键信息，如影响范围、对购买模式的暗示等。

## **代码显示:**

转移到主题的中心，一个人如何根据距离建立群体？

**第 0 步:我会从时间表开始:**

```
def timeit(method):
    def timed(*args, **kw):
        ts = time.time()
        result = method(*args, **kw)
        te = time.time()
        if 'log_time' in kw:
            name = kw.get('log_name', method.__name__.upper())
            kw['log_time'][name] = int((te - ts) )
        else:
            print('%r  %2.2f s' % \
                  (method.__name__, (te - ts) ))
        return result
    return timed
```

**第一步:我将从纬度和经度创建笛卡尔坐标:**

为了使定义简单，在笛卡尔坐标系中:

x 轴穿过 long，lat (0，0)，因此经度 0 与赤道相交

y 轴穿过(0，90)

z 轴穿过磁极

其中 R 是地球的半径:6，378，137 米

```
[@timeit](http://twitter.com/timeit)
def to_cartesian(data, lat, lon):
   rad = 6378137
   data[‘x’] = data.apply(lambda row: rad* math.cos(np.deg2rad(row.lat))*math.cos(np.deg2rad(row.lon)),axis=1)
   data[‘y’] = data.apply(lambda row: rad * math.cos(np.deg2rad(row.lat))*math.sin(np.deg2rad(row.lon)),axis=1)
   data[‘z’] = data.apply(lambda row: rad* math.sin(np.deg2rad(row.lat)), axis = 1)
   return data
```

注意:如果您的数据只包含地址，也可以使用“geopy”之类的包将其转换为地理坐标

**第三步:下一步是创建树:**

用于快速最近邻查找的 kd 树。这个类提供了一组 k 维点的索引，可以用来快速查找任意点的最近邻。

```
[@timeit](http://twitter.com/timeit)
def create(df):
  print(‘creating…’)
  tree = cKDTree(df)
  print(‘created…’)
  return tree
```

**第四步:基于距离查询树**

这里我用的是 query_ball_point。这将找到距离点 x . r 内的所有点，然后将查询的点追加到列表中。

```
[@timeit](http://twitter.com/timeit)
def query(tree, df):
  print(‘query started…’)
  dist_in_mtr = 5 * 1609.34
  #BATCH_SIZE = 100_000
  results = []
  neigh_pair = tree.query_ball_point(df,dist_in_mtr,p=2,n_jobs=-1)
  for neighs in neigh_pair:
    if len(neighs) > 1:
      results.append([neighs[0],‘,’.join([str(x) for x in neighs[1:]]), i])
  print(‘query finished…’)
  return results
```

**第五步:展开列表**

使用 Explode 函数根据列表构建数据框，以便获得相邻对。

```
[@timeit](http://twitter.com/timeit)
def list_to_pandas(data):
  return pd.DataFrame(data, columns = [‘source’, ‘neighs’]).explode(‘neighs’)
```

**步骤加成:导入导出数据**

```
[@timeit](http://twitter.com/timeit)
def save(df, file_name):
    path_out = 'import/file/path' + file_name
    df.to_parquet(path_out, sep = '|', index = False)
    print('save finished...')[@timeit](http://twitter.com/timeit)
def load_df():
    print("fetching...")
    path = 'export/file/path'
    df = pd.read_parquet(path , sep = '|')
    print("fetched...")
    print(df.shape)
    return df
```

## **结论:**

KDTree 是一种计算实体间距离的简单方法，它直观地显示了数据在地图上的分布情况，并有助于查询树中的数据和评估距离。

当数据很大时，需要大量的代码优化，因为树会跳舞，查询会溢出内存，或者函数爆炸会创建一个巨大的数据集。

通过 LinkedIn 与我进行有趣的对话:[www.linkedin.com/comm/mynetwork/discovery-see-all?use case = PEOPLE _ FOLLOWS&follow member = shreepadahs](http://www.linkedin.com/comm/mynetwork/discovery-see-all?usecase=PEOPLE_FOLLOWS&followMember=shreepadahs)

## 参考:

[https://pypi.org/project/geopy/](https://pypi.org/project/geopy/)

[https://docs . scipy . org/doc/scipy/reference/generated/scipy . spatial . CKD tree . html](https://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.cKDTree.html)

[https://en . Wikipedia . org/wiki/Geodetic _ Reference _ System _ 1980](https://en.wikipedia.org/wiki/Geodetic_Reference_System_1980)

[https://stack overflow . com/questions/1185408/converting-from-经度-纬度-笛卡尔坐标#:~:text = Just % 20 to % 20 make % 20 the % 20 definition，axis % 20 goes % 20 through % 20 the % 20 poles](https://stackoverflow.com/questions/1185408/converting-from-longitude-latitude-to-cartesian-coordinates#:~:text=Just%20to%20make%20the%20definition,axis%20goes%20through%20the%20poles)。