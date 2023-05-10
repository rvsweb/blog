---
layout: single
title: Java - JAR & Manifiesto 
date: 2022-05-08
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
  - java-JAR
  - java-Manifiesto
page_css: 
  - /assets/css/mi-css.css
---

## Concepto

* **JAR** ( Java ARchive)  

  * Archivo comprimido 
  
  * Se utiliza para empaquetar , distribuir un conjunto archivos en una sola unidad
  
* **MANIFEST.MF**

  * Archivo de texto contiene metadatos sobre el contenido del archivo ``JAR``

  * Se encuentra en el interior de los archivos ``JAR``

  * Organizados por pares ``nombre-valor`` en diferentes secciones

  * Si se va a usar un archivo ``JAR`` como ejecutable el archivo del ``manifiesto`` debe especificar la clase principal de la aplicación

  * Ejemplo

    ```java
    Manifest-Version: 1.0
    Main-Class: com.miempresa.ClasePrincipal
    Class-Path: lib/mi-libreria1.jar lib/mi-libreria2.jar
    ```

### Crear archivo JAR sin MANIFEST.MF

1. Creamos una clase Java 

```java
// Ruta de los directorios de la clase MiClasePrincipal
package com.miempresa;

public class MiClasePrincipal{

	public static void main(String [] args){
	
		System.out.println("Ejemplo de archivo JAR");
	
	}
}
```

2. Compilamos el archivo ``java`` desde la linea de comandos

```java
javac MiClasePrincipal.java
```

3. Creamos el archivo ``JAR`` a partir del archivo ``.class`` sin añadirle el ``MANIFEST.MF``

```java
java -cf <NuevoNombre.jar> *.class
```

### Crear archivo JAR con MANIFEST.MF

1. Creamos una clase Java 

```java
// Ruta de los directorios de la clase MiClasePrincipal
package com.miempresa;

public class NuevaClasePrincipal{

	public static void main(String [] args){
	
		System.out.println("Ejemplo de archivo JAR");
	
	}
}
```

2. Compilamos el archivo ``java`` desde la linea de comandos

```java
javac NuevaClasePrincipal.java
```

3. Creamos el archivo ``JAR`` a partir del archivo ``.class`` sin añadirle el ``MANIFEST.MF``

```java
java -cf <NuevaClasePrincipal.jar> *.class
```

4. Creamos un directorio llamado ``lib`` para almacenar las librerias ``JAR`` que vamos a incluir en el ``MANIFEST.MF``

  * Estructura de Directorios 

    ```java
    * java_manifiesto
      * com
        * miempresa
            * NuevaClasePrincipal.class
            * NuevaClasePrincipal.java
      * lib
        * MiClasePrincipal1.jar
        * MiClasePrincipal2.jar
    ```

5. Construimos el archivo MANIFEST.MF desde cualquier editor de texto y lo añadimos a la ruta de directorios del proyecto donde tenemos el archivo que queremos transformar en JAR

    ```java
    * java_manifiesto
      * com
        * miempresa
            * NuevaClasePrincipal.class
            * NuevaClasePrincipal.java
      * lib
        * MiClasePrincipal1.jar
        * MiClasePrincipal2.jar
      MANIFEST.MF        
    ```

6. Abrimos el archivo ``MANIFEST.MF`` con cualquier editor de texto y le agregamos los siguientes datos

    ```java
    Manifest-Version: 1.0 // Versión del Manifest 
    Main-Class: com.miempresa.NuevaClasePrincipal // Ruta de los directorios de la clase principal
    Class-Path: lib/MiClasePrincipal1.jar lib/MiClasePrincipal2.jar // Archivos JAR externos que usará el proyecto
    ```

7. Compilamos el proyecto con la clase principal y con el MANIFEST.MF

    * Desde la ruta del proyecto principal

```java
jar cvfm NuevaClasePrincipal.jar MANIFEST.MF .\com\miempresa\NuevaClasePrincipal.class 
```

8. Si todo se ha creado de forma correcta aparecerá este mensaje

```java
  added manifest
  adding: com/miempresa/NuevaClasePrincipal.class(in = 496) (out= 341)(deflated 31%)
```

  * Y el archivo en la ruta en el directorio principal de nuestro proyecto

```java
  NuevaClasePrincipal.jar
```


9. Ejecutamos el archivo ``JAR`` desde la linea de comandos ``cmd`` para comprobar si funciona

```java
java -jar NuevaClasePrincipal.jar
// Salida → Ejemplo de archivo JAR    
```
