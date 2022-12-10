---
layout: single
title: Java - Polimorfismo
date: 2022-12-09
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-clase
tags:
  - java-polimorfismo
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Permite que una misma acción tenga comportamientos diferentes en diferentes objetos

* Podemos utilizar el polimorfismo mediante la creación de clases que heredan de una clase padre y sobrescriben (o implementan) los métodos de la clase padre de diferentes maneras.

## Ejemplo

 ace:

```java
public class Animal {

  public void hacerSonido() {
    System.out.println("Hacer sonido genérico de animal");
  }
}

public class Perro extends Animal {

  public void hacerSonido() {
    System.out.println("Guau!");
  }
}

public class Gato extends Animal {

  public void hacerSonido() {
    System.out.println("Miau!");
  }
}

public class PolimorfismoEjemplo {

  public static void main(String[] args) {

    Animal perro = new Perro();
    perro.hacerSonido();

    Animal gato = new Gato();
    gato.hacerSonido();
  }
}
```

* Explicación

  * La ``clase Animal`` tiene un ``método hacerSonido()`` que se implementa en las clases ``Perro`` y ``Gato`` de manera diferente
  
  * En el ``método main`` se crean instancias de la clase ``Perro`` y ``Gato`` se asignan a ``variables`` de ``tipo Animal``
  
  * Cuando se llama al ``método hacerSonido()`` en estas variables se ejecuta la implementación específica para cada tipo de animal
  
  * Demuestra cómo el ``mismo método`` puede ``trabajar`` de manera diferente dependiendo del ``tipo de datos`` con el que se está trabajando.
