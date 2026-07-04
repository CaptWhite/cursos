<div>
    <iframe 
      src="https://www.youtube.com/embed/T0VlcnJ9r5A"
      style="width: 100%; height: 80vh; border: none;" 
      title="Docker"
      loading="lazy"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
</div>
<hr>
Este es un resumen detallado y estructurado del curso sobre integración de Inteligencia Artificial en aplicaciones web, dividido en seis secciones principales que cubren desde la arquitectura del proyecto hasta el renderizado avanzado en el frontend.

---

# Página 1: Fundamentos del AI Engineer y Monorepositorios

El curso se centra en transformar a un programador tradicional en un **AI Engineer**, definido como aquel profesional que entiende los conceptos de IA y sabe aplicarlos e integrarlos tanto en el backend como en el frontend. El objetivo principal es crear una API que se conecte a proveedores de IA (como OpenAI) y consumirla desde una web utilizando técnicas de **streaming de datos** para mejorar la experiencia del usuario.

### La Estrategia de Monorepositorio Multipaquete
Antes de entrar en código de IA, es vital organizar el proyecto. Se utiliza un **monorepositorio multipaquete**, una técnica empleada por gigantes como Google y bibliotecas como React. 
*   **Ventaja:** Permite gestionar múltiples paquetes (frontend y backend) en un solo repositorio, facilitando los cambios y la instalación de dependencias.
*   **Configuración:** Se utiliza el campo `workspaces` en el `package.json` de la raíz para indicar dónde están las carpetas `frontend` y `backend`.
*   **Eficiencia:** Con comandos como `npm install` desde la raíz, se instalan y reutilizan dependencias en todos los paquetes simultáneamente. Además, se configuran scripts para levantar ambos entornos (back y front) desde la raíz usando el flag `--workspace`.

---

# Página 2: Creación del Backend y Conexión con OpenAI

El backend se construye con **Express** y se enfoca en crear un endpoint para resumir ofertas de trabajo.

### Integración de la API de OpenAI
La API de OpenAI se ha convertido en el estándar de facto. La mayoría de los proveedores (como DeepSeek o Kimi) utilizan formatos compatibles, lo que facilita cambiar de modelo en el futuro.
*   **Variables de Entorno:** Se utiliza la utilidad nativa de Node.js `process.loadEnvFile()` para cargar el archivo `.env` sin dependencias externas.
*   **Configuración del Agente:** Se definen roles: **System** para configurar el comportamiento (ej. "Eres un asistente que resume ofertas") y **User** para pasar el contenido del prompt.
*   **Manejo de Modelos:** Es crucial no "hardcodear" el modelo. Se recomienda usar variables de entorno para facilitar la actualización a modelos más modernos, que suelen ser más baratos, seguros y rápidos.

### Seguridad en la Respuesta
Al manejar errores en la API, nunca se debe enviar el objeto de error interno directamente al cliente, ya que puede filtrar información sensible sobre la infraestructura; en su lugar, se debe devolver un mensaje genérico.

---

# Página 3: Protección de Recursos y Rate Limiting

La Inteligencia Artificial es un recurso costoso. Sin protección, un usuario malintencionado podría agotar el crédito de la API rápidamente mediante ataques de denegación de servicio.

### Implementación de Rate Limit
Para mitigar esto, se integra el middleware `express-rate-limit`.
*   **Configuración:** Se establece una ventana de tiempo (ej. 1 minuto) y un límite de peticiones por IP (ej. 5 peticiones).
*   **Almacenamiento:** Aunque por defecto se usa la memoria, para aplicaciones en producción se recomiendan bases de datos como Redis o PostgreSQL para compartir el estado entre diferentes instancias del servidor.
*   **Headers Estándar:** Es buena práctica activar los `standardHeaders` (draft-8) para informar al usuario cuántas peticiones le quedan y cuánto tiempo debe esperar para reintentar (`Retry-After`).

### El Problema de los Proxies
Muchos servidores están detrás de proxies (Cloudflare, Vercel). Para que el rate limit detecte la IP real del cliente y no la del proxy, se debe configurar `app.set('trust proxy', 1)`. De lo contrario, los atacantes podrían saltarse el límite modificando cabeceras como `X-Forwarded-For`.

---

# Página 4: Streaming de Datos para una UX Superior

Esperar a que la IA genere una respuesta completa puede tardar varios segundos, lo que da una sensación de lentitud. La solución es el **streaming**, que devuelve la respuesta fragmento a fragmento (tokens) conforme se generan.

### Implementación del Stream en el Backend
Se deben modificar las cabeceras de respuesta de HTTP:
*   `Content-Type: text/plain`: Para enviar texto fluido.
*   `Transfer-Encoding: chunked`: Para indicar al navegador que la transferencia será por trozos y debe mantener la conexión abierta.
*   **Iteración Asíncrona:** Se utiliza `stream: true` en la configuración de OpenAI y un bucle `for await` para enviar cada "delta" de contenido al cliente inmediatamente.

### Consumo del Stream en el Frontend
En el frontend, ya no se usa `response.json()`. Se debe obtener un `reader` del `response.body` y utilizar un `TextDecoder` para convertir los bits entrantes en texto. Mediante un bucle `while`, se lee cada fragmento y se concatena al estado actual del resumen, permitiendo que el usuario vea cómo se "escribe" la respuesta en tiempo real.

---

# Página 5: Gateways y Estrategia Multi-modelo

Para evitar el "vendor lock-in" (dependencia total de un proveedor), se introducen los **Gateways** de IA, como el de Vercel.

### Ventajas de los Gateways
*   **Unificación:** Permiten llamar a cientos de modelos (Gemini, Claude, Mistral) usando un solo SDK.
*   **Resiliencia:** Si un proveedor falla, el gateway puede redirigir la petición a otro que ofrezca el mismo modelo.
*   **Simplicidad de Código:** Con funciones como `streamText`, el proceso de enviar un stream se reduce a conectar la salida del modelo con la respuesta del servidor mediante un "pipe" (`pipeTextStreamToResponse`), eliminando bucles manuales complejos.

### Modelos Gratuitos
Existen modelos sin coste de proveedores como Mistral o GLM (disponibles a través de gateways) que son ideales para tareas sencillas como resúmenes o traducciones. Esto permite integrar IA en proyectos sin necesidad de tarjeta de crédito o presupuestos elevados. Es vital revisar la latencia y el coste de cada modelo antes de implementarlo en producción.

---

# Página 6: Renderizado Progresivo de Markdown

Dado que la IA suele responder en formato **Markdown**, mostrarlo como texto plano en el frontend resulta en una experiencia visual pobre.

### Del Renderizado Estático al Progresivo
Un enfoque inicial sería esperar a que termine el stream y usar una librería de Markdown, pero esto rompe la fluidez del streaming. 
*   **Streamdown:** Se introduce la biblioteca `Streamdown`, diseñada específicamente para renderizar Markdown de forma progresiva mientras los datos siguen llegando.
*   **Cursor Animado:** Esta herramienta permite añadir un cursor que parpadea mientras se "escribe" la respuesta, imitando la interfaz de ChatGPT.
*   **Modularización:** Se recomienda extraer toda la lógica de llamada a la IA y gestión de estados (loading, summary, error) a un **Custom Hook** (ej. `useAiSummary`), haciendo que la funcionalidad sea limpia y reutilizable en cualquier parte de la aplicación.

Con estas herramientas, se logra un ciclo completo: un monorepositorio organizado, un backend protegido y eficiente con streaming, y un frontend que renderiza IA de forma elegante y moderna.