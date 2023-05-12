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
 
  * **Símbolos especiales** que realizan operaciones específicas en uno, dos o tres operandos y luego devuelven un resultado

### Delimitadores

  * **Caracteres** que se utilizan para separar elementos en una declaración de ``Java``

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
| &lt; &lt;  | ``número`` | Desplaza los ``bits`` hacia la ``izquierda`` la cantidad de la ``derecha`` |
| &gt; &gt;  | ``número`` | Desplaza los ``bits`` hacia la ``derecha`` la cantidad de la ``derecha`` |
| &gt; &gt; &gt; | ``número`` | Desplaza bits hacia la derecha pero no conserva el signo |
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

* Operadores

  * *Se muestran aquí porque la tabla en formato markdown no lo muestra*
 
    * ``|`` → ``entero`` o ``booleano`` : El operador ``OR``, booleano ``bit`` por ``bit`` del elemento a la ``izquierda`` contra el de la ``derecha``

    * ``||`` → **Cualquier** : El operador ``OR`` condicional 
