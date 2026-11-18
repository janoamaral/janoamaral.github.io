# Design

## Context

Ver `proposal.md` para la motivación y las specs para el comportamiento requerido.

El sitio actual usa Jekyll 4.3.4, Ruby 3.4.1, Tailwind 3.4, PostCSS y un workflow propio de GitHub Pages. `default.html` concentra shell, sidebar y navegación; `home.html` contiene copy duplicado ES/EN y lista cinco posts; `post.html` soporta hero, TOC y contenido Markdown. Las home son `/` y `/en/`; About usa `/about/` y `/en/about/`. Los posts ES derivan su URL de categoría/fecha/slug y los EN declaran `permalink`, con `translation` recíproca.

El build `JEKYLL_ENV=production bundle exec jekyll build` funciona y genera el feed. El build local sin entorno de producción falla al conectar con el servidor de `jekyll-postcss`; además, Jekyll advierte que `paginate` está configurado sin `jekyll-paginate`. La implementación debe aclarar el flujo local y eliminar configuración inerte antes que añadir un plugin no usado.

## Goals / Non-Goals

**Goals:**

- Mantener una única publicación Jekyll estática con contenido profesional ES/EN y posts existentes.
- Separar contenido estructurado, presentación compartida y cuerpos editoriales para reducir duplicación sin crear un design system genérico.
- Permitir que claims sensibles permanezcan en datos de trabajo sin renderizarse hasta su aprobación explícita.
- Hacer la primera entrega desplegable con home, shell compartido y blog intacto antes de ampliar páginas interiores.
- Poder comparar el inventario de URLs antes y después del rediseño.

**Non-Goals:**

- Migrar de Jekyll, actualizar versiones mayores o introducir una SPA.
- Traducir automáticamente posts, consumir GitHub en runtime o automatizar métricas en esta entrega.
- Crear un CMS, filtros de proyectos, theme switcher, formulario de contacto, descarga de CV o biblioteca de componentes general.
- Publicar claims laborales, emails, capturas o activos cuya autorización siga pendiente.
- Replicar Palantir o Lógico pixel a pixel.

## Decisions

### 1. Mantener Jekyll, Tailwind y el pipeline existente

La implementación conservará `Gemfile.lock`, `package-lock.json`, plugins y workflow salvo una corrección mínima demostrablemente necesaria. El CSS seguirá entrando por `assets/css/style.css` y PostCSS. Se documentará el comando de build de producción que ya funciona y el flujo local requerido por `jekyll-postcss`.

Alternativas descartadas: migrar a React/Next/Astro aumenta superficie y riesgo de URLs; actualizar Tailwind/Jekyll no aporta comportamiento del rediseño; añadir `jekyll-paginate` solo para silenciar una advertencia es innecesario si ninguna plantilla pagina.

### 2. Usar front matter para identidad de página y YAML para colecciones repetidas

`index.markdown`, `index-en.markdown`, About y las nuevas páginas conservarán `lang`, `translation` y `permalink` explícitos. `_data/profile.yml`, `_data/navigation.yml`, `_data/experience.yml` y `_data/projects.yml` contendrán enlaces, labels ES/EN, experiencias y catálogo OSS. Los textos editoriales largos de cada página permanecerán en Markdown/Liquid para no convertir YAML en un CMS.

Los items sensibles tendrán un estado explícito como `approved: false`; las plantillas solo renderizarán evidencia laboral con `approved: true`. Las métricas OSS tendrán `observed_on` y campos ausentes cuando el valor no esté confirmado.

Alternativa descartada: duplicar tarjetas en cada idioma hace probable la divergencia; mover todo el copy a un único archivo de datos dificulta edición y no aporta reutilización.

### 3. Crear pocos componentes compartidos

`default.html` será el shell semántico. Se extraerán header y footer porque se usan en todas las páginas. Home mantendrá una composición propia; includes de proyecto, experiencia y artículo se crearán solo al repetirse entre home y páginas interiores. `post.html` conservará su contrato de front matter. Un layout de página interior puede añadirse si About, experiencia y proyectos comparten estructura real.

El menú móvil usará HTML nativo (`details`/`summary`) para funcionar sin JavaScript; un script corto y local solo cubrirá cierre con Escape y comportamiento de foco que el elemento nativo no garantice. No habrá bundle ni dependencia JavaScript.

Alternativa descartada: crear un sistema de componentes exhaustivo antes de encontrar repetición real añade indirection sin beneficio.

### 4. Fijar rutas nuevas y preservar las existentes

Las nuevas páginas usarán `/experiencia/`, `/proyectos/`, `/en/experience/` y `/en/projects/`. La entrada `Artículos/Writing` apuntará a la sección de artículos de la home del idioma activo durante este cambio; no se añadirá un índice de blog separado sin necesidad demostrada. `/`, `/en/`, `/about/`, `/en/about/` y todas las URLs actuales de posts quedan congeladas.

Antes de editar se guardará un inventario de URLs generado por el build actual. Tras cada fase se comparará con el nuevo build. Cualquier cambio no intencional bloquea la fase; si un cambio intencional fuera inevitable, se añadirá redirect y prueba antes de continuar.

Alternativa descartada: inferir equivalencias por `pathname` es frágil; se conservará `translation` explícita y se usará `relative_url`/`absolute_url`.

### 5. Aplicar tokens propios con CSS progresivo

Los colores, escala, gutters, ancho de lectura y motion del brief se implementarán como custom properties y extensiones mínimas de Tailwind. El fondo principal será carbón, el naranja se reservará para acciones/flujo y las superficies usarán líneas de 1 px, sin sombras pesadas ni gradientes. Home usará una grilla editorial; posts conservarán un ancho de lectura de 65-72 caracteres.

