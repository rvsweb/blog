---
layout: single
title: Java - Throw
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
  - java-throw
  - java-excepciones
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Transfiere el control de errores al manejador de excepciones

* Se utiliza para lanzar explícitamente una excepción desde un método o un bloque de código

```java

public class Main {
 
  static void checkAge(int age) {
    if (age < 18) {
      throw new ArithmeticException("Access denied - You must be at least 18 years old.");
    } else {
      System.out.println("Access granted - You are old enough!");
    }
  }

  public static void main(String[] args) {
    checkAge(15); // Set age to 15 (which is below 18...)
  }
}
```