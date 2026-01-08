## 4.1 Imágenes
### 1. El desafío real

Imagina esta situación: has diseñado una imagen hero de 1920×800 píxeles para tu página de inicio. Se ve espectacular en tu monitor de 27 pulgadas. Exportas la imagen desde Figma como PNG (porque es el estándar web según la W3C) y pesa 1.2MB. La subes, la insertas, funciona.

Ahora llega un usuario desde su iPhone 13 en la red 4G del metro. Su pantalla es de 390 píxeles de ancho. Tu imagen de 1920px se está descargando completa (1.2MB) para luego ser reducida por el navegador a 390px de ancho. Estás desperdiciando más del 80% de los píxeles descargados. Ese usuario está esperando 12-15 segundos solo para ver tu hero. Probablemente cierre la pestaña frustrado antes de que termine de cargar.

Ahora imagina que, en cambio, entregas:
- Una versión móvil de 400px de ancho optimizada (85KB)
- Una versión tablet de 800px optimizada (180KB)
- Una versión desktop de 1920px optimizada (420KB)
- Cada una en el formato más eficiente que el navegador soporte

El usuario del iPhone recibe 85KB en vez de 1.2MB. Carga en 2 segundos en vez de 15. La experiencia es completamente diferente.

Esto es lo que vamos a aprender en esta órbita: cómo preparar assets multimedia que estén optimizados para cada contexto, sin sacrificar calidad visual percibida.

### 2. Fundamentos: entendiendo los formatos

#### 2.1. La diferencia fundamental: raster vs vectorial

Antes de hablar de PNG, JPG, WebP o cualquier formato específico, necesitas entender que existen dos formas completamente diferentes de representar imágenes en digital.

**Las imágenes raster** (o de mapa de bits) son como un mosaico: están formadas por una cuadrícula de píxeles, y cada píxel tiene un color específico. Si tienes una foto de 1000×1000 píxeles, esa imagen contiene exactamente un millón de puntos de color. Cuando amplías una imagen raster más allá de su tamaño original, los píxeles individuales se hacen visibles y aparece el efecto "pixelado" que todos conocemos. Las fotografías, las capturas de pantalla, las imágenes con degradados complejos o texturas detalladas son siempre raster.

**Las imágenes vectoriales**, por otro lado, no almacenan píxeles sino fórmulas matemáticas. Un círculo vectorial no es un montón de píxeles rojos formando una forma circular; es una instrucción que dice "dibuja un círculo con centro en X,Y, radio R, y color Z". La ventaja enorme es que puedes escalar un vector infinitamente sin perder calidad: el software simplemente recalcula las formas al nuevo tamaño. Por eso los logotipos, iconos e ilustraciones geométricas funcionan perfectamente como vectores.

En la web moderna usamos ambos tipos, pero cada uno tiene su lugar. Tu logotipo corporativo debería ser SVG (vectorial), escalable desde 16×16 píxeles en un favicon hasta 2 metros en un banner impreso. Pero la foto del equipo en la página "Sobre nosotros" será necesariamente raster.


### 3. Formatos raster: eligiendo con criterio

#### 3.1. PNG: el estándar oficial de la W3C

PNG (Portable Network Graphics) es el formato oficialmente recomendado por la W3C como estándar para imágenes en la web. En junio de 2025, la W3C publicó la tercera edición de la especificación PNG como Recomendación oficial, añadiendo soporte para PNG animado y HDR (High Dynamic Range).

PNG fue diseñado específicamente para web como reemplazo libre de patentes para GIF. Su compresión es sin pérdida, lo que significa que la imagen descomprimida es idéntica al original píxel por píxel. Esta es su gran ventaja cuando necesitas preservar calidad absoluta: textos nítidos, bordes precisos, colores exactos.

La característica más destacada de PNG es su soporte completo de transparencias: a diferencia de GIF que solo puede tener píxeles 100% opacos o 100% transparentes, PNG permite cualquier nivel de opacidad intermedio (canal alpha). Esto lo hace perfecto para logotipos, ilustraciones con sombras suaves, elementos de interfaz que se superponen.

