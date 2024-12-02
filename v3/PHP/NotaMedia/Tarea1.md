### UD3 - PROGRAMACIÓN LADO SERVIDOR - IAW - IES LA SENIA  

La programación de lado servidor es fundamental para el éxito de nuestras aplicaciones web. Este tipo de programación permite gestionar datos, personalizar experiencias de usuario y conectar con bases de datos, funciones esenciales en cualquier servicio moderno.

Hasta ahora, habéis explorado los conceptos básicos de PHP, aprendiendo a recibir y procesar información desde formularios HTML mediante peticiones GET/POST. Ahora es el momento de aplicar estos conocimientos en un caso práctico: desarrollar una solución funcional que combine validación de datos, cálculos y una presentación visual adecuada.

#### **Tarea 1: Gestión Automatizada de Rendimiento del Equipo de Terraformadores**  

En **Terraformadores de Venus**, gestionar datos es clave para optimizar el rendimiento del equipo. Imaginad que sois parte del departamento encargado de evaluar el desempeño de los terraformadores en sus misiones clave. Estas evaluaciones incluyen ejercicios prácticos de simulación y exámenes teóricos sobre protocolos de terraformación.  

Ahora es vuestro turno de diseñar una herramienta eficiente que permita registrar estas evaluaciones, calcular el rendimiento final y mostrar los resultados de manera clara y profesional. Esta herramienta formará parte de nuestro sistema de gestión interna, asegurando que se toman decisiones informadas basadas en datos.  

---

### **Descripción del Ejercicio**  

Como desarrolladores de **Terraformadores**, debéis crear un sistema en PHP que permita:  

1. **Registrar y procesar datos:**  
   - Usar 4 campos de datos para almacenar las calificaciones de **4 prácticas de simulación** ("Práctica1", "Práctica2", etc. puedes utilizar un array asociativo con esas claves).  
   - Usar 2 campos mas para las calificaciones de **2 exámenes teóricos** ("Examen1" y "Examen2", etc. puedes utilizar un array asociativo con esas claves).  

2. **Calcular el rendimiento final:**  
   - Las prácticas tendrán un peso del **40%** y los exámenes del **60%** en el rendimiento total.  
   - Calcular las medias correspondientes y combinarlas para obtener una evaluación final.  

3. **Recibir y validar los datos mediante un formulario web:**  
   - Crear un formulario HTML para registrar:  
     - Nombre del terraformador. (no acepta números ni símbolos, solo carácteres alfabéticos)
     - Correo corporativo (validar formato).  
     - Número de identificación interno (inventarse un formato adecuado y validarlo).  
     - Notas de prácticas y exámenes (validar que están entre 0 y 10).  

4. **Visualizar el rendimiento final:**  
   - Mostrar en la misma página o en una página de resultados:  
     - Datos del terraformador (nombre, correo y número de identificación).  
     - Detalles de las calificaciones introducidas.  
     - Media de prácticas y exámenes.  
     - Evaluación final calculada.  

5. **Diseño profesional y funcional:**  
   - Se pueden utilizar herramientas como **Bootstrap** o similares para diseñar una interfaz moderna.  
   - Organizar las secciones claramente, con un encabezado, área de introducción de datos y área de resultados (si es la misma página).  
   - Añadir elementos visuales como iconos o separadores para mejorar la experiencia de usuario. (opcional, recomendable)

6. **Validación exhaustiva:**  
   - Comprobar que todos los datos son válidos antes de procesarlos en el lado servidor (no incluir validaciones del lado cliente).  
   - Proporcionar mensajes de error claros y accesibles en caso de que falten datos o el formato no sea válido.  


---


### **Entregables:**  

1. **Código del sistema (HTML (si corresponde) y PHP):**  
   - Bien estructurado, con comentarios que expliquen su funcionamiento.  

 
---

Esta tarea os permitirá simular una herramienta de evaluación interna, imprescindible para optimizar procesos en cualquier organización. ¡Adelante, terraformadores! 🚀