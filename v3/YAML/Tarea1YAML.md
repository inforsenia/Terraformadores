### Tarea 1 YAML: Detección de Errores en YAML

En Terraformadores de Venus trabajamos con gran cantidad de configuraciones para desplegar servicios, contenedores y aplicaciones en nuestros servidores y en la nube privada NimbusNet. El lenguaje YAML es esencial en este proceso, ya que lo utilizamos constantemente para describir servicios, entornos y flujos de despliegue.

Un error en la indentación, en la estructura de los datos o en el tipo de valores puede impedir que todo un sistema se despliegue correctamente. Como parte del equipo técnico, tu misión será detectar y corregir errores en ficheros YAML defectuosos, explicando qué tipo de fallo has encontrado y proponiendo la solución adecuada.


## Enunciado de la Actividad

A continuación se te presentan varios fragmentos YAML con errores. Tu tarea es:

1. **Identificar los errores en cada ejercicio.**
2. **Corregirlos y mostrar la versión correcta.**
3. **Explicar brevemente qué estaba fallando.**

---

### Ejercicio 1: El Error de Indentación

Un despliegue en NimbusNet está fallando debido a un problema. Corrige el fichero:

```yaml
---
servicios:
  - nombre: web
    imagen: nginx:latest
    puertos:
      - "80:80"
      - "443:443"
  - nombre: base_de_datos
  imagen: postgres:13
  entorno:
    - POSTGRES_USER=admin
    - POSTGRES_PASSWORD=secret
```

---

### Ejercicio 2: El Error de Tipo y Sintaxis

Un compañero del equipo de despliegue ha escrito este fichero, pero el orquestador lo rechaza. Analiza y corrige:

```yaml
---
usuario:
  nombre: "Juan Perez"
  edad: '25'
  esta_activo: false
  roles: [administrador, editor]
  configuracion:
    notificaciones_email: ON
```

---

### Ejercicio 3: El Error de Clave Duplicada

NimbusNet no acepta este archivo porque tiene errores. Identifica y corrige:

```yaml
---
aplicacion:
  nombre: "Mi App Web"
  version: 1.0.0
  puertos:
    - "8080:80"
  entorno:
    - URL_DB=localhost
    - PUERTO_DB=5432
  entorno:
    - ENV=production
```

---

### Ejercicio 4: El Error de Estructura de Datos

El siguiente *script* de automatización para pruebas está fallando porque la estructura no es la que espera el sistema. Corrige el error:

```yaml
---
tareas:
  - nombre: despliegue
    pasos:
      - etapa: "construir"
        script: "npm run build"
      - etapa: "desplegar"
        script: "docker-compose up -d"
  - nombre: test
    etapa: "unitarios"
    script: "npm test"
    etapa: "integracion"
    script: "mocha"
```

---

### Ejercicio 5: El Error en Variables de Entorno

El equipo de **Angel** detecta que este archivo YAML para un servicio de Terraformadores no es aceptado por el sistema debido al formato de las variables de entorno. Corrígelo:

```yaml
---
servicio:
  nombre: api_gateway
  imagen: terraformadores/api:1.2
  entorno:
    DATABASE_URL: localhost:5432/db
    DEBUG true
    TIMEOUT=30
```
