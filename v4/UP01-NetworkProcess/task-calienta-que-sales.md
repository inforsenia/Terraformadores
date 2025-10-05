# Tarea : [ Calienta que Sales ] 

En una maquina `ubuntuserver` configurada en Red Nat (10.42.42.0/24), y poner accesible
el SSH en el puerto 2242 del hipervisor. 

Cread 3 usuarios más aparte del admin vuestro (adminaso,backupaso y dummy)



| Usuario  | Shell | Opciones                        |
|----------|-------|---------------------------------|
| adminaso | bash  | Estar en sudo                   |
| backupaso| zsh   | Script de creación (ver abajo)  |
| dummy    | rbash | ejecutar nano y cd a directorios|


**Script** cuando el usuario `backupaso` inicie sesión que se comprueben las siguientes rutas:

```bash
/home/backupaso/2025/SEMANA/Lunes
                           /Martes
                           /Miercoles
                           /Jueves
                           /Viernes
                           /Sabado
                           /Domingo


```

Donde la variable `SEMANA` ha de cambiarse por la semana del año en la que estamos, calculada
dinámicamente (pista : `script en python3`). Y para cada uno de los directorios, 
comprobar que existe y si no crearlo mostrando y *loggeando* en el `syslog` todas las operaciones.



Configurad que solo puedan logarse esos 4 usuarios en el sshd de la máquina.

## Ideas para el examen

* Usuarios que puedan iniciar sesión sin password.
* Copia de ficheros remotos con rsync.
* Opciones avanzandas del rsync.
* Cifrado simetrico y asimetrico.
* Comprobaciones básicas de permisos.
* Comprobaciones de ficheros.
* Comprobaciones de estructuras, passwords, tamaños de ficheros, fechas,...

## Consejos

Instalar en vuestra casa GNU/LinuX y Virtualizar como toca.
