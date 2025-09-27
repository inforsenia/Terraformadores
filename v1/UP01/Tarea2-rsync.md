# UP01 – Adopción de pautas de seguridad informática

## Tarea 2: rsync

*rsync* es el comando por excelencia en linux para hacer copias de seguridad de los archivos.

En **Terraformadores de Venus** consideramos de vital importancia tener los datos a salvo, pudiendo recuperarlos en caso de pérdida o modificación no deseada.

A lo largo de esta tarea vais a utilizar y comprobar algunas de las caracterísitcas de funcionamiento de *rsync*, como realizar copias locales, remotas, incrementales, etc.

Deberéis documentar con capturas de pantalla cada uno de los pasos y/o comprobaciones que se piden.

Todas las opciones que se van a pedir podréis encontrarlas con sultando el manual del comando: 

``` man rsync ```

En primer lugar, crea un directorio que será donde vamos a tener los datos originales que queremos guardar mediante una copia de seguridad y, a continuación, crea o descarga varios archivos de diferentes tamaños. Crea también dentro una estrutura de directorios para poder comprobar la recursividad del comando cuando así se solicite.

Crea tambien otro directorio local, en otra ubicación, donde se alamacenarán las copias de seguridad.

**Ahora ya podemos empezar a realizar las pruebas:**

1. Realiza una copia básica del directorio de origen en el directorio de destino. Hazlo primero con la opción ``` -rv ``` y después con ``` -av ``` y explica la diferencia entre ambas.
2. Borra algún fichero en el directorio de origen y realiza de nuevo la copia. ¿Qué pasa?
3. Utiliza la opción correspondiente para que en el directorio de destino haya exactamente la misma información que en el directorio origen.
4. Investiga la opción ``` -b (--backup-dir) ``` y explica para qué sirve. Haz alguna(s) prueba(s) en la que se vea claramente cómo funciona.
5. El profesor ha creado una máquina virtual con un usuario para cada alumno. Realiza una copia remota de tu directorio de origen en tu ```home``` de esa máquina virtual. Te solicitará la contraseña del usuario. De momento la debes poner pero ya solucionaremos esto más adelante.
6. Dentro de tu ``` home ``` de la máquina virtual del profesor hay un directorio llamado *copia250917*. Haz un rsync inverso en tu directorio ``` /tmp ```, es decir, como si realizaras una restauración de datos.
7. Modifica el cron de tu usuario para que realice una copia de seguridad de tu directorio todos los lunes a las 9:20 en la máquina virtual del profesor. 
