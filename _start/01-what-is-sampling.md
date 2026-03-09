---
title: "What is Sampling?"
description: "Understanding the basics of sampling"
order: 1
icon: "🎯"
---

# The sampling problem 

Sampling algorithms play an important role in various fields, including machine learning, image processing, statistical mechanics, inverse problems, Data assimilation and Bayesian inference among others. Their main goal is to approximate high-dimensional integrals of the form  
\begin{equation}\label{problem}
   \pi(f) := \int_{\mathcal{M}} f(x) \pi(x){d}x,
\end{equation}
where $f: \mathcal{M} \rightarrow \mathbb{R}$ is a real-valued integrable function with respect to the probability distribution $\pi$ which is assumed to admit a density (still denoted by $$\pi$$ for convenience) with respect to the Lebesgue measure. The support $\mathcal{M}$ of the distribution can either be the entire space $\mathbb{R}^d$ or a proper subset of $\mathbb{R}^d$ where $d$ denotes the dimensionality of the problem. 

## Key Concepts
- Population vs Sample
- Random Sampling
- Bias and Variance
- Law of Large Numbers

[Continue Reading...](#)