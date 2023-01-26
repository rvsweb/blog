---
layout: single
title: Java - Field
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
  - java-API
tags:
  - java-Field
  - java-Class<T>
page_css: 
  - /assets/css/mi-css.css
---

## Definición

> Reflexión : Capacidad de un software para analizarse a sí mismo

* Pertenece al paquete ``java.lang.reflect``

* La ``clase Field`` → Representa un ``campo`` en una ``clase`` o ``objeto``

* El ``campo`` tiene el mismo propósito que todo el mecanismo de ``reflexión``

  * ``Analizar`` un componente de software
  
  * ``Describir`` sus capacidades dinámicamente en ``tiempo de ejecución`` en lugar de en ``tiempo de compilación``

* La ``reflexión`` permiten pasarlo por alto e introducir algunas características como la recuperación del valor del ``campo`` por nombre

> El **tiempo de ejecución** se refiere al tiempo que tarda un programa en ejecutarse una vez que ha sido compilado ``convertido a código de máquina que puede ser entendido por la computadora``
>
> El **tiempo de compilación** es el tiempo que tarda en convertir el código fuente de un programa a código de máquina
>
> El **tiempo de compilación** suele ser más corto que el ``tiempo de ejecución`` ya que la compilación solo se realiza una vez mientras que la ejecución puede ocurrir varias veces

### ``Campo``
  
* ``Variable`` que forma parte de la definición de una ``clase``
  
* Se utiliza para ``almacenar`` información relacionada con un ``objeto`` de esa ``clase``

#### Ejemplo Campo

* Clase llamada ``Persona`` que tiene ``campos`` para el nombre y la ``edad`` de un objeto persona
  
  * La ``clase Persona`` tiene dos campos

    * ``nombre`` y ``edad``

      * Públicos lo que significa que se pueden acceder desde cualquier parte del código.

```java
public class Persona {
  public String nombre;
  public int edad;
}
```

#### Ejemplo Completo

```java
import java.lang.reflect.Field;

public class ClaseField {

 public static void main(String[] args) {

// Creación de un usuario
  User user = new User();

// Field[] fields = User.class.getFields(); // → Devuelve un objeto de campo que refleja el campo de miembro público especificado de la clase o interfaz representada por este objeto de clase

  Field[] fields = User.class.getDeclaredFields(); // → Devuelve una matriz de objetos Field que reflejan todos los campos declarados por la clase o interfaz representada por este objeto Class

  Object value = null;

  for (int i = 0; i < fields.length; i++) {

   try {

    value = fields[i].get(user);

   } catch (IllegalArgumentException | IllegalAccessException e) {
    e.printStackTrace();
   }

   System.out.println("Valor del campo " + fields[i].getName() + " es " + value);

  }
 }
}

// Clase Concreta
class User {

 public static String name = "John Doe";

 public static String getName() {
  return name;
 }

 public static void setName(String name) {
  User.name = name;
 }
}
```

* Resultado por pantalla

```shell
Valor del campo name es John Doe
```

* Los ``campos`` se declaran dentro de la ``clase`` fuera de los ``métodos`` o ``constructores``

* Para acceder a los ``campos`` de un ``objeto`` se puede utilizar la notación de punto ``(.)`` después del nombre del ``objeto``

### Objeto

* Tenemos un ``objeto`` llamado ``juan`` de la ``clase Persona`` podríamos acceder a sus ``campos`` de la siguiente forma

#### Ejemplo de Objeto

```java
Persona juan = new Persona();
juan.nombre = "Juan";
juan.edad = 35;
```

* Hemos creando un ``nuevo objeto`` de la ``clase Persona`` y asignando valores a sus ``campos nombre`` y ``edad``

  * Una vez que tenemos acceso a los ``campos`` de un ``objeto`` podemos ``leer`` y ``modificar`` sus valores

## Resumen

* ``Clase Field`` representa un ``campo`` en una ``clase`` o ``objeto``

  * Se puede utilizar para ``acceder`` y ``modificar`` los valores ``almacenados`` en esos ``campos``
