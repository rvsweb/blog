---
layout: single
title: Java - Modulo
date: 2022-10-18
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
  - java-modulos
page_css: 
  - /assets/css/mi-css.css
---

## Modulo - Module

* Un ``módulo`` es un conjunto de ``clases`` que pueden contener **uno** o **varios** ``packages`` y que define las ``dependencias`` con el resto de ``módulos`` así como la **visibilidad** de las ``clases`` que las contienen con el resto de proyectos

### Inicios

* Funcionalidad a partir de la ``versión Java 9``

* Antes de la ``versión Java 9`` del 2017 ; las ``clases`` estaban organizadas a través de ``packages`` que estaban dentro de las ``library`` de los archivos ``JAR-Java ARchive``

  * Cada ``package`` tiene una serie de ``clases`` que utilizamos en nuestro programa para realizar una **tarea** o **instrucción**

* El sistema antiguo sin ``modulos`` provocaba desorganización a la hora de trabajar con grupos de ``clases`` y las ``dependencias`` entre ellas

  * Las ``clases`` de un mismo ``package`` podrían estar ubicadas en 2 ``JAR`` diferentes lo que podía provocar cierta confusión a la hora de invocarlas

  * Un ``conjuntos de clases`` pertenece a un determinado ``package`` y ese mismo ``package`` pertenece a ficheros ``JAR``

* A **nivel logico** y **estructural** los ``packages`` son ubicados dentro de los archivos ``JAR-Java Archice`` y este dentro de ``JSE System - LIBRARY``

```java
// Ejemplo
(JSE System - LIBRARY)
     ↓
    JAR → Java ARchive
     ↓
Package - java.io → Bits.class 
Package - java.lang → Character.class
Package - java.net → URL.class
```

* ``MAVEN`` ayudaba a la gestión de las dependencias entre un ``JAR`` y otro con los ``packages`` que estén asociados pero es una ``herramienta`` aparte del propio sistema de ``JAR-Java ARchive``  

* La **modularidad** agrega un mayor nivel de **agregación** por encima de los ``packages``

### Concepto

* **Java 9** utiliza la palabra clave de ``module/modulo``

```java
// Ejemplo
   Module
     ↓
 Dependencies    
     ↓
  Package 
     ↓
java.lang → Character.class
```

#### Formato de Package para Modulos

```java
/**
 * Package Principal
 * 
 * Se usa para ser invocado desde otras dependencias desde una clase distinta al
 * proyecto que fue creado
 * 
 */
package com.domain;
```

### Ejemplo De Uso De Modulos

* Estructura principal de un proyecto estandar en **Java**
  
  * Desglose de todos los elementos que lo componen

![modulo](/rvs.github.io/assets/images/java/modulos/modulos.png)

1- ``JRE System Library`` - Contiene todos archivos ``JAR`` para poder ejecutar el programa

![JRE](/rvs.github.io/assets/images/java/modulos/JAR.png)

2- ``Archivos JAR`` - Listado de los archivos ``JAR`` que contiene los ``packages`` los cuales contienen las ``clases`` con las que utilizar en el programa

![JAR](/rvs.github.io/assets/images/java/modulos/jars.png)

3- ``Package`` - Contiene todas las ``clases`` compiladas para poder ser usadas en el programa que vayamos a desarrollar

![Package](/rvs.github.io/assets/images/java/modulos/package.png)

4- ``Package-Info`` - Contiene el código que relaciona el archivo con el ``package`` del proyecto

![Package_info](/rvs.github.io/assets/images/java/modulos/package_info.png)

```java
/**
 * Package Principal
 * 
 * Se usa para ser invocado desde otras dependencias desde una clase distinta al
 * proyecto que fue creado
 * 
 */
package modulo.ejemplo.basico.core;
```

5- ``Clase Principal`` - Elemento del programa donde se invocan las ``clases`` que contiene los ``packages`` del programa

![Clase](/rvs.github.io/assets/images/java/modulos/clase.png)

