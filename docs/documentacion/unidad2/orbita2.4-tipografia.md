---
hide:
  - navigation
---

# Órbita 2: Diseñar para que se entienda

## 3. Tipografía

### La tipografía es el 95% del diseño web

Esta no es una exageración. Si analizas cualquier interfaz web, te darás cuenta de que la mayor parte del contenido es texto: títulos, párrafos, botones, formularios, menús, labels, mensajes de error, notificaciones. Incluso en aplicaciones muy visuales como Instagram o Pinterest, el texto estructura toda la experiencia. Por eso, si tu tipografía no funciona, tu diseño no funciona. Punto.

La tipografía funcional no se trata de elegir "la fuente más bonita". Se trata de legibilidad, jerarquía, coherencia y propósito. Una buena tipografía es invisible: el usuario lee sin esfuerzo, entiende la estructura de la información, sabe qué es importante y qué es secundario. Una mala tipografía es fricción constante: letras demasiado pequeñas, contraste insuficiente, jerarquía confusa, mezcla caótica de estilos.

### Clasificación básica de fuentes

Entender los tipos de fuentes te ayuda a elegir con criterio, no al azar:

**Serif (con remates)**
- Tienen pequeñas líneas o "patitas" al final de cada trazo
- **Ejemplos**: Times New Roman, Georgia, Playfair Display, Lora
- **Transmiten**: Tradición, elegancia, seriedad, autoridad
- **Uso típico**: Medios impresos, marcas clásicas, contenido editorial largo
- **En web**: Funcionan bien para títulos grandes, pero cuidado en cuerpos de texto pequeños (pueden cansar en pantalla)

**Sans-serif (sin remates)**
- Líneas limpias sin adornos
- **Ejemplos**: Arial, Helvetica, Inter, Roboto, Open Sans
- **Transmiten**: Modernidad, claridad, neutralidad, simplicidad
- **Uso típico**: Interfaces digitales, apps, webs modernas
- **En web**: Son la opción más segura para texto de cuerpo, especialmente en tamaños pequeños

**Monoespaciada (monospaced)**
- Cada letra ocupa exactamente el mismo ancho
- **Ejemplos**: Courier, Fira Code, JetBrains Mono
- **Transmiten**: Técnico, código, datos, precisión
- **Uso típico**: Mostrar código, tablas de datos, terminales
- **En web**: Úsala solo cuando muestres código o datos técnicos. No para texto normal.

**Display o decorativas**
- Diseñadas para tamaños grandes, con mucha personalidad
- **Ejemplos**: Bebas Neue, Righteous, Abril Fatface
- **Transmiten**: Creatividad, impacto, diferenciación
- **Uso típico**: Logos, títulos hero muy grandes, carteles
- **Precaución**: No uses en cuerpo de texto. No uses más de una display en el mismo proyecto.

### Elegir tipografías para tu proyecto

No necesitas diez fuentes. Necesitas **dos o tres como máximo**, bien elegidas y bien usadas.

**Estructura recomendada:**

**Opción 1: Una fuente para todo**
- Usa una sola familia tipográfica con muchos pesos (Light, Regular, Medium, Semibold, Bold, Black)
- Crea contraste solo con tamaño y peso
- **Ventaja**: Máxima cohesión, menos archivos que cargar
- **Recomendadas**: Inter, Poppins, Manrope, Work Sans

**Ejemplo:**
```
Título grande: Poppins Black 48px
Título sección: Poppins Bold 32px
Subtítulo: Poppins Semibold 20px
Texto cuerpo: Poppins Regular 16px
Texto pequeño: Poppins Regular 14px
```

**Opción 2: Una para títulos, otra para cuerpo**
- Fuente expresiva para headings, fuente neutra para body
- Crea contraste entre diferentes familias
- **Ventaja**: Más personalidad visual, estructura clara
- **Precaución**: Las fuentes deben complementarse, no competir

