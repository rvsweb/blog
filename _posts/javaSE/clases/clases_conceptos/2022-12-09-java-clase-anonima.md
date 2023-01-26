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

* Permite ``declarar`` e ``instanciar`` una ``clase`` al mismo tiempo invocando una ``interface`` o ``clase extensible`` como una ``clase abstracta``

* Son como ``clases locales`` excepto que ``no tienen nombre``

> Se utiliza para crear y usar una ``clase local`` una sola vez

## Ventajas

* Son ``clases`` se usan sobre todo como ``escuchadores-Listeners``, ``Callbacks`` o ``Eventos``

* Pueden acceder a ``variables locales`` que se encuentren a su entorno

## Declaración

* Las ``clases locales`` son declaraciones de clase

  * las ``clases anónimas`` son ``expresiones`` → define la ``clase`` en ``otra expresión``

## Sintaxis

> Recuerda : ``Clase anónima`` → ``expresión``

* ``Sintaxis`` de una ``expresión`` de ``clase anónima``

  * Es como la invocación de un ``constructor`` excepto que hay una ``definición`` de ``clase contenida`` en un ``bloque de código``

* Considere la ``instanciación`` del objeto ``frenchGreeting``

```java
//                             Clase Anónima
//                                  ↓
HelloWorld frenchGreeting = new HelloWorld() {

  String name = "tout le monde";

// Método heredados de la interface HelloWorld e implementados in situs
  public void greet() {
    greetSomeone("tout le monde");
} 

// Método heredados de la interface HelloWorld e implementados in situs
  public void greetSomeone(String someone) {
    name = someone;
    System.out.println("Salut " + name);
  }
};

```

* La ``expresión`` de  ``clase anónima`` consta

  1. El ``nuevo operador``

  2. El nombre de una ``interfaz`` para implementar o una ``clase`` para ``extender``

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

## Acceso Variables Locales (Ámbito de la Aplicación)

* Puede capturar ``variables locales``

  * Tienen el ``mismo ámbito`` de acceso a las ``variables locales``

* ``Clase anónima``

  * Tiene ``acceso`` a los ``miembros`` de su ``clase envolvente``

  * No puede acceder a las ``variables locales`` en su ámbito adjunto que no estén declaradas como finales

  * Igual que las ``clases anidadas`` la ``declaración`` de un ``tipo`` **( como una variable )** en una ``clase anónima`` oculta cualquier otra declaración en el ``ámbito`` de la aplicación que tenga el mismo nombre

### Permite

* Campos → ``Fields``

* ``Métodos adicionales`` ( incluso si no implementan ningún ``método`` de la ``SuperClase`` )

* Inicializadores de instancia → ``Constructores``

* Clases locales

### Restricciones

* No puede declarar ``elementos estáticos``

* No puede declarar nuevos ``atributos miembros`` de las ``interfaces``

* Permite ``atributos miembros estáticos`` siempre que sean del ``tipo constantes``

## Ejemplos

### 1. Ejemplo

* Tenemos interfaz llamada ``Operacion`` que tiene un ``método`` llamado ``realizarOperacion``  toma ``dos enteros`` y ``devuelve`` su suma

* Podemos ``implementar`` esta ``interfaz``

```java
//                  Clase Anónima
//                       ↓
Operacion suma = new Operacion() { // Expresión completa de la Clase Anónima 

// Método heredado e implementado
      public int realizarOperacion(int a, int b) {
        return a + b;
      }
}; // Fin de la implementación de la Clase Anónima
```

* Explicación

  * Estamos creando una ``clase anónima`` que implementa la interfaz "Operacion" y redefine el ``método realizarOperacion()`` para que devuelva la suma de dos números

  * La ``clase anónima`` se crea en el ``mismo lugar donde se utiliza`` y ``no tiene un nombre propio``

  * Ejemplo en el que se puede usar una ``clase anónima`` es cuando ``se necesita`` heredar de una ``clase existente`` y ``redefinir`` algunos de sus métodos

### 2. Ejemplo

* Tenemos una clase llamada ``Persona`` que tiene un método ``saludar()`` que imprime un saludo por pantalla

* Podemos ``crear`` una ``clase anónima`` que ``herede`` de ``Persona`` y redefina el método ``saludar()`` de la siguiente forma

