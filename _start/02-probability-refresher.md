---
title: "Probability Refresher"
description: "Review PDFs, CDFs, random variables, expectation, variance, and the probabilistic foundations of sampling methods."
order: 2
icon: "📊"
---


# Probability Refresher

Before studying sampling algorithms such as Monte Carlo methods, Markov Chain Monte Carlo (MCMC), Langevin dynamics, Hamiltonian Monte Carlo, Sequential Monte Carlo, or Diffusion Models, it is important to understand the language of probability.

Probability provides a mathematical framework for reasoning about uncertainty. In real-world problems, we rarely know everything exactly. Measurements are corrupted by noise, future events are uncertain, and many systems contain hidden variables that cannot be directly observed.

Probability allows us to quantify uncertainty and make principled decisions based on incomplete information.

For example:

- What is the probability that it will rain tomorrow?
- What is the true image behind a blurry observation?
- What is the probability that a patient has a disease given a medical test result?
- What is the most likely position of a robot given noisy sensor measurements?

All these questions can be formulated using probability distributions.

In modern machine learning and statistics, probability is everywhere. Bayesian inference, generative models, diffusion models, reinforcement learning, uncertainty quantification, and stochastic optimization all rely heavily on probabilistic concepts.

This chapter reviews the essential probability concepts that form the foundation of the sampling methods studied throughout this library.

## Mathematical core (equation-first view)

For sampling, these are the central identities to remember:

### Probability space

$$
(\Omega, \mathcal{F}, \mathbb{P})
$$

- $\Omega$: sample space
- $\mathcal{F}$: events (a $\sigma$-algebra)
- $\mathbb{P}$: probability measure

### Law of total probability

If $\{B_i\}_{i=1}^n$ is a partition of $\Omega$ with $\mathbb{P}(B_i)>0$:

$$
\mathbb{P}(A) = \sum_{i=1}^{n} \mathbb{P}(A\mid B_i)\,\mathbb{P}(B_i)
$$

### Bayes' theorem

$$
\mathbb{P}(A\mid B) = \frac{\mathbb{P}(B\mid A)\,\mathbb{P}(A)}{\mathbb{P}(B)}
$$

Density form (continuous case):

$$
p(x\mid y)=\frac{p(y\mid x)p(x)}{p(y)}
$$

In Bayesian inference:

$$
p(\theta\mid y) \propto p(y\mid \theta)\,p(\theta)
$$

### Expectation and variance

$$
\mathbb{E}[X] = \int_{\mathbb{R}} x\,p_X(x)\,dx
\quad \text{or} \quad
\mathbb{E}[X]=\sum_x x\,p_X(x)
$$

$$
\mathrm{Var}(X)=\mathbb{E}\big[(X-\mathbb{E}[X])^2\big]=\mathbb{E}[X^2]-\mathbb{E}[X]^2
$$

### Covariance and correlation

$$
\mathrm{Cov}(X,Y)=\mathbb{E}\big[(X-\mathbb{E}[X])(Y-\mathbb{E}[Y])\big]
$$

$$
\rho_{XY}=\frac{\mathrm{Cov}(X,Y)}{\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(Y)}}
$$

### Conditional expectation

$$
\mathbb{E}[X\mid Y=y]=\int x\,p(x\mid y)\,dx
$$

### Monte Carlo estimator (foundation of sampling)

For a target density $\pi$ and test function $f$:

$$
\pi(f)=\int f(x)\pi(x)dx,
\qquad
\hat{\pi}_N(f)=\frac{1}{N}\sum_{i=1}^N f(X_i)
$$

If $X_i\sim\pi$ (or approximately after convergence in MCMC), then $\hat{\pi}_N(f)$ approximates $\pi(f)$.

## Why Probability?

Suppose we toss a fair coin.

Before observing the result, there is uncertainty.

The coin can land on:
- Heads
- Tails

We therefore assign probabilities:

$$
P(\text{Heads}) = 0.5
$$

$$
P(\text{Tails}) = 0.5
$$

These probabilities quantify our uncertainty before the outcome is observed.

After observing the coin, the uncertainty disappears and the outcome becomes known.

Probability theory provides mathematical tools for quantifying uncertainty before observations are made.

## Random Variables

A random variable is a mathematical object used to represent the outcome of a random experiment numerically. It does not represent uncertainty itself. Instead, it maps uncertain outcomes to numerical values that can be analyzed mathematically.

Random variables are typically denoted by capital letters:

$$
X, Y, Z
$$

while specific observed values are denoted by lowercase letters:

$$
x, y, z
$$

