---
layout: single
title: Java - Objeto
date: 2022-04-14
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
  - java-objeto
page_css: 
  - /assets/css/mi-css.css
---

## Concepto de Objeto

* Cuando declaramos una clase en Java , se está creando un nuevo tipo de datos.

* Todos los **objetos** heredan de la **clase Object**

* Todos los objetos se crean a partir de una clase

* Es un **tipo de variable** que apunta a una **dirección de memoria** especifica asignada por el operador ``new``

* Cuando creamos un **nuevo objeto** se reserva **espacio en memoria** para ese **objeto**

* Apunta al **constructor** de la **clase** lo que está ``instanciando/creando``

* Almacena el valor recibido por parte del **constructor** en el caso de que lo tengas asignados

* Se utiliza para invocar los **métodos** que contenta la **clase** a la que este apuntando

> En cierto modo se puede considerar la POO una forma de "envoltura o introducir/apuntar" un objeto dentro de otro como si fueran capas de una cebolla para así poder invocar los atributos y métodos que lo componen
>
> Cada capa es un "objeto" que tiene fijadas las características como son los atributos y métodos del objeto anterior

* Ejemplo

```java

 public static <T> void printObject(Object obj) {

// Objeto 'cls' almacena las características
// del objeto de tipo Person
// el cual "contiene/apunta" los atributos 'name' y 'age'
// y los métodos 'getName()' y 'getAge()' 
  Class<?> cls = obj.getClass();

// Objeto fields "envuelve/contiene/apunta" a los métodos de la clase genérica Class<?> 
  Field[] fields = cls.getDeclaredFields();

// Recorremos todos los elementos del array de tipo 'fields'
  for (Field field : fields) {
   try {
// Invocamos tanto el método 'getName()' de la clase Person 
// y el método get para obtener los valores almacenados
// dentro del mismo objeto 
    System.out.println(field.getName() + ": " + field.get(obj));
   } catch (IllegalAccessException e) {
    e.printStackTrace();
   }
  }
 }

 public static void main(String[] args) {
  Person p = new Person("John", 30);
  Person.printObject(p);
 }
}

// Salida
# name: John
# age: 30
```

### Proceso de creación de un Objeto

1. Declaración

* Declarar la variable de **tipo de clase**
  * Esta **variable** **no define** un **objeto** , simplemente es una **variable** que puede **referirse** a un **objeto**

> Recordar que estas **variables** ``no hacen referencia a ningún`` **objeto** ya que ``no apuntan`` a ninguna posición de memoria

```java
// Sintaxis Básica
// Tipo-Clase     nombre-variable
   String         cadena; // Se ha declarado una referencia a un objeto de tipo String
   Coche          coche; // Se ha declarado una referencia a un objeto de tipo Coche
   Gato           gato; // Se ha declarado una referencia a un objeto de tipo Coche
```

2. Instanciación e Inicialización

* Ahora le asignaremos una **copia física** del **objeto** con el que estamos trabajando y le **asignaremos** la **variable** anteriormente **declarada** que define el **tipo de dato/objeto** que sera

  * Esto realiza utilizando el operador ``new`` el cual **instancia** una **clase** asignando dinámicamente ``(en tiempo de ejecución)`` memoria para un **nuevo objeto** y devolviendo una **referencia** a esa **memoria**

    * Esta **referencia** se almacenará en la variable del **tipo de dato** anteriormente declarada

    * **Operador new** va seguido de una llamada a un **constructor** de clase el cual inicializa un **nuevo objeto**

    * El **constructor** define lo que ocurre cuando se crea un **nuevo objeto** de una clase
      * Dentro del **constructor** tienen definidos los **atributos** y **métodos** de la clase a la que corresponde

```java
// Sintaxis
// nombreVariable = new NombreClase();
   cadena         = new String(); // Ahora la variable 'cadena' se refiere a 
                                  // un objeto de clase String 
   coche          = new Coche();
   gato           = new Gato();
```

### Sintaxis Básica

```java
//   
//   Tipo de dato especifico
//    ↓
//    ↓   Variable que apunta a una dirección de memoria
//    ↓    ↓
//    ↓    ↓   Reserva espacio en la memoria para el objeto que se va a crear (HEAP)
//    ↓    ↓    ↓
//    ↓    ↓    ↓    Constructor : Método especial que crea el objeto 
//    ↓    ↓    ↓     ↓           (Mediante el método instanciado invocamos sus métodos)
//    ↓    ↓    ↓     ↓
//    ↓    ↓    ↓     ↓
    Coche c1 = new Coche();
//         ↓             ↑
//         ↓             ↑
//         → → APUNTA → →   
//               AL
//           CONSTRUCTOR
// 
```

### Arrays son Objetos

* **Arrays** son **objetos** lo que significa que se declaran igual de las clases

```java
// Declaración e Instanciación de un Array
// Tipo de Dato   Objeto      Operador     Longitud del Array
    int           arr[]    =  new           int[5];
```

### Asignación de Variables de Referencias de Objetos

* Cuando asigna una **variable de referencia de objeto** a otra **variable de referencia de objetos** no estamos **creando** una **copia del objeto** ; solo está haciendo una **copia de la referencia**

```java
// Clase para mostrar la asignación de 
//  una referencia a una variable objeto
class Caja
{
// Atributos de la Clase Caja 
double ancho;
double alto;
double profundidad;
} 

// Clase para probar el código 
public class Test
{
// Método para ejecutar el código
public static void main(String[] args)
{
// Creamos la 'variable objeto' llamada 'caja1' 
Caja caja1 = new Caja();
// Referenciamos la misma posición de memoria a la 'variable objeto' caja2 a traves de caja1
// Ahora 'caja2' y 'caja1' se refieren al mismo objeto
Caja caja2 = caja1; // La asignación de "caja1" a "caja2"
              // no asigno ninguna memoria 
              // ni copio ninguna parte del "objeto" original
              // Cualquier cambio realizado en el "objeto" a través de "caja2" afectara
              // al objeto al que se refiere "caja1" ya que son el mismo objeto

// Todos los cambios que realizados en la 'variable objeto' de "caja2" se verán reflejados en "caja1"

// Invocamos el atributo 'alto' mediante las 'variables objeto' "caja1" y "caja2"
System.out.println(caja1.alto); // Ambas variables objeto 'caja1' y 'caja2'
                             // almacenan el valor 0 del atributo 'alto'
                             // Ambas apuntan a la misma posición de la 
                             //  memoria donde se almacena el valor que es 0  
System.out.println(caja2.alto); 

// Cambiamos el valor de 'alto' a traves de la 'variable objeto' caja2
caja2.alto = 20;

// Ahora tanto la 'variable objeto' caja1 y caja2 
// tiene el mismo valor asignado al atributo alto 
System.out.println(caja1.alto);
System.out.println(caja2.alto);
}
```

### Desvinculación de un objeto

* Si ambas variables de instancia como 'caja1' y 'caja2' **apuntan/referencia** al mismo objeto , no estarán vinculadas o enlazadas de ninguna otra manera posible

```java
// Declaración e instanciación de las "variable de instancia" de la clase Caja
Caja caja1 = new Caja();
// Ahora "caja2" apunta a la misma posición de memoria que "caja1"
Caja caja2 = caja1;

// Se establece a 'null' la variable de instancia 'caja1' pero 'caja2' sigue apuntando al objeto original 'Caja()'
caja1 = null;
```

* Nota : Cuando pasamos la **referencia** de un **objeto** a un **método**, el **parámetro** que lo recibe se referirá al **mismo objeto** al que hace **referencia** el **argumento** no al de la **clase** que lo instancio
