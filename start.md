---
layout: default
title: Get Started with Sampling
# hero_subtitle: Beginner Learning Path
# hero_description: Begin your journey into the world of sampling algorithms with a guided, step-by-step sequence.
---

<div class="learning-path">
  <section class="learning-path-introduction" aria-labelledby="learning-path-about-title">
    <h2 id="learning-path-about-title">Building the knowledge to design samplers</h2>
    <p>
      Building reliable sampling methods requires some background in probability,
      probability distributions, statistics, numerical computation, and programming.
      These ideas help explain how a sampler works, why it targets the correct
      distribution, and how to recognise convergence problems or biased results.
    </p>
    <p>
      This page provides the tools needed to develop that foundation. The learning path
      starts with the central ideas behind sampling, refreshes the essential probability
      concepts, and then moves towards implementing and evaluating practical algorithms.
      You do not need to master every topic before beginning—each lesson introduces the
      knowledge you need as you progress.
    </p>
  </section>

  {% assign tutorials = site.start | sort: "order" %}
  <ol class="path-steps" aria-label="Sampling tutorials">
    {% for tutorial in tutorials %}
    <li class="step">
      <article class="step-content">
        <h3>{{ tutorial.title }}</h3>
        <p>{{ tutorial.description }}</p>
        <a href="{{ tutorial.url | relative_url }}" class="step-link">
          Start
          <i class="fas fa-arrow-right" aria-hidden="true"></i>
        </a>
      </article>
    </li>
    {% endfor %}
  </ol>
</div>

<style>
.learning-path {
  display: flex;
  flex-direction: column;
  gap: 22px;
  width: 100%;
  padding: 28px;
}

.learning-path-introduction {
  color: var(--text-secondary);
  line-height: 1.7;
}

.learning-path-introduction h2 {
  margin-bottom: 0.75rem;
  color: var(--text-primary);
  font-size: 1.35rem;
  font-weight: 700;
}

.learning-path-introduction p + p {
  margin-top: 0.85rem;
}

.path-steps {
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin: 0;
  padding: 0;
  list-style: none;
}

.step {
  margin: 0;
  padding: 8px 0;
}

.step-content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 6px;
}

.step-content h3 {
  color: var(--text-primary);
  font-size: 1.3rem;
  font-weight: 700;
  line-height: 1.3;
}

.step-content p {
  color: var(--text-secondary);
  line-height: 1.6;
}

.step-link {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  border-radius: 5px;
  color: var(--accent);
  font-weight: 600;
  text-decoration: none;
  transition: color 0.2s ease, background-color 0.2s ease, transform 0.2s ease;
}

.step-link:hover {
  color: var(--text-primary);
  background: var(--accent-bg);
  transform: translateX(3px);
}

.step-link:focus-visible {
  outline: 3px solid var(--accent);
  outline-offset: 3px;
}

.step-link i {
  font-size: 0.8rem;
}

@media (max-width: 600px) {
  .learning-path {
    padding: 20px;
  }

  .step-content {
    align-items: stretch;
  }

  .step-link {
    align-self: flex-start;
  }
}

@media (prefers-reduced-motion: reduce) {
  .step-link {
    transition: none;
  }

  .step-link:hover {
    transform: none;
  }
}
</style>
