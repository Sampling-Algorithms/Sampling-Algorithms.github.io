---
layout: default
title: Examples
---

<!-- Navigation Bar -->
<!-- <div class="top-nav">
  <a href="{{ site.baseurl }}/" class="nav-link">Home</a>
  <a href="{{ site.baseurl }}/start" class="nav-link">Start</a>
  <a href="{{ site.baseurl }}/sampling-tools" class="nav-link">Sampling tools</a>
  <a href="{{ site.baseurl }}/examples" class="nav-link active">Examples</a>
  <a href="{{ site.baseurl }}/projects" class="nav-link">Projects</a>
</div> -->

<div class="page-header">
  <h1>💡 Examples</h1>
  <p>Real-world applications of sampling algorithms</p>
</div>

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
      <a href="#" class="example-button">View Tutorial</a>
      <a href="#" class="example-button secondary">Run in Colab</a>
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
      <a href="#" class="example-button">View Tutorial</a>
      <a href="#" class="example-button secondary">Run in Colab</a>
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
      <a href="#" class="example-button">View Tutorial</a>
      <a href="#" class="example-button secondary">Run in Colab</a>
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
      <a href="#" class="example-button">View Tutorial</a>
      <a href="#" class="example-button secondary">Run in Colab</a>
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
  background: white;
  border-radius: 10px;
  padding: 2rem;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  transition: all 0.3s ease;
}

.example-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 15px rgba(102, 126, 234, 0.2);
}

.example-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.example-card h2 {
  color: #333;
  margin-bottom: 1rem;
  font-size: 1.5rem;
}

.example-card p {
  color: #666;
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
  background: #f0f0f0;
  padding: 0.3rem 1rem;
  border-radius: 20px;
  font-size: 0.85rem;
  color: #666;
}

.example-links {
  display: flex;
  gap: 1rem;
}

.example-button {
  padding: 0.5rem 1rem;
  background: #667eea;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  font-size: 0.9rem;
  transition: background 0.3s ease;
}

.example-button:hover {
  background: #5a67d8;
}

.example-button.secondary {
  background: transparent;
  color: #667eea;
  border: 1px solid #667eea;
}

.example-button.secondary:hover {
  background: #f8f9fa;
}

.active {
  color: #667eea;
  font-weight: 600;
}
</style>