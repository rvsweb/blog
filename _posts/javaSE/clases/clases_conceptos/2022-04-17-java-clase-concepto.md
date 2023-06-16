---
layout: single
title: Java - Clase
date: 2022-04-17
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
  - java-clase-base
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* ``Clase`` 
  
  **Se asemeja a un ``plano`` o una ``plantilla`` que ``define`` la ``estructura`` y el ``comportamiento`` de un ``tipo de objeto``**

  * **Clases** son las que almacenaran las ``propiedades`` y ``métodos`` que contendran un **objeto**

  * ``Objeto`` cambiará las ``propiedades`` de otros **objetos** por medio de los métodos de esa u otras ``clases``
  
    * ``Clase`` en realidad se refieren a un ``tipo de referencia``

* Una **clase** proporciona el **modelo/plantilla** para la creación de **objetos**

* Las ``clases`` están compuestas por

  * ``Atributos``

    * ``Variable`` de ``instancias``

    * ``Variable`` de ``clase``

    * ``Constantes``

  * ``Métodos``

    * De ``Instancia``

    * De ``Clase``

> Declarar una **clase** permite crear ``un nuevo tipo de dato``

  * Se entiende como un **archivo** del tipo ``.java``
  
* Su ``interior`` tiene definida una **estructura básica** sobre las características las cuales tendrá un **elemento concreto** dentro del **sistema** o **programa** que vayamos a **crear/diseñar**

* Una ``clase`` proporciona un **modelo** para los ``objetos`` que vayamos a construir

  * Se podría decir que es una especie de

    * **Patrón** ←→ **Molde** ←→ **Ejemplo** ←→ **Modelo**
  
* Todas las ``clases`` que construyamos o usemos de la ``API oficial`` de ``Java`` heredan de la ``principal clase`` llamada ``Clase Object``

### Ejemplo de Clase

```java
/**
* Diseño del Patrón de la Clase Persona
* 
* De esta clase podremos sacar/instanciar tantas copias "objetos" con distintos valores como necesitemos
*
*/
public class Persona{
// Atributo de instancia : Define el nombre del objeto persona que se instancia
 private String nombre;
// Atributo de instancia : Define la edad del objeto persona que se instancia
 private int edad;
// Atributo de instancia : Define la altura del objeto persona que se instancia
 private double altura;

/**
* Constructor de la Clase Persona por defecto
* 
*/
public Persona(){
  this.nombre = "Anónimo";
  this.edad = 0;
  this.altura = 0.0;
  }
}
```

### Modificador final

* Una clase con el modificador ``final`` no permite la creación de objetos

```java
// Modificador "final" establece claramente la intención
public final class MiClass { 
//Constructor private por defecto  ==> No puede ser instanciado
//La clase es final porque no se puede subclasificar o extender 
//super() → No puede ser llamado desde la subclase
    private MiClass() {
        throw new AssertionError()
    }

    //...
    public static void ejecutarAccion() {}
}
```
