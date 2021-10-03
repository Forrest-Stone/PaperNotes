# Graph Neural Networks for Recommender Systems: Challenges, Methods, and Directions

[1] Gao, Chen, Yu Zheng, Nian Li, Yinfeng Li, Yingrong Qin, Jinghua Piao, Yuhan Quan, et al. “Graph Neural Networks for Recommender Systems: Challenges, Methods, and Directions.” ArXiv:2109.12843 [Cs], September 27, 2021. http://arxiv.org/abs/2109.12843.


# Abstract

Recommender system is one of the most important information services on today’s Internet. Recently, graph neural networks have become the new state-of-the-art approach of recommender systems. In this survey, we conduct a comprehensive review of the literature in graph neural network-based recommender systems. We first introduce the background and the history of the development of both recommender systems and graph neural networks. For recommender systems, in general, there are four aspects for categorizing existing works: stage, scenario, objective, and application. For graph neural networks, the existing methods consist of two categories, spectral models and spatial ones. We then discuss the motivation of applying graph neural networks into recommender systems, mainly consisting of the high-order connectivity, the structural property of data, and the enhanced supervision signal. We then systematically analyze the challenges in graph construction, embedding propagation/aggregation, model optimization, and computation efficiency. Afterward and primarily, we provide a comprehensive overview of a multitude of existing works of graph neural network-based recommender systems, following the taxonomy above. Finally, we raise discussions on the open problems and promising future directions of this area. We summarize the representative papers along with their codes repositories in https://github.com/tsinghua-fib-lab/GNN-Recommender-Systems.

# Motivation

- 分类了基于 GNN 的推荐系统
- 为什么 GNN 可以用来搞推荐以及难点

# Main Contributions

- 分类了基于 GNN 的推荐系统，从四个方面。阶段，实例，目标和应用。
- 提供了为什么 GNN 可以用来做推荐以及怎么用来做。难点和解决方案是什么

# Introduction

![RS](./images/RS.png)

将 GNN用到推荐中去，面临下面问题：
- 数据输入，怎么构图
- 针对特定任务，如何设计 GNN
- 如何优化
- 如何降低时间复杂度

# Recommender Systems

![RS_pipline](./images/RS_pipline.png)

## Stages

- Matching. 从巨大的 items 集合中选取成百上千个候选集
- Ranking. 对这些候选集排序
- Re-ranking. 根据更多的要求进行再排序

## Scenarios

- Social Recommendation. 社交影响和社会同质性

![Social](./images/social_RS.png)

- Sequential Recommendation. 长期兴趣，短期兴趣，动态兴趣

![SR](./images/SR_RS.png)

- Session-based Recommendation. 用户资料和长期兴趣一般不可见，匿名数据

![session](./images/session_RS.png)

- Bundle Recommendation. 项目的集合，时装药物等

![bundle](./images/bundle_RS.png)

- Cross-Domain Recommendation. 多模态，冷启动，数据稀疏问题

![cross](./images/cross_domain_RS.png)

- Multi-behavior Recommendation. 多行为，浏览购买点击，加入购物车等

![multi](./images/multi_behaviour_RS.png)

## Objectives.

- Diversity. 个体层面和系统层面，长尾问题

![Diversity](./images/diversity_RS.png)

- Explainability.

## Applications.

# Graph Neural Networks

![GNN](./images/GNN_overall.png)

## Graph Construction.

- Homogeneous graph. 每条边连接两个顶点，只有一种类型的节点和边
- Heterogeneous graph. 每条边连接两个顶点，多种类型结点或边
- Hypergraph. 每条边可以连接多个顶点

## Network Design.

- GCN

![GCN](./images/GCN_formula.png)

- GraphSAGE

![graph](./images/GraphSAGE_formula.png)

- GAT

![GAT](./images/GAT_formula.png)

- HetGNN

- HGNN

![HGNN](./images/HGNN_formula.png)

![GNN_comparison](./images/GNN_comparison.png)

## Model Optimization.

分类回归预测，成对损失 BPR，点损失 交叉熵 CE

## Why are GNNs required for recommender systems

- Structural data. 图数据
- High-order connectivity. 相似性，协同过滤信号
- Supervision signal. 半监督信号，附加任务

# CHALLENGES OF APPLYING GNNS TO RECOMMENDER SYSTEMS

## Graph Constrcution

- Nodes.
- Edges.

## Network Design

## Model Optimization

## Computation Efficiency

# EXISTING METHODS

## Taxonomy

![summary](./images/summary_GNN.png)
![scenario](./images/summary_GNN_scenarios.png)
![objectives](./images/summary_GNN_objectives.png)

## GNN in Different Recommendation Stages

- GNN in Matching. 效率，粗粒度

![matching](./images/match_GNN.png)

- GNN in Ranking.

![ranking](./images/ranking_GNN.png)

- GNN in Re-ranking.

根据预先定义的规则或其他的功能去获得更好的质量。

- 不同的项目可以通过某些关系（例如可替代性和互补性）相互影响。
- 不同的用户往往有不同的偏好，因此重新排名也可以个性化。

# GNN in Different Recommendation Scenarios

## GNN in Social Recommendation.

- Graph construction.
- Information propagation.

![illustration](./images/illustration_social_GNN.png)

![details](./images/detail_social_GNN.png)

## GNN in Sequential Recommendation.

![illustration](./images/illustration_sequential_GNN.png)

![details](./images/details_sequential_GNN.png)

## GNN in Session-based Recommendation

会话数据包含用户的兴趣和噪音数据

- Graph construction.
- Information propagation.

![illustration](./images/illustration_session_GNN.png)

![details](./images/details_session_GNN.png)

## GNN in Bundle Recommendation.

- 隶属关系
- 稀疏数据
- 高阶关系

![bundle_details_GNN](./image/../images/bundle_GNN_details.png)

## GNN in Cross-Domain Recommendation

![cross_domian](./image/../images/cross_domian_GNN_details.png)

## GNN in Multi-behavior Recommendation.

![multi_behavior](./images/multi_behavior_GNN_details.png)

# GNN for Different Recommendation Objectives

## GNN for Diversity.

![diversity](./images/diversity_GNN.png)

## GNN for Explainablility.

![explainable](./images/explainable_GNN.png)

## GNN for Fairness.

![fairness](./images/fairness_GNN.png)

## GNN for Specific Recommendation Applications

# OPEN PROBLEMS AND FUTURE DIRECTIONS

## Go Deeper

设计更深的 GNN，强化学习，膨胀卷积，残差网路

## Dynamic GNN in Recommendation

用户数据是动态变化的

## KG-enhanced recommendation with GNN

冷启动，扩展性，动态性

## Efficiency and Scalability

大图

## Self-supervised GNN

更多的监督信息

## Conversational Recommendation with GNN

## AutoML-enhanced GNN

泛化，自动选择

# My Thoughts

- 偶然间看到，还不错很详细
- 论文中提到 21 年的两篇论文关于序列推荐用到了 targets 后面的信息，不过是关于其他的序列中的。我的 idea 还不错哦，至少比他们早了很多，他们的也不错
- 国强假期结束了

# Conclusion

There is a rapid development of graph neural networks models in the research field of recommender systems. This paper provides an extensive survey systematically presenting the challenges, methods, and future directions in this area. Not only the history of development and also the most recent advances are well covered and introduced. We hope this survey can well help both junior and experienced researchers in the relative areas.




@Author: Forrest Stone
@Email: ysbrilliant@163.com
@Github: https://github.com/Forrest-Stone
@Date: 2021-10-03 Sunday 09:53:20
