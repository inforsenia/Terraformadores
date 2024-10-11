
### UD2 - IAW - 2024 IES LA SENIA

# Tarea 1 - *LAMP en Ubuntu*

En Terraformadores de Venus, el dominio del entorno web es clave para el desarrollo y despliegue de aplicaciones y servicios. Ya hemos trabajado en conceptos importantes como Docker y Git, y ahora, siguiendo con el compromiso de implementar infraestructura robusta, es momento de abordar la instalación y configuración de un entorno web completo. Con la ayuda de los conocimientos previos adquiridos nos aseguraremos de que puedas gestionar servicios web de manera eficiente. La pila LAMP (Linux, Apache, MySQL, PHP) es fundamental en nuestro ecosistema, ya que permite alojar y gestionar aplicaciones web dinámicas de manera eficaz, algo que será esencial en muchos de nuestros proyectos futuros.

---

En esta tarea, tendrás la oportunidad de instalar y configurar la pila LAMP en una máquina Ubuntu, asegurando que puedas tanto servir páginas web con Apache y PHP como gestionar bases de datos con MySQL mediante PHPMyAdmin o Adminer. Este proceso reforzará habilidades cruciales que utilizarás constantemente dentro de Terraformadores.

### Instrucciones:

1. **Servidor Web Apache**
   - Instala, configura y prueba el servidor Apache. Asegúrate de que funcione correctamente y captura la página de muestra de Apache desde tu navegador.
   - **Entrega:** Explicación de los pasos seguidos y captura de pantalla.

2. **MySQL**
   - Instala y configura MySQL. Desde la consola, crea una base de datos de prueba, inserta algunos registros en una tabla y realiza una consulta para comprobar la inserción.
   - **Entrega:** Explicación de los pasos y capturas del proceso.

3. **PHP**
   - Instala la última versión de PHP y prueba su funcionalidad creando una página web en Apache que muestre la información de PHP.
   - **Entrega:** Explicación, capturas del proceso, resultado y fichero PHP.
   - **Bola extra:** Bola extra! Basándote en la plantilla que adjuntamos al final del documento, realiza las modificaciones necesaria para establecer una conexión a tu base de datos, recuperar algun dato/s y mostrarlo en una página web que alojarás en tu servidor Apache. 
4. **Gestor web de base de datos (PHPMyAdmin o Adminer)**
   - Instala y configura PHPMyAdmin o/y Adminer para gestionar tu base de datos. Realiza consultas y modificaciones en la estructura y los datos.
   - **Entrega:** Explicación de los pasos seguidos con capturas.

5. **Analizar los logs de Apache**
   - Instala un analizador de logs como **GoAccess** para monitorizar el tráfico web de Apache en tiempo real.
   - **Entrega:** Explicación de los pasos seguidos y capturas del proceso.

Este ejercicio te permitirá no solo familiarizarte con una de las arquitecturas web más utilizadas, sino también con herramientas esenciales para la administración de servidores, reforzando así los conceptos básicos de infraestructura que serán clave en proyectos más grandes dentro de Terraformadores de Venus.



#### Plantilla PHP acceso a datos:
```php
<?php
// Datos de la base de datos
$usuario = "root";
$password = "";
$servidor = "localhost";
$basededatos = "alumnos";

// creación de la conexión a la base de datos
$conexion = mysqli_connect( $servidor, $usuario, "" ) or die ("No se ha podido conectar al servidor de Base de datos");

// Selección del a base de datos a utilizar
$db = mysqli_select_db( $conexion, $basededatos ) or die ("No se ha podido conectar a la base de datos" );
// consulta. guardamos en variable.
$consulta = "SELECT * FROM alumnos";
$resultado = mysqli_query( $conexion, $consulta ) or die ( "Algo ha ido mal en la consulta");

// Motrar el resultado de los registro de la base de datos
// Encabezado de la tabla
echo "<table borde='2'>";
echo "<tr>";
echo "<th>Nombre</th>";
echo "<th>Edad</th>";
echo "</tr>";

// Bucle while que recorre cada registro y muestra cada campo en la tabla.
while ($columna = mysqli_fetch_array( $resultado ))
{
    echo "<tr>";
    echo "<td>" . $columna['nombre'] . "</td><td>" . $columna['edad'] . "</td>";
    echo "</tr>";
}

echo "</table>"; // Fin de la tabla
// cerrar conexión de base de datos
mysqli_close( $conexion );

?>
```