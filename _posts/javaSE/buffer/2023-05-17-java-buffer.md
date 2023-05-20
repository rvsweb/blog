---
layout: single
title: Java - Buffer
date: 2023-05-17
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-basico
tags:
  - java-buffer
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Es una ``pieza de memoria`` que se utiliza para ``leer`` y ``escribir`` datos

  * Se utiliza para interactuar con el canal ``NIO`` de ``Java``

* Un ``buffer`` tiene una posición , un límite y una capacidad

* La posición es el ``índice`` del siguiente elemento que se leerá o escribirá

* El límite es el índice del primer elemento que no debe leerse o escribirse

* La capacidad es el número máximo de elementos que se pueden almacenar en el ``buffer``.

* ``Bloque de memoria`` que ``se utiliza`` para ``almacenar temporalmente`` datos

  * Mientras se ``transfieren`` entre ``dos dispositivos`` 
  
  * Entre un ``programa`` y un ``dispositivo``

* Te ``permite que`` los ``datos`` se ``escriban`` o ``lean`` en ``bloques`` más grandes

* Puede ``mejorar`` el ``rendimiento`` al ``reducir`` el ``número de operaciones`` de ``Entrada/Salida``

* Ejemplo

```java
// Crear un ``buffer`` en Java:
ByteBuffer buf = ByteBuffer.allocate(48);
```

* Existen clases de ``buffer`` en el paquete `java.nio` para trabajar con ``bufferes`` de diferentes tipos de datos 

* `ByteBuffer`

  * Es una ``clase`` de ``buffer`` que se utiliza para ``manipular datos`` de tipo ``byte``
    
  * Proporciona una serie de ``métodos`` para ``leer`` y ``escribir datos`` en el ``buffer``
    
    * Para manipular la ``posición`` y los ``límites`` del ``buffer``

  * ``Clase`` preferida debido a que el tipo de ``dato byte`` es el ``más versátil``

    * Ejemplo
      
      * Podemos usar ``bytes`` para componer otros tipos ``primitivos no booleanos`` en ``JVM`` → ``(Java Virtual Machine)``

      * Podemos usar ``bytes`` para ``transferir datos`` entre ``JVM`` y ``dispositivos`` de ``entrada/salida`` externos

```java
import java.nio.ByteBuffer;

public class ByteBufferExample {
 
    public static void main(String[] args) {
// • allocate() → Asigna un nuevo búfer de bytes
//	  - La posición del nuevo búfer será cero, 
//		su límite será la capacidad (8) en este caso 
//	  - Su marca será indefinida :
//		(La marca de un ByteBuffer es un índice que se puede establecer 
//		y luego restablecer en una posición específica en el búfer.
// ♦ Cuando se llama al método allocate() de la clase ByteBuffer, 
//		la marca se establece en un "valor indefinido"
//	  - Esto significa que no se puede confiar en el valor de la marca 
//		hasta que se establezca explícitamente)
//	  - Cada uno de sus elementos se inicializará a cero y su orden de bytes será BIG_ENDIAN.
//		Tendrá un array de respaldo y su offset de array será 0
        ByteBuffer buffer = ByteBuffer.allocate(8);
//	  • Método put() relativo (operación opcional)
//		Escribe el byte dado en este búfer en la posición actual, y luego incrementa la posición. 
//              ↓
        buffer.put((byte) 1);
        buffer.put((byte) 2);
        buffer.put((byte) 3);
        buffer.put((byte) 4);

        buffer.flip();

        while (buffer.hasRemaining()) {
            System.out.print(buffer.get() + " ");
        }
    }
}
```

