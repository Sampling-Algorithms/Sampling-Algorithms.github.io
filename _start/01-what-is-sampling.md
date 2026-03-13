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
where the normalization constant $\mathcal{Z}$ is defined by 
\begin{equation}
   \mathcal{Z} = \int_{\mathcal{M}} e^{-U(y)} dy,
\end{equation}
and the potential function $U$ is defined from $\mathcal{M}$ to $\mathbb{R}_+$

## The difficulties 
At first, computing the integral $\pi(f)$ look easier but several diffifculties may arise 
- The normalisation constant $\mathcal{Z}$ is unknown
- The variable $x$ is high-dimensional  
- Evaluating $\pi$ in the Bayesian setting is hard especially when it depends on a large number of data. 

## What you will learn in this library 
This library is intended to present a range of algorithms design to tackle/find an approximation of $\pi(f)$. Exact and approximate samples will be presented both for unconstrained (when $\mathcal{M} = \mathbb{R}^d$) and constrained (when $\mathcal{M} \subset \mathbb{R}^d$) sampling problems. For each method, simple examples are provided for a clear understanding of the method accompanied with project to strengthened the knowledge. The methods we present are accompanied with appropriate references. 

## A sample of methods discussed 
Some of the methods we will discussed include 
- Approximate samplers (ULA, SGLD, Unadjusted HMC (UHMC), Proximal Unadjusted Langevin (P-ULA), MYULA, FBULA, Tamed ULA (T-ULA), BAOB/ABOBA/OBABO splitting approaches, Generalised Langevin (GLE) integrators, Projected/Mirror descent Langevin, Stein Variational Gradient descent, Interacting ULA methods, Affine Invariant Interacting Langevin methods, Birth-Death Accelerated Langevin).  
-  Exact samplers (Random Walk Metropolis Hasting (RWM), MALA, HMC, ZZS, BPS, Boomerang sampler, coordinate sampler, Gibbs sampler, Metropolis Within-Gibbs, Preconditioned/Manifold MALA, RJMCMC, Pseudo Marginal MH, Exchange algorithms, Slice sampling, Population MCMC, Affine Invariant sampler, (Importance sampling)).

We equally discuss subsampling techniques to tackle the big data setting in Bayesian computation for example. 





[Continue Reading...](#)