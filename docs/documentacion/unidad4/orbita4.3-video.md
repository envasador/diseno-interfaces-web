## 4.3 Vídeo

### 9. Vídeo para la web

#### 9.1. Entendiendo el vídeo digital

El vídeo digital es básicamente una secuencia de imágenes (frames) mostradas rápidamente, más audio sincronizado. Cuando ves "30 fps" (frames per second), significa 30 imágenes por segundo.

**Tres conceptos determinan la calidad y peso del vídeo:**

**Resolución:** El tamaño de cada frame en píxeles.
- 4K: 3840×2160 (8.3 millones de píxeles por frame)
- 1080p (Full HD): 1920×1080 (2 millones de píxeles)
- 720p (HD): 1280×720 (921 mil píxeles)
- 480p (SD): 854×480 (410 mil píxeles)
- 360p: 640×360 (230 mil píxeles)

**Frame rate:** Cuántos frames por segundo. 24 fps (cine), 30 fps (estándar web), 60 fps (deportes, gaming).

**Bitrate:** Cuántos datos por segundo. Medido en Mbps (megabits por segundo). Mayor bitrate = mejor calidad = mayor peso.

**Ejemplo del impacto del bitrate:**

Vídeo de 1 minuto, 1080p, 30 fps:
- 10 Mbps (alta calidad): ~75MB
- 5 Mbps (buena calidad): ~37MB
- 2 Mbps (calidad aceptable): ~15MB
- 0.5 Mbps (baja calidad): ~3.7MB

La clave está en encontrar el bitrate mínimo donde la calidad sigue siendo aceptable para tu contexto.

#### 9.2. Contenedor vs Códec: la confusión común

Mucha gente confunde contenedor con códec. Son cosas diferentes:

**Contenedor** (o formato): Es el archivo que contiene todo: vídeo, audio, subtítulos, metadatos. Es como una caja. Ejemplos: MP4, WebM, MKV, AVI.

**Códec**: Es el algoritmo que comprime/descomprime el vídeo o audio dentro de esa caja. Ejemplos: H.264, VP9, AV1 (vídeo); AAC, Vorbis, Opus (audio).

Un archivo MP4 puede contener vídeo H.264 + audio AAC, o vídeo H.265 + audio MP3, o múltiples combinaciones. El contenedor es MP4, pero el códec cambia.

Esta distinción importa porque el navegador necesita soportar tanto el contenedor como el códec para reproducir el vídeo.

#### 9.3. Formatos de vídeo: eligiendo con criterio

##### MP4 con H.264: el estándar universal

**Contenedor:** MP4  
**Códec de vídeo:** H.264 (también llamado AVC)  
**Códec de audio:** AAC (típicamente)  
**Soporte:** 100% de navegadores

H.264 lleva con nosotros desde 2003 y sigue siendo el caballo de batalla de la web. Ofrece excelente balance entre calidad, compresión y compatibilidad.

**Bitrate recomendado para web:**

| Resolución | Bitrate vídeo | Uso típico |
|------------|---------------|------------|
| 360p | 0.5-1 Mbps | Conexiones muy lentas, vídeos secundarios |
| 480p | 1-2 Mbps | Conexiones lentas, móviles con datos limitados |
| 720p | 2.5-4 Mbps | HD estándar, buena calidad para web |
| 1080p | 5-8 Mbps | Full HD, vídeo principal o hero |
| 1440p | 10-15 Mbps | Raramente necesario para web |
| 4K | 20-30 Mbps | Casi nunca justificado para web pública |

**Bitrate de audio:** 128-192 kbps (AAC) es suficiente.

**Ejemplo numérico:**

Vídeo tutorial de 5 minutos en diferentes calidades:

- **360p @ 0.7 Mbps:** ~26MB (conexiones 3G lentas)
- **480p @ 1.5 Mbps:** ~56MB (móviles con datos)
- **720p @ 3 Mbps:** ~112MB (calidad estándar web)
- **1080p @ 6 Mbps:** ~225MB (alta calidad)

Para un vídeo hero de fondo decorativo que hace loop, puedes ser más agresivo:
- **720p @ 1 Mbps:** Suficiente para background, especialmente si tiene desenfoque o overlay

