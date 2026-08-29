---
layout: default
title: Examples
hero_subtitle: Applied Sampling Case Studies
hero_description: Explore real-world applications of sampling algorithms across statistics, optimization, and scientific computing.
---

<!-- Navigation Bar -->
<!-- <div class="top-nav">
  <a href="{{ site.baseurl }}/" class="nav-link">Home</a>
  <a href="{{ site.baseurl }}/start" class="nav-link">Start</a>
  <a href="{{ site.baseurl }}/sampling-tools" class="nav-link">Sampling tools</a>
  <a href="{{ site.baseurl }}/examples" class="nav-link active">Examples</a>
  <a href="{{ site.baseurl }}/projects" class="nav-link">Projects</a>
</div> -->

<!-- <div class="page-header">
  <h1>💡 Examples</h1>
  <p>Real-world applications of sampling algorithms</p>
</div> -->

<div class="examples-grid">
  <div class="example-card">
    <div class="example-icon">📈</div>
    <h2>Bayesian Linear Regression</h2>
    <p>Use MCMC to sample from posterior distributions of regression parameters. Includes uncertainty quantification and prediction intervals.</p>
    <div class="example-details">
      <span class="badge">Metropolis-Hastings</span>
      <span class="badge">PyMC3</span>
      <span class="badge">Intermediate</span>
    </div>
    <div class="example-links">
      <a href="{{ site.baseurl }}/examples/bayesian-linear-regression-notebook/" class="example-button">View Notebook Page</a>
      <a href="{{ site.baseurl }}/examples/bayesian-linear-regression-notebook/" class="example-button secondary">Read Details</a>
    </div>
  </div>
  
  <div class="example-card">
    <div class="example-icon">🧊</div>
    <h2>Ising Model Simulation</h2>
    <p>Sample spin configurations in statistical physics. Models magnetic materials and social networks.</p>
    <div class="example-details">
      <span class="badge">Gibbs Sampling</span>
      <span class="badge">Physics</span>
      <span class="badge">Advanced</span>
    </div>
    <div class="example-links">
      <a href="{{ site.baseurl }}/_examples/Statistics/linear-regression" class="example-button">View Tutorial</a>
      <a href="{{ site.baseurl }}/_examples/Statistics/linear-regression" class="example-button secondary">Read Details</a>
    </div>
  </div>
  
  <div class="example-card">
    <div class="example-icon">📉</div>
    <h2>Option Pricing</h2>
    <p>Monte Carlo simulation for financial derivatives. Price European and Asian options.</p>
    <div class="example-details">
      <span class="badge">Monte Carlo</span>
      <span class="badge">Finance</span>
      <span class="badge">Beginner</span>
    </div>
    <div class="example-links">
      <a href="{{ site.baseurl }}/_examples/Statistics/linear-regression" class="example-button">View Tutorial</a>
      <a href="{{ site.baseurl }}/_examples/Statistics/linear-regression" class="example-button secondary">Read Details</a>
    </div>
  </div>
  
  <div class="example-card">
    <div class="example-icon">⛰️</div>
    <h2>Simulated Annealing</h2>
    <p>Global optimization using sampling techniques. Find the minimum of complex functions.</p>
    <div class="example-details">
      <span class="badge">Optimization</span>
      <span class="badge">Annealing</span>
      <span class="badge">Intermediate</span>
    </div>
    <div class="example-links">
      <a href="{{ site.baseurl }}/_examples/Optimisation/linear-regression" class="example-button">View Tutorial</a>
      <a href="{{ site.baseurl }}/_examples/Optimisation/linear-regression" class="example-button secondary">Read Details</a>
    </div>
  </div>

  <div class="example-card">
    <div class="example-icon">📓</div>
    <h2>Notebook: Bayesian Regression</h2>
    <p>Run a full Bayesian linear regression workflow in a Jupyter notebook with posterior sampling and diagnostics.</p>
    <div class="example-details">
      <span class="badge">Jupyter</span>
      <span class="badge">PyMC</span>
      <span class="badge">Interactive</span>
    </div>
    <div class="example-links">
      <a href="{{ site.baseurl }}/_examples/bayesian-linear-regression-notebook" class="example-button">View Notebook Page</a>
      <a href="https://colab.research.google.com/github/Sampling-Algorithms/Sampling-Algorithms.github.io/blob/main/notebooks/bayesian-linear-regression.ipynb" class="example-button secondary">Open in Colab</a>
    </div>
  </div>
</div>

<style>
.examples-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  padding: 2rem;
}

.example-card {
  background: var(--page-bg-alt);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 2rem;
  box-shadow: var(--shadow-sm);
  transition: all 0.3s ease;
}

.example-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-md);
  border-color: rgba(23, 184, 166, 0.35);
}

.example-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.example-card h2 {
  color: var(--text-primary);
  margin-bottom: 1rem;
  font-size: 1.5rem;
}

.example-card p {
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.example-details {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.badge {
  background: var(--page-bg);
  padding: 0.3rem 1rem;
  border-radius: 20px;
  font-size: 0.85rem;
  color: var(--text-secondary);
}

.example-links {
  display: flex;
  gap: 1rem;
}

.example-button {
  padding: 0.5rem 1rem;
  background: var(--accent);
  color: white;
  text-decoration: none;
  border-radius: 5px;
  font-size: 0.9rem;
  transition: background 0.3s ease;
}

.example-button:hover {
  background: var(--accent-dark);
}

.example-button.secondary {
  background: transparent;
  color: var(--accent);
  border: 1px solid var(--accent);
}

.example-button.secondary:hover {
  background: var(--page-bg);
}

.active {
  color: var(--accent);
  font-weight: 600;
}
</style>