Existen dos variantes principales: **PNG-8** (paleta de 256 colores) y **PNG-24** (millones de colores). Para un icono simple de dos o tres colores, PNG-8 puede pesar 2-3KB. El mismo icono como PNG-24 pesaría 15-20KB sin beneficio visual.

**Cuándo usar PNG:**
- Logotipos con transparencia (cuando no uses SVG)
- Ilustraciones con áreas de color plano y transparencias complejas
- Screenshots de interfaces donde necesitas textos perfectamente nítidos
- Imágenes donde la compresión con pérdida causaría artefactos visibles
- Elementos de interfaz con transparencias graduales

**El trade-off del peso:**
PNG usa compresión sin pérdida, excelente para calidad pero no tan eficiente para peso como formatos modernos. Una fotografía en PNG puede pesar 3-5 veces más que en JPG con calidad 80, sin diferencia visual perceptible. Por eso necesitas combinar PNG con optimización agresiva.

#### 3.2. JPG: perfecto para fotografías

JPEG (o JPG) lleva con nosotros desde 1992 y sigue siendo fundamental. Su compresión "con pérdida" funciona eliminando información que el ojo humano difícilmente detectaría. Los algoritmos JPEG aprovechan que nuestra visión es menos sensible a ciertos cambios de color que a cambios de brillo.

Cuando guardas un JPG, eliges un nivel de calidad típicamente entre 0 y 100. Un JPG al 100% tiene compresión mínima y un peso grande; un JPG al 10% pesa muy poco pero se ve terrible, lleno de "artefactos" (bloques cuadrados, bordes borrosos). El punto dulce para web generalmente está entre 75 y 85: la mayoría de usuarios no notarán diferencia visual respecto al original, pero el archivo puede pesar 5-10 veces menos.

JPG es perfecto para fotografías con muchos colores y detalles. Su gran limitación: no soporta transparencia. Si necesitas un logotipo con fondo transparente, JPG no es una opción.

**Ejemplo práctico:** Tienes una foto de producto de 1200×1200 píxeles. Exportada como PNG sin compresión pesa 3.2MB. Exportada como JPG calidad 85 pesa 280KB. Visualmente es indistinguible para el 99% de usuarios. Has pasado de 3.2MB a 280KB (91% de reducción) sin impacto perceptible.

#### 3.3. WebP: eficiencia moderna

WebP fue desarrollado por Google y lanzado en 2010. Hoy tiene más del 97% de soporte global. Es importante entender que WebP no es un estándar W3C oficial, sino una tecnología desarrollada fuera del proceso de estandarización del W3C.

WebP es básicamente "lo mejor de JPG y PNG juntos": soporta compresión con pérdida (como JPG) y sin pérdida (como PNG), soporta transparencias (como PNG), e incluso puede hacer animaciones (como GIF). Ofrece entre 25-35% mejor compresión que JPG/PNG manteniendo la misma calidad perceptible.

**Ejemplo práctico:** Una foto hero que en JPG calidad 80 pesa 180KB, en WebP calidad 80 pesa aproximadamente 120KB con calidad visual equivalente. Una ilustración con transparencia que en PNG pesa 400KB puede pesar 80KB en WebP sin perder ni un píxel.

WebP también tiene un modo de compresión sin pérdida que genera archivos mucho más pequeños que PNG para el mismo contenido.

#### 3.4. AVIF: máxima eficiencia

AVIF (AV1 Image File Format) es el formato más eficiente que existe actualmente. Al igual que WebP, no es un estándar W3C sino que fue desarrollado por la Alliance for Open Media. Puede conseguir la misma calidad que JPG con la mitad del peso, o la misma que WebP con 30-40% menos peso.

**Ejemplo comparativo real:**
- PNG optimizado: 380KB
- JPG calidad 85: 220KB
- WebP calidad 80: 145KB (34% más ligero que JPG)
- AVIF calidad 75: 85KB (61% más ligero que JPG, 41% más ligero que WebP)

