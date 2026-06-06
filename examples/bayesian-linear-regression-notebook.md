---
layout: default
title: "Bayesian Linear Regression Notebook"
hero_subtitle: "Notebook-backed Example"
hero_description: "Run the full Bayesian linear regression workflow in Jupyter or Colab."
permalink: /examples/bayesian-linear-regression-notebook/
---

# Bayesian Linear Regression

This case study shows how sampling gives **parameter uncertainty** and **predictive uncertainty**, not just a single fitted line.

## Model

$$
y_i = \alpha + \beta x_i + \epsilon_i, \qquad \epsilon_i\sim\mathcal{N}(0,\sigma^2)
$$

Priors:

$$
\alpha\sim\mathcal{N}(0,10^2),\quad
\beta\sim\mathcal{N}(0,10^2),\quad
\sigma\sim\mathrm{HalfNormal}(1)
$$

Posterior target:

$$
p(\alpha,\beta,\sigma\mid x,y) \propto p(y\mid x,\alpha,\beta,\sigma)\,p(\alpha)p(\beta)p(\sigma)
$$

## Python example (PyMC)

```python
import numpy as np
import pymc as pm
import matplotlib.pyplot as plt

np.random.seed(42)
X = np.linspace(0, 10, 100)
true_slope = 2.5
true_intercept = 1.0
y = true_intercept + true_slope * X + np.random.normal(0, 2, size=100)

with pm.Model() as linear_model:
    intercept = pm.Normal("intercept", mu=0, sigma=10)
    slope = pm.Normal("slope", mu=0, sigma=10)
    sigma = pm.HalfNormal("sigma", sigma=1)

    mu = intercept + slope * X
    pm.Normal("obs", mu=mu, sigma=sigma, observed=y)

    trace = pm.sample(1500, tune=1000, chains=4, target_accept=0.9)

pm.plot_trace(trace, var_names=["intercept", "slope", "sigma"])
plt.show()
```

## What to report

- Posterior mean and 95% credible interval for `slope`
- Posterior mean and 95% credible interval for `intercept`
- Noise scale estimate from posterior of `sigma`
- Posterior predictive interval on a test grid


## Access options

- Open notebook file: [bayesian-linear-regression.ipynb]({{ site.baseurl }}/notebooks/bayesian-linear-regression.ipynb)
- Open in Colab: [Launch Colab](https://colab.research.google.com/github/Sampling-Algorithms/Sampling-Algorithms.github.io/blob/main/notebooks/bayesian-linear-regression.ipynb)
- Read companion page: [Bayesian Linear Regression](https://github.com/Sampling-Algorithms/Sampling-Algorithms.github.io/blob/main/_examples/Bayesian/linear-regression.md)

## What is inside the notebook

- Synthetic data generation for linear regression
- Bayesian model definition in PyMC
- Posterior sampling with NUTS
- Trace plots for parameter diagnostics

Back to [Examples]({{ site.baseurl }}/examples)
