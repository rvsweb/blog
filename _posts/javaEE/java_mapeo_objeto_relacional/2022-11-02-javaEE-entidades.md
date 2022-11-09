---
layout: single
title: JavaEE - Concepto Entidades
date: 2022-11-02
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-ee
tags:
  - java-entidades
page_css:
  - /assets/css/mi-css.css
---

## Concepto de Entidad

* **Objetivo** del **mapeo objeto relacional** entre **Java** y la **base de datos** es representar la **programación orientada a objetos** mediante una **estructura de datos**

  * Correspondencia entre **clases** y **tablas**

    * Enlace : [javax.persistence.Entity](https://docs.oracle.com/javaee/7/api/)

### Tipos de Mapeo

* Formas de realizarlo

  1. Mediante un archivo externo en ``XML`` que contiene la configuración del mapeo
      * ``sistema antiguo``

  2. Por ``anotaciones``
      * Se colocan encima de los elementos que componen una clase en Java sobre todo en los ``métodos`` que componen el mapeo

### Funcionamiento

* Utilizamos la anotación ``@Entity`` para marcar como ``entidad`` una ``clase Java`` y así vincularla con una ``tabla`` de la ``base de datos``

  * Le indicamos al ``sistema de persistencia`` que la ``clase`` es una ``entidad`` la cual debe de ``mapear`` para ello se importa automáticamente el package ``javax.persistence.Entity``
  