Visualmente, todos son indistinguibles para la mayoría de usuarios.

AVIF soporta transparencias, animación, HDR, y tiene mejor gestión del color. El soporte actual está en torno al 90-92% global: Chrome, Firefox, Edge y Safari modernos (iOS 16+, macOS Ventura+) lo soportan perfectamente.

#### 3.5. La estrategia progressive enhancement

En la web moderna, no tienes que elegir un solo formato. Puedes usar progressive enhancement: ofrecer el formato más eficiente que el navegador soporte, con fallbacks para navegadores antiguos.

```html
<picture>
  <source type="image/avif" srcset="hero.avif">
  <source type="image/webp" srcset="hero.webp">
  <img src="hero.jpg" alt="Hero image">
</picture>
```

Chrome 2025 descarga AVIF (85KB). Safari 2023 descarga WebP (145KB). Navegadores muy antiguos descargan JPG (220KB). Todos ven la misma imagen, optimizada para sus capacidades.

**Consideración práctica:** Para proyectos educativos o pequeños, puedes simplificar usando solo WebP + JPG/PNG, que cubre el 97%+ de usuarios con workflow más simple.

#### 3.6. SVG: el formato vectorial de la web

SVG (Scalable Vector Graphics) no es una imagen, es código XML que describe formas geométricas. Puedes abrirlo con un editor de texto y verás instrucciones como `<circle cx="50" cy="50" r="40" />`.

Las ventajas son enormes:

**Escalabilidad perfecta:** Un SVG de 2KB se ve igual de bien en un icono de 16×16 que en un póster de 2×2 metros. Esto es perfecto para diseño responsive y para pantallas de alta densidad (Retina, 4K). Nunca se pixela porque no hay píxeles, solo fórmulas que se recalculan al tamaño necesario.

**Tamaño de archivo minúsculo:** Un icono complejo en PNG de 64×64 puede pesar 8-12KB. Ese mismo icono en SVG probablemente pesa 1-3KB. Si tienes un sistema de iconos de 50 elementos, la diferencia es entre 400-600KB (PNG) y 50-150KB (SVG).

**Estilizable y animable con CSS:** Puedes cambiar colores, añadir transiciones, modificar formas usando CSS y JavaScript. Un icono de "corazón" que cambia de gris a rojo al hacer hover, una ilustración que se anima al hacer scroll, un gráfico interactivo... todo trivial con SVG.

**Accesibilidad:** Los SVG pueden incluir texto legible por lectores de pantalla, etiquetas semánticas `<title>` y `<desc>`, elementos interactivos con roles ARIA.

**SVG es perfecto para:**
- Logotipos (un logo corporativo debería ser SIEMPRE SVG)
- Iconos de interfaz (menú hamburguesa, flechas, checkmarks)
- Ilustraciones geométricas o con estilo flat design
- Gráficos y visualizaciones de datos

**SVG NO es buena idea para:**
- Fotografías (el archivo sería gigantesco)
- Ilustraciones muy complejas con degradados, texturas, efectos de blur

### 4. Optimización: reduciendo peso sin perder calidad

#### 4.1. El objetivo: calidad percibida vs peso real

Aquí está el secreto del multimedia web: no necesitas calidad perfecta, necesitas calidad **que parezca** perfecta. El ojo humano no puede distinguir entre un PNG sin comprimir y uno optimizado a no ser que los pongas lado a lado y hagas zoom. Y el peso puede ser 3-4 veces menor.

Tu objetivo es encontrar el punto óptimo donde la calidad es indistinguible pero el peso es mínimo. Esto se llama **calidad perceptual** y requiere probar, comparar y ajustar.

#### 4.2. Squoosh: tu herramienta de optimización

Para este curso vamos a usar una única herramienta que te permite controlar todo el proceso de forma visual e interactiva: **Squoosh** (squoosh.app).

Squoosh es una aplicación web gratuita desarrollada por Google que te permite:
- Comparar el original con diferentes versiones optimizadas lado a lado
- Probar múltiples formatos (WebP, AVIF, mozJPG) con ajustes en tiempo real
- Ver el peso resultante actualizado instantáneamente
- Exportar cuando encuentres el balance perfecto entre calidad y peso

