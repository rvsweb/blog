---
layout: single
title: Java - Final
date: 2022-01-10
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
  - java-final
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Palabra reservada

* Se usa para definir una ``entidad`` que solo se puede asignar una vez

* Una vez que se ha asignado una variable ``final`` siempre tendrá el mismo valor

* Si una ``variable final`` contiene una referencia a un objeto entonces el estado del objeto puede cambiar mediante operaciones en el objeto pero la variable siempre se referirá al mismo objeto

  * Propiedad se llama ``no transitividad``

  * Se aplica también a los ``array`` porque objetos
  
    * Si una ``variable final`` contiene una ``referencia`` a una ``matriz`` los componentes de la ``matriz`` pueden cambiarse mediante operaciones en la ``matriz`` pero la variable siempre se referirá a la misma ``matriz``

## Usos

* ``Clases``

  * Evitando que estas puedan ser heredadas
  
    * ``extends``

* ``Métodos``

  * Evitando que estos puedan ser sobrescritos

    * ``@Override``

* ``Atributos o Variables``

  * Para crear ``CONSTANTES``

    * ``public static final double PI = 3.14159265358979323849``

## Métodos finales

* Una ``clase final`` no puede crear ``subclases`` o clases ``hijas``

  * Se utiliza para obtener seguridad y eficiencia
  
    * Algunas clases de la biblioteca estándar de Java son ``finales``

      * ``java.lang.System`` y ``java.lang.String``

* Las ``subclases`` **no pueden anular ni ocultar** un ``método final``

  * Se utiliza para evitar comportamiento inesperado de una ``subclase`` que altera un ``método`` crucial para la ``función`` o la consistencia de una ``clase``

* Error declarar un método ``final`` para mejorar la eficiencia al permitir que el compilador inserte directamente el método cuando se invoque

## Final variables

* Solo se puede ``inicializar`` una vez a través

  * De un inicializador
  
  * Declaración de asignación

  * No es necesario que se inicialice en el punto de declaración
  
    * Se denomina variable ``'final en blanco'`` → ``blank final``

* ``Variable de instancia`` ``'final en blanco'``

  * De una clase debe asignarse en cada ``constructor`` de la ``clase`` en la que se declara

* Una ``variable estática`` ``'final en blanco'``

  * Asignarse en un ``inicializador estático`` de la ``clase`` en la que se declara sino se produce un ``error`` en ``tiempo de compilación``

* Si la ``variable es una referencia``

  * La ``variable`` no se puede volver a vincular para hacer ``referencia`` a otro ``objeto``

  * El ``objeto`` al que hace ``referencia`` es ``mutable`` si lo era antes

* ``Constantes finales`` en mayúsculas utilizando guiones bajos para separar las palabras

## Ejemplo : Clase y Atributos Final

```java
public class Sphere {
// PI es una constante universal, todo lo constante que puede ser algo.
public static final double PI = 3.141592653589793;

public final double radius;
public final double xPos;
public final double yPos;
public final double zPos;

Sphere(double x, double y, double z, double r) {
  radius = r;
  xPos = x;
  yPos = y;
  zPos = z;
} 
```

* Cualquier intento de reasignar el radio ``xPos`` , ``yPos`` o ``zPos`` dará como resultado un error de compilación.

* Si el ``constructor`` no establece una ``variable final`` intentar establecerla fuera del constructor generará un error de compilación.

* Si reemplazamos las tres variables de posición con una sola

```java
  public final Position pos;
```

* Donde ``pos`` es un objeto con tres propiedades ``pos.x`` , ``pos.y`` y ``pos.z``

* Entonces ``pos`` no se puede asignado pero las tres propiedades sí a menos que sean ``finales`` en sí mismas

## Final : Bucle For

* la siguiente es una declaración legal

```java

for (final SomeObject obj : someList) {
// hacer algo con el objeto
}
```

* La ``variable obj`` se vuelve a declarar en cada iteración lo que permite usar el mismo ``token`` o el mismo ``obj`` para representar ``múltiples variables``

