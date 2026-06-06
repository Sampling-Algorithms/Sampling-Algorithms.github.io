---
title: "Importance Sampling for Tail Probability Estimation"
description: "Estimate rare-event probabilities efficiently using weighted samples from a proposal distribution."
difficulty: "Intermediate"
icon: "📊"
category: "statistics"
tags: ["Importance Sampling", "Rare Events", "Monte Carlo"]
order: 1
---

# Importance Sampling for Tail Probability Estimation

Naive Monte Carlo is inefficient for rare events. Importance sampling focuses computation where rare events occur.

## Goal

Estimate the tail probability:

$$
\mathbb{P}(X > a), \quad X\sim\mathcal{N}(0,1), \ a=4
$$

Direct Monte Carlo needs many samples because this event is rare.

## Importance sampling estimator

Choose proposal $q(x)=\mathcal{N}(\mu_q,1)$ with $\mu_q>0$.

$$
\hat{p} = \frac{1}{N}\sum_{i=1}^N \mathbf{1}_{\{x_i>a\}}\,w(x_i),
\quad x_i\sim q,
\quad w(x)=\frac{\pi(x)}{q(x)}
$$

where $\pi$ is the standard normal density.

## Python sketch

```python
import numpy as np
from scipy.stats import norm

N = 10000
a = 4.0
mu_q = 4.0

# Proposal samples
x = np.random.normal(loc=mu_q, scale=1.0, size=N)

# Importance weights
w = norm.pdf(x, loc=0, scale=1) / norm.pdf(x, loc=mu_q, scale=1)

# Rare-event estimate
estimate = np.mean((x > a) * w)
print("Estimated P(X > 4):", estimate)
print("True value:", 1 - norm.cdf(a))
```

## Diagnostics to monitor

- Weight variance (high variance means unstable estimate)
- Effective sample size (ESS)
- Comparison with known analytical benchmark when available

## Key takeaway

A good proposal dramatically reduces variance and makes rare-event estimation practical.

Back to [Examples]({{ site.baseurl }}/examples)
