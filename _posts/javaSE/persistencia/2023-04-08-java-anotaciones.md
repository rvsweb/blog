---
layout: single
title: Java - Anotaciones
date: 2023-04-08
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-JPA
  - java-persistencia
tags:
  - java-anotaciones
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Anotaciones en ``JPA`` (Java Persistence API) 

* Se utilizan para ``mapear objetos`` Java a ``tablas`` de base de datos con las columnas 

* Etiquetas que se colocan sobre 
  
  * Clases
  
  * Atributos 
  
  * Métodos 
  
* Indica cómo ``mapear`` una tabla de base de datos

* JPA es una especificación de Java que proporciona una forma estándar y simplificada de ``mapear objetos`` Java a ``tablas`` de ``base de datos relacionales``

  * Se utilizan para definir la estructura de la base de datos y las relaciones entre las ``entidades`` y para ``establecer restricciones`` y validaciones sobre los datos que se almacenan en la base de datos
  
## Anotaciones JPA

@Entity

  * Se utiliza para indicar que una ``clase`` Java es una ``entidad`` que se mapea a una tabla de base de datos

@Table

  * Se utiliza para especificar el nombre de la tabla de base de datos a la que se debe mapear una ``entidad``

@Id
  
  * Se utiliza para indicar que un ``atributo`` es la ``clave primaria`` de la entidad

@GeneratedValue 

  * Se utiliza para especificar cómo se debe generar automáticamente el valor de la ``clave primaria`` de una ``entidad``

@Column

  * Se utiliza para especificar el ``nombre`` y las ``propiedades`` de una ``columna`` de base de datos que se mapea a un ``atributo`` de la ``entidad``

@ManyToOne 

  * Se utilizan para establecer relaciones entre entidades como una ``relación muchos a uno``

@OneToMany

  * Se utilizan para establecer relaciones entre entidades como una ``relación uno a muchos``

@Transient:
  
  * Se utiliza para indicar que un ``atributo`` no debe ser ``mapeado`` a una columna de base de datos

## Resumen

* Se usa para definir el ``mapeo de objetos`` Java a ``tablas`` de base de datos 

* Facilitan trabajar con datos en una aplicación Java

## Ejemplo de Anotaciones

* La clase Cliente se mapea a una tabla llamada clientes en la base de datos. 

```java
import javax.persistence.*;

@Entity // La anotación @Entity indica que esta clase es una entidad
@Table(name = "clientes") // La anotación @Table especifica el nombre de la tabla en la base de datos con la que se mapea esta entidad

public class Cliente {

    @Id // La propiedad id se mapea a la clave primaria de la tabla clientes
    @GeneratedValue(strategy = GenerationType.IDENTITY) // La anotación @GeneratedValue especifica que el valor de esta propiedad se generará automáticamente utilizando la estrategia IDENTITY

    private Long id;

// Las propiedades nombre y apellido se mapean a las columnas nombre y apellido en la tabla clientes
    @Column(name = "nombre") // La anotación @Column especifica el nombre de la columna en la base de datos con la que se mapea esta propiedad
    private String nombre;

    @Column(name = "apellido") // La anotación @Column especifica el nombre de la columna en la base de datos con la que se mapea esta propiedad
    private String apellido;

    // getters y setters de la clase Cliente

}
```