---
layout: default
title: Home
---
<!-- <div class="welcome-section" style="background-image: url('{{ site.baseurl }}/assets/images/background.png');"> -->
<!-- <div class="welcome-section" style="background-image: url('{{ site.baseurl }}/assets/images/logo2.jpg');"> -->
<div class="welcome-section" id="welcome-section">
  <div class="welcome-overlay">
    <div class="container">
      <h2>Welcome to the Vision Maths Lab</h2>
      <p>We develop and study sampling methods for machine learning, Bayesian inference, and computational science.</p>
    </div>
  </div>

  <div class="quick-links">
    <a href="{{ site.baseurl }}/start" class="quick-link">
      <span class="quick-icon">🚀</span>
      <span>Get Started</span>
    </a>
    <a href="{{ site.baseurl }}/sampling-tools" class="quick-link">
      <span class="quick-icon">🔧</span>
      <span>Sampling Tools</span>
    </a>
    <a href="{{ site.baseurl }}/examples" class="quick-link">
      <span class="quick-icon">💡</span>
      <span>Examples</span>
    </a>
    <a href="{{ site.baseurl }}/projects" class="quick-link">
      <span class="quick-icon">📚</span>
      <span>Projects</span>
    </a>
  </div>
</div>


<!-- Latest Tutorials -->
<div class="latest-tutorials">
  <h2>📖 Latest Tutorials</h2>
  <div class="tutorial-preview">
    {% for post in site.posts limit:5 %}
    <div class="preview-card">
      <h3><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>
      <p class="post-meta">{{ post.date | date: "%B %d, %Y" }}</p>
      <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More →</a>
    </div>
    {% endfor %}
  </div>
</div>

<!-- Add the CSS styles (same as before) -->
<style>
/* Remove default browser spacing */
body {
  margin: 0;
  padding: 0;
}

/* Welcome section flush with navbar */
.welcome-section {
  text-align: center;
  width: 100%;
  margin: 0;           
  padding-top: 20px;   
  padding-bottom: 50px;
}

/* Headings inside welcome section */
.welcome-section h2 {
  font-size: 2rem;
  color: #fcfcfc;
  margin-top: 0;       
  margin-bottom: 1rem;
}

.welcome-section p {
  color: #fcfcfc;
  font-size: 1.2rem;
  margin-top: 0;
  margin-bottom: 2rem;
}

/* Quick links row */
.quick-links {
  display: flex;           
  justify-content: center; 
  gap: 20px;               
  flex-wrap: nowrap;      
  margin-top: 60px;        /
  align-items: center;
}

/* Individual quick links */
.quick-link {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 15px;
  background: rgba(78, 75, 75, 0.5);
  border-radius: 8px;
  text-decoration: none;
  color: white;
  font-weight: bold;
  transition: background 0.3s, transform 0.3s;
}

.quick-link:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
  background: #667eea;
}

/* Quick icons */
.quick-icon {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
}

/* Latest tutorials section */
.latest-tutorials {
  margin: 4rem 0;
}

.latest-tutorials h2 {
  font-size: 2rem;
  color: #333;
  margin-bottom: 2rem;
  text-align: center;
}

/* Grid for tutorial previews */
.tutorial-preview {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

/* Preview cards */
.preview-card {
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  border: 1px solid #f0f0f0;
}

.preview-card h3 {
  margin-bottom: 0.5rem;
}

.preview-card h3 a {
  color: #667eea;
  text-decoration: none;
}

.post-meta {
  color: #999;
  font-size: 0.9rem;
  margin-bottom: 1rem;
}

.read-more {
  display: inline-block;
  margin-top: 1rem;
  color: #667eea;
  text-decoration: none;
  font-weight: 500;
}

/* Responsive tweaks */
@media (max-width: 768px) {
  .quick-links {
    gap: 1rem;
  }
  .quick-link {
    min-width: 120px;
    padding: 1rem;
  }
}
</style>

<!-- Javascript -->
<script>
  const welcomeSection = document.getElementById('welcome-section');

  const backgrounds = [
    "{{ site.baseurl }}/assets/images/logo.jpg",
    "{{ site.baseurl }}/assets/images/logo1.jpg",
    "{{ site.baseurl }}/assets/images/logo2.jpg",
    "{{ site.baseurl }}/assets/images/background.png"
  ];

  let current = 0;

  // Set initial background
  welcomeSection.style.backgroundImage = `url('${backgrounds[current]}')`;

  // Change background every 1 minute
  setInterval(() => {
    current = (current + 1) % backgrounds.length;
    welcomeSection.style.backgroundImage = `url('${backgrounds[current]}')`;
  }, 5000);
</script>