For example,

$$
X = \text{outcome of a die roll}
$$

while

$$
x = 4
$$

represents a particular observation.

### Types of Random Variables

There are two major classes of random variables.

### Discrete Random Variables

A discrete random variable takes values from a finite or countable set.

Example:

$$
X \in \{1,2,3,4,5,6\}
$$

for a die roll.

### Continuous Random Variables

A continuous random variable can take infinitely many values in an interval.

Example:

$$
X \in \mathbb R
$$

for temperature measurements or Gaussian noise.



## Probability Mass Functions (PMF)

For discrete random variables, probabilities are described using a **Probability Mass Function (PMF)**.

The PMF is defined as

$$
p(x) = P(X=x)
$$

and directly gives the probability that the random variable takes a particular value.

For a fair die:

$$
p(x)=\frac16,
\qquad x \in \{1,2,3,4,5,6\}
$$

A valid PMF must satisfy:

### Non-negativity

$$
p(x)\ge 0
$$

Probabilities can never be negative.

### Normalization

$$
\sum_x p(x)=1
$$

The probabilities of all possible outcomes must sum to one.


## Probability Density Functions (PDF)

For continuous random variables, probabilities are described using a **Probability Density Function (PDF)**.

The density is denoted

$$
p(x)
$$

and describes how probability mass is distributed across possible values.

A common misconception is that

$$
p(x)
$$

itself is a probability.

This is not true.

For continuous random variables,

$$
P(X=x)=0
$$

for every individual value.

Instead, probabilities are computed using areas under the density curve.

Specifically,

$$
P(a \le X \le b)=\int_a^b p(x)\,dx
$$

This equation states that the probability of finding the random variable between \(a\) and \(b\) equals the area under the density function between those two points.

Therefore:

- larger areas correspond to more likely events,
- smaller areas correspond to less likely events.

### Properties of PDFs

A valid probability density must satisfy:

#### Non-negativity

$$
p(x)\ge0
$$

#### Normalization

$$
\int_{-\infty}^{+\infty} p(x)\,dx = 1
$$

This ensures that the random variable must take some value.



## Example: The Gaussian Distribution

The Gaussian distribution is arguably the most important probability distribution in science, engineering, machine learning, and statistics.

Its density is

$$
p(x)
=
\frac{1}{\sqrt{2\pi\sigma^2}}
\exp
\left(
-\frac{(x-\mu)^2}{2\sigma^2}
\right)
$$

Although this formula may initially appear intimidating, every component has a clear interpretation.

### Mean

The parameter

$$
\mu
$$

controls the center of the distribution.

Increasing \(\mu\) shifts the bell curve to the right.

Decreasing \(\mu\) shifts it to the left.

### Variance

The parameter

$$
\sigma^2
$$

controls the spread of the distribution.

Large variance:

- wider bell curve,
- greater uncertainty.

Small variance:

- narrower bell curve,
- less uncertainty.

### Exponential Term

The quantity

$$
\exp
\left(
-\frac{(x-\mu)^2}{2\sigma^2}
\right)
$$

causes the density to decrease as we move away from the mean.

Points close to the mean receive high probability density.

Points far away receive low probability density.

### Normalization Constant

The factor

$$
\frac{1}{\sqrt{2\pi\sigma^2}}
$$

ensures that the total area under the density equals one.

Without this factor, the function would not represent a valid probability distribution.



## Cumulative Distribution Functions (CDF)

The cumulative distribution function gives the probability that a random variable is less than or equal to a specified value.

It is defined as

$$
F(x)=P(X\le x)
$$

For continuous random variables,

$$
F(x)
=
\int_{-\infty}^{x}
p(t)\,dt
$$

The CDF accumulates probability from left to right.

As \(x\) increases, the CDF gradually increases from 0 to 1.

### Properties

$$
0\le F(x)\le1
$$

$$
F(-\infty)=0
$$

$$
F(+\infty)=1
$$

and \(F(x)\) is always non-decreasing.

### Relationship Between PDF and CDF

The PDF can be recovered from the CDF through differentiation:

$$
p(x)
=
\frac{dF(x)}{dx}
$$

Thus:

- PDF describes local probability density.
- CDF describes accumulated probability.



## Expectation

Expectation can be interpreted as the long-run average outcome of a random experiment.

Suppose we repeatedly roll a fair die:

$$
1,4,6,2,5,3,\ldots
$$

The average value gradually approaches

$$
3.5
$$

This limiting average is called the expectation.

### Discrete Case

$$
E[X]
=
\sum_x x p(x)
$$

