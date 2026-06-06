---
title: "Simulated Annealing for Non-Convex Optimization"
description: "Use sampling-based optimization to locate global minima in rugged objective landscapes."
difficulty: "Intermediate"
icon: "⛰️"
category: "optimisation"
tags: ["Simulated Annealing", "Optimization", "Metropolis"]
order: 1
---

# Simulated Annealing for Non-Convex Optimization

Simulated annealing uses sampling moves plus a temperature schedule to escape local minima and search for a near-global optimum.

## Objective

Given objective function $f(x)$, we want:

$$
x^* = \arg\min_x f(x)
$$

At temperature $T$, worse proposals can still be accepted with probability:

$$
\alpha = \min\left(1, \exp\left(-\frac{f(x')-f(x)}{T}\right)\right)
$$

## Algorithm outline

1. Start from initial point $x_0$
2. Propose $x' = x + \eta$ with random perturbation
3. Accept/reject with Metropolis rule
4. Decrease temperature: $T_{k+1} = \gamma T_k$, with $\gamma\in(0,1)$
5. Keep best point found

## Python sketch

```python
import numpy as np

# Multi-modal 1D objective
f = lambda x: 0.2 * x**4 - 2 * np.cos(3*x) + 0.1 * x

def anneal(x0=2.5, T0=1.5, gamma=0.995, steps=5000, proposal_std=0.3):
    x = x0
    best_x = x
    best_f = f(x)
    T = T0

    for _ in range(steps):
        x_prop = x + np.random.normal(0, proposal_std)
        delta = f(x_prop) - f(x)

        if delta < 0 or np.random.rand() < np.exp(-delta / max(T, 1e-8)):
            x = x_prop

        if f(x) < best_f:
            best_x, best_f = x, f(x)

        T *= gamma

    return best_x, best_f

x_star, f_star = anneal()
print("Best x:", x_star)
print("Best f:", f_star)
```

## Practical notes

- Large initial temperature improves exploration.
- Slow cooling generally yields better solutions.
- Proposal scale should match the local landscape.

Back to [Examples]({{ site.baseurl }}/examples)