**Cuándo usar MP4/H.264:**
- Es tu formato por defecto siempre
- Necesitas compatibilidad universal
- Es el único formato si solo puedes ofrecer uno

##### WebM con VP9: eficiencia moderna

**Contenedor:** WebM  
**Códec de vídeo:** VP9  
**Códec de audio:** Vorbis u Opus  
**Soporte:** Chrome, Firefox, Edge, Safari (desde 2021)

VP9 fue desarrollado por Google como alternativa open source a H.264. Ofrece aproximadamente 50% mejor compresión que H.264 con la misma calidad percibida.

**Comparativa real:**

Vídeo de 5 minutos, 1080p, 30fps:
- H.264 @ 6 Mbps: 225MB, calidad excelente
- VP9 @ 3 Mbps: 112MB, calidad similar
- Ahorro: 50%

Para un sitio con mucho vídeo (educativo, streaming, portfolio), esto puede significar ahorrar terabytes de ancho de banda mensual.

**Soporte actual (2025):**

- Chrome/Chromium: 100% desde 2014
- Firefox: 100% desde 2015
- Edge: 100% desde 2020
- Safari: 100% desde 2021 (macOS Big Sur, iOS 14.5)
- Android: 100% en versiones modernas

El soporte es suficientemente amplio para usarlo con confianza, siempre con fallback MP4.

**Estrategia recomendada:**

```html
<video controls>
  <source src="tutorial.webm" type="video/webm">
  <source src="tutorial.mp4" type="video/mp4">
</video>
```

Chrome/Firefox/Edge modernos descargan WebM (más ligero). Safari descarga MP4. Usuarios de navegadores antiguos descargan MP4. Todo el mundo ve el vídeo, los modernos ahorran datos.

**Consideración práctica:** Mantener dos versiones (WebM + MP4) significa más trabajo de encoding. Para proyectos pequeños o prototipos educativos, solo MP4 puede ser suficiente. Para proyectos profesionales con múltiples vídeos, WebM + MP4 ahorra ancho de banda significativo.

##### WebM con AV1: el futuro (con precaución)

AV1 es el códec más moderno, sucesor de VP9. Ofrece 30% mejor compresión que VP9 (y por tanto ~65% mejor que H.264).

**El problema:** Soporte aún limitado (70-80% según el mercado) y encoding muy lento (puede tardar 10-20× más que H.264).

En 2025, AV1 es interesante para proyectos vanguardistas o vídeos muy largos donde el ahorro justifica el esfuerzo, pero no es mainstream todavía. Para este curso, nos centramos en H.264 + VP9.

#### 9.4. Herramientas de conversión

##### HandBrake: el conversor amigable

HandBrake es software libre, multiplataforma, con interfaz gráfica intuitiva. Es perfecto para usuarios que quieren resultados profesionales sin tocar la terminal.

**Workflow típico para vídeo web:**

1. **Abre HandBrake** y arrastra tu vídeo original (puede ser MOV, AVI, MKV, cualquier cosa)

2. **Selecciona preset:**
    - Lateral izquierdo → Presets
    - Para MP4: "Fast 720p30" o "Fast 1080p30"
    - Para WebM: "VP9 MKV 720p30" o "VP9 MKV 1080p30"

3. **Ajusta configuración (opcional):**
    - Pestaña "Video":
        - Framerate: 30 fps (constant)
        - Quality: RF 23 (menor número = más calidad = más peso)
    - Pestaña "Audio":
        - Codec: AAC (para MP4) o Opus (para WebM)
        - Bitrate: 128 kbps

4. **Optimiza para web (importante):**
    - Pestaña "Video"
    - Marca "Web Optimized" (pone los metadatos al principio del archivo para que empiece a reproducirse antes de descargar completo)

5. **Selecciona destino** y nombre de archivo

6. **Click en "Start Encode"**

**Para procesar múltiples vídeos:**

HandBrake tiene una cola (Queue). Añades múltiples archivos con la misma configuración y los procesa todos en secuencia. Útil si tienes 10 vídeos de un curso que necesitan el mismo tratamiento.

**Ajustar calidad vs peso:**

El parámetro RF (Rate Factor) controla calidad:
- RF 18: Casi sin pérdida, archivos grandes
- RF 23: Balance óptimo (por defecto)
- RF 28: Compresión agresiva, calidad visible

