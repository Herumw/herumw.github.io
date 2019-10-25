---
layout:     post
title:      "论文：《SocialGCN: An Efficient Graph Convolutional Network based Model for Social Recommendation》（AAAI2019）"
subtitle:   
date:       2019-10-21
author:     SLY
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 推荐系统
    - 图神经网络
---
论文链接：[SocialGCN](https://arxiv.org/pdf/1811.02815.pdf)

# 动机

1.朴素的Collaborative Filtering有冷启动和数据稀疏问题

2.社交网络用于缓解数据稀疏问题，但是现有的模型只是用社交网络简单地考虑用户的朋友，没有考虑用户之间社交网络中用户与朋友间社交流动的情况，如用户的喜好会受到朋友的影响，而朋友的喜好也会受到他的朋友影响。

3.图卷积神经网络能很好地把周围节点的信息聚合到当前节点中

# 解决的问题
给定一个评分矩阵R和一个社交网络S，还有用户和物品的特征矩阵X和Y，要求预测每个用户对之前未打分物品的评分。

# 主要观点
论文提出了SocialGCN模型用于社交推荐问题，结合图卷积神经网络构建了社交网络信息传递的过程，再用经典的隐藏因子模型捕捉用户和物品的喜好。具体地，模型先定义用户的两个向量x和p分别表示用户的特征向量和用户潜在向量，同时定义物品的两个向量y和q分别表示物品的特征向量和物品潜在向量。之后物品向量通过连接它的特征向量和潜在向量来表示，其中特征向量是通过word2vec或者vgg网络从文本或者图像中抽取出来的，潜在向量是作为参数训练出来的。用户向量由两部分向量拼接而成，第一个部分向量通过平均用户喜欢的所有物品向量得到，第二部分通过图卷积神经网络捕捉社交网络信息得到。最后把用户向量和物品向量点乘得到预测的评分。
![avatar](https://raw.githubusercontent.com/Herumw/picture-for-markdownblog/master/picture/socialgcn.png)

# 数据集
yelp
Flickr

# 评价方法
HR
NDCG

