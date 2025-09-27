# UP02 – Cirptografía

## Tarea 2: Cifrado asimétrico y firma digital

Para la tarea de cifrado asimétrico usaremos la misma herramienta que en la tarea anterior, el comando *gpg*

A continuación vamos a explicar cómo se utiliza para generar un par de claves de firma asimétrica y, seguidamente, se planteará una actividad dividida en dos partes.

1. En primer lugar, para generar el par de claves se utiliza ```gpg --gen-key```

Nos solicitará una serie de datos. Con esos datos se identificarán las claves, por lo que conviene poner datos reales.

![](./imgs/tarea6-1.png)

También nos pedirá una contraseña con la que proteger el llavero donde se guardarán las claves generadas.

![](./imgs/tarea6-2.png)

Tardará un rato en generar las claves. Durante ese tiempo podemos ejecutar otros programas o mover el ratón para que el generador de bytes aleatorios tenga más datos con los que trabajar (entropía) y generar así una clave más segura.

Cuando finalice nos mostrará las claves creadas, así como el uid, es decir, el nombre que le hemos dado.

![](./imgs/tarea6-3.png)

En nuestro directorio ```HOME``` se habrá creado un directorio oculto ```.gnupg``` donde se guardan los ficheros internos que utiliza la herramienta.

![](./imgs/tarea6-4.png)

2. Podemos listar las claves con el comando ```gpg --list-keys```

![](./imgs/tarea6-5.png)

3. Para poder enviar nuestra clave privada a alguien con quien queramos comunicarnos, para que nos envíe mensajes cifrados con ella, primero tenemos que sacarla del llavero con el parámetro export:

```gpg -a --export -o ruta/nombre_fichero.pub usuario``` donde hemos usado ```-a``` para que sea en formato texto y ```ruta/nombre_fichero.pub``` será el fichero en el que guardaremos la clave y ```usuario``` será el uid que introdujimos al crear la clave.

Ese fichero ya lo podremos enviar a la persona con quien queramos comunicarnos.

![](./imgs/tarea6-6.png)

4. Esa persona deberá importar nuestra clave pública para poder utilizarla. Se utiliza el comando:
```gpg --import nombre_fichero```

![](./imgs/tarea6-7.png)

Si ese usuario vuelve a ejecutar ```gpg --list-keys``` verá que, junto con sus propias claves, ha aparecido una nueva del usuario alumno.

![](./imgs/tarea6-8.png)

5. Creamos un fichero con un mensaje.

![](./imgs/tarea6-9.png)

Para encriptar el fichero con la clave pública recién importada utilizaremos el siguiente comando:

```gpg -v -a -o ruta/mensaje.cifrado --encrypt --recipient usuario fichero``` donde:

- ```-v``` es modo verbose, o sea, más información visual
- ```-a``` y ```-o``` ya los conocemos
- ```--encrypt``` indica que estamos cifrando
- ```--recipient``` indica la clave del usuario con la que vamos a cifrar
- Por último, ```mensaje``` es el fichero a cifrar

Al intentar cifrar el sistema nos indicará que no hay seguridad de que esa clave pertenezca realmente al usuario que especificamos. Cualquiera podría haber copiado el fichero alumno.pub antes de que hiciésemos el import. El comando nos ofrece la huella como ayuda y nos pide que confirmemos si queremos continuar.

![](./imgs/tarea6-10.png)

Para ver la huella de nuestra clave pública podemos usar el comando ```gpg --fingerprint``` con lo que podríamos pedirle al destinatario que nos envió la clave pública que nos enviase también su huella y comprobar que coincide con la que nos da el sistema.

![](./imgs/tarea6-11.png)

6. Finalmente, cuando recibimos el mensaje cifrado con nuestra clave pública, podemos descifrarlo con el comando ```gpg --decrypt mensaje.cifrado```

El sistema nos solicitará la contraseña de nuestro llavero y mostrará el mensaje por pantalla. También podemos usar ```-o``` para llevarlo a un fichero.

![](./imgs/tarea6-12.png)

![](./imgs/tarea6-13.png)

7. Una vez visto esto podemos entender cómo funciona la firma digital. Vamos a seguir trabajando con el mensaje original. En primer lugar tenemos que crear la huella del mensaje, para lo que utilizaremos el comando:

```gpg -a --detach-sign nombre_fichero```

Este comando nos generará, a partir de  nuestra clave privada, un nuevo fichero llamado ```nombre_fichero.asc``` que contendrá el cifrado del hash del fichero original, es decir, la firma. Si enviamos el fichero junto con la firma a un destinatario que tenga nuestra clave pública, podrá comprobar que el fichero es nuestro y no se ha modificado.

![](./imgs/tarea6-14.png)

El contenido del fichero será algo similar a esto:

![](./imgs/tarea6-15.png)

- Cuando recibimos un fichero con su firma (como en el caso anterior){width=400px} debemos usar el siguiente comando para comprobar esa firma:

```gpg --verify nombre_fichero.asc``` teniendo en cuenta que tanto el fichero original como el fichero con la firma han de estar en el mismo directorio.

