---
layout: single
title: Cyberseguridad - Conceptos básicos 
date: 2026-02-26
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/linux/tux.jpg
categories:
  - cyberseguridad  
  - linux
tags:
  - cyberseguridad-conceptos
  - emnum4linux
page_css: 
  - /assets/css/mi-css.css
---

## Cyberseguridad

### Conceptos básicos

```bash
enum4linux
```

* Es una herramienta de enumeración de servicios Windows/Samba desde sistemas Linux.

* Se usa mucho en auditorías de seguridad para obtener información de máquinas Windows sin autenticación o con credenciales débiles.

* Permite obtener información como usuarios, grupos, shares, políticas de contraseñas, etc.

### Opciones de enum4linux

`-U` → Enumera usuarios del sistema objetivo:

  Lista de cuentas de usuario

  Permisos de acceso

  Nombres de usuario válidos

### Información de cuentas

`-S` → Enumera shares (recursos compartidos):

  Carpetas compartidas en red

  Permisos de acceso

  Recursos SMB/Samba disponibles

### Ejemplo de uso

```bash
enum4linux -a <IP-del-objetivo>
```

* El parámetro `-a` activa todas las opciones de enumeración disponibles, proporcionando una gran cantidad de información sobre el objetivo.

---

* Script básico de enumeración con enum4linux para enumeración de puertos con enum4linux y lo guardamos como `recon.sh`:

```bash
#!/bin/bash
# Verify that nmap and enum4linux are installed.
command -v nmap >/dev/null 2>&1 || { echo "nmap is not installed"; exit 1; }
command -v enum4linux >/dev/null 2>&1 || { echo "enum4linux is not installed"; exit 1; }

# Validate IP format
if [[ ! "$1" =~ ^[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+$ ]]; then
    echo "Invalid IP format"
    exit 1
fi

# Check if IP of target is entered
if [ -z "$1" ]
then
    echo "Correct usage is ./recon.sh <IP>"
    exit 1 # output with error (error generico)
else
    echo "Target IP $1"
    echo "Running Nmap..."
# Run Nmap scan on target and save results to file
    nmap -sV $1 > scan_results.txt
    echo "Scan compete. Results saved to scan_results.txt"
fi

# If the Samba port 445 is found and open , run enum4Linux
if grep 445 scan_results.txt | grep -iq open
then
    echo "Samba found. Enumeration started..."
    enum4linux -U -S $1 >> scan_results.txt
    echo "Enumeration complete."
    echo "Results added to scan_results.txt"
    echo "To view the results, cat the file"
else
    echo "Open SMB share ports not found"
fi
```

* Después de guardarlo y le damos permisos de ejecución con `chmod +x recon.sh`, este script realizará un escaneo de puertos con Nmap y si encuentra el puerto 445 abierto, ejecutará `enum4linux` para enumerar información relacionada con Samba.

  Los resultados se guardarán en un archivo llamado `scan_results.txt`.

* Este script realiza un escaneo de puertos con Nmap y si encuentra el puerto 445 abierto, ejecuta `enum4linux` para enumerar información relacionada con Samba.

---

* Ejecutamos el script con la IP del objetivo , en este caso estamos utilizando una máquina vulnerable creada con Docker con la IP `10.6.6.23`

```bash
# ./recon.sh <IP-del-objetivo>
./recon.sh 10.6.6.23
```

* Realizamos un cat del archivo `scan_results.txt` para ver los resultados obtenidos por el script:

```bash
cat scan_results.txt
```

* Nos aparece la información obtenida por el script , entre la información obtenida podemos ver que el puerto 445 está abierto y que el servicio Samba está corriendo en la máquina objetivo.

