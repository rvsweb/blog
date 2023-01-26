---
layout: single
title: Java - Parámetros & Argumentos
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
  - java-argumentos
  - java-parámetros
page_css: 
  - /assets/css/mi-css.css
---

## Diferencias entre Argumentos & Parámetros

### ``Argumento``

* ``Valores`` que se pasan a un ``método`` cuando este se llama
  
  * Ejemplo

    * El ``método`` que se llama ``sum()`` acepta ``dos valores enteros`` y ``retorna su suma``
  
    * Podrías llamar al ``método`` de esta forma

```java
//  1º Argumento 
//  ↓  2º Argumento 
//  ↓  ↓
sum(2, 3)
```

* En el caso anterior , los valores **2** y **3** serían los ``Argumentos`` que se le están pasando al ``método sum()``

### Detalles de los argumentos

* Son los **valores** que se pasan a los ``Métodos / Procedimientos / Funciones`` declarados de una ``clase`` la cual estamos invocando

  * A veces llamado ``parámetro real`` se refiere a la ``entrada real`` suministrada en la llamada de la ``función``

#### Ejemplo de Argumentos

1. Invocar ``método de instancia``

```java
Coche coche1 = new Coche();
// Invocación del método setCoche
// Argumento que le pasamos al método
// 
        //  1-Argumento
        //       ↓
        //       ↓ 2-Argumento
        //       ↓   ↓
        //       ↓   ↓ 3-Argumento
        //       ↓   ↓   ↓
        //       ↓   ↓   ↓    4-Argumento
        //       ↓   ↓   ↓        ↓                          5-Argumento
        //       ↓   ↓   ↓        ↓                              ↓
        //       ↓   ↓   ↓        ↓                              ↓
        //       ↓   ↓   ↓        ↓                              ↓
        //       ↓   ↓   ↓        ↓                              ↓
 coche1.setCoche(5 ,12 , 3 , "Ferrari 500 TRC de Scaglietti" , "96961" );
```

2. Invocar el ``procedimiento de clase``

```java
// Método de ejemplo
public static void setSuma(int x , int y){
  this.x = x;
  this.y = y;
}
//        1- Argumento
//              ↓       2- Argumento
//              ↓           ↓
           int xx = 5; int yy = 10; 
//             ↓           ↓         
Clase.setSuma( xx    ,    yy);
```

### ``Parámetros``

* Variables que se ``declaran`` dentro de la ``definición`` de un ``método``
  
* Se utilizan para ``recibir`` los ``argumentos`` que se le pasan a la llamada del ``método``
  
  * Ejemplo

    * El ``método sum()`` su definición

```java
// Método de Instancia
public int sum(int x, int y) {
    return x + y;
}
```

* El método ``sum()`` tiene dos ``parámetros`` **x** e **y**

* Se utilizan para ``recibir`` los ``argumentos`` **2** y **3** respectivamente cuando se llama al ``método``

* Los ``parámetros`` permiten a un ``método`` operar con los ``valores`` que se le pasan como ``argumentos`` y producir un resultado.

* Son ``valores`` que dependiendo del momento ``se pasan`` o ``se reciben`` dentro de los ``método`` de la ``clase`` con la que estemos trabajando

### Detalles de los Parámetros

* Es lo que aparece **definido** entre **paréntesis** dentro del ``método``

  * A veces llamado ``parámetro formal`` se usa a menudo para referirse a la ``variable`` tal como se encuentra en la definición de una ``función``

#### Ejemplo de Parámetro

1. ``Procedimiento de Instancia``

```java
// Parámetro define que datos necesita el procedimiento para realizar las operaciones
//                    1º Parámetro     
//                          ↓          2º Parámetro     
//                          ↓               ↓        3º Parámetro     
//                          ↓               ↓             ↓        4º Parámetro     
//                          ↓               ↓             ↓               ↓          5º Parámetro     
//                          ↓               ↓             ↓               ↓                ↓
//                          ↓               ↓             ↓               ↓                ↓
public void setCoche(int marchas , int cilindrada , int puertas , String modelo , String matricula){
  this.marchas = marchas;
  this.cilindrada = cilindrada;
  this.puertas = puertas;
  this.modelo = modelo;
  this.matricula = matricula;
}
```

2. ``Procedimiento de Clase``

```java
 /**
  *                            1º Parámetro
  *                            ↓       2º Parámetro
  *                            ↓       ↓
  *                            ↓       ↓
  */                           ↓       ↓
public static void setSuma(int x , int y){
  this.x = x;
  this.y = y;
}
```
