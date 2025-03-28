---
layout: single
title: Docker
date: 2025-03-28
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/llama.jpg
categories:
  - docker
  - docker-basico
  - docker-comandos
tags:
  - docker-install
  - docker-ps
  - docker-mysql
  - docker-volume
---

## Concepto

* Comando que se utiliza en sistemas operativos basados en Linux (como Ubuntu) para instalar Docker Compose.
 
```
sudo apt install docker-compose
```

* Comando para comprobar la versión con la que se esta trabajando

```
docker-compose --version
```

* Comando que ejecuta un contenedor Docker para una base de datos MySQL

```
sudo docker run -d --rm --name mysql -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 mysql
```

Aquí está el desglose de lo que hace cada parte:

```
-d: Ejecuta el contenedor en segundo plano (modo "detached").

--rm: Elimina el contenedor automáticamente después de que se detenga.

--name mysql: Asigna el nombre "mysql" al contenedor.

-e MYSQL_ROOT_PASSWORD=root: Establece la contraseña para el usuario root de MySQL como "root".

-p 3306:3306: Mapea el puerto 3306 del contenedor al puerto 3306 del host, permitiendo el acceso a MySQL desde el exterior.

mysql: Especifica la imagen de Docker que se utilizará (en este caso, la imagen oficial de MySQL).
```


* Comando que se utiliza para listar los contenedores Docker que están actualmente en ejecución en tu sistema.

```
docker ps
```

* Comando que se utiliza para detener un contenedor Docker que esté en ejecución

```
docker stop <nombre-ID-contenedor>
```

* Comando que se utiliza para acceder al interior del contenedor Docker llamado "mysql" y abrir una sesión interactiva en el shell del contenedor. 

```
docker exec -it mysql bash
```

Aquí está el desglose:

```
docker exec: Ejecuta un comando dentro de un contenedor en ejecución.

-it: Estas opciones combinadas habilitan un modo interactivo:

-i mantiene la entrada estándar activa.

-t asigna un terminal pseudo-TTY (para una interacción en el shell).

mysql: Es el nombre del contenedor al que quieres acceder.

bash: Especifica que deseas abrir el shell Bash dentro del contenedor.
```

* Comando que se utiliza para conectar al servidor MySQL desde el terminal. 

```
mysql -uroot -proot
```

Aquí está el desglose de lo que significa:

```
mysql: Ejecuta el cliente MySQL, que permite interactuar con la base de datos.

-u root: Especifica el usuario con el que te quieres conectar, en este caso, root, que es el usuario administrador de MySQL.

-p root: Proporciona la contraseña del usuario root. Aquí, la contraseña también es root
```


* Este comando se utiliza para ejecutar un contenedor de Docker que aloja una instancia de phpMyAdmin, una herramienta gráfica para gestionar bases de datos MySQL. 

```
docker run --name phpmyadmin -v phpmyadmin_data:/etc/phpmyadmin/config.user.inc.php --link mysql:db -p 82:80 -d phpmyadmin
```

Aquí está el desglose:

```
**`docker run`**: Inicia un nuevo contenedor con los parámetros que sigan.

**`--name phpmyadmin`**: Da el nombre `phpmyadmin` al contenedor.

**`-v phpmyadmin_data:/etc/phpmyadmin/config.user.inc.php`**: Monta un volumen llamado `phpmyadmin_data` en el contenedor, enlazado al archivo de configuración personalizado de phpMyAdmin.

**`--link mysql:db`**: Crea un enlace entre el contenedor `phpmyadmin` y el contenedor `mysql`, asignándole el alias `db` para que phpMyAdmin pueda comunicarse con la base de datos MySQL.

**`-p 82:80`**: Mapea el puerto 80 del contenedor al puerto 82 del sistema anfitrión, permitiendo acceder a phpMyAdmin en `http://localhost:82`.

**`-d`**: Ejecuta el contenedor en segundo plano (modo "detached").

**`phpmyadmin`**: Utiliza la imagen oficial de phpMyAdmin desde Docker Hub.
```

