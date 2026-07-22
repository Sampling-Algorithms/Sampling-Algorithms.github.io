---
layout: default
title: Sampling Tools
hero_subtitle: Algorithm Library
hero_description: Browse a comprehensive collection of sampling algorithms, from foundational methods to advanced MCMC techniques.
---
{% assign basic_tools = site.tools | where_exp: "tool", "tool.path contains '/basics/'" | sort: "order" %}
{% assign mcmc_tools = site.tools | where_exp: "tool", "tool.path contains '/mcmcs/'" | sort: "order" %}
{% assign advanced_tools = site.tools | where_exp: "tool", "tool.path contains '/advanced/'" | sort: "order" %}
{% assign total_tools = basic_tools.size | plus: mcmc_tools.size | plus: advanced_tools.size %}

{% if total_tools == 0 %}
  <div class="tools-empty-state">
    <h2>This page is empty for now</h2>
    <p>New sampling tools will be added soon. Please check back later.</p>
  </div>
{% endif %}

{% assign tool_sections = "Basic Methods|Markov Chain Monte Carlo (MCMC)|Advanced Methods" | split: "|" %}
{% for section_title in tool_sections %}
  {% case section_title %}
    {% when "Basic Methods" %}{% assign section_tools = basic_tools %}
    {% when "Markov Chain Monte Carlo (MCMC)" %}{% assign section_tools = mcmc_tools %}
    {% when "Advanced Methods" %}{% assign section_tools = advanced_tools %}
  {% endcase %}
  {% if section_tools.size > 0 %}
    <div class="tools-category">
      <h2>{{ section_title }}</h2>
      <div class="tools-grid">
        {% for tool in section_tools %}
          <div class="tool-card">
            <h3>{{ tool.title }}</h3>
            <p>{{ tool.description }}</p>
            <a href="{{ tool.url | relative_url }}" class="tool-link">Learn More &rarr;</a>
          </div>
        {% endfor %}
      </div>
    </div>
  {% endif %}
{% endfor %}

<style>
.tools-empty-state {
  margin: 3rem 0;
  padding: 2rem;
  text-align: center;
  background: white;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  font-family: inherit;
}

.tools-empty-state h2 {
  margin: 0 0 1rem;
  color: #333;
}

.tools-empty-state p {
  margin: 0;
  color: #000;
  line-height: 1.6;
}

.tools-category {
  margin: 3rem 0;
  font-family: inherit;
}

.tools-category h2 {
  color: #333;
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 0 solid #0f111a;
  font-family: inherit;
}

.tools-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  font-family: inherit;
}

.tool-card {
  background: white;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  font-family: inherit;
}

.tool-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(102, 126, 234, 0.2);
}

.tool-card h3 {
  color: #000;
  margin-bottom: 1rem;
}

.tool-card p {
  color: #000;
  margin-bottom: 1.5rem;
  line-height: 1.6;
}

.tool-link {
  color: #1120f5;
  text-decoration: none;
  font-weight: 500;
}

.active {
  color: #1120f5;
  font-weight: 600;
}
</style>
