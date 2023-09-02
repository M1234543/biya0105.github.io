---
layout: post
title: "Generative Recommendation: Towards Next-generation Recommender Paradigm"
author: Gan Dingyi
categories: [ 推荐系统 ]
image: assets/images/甘定怡828封面.png
---
# Generative Recommendation: Towards Next-generation Recommender Paradigm


传统推荐属于基于检索的方式，推荐系统将物品库中的物品排序后推荐给用户，再根据用户的反馈（如点击）和上下文信息（如互动时间），以优化个性化的推荐。但这种检索范式存在两种局限。


+ 物品库中可用的内容可能不足以满足用户的个性化需求。比如不同的用户针对内容相同的短视频，可能喜欢不同风格的变体。
+ 被动反馈(隐式)无法明确有效地表达用户的信息需求。比如用户购买了物品但不一定对该物品满意。


作者提出用当下火热的AI-Generated Content (AIGC) 来帮助下一代推荐系统克服历史难题，主要有两方面潜力。

+ **实时调整或生成items以更加贴合用户需求**

+ **用户能通过自然语言指令更准确地表达自己的需求** 

## 作者提出的生成式推荐GeneRec的具体设计
![](https://markdown.liuchengtu.com/work/uploads/upload_4eeb420186f9c80c05040ff09773f51b.png)

+ Instructor分析多模态指令和用户反馈，如果用户通过指令明确请求AIGC或多次拒绝人工生成的项目，则启用AI生成器进行内容生成。并且根据AI生成器的输入要求，将用户的指令和反馈进行预处理形成指导信号。
+ AI editor根据用户的信息需求和偏好，然后相应地重新调整输入物品的用途。
+ AI creator根据用户的需求，并创建新的物品来满足用户的需求。


## 可行性研究
![](https://markdown.liuchengtu.com/work/uploads/upload_2826ba91f1fcbc9213b859667fae38e6.png)
![](https://markdown.liuchengtu.com/work/uploads/upload_4ef23da0e573c633f6d6ff699b2376d6.png)


## conclusion
1.提出了一种推荐系统新范式——GeneRec，集成用户多模态指令和反馈指导，指导AIGC自动生成个性化内容补充物品库。
2.作者初步探索了AI generator的可行性，对于整个GeneRec流程，还需要更多的研究完成。
3.对很多推荐场景的适用性还有待进一步探讨，比如淘宝实体商品推荐。

