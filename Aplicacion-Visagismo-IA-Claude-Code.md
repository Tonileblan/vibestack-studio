# 💇 Así Construí una Aplicación de Visagismo con IA (Claude Code)

> **Autor:** Ángel Aparicio (Vibe Coding / IA Masters Automations)  
> **Duración Masterclass:** 6:25 min  
> **Píldora de Negocio Asociada:** [Visagismo con IA: De una idea a un servicio](https://www.skool.com/ia-masters-automations/visagismo-con-ia-de-una-idea-a-un-servicio?utm_campaign=skool_link_classroom&utm_content=ed2b5d2f6d9c484a9eb75863cf1238d7)  
> **Motor de Construcción:** Claude Code + Vibe Coding  

---

## 🎯 Objetivo de la Clase

Aprender el proceso completo para pasar de una **idea conceptual de servicio estético** a un **prototipo funcional demostrable (MVP)** de una aplicación web de **Visagismo y Asesoría de Imagen con IA**, estructurando el encargo a **Claude Code**, validando la primera versión y conectando el recorrido integral del cliente: **Reserva ➔ Cuestionario ➔ Subida de Fotos ➔ Análisis Morfológico ➔ Informe y Plan de Visitas**.

---

## 🚀 Qué te Llevas de esta Clase

1. **De la Idea a la Demo en Local:** Cómo plantear el encargo al asistente para que diseñe la arquitectura y el flujo de pantallas antes de programar.
2. **El Recorrido de Usuario Completo (User Journey):**
   - **Paso 1 - Reserva:** Selección de fecha, hora y servicio estético (simulación de checkout).
   - **Paso 2 - Cuestionario de Estilo:** Preguntas de hábitos, profesión, tiempo diario de peinado y preferencias.
   - **Paso 3 - Subida de Fotos:** Captura de fotos frontal y de perfil para análisis de facciones.
   - **Paso 4 - Generación del Informe con IA:** Diagnóstico de morfología facial (ovalada, cuadrada, diamante, redonda, alargada) y sugerencias personalizadas de corte, color, barba o gafas.
   - **Paso 5 - Fidelización & Entrega:** Plan de próximas visitas y mantenimiento periódico.
3. **Estructura de Despliegue con `EMPIEZA-AQUI.md`:** Instrucciones precisas para que Claude Code monte y ejecute la demo en tu máquina sin configurar APIs de pago obligatorias en la primera fase.
4. **Validación de Negocio B2B:** Cómo empaquetar la aplicación como un servicio de alto valor para peluquerías, salones de belleza y barberías premium.

---

## 🧩 Recorrido Completo del Cliente (User Journey)

```mermaid
graph TD
    A[📅 1. Reserva y Selección de Servicio] --> B[📝 2. Cuestionario de Hábitos & Preferencias]
    B --> C[📸 3. Carga de Fotos: Frontal & Perfil]
    C --> D[🧠 4. Análisis Morfológico con IA (Visagismo)]
    
    subgraph "Módulos del Informe de Visagismo"
        D --> E1[👤 Forma del Rostro & Proporciones]
        D --> E2[✂️ Recomendación de Corte & Peinado]
        D --> E3[🎨 Paleta de Color & Armonía]
        D --> E4[👓 Accesorios, Barba & Gafas]
    end
    
    E1 --> F[📄 5. Entrega de Informe Ejecutivo PDF / Web]
    E2 --> F
    E3 --> F
    E4 --> F
    F --> G[🔁 6. Plan de Próximas Visitas & Mantenimiento]
```

---

## ⚙️ Las 4 Etapas de Construcción con Claude Code

### 1. El Encargo Maestro (Prompting Arquitectónico)
* En lugar de pedir código aislado, se le pide al asistente:
  1. Dibujar el mapa completo del proceso.
  2. Definir los estados del usuario en frontend.
  3. Establecer la estructura de carpetas modular.

### 2. La Primera Versión (Validación Visual)
* Revisión de las pantallas base:
  - Diseño responsive y limpio con Tailwind.
  - Componente interactivo para subida de fotos con previsualización.
  - Generador de diagnósticos mockeados para probar la UI antes de conectar la API de visión.

### 3. El Recorrido Completo (Conexión de Pantallas)
* Integración fluida entre la reserva, el test de estilo, el procesamiento de imágenes y la visualización del informe final sin recargas de página bruscas.

### 4. La Entrega & Estrategia Comercial
* El informe no termina con un consejo estético, sino con una **llamada a la acción comercial**:
  - Sugerencia de productos de mantenimiento para comprar en el salón.
  - Agenda de la próxima sesión a las 4–6 semanas para mantener el corte óptimo.

---

## 📂 Cómo Probar el Proyecto Adjunto en Local

1. Descargar y descomprimir el archivo **`Proyecto Visagismo.zip`**.
2. Abrir el archivo **`EMPIEZA-AQUI.md`**, que contiene el prompt exacto para Claude Code:
   ```bash
   claude
   "Lee el archivo EMPIEZA-AQUI.md y levanta la demo local de la app de visagismo."
   ```
3. Ejecutar la demo local en el navegador (`http://localhost:5173` o similar).
4. **Objetivo inicial:** Completar el recorrido de prueba de punta a punta hasta obtener el informe sin necesidad de configurar pasarelas de pago reales.

---

## 🧠 Claves de Negocio y Consejos del Autor

* **Prototipar antes de monetizar:** Comprueba que la experiencia de usuario sea impecable antes de complicar el proyecto con Stripe o autenticación pesada.
* **El Visagismo como Servicio Premium:** Un salón tradicional cobra 15€ por un corte básico; con un diagnóstico de visagismo asistido por IA, puede posicionar una asesoría de imagen integral por 50€–90€.
* **Simulación vs Precisión Médica:** La versión demo utiliza fotos para simulación estética visual orientativa; el valor reside en la recomendación personalizada y la experiencia del cliente.

---

## 📚 Recursos y Enlaces Relacionados

* **🎙️ Píldora de Negocio Skool:** [Visagismo con IA: de una idea a un servicio](https://www.skool.com/ia-masters-automations/visagismo-con-ia-de-una-idea-a-un-servicio?utm_campaign=skool_link_classroom&utm_content=ed2b5d2f6d9c484a9eb75863cf1238d7)
* **⚡ Hub Central de Recursos:** [`index.html`](./index.html) \| [`README.html`](./README.html)
* **📘 Catálogo Claude Code Skills:** [`Claude-Code-Skills-App-Templates.html`](./Claude-Code-Skills-App-Templates.html)