```java
/**
 * Package Principal del Proyecto
 */
package modulo.ejemplo.basico.core;

/**
 * Importar Clase desde otro Package
 */
import modulo.ejemplo.basico.utils.ImpuestoIVA;
/**
 * Clase Principal del package para ejecutar el pago
 */
public class Pago {
 /**
  * Almacena el pago total del Pago
  */
 private double importe;
 /**
  * Establece el valor del pago total
  * 
  * @param importe - double - establece el pago total
  */
 public void setImporte(double importe) {
  this.importe = importe;
 }
 /**
  * Devuelve el valor del pago total
  * 
  * @return double - importe total
  */
 public double getImporte() {
  return importe;
 }
 /**
  * Calcula el pago total incluyendole el IVA
  * 
  * @return double - pago total aplicando el IVA
  */
 public double getImporteIVA() {
  return ImpuestoIVA.setCalcularIVA(this.importe);
 }
}
```

6- ``modulo-info.java`` - Archivo que contiene todas las referencias a los ``packages`` que queremos usar y exportar al mismo proyecto o a otros externos con los que trabajar

![Module_info](/rvs.github.io/assets/images/java/modulos/modulos_info.png)

```java
/**
 * Modulo
 *   ↓
 * Packages ---> Dependencias --- otros Modulo
 *   ↓
 * Clases
 */
module ConceptoModuloA {
// Añadimos los 'packages' que queremos usar en otras clases en otros proyectos
// Package Principal - Contiene Clases
 exports modulo.ejemplo.basico.core; 
// Package Secundario - Contiene Clases Complementarias
 exports modulo.ejemplo.basico.utils;
}
```

* Desde un proyecto distinto invocamos los ``packages`` que se encuentra en otros ``proyectos`` para poder invocarlos y utilizarlos en otras ``clases`` distintas

7- ``modulo-info.java`` - Modulo

![Module_info](/rvs.github.io/assets/images/java/modulos/modulos_externo.png)

```java
/**
 * Modulo del proyecto que invoca las clases del otro proyecto
 */
module ConceptoModuloB {
// Invocamos el archivo 'module-info.java' 
// definido en el proyecto independiente 'ConceptoModuloA'
// para poder invocar los 'packages' y que contiene las 'clases' internas 
// con las que vamos trabajar dentro del proyecto externo 'ConceptoModuleB' 
// Utilizamos la palabra 'requires' para invocarlo
 requires ConceptoModuloA;
}
```

* La composición de un ``modulo`` sería a través del archivo ``module-info.java``

* Dentro de los ``packages`` de un proyecto tendriamos

  1. Las ``clases`` con la que vamos a trabajar

  2. El archivo ``package-info.java`` con la referencia al ``package`` de las ``clases`` que queremos utilizar dentro de nuestro ``package``

* Fuera de la carpeta ``src`` del proyecto tendriamos un archivo llamado ``module-info.java``

* El ``nuevo elemento`` clave del lenguaje Java son los ``module``

  * Un grupo reutilizable de ``packages`` relacionados con un **nombre único**, así como recursos (como **imágenes** y **archivos XML**) y una descriptción del ``módulo`` que lo especifica

* Compuesto por :

  1. Nombre del ``module``

  2. Dependencias del ``module``

      * ``Otros modulos de los que depende un modulo en cuestión``

* Los ``packages`` explicitamente pone a disposición de ``otros modulos`` ( todos los demas ``packages`` en el ``modulo`` están implicitamente no disponibles para otros ``modulos``) , los servicios que ofrecen , los ``servicios`` que consumen y a qué otros ``módulos`` permite la ``reflection`` o ``reflexión``

### Objetivos de los modulos

* Configuración confiable

  * La ``modularidad`` proporciona mecanismos para declarar explícitamente las dependencias entre ``módulos`` de una manera que se reconoce tanto en el momento de la ``compilación`` como en el momento de la ``ejecución``

  * El sistema puede recorrer estas ``dependencias`` para determinar el subconjunto de todos los ``módulos`` necesarios para admitir su aplicación

* **Encapsulación fuerte**
  * Los ``paquetes`` en un ``módulo`` son accesibles para otros ``módulos`` solo si el ``módulo`` los exporta explícitamente

* Otro ``módulo`` no puede usar esos ``paquetes`` a menos que indique explícitamente que requiere las capacidades del otro ``módulo``
  * **Mejora la seguridad** de la plataforma porque los atacantes potenciales tienen acceso a menos clases

