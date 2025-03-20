## **IA en la sénia**

### 🔴 **Tenemos un problema**  
El instituto decide utilizar una plataforma de IA basada en la nube (Deepseek, chatgpt, etc..), por ejemplo, para analizar el rendimiento académico de los alumnos y ofrecer recomendaciones personalizadas. Para ello, sube a esta plataforma datos sensibles de los estudiantes, como:

- **Expedientes académicos** (calificaciones, asistencia, informes de conducta).  
- **Datos personales** (nombre, DNI, dirección, etc.).  
- **Información de necesidades educativas especiales**.  

Si esta plataforma pertenece a una empresa con servidores ubicados fuera de la Unión Europea **y no cuenta con las garantías adecuadas de protección de datos exigidas por el RGPD**, se estarían violando varias disposiciones de la **LOPDGDD**, como:

1. **Transferencia internacional de datos sin base legal**  
   - El instituto estaría enviando datos de alumnos a un país que no garantiza el mismo nivel de protección que la UE sin contar con cláusulas contractuales adecuadas o la autorización expresa de los afectados.

2. **Falta de consentimiento o base legal adecuada**  
   - Si los datos se suben sin haber informado correctamente a los alumnos y a sus familias, ni haber obtenido su consentimiento expreso, se incumpliría el principio de **transparencia y licitud** del tratamiento.

3. **Pérdida de control sobre los datos**  
   - Al depender de una plataforma externa, el instituto podría perder el control sobre cómo se procesan y almacenan los datos, corriendo el riesgo de que sean utilizados con fines comerciales o sin autorización.

### ✅ **Solución correcta**  
Para cumplir con la normativa, el IES La Sénia debería optar por una **IA local**, alojada en sus propios servidores o en una infraestructura que garantice que los datos no salen del Espacio Económico Europeo (EEE). Además, debería informar claramente a los alumnos y familias sobre el uso de la IA, asegurando que el tratamiento de los datos se realice conforme a la legislación vigente.

Para que el **IES La Sénia** cumpla con la **LOPDGDD** y el **RGPD** al utilizar una **IA para procesar datos de alumnos**, debe seguir estos pasos:  

---

## ✅ **Solución correcta para cumplir la LOPDGDD y el RGPD**  

### 🔹 **1. Definir la base legal para el tratamiento de datos**  
Antes de implementar la IA, el instituto debe justificar en qué base legal se apoya el tratamiento de datos personales. Según el **RGPD**, las bases legales pueden ser:  
- **Cumplimiento de una obligación legal** (artículo 6.1.c RGPD) → Si la IA se usa para evaluar el aprendizaje, el instituto puede justificar que es necesario para su función educativa.  
- **Interés legítimo** (artículo 6.1.f RGPD) → Si la IA mejora la enseñanza, pero sin afectar negativamente a los alumnos.  
- **Consentimiento informado** (artículo 6.1.a RGPD) → Si el tratamiento no está cubierto por las otras bases, se debe obtener el consentimiento explícito de los alumnos o sus tutores legales.  

💡 **Recomendación**: Usar preferiblemente **obligación legal** o **interés legítimo**, pero si no es posible, recabar consentimiento informado.  

---

### 🔹 **2. Minimización y anonimización de datos**  
El instituto debe aplicar el **principio de minimización**:  
✅ **Solo recoger los datos estrictamente necesarios** → No almacenar información personal innecesaria.  
✅ **Anonimizar o pseudonimizar** los datos cuando sea posible → En vez de usar nombres, usar identificadores anónimos.  
✅ **Eliminar datos cuando ya no sean necesarios** → Establecer un período de retención y proceder a su eliminación segura.  

Ejemplo:  
🚫 **Incorrecto** → Guardar todos los datos del alumno (nombre, DNI, dirección, notas, etc.).  
✅ **Correcto** → Guardar solo un identificador cifrado y los datos de rendimiento necesarios para la IA.  

---

### 🔹 **3. Implementar una infraestructura segura (IA local en servidores propios o europeos)**  
Para evitar la transferencia de datos a terceros no autorizados, el instituto debe:  
✅ Usar **servidores locales** dentro del instituto o en una infraestructura segura dentro de la UE.  
✅ Si se usa la nube, elegir un proveedor con **servidores en la UE** que cumpla con el **RGPD**.  
✅ Asegurar que los datos no sean accesibles fuera del entorno educativo autorizado.  

Ejemplo:  
🚫 **Incorrecto** → Subir los datos a una IA en una nube pública (Amazon, Google, OpenAI) sin contrato adecuado.  
✅ **Correcto** → Usar un servidor privado en el instituto con acceso controlado o un proveedor con garantía de cumplimiento del RGPD.  

---

### 🔹 **4. Informar a los alumnos y tutores**  
El instituto debe ser **transparente** y cumplir con el derecho a la información de los alumnos y sus familias:  
✅ Redactar una **Política de Privacidad** clara y accesible.  
✅ Indicar:  
   - Qué datos se recopilan.  
   - Para qué se usan.  
   - Quién tiene acceso a ellos.  
   - Cuánto tiempo se almacenarán.  
   - Cómo pueden ejercer sus derechos.  

📌 **Ejemplo de aviso en la web del instituto**:  
*"Este centro educativo utiliza Inteligencia Artificial para mejorar la enseñanza. Los datos de los alumnos serán tratados de forma segura y no se compartirán con terceros sin autorización. Para más información, consulte nuestra Política de Privacidad."*  

---

### 🔹 **5. Garantizar la seguridad y acceso restringido**  
Para proteger la información de los alumnos, el instituto debe aplicar:  
✅ **Control de acceso** → Solo personal autorizado puede acceder a los datos.  
✅ **Cifrado de datos** → Para evitar que terceros puedan leer la información en caso de brecha de seguridad.  
✅ **Registros de actividad** → Para saber quién accede a los datos y cuándo.  
✅ **Evaluación de Impacto** (**EIPD**) → Si los datos tratados son especialmente sensibles, se debe hacer un análisis de riesgos.  

Ejemplo:  
🚫 **Incorrecto** → Dejar los datos de la IA accesibles desde cualquier ordenador del instituto.  
✅ **Correcto** → Acceso solo desde dispositivos autorizados con autenticación segura.  

---

### 🔹 **6. Firmar acuerdos de confidencialidad y contratos con proveedores**  
Si la IA usa servicios de terceros, el instituto debe firmar contratos de tratamiento de datos con:  
✅ Empresas de tecnología (si proveen soporte o infraestructura).  
✅ Profesores y personal con acceso a los datos, asegurando que mantendrán la confidencialidad.  

Ejemplo:  
🚫 **Incorrecto** → Usar una plataforma de IA sin contrato específico sobre protección de datos.  
✅ **Correcto** → Firmar un acuerdo con la empresa proveedora donde se especifique el cumplimiento del RGPD.  

---

### 🔹 **7. Permitir el ejercicio de derechos de los alumnos**  
Los alumnos (o sus tutores) tienen derecho a:  
✅ **Acceder** a sus datos.  
✅ **Rectificar** datos incorrectos.  
✅ **Solicitar su eliminación** cuando ya no sean necesarios.  
✅ **Oponerse al tratamiento** en ciertos casos.  

💡 **Recomendación**: Crear un formulario o correo específico para atender estas solicitudes (ejemplo: privacidad@ieslasenia.edu).  

---
