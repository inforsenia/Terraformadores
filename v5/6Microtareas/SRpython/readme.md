## Desarrollo de un protocolo propio de monitorización

### **SDMP/1.0 – Simple Disk Monitoring Protocol**

---

## 🎯 Objetivo de la práctica

El objetivo de esta práctica es que el alumnado diseñe e implemente un **servicio de red cliente-servidor en Python**, utilizando **sockets TCP** y un **protocolo de aplicación propio**, basado exclusivamente en el intercambio de mensajes **JSON**.

El sistema permitirá que un cliente envíe **una única vez información del uso de disco** al servidor, y que este **almacene dicha información en un archivo de registro**, siguiendo un flujo de comunicación previamente definido.

---

## 🧠 Competencias y conceptos trabajados

* Programación cliente-servidor
* Comunicación mediante sockets TCP
* Diseño de protocolos de aplicación
* Serialización de datos con JSON
* Gestión de ficheros de registro
* Control del flujo de comunicación

---

## 🛠️ Tecnologías y librerías permitidas

La práctica se desarrollará en **Python 3**, utilizando exclusivamente librerías de la biblioteca estándar:

* `socket` → comunicación en red
* `json` → serialización de mensajes
* `platform` → identificación del sistema cliente
* `shutil` → obtención del uso de disco
* `datetime` → marca temporal en los registros
* `os` *(opcional)* → gestión de archivos
* `threading` *(opcional)* → soporte para múltiples clientes

⚠️ **No está permitido** el uso de frameworks, librerías externas ni bases de datos.

---

## 📜 Descripción del servicio

El protocolo **SDMP/1.0** define un servicio de tipo *collector* donde:

* El **cliente** se conecta al servidor, envía sus datos y finaliza.
* El **servidor** recibe la información y la almacena en un archivo de registro.

Toda la comunicación se realiza mediante **mensajes JSON**, y todos los mensajes deberán incluir obligatoriamente la clave `comando`.

---

## 🔄 Flujo de comunicación del protocolo SDMP/1.0

### 1️⃣ Conexión y saludo

Una vez establecida la conexión TCP, el cliente enviará el siguiente mensaje:

```json
{
  "comando": "HOLA",
  "nombre": "<nombre_del_equipo>",
  "sistema": "<sistema_operativo>"
}
```

El servidor responderá con:

```json
{
  "comando": "BIENVENIDO",
  "mensaje": "Conexión establecida correctamente"
}
```

---

### 2️⃣ Envío de información del sistema

Tras recibir la bienvenida, el cliente enviará **una única vez** los datos del uso de disco:

```json
{
  "comando": "DATOS_DISCO",
  "datos": {
    "punto_montaje": "/",
    "total": <bytes>,
    "usado": <bytes>,
    "libre": <bytes>,
    "porcentaje": <float>
  }
}
```

El servidor deberá:

* Validar el comando recibido
* Almacenar la información en un fichero
* Confirmar la recepción con:

```json
{
  "comando": "OK",
  "mensaje": "Datos almacenados correctamente"
}
```

---

### 3️⃣ Cierre de la conexión

Para finalizar la comunicación, el cliente enviará:

```json
{
  "comando": "ADIOS"
}
```

El servidor responderá:

```json
{
  "comando": "HASTA_LUEGO",
  "mensaje": "Desconexión correcta"
}
```

Ambas partes cerrarán la conexión de forma ordenada.

---

## 🗄️ Almacenamiento de datos en el servidor

El servidor deberá guardar los datos recibidos en un fichero de texto llamado, por ejemplo:

```
sdmp_registro.log
```

### 📄 Requisitos del fichero de registro

Cada línea del fichero deberá contener, como mínimo:

* Fecha y hora de recepción
* Dirección IP del cliente
* Nombre del equipo
* Sistema operativo
* Punto de montaje
* Porcentaje de uso del disco

📌 El formato es libre, pero debe ser:

* Legible
* Consistente
* Una línea por conexión

### ✍️ Ejemplo de registro

```text
2026-01-28 11:05:42 | 192.168.1.15 | aula-pc-07 | Linux | / | 71.2% usado
```

---

## 📐 Reglas del protocolo

* Todos los mensajes **DEBEN** ser JSON válido.
* Todos los mensajes **DEBEN** incluir la clave `comando`.
* El servidor **NO debe mostrar los datos por pantalla**, solo mensajes de estado.
* El fichero de registro **no debe sobrescribirse**, los datos se añadirán al final.
* El servidor deberá gestionar comandos desconocidos sin bloquearse.
* La comunicación es síncrona y basada en TCP.

---
## Servicio en red
El programa servidor.py deberá ejecutarse automáticamente al arrancar el sistema, utilizando systemd. Nombre del servico sdmp.service


## 📁 Entregables

El alumnado deberá entregar:

1. `servidor.py` 
2. `cliente.py`
3. `sdmp.service`
3. Documento explicativo (PDF o Markdown) que incluya:

   * Descripción del protocolo SDMP/1.0
   * Diagrama del flujo de comunicación
   * Ejemplo del fichero de registro generado
   * Breve explicación del funcionamiento

---

## 🧪 Ampliaciones opcionales (subida de nota)

* Soporte para múltiples clientes simultáneos
* Exportación del registro a formato CSV
* Validación avanzada de datos recibidos
* Inclusión de nuevos comandos en el protocolo
* Manejo de excepciones de red