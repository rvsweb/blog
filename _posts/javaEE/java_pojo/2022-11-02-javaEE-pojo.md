---
layout: single
title: Java POJO
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
  - java-POJO
page_css:
  - /assets/css/mi-css.css
---

## Definición

* ``POJO`` → ``Plain Old Java Object``

## Características

* ``Clases simples`` no dependen de un ``framework``

* ``Objeto`` **no sujeto a ninguna restricción especial**

* ``Objeto POJO`` es una ``instancia`` de una ``clase`` que ``no extiende ni implementa nada``

* Surge como ``oposición`` al estándares ``EJB`` anteriores al ``3.0``

* No sigue ningún de los principales modelos , convecciones o ``framework`` de ``objetos`` de ``Java``

* ``Objeto`` de  ``Java`` no está sujeto a ninguna otra restricción que no este impuesta por la especificación del ``lenguaje Java``

### POJO no debería

1.**Extender** ``extend`` de preespecificadas ``clases``

```java
// NO EXTIENDE
public class Foo extends javax.servlet.http.HttpServlet { ... }
```

2.Implementar ``interface`` preespecificadas

```java
// NO EXTIENDE
public class Foo implements javax.ejb.EntityBean { ... }
```

3.Contener ``anotaciones`` preespecificadas

```java
// NO EXTIENDE
@javax.persistence.Entity public class Baz { ... }
```

* Por cuestiones de dificultades técnicas del ``software`` y ``framework`` compatibles con ``POJO`` requieren el uso de ``anotaciones preespecificadas`` para funciones como la ``persistencia`` funcionen

  * **objeto** ←→ ``"Clase"``

    * Fuera de los ``POJO`` se ``agregaran anotaciones`` y volvería al estado de ``POJO`` , si se eliminan las ``anotaciones`` todavía se puede considerar un ``POJO``

  * ``Objetos`` básicos sigue siendo ``POJO`` en el sentido no tienen características especiales ``como la interfaz implementada`` que convierte un ``objeto`` Java especializado

## POJO - JavaBean

* Un ``JavaBean`` es un ``POJO`` que es ``serializable``

* Tiene un ``constructor sin argumentos`` y permite el ``acceso`` a las ``propiedades`` utilizando ``métodos getter`` y ``setter`` que siguen una convención de nomenclatura simple.

  * Se pueden hacer ``referencias declarativas simples`` a las propiedades de ``JavaBeans arbitrarios``

* El código que usa una ``referencia declarativa`` de este ``tipo`` no tiene que saber nada sobre el tipo de ``bean`` y el ``bean`` se puede usar con muchos ``framework`` sin que estos ``framework`` tengan que saber el tipo exacto del ``bean``

* La especificación de ``JavaBeans`` si se implementa por completo rompe ligeramente el ``modelo POJO`` ya que la ``clase`` debe implementar la ``interfaz Serializable`` para ser un verdadero ``JavaBean``

* Muchas ``clases POJO`` que todavía se llaman ``JavaBeans`` no cumplen este requisito

* Dado que ``Serializable`` es una ``interfaz de marcador (sin método)`` esto supone que no es una gran carga

* Ejemplo de un ``componente JavaServer Faces`` ``(JSF)`` que tiene un ``enlace bidireccional`` a la ``propiedad`` de ``POJO``

```java
<h:inputText value="#{MyBean.someProperty}"/>
```

## Ejemplo 1 - Clase POJO

* Si se define una ``clase Persona`` con sus ``atributos privados`` y sus correspondientes ``getters`` y ``setters públicos`` una ``instancia`` de esta ``simple clase`` es un ``objeto POJO``

```java
/**
* Concepto de POJO
*/
public class Persona {
  public int edad;
  public double peso;
  public String nombre;
  public Persona() {
  }
  /**
   * @return the edad
   */
  public int getEdad() {
    return edad;
  }
  /**
   * @param edad the edad to set
   */
  public void setEdad(int edad) {
    this.edad = edad;
  }
  /**
   * @return the peso
   */
  public double getPeso() {
    return peso;
  }
  /**
   * @param peso the peso to set
   */
  public void setPeso(double peso) {
    this.peso = peso;
  }
  /**
   * @return the nombre
   */
  public String getNombre() {
    return nombre;
  }
  /**
   * @param nombre the nombre to set
   */
  public void setNombre(String nombre) {
    this.nombre = nombre;
  }
}
```

### Ejemplo 2 - Clase POJO

```java
public class MyBean {
  private String someProperty;
  public String getSomeProperty() {
       return someProperty;
}
public void setSomeProperty(String someProperty) {
    this.someProperty = someProperty;
  }
}
```

### Conceptos

* Los diseños que usan ``POJO`` han surgido en ``sistemas`` que ``brindan`` a los ``POJO`` una ``funcionalidad completa`` utilizada en los ``frameworks``

* ``POJO`` se centra en la ``lógica empresarial`` y no depende de los ``frameworks``

* Los ``frameworks`` de programación ``orientados a aspectos (AOP)`` agregan forma transparente la ``persistencia``, ``transacciones`` y ``seguridad``

* ``Spring`` : primera implementaciones del modelo con ``POJO``

* ``Ejemplo`` de un ``bean EJB`` que es un ``POJO``

    1. ``(EJB)`` → ``Enterprise JavaBeans``

    2. ``(JPA)`` →  ``Java Persistence API`` incluyendo ``Hibernate``

    3. ``CDI`` → ``(Contexts and Dependency Injection)`` para la plataforma ``JavaEE``

* ``Bean EJB`` es funcional y demuestra cómo ``EJB3`` aprovecha el modelo ``POJO``

  * Ejemplo

```java
public class HelloWorldService {
  
  public String sayHello() {
    return "Hello, world!";
 }
}
```

* ``Bean`` no necesita extender ninguna ``clase EJB`` ni ``implementar`` ninguna ``interfaz EJB`` ; tampoco necesita contener anotaciones ``EJB``

  * El programador declara un ````archivo XML externo`` los servicios ``EJB`` deben agregarse al ``bean``

```xml
<enterprise-beans>
    <session>
        <ejb-name>helloWorld</ejb-name>
        <ejb-class>com.example.HelloWorldService</ejb-class>
        <session-type>stateless</session-type>
    </session>
</enterprise-beans>
```

## Otros Usos

* ``JSON`` se utilizan ``POJO`` para ``serializar`` los ``objetos`` en formato ``JSON`` , con bibliotecas como ``Gson``
