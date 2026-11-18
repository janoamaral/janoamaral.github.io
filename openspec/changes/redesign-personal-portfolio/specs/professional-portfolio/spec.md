# Spec Delta

## Purpose

Define cómo el sitio presenta de forma bilingue, verificable y accesible la identidad profesional, experiencia, trabajo open source y vías de contacto de Alejandro Amaral.

## ADDED Requirements

### Requirement: Posicionamiento profesional inmediato
La homepage MUST identificar a Alejandro Amaral como Software Engineer y Tech Lead con más de 15 años de experiencia, y MUST priorizar su contratación profesional sobre la oferta comercial de Lógico.

#### Scenario: Primera vista de la homepage
- **WHEN** una persona abre la homepage en español o inglés
- **THEN** puede ver el nombre, rol, propuesta de valor y enlaces a LinkedIn y GitHub sin navegar a otra página

#### Scenario: Afiliación con Lógico
- **WHEN** la homepage menciona a Lógico
- **THEN** lo presenta como afiliación secundaria y no como identidad principal ni catálogo de servicios

### Requirement: Homepage profesional completa
Cada homepage MUST ofrecer hero, impacto, trabajo seleccionado, open source, capacidades, experiencia, artículos, about y contacto en un orden de lectura equivalente entre idiomas.

#### Scenario: Contenido en escritorio
- **WHEN** una persona recorre la homepage en un viewport de escritorio
- **THEN** encuentra todas las secciones requeridas y puede acceder a experiencia, proyectos, artículos, About y contacto

#### Scenario: Contenido en móvil
- **WHEN** una persona recorre la homepage en un viewport de 360 a 390 px
- **THEN** recibe la misma información y enlaces importantes sin contenido oculto por razones estéticas ni desplazamiento horizontal

### Requirement: Contenido profesional bilingue
La interfaz y el contenido profesional MUST tener versiones editoriales ES y EN coherentes, con enlaces de idioma a la página equivalente cuando exista.

#### Scenario: Cambio de idioma con equivalente
- **WHEN** una persona activa el selector de idioma desde una página con traducción declarada
- **THEN** llega a la versión equivalente y el documento declara el idioma correcto

#### Scenario: Artículo sin traducción
- **WHEN** un artículo no tiene una traducción editorial existente
- **THEN** el sitio conserva el artículo original y no publica una traducción automática como contenido revisado

### Requirement: Evidencia laboral publicable
El sitio MUST publicar únicamente roles, resultados, cifras, nombres y detalles laborales aprobados; cualquier dato pendiente MUST omitirse o mostrarse sin la afirmación sensible.

#### Scenario: Métrica aprobada
- **WHEN** una cifra de impacto cuenta con aprobación editorial y de confidencialidad
- **THEN** se muestra con contexto, intervención y atribución suficientes para no presentarla como garantía independiente

#### Scenario: Métrica no aprobada
- **WHEN** una cifra o detalle laboral no cuenta con aprobación
- **THEN** el sitio omite el dato específico y conserva una descripción general verificable o anonimizada

### Requirement: Experiencia profesional diferenciada
El sitio MUST distinguir claramente la experiencia de Taggify, Municipalidad de Bolívar y Lógico, con fechas verificadas y sin atribuir trabajo de un empleo a otro.

#### Scenario: Timeline publicado
- **WHEN** una persona consulta la experiencia
- **THEN** ve empleador, rol, período confirmado y aportes aprobados sin mezclar propiedad, clientes ni resultados entre organizaciones

#### Scenario: Estado laboral no confirmado
- **WHEN** la continuidad de un rol no está confirmada al publicar
- **THEN** el sitio usa la última fecha confirmada y no infiere una relación laboral futura

### Requirement: Catálogo open source verificable
El catálogo MUST incluir los siete proyectos definidos en el brief, con repositorio exacto, resumen, tecnologías relevantes, estado y métricas solo cuando tengan valor y fecha de observación.

#### Scenario: Proyectos destacados
- **WHEN** una persona consulta la homepage
- **THEN** ve Tokyo Night Tmux, ENIAC Development Environment y VestaCP Node.js como selección editorial con enlaces reales

#### Scenario: Catálogo completo
- **WHEN** una persona consulta la página de proyectos
- **THEN** encuentra los siete proyectos, Typewriter marcado como archivado y Typewriter Vim agrupado sin doble contabilización conceptual

#### Scenario: Métrica parcial
- **WHEN** una métrica como forks no está confirmada
- **THEN** el sitio omite ese valor en lugar de asumir cero

#### Scenario: Métrica mostrada
- **WHEN** el sitio muestra estrellas o forks
- **THEN** también muestra la fecha de captura y no los describe como usuarios, instalaciones ni prueba de dominio técnico

### Requirement: Capacidades basadas en experiencia
El sitio MUST organizar tecnologías bajo capacidades de backend, datos, plataforma y developer experience, sin afirmar el mismo nivel de dominio para cada herramienta.

#### Scenario: Presentación del stack
- **WHEN** una persona consulta la sección de capacidades
- **THEN** ve decisiones y usos aplicados antes que una pared de logotipos o una lista indiscriminada

### Requirement: Contacto profesional confirmado
El sitio MUST ofrecer LinkedIn y GitHub como vías principales y MUST publicar email, teléfono, CV o disponibilidad solo si fueron confirmados para uso público.

#### Scenario: Contacto base
- **WHEN** una persona llega al hero, header o sección final de contacto
- **THEN** puede abrir el LinkedIn y GitHub oficiales mediante enlaces accesibles

#### Scenario: Email no confirmado
- **WHEN** no existe aprobación para usar un email como contacto laboral
- **THEN** el sitio no presenta `hola@logico.com.ar` ni otro email como contacto personal

### Requirement: Identidad visual propia y accesible
La experiencia MUST usar una composición editorial industrial original, mantener contraste WCAG 2.2 AA como objetivo, foco visible, semántica, teclado y una alternativa sin movimiento no esencial.

#### Scenario: Navegación por teclado
- **WHEN** una persona recorre header, menú, selector de idioma, enlaces y controles solo con teclado
- **THEN** el foco permanece visible, el orden es lógico y todos los controles se pueden activar

#### Scenario: Movimiento reducido
- **WHEN** el sistema indica `prefers-reduced-motion: reduce`
- **THEN** las animaciones no esenciales se desactivan y ningún contenido depende de JavaScript o animación para ser visible

#### Scenario: Origen de activos
- **WHEN** se incorporan tipografías, diagramas, imágenes o iconos
- **THEN** son originales o tienen licencia compatible y no copian activos, marca, código ni contenido propietario de Palantir