## Variables finales en objetos anidados

* Las ``variables finales`` se pueden utilizar para ``construir`` árboles de ``objetos inmutables``

  * Construidos se garantiza que estos objetos no cambiarán más

* ``Clase inmutable`` solo debe tener ``campos finales`` y estos ``campos finales`` solo pueden tener ``tipos inmutables``

* ``Tipos primitivos`` de Java son ``inmutables`` al igual que ``String`` y algunas ``clases``

* Si la construcción anterior al tener un objeto en el árbol que no es inmutable, la expectativa no se cumple de que todo lo que se pueda alcanzar a través de la
variable final sea constante

## Ejemplo

* Código define un sistema de coordenadas cuyo origen siempre debe estar en ``(0, 0)``

  * El origen se implementa utilizando ``java.awt.Point``  y esta clase define sus ``campos`` como ``públicos`` y ``modificables``

* Al llegar al ``objeto de origen`` a través del acceso con solo ``variables finales`` ese ``objeto`` puede ``modificarse``

```java

import java.awt.Point;

public class FinalDemo {

static class CoordinateSystem {

private final Point origin = new Point(0, 0);

public Point getOrigin() { 
  return origin; 
  }
} 

public static void main(String[] args) {

CoordinateSystem coordinateSystem = new CoordinateSystem();
coordinateSystem.getOrigin().x = 15;
assert coordinateSystem.getOrigin().getX() == 0;
  }
}
```

* Declarar una ``variable final`` significa que esta ``variable apuntará`` al ``mismo objeto`` en cualquier momento

  * El ``objeto`` al que ``apunta`` la ``variable`` no está ``influenciado`` por esa ``variable final``

* El ejemplo anterior las coordenadas ``x`` e ``y`` del origen se pueden modificar

* Requisito común es que todos los campos de un ``objeto inmutable`` deben ser ``finales`` y que los ``tipos`` de estos ``campos`` deben ser ``inmutables``

* Esto descalifica ``java.util.Date`` y ``java.awt.Point`` varias ``otras clases`` para que no se utilicen ``objetos inmutables``

## Final y Clases Internas

* Cuando se define una ``clase interna anónima`` dentro del ``cuerpo`` de un ``método`` todas las ``variables declaradas finales`` en el alcance de ese ``método`` son accesibles desde dentro de la ``clase internas``

  * Para valores de objeto la ``referencia`` no puede cambiar

```java
import javax.swing.*;

public class FooGUI {

public static void main(String[] args) {

//inicializa componente GUI 
final JFrame jf = new JFrame("Hello world!"); //permite acceder a jf desde el cuerpo interno de la clase

jf.add(new JButton("Click me"));
// Empaquetar y hacer visible en el hilo de envío de eventos 'Event-Dispatch'
SwingUtilities.invokeLater(new Runnable() {
@Override
public void run() {
  jf.pack(); //esto sería un error de compilación si 'jf' no fuera final
  jf.setLocationRelativeTo(null);
  jf.setVisible(true);
  }
});
}
}
```

## Final en blanco - Blank Final

* ``Variable final`` cuya declaración carece de ``inicialización``

* Solo se puede asignar una vez y debe estar desasignando  cuando ocurre una ``asignación``

```java
final boolean hasTwoDigits;

if (number >= 10 && number < 100) {
  hasTwoDigits = true;
}

if (number > -100 && number <= -10) {
  hasTwoDigits = true; // error de compilación porque la variable final podría estar ya asignada.
}
```

* También debe asignar definitivamente un ``final en blanco`` →  ``blank final`` antes de acceder

```java
final boolean isEven;

if (number % 2 == 0) {
  isEven = true;
} 
System.out.println(isEven); 
```

* Tenga en cuenta que una ``variable local`` no ``final`` también debe asignarse definitivamente antes de acceder a ella

```java
boolean isEven; // *no* final

if (number % 2 == 0) {
  isEven = true;
} 
System.out.println(isEven); // Mismo error de compilación porque la variable no final no fue asignada en el caso else.
```
