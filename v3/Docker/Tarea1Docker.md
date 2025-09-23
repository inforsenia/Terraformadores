# 🌌 Práctica de Docker Avanzado en Terraformadores de Venus

En **Terraformadores de Venus** trabajamos cada día con tecnologías que permiten desplegar servicios de forma rápida, escalable y sin errores de compatibilidad. Entre ellas, **Docker** es una de las más importantes: nos permite empaquetar aplicaciones en contenedores listos para ejecutarse en cualquier entorno.

En esta práctica vas a realizar una serie de ejercicios para afianzar los conceptos clave de Docker: **contenedores en segundo plano, uso de volúmenes, construcción de imágenes personalizadas, orquestación con Docker Compose y despliegue de aplicaciones reales**.

La secuencia de ejercicios está pensada para que paso a paso adquieras soltura en el uso de Docker, siempre con ejemplos aplicables a los proyectos de Terraformadores.

---

## 🚀 Ejercicio 1: Servidor Nginx en modo demonio

Terraformadores necesita desplegar un servicio web ligero para mostrar documentación interna.

* Crea un contenedor en **segundo plano (modo demonio)** utilizando la imagen oficial de **nginx**.
* Verifica desde el navegador de tu máquina que el servidor está funcionando correctamente.
* Investiga cómo **ver los logs** del contenedor y muéstralos en tu entrega.

📌 *Este ejercicio te permitirá comprobar lo fácil que resulta levantar servicios web con Docker y monitorizar su actividad.*

### 🔎 Pistas

* Para arrancar un contenedor en segundo plano usa:

  ```bash
  docker run -d -p ...
  ```
* Para ver los logs del contenedor:

  ```bash
  docker logs ...
  ```

---

## 📂 Ejercicio 2: Uso de volúmenes en Nginx

En Terraformadores no basta con levantar contenedores: necesitamos **persistencia de datos** y poder modificar contenidos fácilmente.

* Crea un contenedor de **nginx** que utilice un volumen para servir los archivos de la página web.
* Modifica un fichero HTML en el **host** y comprueba que el cambio se refleja inmediatamente en el contenedor.
* Explica la diferencia entre un **volumen nombrado** y un **bind mount**, e indica cuál has usado en tu prueba.

📌 *Este ejercicio te ayudará a entender cómo se maneja la persistencia y la compartición de datos entre contenedores y host.*

### 🔎 Pistas

* Un **bind mount** se define con `-v ruta_host:ruta_contenedor`.
* Por ejemplo, si en tu host tienes un directorio `./miweb` con un `index.html`, puedes montarlo así:

  ```bash
  docker run -d -p 8080:80 -v ./miweb:/usr/share/nginx/html nginx
  ```
* Cualquier cambio en `miweb/index.html` se reflejará al instante.

---

## 🛠️ Ejercicio 3: Construcción de una imagen con Dockerfile

Terraformadores necesita personalizar algunos de sus servicios para que no dependan solo de imágenes externas.

* Crea un **Dockerfile** que parta de la imagen oficial de **nginx** y copie dentro un `index.html` personalizado.
* Construye tu propia imagen con un nombre reconocible.
* Lanza un contenedor a partir de tu nueva imagen y comprueba que sirve tu página personalizada.

📌 *Este ejercicio te mostrará cómo generar imágenes personalizadas y reutilizables, clave en los despliegues internos de Terraformadores.*

### 🔎 Pistas

* Usa en el `Dockerfile`:

  ```dockerfile
  FROM ...
  COPY index.html `ruta_dentro_del_contenedor`
  ...
  ...
  ```
* Construir la imagen:

  ```bash
  docker build -t nombre_imagen ruta_al_dockerfile (generalmente . si estas en la misma carpeta)
  ```
* Ejecutar un contenedor desde tu nueva imagen

---

## ⚙️ Ejercicio 4: Orquestación básica con Docker Compose

En Terraformadores necesitamos coordinar varios servicios a la vez, y hacerlo contenedor por contenedor resulta ineficiente. Para ello utilizamos **Docker Compose**, que permite levantar entornos completos con un solo fichero.

* Crea un fichero `docker-compose.yml` con dos servicios:

  * Un servicio **nginx** expuesto en el puerto 8080.
  * Un servicio **goaccess** (analizador de logs) que se conecte al contenedor de nginx para monitorizar en tiempo real sus registros de acceso.

* Ambos servicios deben estar en la misma red interna definida en el fichero Compose.

* Arranca los servicios con `docker-compose up -d`.

* Comprueba que puedes acceder a la web servida por nginx y que goaccess está procesando sus logs.

📌 *Este ejercicio te muestra cómo levantar un pequeño ecosistema de servicios colaborativos, muy habitual en entornos profesionales como Terraformadores.*

### 🔎 Pistas

* La estructura básica de un `docker-compose.yml` es:

  ```yaml
  version: '3'
  services:
    servicio1:
      image: ...
    servicio2:
      image: ...
  ```
* Para conectar servicios entre sí, basta con declararlos dentro del mismo fichero Compose (la red se crea automáticamente).
* Comandos útiles:

  * Levantar servicios: `docker-compose up -d`
  * Listar servicios: `docker-compose ps`
  * Ver logs: `docker-compose logs -f`

---

## ☁️ Ejercicio 5: Despliegue de Nextcloud

Terraformadores necesita un sistema de almacenamiento en la nube para compartir documentación entre los distintos equipos de trabajo. Para ello vamos a desplegar **Nextcloud** dentro de un contenedor Docker.

* Revisa la documentación oficial de Nextcloud en **Docker Hub**.
* Crea un contenedor que despliegue la aplicación Nextcloud.
* Personaliza la configuración del `docker run` para que use una base de datos **sqlite** con un nombre de fichero definido por ti.
* Debes lanzar el contenedor con un volumen en la misma carpeta donde se lanza el contenedor para persistir datos
* Accede desde el navegador y realiza el proceso de configuración inicial.

📌 *Con este ejercicio practicarás el despliegue de una aplicación real de uso profesional utilizando Docker.*

### 🔎 Pistas

* Busca en Docker Hub la imagen `nextcloud`.
* Recuerda lanzar el contenedor con un volumen para persistir datos
* Antes de lanzar el contenedor busca el parámetro que tienes que añadir al `docker run` para elegir **SQLite** como motor de base de datos y definir el nombre del fichero de datos.

---

## 📑 Entrega

Debes entregar un documento en **Markdown** en tu repositorio de **GitLab/GitHub**, que incluya:

* Una breve explicación de cada paso realizado.
* Capturas de pantalla que demuestren el funcionamiento de cada ejercicio.
