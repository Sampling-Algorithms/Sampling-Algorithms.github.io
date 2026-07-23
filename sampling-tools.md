---
layout: default
title: Sampling Tools
permalink: /sampling-tools/
# hero_subtitle: Algorithm Library
# hero_description: Browse a comprehensive collection of sampling algorithms, from foundational methods to advanced MCMC techniques.
---
{% assign basic_tools = site.tools | where_exp: "tool", "tool.path contains '/basics/'" | sort: "order" %}
{% assign mcmc_tools = site.tools | where_exp: "tool", "tool.path contains '/mcmcs/'" | sort: "order" %}
{% assign advanced_tools = site.tools | where_exp: "tool", "tool.path contains '/advanced/'" | sort: "order" %}
{% assign total_tools = basic_tools.size | plus: mcmc_tools.size | plus: advanced_tools.size %}

<div class="sampling-tools-page">
  {% if total_tools == 0 %}
  <section class="tools-empty-state" aria-labelledby="empty-tools-title">
    <h2 id="empty-tools-title">This page is empty for now</h2>
    <p>New sampling tools will be added soon. Please check back later.</p>
  </section>
  {% else %}
    {% assign tool_sections = "Basic Methods|Markov Chain Monte Carlo (MCMC)|Advanced Methods" | split: "|" %}
    {% for section_title in tool_sections %}
      {% case section_title %}
        {% when "Basic Methods" %}
          {% assign section_tools = basic_tools %}
          {% assign section_id = "basic-methods" %}
        {% when "Markov Chain Monte Carlo (MCMC)" %}
          {% assign section_tools = mcmc_tools %}
          {% assign section_id = "mcmc-methods" %}
        {% when "Advanced Methods" %}
          {% assign section_tools = advanced_tools %}
          {% assign section_id = "advanced-methods" %}
      {% endcase %}
      {% if section_tools.size > 0 %}
  <section class="tools-category" aria-labelledby="{{ section_id }}">
    <h2 id="{{ section_id }}">{{ section_title }}</h2>
    <ul class="tools-list">
      {% for tool in section_tools %}
      <li class="tool-item">
        <article class="tool-content">
          <h3>{{ tool.title }}</h3>
          <p>{{ tool.description }}</p>
          <a href="{{ tool.url | relative_url }}" class="tool-link">
            Read More
            <span aria-hidden="true">&rarr;</span>
          </a>
        </article>
      </li>
      {% endfor %}
    </ul>
  </section>
      {% endif %}
    {% endfor %}
  {% endif %}
</div>

<style>
.sampling-tools-page {
  display: flex;
  flex-direction: column;
  gap: 22px;
  width: 100%;
  padding: 28px;
}

.tools-empty-state {
  padding: 2rem 0;
  text-align: center;
}

.tools-empty-state h2,
.tools-category h2 {
  margin-bottom: 0.75rem;
  color: var(--text-primary);
  font-size: 1.35rem;
  font-weight: 700;
}

.tools-empty-state p {
  color: var(--text-secondary);
  line-height: 1.6;
}

.tools-list {
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin: 0;
  padding: 0;
  list-style: none;
}

.tool-item {
  margin: 0;
  padding: 8px 0;
}

.tool-content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 6px;
}

.tool-content h3 {
  color: var(--text-primary);
  font-size: 1.3rem;
  font-weight: 700;
  line-height: 1.3;
}

.tool-content p {
  color: var(--text-secondary);
  line-height: 1.6;
}

.tool-link {
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

.tool-link:hover {
  color: var(--text-primary);
  background: var(--accent-bg);
  transform: translateX(3px);
}

.tool-link:focus-visible {
  outline: 3px solid var(--accent);
  outline-offset: 3px;
}

@media (max-width: 600px) {
  .sampling-tools-page {
    padding: 20px;
  }

  .tool-content {
    align-items: stretch;
  }

  .tool-link {
    align-self: flex-start;
  }
}

@media (prefers-reduced-motion: reduce) {
  .tool-link {
    transition: none;
  }

  .tool-link:hover {
    transform: none;
  }
}
</style>
