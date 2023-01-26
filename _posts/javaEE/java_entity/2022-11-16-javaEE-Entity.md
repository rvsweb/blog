---
layout: single
title: JavaEE - Entity
date: 2022-11-02
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-ee
tags:
  - java-clase
  - java-hibernate 
  - java-jpa
  - java-entity
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Clase ``persistencia`` en una ``base de datos`` debe anotarse con ``javax.persistence.Entity``

  > Clase ↔ Entidad

* ``JPA`` utiliza ``tabla`` de ``BD`` para cada ``entidad``

* ``Instancias persistentes clase`` se representan como una ``fila`` en la ``tabla``

* ``Clases entidad`` definir ``clave principal`` tener ``constructor`` no sea ``argumento`` y ``no definitiva``

  * ``Claves`` un ``solo campo`` o ``combinación de campos``

* ``JPA`` permite generar ``clave principal`` en ``base de datos`` a través de ``anotación @GeneratedValue``

  * ``Nombre tabla`` corresponde al ``nombre clase``

    * Cambiar esto agregando la ``anotación @Table(name='NEWTABLENAME')``

* Corresponden a las ``clases`` y ``tablas`` de la ``base de datos``

* Indicando al sistema de ``persistencia`` que esta ``clase`` es una ``entidad`` que tiene que ``mapear``

  * Por cada ``clase`` habrá una ``tabla``

* ``Fichero`` de ``configuración XML`` **( Sistema antiguo )**

  * ``Archivo externo`` adjunto a la aplicación

* ``Anotaciones`` **( Mejor sistema )**

  * ``Entidad`` clase ``Java``

  * Vincular con una ``tabla`` en ``base de datos`` utilizaremos la anotación ``@Entity`` ( Indicamos al ``sistema`` de ``persistencia`` que ``clase`` es una ``entidad`` que tiene que ``mapear`` )

* Incluir ``anotación`` se importa de manera automática en el ``paquete``

  * ``package javax.persistence.Entity``

* Las ``anotaciones`` como ``@Entity`` son implementadas en ``clases``

  * Requerimos importarlas como si fuera una clase

## Anotación @Entity

* Si una clase se ``mapea`` a una ``tabla`` ( un atributo se ``mapea`` a una ``columna`` )

* ``Columna`` → ``@Column``

  * Indicando el nombre de la ``columna`` en la ``tabla``

  * Las ``columnas`` se llaman igual que los ``atributos`` no hace falta utilizar la anotación ``@Column``

  * ``@Column(name="nombre_columna")``

    * Cada ``atributo`` tendremos los métodos ``getter/setter`` para que ``Hibernate`` acceda a ellos

* Marcar ``clave primaria`` → ``@Id``

  * Columna autogenerada → ``@GeneratedValue``

  * ``@GeneratedValue(strategy=GenerationType.IDENTITY)``

* Anotación @Id

## Ejemplo

* Tabla queremos mapear una clase ( ``Entidad`` )

```java
package project.orm.manager;

import java.util.Date;

// Librerías JPA de persistencia
import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.Table;

/**
 * Tabla → mapea → Clase (Entidad)
 * 
 * Columna → mapea → Atributo
 * 
 */
@Entity // Debajo de @Entity meteremos la anotación de tabla "pedidos"
@Table(name = "pedido") // Referencia a la tabla Pedidos de la base de datos
public class Pedido {

 /**
  * Columna "Id" que conecta con la tabla 'pedido'
  * 
  * Se usa para marcar la clave primaria dentro de la tabla 'pedido' que
  * utilizamos como anotación @Id
  */
 @Column(name = "id")
 @Id // Marcamos la clave privada de la tabla "pedido"
 @GeneratedValue(strategy = GenerationType.IDENTITY) // Columna auto-generadora (Se usa para evitar tener que poner // @Column)
 private int id;

 /**
  * Columna "referencia" que conecta con la tabla 'pedido'
  */
 @Column(name = "referencia") // Indicamos el nombre de la columna en la tabla @Column
 private String referencia;

 /**
  * Columna "fecha" que conecta con la tabla 'pedido'
  */
 @Column(name = "fecha")
 private Date fecha;

 /**
  * Método de instancia
  * 
  * Obtenemos el id de la tabla pedidos
  * 
  * @return - int - id de la tabla "pedido"
  */
 public int getId() {
  return id;
 }

 /**
  * Procedimiento de instancia
  * 
  * @param id - int - establece el id de la tabla "pedido"
  */
 public void setId(int id) {
  this.id = id;
 }

 /**
  * Método de instancia
  * 
  * @return - String - devuelve la referencia de la tabla 'pedido'
  */
 public String getReferencia() {
  return referencia;
 }

 /**
  * Método de instancia
  * 
  * @param referencia - String - establece el valor de la referencia de la tabla
  *                   'pedido'
  */
 public void setReferencia(String referencia) {
  this.referencia = referencia;
 }

 /**
  * Metodo de instancia
  * 
  * @return - fecha - Date - objeto de la clase Date para establecer la fecha de
  *         la tabla 'pedido'
  */
 public Date getDate() {
  return fecha;
 }

 /**
  * Procedimiento de instancia
  * 
  * @param fecha - Date - establece la fecha de la tabla 'pedido'
  */
 public void setDate(Date fecha) {
  this.fecha = fecha;
 }
}
```
