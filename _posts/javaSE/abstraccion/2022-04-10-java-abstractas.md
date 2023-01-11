---
layout: single
title: Java - Clase Abstracta
date: 2022-04-10
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
  - java-abstractas
page_css: 
  - /assets/css/mi-css.css
---
<!-- Revisar  -->

## Concepto

* ``Clases especiales`` similares a las ``interfaces``

## Características

* Una ``clase abstracta`` puede o no incluir ``métodos abstractos``

* Permite la ``implementación`` de los ``métodos`` en la ``clase abstracta`` como si fuera una ``clase concreta`` siempre que esos métodos no lleven en modificador ``abstract``

  * ``Métodos abstractos`` no están implementados y lleva el modificador ``abstract``

    * Tenemos que proporcionar una implementación en la ``subclase hija`` que la extienda mediante el uso del modificador ``extends``

    * Métodos abstractos ``implementados`` por las ``subclases`` o ``clases hijas`` que heredan de la ``clase abstracta``

    * No permiten el uso del modificador ``final`` en su declaración

      ```java
       //ERROR del compilador → illegal combination of modifiers: abstract and final
        abstract final void getShow();
      ```

* Ejemplo básico de un ``método abstracto``

```java
// Método Abstracto
  public abstract void metodoAbstracto();
}
```  

* Las ``clases hijas`` que ``hereden`` de la ``clase abstracta`` serán quiénes puedan ``crear`` los objetos

* Pueden tener ``métodos concretos``

  * ``Métodos`` con una ``implementación específica``

* Pueden tener ``atributos/variables`` de ``clase``

  * Accedidas desde las ``subclases hijas`` y también pueden ser protegidas mediante ``modificadores de acceso``

* Pueden tener ``constructores``

  * Utilizados para inicializar los ``atributos/campos`` de la ``clase``

* Puede ser ``extensión`` de otra ``clase``

  * Una ``clase abstracta`` puede ``extender`` otra clase concreta o ``clase abstracta`` que heredan los ``atributos`` y ``métodos`` de la ``clase padre``

* Una ``clase abstracta`` puede declarar métodos con el modificador ``final``

  * Significa que no se pueden invocar e implementar en sus ``subclases`` a partir de ella

* Pueden contener ``métodos estáticos``

  * Pertenecen a la ``clase concreta`` y no a un ``objeto`` de la ``clase abstracta``

* Pueden ser utilizadas en ``polimorfismo``

  * Una ``clase abstracta`` puede ser util en ``polimorfismo`` ya que las ``subclases`` pueden ser ``tratadas`` como ``objetos`` de la ``clase abstracta``

  * Significa que una ``variable`` de ``tipo clase abstracta`` puede ``hacer referencia`` a un ``objeto`` de una de sus ``subclases`` y pueden utilizar ``métodos`` de la ``clase abstracta`` en ``objetos`` de sus ``subclases``

  * Pueden ser ``utilizadas`` como ``clases de utilidad``

    * Una ``clase de utilidad`` es la que puede contener ``métodos estáticos`` útiles para varias ``clases``

* Las ``clases abstractas`` es una ``clase`` que se utiliza como una plantilla para crear ``subclases`` más específicas

  * Pueden ``implementar`` todos los ``métodos`` heredados de las ``interfaces``

* Una ``clase abstracta`` puede implementar ``varias interfaces`` a la vez

```java
  public abstract class MiClase implements Interface1, Interface2, Interface3 {
  // Aquí va el código de la clase abstracta
}
```

## Estructura básica

* No permiten ``instanciar/crear objetos`` desde la propia ``clase abstracta`` pero si se pueden ``crear objetos`` desde sus ``clases hijas`` las cuales descienden de la propia ``clase abstracta``

* ``No se`` pueden ``instanciar`` directamente desde la ``clase abstracta`` pero puede tener ``métodos abstractos`` y ``métodos implementados``

* Cuando una ``clase abstracta`` es una ``subclase`` o ``clase hija`` de otra ``clase abstracta``

  * La ``subclase abstracta`` proporciona implementaciones para todos los ``métodos abstractos`` en su ``clase principal``

> **Los elementos del tipo abstracto**
>
>**→ TE DICEN QUE HACER** pero **NO COMO HACERLO**
>
>**Esa tarea las realizarán las clases hijas que desciendan de la clase abstracta**

```java
//  Modificador de clase para convertirla en una clase abstracta
//           ↓
  public abstract class GraphicObject {

  // • Espacio para declara atributos/campos

  // • Espacio para declara métodos no abstractos

// Método abstracto
  abstract void draw();
 
  }
```

## Atributos : Clase Abstracta

* Permite ``declarar campos/atributos`` de instancia

  * Permiten el uso de ``modificadores``

    * ``public``
  
    * ``protected``

    * ``private``  

  * Permite ``atributos`` del tipo ``CONSTANTES``

    * ``Variables definidas`` con el modificador ``static final``

    * Esta constante ``nunca modificara su valor original`` en la ejecución del programa

```java
  public static final int PI = 3.14159265358979323846;
```

## Métodos : Clase Abstracta

* Permite el uso de los ``modificadores``

  * ``public``
  
  * ``protected``

  * ``private``  

