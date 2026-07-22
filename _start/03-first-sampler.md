---
title: "Your First Sampler"
description: "Build your first practical sampler from scratch using inverse transform and Box-Muller methods."
order: 3
# icon: "🛠️"
---

# Your First Sampler

This lesson builds your first sampler from scratch using only uniform random numbers.

## Learning goals

By the end of this page, you will be able to:
- transform uniform random numbers into samples from another distribution,
- generate Gaussian samples with the Box-Muller transform,
- validate your sampler using simple diagnostics.

## Step 1: Start from a uniform source

Most programming environments provide a pseudo-random generator for:

$$
U \sim \mathrm{Uniform}(0,1)
$$

This is the basic building block for many samplers.

## Step 2: Inverse transform sampling

If a target distribution has CDF $F$, and we can compute $F^{-1}$, then:

$$
X = F^{-1}(U), \quad U\sim\mathrm{Uniform}(0,1)
$$

has the target distribution.

### Example: Exponential distribution

For $X\sim \mathrm{Exp}(\lambda)$,

$$
F(x)=1-e^{-\lambda x}, \quad x\ge0
$$

So,

$$
F^{-1}(u)= -\frac{1}{\lambda}\log(1-u)
$$

Thus a sampler is:

$$
X = -\frac{1}{\lambda}\log(1-U)
$$

## Step 3: Box-Muller for Gaussian sampling

To sample from $\mathcal{N}(0,1)$, draw $U_1,U_2\sim \mathrm{Uniform}(0,1)$ and compute:

$$
Z_1=\sqrt{-2\log U_1}\cos(2\pi U_2),
\qquad
Z_2=\sqrt{-2\log U_1}\sin(2\pi U_2)
$$

Then $Z_1$ and $Z_2$ are independent standard normal variables.

## Python implementation

```python
import numpy as np
import matplotlib.pyplot as plt

def sample_exponential(n, lam=1.0):
	u = np.random.rand(n)
	return -(1 / lam) * np.log(1 - u)

def sample_normal_box_muller(n):
	m = (n + 1) // 2
	u1 = np.random.rand(m)
	u2 = np.random.rand(m)

	r = np.sqrt(-2.0 * np.log(u1))
	theta = 2.0 * np.pi * u2

	z1 = r * np.cos(theta)
	z2 = r * np.sin(theta)
	z = np.concatenate([z1, z2])
	return z[:n]

# Generate samples
exp_samples = sample_exponential(5000, lam=2.0)
normal_samples = sample_normal_box_muller(5000)

# Quick diagnostics
print("Exp mean (theory 0.5):", exp_samples.mean())
print("Normal mean (theory 0):", normal_samples.mean())
print("Normal var  (theory 1):", normal_samples.var())

fig, axes = plt.subplots(1, 2, figsize=(12, 4))
axes[0].hist(exp_samples, bins=50, density=True, alpha=0.7)
axes[0].set_title("Exponential samples")
axes[1].hist(normal_samples, bins=50, density=True, alpha=0.7)
axes[1].set_title("Normal samples (Box-Muller)")
plt.tight_layout()
plt.show()
```

## How to check if your sampler is correct

Use these checks:
1. **Histogram shape** matches the target distribution.
2. **Sample moments** are close to theory (mean/variance).
3. **Stability with larger $N$**: estimates improve as sample size increases.

## Common beginner mistakes

- Using `log(U)` with `U=0` (numerical issue).
- Forgetting that finite samples have noise.
- Assuming one nice-looking histogram proves correctness.

## Summary

You now built your first practical samplers from first principles. This is the foundation for more advanced methods (rejection sampling, MCMC, HMC, Zig-Zag).

Next: [Basic Methods]({{ site.baseurl }}/start/04-basic-methods/)