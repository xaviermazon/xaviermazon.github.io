---
title: Como instalar Jekyll desde 0
author: Xavi
date: 2023-07-28 17:21:00 +0200
categories: [Blogging, Tutorial, Jekyll, CSS, html, ruby, página, web, herramienta]
tags: [writing]
---

# Índice

# Introducción

El objetivo de este blog tutorial, es explicar como instalar jekyll desde 0, se pasará desde no tener ninguna idea a tener algo de idea y tenerlo instalado para crear paginas web.

# Punto de partida

Para hacer la instalación, se necesita lo siguiente:
- Una distribución Linux(Concretamente Arch linux, es lo que he usado)
- Un editor de texto(como si quieres trabajar con vi o Visual Studio Code)
- Internet(Si estas leyendo esto pues tendrás internet, digo yo)
- Un navegador web(Firefox, me gusta, siempre va bien)
- Tener idea de como instalar con el gestor de paquetes
- Interprete de comandos para el sistema de linux(Bash, es el más usado)

# Antes de instalar

Bueno para empezar lo que haremos es actualizar el sistema, dependiendo de que distribución Linux el gestor de paquetes cambia, entonces puede que las instrucciones del comando pacman no servirá para Debian.

Por mi parte seria:

```console
$ sudo pacman -Syyuu
```

Lo que haremos es forzar el gestor de paquetes a que haga una petición a los servidores de los repositorios de los paquetes, obtendrá un registro de paquetes con las versiones correspondientes y si hay alguna version más reciente, nos mostrará por terminal que paquetes habrá que actualizar. Pulsamos la S para que nos actualize los paquetes.

# Instalando paquetes

Primero instalaremos las herramientas que le hace falta Jekyll para hacerlo funcionar(esto se le llama dependencias).

```console 
$ sudo pacman -Sy make gcc ruby base-devel 
```

# Configuración de entorno de trabajo

Despues, de tenerlo instalado y sin ningun error, haremos lo siguiente

```console
$ nano .bashrc
```

Y en el final del fichero, añadimos:

```console
export GEM_HOME=”~/.local/share/gem/ruby/3.0.0"
export PATH="$PATH:$GEM_HOME/bin"
```

Se recomienda que, se le añade un comentario antes, para saber que se ha modificado y que lo habeís hecho vosotros, un comentario que os sugiero es:

```console
# Variables de entorno para Jekyll - Modificado el dia [dd/mm/aaaa], por [vuestro nombre/usuario]
```

# Puesta a punto de Gem

Una vez hecho esto, ahora instalaremos más paquetes con gem, es el gestor de paquetes para ruby(lenguage de programación), haremos una única vez:

```console
$ gem env
```

Lo que hacemos es para preparar el entorno de trabajo de ruby. Despues, actualizaremos la paqueteria:

```console
$ gem update
```

Puede tardar bastante si tienes un hardware poco potente, cuando más potente más rápido será. Instalamos ahora Jekyll:

```console
$ gem Jekyll
```

Os dejaré las fuentes donde he mirado, pero por mi con esto me ha bastado para instalarlo. A partir de aqui, podemos o bien bajarnos un site web que tenga ya Jekyll o crearnos uno desde 0. Si optais la opcion de crear desde 0 consultad la fuente de otro blog para instalar unos paquetes minimos y instalar:

```console
$ jekyll new <NombreDeLaCarpetaQueContendraElSiteWeb>
$ cd <NombreDeLaCarpetaQueContendraElSiteWeb>
$ sudo bundle install
```

Si os habeis descargado un site pre-hecho, os saltais los comandos jekyll, pero si tendreis que ir a la carpeta e instalar el bundle en la carpeta.

Ya por finalizar, haremos una prueba de que este todo en funcionamento:

```console
$ bundle exec jekyll serve
```

Os deberia salir algo parecido a esto:

```bash
Configuration file: /home/<user/ruta/absoluta/hacia/la/carpeta/contenedora>/_config.yml
 Theme Config file: /home/<user/ruta/absoluta/hacia/la/carpeta/contenedora>/_config.yml
            Source: /home/<user/ruta/absoluta/hacia/la/carpeta/contenedora>
       Destination: /home/<user/ruta/absoluta/hacia/la/carpeta/contenedora>/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 1.061 seconds.
 Auto-regeneration: enabled for '/home/<user/ruta/absoluta/hacia/la/carpeta/contenedora>'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

# Notas

- Si hubiese un problema o encontrase algo que no acabase de funcionar, se actualizaria el post
- Se puede hacer un script de instalación.

# Fuente de información

- [jmgomez(Graciás guapo)](https://jmgomez-iaa.github.io/blog/ArchLinux-Instalacion-Jekyll/).
- [Página official de Jekyll](https://jekyllrb.com/).
