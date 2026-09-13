---
layout: post
title: "Mi workstation se está convirtiendo en una terminal boba, y eso es algo bueno"
intro: 'Nueva era, viejas maneras de trabajar. Con la IA, las herramientas se han vuelto más dinámicas y cada vez tiene menos sentido que nuestro entorno de desarrollo esté atado a una máquina física.'
date: 2026-09-11 17:49:02 -0300
categories: general
toc: true
hero: /26-09-11/header.jpg
---

## La muerte digna del workstation

Desde el inicio de mi carrera profesional, el objetivo siempre fue tener el
mejor flujo de trabajo local y generar código de la manera más rápida y
eficiente posible. Terminé armando complejas configuraciones de `tmux` y `zsh`,
con un montón de _plugins_ y _aliases_ para salir lo menos posible de la
terminal. Me pasé a _Linux_ para poder personalizar el escritorio y hasta armé
—literalmente, soldé todas las partes— mi propio teclado con atajos para
depender lo menos posible del mouse y ser lo más eficiente posible.

Hace unos dos meses me di cuenta de que mi _workstation_ se estaba volviendo una
terminal boba. Y eso, lejos de preocuparme, me pareció una buena señal. Para
llevar control de versiones utilizo GitHub, la inteligencia de los agentes está
en la nube (OpenAI, Anthropic, Qwen, etc.), y mi _workstation_ es solo un punto
de acceso. Si bien el editor de código y la terminal siguen en mi máquina, todo
lo demás está en la nube.

Entonces tuve una idea: quizás la computadora que tengo enfrente ya no debería
ser el entorno de desarrollo… Quizás debería ser solo el medio a través del cual
termino accediendo a él. Y me puse a investigar qué opciones había para mover el
entorno a la nube y dejar de depender de una máquina local (infraestructura
incluida).

## La necesidad es la madre de los inventos

La primera necesidad que me surgió fue poder tener un entorno de desarrollo en
la nube, para trabajar desde cualquier lugar y con cualquier dispositivo. Pero
durante la investigación aparecieron otras, quizás secundarias, que igual me
importan:

- Poder conectarme desde cualquier máquina en cualquier momento (duh)
- Que los procesos sigan corriendo aunque apague la notebook o la _workstation_
- Poder separar diferentes proyectos en diferentes entornos, sin tener que
  preocuparme por conflictos de dependencias o configuraciones
