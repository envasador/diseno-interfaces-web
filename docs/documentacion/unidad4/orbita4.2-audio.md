## 4.2 Audio

### 8. Audio para la web
#### 8.1. Entendiendo el audio digital

Antes de hablar de formatos y códecs, necesitas entender qué es el audio digital. Cuando grabas sonido, estás capturando ondas sonoras (variaciones de presión en el aire) y convirtiéndolas en números. Este proceso se llama **muestreo** (sampling).

Dos conceptos clave determinan la calidad del audio digital:

**Sample rate (frecuencia de muestreo):** Cuántas veces por segundo se captura el valor de la onda sonora. Se mide en Hz (hercios). Un CD de audio usa 44.100 Hz (44.1 kHz), lo que significa que captura 44.100 muestras por segundo. El oído humano puede percibir frecuencias hasta aproximadamente 20 kHz, así que 44.1 kHz es más que suficiente para reproducir todo el espectro audible.

**Bit depth (profundidad de bits):** Cuántos valores diferentes puede tener cada muestra. Un audio de 16 bits puede tener 65.536 valores diferentes por muestra. Más bits = mayor rango dinámico (diferencia entre el sonido más suave y el más fuerte que puedes capturar sin distorsión).

**Canales:** Mono (1 canal), estéreo (2 canales - izquierda y derecha), o multicanal (5.1, 7.1 para cine).

Para web, estos son los estándares comunes:
- **Música:** 44.1 kHz, 16 bits, estéreo
- **Voz (podcasts):** 22.05 kHz o 44.1 kHz, 16 bits, mono
- **Audio para vídeo:** 48 kHz, 16 bits, estéreo

#### 8.2. Formatos de audio: eligiendo el apropiado

##### MP3: el veterano universal

MP3 (MPEG-1 Audio Layer 3) lleva con nosotros desde 1993 y tiene soporte del 100% en navegadores. Usa compresión con pérdida: elimina información que el oído humano difícilmente detectaría para reducir el tamaño del archivo.

La calidad se controla con el **bitrate** (tasa de bits), medido en kbps (kilobits por segundo):

- **96 kbps:** Calidad mínima. Solo para voz donde la inteligibilidad es lo único importante.
- **128 kbps:** Calidad aceptable para voz. Suficiente para podcasts sencillos.
- **192 kbps:** Buena calidad para música casual. La mayoría de usuarios no notará diferencias con calidades superiores.
- **256 kbps:** Alta calidad. Indistinguible del original para la mayoría de oyentes.
- **320 kbps:** Máxima calidad MP3. Probablemente excesivo para web.

**Ejemplo numérico real:**

Podcast solo voz, 30 minutos de duración:
- 96 kbps mono: ~21MB
- 128 kbps mono: ~28MB
- 192 kbps estéreo: ~42MB
- 320 kbps estéreo: ~72MB

Para voz, la diferencia entre 128 kbps y 192 kbps es apenas perceptible, pero el archivo pesa un 50% más. No tiene sentido.

**Optimización adicional para contenido de voz:**

Cuando tu audio es principalmente voz (podcasts, audiolibros, tutoriales), puedes optimizar aún más:

1. **Usa mono en vez de estéreo:** La voz no gana nada estando en estéreo. Un archivo mono pesa exactamente la mitad que uno estéreo al mismo bitrate.

2. **Reduce el sample rate:** Para voz puedes bajar a 22.05 kHz sin pérdida perceptible. La voz humana tiene su energía principalmente entre 300 Hz y 3.4 kHz.

3. **Usa compresión dinámica:** Antes de exportar, aplica un compresor para igualar los niveles de volumen. Esto permite usar bitrates más bajos sin perder inteligibilidad.

Resultado: un podcast de 30 minutos puede pasar de 42MB (192 kbps estéreo) a 14MB (128 kbps mono, 22.05 kHz) sin que nadie note la diferencia.

**Cuándo usar MP3:**
- Es tu formato por defecto para audio en web
- Compatibilidad universal es prioridad
- Audiencia diversa con dispositivos desconocidos
- Contenido de voz o música donde el tamaño importa

##### OGG Vorbis: open source y eficiente

OGG es un contenedor (como MP4) y Vorbis es el códec de audio. Fue desarrollado como alternativa libre de patentes a MP3. Ofrece mejor calidad que MP3 al mismo bitrate, o mismo nivel de calidad con menor tamaño de archivo.

**Comparativa real:**
- MP3 @ 192 kbps: 28MB, calidad buena
- OGG Vorbis @ 160 kbps: 23MB, calidad equivalente

El problema es el soporte: funciona en Firefox, Chrome, Edge, Android, pero **no en iOS/Safari**. Esto es crítico porque iOS representa aproximadamente el 25-30% del tráfico web móvil en muchos mercados.

**Estrategia de uso:**