* ``Modularidad`` lo ayuda a crear diseños más ``limpios`` y ``lógicos``

* Puede crear ``tiempos de ejecución/runtimes`` personalizados que consisten solo en los ``módulos/module`` que necesita para sus aplicaciones o los dispositivos a los que se dirige

> Si un dispositivo no es compatible con las ``GUI`` , puede crear en ``tiempo de ejecución/runtime execute`` que no incluya los módulos de la GUI, lo que reduce significativamente el tamaño del ``tiempo de ejecución``

* Antes de **Java 9** era posible usar muchas ``clases`` en la plataforma que no estaban pensadas para que las usaran las ``clases`` de una aplicación

* Migración de ``código heredado`` a ``Java 9`` modularizado sea problemática si su código depende de las ``API internas``

### Listas Modulos JDK

* **Java 9** es ``dividir`` el ``JDK`` en ``módulos`` para **admitir varias configuraciones**

* Usando el ``comando java`` de la ``carpeta bin`` de **JDK** con la opción

```bash
java --list-mmodules
```

### Declaración de Modulos

* Un ``módulo`` debe proporcionar un descriptor de módulo
  * ``metadatos`` que especifican las ``dependencias`` del ``módulo``, los ``paquetes`` que el ``módulo`` pone a disposición de otros ``módulos`` y más

* Un descriptor de ``módulo`` es la **versión compilada** de una ``declaración`` de ``módulo`` que se define en un archivo denominado ``module-info.java``

* Cada declaración de ``módulo`` comienza con la palabra clave ``module`` , seguida de un nombre de ``módulo`` único y un cuerpo de ``módulo`` encerrado entre llaves

* Sintaxis

```java
// Palabra clave
//  ↓  Nombre del Modulo 
//  ↓       ↓
module modulename{
}
```

* Ejemplo

```java
module java.base{
exports java.lang;
exports java.io;
exports java.net;
exports java.util;
}
```

### Directivas

* El cuerpo de la declaración del ``módulo`` puede estar ``vacío`` o puede ``contener`` varias ``directivas`` de ``módulo`` incluidas

#### requires

* Una ``directiva`` de ``módulo`` requiere especifica que este ``módulo`` depende de otro módulo; esta relación se denomina ``dependencia`` de ``módulo``

  * Cada ``módulo`` debe indicar explícitamente sus dependencias

    * Cuando el **módulo A** ``requires`` el **módulo B**, se dice que el **módulo A** lee el **módulo B** y el **módulo A** lee el **módulo B**

  * Para especificar una dependencia en otro ``módulo``, use ``requires``

```java
// Palabra Clave
//  ↓    Nombre del Modulo
//  ↓         ↓
requires moduleName;
```

* También hay una directiva ``requires static`` para indicar que se requiere un ``módulo`` en ``tiempo de compilación`` , pero es opcional en ``tiempo de ejecución``

  * Se conoce como una ``dependencia opcional``

##### requires transitive

* Para especificar una ``dependencia`` en otro ``módulo`` y asegurarse de que ``otros módulos`` que lean su ``módulo`` también lean esa ``dependencia`` , conocida como ``legibilidad implícita`` , el uso ``requiere transitive``

```java
requires transitive modulename;
```

* Considere la siguiente ``directiva`` de la declaración del módulo ``java.desktop``

```java
requires transitive java.xml;
```

Cualquier ``módulo`` que lea ``java.desktop`` también lee implícitamente ``java.xml``

* Si un método del ``módulo`` ``java.desktop`` devuelve un tipo del ``módulo java.xml`` , el código de los ``módulos`` que leen ``java.desktop`` pasa a depender de ``java.xml``

* ``Módulos`` estándar de Java SE deben otorgar legibilidad implícita en todos los casos como el que se describe aquí

  * Aunque un ``módulo estándar`` de **Java SE** puede depender de ``módulos no estándar``, no debe otorgarles ``legibilidad implícita``

  * Garantiza que el código que depende solo de los ``módulos estándar`` de ``Java SE`` sea portátil entre las implementaciones de ``Java SE``

### exports and exports…to

