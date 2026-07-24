<div>
    <iframe 
      src="https://www.youtube.com/embed/2aN_-m1uU4k"
      style="width: 100%; height: 80vh; border: none;" 
      title="Docker"
      loading="lazy"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
</div>
<hr>

Este es un resumen exhaustivo y detallado del curso para programadores sobre Inteligencia Artificial en 2026, estructurado en seis secciones principales que equivalen a seis páginas de contenido técnico y estratégico.

---

La Inteligencia Artificial está cambiando la forma en la que programamos.
Y entender cómo usarla bien empieza a marcar una diferencia enorme entre unos desarrolladores y otros.

En este pequeño curso te explico qué es realmente la IA en 2026, sin humo y sin promesas mágicas. Vas a entender qué hay detrás de los LLM, cómo generan respuestas, por qué a veces alucinan, qué son los tokens y cómo influyen tanto en el coste como en la calidad de los resultados.

Entramos de lleno en las herramientas que ya están transformando el desarrollo de software: autocompletado avanzado, asistentes inteligentes y agentes capaces de leer tu código, modificar archivos y ejecutar comandos por ti.

Trabajamos con Claude Code desde la terminal, vemos qué es el Model Context Protocol (MCP) y por qué es clave para conectar la IA con el mundo real. También entenderás qué son las Agent Skills, cómo amplían lo que un agente puede hacer y cómo combinarlas para crear flujos realmente potentes.

Y lo mejor. También te explico cómo puedes ejecutarlo en local, en tu propia máquina, gratis y sin enviar tu código a la nube.

Este no es un vídeo para mirar pasivamente. Es un vídeo para entender la IA, perderle el miedo y empezar a construir cosas reales con ella como programador.

Capítulos:
00:00 - Introducción \
00:37 - ¿Qué es la IA? \
04:00 - Las 3 fases del entrenamiento de la IA \
09:31 - ¿Por qué es importante entender cómo funciona? \
17:20 - Los tokens \
24:33 - Editores de código con IA \
43:38 - Agentes de IA \
56:35 - Claude Code \
01:11:54 - MCPs \
01:15:18 - Agent Skills \
01:26:15 - ¿Cómo ejecutarlo gratis en local? \
01:30:00 - OpenCode \
01:33:30 - NotebookLM

---

# Página 1: Fundamentos de los LLM y el Proceso de Entrenamiento

La Inteligencia Artificial aplicada a la programación hoy en día se centra principalmente en los **LLM (Large Language Models)**. Un LLM es, en esencia, una red neuronal con miles de millones de parámetros entrenada para una tarea aparentemente simple: **predecir el siguiente token dado un contexto determinado**. Se puede visualizar como una función gigante a la que se le pasa información y devuelve el fragmento más probable a continuación.

### Las Tres Fases del Entrenamiento
Para que un modelo sea útil, debe pasar por tres etapas críticas:
1.  **Preentrenamiento:** Es la fase más costosa donde se "queman las GPUs" alimentando al modelo con cantidades masivas de datos (Wikipedia, GitHub, libros, etc.) para que aprenda gramática, patrones estadísticos y razonamiento básico.
2.  **Fine-tuning (Ajuste fino):** Una vez que el modelo sabe mucho sobre el lenguaje, se le entrena para mantener conversaciones y seguir instrucciones específicas de tipo pregunta-respuesta.
3.  **RLHF (Aprendizaje reforzado con feedback humano):** Humanos o incluso otras IA evalúan las respuestas para refinar el comportamiento, asegurando que el modelo sea educado, útil y evite contenido dañino.

### Parámetros e Inteligencia
El tamaño de un modelo se mide en **parámetros (B, de Billions)**, que funcionan como "diales" internos que se ajustan durante el entrenamiento. Aunque más parámetros suelen implicar mayor capacidad y razonamiento, también conllevan mayores costes y tiempos de ejecución. Sin embargo, existen modelos pequeños que sorprenden por su eficiencia y rapidez.

---

# Página 2: Tokens, Contexto y Seguridad del Modelo

Es un error común pensar que las IA "entienden" el texto de forma humana; en realidad, calculan probabilidades matemáticas basándose en el contexto previo. Para ello, no procesan palabras, sino **tokens**.

### La Naturaleza de los Tokens
Un token es un fragmento de texto que puede ser una palabra, parte de ella o un carácter especial. La división en tokens depende del modelo específico y no es universal.
*   **Eficiencia lingüística:** El inglés suele ser el idioma más eficiente en el uso de tokens; el español es aceptable, mientras que idiomas como el alemán o el chino consumen muchos más tokens para expresar la misma idea.
*   **Impacto en el coste:** El uso de IA se paga por número de tokens enviados (entrada) y generados (salida). Generalmente, la salida es significativamente más cara que la entrada.

### La Ventana de Contexto (Context Window)
Cada modelo tiene un límite físico de información que puede procesar simultáneamente, conocido como **ventana de contexto**. Este límite determina cuánta documentación, código o historial de conversación podemos enviarle en una sola petición.

### System Prompts y Seguridad
El **System Message** es una instrucción persistente que define cómo debe comportarse el modelo y qué limitaciones tiene. Esto es vital para evitar ataques de **Prompt Injection**, donde los usuarios intentan que la IA ignore sus reglas previas (por ejemplo, pidiendo que responda sobre temas no permitidos apelando a la "abuelita enferma").

---

# Página 3: Evolución de Herramientas y AI en VS Code

El uso de la IA en programación ha evolucionado a través de diferentes niveles de integración, desde simples sugerencias hasta la autonomía total.

