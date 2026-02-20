---
layout: default
title: Projects
---

<!-- Navigation Bar -->
<!-- <div class="top-nav">
  <a href="{{ site.baseurl }}/" class="nav-link">Home</a>
  <a href="{{ site.baseurl }}/start" class="nav-link">Start</a>
  <a href="{{ site.baseurl }}/sampling-tools" class="nav-link">Sampling tools</a>
  <a href="{{ site.baseurl }}/examples" class="nav-link">Examples</a>
  <a href="{{ site.baseurl }}/projects" class="nav-link active">Projects</a>
</div> -->

<div class="page-header">
  <h1>📚 Projects</h1>
  <p>Hands-on projects to apply your sampling knowledge</p>
</div>

<div class="projects-grid">
  <div class="project-card featured">
    <span class="project-tag">Featured</span>
    <h2>🔬 MCMC Diagnostics Suite</h2>
    <p class="project-description">Build a comprehensive diagnostic tool for MCMC algorithms. Implement trace plots, autocorrelation analysis, effective sample size calculation, and convergence diagnostics.</p>
    
    <div class="project-specs">
      <div class="spec">
        <span class="spec-label">Difficulty</span>
        <span class="spec-value">Intermediate</span>
      </div>
      <div class="spec">
        <span class="spec-label">Time</span>
        <span class="spec-value">2-3 hours</span>
      </div>
      <div class="spec">
        <span class="spec-label">Prerequisites</span>
        <span class="spec-value">MCMC basics</span>
      </div>
    </div>
    
    <div class="project-steps">
      <h3>What you'll build:</h3>
      <ul>
        <li>📊 Trace plot visualizer with multiple chains</li>
        <li>📈 Autocorrelation function calculator</li>
        <li>📉 Effective sample size estimator</li>
        <li>✅ Gelman-Rubin diagnostic</li>
      </ul>
    </div>
    
    <div class="project-actions">
      <a href="#" class="project-button">Start Project</a>
      <a href="#" class="project-button secondary">View Solution</a>
    </div>
  </div>
  
  <div class="project-card">
    <h2>🧬 Phylogenetic Tree Inference</h2>
    <p class="project-description">Use MCMC to reconstruct evolutionary trees from DNA sequences. Implement a simple version of MrBayes.</p>
    
    <div class="project-specs">
      <div class="spec">
        <span class="spec-label">Difficulty</span>
        <span class="spec-value">Advanced</span>
      </div>
      <div class="spec">
        <span class="spec-label">Time</span>
        <span class="spec-value">3-4 hours</span>
      </div>
    </div>
    
    <div class="project-actions">
      <a href="#" class="project-button">Start Project</a>
    </div>
  </div>
  
  <div class="project-card">
    <h2>🤖 Robot Localization with Particle Filters</h2>
    <p class="project-description">Implement a particle filter for robot position tracking using sensor data and motion models.</p>
    
    <div class="project-specs">
      <div class="spec">
        <span class="spec-label">Difficulty</span>
        <span class="spec-value">Intermediate</span>
      </div>
      <div class="spec">
        <span class="spec-label">Time</span>
        <span class="spec-value">2-3 hours</span>
      </div>
    </div>
    
    <div class="project-actions">
      <a href="#" class="project-button">Start Project</a>
    </div>
  </div>
  
  <div class="project-card">
    <h2>🎨 Variational Autoencoder from Scratch</h2>
    <p class="project-description">Build a VAE and understand the reparameterization trick for sampling from latent spaces.</p>
    
    <div class="project-specs">
      <div class="spec">
        <span class="spec-label">Difficulty</span>
        <span class="spec-value">Advanced</span>
      </div>
      <div class="spec">
        <span class="spec-label">Time</span>
        <span class="spec-value">4 hours</span>
      </div>
    </div>
    
    <div class="project-actions">
      <a href="#" class="project-button">Start Project</a>
    </div>
  </div>
</div>

<style>
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  padding: 2rem;
}

.project-card {
  background: white;
  border-radius: 10px;
  padding: 2rem;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  transition: all 0.3s ease;
  position: relative;
}

.project-card.featured {
  grid-column: span 2;
  border: 2px solid #667eea;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 15px rgba(102, 126, 234, 0.2);
}

.project-tag {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: #667eea;
  color: white;
  padding: 0.3rem 1rem;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 500;
}

.project-card h2 {
  color: #333;
  margin-bottom: 1rem;
  font-size: 1.5rem;
  padding-right: 80px;
}

.project-description {
  color: #666;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.project-specs {
  background: #f8f9fa;
  border-radius: 8px;
  padding: 1rem;
  margin-bottom: 1.5rem;
}

.spec {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 0;
  border-bottom: 1px solid #f0f0f0;
}

.spec:last-child {
  border-bottom: none;
}

.spec-label {
  color: #999;
  font-size: 0.9rem;
}

.spec-value {
  color: #333;
  font-weight: 500;
  font-size: 0.9rem;
}

.project-steps {
  margin-bottom: 1.5rem;
}

.project-steps h3 {
  color: #333;
  font-size: 1.1rem;
  margin-bottom: 0.5rem;
}

.project-steps ul {
  list-style: none;
  padding: 0;
}

.project-steps li {
  padding: 0.3rem 0;
  color: #666;
  font-size: 0.95rem;
}

.project-actions {
  display: flex;
  gap: 1rem;
  margin-top: 1.5rem;
}

.project-button {
  padding: 0.6rem 1.2rem;
  background: #667eea;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  font-size: 0.95rem;
  transition: background 0.3s ease;
  flex: 1;
  text-align: center;
}

.project-button:hover {
  background: #5a67d8;
}

.project-button.secondary {
  background: transparent;
  color: #667eea;
  border: 1px solid #667eea;
}

.project-button.secondary:hover {
  background: #f8f9fa;
}

.active {
  color: #667eea;
  font-weight: 600;
}

@media (max-width: 768px) {
  .project-card.featured {
    grid-column: span 1;
  }
  
  .project-actions {
    flex-direction: column;
  }
}
</style>