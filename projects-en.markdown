---
layout: page
lang: en
title: Projects
eyebrow: Alejandro Amaral / Open source
description: Tools for terminals, Unix, infrastructure, and development workflows, presented for their engineering value rather than popularity alone.
permalink: /en/projects/
translation: /proyectos/
---

<div class="project-grid">
  {% assign projects = site.data.projects | sort: 'display_order' %}
  {% for project in projects %}
    {% include project-card.html project=project heading_level=2 %}
  {% endfor %}
</div>
