---
layout: single
title: Java - Clase Anónima
date: 2022-12-07
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
  - java-clase-anónima
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* ``Clase`` sin nombre que define y utiliza en un solo lugar en el código

## Ventajas

* Son ``clases`` se usan sobre todo como ``escuchadores-listeners``, ``callbacks`` o ``eventos`

* Pueden acceder ``variables locales`` que se encuentren a su alcance

## Declaración

* Las ``clases locales`` son declaraciones de clase

  * las ``clases anónimas`` son ``expresiones`` → define la ``clase`` en ``otra expresión``

## Sintaxis

> Recuerda : ``Clase anónima`` → ``expresión``

* Sintaxis de una expresión de ``clase anónima``

  * Es como la invocación de un constructor excepto que hay una ``definición`` de ``clase contenida`` en un bloque de código

* Considere la ``instanciación`` del objeto ``frenchGreeting``

```java

HelloWorld frenchGreeting = new HelloWorld() {

  String name = "tout le monde";

  public void greet() {
    greetSomeone("tout le monde");
} 

  public void greetSomeone(String someone) {
    name = someone;
    System.out.println("Salut " + name);
  }
};

```

* La ``expresión`` de  ``clase anónima`` consta

  1. El ``nuevo operador``

  2. El nombre de una ``interfaz`` para implementar o una ``clase`` para extender

* Ejemplo

  * La ``clase anónima`` implementa la ``interfaz HelloWorld``

* ``Paréntesis`` que contienen los ``argumentos`` de un ``constructor`` , como una ``expresión`` de ``creación`` de ``instancia`` de ``clase concreta``

    > Cuando implementa una interfaz no hay un constructor por lo que usa un par de paréntesis vacíos, como en este ejemplo

* El ``cuerpo`` que es una de ``declaración de clase``

  * Se permiten las ``declaraciones de métodos`` pero ``no`` las ``declaraciones``

* ``Definición`` de ``clase anónima`` es una ``expresión`` que debe ser parte de una ``declaración``

  * Ejemplo
  
    * La expresión de ``clase anónima`` es parte de la ``instrucción`` que ``instancia`` el ``objeto frenchGreeting``

      > Esto explica por qué hay un punto y coma después de la llave de cierre

## Ejemplos

### 1. Ejemplo

* Tenemos interfaz llamada ``Operacion`` que tiene un ``método`` llamado ``realizarOperacion``  toma ``dos enteros`` y ``devuelve`` su suma

* Podemos ``implementar`` esta ``interfaz``

```java
// 
    Operacion suma = new Operacion() {

      public int realizarOperacion(int a, int b) {
        return a + b;
      }
    };
```

* Explicación

  * Estamos creando una ``clase anónima`` que implementa la interfaz "Operacion" y redefine el ``método realizarOperacion()`` para que devuelva la suma de dos números

  * La ``clase anónima`` se crea en el ``mismo lugar donde se utiliza`` y ``no tiene un nombre propio``

  * Ejemplo en el que se puede usar una ``clase anónima`` es cuando ``se necesita`` heredar de una ``clase existente`` y ``redefinir`` algunos de sus métodos

### 2. Ejemplo

* Tenemos una clase llamada ``Persona`` que tiene un método ``saludar()`` que imprime un saludo por pantalla

* Podemos ``crear`` una ``clase anónima`` que ``herede`` de ``Persona`` y redefina el método ``saludar()`` de la siguiente forma

```java
Persona saludadorEspecial = new Persona() {

  public void saludar() {
    System.out.println("Hola, ¿cómo estás?");
  }
};
```

* Explicación

  * Estamos creando una ``clase anónima`` que hereda de ``Persona`` y redefine su ``método saludar()`` para que ``imprima`` un saludo ``diferente`` al ``original``
  
    * La ``clase anónima`` se ``crea`` y se ``utiliza`` en el ``mismo lugar`` y no tiene un nombre propio

### 3. Ejemplo

* La clase ``HelloWorldAnonymousClasses`` usa ``clases anónimas`` en las **declaraciones** de **inicialización** de ``variables locales`` ``frenchGreeting`` y ``spanishGreeting``  pero usa una ``clase local`` para la inicialización de la ``variable englishGreeting``

```java

public class HelloWorldAnonymousClasses {
  
        interface HelloWorld {
            public void greet();
            public void greetSomeone(String someone);
        }
  
    public void sayHello() {
        
        class EnglishGreeting implements HelloWorld {
            
            String name = "world";
            
            public void greet() {
                greetSomeone("world");
            }
            
            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Hello " + name);
            }
        }
      
        HelloWorld englishGreeting = new EnglishGreeting();
        
        HelloWorld frenchGreeting = new HelloWorld() {
            
            String name = "tout le monde";
            
            public void greet() {
                greetSomeone("tout le monde");
            }

            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Salut " + name);
            }
        };
        
        HelloWorld spanishGreeting = new HelloWorld() {
            
            String name = "mundo";
            
            public void greet() {
                greetSomeone("mundo");
            }
            
            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Hola, " + name);
            }
        };

        englishGreeting.greet();
        frenchGreeting.greetSomeone("Fred");
        spanishGreeting.greet();
    }

    public static void main(String... args) {

        HelloWorldAnonymousClasses myApp = new HelloWorldAnonymousClasses();
        myApp.sayHello();
    }            
}
```

## Resumen

* Permite ``declarar`` e ``instanciar`` una ``clase`` al mismo tiempo

* Son como ``clases locales`` excepto que ``no tienen nombre``

> Se utiliza para usar una ``clase local`` una sola vez
