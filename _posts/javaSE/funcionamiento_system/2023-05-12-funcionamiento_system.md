---
layout: single
title: Java - ¿ Cómo funciona System.out.print() ?
date: 2023-05-12
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-basico
  - java-funcionamiento
  - java-clases
tags:
  - java-System
  - java-propiedades
  - java-metodos
page_css: 
  - /assets/css/mi-css.css
---

## Conceptos

* Tenemos esta ``sentencia`` de ``código`` que invoca el ``método println`` 

* ``Método`` en ``Java`` que se utiliza para ``imprimir texto`` por ``consola``

```java
// Método utilizado para imprimir por consola
System.out.println("Mensaje");
```

* ``System`` es una ``clase final`` del paquete ``java.lang`` 

  * Incluyendo la ``clase`` sería 
  
    * Paquete : ``java.lang.System`` 
  
  * Se ``inicializa`` cuando se arranca la ``JVM``
  
  * La clase ``System`` contiene una ``instancia`` de la ``clase PrintStream``
  
* La ``variable de instancia`` se llama → ``.out``
  
  * Pertenece a la ``clase PrintStream`` contiene los ``métodos`` → ``.print()`` y ``.println()`` 
  
* ``System.out`` nos da la ``variable de instancia → out`` de la clase ``PrintStream``  el cual nos permite llamar al método ``print()`` o ``println()`` en esta ``variable de instancia``

## Disección de la sentencia completa

### Clase : ``System`` 

  * Es una ``clase final`` del ``paquete java.lang`` 

  * Se inicializa automáticamente cuando se inicia la ``JVM``

  * La ``clase System`` contiene una ``instancia`` de la ``clase PrintStream``

### Propiedad : ``out`` 

  * ``Variable de instancia``

  * Es una ``variable estática`` en la ``clase System`` que se inicializa con una ``instancia`` de la ``clase PrintStream``

    * Esto significa que ``out`` es una ``variable`` que pertenece a la ``clase System`` y no a la ``clase PrintStream``
    
      * Sin embargo el valor de ``out`` es una ``instancia`` de la ``clase PrintStream`` lo que nos permite llamar a los ``métodos`` de la ``clase PrintStream`` en ``System.out``

  	  * Nos da una ``variable de instancia`` de la ``clase PrintStream``

    * Con esta ``variable de instancia`` podemos llamar al ``método`` ``print()`` o ``println()`` que están en la ``variable de instancia``
  
      * La clase ``PrintStream`` contiene los métodos ``print()`` y ``println()``
    
    * ``out`` → Dentro de la ``clase PrintStream`` se define con los modificadores ``public`` , ``static`` y ``final`` 

      * **Variable de instancia**  : ``out`` → ``public static final PrintStream out = null;``

### Método : ``print() o println()``      

  * Se diferencian en el tipo de ``parámetros`` aceptados

    * Existe un ``método sobrecargado`` para todos los ``tipos primitivos``

  * El ``tipo de devolución`` de todos ellos es ``nulo``

    * También contiene un ``método sobrecargado`` para ``imprimir cadenas`` y otro para ``objetos``

## Resumen

* ``System`` es una clase final del paquete ``java.lang`` 

* ``out`` es una ``variable estática final`` dentro de la ``clase System`` creada a partir de una ``instancia`` de la ``clase PrintStream``

  * Se usa para invocar los ``métodos`` de la ``clase PrintStream`` para mostrar datos

  * La ``clase PrintStream`` tiene varios ``métodos`` para imprimir ``datos`` incluidos ``print()`` y ``println()``

* Estamos llamando a los ``métodos print()`` y ``método println()``  mediante el uso de la ``variable out`` la cual es una ``instancia`` de la ``clase PrintStream``

  * Significa que ``todas`` las ``instancias`` de la ``clase System`` comparten la misma variable ``out``

### Aclaración 

* Una ``variable estática final`` es una ``variable`` que reserva memoría para ese elemento el cual pertenece a toda la ``clase`` en lugar de ser una copia de esa ``variable`` de la propia ``clase`` 

  * Significa que 
  
    > ``Solo hay una copia`` de la ``variable`` para todas las ``instancias`` de la ``clase``
  