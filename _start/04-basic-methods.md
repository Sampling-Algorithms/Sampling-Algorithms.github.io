---
title: "Basic Methods"
description: "Learn the three foundational sampling methods: inverse transform, rejection sampling, and importance sampling."
order: 4
icon: "🎲"
---

# Basic Sampling Methods

Now that you have built a first sampler, we can organize the three core methods you will use repeatedly in practice.

## 1) Inverse Transform Sampling

If $F$ is the CDF of the target distribution and $F^{-1}$ is available, then:

$$
X = F^{-1}(U), \quad U\sim\mathrm{Uniform}(0,1)
$$

### Strengths
- Exact sampling (up to RNG precision)
- Fast and simple in 1D when inverse CDF is known

### Limitations
- Hard in high dimensions
- Often impossible when $F^{-1}$ has no closed form

## 2) Rejection Sampling

Suppose target density is $\pi(x)$ and proposal density is $q(x)$ such that:

$$
\pi(x) \le M q(x) \quad \text{for all } x
$$

Algorithm:
1. Sample $X\sim q$ and $U\sim \mathrm{Uniform}(0,1)$
2. Accept $X$ if
	$$
	U \le \frac{\pi(X)}{M q(X)}
	$$
3. Else reject and repeat

### Strengths
- Conceptually simple
- Works when only unnormalized target is available

### Limitations
- Efficiency depends strongly on $M$
- Poor choice of $q$ can lead to many rejections

## 3) Importance Sampling

To estimate:

$$
\pi(f)=\int f(x)\pi(x)dx
$$

using proposal $q$, rewrite:

$$
\pi(f)=\int f(x)\frac{\pi(x)}{q(x)}q(x)dx
= \mathbb{E}_q\left[f(X)w(X)\right]
$$

where

$$
w(x)=\frac{\pi(x)}{q(x)}
$$

Self-normalized estimator:

$$
\hat{\pi}_N(f)=\frac{\sum_{i=1}^N w_i f(x_i)}{\sum_{i=1}^N w_i}
$$

### Strengths
- No rejection step
- Useful for expectation estimation and rare events

### Limitations
- Weight degeneracy if $q$ misses high-density regions of $\pi$
- Can have very high variance

## Choosing the right basic method

- Use **Inverse Transform** when inverse CDF is available and low-dimensional.
- Use **Rejection Sampling** when you can build a good envelope $Mq(x)$.
- Use **Importance Sampling** when your main goal is estimating expectations.

## Practical checklist

Before implementation, verify:
1. Can you evaluate $\pi(x)$ up to a constant?
2. Is your proposal easy to sample from?
3. Does proposal coverage match target support?
4. What diagnostic will you monitor (acceptance rate, ESS, variance)?

## Summary

These methods are the foundation for advanced techniques (Metropolis-Hastings, SMC, HMC, Zig-Zag). Mastering them first makes advanced samplers much easier to understand.

Next: [Zig-Zag Sampler]({{ site.baseurl }}/start/05-ZigZag-sampler/)