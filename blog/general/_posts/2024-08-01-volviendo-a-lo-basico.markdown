---
layout: post
title: "Volviendo a lo básico"
intro: 'Después de varios años de crear blogs en diferentes tecnologías decidí volver al primer amor: Jekyll y GitHub pages.'
date: 2024-08-01 20:29:02 -0300
categories: general
toc: true
---

## Keep It Simple Stupid

Y vamos pegando la vuelta. Esta es la tercera vez que pongo un blog
personal en línea. Y el quinto intento de diseño... Después de probar Next,
vanilla JS, HTMx y visto que el tiempo es tirano, decidí volver a lo más
básico de lo básico: un sitio estático en [Jekyll][jekyllrb].

Al fin y al cabo, lo que realmente quiero es una plataforma para poder subir mi
contenido, sin ser esclavo de las redes sociales (tema para otro post).
Así que, armado con Neovim, un poco de HTML, algunas líneas de CSS y unas 4
horas para mezclar todo, acá estamos de nuevo.

Esta nueva edición del blog está orientada 100% al pragmatismo, ya no tengo
tanto tiempo cómo en otras épocas, así que ponerme a desarrollar o implementar
y mantener un sistema en mi otro servidor estaba fuera de toda duda. Por lo que
terminé decidiendo usar [GitHub pages][ghpages] para hostear el sitio.

¿Por qué GitHub pages? Primero y principal porque quería poder escribir notas en
archivos markdown sin tener que utilizar una base de datos. La versión anterior
del blog utilizaba [PocketBase][pocketbase] pero, _mea culpa_, hice sobreingeniería:
deploys automáticos, github actions, integración de analíticas, etc. El segundo
punto es que me olvido de tener que hacer backups, mantener nombres de dominios,
certificados y todo lo que trae aparejado mantener un servidor. Me parece un
buen balance entre tener control de mi información y delegar tareas en una
plataforma de un tercero.

Con el paso del tiempo iré agregando nuevas features. Reconozco que actualmante
está bastante espartano, pero _¡hey!_ al menos puedo empezar a escribir sin tener
que preocuparme por otros aspectos que no sean el contenido.

Si estás leyendo esto y no conoces sobre que escribo, entonces te doy la
bienvenida y te cuento que me gusta compartir conocimiento, opiniones, tutoriales
sobre **Linux, programación, AI, teclados y tecnología** en general.

Si ya me conocés, entonces ¡gracias por el aguante!

[jekyllrb]: https://jekyllrb.com/
[ghpages]: https://pages.github.com
[pocketbase]: https://pocketbase.io/