* `CharBuffer`

  * ``Clase`` en ``Java SE`` que representa un ``buffer`` de caracteres

  * Define ``cuatro categorías`` de operaciones sobre los ``buffer``es de caracteres

    1. ``Métodos de obtención`` 
    
      * Colocación absolutos y relativos que ``leen`` y ``escriben`` caracteres individuales
    
    2. ``Métodos de obtención masiva relativos`` 
    
      * Transfieren secuencias contiguas de caracteres desde este ``buffer`` a una ``matriz``
    
    3. ``Métodos de colocación masiva relativos``
    
      * Transfieren secuencias contiguas de caracteres desde una matriz de caracteres y una cadena o algún otro ``buffer`` de caracteres a este ``buffer``
    
    4. Métodos para ``compactar`` , ``duplicar`` y ``cortar`` un ``buffer`` de caracteres

  * Los ``buffer`` es de caracteres se pueden crear mediante asignación

  * Asigna espacio para el contenido del ``buffer`` envolviendo una ``matriz`` de ``caracteres`` o una ``cadena`` existente en un ``buffer`` 
  
  * Creando una vista de un ``buffer`` de ``bytes`` existente
  
  * Al igual que un ``buffer`` de ``bytes`` un ``buffer`` de caracteres es ``directo`` o ``no directo``
  
  * Un ``buffer`` de ``caracteres`` creado a través de los métodos ``wrap()`` de esta ``clase`` será ``no directo`` 
  
    * Un ``buffer`` de ``caracteres`` creado como una vista de un ``buffer`` de ``bytes`` será directo si el propio ``buffer`` de ``bytes`` es directo 1.
  
```java
// Ejemplo básico de cómo se puede usar un buffer en Java
import java.nio.CharBuffer;

public class BufferExample {

    public static void main(String[] args) {
// Se crea un `CharBuffer` con una capacidad de 8 caracteres. 
        CharBuffer buffer = CharBuffer.allocate(8);
// Se agregan algunos caracteres al buffer usando el método `put()`
        buffer.put('H');
        buffer.put('o');
        buffer.put('l');
        buffer.put('a');
// Después de agregar los caracteres, se llama al método `flip()` para preparar el buffer para la lectura. 
        buffer.flip();

// Se lee el contenido del buffer usando el método `get()` en un bucle while hasta que ya no queden más caracteres en el buffer
        while (buffer.hasRemaining()) {
            System.out.print(buffer.get());
        }
    }
}
```

* `IntBuffer` 

  * Clase de Java SE que representa un ``buffer`` de enteros

  * Esta clase define cuatro categorías de operaciones sobre los ``buffer`` de enteros

  * Métodos de obtención , colocación absolutos , relativos que leen y escriben enteros individuales

  * Métodos de obtención masiva relativos que transfieren secuencias contiguas de enteros desde este ``buffer`` a una matriz

  * Métodos de colocación masiva relativos que transfieren secuencias contiguas de enteros desde una matriz de enteros o algún otro ``buffer`` de enteros a este ``buffer``

  * Métodos para compactar, duplicar y cortar un ``buffer`` de enteros

  * Los ``buffer``es de enteros se pueden crear mediante la asignación, que asigna espacio para el contenido del ``buffer`` envolviendo una matriz de enteros existente en un ``buffer`` o creando una vista de un ``buffer`` de bytes existente

  * Al igual que un ``buffer`` de bytes un ``buffer`` de enteros puede ser directo o no directo

  * Un ``buffer`` de enteros creado a través de los métodos wrap() de esta clase será no directo 

  * Un ``buffer`` de enteros creado como una vista de un ``buffer`` de bytes será directo si el propio ``buffer`` de ``bytes`` es directo

* Ejemplo 

```java
// Crea un IntBuffer con capacidad para 10 enteros 
// utilizando el método allocate() de la clase IntBuffer
import java.nio.IntBuffer;

public class IntBufferExample {
    public static void main(String[] args) {
// Crear un IntBuffer con capacidad para 10 enteros
        IntBuffer buffer = IntBuffer.allocate(10);
// Colocan algunos enteros en el buffer utilizando el método put()
// Poner algunos enteros en el buffer
        buffer.put(1);
        buffer.put(2);
        buffer.put(3);
        buffer.put(4);
// Preparar el buffer para la lectura
// Antes de leer los enteros del buffer preparar para la lectura llamando al método flip() 
        buffer.flip();
// Leer los enteros del buffer
        while (buffer.hasRemaining()) {
            System.out.print(buffer.get() + " ");
        }
    }
}
```

* ``Clases`` que proporcionan ``métodos`` para ``leer`` y ``escribir`` datos en el ``buffer``

* Como para ``manipular`` la ``posición`` y los ``límites`` del ``buffer``

## Ejemplo 

* Cómo usar un `CharBuffer` en Java para ``almacenar`` y ``recuperar`` caracteres

* Hay otras operaciones que puedes realizar con ``bufferes``

 1. Como ``manipular`` la ``posición`` 
 
 2. Los ``límites`` del ``buffer`` , ``marcar`` y ``restablecer`` la posición del ``buffer``
