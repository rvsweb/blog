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

## Definición - JPA

 ``JPA`` → **Java Persistence API**

* Especificación del documento [JSR338](https://jcp.org/aboutJava/communityprocess/mrel/jsr338/index.html)

* Define ``como gestionar las funcionalidades concretas de la API`` como puede ser en este caso la ``capa de persistencia`` con ``objetos Java``

  * Ejemplo de pautas a seguir dentro de la especificación

  1.``Anotaciones que han de usarse``
  
  2.``Como han de persistirse los objetos que han de buscarse``
  
  3.``Cual es el ciclo de vida``

## Conceptos

* La especificación ``JPA`` **no implementan nada**

  * ``Solo indica las pautas a seguir`` a la hora de desarrollar un aplicación utilizando esta ``API``
  
* Para trabajar con la ``API`` necesitaremos utilizar un ``framework`` como por ejemplo

  * ``Hibernate``
  
  * ``DataNucleus``
  
  * ``EclipseLink``
  
  * ``ObjectDB``

* ``API`` de persistencia desarrollada para la ``plataforma Java-EE``

* Maneja ``datos relacionales`` en aplicaciones usando plataforma ``JAVA-SE`` y ``JAVA-EE``

## Areas de Persistencia

* ``API`` definida en el ``package javax.persistence``

* Lenguaje de consulta ``JAVA Persistence Query Language`` ``(JPQL)``

* ``Metadatos`` **objeto/relacional**

## Objetivos de la API JPA

* No perder la ``orientación a objetos`` al interactuar con la ``base de datos`` **(siguiendo el patrón mapeo-objeto-relacional)**

* Usar ``objetos regulares`` [POJOS](https://rvsweb.github.io/rvs.github.io/java/java-manual/java-ee/java-pojo/)

* Trabajar con las ``anotaciones`` dentro del ámbito del ``mapeo objeto relacional`` utilizando
  
  * ``package`` → ``javax.persistence``
