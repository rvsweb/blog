---
layout: single
title: Git refspec
date: 2022-03-12
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/llama.jpg
categories:
  - git
  - git-basico
  - git-manual
tags:
  - git-remotas 
  - git-ramas 
page_css: 
  - /assets/css/mi-css.css
---
 
## Refspec

* Indica las **ramas locales** y las **ramas remotas** entre las que se descargaran los **archivos** y **directorios**

* Puede ser un nombre de una rama **local** como **remota**

* Si no se especifica este parámetro , se bajarán las actualizaciones de todas las **ramas locales** que existan también en el **[Repositorio Remoto]**

### Comandos donde se aplican

* Descargarse los datos de un **remoto** y a la vez aplicar el comando ``git merge`` automáticamente

```bash
git pull [nombre_URL_remota [refspec]]
# Ejemplo
git pull origin 
git pull origin master
```

* Subir contenido a un **Repositorio Remoto**

```bash
git push [nombre-URL-remoto] [refspec]
```
