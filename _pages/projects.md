---
layout: page
title: projects
permalink: /projects/
description: Selected research and course projects spanning medical AI, generative modeling, computer vision, and embodied perception.
nav: true
nav_order: 3
display_categories: [research, course-projects]
---

<style>
.publications-style-projects { margin-top: 1rem; }

.publications-style-projects h2.project-category {
  text-transform: capitalize;
  font-weight: 500;
  color: var(--global-text-color);
  border-bottom: 1px solid var(--global-divider-color);
  padding-bottom: 0.4rem;
  margin-top: 2.5rem;
  margin-bottom: 1.5rem;
  font-size: 1.4rem;
}

.publications-style-projects .project-item {
  display: flex;
  align-items: flex-start;
  gap: 1.5rem;
  margin-bottom: 2.5rem;
  padding-bottom: 1.5rem;
  border-bottom: 1px solid var(--global-divider-color);
}

.publications-style-projects .project-item:last-child {
  border-bottom: none;
}

.publications-style-projects .project-image {
  flex: 0 0 220px;
  max-width: 220px;
}

.publications-style-projects .project-image img {
  width: 100%;
  height: auto;
  border-radius: 4px;
  display: block;
}

.publications-style-projects .project-text {
  flex: 1 1 auto;
  min-width: 0;
}

.publications-style-projects .project-title {
  font-size: 1.05rem;
  font-weight: 600;
  margin: 0 0 0.3rem 0;
  line-height: 1.35;
}

.publications-style-projects .project-title a {
  color: var(--global-text-color);
  text-decoration: none;
}

.publications-style-projects .project-title a:hover {
  color: var(--global-theme-color);
}

.publications-style-projects .project-authors {
  font-size: 0.95rem;
  color: var(--global-text-color);
  margin: 0 0 0.2rem 0;
}

.publications-style-projects .project-venue {
  font-size: 0.95rem;
  color: var(--global-text-color-light);
  margin: 0 0 0.2rem 0;
}

.publications-style-projects .project-links {
  font-size: 0.9rem;
  margin: 0.2rem 0 0.6rem 0;
}

.publications-style-projects .project-links a {
  color: var(--global-theme-color);
  text-decoration: none;
}

.publications-style-projects .project-links a:hover {
  text-decoration: underline;
}

.publications-style-projects .project-abstract {
  font-size: 0.95rem;
  line-height: 1.55;
  color: var(--global-text-color);
  margin: 0;
  text-align: justify;
}

@media (max-width: 768px) {
  .publications-style-projects .project-item {
    flex-direction: column;
  }
  .publications-style-projects .project-image {
    flex: 0 0 auto;
    max-width: 100%;
  }
}
</style>

<div class="publications-style-projects">
  {% for category in page.display_categories %}
    {% assign categorized_projects = site.projects | where: "category", category %}
    {% assign sorted_projects = categorized_projects | sort: "importance" %}
    {% if sorted_projects.size > 0 %}
      <h2 class="project-category">{{ category | replace: "-", " " }}</h2>

      {% for project in sorted_projects %}
        <div class="project-item">
          <div class="project-image">
            {% if project.img %}
              <a href="{{ project.url | relative_url }}">
                <img src="{{ project.img | relative_url }}" alt="{{ project.title }}">
              </a>
            {% endif %}
          </div>
          <div class="project-text">
            <h3 class="project-title">
              <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
            </h3>
            {% if project.authors %}
              <p class="project-authors">{{ project.authors }}</p>
            {% endif %}
            {% if project.venue %}
              <p class="project-venue"><em>{{ project.venue }}</em></p>
            {% endif %}
            <p class="project-links">
              {% if project.paper %}<a href="{{ project.paper }}" target="_blank" rel="noopener">Paper</a>{% endif %}
              {% if project.paper and project.code %} / {% endif %}
              {% if project.code %}<a href="{{ project.code }}" target="_blank" rel="noopener">Code</a>{% endif %}
              {% if (project.paper or project.code) and project.website %} / {% endif %}
              {% if project.website %}<a href="{{ project.website }}" target="_blank" rel="noopener">Website</a>{% endif %}
              {% if (project.paper or project.code or project.website) and project.slides %} / {% endif %}
              {% if project.slides %}<a href="{{ project.slides }}" target="_blank" rel="noopener">Slides</a>{% endif %}
            </p>
            {% if project.abstract %}
              <p class="project-abstract">{{ project.abstract }}</p>
            {% else %}
              <p class="project-abstract">{{ project.description }}</p>
            {% endif %}
          </div>
        </div>
      {% endfor %}
    {% endif %}
  {% endfor %}
</div>
