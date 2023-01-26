---
layout: single
title: Java - Signatura Métodos 
date: 2022-12-13
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-metodos
tags:
  - java-manual
  - java-signatura
page_css: 
  - /assets/css/mi-css.css
---

## Definición

* Combinación del ``nombre del método`` y la ``lista`` de ``tipos de parámetros`` del ``método``

* La ``signatura`` de un ``método`` es lo que lo diferencia de otros ``métodos`` en la misma ``clase`` o en ``clases relacionadas``

## Ejemplo

* Supongamos que tenemos una ``clase`` llamada ``Calculadora`` con dos ``métodos`` llamados ``sumar`` y ``multiplicar``

```java

public class Calculadora {

  // Primer método
  public int sumar(int a, int b) {
    return a + b;
  }

  // Segundo método
  public int multiplicar(int a, int b) {
    return a * b;
  }
}
```

* Explicación

  * Las **signaturas** de los ``métodos`` son ``sumar(int, int)`` y ``multiplicar(int, int)`` respectivamente
  
  * Estas **signaturas** incluyen el nombre del ``método`` y la lista de ``tipos de parámetros`` que se esperan para cada ``método``
  
  * Esto nos permite ``invocar`` a cada ``método`` de manera única dentro de la ``clase`` y en cualquier otro lugar donde tengamos una ``referencia`` a un ``objeto`` de la ``clase Calculadora``