Si quieres aprovechar OGG para usuarios que lo soporten, usa múltiples fuentes con fallback:

```html
<audio controls>
  <source src="podcast.ogg" type="audio/ogg">
  <source src="podcast.mp3" type="audio/mpeg">
  <p>Tu navegador no soporta audio HTML5. 
     <a href="podcast.mp3">Descarga el archivo MP3</a>
  </p>
</audio>
```

Firefox descarga OGG (más ligero). Safari descarga MP3. Todos escuchan el audio.

**Cuándo usar OGG:**
- Tu audiencia es principalmente Android/PC
- Quieres máxima eficiencia de compresión
- Puedes mantener dos versiones (OGG + MP3 fallback)
- Tu proyecto valora software open source

##### AAC: la elección de Apple

AAC (Advanced Audio Coding) es el formato que usa Apple en iTunes, iPhone, iPad. Los archivos suelen tener extensión .m4a. Ofrece mejor calidad que MP3 al mismo bitrate.

**Comparativa:**
- MP3 @ 160 kbps: calidad aceptable
- AAC @ 128 kbps: calidad similar o superior

El problema del soporte es inverso a OGG: AAC funciona perfectamente en todo el ecosistema Apple y Windows, razonablemente bien en Chrome/Edge, pero puede tener problemas en Linux antiguo y algunos dispositivos Android viejos.

**Soporte actual (2025):**
- iOS/macOS/Safari: 100%
- Windows/Edge: 100%
- Chrome: 100%
- Firefox: 100% (desde hace años)
- Android moderno: 100%
- Android viejo (pre-2018): variable

Para proyectos nuevos en 2025, AAC es bastante seguro, pero MP3 sigue siendo más universal.

**Cuándo usar AAC:**
- Tu audiencia es principalmente iOS/macOS
- Necesitas mejor calidad/peso que MP3
- Estás desarrollando app nativa iOS
- El audio es parte de vídeo (MP4 usa AAC por defecto)

##### WAV: sin comprimir, solo para producción

WAV es audio sin compresión. Calidad perfecta, peso gigantesco. Un minuto de audio WAV estéreo (44.1 kHz, 16 bits) pesa aproximadamente 10MB.

**Nunca uses WAV para web** como formato final de distribución. Es el formato que usas durante producción/edición, pero siempre exportas a formato comprimido para publicar.

La única excepción: si estás distribuyendo samples de audio profesional para productores musicales y el peso no importa.

#### 8.3. Herramientas de conversión y optimización

##### Audacity: el editor gratuito estándar

Audacity es software libre, multiplataforma, perfecto para usuarios que prefieren interfaz gráfica.

**Workflow típico para preparar podcast:**

1. **Importa tu grabación original** (puede ser WAV, MP3, cualquier cosa)
    - File → Open

2. **Limpia el audio:**
    - Selecciona silencio inicial/final → Delete
    - Effect → Noise Reduction (si hay ruido de fondo)
    - Effect → Normalize (igualar volumen)
    - Effect → Compressor (reducir diferencias entre partes suaves y fuertes)

3. **Convierte a mono si es solo voz:**
    - Tracks → Mix → Mix Stereo Down to Mono

4. **Exporta optimizado:**
    - File → Export → Export as MP3
    - En Quality, elige bitrate: 128 kbps para voz, 192 kbps para música
    - Si exportas para voz, en Project Rate (abajo izquierda) puedes cambiar a 22050 Hz antes de exportar

5. **Nombra el archivo descriptivamente:**
    - `podcast-episodio-01-introduccion.mp3`

**Exportar múltiples formatos:**

Para máxima compatibilidad, exporta dos versiones:

```
File → Export → Export as MP3 → podcast.mp3
File → Export → Export as OGG → podcast.ogg
```

Audacity maneja ambas conversiones con interfaz sencilla.

##### FFmpeg: automatización por línea de comandos

FFmpeg es la herramienta profesional de facto. Sin interfaz gráfica, todo por comandos, pero tremendamente potente.

**Convertir WAV a MP3 optimizado para voz:**

```bash
ffmpeg -i original.wav \
  -codec:a libmp3lame \
  -b:a 128k \
  -ac 1 \
  -ar 22050 \
  podcast.mp3
```

Parámetros explicados:
- `-i original.wav`: archivo de entrada
- `-codec:a libmp3lame`: usa el códec LAME (el mejor MP3 encoder)
- `-b:a 128k`: bitrate de 128 kbps
- `-ac 1`: un canal (mono)
- `-ar 22050`: sample rate de 22.05 kHz

**Convertir a MP3 para música:**

```bash
ffmpeg -i cancion.wav \
  -codec:a libmp3lame \
  -b:a 192k \
  -ac 2 \
  -ar 44100 \
  cancion.mp3
```

- `-ac 2`: dos canales (estéreo)
- `-ar 44100`: sample rate estándar de CD

**Convertir a OGG:**

