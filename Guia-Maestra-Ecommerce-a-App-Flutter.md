# 📱 Guía Maestra: De Web E-Commerce a App Nativa Flutter

> **Enlace Original Notion:** [Ver en Notion (Duplicar en tu Workspace)](https://app.notion.com/p/Gu-a-Maestra-De-Web-E-Commerce-a-App-Nativa-Flutter-3122cd2e5d1580398c00d7124bc06bd0)
> **Categoría:** Vibe Coding / De Web E-Commerce a App Nativa Flutter

---

## 1. Ficha Técnica del Proyecto

| **Elemento** | **Descripción** |
| :--- | :--- |
| **Nombre del Proyecto** | Orquestación Móvil: E-Commerce a Flutter |
| **Stack Tecnológico** | Antigravity, Stitch, Firecrawl, Dart/Flutter |
| **Objetivo Principal** | Transformar una página web e-commerce de referencia en una aplicación móvil nativa en Flutter totalmente funcional, replicando su UI/UX. |
| **Requisito Único** | Antigravity instalado |

---

## 2. Arquitectura (El Cerebro Digital)

Este proyecto se integra en el ecosistema general replicando el ciclo de trabajo de un equipo de desarrollo completo dentro de una sola estación de trabajo. A partir de una idea o referencia web, utilizamos múltiples "Cerebros" para ejecutar la visión:

- **Investigación y Extracción (Firecrawl):** Actúa como el analista de datos, haciendo scraping profundo del DOM para extraer branding, catálogos y flujos.
- **Dirección Creativa (Stitch):** Funciona como tu Director Creativo personal para generar la identidad y la interfaz móvil desde cero.
- **Ingeniería Ágil (Dart/Flutter MCP + Antigravity):** Ejecuta el código de la arquitectura, conectando el razonamiento estratégico con la escritura de código limpio y escalable.

---

## 3. Configuración Técnica (Orquestación)

Para que Antigravity pueda "hablar" con estas tecnologías, necesitamos configurar los puentes (Servidores MCP) y dotar al agente de las herramientas correctas.

### PASO 0: Auditoría del Entorno (Agente como Soporte Técnico)

*Copia todo este prompt:*

```text
- Antes de analizar la idea, debes garantizar que la computadora del usuario esté lista para compilar aplicaciones móviles.
- Ejecuta comandos de lectura en la terminal para comprobar la existencia de las siguientes 3 herramientas vitales:
    1. **Flutter SDK:** Ejecuta `flutter --version`
    2. **JDK 17 (Java):** Ejecuta `java -version` (Asegúrate de que la versión detectada corresponda a la 17).
    3. **Android SDK:** Ejecuta `flutter doctor` para comprobar el estado de las herramientas de Android.

- **Si falta alguna herramienta (Instalación Proactiva):** NO te detengas. Tu objetivo es resolverlo de forma autónoma. Sigue estos pasos estrictamente:
    1. Ejecuta un comando para identificar el sistema operativo del usuario (Windows, macOS o Linux).
    2. Busca e implementa los comandos de terminal necesarios para instalar la herramienta faltante de forma silenciosa o desatendida. (Usa gestores de paquetes nativos como `winget` o `choco` para Windows, `brew` para macOS, o `apt` para Linux).
    3. Para el Android SDK, si se requieren aceptar licencias, ejecuta automáticamente: `yes | flutter doctor --android-licenses` (o el equivalente en el sistema operativo detectado).
    4. Una vez que el comando de instalación termine, vuelve a ejecutar la comprobación (Paso 2) para confirmar el éxito de la operación.

- **Si la instalación automática requiere permisos (Sudo/Admin) o falla:** Solo en este escenario, detente y comunícate con el usuario de forma muy amigable y sin jerga técnica. Explícale que intentaste instalar los "motores" para la app pero necesitas su autorización. Entrégale el comando exacto que debe pegar en su terminal para completar la instalación.

- **Si todo está instalado y configurado correctamente:** Confírmale al usuario de forma entusiasta que su sistema está en perfectas condiciones y avanza automáticamente al Paso 1.
```

> 💡 *Nota: Con el LLM de Claude Code instala automáticamente las librerías, pero con Gemini te va a guiar en el paso a paso de la instalación.*

---

### A. Configuración de Servidores MCP (`mcp_config.json`)

Debes inyectar estos tres servidores en tu archivo `mcp_config.json` (ubicado en tu AppData o configuración global). *Copia el siguiente prompt:*

```text
Actúa como un Especialista en Integraciones de mi entorno VS Code. Necesito que actualices mi configuración de servidores MCP de forma autónoma siguiendo estos 4 pasos exactos:

1. Localiza mi archivo de configuración de servidores MCP (generalmente `mcp_config.json` o `claude_desktop_config.json` ubicado en mi AppData o en la carpeta de configuración global).

2. Inyecta exactamente las siguientes configuraciones dentro del objeto "mcpServers". Asegúrate de mantener la sintaxis JSON válida y no sobrescribir mis configuraciones previas:

{
  "firecrawl": {
    "command": "npx",
    "args": ["-y", "firecrawl-mcp"],
    "env": {
      "FIRECRAWL_API_KEY": "TU_API_KEY_AQUI"
    }
  },
  "stitch": {
    "command": "npx",
    "args": ["-y", "stitch-mcp-auto@latest"]
  },
  "dart-mcp-server": {
    "command": "dart",
    "args": ["mcp-server"]
  }
}

3. Guarda y valida el archivo JSON para asegurarte de que no haya errores de formato.

4. Abre la terminal integrada de mi editor y ejecuta globalmente la instalación del paquete de Dart usando este comando:
dart pub global activate dart_mcp_server

Confírmame cuando hayas terminado, avísame si necesito reiniciar el editor (o darle al botón Refresh de MCP) y recuérdame dónde debo introducir mi API Key real de Firecrawl.
```

---

### B. Instalación de Skills (Herramientas Locales)

Una vez configurado el cerebro base, activa las habilidades de desarrollo en la terminal de Antigravity:

```bash
npx skills add https://github.com/jeffallan/claude-skills --skill flutter-expert
npx skills add https://github.com/madteacher/mad-agents-skills --skill flutter-animations
npx skills add https://github.com/davila7/claude-code-templates --skill mobile-design
npx claude-code-templates@latest --skill=creative-design/frontend-design --yes
npx claude-code-templates@latest --skill=development/senior-frontend --yes
npx claude-code-templates@latest --agent=development-team/mobile-app-developer --yes
npx skills add https://github.com/wshobson/agents --skill mobile-android-design
npx skills add https://github.com/wshobson/agents --skill mobile-ios-design
npx skills add google-labs-code/stitch-skills --list
```

---

## 4. Flujo de Trabajo (The Workflow)

El proceso de desarrollo sigue un pipeline estricto de 3 fases impulsado por IA:

1. **Extracción Profunda (Scraping):** Firecrawl mapea el sitio web original para capturar colores, tipografías, catálogos y logos, asegurando que no se pierda la esencia de la marca.
2. **Estructuración Visual (UX/UI):** Stitch toma los datos crudos y diseña las pantallas clave (Splash Screen, Home, Búsqueda, Carrito, Checkout) adaptadas a la experiencia móvil.
3. **Desarrollo en Flutter:** Antigravity utiliza la skill `flutter-architecture` para montar una base profesional utilizando gestores de estado modernos y enrutamiento avanzado.

---

## 5. Guía de Réplica (El Prompt Maestro)

Con tu entorno configurado, copia y pega el siguiente prompt en el chat de Antigravity para desatar la automatización.

> 💡 **Tip de Réplica:** Solo necesitas cambiar la URL de referencia al final del prompt por el e-commerce que desees clonar (por ejemplo: `https://chamelo.com/pages/innovation`).

```text
# ROL Y CONTEXTO
Eres un Agente Experto en Desarrollo Móvil (Flutter), UI/UX y Arquitectura de Software, operando dentro del entorno VS Code con la extensión Antigravity. Tienes acceso a herramientas MCP (Firecrawl, Stitch) y a las skills instaladas en este espacio de trabajo local (especialmente la skill `flutter-architecture`).

# OBJETIVO PRINCIPAL
Transformar una página web e-commerce de referencia en una aplicación móvil nativa en Flutter totalmente funcional. Debe ser estéticamente idéntica a la marca original, incluir animaciones premium y estar montada sobre una arquitectura de código profesional y escalable.

# FLUJO DE TRABAJO ESTRICTO (Ejecuta en este orden exacto):

## PASO 1: Extracción Profunda y Comprensión de Datos (Firecrawl MCP)
- Utiliza el MCP de Firecrawl para realizar un web scraping PROFUNDO Y EXHAUSTIVO de la siguiente URL: [INSERTA_TU_URL_AQUÍ]
- REGLA DE SCRAPING: No omitas absolutamente nada. Navega y extrae la estructura completa del e-commerce: catálogo de productos, descripciones, carruseles de imágenes, menús de navegación, footer, y toda la paleta de colores (HEX/RGB) y tipografías.
- Si encuentras paginaciones o enlaces internos clave del flujo de compra, extráelos también.
- Extrae el logo principal de la marca en la mejor resolución posible (preferiblemente SVG o PNG transparente).
- Si ocurre un error o bloqueo durante el scraping, implementa reintentos automáticos o busca rutas alternativas dentro del DOM hasta obtener el contexto completo.

## PASO 2: Estructuración Visual y UX Móvil (Stitch MCP)
- Toma toda la información extraída en el Paso 1 y comunícate con el MCP de Stitch.
- Instruye a Stitch para que diseñe visualmente los siguientes flujos de la app:
  1. Splash Screen (NUEVO): Una pantalla de carga inicial limpia que destaque el logo extraído.
  2. Pantalla de inicio (Home) que sea una réplica exacta y adaptada a móvil de la URL.
  3. Sistema de búsqueda dinámico e intuitivo.
  4. Lógica y UI del Carrito de compras (menú desplegable al agregar un producto y pantalla de resumen).
  5. Flujo de Checkout de múltiples fases (datos, envío, pago).
- El resultado debe ser una maqueta visual aprobada para desarrollo, sin perder ningún elemento de la web original.

## PASO 3: Arquitectura, Configuración y Desarrollo en Flutter (Skills Locales Antigravity)
- Tu primera acción en código DEBE ser invocar la skill local `flutter-architecture` (proveniente de mad-agents-skills) para generar toda la base arquitectónica del proyecto.
- Configura las dependencias base en el `pubspec.yaml` incluyendo obligatoriamente:
  - `flutter_riverpod` (Gestor de estado)
  - `go_router` (Para enrutamiento)
  - `google_fonts` (Para tipografías)
  - `cached_network_image` (Para el manejo de imágenes del catálogo)
  - `flutter_svg` (Para gráficos vectoriales)
  - `animate_do` (Para animaciones fluidas y el Splash Screen)
- Desarrollo de la UI: Comienza programando el Splash Screen. Debe tener una animación de entrada elegante y moderna (fade in, zoom in suave o rebote) utilizando el logo de la página. Tras 2-3 segundos, debe redirigir automáticamente al Home.
- Continúa con el resto de la UI respetando estrictamente la estructura generada por la skill `flutter-architecture`. El diseño debe ser "pixel-perfect" respecto a la web.

# REGLAS Y RESTRICCIONES
- ARQUITECTURA Y ESTADO: La estructura la dicta la skill `flutter-architecture`. Es OBLIGATORIO utilizar Riverpod de forma reactiva y global para el carrito, las búsquedas y el checkout.
- La aplicación debe ser 100% servible, escalable y no debe faltar ninguna sección del e-commerce original.
- Al finalizar cada paso (1 y 2), dame un brevísimo resumen de lo que lograste antes de avanzar automáticamente al siguiente paso. Nunca saltes al Paso 3 sin haber completado los dos primeros.

# URL DE REFERENCIA
https://chamelo.com/pages/innovation

¡Comienza con el Paso 1 ahora!
```

---

## 📖 Documentación

- **Repositorio de Skills:** [https://skills.sh/](https://skills.sh/)
- **Documentación Oficial Flutter:** [https://flutter.dev/](https://flutter.dev/)
