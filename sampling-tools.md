---
layout: default
title: Sampling Tools
---

<!-- Navigation Bar -->
<!-- <div class="top-nav">
  <a href="{{ site.baseurl }}/" class="nav-link">Home</a>
  <a href="{{ site.baseurl }}/start" class="nav-link">Start</a>
  <a href="{{ site.baseurl }}/sampling-tools" class="nav-link active">Sampling tools</a>
  <a href="{{ site.baseurl }}/examples" class="nav-link">Examples</a>
  <a href="{{ site.baseurl }}/projects" class="nav-link">Projects</a>
</div> -->

<div class="page-header">
  <h1>🔧 Sampling Tools</h1>
  <p>A comprehensive collection of sampling algorithms</p>
</div>

<div class="tools-category">
  <h2>Basic Methods</h2>
  <div class="tools-grid">
    <div class="tool-card">
      <h3>🎲 Inverse Transform</h3>
      <p>The simplest approach when you have the CDF. Works for any 1D distribution.</p>
      <div class="tool-meta">
        <span class="difficulty">★☆☆</span>
        <span class="type">Direct</span>
      </div>
      <a href="#" class="tool-link">Learn More →</a>
    </div>
    
    <div class="tool-card">
      <h3>📦 Rejection Sampling</h3>
      <p>Sample from any distribution using a simpler proposal distribution.</p>
      <div class="tool-meta">
        <span class="difficulty">★★☆</span>
        <span class="type">Direct</span>
      </div>
      <a href="{{ site.baseurl }}/2026/02/13/rejection-sampling" class="tool-link">Learn More →</a>
    </div>
    
    <div class="tool-card">
      <h3>⚖️ Importance Sampling</h3>
      <p>Weighted samples for expectation estimation. Great for rare events.</p>
      <div class="tool-meta">
        <span class="difficulty">★★☆</span>
        <span class="type">Direct</span>
      </div>
      <a href="#" class="tool-link">Learn More →</a>
    </div>
  </div>
</div>

<div class="tools-category">
  <h2>Markov Chain Monte Carlo (MCMC)</h2>
  <div class="tools-grid">
    <div class="tool-card">
      <h3>🔄 Metropolis-Hastings</h3>
      <p>The classic MCMC algorithm. The workhorse of Bayesian inference.</p>
      <div class="tool-meta">
        <span class="difficulty">★★☆</span>
        <span class="type">MCMC</span>
      </div>
      <a href="#" class="tool-link">Learn More →</a>
    </div>
    
    <div class="tool-card">
      <h3>🔄 Gibbs Sampling</h3>
      <p>Coordinate-wise MCMC. Perfect when conditionals are known.</p>
      <div class="tool-meta">
        <span class="difficulty">★★★</span>
        <span class="type">MCMC</span>
      </div>
      <a href="#" class="tool-link">Learn More →</a>
    </div>
    
    <div class="tool-card">
      <h3>⚡ Hamiltonian MC</h3>
      <p>Gradient-based efficient sampling for high dimensions.</p>
      <div class="tool-meta">
        <span class="difficulty">★★★</span>
        <span class="type">MCMC</span>
      </div>
      <a href="#" class="tool-link">Learn More →</a>
    </div>
  </div>
</div>

<div class="tools-category">
  <h2>Advanced Methods</h2>
  <div class="tools-grid">
    <div class="tool-card">
      <h3>🍰 Slice Sampling</h3>
      <p>Adaptive MCMC that requires no tuning parameters.</p>
      <div class="tool-meta">
        <span class="difficulty">★★★</span>
        <span class="type">MCMC</span>
      </div>
      <a href="#" class="tool-link">Learn More →</a>
    </div>
    
    <div class="tool-card">
      <h3>🌡️ Parallel Tempering</h3>
      <p>Better mixing for multimodal distributions using temperature swaps.</p>
      <div class="tool-meta">
        <span class="difficulty">★★★★</span>
        <span class="type">MCMC</span>
      </div>
      <a href="#" class="tool-link">Learn More →</a>
    </div>
    
    <div class="tool-card">
      <h3>🔮 Sequential Monte Carlo</h3>
      <p>Particle filtering for time series and dynamic systems.</p>
      <div class="tool-meta">
        <span class="difficulty">★★★★</span>
        <span class="type">SMC</span>
      </div>
      <a href="#" class="tool-link">Learn More →</a>
    </div>
  </div>
</div>

<style>
/* Add the styles - combining previous styles with new ones */
.tools-category {
  margin: 3rem 0;
}

.tools-category h2 {
  color: #333;
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #667eea;
}

.tools-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.tool-card {
  background: white;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;
}

.tool-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(102, 126, 234, 0.2);
}

.tool-card h3 {
  color: #667eea;
  margin-bottom: 1rem;
}

.tool-card p {
  color: #666;
  margin-bottom: 1.5rem;
  line-height: 1.6;
}

.tool-meta {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1.5rem;
  padding-top: 1rem;
  border-top: 1px solid #f0f0f0;
}

.difficulty {
  color: #999;
  font-size: 0.9rem;
}

.type {
  background: #f0f0f0;
  padding: 0.2rem 1rem;
  border-radius: 15px;
  font-size: 0.8rem;
  color: #666;
}

.tool-link {
  color: #667eea;
  text-decoration: none;
  font-weight: 500;
}

.active {
  color: #667eea;
  font-weight: 600;
}
</style>