**Combinaciones que funcionan:**
- **Serif + Sans-serif** (contraste clásico)
  - Títulos: Playfair Display (serif elegante)
  - Cuerpo: Inter (sans-serif moderna)

- **Sans-serif expresiva + Sans-serif neutra**
  - Títulos: Montserrat Bold
  - Cuerpo: Open Sans

- **Display + Sans-serif neutra**
  - Títulos: Bebas Neue (muy impactante)
  - Cuerpo: Roboto (muy legible)

**Criterios para elegir tu fuente de títulos:**
- Que tenga varios pesos (Light, Regular, Bold como mínimo)
- Que funcione bien en tamaños grandes (48px+)
- Que tenga personalidad pero no canse
- Que represente la identidad de tu proyecto

**Criterios para elegir tu fuente de cuerpo:**
- **Legibilidad ante todo**. Si no se lee bien en 16px, descártala
- Que tenga x-height generoso (las minúsculas no deben verse aplastadas)
- Que funcione bien en tamaños pequeños (14-16px)
- Que tenga varios pesos (necesitas Regular, Medium, Bold)

**Fuentes de cuerpo probadas y seguras:**
- **Inter**: Diseñada específicamente para pantallas, excelente legibilidad
- **Open Sans**: Clásica, versátil, funciona en todo
- **Roboto**: La fuente de Android, muy probada en interfaces
- **System fonts**: Usar las fuentes del sistema operativo (San Francisco en Mac, Segoe UI en Windows) es una opción válida y rápida

### Sistema de jerarquía tipográfica

Define tu escala tipográfica **antes** de diseñar. Esto no es opcional. Sin una escala clara, cada pantalla se convertirá en una decisión arbitraria de "¿qué tamaño pongo aquí?".

**Escala recomendada:**

```
H1 - Título principal de página
  Tamaño: 48px / 3rem
  Peso: Bold (700)
  Line-height: 1.2
  Uso: Solo 1 por página, el título más importante

H2 - Títulos de sección
  Tamaño: 36px / 2.25rem
  Peso: Bold (700)
  Line-height: 1.3
  Uso: Divide contenido en bloques principales

H3 - Subtítulos
  Tamaño: 24px / 1.5rem
  Peso: Semibold (600)
  Line-height: 1.4
  Uso: Dentro de secciones, jerarquía terciaria

H4 - Subtítulos pequeños
  Tamaño: 20px / 1.25rem
  Peso: Semibold (600)
  Line-height: 1.4
  Uso: Cuando necesitas más niveles de jerarquía

Body Large - Párrafos destacados
  Tamaño: 18px / 1.125rem
  Peso: Regular (400)
  Line-height: 1.6
  Uso: Introducciones, lead paragraphs, textos importantes

Body Regular - Texto principal
  Tamaño: 16px / 1rem
  Peso: Regular (400)
  Line-height: 1.5
  Uso: Contenido general, el 80% de tu texto

Body Small - Texto secundario
  Tamaño: 14px / 0.875rem
  Peso: Regular (400)
  Line-height: 1.5
  Uso: Metadatos, descripciones cortas, labels

Caption - Textos mínimos
  Tamaño: 12px / 0.75rem
  Peso: Regular (400)
  Line-height: 1.4
  Uso: Etiquetas, timestamps, texto legal, footnotes
```

**Reglas de oro para line-height (interlineado):**

El line-height controla el espacio vertical entre líneas de texto. Es crítico para la legibilidad:

- **Texto pequeño (12-16px)**: 1.5 - 1.6
- **Texto medio (16-20px)**: 1.5
- **Títulos grandes (24px+)**: 1.2 - 1.3
- **Nunca menos de 1.4** (dificulta la lectura)
- **Texto más ancho necesita más line-height**

**Reglas para longitud de línea:**

La longitud de línea (cuántos caracteres caben en una línea) afecta directamente la comodidad de lectura:

