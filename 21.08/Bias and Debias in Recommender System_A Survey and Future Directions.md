# Bias and Debias in Recommender System: A Survey and Future Directions

[1] Chen, Jiawei, Hande Dong, Xiang Wang, Fuli Feng, Meng Wang, and Xiangnan He. “Bias and Debias in Recommender System: A Survey and Future Directions.” ArXiv:2010.03240 [Cs], October 7, 2020. http://arxiv.org/abs/2010.03240.


# Abstract

While recent years have witnessed a rapid growth of research papers on recommender system (RS), most of the papers focus on inventing machine learning models to better fit user behavior data. However, user behavior data is observational rather than experimental. This makes various biases widely exist in the data, including but not limited to selection bias, position bias, exposure bias, and popularity bias. Blindly fitting the data without considering the inherent biases will result in many serious issues, e.g., the discrepancy between offline evaluation and online metrics, hurting user satisfaction and trust on the recommendation service, etc. To transform the large volume of research models into practical improvements, it is highly urgent to explore the impacts of the biases and perform debiasing when necessary. When reviewing the papers that consider biases in RS, we find that, to our surprise, the studies are rather fragmented and lack a systematic organization. The terminology “bias” is widely used in the literature, but its definition is usually vague and even inconsistent across papers. This motivates us to provide a systematic survey of existing work on RS biases. In this paper, we first summarize seven types of biases in recommendation, along with their definitions and characteristics. We then provide a taxonomy to position and organize the existing work on recommendation debiasing. Finally, we identify some open challenges and envision some future directions, with the hope of inspiring more research work on this important yet less investigated topic.

# Motivation

- 用户行为数据是观察性的而不是实验性的。导致数据中存在很多的偏差。
- 现有的定义包括研究都是很分散的没有体系

# Main Contributions

- 总结论推荐系统中的七种偏置，并提供了定义和特点
- 总结了现在有的推荐系统中的去偏差的方法并分类
- 研究现有挑战并讨论未来的方向

# Introduction

推荐系统中偏差广泛存在
- 推荐模型训练用的用户行为数据是观察性的而不是实验性的。主要原因是用户根据暴露的物品产生行为，使得观察数据被系统的暴露机制和用户的自我选择所混淆。
- 项目或者用户在数据中表现得不同。例如，某些项目比其他项目更受欢迎，因此会收到更多的用户行为。因此，这些热门项目会对模型训练产生更大的影响，从而使推荐偏向于它们。同样的情况也适用于用户端。
- 推荐系统的一种性质是反馈循环。其曝光机制决定了用户行为，这些行为又被作为推荐系统的训练数据。这种反馈循环不仅会产生偏见，而且会随着时间的推移加剧偏见，导致 “富人更富” 的马太效应。

# Feedback Loop in Recommendation

将推荐的生命周期分为三个主要组件，如下图：

![feedback](./images/feedback_loop.png)

- User->Data：从用户收集数据的阶段。包含隐式反馈数据和显式反馈数据
- Data->Model：用收集的数据训练推荐模型，从用户历史行为数据学习用户的偏好
- Model->User：给用户推荐结果，将会影响用户未来的选择和决定

# Bias in Recommendation

## Bias in Data

### Bias in explicit feedback data

- Selection Bias. 选择偏差是因为用户可以自由选择要评分的项目，因此观察到的评分不是所有评分的代表性样本。换句话说，评级数据通常不是随机丢失的（MNAR）。
  - 用户往往喜欢倾向于给他们喜欢的项目评分
  - 用户尤其喜欢评分非常好或者非常差的项目
- Conformity Bias. 从众偏差的发生是因为用户倾向于与组中的其他人评分相似，即使这样做与他们自己的判断背道而驰，使得评分值并不总是表示用户的真实偏好。

### Bias in implicit feedback data

- Exposure Bias. 暴露偏差发生是因为用户只能接触到一部分的特定项目，因此未观察到的交互并不总是代表负面偏好。

未被观测的交互可能有两个原因：
- 项目不是用户感兴趣的
- 用户不知道这个项目

因此对于未观察到的数据很容易导致歧义，无法区分真正的负面互动（例如暴露但不感兴趣）和潜在的正面互动（例如未暴露）。

可以细分为：
  - previous mode bias. 暴露受先前推荐系统策略的影响，该系统控制要显示的项目。
  - selection bias. 用户会搜索查找感兴趣的，用户的选择也是一种曝光，让更相关的项目更容易被曝光
  - 用户的背景信息也会影响项目的曝光，比如社交朋友，所属社区以及地理位置等
  - popularity bias. 流行的项目更容易被用户看到

- Position Bias. 位置偏差是因为用户倾向于与推荐列表中较高位置的项目进行交互，而不管项目的实际相关性如何，因此交互的项目可能不是高度相关的。

## Bias in Model

偏置也不一定是有害的，事实上，在模型设计中故意添加了一些归纳偏置，以实现一些理想的特性。

- Inductive Bias. 归纳偏差表示模型为更好地学习目标函数和泛化训练数据而做出的假设。

