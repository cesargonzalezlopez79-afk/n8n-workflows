# 🤖 Agente de Inteligencia Artificial Multimodal con n8n

Este repositorio contiene un flujo de trabajo avanzado de automatización desarrollado en **n8n**. El sistema actúa como un asistente virtual inteligente capaz de procesar múltiples formatos de entrada (texto, audio y enlaces), gestionar estados en bases de datos y ejecutar acciones en tiempo real mediante un **AI Agent** conectado a herramientas externas.

---

## 🚀 Arquitectura del Flujo de Trabajo

El workflow se divide en tres etapas principales estructuradas de forma lógica y modular:

### 1. Recepción y Clasificación de Datos (Ingest)
*   **Trigger (Evolution):** Escucha y recibe eventos webhooks entrantes de forma automatizada.
*   **Enrutamiento Inteligente (Switch):** Clasifica dinámicamente el tipo de mensaje entrante en tres canales de procesamiento:
    *   **Audio:** Descarga el archivo multimedia (`obtiene file1`), procesa el binario (`file1`) y realiza la transcripción de voz a texto utilizando el nodo de OpenAI (`extrae audio1`).
    *   **Texto:** Mapea directamente el mensaje para su posterior lectura.
    *   **Enlaces / Medios adicionales:** Canalizados mediante lógica personalizada.

### 2. Gestión de Persistencia y Lógica de Negocio
*   **Control de Estado (Google Sheets):** Consulta el historial del usuario (`Get many rows1`) y registra nuevas interacciones en una base de datos en la nube (`Create a row1`).
*   **Evaluación de Condiciones (If / Switch):** Lógica condicional avanzada para determinar si el usuario pertenece a un grupo específico (`siesgrupo`) y formatear las propiedades del mensaje antes de enviarlo al núcleo de IA.

### 3. Núcleo de Inteligencia Artificial (AI Agent)
El corazón del sistema es un **AI Agent** conversacional configurado con:
*   **Modelo de Lenguaje:** OpenAI Chat Model.
*   **Memoria:** Simple Memory para mantener el contexto de la conversación.
*   **Integración de Herramientas (Tools / Google Calendar):** El agente tiene la capacidad autónoma de decidir cuándo interactuar con calendarios mediante subflujos y nodos dedicados para:
    *   📅 Crear eventos
    *   ❌ Eliminar eventos
    *   🔄 Actualizar eventos
    *   🔍 Buscar múltiples eventos existentes
*   **Generación de Respuestas:** El flujo sintetiza una respuesta de texto o genera dinámicamente un archivo de voz (`Generate audio1` + `Code in JavaScript`) para responder al usuario final por canales de mensajería como WhatsApp.

---

## 🛠️ Tecnologías y Nodos Clave Utilizados

*   **n8n** (Orquestador principal y lógica de nodos)
*   **OpenAI API** (Procesamiento de Lenguaje Natural, Transcripción de Audio y Agente Autónomo)
*   **Google Sheets / Google Calendar** (Herramientas de productividad e infraestructura de datos)
*   **JavaScript** (Manipulación y transformación avanzada de datos binarios y JSON)
*   **Webhooks & HTTP Request** (Integración de APIs externas)

---

## 💻 Instrucciones de Instalación

Para replicar o probar este flujo de trabajo en tu propia instancia de n8n:

1.  Descarga el archivo `.json` de este repositorio.
2.  Abre tu panel de control de **n8n**.
3.  Crea un nuevo flujo de trabajo (Workflow).
4.  Haz clic en el menú de los tres puntos (esquina superior derecha) y selecciona **Import from File**.
5.  Selecciona el archivo `.json` descargado.
6.  Configura tus propias credenciales para los nodos de **OpenAI**, **Google Calendar** y **Google Sheets**.
