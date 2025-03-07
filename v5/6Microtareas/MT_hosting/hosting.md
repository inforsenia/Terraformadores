**RA3. Administra servidores web aplicando criterios de configuración y asegurando el funcionamiento del servicio.**

La asociación de fans de David Bowie nos ha solicitado ayuda para configurar su infraestructura web. Quieren disponer de varios sitios web relacionados con la comunidad y su admiración por el artista. Nos han proporcionado los siguientes requerimientos para que la experiencia de los usuarios sea la mejor posible.

Todos los sitios web deben alojarse en la carpeta **/srv/www/bowie/**, con subdirectorios específicos para cada dominio. Por ejemplo, **/srv/www/bowie/davidbowie/** para www.davidbowie.edu, **/srv/www/bowie/starman/** para www.starman.edu, etc.

Atentos por que el informático de la asociación es muy exigente con la configuración y ha solicitado que la web principal de la asociación **bowiefans.org** esté en un servidor **nginx** separado, funcionando en el puerto **8080**. El resto de sitios web se alojarán en **Apache**. 
La asociación quiere que sus usuarios puedan publicar páginas web propias pero no quiere pagarles un dominio propio, así que, utilizarán el sitio **www.davidbowie.edu**
A continuación, se detallan las configuraciones requeridas:

### Requerimientos

1. **Configuración de Virtual Hosts en Apache:**
   - Configurar un host virtual en Apache que responda con la web ubicada en **/srv/www/bowie/davidbowie/** cuando se reciba una petición a **http://www.davidbowie.edu/**.
        - Está es la web que ha hecho el diseñador. [davidbowie.edu](vh1_24_25.zip)

   - Configurar un nuevo host virtual en Apache que responda con la web ubicada en **/srv/www/bowie/starman/** cuando se reciba una petición a **http://www.starman.edu/**.
         - Está es la web que ha hecho el diseñador. [starman.edu](vh2_24_25.zip)


2. **Publicación de páginas personales de los asociados:**
   - Configurar Apache para que los usuarios locales puedan publicar sus propias páginas web.
   - Crear un usuario local llamado **ziggy** con la contraseña **ziggy**.
   - Para probar hacer que el usuario **ziggy** cree un archivo llamado **index.html** en su espacio web con el siguiente contenido:
     ```html
     <!DOCTYPE html>
     <html>
     <body> Ziggy Says Hello</body>
     </html>
     ```
   - Este contenido debe ser accesible desde **http://www.davidbowie.edu/~ziggy**.

3. **Seguridad SSL:**
   - Configurar Apache con seguridad SSL para que sea capaz de resolver peticiones a **https://www.davidbowie.edu/**.
   - El certificado SSL debe incluir en el **Common Name (CN)** el nombre **davidbowie.edu**.

4. **Seguridad Digest:**
   - Configurar seguridad digest en el virtual host de **http://www.starman.edu/** para proteger el acceso al directorio **blackstar**.
   - Solo el usuario **majortom** con contraseña **majortom** podrá acceder a **http://www.starman.edu/blackstar**.

5. **Configuración del servidor Nginx:**
   - Configurar un servidor **nginx** separado, que escuche en el puerto **8080**.
   - Este servidor responderá con la web ubicada en **/srv/www/bowie/bowiefans/** cuando se reciba una petición a **http://bowiefans.org:8080**.

### Batería de pruebas
Para verificar que la configuración se ha realizado correctamente, se deben probar los siguientes accesos:
- **http://www.davidbowie.edu/**
- **http://www.davidbowie.edu/~ziggy**
- **https://www.davidbowie.edu/**
- **http://www.starman.edu/**
- **http://www.starman.edu/blackstar** (requiere autenticación digest)
- **http://bowiefans.org:8080**

Con esta configuración, la asociación de fans podrá gestionar su red de sitios web con Apache y Nginx cumpliendo con sus necesidades y garantizando la seguridad y accesibilidad de sus páginas.



**RA4. Administra servicios de transferencia de archivos asegurando y limitando el acceso a la información.**

### Expansión del Proyecto: Configuración de Hosting

La asociación de fans de David Bowie también desea ofrecer a sus miembros la posibilidad de alojar y actualizar sus páginas web dentro del servidor. Para ello, se han solicitado las siguientes configuraciones adicionales:

6. **Configuración de un servidor FTPS seguro:**
   - Configurar el servidor para que utilice el protocolo **FTPS** empleando el mismo certificado SSL configurado anteriormente.
   - El servidor FTPS debe funcionar estar configurado en un modo adecuado para que los clientes no tengan que modificar sus firewalls
   - El usuario **ziggy** podrá subir y descargar archivos exclusivamente en su directorio de publicación, **/home/ziggy/public_html/**.
   - El usuario **ziggy** debe estar **enjaulado** dentro de su directorio personal para que no tenga acceso a otras partes del sistema.

7. **Acceso por SFTP:**
   - Configurar el servidor para que los usuarios puedan conectarse mediante **SFTP**.
   - Los usuarios estarán **enjaulados** en la carpeta de publicación de sus respectivas webs, de modo que solo puedan gestionar sus propios archivos sin acceso a otras partes del servidor.

### Batería de pruebas
Para verificar que la configuración se ha realizado correctamente, se deben probar los siguientes accesos:
- **Acceso por FTPS con el usuario ziggy a /home/ziggy/public_html/**
- **Acceso por SFTP con los usuarios enjaulados en sus respectivas carpetas de publicación  /home/ziggy/public_html/**

Con esta configuración, la asociación de fans podrá gestionar su red de sitios web con Apache y Nginx, además de ofrecer un servicio de hosting seguro para sus miembros, garantizando la privacidad y seguridad de los archivos alojados.

