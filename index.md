---
layout: default
title: Home
hero_title: Vision Maths Lab
hero_subtitle: Library of Sampling Methods
hero_description: We develop and study sampling methods for machine learning, Bayesian inference, and computational science.
hero_rotate: true
---
<div class="poster-container">
  <main class="main-content">
    <section class="section">
      <h2 class="section-title">Quick Links</h2>
      <div class="flow">
        <a href="{{ site.baseurl }}/start" class="flow-step">
          Start Tutorial
        </a>
        <a href="{{ site.baseurl }}/sampling-tools"  
          class="flow-step">Sampling Tools
        </a>
        <a href="{{ site.baseurl }}/examples" class="flow-step">
          Examples
        </a>
        <!-- <a href="{{ site.baseurl }}/projects" class="flow-step">Projects</a> -->
      </div>
    </section>

    <section class="section">
      <h2 class="section-title">Latest Tutorials</h2>
      <div class="latest-list">
        {% for post in site.posts limit:5 %}
        <article class="post-item">
          <h3><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>
          <p class="post-meta">{{ post.date | date: "%B %d, %Y" }}</p>
          <p class="section-text">{{ post.excerpt | strip_html | truncatewords: 25 }}</p>
        </article>
        {% endfor %}
      </div>
    </section>

    <!-- <section class="section">
      <h2 class="section-title">Website Snapshot</h2>
      <div class="stat-grid">
        <div class="stat-card">
          <div class="stat-number">5+</div>
          <div class="stat-label">Starter Lessons</div>
        </div>
        <div class="stat-card">
          <div class="stat-number">{{ site.posts | size }}</div>
          <div class="stat-label">Published Tutorials</div>
        </div>
        <div class="stat-card">
          <div class="stat-number">4</div>
          <div class="stat-label">Core Sections</div>
        </div>
      </div>
    </section> -->
  </main>
</div>

<style>
  .page-hero-title,
  .page-hero-subtitle,
  .page-hero-description {
    color: #ffd700 !important;
  }

  .poster-container {
    max-width: 100%;
    margin: 32px auto 0;
    background: var(--page-bg);
    border-radius: 28px;
    box-shadow: 0 8px 32px rgba(58, 143, 183, 0.12);
    overflow: hidden;
  }

  .main-content {
    display: flex;
    flex-direction: column;
    gap: 22px;
    padding: 28px;
  }

  .section {
    padding: 22px 24px;
    background: var(--accent-bg);
    border-radius: 22px;
  }

  .section-title {
    margin: 0 0 12px;
    border: 0;
    color: var(--text-primary);
    font-size: 20px;
    font-weight: 800;
  }

  .section-text {
    margin: 0;
    color: var(--text-secondary);
    line-height: 1.6;
  }

  .flow {
    display: flex;
    flex-direction: row;
    gap: 10px;
  }

  .flow-step {
    flex: 1;
    padding: 13px 15px;
    background: var(--page-bg);
    border: 1px solid var(--brand);
    border-radius: 10px;
    font-weight: 600;
    text-decoration: none;
    color: var(--text-primary);
  }

  .flow-step:hover {
    color: var(--brand);
  }

  .latest-list {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .post-item {
    padding: 14px;
    background: var(--page-bg);
    border: 1px solid var(--border);
    border-radius: 12px;
  }

  .post-item h3 {
    margin: 0 0 6px;
    color: var(--text-primary);
  }

  .post-item h3 a {
    text-decoration: none;
    color: var(--accent);
  }

  .post-meta {
    margin: 0 0 8px;
    color: var(--text-muted);
    font-size: 14px;
  }

  .stat-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 14px;
  }

  .stat-card {
    padding: 18px 14px;
    background: var(--page-bg);
    border: 1px solid var(--border);
    border-radius: 16px;
    text-align: center;
  }

  .stat-number {
    color: var(--accent);
    font-size: 28px;
    font-weight: 800;
  }

  .stat-label {
    margin-top: 6px;
    color: var(--text-muted);
    font-size: 14px;
  }

  @media (max-width: 600px) {
    .poster-container {
      margin-top: 0;
      border-radius: 0;
    }

    .main-content {
      padding: 20px;
    }
  }
</style>
