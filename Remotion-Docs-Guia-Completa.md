# 📘 Remotion Docs: Guía Maestra y Referencia Técnica Completa

> **Origen:** [Documentación Oficial Remotion.dev](https://www.remotion.dev/docs/)  
> **Categoría:** Vibe Coding / Video Programático con React, WebGL y Chromium  
> **Versión:** Remotion 4.x / Ecosistema 2026  

---

## 📑 Tabla de Contenidos
1. [Arquitectura & Determinismo](#1-arquitectura--determinismo)
2. [Instalación y Setup](#2-instalación-y-setup)
3. [Componentes Fundamentales](#3-componentes-fundamentales)
4. [Hooks Esenciales](#4-hooks-esenciales)
5. [Animaciones e Interpolación (`interpolate`)](#5-animaciones-e-interpolación-interpolate)
6. [Físicas de Resorte Orgánicas (`spring`)](#6-físicas-de-resorte-orgánicas-spring)
7. [Manejo de Assets (Audio / Video / Img)](#7-manejo-de-assets-audio--video--img)
8. [Validación de Props Dinámicas con Zod](#8-validación-de-props-dinámicas-con-zod)
9. [Remotion Player en Aplicaciones Web](#9-remotion-player-en-aplicaciones-web)
10. [Renderizado por CLI y Cloud Lambda](#10-renderizado-por-cli-y-cloud-lambda)
11. [Reglas de Oro del Vibe Coding](#11-reglas-de-oro-del-vibe-coding)

---

## 1. Arquitectura & Determinismo

Remotion no graba la pantalla. En su lugar, inicializa un navegador Chromium headless, evalúa tu árbol de componentes React fotograma a fotograma de forma determinista, toma capturas de cada frame individual y las une mediante **FFmpeg** en un contenedor MP4, WebM, ProRes o GIF.

> 🧠 **Principio de Determinismo:** Dado un número de fotograma `frame = N` y unas `props`, la función React **debe renderizar exactamente la misma vista visual** en cualquier máquina o servidor. No uses funciones no deterministas como `Math.random()` sin semilla o `Date.now()`.

---

## 2. Instalación y Setup

```bash
# 1. Crear nuevo proyecto Remotion (en blanco o con Tailwind)
npx create-video@latest --yes --blank mi-video-remotion

# 2. Navegar a la carpeta
cd mi-video-remotion

# 3. Instalar habilidades de IA para Remotion (Skills de Anthropic/OpenAI/Gemini)
npx -y skills@latest add remotion-dev/skills -g -y

# 4. Iniciar Remotion Preview Studio en el navegador (http://localhost:3000)
npm run dev
```

---

## 3. Componentes Fundamentales

| Componente | Paquete | Función y Uso |
| :--- | :--- | :--- |
| `<Composition />` | `remotion` | Declara la composición raíz. Define dimensiones (`width`, `height`), tasa de cuadros (`fps`), duración (`durationInFrames`), componente y `defaultProps`. |
| `<Sequence />` | `remotion` | Desplaza el tiempo de inicio (`from`) y delimita la duración (`durationInFrames`). Los componentes hijos reciben `useCurrentFrame()` reiniciado desde 0. |
| `<Series />` | `remotion` | Permite encadenar secuencias consecutivas automáticamente sin calcular manualmente el parámetro `from` de cada una. |
| `<Loop />` | `remotion` | Repite en bucle un fragmento de video o animación durante una duración determinada. |
| `<Freeze />` | `remotion` | Congela la animación en un fotograma específico (`frame={N}`). |
| `<AbsoluteFill />` | `remotion` | Contenedor `div` con estilos absolutos para ocupar el 100% del viewport del video (`position: absolute, top: 0, left: 0, width: 100%, height: 100%`). |
| `<OffthreadVideo />` | `remotion` | Decodifica clips de video pesados en hilos separados evitando cuellos de botella en el hilo principal del DOM. |

### Ejemplo: Secuencias Encadenadas con `Series`
```tsx
import { Series, AbsoluteFill } from 'remotion';
import { IntroScene } from './IntroScene';
import { MainDemo } from './MainDemo';
import { OutroCTA } from './OutroCTA';

export const MasterTimeline = () => {
  return (
    <AbsoluteFill style={{ backgroundColor: '#090d16' }}>
      <Series>
        {/* Escena 1: 0s a 3s (90 frames a 30fps) */}
        <Series.Sequence durationInFrames={90}>
          <IntroScene />
        </Series.Sequence>

        {/* Escena 2: 3s a 8s (150 frames a 30fps) */}
        <Series.Sequence durationInFrames={150}>
          <MainDemo />
        </Series.Sequence>

        {/* Escena 3: 8s a 10s (60 frames a 30fps) */}
        <Series.Sequence durationInFrames={60}>
          <OutroCTA />
        </Series.Sequence>
      </Series>
    </AbsoluteFill>
  );
};
```

---

## 4. Hooks Esenciales

| Hook | Retorno | Uso Típico |
| :--- | :--- | :--- |
| `useCurrentFrame()` | `number` | El fotograma relativo actual dentro de la secuencia activa (0, 1, 2, ...). |
| `useVideoConfig()` | `{ fps, durationInFrames, width, height, id }` | Metadatos globales del video para calcular duraciones en segundos y escalas. |
| `delayRender()` / `continueRender()` | `handle / callback` | Pausa la captura de fotogramas hasta que fuentes web, modelos 3D o peticiones de API se hayan descargado por completo. |
| `random(seed)` | `number (0 a 1)` | Generador pseudo-aleatorio determinista. Siempre produce el mismo valor para una semilla dada. |

### Carga Asíncrona Determinista con `delayRender`
```tsx
import { useEffect, useState } from 'react';
import { delayRender, continueRender, AbsoluteFill } from 'remotion';

export const AsyncDataScene = () => {
  const [data, setData] = useState<string | null>(null);
  const [handle] = useState(() => delayRender('Cargando datos de API...'));

  useEffect(() => {
    fetch('https://api.ejemplo.com/stats')
      .then((res) => res.json())
      .then((json) => {
        setData(json.metric);
        continueRender(handle); // Desbloquea el renderizado del frame
      })
      .catch((err) => {
        console.error(err);
        continueRender(handle);
      });
  }, [handle]);

  if (!data) return null;

  return (
    <AbsoluteFill>
      <h1>Métrica en Vivo: {data}</h1>
    </AbsoluteFill>
  );
};
```

---

## 5. Animaciones e Interpolación (`interpolate`)

```tsx
import { useCurrentFrame, interpolate, Easing } from 'remotion';

export const SmoothCard = () => {
  const frame = useCurrentFrame();

  // Opacidad de 0 a 1 entre el frame 0 y 20
  const opacity = interpolate(frame, [0, 20], [0, 1], {
    extrapolateRight: 'clamp',
    extrapolateLeft: 'clamp'
  });

  // Traslación vertical con curva Bézier suave
  const translateY = interpolate(frame, [0, 30], [100, 0], {
    easing: Easing.bezier(0.16, 1, 0.3, 1),
    extrapolateRight: 'clamp'
  });

  return (
    <div style={{ opacity, transform: `translateY(${translateY}px)` }}>
      <h2>Tarjeta Animada Suave</h2>
    </div>
  );
};
```

---

## 6. Físicas de Resorte Orgánicas (`spring`)

```tsx
import { useCurrentFrame, useVideoConfig, spring, AbsoluteFill } from 'remotion';

export const SpringBadge = () => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();

  // Entrada con rebote orgánico (escala 0 -> 1)
  const scale = spring({
    frame,
    fps,
    config: {
      damping: 10,   // Menor damping = más rebote
      mass: 0.6,     // Masa del objeto
      stiffness: 120 // Rigidez del resorte
    }
  });

  return (
    <AbsoluteFill style={{ justifyContent: 'center', alignItems: 'center' }}>
      <div style={{
        transform: `scale(${scale})`,
        padding: '2rem 4rem',
        background: 'linear-gradient(135deg, #0ea5e9, #c084fc)',
        borderRadius: 24,
        color: '#ffffff',
        fontSize: 48,
        fontWeight: 800,
        boxShadow: '0 20px 50px rgba(14, 165, 233, 0.4)'
      }}>
        ¡Lanzamiento 2026! 🚀
      </div>
    </AbsoluteFill>
  );
};
```

---

## 7. Manejo de Assets (Audio / Video / Img)

```tsx
import { Img, Audio, Video, staticFile, AbsoluteFill, Sequence, interpolate } from 'remotion';

export const MediaComp = () => {
  return (
    <AbsoluteFill style={{ backgroundColor: '#000000' }}>
      {/* Pista de Audio con Fade-Out */}
      <Audio
        src={staticFile('soundtrack.mp3')}
        volume={(f) => interpolate(f, [0, 30, 270, 300], [0, 0.8, 0.8, 0], { extrapolateRight: 'clamp' })}
      />

      {/* Imagen de fondo */}
      <Img src={staticFile('background.webp')} style={{ width: '100%', height: '100%', objectFit: 'cover' }} />

      {/* Video superpuesto a partir del segundo 2 */}
      <Sequence from={60}>
        <Video src={staticFile('screen_record.mp4')} style={{ width: 1280, height: 720, borderRadius: 20 }} />
      </Sequence>
    </AbsoluteFill>
  );
};
```

---

## 8. Validación de Props Dinámicas con Zod

```tsx
import { Composition } from 'remotion';
import { z } from 'zod';
import { DynamicAd } from './DynamicAd';

export const dynamicSchema = z.object({
  title: z.string(),
  price: z.number(),
  themeColor: z.string().default('#0ea5e9'),
  showBadge: z.boolean().default(true),
});

export const Root = () => {
  return (
    <Composition
      id="DynamicAdComp"
      component={DynamicAd}
      schema={dynamicSchema}
      fps={30}
      width={1080}
      height={1920} // Vertical 9:16
      durationInFrames={180}
      defaultProps={{
        title: "Pack Smartwatch Pro",
        price: 199.99,
        themeColor: "#0ea5e9",
        showBadge: true
      }}
      calculateMetadata={async ({ props }) => {
        const calculatedFrames = props.title.length > 25 ? 240 : 180;
        return {
          durationInFrames: calculatedFrames,
          props: { ...props }
        };
      }}
    />
  );
};
```

---

## 9. Remotion Player en Aplicaciones Web

```tsx
import { Player } from '@remotion/player';
import { MainVideo } from '@/remotion/MainVideo';

export default function VideoPreviewPage() {
  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '2rem' }}>
      <h1>Vista Previa Interactiva</h1>
      <Player
        component={MainVideo}
        durationInFrames={300}
        fps={30}
        compositionWidth={1920}
        compositionHeight={1080}
        style={{ width: '100%', borderRadius: '16px', overflow: 'hidden' }}
        controls
        autoPlay
        loop
        inputProps={{
          titulo: "Video en Vivo desde Web App",
          colorAcento: "#38bdf8"
        }}
      />
    </div>
  );
}
```

---

## 10. Renderizado por CLI y Cloud Lambda

```bash
# 1. Render estándar a MP4 (Full HD, 30fps)
npx remotion render src/index.ts MiVideoPromocional out/video.mp4

# 2. Render pasando JSON de Props dinámicas
npx remotion render src/index.ts DynamicAdComp out/ad-rebajas.mp4 --props='{"title":"Rebajas de Verano","price":89.99,"themeColor":"#f43f5e"}'

# 3. Render con fondo transparente (ProRes 4444 para After Effects / Final Cut)
npx remotion render src/index.ts AlphaOverlay out/overlay.mov --codec=prores --prores-profile=4444

# 4. Render con aceleración GPU (SwiftShader / ANGLE para WebGL / Three.js)
npx remotion render src/index.ts ThreeDScene out/3d.mp4 --gl=angle

# 5. Render en la nube a velocidad hiper-rápida con AWS Lambda (100x más rápido)
npx remotion lambda render <function-name> <serve-url> MiVideoPromocional
```

---

## 11. Reglas de Oro del Vibe Coding

1. **No uses `Date.now()` ni `Math.random()`:** Remotion necesita reproducibilidad frame a frame. Usa `random(seed)` de `remotion`.
2. **Usa `staticFile()` para assets:** Coloca los archivos en `public/` y usa `staticFile('nombre.ext')`.
3. **Envuélvelo en `delayRender()`:** Si cargas fuentes de Google Fonts, modelos 3D o datos asíncronos, frena la captura hasta completar la carga.
4. **Prefiere `spring()` sobre `ease-in-out`:** Las físicas de resorte aportan dinamismo natural e inercia a cualquier interfaz o banner.

---

## 📚 Enlaces Oficiales
- **Remotion Docs:** [https://www.remotion.dev/docs/](https://www.remotion.dev/docs/)
- **Remotion Prompts Showcase:** [https://www.remotion.dev/prompts](https://www.remotion.dev/prompts)
