---
layout: single
title: Java - Clase Optional<T>
date: 2022-11-23
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
  - java-Optional<T>
page_css: 
  - /assets/css/mi-css.css
---

## Definición

* ``Clase concreta`` que acepta elementos de ``tipos genéricos`` y permite administrar distintos ``tipos de datos``

```java
// Definición completa de la clase concreta
//           Clase Concreta
//              ↓ 
//              ↓    Elemento Tipo Genérico           
//              ↓     ↓
public class Optional<T>
```

* ``Clase contenedor`` que puede ``almacenar o no`` un valor ``no nulo``

  * ``Tipo de variable`` puede almacenar ``2 valores`` distintos

    1. **Primer valor**

        * Es un ``objeto`` a utilizar

    2. **Segundo valor**

        * Es un ``elemento/valor vació`` o ``empty``

          * Cuando no se encuentra un ``valor concreto`` y queremos ``informar`` del problema

  * **Método** ``isPresent()``
  
    * Devolverá ``true`` si hay valor

    * Devolverá ``false`` si no hay valor

  * **Método** ``get()``
  
    * Devolverá el valor ``si lo contiene``

  * **Método** ``of()``

    * Devuelve un ``Optional`` que describe el valor ``no nulo - non-null``

  * Método ``orElse()``

    * Devuelve ``valor predeterminado`` si el valor ``no está presente``

  * Método ``empty()``

    * Devuelve una ``instancia opcional vacía`` si no hay ningún valor presente

* Proporciona ``métodos adicionales`` depende ``presencia`` o ``ausencia valor`` contenido

* ``Clase Concreta y Genérica`` basada en valores

  * Utilizada ``operaciones`` de ``identidad`` que incluyen tener ``resultados`` impredecibles y a evitar

    * ``Ejemplo``

      * Referencias de ``igualdad`` → ``==``

      * Código ``hash`` de identidad

      * ``Sincronización``

## Ejemplo

* Definimos la clase concreta con la que vamos a trabajar

```java
package com.ej.usando.optional.no.nulls;
/**
 * Clase Concreta llamada Calificaciones
 * 
 * Define la clase Calificaciones con todos sus atributos y métodos
 * 
 * @date 22 nov 2022 23:07:29
 * 
 * @author RVS
 * 
 */
public class Calificaciones {

 /**
  * Atributo de instancia
  */
 private String asignatura;

 /**
  * Atributo de instancia
  */
 private double valor;

 /**
  * Constructor parametrizado
  * 
  * @param asignatura
  * @param valor
  */
 public Calificaciones(String asignatura, double valor) {
  super();
  this.asignatura = asignatura;
  this.valor = valor;
 }

 /**
  * 
  * @return  
  */
 public String getAsignatura() {
  return asignatura;
 }

 /**
  * 
  * @param asignatura
  */
 public void setAsignatura(String asignatura) {
  this.asignatura = asignatura;
 }

 /**
  * 
  * @param valor
  */
 public void setValor(double valor) {
  this.valor = valor;
 }

 /**
  * 
  * @return
  */
 public double getValor() {
  return valor;
 }
}
```

* Definimos la ``clase`` donde ejecutaremos el ``código`` y utilizaremos la ``clase Genérica Optional<T>`` para reali zar las comprobaciones necesarias para evitar producir el error ``java.lang.NullPointerException``

```java
package com.ej.usando.optional.no.nulls;

import java.util.ArrayList;
import java.util.List;
import java.util.Optional;

/**
 * Clase Concreta Principal 
 * 
 * Contiene el método Main para ejecutar la clase 'Calificaciones' 
 * 
 * @date 22 nov 2022 23:07:35
 * 
 * @author RVS
 *
 */
public class OptionalPrincipal {

 public static void main(String[] args) {

//    Interface
//    ↓        Variable de Referencia
//    ↓          ↓ 
//    ↓          ↓     Reserva espacio en la memoria para el objeto
//    ↓          ↓      ↓  
//    ↓          ↓      ↓  Clase Concreta que implementa la interface List<Not>
//    ↓          ↓      ↓    ↓
  List<Calificaciones> notas = new ArrayList<Calificaciones>();
  
// Objeto de tipo List<Nota> implementando por la Clase Concreta ArrayList<Nota>
//   ↓
//   ↓           Ninguna de las notas es mayor de 9 lo cual no encontrará objeto que mostrar con esa calificación    
//   ↓
  notas.add(new Calificaciones("matemáticas", 3));
  notas.add(new Calificaciones("ingles", 5));
  notas.add(new Calificaciones("física", 7));

//  Clase Genérica<Tipo de Dato>
//     ↓        
//     ↓          Ref.Objeto
//     ↓             ↓ 
//     ↓             ↓     Método que utilizará la comprobación 
//     ↓             ↓     de los métodos 'of()' 'empty()' para encontrar 
//     ↓             ↓     valores superiores a 9 dentro 
//     ↓             ↓     de los objetos y en caso de no ser así 
//     ↓             ↓     no mostrar nada en lugar de lanzar 
//     ↓             ↓     la excepción "java.lang.NullPointerException"
  Optional<Calificaciones> oNota = buscarNotasSobresalientes(notas);
// Utilizamos el método 'isPresent()' para comprobar si existen esos elementos dentro del objeto  
  if (oNota.isPresent()) {
// Usamos el método 'get()' para obtener el valor que contenga los objetos    
   Nota nota = oNota.get();
// Obtenemos todos los valores mediante los métodos
   System.out.println(nota.getValor());
   System.out.println(nota.getAsignatura());
  }
 }

 /**
  * Función de Clase
  * 
  * @param notas - List<Calificaciones> - Contiene un objeto con todos los elementos de la lista
  * @return - Calificaciones - Devuelve un objeto con todos los elementos de la lista
  */
 public static Optional<Calificaciones> buscarNotasSobresalientes(List<Calificaciones> notas) {
// Añadimos un objeto pasado por parámetro 
// al bucle foreach para recorrer todos los elementos  
  for (Calificaciones unaNota : notas) {
// Si el valor de la nota dentro del objeto pasado por parámetro es mayor que 9
   if (unaNota.getValor() >= 9) {
// Almacenamos la referencia del objeto dentro del objeto Local    
    return Optional.of(unaNota);
   }
  }
// Lo devolvemos con la referencia apuntando al objeto 
// que le pasamos por parámetro y que contiene el valor mayor a 9  
  return Optional.empty();
 }
}
```
