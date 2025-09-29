# 📘 Dossier de Ejercicios de Repaso – Introducción a la Programación (Python)

**Módulo: Introducción a la Programación – Mentor: Dr. Strange (Terraformadores de Venus)**

---

## 🔹 Ejercicio 0.1: 🔐 Control de acceso a NimbusNet

En la nube **NimbusNet**, el sistema de autenticación protege los recursos más valiosos de Terraformadores. Los aprendices deben demostrar que saben gestionar **condicionales y bucles** para validar la seguridad.

* El programa pedirá al usuario su **usuario** y **contraseña**.
* Si coinciden con unas credenciales predefinidas (por ejemplo, usuario `"admin"`, contraseña `"1234"`), mostrará **“Acceso concedido”**.
* Si falla **3 veces**, el sistema mostrará **“Acceso denegado. Contacta con seguridad (Prof. Xavier)”** y finalizará.

---

## 🔹 Ejercicio 0.2: 📦 Control de suministros en la base

Los Terraformadores reciben un cargamento de cajas con repuestos tecnológicos. No todas cumplen los estándares, así que hay que validarlas.

* Pregunta al usuario el **número total de cajas**.
* Con un **bucle**, pregunta para cada caja si está en **buen estado** (`sí/no`).
* Al final muestra:

  * Número total de cajas buenas.
  * Número total de cajas defectuosas.
  * Mensaje:

    * **“Todo correcto, almacén operativo”** si más del 80% están bien.
    * **“Atención: revisar inventario”** en caso contrario.


---

## 🔹 Ejercicio 1: 📊 La evaluación de aprendices

Los aprendices de programación deben demostrar su progreso. Dr. Strange quiere un sistema que almacene las notas de las asignaturas mágicas y ofrezca un informe completo.

* Guardar en un **diccionario** el nombre de cada asignatura como clave y la nota como valor.
* Calcular y mostrar:

  * Media final.
  * Nota más alta y más baja.
  * Mensaje de aprobado o suspenso según la media.
* Mostrar un **informe ordenado y claro** con todos los resultados.

---

## 🔹 Ejercicio 2: 🛒 El mercado intergaláctico de Paiporta

Los Terraformadores van a comprar suministros en el **mercado intergaláctico de Paiporta**. Debemos programar un pequeño sistema que permita simular las compras de un cliente.

S
1. Crea un **diccionario** con algunos productos y sus precios.

   ```python
   productos = {
       "cristal_kyber": 50,
       "comunicador": 20,
       "sable_luz": 150,
       "traje_espacial": 200
   }
   ```
2. El usuario podrá **realizar una compra** escribiendo el nombre del producto y la cantidad.
4. El programa debe calcular y mostrar:

   *  El subtotal de la compra (precio del producto x cantidad).
   *  El total de la compra con IVA (21%).
   *  Se debe el producto existe y validar que las cantidades sean **mayores que cero**.

### ✨ Extra

   * Permitir repetir compras hasta que se escriba `"fin"` .
   * El total se mostrará al final, con el total de cada producto y el total con IVA de la suma de todos los productos
   *  Se debe mostrar el producto más caro que se haya comprado.


---

### 📌 Ejemplo de ejecución sin extra

```
=== Bienvenido al mercado intergaláctico de Paiporta ===
Productos disponibles:
- cristal_kyber: 50 créditos
- comunicador: 20 créditos
- sable_luz: 150 créditos
- traje_espacial: 200 créditos

¿Qué producto deseas comprar?: comunicador
¿Cuántas unidades?: 2

--- Factura de compra ---
comunicador (2 x 20) = 40 créditos
Total con IVA (21%): 48.4 créditos
```

---

### 📌 Ejemplo de ejecución con extra

