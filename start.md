---
layout: default
title: Get Started with Sampling
---

<!-- Navigation Bar -->
<!-- <div class="top-nav">
  <a href="{{ site.baseurl }}/" class="nav-link">Home</a>
  <a href="{{ site.baseurl }}/start" class="nav-link active">Start</a>
  <a href="{{ site.baseurl }}/sampling-tools" class="nav-link">Sampling tools</a>
  <a href="{{ site.baseurl }}/examples" class="nav-link">Examples</a>
  <a href="{{ site.baseurl }}/projects" class="nav-link">Projects</a>
</div> -->

<div class="page-header">
  <h1>🚀 Get Started with Sampling</h1>
  <p>Begin your journey into the world of sampling algorithms</p>
</div>

<div class="learning-path">
  <h2>Learning Path</h2>
  <p class="path-description">Follow these steps in order to build a solid foundation</p>
  
  <div class="path-steps">
    {% assign tutorials = site.start | sort: 'order' %}
    {% for tutorial in tutorials %}
    <div class="step">
      <div class="step-number">{{ tutorial.order }}</div>
      <div class="step-content">
        <div class="step-icon">{{ tutorial.icon }}</div>
        <h3>{{ tutorial.title }}</h3>
        <p>{{ tutorial.description }}</p>
        <a href="{{ site.baseurl }}{{ tutorial.url }}" class="step-link">
          Start 
          <i class="fas fa-arrow-right"></i>
        </a>
      </div>
    </div>
    {% endfor %}
  </div>
</div>

<!-- Progress Tracker -->
<div class="progress-tracker">
  <h3>Your Progress</h3>
  <div class="progress-bar-container">
    <div class="progress-bar" style="width: 0%" id="progress-bar"></div>
  </div>
  <p class="progress-text">0/{{ site.start | size }} completed</p>
</div>

<style>
.page-header {
  text-align: center;
  margin: 3rem 0;
}

.page-header h1 {
  font-size: 2.5rem;
  color: #333;
  margin-bottom: 0.5rem;
}

.page-header p {
  font-size: 1.2rem;
  color: #666;
}

.learning-path {
  max-width: 900px;
  margin: 0 auto;
  padding: 2rem;
}

.learning-path h2 {
  text-align: center;
  margin-bottom: 0.5rem;
  color: #333;
  font-size: 2rem;
}

.path-description {
  text-align: center;
  color: #666;
  margin-bottom: 3rem;
}

.path-steps {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.step {
  display: flex;
  gap: 1.5rem;
  align-items: flex-start;
  background: white;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  transition: all 0.3s ease;
  border: 1px solid transparent;
}

.step:hover {
  transform: translateX(10px);
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.2);
  border-color: #667eea;
}

.step-number {
  width: 40px;
  height: 40px;
  background: #667eea;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 1.2rem;
  flex-shrink: 0;
}

.step-content {
  flex: 1;
  display: flex;
  flex-direction: column;
}

.step-icon {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

.step-content h3 {
  color: #333;
  margin-bottom: 0.5rem;
  font-size: 1.3rem;
}

.step-content p {
  color: #666;
  margin-bottom: 1rem;
  line-height: 1.6;
}

.step-link {
  align-self: flex-start;
  color: #667eea;
  text-decoration: none;
  font-weight: 500;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background: #f0f4ff;
  border-radius: 5px;
  transition: all 0.3s ease;
}

.step-link:hover {
  background: #667eea;
  color: white;
  gap: 1rem;
}

.step-link i {
  font-size: 0.8rem;
}

/* Progress Tracker */
.progress-tracker {
  max-width: 900px;
  margin: 3rem auto;
  padding: 2rem;
  background: white;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  text-align: center;
}

.progress-tracker h3 {
  color: #333;
  margin-bottom: 1rem;
}

.progress-bar-container {
  height: 10px;
  background: #f0f0f0;
  border-radius: 5px;
  overflow: hidden;
  margin-bottom: 0.5rem;
}

.progress-bar {
  height: 100%;
  background: linear-gradient(90deg, #667eea, #764ba2);
  border-radius: 5px;
  transition: width 0.3s ease;
}

.progress-text {
  color: #666;
  font-size: 0.9rem;
}

.active {
  color: #667eea;
  font-weight: 600;
}

@media (max-width: 768px) {
  .step {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  
  .step-link {
    align-self: center;
  }
  
  .step-icon {
    margin-bottom: 0.5rem;
  }
}
</style>

<script>
// Simple progress tracker using localStorage
document.addEventListener('DOMContentLoaded', function() {
  const totalSteps = {{ site.start | size }};
  let completed = 0;
  
  // Check which tutorials are completed
  document.querySelectorAll('.step').forEach((step, index) => {
    const tutorialUrl = step.querySelector('.step-link').getAttribute('href');
    if (localStorage.getItem('completed_' + tutorialUrl) === 'true') {
      step.classList.add('completed');
      completed++;
    }
  });
  
  // Update progress bar
  const progressPercent = (completed / totalSteps) * 100;
  document.getElementById('progress-bar').style.width = progressPercent + '%';
  document.querySelector('.progress-text').textContent = 
    `${completed}/${totalSteps} completed`;
  
  // Mark as completed when clicking start
  document.querySelectorAll('.step-link').forEach(link => {
    link.addEventListener('click', function(e) {
      // Don't prevent default - we want to navigate
      const tutorialUrl = this.getAttribute('href');
      localStorage.setItem('completed_' + tutorialUrl, 'true');
    });
  });
});
</script>