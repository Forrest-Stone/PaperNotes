# Session-aware Linear Item-Item Models for Session-based Recommendation

[1] Choi, M., Lee, J., Shim, H., & Lee, J. (2021). Session-aware Linear Item-Item Models for Session-based Recommendation. arXiv preprint arXiv:2103.16104.

# Abstract

Session-based recommendation aims at predicting the next item given a sequence of previous items consumed in the session, e.g., one-commerce or multimedia streaming services. Specifically, session
data exhibits some unique characteristics, i.e., session consistency and sequential dep endency over items within the session, rep eated item consump tion, and session timeliness. In this paper, we propose
simple-yet-effective linear models for considering the holistic aspects of the sessions. The comprehensive nature of our models helps improve the quality of session-based recommendation. More
importantly, it provides a generalized framework for reflecting different perspectives of session data. Furthermore, since our models can be solved by closed-form solutions, they are highly scalable. Experimental results demonstrate that the proposed linear models show competitive or state-of-the-art performance in various metrics on several real-world datasets.

# Main Contributions

- 这篇论文将会话推荐的几个属性都考虑进来，并且融合在一起。
- 这篇线性的模型用一个闭环解决方案更加具有扩展性。
- 在不同的数据集上不同的评价指标上做了对比试验。

# Model

介绍了会话推荐的四个特点：

- Session consistency：会话一致性。会话内的items都是高度相关的，反映了用户的特定相关的兴趣。比如，用户听的歌单通常有一个主题，要么是相似的心情，同样类型的或者同一个专辑等等；
- Sequential dependency：序列依赖性。有一些items往往被交互在一个特定的序列下。比如电视的节目，集数都是顺序被观看的。所以在这样的情况下，当前会话的最后一个经常具有很重要的信号来预测下一个。
- Repeated item consumption：重复的项目消费。在一个会话中用户可能重复消费多次同一个item。比如一个用户重复听喜欢的歌曲很多次，或者用户选一个item跟其他的比较也会多次点击。
- Timeliness of sessions： 会话的即时性？一个会话反映用户在某个时刻的兴趣，一组这样的会话反映了用户最近的兴趣变化趋势。例如，许多用户倾向于更频繁地观看新发行的音乐视频。因此，与过去的会话相比，最近的会话可能是预测用户当前兴趣的更好指标。换句话看也就是说要关注一下会话间的关系？并且最后的会话占比重要性越大？


RNN 或者 attention 更关注于 sequential dependency，GNN 除了上面的 SD 还考虑了 session consistency。一些 attention 如 repeatnet 关注于重复的，即时性则是权重值加和方法。

![session representations](./image)

介绍了会话的两种表示：

- Full session representation：

# My Thoughts

# Conclusion

@Author: Forrest Stone

@Email: ysbrilliant@163.com

@Github: https://github.com/Forrest-Stone

@Date: 2021-04-11 Sunday 15:45:25