将预测泛化到看不见的例子的能力是机器学习的核心。如果没有对数据或模型的假设，则无法实现泛化，因为看不见的示例可能具有任意的输出空间。同样，构建 RS 需要对目标函数的性质添加一些假设。除了目标函数，在其他方面也加入了归纳偏置。一个例子是自适应负采样器，其目的是对 “困难” 实例进行过采样以提高学习速度，即使最终的损失函数和原来的不一样。另一个例子是离散排序模型，它将用户和项目作为二进制代码嵌入以提高推荐效率，这是以牺牲表示能力为代价的。

## Bias and Unfairness in Results

- Popularity Bias. 热门商品的推荐频率甚至超过其受欢迎程度。

长尾现象：在大多数情况下，一小部分热门项目占了用户交互的大部分。

忽视流行偏置导致的问题：
- 它降低了个性化的水平并损害了偶然性。特别是对于小众用户而言
- 它降低了推荐结果的公平性。受欢迎的商品并不总是高质量的。过度推荐热门物品即使是很好的匹配也会降低其他物品的知名度，这是不公平的。
- 流行偏差会进一步增加流行物品的曝光机会，使流行物品更受欢迎。为未来训练收集的数据变得更加不平衡，产生所谓的 “马太效应” 问题。

- Unfairness. 该系统系统地和不公平地歧视某些个人或个人群体以利于其他人。

基于种族、性别、年龄、教育水平或财富等属性，不同的用户群体通常在数据中的代表是不平等的。在对此类不平衡数据进行训练时，模型极有可能学习这些代表性过高的群体，在排名结果中加强它们，并可能导致系统性歧视并降低弱势群体的可见性（例如，代表性不足的少数群体、种族或性别刻板印象）。例如，男性和女生所看到的工作推荐不一样。类似地，社交图中的朋友推荐可能会强化对多数人的历史偏见，并防止少数人成为具有高影响力的社会影响者。

## Feedback Loop Amplifies Biases

不同阶段发生的偏差可能会随着时间的推移沿着循环进一步加剧。以位置偏差为例，顶级项目通常受益于更大的流量，这反过来又增加了它们的排名突出和它们收到的流量，从而导致了富人变富的场景。这些放大的偏差也会降低多样性并加剧用户的同质化，从而增加所谓的 “回声室” 或 “过滤气泡”。

# Debias Methods

![debiasing_model](./images/debias_model.png)

## Methods for Selection Bias

观察到的评分数据并不是所有评分的代表性样本

### Debiasing in evaluation

这几种都是对有偏的训练好的模型进行评价

- Propensity Score. 使用逆序倾向得分，其实就是一个概率值

![ps_evaluation](./images/ps_evaluation.png)

- ATOP. 基于以下假设：在观察到的数据中随机缺少相关（高）评级值；关于其他评级值，我们允许任意缺失的数据机制，只要它们缺少比相关评级值更高的概率。

![atop_evaluation](./images/atop_evaluation.png)

缺点：只有真正的倾向可见时，才能保证 IPS 的估计器无偏。如果未正确指向倾向性，IPS 估算器仍将有偏。仅当两个假设保持时，才能保证 ATOP 的无偏。在实践中，丢失的机制通常很复杂，假设并不总是有效的。

### Debiasing in model training

- Data imputation. 数据的缺失值处理。考虑两个任务：评级预测任务（用户给出的评级值）和缺少数据预测任务（用户选择哪个项目去评分）。性能不好，因为缺失值的处理

- Propensity score. 倾向得分。跟以前一样，不过会导致高方差的影响，特别是当项目的流行度或者用户的火哦的那个有倾斜的时候。

- Doubly robust model.

![doubly_robust](./images/doubly_robust_model.png)

仍然需要相对准确的倾向分数或归纳数据，这通常很难指定。

- Meta Learning. 首先使用两个特定的推荐模型预先列出两个预测器（A1，A2），以产生具有伪额定值的可靠数据集，然后在伪额定值上培训目标推荐模型 A0。取决于预训练的预测器 A2 的质量。

## Methods for Conformity Bias

- 考虑用户评级符合公众意见。
- 将用户的评级值视为用户偏好和社会影响的合成结果。

## Methods for Exposure Bias

当用户仅暴露于项目的一部分时，发生曝光偏差，以至于未观察到的交互数据并不总是意味着负信号。

### Debiasing in evaluation

### Debiasing in model training

## Methods for Position Bias

### Click models

### Propensity score

## Methods for Popularity Bias

### Regularization

### Adversarial learning


### Causal graph

###

## Methods for Unfairness

### Fairness Formulations

### Rebalancing

### Regularization


### Adversarial Learning

### Causal Modeling

## Methods for Mitigating Loop Effect

### Uniform data.

### Reinforcement learning

### Others.

# Future work

## Evaluation of Propensity Scores

## General Debiasing Framework

## Better Evaluation

## Knowlege-enhanced Debiasing

## Explanation and Reasoning with Causal Graph

## Dynamic Bias

## Fairness-Accuracy Trade-off

# My Thoughts

# Conclusion

In this article, with reviewing more than 140 papers, we systematically summarize the seven kinds of biases in recommendation, along with providing their definitions and characteristics. We further devise a taxonomy to organize and position existing debiasing approaches. We list some open problems and research topics worth to be further explored. We hope this survey can benefit the researchers and practitioners who are keen to understand the biases in recommendation and inspire more research work in this area.



@Author: Forrest Stone
@Email: ysbrilliant@163.com
@Github: https://github.com/Forrest-Stone
@Date: 2021-08-25 Wednesday 10:37:22
