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
where $f: \mathcal{M} \rightarrow \mathbb{R}$ is a real-valued integrable function with respect to the probability distribution $\pi$ which is assumed to admit a density (still denoted by $\pi$ for convenience) with respect to the Lebesgue measure. The support $\mathcal{M}$ of the distribution can either be the entire space $\mathbb{R}^d$ or a proper subset of $\mathbb{R}^d$ where $d$ denotes the dimensionality of the problem.  

The density $\pi$ of the distribution usually takes the form 
\begin{equation}
  \pi(x) = \frac{1}{\mathcal{Z}} e^{-U(x)}, \quad x \in \mathcal{M}
\end{equation}
and the potential function $U$ is defined from $\mathcal{M}$ to $\mathbb{R}_+$

## The difficulties 
At first, computing the integral $\pi(f)$ look easier but several diffifculties may arise 
- The normalisation constant $\mathcal{Z}$ is unknown
- The variable $x$ is high-dimensional  
- Evaluating $\pi$ in the Bayesian setting is hard especially when it depends on a large number of data. 

## What you will learn in this library 





[Continue Reading...](#)