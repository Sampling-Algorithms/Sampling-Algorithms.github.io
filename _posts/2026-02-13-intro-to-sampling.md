---
layout: post
title: "Introduction to Sampling: Why Randomness Matters"
date: 2026-02-13
categories: [get-started, basics]
math: true
---

# Why do we need sampling?

Many modern problems require expectations of the form

$$
\pi(f)=\int f(x)\pi(x)dx
$$

where $\pi$ can be high-dimensional or only known up to a constant. Direct integration is often impossible, so we estimate expectations using samples.

## Intuition

Instead of evaluating every possible state, we draw representative random states and average:

$$
\hat{\pi}_N(f)=\frac1N\sum_{i=1}^N f(x_i)
$$

As $N$ grows, this approximation becomes more accurate under standard conditions.

## A tiny example

```python
import numpy as np

# Estimate E[X^2] for X ~ N(0,1)
N = 10000
x = np.random.normal(0, 1, size=N)
estimate = np.mean(x**2)
print("Estimated E[X^2]:", estimate)  # should be close to 1
```

## Where sampling appears

- Bayesian inference (posterior uncertainty)
- Machine learning (stochastic optimization and probabilistic models)
- Statistical physics (state-space exploration)
- Signal and image processing (inverse problems)
- Robotics and control (state estimation under noise)

## Common families of samplers

1. **Direct methods**: inverse transform, rejection sampling
2. **MCMC methods**: Metropolis-Hastings, Gibbs, HMC
3. **Sequential methods**: particle filtering / SMC
4. **PDMP methods**: Zig-Zag, Bouncy Particle Sampler

## What makes sampling difficult

- Unknown normalizing constants
- High dimensional geometry
- Correlated samples (in MCMC)
- Poor tuning can slow convergence

## Practical checklist

Before trusting estimates, always check:

- trace plots and stationarity
- autocorrelation and effective sample size
- acceptance rate (for MCMC)
- sensitivity to initialization

## Next steps

If you are starting out, follow this order:

1. What is sampling?
2. Probability refresher
3. Your first sampler
4. Basic methods
5. Zig-Zag sampler

Continue from [Get Started]({{ site.baseurl }}/start).
