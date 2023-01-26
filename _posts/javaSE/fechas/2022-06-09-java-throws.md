---
layout: single
title: Java - Formateo de Fechas
date: 2022-08-09
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-fechas
tags:
  - java-formateo-de-fechas
  - java-DateFormat
  - java-SimpleDateFormat
page_css: 
  - /assets/css/mi-css.css
---

## Formateo de fechas

* Mostrar de forma legible las fechas podemos utilizar

  * ``DateFormat``

    * **Clase abstracta** para **subclases** de formato de **fecha/hora** que formatea y analiza **fechas** u **horas** de forma independiente del idioma.

  * ``SimpleDateFormat``

    * **Clase concreta** para **formatear** y **analizar fechas** de manera sensible a la configuración regional.

    * Esta clase nos permite

      * Convertir de ``String/texto`` a ``Date/fecha`` → **(parsear)**

      * Convertir de ``Date/fecha`` a ``String/texto`` → **(formatear)**

* Para instanciar un **objeto** del tipo ``SimpleDateFormat`` tenemos que proporcionarle un **patrón** de fecha que deseemos y como opcional una localización mediante el objeto ``locale`` de la clase ``java.util.Locale``

  * La **clase Locale** representa una **región geográfica** , **política** o **cultural**
