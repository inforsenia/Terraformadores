# UD3 – Técnicas de Acceso Remoto

## Tarea 1: VPN acceso remoto

En esta tarea vamos a simular unas empresas en las que habilitaremos **conexiones VPN** para el acceso remoto de clientes individuales.
       
Trabajaremos por parejas y cada una dispondrá de un router Mikrotik con el que simulará su propia empresa. Deberemos crear una red interna con un direccionamiento diferente al del resto de compañeros. El router hará de enlace entre la red interna de la empresa e *Internet*, pero para poder hacer las pruebas haremos un Internet simulado: será la **red del aula**. Así pues, todos los routers tendrán configurada la interfaz externa como **cliente DHCP**.
       
Habrá que configurar los direccionamientos correspondientes para que cada equipo interno alcance *Internet*.
       
Como equipos internos podemos tener uno de los dos ordenadores físicos de la pareja y/o alguna máquina virtual en adaptador puente.

Una vez tenemos la base para poder trabajar (las empresas) vamos a **configurar las VPNs**.
       
En cada router habrá que configurar un **servidor VPN** de manera que podemos conectarnos a la red interna de la empresa desde cualquier lugar de *Internet* (en nuestro caso, desde cualquier ordenador de otra empresa o del aula). En la configuración crearemos 3 usuarios: dos genéricos y otro para el profesor. 

Este enlace pueden ser de ayuda: 

[Configure OpenVPN Server on MikroTik](https://www.d4d.lt/how-to-configure-the-openvpn-server-on-the-mikrotik-router)

Una vez configurado el servidor VPN en el router, configuraremos el **cliente OpenVPN** en alguna de nuestras máquinas para conectarnos a la VPN de otra empresa. Investiga la instalación y fichero de configuración del cliente.
       
Haremos pruebas para ver la *dirección IP* que tenemos una vez conectados y para comprobar que podemos hacer *ping* al resto de equipos de la empresa.

Documenta el proceso en GitHub/GitLab aportando explicaciones y capturas de los pasos.
