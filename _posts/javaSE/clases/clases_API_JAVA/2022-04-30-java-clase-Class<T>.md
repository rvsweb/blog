---
layout: single
title: Java - Class <T>
date: 2022-12-14
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
  - java-Class<T>
page_css: 
  - /assets/css/mi-css.css
---

## Definición

* ``Clase genérica`` se utiliza para **representar** la ``clase`` de un ``tipo de objeto``

  * Representa una clase de un tipo particular ``T``

* ``Clase`` contiene información sobre el ``tipo de objeto`` que representa

  * Como ``nombre`` , ``estructura`` y ``métodos``

* La ``clase Class<T>`` se utiliza para **obtener información** sobre un ``tipo de objeto`` en ``tiempo de ejecución``

  * ``Permite`` a los desarrolladores ``crear código`` que se ``comporte`` de ``manera diferente`` dependiendo del ``tipo de objeto`` con el que se esté trabajando

  * Un objeto ``Class`` representa la definición de la clase

## Ejemplo

* Supongamos que tenemos una clase ``Person`` que representa a una ``persona``

  * La ``clase Person`` tiene los siguientes ``atributos`` de clase

```java

class Person {
  private String name;
  private int age;

  public Person(String name, int age) {
    this.name = name;
    this.age = age;
  }

  public String getName() {
    return this.name;
  }

  public int getAge() {
    return this.age;
  }
}
```

* Supongamos que queremos crear un ``método`` que ``imprima`` el ``nombre`` y la ``edad`` de una ``persona`` en la terminal

  * Podríamos ``crear`` un ``método`` que tome un ``objeto Person`` como ``argumento`` y lo imprima en la terminal de la siguiente manera

```java

public void printPerson(Person p) {

  System.out.println("Name: " + p.getName());
  
  System.out.println("Age: " + p.getAge());
}
```

* Si queremos que este ``método`` pueda ``imprimir`` la ``información`` de ``cualquier tipo de objeto`` no solo de ``objetos`` de la ``clase Person``

  * Podemos utilizar la ``clase Class<T>`` para hacer que el ``método`` sea **"genérico"** y ``pueda trabajar`` con cualquier ``tipo de objeto``

* Para hacer esto

  * Debemos cambiar la ``signatura/cabecera/firma`` del ``método`` para que acepte un ``argumento`` de tipo ``Class<T>`` en lugar de un ``objeto Person``
  
    * La nueva ``signatura/cabecera/firma`` del método quedaría así

```java
public static <T> void printObject(Object obj) {
  // El cuerpo del método se implementará más adelante
}
```

* Ahora que tenemos la ``signatura/cabecera/firma`` del método

  * Debemos ``implementar`` el ``cuerpo del método``

* En el ``cuerpo del método`` podemos utilizar la ``clase Class<T>`` para obtener información sobre el ``tipo de objeto`` que se está pasando como ``argumento``

  * Luego utilizar esa información para ``imprimir`` los ``atributos`` del ``objeto`` en la ``terminal``

* Para hacer esto debemos utilizar el ``método getDeclaredFields()`` de la ``clase Class<T>`` para obtener una ``lista`` de los ``atributos`` del objeto

  * Podemos ``iterar`` sobre esta ``lista`` y utilizar los ``métodos get()`` y ``getName()`` de la ``clase Field`` para obtener el valor y el nombre de cada atributo respectivamente

* Finalmente ``imprimir`` esta información en la terminal para que el usuario pueda verla

* El cuerpo del ``método`` quedaría así

```java
 public static <T> void printObject(T obj) {

  Class<?> cls = obj.getClass();

  Field[] fields = cls.getDeclaredFields();

  for (Field field : fields) {
   try {
    System.out.println(field.getName() + ": " + field.get(obj));
   } catch (IllegalAccessException e) {
    e.printStackTrace();
   }
  }
 }
```

* Podemos utilizar este ``método`` para ``imprimir`` la información de cualquier tipo de objeto en la terminal

### Ejemplo de impresión

* Si queremos imprimir la información de un ``objeto Person`` podemos pasar una ``instancia`` de la ``clase Person`` como ``argumento`` al ``método printObject()`` de la siguiente manera

```java
Person p = new Person("John Doe", 30);
printObject(p);
```

* Imprimirá en la ``terminal`` la información del ``objeto Person``

```cmd
Name: John Doe
Age: 30
```

## En resumen

* ``Clase Class<T>`` permite

  * Obtener información sobre ``tipos de objetos`` en ``tiempo de ejecución``
  
  * ``Crear`` código más flexible y reutilizable

* Utilizamos la ``clase Class<T>`` para

  * Crear un ``método genérico`` que puede ``imprimir`` la ``información`` de cualquier ``tipo de objeto`` en la terminal