Para vídeos hero decorativos puedes usar RF 26-28. Para tutoriales donde necesitas ver detalles, RF 20-23.

##### FFmpeg: control total por comandos

**Convertir a MP4/H.264 optimizado para web:**

```bash
ffmpeg -i original.mov \
  -c:v libx264 \
  -preset slow \
  -crf 23 \
  -c:a aac \
  -b:a 128k \
  -movflags +faststart \
  -vf "scale=1920:-2" \
  tutorial.mp4
```

Parámetros explicados:
- `-c:v libx264`: códec H.264
- `-preset slow`: mejor compresión (slow/medium/fast/ultrafast)
- `-crf 23`: calidad (18=mejor, 28=peor, 23=óptimo)
- `-c:a aac`: audio AAC
- `-b:a 128k`: bitrate audio
- `-movflags +faststart`: optimiza para streaming web
- `-vf "scale=1920:-2"`: escala a ancho 1920, altura automática (el -2 mantiene divisible por 2)

**Convertir a WebM/VP9:**

```bash
ffmpeg -i original.mov \
  -c:v libvpx-vp9 \
  -crf 30 \
  -b:v 0 \
  -c:a libopus \
  -b:a 128k \
  tutorial.webm
```

**Crear vídeo a múltiples resoluciones:**

```bash
# 1080p
ffmpeg -i original.mov -c:v libx264 -preset slow -crf 23 \
  -vf "scale=1920:-2" -c:a aac -b:a 128k -movflags +faststart \
  tutorial-1080.mp4

# 720p
ffmpeg -i original.mov -c:v libx264 -preset slow -crf 23 \
  -vf "scale=1280:-2" -c:a aac -b:a 128k -movflags +faststart \
  tutorial-720.mp4

# 480p
ffmpeg -i original.mov -c:v libx264 -preset slow -crf 24 \
  -vf "scale=854:-2" -c:a aac -b:a 96k -movflags +faststart \
  tutorial-480.mp4
```

Nota: CRF sube ligeramente en resoluciones menores (24 para 480p) porque los artefactos son menos visibles en vídeo pequeño.

**Extraer frame como poster image:**

```bash
ffmpeg -i video.mp4 -ss 00:00:05 -vframes 1 poster.jpg
```

Esto extrae el frame en el segundo 5 como imagen JPG, útil para el atributo `poster` de `<video>`.

#### 9.5. Integración básica en HTML

La etiqueta `<video>` comparte muchos conceptos con `<audio>`, pero añade dimensiones visuales.

**Ejemplo básico:**

```html
<video controls width="640" height="360">
  <source src="tutorial.webm" type="video/webm">
  <source src="tutorial.mp4" type="video/mp4">
  <p>Tu navegador no soporta vídeo HTML5.</p>
</video>
```

**Atributos importantes de `<video>`:**

**width y height:** Dimensiones en píxeles. **Importante:** Especifica siempre ambos para evitar layout shift. El navegador mantiene el aspect ratio automáticamente si el vídeo tiene dimensiones diferentes.

```html
<!-- El navegador reserva 640×360 inmediatamente -->
<video src="video.mp4" controls width="640" height="360"></video>

<!-- Sin dimensiones, la página "salta" cuando el vídeo carga -->
<video src="video.mp4" controls></video> <!-- MAL -->
```

**poster:** Imagen que se muestra antes de reproducir. Elige un frame representativo del vídeo.

```html
<video controls width="1920" height="1080" poster="thumbnail.jpg">
  <source src="video.mp4" type="video/mp4">
</video>
```

Sin poster, el navegador muestra el primer frame del vídeo, que puede ser negro o una transición extraña.

**autoplay, loop, muted:** Igual que en audio.

```html
<!-- Vídeo de fondo que hace loop -->
<video autoplay loop muted playsinline width="1920" height="1080">
  <source src="hero-background.webm" type="video/webm">
  <source src="hero-background.mp4" type="video/mp4">
</video>
```

**playsinline:** Crítico para iOS. Sin este atributo, Safari abre el vídeo en pantalla completa al reproducir. Con `playsinline`, reproduce dentro del layout de la página.