```bash
 Starting Nmap 7.94 ( https://nmap.org ) at 2026-03-04 17:10 UTC
Nmap scan report for gravemind.vm (10.6.6.23)
Host is up (0.00017s latency).
Not shown: 994 closed tcp ports (conn-refused)
PORT    STATE SERVICE     VERSION
21/tcp  open  ftp         vsftpd 3.0.3
22/tcp  open  ssh         OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
53/tcp  open  domain      ISC BIND 9.11.5-P4-5.1+deb10u5 (Debian Linux)
80/tcp  open  http        nginx 1.14.2
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
Service Info: Host: GRAVEMIND; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.41 seconds
Starting enum4linux v0.9.1 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Wed Mar  4 17:11:09 2026

 =========================================( Target Information )=========================================
Target ...........                                                                                    
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none

 =============================( Enumerating Workgroup/Domain on 10.6.6.23 )=============================
[E] Can't find workgroup/domain                                                               
 =====================================( Session Check on 10.6.6.23 )=====================================
[+] Server 10.6.6.23 allows sessions using username '', password ''
 ==================================( Getting domain SID for 10.6.6.23 )==================================
 Domain Name: WORKGROUP
 Domain Sid: (NULL SID)
[+] Can't determine if host is part of domain or part of a workgroup
 =========================================( Users on 10.6.6.23 )=========================================

index: 0x1 RID: 0x3e8 acb: 0x00000015 Account: masterchief      Name:   Desc:                                                                                                                                                               
index: 0x2 RID: 0x3e9 acb: 0x00000015 Account: arbiter  Name:   Desc: 

user:[masterchief] rid:[0x3e8]
user:[arbiter] rid:[0x3e9]
===================================( Share Enumeration on 10.6.6.23 )===================================                                                                                                   
        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      All home directories
        workfiles       Disk      Confidential Workfiles
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (Samba 4.9.5-Debian)
Reconnecting with SMB1 for workgroup listing.

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
[E] Can't understand response:

tree connect failed: NT_STATUS_BAD_NETWORK_NAME

//10.6.6.23/homes       Mapping: N/A Listing: N/A Writing: N/A
//10.6.6.23/workfiles   Mapping: OK Listing: OK Writing: N/A
//10.6.6.23/print$      Mapping: OK Listing: OK Writing: N/A

[E] Can't understand response:
NT_STATUS_OBJECT_NAME_NOT_FOUND listing \*                                               
//10.6.6.23/IPC$        Mapping: N/A Listing: N/A Writing: N/A
enum4linux complete on Wed Mar  4 17:11:20 2026
```

Dirección IP del objetivo:

```txt
   10.6.6.11
   10.6.6.12
   10.6.6.13
   10.6.6.14
   10.6.6.23
  172.17.0.2
```

* Ejecutamos el comando `container` para ver los contenedores que tenemos corriendo en Docker y copiamos todas las direcciones IP de los contenedores para guardarlas en un archivo llamado `hosts.txt` y luego ejecutar el comando `nmap` para hacer un escaneo de ping a todas las direcciones IP que tenemos en el archivo `hosts.txt` para ver cuáles están activas.

```bash
nmap -sn -iL hosts.txt
```

* `-sn`

  > Ping scan (solo detecta si el host está activo, NO escanea puertos)

* `-iL <archivo.txt>` como por ejemplo `hosts.txt`

  > Lee la lista de IPs desde el archivo hosts.txt

```bash
(kali㉿Kali)-[~]
└─$ sudo nmap -sn -iL to_scan.txt 
Starting Nmap 7.94 ( https://nmap.org ) at 2026-03-04 17:58 UTC
Nmap scan report for 10.6.6.1
Host is up.
Nmap scan report for webgoat.vm (10.6.6.11)
Host is up (0.0000080s latency).
MAC Address: 02:42:0A:06:06:0B (Unknown)
Nmap scan report for juice-shop.vm (10.6.6.12)
Host is up (0.000061s latency).
MAC Address: 02:42:0A:06:06:0C (Unknown)
Nmap scan report for dvwa.vm (10.6.6.13)
Host is up (0.000011s latency).
MAC Address: 02:42:0A:06:06:0D (Unknown)
Nmap scan report for mutillidae.vm (10.6.6.14)
Host is up (0.0000080s latency).
MAC Address: 02:42:0A:06:06:0E (Unknown)
Nmap scan report for gravemind.vm (10.6.6.23)
Host is up (0.000010s latency).
MAC Address: 02:42:0A:06:06:17 (Unknown)
Nmap scan report for 10.6.6.100
Host is up (0.000010s latency).
MAC Address: 02:42:0A:06:06:64 (Unknown)
Nmap scan report for metasploitable.vm (172.17.0.2)
Host is up (0.000035s latency).
MAC Address: 02:42:AC:11:00:02 (Unknown)
Nmap done: 8 IP addresses (8 hosts up) scanned in 0.33 seconds
```

* Datos de los hosts encontrados:

| IP         | Hostname      | ¿Qué es?                                      |
| ---------- | ------------- | --------------------------------------------- |
| 10.6.6.1   | —             | Gateway/Router de la red                      |
| 10.6.6.11  | webgoat.vm    | App vulnerable para practicar (OWASP WebGoat) |
| 10.6.6.12  | juice-shop.vm | App vulnerable de OWASP (tienda online)       |
| 10.6.6.13  | dvwa.vm       | Damn Vulnerable Web App                       |
| 10.6.6.14  | mutillidae.vm | App web vulnerable (NOWASP Mutillidae)        |
| 10.6.6.23  | gravemind.vm  | Target principal del curso                    |
| 10.6.6.100 | —             | Host adicional del entorno                    |