```java
//                          Clase Anónima
//                               ↓
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
// Clase Concreta
public class HelloWorldAnonymousClasses {
// Declaración de una interface dentro de la Clase Concreta
        interface HelloWorld {
          // Declaración de procedimientos 
            public void greet();
            public void greetSomeone(String someone);
        }
// Procedimiento de la clase HelloWorldAnonymousClasses
    public void sayHello() {

  // Clase Interna Local que hereda de la Interface HelloWorld para implementar sus método
  //                                    
  //                                    Clase Anónima
  //                                         ↓ 
        class EnglishGreeting implements HelloWorld {
            // Atributo Local
            String name = "world";
            // Procedimiento de la Clase HelloWorldAnonymousClasses
            public void greet() {
                greetSomeone("world");
            }
            
            // Procedimiento de la Clase HelloWorldAnonymousClasses
            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Hello " + name);
            }
        }
      
      // Instanciación de la clase HelloWorld
        HelloWorld englishGreeting = new EnglishGreeting();
        
      // Instanciación de la "Clase Anónima HelloWorld"
      //                                   ↓
        HelloWorld frenchGreeting = new HelloWorld() {
            
            // Atributo local
            String name = "tout le monde";
            
            // Procedimiento de la Clase HelloWorldAnonymousClasses
            public void greet() {
                greetSomeone("tout le monde");
            }

            // Procedimiento de la Clase HelloWorldAnonymousClasses
            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Salut " + name);
            }
        };
        
// Declaración de la "Interface" convertida en "Clase Anónima"
        HelloWorld spanishGreeting = new HelloWorld() {
            
            // Atributo local
            String name = "mundo";
            
            // Procedimiento implementando desde la Interface - Clase Anónima
            public void greet() {
                greetSomeone("mundo");
            }
            
            // Procedimiento implementando desde la Interface - Clase Anónima
            public void greetSomeone(String someone) {
                name = someone;
                System.out.println("Hola, " + name);
            }
        };

// Instanciaciones 
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

### 4. Ejemplo

* ``Clase anónima`` usado en una ``interface gráfica de usuario (GUI)``

  * Crea ``frame/marco`` que contiene un botón que diga ``'Hello World'``

* Invocación del método ``btn.setOnAction()`` especifica lo que sucede cuando se pulsa el botón ``Hello World``

* ``Método`` requiere un objeto de tipo ``EventHandler<ActionEvent>``

* La ``interfaz EventHandler<ActionEvent>`` contiene solo un método llamado ``handle``

* En lugar de implementar este método con una ``nueva clase``
  
  * Ejemplo usa una ``expresión`` de ``clase anónima``

* Observe que esta ``expresión`` es el ``argumento`` pasado al método ``btn.setOnAction``

* Debido a que la ``interfaz EventHandler<ActionEvent>`` contiene solo un método puede usar una ``expresión lambda`` en lugar de una ``expresión de clase anónima``

* Las ``clases anónimas`` son ideales para implementar una ``interfaz`` que contiene dos o más ``métodos``

```java

import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;

public class HelloWorld extends Application {

  public static void main(String[] args) {
    launch(args);
  } 

  @Override
  public void start(Stage primaryStage) {
    primaryStage.setTitle("Hello World!");
    Button btn = new Button();
    btn.setText("Say 'Hello World'");
    
    //                  AQUÍ SE DECLARA : Clase Anónima    
    //                       ↓
    btn.setOnAction(new EventHandler<ActionEvent>() {

  @Override
  public void handle(ActionEvent event) {
    System.out.println("Hello World!");
    }
  });

  StackPane root = new StackPane();
  root.getChildren().add(btn);
  primaryStage.setScene(new Scene(root, 300, 250));
  primaryStage.show();  

  } 
}
```

### 5. Ejemplo

* Personalización de controles de interfaz de usuario

* El crea un campo de texto que solo acepta valores numéricos

* Redefine la ``implementación`` predeterminada de la ``clase TextField`` con una ``Clase Anónima`` reemplazando los ``métodos replaceText()`` y ``replaceSelection()`` heredados de la ``clase TextInputControl``

```java

import javafx.application.Application;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.geometry.Insets;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.GridPane;
import javafx.scene.layout.HBox;
import javafx.stage.Stage;

public class CustomTextFieldSample extends Application {
 
  final static Label label = new Label();

 @Override
 public void start(Stage stage) {

  Group root = new Group();
  Scene scene = new Scene(root, 300, 150);

  stage.setScene(scene);
  stage.setTitle("Text Field Sample");

  GridPane grid = new GridPane();
  grid.setPadding(new Insets(10, 10, 10, 10));
  grid.setVgap(5);
  grid.setHgap(5);
 
  scene.setRoot(grid);
  
  final Label dollar = new Label("$");

  GridPane.setConstraints(dollar, 0, 0);
  grid.getChildren().add(dollar);

  final TextField sum = new TextField() {
    
   @Override
   public void replaceText(int start, int end, String text) {
    if (!text.matches("[a-z, A-Z]")) {
     super.replaceText(start, end, text);
    }
    label.setText("Enter a numeric value");
   }

   @Override
   public void replaceSelection(String text) {
    if (!text.matches("[a-z, A-Z]")) {
     super.replaceSelection(text);
    }
   }
  };

  sum.setPromptText("Enter the total");
  sum.setPrefColumnCount(10);
 
  GridPane.setConstraints(sum, 1, 0);
  grid.getChildren().add(sum);
 
  Button submit = new Button("Submit");
 
  GridPane.setConstraints(submit, 2, 0);
  grid.getChildren().add(submit);
 
//                        Clase Anónima
//                             ↓ 
  submit.setOnAction(new EventHandler<ActionEvent>() {
 
   @Override
   public void handle(ActionEvent e) {
    label.setText(null);
   }
  });
 
  GridPane.setConstraints(label, 0, 1);
  GridPane.setColumnSpan(label, 3);
 
  grid.getChildren().add(label);
  
  scene.setRoot(grid);
  stage.show();
 }

 public static void main(String[] args) {
  launch(args);
 }
}
```
