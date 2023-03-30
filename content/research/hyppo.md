---
title: "Multivariate Hypothesis Testing"
date: 2018-08-25
subtitle: "Developing and implementing multivariate nonparametric hypothesis tests with high finite testing power in Python"
excerpt: "Hypothesis testing allows scientists to test their hypotheses. Many current standards perform poorly on high-dimensional and highly nonlinear data. Here, we develop tests that perform well in those situations, and package it nicely in a Python package."
images:
- "/research/assets/multivar-feature.png"
draft: false
layout: single
mathjax: true
current: true
---

![MGC Map](/research/assets/multivar-feature.png)

## Summary

Hypothesis testing is a fundamental problem in science and provides a framework for testing hypotheses. Two popular ones are independence and $k$-sample testing. Generally, independence testing asks whether the distributions of inputs $X$ and $Y$ are sampled independently or not from a joint distribution. In other words, if $F_X$ is the distribution of $X$, $F_Y$ is the distribution of $Y$, and $F_{XY}$ is the joint distribution of $X$ and $Y$, independence testing performs this test:
$$
\begin{split}
    H_0 : F_{XY} &= F_X F_Y \\\
    H_A : F_{XY} &\neq F_X F_Y
\end{split}
$$
$k$-sample testing is similar. Here, we are asking if we had $k$ inputs, are the distributions of all these inputs the same or is at least one different? Specifically, for $k$ inputs $U_1, \ldots, U_k$, with distributions $F_{u_1}, \ldots F_{u_k}$, $k$-sample testing asks:
$$
\begin{split}
    H_0 &: F_{U_1} = F_{U_2} = \ldots = F_{U_k} \\\
    H_A &: \exists\ i \neq j \text{ s.t. } F_{U_i} \neq F_{U_j}
\end{split}
$$
Many test have been designed to answer this question, however many do not work well for high-dimensional and highly nonlinear data. Our lab has designed multiscale graph correlation (MGC), which works well with this kind of data specifically, and I ported MGC into [SciPy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.multiscale_graphcorr.html). We built upon these tests, whether it be ore accurate ones such as one based on Random Forest or faster implementations of existing ones. We also implemented a framework for running $k$-sample tests that reduces the $k$-sample testing problem to the indpendence testing problem. This allows us to use powerful independence tests that work well with nonlinear and multivariate data and opens up a whole new avenue of new powerful $k$-sample tests.

All of these algorithms and more have been implemented in the [hyppo](https://github.com/neurodata/hyppo) package. The package contains many state-of-the art hypothesis tests and was based on an old package that I had written with a team of students earlier. I currently maintain the package and wrote much of it, including the [documentation](https://hyppo.neurodata.io/). This work was what I did during my M.S.E. and the beginning part of my Ph.D. at Johns Hopkins.

---

### 📚 [The Chi-Square Test of Distance Correlation](https://doi.org/10.1080/10618600.2021.1938585)

Cencheng Shen, **Sambit Panda**, Joshua T. Vogelstein

[Cite](../bibs/fastdcorr.bib)・[arXiv](https://arxiv.org/abs/1912.12150)・[Code](https://hyppo.neurodata.io/api/generated/hyppo.independence.dcorr#hyppo.independence.Dcorr.test)・[Figures](https://github.com/neurodata/hyppo-papers/tree/main/fast)

### 📚 [Nonpar MANOVA via Independence Testing](https://arxiv.org/abs/1910.08883)

**Sambit Panda**, Cencheng Shen, Ronan Perry, Jelle Zorn, Antoine Lutz, Carey E. Priebe, Joshua T. Vogelstein

[Cite](../bibs/ksample.bib)・[Code](https://hyppo.neurodata.io/api/generated/hyppo.ksample.ksample#hyppo.ksample.KSample)・[Figures](https://github.com/neurodata/hyppo-papers/tree/main/ksample)・[Talk](../work/2021-hyppo-gyss.pdf)・[Poster](../work/2021-hyppo-brain.pdf)

### 📚 [hyppo: A Multivariate Hypothesis Testing Python Package](https://arxiv.org/abs/1907.02088)

**Sambit Panda**, Satish Palaniappan, Junhao Xiong, Eric W. Bridgeford, Ronak Mehta, Cencheng Shen, Joshua T. Vogelstein

[Cite](../bibs/hyppo.bib)・[Code](https://github.com/neurodata/hyppo)・[Docs](https://hyppo.neurodata.io/)・[Figures](https://github.com/neurodata/hyppo-papers/tree/main/hyppo)・[Talk](https://neurodata.io/talks/scipy21.html)

### 📚 [Learning Interpretable Characteristic Kernels via Decision Forests](https://arxiv.org/abs/1812.00029)

Cencheng Shen, **Sambit Panda**, Joshua T. Vogelstein

[Cite](../bibs/kmerf.bib)・[Code](https://hyppo.neurodata.io/api/generated/hyppo.independence.kmerf#hyppo.independence.KMERF)・[Figures](https://github.com/neurodata/hyppo-papers/tree/main/kmerf)
