---
title: "Random Forest and Extensions"
date: 2021-04-01
subtitle: "Using the theoretical guarantees of Random Forest to extend and improve the algorithm"
excerpt: "Random forest is a classification and regression algorithm with sound theory that has been shown to answer a variet of Machine Learning Problems. Here we try to understand the algorithm better and develop new tests, classifiers, etc. based on Random Forest."
images:
- "/research/assets/multivar-feature.png"
draft: false
layout: single
mathjax: false
current: true
---

![RF Feature Importance](/research/assets/rf-feature.png)

## Summary

Random Forest is a popular classification and regression algorithm in the machine learning literature primarily because of it's performance and relatively low computational complexity. It basically works by taking the data, subsampling it, and constructing a decision tree out of it, where each split in the tree is based on the relative "purity" of the data. Purity in this sense is essentially a measure of how many observations share the same label. The subsampling and construting a decision tree is repeated for each tree of the forest. The trees are gernally built until a minimal impurity threshold is met with a leaf node.

Random forest has been shown to have very strong theoretical guarantees. Our work in this area has primarily focused around the nature of when the algorithm performs well and poorly as well as extensions of it. We compare the performance of Random Forests with Deep learning, another popular classification algorithm, and compare performance among various sample sizes with tabular, audio, and visual data types. In this paper, we find that random forest tends to perform optimally especially at low sample sizes.

As for extensions, we show that random forest in fact induces a kernel, which in this case is a pairwise similarity matrix, which basically is constructed by looking at the number of times two observations lie in the same leaf node across all the trees in the forest. This can be applied to hypothesis testing where we show that we can get a highlighly powerful test for high dimensional data using this kernel. We also develop new streaming trees and forests, which basically allows the algorithm to updated with new data without having to retrain the forest.

This work has been going on through my Ph.D. and still relatively new, though I hope to investigate further in my disertation.

---

### 📚 [Streaming Decision Trees and Forests](https://arxiv.org/abs/2110.08483)

Haoyin Xu, Jayanta Dey, **Sambit Panda**, Joshua T. Vogelstein

[Cite](../bibs/streaming.bib)

### 📚 [When are Deep Networks really better than Decision Forests at small sample sizes, and how?](https://arxiv.org/abs/2108.13637)

Haoyin Xu, Kaleab A. Kinfu, Will LeVine, **Sambit Panda**, Jayanta Dey, Michael Ainsworth, Yu-Chung Peng, Madi Kusmanov, Florian Engert, Christopher M. White, Joshua T. Vogelstein, Carey E. Priebe

[Cite](../bibs/dnvsrf.bib)

### 📚 [Learning Interpretable Characteristic Kernels via Decision Forests](https://arxiv.org/abs/1812.00029)

Cencheng Shen, **Sambit Panda**, Joshua T. Vogelstein

[Cite](../bibs/kmerf.bib)・[Code](https://hyppo.neurodata.io/api/generated/hyppo.independence.kmerf#hyppo.independence.KMERF)・[Figures](https://github.com/neurodata/hyppo-papers/tree/main/kmerf)
