---
layout: default
title: Eva Gottesfeld
permalink: /projects/
---

<div class="gallery-container">
  <div class="project-gallery">
    {% for project in site.projects %}
      <div class="gallery-item">
        <a href="{{ project.url | relative_url }}">
          <img src="{{ project.image | relative_url }}" alt="{{ project.title }}" />
          <p>{{ project.title }}</p>
        </a>

        {% if project.title == "Spotted Lanternfly Trap" %}
          <div class="project-sublinks">
            <a href="{{ project.url | relative_url }}#client-pitch">Client Pitch</a>
            <span>•</span>
            <a href="{{ project.url | relative_url }}#functional-prototype">Functional Prototype</a>
          </div>
        {% endif %}
      </div>
    {% endfor %}
  </div>
</div>

<style>
.project-sublinks {
  margin-top: 0.35rem;
  text-align: center;
  font-size: 0.95rem;
}

.project-sublinks a {
  text-decoration: none;
  font-weight: 500;
}

.project-sublinks a:hover {
  text-decoration: underline;
}

.project-sublinks span {
  margin: 0 0.35rem;
  opacity: 0.7;
}
</style>