### Niveles de Herramientas
1.  **Autocompletado:** Herramientas como GitHub Copilot o Cursor Tab sugieren código en línea mientras escribes basándose en el contexto del archivo actual.
2.  **Asistentes Conversacionales:** Chats como ChatGPT o Claude que permiten interactuar con el código. Una funcionalidad destacada es el **Canvas (Lienzo)**, que abre un editor especial para previsualizar y editar código en tiempo real.
3.  **Editores con IA Nativa:** Editores como Cursor o la nueva integración de **Visual Studio Code**, donde la IA reside en el corazón del editor.

### Funcionamiento de Agentes en VS Code
VS Code ha integrado agentes que pueden realizar tareas en diferentes modos:
*   **Local:** Ejecuta cambios directamente en tu máquina.
*   **Background (Segundo plano):** Trabaja de forma asíncrona creando ramas de Git para no interrumpir tu flujo de trabajo.
*   **Cloud:** Delega la tarea a servidores externos que pueden incluso implementar los cambios en una Pull Request mientras tu ordenador está apagado.
*   **Modo Planear:** El agente realiza una investigación previa del proyecto y propone un plan de múltiples pasos antes de ejecutar cualquier cambio, ideal para tareas complejas.

---

# Página 4: Agentes Autónomos vs. Modelos Reactivos

Un concepto clave para el desarrollador moderno es entender la diferencia entre un LLM y un Agente.

### El LLM como Cerebro y el Agente como Brazos
*   **LLM (Reactivo):** Es una función que recibe un mensaje y devuelve una respuesta. No puede leer archivos ni ejecutar comandos por sí solo.
*   **Agente (Autónomo):** Es un sistema que utiliza un LLM como "cerebro" para decidir qué pasos tomar. El agente tiene herramientas (**Tools**) y opera en un bucle: observa el estado, decide una acción, la ejecuta (editar un archivo, correr un test) y repite hasta completar la tarea.

### Orquestación y Sesiones en el Editor
Los editores modernos permiten gestionar múltiples **sesiones en paralelo** para diferentes tareas. Es fundamental el uso de **Checkpoints**, que permiten restaurar el estado de los archivos y de la conversación a un punto anterior si los resultados de la IA no son satisfactorios.

### Agentes Personalizados (Custom Agents)
Es posible definir agentes propios, por ejemplo, un agente de "Antihacking". Al definir reglas específicas y contextos empresariales en archivos Markdown, el agente puede especializarse en detectar vulnerabilidades de seguridad o fallos de rendimiento específicos de tu arquitectura, actuando como un revisor experto automático.

---

# Página 5: Agentes de Terminal, MCP y Agent Skills

Una tendencia creciente es el uso de agentes que viven exclusivamente en la terminal, como **Claude Code**, permitiendo una interfaz limpia y operación directa sobre el repositorio.

### Claude Code y la Autonomía en Terminal
Claude Code puede inicializar el contexto de un proyecto (`/init`), entender su estructura y ejecutar comandos de Git o Bash mediante lenguaje natural. Es capaz de detectar errores de ejecución y corregir sus propios pasos de forma autónoma.

### MCP (Model Context Protocol) vs. Agent Skills
Es crucial distinguir entre estas dos formas de extender la IA:
*   **MCP (Funcionalidad):** Son herramientas de terceros que conectan la IA con el mundo exterior. Permiten que la IA controle Chrome, consulte APIs externas (como Ticket Taylor para ver ventas de entradas) o use herramientas del sistema operativo.
*   **Agent Skills (Conocimiento):** Son módulos reutilizables de conocimiento en formato Markdown que enseñan a la IA el "saber hacer". Por ejemplo, una skill de **Frontend Design** le da instrucciones expertas para evitar estéticas genéricas y crear interfaces modernas y pulidas.

Para optimizar costes en conversaciones largas, se utiliza el comando **`/compact`**, que resume el historial previo para liberar espacio en la ventana de contexto sin perder la información esencial.

---

# Página 6: Ejecución Local, OpenCode y NotebookLM

El ecosistema ofrece alternativas para ejecutar estos modelos de forma gratuita y privada, así como herramientas para la gestión del conocimiento.

### IA en Local con Ollama
**Ollama** permite descargar e instalar modelos directamente en tu máquina (como GLM 4.7 Flash). Esto garantiza privacidad total y elimina costes de API. Es posible incluso lanzar agentes de terminal como Claude Code apuntando a estos modelos locales para trabajar de forma 100% gratuita si se dispone de suficiente GPU.

### OpenCode: La Alternativa Abierta
**OpenCode** se posiciona como una alternativa de código abierto a Claude Code. Ofrece una interfaz visualmente atractiva y permite conectar con múltiples proveedores (OpenAI, Anthropic, Google) o usar modelos locales de Ollama. Además, ofrece modelos gratuitos limitados (como MiniMax o Kimi) para pruebas rápidas sin necesidad de configuración compleja.

### Gestión de Fuentes con NotebookLM
Finalmente, **NotebookLM** de Google es una herramienta revolucionaria para el estudio y la documentación. Permite subir PDFs, vídeos de YouTube y URLs para crear una IA personalizada basada exclusivamente en esas fuentes.
*   **Citado de fuentes:** Cada respuesta incluye citas directas de los documentos originales.
*   **Generación de Artefactos:** A partir de las fuentes, puede crear automáticamente guías de estudio, cuestionarios, infografías, mapas mentales e incluso podcasts de audio donde dos voces discuten el contenido de tus documentos.