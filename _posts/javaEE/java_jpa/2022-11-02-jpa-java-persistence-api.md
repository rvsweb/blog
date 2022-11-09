---
layout: single
title: JavaEE - JPA - Java Persistence API
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
  - java-jpa
  - java-persistence
  - java-orm
  - java-api
page_css:
  - /assets/css/mi-css.css
---

## Definición

* Especificación recogida en el documento [JSR338](https://jcp.org/aboutJava/communityprocess/mrel/jsr338/index.html)

  * Define **como gestionar las funcionalidades** de las **persistencias de datos** en las aplicaciones **Java**

  * El documento ``JPA`` no implementa nada ; ``indica las pautas a seguir``
  
  * Para trabajar con el documento necesitaremos utilizar un ``framework`` como ``Hibernate``

 ``JPA`` → **Java Persistence API**

* ``API`` de persistencia desarrollada para la **plataforma Java EE**

## Concepto

* Maneja ``datos relacionales`` en aplicaciones usando plataforma ``JAVA-SE`` y ``JAVA-EE``

## Areas de Persistencia

* ``API`` definida en el ``package javax.persistence``

* Lenguaje de consulta ``JAVA Persistence Query Language`` ``(JPQL)``

* ``Metadatos`` objeto/relacional

## Objetivos de la API JPA

* No perder la ``orientación a objetos`` al interactuar con la ``base de datos`` **(siguiendo el patrón mapeo-objeto-relacional)**

* Usar ``objetos regulares`` [POJOS](https://rvsweb.github.io/rvs.github.io/java/java-manual/java-ee/java-pojo/)

* Trabajar con las ``anotaciones`` dentro del ámbito del ``mapeo objeto relacional`` utilizando
  
  * ``package`` → ``javax.persistence``