* Pueden contener ``métodos de instancia`` con o sin implementación

  * Métodos ``sin implementación``

    * Se utilizan cuando

      * ``No sabemos`` la ``implementación`` que necesitara el ``método`` con ``respeto`` a su desempeño dentro del programa

      * Se ``implementará`` más adelante la ``operación/acción`` que tenga que realizar los ``métodos abstractos`` en las **clases hijas** que hereden de la **clase abstracta**

        * Las **clases hijas** tanto ``(abstractas como especificas)`` serán quienes implementen lo que aún se desconoce que deben de hacer el ``método`` dentro del programa

          ```java
            abstract void makeSound();
          ```

  * Métodos ``con implementación``

      ```java
        public void (int newX , int newY){
          // ... Implementación del método ...
        }
      ```
  
* Pueden contener ``métodos de clase`` con o sin implementación

    ```java
      abstract static void makeSound(String sound);
    ```

  * Sabemos que **tarea/acciones** tienen ``que realizar``

    * Por ello se implementan en la misma ``clase abstracta`` para que las ``clases hijas`` que hereden esta ``clase abstracta`` puedan invocarla e implementarla

### Ejemplo : Clase Abstracta

```java
/**
 *  Clase Básica Abstracta
 */
public abstract class ClaseAbstractaEjemplo implements InterfaceEjemplo{
  . . .
}
```

## Modificador ``abstract``

* Si una ``clase`` contiene un ``método abstracto`` se le añade el modificador ``abstract`` para convertirla en una  ``clase abstracta``

  * Cuando declaremos un ``método abstracto`` **no lo implementaremos**

    * Solo declararemos la cabecera con el punto y coma al final

* Una clase es ``abstracta`` necesita ser ``extendida`` por lo que no puede ser tener el **modificador final**
  
  * Utilizar el modificador ``final``
  
    * ``No permite que sea extendida`` por las ``clases hijas`` de esta lo cual pierde la posibilidad de la herencia e implementación

* Cuando una ``clase abstracta`` es una subclases proporcionan implementaciones para todos los ``métodos abstractos`` en su ``clase principal`` sino es así la subclase se declara ``abstracta``

### Ejemplo : Métodos Abstractos

```java
  public abstract int getValor();

  public abstract void moveTo(double deltaX , double deltaY);
```

* Si una ``clase hija`` hereda de una ``clase abstracta`` se tiene que indicar con la palabra clave ``extends``

  * Esta **clase** heredará todos los **atributos** y **métodos** tanto **implementados** como **sin implementar** de la **clase abstracta**

```java
/**
 *  Clase Básica Abstracta
 */
public class ClaseHija extends ClaseAbstractaEjemplo {
}
```

* Solo se puede heredar de una **clase Padre** o **abstracta** y se puede implementar de tantas **interfaces** se necesite

```java
/**
 *  Clase Básica Abstracta
 */
public class ClaseHija extends ClaseAbstractaEjemplo implements InterfaceEjemplo1 , InterfaceEjemplo2 {
  // . . . Implementación de la clase Hija
}
```

## Implementar Clase Concreta y Varias Interfaces a la vez desde la Clase Abstracta

* Puede extender ``"extend"`` de una sola ``clase`` sea ``clase abstracta`` o ``clase concreta``

  * **No permiten la herencia multiple**

    * Sólo puede tener una ``superclase directa``

### Ejemplo

```java

public interface Interface1 {
  
    void metodo1();
}

public interface Interface2 {
  
    void metodo2();
}

public abstract class MiClase implements Interface1, Interface2 {
   
    // La clase abstracta debe implementar todos los métodos declarados en las interfaces
    public void metodo1() {
        // Código de la implementación del método 1
    }

    public void metodo2() {
        // Código de la implementación del método 2
    }
}

// Una Clase Concreta que extiende de MiClase debe implementar cualquier método abstracto adicional
public class ClaseConcreta extends MiClase {
  
    public void metodo3() {
        // Código de la implementación del método 3
    }
}
```

#### Explicación

* ``MiClase`` es una ``clase abstracta`` que implementa las ``interfaces Interface1`` y ``Interface2``

  * Debe proporcionar una ``implementación`` de los métodos ``metodo1`` y ``metodo2``

* ``ClaseConcreta`` es una ``clase concreta`` que extiende de ``MiClase``

* Como ``MiClase`` es una ``clase abstracta```

  * ``ClaseConcreta`` debe ``implementar`` cualquier ``método abstracto`` adicional que no esté implementado en ``MiClase``

* ``ClaseConcreta`` implementa el método ``metodo3``

## Resumen

* Las ``clases abstractas`` son una especie de ``fabricas de estructuras de métodos`` sin implementar

  * Otras clases descendientes ``subclases`` las extiende mediante la implementación para darle una ``funcionalidad especifica`` según la necesidad o requisitos del programa

    * Como una ``plantilla`` para crear ``subclases`` más específicas

  * Contiene ``atributos`` , ``constructores`` , ``extender`` otras ``clases hijas`` o ``subclases``
  
  * Puede declarar los ``métodos`` como ``final`` siempre que no sean ``abstractos``
  
  * Contener ``métodos estáticos`` para ser utilizados en el ``polimorfismo``
  
  * Puede ser utilizada como ``interface`` que contiene métodos con y sin implementar  
  
  * Se utiliza como ``clase de utilidad``
