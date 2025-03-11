
### Prueba Objetiva: Configuración de Servidores Web y Servicios de Transferencia de Archivos

**RA3. Administra servidores web aplicando criterios de configuración y asegurando el funcionamiento del servicio.**

**RA4. Administra servicios de transferencia de archivos asegurando y limitando el acceso a la información.**

---

#### Contexto:

La **Asociación de Turismo Ecológico "EcoTravel"** ha solicitado tu ayuda para configurar su infraestructura web y servicios de transferencia de archivos. La asociación gestiona varios sitios web relacionados con destinos turísticos ecológicos y necesita que los colaboradores puedan publicar contenido en sus respectivas secciones. Además, requieren que los servicios sean seguros y estén bien organizados.

La asociación ha proporcionado los siguientes requerimientos:

---

### Requerimientos de Configuración:

#### 1. **Configuración de Virtual Hosts en Apache:**

- Los sitios web deben alojarse en directorios base diferentes:
  - El sitio `www.ecoamazonia.com` debe estar en `/var/www/ecoamazonia/`
    Los diseñadores han realizado esta [web](vh_ecoamazonia/index.html) [ecoamazonia.zip](vh_ecoamazonia.zip)
  - El sitio `www.ecopatagonia.com` debe estar en `/srv/www/ecopatagonia/`
    Los diseñadores han realizado esta [web](vh_ecopatagonia/index.html)[ecopatagonia.zip](vh_ecopatagonia.zip)


- **Configuración de hosts virtuales:**
  - Configurar un host virtual en Apache que responda con la web ubicada en `/var/www/ecoamazonia/` cuando se reciba una petición a `https://www.ecoamazonia.com/`. Siempre debe mostrar seguridad SSL si recibe una petión http://www.ecoamazonia.com debe redirigirla a https://www.ecoamazonia.com/. El certificado será autofirmado.
  - Configurar un nuevo host virtual en Apache que responda con la web ubicada en `/srv/www/ecopatagonia/` cuando se reciba una petición a `http://www.ecopatagonia.com/`.


#### 2. **Publicación de páginas personales de los colaboradores:**

- Configurar Apache para que los colaboradores locales puedan publicar sus propias páginas web.
- Crear un usuario local llamado `eco1` con la contraseña `eco1`.
- El usuario `eco1` debe crear un archivo llamado `index.html` en su espacio web con el siguiente contenido:

  ```html
  <!DOCTYPE html>
  <html>
  <body> Eco1 Says Welcome to EcoTravel!</body>
  </html>
  ```

  Este contenido debe ser accesible desde `http://www.ecoamazonia.com/~eco1`.



#### 3. **Seguridad Digest:**

- Configurar seguridad digest en el virtual host de `http://www.ecopatagonia.com/` para proteger el acceso al directorio `glaciers`.
- Solo el usuario `explorer` con contraseña `explorer` podrá acceder a `http://www.ecopatagonia.com/glaciers`.

#### 4. **Configuración del servidor Nginx:**

- Configurar un servidor Nginx separado, que escuche en el puerto 8090.
- Este servidor responderá con la web ubicada en `/srv/www/ecotravel/` cuando se reciba una petición a `http://ecotravel.org:8090`.

---

### Requerimientos Adicionales (RA4):

#### 6. **Configuración de un servidor FTPS seguro:**

- Configurar el servidor para que utilice el protocolo FTPS empleando el mismo certificado SSL configurado anteriormente.
- El servidor FTPS debe estar configurado en modo pasivo para que los clientes no tengan que modificar sus firewalls.
- El usuario `eco1` podrá subir y descargar archivos exclusivamente en su directorio de publicación, `/home/eco1/public_html/`.
- El usuario `eco1` debe estar enjaulado dentro de su directorio personal para que no tenga acceso a otras partes del sistema.

#### 7. **Acceso por SFTP:**

- Configurar el servidor para que los usuarios puedan conectarse mediante SFTP.
- Los usuarios estarán enjaulados en la carpeta de publicación de sus respectivas webs, de modo que solo puedan gestionar sus propios archivos sin acceso a otras partes del servidor.

---

### Batería de Pruebas:

Para verificar que la configuración se ha realizado correctamente, se deben probar los siguientes accesos:

1. **Accesos Web:**
   - `http://www.ecoamazonia.com/`
   - `http://www.ecoamazonia.com/~eco1`
   - `https://www.ecoamazonia.com/`
   - `http://www.ecopatagonia.com/`
   - `http://www.ecopatagonia.com/glaciers` (requiere autenticación digest)
   - `http://ecotravel.org:8090`

2. **Accesos de Transferencia de Archivos:**
   - Acceso por FTPS con el usuario `eco1` a `/home/eco1/public_html/`.
   - Acceso por SFTP con el usuario `eco1` enjaulado en `/home/eco1/public_html/`.