- Darle libertad a los agentes de IA para que puedan correr comandos sin
  restricciones ([YOLO
  mode](https://www.codeagentswarm.com/en/guides/claude-code-yolo-mode-explained))
  sin miedo a que hagan un `dd if=/dev/zero of=/dev/sda` y me borren todo el
  disco
- Y si el agente realiza una acción destructiva, que no me lleve tres días
  restaurar una copia de seguridad
- Mantener una base de software estable: ocho años de Debian no se quitan fácil
- Y además, mantener todo el software relacionado con IA actualizado a las
  últimas versiones, ya que tenemos cambios todos los meses o incluso menos
- Y por último, poder mantener un grado de personalización que no sea demasiado
  intrusivo, ya que me gusta tener un entorno de desarrollo a mi gusto
- Mantener identidades y credenciales distintas para cada proyecto, y así
  separar lo personal, los pasatiempos y el trabajo

## El stack: ambiente remoto sí, escritorio remoto no

Hace un tiempo intenté hacer algo con
[Codespaces](https://docs.github.com/es/codespaces), pero en su momento no me
convenció. Quizás el precio, no la capacidad: en GitHub Pro son 180 horas de
cómputo y 20 GB. El almacenamiento ya es un chiste, pero dejando eso de lado, el
cómputo es limitado cuando tenés 160 horas solo con el trabajo y después los
proyectos personales.

En fin, volviendo al tema, el primer instinto fue contratar un VPS, instalar las
herramientas básicas, un poco de Docker aquí y allá y hacer todo ahí. Servía,
pero lo sentí como muy básico y un tiro en el pie a futuro. De hecho, era lo
mismo que venía haciendo, pero pagando un VPS y más latencia.

Así que me resistí al primer impulso y me puse a investigar un poco más. Y
encontré algo que me gustó mucho: [Coder](https://coder.com/), una plataforma de
código abierto donde los desarrolladores y los agentes de IA colaboran de forma
segura en entornos autocontenidos, utilizando mi propia infraestructura. Amor a
primera vista. Empecé a probar en una máquina virtual con plantillas y
diferentes configuraciones, y así estuve trabajando durante aproximadamente un
mes y medio.

Esto me sirvió para ver algunos problemas y descubrir qué necesidades y mejoras
hacían falta. Hace un par de semanas puse manos a la obra, junté todos los
requerimientos y, pensándolo un poco, llegué a la conclusión de que no estaba
inventando nada: la respuesta estaba frente a mis ojos.
[Omarchy](https://omarchy.org/) utiliza una máquina con Linux y la transforma en
un sistema operativo especializado para desarrolladores y agentes. Buscaba algo
conceptualmente similar, pero sin que la máquina tuviera que estar sobre mi
escritorio.

Con Omarchy: `Computadora → Omarchy → Dev OS`

Y así nació [ENIAC](https://github.com/janoamaral/coder-dev-environment), que
convierte cualquier máquina o VPS en un entorno de desarrollo. Tu código,
herramientas, configuración, estado y agentes de IA viven en un espacio de
trabajo reproducible en la nube, listo para trabajar sin importar desde dónde te
conectes.

Mi enfoque: `VPS / Remote Compute → Eniac → Remote Dev OS`

![Flujo de entorno de desarrollo](/assets/images/blog/26-09-11/infra-en.png)

Como dije, la idea es bastante simple. Estos son los ingredientes:

- Un VPS o servidor remoto con Linux
- Un playbook de Ansible para instalar y configurar todo
- Una imagen de Docker con el stack necesario para desarrollar
- Una plantilla de Coder para crear un entorno con todo listo
- El usuario trae sus configuraciones, repositorios y credenciales, y el entorno
  se despliega en la nube con todo listo para trabajar
- Opcionalmente un nombre de dominio o subdominio para acceder al entorno de
  desarrollo desde cualquier lugar con un lindo nombre y usando SSL

Con solo ejecutar Ansible y cargar la plantilla de Coder (todo incluido), ya
estás listo para trabajar. Y lo mejor es que el entorno es personalizable,
reproducible y, sobre todo, aislado. Los agentes de IA pueden correr sin miedo a
romper algo: si hay problemas, el entorno se reinicia fácilmente.

## Decisiones, decisiones... Qué tuve que dejar afuera

Como todo en ingeniería, la vida es un intercambio. En este caso, tuve que tomar
algunas decisiones para llegar a un sistema equilibrado entre funcionalidad,
seguridad y facilidad de uso. Los "sí" son fáciles: si algo está claro en las
especificaciones, generalmente alcanza. Pero en cuanto a diseño de
infraestructura, lo más complicado es decidir **qué NO automatizar**. Algunas de
las decisiones que tomé:

- **No Docker-in-Docker**: ya existía un límite de aislamiento. Agregar otro
  daemon no resolvía un problema real.
- **No usar `latest` en la imagen base**: la base debe cambiar de forma
  explícita.
- **No meter herramientas de IA en la imagen**: Codex, OpenCode, CodeGraph y
  compañía cambian demasiado rápido. Mejor inicializarlas al arrancar.
- **No resetear repos automáticamente**: si un repo existe, se preserva. La
  automatización no debería destruir trabajo local para alcanzar una supuesta
  pureza declarativa.
- **No guardar secretos en texto plano por workspace**: la identidad se
  selecciona declarativamente, pero las credenciales se materializan en tiempo
  de ejecución.

El diseño empezaba a sentirse sólido en papel. La realidad, naturalmente, tenía
otros planes.

## Lo bueno (ya lo conté), lo malo y lo feo

Todo hermoso hasta el momento. Como buen profesional, tengo que tocar estas
partes para evitar vender que el proyecto es la segunda venida de Cristo. Y la
realidad es que no todo es color de rosa.

El primer tema es la latencia, y tengo sentimientos encontrados. Primero lo
malo: lógicamente, la experiencia no es la misma cuando escribís localmente, que
cuando escribís en un servidor dentro de tu misma LAN, que en un servidor a
miles de kilómetros. En el último caso, con una conexión SSH básica, estando yo
en Argentina y el servidor en Canadá, no era la mejor experiencia. Tuneando un
poco la conexión o utilizando [Mosh](https://mosh.org/), la verdad es que es
completamente utilizable. No es nativo, pero es funcional. Y lo bueno es que la
latencia no es un problema para los agentes. Además, al ser un VPS, la velocidad
de transferencia es mucho mayor que la de mi proveedor local. Starlink es bueno,
pero no llega a los 3Gbps del server. Clonar repos se siente instantáneo, y eso
es un gran plus.

Sobre el último punto, un poco de contexto. Vivo en un área semirrural, y la
velocidad de internet es un problema. Starlink me da 300 Mbps de descarga y a
veces llego a los 100 Mbps de subida. Comparado con los 20/5Mbps que me daba el
proveedor anterior, es un sueño. Además sufro regularmente (no tanto como hace
un tiempo) de cortes de energía. Este proyecto también soluciona esos dos
problemas: no importa si me cortan todos los servicios, cualquier proceso que
haya iniciado se mantiene en el servidor remoto.

Otro tema que tengo que mencionar son los costos. Con el desarrollo local, ya
está parcialmente pagado cuando comprás la computadora o el empleador te da una.
Con el desarrollo remoto se introducen:

- Costo mensual del VPS
- Backups automáticos, si los querés
- Costo de almacenamiento: mi VPS tiene 200 GB (10x lo que ofrece Codespaces),
  más que suficiente, aunque según el proyecto puede quedarse corto

No es caro, pero ya deja de ser gratis. En total a día de hoy el costo mensual
es de $27.5 USD.

Otro tema, en la categoría de "lo feo" y quizás más psicológico: hacerte la idea
de no ser dueño de tu entorno de desarrollo. Es un cambio de paradigma, y no es
fácil.

- Estás físicamente en una infraestructura ajena
- Dependés del proveedor de VPS
- Una caída o un mantenimiento de esa infraestructura puede dejarte sin acceso a
  tu entorno
- Tenés que mantener el host agrega trabajo operacional extra. No es la muerte
  de nadie, pero es una carga más

Es cambiar control físico por comodidad y flexibilidad. Y eso no es fácil de
aceptar, pero es un cambio que vale la pena.

## Volviendo a la terminal boba, casi

Realmente no es que estoy volviendo al terminal bobo, que tranquilamente podría:
una Raspberry con un teclado y un monitor sería suficiente para trabajar. Pero
no es lo mismo. Mi máquina local sigue teniendo las herramientas de siempre,
[Ghostty](https://ghostty.org/) cómo terminal emulator, todos mis scripts y
[workflows personalizados en
tmux](https://github.com/janoamaral/tokyo-night-tmux), pero ahora los uso de
manera diferente. Mediante tuneles reverso SSH puedo compartir mi instancia de
Ollama a mis agentes de IA con la máquina remota para así ahorrar tokens en
tareas que perfectamente un modelo mucho más chico puede hacer.

Creo que por hoy lo voy a dejar acá. Para el siguiente post voy a entrar en más
detalle en la parte técnica, cómo está armado el _stack_ y cómo se puede usar.
Por ahora, si querés probarlo, podés [clonar el repositorio](https://github.com/janoamaral/ENIAC-dev-environment) y seguir las
instrucciones de instalación. Y si tenés dudas, podés escribirme por cualquier red social o
abrir un _issue_ en GitHub. Me encantaría recibir comentarios y sugerencias para
mejorar el proyecto.
