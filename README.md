🚀 Workflow: Automatización de Notificaciones para "La Soberana"
Este flujo automatiza el envío de mensajes de bienvenida personalizados a través de WhatsApp cada vez que un nuevo emprendedor se registra en la feria mediante un formulario de Google.

<img width="612" height="236" alt="image" src="https://github.com/user-attachments/assets/967c52c7-dbf0-4c98-8167-475a7633cf50" />


📋 Componentes del Workflow
El diseño consta de tres nodos principales interconectados:

Google Sheets Trigger (rowAdded):

Función: Escucha en tiempo real la hoja de cálculo de inscripciones.

Activación: Se dispara automáticamente cada vez que se añade una nueva fila (un nuevo feriante registrado).

Edit Fields (Manual):

Función: Actúa como un paso de transformación de datos.

Proceso: Toma los datos crudos (nombre, teléfono, etc.) y los prepara para el siguiente nodo. Aquí es donde se asegura que el número de teléfono tenga el formato correcto para WhatsApp (ej. agregando el código de país).

HTTP Request (POST):

Función: El "motor" de envío que se comunica con la API de WAHA (WhatsApp HTTP API).

Configuración Técnica:

URL: http://host.docker.internal:3000/api/sendText (conexión interna entre contenedores Docker).

Autenticación: Uso de X-Api-Key en los Headers para seguridad.

Cuerpo (JSON): Envía un objeto dinámico que incluye el chatId del destinatario y un mensaje personalizado con emojis y enlaces a canales oficiales.

🛠️ Especificaciones Técnicas (Stack)
Orquestador: n8n (Self-hosted en Docker).

Motor de Mensajería: WAHA (WhatsApp HTTP API).

Base de Datos de Entrada: Google Sheets API.

Formato de Datos: JSON dinámico con expresiones de n8n.

✅ Logros del Proyecto
Eliminación de tareas manuales: El organizador ya no tiene que agendar y escribir manualmente a cada feriante.

Comunicación Inmediata: Los emprendedores reciben la información de los canales oficiales en el segundo exacto de su inscripción.

Escalabilidad: El sistema puede procesar cientos de registros sin intervención humana.

