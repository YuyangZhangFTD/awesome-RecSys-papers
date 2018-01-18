# Writing Practice

## Introduction

---

集成模型应用广泛

> As a result, tree ensemble models in general, have gained or are gaining widespread popularity in a number of application areas; examples include chemistry [1], genomics [2], ecology [3,4], economics [5,6], marketing [7] and operations management [8].

---

---

---

---

---

---

---

---

## Related Work

---

决策树算法发展历史

> Decision tree models became popular in machine learning with the introduction of two algorithms,
ID3 (iterative dichotomiser; see [9]) and CART (classification and regression tree; see [10]). 

---

集成学习发展，bagging和boosting

> [11] proposed the idea of bootstrap aggregation, or bagging, where one builds a collection of predictive models, each trained with a bootstrapped sample of the original training set; the predictions of each model are then aggregated into a single prediction (for classification, this is by majority vote; for regression, this is by averaging). The motivation for bagging is that it reduces the prediction error for predictive models that are unstable/highly sensitive to the training data (such as CART); indeed, [11] showed that bagged regression trees can be significantly better than ordinary regression trees in out-of-sample prediction error. Later, [12] proposed the random forest model, where one builds a collection of bagged CART tree for which the subset of features selected for splitting at each node of each tree is randomly sampled from the set of all features (the so-called random subspace method; see [13]). Concurrently, a separate stream of literature has considered the idea of boosting [14], wherein one iteratively builds a weighted collection of basic predictive models (such as CART trees), with the goal of reducing the prediction error with each iteration.

> Tree ensembles occupy a central place in machine learning because they generally work very well in practice. In a systematic comparison of 179 different prediction methods on a broad set of benchmark data sets, [15] found that random forests achieved best or near-best performance over all of these data sets. Boosted trees have been similarly successful: on the data science competition website Kaggle, one popular implementation of boosted trees, XGBoost, was used in more than half of the winning solutions in the year 2015 [16]. There exist robust and open source implementations of many tree ensemble models. For boosted trees, the R package gbm [17] and XGBoost are widely used; for random forests, the R package randomForest [18] is extremely popular.

---

集成模型理论

> At the same time, there has been a significant effort in the machine learning research community to develop a theoretical foundation for tree ensemble methods; we briefly survey some of the work in this direction for random forests. For random forests, the original paper [12] developed an upper bound on the generalization error of a random forest. Later research studied the consistency of both simplified versions of the random forest model (for example, [19]) as well as the original random forest model (for example, [20]). Recently, [21] showed that certain forms of regression trees and random forests converge uniformly over the feature space to the true regression function, while [22] considered how to use random forests for causal inference. For an excellent overview of recent theoretical advances in random forests, the reader is referred to [23].

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

# Reference
1. V. Svetnik, A. Liaw, C. Tong, J. C. Culberson, R. P. Sheridan, and B. P. Feuston. Random forest: a classification and regression tool for compound classification and qsar modeling. Journal of Chemical Information and Computer Sciences, 43(6):1947-1958, 2003.
2. R. D´ıaz-Uriarte and S. A. De Andres. Gene selection and classification of microarray data using random forest. BMC bioinformatics, 7(1):3, 2006.
3. J. Elith, J. R. Leathwick, and T. Hastie. A working guide to boosted regression trees. Journal of Animal Ecology, 77(4):802-813, 2008.
4. D. R. Cutler, T. C. Edwards, K. H. Beard, A. Cutler, K. T. Hess, J. Gibson, and J. J. Lawler. Random forests for classification in ecology. Ecology, 88(11):2783-2792, 2007.
5. H. R. Varian. Big data: New tricks for econometrics. The Journal of Economic Perspectives, 28(2):3-27,2014.
6. P. Bajari, D. Nekipelov, S. P. Ryan, and M. Yang. Machine learning methods for demand estimation. The American Economic Review, 105(5):481-485, 2015.
7. A. Lemmens and C. Croux. Bagging and boosting classification trees to predict churn. Journal of Marketing Research, 43(2):276-286, 2006.
8. K. J. Ferreira, B. H. A. Lee, and D. Simchi-Levi. Analytics for an online retailer: Demand forecasting and price optimization. Manufacturing & Service Operations Management, 18(1):69-88, 2015.
9. J. R. Quinlan. Induction of decision trees. Machine learning, 1(1):81-106, 1986.
10. L. Breiman, J. Friedman, C. J. Stone, and R. A. Olshen. Classification and regression trees. CRC press,1984.
11. L. Breiman. Bagging predictors. Machine learning, 24(2):123-140, 1996.
12. L. Breiman. Random forests. Machine Learning, 45(1):5-32, 2001.
13. T. K. Ho. The random subspace method for constructing decision forests. IEEE Transactions on Pattern Analysis and Machine Intelligence, 20(8):832-844, 1998.
14. R. E. Schapire and Y. Freund. Boosting: Foundations and algorithms. MIT press, 2012.
15. M. Fern´andez-Delgado, E. Cernadas, S. Barro, and D. Amorim. Do we need hundreds of classifiers to solve
real world classification problems. Journal of Machine Learning Research, 15(1):3133-3181, 2014.
16. T. Chen and C. Guestrin. XGBoost: A scalable tree boosting system. In Proceedings of the 22Nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pages 785-794. ACM, 2016.
17. G. Ridgeway. gbm: Generalized boosted regression models. R Package version 1.5-7, 2006
18. A. Liaw and M. Wiener. Classification and regression by randomForest. R news, 2(3):18-22, 2002.
19. G. Biau, L. Devroye, and G. Lugosi. Consistency of random forests and other averaging classifiers. Journal of Machine Learning Research, 9(Sep):2015-2033, 2008.
20. E. Scornet, G. Biau, and J.-P. Vert. Consistency of random forests. The Annals of Statistics, 43(4):1716-1741, 2015
21. S. Wager and G. Walther. Adaptive concentration of regression trees, with application to random forests. arXiv preprint arXiv:1503.06388, 2015.
22. S. Wager and S. Athey. Estimation and inference of heterogeneous treatment effects using random forests. arXiv preprint arXiv:1510.04342, 2015.
23. G. Biau and E. Scornet. A random forest guided tour. TEST, 25(2):197-227, 2016.