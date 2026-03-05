---
layout: single
title: Cyberseguridad - Conceptos basicos 
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
page_css: 
  - /assets/css/mi-css.css
---

## Cyberseguridad - Conceptos basicos

### Escala de Severidad (CVSS v3)

* **CVSS** *(Common Vulnerability Scoring System) es un estándar para evaluar la gravedad de las vulnerabilidades de seguridad.*

---

* La versión 3.0 introduce una escala de severidad que clasifica las vulnerabilidades en cinco categorías: baja, media, alta, alta moderada y crítica.

      | Parámetro                   | Pregunta que responde                         | Ejemplo del informe                |
      | --------------------------- | --------------------------------------------- | ---------------------------------- |
      | Vector de ataque            | ¿Desde dónde ataca el atacante? (Red / Local) | Red (ataque remoto desde Internet) |
      | Complejidad                 | ¿Es fácil o difícil ejecutar el ataque?       | Baja = cualquiera puede intentarlo |
      | Privilegios requeridos      | ¿Necesita cuenta previa?                      | Ninguno = sin cuenta               |
      | Interacción de usuario      | ¿Necesita que alguien haga clic en algo?      | Ninguno = totalmente automático    |
      | Impacto en confidencialidad | ¿Roba datos?                                  | Alto / Bajo                        |
      | Impacto en integridad       | ¿Modifica datos?                              | Alto / Bajo                        |
      | Impacto en disponibilidad   | ¿Tumba el servicio?                           | Alto / Bajo                        |

  > Calculando la puntuación CVSS v3, se asigna una severidad a la vulnerabilidad:

      | Severidad   | Rango de puntuaciones CVSS v3 | Definición |
      | :---        | :---                          | :---       |
      | Crítica     | 9.0 – 10.0                    | La explotación es sencilla y suele resultar en un compromiso a nivel de sistema. Se aconseja elaborar un plan de acción y parchear inmediatamente. |
      | Alta        | 7.0 – 8.9                     | La explotación es más difícil, pero podría causar privilegios elevados y potencialmente una pérdida de datos o tiempo de inactividad. Se recomienda elaborar un plan de acción y parchear lo antes posible. |
      | Moderada    | 4.0 – 6.9                     | La explotación es moderada. Existen vulnerabilidades pero no son explotables o requieren pasos adicionales como la ingeniería social. Se aconseja elaborar un plan de acción y aplicar parches una vez resueltos los problemas de alta prioridad.    |
      | Baja        | 0.1 – 3.9                     | La explotación es débil. Existen vulnerabilidades, que podrían ser explotables, aumentan la superficie de ataque de una organización. Se aconseja elaborar un plan de acción y parchear durante la próxima ventana de mantenimiento. |
      | Informativa | N/A                           | No existe ninguna vulnerabilidad conocida. Se proporciona información adicional sobre los elementos detectados durante las pruebas, los controles estrictos y la documentación adicional. |

      

* **HTTP_X_FORWARDED_FOR**

  Es una cabecera HTTP que cualquier cliente puede escribir a mano.

  Un atacante bloqueado por IP podría hacer uso de esta cabecera para engañar al servidor web y hacer que registre una dirección IP falsa.

```bash
curl -H "X-Forwarded-For: 192.168.1.100" http://vulnerable-website.com
```

  Esto haría que el servidor web registre la dirección IP del atacante como 192.168.1.100, evitando así el bloqueo por IP.

* **XMLRPC.PHP**

  * Es un archivo comúnmente utilizado en sitios web como WordPress.

  Este archivo permite la comunicación remota con el sitio web, lo que puede ser explotado por atacantes para realizar ataques de fuerza bruta o DDoS.

    > Ataques de fuerza bruta "amplificados" (en un solo intento puede probar miles de contraseñas) y ataques DoS.

  Para proteger tu sitio web, es recomendable deshabilitar el acceso a `xmlrpc.php` si no se necesita o implementar medidas de seguridad adicionales como firewalls o plugins de seguridad.