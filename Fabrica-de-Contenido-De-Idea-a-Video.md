# 🎬 Tu Fábrica de Contenido: De Idea a Video sin Editar

> **Enlace Original Notion:** [Ver en Notion (Duplicar en tu Workspace)](https://app.notion.com/p/Tu-F-brica-de-Contenido-De-Idea-a-Video-sin-Editar-3032cd2e5d1580218079f6fec88452a4)
> **Categoría:** Vibe Coding / Video Programático con Remotion & Antigravity

---

# 🚀 Fase 1: Configuración del Entorno (El Setup)

Antes de crear magia, necesitamos preparar el taller. Sigue estos pasos para conectar el cerebro (Antigravity) con los músculos (Remotion).

### 1. Instalar Antigravity (El Cerebro)
- **Opción A: Visual (Mac/Windows):** Ve a [https://antigravity.google/](https://antigravity.google/) y descarga el instalador.
- **Opción B: Vía Terminal (Linux/WSL):** `sudo apt install antigravity -y`

---

### 2. Preparar el Motor de Video (Remotion)
```bash
# 1. Crear proyecto base
npx create-video@latest

# 2. Entrar a la carpeta
cd mi-video-ia
```

---

### 3. Instalar las "Skills" (Los Superpoderes)

Ejecuta estos 4 comandos en la terminal de Antigravity:

```bash
# A. La Madre de las Skills (Contexto General)
npx skills add https://github.com/vercel-labs/skills --skill find-skills

# B. El Manual de Instrucciones (Best Practices)
npx skills add https://github.com/remotion-dev/skills --skill remotion-best-practices

# C. El Arquitecto (Stitch Skills de Google)
npx skills add https://github.com/google-labs-code/stitch-skills --skill remotion

# D. El Animador (Startup OS)
npx skills add https://github.com/ncklrs/startup-os-skills --skill remotion-animation
```

---

# 🎬 Método 1: De URL a Video (Landing Page)

### El Prompt Maestro 🧠
*Copia y pega este prompt en Antigravity reemplazando `[TU_URL_AQUI]`:*

```text
Actúa como un Experto en Producción de Video y Desarrollador Senior de React/Remotion.

TU OBJETIVO:
Analizar el contenido visual y textual de la siguiente URL: [TU_URL_AQUI] y generar un código completo de Remotion para un video promocional de 15 segundos.

INSTRUCCIONES TÉCNICAS:
1. Usa las skills instaladas (@remotion/player y startup-os-skills) para crear animaciones fluidas.
2. Extrae los "H1", "H2" y los colores principales de la web para mantener la identidad de marca.
3. Estructura el video en 3 escenas:
   - Escena 1 (0-5s): Gancho visual con el problema o título principal.
   - Escena 2 (5-10s): Explicación de valor o demostración del producto.
   - Escena 3 (10-15s): Call to Action (CTA) claro y grande.
4. El código debe ser un componente funcional de React listo para renderizar.

SALIDA ESPERADA:
Entrégame únicamente el código .tsx optimizado.
```

---

# 🖼️ Opción 2: De Imagen Estática a Video Dinámico

### Paso 1: Prepara tu Imagen
Pega tu imagen en la carpeta `public/promo.png` dentro de tu proyecto.

### Paso 2: El Prompt de Animación
```text
ROL: Experto en Motion Graphics y Remotion.

TAREA:
Tengo una imagen llamada "promo.png" en la carpeta public/.
Quiero crear un video de 10 segundos que anime esta imagen estática.

REQUERIMIENTOS DE ANIMACIÓN:
1. Fondo: Usa la imagen "promo.png" con un efecto "Ken Burns" (un zoom lento y sutil hacia adentro) para darle dinamismo.
2. Superposición: Agrega un texto grande y moderno que diga "OFERTA LIMITADA" que aparezca con una animación de rebote (spring) en el segundo 2.
3. Estilo: Usa la skill `remotion-animation` para que las transiciones sean suaves.
4. Salida: Genera el componente <Composition /> completo en React.

IMPORTANTE:
Usa el componente <Img /> de Remotion y asegúrate de importar `staticFile` si es necesario para la ruta.
```

---

# 🧠 Opción 3: Modo Director (De una Idea a Video)

```text
ROL: Director Creativo y Desarrollador Senior de Remotion.

TAREA:
Crea un video tipográfico y geométrico de 15 segundos sobre: [TU IDEA AQUÍ, EJ: "Los beneficios de beber agua"].

GUION Y ESTRUCTURA (Tú decides el copy):
1. Intro (0-3s): Título impactante con colores vibrantes.
2. Desarrollo (3-12s): Muestra 3 puntos clave usando listas animadas o iconos simples (puedes usar lucide-react si está disponible o formas geométricas básicas).
3. Cierre (12-15s): Un llamado a la acción claro.

DETALLES TÉCNICOS:
- No uses imágenes externas, todo debe ser generado con CSS, formas (divs, svg) y tipografía.
- Usa una paleta de colores moderna (ej: gradientes o colores pastel).
- La animación debe ser muy dinámica, con mucho ritmo.

SALIDA:
Código completo en .tsx listo para pegar en `src/Composition.tsx`.
```

---

### 🎥 Renderizar en MP4
```bash
npx remotion render
```
*El video final se guardará en la carpeta `out/`.*

---

## 🧰 Recursos y Referencias
- **Antigravity Google:** [https://antigravity.google/](https://antigravity.google/)
- **Remotion Docs:** [https://www.remotion.dev/docs/](https://www.remotion.dev/docs/)
- **Skills Repository:** [https://skills.sh/?q=remotion](https://skills.sh/?q=remotion)
- **Iconos Lucide:** [https://lucide.dev/](https://lucide.dev/)
