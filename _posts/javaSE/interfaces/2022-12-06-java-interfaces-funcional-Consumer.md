---
layout: single
title: Java - Interfaz Funcional Consumer<T>
date: 2022-12-20
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
  - java-clase
  - java-interface
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Se utiliza para representar una operación con ``un único argumento`` y ``sin devolver ningún resultado``

  * Indicado para elementos del ``tipo colecciones`` o ``stream`` para realizar una acción en cada elemento

## Ejemplo Método ``Consumer<T>``

```java

@FunctionalInterface
  public interface Consumer<T> {
    void accept(T t);
}
```
