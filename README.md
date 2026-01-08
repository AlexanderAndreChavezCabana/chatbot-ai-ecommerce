# 🤖 Taller Sesión 4: Chatbot con LangChain y Gestión de Contexto

**Curso:** Diseño e Implementación de Chatbots
**Docente:** Angelo Castillo Meca

---

## 📋 Descripción

Este taller te enseña a implementar un asistente conversacional para e-commerce usando LangChain, con gestión de memoria conversacional y orquestación de LLMs.

## 🎯 Objetivos de Aprendizaje

- Usar LangChain para orquestar interacciones con LLMs
- Implementar gestión de memoria conversacional
- Diseñar prompts efectivos para chatbots especializados
- Crear cadenas de procesamiento (Chains)
- Construir un chatbot con contexto persistente

## 📦 Requisitos

### API Key de OpenAI

**⚠️ IMPORTANTE:** Este taller requiere una API key de OpenAI.

1. Crea una cuenta en [OpenAI](https://platform.openai.com/)
2. Ve a [API Keys](https://platform.openai.com/api-keys)
3. Crea una nueva API key
4. **Nota:** Nuevas cuentas tienen $5 de crédito gratis

**Alternativa Gratuita:** El notebook incluye una sección para usar modelos locales de HuggingFace (sin costo)

### Python y Dependencias

```bash
pip install langchain langchain-community langchain-openai openai python-dotenv
```

### Versiones Recomendadas

- Python 3.8 o superior
- langchain >= 0.1.0
- openai >= 1.0.0

## 🚀 Cómo Usar el Taller

### Opción 1: Google Colab (Recomendado)

1. Abre el notebook en Google Colab:
   - Ve a [Google Colab](https://colab.research.google.com/)
   - Selecciona "Archivo" → "Abrir cuaderno"
   - Sube el archivo `Taller_Sesion4_LangChain_Chatbot.ipynb`

2. **Configura tu API Key:**
   ```python
   # El notebook te pedirá la API key de forma segura
   # NO la compartas ni la subas a repositorios públicos
   ```

3. Ejecuta las celdas en orden

### Opción 2: Jupyter Notebook Local

1. Instala Jupyter:
   ```bash
   pip install jupyter
   ```

2. **Configura tu API Key (Opción A - Variable de entorno):**
   ```bash
   # Linux/Mac
   export OPENAI_API_KEY='tu-api-key-aquí'

   # Windows (CMD)
   set OPENAI_API_KEY=tu-api-key-aquí

   # Windows (PowerShell)
   $env:OPENAI_API_KEY='tu-api-key-aquí'
   ```

3. **Configura tu API Key (Opción B - Archivo .env):**
   ```bash
   # Crea archivo .env en la misma carpeta del notebook
   echo "OPENAI_API_KEY=tu-api-key-aquí" > .env
   ```

4. Inicia Jupyter:
   ```bash
   jupyter notebook
   ```

5. Abre el archivo `Taller_Sesion4_LangChain_Chatbot.ipynb`

### Opción 3: VS Code

1. Instala extensiones: "Jupyter" y "Python"
2. Abre el archivo `.ipynb`
3. Configura la API key (mismo proceso que Jupyter Local)
4. Ejecuta las celdas

## 📚 Contenido del Taller

### Parte 1-3: Setup Inicial
- Instalación de dependencias
- Configuración de API key
- Importar bibliotecas

### Parte 4: Inicializar LLM
- Configuración de ChatOpenAI
- Parámetros: temperature, max_tokens

### Parte 5: Memoria Conversacional
- ConversationBufferMemory (completo)
- ConversationBufferWindowMemory (ventana)
- ConversationSummaryMemory (resumen)

### Parte 6: Prompt Engineering
- Diseño de prompt template
- Contexto de e-commerce
- Catálogo de productos
- Políticas de la tienda

### Parte 7: ConversationChain
- Integración LLM + Memoria + Prompt
- Cadena de procesamiento completa

### Parte 8-10: Chatbot Funcional
- Clase `ChatbotEcommerce`
- Métodos: chat, reset, ver_historial
- Conversación de ejemplo
- Estadísticas

### Parte 11: Tipos de Memoria
- Comparación de estrategias
- Pruebas con ventana limitada

### Parte 12: Chat Interactivo
- Loop en consola
- Comandos especiales

### Parte 13: Ejercicios Propuestos
- Sistema de descuentos
- Filtrado inteligente
- Integración con DB
- Sentiment analysis

### Alternativa: Modelos Locales
- Uso de HuggingFace sin API key
- Configuración alternativa

## 🔑 Gestión Segura de API Keys

### ✅ Hacer:
- Usar variables de entorno
- Usar archivos `.env` (y agregarlos a `.gitignore`)
- Usar servicios de secrets management en producción
- Rotar keys periódicamente

### ❌ NO Hacer:
- Hardcodear la API key en el código
- Subir la API key a GitHub/GitLab
- Compartir la API key en capturas de pantalla
- Usar la misma key en múltiples proyectos

### Ejemplo Seguro:

```python
import os
from dotenv import load_dotenv

# Cargar desde archivo .env
load_dotenv()
api_key = os.getenv("OPENAI_API_KEY")

# O solicitar al usuario (como en el notebook)
import getpass
api_key = getpass.getpass("Ingresa tu API Key: ")
```

## ⚙️ Configuración del LLM

### Modelos Disponibles (OpenAI)

1. **gpt-3.5-turbo** (Usado en el taller)
   - Costo: $0.0005 / 1K tokens (input)
   - Velocidad: Rápida
   - Calidad: Alta
   - Recomendado para: Producción

2. **gpt-4**
   - Costo: $0.03 / 1K tokens (input)
   - Velocidad: Media
   - Calidad: Muy alta
   - Recomendado para: Tareas complejas

3. **gpt-4-turbo**
   - Costo: $0.01 / 1K tokens (input)
   - Velocidad: Rápida
   - Calidad: Muy alta
   - Recomendado para: Balance costo/calidad

### Parámetros del LLM

```python
llm = ChatOpenAI(
    model="gpt-3.5-turbo",
    temperature=0.7,      # Creatividad (0.0-2.0)
    max_tokens=500,       # Longitud de respuesta
    model_kwargs={
        "top_p": 0.9,     # Nucleus sampling
        "frequency_penalty": 0.0,
        "presence_penalty": 0.0
    }
)
```

### Temperature:
- **0.0-0.3:** Determinístico, preciso (FAQs, soporte)
- **0.7-0.9:** Balanceado (conversación general)
- **1.0-2.0:** Creativo (brainstorming, storytelling)

## 💾 Tipos de Memoria en LangChain

### 1. ConversationBufferMemory
- **Uso:** Almacena todo el historial
- **Ventaja:** Contexto completo
- **Desventaja:** Puede exceder límite de tokens
- **Recomendado para:** Conversaciones cortas/medias

### 2. ConversationBufferWindowMemory
- **Uso:** Solo últimas K interacciones
- **Ventaja:** Control de tamaño
- **Desventaja:** Pierde contexto antiguo
- **Recomendado para:** Conversaciones largas

```python
memory = ConversationBufferWindowMemory(k=5)  # Últimas 5 interacciones
```

### 3. ConversationSummaryMemory
- **Uso:** Resume automáticamente el historial
- **Ventaja:** Mantiene esencia con menos tokens
- **Desventaja:** Costo adicional (resumen usa LLM)
- **Recomendado para:** Conversaciones muy largas

```python
memory = ConversationSummaryMemory(llm=llm)
```

## 💡 Tips y Mejores Prácticas

### Prompt Engineering

1. **Define el rol claramente:**
   ```
   "Eres un asistente virtual experto en [dominio]"
   ```

2. **Proporciona contexto:**
   - Catálogo de productos
   - Políticas de la empresa
   - Limitaciones del asistente

3. **Especifica el formato:**
   - Tono (formal/informal)
   - Longitud de respuestas
   - Estructura (bullets, párrafos)

4. **Incluye instrucciones de seguridad:**
   - "Si no tienes información, admítelo"
   - "No inventes datos"
   - "Cita las fuentes cuando sea relevante"

### Optimización de Costos

1. **Usa el modelo apropiado:**
   - gpt-3.5-turbo para la mayoría de casos
   - gpt-4 solo cuando sea necesario

2. **Limita el contexto:**
   - Usa ConversationBufferWindowMemory
   - No envíes información redundante

3. **Cachea respuestas frecuentes:**
   - FAQ común → respuesta pre-generada
   - Solo usa LLM para consultas únicas

4. **Monitorea el uso:**
   ```python
   # Ver cuántos tokens consume
   from langchain.callbacks import get_openai_callback

   with get_openai_callback() as cb:
       response = conversation.predict(input=mensaje)
       print(f"Tokens: {cb.total_tokens}, Costo: ${cb.total_cost}")
   ```

## 🐛 Troubleshooting

### Error: "Invalid API Key"
**Solución:**
- Verifica que la API key sea correcta
- Revisa que no tenga espacios al inicio/final
- Confirma que la cuenta tenga crédito disponible

### Error: "Rate limit exceeded"
**Solución:**
- Has excedido el límite de requests por minuto
- Espera 60 segundos
- Considera upgrade de cuenta

### Error: "Context length exceeded"
**Solución:**
- Reduce `max_tokens`
- Usa ConversationBufferWindowMemory con k más pequeño
- Limpia la memoria: `conversation.memory.clear()`

### Respuestas en inglés
**Solución:**
- Agrega al prompt: "IMPORTANTE: Responde SIEMPRE en español"
- Verifica que los ejemplos en el prompt estén en español

## 💰 Estimación de Costos

### Ejemplo de Conversación:

- **Modelo:** gpt-3.5-turbo
- **Conversación:** 10 turnos
- **Promedio por turno:** 500 tokens (input + output)
- **Total:** ~5,000 tokens
- **Costo:** ~$0.0025 (menos de 1 centavo)

### Costo por 1000 conversaciones:
- **gpt-3.5-turbo:** ~$2.50
- **gpt-4:** ~$150

**Conclusión:** Para producción, gpt-3.5-turbo es muy económico.

## 📊 Tiempo Estimado

- Setup inicial (incluye API key): 15-20 minutos
- Completar taller: 75-90 minutos
- Ejercicios adicionales: 45-60 minutos

## 🎓 Ejercicios Propuestos

### Ejercicio 1: Sistema de Descuentos (30 min)
Implementa lógica para aplicar descuentos automáticos

### Ejercicio 2: Filtrado Inteligente (20 min)
Filtra productos por rango de precios y características

### Ejercicio 3: Integración con SQLite (45 min)
Conecta a una base de datos real para productos dinámicos

### Ejercicio 4: Sentiment Analysis (30 min)
Detecta clientes insatisfechos y escala a humano

### Ejercicio 5: Multi-idioma (25 min)
Agrega soporte para inglés/español automático

## 📚 Recursos Adicionales

- [LangChain Documentation](https://python.langchain.com/docs/get_started/introduction)
- [OpenAI API Reference](https://platform.openai.com/docs/api-reference)
- [LangChain Memory Guide](https://python.langchain.com/docs/modules/memory/)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)

## 🆓 Alternativa Sin Costo

El notebook incluye código (comentado) para usar modelos locales de HuggingFace:

```python
# Usar google/flan-t5-base local (sin API key)
from langchain_huggingface import HuggingFacePipeline

llm_local = HuggingFacePipeline.from_model_id(
    model_id="google/flan-t5-base",
    task="text2text-generation"
)
```

**Ventajas:**
- Sin costo
- Sin límites de uso
- Privacidad total

**Desventajas:**
- Menor calidad que GPT-3.5/4
- Requiere más memoria RAM
- Más lento

## 🆘 Soporte

Si tienes problemas:
1. Revisa la sección de Troubleshooting
2. Consulta la documentación de LangChain
3. Contacta al docente: castillomeca53@gmail.com

---

**¡Éxito en tu taller!** 🚀
