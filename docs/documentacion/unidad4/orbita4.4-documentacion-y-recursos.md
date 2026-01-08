## 4.4 Documentación y recursos.

### 10. Documentación del proyecto: MULTIMEDIA.md

#### 10.1. Por qué documentar

En 6 meses no recordarás por qué elegiste ciertos formatos o cuál fue el proceso de optimización. La documentación también es evidencia para tu portfolio: demuestras decisiones técnicas informadas.

#### 10.2. Estructura recomendada

Crea archivo `MULTIMEDIA.md` en la raíz de tu repositorio:

```markdown
# Documentación de Assets Multimedia

## Tabla de Assets

### Imágenes Hero

| Archivo | Formato | Resolución | Peso | Uso |
|---------|---------|------------|------|-----|
| hero-desktop-1920.webp | WebP | 1920×800 | 145KB | Desktop ≥1200px |
| hero-desktop-1920.jpg | JPG | 1920×800 | 220KB | Desktop fallback |
| hero-mobile-400.webp | WebP | 400×711 | 58KB | Mobile <768px |
| hero-mobile-400.jpg | JPG | 400×711 | 95KB | Mobile fallback |

### Galería de Productos

| Archivo | Formato | Resolución | Peso | Uso |
|---------|---------|------------|------|-----|
| producto-01-800.webp | WebP | 800×800 | 68KB | Vista grid/detalle @1x |
| producto-01-1600.webp | WebP | 1600×1600 | 185KB | Vista detalle @2x |

### Iconos

| Archivo | Formato | Tamaño | Peso | Uso |
|---------|---------|--------|------|-----|
| cart.svg | SVG | Escalable | 0.8KB | Icono carrito header |
| menu.svg | SVG | Escalable | 0.5KB | Menú hamburguesa móvil |

### Audio

| Archivo | Formato | Duración | Bitrate | Peso | Uso |
|---------|---------|----------|---------|------|-----|
| podcast-01.mp3 | MP3 | 28min | 128kbps mono | 14MB | Episodio podcast |
| podcast-01.ogg | OGG | 28min | 112kbps mono | 11.5MB | Fallback moderno |

### Vídeo

| Archivo | Formato | Resolución | Duración | Bitrate | Peso | Uso |
|---------|---------|------------|----------|---------|------|-----|
| tutorial-720.mp4 | MP4/H.264 | 1280×720 | 5min | 3Mbps | 112MB | Tutorial principal |
| tutorial-720.webm | WebM/VP9 | 1280×720 | 5min | 1.5Mbps | 56MB | Fallback moderno |
| hero-bg.mp4 | MP4/H.264 | 1280×720 | 15seg | 1Mbps | 1.9MB | Vídeo hero loop |

## Comparativa Antes/Después

### Estado Inicial (exportación directa desde Figma)
- Hero desktop: 1.2MB (PNG sin optimizar)
- Hero mobile: 1.2MB (misma imagen sin responsive)
- Galería 8 productos: 2.4MB (PNG sin optimizar)
- Audio podcast: 42MB (MP3 192kbps estéreo)
- Vídeo tutorial: 225MB (1080p 6Mbps)
- Total: ~273MB

### Estado Optimizado
- Hero desktop: 145KB (WebP), 220KB (JPG fallback)
- Hero mobile: 58KB (WebP), 95KB (JPG fallback)
- Galería 8 productos: 1.2MB (WebP responsive)
- Audio podcast: 14MB (MP3 128kbps mono)
- Vídeo tutorial: 112MB (720p 3Mbps MP4) / 56MB (WebM)
- Total: ~128MB (MP4) / ~72MB (WebM)

**Ahorro:** 145-201MB (53-74% reducción) dependiendo del navegador.

**Impacto en performance:**
- LCP antes: 6.8s (3G throttling)
- LCP después: 1.8s (3G throttling)
- Mejora: 74% más rápido

## Herramientas Utilizadas

- **Figma:** Diseño y exportación inicial
- **Squoosh:** Optimización de imágenes y conversión a WebP
- **Audacity:** Edición y exportación de audio
- **HandBrake:** Conversión y optimización de vídeo
- **FFmpeg:** Procesado por lotes y conversión a WebM

## Decisiones de Dirección de Arte

### Hero Principal

**Desktop (1920×800):**
- Composición horizontal amplia
- Muestra paisaje completo con personas practicando kayak
- Ratio 2.4:1 optimizado para pantallas widescreen

**Mobile (400×711):**
- Composición vertical portrait
- Crop cerrado en kayak principal con montaña de fondo
- Ratio ~1:1.7 optimizado para móviles
- Justificación: Versión desktop reducida dejaba sujetos microscópicos

**Implementación:**
- Elemento `<picture>` con media queries
- 2 formatos (WebP/JPG) para cada composición
- Múltiples resoluciones por formato (1x, 2x)

## Decisiones de Audio

**Podcast:**
- Formato: MP3 + OGG fallback
- Bitrate: 128 kbps (suficiente para voz)
- Canales: Mono (la voz no beneficia de estéreo)
- Sample rate: 44.1 kHz (estándar)
- Justificación: Reducción de 42MB a 14MB (67%) sin pérdida perceptible en voz

## Decisiones de Vídeo

**Tutorial principal:**
- Resolución: 720p (1080p innecesario para tutorial de interfaz)
- Formatos: MP4 (H.264) + WebM (VP9)
- Bitrate: 3 Mbps MP4, 1.5 Mbps WebM
- Audio: 128 kbps AAC/Opus
- Subtítulos: VTT en español e inglés
- Justificación: 720p ofrece claridad suficiente, ahorro masivo vs 1080p

**Vídeo hero background:**
- Resolución: 720p
- Duración: 15 segundos loop
- Bitrate: 1 Mbps (compresión agresiva aceptable para decorativo)
- Sin audio
- Peso target: <2MB
- Justificación: Background no requiere alta fidelidad, prioridad es carga rápida

## Fuentes y Licencias

- **Imágenes hero:** Unsplash (licencia gratuita)
  - Autor: John Doe (unsplash.com/@johndoe)
- **Fotos de productos:** Fotografías propias
- **Iconos:** Diseño propio
- **Audio podcast:** Grabación propia
- **Vídeo tutorial:** Producción propia

## Notas Técnicas

### Por qué WebP + JPG/PNG (no AVIF)

- **WebP:** 97%+ soporte, 25-35% más ligero que JPG/PNG
- **JPG/PNG:** 100% soporte (fallback universal)
- **AVIF no incluido:** Requiere exportación adicional, ahorro marginal (10-15% sobre WebP), complejidad no justificada para proyecto educativo

### Por qué 720p para vídeo (no 1080p)

- Tutorial de interfaz web: resolución más importante en ventana pequeña del IDE
- 720p permite ver texto y UI claramente
- Peso: 112MB vs 225MB (50% de ahorro)
- Para viewport típico de reproducción (70% pantalla), 720p es indistinguible de 1080p

### Audio mono vs estéreo para podcast

- Voz humana no beneficia de imagen estéreo
- Mono reduce peso exactamente 50%
- Única excepción: contenido musical o efectos de sonido espaciales

## Checklist de Validación

- [x] Todas las imágenes <200KB desktop, <100KB mobile
- [x] Hero con dirección de arte implementada
- [x] Todos los `<img>` tienen `alt` descriptivo
- [x] Imágenes below-fold con `loading="lazy"`
- [x] Imágenes con `width` y `height` especificados
- [x] LCP <2.5s en 3G throttling (Lighthouse)
- [x] CLS <0.1
- [x] Iconos SVG optimizados (<2KB cada uno)
- [x] Audio con múltiples formatos (OGG + MP3)
- [x] Vídeo con múltiples formatos (WebM + MP4)
- [x] Vídeo con subtítulos VTT en 2 idiomas
- [x] Vídeo hero <3MB
- [x] Documentación completa en este archivo
```

