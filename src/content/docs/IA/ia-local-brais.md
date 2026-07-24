<div>
    <iframe 
      src="https://www.youtube.com/embed/LQqv4M_NtNc"
      style="width: 100%; height: 80vh; border: none;" 
      title="Docker"
      loading="lazy"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
</div>
<hr>

Aprende a utilizar modelos de IA que se ejecutan desde tu propia máquina gratis y de manera privada con Ollama o LM Studio. Desde su elección y configuración hasta su uso en herramientas de desarrollo como VSCode, Cursor o Claude Code.

Índice del curso:
00:00:00 | Introducción
00:02:09 | Fundamentos de la IA local
00:16:34 | Cómo elegir un modelo
00:22:52 | Modelos locales con LM Studio
00:35:23 | Modelos locales con Ollama
00:47:36 | Modelos locales en VS Code
01:03:52 | Modelos locales en Claude Code
01:09:06 | Conclusiones y recomendaciones

--- 
### Documentación
- [llm-stats.com](llm-stats)

AI Leaderboard — Compare 300+ Top AI Models by Intelligence, Speed & Price
Independent rankings of GPT, Claude, Gemini, Llama, DeepSeek and 300+ AI models — composite LLM Stats Score, updated continuously from public benchmarks and live API metrics. See the full LLM Leaderboard for complete LLM rankings with advanced.

