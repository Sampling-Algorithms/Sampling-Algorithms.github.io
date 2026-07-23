---
title: "Flow Matching"
description: "Learn how flow matching trains a continuous-time vector field to transport noise into data samples."
# order: 3
# icon: "🛠️"
---

# Flow Matching

Flow matching is a generative modeling method that learns to transport samples from a
simple source distribution, usually Gaussian noise, to a data distribution. It learns
a time-dependent velocity field; generation then consists of drawing noise and solving
an ordinary differential equation (ODE).

## From noise to data

Let $p_0$ be an easy-to-sample source distribution and $p_1$ the data distribution.
We seek a vector field $v_\theta(x,t)$ whose ODE

$$
\frac{dX_t}{dt}=v_\theta(X_t,t), \qquad X_0\sim p_0
$$

transforms $p_0$ into $p_1$ at $t=1$. The intermediate density $p_t$ follows the
continuity equation

$$
\partial_t p_t(x)+\nabla\cdot\left(p_t(x)v_t(x)\right)=0.
$$

Because the data distribution is known only through samples, constructing $v_t$
directly is difficult. Conditional flow matching turns the task into supervised
regression.

## A linear probability path

Draw independent endpoints

$$
X_0\sim p_0,\qquad X_1\sim p_1
$$

and interpolate between them:

$$
X_t=(1-t)X_0+tX_1,\qquad t\in[0,1].
$$

The velocity of this conditional path is especially simple:

$$
U_t=\frac{dX_t}{dt}=X_1-X_0.
$$

This gives the flow-matching objective

$$
\mathcal{L}_{\mathrm{FM}}(\theta)
=\mathbb{E}_{t,X_0,X_1}
\left[\left\|v_\theta(X_t,t)-(X_1-X_0)\right\|^2\right],
$$

where $t\sim\mathrm{Uniform}(0,1)$. The mean-squared-error optimum is the marginal
velocity $\mathbb{E}[U_t\mid X_t=x]$, so the learned ODE transports the intermediate
distributions along the chosen path.

Other paths can use time-dependent Gaussian noise schedules or non-independent
couplings of $X_0$ and $X_1$. The path affects trajectory curvature and therefore the
number of ODE steps needed at sampling time.

## Training

For each minibatch:

1. Draw data $x_1$ and Gaussian noise $x_0$ of the same shape.
2. Draw one time $t\sim\mathrm{Uniform}(0,1)$ per sample.
3. Form $x_t=(1-t)x_0+tx_1$.
4. Predict $v_\theta(x_t,t)$.
5. Minimize the mean squared error to $x_1-x_0$.

A minimal PyTorch loss is:

```python
def flow_matching_loss(model, x1):
    x0 = torch.randn_like(x1)
    t = torch.rand(x1.shape[0], device=x1.device)
    shape = (x1.shape[0],) + (1,) * (x1.ndim - 1)
    t_view = t.view(shape)

    xt = (1.0 - t_view) * x0 + t_view * x1
    target = x1 - x0
    prediction = model(xt, t)
    return torch.mean((prediction - target) ** 2)
```

The model must receive time as an input, commonly through sinusoidal or learned time
embeddings. A multilayer perceptron works for low-dimensional examples; image models
typically use a U-Net or transformer architecture.

## Sampling

After training, draw $x_0\sim p_0$ and integrate forward from $t=0$ to $t=1$. Euler's
method provides a minimal sampler:

```python
@torch.no_grad()
def sample_euler(model, shape, steps, device):
    x = torch.randn(shape, device=device)
    dt = 1.0 / steps

    for i in range(steps):
        t = torch.full((shape[0],), i * dt, device=device)
        x = x + dt * model(x, t)

    return x
```

Euler integration is useful for debugging. Midpoint or Heun integration usually
achieves better accuracy with fewer steps. Adaptive ODE solvers are convenient, but
their runtime and number of model evaluations vary between samples.

## Flow matching and diffusion models

Both methods transform noise into data, but their common formulations use different
training targets:

- Diffusion models often predict a score, noise, or a denoised sample and generate
  with a reverse-time stochastic differential equation or a related ODE.
- Flow matching directly predicts the velocity of a chosen probability path and
  generates with its forward ODE.

Flow matching therefore uses a standard regression loss and does not require
simulating a diffusion process during training.

## Practical considerations

- Scale the data so its numerical range is compatible with the source noise.
- Always condition the network on time.
- For paths with endpoint singularities, sample time from
  $[\varepsilon,1-\varepsilon]$.
- Compare multiple solver step counts; low training loss does not guarantee low
  discretization error.
- Use straighter probability paths or higher-order solvers to reduce model evaluations.
- An exponential moving average of model parameters often makes sampling more stable.

## Summary

Flow matching has two core operations:

1. Regress a time-dependent vector field against velocities of sampled paths.
2. Transport fresh noise through the learned ODE to obtain data-like samples.

Linear interpolation is a useful starting point because its target velocity is simply
$X_1-X_0$. More advanced variants improve the coupling, probability path, model, or
ODE solver while retaining the same training principle.
