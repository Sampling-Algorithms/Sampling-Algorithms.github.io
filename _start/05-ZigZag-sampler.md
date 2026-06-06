---
title: "Zig-Zag Sampler"
description: "Understand the Zig-Zag piecewise deterministic Markov process (PDMP) sampler for high-dimensional Bayesian inference."
order: 5
icon: "⚡"
---

# Zig-Zag Sampler (PDMP)

The Zig-Zag sampler is a **non-reversible** continuous-time MCMC method. It belongs to the family of piecewise deterministic Markov processes (PDMPs).

Unlike random-walk proposals, Zig-Zag moves in straight lines and changes direction (velocity sign) at random event times.

## State representation

The state is $(x,v)$ where:
- $x\in\mathbb{R}^d$ is position
- $v\in\{-1,+1\}^d$ is velocity

Between events:

$$
x(t)=x_0 + t v, \qquad v(t)=v_0
$$

At event times, one coordinate of $v$ flips sign.

## Event rates

For target density $\pi(x)\propto e^{-U(x)}$, define coordinate-wise rates:

$$
\lambda_i(x,v)=\big[v_i\,\partial_i U(x)\big]_+ + \gamma_i(x,v)
$$

where $[a]_+=\max(a,0)$ and $\gamma_i$ is an optional refreshment term.

When event $i$ occurs:

$$
v_i \leftarrow -v_i
$$

All other velocity components remain unchanged.

## Why Zig-Zag is useful

- Better exploration than reversible random-walk samplers in many problems
- Can exploit gradient information
- Supports subsampling variants for large datasets

## High-level algorithm

1. Initialize $(x,v)$
2. Simulate next event time from dominating Poisson bounds
3. Move linearly to event time
4. Accept event with thinning probability
5. Flip one velocity component and repeat

## Practical interpretation

Think of a particle moving with constant speed in each coordinate. The local geometry of $U(x)$ decides how often each coordinate reverses direction.

Coordinates moving "uphill" in the potential tend to flip more often; coordinates moving "downhill" continue longer.

## Comparison with HMC and MH

- **vs Random-Walk MH**: less diffusive, often better scaling
- **vs HMC**: event-driven (no leapfrog trajectory length tuning)
- **vs Langevin methods**: deterministic flow between stochastic events

## When to use Zig-Zag

Good candidates:
- medium/high-dimensional smooth posteriors
- large data settings with factorized likelihoods
- problems where non-reversibility improves mixing

Be careful with:
- very rough/non-smooth targets
- poor event-rate bounds (can reduce efficiency)

## Summary

Zig-Zag is an advanced yet powerful sampler: deterministic motion + random event flips. It is especially attractive when you want scalable, non-reversible dynamics-based MCMC.

To go deeper, next steps are:
1. derive invariant measure proof sketch,
2. implement 1D Zig-Zag,
3. extend to Bayesian logistic regression with subsampling.