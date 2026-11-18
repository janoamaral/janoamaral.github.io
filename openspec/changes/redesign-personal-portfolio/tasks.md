# Tasks

## 1. Baseline y publicación reproducible

- [x] 1.1 Ejecutar el build de producción actual, guardar un inventario temporal de rutas generadas para `/`, `/en/`, About y todos los posts, y verificar que `feed.xml` existe antes de editar templates.
- [x] 1.2 Identificar posts representativos con hero, TOC, código, imágenes, premonitions y embeds, y verificar en el build actual una URL ES y su contraparte EN para cada contrato usado.
- [x] 1.3 Corregir los globs de Tailwind para incluir `blog/**/_posts/*.{md,markdown}`, eliminar `paginate`/`paginate_path` si se confirma que ninguna plantilla los usa y verificar que el build de producción no purga clases necesarias ni advierte sobre paginación.
- [x] 1.4 Documentar el comando local requerido por `jekyll-postcss` y el comando equivalente a CI, y verificar que ambos generan el sitio con las dependencias bloqueadas sin actualizar versiones mayores.

## 2. Fase 1: base visual, shell y homepage

- [x] 2.1 Crear datos mínimos de perfil y navegación ES/EN con LinkedIn, GitHub y Lógico, excluir email/CV no aprobados y verificar que cada enlace renderizado coincide con una URL oficial.
- [x] 2.2 Crear `_data/experience.yml` con roles y fechas confirmadas más flags de aprobación, y verificar que el build no contiene `~90 s`, `<1 s`, near-real-time ni estado laboral no confirmado mientras esos items estén deshabilitados.
- [x] 2.3 Crear `_data/projects.yml` con los siete repositorios, estado de Typewriter, agrupación de Typewriter Vim y métricas fechadas disponibles, y verificar que Sparkle no recibe un valor de forks inventado.
- [x] 2.4 Implementar tokens de color, tipografía, grilla, ancho de lectura, foco y motion reducido en CSS/Tailwind; usar fuentes locales solo con licencia confirmada y verificar contraste, fallback y ausencia de contenido oculto sin animación.
- [x] 2.5 Refactorizar `default.html` en un shell semántico con header y footer compartidos, menú móvil nativo, selector por `translation` y paths filtrados por Jekyll; verificar navegación con teclado, cierre con Escape, foco visible y funcionamiento esencial sin JavaScript.
- [x] 2.6 Implementar el hero ES/EN y su SVG técnico original con título, descripción y fallback estático, y verificar que nombre, rol, propuesta, LinkedIn y GitHub aparecen en la primera vista sin assets o telemetría de terceros.
- [x] 2.7 Reconstruir `home.html` con impacto cualitativo, trabajo seleccionado, tres OSS, capacidades, timeline, tres posts reales, About y contacto; verificar que `/` y `/en/` contienen la misma jerarquía informativa y enlazan únicamente contenido del idioma correcto.
- [x] 2.8 Ejecutar el build de producción y comparar el inventario de rutas con el baseline; revisar además posts representativos, capturas a 390 px y 1440 px, teclado y motion reducido, y no continuar si alguna URL o contrato del blog se rompe.

## 3. Fase 2: experiencia, proyectos y About

- [x] 3.1 Crear `/experiencia/` y `/en/experience/` con front matter recíproco y contenido derivado de datos aprobados, y verificar que empleadores, períodos y aportes no se mezclan ni infieren continuidad laboral.
- [x] 3.2 Crear `/proyectos/` y `/en/projects/` con el catálogo OSS completo, y verificar los siete enlaces, el estado archivado, las fechas de métricas y la omisión de valores desconocidos.
- [x] 3.3 Actualizar About ES/EN sobre `/about/` y `/en/about/`, retirar widgets externos de estadísticas que contradigan el snapshot versionado y verificar que se conserva el tono humano y la equivalencia de idioma.
- [x] 3.4 Reutilizar includes de proyecto, experiencia o artículo solo donde home y páginas interiores repitan markup, y verificar que el build no duplica contenido ni introduce un sistema de componentes sin consumidores reales.
- [x] 3.5 Ejecutar build y revisión responsive/teclado de las cuatro páginas nuevas o actualizadas, y verificar que todas están enlazadas desde la navegación sin cambiar las rutas previas.

## 4. Fase 3: blog, metadatos y descubrimiento

- [x] 4.1 Adaptar `post.html` y estilos de artículo a la identidad editorial manteniendo el front matter actual, y verificar posts con hero, TOC, código, tablas/listas, imágenes, premonitions y lazy YouTube sin editar sus cuerpos Markdown.
- [x] 4.2 Unificar el include de `<head>` para páginas y artículos con fallback a `site.description`, canonical absoluto, Open Graph y `hreflang` condicional, y verificar HTML generado de una home, una página interior y un par de posts traducidos.
- [x] 4.3 Actualizar `_config.yml` con descripción profesional verificable y datos públicos confirmados, omitir contacto personal no aprobado y verificar que feed y metadatos no exponen `hola@logico.com.ar` como email laboral.
- [x] 4.4 Añadir JSON-LD `Person` mínimo solo con datos confirmados y verificar con un validador de datos estructurados que nombre, rol y `sameAs` no contienen credenciales ni afirmaciones inventadas.
- [x] 4.5 Ejecutar builds con `baseurl` vacío y de prueba, y verificar CSS, imágenes, navegación, canonical, alternates, `feed.xml` y URLs de posts en ambos resultados antes de añadir cualquier mecanismo de sitemap.

## 5. Fase 4: calidad y entrega

- [x] 5.1 Comparar el inventario final con el baseline y verificar que todas las URLs existentes permanecen; documentar y probar redirect solo si una diferencia fue aprobada como inevitable.
- [x] 5.2 Verificar 360, 390, 768, 1024, 1440 y 1920 px, zoom 200%, ausencia de overflow y conservación del contenido móvil, y guardar capturas representativas de home, proyecto y artículo.
- [x] 5.3 Ejecutar una revisión WCAG 2.2 AA de contraste, landmarks, headings, nombres accesibles, alt text, foco, teclado y motion reducido, y corregir cada incumplimiento reproducible antes de cerrar la fase.
- [x] 5.4 Ejecutar una medición local de LCP, CLS e INP o su proxy disponible, registrar resultados como laboratorio sin afirmar cumplimiento de campo y corregir únicamente regresiones atribuibles al rediseño.
- [x] 5.5 Auditar el output y los assets por secretos, datos privados, contacto no aprobado, detalles laborales sensibles y licencias; verificar además que no hay llamadas runtime bloqueantes a GitHub ni activos copiados de Palantir.
- [x] 5.6 Ejecutar el build final equivalente a GitHub Pages, comprobar enlaces principales ES/EN, feed y 404, y entregar un resumen de archivos, comandos, decisiones editoriales pendientes y URLs migradas.

## Workflow follow-up

- Archivar el cambio cuando la implementación y la revisión editorial estén aprobadas.