### 11. Recursos y referencias

#### 11.1. Herramienta principal de optimización

**Squoosh:** https://squoosh.app
- Optimización visual interactiva
- Comparación lado a lado
- Múltiples formatos (WebP, AVIF, MozJPEG, OxiPNG)
- Gratuita, no requiere instalación

#### 11.2. Documentación técnica

**Imágenes:**
- MDN Responsive Images: https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images
- MDN Picture element: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture
- Web.dev Optimize Images: https://web.dev/use-imagemin-to-compress-images/
- Can I Use (compatibilidad): https://caniuse.com

**Audio y Vídeo:**
- LenguajeHTML - Formatos multimedia: https://lenguajehtml.com/html/multimedia/formatos-multimedia/
- LenguajeHTML - Etiqueta audio: https://lenguajehtml.com/html/multimedia/etiqueta-html-audio/
- LenguajeHTML - Etiqueta video: https://lenguajehtml.com/html/multimedia/etiqueta-html-video/
- LenguajeHTML - Etiqueta track (subtítulos): https://lenguajehtml.com/html/multimedia/etiqueta-html-track/
- MDN Video element: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video
- MDN Audio element: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio
- WebVTT specification: https://w3c.github.io/webvtt/

#### 11.3. Herramientas de audio

**Audacity:** https://www.audacityteam.org/
- Editor de audio gratuito multiplataforma
- Exportación a MP3, OGG, WAV
- Efectos de procesado (normalización, compresión, reducción de ruido)

