<div>
    <iframe 
      src="https://www.youtube.com/embed/ZZq4TpNgnvg"
      style="width: 100%; height: 80vh; border: none;" 
      title="Docker"
      loading="lazy"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
</div>

Este es un resumen detallado y estructurado del curso de **OpenCode**, basado en el material proporcionado en las fuentes.

---

En este video te muestro cómo instalarlo, dominar su TUI, optimizar prompts, ahorrar tokens y construir una app real de running paso a paso. Además, exploramos agentes, comandos personalizados, modelos de pago y cómo sacarle el máximo rendimiento en tu flujo de desarrollo.

00:00:00 - ¿Que es OpenCode? \
00:02:58 - Instalando OpenCode + TUI \
00:05:30 - Ventajas \
00:09:32 - Nuestro primer prompt en un proyecto \
00:11:22 - Más comandos y TUI \
00:13:57 - Build y Plan \
00:16:53 - Cómo ahorrar tokens \
00:20:10 - Modo shell \
00:22:08 - ¿Por que importa el historial? \
00:23:25 - Creando un proyecto desde cero \
00:27:58 - Archivo SPEC.md \
00:29:39 - Tareas agrupadas \
00:30:50 - Comando Timeline \
00:32:50 - Cambiar tema \
00:34:19 - Notificaciones y revertir cambios \
00:38:51 - Modelos de Pago (OpenCode GO) + Beneficios \
00:43:05 - Construyendo aplicacion de running \
00:52:04 - AGENTS.md \
01:01:35 - Cambiar entre sesiones \
01:04:14 - mejores modelos de pago \
01:05:32 - AgentSkill \
01:13:00 - Skill para crear videos con HTML, CSS y JS \
01:23:42 - Reducir el porcentaje usado \
01:25:00 - Conectar tu suscripción a OpenCode \
01:33:01 - Comparativa de modelos \
01:35:14 - Agentes \
01:42:10 - Crea tus propios comandos \
01:45:50 - Compartir sesiones \
01:46:50 - Ejecutar OpenCode desde la terminal \
01:48:16 - Crear servidor y web \
01:50:18 - Arguments 

---

# Página 1: Introducción y Fundamentos de OpenCode

**OpenCode** se define como un **agente de código con inteligencia artificial de código abierto**, que funciona directamente en la terminal. Surge como una alternativa potente a herramientas comerciales como Claude Code, destacando por su soporte comunitario y su transparencia. A diferencia de otras opciones pagas, OpenCode permite una personalización profunda y el uso de diversos proveedores de IA.

### Requisitos y Configuración Inicial
Para utilizar OpenCode, el requisito básico es contar con una **terminal**. Aunque es compatible con múltiples opciones, se recomiendan terminales modernas como:
*   **Warp:** (Recomendada por el autor) Ahora de código abierto y con integraciones específicas para agentes de IA.
*   **Alacritty:** Una opción clásica, multiplataforma y gratuita.
*   **Ghostty:** Destacada por su alto rendimiento gracias a la aceleración por GPU.

**Instalación:** El proceso es sencillo mediante un comando universal de instalación (`opencode.ai/install`) que gestiona las dependencias según el sistema operativo. Una vez instalado, se puede verificar la versión con el comando `opencode --version`.

### La Interfaz de Usuario de Terminal (TUI)
Al ejecutar `opencode` en la raíz de un proyecto, se despliega una **TUI (Terminal User Interface)**. Esta interfaz permite:
*   Interactuar mediante un chat persistente con el agente.
*   Visualizar el **hilo de pensamiento** (*thinking*) del modelo y las herramientas que está ejecutando.
*   Monitorear en tiempo real el consumo de **tokens** y el porcentaje de **contexto** utilizado.
*   Recibir notificaciones cuando el agente termina una tarea compleja.

---

# Página 2: Modelos, Proveedores y Suscripciones

