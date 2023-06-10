---
layout: single
title: Java - IO vs NIO
date: 2023-05-18
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
tags:
  - java-buffer
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* ``Java IO`` y ``Java NIO`` 

  * Dos paquetes de la ``API`` que gestiona ``entrada/salida`` en ``Java SE``

* ``Java IO (Entrada/Salida)`` 

  * Se utiliza para realizar ``operaciones`` de ``lectura`` y ``escritura`` 
  
    * Opera dentro del ``paquete`` ``java.io``

* ``Java NIO (Nueva Entrada/Salida)`` 

  * Se introdujo a partir de ``JDK 4`` para implementar operaciones de ``E/S`` de ``alta velocidad`` y ``opera`` dentro del ``paquete java.nio``

## Diferencias Principales 

* Entre los ``paquetes``  

  * ``Java IO`` es un ``paquete`` orientado a ``secuencias`` 

    * Significa 
  
      * Que puede ``leer`` uno o más ``bytes`` a la vez desde una ``secuencia``
  
  * ``Java NIO`` es un paquete orientado al ``buffer``
  
    * Significa 
      
      * Que los ``datos`` se leen en un ``buffer`` desde el cual se procesan más utilizando un canal

## Otras diferencias

* ``Java IO`` es un ``IO`` de **bloqueo**

  * Significa 
  
    * Que si un ``subproceso`` está ``invocando`` una ``operación`` de ``lectura`` o ``escritura`` ese ``subproceso`` **se bloquea** hasta que haya algunos ``datos`` para ``leer`` o los ``datos estén`` completamente escritos
  
    * ``Java IO`` tiene **bloqueo**
    
    > Es por eso que ``IO síncrono`` o ``IO de bloqueo``
  
* ``Java NIO`` es un ``IO`` **sin bloqueo**
    
  * Significa
    
    * Que si un ``subproceso`` está ``invocando`` una ``operación`` de ``lectura`` o ``escritura`` ese ``subproceso`` **no se bloquea** hasta que haya algunos ``datos`` para ``leer`` o los ``datos`` estén completamente ``escritos`` en lugar de que el ``subproceso`` continúe con otra cosa
  