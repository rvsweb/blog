---
layout: single
title: Java - Synchronized
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
  - java-synchronized
  - java-modificadores
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* Los elementos sincronizados sólo podrán ser accedidos por un hilo a la vez se suele utilizar en la programación concurrente

* Se suele aplicar en bloques de código o en métodos

  * El ``modificador synchronized`` en Java se utiliza para controlar el acceso concurrente a un método o bloque de código

* Cuando un hilo intenta ejecutar un método o bloque de código marcado como ``synchronized`` el hilo adquirirá el bloqueo del ``objeto`` en el cual se encuentra el ``método`` o ``bloque de código``

* Mientras el hilo tiene el bloqueo otros hilos que intenten adquirir el mismo bloqueo serán bloqueados y tendrán que esperar hasta que el hilo actual libere el bloqueo

  * Un ejemplo de uso del ``modificador synchronized`` es cuando se tiene una clase que representa una cuenta bancaria y varios hilos que intentan realizar operaciones de retirada y depósito en la cuenta al mismo tiempo.

* Sin el uso de ``synchronized`` es posible que dos hilos intenten retirar fondos de la cuenta al mismo tiempo lo que resultaría en un saldo incorrecto.

```java

public class BankAccount {
    private double balance;

    public synchronized void deposit(double amount) {
        balance += amount;
    }

    public synchronized void withdraw(double amount) {
        balance -= amount;
    }

    public double getBalance() {
        return balance;
    }
}
```

* Ejemplo

* Los métodos ``deposit`` y ``withdraw`` están marcados como ``synchronized`` lo que significa que solo un hilo puede ejecutar uno de estos ``métodos`` a la vez

  * Esto garantiza que no se produzcan conflictos entre ``hilos`` al acceder al saldo de la cuenta

  * También se puede usar el modificador ``synchronized`` en bloques de código en lugar de ``métodos`` completos

* Ejemplo

  * Si solo deseamos ``sincronizar`` una parte de un método podemos hacerlo de la siguiente manera

```java

public class BankAccount {

    private double balance;

    public void deposit(double amount) {
        synchronized (this) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        synchronized (this) {
            balance -= amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}

```

* En el ejemplo solo las operaciones de actualización del saldo están ``sincronizadas`` mientras que el acceso a la lectura del saldo no lo esta

## Resumen

* El modificador ``synchronized`` en ``Java`` se utiliza para garantizar que solo un ``hilo`` pueda acceder a un método o ``bloque de código`` a la vez lo que ayuda a evitar conflictos entre hilos al acceder a recursos compartidos