Una de las mayores fortalezas de OpenCode es su **agnosticismo respecto a los modelos** de lenguaje. Permite conectar diversas suscripciones que el usuario ya posea o utilizar opciones gratuitas.

### Proveedores Disponibles
El comando `/connect` permite vincular servicios como:
*   **GitHub Copilot:** Reutiliza la suscripción existente para acceder a modelos como Claude 3.5 Sonnet u Opus.
*   **OpenAI:** Permite usar modelos como GPT-4o o GPT-5.5 (según disponibilidad) con la cuenta de ChatGPT Plus.
*   **OpenCode Zen:** Ofrece **modelos gratuitos** (MiniMax, Big Pickle, Nemotron) que funcionan sin tarjeta de crédito ni registro previo.

### Suscripción OpenCode Go
Para usuarios que buscan la mejor relación calidad-precio, existe **OpenCode Go**. 
*   **Costo:** Aproximadamente $5 el primer mes y $10 los siguientes.
*   **Valor:** La suscripción está "subsidiada", ofreciendo un valor real de modelos de aproximadamente $60 por solo $10 al mes.
*   **Modelos destacados:** Incluye acceso a modelos potentes como **DeepSeek V4**, **Qwen 3.6 Plus** y **Mimo 2.5/2.7** (de Xiaomi). Estos modelos suelen estar al nivel de los mejores del mercado (*State of the Art*).

### Selección del Modelo
Con el comando `/models`, el usuario puede cambiar de modelo en cualquier momento de la conversación. Por ejemplo, se puede usar un modelo gratuito para tareas simples y cambiar a uno "X-High" (pensamiento profundo) para resolver problemas de arquitectura complejos.

---

# Página 3: Eficiencia y Ahorro de Tokens

El manejo de tokens es crítico para no agotar los límites de las suscripciones y mantener la velocidad de respuesta. OpenCode ofrece herramientas específicas para optimizar este consumo.

### Selección Específica de Archivos con `@`
En lugar de pedirle al agente que "explore todo el proyecto" (lo cual consume mucho contexto), se puede usar el símbolo **`@`** seguido del nombre del archivo.
*   **Ventaja:** El agente solo lee el archivo mencionado, reduciendo el tiempo de respuesta de segundos a milisegundos y ahorrando tokens innecesarios.

### Modo Shell con `!`
Un error común es pedirle a la IA que ejecute comandos básicos (como `git status` o `ls`). Esto consume tokens y tiempo de procesamiento.
*   **Solución:** Usar el prefijo **`!`** activa el modo **Shell**, permitiendo ejecutar comandos reales de la terminal directamente desde la interfaz de OpenCode. 
*   **Integración:** Lo que devuelve la terminal en modo Shell se añade al contexto, por lo que el agente puede razonar sobre el *output* de un test o un error de compilación sin haber tenido que ejecutarlo él mismo.

### Compactación de Sesiones
Cuando una conversación se alarga, el historial consume gran parte del contexto (ruido). El comando **`/compact`** crea un resumen de lo avanzado hasta el momento, borra el historial detallado y libera espacio de contexto, permitiendo que el modelo recupere precisión en sus respuestas.

---

# Página 4: Agentes, Subagentes y Personalización

OpenCode no es solo un chat; es un ecosistema de agentes especializados que pueden trabajar de forma coordinada.

### Agentes Primarios: Build vs. Plan
*   **Build (Modo Construcción):** Es el agente por defecto con permisos para escribir archivos y realizar cambios directos en el disco.
*   **Plan (Modo Planificación):** Un agente restringido que analiza el proyecto y propone soluciones sin modificar el código. Es ideal para explorar mejoras de rendimiento o accesibilidad antes de implementarlas.

### Subagentes y Orquestación
OpenCode permite delegar tareas a **subagentes** especializados para trabajar en paralelo:
*   **`explore`:** Para inspeccionar partes específicas del código.
*   **`general`:** Para investigaciones de alto nivel o búsqueda de librerías.
*   **`reviewer`:** Un revisor de código que busca fallos sin alterar el archivo.
*   **`security`:** Especializado en identificar vulnerabilidades.