- **Óptimo**: 50-75 caracteres por línea
- **Máximo aceptable**: 90 caracteres
- **Menos de 40**: Lectura entrecortada, saltos constantes
- **Más de 100**: El ojo se pierde al volver al inicio de la siguiente línea

**Cómo controlar la longitud:** Usa `max-width` en tus contenedores de texto. Ejemplo: `max-width: 65ch` (65 caracteres).

**Contraste de peso:**

Si tus títulos usan Bold (700), tu texto debe usar Regular (400). El contraste de peso crea jerarquía visual automática. No uses Light (300) en textos pequeños, se lee fatal.

**Tamaños mínimos:**

- **Texto principal**: Nunca menos de 16px (en móvil considera 17-18px)
- **Texto secundario**: Nunca menos de 14px
- **Texto legal/footnotes**: 12px mínimo absoluto

### Implementación en Figma

Define tus Text Styles en Figma desde el principio:

1. **Crea un Text Style para cada nivel**: Heading 1, Heading 2, Heading 3, Body, Body Small, Caption
2. **Asigna todo**: Familia, tamaño, peso, line-height, alineación
3. **Nómbralos claramente**: "H1 / Display" o "Body / Regular"
4. **Úsalos siempre**: Si un texto es un H2, aplica el Text Style H2. Sin excepciones.

**Ventaja**: Si cambias de fuente o ajustas tamaños después, actualizas el Text Style y se propaga automáticamente a toda la interfaz.

### Dónde encontrar fuentes

**Gratuitas y optimizadas para web:**
- **[Google Fonts](https://fonts.google.com)**: La opción más común, gratuitas, bien optimizadas
- **[Adobe Fonts](https://fonts.adobe.com)**: Si tienes Adobe CC
- **[Font Squirrel](https://www.fontsquirrel.com)**: Fuentes gratuitas con licencia comercial clara

**Tip**: Filtra por "Number of styles". Necesitas fuentes con al menos 4-5 pesos diferentes (Regular, Medium, Semibold, Bold).

### Para profundizar

**Artículos en español:**

- **Tipografía en el diseño web: claves para una mejor legibilidad** (Koncept Creativo) - Explica los fundamentos de legibilidad, espaciado e interlineado aplicados a web.
  [Ver artículo](https://www.koncept.es/tipografia-diseno-web-legibilidad/)

- **El papel de la tipografía en el diseño web** (Cámara de Comercio de Sevilla) - Cómo la tipografía afecta la percepción y la identidad de marca.
  [Ver artículo](https://en.camaradesevilla.com/tipografia/)

**Artículos en inglés:**

- **Butterick's Practical Typography** - La guía definitiva de tipografía, con sección específica para web. Referencia obligada.
  [Ver recurso](https://practicaltypography.com)

**Documentales:**

- **Abstract: The Art of Design - Season 2, Episode 6: Jonathan Hoefler: Typeface Design** (Netflix) - Documental imprescindible que muestra el proceso completo de diseño de tipografías por uno de los diseñadores de tipos más importantes del mundo. Hoefler (creador de las tipografías de Apple, Obama's "Change" campaign, y muchísimas más) explica conceptos como kerning, ligaduras, optical adjustments y todo el trabajo que hay detrás de cada letra. Incluye segmentos didácticos llamados "These Are Letters!" donde se explican principios tipográficos con efectos físicos. Es fascinante y educativo.
  [Ver en Netflix](https://www.netflix.com/title/80057883)

- **Abstract: The Art of Design - Season 1, Episode 6: Paula Scher: Graphic Design** (Netflix) - Paula Scher, diseñadora legendaria de Pentagram, habla sobre su trabajo con tipografía en branding. Famosa por su frase "Typography is painting with words". Muestra proyectos como el Public Theater de Nueva York y su enfoque del diseño tipográfico en sistemas de marca.
  [Ver en Netflix](https://www.netflix.com/title/80057883)
