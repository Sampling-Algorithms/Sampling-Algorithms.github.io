---
layout: default
title: Projects
# hero_subtitle: Practice Through Projects
# hero_description: Apply your sampling knowledge with hands-on projects designed to build intuition and implementation skills.
---

<div class="projects-grid">
  <div class="project-card featured">
    <span class="project-tag">Featured</span>
    <h2>MCMC Diagnostics Suite</h2>
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
        <li>Trace plot visualizer with multiple chains</li>
        <li>Autocorrelation function calculator</li>
        <li>Effective sample size estimator</li>
        <li>Gelman-Rubin diagnostic</li>
      </ul>
    </div>
    
    <div class="project-actions">
      <a href="{{ site.baseurl }}/_examples/Bayesian/linear-regression" class="project-button">Start Project</a>
      <a href="{{ site.baseurl }}/examples" class="project-button secondary">View Solution</a>
    </div>
  </div>
  
  <div class="project-card">
    <h2>Phylogenetic Tree Inference</h2>
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
      <a href="{{ site.baseurl }}/examples" class="project-button">Start Project</a>
    </div>
  </div>
  
  <div class="project-card">
    <h2> Robot Localization with Particle Filters</h2>
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
      <a href="{{ site.baseurl }}/examples" class="project-button">Start Project</a>
    </div>
  </div>
  
  <div class="project-card">
    <h2> Variational Autoencoder from Scratch</h2>
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
      <a href="{{ site.baseurl }}/examples" class="project-button">Start Project</a>
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
  background: var(--page-bg-alt);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 2rem;
  box-shadow: var(--shadow-sm);
  transition: all 0.3s ease;
  position: relative;
}

.project-card.featured {
  grid-column: span 2;
  border: 2px solid var(--accent);
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-md);
  border-color: rgba(23, 184, 166, 0.35);
}

.project-tag {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: var(--accent);
  color: white;
  padding: 0.3rem 1rem;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 500;
}

.project-card h2 {
  color: var(--text-primary);
  margin-bottom: 1rem;
  font-size: 1.5rem;
  padding-right: 80px;
}

.project-description {
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.project-specs {
  background: var(--page-bg);
  border-radius: 8px;
  padding: 1rem;
  margin-bottom: 1.5rem;
}

.spec {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 0;
  border-bottom: 1px solid var(--border);
}

.spec:last-child {
  border-bottom: none;
}

.spec-label {
  color: var(--text-muted);
  font-size: 0.9rem;
}

.spec-value {
  color: var(--text-primary);
  font-weight: 500;
  font-size: 0.9rem;
}

.project-steps {
  margin-bottom: 1.5rem;
}

.project-steps h3 {
  color: var(--text-primary);
  font-size: 1.1rem;
  margin-bottom: 0.5rem;
}

.project-steps ul {
  list-style: none;
  padding: 0;
}

.project-steps li {
  padding: 0.3rem 0;
  color: var(--text-secondary);
  font-size: 0.95rem;
}

.project-actions {
  display: flex;
  gap: 1rem;
  margin-top: 1.5rem;
}

.project-button {
  padding: 0.6rem 1.2rem;
  background: var(--accent);
  color: white;
  text-decoration: none;
  border-radius: 5px;
  font-size: 0.95rem;
  transition: background 0.3s ease;
  flex: 1;
  text-align: center;
}

.project-button:hover {
  background: var(--accent-dark);
}

.project-button.secondary {
  background: transparent;
  color: var(--accent);
  border: 1px solid var(--accent);
}

.project-button.secondary:hover {
  background: var(--page-bg);
}

.active {
  color: var(--accent);
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