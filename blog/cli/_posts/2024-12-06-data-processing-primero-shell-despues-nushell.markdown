---
layout: post
lang: es
translation: /en/blog/cli/2024/12/05/data-processing-first-shell-after-nushell.html
title: "Data processing primero, shell después: Nushell"
intro: 'Hace un par de años me enteré de esta herramienta que sinceramente no
logró cautivarme cómo para reemplazar mi Zsh. No fue sino hasta
ayer nomás que finalmente entendí su verdadero poder: data processing'
date: 2024-12-05 20:29:02 -0300
categories: cli
toc: true
---

## Nushell no es Zsh

Como desarrollador con años de experiencia trabajando en entornos de línea de
comandos, siempre ando buscando maneras y herramientas para poder mejorar mi
productividad. Es así que hace un par de años me encuentro con
[Nushell](https://nushell.sh), una shell desarrollada en Rust, ultra rápida que
tenía una linda sintaxis para manejar datos... Hype de por medio, procedo a
compilarlo y a tratar de migrar mi configuración de Zsh.

Primer error: **Nushell no es POSIX**. Algunas funcionalidades y comportamientos 
de los comandos diferían de lo que estaba acostumbrado en Zsh. Tras varios
intentos de adaptación, decidí volver a mi shell habitual. Hasta ayer.

## Cambio de paradigma: procesamiento de datos primero

Necesitaba procesar y cruzar datos de diferentes fuentes en archivos CSV y JSON.
Mi primir instinto cuando se refieren a este tipo de tareas es agarrar y tratar
de hacer un one-liner con Bash, si eso no funciona, script en Bash y finalmente
hacer un script en Python y a otra cosa. Sin embargo, esta vez el one-liner lo
hice en Nushell. ¡Vaya sorpresa que me lleve!

Primero que nada, en lugar de manejar cadenas de texto cómo lo hacen los
intérpretes de comandos convencionales, Nushell trabaja con tablas y objetos estructurados. Esto quiere
decir que podés realizar operaciones complejas sobre cualquier tipo de dato
estructurado cómo si fuese una base de datos. Pero desde la línea de comando.
Una locura.

Ahí tuve un momento de iluminación: no estás simplemente construyendo pipes de
texto, estás manipulando estructuras de datos organizadas 🤯.

![Neo sayung kung fu](https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExMGV2eW16aTVvNDJ2czVlejlhbWxsNGg2OWYwdjZ5OXdoMDUzazZzbiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7btNhMBytxAM6YBa/giphy.gif)

No sólo archivos estructurados también salidas _normales_ cómo `ls` pueden ser
tratadas cómo tablas. Por ejemplo en vez de ejecutar `ls -lh | awk '{print $9"\t"$5}'`
para tener una tabla de nombre de archivo y su correspondiente tamaño, en
Nushell se traduce a `ls -la | select name size`

![](/assets/images/blog/24-12-06/2024-12-06_18-34-15.png)

## Ventajas que marcan la diferencia

**Procesamiento de Datos Estructurados**

Nushell maneja datos estructurados en forma de tablas y objetos JSON. Esto facilita tareas como:

- Filtrar datos de forma precisa.
- Convertir formatos (CSV, JSON, YAML, etc.) sin herramientas externas.
- Explorar y transformar datos tabulares con una sintaxis legible y concisa.

**Conexión natural con APIs y herramientas modernas**

Seguro que si estás leyendo esto es porque regularmente te toque trabajar con
APIs REST y formatos cómo JSON. Nushell es un placer

```Bash
http get https://restcountries.com/v3.1/all?fields=name | get name | select common nativeName | sort | first 3
```

No es necesario `cURL` o `wget` ni acordarse de la sintaxis de `jq`, esta shell
se encarga de todo.

**Integración intuitiva con otras herramientas**

Nushell mantiene las funcionalidades básicas de un intérprete, como navegar por directorios, 
ejecutar comandos del sistema y manejar procesos. Sin embargo, extiende estas 
capacidades con comandos integrados que entienden el contexto de los datos, 
mejorando significativamente la experiencia. Así que no hay demasiado problema
si querés usar `jq` en vez de los comandos nativos.

**Documentación clara y comunidad activa**

Para los desarrolladores que buscamos eficiencia, Nushell ofrece documentación 
bien estructurada y una comunidad activa, lo que nos acelera la curva de aprendizaje 
y ayuda a la adopción.

## ¿Zsh o Nushell? Ambos

Nushell es una herramienta para procesar datos primero y un shell después. Esto 
significa que podés usar Nushell para realizar tareas complejas de procesamiento 
de datos como: análisis, manipulación y visualización de datos.

En mi caso en particular voy a continuar usando Zsh pero cada vez que tenga que
procesar información voy a usar esta herramienta cómo primera opción. Y quien dice
¿que tal que termine por adoptarla cómo shell principal? 

Si estás acostumbrado a usar intérpretes tradicionales como Bash o Zsh, es posible 
que necesites un poco de tiempo para adaptarte a Nushell. Sin embargo, 
una vez que te hayas acostumbrado, vas a encontrar que es una herramienta 
valiosa que podés usar para una variedad de tareas.


