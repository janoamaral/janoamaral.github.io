---
layout: post
lang: es
translation: /en/blog/general/2025/12/08/i-use-arch-btw.html
title: "I use Arch, btw"
intro: 'Finalmente me armé de tiempo y decidí migrar todo mi workflow a Arch. Mi experiencia de migrar a Arch Linux (y Wayland) tras 8 años en Debian.'
date: 2025-12-08 20:29:02 -0300
categories: general
toc: true
hero: /25-12-08/header.jpg
---

## Mi historia con Debian
Mi historia en Linux comienza con Fedora Core 3 y un poco de Solaris 10 allá por
el año 2005. Al muy poco tiempo empecé a hacer distro hopping como cualquier hijo 
de vecino. Ya para 2010 me había asentado bastante en Ubuntu por los siguientes 7/8 años.
Con el tiempo, sentía que el sistema operativo debía ser más
personalizado a mi gusto, sin que el distribuidor pusiera paquetes que yo nunca
iba a utilizar. Cómo ya había ganado bastante experiencia en la gestión de
servidores un buen día decidí una instalación mínima de Debian e instalar todos los
paquetes que iba a utilizar. Es a partir de aquí que empiezo a crear scripts,
programas y atajos de teclado que se adapten a mis necesidades.

Y así pasaron 8 años. Sólo reinstalé una vez, que fue cuando renové la
computadora.

## Los problemas de Debian
Debian es un sistema súper sólido, de eso nadie puede quejarse. Pero eso
conlleva un problema inherente: el software generalmente también es viejo ya que la única
manera de confirmar la robustez es, precisamente el paso del tiempo. Una manera que encontré para poder
tener lo mejor de los dos mundos (solidez y software actualizado) fue la de
compilar desde código fuente todos los programas que necesitara tenerlos
actualizados: alacritty, ghostty, tmux, nvim, etc. Y por un tiempo funcionó.

Creé un repositorio y mediante scripts automaticé todo el proceso _a la_ [OpenBSD
ports](https://www.openbsd.org/faq/ports/ports.html). El problema apareció
con las nuevas demandas de los proyectos de inteligencia artificial. Quería probar modelos o proyectos y generalmente
necesitaban librerías del sistema actualizadas. La alternativa que encontré fue
moverme a la [rama inestable (Sid)](https://wiki.debian.org/DebianUnstable). Pero aún así
a veces no era suficiente y otras veces llegué a romper el sistema. Nada que no
pudiera solucionar, pero era algo que me estaba molestando.

## Derrumbando mitos
Tengo que confesar que tenía mis prejuicios con Arch. Algunos fundados (sistema
inestable) y otros totalmente infundados (dificultad para instalar). El segundo
mito quizás fue el que más retrasó la migración ya que no me gusta perder tiempo
en cosas que no valen la pena. Sobre la estabilidad voy a hablar más adelante.

Después de ver un par de videos de
instalación de Arch y [Omarchy](https://omarchy.org) en particular, me dí cuenta que no es muy
diferente a instalar Debian. Si bien no uso Omarchy, la instalación base del
sistema operativo es igual. Acá está cómo instalarlo en el caso de
querer hacer la prueba.

<a href="https://youtu.be/6YJImMYKefk" class="lazy-youtube-embed">Omarchy Install</a>

La instalación fue tremendamente fácil y rápida. Cómo debe ser. En una
instalación nueva no debería haber ningún tipo problema. En mi caso, tengo también
una instalación de Windows 10 (que se actualizó automagicamente a 11 🤮)...
Pero cómo ya he tenido varias malas experiencias, tengo los sistemas
separados en distintos discos y la partición `/home` también se encuentra separada en otro
disco. De esta manera no corro riesgo de borrar algo que no debería. Así que
supongo que parte de esa simpleza puede venir porque tenía todo ordenado.

## El milagro Nvidia
Lo que más me sorprendió de la instalación fue que me dejara instalar los drives
privativos de Nvidia directamente. Quizás sea porque en Debian son bastante
celosos respecto a drivers que no sean open source, pero siempre me costó
instalarlo. Que DKMS, que los headers del kernel, etc, etc... Pero en Arch fue
sumamente fácil. Elegir el modelo de driver correspondiente a mi gráfica y
listo. Instaló todos los drivers y configuró el kernel correctamente (beso de
chef).

## Chau X11, hola fluidez
Desde que instalé la versión mínima de Debian que empecé a utilizar tiling
windows managers. Pasé por [i3](https://i3wm.org/), [dwm](https://dwm.suckless.org/) 
y finalmente me asenté en [bspwm](https://wiki.archlinux.org/title/Bspwm_(Espa%C3%B1ol)).
Todos estos corriendo sobre X11. Cómo también hace un tiempo quería ver que tal
funciona Wayland me decidí por instalar [Hyprland](https://hypr.land/).

La verdad que en este tiempo que llevo usándolo me voló la cabeza. Todo funciona
mucho más rápido. El [navegador Zen](https://zen-browser.app/) que tenía problemas de 
performance en YouTube de repente parece un fork de Chrome (si es que sirve la
comparativa). Otra cosa fue el screen tearing... Después de años de luchar sin
resultado favorable con la configuración de Compton (un compositor de X11) por
fin los videos renderizan sin ningún tipo de artefacto.

![Zen Browser](https://zen-browser.app/_astro/ComImage.DV0rTSHO_BBUc2.webp)

## Uptime: 100%
¿Lo mejor de todo? Todo el proceso de instalación no me llevó más de media hora
de un domingo y migrar todos los atajos algunas horas más. Sólo porque le
dedique tiempo a mejorar algunos scripts que venia procrastinando.

En conclusión: después de 3 semanas de zarpar a nuevos mares, me encuentro más a
gusto que nunca. Todo funciona cómo quiero y no he tenido ningún problema con
nada. Definitivamente tendría que haber tomado la decisión antes, pero ¡hey!
nunca es tarde. 