**Workflow básico en Squoosh:**

1. **Sube tu imagen** arrastrándola a la ventana del navegador
2. **Ves dos paneles:** izquierda = original, derecha = versión optimizada
3. **Arrastra el slider central** para comparar directamente ambas versiones
4. **Selecciona el formato de salida** en el panel derecho (WebP, AVIF, JPG optimizado)
5. **Ajusta la calidad** moviendo el slider mientras observas el resultado
6. **Mira el peso** actualizado en tiempo real (arriba de cada panel)
7. **Cuando estés satisfecho**, descarga la versión optimizada

**Ejemplo paso a paso:**

Tienes `hero-desktop.png` exportado desde Figma (1920×800, 1.2MB).

1. Subes a Squoosh
2. Panel derecho: seleccionas "WebP" como formato
3. Ajustas calidad a 80% → ves 340KB, visualmente casi idéntico
4. Pruebas 75% → 280KB, sigues sin ver diferencia
5. Pruebas 70% → 245KB, empiezas a notar pequeños artefactos en zonas con degradados
6. Vuelves a 75% → ese es tu punto óptimo
7. Descargas `hero-desktop.webp` (280KB, ahorro del 77%)

Repites el proceso creando versión JPG como fallback:
1. Cambias formato a "MozJPEG" (versión optimizada de JPG)
2. Calidad 80% → 380KB
3. Descargas `hero-desktop.jpg`

**Para múltiples resoluciones:**

Si tienes que exportar la misma imagen en 4 tamaños (400px, 800px, 1200px, 1920px):

1. Primero creas las 4 resoluciones en Figma y las exportas como PNG
2. Procesas cada una en Squoosh individualmente
3. Las imágenes más pequeñas (400px, 800px) pueden usar calidad más baja (70-75%) porque los artefactos son menos visibles
4. Las imágenes grandes (1200px, 1920px) necesitan calidad superior (75-80%)

**Optimización de PNG:**

Aunque PNG es el estándar W3C, sigue necesitando optimización. En Squoosh:

1. Selecciona formato "OxiPNG" (optimizador de PNG)
2. Ajusta el nivel de esfuerzo (mayor nivel = mejor compresión pero más lento)
3. Para ilustraciones simples, activa "Reduce palette" para convertir a PNG-8
4. Puedes conseguir reducciones del 40-60% sin pérdida visual

**Para SVG:**

SVG exportado desde Figma suele contener código innecesario. En Squoosh:

1. Selecciona formato "SVG"
2. Activa las opciones de limpieza (remove metadata, simplify paths)
3. Puedes reducir 50-70% el tamaño

**Comparativa de formatos en Squoosh:**

Una de las mejores features es que puedes comparar formatos fácilmente. Para la misma imagen:

- Original PNG: 1.2MB
- OxiPNG optimizado: 780KB (35% más ligero)
- WebP calidad 75: 280KB (77% más ligero que original)
- AVIF calidad 70: 165KB (86% más ligero que original)
- MozJPG calidad 80: 380KB (68% más ligero que original)

Esto te permite tomar decisiones informadas sobre qué formato usar según tus prioridades (compatibilidad vs peso).

#### 4.3. Estrategia de optimización por tipo de contenido

**Fotografías grandes (hero, banners):**
- Exporta PNG desde Figma en resolución nativa
- Procesa con Squoosh → WebP 75-80% + JPG 80-85% como fallback
- Si el proyecto lo justifica, añade AVIF 70-75%
- Target: <200KB para desktop, <100KB para móvil

**Imágenes de producto con fondo blanco:**
- Exporta PNG desde Figma (para mantener transparencia/fondo limpio)
- Optimiza con OxiPNG en Squoosh
- Alternativamente: WebP con transparencia (aún más ligero)
- Target: <100KB por imagen

**Iconos:**
- Exporta SVG desde Figma con opciones de optimización
- Pasa por Squoosh formato SVG con limpieza activada
- Target: <2KB por icono
- Si algunos quedan muy pesados, considera inline en HTML