### Continuous Case

$$
E[X]
=
\int_{-\infty}^{+\infty}
x p(x)\,dx
$$

### Interpretation

Expectation is a weighted average.

Values that occur frequently contribute more heavily than values that occur rarely.

More generally,

$$
E[g(X)]
=
\int g(x)p(x)\,dx
$$

This quantity appears constantly in statistics, Bayesian inference, and machine learning.



## Variance

Expectation tells us where a distribution is centered.

Variance tells us how uncertain the distribution is.

Consider two students:

- Student A scores around 70 on every exam.
- Student B scores anywhere between 20 and 120.

They may have the same average score, but Student B exhibits much larger variability.

Variance measures this variability.

It is defined as

$$
\mathrm{Var}(X)
=
E[(X-E[X])^2]
$$

The term

$$
X-E[X]
$$

measures deviation from the mean.

Squaring prevents positive and negative deviations from cancelling each other.

The expectation then computes the average squared deviation.

### Alternative Formula

Expanding the square yields

$$
\mathrm{Var}(X)
=
E[X^2]
-
(E[X])^2
$$

which is often easier to compute.

### Standard Deviation

The square root of the variance is called the standard deviation:

$$
\sigma
=
\sqrt{\mathrm{Var}(X)}
$$

and is expressed in the same units as the random variable.



## Joint Distributions

Many real-world problems involve several random variables simultaneously.

Suppose we study:

- Height \(X\)
- Weight \(Y\)

Their combined behavior is described by the joint distribution

$$
p(x,y)
$$

The joint distribution specifies the probability of observing both variables simultaneously.



## Marginal Distributions

Sometimes we only care about one variable.

The distribution of \(X\) alone is obtained by integrating out \(Y\):

$$
p(x)
=
\int p(x,y)\,dy
$$

This process is called marginalization.

Marginalization is one of the most important operations in Bayesian inference.



## Conditional Probability

Conditional probability describes what happens when additional information becomes available.

The probability of \(X\) given \(Y\) is

$$
p(x|y)
=
\frac{p(x,y)}{p(y)}
$$

Conditional distributions are fundamental in machine learning, statistics, and Bayesian inference.



## Bayes' Rule

Bayes' theorem provides a mechanism for updating beliefs when new data are observed.

It is given by

$$
p(x|y)
=
\frac{p(y|x)p(x)}
     {p(y)}
$$

where:
<ul>
    <li>\(p(x)\) is the prior distribution representing our initial beliefs about \(x\)</li>
    <li>\(p(y|x)\) is the likelihood representing how likely the observed data \(y\) is given \(x\)</li>
    <li>\(p(x|y)\) is the posterior distribution representing our updated beliefs about \(x\) after observing \(y\)</li>
    <li>\(p(y)\) is the evidence representing the overall probability of observing \(y\)</li>
</ul>

Bayes' rule lies at the heart of modern Bayesian statistics and probabilistic machine learning.



## Why Probability Matters for Sampling

Many quantities of interest can be written as expectations:

$$
E[f(X)]
=
\int f(x)p(x)\,dx
$$

Unfortunately, these integrals are often impossible to evaluate analytically.

Sampling methods overcome this difficulty.

If we generate samples

$$
x_1,\ldots,x_N
\sim p(x)
$$

then the expectation can be approximated by

$$
E[f(X)]
\approx
\frac1N
\sum_{i=1}^{N}
f(x_i)
$$

This simple idea forms the foundation of:

- Monte Carlo Methods
- Importance Sampling
- Rejection Sampling
- Markov Chain Monte Carlo (MCMC)
- Gibbs Sampling
- Metropolis-Hastings
- Langevin Dynamics
- Hamiltonian Monte Carlo
- Diffusion Models
- Bayesian Inference

Everything that follows in this library builds upon these probabilistic concepts.



## Key Takeaways

After completing this chapter, you should understand:

- ✓ What random variables represent
- ✓ The difference between PMFs and PDFs
- ✓ How probabilities are computed using density functions
- ✓ The meaning of cumulative distribution functions
- ✓ How expectation and variance characterize distributions
- ✓ The role of joint, marginal, and conditional probabilities
- ✓ How Bayes' rule updates uncertainty
- ✓ Why probability theory is the mathematical foundation of sampling methods



## Next Chapter

In the next chapter, we will study common probability distributions used throughout statistics, machine learning, Bayesian inference, and Monte Carlo sampling.

**Next: Probability Distributions**

[Continue to Your First Sampler]({{ site.baseurl }}/start/03-first-sampler/)