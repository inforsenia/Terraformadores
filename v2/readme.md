<a name="principio"></a>
## ASGBD - Jean Grey llamando a la Tierra

### Comunicación con el resto de planetas del sistema solar
Bienvenidos al equipo de trabajo de telecomunicaciones entre los planetas habitados de la **Vía Lactea**.
Nuestra tarea es poder obtener información económica de los planetas que conforman la Vía Lactea, para ello tenemos una Base de Datos Distribuida, en la que cada planeta tiene una super base de datos, que replicará su información en los planetas habitados vecinos. La base de datos contiene información económica de sus principales países.

Aunque Jean Grey tiene poderes de telepática y telequinética, no es capaz de trasladar toda la información de la base de datos a los planetas vecinos, por esta razón necesita vuestra ayuda.

### Acometido de las tareas
Próximamente se va a conectar nuestra Base de Datos Distribuida a las galaxias vecinas, por lo que necesitamos tener todas las comunicaciones correctamente. Necesitaremos:
- Tener una base de datos documental, que nos diga con qué planeta debo contactar en caso de que la comunicación del planeta en el que vivo, tenga interferencias por *radiación solar* o *distorsión de señales* por lluvia de meteoritos.
- Comunicación plena con cualquier planeta de la Vía Lactea, a través de la Base de Datos Distribuida.
- Automatización de las comunicaciones.

### Contacto
El equipo de trabajo puede contactar con Jean Grey por telepatía, de lunes a viernes de 8:00 a 14:30.
Un saludo
    Jean Grey.

## Enunciados y tareas a realizar:
* [Preparando el Sistema](#preparacion)
* [Elaborando guiones: cursores y disparadores](#guiones)

![Poderes de Jean Gray](./Jean_Gray.png)

<a name="preparacion"></a>
### **Preparando el Sistema**
### Preparación de las herramientas adecuadas
El equipo de trabajo elegido de entre toda la Vía Láctea, va pasar a trabajar en la preparación del software necesario, para podernos comunicarnos con el resto de planetas habitados, para esto se requieren las siguientes tareas, que serán **debidamente documentadas** para poder obtener el certificado de calidad:
### Implantación de sistemas gestores de bases de datos analizando sus características y ajustándose a los requerimientos del sistema.
- Deberemos analizar el uso y función de los dos elementos de los sistema gestor de bases de datos, tanto en Oracle como en el SGBD de software libre elegido, que sea capaz de trabajar con bases de datos distribuidas y relacionales.
- Analizar las características de los dos SGBD con los que vamos a trabajar.
- Identificar el software necesario para llevar a cabo la instalación, además de verificar el cumplimiento de los requisitos hardware.
- Documentar el proceso de instalación
- Interpretar la información suministrada por los mensajes de error y ficheros de registro, documentando los errores y problemas que han ido surgiendo y cómo se ha solucionado.
- Resolver las incidencias de la instalación.
- Verificar que los SGBD funcionan de forma correcta.

### Configuración de los sistema gestor de bases de datos (SGBD) interpretando las especificaciones técnicas y los requisitos de explotación
- Crear: usuarios administradores y usuarios normales.
- Configurar herramientas y software cliente del sistema gestor.
- Configurar la conectividad en red del sistema gestor.
- Definir las características por defecto de las bases de datos: tablespace, contraseñas, espacio de memoria por defecto, etc.
- Definir los parámetros relativos a las conexiones (tiempos de espera, número máximo de conexiones, entre otros).
- Documentar el proceso de configuración.

### Implantación de métodos de control de acceso utilizando asistentes, herramientas gráficas y comandos del lenguaje del sistema gestor
Para garantizar que cada usuario solamente podrá acceder a los objetos para los que va a tener permiso, deberemos:
- Definir y eliminar cuentas de usuario.
- Identificar los privilegios sobre las bases de datos y sus elementos.
- Agrupar y desagrupar privilegios en roles
- Asignar y eliminar privilegios a usuarios.
- Asignar y eliminar grupos de privilegios a usuarios.
- Garantizar el cumplimiento de los requisitos de seguridad.
- Crear sinónimos de tablas y vistas.
- Crear vistas personalizadas para cada tipo de usuario.
  
[Subir](#principio)

<a name="guiones"></a>  
## **Guiones de sentencias**
### Objetivos:
1. Reconocerla importancia de automatizar tareas administrativas.
2. Describir los distintos métodos de ejecución de guiones.
3. Identificar las herramientas disponibles para redactar guiones.
4. Definir y utilizar guiones para automatizar tareas.
5. Identificar los eventos susceptibles de activar disparadores.
6. Definir disparadores.
7. Utilizar estructuras de control de flujo.
8. Adoptar medidas para mantener la integridad y consistencia de la información.

### Tareas a realizar:
Queremos configurar y administrar la información de cada planeta, para ello debemos preparar a los paises con las tablas que se acuerden en el Congreso Interplanetario de Informáticos.
Se deberán analizar las necesidades, acordar una nomenclatura de codificación y ver las necesidades.

#### Tarea 1:
Se necesita crea un procedimiento que muestre el nombre de los usuarios y el planeta en el que viven, siempre que hayan nacido antes del año introducido por parámetro.  
Utilizando parámetros de cursores y tratando las excepciones preestablecidas.

#### Tarea 2:
Se requiere mostrar los movimientos en la cuenta de los usuarios, según los parámetros de entrada del procedimiento que será: el código del país, el código del usuario y la fecha. 
Utilizando parámetros de cursores y tratando las excepciones preestablecidas.

#### Tarea 3:
Se requiere crear un procedimiento que reciba el nombre de una ciudad y que imprima el salario de todos los usuarios de esa ciudad y el número de usuarios. 
Utilizando parámetros de cursores y tratando las excepciones preestablecidas.
Por ejemplo: 

|Población |Número de usuario|Saldo        |
|----------|-----------------|---------------|
|Keocs     |234              |875412  |

#### Tarea 4:
Se requiere crear una función llamada comprueba_saldo, que recibirá el valor de todos los campos para realizar una extracción monetaria. Creando una excepción propia para que, en caso de que el saldo quede negativo cuando se extraiga la cantidad solicitada, muestre un mensaje en la parte de excepciones diciendo "Operación no permitida. Saldo negativo". Si ha ido todo bien la función devolverá True y en caso contrario devolverá False. 
 
[Subir](#principio)

