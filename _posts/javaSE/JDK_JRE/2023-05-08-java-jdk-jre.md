---
layout: single
title: Java - JDK - JRE - JVM
date: 2023-05-08
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
tags:
  - java-JDK
  - java-JRE
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* **JDK** ``( Java Development Kit )`` contiene

  * Un compilador

  * Comando ``jar`` para comprimir un proyecto en un solo archivo (compatible con ZIP)

  * Un entorno de ejecución para binarios

* Proyecto terminado no es necesario tener el compilador utilizamos el entorno de ejecución JRE (Java Runtime Environment)

* **JRE** ``( Java Runtime Environment)`` contiene

  * Entorno de ejecución de Java

  * Conjunto de elementos para diseñar y ejecutar aplicaciones Java

  * Parte del kit de desarrollo Java ``(JDK)``

    * Compuesto por la bibliotecas de las clases , el cargador de clases y la maquina virtual de Java ( JVM )

### Relación entre JDK , JRE y JVM

* **JDK** ``(Java Development Kit)`` 

  * Entorno de desarrollo de software utilizado para desarrollar aplicaciones Java 
  
  * Incluye el **JRE** ``(Java Runtime Environment)`` proporciona requisitos mínimos para ejecutar una aplicación
  
  * **JRE** consiste en la **JVM** ``(Java Virtual Machine)`` , clases principales y archivos auxiliares

* Resumen 

  * **JDK** proporciona el entorno para desarrollar y ejecutar el programa Java
  
  * **JRE** proporciona un entorno para ejecutar (no desarrollar) el programa Java en su máquina
  
  * **JVM** es una parte del **JDK** y **JRE** porque está incorporada en ambos
  
  * Cualquier programa Java que ejecute utilizando **JRE** o **JDK** entra en la **JVM** y la **JVM** es responsable de ejecutar el programa Java línea por línea