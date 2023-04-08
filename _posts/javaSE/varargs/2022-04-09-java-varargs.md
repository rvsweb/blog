---
layout: single
title: Java - Varargs
date: 2022-03-27
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
  - java-varargs
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Permite pasar cualquier numero de argumentos del tipo especificado a los **argumentos** del método en cuestión

  * El método principal puede aceptar cualquier cantidad de **argumentos** del mismo tipo

  * Hace **referencia** a un **array de elementos** del tipo que aparece a la izquierda de la declaración

### Ejemplo de código

```java
public class VarargsEjemplo {

	/**
	 * Procedimiento de clase o estático
	 * 
	 * Muestra una lista de elementos de tipo enteros
	 * 
	 * @param numbers - int [] - Recibe una lista de numeros entero
	 */
	public static void printNumbers(int... numbers) {
		for (int number : numbers) {
			System.out.println(number);
		}
	}

	public static void main(String[] args) {
		VarargsEjemplo.printNumbers(1, 2, 3);
		VarargsEjemplo.printNumbers(4, 5);
		VarargsEjemplo.printNumbers(6);

	}
}
```

## Diferencias entre arrays  y varargs

### Arrays

* Una array es un **objeto contenedor** que contiene un **número fijo** de valores de un solo tipo de dato

  * La longitud del **array** se establece cuando ``se crea`` la **array**

```java
int [] numeros = { 1, 2 ,3 }
```

### Varargs

* Función que permite pasar cualquier ``cantidad de argumentos`` del tipo especificado a un método

  * El compilador coloca automáticamente los ``argumentos`` en una ``array``

```java
// Procedimiento estático que recibe un número indeterminado de enteros
  public static void imprimirNumeros(int... numbers) {
	// Bucle iterativo que recorre el contenedor de elementos enteros 
	// nombrado como 'numbers' 
    for (int number : numbers) {
		// Mostramos por pantalla cada elemento almacenado
        System.out.println(number);
    }
}
```  
