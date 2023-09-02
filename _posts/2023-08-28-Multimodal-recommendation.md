---
layout: post
title: "Multimodal Recommendation"
author: ChenWuhan
categories: [ 推荐系统 ]
image: assets/images/18.jpg
---
#    Section1:Traditional multimodal recommendations
**Multimodal recommendation**:use  various  types of data(text, audio, video)  to give users personalized advice
**Goal**:served as supplementary information of user-item interactions, aimed  to  improve recommendation effect
**Keyword**: fusion    

![](https://markdown.liuchengtu.com/work/uploads/upload_9efce1af6c64374dbc5821e9fb08ecc8.png)


There are three important questions:
**1.When to fusion?**
Early fusion: The features are fused, then send to the recommendation model.
Intermediate fusion: The featues are fused in the recommendation model.
Late fusion: The features are fused after making the interaction independently.
**2.How to fusion?**
concatenation, attention-based.....
**3.Where to fusion?**
user side(a), item side(b), both( c)
![](https://markdown.liuchengtu.com/work/uploads/upload_73780c68934e8bbe5165349ed67243b3.png)


**An example of user side fusion:**
**Feature**：item videos/item  pictures
**Fusion method**：attention
**Fusion stage**：intermediate
![](https://markdown.liuchengtu.com/work/uploads/upload_da0b263b44e2ae7df406de8b2faefe73.png)


**An example of item side fusion:**
**Feature**：text+picture  
**Fusion  method**：attention
**Fusion  stage**：intermediate
![](https://markdown.liuchengtu.com/work/uploads/upload_9b966f7481773068ccc4b7ce94e62331.png)


**An example of item fusion on both side:**
**Feature**：text/picture/audio
**Fusion method**：concatenation
**Fusion stage**：late 
![](https://markdown.liuchengtu.com/work/uploads/upload_5b52da04c36bfbf520d16bf218f994bc.png)

The similarity of these fusion methods is using item embeddings, but is it good?


# Section2 IDRec VS MoRec 
**The  definition of IDRec:** methods with item embeddings.
**The  definition of MoRec:** methods without item embeddings.

Several papers pointed out the disadvantage of IDRec:


"A major issue with this modeling way is that the learned model is <font class="text-color-13" color="#ffeb3b">difficult to be transferred</font> to new recommendation scenarios, even when the underlying data forms are exactly the same. Such an issue limits the reuse of the recommendation model across domains . As a common case, we need to<font class="text-color-13" color="#ffeb3b"> re-train</font> a sequential recommender from scratch when adapting to a new domain, which is tedious and resource-consuming. ——KDD’22 "

   

"pre-trained IDRec <font class="text-color-121" color="#ffeb3b">is not transferable across platforms<font class="text-color-13" color="#ffeb3b"></font></font> given that user IDs and item IDs are in general not shareable in practice.” ——MoRec SIGIR’23 "

Why IDRec is not transderable? If we want to achieve a recommendtion foundation model, we need to follow the pipelines below:
![](https://markdown.liuchengtu.com/work/uploads/upload_798049a16194270532468cddf421479e.png)
In pre-training stage, we got source dataset A, in fine-tuning stage, we got target dataset B,the item sets of A and B are not shared.If we use item embeddings,we have to add randomly initialized item embeddings of B to recommendation model in fine-tuning stage, as shown in the red markings in the following figure .These item embeddings need to be retrained, it is time consuming.
![](https://markdown.liuchengtu.com/work/uploads/upload_cb151fc47227fbeadfca5dfe6b8b2545.png)

But MoRec also has its advantages and disadvantages:


**Advantage**
1. MoRec utilize the internal characteristics of the modality, thus build a bridge between source field and target field.
2. MoRec can benefit from the progress of CV and NLP methods.
   

**Disadvantage**
1. computation overhead
   
# Section3 Experiment 
   Conclusion 1: MoRec is competent for regular recommendation under the SASRec framework.
![](https://markdown.liuchengtu.com/work/uploads/upload_7ad8c3d9eab5d5442c8344366661a1f3.png)


Conclusion 2: MoRecoutperforms IDRec on cross domain recommendation. 
![](https://markdown.liuchengtu.com/work/uploads/upload_55c657ae1a1a1b62a71ee6d995005290.png)

   

Conclusion 3 . The cost of MoRec is still much higher than IDRec. 
![](https://markdown.liuchengtu.com/work/uploads/upload_8ab627b587f8f3e3c1c064986c7d14ad.png)


# Section4 Our thought 
What  to  do  in  pretraining stage？ 
1.   We need to design a better conversion module from original feature to ‘mature feature’, which is suitable enough for fusion and recommendation task. 
2.    We can conduct experimental research to find the ideal size and range of pre-trained recommendation datasets. 

What  to  do  in  fine-tuning stage？ 
 1.  We can add unique module that belongs to the downstream task, for example, each platform has its own tensor. 


# References 


[1] Zhou H, Zhou X, Zeng Z, et
al. A Comprehensive Survey on Multimodal Recommender Systems: Taxonomy,
Evaluation, and Future Directions[J]. arXiv preprint arXiv:2302.04473, 2023.

[2] Li J, Wang M, Li J, et al.
Text Is All You Need: Learning Language Representations for Sequential
Recommendation[J]. arXiv preprint arXiv:2305.13731, 2023.

[3] Yuan
Z, Yuan F, Song Y, et al. Where to go next for recommender systems? id-vs.
modality-based recommender models revisited[J]. arXiv preprint arXiv:2303.13835, 2023.

[4]  Hou
Y, Mu S, Zhao W X, et al. Towards universal sequence representation learning
for recommender systems[C]//Proceedings of the 28th ACM SIGKDD Conference on
Knowledge Discovery and Data Mining. 2022: 585-593.





 









