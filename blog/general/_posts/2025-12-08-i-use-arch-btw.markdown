---
layout: post
title: "I use Arch, btw"
intro: 'Finalmente me armé de tiempo y decidí migrar todo mi workflow a Arch. Mi experiencia de migrar a Arch Linux (y Wayland) tras 8 años en Debian.'
date: 2025-12-08 20:29:02 -0300
categories: general
toc: true
hero: /25-12-08/header.jpg
---

## Mi historia con Debian
Mi historia en Linux comienza con Fedora Core 3 y un poco de Solaris 10 allá por
el año 2005. Al muy poco tiempo empecé a hacer distro hopping cómo cualquier hijo 
de vecino. Ya para 2010 me había asentado bastante en Ubuntu por los siguientes 7/8 años.
En el pasar de ese tiempo ya sentía que el sistema operativo debía ser más
personalizado a mi gusto, sin que el distribuidor pusiera paquetes que yo nunca
iba a utilizar. Cómo ya había ganado bastante experiencia en la gestión de
servidores un buen día decidí una instalación mínima de Debian e instalar todos los
paquetes que iba a utilizar. Es a partir de aquí que empiezo a crear scripts,
programas y atajos de teclado que se adapten a mis necesidades.

Y así pasaron 8 años. Sólo reinstalé una vez, que fue cuando renové la
computadora.

## Los problemas de Debian

Debian es un sistema súper sólido, de eso nadie puede quejarse. Pero viene con
el problema aparejado que el software generalmente también es viejo: la única
manera de confirmar la robustez es el tiempo. Una manera que encontré para poder
tener lo mejor de los dos mundos (solidez y software actualizado) fue la de
compilar desde código fuente todos los programas que necesitara tenerlos
actualizados: alacritty, ghostty, tmux, nvim, etc. Y por un tiempo funcionó.

Creé un repositorio y mediante scripts automaticé todo el proceso _a la_ [OpenBSD
ports](https://www.openbsd.org/faq/ports/ports.html). El problema apareció
con la revolución AI. Quería probar modelos o proyectos y generalmente
necesitaban librerías del sistema actualizadas. La alternativa que encontré fue
moverme a la [rama inestable (Sid)](https://wiki.debian.org/DebianUnstable). Pero aún así
a veces no era suficiente y otras veces llegué a romper el sistema. Nada que no
pudiera solucionar, pero era algo que me estaba molestando.

## El milagro Nvidia

## Chau X11, hola fluidez

## Uptime: 100%
