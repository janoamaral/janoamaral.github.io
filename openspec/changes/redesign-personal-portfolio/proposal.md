# Proposal

## Why

El sitio actual presenta a Alejandro principalmente como "System Analyst" y bloguero, pero no comunica con rapidez su alcance como Senior Software Engineer / Tech Lead, su experiencia en producción ni su trabajo open source. El rediseño debe mejorar esa narrativa profesional sin abandonar Jekyll, romper el contenido bilingue ni alterar las URLs publicadas.

## What Changes

- Rediseñar la experiencia visual con una dirección editorial industrial propia, oscura, accesible y responsive, inspirada sin copiar activos ni identidad de terceros.
- Reestructurar las home ES y EN para presentar posicionamiento, impacto verificable, trabajo seleccionado, OSS, capacidades, experiencia, artículos y contacto.
- Incorporar datos Jekyll bilingues para perfil, navegación, experiencia y los siete proyectos OSS, incluidas fechas de captura y estados como "archivado".
- Crear páginas ES/EN de experiencia y proyectos, y actualizar las páginas About existentes sin cambiar sus permalinks.
- Modernizar header, footer, selector de idioma, metadatos y componentes compartidos con HTML/Liquid/CSS; usar JavaScript solo cuando sea imprescindible.
- Aplicar la nueva base visual al blog conservando cuerpos Markdown, rutas, traducciones existentes, feed, TOC, bloques especiales e imágenes.
- Publicar solo hechos, métricas y detalles laborales aprobados; omitir o anonimizar material pendiente de validación editorial o de confidencialidad.
- Verificar build, rutas, enlaces, responsive, teclado, contraste, zoom y movimiento reducido antes de publicar.
- Entregar por fases: primero homepage ES/EN y componentes compartidos con el blog funcional; luego páginas interiores, blog/SEO y calidad final.

## Capabilities

### New Capabilities

- `professional-portfolio`: Presentación bilingue de identidad profesional, experiencia, impacto aprobado, capacidades, proyectos OSS y vías de contacto.
- `content-publishing`: Publicación Jekyll accesible de páginas y artículos, con navegación bilingue, URLs estables, metadatos, feed y compatibilidad con contenido existente.

### Modified Capabilities

Ninguna; el proyecto no tenía especificaciones OpenSpec previas.

## Impact

- Afecta `_config.yml`, páginas raíz ES/EN y About, layouts e includes compartidos, estilos Tailwind/PostCSS, datos Jekyll y nuevos assets propios.
- Añade páginas de experiencia y proyectos bajo rutas definitivas derivadas del build, priorizando compatibilidad con `/`, `/en/`, `/about/`, `/en/about/` y todas las URLs actuales de posts.
- Mantiene Jekyll 4.3, Tailwind 3, plugins, Ruby/Node y el workflow de GitHub Pages salvo correcciones mínimas necesarias para que el build existente sea reproducible.
- Requiere revisión editorial antes de publicar cifras de impacto laboral, estado de empleo, contacto por email, capturas o detalles de terceros.
- No introduce SPA, consumo runtime de GitHub, traducción automática de artículos, librerías de animación ni activos de Palantir.
