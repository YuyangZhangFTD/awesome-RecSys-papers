# Writing Practice

## Introduction

---

推荐系统分成显式和隐式两种

> Personalized recommendation of relevant content is a common task in many retrieval systems. Many collaborative filtering approaches [1] attempt to identify user preferences based on explicit feedback such as user ratings. However, implicit feedback[2], in which a user’s preferences are expressed through item interactions such as views or purchases, is often more common than explicit feedback.

---

开头引出推荐系统

> The past decade has seen a large number of web-based recommendation systems deployed with great success in diverse domains. Their surge can be attributed to a variety of factors. Among them, a key factor is the rather limitless choice of items available to a user in a multitude of applications. A partial list of extremely popular web-based recommender services are: Netflix, for movies, Amazon.com for products, Pandora, Last.fm, and iTunes Genius for music, YouTube’s Recommended For You, for online videos, Facebook’s Other People You May Know, for social networking, What Should I Read Next, for books etc

---

MSE并不是一个好的评估标准，原因一推荐系统往往只需要topk个推荐物品，而不是准确的评分，原因二是这些分数并没有直接被用到，所以减小MSE并不是必须的。

> The reasons are two-fold. First, as mentioned earlier, the way most recommenders are used in practice is to generate a top-k list of the items to show each user. The second main criticism of MSE as a training criterion is that most of the time, the actual predicted ratings values themselves are not even shown to the users directly.

---

引出问题，后面跟问句

> A number of questions naturally crop up. ...

---

---

---

---

---

## Related Work

---

NDCG 描述

> NDCG was developed with ranking in information retrieval as the target application [3]. Given relevance values (typically on an ordinal scale) for a set of items (web-pages) returned as response to a search query, NDCG can score any list of permutations of these items. NDCG was designed so that the list with the highest relevance items in the top ranked positions is the one which gets the maximum score. 

---

deep learning 和 recommendation system

> Inspired by the immense progress in deep learning and natural language processing, a series of works have emerged from new perspectives [4]. YouTube introduces its recommender system [5], where the recommendation is posed as an extreme multiclass classification, and sampled softmax [6] is used to reduce computational complexity. In this way, the model can learn both user and item embeddings with user behaviors as input. Such user embedding can response to user interests’ evolution instantaneously, and the efficiency of online serving could also be ensured by hashing [7] or quantization [8] indices. Nevertheless, the approximate kNN search manner limits the similarity metric between user and item to inner product or Euclidean distance of their embeddings, which amounts to limit the complexity and capacity of the last mile model that used to distinguish whether user-item pairs are related. Furthermore, as one of the most important transformed features in recommender system [9], the cross-product transformation between user’s historical behaviors and candidate items can not take efforts in this kind of system design.

---

---

---

---

---

---

---

## Model define
---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

# Reference
1. Koren, Yehuda, Robert Bell, and Chris Volinsky. "Matrix factorization techniques for recommender systems." Computer 42.8 (2009). **矩阵分解模型最早的一篇**
2. Hu, Yifan, Yehuda Koren, and Chris Volinsky. "Collaborative filtering for implicit feedback datasets." Data Mining, 2008. ICDM'08. Eighth IEEE International Conference on. Ieee, 2008. **隐式反馈比较早的一篇，加权矩阵分解模型**
3. K. J¨ arvelin and J. Kek¨ al¨ ainen. Cumulated gain-based evaluation of ir techniques. ACM Trans. Inf. Syst., 20:422-446, October 2002.  **NDCG用于信息检索领域**
4. Shuai Zhang, Lina Yao, and Aixin Sun. 2017. Deep Learning based Recommender System: A Survey and New Perspectives. (2017).   **DL和RS的survey**
5. Paul Covington, Jay Adams, and Emre Sargin. 2016. Deep Neural Networks for YouTube Recommendations. In ACM Conference on Recommender Systems. 191–198.   **youtube 16年深度学习推荐系统**
6. SÃľbastien Jean, Kyunghyun Cho, Roland Memisevic, and Yoshua Bengio. 2014. On Using Very Large Target Vocabulary for Neural Machine Translation. Computer Science (2014).    **bengio nlp 语音翻译，负采样**
7. J. Weston, A. Makadia, and H. Yee. 2013. Label partitioning for sublinear ranking. In International Conference on Machine Learning. 181–189
8. Zeno Gantner, Steffen Rendle, Christoph Freudenthaler, and Lars SchmidtThieme. 2011. MyMediaLite: A free recommender system library. In Proceedings of the fifth ACM conference on Recommender systems. ACM, 305–308.     **推荐系统库MyMediaLite **
9. Heng-Tze Cheng, Levent Koc, Jeremiah Harmsen, Tal Shaked, Tushar Chandra, Hrishi Aradhye, Glen Anderson, Greg Corrado, Wei Chai, Mustafa Ispir, et al. 2016. Wide & deep learning for recommender systems. In Proceedings of the 1st Workshop on Deep Learning for Recommender Systems. ACM, 7–10.  **Google的wide&deep模型**