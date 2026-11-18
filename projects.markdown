---
layout: page
lang: es
title: Proyectos
eyebrow: Alejandro Amaral / Open source
description: Herramientas para terminales, Unix, infraestructura y flujos de desarrollo, presentadas por su valor técnico y no solo por popularidad.
permalink: /proyectos/
translation: /en/projects/
---

<div class="project-grid">
  {% assign projects = site.data.projects | sort: 'display_order' %}
  {% for project in projects %}
    {% include project-card.html project=project heading_level=2 %}
  {% endfor %}
</div>
