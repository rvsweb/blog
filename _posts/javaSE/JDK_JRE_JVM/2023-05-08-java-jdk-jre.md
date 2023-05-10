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
  - java-JVM
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* **JDK** ``( Java Development Kit )``

  * Paquete completo para desarrollar programas ``Java``

  * Contiene un compilador ``javac``

  * Herramienta de depuración y desarrollo de programas ``Java``

  * Comando ``jar`` para comprimir un proyecto en un solo archivo **(compatible con ZIP)**

  * Un entorno de ejecución ``JRE ( Java Runtime Environment)`` para ejecutar ``binarios``

* Proyecto terminado no es necesario tener el compilador utilizamos el entorno de ejecución ``JRE (Java Runtime Environment)``

* **JRE** ``( Java Runtime Environment)``

  * Paquete ligero para ejecutar aplicaciones ``Java``

  * Posee un conjunto de elementos para diseñar y ejecutar aplicaciones ``Java``
   
  * Contiene un ``JVM ( Java Virtual Machine )`` como entorno de ejecución de ``Java``

  * Dispone de ``bibliotecas de clases`` estandar
      
  * Parte del kit de desarrollo Java ``(JDK)``

  * Compuesto por la bibliotecas de las clases y el cargador de clases ``Java``

* **JVM** ``( Java Virtual Machine)``

* Componente que se instala en el ``sistema operativo`` a través del ``(JDK o JRE)`` que actua como un ``motor en tiempo de ejecución`` de la aplicaciones ``Java``

* Convierte el código ``bytecode`` a ``código nativo`` 

* Permite ejecutar un programa en diferentes sistemas operativos sin reescribir el código para adaptarlo a esa arquitectura

* ``JVM`` no se instala de forma independiente ya que se incluye como parte del ``JDK`` o del ``JRE``

### Relación entre JDK , JRE y JVM

* **JDK** ``(Java Development Kit)`` 

  * Entorno de desarrollo de software utilizado para desarrollar aplicaciones Java 
  
  * Incluye el **JRE** ``(Java Runtime Environment)`` proporciona requisitos mínimos para ejecutar una aplicación
  
  * **JRE** consiste en la **JVM** ``(Java Virtual Machine)`` , clases principales y archivos auxiliares

* Resumen 

  * **JDK** proporciona el ``entorno para desarrollar`` y ejecutar el programa ``Java``
  
  * **JRE** proporciona un entorno para ejecutar (pero no desarrolla) el programa ``Java`` en su máquina
  
  * **JVM** es una parte del **JDK** y **JRE** porque está incorporada en ambos
  
  * Cualquier programa ``Java`` que ejecute utilizando **JRE** o **JDK** entra en la **JVM** y la **JVM** es responsable de ejecutar el programa ``Java`` línea por línea