**preload:** Controla precarga.

```html
<!-- No precarga nada (ahorra datos) -->
<video src="video.mp4" controls preload="none" poster="thumb.jpg"></video>

<!-- Precarga solo metadatos: duración, dimensiones (recomendado) -->
<video src="video.mp4" controls preload="metadata" poster="thumb.jpg"></video>

<!-- Precarga todo (solo para vídeos críticos) -->
<video src="video.mp4" controls preload="auto"></video>
```

Para una página con galería de vídeos, usa `preload="none"` o `preload="metadata"`. El usuario probablemente solo verá uno o dos.

#### 9.6. Vídeo hero de fondo: el caso especial

Uno de los usos más comunes es vídeo decorativo de fondo con texto superpuesto.

**HTML:**

```html
<section class="hero">
  <video class="hero-video" autoplay loop muted playsinline>
    <source src="hero-bg.webm" type="video/webm">
    <source src="hero-bg.mp4" type="video/mp4">
  </video>
  
  <div class="hero-content">
    <h1>Bienvenido a Nuestra Agencia</h1>
    <p>Creamos experiencias digitales memorables</p>
    <a href="#contacto" class="btn">Contáctanos</a>
  </div>
</section>
```

**CSS:**

```css
.hero {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
}

.hero-video {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  min-width: 100%;
  min-height: 100%;
  width: auto;
  height: auto;
  z-index: 0;
  object-fit: cover;
}

.hero-content {
  position: relative;
  z-index: 1;
  text-align: center;
  color: white;
  padding: 2rem;
}
```

**Optimización crítica:** Este vídeo debe ser lo más ligero posible sin perder calidad aceptable:
- Resolución: 720p máximo (1080p es overkill para background)
- Bitrate: 1-1.5 Mbps (compresión agresiva)
- Duración: 10-20 segundos loop (no 2 minutos)
- Target: <3MB para el archivo completo

Un vídeo hero de 10 segundos, 720p, 1 Mbps, pesa ~1.5MB. Es aceptable. Uno de 30 segundos en 1080p a 5 Mbps pesa 18MB. Inaceptable.

#### 9.7. Vídeo responsive: adaptando a diferentes pantallas

Similar a imágenes, puedes servir diferentes versiones según el dispositivo:

```html
<video controls width="1920" height="1080" poster="poster.jpg">
  <!-- Desktop: 1080p -->
  <source 
    src="tutorial-1080.webm" 
    type="video/webm"
    media="(min-width: 1200px)"
  >
  <source 
    src="tutorial-1080.mp4" 
    type="video/mp4"
    media="(min-width: 1200px)"
  >
  
  <!-- Tablet: 720p -->
  <source 
    src="tutorial-720.webm" 
    type="video/webm"
    media="(min-width: 768px)"
  >
  <source 
    src="tutorial-720.mp4" 
    type="video/mp4"
    media="(min-width: 768px)"
  >
  
  <!-- Mobile: 480p -->
  <source src="tutorial-480.webm" type="video/webm">
  <source src="tutorial-480.mp4" type="video/mp4">
  
  <p>Tu navegador no soporta vídeo HTML5.</p>
</video>
```

El navegador elige la primera `<source>` cuya media query coincida. Usuario desktop descarga 1080p, tablet 720p, móvil 480p.

**Consideración práctica:** Esto significa mantener 6 archivos (3 resoluciones × 2 formatos). Para proyectos educativos o pequeños, puede ser excesivo. Una estrategia simplificada es ofrecer solo 720p optimizado, que funciona bien en todos los dispositivos.

#### 9.8. Subtítulos con WebVTT

Los subtítulos no solo ayudan a personas con problemas auditivos; mucha gente ve vídeos sin sonido (transporte público, oficina, navegación casual).

**Etiqueta `<track>`:**

```html
<video controls width="1280" height="720">
  <source src="tutorial.mp4" type="video/mp4">
  
  <track 
    kind="subtitles" 
    src="subtitulos-es.vtt" 
    srclang="es" 
    label="Español"
    default
  >
  <track 
    kind="subtitles" 
    src="subtitles-en.vtt" 
    srclang="en" 
    label="English"
  >
  <track 
    kind="descriptions" 
    src="audiodesc-es.vtt" 
    srclang="es" 
    label="Audiodescripción"
  >
</video>
```

