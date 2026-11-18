---
layout: page
lang: es
title: Experiencia
eyebrow: Alejandro Amaral / Trayectoria
description: Arquitectura, entrega y liderazgo técnico en sistemas que operan bajo restricciones reales.
permalink: /experiencia/
translation: /en/experience/
---

<div class="experience-list">
  {% for experience in site.data.experience %}
    {% include experience-item.html experience=experience heading_level=2 %}
  {% endfor %}
</div>

Las descripciones se limitan a información profesional confirmada y no exponen detalles internos, contratos ni cifras pendientes de aprobación editorial.
