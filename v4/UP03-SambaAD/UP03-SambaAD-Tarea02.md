---
title: UP03 - Tarea Personalización del Directorio
author: Angel Berlanas Vicente
theme: Copenhagen
date: 2025/12/12
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

# Ajustes a la instalación, nuevos dominios.

Ahora que ya hemos instalado y sabemos que la Guía de Ubuntu funciona (esto es siempre una buena idea), 
ha llegado el momento de adecuar el *Servidor de Dominio* a nuestra infraestructura.

Cada uno de vosotros usará el nombre de dominio que le ha sido asignado en el módulo de 
Servicios en Red : [ Proyecto: Infraestructura Hosting para Terraformadores de Venus ](https://inforsenia.github.io/Terraformadores/v5/5Retos2EVAL/R1/r1).

---

# Ajustes a la instalación, nuevos dominios.

Pero para no entrar en conflicto con dominios que *no son nuestros*, lo que vamos a hacer es usar 
el dominio propuesto *SIN* **freedns.com** y lo cambiaremos a **.internal**, que es como lo hace Ubuntu en la guía, pero además he estado investigando y la `ICANN incorporó ese dominio como *estándar* en el 2024, lo que nos permite aprender varias cosas nuevas a la vez ^_^.

**MUY IMPORTANTE**: Leed toda la práctica antes de comenzar a configurar, ya que aparecen
una serie de requisitos de funcionamiento que deben ser tenidos en cuenta desde el comienzo
para poder realizar la tarea con éxito.

---

# DNS de las diferentes empresas

A continuación se muestra una tabla con los Dominios que se deberán configurar dentro 
de nuestras máquinas virtuales.

//TODO Añadir a los diferentes alumn@s con sus dominios.

| Empresa      | Alumn@        | Dominio               |
|--------------|---------------|-----------------------|
| vencedorestic|      ---      |vencedorestic.internal |
| ecotravel    |      ---      |ecotravel.interal      |


---

# Creación de usuarios y grupos en el Dominio

Dentro del dominio debéis crear los siguientes usuarios y grupos:

| Usuario | Password     | Grupos      | 
|---------|--------------|-------------|
|recursos | *keepass*    | rrhh        |
|imprenta | *keepass*    | print       |
|oficinap | *keepass*    | oficinas    |
|oficinav | *keepass*    | oficinas    |
|oficinat | *keepass*    | oficinas    |

Los Passwords debéis generarlos de manera segura y almacenarlos en un fichero 
de `keepass` organizado por grupos y carpetas (esto os vendrá bien más adelante).

Los usuarios `oficinap`,`oficinav` y `oficinat`, representan a los usuarios de
las oficinas de Paiporta, Valencia y Torrent respectivamente.

---

# Unión al dominio

Instalad un **Ubuntu 24.04** (*Noble Numbat*) con entorno de Escritorio GNOME y 
unirlo a vuestro dominio. Recordad que actualizar es siempre una buena idea.

Cómo tenéis libertad para gestionar las direcciones IP en la **red interna** del servidor, 
configuradlo como consideréis, pero yo os aconsejo el uso de IP fijas para esta práctica.

Tenéis una referencia aquí:

* [Connect Ubuntu to Samba ](https://github.com/RNViththagan/Samba-AD-DC-Setup/blob/main/connect-ubuntu-to-samba-ad-dc.markdown)

Probad que todos los usuarios creados inician sesión en el dominio. 

Os he puesto una serie de enlaces al final como referencias interesantes.

---

# Impresoras!

Instalad la impresora de `CUPS-PDF` en el Servidor Samba y compartirla en vuestro dominio
usando la guía propuesta:

* [Samba as Print Server](https://documentation.ubuntu.com/server/how-to/samba/print-server/)

Instalación de la impresora PDF en el servidor del Dominio:

```bash
sudo apt install printer-driver-cups-pdf
```

---

# Servidor de ficheros

Desde el propio **Servidor del Dominio**, compartir vía Samba las siguientes carpetas:

* `/srv/rrhh/`
* `/srv/impresiones/`
* `/srv/oficinas/`

Las tres carpetas deberán ser creadas en el Servidor del Dominio. La guia para configurar
el Servidor de Ficheros es esta:

* [Samba as File Server](https://documentation.ubuntu.com/server/how-to/samba/file-server/)


---

# Retos: Juntando las piezas

Una vez tenemos toda la infraestructura montada, es decir, los usuarios en el *SAMBA DC*, 
el cliente 24.04 instalado y *unido al dominio*, la impresora `cups-pdf` compartida y las carpetas
compartidas **preparadas** desde el servidor, ha llegado el momento de que comencemos
a poner todo esto en marcha.

Documentad cada uno de los retos en un documento Markdown diferente, con capturas, los scripts
realizados y todo lo necesario para luego poder consultarlo más adelante (examen):

* `RepositorioASO/UP03/Reto01.md`
* `RepositorioASO/UP03/Reto02.md`
* `RepositorioASO/UP03/RetoXX.md`
* ...

---

# Retos: Juntando las piezas

## Reto 01: Imprimiendo en PDF

Configurad la impresora pdf del servidor para que cuando **desde el cliente** se imprima en ella,
se cree un fichero `.pdf` en la carpeta compartida: `/srv/impresiones/$USER/`.

## Reto 02: Montando la carpeta de Impresiones

La carpeta destino de las impresiones ha de estar montada en el cliente, de tal manera que 
cuando el usuario inicie sesión se le cree un enlace a **SU CARPETA** de impresiones 
en el Escritorio, en caso de que el enlace ya exista no debe ocurrir nada.

---

# Retos: Juntando las piezas

## Reto 03: Usuarios de las Oficinas

Los miembros del grupo oficinas han de acceder en lectura/escritura a la carpeta `/srv/oficinas`.
Para facilitarles el acceso, se les creará un acceso directo en su Escritorio a la ruta del punto 
de montaje local.

---

# Retos: Juntando las piezas

## Reto 04: Recursos Humanos

Recursos Humanos necesita realizar ciertas auditorías de manera semanal para comprobar que todo 
el mundo está trabajando de manera correcta. Para ello, verifica que en la semana los usuarios
de las diferentes oficinas están iniciando sesión en los equipos del dominio a las horas en las
que se abren las oficinas.

Crea un ShellScript que al ejecutarse en el **Servidor del Dominio** muestre todos los inicios de
sesión de los miembros del grupo `oficinas` de los últimos 7 días. El formato de salida ha de ser 
el siguiente:

```ShellScript
|Usuario  | Hora |
|oficinap | 2025-12-13T12:35:01|
|oficinav | 2025-12-14T09:23:21|
|oficinat | 2025-12-14T10:51:44|
```
---

# Retos: Juntando las piezas

## Reto 05: Backups para un Hospital

Aprovechando que el Servidor del Dominio está en ambas redes, añade una carpeta compartida por Samba
que se llame: 

* `/srv/externo/hospital-backups`

Y accede desde la máquina que tiene la Base de Oracle de Hospital 
para almacenar ahí backups de la BBDD.

Para ello deberéis exportar la BBDD y guardarla en la carpeta montada.

Tenéis esta documentación de RedHat para montar desde Windows:

* [Mounting and Mapping](https://www.redhat.com/en/blog/samba-windows-linux)

Documenta los pasos seguidos, te pueden hacer falta para el examen.

---

# Retos: Juntando las piezas

## Reto 06: Recursos Humanos, en Python3 [Opcional]

Buscando alguna librería de `Python3` que lo permita, desarrolla el Script del **Reto 04** en Python.

El resultado generado en la terminal ha de ser el mismo que en la ejecución del Script del **Reto 04**.

---



# Enlaces de referencia

* [Dominio .internal](https://en.wikipedia.org/wiki/.internal)
* [Guia Instalación SAMBA AD DC](https://documentation.ubuntu.com/server/how-to/samba/provision-samba-ad-controller/)
* [Keepass](https://keepass.info/download.html)
* [Connect Ubuntu to Samba ](https://github.com/RNViththagan/Samba-AD-DC-Setup/blob/main/connect-ubuntu-to-samba-ad-dc.markdown)
* [Intro SSSD](https://documentation.ubuntu.com/server/explanation/intro-to/sssd/)
* [SSSD](https://sssd.io/)
* [Beneficios del SSSD](https://docs.redhat.com/es/documentation/red_hat_enterprise_linux/8/html/configuring_authentication_and_authorization_in_rhel/understanding-sssd-and-its-benefits_configuring-authentication-and-authorization-in-rhel)
* [Samba as Print Server](https://documentation.ubuntu.com/server/how-to/samba/print-server/)
* [Samba as File Server](https://documentation.ubuntu.com/server/how-to/samba/file-server/)
* [Mounting and Mapping](https://www.redhat.com/en/blog/samba-windows-linux)
