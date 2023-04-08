---
layout: single
title: Java - Record
date: 2023-04-08
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-record
tags:
  - java-clases
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* En la ``JEP 395`` los ``Records`` de ``Java`` son un **nuevo tipo de clase**

  * Los ``records`` en Java son un nuevo tipo de declaración en Java 14 y versiones posteriores

* **Tipo especial** de declaración de ``clase`` destinado a ``reducir el código repetitivo`` 

* Introducido para ser utilizados como una forma rápida de ``crear clases`` de soporte de datos

## Objetivo de estas clases

  * Contener datos 
  
  * Transportarlos entre módulos

## Proporcionan 

  * Un ``constructor público``

  * ``Métodos de lectura`` para cada ``campo``

  * Implementación de ``hashCode``, ``equals`` y el ``toString``

## Información adicional

* Este tipo de clases van a permitir modelar objetos de datos simples de una manera más simple y eliminando ese ``boilerplate`` 

  * ``boilerplate`` : "Repetición de código que se itera constantemente y que presenta cambios mínimos o no presentan ningún cambio" para transformar a objetos inmutables

* Es una característica semántica que permite una manera para modelar únicamente datos y proporcionar un patrón de programación común

* La clase y sus miembros de datos se han declarado como ``finales`` 

  * Implica que esta clase ``no se puede extender`` o ``no se puede heredar`` 
y también es inmutable

* Todos los registros son una subclase de Registro definido en el paquete ``java.lang``

## Declaración

Para declarar un ``record`` en Java se utiliza la palabra clave ``record`` seguida del 
nombre del ``record`` y una lista de ``campos`` entre paréntesis

### Ejemplo de Record

* Para crear un ``record`` llamado ``Persona`` con los ``campos nombre`` y ``edad`` se podría escribir el siguiente código

```java
public record Persona(String nombre, int edad) { ... }
```

  * Este código genera automáticamente 
    
    * ``Constructor público`` 
    
    * ``Métodos de lectura`` para cada campo
    
    * La ``implementación`` de ``hashCode``, ``equals`` y el ``toString``

* Los ``records`` en Java son útiles para crear ``POJOs`` **(objetos Java antiguos sin formato)** de forma rápida y sencilla

## Uso común 

* Los ``records`` en Java es para hacer uso de ``DTOs`` **(Data Transfer Objects)** en aplicaciones ``REST2`` 

* Al ser ``clases inmutables`` y de ``fácil definición`` los ``records`` pueden ser utilizados en la **parte del controlador** de una aplicación ``REST2``

### Ejemplo de Record

* Si se tiene un ``record`` llamado ``Persona`` con los campos nombre y edad se puede crear una ``instancia`` del ``record`` de la siguiente manera

```java
Persona persona = new Persona("Juan", 25);
```

* Se pueden acceder a los ``campos`` del ``record`` utilizando los ``métodos de lectura`` generados automáticamente

```java
String nombre = persona.nombre();
int edad = persona.edad(); 
```
