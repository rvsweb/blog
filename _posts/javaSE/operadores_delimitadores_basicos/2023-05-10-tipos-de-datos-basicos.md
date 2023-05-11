---
layout: single
title: Java - Operadores y Delimitadores Básicos
date: 2023-05-10
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
  - java-operadores
  - java-delimitadores
page_css: 
  - /assets/css/mi-css.css
---

## Conceptos

### Operadores

* Elementos que se utilizan para almacenar un valor concreto con el cual realizar **operaciones matemáticas** y **booleanas**

  * Permiten definir operaciones los cuales se van a procesar en un programa

| **Tipos de Datos** | **Alcance** o **Rango** |
| --- | --- |
| ``byte`` | **-128** a **127** ``( 1 Byte)``|
| ``short`` | **-32768** a **32767** ``( 2 Bytes)`` |
| ``int`` | **-2147483648** a **2147483647** ``( 4 bytes )`` |
| ``long`` | **-9223372036854775808** a **9223372036854775807** ``( 8 Bytes)`` |
| ``char`` | **'\u0000'** a **'\uffff'** , ambos incluidos el cual es lo mismo que de **0** a **65535** , 1 letra |
| ``boolean`` | **0** o **1** ``( 1 bit)`` |
| ``float`` | **4 Bytes**, punto flotante |
| ``double`` | **8 Bytes**, punto flotante |
| ``String`` | **No es un tipo de datos básico** <br> Es un **objeto básico** en si mismo, el cual contiene propiedades y métodos, pero el lenguaje ``Java`` permite definir un nuevo objeto con el ``delimitador(")`` por lo que podemos concatenar texto utilizando el ``operador(+)`` con los nombres de los objetos de tipo ``String`` y otros los trozos de texto delimitados con ``(")``
|    |     |

### Delimitadores

| **Operador** | **Datos** | **Acción** |
| --- | --- |--- |
| ``+`` | ``String`` | Une cadena de caracteres "texto" ``( concatenador )`` |
| ``+`` | ``número`` | Suma |
| ``-`` | ``número`` | Invierte el signo del número |
| ``-`` | ``número`` | Resta |
| ``*`` | ``número`` | Multiplica y tiene prioridad sobre la suma y la resta |
| ``/`` | ``número`` | Divide y tiene prioridad sobre la suma y la resta |
| ``%`` | ``numero`` | Devuelve el ``resto`` de la ``division`` del ``operador derecho`` por el ``izquierdo`` |
| ``!`` | ``booleano`` | El operador ``NOT`` **booleano** |
| ``~`` | ``número`` | Invierte ``bit`` por ``bit`` el operando de la derecha |
| ``&`` | ``entero`` o ``booleano`` | El operador ``AND`` , booleano ``bit`` por ``bit`` del elemento a la ``izquierda`` contra el de la ``derecha`` |
| ``&&`` | **Cualquier** | El operador ``AND`` condicional |
| &vert;  | ``entero`` o ``booleano`` | El operador ``OR``, booleano ``bit`` por ``bit`` del elemento a la ``izquierda`` de la ``derecha`` |
| &vert; &vert;  | **Cualquier** | El operador ``OR`` condicional |
| &lt; &lt;  | ``número`` | Desplaza los ``bits`` hacia la ``izquierda`` la cantidad de la ``derecha`` |
| &gt; &gt;  | ``número`` | Desplaza los ``bits`` hacia la ``derecha`` la cantidad de la ``derecha`` |
| &vert; &vert; &vert;  | ``número`` | Desplaza los ``bits`` hacia la ``derecha`` pero no conserva el signo |
| ``=``  | **Cualquier** | Asigna al elemento de la ``izquierda``, el de la ``derecha``
| ``==``  | **Cualquier** | El ``operador condicional`` de igualdad , devuelve verdadero si ``derecha`` e ``izquierda`` es lo mismo |
| ``<``  | ``Básicos`` | Menor que , devuelve verdadero si ``izquierda`` es menor que ``derecha`` |
| ``<=``  | ``Básicos`` | Menor o igual que , devuelve verdadero si ``izquierda`` es menor o igual que ``derecha`` |
| ``>``  | ``Básicos`` | Mayor que , devuelve verdadero si ``izquierda`` es mayor que ``derecha`` |
| ``>=``  | ``Básicos`` | Mayor o igual que, devuelve verdadero si ``izquierda`` es mayor o igual que ``derecha``
| ``(op)=`` | ``Básicos`` | Hace la operación op ``[+,-,*,/.etc..]`` entre los dos operandos y el resultado lo guarda en el de la ``izquierda``
| ``var++`` | ``Básicos`` | Incrementa en uno la variable ``var``
| ``var--`` | ``Básicos`` | Decrementa en uno la variable ``var``
| ``.`` | ``objetos`` | Separa e invoca los nombres de los ``objetos`` , ``propiedades`` , ``métodos`` , ``nombres`` y jerarquía de ``clases``
| ``(int)`` | ``tipo de datos`` | Convierte un tipo de datos a ``entero`` , si reemplazamos ``int`` por una ``clase`` de objetos, podemos siempre y cuando sea correcto convertir al ``tipo de datos`` indicado entre paréntesis
| ``,`` | **Cualquier** | Separa argumentos de un ``método`` o ``procedimiento``
| ``;`` | **Cualquier** | Termina una línea de orden
| ``//`` | **Cualquier** | Empieza una línea de comentario
| ``/* */`` | **Cualquier** | Delimitan un trozo de texto como comentario
| ``/** */`` | **Cualquier** | Delimitan un trozo de texto como documentación para ``JavaDoc``
| ``{}`` | **Cualquier** | Delimitan un ``bloque de código`` de una estructura de datos
| ``()`` | **Cualquier** | Asocia una ``operación`` teniendo prioridad o en caso de un ``método`` agrupa los ``argumentos`` separados por comas
