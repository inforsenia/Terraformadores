# 🧠 Boletín de Ejercicios – Programación Modular

### *Dr. Strange y el poder del código modular*

En Terraformadores de Venus, el caos no tiene cabida en el desarrollo de software. Bajo la guía de **Dr. Strange**, los aprendices aprenden a controlar la complejidad del código utilizando **funciones**, el verdadero arte de la modularidad.

Estas prácticas te ayudarán a **dividir problemas en partes más pequeñas y reutilizables**, a comprender el **paso de parámetros**, el **valor de retorno** y la **organización lógica del código**.

Recuerda: en el universo de la programación, dominar las funciones es como dominar los portales dimensionales del código — el camino más directo hacia un desarrollo claro, eficiente y elegante.

---

### 🧩 Ejercicio 1: Analizador de Texto Místico

Crea un programa que analice un texto introducido por el usuario y obtenga la siguiente información:

1. Número total de caracteres.
2. Número de palabras.
3. Palabra más larga y más corta.
4. Número de veces que aparece una letra concreta (pasada como parámetro opcional).

**Indicaciones:**

Crea una función `analizar_texto` que reciba dos parámetros: 
  * el texto a analizar
  * (opcional) una letra, si no se pasa de forma explícita debe tomar el valor 'a'

Ademas la funcion debe devolver **cuatro valores**:

  * Total de caracteres
  * Total de palabras
  * Palabra más larga
  * Veces que aparece la letra indicada (por defecto “a”).

En el programa principal, pide el texto al usuario y muestra los resultados de forma clara.

---

### 🔢 Ejercicio 2: Calculadora Modular Interactiva

Implementa una calculadora que pueda realizar operaciones sobre dos o más números.

1. Define una función `operar` que reciba:

- `operacion`: el tipo de operación a realizar (“suma”, “media”, “mayor”, “menor”).

- los dos primeros números (operandos) obligatorios.

- valores adicionales, resto de números (puede ser uno, muchos o incluso ninguno) opcionales.

2. La función debe devolver el resultado de la operación correspondiente:

- `"suma"` → suma de todos los números.

- `"media"` → media aritmética de todos los números.

- `"mayor"` → número más alto.

- `"menor"` → número más bajo.

3. En el programa principal:

- Solicita la operación.

- Pide al menos dos números, y luego pregunta si desea introducir más.

- Llama a la función y muestra el resultado.

**Ejemplo de uso:**

```bash
Introduce operación: suma
Introduce primer número: 4
Introduce segundo número: 8
¿Quieres añadir más números? (s/n): s
Introduce número: 2
¿Quieres añadir más números? (s/n): n

Resultado: 14

```

---

### 🌡 Ejercicio 3: Registro de Temperaturas Planetarias

Dr. Strange ha registrado las temperaturas diarias de varios planetas y necesita procesarlas.

**Objetivo:**
Diseñar un programa modular que calcule y muestre la temperatura media diaria y la media total de un planeta.

#### Paso 1 – Función para calcular media diaria

Crea una función `calcular_media` que:

* Reciba **dos parámetros numéricos**: temperatura máxima y mínima.
* Devuelva la media aritmética de ambos valores.

#### Paso 2 – Función para procesar varios días

Crea otra función `registro_temperaturas` que:

* Reciba:

  * El nombre del planeta (cadena).
  * Un número variable de **tuplas** con las temperaturas (máxima, mínima) de cada día.
* Use la función anterior para calcular la media de cada día.
* Devuelva **una lista de medias diarias**.

#### Paso 3 – Programa principal

* Pide al usuario el nombre del planeta.
* Pide las temperaturas máximas y mínimas de 3 días.
* Muestra las medias de cada día y la media total.

**Ejemplo de ejecución:**

```
Planeta: Marte
Introduce temperatura máxima y mínima del día 1: 18 10
Introduce temperatura máxima y mínima del día 2: 16 9
Introduce temperatura máxima y mínima del día 3: 15 6

Resultados:
Día 1 → Media: 14.0 ºC
Día 2 → Media: 12.5 ºC
Día 3 → Media: 10.5 ºC
Temperatura media total: 12.3 ºC
```

---

### ⚗️ Ejercicio 4: Simulador de Conjuros Aleatorios

El Doctor Strange necesita calcular su **poder total** en una batalla.
Su poder se obtiene a partir de un **poder base**, un **multiplicador**, y una serie de **factores mágicos adicionales** que pueden sumarse al resultado.

Crea una función llamada `calcular_poder(base, multiplicador, *factores)` que devuelva el resultado final.

El programa principal:

1. Pedirá al usuario el poder base.
2. Luego preguntará por el multiplicador, si no se indica nada, se le asginará el valor 1, pero el parámetro ha de tener un valor.
3. A continuación, permitirá introducir factores adicionales hasta escribir `"fin"`.
4. Finalmente, mostrará el poder total calculado **tal y como se ve** en el siguiente ejemplo de ejecución.

### Ejemplo de ejecución

```
Introduce el poder base: 50
Introduce el multiplicador (Enter para 1): 2
Introduce factor adicional (fin para terminar): 10
Introduce factor adicional (fin para terminar): 5
Introduce factor adicional (fin para terminar): fin
El poder total es: 50 * 2 + (10 + 5) = 115
```