```bash
ffmpeg -i audio.wav \
  -codec:a libvorbis \
  -b:a 160k \
  audio.ogg
```

**Procesar múltiples archivos en lote (Bash):**

```bash
for file in *.wav; do
  ffmpeg -i "$file" \
    -codec:a libmp3lame \
    -b:a 128k \
    -ac 1 \
    -ar 22050 \
    "${file%.wav}.mp3"
done
```

Este script convierte todos los WAV de una carpeta a MP3 optimizado para voz.

#### 8.4. Integración básica en HTML

La etiqueta `<audio>` es sorprendentemente simple en su forma básica:

```html
<audio controls>
  <source src="podcast.mp3" type="audio/mpeg">
  <source src="podcast.ogg" type="audio/ogg">
  <p>Tu navegador no soporta audio HTML5.</p>
</audio>
```

**Atributos importantes de `<audio>`:**

**controls:** Muestra los controles nativos del navegador (play, pausa, volumen, barra de progreso). Sin este atributo, el audio es invisible y no se puede controlar.

```html
<!-- CON controles visibles -->
<audio src="musica.mp3" controls></audio>

<!-- SIN controles (invisible, inútil sin JavaScript) -->
<audio src="musica.mp3"></audio>
```

**autoplay:** El audio empieza a reproducirse automáticamente al cargar la página. **Importante:** Los navegadores modernos bloquean autoplay de audio a menos que el usuario haya interactuado con la página primero (click, scroll, etc.). Esto evita sitios molestos que empiezan a sonar sin permiso.

```html
<!-- Esto NO funcionará sin interacción previa del usuario -->
<audio src="musica.mp3" autoplay controls></audio>
```

**loop:** El audio se repite infinitamente.

```html
<audio src="musica-ambiente.mp3" controls loop></audio>
```

**muted:** El audio empieza silenciado. Útil si combinas con autoplay (los navegadores permiten autoplay si está muted).

```html
<!-- Esto SÍ funciona: autoplay pero silenciado -->
<audio src="ambiente.mp3" autoplay loop muted controls></audio>
```

**preload:** Controla cuánto pre-descarga el navegador antes de que el usuario haga play.

```html
<!-- No precarga nada (ahorra datos) -->
<audio src="podcast.mp3" controls preload="none"></audio>

<!-- Precarga solo metadatos: duración, etc. (recomendado) -->
<audio src="podcast.mp3" controls preload="metadata"></audio>

<!-- Precarga todo el archivo (usar solo para audio corto) -->
<audio src="efecto-corto.mp3" controls preload="auto"></audio>
```

Para una página con múltiples podcasts, usa `preload="none"` o `preload="metadata"`. No tiene sentido descargar 500MB de audio si el usuario solo va a escuchar uno.

#### 8.5. Múltiples fuentes para compatibilidad

La estrategia correcta es ofrecer múltiples formatos y dejar que el navegador elija el primero que entienda:

```html
<audio controls>
  <source src="podcast.ogg" type="audio/ogg">
  <source src="podcast.mp3" type="audio/mpeg">
  <p>Tu navegador no soporta audio HTML5. 
     <a href="podcast.mp3" download>Descarga el MP3</a>
  </p>
</audio>
```

**Orden de fuentes:** Pon primero el formato más eficiente que quieras usar (OGG), luego el fallback universal (MP3). El navegador usa el primero que soporte y ignora el resto.

**El párrafo final** solo se muestra si el navegador no soporta `<audio>` en absoluto (navegadores antiquísimos). Es buena práctica incluir un enlace de descarga como última opción.

#### 8.6. Ejemplo real: podcast con transcripción

```html
<article class="podcast-episode">
  <h2>Episodio 12: Optimización de imágenes para web</h2>
  
  <audio controls preload="metadata">
    <source src="episodio-12.ogg" type="audio/ogg">
    <source src="episodio-12.mp3" type="audio/mpeg">
    <p>
      Tu navegador no soporta audio HTML5.
      <a href="episodio-12.mp3" download>Descargar MP3 (14MB)</a>
    </p>
  </audio>
  
  <div class="episode-meta">
    <p><strong>Duración:</strong> 28 minutos</p>
    <p><strong>Publicado:</strong> 15 de enero de 2025</p>
  </div>
  
  <details class="transcript">
    <summary>Ver transcripción completa</summary>
    <div>
      <p><strong>[00:00]</strong> Hola y bienvenidos al episodio 12...</p>
      <p><strong>[00:35]</strong> Hoy vamos a hablar sobre...</p>
      <p><strong>[02:15]</strong> El primer concepto importante es...</p>
    </div>
  </details>
</article>
```

Este ejemplo incluye:
- Formatos múltiples (OGG + MP3)
- Preload optimizado (metadata)
- Fallback con descarga
- Metadatos visibles (duración, fecha)
- Transcripción expandible (accesibilidad)

---
