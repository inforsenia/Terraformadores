### Primer Ejercicio: Configuración de Redes con Netplan y YAML en Terraformadores de Venus

¡Bienvenidos a vuestra primera misión trabajando con el lenguaje de marcas **YAML** en **Terraformadores de Venus**! En esta ocasión, nos adentraremos en una de las aplicaciones más prácticas de YAML en el ámbito de la administración de sistemas: la configuración de redes en sistemas Linux. 

En **Terraformadores de Venus**, el uso de herramientas como **Netplan** es fundamental para garantizar que nuestras infraestructuras estén siempre optimizadas, conectadas y seguras. Netplan, que utiliza archivos en formato YAML, permite gestionar la configuración de redes de manera sencilla y eficiente. Lo empleamos especialmente en nuestras soluciones basadas en **Ubuntu**, donde facilita la definición y aplicación de configuraciones de interfaces de red, tanto para conexiones por cable como inalámbricas.

**Ejercicio: Configuración de Interfaces de Red en Terraformadores**

Tu misión es configurar tres interfaces de red en uno de nuestros entornos, utilizando **Netplan** y trabajando con **Docker** para desplegar una máquina virtual. A continuación, se detallan las especificaciones que debes seguir para configurar cada una de las interfaces:

- **Interfaz 1 (eth0):** Configura una dirección IP estática con los siguientes parámetros:
  - **Dirección IP:** Debe ser una IP válida dentro del rango de ordenadores de tu aula.
  - **Puerta de enlace:** Utiliza la puerta de enlace que emplean los ordenadores de tu aula.
  - **Servidores DNS:** Configura los servidores DNS de Consellería, que son `10.238.3.7` y `10.238.3.8`.

- **Interfaz 2 (eth1):** Configura esta interfaz para que obtenga su configuración de red automáticamente mediante **DHCP**.

- **Interfaz 3 (wlan0):** Configura una interfaz Wi-Fi. Para ello, deberás introducir el **SSID** de la red y la **contraseña** del punto de acceso que tu profesor habilitará en el aula.

**Entrega del ejercicio:**

En esta tarea, tu objetivo es demostrar no solo que puedes manejar la configuración de redes mediante **YAML** y **Netplan**, sino también que eres capaz de hacerlo dentro de una máquina virtual desplegada con **Docker**. A continuación, se detalla lo que debes entregar:

1. **Archivo YAML:** El fichero de configuración de **Netplan** generado con las tres interfaces de red configuradas.
   
2. **Documento Markdown:** Un documento con explicaciones breves del proceso que seguiste para la configuración de las interfaces. Incluye capturas de pantalla que demuestren que las configuraciones aplicadas en la máquina virtual (desplegada con Docker) se ejecutan correctamente.

Esta es la primera de dos actividades en las que trabajarás con **YAML**, un lenguaje que es de suma utilidad en la administración de sistemas y la gestión de configuraciones en **Terraformadores de Venus**.
