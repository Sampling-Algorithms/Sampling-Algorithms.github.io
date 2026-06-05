---
title: "Bayesian Linear Regression"
description: "Use MCMC to sample from posterior distributions of regression parameters. Includes uncertainty quantification and prediction intervals."
difficulty: "Intermediate"
icon: "📈"
category: "bayesian"
tags: ["Metropolis-Hastings", "PyMC3", "Regression"]
order: 1
github: "https://github.com/charles-kmc/library-of-sampling-methods/tree/main/examples/bayesian-regression"
colab: "https://colab.research.google.com/github/charles-kmc/library-of-sampling-methods/blob/main/examples/bayesian-regression.ipynb"
---

# Bayesian Linear Regression

This example demonstrates how to use MCMC for Bayesian linear regression, allowing you to quantify uncertainty in your predictions.

## What You'll Learn
- Setting up a Bayesian linear regression model
- Using Metropolis-Hastings to sample from the posterior
- Visualizing posterior distributions
- Making predictions with uncertainty intervals

## Code Example
```python
import numpy as np
import pymc3 as pm
import matplotlib.pyplot as plt

# Generate synthetic data
np.random.seed(42)
X = np.linspace(0, 10, 100)
true_slope = 2.5
true_intercept = 1.0
y = true_intercept + true_slope * X + np.random.normal(0, 2, size=100)

# Build Bayesian model
with pm.Model() as linear_model:
    # Priors
    intercept = pm.Normal('intercept', mu=0, sigma=10)
    slope = pm.Normal('slope', mu=0, sigma=10)
    sigma = pm.HalfNormal('sigma', sigma=1)
    
    # Likelihood
    mu = intercept + slope * X
    likelihood = pm.Normal('y', mu=mu, sigma=sigma, observed=y)
    
    # Sample from posterior
    trace = pm.sample(2000, return_inferencedata=False)

# Plot results
pm.plot_trace(trace)
plt.show()