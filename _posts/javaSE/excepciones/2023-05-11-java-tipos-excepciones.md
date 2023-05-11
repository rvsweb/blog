---
layout: single
title: Java - Tipos de Excepciones
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
  - java-excepciones
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Las excepciones en Java son eventos que ocurren durante la ``ejecución`` del programa 

  * Interrumpen el ``flujo normal`` de las instrucciones

  * Las ``excepciones`` pueden ser ``causadas`` por ``errores`` en el código 
  
    * Ejemplo
    
      * Intentar dividir un número por cero o acceder a un elemento fuera de los límites de un ````array```` 
      
      * Situaciones externas al programa como un archivo que no se encuentra 
      
      * Una conexión de ``red`` que falla

* Java proporciona un mecanismo para manejar ``excepciones`` mediante el uso de bloques ``try``, ``catch`` y ``finally``

* El ``código`` que puede ``producir`` una ``excepción`` se coloca dentro de un bloque ``try``

* Si ocurre una ``excepción`` en el bloque ``try`` el control pasa al primer bloque ``catch`` que puede manejar la ``excepción``

* Si no hay ningún bloque ``catch`` que pueda manejar la ``excepción`` el programa terminará

* El bloque ``finally`` si está presente siempre se ejecutará después del bloque ``try`` ``independientemente`` de si se produjo una excepción o no

### Tipos de Excepciones

* ``ArrayIndexOutOfBoundsException``

  * ``Excepción`` que se produce cuando se intenta acceder a un elemento de un ``array`` con un ``índice`` que está fuera de los límites del ``array``
  
  * Ejemplo
    
    * Tienes un ``array`` de ``5 elementos`` y tratas de acceder al elemento en el ``índice 5``
      
    * (No existe porque los índices van de 0 a 4) 
        
    * Se producirá una excepción ``ArrayIndexOutOfBoundsException``