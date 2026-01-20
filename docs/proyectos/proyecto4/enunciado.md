# Proyecto Órbita 4: Diseñar para todo el mundo

## Contexto del proyecto

Este proyecto representa el **momento de la verdad de la accesibilidad**. Hasta ahora habéis construido la estructura funcional, aplicado la capa visual y maquetado en código. Ahora toca verificar que lo que habéis creado realmente funciona para **todas las personas**, independientemente de sus capacidades o dispositivos.

Vais a añadir un elemento multimedia simple a vuestro proyecto y someterlo a un análisis práctico de accesibilidad. Ya habéis hecho mucha documentación en el Proyecto 3, así que aquí el foco es **auditar, corregir y verificar**.

---

## Resultados de Aprendizaje

### RA4: Integrar contenido multimedia (30%)
- **RA4.e:** Agregar elementos multimedia
- **RA4.f:** Añadir interactividad
- **RA4.g:** Verificar funcionamiento cross-browser

### RA5: Desarrollar interfaces accesibles (70%)
- **RA5.a:** Reconocer la necesidad de diseñar webs accesibles
- **RA5.b:** Analizar la accesibilidad de diferentes documentos web
- **RA5.c:** Analizar los principios y pautas WCAG
- **RA5.d:** Analizar errores de accesibilidad
- **RA5.e:** Alcanzar conformidad WCAG
- **RA5.f:** Verificar con herramientas externas
- **RA5.g:** Verificar con tecnologías asistivas

---

## El proyecto

### Parte 1: Añadir multimedia (1h)

Añade **UNO** de estos elementos a tu proyecto:

**Opción A - Galería:**
- 4-6 imágenes con `<figure>` y `<figcaption>`
- Alt text descriptivo
- Lazy loading: `<img loading="lazy">`

**Opción B - Video:**
- Video HTML5 con controles nativos
- Subtítulos .vtt
- Transcripción en texto

**Opción C - Carrusel:**
- Botones anterior/siguiente
- Navegación con teclado
- Indicador de posición




### Parte 2: Análisis de accesibilidad (4h)

Crear un único documento en `docs/accesibilidad/README.md`.


## Entregables

### Estructura del repositorio

```
proyecto-4/             
├── src/
├── docs/
│   └── accesibilidad/
│       ├── README.md          # Documento único
│       └── capturas/          # Todas las capturas
│           ├── lighthouse-antes.png
│           ├── lighthouse-despues.png
│           ├── wave-antes.png
│           ├── wave-despues.png
│           ├── taw.png
│           ├── chrome.png
│           ├── firefox.png
│           └── safari.png
└── README.md
```

---

## Documento único: `docs/accesibilidad/README.md`

```markdown
# Análisis de Accesibilidad

## 1. Introducción

### ¿Por qué accesibilidad?
[50-75 palabras sobre tipos de discapacidad y beneficios para todos]

### Principios WCAG 2.1
1. **Perceptible** - Ejemplo: [tu ejemplo]
2. **Operable** - Ejemplo: [tu ejemplo]
3. **Comprensible** - Ejemplo: [tu ejemplo]
4. **Robusto** - Ejemplo: [tu ejemplo]

**Objetivo:** Nivel AA

---

## 2. Componente multimedia

**Tipo:** [Galería/Video/Carrusel]

**Características accesibles:**
- [Característica 1]
- [Característica 2]
- [Característica 3]


## 3. Auditoría automatizada

### Herramientas
- Lighthouse
- WAVE
- TAW

### Resultados iniciales

| Herramienta | Puntuación/Errores | Captura |
|-------------|-------------------|---------|
| Lighthouse | [X]/100 | ![](./capturas/lighthouse-antes.png) |
| WAVE | [X] errores | ![](./capturas/wave-antes.png) |
| TAW | [X] problemas | ![](./capturas/taw.png) |


## 4. Errores encontrados y correcciones

### Resumen

| # | Error | WCAG | Herramienta | Solución |
|---|-------|------|-------------|----------|
| 1 | [Breve] | 1.1.1 | WAVE | [Breve] |
| 2 | [Breve] | X.X.X | Lighthouse | [Breve] |
| 3 | [Breve] | X.X.X | TAW | [Breve] |
| 4 | [Breve] | X.X.X | WAVE | [Breve] |
| 5 | [Breve] | X.X.X | Lighthouse | [Breve] |

### Detalle de errores

#### Error #1: [Título]
**Problema:** [Qué estaba mal]  
**Impacto:** [A quién afecta]

```html
<!-- ANTES -->
[código con error]
```

```html
<!-- DESPUÉS -->
[código corregido]
```

#### Error #2: [Título]
[Misma estructura]

#### Error #3: [Título]
[Misma estructura]

#### Error #4: [Título]
[Misma estructura]

#### Error #5: [Título]
[Misma estructura]


## 5. Análisis de estructura

### Landmarks
- [x] `<header>`
- [x] `<nav>`
- [x] `<main>`
- [ ] `<article>`
- [x] `<footer>`

### Encabezados
```
H1: [título]
  H2: [sección]
  H2: [sección]
