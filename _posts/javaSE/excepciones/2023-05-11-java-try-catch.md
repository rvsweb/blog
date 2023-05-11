---
layout: single
title: Java - Try & Catch
date: 2023-05-11
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
  - java-try
  - java-catch
  - java-manejar-excepciones
  - java-excepciones
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Estructura de manejador de ``excepciones`` o ``control de errores``

* Palabra clave ``try`` 

  * Inicia el **bloque de código** que será ``manejado`` en caso de ``errores``

* Sentencia ``catch`` 

  * Indica el tipo de ``excepción`` que se capturará
  
  * Puede repetirse varias veces para ``capturar excepciones`` de diferentes tipos 

### Ejemplo 1 : Try Catch Finally

```java
  try {
    // Código que puede producir una excepción
    int x = 10 / 0;
  } catch (ArithmeticException e) {
    // Código para manejar la excepción
    System.out.println("Ocurrió una excepción: " + e.getMessage());
  } finally {
    // Código que siempre se ejecutará después del bloque try
    System.out.println("El bloque finally siempre se ejecuta");
  }
```

* El código en el bloque ``try`` produce una ``excepción ArithmeticException`` porque intenta dividir un número por cero

* El control pasa al bloque ``catch`` que maneja la ``excepción`` y muestra un mensaje en la consola
  
* Después de eso el bloque ``finally`` se ejecuta y muestra otro mensaje en la consola

### Ejemplo 2 : Try Catch Finally

```java
  try {
  // Código que puede producir una excepción
    String s = null;
    System.out.println(s.length());
  } catch (NullPointerException e) {
    // Código para manejar la excepción
    System.out.println("Ocurrió una excepción: " + e.getMessage());
  } finally {
    // Código que siempre se ejecutará después del bloque try
    System.out.println("El bloque finally siempre se ejecuta");
  }
```

* El código en el bloque ``try`` produce una ``excepción NullPointerException`` porque intenta llamar al método ``length()`` en una variable ``String`` que es ``null``

* El control pasa al bloque ``catch`` que maneja la ``excepción`` y muestra un mensaje en la consola 

* El bloque ``finally`` se ejecuta y muestra otro mensaje en la consola

### Como actua las excepciones en el JVM 

* Si una ``excepción`` no es capturada por el listado de la cláusulas ``catch`` entonces es probable que la ``JVM`` inicie el ``reporte`` y la salida de la ``instancia`` completa de la ``JVM`` interrumpiendo todos los ``hilos`` de ``ejecución``

* La sentencia ``finally`` se ``ejecutará`` de todas maneras al salir del código
