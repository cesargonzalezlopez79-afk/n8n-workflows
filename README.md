# 🤖 Flujo de n8n: Agente de IA para WhatsApp (Texto y Voz)

Este repositorio contiene un flujo de trabajo avanzado para **n8n** que conecta WhatsApp con un Agente de Inteligencia Artificial de OpenAI. Es capaz de procesar mensajes de texto y transcribir mensajes de voz automáticamente utilizando Whisper.

## 🚀 Características
- **Validación de Horario**: Filtra mensajes automáticamente si entran fuera del horario de atención.
- **Soporte Multimedia**: Descarga y transcribe mensajes de voz mediante OpenAI Whisper.
- **Agente con Memoria**: Utiliza nodos de LangChain (`AI Agent`, `Chat Model` y `Simple Memory`) para mantener el hilo de la conversación.
- **Multicanal**: Funciona tanto para chats individuales como para grupos (configurable en el nodo `siesgrupo1`).

## 🛠️ Requisitos Previos
Para utilizar este flujo, necesitarás tener cuentas y credenciales en:
1. **n8n** (Instancia propia o Cloud).
2. **API de WhatsApp Business** (Token de acceso y ID de teléfono).
3. **OpenAI API Key** (Para el modelo de chat y la transcripción de audio).

## 📦 Instalación
1. Descarga el archivo `whatsapp-ai-agent-flow.json` de este repositorio.
2. Abre tu panel de n8n, crea un nuevo flujo de trabajo vacío.
3. En la esquina superior derecha, haz clic en el menú y selecciona **Import from File**.
4. Selecciona el archivo JSON descargado.
5. Configura tus credenciales en los nodos de **OpenAI** y en los nodos HTTP de **WhatsApp**.

## 📝 Notas de Configuración
- Asegúrate de rellenar las variables de entorno o credenciales internas de n8n para que las llamadas HTTP no fallen.
- El nodo de horario (`If`) debe ajustarse con la zona horaria local de tu país.
