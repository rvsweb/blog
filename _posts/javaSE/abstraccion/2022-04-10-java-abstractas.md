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

## Concepto

* ``Clases especiales`` similares a las ``interfaces``

* Permite la ``implementación de los métodos`` en la propia ``clase abstracta``

* Puede ``implementar`` todos los ``métodos`` heredados de las ``interfaces``

  * Una ``clase abstracta`` puede implementar ``varias interfaces`` a la vez

    ```java
    public abstract class MiClase implements Interface1, Interface2, Interface3 {
    // Aquí va el código de la clase abstracta
    }
    ```

## Estructura básica

* ``No permiten instanciar/crear objetos`` desde la ``propia clase`` pero si se pueden ``crear objetos`` desde sus ``clases hijas`` las cuales descienden de la propia ``clase abstracta``

> **Son elementos del tipo abstracto**
>
>**Te Dicen Que Hacer** pero **No Como Hacerlo**

```java
//  Modificador de clase para convertirla en una clase abstracta
//           ↓
  public abstract class GraphicObject {

  // Espacio para declara atributos/campos

  // Espacio para declara métodos no abstractos

// Método abstracto
  abstract void draw();
 
  }
```

## Atributos : Clase Abstracta

* Permite ``declarar campos/atributos de instancia``

  * Permiten el uso de modificadores

    * ``public``
  
    * ``protected``

    * ``private``  

  * Permite ``atributos`` del tipo ``Constantes``

    * ``Variables definidas`` con el modificador ``static final``

    * Esta declaración ``nunca modificara su valor original`` en toda la ejecución del programa

      * Ejemplo :

        * ``public static final int PI = 3.14159265358979323846``

## Métodos : Clase Abstracta

* Permite el uso de los modificadores

  * ``public``
  
  * ``protected``

  * ``private``  

* Pueden contener ``métodos de instancia con o sin implementación``

  * ``Métodos sin implementación``

    * Se utilizan cuando

      * ``No sabemos`` la ``implementación`` que necesitara el ``método`` con ``respeto`` a su desempeño dentro del programa

      * Se ``implementará`` más adelante  la ``tarea/acción`` que tenga que realizar los ``métodos abstractos``

      * Las **clases hijas** tanto ``(abstractas como especificas)`` serán quienes implementen lo que aún se desconoce que deben de hacer el ``método`` dentro del programa

          ```java
            abstract void makeSound();
          ```

  * ``Métodos con implementación``

      ```java
        public void (int newX , int newY){
          // ... Implementación del método ...
        }
      ```
  
* Pueden contener ``métodos de clase con o sin implementación``

    ```java
      abstract static void makeSound(String sound);
    ```

  * Sabemos que **tarea/acciones** tienen ``que realizar``

    * Por ello se implementan en la misma ``clase abstracta`` para que las ``clases hijas`` que herede esta ``clase abstracta`` puedan invocarla y ejecutarla

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

* Si una clase es ``abstracta`` necesita ser ``extendida`` y la clase **no puede ser final**
  
  * Utiliza el modificador ``final``
  
    * ``No permite que sea extendida`` por las ``clases hijas`` de esta

* Los ``métodos abstractos`` no están implementados
  
  * ``Se implementarán`` en una ``clase hija``

* Si una ``clase`` contiene un ``método abstracto`` se le añade el modificador ``abstract`` para convertirla en una  ``clase abstracta``

  * Cuando declaremos un ``método abstracto`` **no lo implementaremos**

    * Solo declararemos la cabecera con el punto y coma al final

* Cuando una ``clase abstracta`` es una subclases proporcionan implementaciones para todos los ``métodos abstractos`` en su ``clase principal`` sino es así la subclase se declara ``abstracta``

### Ejemplo : Métodos Abstractos

```java
  public abstract int getValor();

  public abstract void moveTo(double deltaX , double deltaY);
```

* Si una ``clase hija`` hereda de una ``clase abstracta`` se tiene que indicar con la palabra clave ``extends``

  * Esta **clase** heredará todos los **atributos/propiedades** y **métodos** tanto **implementados** como **sin implementar** de la **clase abstracta**

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

* Las ``clases abstractas`` son como una especie de ``fabricas de estructuras de métodos`` sin implementar

  * Otras clases descendientes las implementaran para darle una ``funcionalidad concreta o especifica`` según la necesidad o requisitos del programa
