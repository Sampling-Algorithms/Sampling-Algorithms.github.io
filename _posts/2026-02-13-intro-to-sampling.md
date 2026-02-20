---
layout: post
title: "🎯 Introduction to Sampling: Why Randomness Matters"
date: 2026-02-13
categories: [get-started, basics]
math: true
---

# Why Do We Need Sampling?

Imagine you're a baker trying to perfect your chocolate chip cookie recipe. You bake a batch and want to know: "Are the chips evenly distributed?" You could:

1. **Eat the whole batch** (computationally expensive! 🍪)
2. **Take a few cookies as samples** (much more efficient!)

This is sampling in a nutshell: **understanding the whole by examining a representative part**.

## 🎲 What is Sampling?

In computational terms, sampling means generating random values from a probability distribution. Instead of computing with the entire distribution (which might be impossible), we work with a set of samples.

```python
import numpy as np
import matplotlib.pyplot as plt

# Generate 1000 samples from a normal distribution
samples = np.random.normal(loc=0, scale=1, size=1000)

plt.hist(samples, bins=30, density=True, alpha=0.7)
plt.title('1000 Samples from N(0,1)')
plt.show()