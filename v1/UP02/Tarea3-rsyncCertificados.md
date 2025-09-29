# UD2 – Criptografía

## Tarea 3: Uso de rsync con certificados

Anteriormente hicimos varias tareas con el ```rsync```. Este comando, cuando se utiliza para sincronizar datos por red, se basa en ```ssh``` para realizar la transferencia.

En una de esas tareas, si intentábamos sincronizar datos por red, nos pedía usuario y contraseña.

Vamos a utilizar los certificados generados para **SSH** para automatizar completamente la copia de seguridad con ```rsync```. 

Realiza los siguiente pasos (necesitarás 2 máquinas virtuales):

- En primer lugar, como siempre, crea un documento *Markdown* en tu repositorio de GitHub/GitLab donde irás explicando los pasos realizados y contestando a las prguntas propuestas.

- Crea un directorio con una estructura de varios directorios y ficheros en la máquina origen.

- En la máquina destino establece un directorio donde se realizará la sincronización (copia exacta del directorio de origen) y otro donde se guaradarán los incrementales (backup-dir).

- Añade al **cron** de tu equipo una instrucción de manera que todos los días a una hora concreta, se haga una copia del directorio anterior en la máquina destino, dejando la sincronización y los incrementales en los directorios correspondientes. Evidentemente, tendrás que configurar todo lo necesario para que la copia se haga correctamente sin pedir usuario y contraseña y tendrás que utilizar el comando correcto de ```rsync``` de forma que se realice todo con **un único comando**. Además, fuerza a que se ejecute en una hora próxima a la hora actual para que puedas comprobar el funcionamiento correcto.

- Sube a tu repositorio una copia del fichero de cron.

- Sube a la entrega de la tarea en *Aules* un enlace al documento de tu repositorio donde has redactado todo el proceso, con capturas de las ejecuciones, etc.