El usuario puede actuar como orquestador, lanzando tareas a múltiples subagentes simultáneamente (ej. "Security busca vulnerabilidades mientras Explore analiza el CSS") y recibiendo un plan consolidado al final.

### Creación de Agentes Propios
Es posible definir agentes personalizados creando archivos Markdown en la carpeta `.opencode/agents/`. En estos archivos se definen:
*   La **descripción** y el rol del agente.
*   Los **permisos** (qué comandos de shell puede usar o si puede editar archivos).
*   El **modelo** de IA y la temperatura específica para ese rol.

---

# Página 5: El Contexto del Proyecto (`agents.md` y `design.md`)

Para evitar repetir instrucciones en cada prompt (como "no uses TypeScript" o "usa pnpm"), OpenCode utiliza archivos de especificación abierta.

### `agents.md`: El manual para la IA
Mediante el comando `/init`, se genera un archivo **`agents.md`**. Este archivo sirve como un "README" exclusivo para la inteligencia artificial, donde se detallan:
*   Decisiones de **arquitectura** (ej. "siempre usar Bun en lugar de Node").
*   Restricciones de **dependencias** y estilos de codificación.
*   **Comandos** específicos del proyecto.
Este formato es un estándar compatible con otras herramientas como Cursor o Claude Code.

### `design.md`: Guía de Estilos
Similar al anterior, el archivo **`design.md`** define las reglas visuales del proyecto: colores, tipografías y comportamientos de la interfaz. Esto asegura que cualquier componente nuevo que el agente cree sea coherente con la estética existente.

### Agent Skills (Habilidades)
Las **Skills** son archivos Markdown que dotan a la IA de conocimientos expertos en bibliotecas o áreas específicas (React, SEO, Accesibilidad).
*   **Auto-Skills:** Existe una herramienta (`npx auto-skills`) que audita el proyecto, detecta las dependencias y recomienda qué habilidades instalar para mejorar los resultados del agente. Estas habilidades actúan como "disparadores" automáticos cuando el usuario pide optimizar ciertas áreas.

---

# Página 6: Funciones Avanzadas y Automatización

OpenCode incluye capacidades que van más allá de la simple escritura de código, permitiendo incluso la generación de contenido multimedia y la automatización de flujos de trabajo.

### Hyperframes: Vídeo desde Código
Mediante una Skill especializada llamada **Hyperframes**, OpenCode puede generar vídeos promocionales de corta duración utilizando únicamente HTML, CSS y JavaScript. 
*   El agente crea una composición animada basada en el código del proyecto.
*   Permite editar el vídeo cambiando variables de código en una interfaz de estudio (Timeline), sin necesidad de herramientas de edición de vídeo tradicionales.

### Comandos Personalizados
El usuario puede crear sus propios comandos rápidos (ej. `/super-commit`) definiendo un archivo Markdown en `.opencode/commands/`. Estos comandos pueden recibir argumentos y automatizar tareas complejas como agrupar cambios en commits semánticos y hacer push automáticamente. Los comandos pueden ser locales al proyecto o **globales** para el usuario.

### Timeline y Compartición
*   **Timeline:** Permite navegar por todo el historial de la sesión, buscar prompts específicos y revertir o "forkear" el proyecto a un punto anterior.
*   **Share:** Genera una URL pública donde otros pueden ver todo el hilo de ejecución, los cambios realizados y los modelos utilizados, facilitando la colaboración.

### Automatización y Modo Servidor
OpenCode puede integrarse en scripts de CI/CD o servidores remotos:
*   **CLI:** Ejecución directa con `opencode run "instrucción"` sin entrar en la interfaz gráfica.
*   **Server:** El comando `opencode serve` levanta un servidor web con contraseña que permite interactuar con el agente y los archivos del proyecto desde cualquier navegador, ofreciendo una interfaz visual completa (OpenCode Web).