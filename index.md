---
layout: default
title: Home
hero_title: Vision Maths Lab
hero_subtitle: Library of Sampling Methods
hero_description: We develop and study sampling methods for machine learning, Bayesian inference, and computational science.
hero_rotate: true
---
<div class="home-page">
  <section class="home-section" aria-labelledby="about-sampling-tools">
    <h2 id="about-sampling-tools" class="home-section-title">About Sampling Tools</h2>
    <div class="about-content">
      <p>
        Sampling Tools is an educational library for learning, comparing, and applying
        computational sampling methods. It brings together clear explanations,
        step-by-step tutorials, practical algorithms, and worked examples for problems
        in machine learning, Bayesian inference, statistics, and computational science.
      </p>
      <p>
        Sampling is important because many real-world probability distributions are too
        complex to study directly. Well-designed sampling methods allow us to approximate
        expectations, quantify uncertainty, explore complicated models, and make reliable
        inferences when an exact analytical solution is unavailable.
      </p>

      <h3>What you will find here</h3>
      <ul>
        <li><strong>Guided tutorials</strong> that introduce the key ideas from the ground up.</li>
        <li><strong>Sampling algorithms</strong> ranging from foundational methods to advanced MCMC techniques.</li>
        <li><strong>Practical examples</strong> showing how the methods behave and when to use them.</li>
        <li><strong>Implementation guidance</strong> for building, validating, and comparing your own samplers.</li>
      </ul>

      <p>
        The library is intended for students, researchers, and practitioners at different
        levels of experience. New visitors can begin with the introductory tutorial, while
        experienced users can go directly to the algorithm library or explore the examples.
      </p>
    </div>
  </section>

  <section class="home-section" aria-labelledby="latest-tutorials">
    <h2 id="latest-tutorials" class="home-section-title">Latest Tutorials</h2>
    <div class="latest-list">
      {% for post in site.posts limit: 3 %}
      <article class="post-item">
        <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
        <time class="post-meta" datetime="{{ post.date | date_to_xmlschema }}">
          {{ post.date | date: "%B %d, %Y" }}
        </time>
        <p>{{ post.excerpt | strip_html | truncatewords: 25 }}</p>
      </article>
      {% endfor %}
    </div>
  </section>
</div>

<style>
.page-hero-title,
.page-hero-subtitle,
.page-hero-description {
  color: var(--bright-gold) !important;
}

.home-page {
  display: flex;
  flex-direction: column;
  gap: 22px;
  width: 100%;
  margin: 32px auto 0;
  padding: 28px;
  background: var(--page-bg);
  border-radius: 28px;
  box-shadow: 0 8px 32px rgba(58, 143, 183, 0.12);
}

.home-section-title {
  margin-bottom: 12px;
  color: var(--text-primary);
  font-size: 1.35rem;
  font-weight: 800;
}

.about-content {
  color: var(--text-secondary);
  line-height: 1.7;
}

.about-content p + p {
  margin-top: 14px;
}

.about-content h3 {
  margin: 20px 0 8px;
  color: var(--text-primary);
  font-size: 1.1rem;
  font-weight: 700;
}

.about-content ul {
  margin: 0 0 16px;
  padding-left: 24px;
}

.about-content li + li {
  margin-top: 7px;
}

.latest-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.post-item {
  padding: 14px 0;
}

.post-item h3 {
  margin-bottom: 6px;
  font-size: 1.2rem;
  line-height: 1.3;
}

.post-item h3 a {
  color: var(--accent);
  text-decoration: none;
}

.post-item h3 a:hover {
  text-decoration: underline;
}

.post-item h3 a:focus-visible {
  outline: 3px solid var(--accent);
  outline-offset: 3px;
}

.post-meta {
  display: block;
  margin-bottom: 8px;
  color: var(--text-muted);
  font-size: 0.875rem;
}

.post-item p {
  color: var(--text-secondary);
  line-height: 1.6;
}

@media (max-width: 600px) {
  .home-page {
    margin-top: 0;
    padding: 20px;
    border-radius: 0;
  }
}
</style>