**Ilustraciones complejas:**
- Evalúa si SVG tiene sentido (degradados complejos pueden pesar más como vector)
- Si conviertes a raster: WebP o PNG optimizado según necesidad de transparencia
- Target: <200KB

### 5. Imágenes responsive: servir el tamaño correcto

#### 5.1. El problema del "one size fits all"

Durante años, la práctica estándar era simple: tenías una imagen, la insertabas con `<img src="foto.jpg">`, y el navegador la mostraba. Si la imagen era muy grande, el navegador la escalaba. Si era muy pequeña, se veía pixelada. Pero siempre descargabas la misma imagen independientemente del dispositivo.

Esto no tiene sentido en 2025, cuando tus usuarios pueden estar en:
- iPhone SE: 375px de ancho, pantalla Retina (×2)
- iPad Pro: 1024px de ancho, pantalla Retina (×2)
- Desktop Full HD: 1920px de ancho, pantalla normal (×1)
- Desktop 4K: 3840px de ancho, pantalla de alta densidad

Si usas una imagen única, o desperdicias recursos (usuario móvil descarga imagen gigante) o pierdes calidad (usuario 4K ve imagen pixelada).

**Ejemplo numérico:** Diseñas un hero que en desktop ocupa 1200px de ancho. En tablet ocupa 800px. En móvil ocupa 100% del viewport (375px típico).

Si usas imagen única de 1200px:
- Usuario desktop: correcto (descarga 1200px, muestra 1200px)
- Usuario tablet: desperdicio del 33% (descarga 1200px, muestra 800px)
- Usuario móvil: desperdicio del 68% (descarga 1200px, muestra 375px)

No tiene sentido. Necesitamos una forma de decirle al navegador: "Tengo esta imagen en varios tamaños, elige la apropiada según el contexto".

#### 5.2. Atributo srcset: ofreciendo opciones

El atributo `srcset` permite especificar múltiples versiones de la misma imagen y dejar que el navegador elija. La sintaxis básica:

```html
<img 
  src="producto.jpg"
  srcset="
    producto-400.jpg 400w,
    producto-800.jpg 800w,
    producto-1200.jpg 1200w,
    producto-1600.jpg 1600w
  "
  alt="Zapatillas deportivas Nike Air Max"
/>
```

La notación `400w` significa "esta imagen tiene 400 píxeles de ancho físico". No es CSS, es una descripción de la resolución del archivo. El navegador usa esta información para decidir cuál descargar.

**Cómo decide el navegador:**

1. Mira el ancho disponible en el layout
2. Mira la densidad de píxeles de la pantalla (1x, 2x, 3x)
3. Calcula: necesito mostrar X píxeles lógicos en una pantalla Y× = necesito X×Y píxeles reales
4. Elige la imagen más pequeña que cumple o supera esa necesidad

**Ejemplo:** Usuario con iPhone 14 (390px de ancho, pantalla 3x):
- La imagen ocupa 100% del viewport = 390 píxeles lógicos
- Pantalla 3x = necesita 390 × 3 = 1170 píxeles reales
- Navegador elige `producto-1200.jpg` (la más pequeña que cubre 1170px)

**Importante:** El navegador elige, no tú. Le das opciones y él decide basándose en factores que conoce perfectamente: ancho real, densidad, incluso configuración de ahorro de datos del usuario.

#### 5.3. Atributo sizes: comunicando el layout

El problema es que el navegador necesita saber cuánto espacio va a ocupar la imagen en tu diseño. No puede esperar a que el CSS se descargue porque para entonces ya habría tomado la decisión de qué imagen descargar.

El atributo `sizes` le comunica al navegador el tamaño que tendrá la imagen usando media queries:

```html
<img 
  src="producto.jpg"
  srcset="
    producto-400.jpg 400w,
    producto-800.jpg 800w,
    producto-1200.jpg 1200w
  "
  sizes="
    (max-width: 600px) 100vw,
    (max-width: 1200px) 50vw,
    800px
  "
  alt="Zapatillas deportivas Nike Air Max"
/>
```

