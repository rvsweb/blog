---
layout: single
title: Java - Métodos
date: 2022-03-23
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-metodos
tags:
  - java-manual
page_css: 
  - /assets/css/mi-css.css
---

## Definición

* Es una ``guía detallada`` , ``secuencial`` y ``ordenadamente`` de ``instrucciones`` dentro de un **bloque de código** que le indica al programa que estamos desarrollando ``como realizar`` una ``determinada acción/tarea`` dentro del programa que estemos ejecutando en ese momento

* Mecanismo que permiten ``agrupar`` este ``conjunto de instrucciones`` para realizar una ``determinada tarea``

* Podemos llamarla a través de una **clase** o un **objeto** dentro de nuestro programa

## Tipos de Instrucciones Básicas

### Métodos

* ``Instrucción/Tarea`` que pertenece a un **objeto** de la **clase especifica**
  
* Puede ``recibir o no`` una serie de parámetros **"aunque lo normal sería que no los llevase declarados"** dentro de la sintaxis de la declaración del método

* ``Devuelve`` un valor al final de la ejecución del mismo que puede ser incorporado a otro **método** igual o distinto o almacenarlo dentro de una ``variable`` , un ``objeto`` o un ``método`` del mismo tipo y que ``tenga`` el mismo ``tipo de valor`` al devuelto por el ``método`` que lo invoca

* Esta ``instrucción`` se suele ``usar`` para ``devolver valores`` de todo tipo

  * Por eso se le suele poner el prefijo ``get`` y el nombre que defina su función dentro del **método**

* Puede tener más de una ``copia`` de este ``método`` en toda la ``clase principal``

```java
/**
* Declaración
* 
* Método de instancia 
*/
public int getSuma(){
  return a + b;
}

// Instanciación del metodo mediante la clase que lo alberga
Sumar suma = new Sumar();
suma.getSuma();
```

### Procedimientos

* ``Instrucción`` que pertenece a un **objeto** de una **clase especifica**

  * Puede recibir **parámetros o no**

* ``Ejecuta`` una **acción especifica** pero **no devuelve ningún tipo de valor**

  * Va acompañado del modificador ``void``

* Se suele ``usar`` para **establecer** los valores de los **atributos** de la **clase** en la que nos encontramos entre otras opciones con el objetivo de realizar ciertas tareas

  * Se le coloca el prefijo de ``set`` dentro de la sintaxis de la declaración del ``procedimiento`` y el ``nombre`` que defina su función principal dentro de la clase

* Puede tener más de una ``copia de este procedimiento`` en toda la clase principal mediante la creación de objetos de la clase que lo albergue

```java
/**
* Declaración 
*
* Procedimiento de instancia para cambiar el valor de los atributos de instancia de la clase principal
*/
public void SetVariablesSuma(int a , int b){
  int a = a;
  int b = b;
}

// Instanciación del procedimiento mediante la clase que lo alberga
Sumar suma = new Sumar();
suma.setSuma(5,5);
```

### Funciones

> Concepto de static :
>
> Un solo objeto por clase ; en este caso la propia clase se encarga de invocarlo
>
> Math.pow(1,2)

* ``Instrucción``

  * Pertenece a una **clase estática** ``static`` y **no se puede**
  
  * ``instanciar = crear un objeto``  desde la ``propia clase`` en la que se encuentra

* Tiene asignado el ``modificador`` llamado ``static`` dentro de sus sintaxis para identificarse como **método** de **clase estática**

* ``Solo`` se tiene ``una copia`` de esta ``función`` en toda la ``clase principal`` y su ``invocación`` es a través de la ``clase`` que lo alberga

#### Ejemplo de Función

```java
/**
* Clase Concreta
*/
public class Matematicas{

/**
* Declaración 
*
* Método de Clase 
*/
public static void SetSuma(int a , int b){
  int a = a;
  int b = b;
}

public static void main(String [] args){
// Instanciación de la función mediante la clase estática que lo alberga

// Como se puede ver , necesita de una variable para almacenar el valor generado
int suma = Sumar().setSuma(5,5);

// Otra forma sería pero el valor no se quedará almacenado en ninguna variable u objeto
new Sumar().setSuma(5,5);
  }
}
```
