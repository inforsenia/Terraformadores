## Segundo Ejercicio: Domina Git y Conéctate al Repositorio de Terraformadores de Venus

¡Bienvenidos de nuevo a vuestra segunda misión en **Terraformadores de Venus**! En este ejercicio, continuaremos nuestra aventura tecnológica aprendiendo a utilizar **Git** para la gestión y control de versiones, una habilidad esencial en cualquier entorno de desarrollo. Además, aprovecharemos para subir el documento en Markdown que creasteis en el primer ejercicio.

### Ejercicio: Creación y Gestión de Repositorios en GitLab utilizando HTTPS

1. **Crea una cuenta en GitLab (si no la tienes ya).** Este es tu primer paso para conectarte y colaborar en proyectos con el equipo.

2. **Acceso a los repositorios remotos:** Vamos a utilizar HTTPS para conectarnos a los repositorios de GitLab. No es necesario configurar claves SSH para este ejercicio.

3. **Crea un repositorio en GitLab:**
   - Crea un nuevo repositorio con el nombre `prueba_tu_nombre` (reemplaza "tu_nombre" con tu nombre real) y añade una descripción como "Repositorio de prueba 2ASIR".
   - Asegúrate de inicializar el repositorio con un archivo `README.md`.

4. **Instala Git en tu ordenador (si no lo tienes instalado ya).** Utiliza el siguiente comando en tu terminal o consola:

   ```bash
   apt-get install git
   ```

5. **Configuración inicial de Git:** Configura tu nombre de usuario y correo electrónico después de instalar Git.

   ```bash
   git config --global user.name "Tu Nombre Completo"
   git config --global user.email tunombre@ejemplo.com
   ```

6. **Clona el repositorio remoto:** Copia la URL HTTPS de tu repositorio de GitLab y clónalo en tu ordenador.

   ```bash
   git clone https://gitlab.com/tu_usuario/prueba_tu_nombre.git
   ```

7. **Verifica que el archivo `README.md` está presente** en el repositorio clonado.

8. **Sube tu archivo Markdown creado en el primer ejercicio:**
   - Copia el archivo Markdown que creaste sobre el protocolo HTTP en la primera tarea (por ejemplo, `documento_http.md`) a la carpeta de tu repositorio local.

   ```bash
   cp /ruta/a/tu/documento_http.md /ruta/al/repositorio/prueba_tu_nombre/
   ```
   - Añade el archivo al área de preparación:

   ```bash
   git add documento_http.md
   ```
   - Realiza un commit con un mensaje claro:

   ```bash
   git commit -m "Añadido el documento Markdown sobre el protocolo HTTP"
   ```
   - Sincroniza los cambios con tu repositorio remoto en GitLab:

   ```bash
   git push
   ```

9. **Realiza modificaciones adicionales y gestiona los cambios:**
   - Modifica el archivo Markdown (`documento_http.md`) si es necesario y realiza un nuevo commit con la opción `-a` para incluir todos los cambios:

     ```bash
     git commit -am "Actualizado el documento Markdown sobre HTTP"
     git push
     ```
   - Gestiona otros archivos como en las instrucciones originales (crear, renombrar, eliminar) para practicar.

10. **Sincroniza antes de trabajar:** Si trabajas en varios ordenadores, asegúrate de sincronizar tu repositorio local con el remoto:

    ```bash
    git pull
    ```

11. **Revisa el estado del repositorio local:**

    ```bash
    git status
    ```

**¿Qué tienes que entregar?**

- El contenido del fichero `.git/config` para demostrar que has clonado el repositorio usando la URL HTTPS.
- La salida del comando `git log` para ver los commits que has realizado (debe aparecer como autor tu nombre completo).
- **Memoria del proceso:** Documenta todo el proceso seguido con capturas de pantalla en otro fichero Markdown (por ejemplo, `memoria_proceso.md`). Este archivo también debe ser subido al mismo repositorio.EN esta memoria debe aparecer información y capturas de pantalla que muestren cómo creaste un nuevo repositorio llamado `prueba2_tu_nombre`, primero como repositorio local (usando `git init`) y luego sincronizándolo para crear el repositorio remoto en GitLab. Comenta los pasos realizados y proporciona alguna prueba del proceso finalizado.


---

¿Hay algo más que te gustaría ajustar o añadir?