# Inter-Sequence Enhanced Framework for Personalized Sequential Recommendation

[1] Liu, Feng, Weiwen Liu, Xutao Li, and Yunming Ye. “Inter-Sequence Enhanced Framework for Personalized Sequential Recommendation.” ArXiv:2004.12118 [Cs], April 28, 2020. http://arxiv.org/abs/2004.12118.

## 摘要

Modeling sequential correlation of users’ historical interactions is essential in sequential recommendation. However, the majority of the approaches mainly focus on modeling the intra-sequence item correlation within each individual sequence but neglect the inter-sequence item correlation across
different user interaction sequences. Though several studies have been aware of this issue, their method is either simple or implicit. To make better use of such information, we propose an inter-sequence enhanced framework for the Sequential Recommendation (ISSR). In ISSR, both inter-sequence and intra-sequence item correlation are considered. Firstly, we equip graph neural networks in the inter-sequence correlation encoder to capture the high-order item correlation from
the user-item bipartite graph and the item-item graph. Then, based on the inter-sequence correlation encoder, we build GRU network and attention network in the intra-sequence correlation encoder to model the item sequential correlation within each individual sequence and temporal dynamics for predicting users’ preferences over candidate items. Additionally, we conduct extensive experiments on three real-world datasets. The experimental results demonstrate the superiority of ISSR over many state-of-the-art methods and the effectiveness of the inter-sequence correlation encoder.

## 结论

In this paper, we propose a Inter-Sequence enhanced framework for personalized Sequential Recommendation (ISSR). The inter-sequence item correlation encoder in ISSR utilizes two graphs (i.e., a user-item bipartite graph and an item-item co-occurrence graph) to capture the inter-sequence item correlations. The intra-sequence item correlation encoder aggregates the learned inter-sequence item correlation information and considers the item sequential correlations and temporal dynamics in a current sequence to generate the representation of users’ interests. Then the user’s next behavior
on the candidate items can be predicted by the learned interests. Extensive experiments on three real-world datasets are conducted. The results demonstrate the superiority of ISSR over many state-of-the-art methods.