* Una ``directiva`` de ``módulo de exportaciones`` especifica uno de los ``paquetes`` del ``módulo`` cuyos tipos públicos (y sus tipos ``public``  y ``protected`` anidados) deben ser accesibles para el código en todos los demás ``módulos``

* Una ``directiva`` de ``exports…to`` le permite especificar en una lista separada por comas con precisión qué ``módulo`` o código de ``módulos`` puede acceder al ``paquete exportado`` ; esto se conoce como ``exportación calificada``

### uses

* Una ``directiva`` de ``módulo`` de usos especifica un servicio utilizado por este ``módulo``, lo que convierte al ``módulo`` en un consumidor de servicios

* Un servicio es un objeto de una clase que implementa la ``interfaz`` o ``extiende`` la ``clase abstracta`` especifica en la directiva de usos

### provides...with

* Una ``directiva`` de módulo ``provides...with`` especifica que un ``módulo`` proporciona una ``implementación`` de servicio, lo que convierte al ``módulo`` en un proveedor de ``servicios``

* La parte de la ``directiva`` que proporciona especifica una ``interfaz`` o ``clase abstracta`` enumerada en la ``directiva`` de usos de un ``módulo`` y la parte con de la ``directiva especifica`` el ``nombre de la clase`` de proveedor de servicios que implementa la ``interfaz`` o amplía la ``clase abstracta``

### open, opens, and opens…to

* Antes de ``Java 9`` , la ``reflection`` se podía usar para obtener información sobre todos los ``tipos`` en un ``paquete`` y todos los ``miembros`` de un tipo, incluso sus ``miembros privados`` , ya sea que desee permitir esta capacidad o no

* Una motivación clave del sistema de ``módulos`` es la ``encapsulación fuerte``

* De forma predeterminada, un tipo en un ``módulo`` no es accesible para otros ``módulos`` a menos que sea un ``tipo público`` y exporte su paquete

* Expone solo los ``paquetes`` que desea exponer ,  esto también se aplica a la **reflection**

* Compilar la declaración del ``módulo`` se crea el descriptor del ``módulo`` , que se almacena en un archivo llamado ``module-info.class`` en la carpeta raíz del ``módulo``

* Permitir el acceso solo en tiempo de ejecución a un paquete
  ``Allowing runtime-only access to a package``
      * Abrir una ``directiva`` de ``módulo`` de la siguiente forma

```java
opens package
```

* Indica que los ``tipos públicos`` de un ``paquete especifico`` (y sus tipos ``public`` y ``protected`` anidados) son accesibles para el código en otros ``módulos`` solo en tiempo de ejecución ``runtime execute``

* Permitir el acceso solo en ``tiempo de ejecución`` a un ``paquete`` por parte de ``módulos`` especificos
    ``Allowing runtime-only access to a package by specific modules``

* Una ``directiva`` de módulo ``opens…to`` del formulario

```java
opens package to comma-separated-list-of-modules
```

* Indica que los ``tipos públicos`` de un ``paquete especifico`` (y sus tipos ``públicos`` y ``protegidos`` anidados) son accesibles para el código en los ``módulos enumerados`` solo en tiempo de ejecución ``runtime execute``

* Todos los tipos en el ``paquete especifico`` (y todos los miembros de los tipos) son accesibles a través de la ``reflexión`` del código en los ``módulos especificos``

* Permitir el acceso solo en ``tiempo de ejecución`` a todos los ``paquetes`` en un ``módulo``
  ``Allowing runtime-only access to all packages in a module``

* Si se debe poder acceder a todos los ``paquetes`` en un ``módulo`` dado en ``tiempo de ejecución/runtime execute`` y mediante ``reflection`` a todos los demás ``módulos`` , puede abrir el ``módulo completo`` , como en

```java
open module modulename {
// module directives
}
```

### Reflection Default

* De forma predeterminada, un ``módulo`` con ``acceso reflection`` en ``tiempo de ejecución/runtime execute`` a un ``paquete`` puede ver los ``tipos públicos`` del ``paquete`` (y sus tipos ``public`` y ``protected`` anidados)

* El código de otros ``módulos`` puede acceder a todos los ``tipos del paquete`` expuesto y a todos los ``miembros`` dentro de esos tipos, incluidos los miembros ``private`` a través de ``setAccessible`` como en versiones anteriores de Java
