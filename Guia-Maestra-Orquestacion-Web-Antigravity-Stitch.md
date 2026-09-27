# 📘 Guía Maestra: Orquestación Web con Antigravity + Stitch

> **Enlace Original Notion:** [Ver en Notion (Duplicar en tu Workspace)](https://app.notion.com/p/Gu-a-Maestra-Orquestaci-n-Web-con-Antigravity-Stitch-30a2cd2e5d1580d5bdb4ef263609adfc)
> **Categoría:** Vibe Coding / Orquestación Web con Antigravity & Stitch

---

¿Tienes una web que funciona pero se siente atrapada en el pasado? No necesitas tirarla a la basura y empezar de cero. Esta guía es tu "túnel de lavado" con Inteligencia Artificial.

Vamos a tomar tus archivos actuales (HTML, CSS o JS) y, mediante la orquestación de **Antigravity** y el motor de diseño **Stitch**, los transformaremos en una aplicación **React moderna**. Mantendremos tu contenido y tu esencia, pero elevaremos la estética a un nivel **High-End** (estilo Apple VisionOS), añadiendo animaciones fluidas y una arquitectura lista para el futuro.

---

## 1. Preparación de Archivos (Antes de abrir el Agente)

> ⚠️ **Advertencia:** Antigravity no puede adivinar tu contenido. Necesitas darle el código fuente.

**Si no tienes el archivo `index.html` a la mano:**

1. Ve a tu sitio web actual.
2. Presiona `CTRL + U` (o clic derecho > Ver código fuente).
3. Copia todo ese código.
4. Ve a [CodeBeautify HTML Viewer](https://codebeautify.org/htmlviewer).
5. Pega el código a la izquierda y dale al botón "Beautify" (esto lo limpia y ordena).
6. Copia el resultado limpio y guárdalo en tu carpeta del proyecto como `inicio.html`.

**Estructura Obligatoria de tu Carpeta:**
```text
/mi-rediseño-web
├── inicio.html       <-- El código que sacaste de CodeBeautify
├── css/              <-- (Opcional) Tus estilos viejos
└── assets/
    ├── logo.png      <-- Tu logo (¡Importante!)
    └── video.mp4     <-- (Opcional)
```

---

## 🧱 Paso 0: Conexión del MCP (Cerebro Base)

*Copia y pega esto en el chat de Antigravity:*

```text
Hola Antigravity. Vamos a iniciar el rediseño, pero primero necesitamos conectar el "Cerebro".

Por favor, realiza la instalación del Servidor MCP (Model Context Protocol) de Stitch.

Ejecuta el siguiente comando para inicializar el servidor base:
npx -y @_davideast/stitch-mcp init

(Nota: Si este comando específico requiere confirmación o descarga de paquetes adicionales, acéptalos automáticamente).

Una vez el servidor MCP esté instalado y escuchando, responde únicamente: "Servidor Stitch Conectado. Dame las Skills".
```

---

## 🔴 Paso 1: Instalación del Cerebro (MCP Stitch)

```text
Necesito activar el modo Diseñador. Por favor, instala el servidor MCP de Stitch y sus skills ejecutando estos comandos exactos:

// 1. Instalar el MCP Core y Skills de Diseño
npx skills add google-labs-code/stitch-skills --skill design-md --global
npx skills add google-labs-code/stitch-skills --skill react:components --global
npx skills add google-labs-code/stitch-skills --skill stitch-loop --global
npx skills add google-labs-code/stitch-skills --skill enhance-prompt --global
npx skills add google-labs-code/stitch-skills --skill remotion --global
npx skills add google-labs-code/stitch-skills --skill shadcn-ui --global

// 2. Instalar Templates de Arquitectura (Superpoderes)
npx claude-code-templates@latest --skill=development/senior-frontend --yes
npx claude-code-templates@latest --skill=web-development/react-best-practices --yes
npx claude-code-templates@latest --skill=creative-design/ui-design-system --yes
npx skills add https://github.com/wshobson/agents --skill responsive-design

Avísame única y exclusivamente cuando hayas terminado de instalar todo diciendo: "MCP y Skills activos. Dame el Paso 1".
```

---

## 🟡 Paso 1 (Bis): Análisis de Archivos Legados

```text
Vamos a modernizar este sitio web. Tengo los archivos fuente listos en el directorio.

1.  **Lectura de Fuente:**
    Lee el archivo `inicio.html` (que ya está formateado y limpio). Extrae:
    - Todos los textos comerciales.
    - La estructura del menú actual.
    - La jerarquía de las secciones.

2.  **Identificación de Assets:**
    Busca en la carpeta `/assets` el archivo del logo. Confirma su ruta.

3.  **Orden de Diseño a Stitch:**
    Usa tu skill `stitch-loop` para generar una propuesta de diseño.
    Prompt para Stitch: "Genera un SITIO WEB MODERNO en React tomando el contenido de `inicio.html`.
    
    Estilo Visual:
    - Fondo Oscuro Elegante: #431844
    - Acentos Vibrantes: #7D255B y #965972
    - Texto y Claridad: #E6DEE4 y #FEFEFE
    
    Objetivo: Transformar una web antigua HTML en una App React interactiva."

Cuando Stitch haya generado la estructura base en React con los textos de mi HTML, responde: "Análisis completado y Diseño base listo. Terminé el Paso 1".
```

---

## 🟢 Paso 2: Arquitectura "Liquid Glass"

```text
El diseño base es funcional, pero quiero que se vea Premium.

1.  **Navegación Liquid Glass:**
    Reemplaza el menú estándar por uno flotante.
    - Debe tener `backdrop-filter: blur(xl)`.
    - Fondo semitransparente (#E6DEE4 con opacidad 0.1).
    - Bordes redondeados sutiles.
    - **Importante:** Coloca mi logo (desde `/assets`) en la izquierda del menú.

2.  **Layout React:**
    Organiza el contenido que extrajiste del HTML en componentes modernos:
    - `<HeroSection />` con un título grande.
    - `<ServicesGrid />` para la lista de servicios.
    - `<Footer />` con los datos de contacto del HTML original.

Cuando tengas el menú flotante con mi logo y el contenido organizado, responde: "Estructura Premium lista. Terminé el Paso 2".
```

---

## 🔵 Paso 3: Animaciones y Movimiento

```text
La estructura está bien, pero está estática. Vamos a darle vida con `creative-design`.

1.  **Efectos Interactivos (ReactBits):**
    - Haz que los botones brillen o se eleven al pasar el mouse (Hover effects).
    - Haz que las tarjetas de servicios tengan un borde luminoso sutil.

2.  **Fondos Dinámicos:**
    En las secciones que tienen los colores #7D255B o #965972, no uses un color plano. Usa `SimpleParallax` o un gradiente animado suave para dar profundidad.

3.  **Transiciones:**
    Asegúrate de que al hacer scroll, los textos aparezcan suavemente (Fade In).

Cuando la web tenga movimiento fluido, responde: "Animaciones integradas. Terminé el Paso 3".
```

---

## 🟣 Paso 4: Video Programático (Remotion) y Cierre

```text
Paso Final.

1.  **Video Programático (Remotion):**
    Usa el skill `remotion` para crear un video corto de presentación usando los textos principales de mi `inicio.html`.
    Intégralo en la página de inicio.

2.  **Revisión Final:**
    - Confirma que el logo se ve bien.
    - Confirma que no quedó código HTML viejo sin traducir a React.
    - Verifica los colores: #431844, #7D255B, #FEFEFE.

Si todo está listo, confirma: "Rediseño Finalizado con Éxito".
```

---

## 🛡️ Paso 5: Auditoría de Calidad (SEO y Seguridad)

```text
El diseño y el video están espectaculares. Ahora vamos a aplicar ingeniería de calidad.

Primero, instala estas skills de auditoría especializada:
1. npx skills add https://github.com/coreyhaines31/marketingskills --skill seo-audit
2. npx claude-code-templates@latest --skill=security/top-web-vulnerabilities --yes

Una vez instaladas, ejecuta las siguientes tareas de optimización sobre el código actual:

1.  **Auditoría SEO (`seo-audit`):**
    - Revisa la estructura semántica (H1, H2, H3).
    - Asegúrate de que todas las imágenes tengan atributos `alt`.
    - Genera las metaetiquetas (Title, Description) optimizadas para el nombre de mi marca y mis servicios.
    - Crea un archivo `sitemap.xml` y `robots.txt` básicos.

2.  **Blindaje de Seguridad (`security/top-web-vulnerabilities`):**
    - Analiza los componentes de React en busca de vulnerabilidades comunes (XSS, inyecciones).
    - Asegúrate de que `dangerouslySetInnerHTML` no se esté usando de forma insegura.
    - Verifica que las dependencias externas sean seguras.

Si encuentras errores críticos, corrígelos automáticamente.
Cuando el código esté limpio, seguro y optimizado para buscadores, responde: "Sitio Blindado y Optimizado para Google. Terminé el Paso 5".
```

---

## 🛠️ Herramientas y Recursos Recomendados

- **Limpieza de Código:** [CodeBeautify HTML Viewer](https://codebeautify.org/htmlviewer)
- **Cerebro de Diseño:** [Google Stitch](https://stitch.withgoogle.com/)
- **Micro-interacciones:** [React Bits](https://reactbits.dev/)
- **Componentes Animados:** [Animate UI](https://animate-ui.com/)
- **Fondos con Movimiento:** [Simple Parallax](https://simpleparallax.com/)
- **Video con Código:** [Remotion](https://www.remotion.dev/)
- **Ejemplo Web en Producción:** [Solutech IA](https://solutech-ia.vercel.app/)
