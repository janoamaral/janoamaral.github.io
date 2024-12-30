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

Ghostty es un terminal emulator creado por Mitchell Hashimoto (tal vez lo
conozcan por HashiCorp) cómo proyecto personal. Los puntos más importantes:

- **Es nativo**: está diseñado para que sea buildeado nativamente para cada
  plataforma, usando Swift y AppKit para macOS y Zig con GTK4 para Linux. Esto
  permite que se integre naturalmente con las funcionalidades del propio sistema
  operativo, incluyendo atajos de teclado, UI y caracteristicas específicas del
  OS.
- **Funcionalidades**: ofrece features tanto a nivel de terminal (como el protocolo
  gráfico Kitty, notificaciones, hyperlinks, etc) cómo a nivel de aplicación:
  pestañas nativas, split screen y drop-down terminal tipo Quake, etc.
- **Rápido**: Busca estar al nivel de terminales ultra rápidas cómo Alacritty, para
  esto se vale de renderizado en la GPU y el lenguaje de programación Zig.

![ghostty slide](/assets/images/blog/24-12-27/slide-7.webp)

## Prerrequisitos

Ghostty al estar programado en Zig necesita que si o si tengas su compilador
instalado en tu máquina. En el sitio oficial recomiendan utilizar `Nix` cómo
ambiente de desarrollo/build oficial, pero la verdad que instalar Zig es muy
fácil y además, ya que está, queda disponible por si tenemos ganas de trastear con el
lenguaje más adelante.

> warning "Zig 0.13"
> Hay que usar la versión exacta 0.13 de Zig porque de lo contrario va a fallar
> la compilación. Intenté con la versión más nueva y falló...

Puedes usar este link para ir la página de descarga de [Zig
0.13](https://ziglang.org/download/) o correr este comando:

```bash
curl -O 'https://ziglang.org/builds/zig-linux-x86_64-0.14.0-dev.2571+01081cc8e.tar.xz'
```

Una vez descargado hay que extraer el archivo `tar` y poner el binario en un
directorio que esté dentro del `$PATH` de tu sistema. En mi caso en particular
tengo a `~/.local/bin/` en mi `$PATH`, entonces voy a usar ese directorio. Si lo
quieres tener disponible para todos los usuarios puedes hacer el link simbólico
a `/usr/bin/`.

En cuanto al directorio donde muevo el binario es porque tengo un [repositorio de código fuente](https://github.com/janoamaral/jsr)
inspirado en [FreeBSD src tree](https://cgit.freebsd.org/src/about/) donde tengo scripts para mantener y buildear
software desde el código fuente. Es un tema para otro post, pero es importante
saber para despejar dudas. En tu caso puedes mover los directorios a donde más
te guste.

```bash
# Extraer archivos
tar -xvf zig-linux-x86_64-0.14.0-dev.2569+30169d1d2.tar.xz

# [Opcional] Mover los archivos extraidos
mv zig-linux-x86_64-0.14.0-dev.2569+30169d1d2.tar.xz ~/jsr/zig/src

# Hacer un link simbólico del binario
ln -s "$HOME/jsr/zig/src/zig" ~/.local/bin/zig
```

> info "Links simbólicos"
> En esta guía utilizo mucho los links simbólicos porque vamos a tener la
> ventaja que una vez que esté todo instalado, para actualizar Ghostty sólo va a
> ser cuestión de hacer un `pull` del repositorio y volver a compilar para que
> todo se actualice al mismo tiempo.

Realmente no necesita mucho más requisitos instalados. En el caso que estés usando otra distro
puedes ver más [requisitos en la página oficial](https://ghostty.org/docs/install/build#linux-installation-tips).
Para Debian con sólo correr el siguiente comando es suficiente.

```bash
sudo apt install libgtk-4-dev libadwaita-1-dev git
```

Ahora sólo queda descargar el repo:

```bash
git clone https://github.com/ghostty-org/ghostty.git
```

## Compilación

Llegado a este punto debería ser bastante sencillo compilar Ghostty. Sólo hay
que moverse al directorio del código y buildear

```bash
# Moverse al directorio con el código
cd ghostty

# Buildear
zig build -Doptimize=ReleaseFast
```

Según las caracteristicas de tu máquina (CPU, RAM, etc) puede tardar unos segundos o varios
minutos. Una vez finalizado el proceso, vamos a encontrar los binarios en el
directorio `zig-out/bin/ghostty`. También es necesario saber que hay un directorio
llamado `dist` que va a ser importante en el siguiente paso. Por lo pronto la
estructura quedaría así:

```bash
ghostty
├── dist
│  ├── linux
│  ├── macos
│  └── windows
…
└── zig-out
   ├── bin
   └── share
```

## Instalación

Si todo funcionó correctamente ahora sólo queda la instalación, que es linkear
el binario a un directorio dentro del `$PATH` de tu sistema y mover los archivos
`dist/linux/*.desktop` para que puedas ver los íconos y aparezca en el launcher de tu
distro.

```bash
# Instalar Ghosty
ln -s "$HOME/jsr/ghosty/src/zig-out/bin/ghostty" ~/.local/bin

# Instalar los archivos desktop
ln -s "$HOME/jsr/ghostty/src/dist/linux/ghostty.desktop" ~/.local/share/applications
ln -s "$HOME/jsr/ghostty/src/dist/linux/ghostty_dolphin.desktop" ~/.local/share/applications
```

Finalmente para configurar la terminal hay que crear el archivo de
configuración, y es tan simple cómo ejecutar lo siguiente

```bash
# Crear el directorio si no existe
mkdir -p ~/.config/ghostty/

# Crear el archivo de configuración si no existe
touch ~/.config/ghostty/config
```

Una vez hecho eso, a configurar Ghostty a tu gusto. Aquí está la
[documentación](https://ghostty.org/docs/config/reference) con todas las
opciones disponibles.

## Demo y configuración

Dejo algunos videos para ver de que se trata esta nueva terminal y cómo
configurarla. Y eso es todo, Happy hacking!

<a href="https://youtu.be/7Jon_cAK_to" class="lazy-youtube-embed">Ghostty Overview</a>

<a href="https://youtu.be/RGlj4dcdWgM" class="lazy-youtube-embed">Ghostty Install and Config</a>

Mi configuración

```yml
font-family = JetBrainsMono NF Medium
font-family-italic = JetBrainsMono NF Medium Italic
font-family-bold = JetBrainsMono NF Bold
font-family-bold-italic = JetBrainsMono NF Bold Italic
font-size = 10.2
theme = tokyonight
adjust-cell-height = 6
window-padding-x = 0
window-padding-y = 0
window-decoration = false
adjust-cursor-thickness = 2 
adjust-cursor-height = 6 
cursor-color = #00C2FF
```


![ghostty config](/assets/images/blog/24-12-27/ghostty.png)
