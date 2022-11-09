---
layout: single
title: JavaEE - DAO - Data Access Object
date: 2022-11-04
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
  - java-hibernate 
  - java-dao 
  - java-abstract 
page_css: 
  - /assets/css/mi-css.css
---

## Definición

* ``DAO`` → ``Data Access Object`` → **Objeto de Acceso a Datos**

## Concepto

* Utilizado para ocultar detalles de la **implementación** de la **capa de persistencia**

* Ofrecer ``interfaz`` sencilla en ciertas partes de la aplicación

> Necesario cuando se utilizan API de bajo nivel como JDBC en las que las operaciones sobre la base de datos conllevan utilización de sentencias SQL que queremos aislar de otras capas de la aplicación

## Utilidad

* ``Acceder a datos`` utilizando ``objetos`` mediante los ``métodos`` de una ``clase especializada en Java``

* Mediante ``entidades`` que se emparejan con ``tablas`` de la ``base de datos``

  * ``Métodos`` del ``DAO`` que se **emparejan** con las operaciones ``CRUD``
    1. **C** → ``Create``
    2. **R** → ``Read``
    3. **U** → ``Update``
    4. **D** → ``Delete``

> Actúa de intermediario entre la aplicación y la base de datos

* ``Clases DAO`` habrá una por ``entidad`` o ``tabla`` de la ``base de datos`` y tendremos ``métodos`` para realizar ``consultas genéricas`` o ``adaptadas`` a nuestra ``lógica de negocio``

```java
package rvs.orm.gestor;

import java.util.Date;

// Librerias de persistencia JPA
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
@Table(name = "pedido")
public class Pedido {

 /**
  * Columna "Id" que conecta con la tabla 'pedido'
  * 
  * Se usa para marcar la clave primaria dentro de la tabla 'pedido' que
  * utilizamos como anotación @Id
  */
 @Column(name = "id")
 @Id // Marcamos la clave privada de la tabla "pedido"
 @GeneratedValue(strategy = GenerationType.IDENTITY) // Columna auto-generadora (Se usa para evitar tener que poner
              // @Column)
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
  * Metodo de instancia
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
  * Metodo de instancia
  * 
  * @return - String - devuelve la referencia de la tabla 'pedido'
  */
 public String getReferencia() {
  return referencia;
 }

 /**
  * Metodo de instancia
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

* **Patrón  de diseño** que proporciona una ``interface abstracta`` hacia algún tipo de base de datos mediante otro mecanismo de ``persistencia``

  > **Patrón** aplicable a la mayoría de los **lenguajes de programación** que necesitan uso de la **persistencia** y **conexión** con una **base de datos** asociados a las aplicaciones ``Java EE`` y las ``base de datos relacionales`` a las que se accede mediante las ``API`` de ``JDBC``

* Asignar llamadas de aplicaciones de ``capa de persistencia (DAO)`` proporciona especificas operaciones de datos sin especificar detalles de la ``base de datos``

* Separa ``acceso a datos`` necesita la ``aplicación`` (términos de ``objetos`` y ``tipos de datos``) específicos del dominio (la ``interfaces pública`` de la ``DAO``)
como apoyar las necesidades de la ``DBMS especifico`` , un esquema de ``base de datos`` , etc. la implementación de la ``DAO``

## Ventajas

* Usar ``objetos`` del tipo de ``acceso a datos`` en la separación de las ``2 capas`` de la ``aplicación`` que existen y que no conocen como esta implementada una capa con respeto a la otra y que se tiene en cuenta que en el futuro puedan evolucionar de forma independiente pero mantenga la funcionalidad

  > Los detalles del almacenamiento están ocultos del resto de la aplicación

* Cambiar la ``lógica de negocio`` basada en la ``interfaz DAO`` mientras los cambios en la ``lógica de persistencia`` **no afecten** a los ``clientes`` que utilizan ``DAO`` siempre que la ``interfaz`` siga implementada

* Cambios mecanismo de ``persistencia`` implementarse ``modificando`` una implementación ``DAO`` mientras el resto de aplicación ``no se ve afectado``

## Desventajas

* ``Leaky abstraction`` → abstracción con fugas
  > Abstracción que filtra detalles que se supone que debe abstraer

* ``Duplicidad de código``

* ``Inversión de abstracción``

* La ``abstracción`` de la ``DAO`` como un **objeto** Java puede **ocultar** el **alto costo** de cada ``acceso`` a la ``base de datos`` y puede obligar a los desarrolladores a ``activar múltiples consultas`` a la ``base de datos`` para ``recuperar información`` que podría devolverse en una **sola operación** utilizando **operaciones de conjunto** de ``SQL``

## Funcionamiento

* Mueve los ``datos`` entre los ``objetos`` y los ``registros`` de la ``base de datos`` como ``intermediario``

* Pruebas unitarias del código se facilita al sustituir el ``DAO`` con una ``doble prueba`` dentro del mismo ``test`` haciendo que sean esas pruebas independientes a la ``capa de persistencia``

* Dentro del contexto de la ``programación Java`` los ``objetos de acceso a datos`` como concepto de diseño se pueden ``implementar`` de distintas formas dependiendo de la ``interfaz`` que separe las partes de ``acceso a los datos`` de la ``lógica de la aplicación`` como ``Framework`` y demás elementos que lo compongan

## Herramientas Populares de los ORM para realizar DAO

1. Frameworks : ``Hibernate, iBATIS``

2. Library : ``JPA, como Apache OpenJPA``

## Casos de uso

* ``App`` de contratos a desarrollar para 2 clientes diferentes

* Las ``especificaciones`` de la aplicación son casi idénticas para los 2 clientes

* Ambos clientes administran datos usando ``bases de datos SQL`` , pero una empresa usa una ``base de datos propietaria`` y la otra usa una ``alternativa`` de ``código abierto`` lo que implica que la ``capa de persistencia`` de su ``aplicación`` deberá implementarse de 2 maneras diferentes

* A medida que surgen nuevos clientes se necesiten implementaciones adicionales en la ``app``

* El uso del ``patrón Objeto`` de ``acceso a datos`` garantizaría la cantidad correcta de ``abstracción`` y ``encapsulación`` requerida para acceder a cualquiera de las diferentes ``bases de datos`` de ``back-end`` de la aplicación
