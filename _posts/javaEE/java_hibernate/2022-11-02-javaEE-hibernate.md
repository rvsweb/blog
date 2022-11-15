---
layout: single
title: JavaEE - Framework Hibernate 
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
  - java-hibernate 
  - java-framework
page_css: 
  - /assets/css/mi-css.css
---

## Framework - Hibernate

* Configura la ``persistencia`` del proyecto indicándole a que ``base de datos`` comunicarse , conectarse y que datos realizar

* Implementación de ``persistencia`` más usado y anterior a ``JPA``

* Ofrecen capacidades adicionales que ``JPA`` como ``standard`` y ``especificaciones no soportan``

  > Esos aportes no son críticos y las ventajas aportan no son suficientes comparadas con usar la especificación ``JPA``

* Para trabajar con las ``anotaciones`` dentro del ámbito del ``mapeo objeto relacional``

  * ``package`` → ``org.hibernate.annotations``

## Reflexiones

* Utilizar la especificación ``JPA``

  * Extendida desarrolladores

  * Permite cambiar implementación forma transparente

  * Permite portar aplicación entre servidores ``Java EE`` usan diferentes especificaciones

  * Es atemporal por ser un documento

  * Inmutable

    * Nuevos ``frameworks/especificaciones`` lo complementan

  * Ejemplo
  
    * El uso de ``Spring Data`` con ``JPA`` permite trabajo cómodo y rápido con repositorios

* Usar ``JPA`` como especificación y programar contra la especificación usando ``EntityManager`` , ``EntityManagerFactory``

  * No usar ``clases concretas`` de una implementación como ``Hibernate Session`` y ``SessionFactory``

* ``Hibernate`` la implementación más conocida

  * Usar ``anotaciones standard`` de ``JPA``

  * Evitar hacer uso directo de funciones de Hibernate para tener mayor portabilidad del código

  