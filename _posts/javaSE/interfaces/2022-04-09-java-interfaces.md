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

* ``Interfaz`` es una ``clase abstracta pura``

  * Todos los ``métodos`` son ``implícitamente abstractos``
  
    * No es necesario especificar la palabra clave ``"abstract"``

    ```java
    void myMethod();
    ```

## Estructura

* Declaración Interface

  * Debe empezar la ``interface`` con la letra mayúscula **I** y el nombre de la clase que vayamos a usar

  * Ejemplo : **IControlador** , **IConnector** , **IBase** , **IRemote** , **IDataBaseLocal** , **IRoot**

```java
public interface <NombreInterface> { 
  ... 
  } 
```

## Campos / Atributos

* Son ``públicos``  ``estáticos`` y ``finales``

  * **CONSTANTES**

    * Ejemplo

      ```java
      public static final int PI = 3.14159265358979323846;  
      ```

## Métodos

* Se declaran ``públicos``

* **Sin la implementación** o sin el **bloque de código**

  * Solo la ``declaración/signatura`` del ``método``

    * Ejemplo

        ```java
        public int getCalcularPI(int x , int y );
        ```

> **Son elementos del tipo abstracto**
>
> **"Te Dicen Que Hacer** pero **No Como Hacerlo"**

* Desde la versión de ``Java 8`` es posible declarar ``métodos default``

  * Contienen una implementación ``predeterminada/preestablecida``

    * Utiliza la palabra clave ``"default"`` y la ``signatura del método``

        ```java
          default void myDefaultMethod() {
            // Ejemplo : Código con la implementación 
            System.out.println("Realizar acción / tarea ");
          }
        ```

* Permiten declarar ``métodos estáticos`` igual que en las ``clases concretas``

  * Contiene una implementación ``preestablecida``

      ```java
      // Declarar método estático en una interfaz
      static void myStaticMethod() {
        // código de implementación aquí
            System.out.println("Realizar acción / tarea ");
      }
      ```

* ``Interfaz`` proporcionan

  * Un ``mecanismo de encapsulación`` de los detalles de los ``métodos`` sin forzar al ``usuario`` a utilizar la ``herencia``

    * Se define con la palabra clave ``interface``

    * Los ``métodos`` que lo componen solo tienen la ``signatura/firma`` del método en si

      * Salvo los ``métodos default`` o ``métodos estáticos`` o ``de clase`` que si contienen la implementación

* Ejemplo

  * Métodos ``default`` y ``estáticos`` o ``de clase``

```java
// Una interfaz en Java se define con la palabra clave "interface"
public interface MyInterface {
  // Todas las variables declaradas en una interfaz son public, static y final por defecto
  public static final int MY_INT = 0;
  
  // Los métodos en una interfaz son abstractos por defecto, por lo que no es necesario especificar la palabra clave "abstract"
  void myMethod();
  
  // También es posible declarar métodos con una implementación predeterminada
  // Estos métodos deben tener la palabra clave "default" y un cuerpo de método
  default void myDefaultMethod() {
    // código de implementación aquí
  }
  
  // También es posible declarar métodos estáticos en una interfaz
  static void myStaticMethod() {
    // código de implementación aquí
  }
}

// Una clase puede implementar una interfaz usando la palabra clave "implements"
public class MyClass implements MyInterface {
  // La clase debe proporcionar una implementación para todos los métodos abstractos de la interfaz
  public void myMethod() {
    // código de implementación aquí
  }
  
  // También puede usar la implementación predeterminada proporcionada por la interfaz o proporcionar una nueva implementación
  public void myDefaultMethod() {
    // nueva implementación aquí
  }
}
```

## Ejemplo de uso

* Una ``interfaz`` permite que una ``clase`` acceda a los ``métodos`` y ``datos`` de otra ``clase``
  
* Esto permite a las ``clases`` que implementen la ``interfaz`` proporcionar su propia ``implementación`` de los ``métodos`` definidos en la ``interfaz``

* Las ``interfaces`` son útiles porque ``permiten`` a los ``programadores`` crear código el cual es más ``modular`` y ``reutilizable``

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
``concreta``

  * Ss decir ; una sin ``métodos abstractos``

* ``Si se hereda`` desde una ``clase`` y no de una ``interfaz`` **solamente se puede heredar de una clase**

  * El resto de los elementos base deben ser ``interfaces``

* Todos los nombres de la ``interfaces`` se colocan después de la palabra clave ``implements`` y **separados por comas**

```java
public class Bird implements Animal, Flyable
```

* Se pueden tener tantos ``interfaces`` como se necesite y cada uno de ellos será **un tipo independiente**

  * Muestra una ``clase concreta`` combinada con varios ``interfaces`` para producir una ``nueva clase``

* La ``herencia múltiple``

  * Se refiere a la capacidad de una ``clase`` para derivar de ``múltiples clases padre``

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

  * La ``clase Bird`` implementa ambas ``interfaces``
  
    * ``Animal`` y ``Flyable``
  
  * Esto le permite tener los ``métodos declarados`` en ambas ``interfaces`` y comportarse como un ``animal`` que puede volar

* La ``herencia múltiple`` en Java se logra mediante la ``implementación`` de ``múltiples interfaces`` dentro de una ``clase concreta`` lo que le permite tener las ``propiedades`` y ``métodos`` de cada ``interfaz`` y poderlos definir a sus necesidades o lógica de negocio

## Resumen

* Una clase ``abstracta`` o ``concreta`` implementa una ``interface`` utilizará la palabra clase ``implements``

* Una ``interfaz`` es una herramienta que permite a los distintos componentes de un programa interactuar entre sí
  
* Los métodos ``no contienen`` bloques de código dentro del ``cuerpo`` a excepción de los ``métodos default`` y ``estáticos o de clase``

  * Se usan para definir sólo las ``"cabeceras/protocolos/cooperaciones"`` de los ``métodos`` o ``constantes`` que implementarán las ``clases abstractas`` o las ``clases concretas`` que los implementen

> Se utilizan para indicar que **hacer** pero **no contienen la implementación en código** salvo los métodos ``default`` y ``de clase`` o ``estáticos``

* Las ``clases concretas`` y ``clases abstractas`` que implementen las ``interfaces`` serán las que le **añadan el código** con la ``lógica de negocio`` o el funcionamiento de los ``métodos abstractos`` que se invoquen dentro de ellas
  
  * Las ``interfaces`` no pueden ``crear`` o ``instanciar objetos`` dentro de la propia ``interface``
  
    * Sólo pueden implementar las ``clases concretas`` las cuales hereden de ellas los ``métodos`` mediante el modificador `implements`

* Una **clase** del ``tipo abstracto`` o ``concreta`` no tiene límite a la hora de recibir ``interfaces``

## Recuerda

> Interface
>
> Se utiliza como previsión de lo que podremos hacer de cara al futuro en nuestra aplicación mediante las clases que hereden de las **Interfaces** que creamos o invoquemos dentro de ella
