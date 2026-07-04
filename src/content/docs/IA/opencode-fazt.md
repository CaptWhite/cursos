<div>
    <iframe 
      src="https://www.youtube.com/embed/2gO8WyctqMk"
      style="width: 100%; height: 80vh; border: none;" 
      title="Docker"
      loading="lazy"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
</div>
<hr>
A continuación, presento un resumen exhaustivo y detallado del video informativo sobre **OpenCode**, estructurado en seis secciones principales para cubrir todos los aspectos técnicos y operativos de esta herramienta.

---

# Página 1: Introducción y Fundamentos de OpenCode

**OpenCode** se presenta como uno de los agentes de inteligencia artificial más populares y potentes para programar, destacando por ser una **herramienta de código abierto**. A diferencia de opciones propietarias, funciona principalmente desde la terminal y ofrece una versatilidad superior al permitir la conexión con prácticamente cualquier modelo de lenguaje, ya sea privado (como GPT o Claude) o modelos abiertos.

### Características Principales
*   **Agnosticismo de Modelos:** No está ligado a ninguna empresa específica, lo que permite integrar servicios de OpenAI, Anthropic, Google Gemini, GitHub Copilot y modelos locales o internacionales.
*   **Interfaz de Usuario de Terminal (TUI):** Ofrece una experiencia rica con múltiples sesiones, configuraciones, temas personalizados y atajos de teclado optimizados para el flujo de trabajo del desarrollador.
*   **Multiplataforma:** Aunque está optimizado para entornos Linux y Mac, tiene soporte completo para Windows.

### Proceso de Instalación
Para instalar OpenCode, es indispensable contar con **Node.js**. El proceso recomendado por el autor es:
1.  Descargar e instalar Node.js desde su sitio oficial.
2.  Verificar la instalación con los comandos `node -v` y `npm -v`.
3.  Ejecutar el comando de instalación universal de OpenCode proporcionado en su sitio web oficial.
4.  Comprobar el funcionamiento escribiendo simplemente `opencode` en la terminal, lo cual lanzará la interfaz de chat.

---

# Página 2: Modelos, Suscripciones y Autenticación

Una de las grandes ventajas de OpenCode es su capacidad para gestionar múltiples suscripciones de IA de manera centralizada.

### OpenCode Zen y Modelos Gratuitos
La herramienta incluye por defecto acceso a modelos gratuitos a través de un servicio llamado **OpenCode Zen**. Estos modelos (como GLM, Kimi o MiniMax) permiten probar la herramienta sin costo inicial ni necesidad de registro, aunque pueden ser más lentos debido a la alta demanda.

### Conexión de Proveedores (Auth-Login)
Para un uso profesional, el usuario puede vincular sus propias suscripciones pagas mediante el comando **`opencode auth-login`**.
*   **Suscripciones Soportadas:** Es posible autenticarse con OpenAI (ChatGPT Plus), Anthropic (Claude Pro/Max), GitHub Copilot y Google Gemini.
*   **Método de Autenticación:** Generalmente, la herramienta genera una URL que se abre en el navegador para autorizar el acceso o solicita una API Key directa.
*   **Cambio Dinámico:** Una vez logueado, el comando **`/models`** o el atajo **`Control + P`** permite alternar instantáneamente entre los modelos disponibles (por ejemplo, cambiar de GPT-4o a Claude 3.5 Opus) según la complejidad de la tarea.

---

# Página 3: Atajos de Teclado y Gestión de Sesiones

Para maximizar la eficiencia en la terminal, OpenCode incorpora un sistema robusto de navegación y gestión de hilos de trabajo.

### Atajos de Teclado Esenciales
*   **`Control + P` (Command Palette):** Permite lanzar rápidamente funciones como cambio de modelos, temas o sesiones.
*   **Edición Rápida:** `Control + Izquierda/Derecha` para saltar palabras, `Control + W` para borrar palabras completas y `Control + U` para limpiar toda la línea de comandos.
*   **Variantes de Modelo:** `Control + T` permite alternar entre versiones rápidas o pesadas (High, Medium, Max) del modelo activo.

