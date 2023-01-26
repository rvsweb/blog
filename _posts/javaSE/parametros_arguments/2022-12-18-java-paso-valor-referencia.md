---
layout: single
title: Java - Parámetros Por Valor & Por Referencia
date: 2022-05-05
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
  - java-por-valor
  - java-por-referencia
  - java-parámetros
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* los ``parámetros`` se pueden pasar a un ``método`` de dos maneras diferentes

  * ``Por valor``
  
  * ``Por referencia``

## Parámetro por Valor

* Cuando se pasa un ``parámetro`` a un ``método por valor`` se envía una copia del valor del ``parámetro`` al ``método``

  * Esto significa que cualquier cambio que se haga al ``parámetro`` dentro del ``método`` no afectará al valor original del parámetro en el método que lo llamó

## Ejemplo 1 - Paso de Parámetro por valor

```java
public void incrementarValor(int numero) {
  numero = numero + 1;
}

int x = 5;
incrementarValor(x);
System.out.println(x);  // Imprime 5
```

## Ejemplo 2 - Paso de Parámetro por valor

```java
public void duplicarValor(int numero) {
  numero = numero * 2;
}

int x = 5;
duplicarValor(x);
System.out.println(x);  // Imprime 5
```

* Se pasa una ``copia`` del ``valor`` de ``x`` al ``método incrementarValor()``

* Dentro del ``método`` se le ``suma 1`` al ``valor del parámetro`` pero esto no afecta al ``valor`` original de ``x`` fuera del ``método``

  * Al imprimir x después de ``llamar`` al ``método`` se obtiene el ``valor`` original de x  que es 5.

## Parámetro por Referencia

* Cuando se pasa un parámetro a un ``método por referencia`` se envía la ``dirección de memoria`` del objeto al ``método``

  * Significa que ``cualquier cambio`` que se haga al ``objeto`` dentro del ``método`` sí afectará al ``objeto original`` en el ``método`` que lo llamó

### Ejemplo 1 - Paso de Parámetro por Referencia

* Se pasa la ``dirección de memoria`` del ``objeto`` lista al ``método incrementarValor()``

```java
public void incrementarValor(ArrayList<Integer> lista) {
  lista.add(1);
}

ArrayList<Integer> lista = new ArrayList<>();
incrementarValor(lista);
System.out.println(lista.size());
```

### Ejemplo 2 - Paso de Parámetro por Referencia

```java
public void duplicarValores(ArrayList<Integer> lista) {
  for (int i = 0; i < lista.size(); i++) {
    lista.set(i, lista.get(i) * 2);
  }
}

ArrayList<Integer> lista = new ArrayList<>(Arrays.asList(1, 2, 3));
duplicarValores(lista);
System.out.println(lista);  // Imprime [2, 4, 6]
```

* Dentro del ``método`` se agrega un ``elemento`` a la ``lista``

  * Esto sí afecta al ``objeto`` original de ``lista`` fuera del ``método`` ya que ``ambos tienen la misma dirección de memoria``

    * Al imprimir el tamaño de la ``lista`` después de llamar al ``método`` se obtiene 1 ya que se ha agregado un elemento a la ``lista``

* Importante
  
  * ``Primitivos`` (como int, float, etc.) siempre se pasan ``por valor``
  
  * ``Objetos`` (como ArrayList, String, etc.) se pasan ``por referencia``

## Resumen

* Diferencia entre pasar un ``parámetro por valor`` y ``por referencia``

  * Cuando se pasa ``por valor`` **se envía una copia** del ``valor del parámetro`` al ``método``
  
    * Cualquier cambio que se haga al ``parámetro dentro del método`` **no afecta al valor original** del ``parámetro`` en el ``método`` que lo llamó
  
  * Cuando se pasa ``por referencia`` **se envía la ``dirección de memoria``** del ``objeto`` al ``método``
  
    * Cualquier cambio que se haga al ``objeto`` dentro del ``método`` sí afecta al ``objeto`` original en el método que lo llamó