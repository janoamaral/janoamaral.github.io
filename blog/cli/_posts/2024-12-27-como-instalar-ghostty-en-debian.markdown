---
layout: post
title: "Compilar Ghostty en Debian"
intro: 'Ghostty es un nuevo terminal emulator escrito en Zig que fue lanzado
hace días nomás. Ya sea porque te gusta compilar los programas cómo yo o querés probarlo ya en tu
máquina con Debian (u otra distro sin paquete oficial), acá esta el tutorial para hacerlo.'
date: 2024-12-27 22:29:02 -0300
categories: cli
toc: true
---

## ¿Que es Ghostty?

![](/assets/images/blog/24-12-27/slide-7.webp)

## Prerrequisitos

> warning "Zig 0.13"
> Hay que usar la versión exacta 0.13 de Zig porque de lo contrario va a fallar
> la compilación. 

[Descargar Zig = 0.13](https://ziglang.org/download/)

```bash
# Extraer archivos
tar -xvf zig-linux-x86_64-0.14.0-dev.2569+30169d1d2.tar.xz

# [Opcional] Mover los archivos extraidos
mv zig-linux-x86_64-0.14.0-dev.2569+30169d1d2.tar.xz ~/dev/jsr/zig/src

# Hacer un link simbólico del binario
ln -s "$HOME/dev/jsr/zig/src/zig" ~/.local/bin/zig
```

[Instalar las dependencias](https://ghostty.org/docs/install/build#linux-installation-tips)

```bash
sudo apt install libgtk-4-dev libadwaita-1-dev git
```
