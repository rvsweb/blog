---
layout: single
title: Java - Variables de Instancia vs Variables de Clase
date: 2023-05-16
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-variables
tags:
  - java-instancia
  - java-clase
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* ``Variable de Instancia``

  * Pertenecen a cada ``objeto individual`` 
  
  * Se accede a ellas a través de una ``referencia de objeto``

## Ejemplo

```java
/**
 * En este ejemplo <br>
 * <br>
 * miVariableDeClase es una variable de clase <br>
 * <br>
 * miVariableDeInstancia es una variable de instancia <br>
 * <br>
 * Cuando creamos dos instancias de MiClase, objeto1 y objeto2, ambas variables
 * se incrementan en el constructor. <br>
 * <br>
 * Sin embargo, como miVariableDeClase es una variable de clase, su valor se
 * comparte entre ambas instancias y se incrementa dos veces. <br>
 * <br>
 * Por otro lado, como miVariableDeInstancia es una variable de instancia, cada
 * instancia tiene su propia copia y su valor solo se incrementa una vez.
 * 
 */
public class EjemploInstanciasYClase {

	public static void main(String[] args) {

		MiClase objeto1 = new MiClase();

		MiClase objeto2 = new MiClase();

// • Variables de Clase - Cada objeto comparte la misma posición de la memoria 
//	 'Todos los objetos tiene la misma copia de la variable' para toda la clase
		System.out.println("objeto1.miVariableDeClase: " + objeto1.miVariableDeClase);
//		System.out.println("objeto1.miVariableDeClase: " + MiClase.miVariableDeClase);

		System.out.println("objeto2.miVariableDeClase: " + objeto2.miVariableDeClase);
//		System.out.println("objeto2.miVariableDeClase: " + MiClase.miVariableDeClase);

// • Variables de Instancia - Cada objeto tiene su propia posición en la memoria 
//	 'Cada uno tiene su propia copia de la variable '
		System.out.println("objeto1.miVariableDeInstancia: " + objeto1.miVariableDeInstancia);
		System.out.println("objeto2.miVariableDeInstancia: " + objeto2.miVariableDeInstancia);
	}
}

/**
 * Clase Concreta 
 */
class MiClase {

	/**
	 * Variable de Clase
	 */
	public static int miVariableDeClase = 0;

	/**
	 * Variable de Instancia
	 */
	public int miVariableDeInstancia = 0;

	/**
	 * Constructor por defecto
	 */
	public MiClase() {
		miVariableDeClase++;
		miVariableDeInstancia++;
	}

}
```