Ese comando nos dirá si realmente la firma corresponde al fichero original, con lo que podremos garantizar que el fichero es de quien dice ser y no se ha modificado. De hecho, podemos probar a modificar el fichero original y veremos como al ejecutar el comando anterior la verificación fallará.

8. Si en lugar de enviar dos ficheros, queremos enviar tanto el mensaje como la firma en el mismo fichero, podemos utilizar el comando siguiente:

```gpg -a --clearsign nombre_fichero```

En este caso tendremos tanto la firma como el contenido del fichero original dentro del fichero ```nombre_fichero.asc```. El contenido del fichero será similar a esto:

![](./imgs/tarea6-16.png)

También podemos comprobar que el fichero es de quién dice ser utilizando el comando del punto anterior.

9. El problema de esto es que el fichero lo hemos enviado sin cifrar, es decir, cualquiera podría haberlo interceptado y haber visto el contenido. Para enviar un único fichero con el contenido y la firma, pero en formato encriptado, usaremos el siguiente comando:

```gpg -a --sign nombre_fichero```

Esta vez tendremos un fichero llamado ```nombre_fichero.asc``` que contendrá tanto el contenido del fichero original como la firma y, además, estará cifrado con nuestra clave privada. Ya podemos enviarlo de forma segura al destinatario que queramos.

![](./imgs/tarea6-17.png)

10. Ahora vemos otro punto débil. Cualquiera que intercepte el mensaje y tenga nuestra clave pública, podrá desencriptarlo. ¿Cómo lo solucionamos? La solución es encriptar con la clave pública del destinatario y después, firmar con nuestra clave privada. Así, cualquiera que intercepte el mensaje y tenga nuestra clave pública podrá comprobar que el mensaje que ha interceptado es nuestro, pero no podrá acceder al contenido ya que sólo el destinatario podrá desencriptarlo con su clave privada.

Sin embargo, el destinatario podrá tanto comprobar que el mensaje es nuestro como acceder al contenido de ese mensaje. Para poder utilizar correctamente todos estos pasos, debemos firmar las claves públicas que tengamos de los destinatarios, para que así, siempre que las utilicemos, el sistema sepa con seguridad que son correctas. 

Para firmar la clave pública de un destinatario, una vez importada como vimos en la práctica anterior, utilizaremos el comando:

```gpg --sign-key destinatario```


Una vez visto esto, podemos comenzar con la tarea.

**Tarea a realizar:**

**Primera parte**

- Debes generar tu par de claves pública y privada
- Sube tu clave pública al repositorio de claves que hemos creado para que cualquiera pueda encriptar con ella un fichero con un mensaje
- Haz pruebas subiendo algún mensaje encriptado con la clave pública de un compañero y subiéndolo a su espacio. Mira también si te han mandado a ti mensajes cifrados con tu clave pública. Documenta todo esto en una memoria para la tarea en tu GitHub mostrando los mensajes enviado y recibidos y cómo has realizado la encriptación/desencriptación

**Segunda parte**

- Descarga del repositorio las claves públicas del profesor y el fichero de texto con su huella
- Comprueba cuál de las claves es la correcta y encripta con esa clave un fichero de texto llamado ```parte2``` con algún mensaje
- Sube al espacio del profesor el fichero encriptado. El profesor debería poder descifrarlo con su clave privada.

**Tercera parte**

- Descarga el fichero ```mensaje.txt.asc``` de Aules. Descarga además los ficheros ```mensaje1.txt```, ```mensaje2.txt``` y ```mensaje3.txt```. Deberás comprobar cuál de los 3 mensajes no ha sido modificado tras firmarlo. Explica cómo lo has averiguado. Ahora escribe tú algún mensaje en un fichero. Crea otro fichero con la firma del mensaje y sube los dos ficheros a un espacio llamado ```Tarea 4.3.1``` en tu repositorio.
      
- Descarga los ficheros ```mensaje1.txt.asc```, ```mensaje2.txt.asc``` y ```mensaje3.txt.asc```. Estos ficheros contienen tanto el mensaje como la firma. Debes hacer lo mismo que en el primer ejercicio, es decir, averiguar cuál de ellos no se ha modificado tras la firma. De nuevo, explica en la memoria cómo lo has sabido. Ahora escribe algo en un fichero. Firma el fichero de manera que se genere otro fichero con el mensaje y la firma, ambos en el mismo fichero. Sube ese fichero a un espacio llamado ```Tarea 4.3.2``` en tu repositorio.
      
- Descarga del repositorio el fichero con tus iniciales y extensión ```.txt.asc```. Se trata de un fichero firmado por el profesor y y cifrado con tu clave pública. Debes realizar los siguientes pasos:
      
    - Firma la clave pública del profesor
    - Descifra el fichero
    - Comprueba que el mensaje no se ha modificado por el camino, es decir, que la firma del profesor es válida. Describe en la memoria cómo lo has comprobado.
    - Escribe un mensaje en un fichero 
    - Firma el fichero que has creado de manera que se cree un único fichero con el mensaje y la firma y que, además, ese fichero esté cifrado con tu clave privada. Cifra ese fichero con la clave pública del profesor y súbelo a un espacio llamado ```Tarea 4.3.3``` en tu repositorio. 