Las familias Inter Tight, Inter e IBM Plex Mono se autohospedarán únicamente si se obtienen archivos y licencias compatibles; si no, se usará la pila de sistema definida en CSS sin bloquear la entrega. `font-display: swap`, foco visible y `prefers-reduced-motion` son obligatorios.

Alternativa descartada: cargar fuentes de terceros en runtime añade dependencia, privacidad y riesgo de rendimiento; WebGL/parallax/librerías de animación no mejoran la evidencia profesional.

### 6. Renderizar un diagrama técnico original y estático primero

El hero incluirá un SVG inline original que represente un flujo técnico abstracto, con `title`, `desc` y texto alternativo equivalente. El SVG será legible sin animación; cualquier reveal será CSS y se desactivará con motion reducido. No representará telemetría, arquitectura laboral interna ni datos falsos.

Alternativa descartada: capturas propietarias y dashboards inventados crean riesgos legales y de credibilidad.

### 7. Publicar la homepage con evidencia segura por defecto

La fase 1 usará el copy profesional ES/EN, experiencia general aprobable, tres OSS con métricas fechadas y tres posts reales. Las cifras laborales de `~90 s → <1 s`, near-real-time y detalles de integraciones no se renderizarán hasta recibir aprobación explícita; la sección de impacto funcionará con descripciones cualitativas verificables.

LinkedIn y GitHub serán los únicos contactos garantizados. `hola@logico.com.ar` dejará de presentarse como contacto personal salvo confirmación posterior.

### 8. Unificar metadatos sin añadir plugins

El include de `<head>` se ajustará para distinguir páginas de artículos, usar fallback a `site.description`, canonical con `absolute_url`, Open Graph y `hreflang` solo cuando exista `translation`. `_config.yml` recibirá una descripción profesional no sensible. JSON-LD `Person` se añadirá solo con nombre, rol y `sameAs` confirmados.

Se conservará `jekyll-feed`; antes de considerar sitemap se verificará si GitHub Pages o el build ya lo producen. Los paths de CSS, imágenes y navegación pasarán por filtros Jekyll para respetar `baseurl`.

Alternativa descartada: incorporar un plugin SEO o sitemap cambia dependencias para una cantidad pequeña de metadatos que Liquid ya puede generar.

### 9. Entregar y validar por cortes desplegables

Fase 1 cambia shell, tokens, home ES/EN y componentes compartidos, pero mantiene `post.html` funcional. Fase 2 añade experiencia, proyectos y revisa About. Fase 3 adapta el blog y metadatos. Fase 4 ejecuta auditoría de rutas, accesibilidad, responsive y rendimiento. Cada fase termina con build de producción y revisión de URLs; no se acumulará una migración completa sin puntos de control.

## Risks / Trade-offs

- [Claims profesionales todavía no aprobados] → usar `approved: false`, copy cualitativo y una revisión editorial explícita antes de habilitarlos.
- [Cambiar `default.html` afecta todos los posts] → mantener primero el contrato de `post.html`, probar posts representativos con TOC, hero, premonition, código e imágenes en cada fase.
- [Tailwind no escanea todos los posts porque su `content` actual apunta a `_posts` raíz] → ampliar globs a `blog/**/_posts/*.{md,markdown}` antes de depender de clases presentes en Markdown.
- [Build local de PostCSS no es reproducible con el comando simple] → documentar/probar el comando real del plugin; no cambiar versiones salvo que el lockfile actual impida ese flujo.
- [Fuentes autohospedadas aumentan peso] → usar solo WOFF2 necesarios, preload selectivo y fallback de sistema; omitirlas si licencia o archivos no están confirmados.
- [Navegación extensa en móvil] → usar menú nativo pequeño y comprobar teclado, Escape, foco, zoom 200% y ausencia de overflow.
- [Datos YAML bilingues pueden quedar incompletos] → validar que cada item publicado tenga labels/resúmenes de ambos idiomas o un fallback editorial explícito.
- [La analítica Matomo actual es una dependencia externa] → conservarla inicialmente para evitar un cambio no solicitado, pero verificar que no bloquee render ni incluya datos sensibles.
- [Las métricas OSS envejecen] → mostrar siempre `observed_on`; actualizar el snapshot solo mediante cambio versionado y revisado.

## Migration Plan

1. Capturar build de producción e inventario de rutas actual; registrar advertencias conocidas y posts representativos.
2. Introducir datos verificados, tokens, shell/header/footer y home ES/EN. Mantener cifras laborales no aprobadas deshabilitadas.
3. Construir y comparar rutas; revisar 390 px y 1440 px, teclado, contraste y motion reducido. Publicar este corte solo si el blog sigue intacto.
4. Añadir páginas de experiencia/proyectos ES/EN y actualizar About sobre sus permalinks actuales.
5. Aplicar estilos editoriales al layout de posts y unificar metadatos sin alterar cuerpos ni front matter de URLs.
6. Ejecutar build con y sin `baseurl`, comprobar feed, enlaces, rutas, zoom y viewports objetivo; documentar cualquier redirect.
7. Revertir por fase mediante el control de versiones si falla una garantía. Como no hay migración de datos ni backend, el rollback consiste en restaurar templates, datos y assets del último corte válido.

## Open Questions

- Confirmar antes de publicación si se autoriza mostrar las cifras laborales detalladas y el estado actual de Taggify; hasta entonces permanecerán ocultos.
- Confirmar si existe un email personal o CV aprobado para publicar; hasta entonces el contacto será LinkedIn y GitHub.
- Confirmar licencia y activo concreto para una captura de Tokyo Night Tmux; si no se valida, la ficha usará composición tipográfica sin captura.
