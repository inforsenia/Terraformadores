### Segundo Ejercicio de Git: Trabajando con Ramas en el Proyecto de Terraformadores de Venus

En **Terraformadores de Venus**, el trabajo en equipo y la colaboración eficiente son esenciales para gestionar la infraestructura crítica que operamos. En este ejercicio, Beast os guiará en el uso avanzado de **Git**, especialmente en el manejo de **ramas**, lo cual os permitirá realizar cambios sin afectar la rama principal del proyecto. Vamos a trabajar de manera aislada para luego fusionar los cambios cuando estén listos, un enfoque clave en el desarrollo profesional.

---

### Primera Parte: Explicación y Práctica Individual

#### Conceptos Clave: ¿Qué es una Rama?

Una rama en **Git** representa una línea independiente de desarrollo. Imagina que es una copia paralela de tu proyecto donde puedes trabajar libremente, sin afectar el trabajo en la rama principal. Los cambios en una rama no se reflejan en otras hasta que decides fusionarlos, lo cual permite realizar pruebas o desarrollos en un entorno aislado.

#### Ejercicio: Manejo de Ramas

1. **Listar las ramas locales:**
   Ejecuta el siguiente comando para listar las ramas locales:

   ```bash
   $ git branch
   ```

   Observa que estás en la rama principal **main**, marcada con un asterisco.

2. **Crear una nueva rama:**
   Crea una nueva rama donde puedas trabajar de forma aislada:

   ```bash
   $ git branch [nombre_rama]
   ```

   Para cambiar a la nueva rama, usa el siguiente comando:

   ```bash
   $ git checkout [nombre_rama]
   ```

   También puedes crear y cambiarte a la nueva rama con un solo comando:

   ```bash
   $ git checkout -b [nombre_rama]
   ```

3. **Modificar y realizar cambios:**
   Realiza modificaciones en la nueva rama, como crear o modificar un fichero. Por ejemplo:

   ```bash
   $ echo "Nuevo contenido en la rama [nombre_rama]" > fichero.txt
   $ git add fichero.txt
   $ git commit -m "Añadido nuevo fichero en la rama [nombre_rama]"
   ```

4. **Fusionar ramas:**
   Cuando termines los cambios en la nueva rama, vuelve a la rama principal y fusiona los cambios:

   ```bash
   $ git checkout main
   $ git merge [nombre_rama]
   ```

5. **Gestionar conflictos:**
   Para generar y resolver un conflicto, sigue estos pasos:
   
   - Crea un fichero `prueba.txt` en la rama **main** y haz un commit.
   - Cambia a una nueva rama, modifica el fichero y haz otro commit.
   - Vuelve a la rama **main**, modifica el fichero de nuevo y luego intenta fusionar la nueva rama.
   - Si surge un conflicto, Git te lo mostrará y podrás resolverlo manualmente. 

6. **Sincronizar con el remoto:**
   Para que la nueva rama esté disponible en el repositorio remoto de **GitLab**, debes ejecutar el siguiente comando:

   ```bash
   $ git push origin [nombre_rama]
   ```

7. **Eliminar una rama:**
   Una vez fusionada la rama, elimínala para mantener el repositorio limpio:

   ```bash
   $ git branch -d [nombre_rama]
   ```

#### ¿Qué tienes que entregar?

1. Crea una rama llamada `primera` en tu repositorio local, realiza un commit en esa rama, y fusiónala con la principal. Indica si se ha producido algún conflicto y razona tu respuesta.
2. Elimina la rama `primera`.
3. Crea una nueva rama llamada `segunda`, modifica un fichero para generar un conflicto, y fusiónala con la rama principal. Entrega el contenido del fichero donde se ha producido el conflicto y la resolución.
4. Haz un **push** de la rama `segunda` al repositorio remoto en **GitLab**. Entrega una captura de pantalla donde se vea la creación de la rama en el repositorio remoto.

---

### Segunda Parte: Trabajo en Equipo con Git

En **Terraformadores de Venus**, la colaboración en equipo es fundamental. Ahora que ya tienes claro cómo funcionan las ramas, es el momento de poner en práctica tus habilidades en un entorno colaborativo. Trabajaréis en parejas para experimentar la gestión de conflictos y la resolución conjunta de problemas.

#### Ejercicio: Trabajo en Equipo con Ramas y Conflictos

1. **Crear un repositorio compartido:**
   Trabaja en pareja para crear un repositorio compartido en **GitLab**. Uno de vosotros creará el repositorio y añadirá al otro como colaborador.

2. **Trabajo colaborativo con ramas:**
   Cada miembro del equipo creará su propia rama dentro del mismo proyecto. En ambas ramas, modificad el mismo fichero con diferentes contenidos. Recuerda hacer commits de los cambios realizados.

3. **Generar un conflicto:**
   Sin saber lo que ha modificado tu compañero, ambos debéis realizar modificaciones en el mismo fichero, lo que generará un conflicto al intentar fusionar las ramas.

4. **Resolución del conflicto:**
   Una vez generado el conflicto, trabajad juntos para resolverlo. Git os mostrará las diferencias entre las ramas, y debéis decidir cómo dejar el fichero final.

5. **Historial de commits:**
   Al final, deberéis mostrar el historial de commits con fechas y autores, tanto desde la consola como desde **GitLab**. Esto os permitirá ver claramente quién hizo cada cambio y cuándo.

#### ¿Qué tienes que entregar?

1. Capturas de pantalla mostrando el conflicto generado y cómo se ha resuelto.
2. Capturas del historial de commits, tanto desde la consola como desde el repositorio remoto en **GitLab**, mostrando los cambios realizados por ambos miembros del equipo.

---

Este ejercicio, guiado por **Beast**, os ayudará a dominar el uso de **ramas** en Git, una habilidad esencial en vuestro trabajo diario en **Terraformadores de Venus**. Además, aprenderéis a colaborar eficazmente, a resolver conflictos y a mantener el control sobre los cambios de manera eficiente.