```
=== Bienvenido al mercado intergaláctico de Paiporta ===
Productos disponibles:
- cristal_kyber: 50 créditos
- comunicador: 20 créditos
- sable_luz: 150 créditos
- traje_espacial: 200 créditos

¿Qué producto deseas comprar? (escribe 'fin' para terminar): comunicador
¿Cuántas unidades?: 2

¿Qué producto deseas comprar? (escribe 'fin' para terminar): sable_luz
¿Cuántas unidades?: 1

¿Qué producto deseas comprar? (escribe 'fin' para terminar): fin

--- Factura de compra ---
comunicador = 40 créditos
sable_luz = 150 créditos
------------------------------
Total sin IVA: 190 créditos
Total con IVA (21%): 229.9 créditos
Producto más caro comprado: sable_luz
```



---

## 🔹 Ejercicio 3: 📇 La agenda secreta de contactos

Los Terraformadores mantienen una red de aliados repartidos por toda la galaxia. Para no perder el control, los aprendices deben construir una agenda digital que permita:

1. Añadir un contacto con nombre, teléfono y correo.
2. Buscar un contacto por nombre.
3. Listar todos los contactos.
4. Eliminar un contacto.
5. Salir del programa.


---

## 🔹 Ejercicio 4: 🎲 El número secreto de Strange

Dr. Strange reta a los aprendices a un duelo de adivinación. Ha pensado un número secreto (del 1 al 100) y deben adivinarlo.

* El programa genera un número aleatorio.
* El usuario debe introducir números e irá recibiendo pistas:

  * “El número es mayor” o “El número es menor”.
* Se permiten un máximo de **10 intentos**.
* Al finalizar, el programa indica si el aprendiz ha ganado o perdido.


---

## 🔹 Ejercicio 5: 🖥️ Inventario de servidores en NimbusNet

En los servidores de NimbusNet es crucial saber cuántos recursos están operativos. Los aprendices deben crear un programa que gestione el inventario.

* Representa los servidores con una **lista de diccionarios**, cada uno con:

  * `nombre`
  * `CPU`
  * `RAM`
  * `estado` ("activo" o "apagado").
* Funciones:

  * Añadir servidores.
  * Listar servidores.
  * Buscar servidor por nombre.
  * Mostrar cuántos están activos y cuántos apagados.

### ✨ Extra:

* Mostrar mensajes especiales según el porcentaje de activos:

  * Más del 70% activos → “Infraestructura estable”.
  * 70% o menos → “Atención: revisar servidores”.


### 📌 Ejemplo de ejecución

```
  === Sistema de Inventario de NimbusNet ===
1. Añadir servidor
2. Listar servidores
3. Buscar servidor
4. Contar activos/apagados
5. Salir
Elige una opción: 1

Nombre del servidor: Alfa
CPU (núcleos): 8
RAM (GB): 16
Estado (activo/apagado): activo
Servidor añadido correctamente

-----------------------------------------
1. Añadir servidor
2. Listar servidores
3. Buscar servidor
4. Contar activos/apagados
5. Salir
Elige una opción: 1

Nombre del servidor: Beta
CPU (núcleos): 4
RAM (GB): 8
Estado (activo/apagado): apagado
Servidor añadido correctamente

-----------------------------------------
1. Añadir servidor
2. Listar servidores
3. Buscar servidor
4. Contar activos/apagados
5. Salir
Elige una opción: 2

--- Inventario de Servidores ---
Nombre: Alfa | CPU: 8 | RAM: 16 GB | Estado: activo
Nombre: Beta | CPU: 4 | RAM: 8 GB | Estado: apagado
-----------------------------------------

Elige una opción: 3
Introduce el nombre del servidor a buscar: Alfa
Servidor encontrado
Nombre: Alfa | CPU: 8 | RAM: 16 GB | Estado: activo

-----------------------------------------
Elige una opción: 4
Servidores activos: 1
Servidores apagados: 1

>>> Estado general de la infraestructura: Atención: revisar servidores
-----------------------------------------

Elige una opción: 5
Saliendo del sistema...
```

