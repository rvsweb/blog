---
layout: single
title: JavaEE - DAO
date: 2022-11-04
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
  - java-dao 
page_css: 
  - /assets/css/mi-css.css
---

## DAO - Objeto de Acceso a Datos

* **Patrón**  de diseño que proporciona una ``interface abstracta`` hacia algún tipo de base de datos mediante otro mecanismo de ``persistencia``

  > **Patrón** aplicable a la mayoría de los **lenguajes de programación** que necesitan uso de la **persistencia** y **conexión** con una **base de datos** asociados a las aplicaciones ``Java EE`` y las ``base de datos relacionales`` a las que se accede mediante las ``API`` de ``JDBC``

* Asignar llamadas de aplicaciones de ``capa de persistencia (DAO)`` proporciona especificas operaciones de datos sin especificar detalles de la ``base de datos``

* Separa ``acceso a datos`` necesita la ``aplicación`` (términos de ``objetos`` y ``tipos de datos``) específicos del dominio (la ``interfaces pública`` de la ``DAO``)
como apoyar las necesidades de la ``DBMS especifico`` , un esquema de ``base de datos`` , etc. la implementación de la ``DAO``

### VENTAJAS

* Usar ``objetos`` del tipo de ``acceso a datos`` en la separación de las ``2 capas`` de la ``aplicación`` que existen y que no conocen como esta implementada una capa con respeto a la otra y que se tiene en cuenta que en el futuro puedan evolucionar de forma independiente pero mantenga la funcionalidad

  > Los detalles del almacenamiento están ocultos del resto de la aplicación

* Cambiar la ``lógica de negocio`` basada en la ``interfaz DAO`` mientras los cambios en la ``lógica de persistencia`` **no afecten** a los ``clientes`` que utilizan ``DAO`` siempre que la ``interfaz`` siga implementada

