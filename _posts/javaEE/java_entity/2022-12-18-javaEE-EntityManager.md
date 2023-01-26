---
layout: single
title: JavaEE - EntityManager
date: 2022-12-18
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
  - java-entityManager
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* ``Interfaz`` proporciona conjunto ``métodos`` para gestionar ``entidades``

* Las ``entidades`` son ``objetos`` representan ``tablas`` de una ``base de datos``

  * Se utilizan en el contexto de la ``persistencia`` de ``Objetos Orientados a Relaciones`` → ``(ORM)``

* Es una de las principales ``interfaces`` de la ``API`` de ``Persistencia de Java`` (``JPA``)

  * ``JPA`` para la ``persistencia`` de ``objetos`` en ``Java`` se utiliza
  
    1. ``Mapear/rastrear`` objetos a ``tablas`` de ``bases de datos``

    2. Para gestionar la ``persistencia`` de estos ``objetos``

* Se utiliza para realizar ``operaciones`` de ``persistencia`` en una ``base de datos``

  1. ``Crear``, ``actualizar``, ``eliminar`` y ``recuperar`` **entidades**
  
  2. ``Ejecutar consultas`` y ``obtener resultados`` en forma de listas de ``entidades`` o ``valores escalares``

* ``Interface`` se implementa con una ``clase`` de proveedor de ``persistencia``

  * Ejemplo : ``Hibernate`` o ``EclipseLink``

* Implementación de ``EntityManager`` mediante ``Hibernate: org.hibernate.jpa.HibernateEntityManager`` utilizando la ``clase Persistence``

## Ejemplo

* Se utiliza el ``método createEntityManagerFactory`` de la ``clase Persistence`` para obtener una instancia de ``EntityManagerFactory``

* Se invoca el ``método createEntityManager`` de ``EntityManagerFactory`` para obtener una instancia de ``EntityManager``

* La cadena ``"mi_configuracion"`` es el nombre del ``persistence unit`` que se define en el ``archivo persistence.xml``

```java
EntityManagerFactory emf = Persistence.createEntityManagerFactory("mi_configuracion");
EntityManager em = emf.createEntityManager();
```

* Esta ``clase`` proporciona la implementación concreta de los ``métodos`` de ``EntityManager``
  
* Se encarga de realizar las ``operaciones`` de ``persistencia``

## Uso

* Para utilizar ``EntityManager`` necesario incluir la dependencia de ``JPA`` en el proyecto

  * Crear una ``clase`` de ``configuración`` que especifique la implementación de ``JPA`` que se va a utilizar ``Hibernate``

    * Se crea una ``entidad`` que es una ``clase`` que representa a una ``tabla`` de la ``base de datos``
  
    * Se anota con el fin de ``mapearla`` a una ``tabla`` de la ``base de datos``

## Ejemplo Mapeo Clase

```java
@Entity
@Table(name = "customers")
public class Customer {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;
  private String name;
  private String email;
  // constructores, getters y setters omitidos por brevedad
}
```

* Creada la ``entidad`` se puede utilizar ``EntityManager`` para realizar operaciones de ``persistencia``

  * Necesario obtener una instancia de ``EntityManager`` a través de un ``EntityManagerFactory``
  
## Ejemplo de EntityManagerFactory

```java
EntityManagerFactory emf = Persistence.createEntityManagerFactory("myPersistenceUnit");
EntityManager em = emf.createEntityManager();
```

* Con la ``instancia`` de ``EntityManager`` se pueden realizar ``operaciones`` de ``persistencia``

* Para crear una ``entidad`` y ``persistirla`` en la ``base de datos``

```java
Customer customer = new Customer("John Smith", "john@example.com");
em.getTransaction().begin();
em.persist(customer);
em.getTransaction().commit();
```

* Para ``actualizar`` una ``entidad`` existente

```java
em.getTransaction().begin();
customer.setName("John Doe");
em.merge(customer);
em.getTransaction().commit();
```

* Para ``eliminar`` una ``entidad``

```java
em.getTransaction().begin();
em.remove(customer);
em.getTransaction().commit();
```

* Para ``recuperar`` una ``entidad`` a partir de su ``clave primaria``

```java
Customer customer = em.find(Customer.class, 1L);
```

* Para ``ejecutar`` una ``consulta`` y obtener una lista de ``entidades``

```java
TypedQuery<Customer> query = em.createQuery("SELECT c FROM Customer c WHERE c.email = :email", Customer.class);
query.setParameter("email", "john@example.com");
List<Customer> customers = query.getResultList();
```

## Resumen

* ``Interfaz`` para ``JPA`` que se utiliza para gestionar la ``persistencia`` de ``entidades`` en Java

* Realizar operaciones de persistencia en una base de datos
