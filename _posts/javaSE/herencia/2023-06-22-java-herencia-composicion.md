---
layout: single
title: Java - Herencia & Composición
date: 2023-06-22
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-conceptos
tags:
  - java-herencia
  - java-composición
page_css: 
  - /assets/css/mi-css.css
---

## Concepto - Herencia

> Relación ``"Es un"`` entre clases

* Cuando una clase ``extiende`` a otra clase (``Hereda`` todos los ``métodos`` / ``propiedades``)

* Utiliza el comportamiento de la **clase Padre** en la subclase (``Sobrescribir`` / ``Agregar`` nnuevos comportamientos)

* ``Herencia`` se utiliza para representar ``relaciones`` jerarquicas entre ``clases`` ( Donde una ``subclase`` es un tipo más especifico de su ``clase Padre``)


```java
/**
* Ejemplo de Herencia
*/

/**
 * Clase Padre Concreta - Vehiculo
 */
public class Vehiculo {

	/**
	 * Atributo de instancia
   * 
   * Almacena el valor númerico de la velocidad
	 */
	private int velocidad;

	/**
   * Método de instancia
	 * 
	 * @param incremento la velocidad del objeto Vehiculo
	 */
	public void acelerar(int incremento) {
		velocidad += incremento;
	}

}

/**
 * Clase Hija Concreta - Vehiculo
 */
class Coche extends Vehiculo {

	/**
	 * Atributo de instancia
   * 
   * Almacena la cantidad de ruedas que tiene un Coche
   * 
	 */
	private int ruedas;

	/**
   * Constructor por defecto
	 * 
	 * @param ruedas que posee el objeto Vehiculo
	 */
	public Coche(int ruedas) {
		this.ruedas = ruedas;
	}
}
```

## Concepto - Composición

> La relación ``"tiene un`` entre clases

- En lugar de ``heredar`` comportamiento de una **clase Padre** , una clase puede contener una ``instancia`` de otra **clase** y utilizar su ``comportamiento``

- La **composición** se utiliza a menudo para representar relaciones entre ``objetos`` donde un ``objeto`` contiene o estas **compuestos** por otros ``objetos``

```java
/**
 * Ejemplo de Composición
 * 
 * En lugar de heredar comportamientos de una clase padre , 
 * una clase puede contener una instancia de otra clase y utilizar su comportamiento
 * 
 * La composición se utiliza a menudo para representar relaciones 
 * entre objetos donde un objeto contiene o esta compuestos por otros objetos
 */

/**
 * Clase Concreta Padre - Coche
 * 
 * Contiene un objeto de otra clase para implementar sus propios objetos
 *
 */
public class Coche {

	/**
	 * Atributo de instancia
	 * 
	 * Almacena la cantidad de ruedas
	 */
	private int ruedas;

	/**
	 * Atributo de instancia 
	 * 
	 * Contiene un objeto de la clase Motor para implementar los objetos de la clase Coche
   * 
	 */
	private Motor motor;

	/**
	 * Constructor parametrizado de la clase Coche
	 * 
	 * @param ruedas - Atributo de la clase Coche
	 * @param motor  - Atributo de la clase motor - Almacena un objeto Motor para poder invocar tanto los metodos / atributos propios de la clase
	 */
	public Coche(int ruedas, Motor motor) {
		this.ruedas = ruedas;
		this.motor = motor; // Objeto de la clase Motor
	}

}

/**
 * Clase Concreta Hija - Motor
 *  
 * Crea una clase que se añadira un objeto a otra clase en su definición
 *
 */
class Motor {

	/**
	 * Atributo de instancia
	 * 
	 * Almacena un elemento del tipo entero
	 */
	private int caballosDeFuerza;

	/**
	 * Constructor para inicializar objetos de la clase Motor
	 * 
	 * @param caballosDeFuerza - Almacena la cantidad de caballos de fuerza del objeto motor
	 */
	public Motor(int caballosDeFuerza) {
		this.caballosDeFuerza = caballosDeFuerza;
	}
}
```