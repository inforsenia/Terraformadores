---
title: UP03 - Tarea Instalacion SambaAD
author: Angel Berlanas Vicente
theme: Copenhagen
date: 2025/11/29
---

# Criterios de Evaluación presentes en la Tarea

|ID    |Descripción|
|------|----------------------------------------------|
|RA01.a|Se han identificado la función, los elementos y las estructuras lógicas del Directorio.|
|RA01.b|Se ha determinado y creado el esquema del Directorio.|
|RA01.c|Se ha realizado la instalación del Directorio en el servidor.|
|RA01.d|Se ha realizado la configuración y personalización del Directorio.|
|RA01.i|Se han utilizado herramientas gráficas y comandos para la administración del Directorio.|
|RA01.j|Se ha documentado la estructura e implantación del Directorio.|

---

# Sistema Operativo Base

Ubuntu 24.04 Server, para comenzar usaremos una instalación limpia, con la siguiente configuración de la RED.


|nº | Adaptador de Red| Modo de Red              |
|---|-----------------|--------------------------|
|1  | Adaptador puente| IP Fija - Anfitrión +200 |
|2  | Red Interna     | IP Fija - Rango Custom   | 

Usuario Administrador LOCAL: (El vuestro)

| Usuario | Password |
|---------|----------|
| localadmin| `nimdalacol` |

En caso de que no sea este, se procederá a no corregir la tarea/examen.

---

# Actualización

Actualiza el Ubuntu Server, instala el `tree` y usando SSH todo el rato procede con la instalación de Samba4 AD DC.

---

# Instalación de Samba AD DC

Crea un snapshot de la máquina en este punto y realiza la instalación tal y como aparece en la guia de Ubuntu:

* [documentation.ubuntu.com/server/how-to/samba/provision-samba-ad-controller/](https://documentation.ubuntu.com/server/how-to/samba/provision-samba-ad-controller/)

Avisa al profesor cuando lo tengas configurado e instalado.
