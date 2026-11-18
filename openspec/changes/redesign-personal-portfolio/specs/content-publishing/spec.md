# Spec Delta

## Purpose

Define las garantías de publicación estática, compatibilidad de contenido, navegación bilingue, metadatos y estabilidad de URLs que el sitio Jekyll debe mantener durante el rediseño.

## ADDED Requirements

### Requirement: URLs públicas estables
El rediseño MUST conservar las URLs públicas existentes de home, About y artículos; una URL que deba cambiar MUST mantener compatibilidad mediante una redirección verificable.

#### Scenario: Rutas base existentes
- **WHEN** se genera el sitio rediseñado
- **THEN** `/`, `/en/`, `/about/` y `/en/about/` continúan resolviendo al contenido correspondiente

#### Scenario: Artículo existente
- **WHEN** se solicita cualquiera de las URLs generadas actualmente desde categorías, fecha, slug o `permalink`
- **THEN** se entrega el mismo artículo y lenguaje sin error 404 ni cambio silencioso de canonical

#### Scenario: Cambio inevitable de URL
- **WHEN** una página pública adopta una ruta nueva
- **THEN** la ruta anterior redirige a la nueva y la migración queda registrada

### Requirement: Páginas profesionales navegables
El sitio MUST ofrecer páginas ES y EN para experiencia y proyectos, además de las home y About existentes, mediante rutas declaradas y enlazadas desde la navegación principal.

#### Scenario: Navegación española
- **WHEN** una persona usa la navegación en español
- **THEN** puede abrir Inicio, Experiencia, Proyectos, Artículos, Sobre mí y Contactar sin cambiar involuntariamente de idioma

#### Scenario: Navegación inglesa
- **WHEN** una persona usa la navegación en inglés
- **THEN** puede abrir Home, Experience, Projects, Writing, About y Get in touch sin cambiar involuntariamente de idioma

### Requirement: Compatibilidad del contenido del blog
El layout de artículos MUST seguir renderizando Markdown, fechas, hero images, bloques de código, tablas, listas, imágenes, TOC, premonitions y embeds ya usados por el contenido existente.

#### Scenario: Artículo con TOC y hero
- **WHEN** se genera un post con `toc: true` y `hero`
- **THEN** muestra fecha, título, introducción, imagen, tabla de contenidos y cuerpo sin perder jerarquía ni enlaces

#### Scenario: Artículo técnico antiguo
- **WHEN** se genera un post que contiene bloques especiales, código, imágenes o lazy YouTube
- **THEN** esos elementos siguen siendo legibles, accesibles y funcionales sin modificar el cuerpo Markdown

### Requirement: Selección real de artículos
Las home MUST mostrar tres artículos reales del idioma activo, elegidos por front matter o recencia, usando sus títulos, fechas, extractos y URLs existentes.

#### Scenario: Artículos en español
- **WHEN** se genera la homepage española
- **THEN** cada preview corresponde a un post no inglés existente y enlaza a su URL real

#### Scenario: Artículos en inglés
- **WHEN** se genera la homepage inglesa
- **THEN** cada preview corresponde a un post inglés existente y enlaza a su `permalink` real

### Requirement: Navegación accesible y resiliente
El header MUST funcionar en escritorio y móvil con teclado, foco visible y semántica correcta; el contenido y enlaces esenciales MUST permanecer disponibles sin JavaScript.

#### Scenario: Menú móvil
- **WHEN** una persona abre y cierra el menú móvil con teclado
- **THEN** el estado se comunica, Escape lo cierra, el foco queda controlado y los destinos siguen siendo accesibles

#### Scenario: JavaScript no disponible
- **WHEN** JavaScript no carga o está desactivado
- **THEN** el contenido principal, navegación esencial, selector de idioma y enlaces de proyecto siguen visibles o tienen una alternativa HTML funcional

### Requirement: Metadatos por página
Cada página indexable MUST publicar título, descripción verificable, canonical absoluto, idioma, Open Graph y alternates `hreflang` solo para equivalencias reales.

#### Scenario: Página profesional bilingue
- **WHEN** una página tiene contraparte ES/EN declarada
- **THEN** ambas versiones emiten canonical propio y alternates recíprocos con URLs absolutas correctas

#### Scenario: Página sin traducción
- **WHEN** una página no tiene contraparte editorial
- **THEN** no emite un `hreflang` hacia contenido inexistente o no equivalente

#### Scenario: Datos estructurados
- **WHEN** se publica JSON-LD de tipo `Person`
- **THEN** contiene únicamente datos públicos confirmados y enlaces oficiales de GitHub y LinkedIn

### Requirement: Feed y descubrimiento conservados
El rediseño MUST conservar la generación del feed existente y MUST evitar duplicados indexables o entradas rotas por idioma.

#### Scenario: Build de producción
- **WHEN** Jekyll genera el sitio con el entorno de producción
- **THEN** produce `feed.xml` con enlaces válidos a los posts publicados

#### Scenario: Sitemap existente
- **WHEN** el repositorio ya genera un sitemap mediante configuración o plataforma
- **THEN** el rediseño lo valida antes de añadir otro mecanismo o plugin

### Requirement: Build reproducible con el stack existente
El sitio MUST compilar con las versiones fijadas de Jekyll, Ruby, plugins, Node, Tailwind y PostCSS, sin una actualización mayor ni un framework SPA como efecto colateral.

#### Scenario: Build equivalente a CI
- **WHEN** se instalan dependencias bloqueadas y se ejecuta `JEKYLL_ENV=production bundle exec jekyll build`
- **THEN** el build termina correctamente y genera las páginas, posts, CSS y feed esperados

#### Scenario: Desarrollo local
- **WHEN** se ejecuta el flujo de desarrollo documentado
- **THEN** PostCSS está disponible y Jekyll puede generar o servir el sitio sin depender de pasos implícitos desconocidos

### Requirement: Enlaces compatibles con baseurl
Los enlaces internos y assets MUST respetar la configuración Jekyll para funcionar tanto en la URL raíz como con el `base_path` proporcionado por GitHub Pages.

#### Scenario: Build con base path
- **WHEN** CI ejecuta Jekyll con un `baseurl` no vacío
- **THEN** navegación, CSS, imágenes, canonical y enlaces internos apuntan a ubicaciones válidas

### Requirement: Rendimiento sin dependencias bloqueantes
El sitio MUST renderizar su contenido estático sin consultar APIs externas en cada visita y MUST evitar efectos que bloqueen lectura, interacción o carga principal.

#### Scenario: Métricas OSS
- **WHEN** una página muestra métricas de GitHub
- **THEN** usa un snapshot versionado con fecha y no bloquea el render consultando la API de GitHub desde el navegador

#### Scenario: Visual técnico
- **WHEN** una animación o diagrama interactivo no puede ejecutarse
- **THEN** permanece visible una versión estática informativa y accesible

### Requirement: Publicación segura
El sitio MUST excluir secretos, datos privados, contacto no aprobado y detalles confidenciales de empleadores o terceros.

#### Scenario: Revisión previa a publicación
- **WHEN** se prepara el build final
- **THEN** los datos, assets y enlaces públicos no incluyen tokens, infraestructura interna, capturas no autorizadas ni información personal no confirmada
