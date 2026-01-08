# 🤖 Taller Sesión 4: Chatbot LangChain para E-commerce

**Estudiante:** Sistema Completo de Chatbot Inteligente  
**Módulo:** Sesión 4 - LangChain & IA Conversacional

---

## 📋 Contenido

**Chatbot inteligente para e-commerce con LangChain** que incluye:
- Gestión de memoria conversacional (5 tipos)
- Catálogo de 20+ productos
- Sistema de descuentos automáticos
- Filtrado y búsqueda avanzada
- Base de datos SQLite
- Análisis de sentimiento
- Escalación a soporte humano

## 🔧 Requisitos

```bash
pip install -r requirements.txt
```

**Dependencias principales:**
- LangChain 0.1.0+
- OpenAI API (o Alibaba DashScope)
- SQLite3
- Python 3.8+

---

## 🚀 Inicio Rápido

### 1. Configurar API Key

```bash
# Windows PowerShell
$env:DASHSCOPE_API_KEY='tu-api-key'

# Linux/Mac
export DASHSCOPE_API_KEY='tu-api-key'

# O crear archivo .env
echo "DASHSCOPE_API_KEY=tu-api-key" > .env
```

### 2. Ejecutar Notebook

```bash
jupyter notebook Taller_Sesion4_LangChain_Chatbot.ipynb
```

---

## � Archivos Generados

```
techstore.db              # Base de datos SQLite con pedidos y clientes
pedidos_techstore.json    # Backup de pedidos en JSON
notificaciones_ventas.json # Log de notificaciones
```

---

## 🎬 Comenzar Ahora

```bash
# Clonar repositorio
git clone <url>
cd Taller

# Instalar dependencias
pip install -r requirements.txt

# Ejecutar notebook
jupyter notebook Taller_Sesion4_LangChain_Chatbot.ipynb
```

---

## 📞 Contacto

**Docente:** Angelo Castillo Meca  
**Email:** castillomeca53@gmail.com

---

**¡Bienvenido al Taller de Chatbots! 🚀**

| Sección | Contenido |
|---------|----------|
| **Parte 1-3** | Instalación, configuración e importes |
| **Parte 4-7** | Inicialización de LLM y memoria |
| **Parte 8-11** | Tipos de memoria conversacional (5 tipos) |
| **Parte 12-13** | JSON estructurado y chatbot interactivo |
| **Ejercicio 1** | ✅ Catálogo expandido (20 productos) |
| **Ejercicio 2** | ✅ Sistema de descuentos inteligente |
| **Ejercicio 3** | ✅ Filtrado y búsqueda avanzada |
| **Ejercicio 4** | ✅ Base de datos SQLite |
| **Ejercicio 5** | ✅ Análisis de sentimiento + Escalación |

---

## 💡 Características Principales

### 📦 Gestión de Catálogo
```python
CATALOGO_EXPANDIDO  # 20 productos en 7 categorías
FiltroProductos()   # Búsqueda por precio, categoría, keywords
```

### 💳 Descuentos Automáticos
```python
GestorDescuentos()  # Descuentos por monto, cantidad, combos, VIP
```

### 🗄️ Persistencia de Datos
```python
GestorBDTechStore()  # SQLite con 5 tablas (productos, clientes, pedidos, etc.)
```

### 😊 Sentimientos e Inteligencia
```python
AnalizadorSentimiento()  # Detección + Escalación automática
ChatbotConSentimiento()  # Integración total
```

---

## 📊 Estadísticas

- **5 Ejercicios Completados:** ✅✅✅✅✅
- **10+ Clases Implementadas**
- **30+ Funciones Funcionales**
- **800+ Líneas de Código**

---

## 📖 Lo Que Aprenderás

✅ **Orquestación de LLMs** con LangChain  
✅ **Memoria Conversacional** (5 tipos diferentes)  
✅ **Gestión de Productos** y Catálogos Dinámicos  
✅ **Descuentos Inteligentes** (por monto, cantidad, combos, VIP)  
✅ **Filtrado Avanzado** por precio, categoría, keywords  
✅ **Base de Datos SQLite** con relaciones  
✅ **Análisis de Sentimientos** para detectar insatisfacción  
✅ **Escalación a Soporte** automática  
✅ **Chatbot Interactivo** fully funcional  

---

## 🎯 Casos de Uso

---

## 🎯 Casos de Uso

| Caso | Descripción | Clase |
|------|-------------|-------|
| **Tienda Online** | Recomendaciones de productos | `ChatbotEcommerce` |
| **Soporte 24/7** | Responder FAQs automáticamente | `AnalizadorSentimiento` |
| **Análisis de Satisfacción** | Detectar clientes insatisfechos | `GestorEscalacion` |
| **Gestión de Inventario** | Consultar disponibilidad en tiempo real | `GestorBDTechStore` |
| **Reportes de Ventas** | Generar estadísticas automáticas | `FiltroProductos` |

---

## ✨ Ejemplo de Uso Rápido

```python
# 1. Iniciar chatbot
from solution import ChatbotEcommerce, GestorDescuentos, AnalizadorSentimiento

chatbot = ChatbotEcommerce(conversation)
gestor = GestorDescuentos()
analizador = AnalizadorSentimiento()

# 2. Chat simple
respuesta = chatbot.chat("¿Tienen laptops disponibles?")

# 3. Calcular descuento
descuento = gestor.aplicar_descuentos(
    productos=["PROD-001", "PROD-004"],
    monto_total=1348
)

# 4. Analizar sentimiento
sentimiento = analizador.analizar_sentimiento(
    "¡Excelente producto, muy satisfecho!"
)
```

---

## 📁 Archivos Generados
