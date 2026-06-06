---

layout: post
title: "Introduction to Sampling: Why Randomness Matters"
date: 2026-02-13
categories: [get-started, basics]
math: true
----------

# Introduction to Sampling: Why Randomness Matters

Sampling is one of the most powerful ideas in modern science. It lies at the heart of statistics, machine learning, artificial intelligence, physics, engineering, finance, and many other disciplines. Although the applications are diverse, the underlying principle is surprisingly simple: when a problem becomes too large or too complex to solve exactly, we can often learn about it by generating representative random samples and studying their behavior.

At first glance, randomness may seem like an odd tool for scientific computation. After all, scientists and engineers usually seek precision, determinism, and exact answers. Yet randomness has become one of the most effective computational tools ever developed. In many situations, carefully designed random experiments provide answers that would be impossible to obtain through deterministic calculations alone.

To understand why sampling is needed, consider a common problem in probability and statistics. Suppose we are interested in a quantity $x$ that follows a probability distribution $\pi(x)$. We would like to compute the average value of some function $f(x)$ under this distribution. This quantity is known as an expectation and is written as

\begin{equation}\label{eq:expectation}
 \mathbb E_{\pi}[f(X)] = \int f(x)\pi(x)dx.
\end{equation}

This expression appears everywhere in science. Depending on the context, it may represent the average temperature of a system, the expected return of a financial portfolio, the uncertainty of a machine learning model, or the average intensity of a pixel in an image. In principle, solving the problem simply requires evaluating the integral above. Unfortunately, the integral in \eqref{eq:expectation} is often intractable in high dimensional settings. In many practical applications, the probability distribution $\pi(x)$ is extremely complicated with no closed-form expression.  

A natural idea would be to approximate the integral numerically. In low dimensions, this works quite well. We can discretize the domain into a grid of points, evaluate the function at each location, and combine the results. However, this approach rapidly becomes impractical as the number of dimensions increases. Suppose that we discretize each variable using only one hundred points. In one dimension, this requires one hundred evaluations. In two dimensions, it requires ten thousand evaluations. In ten dimensions, it requires one hundred billion evaluations. By the time we reach one hundred dimensions, the number of required evaluations exceeds the number of atoms in the observable universe. This phenomenon is known as the **curse of dimensionality**, and it renders traditional numerical integration ineffective for many modern problems.

Sampling provides a fundamentally different perspective. Instead of trying to evaluate the function everywhere, we select a relatively small number of representative points drawn from the probability distribution itself. If we generate samples

$$
x_1,x_2,\ldots,x_N \sim \pi(x),
$$

then we can approximate the expectation using the empirical average

$$
\hat{\pi}_N(f)=\frac{1}{N}\sum_{i=1}^{N}f(x_i).
$$

This approximation is known as a **Monte Carlo estimator**. The remarkable fact is that, under very general conditions,

$$
\hat{\pi}_N(f)\rightarrow\pi(f)
$$

as

$$
N \rightarrow \infty.
$$

In other words, averages of random samples eventually converge to the true expectation. This result is a consequence of the Law of Large Numbers and forms the foundation of modern sampling theory.

The power of this idea is difficult to overstate. Rather than fighting the complexity of high-dimensional spaces, sampling embraces it. The computational cost depends primarily on the number of samples generated rather than directly on the dimensionality of the space. This property explains why Monte Carlo methods remain effective in settings where conventional numerical methods completely fail.

To make this idea more concrete, consider a standard Gaussian random variable

$$
X \sim \mathcal N(0,1).
$$

Suppose we wish to compute

$$
\mathbb E[X^2].
$$

From elementary probability theory, we know that the answer is exactly one. However, imagine that we do not know the analytical solution. We can generate many random samples from the Gaussian distribution, square each sample, and compute the average. Even with a relatively modest number of samples, the resulting estimate is usually very close to the true value.

```python
import numpy as np

# Estimate E[X²] for X ~ N(0,1)

N = 10000

x = np.random.normal(0, 1, size=N)

estimate = np.mean(x**2)

print("Estimated E[X²]:", estimate)
```

A typical output might be

```text
Estimated E[X²]: 1.003
```

which is already extremely close to the exact answer. As the number of samples increases, the estimate becomes increasingly accurate.

The ability to transform difficult integrals into averages over random samples has made sampling indispensable across scientific disciplines. In Bayesian statistics, sampling is used to characterize posterior distributions and quantify uncertainty. In machine learning, stochastic algorithms rely on random samples to train models efficiently on massive datasets. In robotics, particle-based methods help autonomous systems estimate their position in uncertain environments. In computational imaging, sampling methods allow researchers to reconstruct images while simultaneously assessing uncertainty. Even modern diffusion models, which currently power many state-of-the-art image generation systems, can be interpreted as sophisticated sampling procedures designed to generate samples from highly complex probability distributions.

Of course, generating samples is not always easy. The probability distribution of interest may only be known up to an unknown normalizing constant. The geometry of the distribution may be highly irregular. High-dimensional spaces often contain regions that are difficult to explore efficiently. Furthermore, many practical algorithms generate correlated samples rather than independent ones, introducing additional challenges for statistical estimation. As a result, the central question of sampling theory is not merely how to compute averages, but how to generate representative samples efficiently and reliably.

Over the past century, researchers have developed a remarkable collection of algorithms to address this challenge. Some methods generate samples directly from a distribution. Others construct Markov chains whose long-term behavior reproduces the target distribution. More recent approaches combine deterministic dynamics with random events to improve exploration of high-dimensional spaces. Although these algorithms may appear very different on the surface, they all pursue the same objective: generating samples that faithfully represent a probability distribution.

This library is devoted to understanding these methods from first principles. We will begin with the foundations of probability theory and gradually build toward modern sampling algorithms such as Rejection Sampling, Importance Sampling, Metropolis–Hastings, Gibbs Sampling, Hamiltonian Monte Carlo, Langevin Dynamics, Sequential Monte Carlo, Piecewise Deterministic Markov Processes, and diffusion-based samplers. Along the way, we will develop both the mathematical intuition and practical skills needed to apply these methods to real-world problems.

The key message of this chapter is simple but profound. Many of the most important quantities in science and machine learning can be expressed as expectations with respect to probability distributions. Direct computation is often impossible, especially in high-dimensional settings. Sampling provides a powerful alternative by replacing difficult integrals with averages over representative random samples. What initially appears to be randomness is, in reality, a carefully designed computational strategy that allows us to solve problems far beyond the reach of classical deterministic methods.

## What You'll Learn Next

Now that we understand *why* sampling is needed, the next step is to understand the language of probability. In the next chapter, we will review the essential concepts that underpin all sampling algorithms, including random variables, probability distributions, probability density functions, cumulative distribution functions, expectations, variances, and conditional probabilities.

**Next:** Probability Refresher →
