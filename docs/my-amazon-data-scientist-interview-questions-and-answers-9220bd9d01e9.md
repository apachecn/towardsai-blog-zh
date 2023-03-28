# 我的亚马逊数据科学家面试问题和答案！

> 原文：<https://pub.towardsai.net/my-amazon-data-scientist-interview-questions-and-answers-9220bd9d01e9?source=collection_archive---------0----------------------->

## 所有真实的东西，没有多余的绒毛

![](img/31d6347ea096fa3fa6793682fbf3b988.png)

[日出王](https://unsplash.com/@sunriseking?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/amazon?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上的照片

你好。

我将直接进入它，因为就像我说的，这是你可以找到所有有用的和信息丰富的东西，没有无用的绒毛。我已经在亚马逊做了 6 个多月的数据科学家，这就是我的面试过程。在这篇文章中，你会发现我参加的几轮面试的细节，我被问到的问题，我给出的回答以及一些小技巧和窍门。

如果你想知道我*是如何为这次采访准备*的，你可以看看[这篇](/how-i-prepared-for-my-amazon-data-scientist-interview-5904db944378)文章。

好了，我们走吧！

# 1.人力资源筛选面试

我的第一次面试是通过电话进行的，时长将近 30 分钟。这是一个相当基本的步骤，人力资源代表会查看我的简历和过去的数据科学经历。我没有被问到任何详细的技术或行为问题，也没有得到深入的回答。这样做的唯一目的是初步筛选，以确认我符合我申请的职位的要求。我简单分享了我现在和以前的数据科学项目。我还确保使用一些技术术语来证明我确实拥有相关的知识。

因此，在这个面试步骤中需要记住的一些重要事情是:

```
Share your previous/latest Data Science job and project experiencesUse technical terms where necessary, but keep it simple.
```

# 2.视频电话面试招聘经理

我的第二次面试持续了一个小时，技术和行为部分各 30 分钟。

行为部分是我的招聘经理，他关注亚马逊的领导原则。其中包括**客户困扰**和**冲突解决**。你可以在这里 *找到更多关于这些 [*的细节。*我强烈建议每个人至少拿出两个你以前工作经历中的例子。](https://www.amazon.jobs/en/principles)*

```
For the behavioural part look up the Amazon Leadership Principles and come up with at least 2 examples for each principle.
```

技术部分由高级数据科学家进行。我得到了一个汽车制造商的样本数据集，并被要求使用分类模型预测汽车的价格。有人与我分享了一个屏幕，我在上面从头开始编写解决方案。对我帮助很大的是，当我继续研究解决方案时，能够讨论我的思维过程，因为当时间用完时，我还没有完成代码，但我的面试官对我所做的很满意。

```
For ML questions, keep your thought process clean. Remember the basics that is- Explore the data- Preprocess the data- Remember basic preprocessing requirements such as filling in null values, what kind of null values you are looking for, normalising the data, how you'll handle numerical and categorical values and how you'll handle missing values- What kind of model you will use and why (safest to start with is Random Forest for Gradient Boosting). Think of advantages and disadvantages of your model- Remember hyper-parameter optimization- Final variable you'll be tracking (basically result)
```

# 3.人力资源视频电话面试

我对这个职位的第三次面试又是和一个人力资源代表(对我来说，就是我最初面试的那个人)。这也持续了 30 分钟，只是行为上的。它包括对一个领导原则的讨论——顾客至上。这是我使用之前准备的第二个例子的地方。

剩下的时间都是代表帮我理解下一次面试(最难也是最长的一次)和分享如何准备的小技巧。

```
Again, for the behavioural part, look up the Amazon Leadership Principles and come up with at least 2 examples for each principle from your personal experiences. Try your best not to repeat the examples - share unique experiences with each interviewee.
```

# 4.循环(6 次视频电话采访)

这是整个过程中最令人紧张、出汗、心跳和口干舌燥的一轮。我和 6 个不同的面试官进行了 45-60 分钟的单独谈话。这些会议分为两天(每天 3 次面谈)。

有 3 场技术面试，分别与 SQL、机器学习、深度学习有关。

对于 SQL 面试，给了我两个表——客户 id 和订单 id。

```
**SQL Question**cust_table: cust_id, country, phone
order_table: order_id, order_val, order_name, country, cust_id, dateQ1\. Total order value for every customer
select cust_table.cust_id, sum(order_val)
from cust_table LEFT JOIN order_table
ON cust_table.cust_id = order_table.cust_id
group by 1Q2\. Total count of orders by country
select country, count(distinct order_id)
from order_table
group by 1Q3\. Max value of order bought by customer each month
select cust_table.cust_id, date_trunc('month', date) as mnth,
max(order_val) over (partition by cust_id, date_trunc('month', date)) as max_val
from cust_table LEFT JOIN order_table
ON cust_table.cust_id = order_table.cust_id
group by 1, 2
```

关于机器学习面试，有人告诉我，我们要在 XYZ 乡下开一家新店。然后我被问了一系列相关的问题，包括我将如何决定在哪里设立履行中心，我将考虑什么指标，我将使用什么模型，以及我将如何获得数据。

```
**ML Question**- Before starting work on the problem, remember to ask A LOT of questions. Make sure you understand what the interviewer is asking and looking for.- In this interview, I asked a few questions such as: Is this the first store in the country? Is there any historic data available for this country, etc.- For metrics, I recommended to use current metrics from existing fulfilment centres that'll help decide where to build the centre. These included distance of current fulfilment centres from city centre, demand of orders, supply available, weather conditions.- I used a XGBoost regression model to predict a distance value for the future fulfilment centre from the main city.- In hindsight, I believe I should have spent a bit more time to explore available metrics and how to better use them in my model.
```

对于第三个技术问题，我必须解释 LSTMs、BERT 和注意力层。

```
Following are some amazing sources to understand these:
[LSTM](https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21), [BERT](https://huggingface.co/blog/bert-101), [Attention](https://theaisummer.com/attention/).
```

其他三次面试都是行为(主要围绕领导原则)和过去经历的混合。

```
Again, remember to share unique experiences with each interviewee.
```

# 5.视频电话面试招聘经理

我参加的第五次也是最后一次面试持续了 30 分钟，面试者是我的招聘经理。我被问了两个机器学习问题——第一个是关于随机森林及其工作原理，第二个是关于 NLP 和 LSTM。

```
Following are some amazing sources to understand:
[Random Forest](https://www.analyticsvidhya.com/blog/2021/06/understanding-random-forest/), [LSTM](https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21)
```

现在你知道了。当我自己准备的时候，老实说，我找不到一篇文章包含了我需要知道的关于面试过程的一切。所以，我对自己发誓，我将分享我学到的任何东西，希望它能让寻找这些资源的其他人受益。

让我知道这是否有帮助，如果你有任何其他你个人经验的补充！