**FFmpeg:** https://ffmpeg.org/
- Conversión y procesado por comandos
- Soporta todos los formatos
- Automatización por scripts

#### 11.4. Herramientas de vídeo

**HandBrake:** https://handbrake.fr/
- Conversor de vídeo gratuito con interfaz gráfica
- Presets optimizados para web
- Soporte MP4 y WebM

**FFmpeg:** https://ffmpeg.org/
- Control total por línea de comandos
- Conversión a múltiples formatos y resoluciones
- Extracción de frames para posters

#### 11.5. Bancos de recursos libres

**Imágenes:**
- Unsplash: https://unsplash.com (fotografías alta calidad, licencia gratuita)
- Pexels: https://www.pexels.com (fotografías e ilustraciones)

**Vídeo:**
- Pexels Videos: https://www.pexels.com/videos/ (clips gratuitos)
- Coverr: https://coverr.co/ (vídeos para backgrounds)

**Audio:**
- Freesound: https://freesound.org/ (efectos de sonido, Creative Commons)
- YouTube Audio Library: https://studio.youtube.com/channel/UC.../music (música libre de derechos)

**Iconos SVG:**
- Heroicons: https://heroicons.com/ (iconos minimalistas, gratis)
- Feather Icons: https://feathericons.com/ (open source)
- Material Icons: https://fonts.google.com/icons (Google, gratis)

### 12. Conclusión

El multimedia optimizado separa desarrolladores/as amateur de profesionales. Dominar estos conceptos te hace inmediatamente más capacitado o capacitada para quedarte en una empresa. Las empresas buscan desarrolladores que:

- Entienden la diferencia entre PNG, WebP y AVIF y cuándo usar cada uno
- Saben implementar imágenes responsive correctamente con `srcset` y `sizes`
- Pueden aplicar dirección de arte con `<picture>`
- Optimizan audio eligiendo bitrate y canales apropiados
- Convierten vídeo a formatos web con balance calidad/peso
- Documentan decisiones técnicas con datos reales

Tu próximo paso: audita tu proyecto actual. ¿Cuánto pesa la página? ¿Usas responsive images? ¿Tus vídeos están optimizados? Implementa lo aprendido, documenta resultados con métricas antes/después. Ese análisis con números reales es oro para tu portfolio.

El medio ambiente te lo agradecerá. Y tus usuarios también.