```

### Imágenes
- Total: [X]
- Con alt: [X]
- Sin alt corregidas: [X]


## 6. Verificación manual

### Test de teclado

- [x] Navegación completa con Tab
- [x] Orden lógico
- [x] Focus visible
- [x] Multimedia funciona con teclado
- [x] Sin trampas

**Problemas:** [Ninguno / Descripción]

### Test con lector de pantalla

**Herramienta:** [NVDA/VoiceOver]

| Aspecto | ✅/⚠️/❌ | Observación |
|---------|---------|-------------|
| Estructura clara | ✅ | [Breve] |
| Landmarks | ✅ | [Breve] |
| Imágenes descritas | ✅ | [Breve] |
| Enlaces descriptivos | ✅ | [Breve] |
| Multimedia accesible | ✅ | [Breve] |

### Cross-browser

| Navegador | Layout | Multimedia | Notas |
|-----------|--------|------------|-------|
| Chrome | ✅ | ✅ | ![](./capturas/chrome.png) |
| Firefox | ✅ | ✅ | ![](./capturas/firefox.png) |
| Safari | ✅ | ✅ | ![](./capturas/safari.png) |


## 7. Resultados finales

### Puntuaciones finales

| Herramienta | Antes | Después | Mejora |
|-------------|-------|---------|--------|
| Lighthouse | [X] | [X] | +[X] |
| WAVE | [X] | [X] | -[X] |
| TAW | [X] | [X] | -[X] |

**Capturas:**
- Lighthouse: ![](./capturas/lighthouse-despues.png)
- WAVE: ![](./capturas/wave-despues.png)

### Conformidad WCAG 2.1 AA

**Perceptible:**
- [x] 1.1.1 Contenido no textual
- [x] 1.3.1 Info y relaciones
- [x] 1.4.3 Contraste (4.5:1)
- [x] 1.4.4 Texto redimensionable

**Operable:**
- [x] 2.1.1 Teclado
- [x] 2.1.2 Sin trampas
- [x] 2.4.7 Focus visible

**Comprensible:**
- [x] 3.1.1 Idioma (lang="es")

**Robusto:**
- [x] 4.1.2 Nombre, función, valor

**Nivel:** [A / AA / AA parcial]


## 8. Conclusiones

### ¿Es accesible mi proyecto?
[100-150 palabras de reflexión honesta]

### Mejoras aplicadas
1. [Mejora importante]
2. [Mejora importante]
3. [Mejora importante]

### Mejoras futuras
1. [Qué harías con más tiempo]
2. [Qué harías con más tiempo]

### Aprendizaje clave
[2-3 frases sobre lo más importante aprendido]

---

## Recursos

- [Lighthouse](https://developers.google.com/web/tools/lighthouse)
- [WAVE](https://wave.webaim.org/extension/)
- [TAW](https://www.tawdis.net/?lang=es)
- [NVDA](https://www.nvaccess.org/)
- [WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
```

---

## README.md del proyecto (raíz)

```markdown
# Proyecto 4 - Accesibilidad

## Componente multimedia
[Galería/Video/Carrusel]: [descripción 1 línea]

## Resultados

| Herramienta | Antes | Después | Mejora |
|-------------|-------|---------|--------|
| Lighthouse | [X]/100 | [X]/100 | +[X] |
| WAVE | [X] | [X] | -[X] |

**Nivel:** WCAG 2.1 [A/AA/AA parcial]

## Documentación
📄 [Análisis completo](./docs/accesibilidad/README.md)

## Verificación
- ✅ Lighthouse, WAVE, TAW
- ✅ [NVDA/VoiceOver]
- ✅ Navegación teclado
- ✅ Chrome, Firefox, Safari

## Autor
[Tu nombre]
```

---

## Rúbrica de evaluación

| Criterio | 10 | 7.5 | 5 | 2.5 | 0 |
|----------|-----|-----|---|-----|---|
| **RA5.a+c - Fundamentos** | Intro completa (50-75 pal). 4 principios con ejemplos. | Intro y principios explicados. | Explicación básica. | Superficial. | Sin intro. |
| **RA4.e-f-g - Multimedia** | Multimedia accesible. 3 navegadores con capturas. | Multimedia accesible. 2-3 navegadores. | Básico funcional. | Con errores. | Sin multimedia. |
| **RA5.d - Errores** | 5 errores con antes/después. Tabla resumen + detalle. | 5 errores documentados. | 3-4 errores. | Pocos errores. | Sin errores. |
| **RA5.f - Test externos** | 3 herramientas. Capturas antes/después. Mejora cuantificada. | 3 herramientas. Capturas. | 2 herramientas. | 1 herramienta. | Sin test. |
| **RA5.b+e - Análisis** | Estructura completa. Checklist WCAG. Lighthouse 85+. | Análisis completo. Lighthouse 75+. | Análisis básico. 65+. | Superficial. | Sin análisis. |
| **RA5.g - Verificación** | NVDA/VO + teclado + 3 navegadores. Tabla completa. | Lector + teclado + 3 nav. | Lector O teclado. 2 nav. | Superficial. | Sin verificación. |
| **Organización** | 1 MD bien estructurado. 8 capturas. Markdown perfecto. | Bien estructurado. Capturas. | Estructura básica. | Desorganizado. | Sin estructura. |

---

## Recursos

**Herramientas:**
- Lighthouse (F12 → Chrome DevTools)
- WAVE: https://wave.webaim.org/extension/
- TAW: https://www.tawdis.net/?lang=es
- NVDA: https://www.nvaccess.org/

**Referencias:**
- WCAG 2.1: https://www.w3.org/WAI/WCAG21/quickref/
- Accesible.es: https://accesible.es
