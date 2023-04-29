---
layout: single
title: Java - Atributos de instancia
date: 2022-04-28
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-variables
tags:
  - java-instancia
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* ``Atributos de instancia`` son variables que pertenecen al **objeto en sí** y no a una **única clase concreta** y **específica**

	* ``Atributos de instancia`` → Termino que se utiliza en la ``documentación oficial de Java``

	* Se utilizan para referirse a las ``variables declaradas`` dentro de una ``clase`` que almacenan ``datos específicos`` de cada **objeto** de esa **clase concreta**

	* ``Variables de instancia`` se le conocen como ``campos de instancia`` o ``campos de objeto``

## Otras Definiciones 

1. *Variables de instancia*

2. *Atributos de instancia* → Preferida

5. *Campos*

3. *Campos de instancia*

4. *Campos de objeto*

## Ejemplo de Atributos de Instancia

```java
// Clase
public class Persona {

    // Atributos de instancia
    private String nombre;
    private int edad;

    // Constructor
    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    // Métodos de instancia
    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public int getEdad() {
        return edad;
    }

    public void setEdad(int edad) {
        this.edad = edad;
    }
}
```
