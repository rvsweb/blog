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
  
* La ``variable de instancia`` se llama → ``out``
  
  * Pertenece a la ``clase PrintStream`` contiene los ``métodos`` → ``print()`` y ``println()`` 
  
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

* ``System`` es una clase en el paquete ``java.lang`` 

* ``out`` es una ``variable estática`` en la ``clase System`` que es una ``instancia`` de la ``clase PrintStream``

  * La ``clase PrintStream`` tiene varios ``métodos`` para imprimir ``datos`` incluidos ``print()`` y ``println()``

* Estamos llamando al ``método print()`` en la ``variable out`` que es una ``instancia`` de la ``clase PrintStream``

* En el caso de System.``out`` es una ``variable estática`` en la ``clase System`` que se ``inicializa`` con una ``instancia`` de la ``clase PrintStream``

  * Significa que ``todas`` las ``instancias`` de la ``clase System`` comparten la misma variable ``out`` y esta ``variable`` es una ``instancia`` de la ``clase PrintStream``

### Aclaración 

* Una ``variable estática`` es una ``variable`` que pertenece a la ``clase`` en lugar de alguna ``instancia`` de la ``clase``

  * Significa que 
  
    > ``Solo hay una copia`` de la ``variable`` para todas las ``instancias`` de la ``clase``