- [https://lmstudio.ai/](https://lmstudio.ai/)

Run AI models, locally and privately.
Use local LLMs like gpt-oss, Qwen3.6, Gemma4, DeepSeek and many more, locally on your own hardware.

- [https://ollama.com](https://ollama.com/)

Run any app or agent with open models.
Get up and running with OpenClaw, Claude Code, and more in minutes using open models powered by Ollama.
---

A continuación, presento un resumen exhaustivo y estructurado del taller de Inteligencia Artificial en local, basado íntegramente en la fuente proporcionada. El contenido se ha dividido en seis secciones principales para cubrir todos los aspectos técnicos y estratégicos mencionados en el video.

---

# Página 1: Fundamentos y Ventajas de la IA en Local

La Inteligencia Artificial en local representa un cambio de paradigma frente al modelo tradicional basado en la nube (como ChatGPT, Claude o Gemini). Ejecutar modelos directamente en nuestra propia máquina no es solo una alternativa técnica, sino una decisión estratégica basada en cuatro pilares fundamentales:

### ¿Por qué utilizar IA en Local?
*   **Privacidad Absoluta:** Los datos y el código que se procesan nunca salen de la máquina. Esto es crítico para empresas o desarrolladores que trabajan con información sensible o propiedad intelectual que no debe ser enviada a servidores externos.
*   **Costo Cero:** A diferencia de las suscripciones premium o el pago por uso de tokens en la nube, el costo de ejecutar estos modelos es cero, ya que se utiliza el hardware propio.
*   **Funcionamiento Offline:** Al estar el modelo descargado en el disco duro, la IA funciona perfectamente sin conexión a internet.
*   **Control Total:** El usuario decide exactamente qué modelo usar, qué versión, los parámetros de configuración y el tamaño del contexto sin depender de las actualizaciones o restricciones de un proveedor externo.

### Requisitos de Hardware
No se requiere una "máquina de la NASA" para empezar. El autor sugiere como **mínimo unos 8 GB de RAM** (preferiblemente memoria unificada o GPU). Por ejemplo, un modelo de 3 billones de parámetros ocupa unos 3 o 4 GB en disco y aproximadamente lo mismo en RAM al cargarse. Máquinas con 16 GB o 32 GB de RAM ya permiten ejecutar modelos de 7 a 10 billones de parámetros con gran fluidez.

---

# Página 2: Conceptos Técnicos: Pesos, Parámetros y Cuantización

Para dominar la IA local, es necesario entender cómo se estructuran y comprimen los modelos para que puedan ser ejecutados en hardware de consumo.

### Pesos Abiertos y Modelos Open Source
El concepto clave son los **pesos abiertos**. Esto significa que, aunque el código de entrenamiento no sea siempre público, los "pesos" (los archivos descargables que contienen el conocimiento del modelo) sí lo son, permitiendo su ejecución local.

### Parámetros e Inteligencia
Los modelos se clasifican por su número de **parámetros** (expresados en billones, como 3B, 7B, 70B).
*   **Más parámetros:** Mayor calidad de respuesta, razonamiento más profundo, pero requieren más memoria RAM y son más lentos.
*   **Menos parámetros:** Mayor velocidad y menor consumo de recursos, ideales para tareas sencillas o máquinas limitadas.

### Cuantización y Formatos
La **cuantización** es el proceso de comprimir los pesos del modelo para que ocupen menos espacio sin perder demasiada calidad. El autor recomienda el formato **GGUF** y la cuantización **Q4_K_M** como el "punto dulce" o equilibrio perfecto entre tamaño y rendimiento para equipos domésticos. Modelos sin comprimir (FP16) requerirían infraestructuras profesionales inalcanzables para un usuario estándar.

---

# Página 3: Selección de Modelos y Estrategia de Uso

No todos los modelos sirven para todo. La clave está en saber filtrar y elegir el modelo adecuado según la potencia de nuestra máquina y la tarea a realizar.

### Clasificaciones y Rankings
Existen herramientas como **llm-stats** que permiten ver rankings actualizados de modelos. Es importante distinguir entre:
1.  **Modelos Frontera:** Los más potentes (GPT-5.5, Claude Opus) que solo viven en la nube debido a su costo millonario de infraestructura.
2.  **Modelos Abiertos:** Como **Gemma** (Google), **Llama** (Meta), **Qwen** (Alibaba), **Mistral** o **Nemotron**.

### Filtrado por Hardware
Para un teléfono móvil o máquinas muy básicas, se recomiendan modelos de menos de 4 billones de parámetros. Para una máquina estándar de 16 GB de RAM, los modelos de **7 a 10 billones** son los más adecuados.

### Estrategia de Ahorro de Costos
La IA local no reemplaza necesariamente a la de pago, sino que la complementa. El desarrollador inteligente utiliza su **IA local para tareas cotidianas** (explicar código, generar bloques simples, hacer tests) y reserva sus tokens de pago o suscripciones premium para tareas de alta complejidad arquitectónica.

---

# Página 4: Herramienta Visual: LM Studio

**LM Studio** es la herramienta recomendada para quienes prefieren una interfaz gráfica intuitiva para gestionar sus IAs locales.

### Características de LM Studio
*   **Interfaz Gráfica (GUI):** Es gratuita, multiplataforma y permite buscar, descargar y ejecutar modelos sin tocar la terminal.
*   **Buscador Integrado:** Permite filtrar modelos por popularidad, fecha o compatibilidad con el hardware detectado automáticamente.
*   **Configuración del Modelo:** Permite ajustar la **ventana de contexto** (cuánta información recuerda el modelo) y el **GPU Offload** (cuánto trabajo se delega a la tarjeta gráfica para acelerar la respuesta).

### Modo Servidor (Developer)
Una de las funciones más potentes de LM Studio es la capacidad de convertir el modelo en un **servidor local (API)**. Al pulsar el botón de "arrancar servidor", cualquier otra herramienta de desarrollo puede conectarse a LM Studio para usar la IA local como si fuera un servicio en la nube, pero funcionando internamente en la máquina.

---

# Página 5: Integración con el Entorno de Desarrollo (IDE)

El verdadero potencial de la IA local se desbloquea al integrarla directamente en el flujo de trabajo del programador, específicamente en editores como **Visual Studio Code**.

### Ollama: El Estándar para Integraciones
Aunque LM Studio es visual, **Ollama** es la herramienta preferida para integraciones técnicas debido a su ligereza y enfoque en la terminal. Ollama permite lanzar modelos con comandos sencillos como `ollama run [modelo]` y ofrece un servidor API persistente en segundo plano.

### Métodos de Conexión en VS Code
1.  **Extensión "Continue":** Permite conectar VS Code con Ollama o LM Studio de forma sencilla, permitiendo usar la IA en modo chat o incluso en modo agente (capaz de crear archivos y leer el sistema).
2.  **Integración Nativa con Copilot:** El chat oficial de GitHub Copilot en VS Code ya permite añadir proveedores externos. Configurando el puerto local de Ollama, el usuario puede seleccionar sus modelos locales (como Gemma o Qwen) directamente desde el desplegable de modelos de Copilot.

---

# Página 6: Agentes de Terminal y Conclusiones

La IA local también puede potenciar las herramientas más modernas de la industria, como los agentes autónomos de terminal.

### Claude Code con IA Local
Herramientas como **Claude Code** (la utilidad de terminal de Anthropic) son conocidas por ser costosas debido al uso de modelos premium en la nube. Sin embargo, mediante comandos específicos (`ollama launch-code`), es posible forzar a Claude Code a utilizar los **modelos locales** que tenemos en Ollama. Esto permite disfrutar de las capacidades agénticas de la herramienta de forma totalmente gratuita y privada.

### Consideraciones Finales
*   **Limitaciones de los Agentes:** Los modelos muy pequeños pueden fallar en tareas complejas de "agente" (como lanzar comandos o navegar archivos); para estos casos se requieren modelos con más billones de parámetros y ventanas de contexto más amplias (16K o 32K).
*   **Velocidad vs. Calidad:** Existe una relación directa entre el hardware (CPU/RAM), el número de parámetros y la velocidad de respuesta.
*   **El Futuro es Local:** El autor concluye que, aunque los modelos frontera en la nube seguirán existiendo, el futuro de la IA pasa por modelos locales cada vez más eficientes que se convertirán en el estándar para el desarrollo diario.

Este taller demuestra que la barrera de entrada para la IA local ha caído, permitiendo a cualquier desarrollador tener un asistente potente, privado y gratuito en su propia máquina.