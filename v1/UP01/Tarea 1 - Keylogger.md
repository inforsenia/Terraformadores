# UP01 – Adopción de pautas de seguridad informática

## Tarea 1: Keylogger

En la siguiente tarea vamos a instalar un ***keylogger*** y analizar su comportamiento.

Dado que no existe un paquete en un repositorio de *apt* que nos permita instalarlo directamente, tendremos que remitirnos a los fuentes y realizar la compilación e instalación del programa. Por lo tanto, deberemos comprobar si tenemos instalado el paquete ``` build-essential ```, que incluyecompiladores de C++ y las bibliotecas de gcc, así como el paquete ``` automake ``` que nos permitirá utilizar la herramienta makefile.

Vamos a trabajar con el programa **logkeys** que podemos encontrar en el siguiente repositorio de github: 
[https://github.com/kernc/logkeys/](https://github.com/kernc/logkeys/)

Si descargamos toda la rama *master* en zip y los descomprimimos tendremos el directorio **logkeys-master** con todo el contenido del proyecto.

El fichero *INSTALL* contiene toda la información necesaria para la instalación del programa, pero aquí tenemos un resumen de las instrucciones necesarias para la instalación:

```
./autogen.sh
cd build
../configure
make
sudo make install
```

Por último ejecutaremos ``` locale-gen``` para generar las locales de diferentes idiomas.

Ahora consultaremos el manual del programa para saber cómo se ejecuta y haremos diferentes pruebas. Es muy probable que los resultados del fichero de log no se correspondan con las teclas apretadas. Intenta solucionarlo. Este comportamiento tiene que ver con los keymaps.

Intenta averiguar cómo podríamos detectar si hay un *keylogger* en ejecución. 

Durante las pruebas que realices intenta cambiar de usuario sin que el proceso del logkeys termine y averigua si el programa sigue registrando o no las pulsaciones de teclado.

Elabora un documento explicando todo el proceso, con capturas de pantalla en las que se muestre los comandos que ejecutas, el contenido del fichero de log, etc. También aporta respuestas a lo que se plantea en el enunciado.
