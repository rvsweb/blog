---
layout: single
title: Java - Interface
date: 2022-04-09
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
  - java-clase
  - java-interface
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* ``Interfaz`` es una ``clase abstracta`` pura

* Tipo ``clase especial`` que contienen

  * ``Constantes``

    * **Miembros / Atributos** definidos

      * Ejemplo : ``private static int PI = 3.14159265358979323846;``

  * ``Declaraciones / signaturas de métodos`` sin implementación o bloques de código en su interior

    * **Cabeceras / Signatura de los métodos**

      * ``public int getCalcularPI(int x , int y );``

> **Elemento de tipo abstracto** → **Te Dicen Que Hacer** pero **No Como Hacerlo**

* ``Interfaz`` proporciona un ``mecanismo de encapsulación`` de los detalles del ``métodos`` sin forzar al ``usuario`` a utilizar la ``herencia``

* Se define con la palabra ``clave interface`` y los ``métodos`` que lo componen solo tienen la ``signatura``
  
  * ``No contiene`` bloques de código dentro del ``cuerpo``

* Se usa para definir sólo la ``"Cabecera/Protocolo/Cooperación"`` de los ``métodos`` o las ``constantes`` que implementarán las **clases concretas**

  * Se utilizan para indicar que **hacer** pero **no contienen la implementación en código**

* Las ``clases concretas`` que implementen las ``interfaces`` serán las que le **añadan el código** con la ``lógica`` o funcionamiento de los ``métodos abstractos`` que se invoquen dentro de ellas
  
  * Recuerda : Las ``interfaces`` no pueden ``crear o instanciar objetos``
  
    * Sólo pueden implementar las ``clases concretas`` las cuales hereden de ellas los ``métodos`` mediante el modificador `implements`

* Una utilidad sería disponer de distintas implementaciones de la misma **clase** de las que herede la ``interfaz principal``

* Una **clase** del ``tipo abstracta`` no tiene límite a la hora de recibir ``interfaces``

* Herramienta que permite a los distintos componentes de un programa interactuar entre sí

### Estructura

* Como buena practica deben empezar la ``interface`` con la letra mayúscula **I** y el nombre de la clase que vayamos a usar

  * Ejemplo : **IControlador** , **IConnector** , **IBase** , **IRemote** , **IDataBaseLocal** , **IRoot**

```java
public interface <NombreInterface> { ... } 
```

## Ejemplo de uso

* Una ``interfaz`` puede ``permitir`` que una ``clase`` acceda a los ``métodos`` y ``datos`` de otra ``clase``
  
* Las ``interfaces`` en ``Java`` se definen mediante la palabra clave ``interface`` y pueden incluir ``métodos`` y ``constantes`` pero no pueden tener ``implementaciones concretas`` dentro de los ``métodos``

* Esto permite a las ``clases`` que implementan la ``interfaz`` proporcionar su propia ``implementación`` para los ``métodos`` definidos en la ``interfaz``

* Las ``interfaces`` son útiles porque ``permiten`` a los ``programadores`` crear código que es más ``modular`` y ``reutilizable``

```java
Interface interface = new ClaseImplementaInterface();
```

### Ejemplo - Declaración

```java
// Definición de Interface
public interface IControlador {
// CONSTANTE
  private static final int ID_CONTROLADOR = 132435;
// Signatura de método
  int getControlador(); 

// Signatura de procedimiento
  void setControlador(Controlador controlador);

// Signatura de método
  boolean isControlador(Controlador controlador);
} 
```

## Herencia Multiple

* Una ``interfaz`` no tiene implementación como se explico anteriormente

  * **No hay ningún** ``tipo de almacenamiento`` asociado al ``interfaz`` ni tampoco hay nada que impida la combinación de varias ``interfaces``

* En una ``clase derivada`` no se está forzado a tener una ``clase base`` sea esta ``abstracta`` o
``concreta`` es decir ; una sin ``métodos abstractos``.

* ``Si se hereda`` desde una ``clase`` y no ``interfaz`` **solamente se puede heredar de una clase**

  * El resto de los elementos base deben ser ``interfaces``

* Todos los nombres de la ``interfaces`` se colocan después de la palabra clave ``implements`` y **separados por comas**

```java
public class Bird implements Animal, Flyable
```

* Se pueden tener tantos ``interfaces`` como se quiera y cada uno de ellos será un tipo independiente

  * Muestra una ``clase concreta`` combinada con varios ``interfaces`` para producir una ``nueva clase``

* La ``herencia múltiple`` en Java se refiere a la capacidad de una ``clase`` para derivar de ``múltiples clases padre``

* Las ``clases`` solo pueden tener una ``sola clase padre directa`` pero pueden implementar ``múltiples interfaces`` lo que le da algo de las características de la ``herencia múltiple``

### Ejemplo Herencia Multiple

* Tenemos las siguientes ``clases`` y ``interfaces``

```java
public interface Animal {
  public void makeSound();
}

public interface Flyable {
  public void fly();
}

public class Bird implements Animal, Flyable {

  public void makeSound() {
    // Implementación código para hacer un sonido de pájaro
  }
  
  public void fly() {
    // Implementación código para volar
  }
}
```

* Explicación

  * La ``clase Bird`` implementa ambas ``interfaces`` , ``Animal`` y ``Flyable``
  
  * Esto le permite tener los ``métodos declarados`` en ambas ``interfaces`` y comportarse como un ``animal`` que puede volar

* La ``herencia múltiple`` en Java se logra mediante la ``implementación`` de ``múltiples interfaces`` dentro de una ``clase concreta`` lo que le permite tener las ``propiedades`` y ``métodos`` de cada ``interfaz`` y poderlos definir a sus necesidades

### En Resumen

> Interface <br>
> Se utiliza como previsión de lo que podremos hacer de cara al futuro en nuestra aplicación mediante las clases que hereden de las **Interfaces** que creamos o invoquemos dentro de ella

### Recuerda

* Cuando una clase ``abstracta`` o ``concreta`` implemente una ``interface`` utilizará la palabra clase ``implements``
