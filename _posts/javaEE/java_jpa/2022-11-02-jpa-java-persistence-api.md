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

* Creado en **2006**

* Especificación del documento [JSR338](https://jcp.org/aboutJava/communityprocess/mrel/jsr338/index.html)

* ``No proporciona clases para trabajar con la información``

* ``Proporciona interfaces`` podemos usar para ``implementar`` la ``capa de persistencia`` de la aplicación ayudándonos de la implementación ``JPA``

> En la practica utilizarás una ``librerías de persistencia`` que implemente ``JPA`` , no directamente ``JPA``  

* Define ``como gestionar las funcionalidades concretas de la API`` 
  * La ``capa de persistencia`` con ``objetos Java``

* Ejemplo de pautas a seguir dentro de la especificación

  1.``Anotaciones que han de usarse``
  
  2.``Como han de persistirse los objetos que han de buscarse``
  
  3.``Cual es el ciclo de vida``

## Conceptos

* La especificación ``JPA`` **no implementan nada**

* ``Solo indica las pautas a seguir`` a la hora de desarrollar un aplicación utilizando la ``API``
  
* Para trabajar con la ``API`` necesitaremos utilizar un ``framework``

* Ejemplo

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

* Trabajar con ``anotaciones`` dentro del ámbito ``mapeo objeto relacional`` utilizando
  
  * ``package`` → ``javax.persistence``

* Utilizar ``orientación a objetos`` al interactuar con ``base de datos`` (siguiendo el patrón ``mapeo-objeto-relacional``)

* El ``mapeo`` entre ``objetos`` de ``Java`` y las ``tablas`` de la ``base de datos`` se define a traves del ``metadatos de persistencia``

* Proveedor de ``JPA`` utilizará información de ``metadatos`` de ``persistencia`` para realizar ``operaciones`` de ``base de datos``

* ``Metadatos JPA`` se definen a través de ``anotaciones`` en la ``clases Java``

* ``Configuración XML`` sobrescribe ``anotaciones``

  * Se definen a través de ``archivos XML`` o combinación de ambos

    > La configuración XML sobrescribe las anotaciones

* ``JPA`` define ``lenguaje de consulta`` similar a ``SQL`` para ``consultas estáticas`` y ``dinámicas``

* Proveedores de ``persistencia JPA`` ofrecen la opción de ``crear esquemas`` de ``base de datos`` automáticamente en función de los ``metadatos``

* Usar ``objetos regulares`` [POJOS](https://rvsweb.github.io/rvs.github.io/java/java-manual/java-ee/java-pojo/)