**Traducción del atributo sizes:**
- "Si el viewport es ≤600px, la imagen ocupa 100% del viewport (`100vw`)"
- "Si el viewport es ≤1200px, la imagen ocupa 50% del viewport (`50vw`)"
- "En viewports mayores, la imagen tiene tamaño fijo de 800px"

Ahora el navegador puede calcular exactamente qué necesita.

#### 5.4. Caso práctico: galería de productos

Imagina que estás maquetando una tienda online. La página de categoría muestra productos en grid:
- **Móvil:** 1 producto por fila (cada imagen ocupa ~100% del ancho)
- **Tablet:** 2 productos por fila (cada imagen ocupa ~48%)
- **Desktop:** 3 productos por fila (cada imagen ocupa ~31%)

Tu CSS:

```css
.productos {
  display: grid;
  gap: 1rem;
  grid-template-columns: 1fr;
}

@media (min-width: 768px) {
  .productos {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1200px) {
  .productos {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

El HTML correspondiente para cada imagen:

```html
<img 
  src="zapatilla-800.jpg"
  srcset="
    zapatilla-400.jpg 400w,
    zapatilla-600.jpg 600w,
    zapatilla-800.jpg 800w,
    zapatilla-1200.jpg 1200w
  "
  sizes="
    (max-width: 767px) 100vw,
    (max-width: 1199px) 48vw,
    31vw
  "
  alt="Nike Air Max 2024 - Color azul marino"
  loading="lazy"
  width="800"
  height="800"
/>
```

**Desglose de escenarios:**

Usuario iPhone SE (375px viewport, 2x):
- Cumple `(max-width: 767px)` → imagen ocupa `100vw` = 375px lógicos
- Pantalla 2x → necesita 750px reales
- Elige `zapatilla-800.jpg`

Usuario iPad (768px viewport, 2x):
- Cumple `(max-width: 1199px)` → imagen ocupa `48vw` = 369px lógicos
- Pantalla 2x → necesita 738px reales
- Elige `zapatilla-800.jpg`

Usuario desktop (1400px viewport, 1x):
- Usa default → imagen ocupa `31vw` = 434px lógicos
- Pantalla 1x → necesita 434px reales
- Elige `zapatilla-600.jpg`

#### 5.5. Atributos importantes para performance

**loading="lazy":**

```html
<img 
  src="imagen.jpg" 
  alt="Descripción"
  loading="lazy"
/>
```

`loading="lazy"` hace que el navegador solo descargue la imagen cuando esté cerca de aparecer en viewport. En una página con 50 imágenes, esto puede acelerar la carga inicial dramáticamente.

**width y height para evitar layout shift:**

```html
<img 
  src="foto.jpg" 
  width="800" 
  height="600"
  alt="Descripción"
/>
```

Especificar dimensiones permite al navegador reservar el espacio correcto antes de que la imagen cargue, evitando que la página "salte" (layout shift). Esto mejora CLS (Cumulative Layout Shift), una métrica Core Web Vital importante.

### 6. Dirección de arte: diferentes composiciones para diferentes contextos

#### 6.1. Más allá del simple resize

Hasta ahora hemos hablado de imágenes responsive donde ofreces **la misma composición** en diferentes tamaños. Pero a veces escalar no es suficiente. A veces necesitas cambiar la composición misma: hacer zoom en un sujeto, cambiar el crop, rotar la orientación.

Esto se llama **dirección de arte** (art direction) y es una herramienta fundamental del diseño responsive profesional.

**Ejemplo clásico:** Tienes una foto panorámica de 1920×600 para el hero de escritorio. Muestra un paisaje de montaña con una persona en el centro practicando escalada, rocas a la izquierda, valle a la derecha. Se ve espectacular en pantalla ancha.

Ahora reduces esa imagen proporcionalmente para móvil (375×117). La persona queda microscópica, los detalles se pierden, es difícil entender qué estás mirando. No funciona.

Lo que necesitas es una versión móvil con crop vertical (375×667) que hace zoom en la persona, manteniendo el sujeto como protagonista visible. Esto no es simplemente "la misma imagen en diferente tamaño", es **una composición diferente de la misma escena**.

#### 6.2. El elemento `<picture>`: contenedor para múltiples fuentes

Para implementar dirección de arte usamos el elemento `<picture>`, que funciona como contenedor que puede incluir múltiples `<source>` con condiciones:

```html
<picture>
  <source 
    media="(max-width: 767px)" 
    srcset="hero-mobile-portrait.jpg"
  />
  <source 
    media="(min-width: 768px)" 
    srcset="hero-desktop-landscape.jpg"
  />
  <img 
    src="hero-desktop-landscape.jpg" 
    alt="Escalador en montaña al amanecer"
  />
