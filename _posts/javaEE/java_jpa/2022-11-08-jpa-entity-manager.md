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
  - java-interface
  - java-entity-manager
page_css:
  - /assets/css/mi-css.css
---

## JPA - EntityManager

* ``Interface`` utilizada para interactuar en el contexto de la ``persistencia``

* Una ``instancia`` de ``EntityManager`` asociada contexto de la ``persistencia``

* Contexto de ``persistencia`` ( conjunto de ``instancias`` de entidad ) para cualquier identidad ``persistente`` existe una instancia de **entidad única**

* Dentro ``contexto de persistencia`` ( se gestiona las ``instancias`` de ``entidad`` y su ``ciclo de vida``)

* ``API (application programming interface)`` de ``EntityManager`` se usa para ``crear`` / ``eliminar`` instancias de ``entidades persistentes`` ( para buscar ``entidades`` por su ``clave principal`` y para ``consultar entidades``)

* Conjunto de ``entidades`` pueden ``gestionar instancias`` de ``EntityManager`` definido por una ``unidad de persistencia``

* Unidad de ``persistencia``

  * Define el conjunto de todas las ``clases relacionadas`` o ``agrupadas`` por la aplicación que debe colocarse en su asignación a una ``única base de datos``
