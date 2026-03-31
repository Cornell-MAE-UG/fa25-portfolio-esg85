---
layout: default
title: Eva Gottesfeld
permalink: /projects/
---

<div class="gallery-container">
  <div class="project-gallery">
    {% for project in site.projects %}
      <div class="gallery-item">

        <a class="project-main-link" href="{{ project.url | relative_url }}">
          <img src="{{ project.image | relative_url }}" alt="{{ project.title }}" />
        </a>

        <p class="project-title">
          <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
        </p>

        {% if project.url contains 'MAE-2250-Portfolio' %}
          <div class="project-sublinks">
            <a href="{{ project.url | relative_url }}#client-pitch">Client Pitch</a>
            <a href="{{ project.url | relative_url }}#functional-prototype">Functional Prototype</a>
          </div>
        {% endif %}

      </div>
    {% endfor %}
  </div>
</div>

<style>
.project-main-link {
  display: block;
}

.project-title {
  margin: 0.6rem 0 0.25rem 0;
  text-align: center;
}

.project-title a {
  text-decoration: none;
  color: inherit;
  font-weight: 500;
}

.project-title a:hover {
  text-decoration: underline;
}

.project-sublinks {
  display: flex;
  justify-content: center;
  gap: 0.75rem;
  flex-wrap: wrap;
  margin-top: 0.25rem;
  font-size: 0.95rem;
}

.project-sublinks a {
  text-decoration: none;
  padding: 0.2rem 0.55rem;
  border: 1px solid #cfcfcf;
  border-radius: 999px;
}

.project-sublinks a:hover {
  text-decoration: underline;
}
</style>