</picture>
```

**Cómo funciona:**

1. El navegador evalúa cada `<source>` en orden de arriba abajo
2. Usa el primero cuya media query coincida con el contexto actual
3. Si ninguno coincide, usa el `<img>` del final como fallback

**Elemento `<img>` obligatorio:** Aunque uses `<picture>`, dentro SIEMPRE debe haber un `<img>`. Este elemento es el que realmente renderiza la imagen; `<picture>` y `<source>` solo controlan cuál se usa.

#### 6.3. Ejemplo real: hero responsive con dirección de arte

**Contexto:** Página de inicio de una agencia de viajes de aventura. El hero muestra personas haciendo kayak en un lago rodeado de montañas.

**Diseño en Figma:**
- **Desktop (1920×800):** Composición horizontal amplia. Kayaks en el centro-izquierda, montañas en el fondo, cielo ocupando tercio superior.
- **Tablet (1024×600):** Composición similar pero más cerrada. Menos cielo, enfoque en los kayaks.
- **Mobile (375×667):** Composición vertical. Crop cerrado en un solo kayak, montaña de fondo, casi sin cielo. Orientación portrait.

**Paso 1: Exportar las composiciones desde Figma**

Para cada composición, exportamos en múltiples resoluciones:

Mobile:
- `hero-mobile-400.png` (400×711)
- `hero-mobile-750.png` (750×1333)

Tablet:
- `hero-tablet-1024.png` (1024×600)
- `hero-tablet-2048.png` (2048×1200)

Desktop:
- `hero-desktop-1920.png` (1920×800)
- `hero-desktop-2560.png` (2560×1067)

**Paso 2: Optimizar cada imagen en Squoosh**

Mobile:
- `hero-mobile-400.png` → Squoosh → WebP 75% → `hero-mobile-400.webp` (45KB)
- `hero-mobile-400.png` → Squoosh → MozJPG 80% → `hero-mobile-400.jpg` (68KB)
- Repetir para versión 750px

Tablet y Desktop: mismo proceso, ajustando calidad según tamaño (más grandes usan calidad ligeramente superior).

**Paso 3: Implementar con `<picture>`**

```html
<picture>
  <!-- Mobile: WebP + JPG fallback -->
  <source 
    media="(max-width: 767px)" 
    type="image/webp"
    srcset="
      hero-mobile-400.webp 400w,
      hero-mobile-750.webp 750w
    "
    sizes="100vw"
  />
  <source 
    media="(max-width: 767px)" 
    srcset="
      hero-mobile-400.jpg 400w,
      hero-mobile-750.jpg 750w
    "
    sizes="100vw"
  />
  
  <!-- Tablet: WebP + JPG fallback -->
  <source 
    media="(min-width: 768px) and (max-width: 1199px)" 
    type="image/webp"
    srcset="
      hero-tablet-1024.webp 1024w,
      hero-tablet-2048.webp 2048w
    "
    sizes="100vw"
  />
  <source 
    media="(min-width: 768px) and (max-width: 1199px)" 
    srcset="
      hero-tablet-1024.jpg 1024w,
      hero-tablet-2048.jpg 2048w
    "
    sizes="100vw"
  />
  
  <!-- Desktop: WebP + JPG fallback -->
  <source 
    type="image/webp"
    srcset="
      hero-desktop-1920.webp 1920w,
      hero-desktop-2560.webp 2560w
    "
    sizes="100vw"
  />
  
  <!-- Fallback final -->
  <img 
    src="hero-desktop-1920.jpg"
    srcset="
      hero-desktop-1920.jpg 1920w,
      hero-desktop-2560.jpg 2560w
    "
    sizes="100vw"
    alt="Aventureros haciendo kayak en lago de montaña al amanecer"
    width="1920"
    height="800"
  />
