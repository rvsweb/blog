---
layout: single
title: Java - Stream
date: 2022-12-10
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
  - java-clase
tags:
  - java-stream
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

> Es una ``secuencia de datos`` que se puede ``leer`` o ``escribir`` de forma secuencial

* La ``API`` de ``streams`` ofrece ``métodos`` y ``opciones`` para realizar ``operaciones complejas`` y ``personalizadas``

* Característica de la ``plataforma Java`` implementada desde la ``version 1.8`` de Java en ``2014``

* Un ``stream`` se puede usar para realizar una variedad de tareas

  1. ``convertir`` el formato de los datos
  
  2. ``realizar`` cálculos mientras se leen

  3. ``escriben`` los datos

  4. ``filtrar`` datos

* Es una ``secuencia de elementos`` que se pueden procesar de ``forma secuencial`` o ``en paralelo``

* Un ``stream`` no almacena los ``elementos`` sino que aplica las ``operaciones`` sobre los elementos de la ``fuente de datos``

* Una ``colección``

* Un ``array``

* Un ``generador de números``

* Los ``streams`` se utilizan para trabajar con

  * ``Datos de entrada`` como cuando ``se lee`` información ``desde`` un archivo
  
  * ``Datos de salida`` como cuando ``escribe`` información ``hacia`` un archivo
  
  * ``Envía`` información a través de la red

## Ejemplo

* Operaciones que se pueden realizar con ``streams`` en Java

1. ``Filtrar`` elementos de una ``colección``

    * Se puede obtener un ``stream`` con los elementos mayores a 10 de una ``lista de números`` utilizando el ``método filter`` del ``stream``

```java

List<Integer> numeros = Arrays.asList(1, 5, 10, 15, 20);
List<Integer> mayoresA10 = numeros.stream()
                                  .filter(n -> n > 10)
                                  .collect(Collectors.toList());
```

2. ``Transformar`` elementos

    * Se puede obtener un ``stream`` con los nombres de los usuarios de una lista de ``objetos Usuario`` utilizando el ``método map()`` del ``stream``

```java

List<Usuario> usuarios = ...;
List<String> nombres = usuarios.stream()
                               .map(u -> u.getNombre())
                               .collect(Collectors.toList());
```

3. ``Reducir`` elementos a un valor único

    * Se puede obtener el número total de elementos de un ``stream`` utilizando el ``método count()`` del ``stream``

```java
List<Integer> numeros = Arrays.asList(1, 5, 10, 15, 20);
long cantidad = numeros.stream().count();
```

4. ``Realizar`` operaciones en paralelo
  
* Puede mejorar el rendimiento en ``sistemas`` con ``varios núcleos`` de ``procesamiento``

### Ejemplo de Calculo

* Se puede utilizar el ``método parallelStream()`` en lugar de ``stream`` para realizar las operaciones en un ``stream`` de manera concurrente en ``varios hilos`` de ejecución

```java

List<Integer> numeros = Arrays.asList(1, 5, 10, 15, 20);

List<Integer> mayoresA10 = numeros.parallelStream()
                                  .filter(n -> n > 10)
                                  .collect(Collectors.toList());
```

### Ejemplo de Lectura de Datos

* Archivo contiene una ``lista de números`` y desea ``calcular`` la ``suma`` de todos los números en el archivo
  
  * Usar un ``stream`` para ``leer`` los datos del ``archivo secuencialmente`` y realizar el ``cálculo`` de la ``suma`` mientras recorre los datos

* Utiliza un ``stream`` para ``leer`` los ``datos`` del archivo ``numbers.txt`` línea a línea

* ``Convertir`` cada línea en un número

* Se utiliza el ``método mapToInt()`` para ``convertir`` el ``stream`` de ``String`` a un ``stream`` de números ``int``

* Utiliza el ``método sum()`` para calcular la suma de todos los ``números`` en el ``stream``

```java
// Crear un stream que lea los datos del archivo
Stream<String> stream = Files.lines(Paths.get("numbers.txt"));

// Convertir el stream de String a un stream de números y calcular la suma de todos los números
int sum = stream.mapToInt(Integer::parseInt)
                 .sum();

// Imprimir la suma
System.out.println("Suma: " + sum);
```