### El Poder de las Sesiones
OpenCode permite trabajar en múltiples tareas simultáneamente dentro de un mismo proyecto sin perder el contexto.
*   **`/new`**: Crea una sesión de chat totalmente nueva.
*   **`/sessions`**: Lista todas las sesiones activas.
*   **`/switch` (o `Control + X + L`):** Permite saltar entre hilos de conversación, por ejemplo, corrigiendo un error en una sesión mientras se genera documentación en otra.
*   **Renombrado y Borrado:** Con `Control + R` se puede dar un nombre descriptivo a la sesión, y con `Control + D` se eliminan las sesiones innecesarias.

---

# Página 4: Contexto del Proyecto y Modos de Trabajo

El sistema está diseñado para "entender" la estructura completa del código mediante archivos de especificación estándar.

### Inicialización y Contexto (`agents.md`)
Al ejecutar el comando **`/init`**, OpenCode explora todo el proyecto (carpetas, archivos y dependencias) para generar un archivo llamado **`agents.md`**.
*   Este archivo actúa como un **contexto inicial** que la IA lee cada vez que se inicia una sesión, evitando que el usuario tenga que explicar la arquitectura del proyecto en cada prompt.
*   Es un estándar compatible con otras herramientas de IA como Cursor o GitHub Copilot.

### Modos: Build vs. Plan
El usuario puede alternar entre dos filosofías de trabajo usando la tecla **`Tab`**:
1.  **Modo Build (Construcción):** Es el modo operativo por defecto donde el agente escribe código, crea archivos y ejecuta comandos directamente para cumplir una instrucción.
2.  **Modo Plan (Planificación):** En este modo, la IA no realiza cambios inmediatos. En su lugar, analiza la tarea y propone un **paso a paso (especificación)**. Esto es ideal para tareas complejas, ya que permite al desarrollador revisar y confirmar el plan antes de que se ejecute una sola línea de código.

---

# Página 5: Protocolo de Contexto de Modelo (MCP)

Una de las innovaciones más potentes que menciona el video es la integración de los **MCP (Model Context Protocol)**, que actúan como "conectores" entre la IA y herramientas externas.

### ¿Qué son los MCP?
Son extensiones que permiten a la IA interactuar con servicios externos como Gmail, Notion, Slack o incluso el propio sistema operativo y navegadores web.

### Ejemplos Prácticos de MCP
*   **Context Seven:** Proporciona documentación actualizada de frameworks y librerías a la IA en tiempo real, superando el límite de conocimiento de entrenamiento de los modelos.
*   **Chrome DevTools:** Permite que la IA abra una instancia de Chrome, navegue por la aplicación en desarrollo, detecte errores en la consola y se "repare a sí misma" basándose en el comportamiento real del navegador.
*   **Test Sprite:** Un sistema avanzado de testing que genera archivos de prueba en Python, ejecuta los tests en la nube y proporciona reportes visuales y grabaciones en video de los fallos encontrados.

---

# Página 6: Skills, IDEs y Configuración Avanzada

Para finalizar, OpenCode permite una personalización profunda mediante habilidades específicas e integración con entornos de desarrollo.

### Agent Skills (Habilidades)
A diferencia de los MCP, los **Skills** son archivos Markdown (`skill.md`) que contienen instrucciones expertas sobre cómo la IA debe comportarse o diseñar.
*   **Interface Design:** Es un skill popular que enseña a la IA principios de diseño moderno, mejorando drásticamente la calidad visual de las interfaces generadas (añadiendo skeletons, mejores proporciones y animaciones) frente a las respuestas estándar del modelo.

### Integración con Editores (VS Code)
Aunque su hogar es la terminal, OpenCode cuenta con una **extensión oficial para VS Code** (y otros editores basados en él como Cursor). Esto permite tener el chat de OpenCode anclado a un lado del editor, con la capacidad de arrastrar archivos directamente al chat presionando `Shift` para dar contexto inmediato a la IA.

### Solución de Problemas y Configuración Global
*   **`opencode.jsonc`**: Es el archivo central donde se configuran temas, MCPs y permisos globales.
*   **Bug de Almacenamiento en Windows:** El autor advierte sobre un problema donde las capturas (snapshots) pueden consumir mucho espacio en disco (GBs). La solución es editar la configuración global y establecer la propiedad `"snapshot": false`.
*   **Modo Web:** Ejecutando `opencode web` se abre una interfaz gráfica completa que facilita la gestión de múltiples proyectos y agentes de forma visual.