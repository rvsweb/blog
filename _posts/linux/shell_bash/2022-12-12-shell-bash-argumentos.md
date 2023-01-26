---
layout: single
title: Shell Bash - Argumentos
date: 2022-01-15
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/linux/tux.jpg
categories:
  - shell-bash
  - shell-bash-básico
tags:
  - shell-bash-argumentos
page_css: 
  - /assets/css/mi-css.css
---

## Argumentos

* En programación, un ``argumento`` es un ``valor`` que se pasa a una ``función`` o ``programa`` cuando se llama

* Los ``argumentos`` son usados dentro del ``programa`` o ``función`` para realizar ciertas ``acciones`` o ``cálculos``

* En el ``shell de bash``

  * Los ``argumentos`` se pasan después del nombre del ``programa`` o ``función`` que se está llamando
  
* Por ejemplo

  * Si queremos llamar a un programa llamado ``mi_programa`` y pasarle dos argumentos ``arg1`` y ``arg2`` podríamos hacerlo de la siguiente manera

## Ejemplo

```shell
mi_programa arg1 arg2
```

* Dentro del programa ``mi_programa`` podríamos acceder a los ``argumentos`` pasados de la siguiente manera

```shell
#!/bin/bash

# accediendo al primer argumento
echo $1

# accediendo al segundo argumento
echo $2
```

* En este ejemplo el programa imprimiría ``arg1`` y ``arg2`` en dos líneas distintas