</picture>
```

**Qué hace este código:**

Usuario iPhone 14 (Chrome):
1. Viewport 390px → cumple `(max-width: 767px)`
2. Navegador entiende WebP → usa primer `<source>` móvil
3. Pantalla 3x, necesita ~1170px → elige `hero-mobile-750.webp`

Usuario iPad Pro (Safari):
1. Viewport 1024px → cumple media query tablet
2. Safari moderno entiende WebP → usa `<source>` tablet WebP
3. Pantalla 2x → elige `hero-tablet-2048.webp`

Usuario desktop (Edge):
1. Viewport 1920px → no cumple condiciones móvil/tablet
2. Edge entiende WebP → usa `<source>` desktop WebP
3. Pantalla 1x → elige `hero-desktop-1920.webp`

**Resultado:** Cada usuario recibe la composición apropiada para su dispositivo, en el formato más eficiente que su navegador soporta, en la resolución justa que necesita.

### 7. Flujo de trabajo: de Figma a producción

#### 7.1. Preparación en Figma: nomenclatura y organización

Antes de exportar, tu archivo Figma necesita estar organizado.

**Nomenclatura sistemática:**

```
hero-desktop-main
hero-tablet-main
hero-mobile-main

product-card-thumbnail
product-detail-gallery-01

icon-menu-hamburger
icon-cart-24
icon-user-32
```

Evita nombres autogenerados tipo "Rectangle 47". En 6 meses no sabrás qué es qué.

**Frames en tamaños reales:**

Si vas a exportar una imagen de 800px para web, el frame en Figma debería medir 800px. Diseña a 1x y deja que Figma escale al exportar múltiples densidades.

#### 7.2. Configuración de exportación en Figma

Selecciona el elemento, ve al panel "Export" en la sidebar derecha.

**Para fotografías:**
```
1x → PNG
2x → PNG
```

Luego optimizas en Squoosh.

**Para iconos:**
```
SVG (con "Outline text" activado)
```

Luego optimizas en Squoosh.

**Nomenclatura de archivos:**

Figma añade `@2x` automáticamente. Si exportas "logo" a 2x, genera `logo@2x.png`.

Puedes renombrar después según tu convención:
- `logo-800.png` y `logo-1600.png`
- O mantener `logo.png` y `logo@2x.png`

La consistencia importa más que la convención específica.

#### 7.3. Proceso completo para proyecto

**Ejemplo: página de producto**

1. **Organiza en Figma:**
    - Frame "Product Hero Desktop" (1920×800)
    - Frame "Product Hero Tablet" (1024×600)
    - Frame "Product Hero Mobile" (375×667)
    - 6 frames "Product Gallery" (800×800 cada uno)
    - 12 iconos de features

2. **Exporta desde Figma:**
    - Heroes: PNG 1x y 2x
    - Galería: PNG 1x y 2x
    - Iconos: SVG

3. **Optimiza con Squoosh:**
    - Cada hero → WebP + JPG
    - Cada imagen galería → WebP + JPG
    - Cada icono SVG → optimizar con limpieza

4. **Organiza en carpeta del proyecto:**
   ```
   /assets
     /images
       /hero
         hero-desktop-1920.webp
         hero-desktop-1920.jpg
         hero-mobile-400.webp
         hero-mobile-400.jpg
         ...
       /products
         producto-01-800.webp
         producto-01-800.jpg
         producto-01-1600.webp
         ...
     /icons
       cart.svg
       user.svg
       menu.svg
   ```

---


