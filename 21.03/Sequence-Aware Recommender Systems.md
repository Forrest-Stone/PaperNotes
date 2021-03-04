# Sequence-Aware Recommender Systems

[1] Quadrana, Massimo, Paolo Cremonesi, and Dietmar Jannach. “Sequence-Aware Recommender Systems.” ArXiv:1802.08452 [Cs], February 23, 2018. http://arxiv.org/abs/1802.08452.

# Abstract

Recommender systems are one of the most successful applications of data mining and machine learning
technology in practice. Academic research in the field is historically often based on the matrix completion problem formulation, where for each user-item-pair only one interaction (e.g., a rating) is considered. In many application domains, however, multiple user-item interactions of different types can be recorded over time. And, a number of recent works have shown that this information can be used to build richer individual user models and to discover additional behavioral patterns that can be leveraged in the recommendation process.

In this work we review existing works that consider information from such sequentially-ordered user-item interaction logs in the recommendation process. Based on this review, we propose a categorization of the corresponding recommendation tasks and goals, summarize existing algorithmic solutions, discuss methodological approaches when benchmarking what we call sequence-aware recommender systems, and outline open challenges in the area.

# Main Contributions

- 主要是介绍了序列感知推荐

# Model

## Introduction

![问题定义](./images/model.png)

序列感知推荐问题其实挺复杂的，我们研究的都是一些简单的基础的情况。用户的行为也是有很多类型的，以前都没有考虑过我。现有研究还是挺不统一的，者在研究中也发现了，应该针对某个具体的问题去研究。

## characterizing sequence-aware recommender systems

问题定义如图所示：

- inputs
- outputs
- abstract characterization

$$\forall c \in C, l_{c}^{'} = \mathop{\arg\min}\limits_{l\in L^*} u(c,l)$$

$c\in C$ 表示用户，$l\in L$ 表示序列

### 和其他领域的关系

- Implicit-Feedback Recommender Systems
  - 考虑为隐式反馈推荐。主要是有评分，没有考虑多次交互或者评分的时间戳顺序可能会误导推荐效果，怎么说呢，比如一般在注册的时候让你打分，即用户评分的时间点和消费交互的时间点不匹配
- Context-Aware and Time-Aware Recommender Systems
  - 在会话推荐中，用户的短期兴趣特备是最后一个或几个将是关键的上下文信息；时间感知推荐系统（TARS）通常考虑与过去用户操作相关的时间信息，以相应地调整推荐。顺序感知推荐器的重点通常不是过去用户交互的确切时间点，而是事件的顺序。
- 其他相关领域
  - 对话建议和兴趣转移

## A categorization of Sequence-Aware recommendation tasks

### Context Adaptation

### Trend Detection

### Repeated Recommendation

### Consideration of Order Constraints and Sequential Patterns

# My Thoughts

# Conclusion

@Author: Forrest Stone

@Email: ysbrilliant@163.com

@Github: https://github.com/Forrest-Stone

@Date: 2021-03-04 Thursday 09:38:37

