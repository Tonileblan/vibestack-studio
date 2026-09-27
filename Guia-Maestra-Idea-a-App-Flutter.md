# 🚀 Guía Maestra: De Idea Conceptual a App Nativa Flutter (Plantilla "Desde Cero")

> **Enlace Original Notion:** [Ver en Notion (Duplicar en tu Workspace)](https://app.notion.com/p/Gu-a-Maestra-De-Idea-Conceptual-a-App-Nativa-Flutter-Plantilla-Desde-Cero-30a2cd2e5d158050aad9f01e0d7276cd)
> **Categoría:** Vibe Coding / Plantillas de Proyectos IA

---


## 1. Ficha Técnica del Proyecto

| **Elemento** | **Descripción** |
| :--- | :--- |
| **Nombre del Proyecto** | Orquestación Móvil: E-Commerce a Flutter |
| **Stack Tecnológico** | Antigravity, Stitch, Firecrawl, Dart/Flutter |
| **Objetivo Principal** | Transformar tu idea en una aplicación movil  |
| **Requisito Único** | Antigravity instalado  |


## 2. Arquitectura (El Cerebro Digital)

Este proyecto se integra en el ecosistema general replicando el ciclo de trabajo de un equipo de desarrollo completo dentro de una sola estación de trabajo. A partir de una idea abstracta o conceptual, utilizamos múltiples "Cerebros" conectados en secuencia para ejecutar la visión:

- Gestión de Producto y Análisis (Agente IA): Actúa como el Product Manager (PM) del proyecto. Su función es interpretar la idea original, estructurar los requerimientos, definir las historias de usuario y trazar el mapa de navegación lógico antes de tocar un solo píxel de diseño.
- Dirección Creativa y UX/UI (Stitch MCP): Funciona como tu Lead Designer personal. Toma los requerimientos estructurados por el PM y propone la identidad de marca desde cero (paletas de colores, tipografías, "vibra" estética) para luego maquetar la interfaz móvil completa sin depender de URLs o referencias externas.
- Ingeniería Ágil (Antigravity + Skills Locales): Ejecuta la construcción del software. Inyecta estándares profesionales al instante invocando la skill flutter-architecture y conecta el diseño estratégico con la escritura de código nativo limpio, modular y escalable (usando Riverpod para el estado).

## 3. Configuración Técnica (Orquestación)

Para que Antigravity pueda "hablar" con estas tecnologías, necesitamos configurar los puentes (Servidores MCP) y dotar al agente de las herramientas correctas.


## PASO 0: Auditoría del Entorno (Agente como Soporte Técnico)

Copia todo este promt: 

```javascript
- Antes de analizar la idea, debes garantizar que la computadora del usuario esté lista para compilar aplicaciones móviles.
- Ejecuta comandos de lectura en la terminal para comprobar la existencia de las siguientes 3 herramientas vitales:
1. Flutter SDK: Ejecuta flutter --version
2. JDK 17 (Java): Ejecuta java -version (Asegúrate de que la versión detectada corresponda a la 17).
3. Android SDK: Ejecuta flutter doctor para comprobar el estado de las herramientas de Android.

- Si falta alguna herramienta (Instalación Proactiva): NO te detengas. Tu objetivo es resolverlo de forma autónoma. Sigue estos pasos estrictamente:
1. Ejecuta un comando para identificar el sistema operativo del usuario (Windows, macOS o Linux).
2. Busca e implementa los comandos de terminal necesarios para instalar la herramienta faltante de forma silenciosa o desatendida. (Usa gestores de paquetes nativos como winget o choco para Windows, brew para macOS, o apt para Linux).
3. Para el Android SDK, si se requieren aceptar licencias, ejecuta automáticamente: yes | flutter doctor --android-licenses (o el equivalente en el sistema operativo detectado).
4. Una vez que el comando de instalación termine, vuelve a ejecutar la comprobación (Paso 2) para confirmar el éxito de la operación.

- Si la instalación automática requiere permisos (Sudo/Admin) o falla: Solo en este escenario, detente y comunícate con el usuario de forma muy amigable y sin jerga técnica. Explícale que intentaste instalar los "motores" para la app pero necesitas su autorización. Entrégale el comando exacto que debe pegar en su terminal para completar la instalación.

- Si todo está instalado y configurado correctamente: Confírmale al usuario de forma entusiasta que su sistema está en perfectas condiciones y avanza automáticamente al Paso 1.
```


### A. Configuración de Servidores MCP (`mcp_config.json`)

Debes inyectar estos tres servidores en tu archivo `mcp_config.json` (ubicado en tu AppData o configuración global). Copia el siguiente promt

```javascript
Actúa como un Especialista en Integraciones de mi entorno VS Code. Necesito que actualices mi configuración de servidores MCP de forma autónoma siguiendo estos 4 pasos exactos:

1. Localiza mi archivo de configuración de servidores MCP (generalmente `mcp_config.json` o `claude_desktop_config.json` ubicado en mi AppData o en la carpeta de configuración global).

2. Inyecta exactamente las siguientes configuraciones dentro del objeto `"mcpServers"`. Asegúrate de mantener la sintaxis JSON válida y no sobrescribir mis configuraciones previas:

{
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
`dart pub global activate dart_mcp_server`

Confírmame cuando hayas terminado, avísame si necesito reiniciar el editor (o darle al botón Refresh de MCP) y recuérdame dónde debo introducir mi API Key real de Firecrawl.
```


### B. Instalación de Skills (Herramientas Locales)

Una vez configurado el cerebro base, activa las habilidades de desarrollo en la terminal de Antigravity:

Bash

`npx skills add https://github.com/jeffallan/claude-skills --skill flutter-expert
npx skills add https://github.com/madteacher/mad-agents-skills --skill flutter-animations
npx skills add https://github.com/davila7/claude-code-templates --skill mobile-design
npx claude-code-templates@latest --skill=creative-design/frontend-design --yes
npx claude-code-templates@latest --skill=development/senior-frontend --yes
npx claude-code-templates@latest --agent=development-team/mobile-app-developer --yes
npx skills add https://github.com/wshobson/agents --skill mobile-android-design
npx skills add https://github.com/wshobson/agents --skill mobile-ios-design
npx skills add google-labs-code/stitch-skills --list`


## 4. Flujo de Trabajo (The Workflow)

El proceso de desarrollo sigue un pipeline estricto de 3 fases impulsado por IA:

1. **Estructuración Visual (UX/UI):** Stitch toma los datos crudos y diseña las pantallas clave (Splash Screen, Home, Búsqueda, Carrito, Checkout) adaptadas a la experiencia móvil.
1. **Desarrollo en Flutter:** Antigravity utiliza la skill `flutter-architecture` para montar una base profesional utilizando gestores de estado modernos y enrutamiento avanzado.

## 5. Guía de Réplica (El Prompt Maestro)

```javascript
# ROL Y CONTEXTO
Eres un Agente Experto en Desarrollo de Producto Digital, UI/UX y Arquitectura de Software Móvil (Flutter), operando dentro del entorno VS Code con la extensión Antigravity. Tienes acceso a la herramienta MCP de Stitch y a las skills instaladas en este espacio de trabajo local (especialmente la skill `flutter-architecture`).

# OBJETIVO PRINCIPAL
Materializar una idea conceptual descrita por el usuario en una aplicación móvil nativa en Flutter totalmente funcional. Debes interpretar los requerimientos abstractos, proponer una identidad visual acorde a la "vibra" deseada, diseñar la experiencia de usuario y construirla sobre una arquitectura de código profesional y escalable.

# INPUTS DEL PROYECTO (Idea Conceptual)
- NOMBRE DEL PROYECTO (Tentativo): [INSERTA_NOMBRE_DEL_PROYECTO]
- DESCRIPCIÓN GENERAL DE LA IDEA: [DESCRIBE_AQUI_TU_IDEA_CON_DETALLE. ¿Qué problema resuelve? ¿Qué hace la app?]
- PÚBLICO OBJETIVO: [EJ: Jóvenes profesionales entre 25-35 años, interesados en finanzas personales]
- FUNCIONALIDADES CLAVE (Listar 3-5):
  1. [FUNCIONALIDAD_1]
  2. [FUNCIONALIDAD_2]
  3. [FUNCIONALIDAD_3]
  ...
- VIBRA ESTÉTICA DESEADA: [EJ: Minimalista, oscuro y serio / Colorido, juguetón y amigable / Corporativo y confiable]

# FLUJO DE TRABAJO ESTRICTO (Ejecuta en este orden exacto):

## PASO 1: Análisis de Requerimientos y Síntesis de Producto (Agente como PM)
- Analiza profundamente los INPUTS DEL PROYECTO proporcionados arriba.
- Actúa como un Product Manager experimentado. Tu objetivo es estructurar la abstracción.
- Define y lista formalmente:
  1. Las historias de usuario principales basadas en las funcionalidades clave.
  2. Un mapa de navegación propuesto (qué pantallas son necesarias).
- **IMPORTANTE:** Al final de este paso, preséntame un resumen estructurado de lo que entendiste que vamos a construir para mi aprobación antes de pasar al diseño.

## PASO 2: Creación de Identidad Visual y UX Móvil (Stitch MCP)
- Una vez aprobados los requerimientos del Paso 1, comunícate con el MCP de Stitch.
- Como no tenemos una URL de referencia, instruye a Stitch para que PROPONGA una identidad visual basada en la "VIBRA ESTÉTICA DESEADA":
  - Definir una paleta de colores (Primario, Secundario, Fondo, Texto) con códigos HEX.
  - Sugerir tipografías modernas y legibles (Google Fonts) acordes al tono.
- Diseña visualmente los flujos de la app definidos en el mapa de navegación, incluyendo:
  1. **Splash Screen:** Diseño limpio con el nombre del proyecto y la paleta de colores propuesta.
  2. **Pantallas Principales:** Wireframes de alta fidelidad para las funcionalidades clave listadas en los inputs.
- El resultado debe ser una propuesta visual coherente y una maqueta de UX aprobada para desarrollo.

## PASO 3: Arquitectura, Configuración y Desarrollo en Flutter (Skills Locales Antigravity)
- Tu primera acción en código DEBE ser invocar la skill local `flutter-architecture` para generar toda la base arquitectónica del proyecto.
- Configura las dependencias base en el `pubspec.yaml` incluyendo obligatoriamente:
  - `flutter_riverpod` (Gestor de estado principal)
  - `go_router` (Para enrutamiento)
  - `google_fonts` (Para implementar las tipografías propuestas)
  - `flutter_svg` (Para iconos)
  - `animate_do` (Para animaciones fluidas y el Splash Screen)
- **Desarrollo de la UI:** Comienza programando el Splash Screen con la identidad visual definida. Continúa con el resto de la UI respetando estrictamente la estructura generada por la skill de arquitectura y los diseños de Stitch.

# REGLAS Y RESTRICCIONES
- **ARQUITECTURA Y ESTADO:** La estructura la dicta la skill `flutter-architecture`. Es OBLIGATORIO utilizar **Riverpod** de forma reactiva y global para manejar la lógica de negocio y los estados de la aplicación.
- **SIN REFERENCIA VISUAL:** Debes ser creativo pero profesional al proponer la estética en el Paso 2, siempre alineado a la "Vibra Estética Deseada" descrita por el usuario.
- La aplicación debe ser 100% servible y escalable, lista para ser iterada.
- **PAUSAS OBLIGATORIAS:** Al finalizar el Paso 1 (Análisis) y el Paso 2 (Diseño), preséntame el resultado y ESPERA mi confirmación explícita antes de avanzar al siguiente paso. No escribas código hasta que el diseño esté aprobado.

¡Comienza con el Paso 1: Analiza la idea y preséntame la estructura del producto!
```

**📖 Documentación**

Link de skil: [https://skills.sh/](https://skills.sh/)
Link de documentación flutter: [https://flutter.dev/](https://flutter.dev/)