**Atributos de `<track>`:**

**kind:** Tipo de pista.
- `subtitles`: Subtítulos (traducción de diálogos)
- `captions`: Subtítulos completos (incluyen efectos sonoros, música)
- `descriptions`: Audiodescripción (describe acciones visuales para personas ciegas)
- `chapters`: Capítulos (navegación por secciones)
- `metadata`: Metadatos (no visible, para JavaScript)

**src:** Ruta al archivo VTT

**srclang:** Código de idioma (es, en, fr...)

**label:** Texto que aparece en el selector de subtítulos del reproductor

**default:** Marca esta pista como activada por defecto

**Formato de archivo WebVTT:**

```
WEBVTT

00:00:00.000 --> 00:00:03.500
Hola, bienvenidos a este tutorial sobre
optimización de vídeo para web.

00:00:03.500 --> 00:00:07.800
En este vídeo aprenderemos a elegir
los formatos correctos.

00:00:07.800 --> 00:00:12.200
Empezaremos hablando sobre contenedores
y códecs.

NOTE Esto es un comentario, no se muestra

00:00:12.200 --> 00:00:16.500
<v Instructor>H.264 es el códec más compatible.</v>

00:00:16.500 --> 00:00:20.100
<v Alumno>¿Y qué pasa con WebM?</v>
<v Instructor>WebM ofrece mejor compresión.</v>
```

**Características avanzadas de VTT:**

**Etiquetas de voz (`<v>`):** Identifican quién habla

**Estilos CSS:** Puedes aplicar estilos a subtítulos

```
WEBVTT

STYLE
::cue {
  background-color: rgba(0, 0, 0, 0.8);
  color: white;
  font-size: 1.2em;
}

00:00:00.000 --> 00:00:03.000
Subtítulo con estilo personalizado
```

**Posicionamiento:**

```
00:00:00.000 --> 00:00:03.000 align:start position:10%
Texto alineado a la izquierda, arriba
```

**Crear archivos VTT:**

Opción 1: **Manualmente** - Para vídeos cortos, puedes escribir el VTT en cualquier editor de texto.

Opción 2: **Servicios de transcripción automática:**
- YouTube: Sube vídeo → genera subtítulos auto → descarga como VTT (Edición → Subtítulos → Descargar)
- Happy Scribe, Rev.com, Otter.ai: Servicios especializados

Opción 3: **Software de subtitulado:**
- Subtitle Edit (Windows, gratis)
- Aegisub (multiplataforma, gratis)

#### 9.9. Vídeo como reemplazo de GIF animado

GIF animado está obsoleto para web. Un GIF de 5 segundos puede pesar 3-5MB. Ese mismo clip como vídeo MP4 sin audio pesa 200-300KB con mejor calidad.

**Conversión de GIF a vídeo con FFmpeg:**

```bash
ffmpeg -i animacion.gif \
  -movflags faststart \
  -pix_fmt yuv420p \
  -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" \
  -c:v libx264 \
  -crf 20 \
  -an \
  animacion.mp4
```

Parámetros:
- `-movflags faststart`: optimiza para web
- `-pix_fmt yuv420p`: compatibilidad universal
- `-vf scale`: asegura dimensiones pares (requerido por H.264)
- `-crf 20`: alta calidad (GIF suele ser ilustración)
- `-an`: sin audio

**Implementación como "GIF":**

```html
<video autoplay loop muted playsinline class="gif-replacement">
  <source src="animacion.webm" type="video/webm">
  <source src="animacion.mp4" type="video/mp4">
</video>
```

```css
.gif-replacement {
  max-width: 400px;
  height: auto;
  display: inline-block;
}
```

Se comporta exactamente como un GIF (autoplay, loop, sin sonido) pero pesa 90% menos.

**Comparativa real:**

Animación de 5 segundos, 400×300:
- GIF original: 2.8MB
- MP4 H.264 CRF 20: 280KB (90% más ligero)
- WebM VP9: 160KB (94% más ligero)

Para un sitio con 10 animaciones, es la diferencia entre 28MB y 2.8MB (MP4) o 1.6MB (WebM).

