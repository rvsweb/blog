---
layout: single
title: Java - Secuencias de escape
date: 2023-05-12
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
  - java-secuencias de escape
  - java-delimitadores
tags:
  - java-version hexadecimal
  - java-version octal
page_css: 
  - /assets/css/mi-css.css
---

## Conceptos

* Son combinaciones de caracteres con un uso especial 

* Se utilizan dentro de las ``cadenas de texto`` para representar ``caracteres especiales`` o controlar el ``formato de salida``

* Comienzan con el carácter de **barra invertida** `\` seguido de ``uno o más caracteres`` 

* Indican la ``acción`` o el ``carácter especial`` que se desea representar

* Son ``interpretadas`` por el ``compilador`` o el ``intérprete`` de ``Java`` 

* Se reemplazan por el ``carácter`` correspondiente antes de que se ``procese`` la ``cadena de texto``

## Secuencias de escape más comunes

```java
// \n: Salto de línea.
System.out.println("Hola,\n¿Cómo estás?");

// \t: Tabulación.
System.out.println("Nombre:\tJuan");

// \": Comilla doble.
System.out.println("Ella dijo: \"Hola\"");

// \': Comilla simple.
System.out.println("Es un día \'soleado\'");

// \\: Barra invertida.
System.out.println("La ruta del archivo es C:\\Directorio\\Archivo.txt");

// \b: Retroceso (borra el carácter anterior).
System.out.println("Open\bAI"); // Imprimirá "OpeAI"

// \r: Retorno de carro (vuelve al inicio de la línea).
System.out.println("Hola\rMundo"); // Imprimirá "Mundo"
```

* ``Secuencias de escape`` permiten agregar ``caracteres especiales`` en tus ``cadenas de texto`` 

* Controlar el ``formato de salida`` en la consola 

## Secuencias de escape - Versión **Octal**

* Utilizamos el ``valor octal`` 

  * Ejemplo
  
    ``char c = \141`` → Para representar el carácter ``'a'`` en la ``tabla ASCII``

* La secuencia de escape ``'\141'`` se interpreta como el **carácter** correspondiente al valor ``octal 141``

* Utilizalo para representar caracteres en su ``versión octal`` 

  * Necesitas tres dígitos en el rango de ``000`` a ``377`` **(0 a 255 en decimal)** de la ``tabla ASCII``

* Recuerda que los caracteres representados en ``octal`` son ``interpretados`` y utilizados en el ``contexto`` del ``juego de caracteres`` utilizado en tu programa

  * Asegúrate que el ``juego de caracteres`` sea **compatible** con los ``caracteres`` que deseas representar

    ```java
    // \ooo: Tres dígitos octales que representan el valor del carácter en la tabla ASCII
    char c = '\141';  // Representación octal del carácter 'a'
    System.out.println(c);  // Imprimirá "a"
    ```

## Secuencias de escape - Versión **Hexadecimal**

* Utilizamos el ``valor hexadecimal`` 

  * Ejemplo

    ``char c = '\u0061';`` → Representación hexadecimal del carácter ``'a'``

* Utilizar el ``formato \u####`` donde ``"####"`` son cuatro ``dígitos hexadecimales`` que representan el **valor Unicode** del carácter

  * Ejemplo de cómo usar cuatro dígitos hexadecimales para representar un carácter

    ```java 
    System.out.println(c);  // Imprimirá "a"
    ```

* Utilizamos el ``valor hexadecimal \u0061`` para representar el ``carácter 'a'``

* La secuencia de escape ``'\u0061'`` se interpreta como el ``carácter`` correspondiente al valor ``Unicode hexadecimal 0061``

  * Se usa para representar caracteres en su ``versión hexadecimal`` utilizando ``cuatro dígitos hexadecimales`` que van desde ``0000`` a ``FFFF`` en la ``tabla Unicode``

### Ejemplo de código usando secuencia **Octal** y **Hexadecimal**

* Usar las secuencias de ``escape octales`` en ``Java`` para representar caracteres

  * Ejemplo
  
    * Utilizamos una ``secuencia de escape`` **octal** ``( \101 )`` 
    
      * Para representar el ``carácter 'A'`` en ``base octal``

    * Utilizamos una ``secuencia de escape`` **Unicode** ``( \u0041 )`` 
      
      * Para representar el mismo carácter en ``base hexadecimal``

```java
// Ambos caracteres se imprimen como 'A' en la consola.
public class Main {

public static void main(String[] args) {

  char c1 = '\101'; // Representa el carácter 'A' en base octal

  char c2 = '\u0041'; // Representa el carácter 'A' en base hexadecimal

  System.out.println(c1); // Imprime 'A'

  System.out.println(c2); // Imprime 'A'
  
  }
}
```

* **Recuerda** 

  * Lo caracteres representados en ``hexadecimal`` son ``interpretados`` 
  
    * Utilizados el contexto del ``juego de caracteres`` utilizado en ``Java``

* Establece que el ``juego de caracteres`` es compatible con los ``caracteres`` que deseas representar






