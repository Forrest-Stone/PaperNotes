# Rethinking Item Importance in Session-Based Recommendation

[1] Pan, Zhiqiang, Fei Cai, Yanxiang Ling, and Maarten de Rijke. “Rethinking Item Importance in Session-Based Recommendation.” ArXiv:2005.04456 [Cs], May 9, 2020. http://arxiv.org/abs/2005.04456.

## 摘要

Session-based recommendation aims to predict users’ based on anonymous sessions. Previous work mainly focuses on the transition relationship between items during an ongoing session. They generally fail to pay enough atention to the importance of the items in terms of their relevance to user’s main intent. In this paper, we propose a Session-based Recommendation approach with an Importance Extraction Module, i.e., SR-IEM, that considers both a user’s long-term and recent behavior in an ongoing session. We
employ a modifed self-atention mechanism to estimate item importance in a session, which is then used to predict user’s long-term preference. Item recommendations are produced by combining the user’s long-term preference and current interest as conveyed by the last interacted item. Experiments conducted on two benchmark datasets validates that SR-IEM outperforms the start-of-the-art in terms of Recall and MRR and has a reduced computational complexity.

## 结论

We have proposed an Importance Extraction Module for Sessionbased Recommendation (SR-IEM), that incorporates a user’s longterm preference and his current interest for item recommendation. A modifed self-atention mechanism is applied to estimate item importance in a session for modeling a user’s long-term preference, which is combined with user’s current interest indicated by the last item to produce the fnal item recommendations. Experimental results show that SR-IEM achieves considerable improvements in terms of Recall and MRR over state-of-the-art models with reduced computational costs compared to competitive neural models. As to future work, we would like to apply the Importance Extraction Module to other tasks, e.g., dialogue systems and conversation recommendation.
