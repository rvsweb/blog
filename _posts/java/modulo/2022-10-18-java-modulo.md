---
layout: single
title: Java - Modules
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

## Module - Modulos

* Un ``módulo`` es un conjunto de ``clases`` que pueden contener **uno** o varios ``packages`` y que define las ``dependencias`` con el resto de ``módulos`` así como la **visibilidad** de las ``clases`` que las contienen

### Inicios

* Funcionalidad a partir de la ``versión Java 9``

* Antes de la ``versión Java 9`` del 2017 ; las ``clases`` estaban organizadas a través de ``paquetes/packages`` que estaban dentro de las ``bibliotecas/libray`` de los archivos ``JAR-Java ARchive``

  * Cada ``package`` tiene una serie de ``clases`` que utilizamos en nuestro programa para realizar una tarea o instrucción

* El sistema antiguo sin ``modulos`` provocaba desorganización a la hora de trabajar con grupos de ``clases`` y las ``dependencias`` entre ellas

  * Las ``clases`` de un mismo ``paquete`` podrían estar ubicadas en 2 ``JAR`` diferentes

  * Un ``conjuntos de clases`` pertenece a un determinado ``paquete`` y ese mismo ``paquete`` pertenece a ficheros ``JAR``

* A **nivel logico** y **estructural** los ``packages`` son ubicados dentro de los archivos JAR ``Java Archice`` y este dentro de ``JSE System - LIBRARY``

```java
// Ejemplo
(JSE System - LIBRARY)
     ↓
    JAR → Java ARchive
     ↓
• Package java.io → Bits.class 
• Package java.lang → Character.class
• Package java.net → URL.class
```

* ``MAVEN`` ayudaba a la gestión de las dependencias entre un ``JAR`` y otro con los ``packages`` que estén asociados pero es una ``herramienta`` aparte del propio sistema de ``JAR``  

* La **modularidad** agrega un mayor nivel de **agregación** por encima de los ``paquetes/packages``

### Concepto

* **Java 9** utiliza el concepto de ``modulo``

```java
// Ejemplo
  MODULO
     ↓
 Dependencias    
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

* Estructura del proyecto

![modulo](/rvs.github.io/assets/images/java/modulos/modulos.png)

* La composición de un ``modulo`` sería a través del archivo ``module-info.java``

* Dentro de los ``package`` de un proyecto tendriamos
  * Las ``clases`` con la que vamos a trabajar

  * El archivo ``package-info.java`` con la referencia al ``paquete`` de las ``clases`` que queremos utilizar

```java
/**
 * Package : Gestion Principal de los elementos
 * 
 * @since 1.0
 * @author Roboto
 * @version 1.0
 * @date 19 oct 2022 16:50:33
 * 
 */
package modulo.ejemplo.basico.core;
```

* Fuera de la carpeta ``src`` del proyecto tendriamos un archivo llamado ``module-info.java``

```java
/**
 * Modulo
 *   ↓
 * Packages ---> Dependencias --- otros Modulo
 *   ↓
 * Clase 
 *
 */
module ConceptoModulo {
// Añadimos 'packages' que queremos usar en otras clases
exports modulo.ejemplo.basico.utils; // Nombre del Package con las clases a usar
exports modulo.ejemplo.basico.core; // Nombre del Package con las clases a usar
}
```

* El ``nuevo elemento`` clave del lenguaje es el ``module``

  * Un grupo reutilizable de ``paquetes`` relacionados con un **nombre único**, así como recursos (como **imágenes** y **archivos XML**) y una descriptción del ``módulo`` que especifica

* Compuesto por :

  1. Nombre del ``module``

  2. Dependencias del ``module``

      * ``Otros modulos de los que depende este modulo``

* Los ``paquetes/packages`` explicitamente pone a disposición de ``otros modulos`` ( todos los demas ``paquetes/packages`` en el ``modulo/module`` están implicitamente no disponibles para otros ``modulos``) , los servicios que ofrecen , los ``servicios`` que consumen y a qué otros ``módulos`` permite la ``reflection``

### Objetivos de los modulos

* Configuración confiable

  * La ``modularidad`` proporciona mecanismos para declarar explícitamente las dependencias entre ``módulos`` de una manera que se reconoce tanto en el momento de la ``compilación`` como en el momento de la ``ejecución``

  * El sistema puede recorrer estas ``dependencias`` para determinar el subconjunto de todos los ``módulos`` necesarios para admitir su aplicación

* **Encapsulación fuerte** : los ``paquetes`` en un ``módulo`` son accesibles para otros ``módulos`` solo si el módulo los exporta explícitamente

* Otro ``módulo`` no puede usar esos ``paquetes`` a menos que indique explícitamente que requiere las capacidades del otro ``módulo``
  * **Mejora la seguridad** de la plataforma porque los atacantes potenciales tienen acceso a menos clases

* ``Modularidad`` lo ayuda a crear diseños más ``limpios`` y ``lógicos``

* Puede crear tiempos de ejecución ``runtimes`` personalizados que consisten solo en los ``módulos/module`` que necesita para sus aplicaciones o los dispositivos a los que se dirige

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

* El cuerpo de la declaración del ``módulo/module`` puede estar ``vacío`` o puede ``contener`` varias ``directivas`` de ``módulo`` incluidas

#### requires

* Una ``directiva`` de ``módulo`` requiere especifica que este ``módulo`` depende de otro módulo; esta relación se denomina ``dependencia`` de ``módulo``

  * Cada ``módulo`` debe indicar explícitamente sus dependencias

    * Cuando el módulo A ``requires`` el módulo B, se dice que el ``módulo`` A lee el ``módulo`` B y el ``módulo`` A lee el ``módulo`` B

  * Para especificar una dependencia en otro módulo, use ``requires``

```java
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
