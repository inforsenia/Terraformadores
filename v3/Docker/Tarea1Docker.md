### Introducción a Docker en Terraformadores de Venus

En **Terraformadores de Venus**, la eficiencia y la flexibilidad son claves para gestionar nuestra infraestructura. **Docker** es una herramienta esencial que permite empaquetar aplicaciones y todas sus dependencias en contenedores aislados, lo que asegura que se ejecuten de manera consistente en cualquier entorno. Esto minimiza problemas de compatibilidad y facilita el despliegue continuo, vital para las operaciones de nuestra empresa.

Sabemos que el equipo de **Iceman** os guiará en el aprendizaje más avanzado de **Docker**, pero esta tarea servirá para reforzar algunos de los conceptos básicos, esenciales en vuestro trabajo en **Terraformadores de Venus**. Docker será una herramienta central en muchas de las soluciones que desarrollaréis.

### Ejercicio: Primeros Pasos con Docker

1. **Instalación de Docker:**
   - Investiga cómo instalar Docker en una máquina y configurarlo para que puedas usarlo sin privilegios de superusuario.

2. **Ejecutar el contenedor hello-world:**
   - Ejecuta un contenedor utilizando la imagen oficial `hello-world` y verifica que devuelve la salida adecuada. 
   - Asegúrate de investigar cómo listar los contenedores detenidos y eliminarlos una vez hayan finalizado.

3. **Crear un contenedor interactivo con Debian:**
   - Crea un contenedor interactivo con la imagen oficial de **Debian**. 
   - Instala un paquete dentro del contenedor, como **nano**.
   - Asegúrate de entender qué ocurre cuando sales del terminal y cómo volver a acceder al contenedor. Además, comprueba si los cambios persisten cuando se reinicia.

4. **Crear un contenedor demonio con nginx:**
   - Crea un contenedor en modo demonio con **nginx**. Accede al servidor desde tu navegador y verifica que funciona correctamente.
   - Investiga cómo mostrar los logs de este contenedor.

5. **Crear un contenedor con Nextcloud:**
   - Crea un contenedor con **Nextcloud** utilizando la documentación en **Docker Hub**. Personaliza la configuración para que utilice una base de datos **SQLite** con un nombre específico que hayas definido.

---

### Entrega

Debes entregar un documento en **Markdown** a través de **GitLab**, en el que incluyas breves explicaciones del proceso seguido, así como capturas de pantalla que demuestren que los ejercicios han sido finalizados correctamente. Asegúrate de documentar cada paso de forma clara y concisa.