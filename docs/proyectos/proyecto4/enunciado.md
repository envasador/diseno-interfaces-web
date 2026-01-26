# Proyecto Órbita 4: Diseñar para todos

## Contexto del proyecto

Este proyecto representa el **momento de la verdad de la accesibilidad**. Hasta ahora habéis construido la estructura funcional, aplicado la capa visual y maquetado en código. Ahora toca verificar que lo que habéis creado realmente funciona para **todas las personas**, independientemente de sus capacidades o dispositivos.

Vais a añadir un elemento multimedia simple a vuestro proyecto y someterlo a un análisis práctico de accesibilidad. Ya habéis hecho mucha documentación en el Proyecto 3, así que aquí el foco es **auditar, corregir y verificar**.

---

## Resultados de Aprendizaje y Criterios de Evaluación

### RA4: Integrar contenido multimedia e interactivo
- **RA4.e (2.81%):** Agregar elementos multimedia a documentos web
- **RA4.f (2.81%):** Añadir interactividad a elementos de un documento web
- **RA4.g (2.81%):** Verificar el funcionamiento de los elementos multimedia e interactivos en distintos navegadores y dispositivos

### RA5: Desarrollar interfaces web accesibles
- **RA5.a (2.70%):** Reconocer la necesidad de diseñar webs accesibles
- **RA5.b (2.70%):** Analizar la accesibilidad de diferentes documentos web
- **RA5.c (2.70%):** Analizar los principios y pautas de accesibilidad al contenido (WCAG)
- **RA5.d (2.70%):** Analizar los posibles errores según los puntos de verificación de prioridad
- **RA5.e (2.70%):** Alcanzar el nivel de conformidad deseado
- **RA5.f (2.70%):** Verificar los niveles alcanzados mediante el uso de test externos
- **RA5.g (2.70%):** Verificar la visualización del interfaz con diferentes navegadores y tecnologías

---

## Descripción de las tareas

### Tarea 1: Implementar componente multimedia.

**Objetivo:** Añadir un elemento multimedia accesible a tu proyecto.

**Elige UNA de estas opciones:**

#### Opción A: Galería de imágenes
- 4-6 imágenes usando `<figure>` y `<figcaption>`
- Texto alternativo descriptivo en cada imagen (no genérico)
- Implementar lazy loading: `<img loading="lazy">`

#### Opción B: Reproductor de video
- Video HTML5 con controles nativos
- Archivo de subtítulos en formato WebVTT (.vtt)
- Transcripción completa en texto plano debajo del video

#### Opción C: Carrusel/Slider
- Botones de navegación anterior/siguiente
- Navegación funcional con teclado (flechas o Tab + Enter)
- Indicador visual de posición actual (ej: "3/8")

**Entregable:** Componente multimedia integrado y funcional en tu proyecto.

**Criterios evaluados:** RA4.e, RA4.f

---

### Tarea 2: Crear documentación de accesibilidad (4 horas)

**Objetivo:** Analizar la accesibilidad de tu proyecto completo y documentarlo en un único archivo Markdown.

**Ubicación:** `docs/accesibilidad/README.md`

**Estructura del documento: La que a contunación se detalla con 8 secciones.**


#### **Sección 1: Fundamentos de accesibilidad**

**Qué debes incluir:**

1. **¿Por qué es necesaria la accesibilidad web?** (50-75 palabras)
    - Menciona tipos de discapacidades (visual, auditiva, motora, cognitiva)
    - Explica cómo beneficia a todos los usuarios
    - Menciona la obligatoriedad legal en España/Europa

2. **Los 4 principios de WCAG 2.1**

   Para cada principio, escribe:
    - Nombre del principio
    - Explicación breve (1 frase)
    - **Un ejemplo concreto** de tu proyecto o tu vida diaria

   Ejemplo:
   ```markdown
   1. **Perceptible:** La información debe poder percibirse
      - Ejemplo: Las imágenes de mi galería tienen texto alternativo para usuarios ciegos
   ```

3. **Niveles de conformidad**
    - Explica brevemente qué son los niveles A, AA y AAA
    - Indica que el objetivo del proyecto es **nivel AA**

**Recursos para consultar:**
- https://www.w3.org/WAI/fundamentals/accessibility-intro/es
- https://accesible.es

**Criterios evaluados:** RA5.a, RA5.c

---

#### **Sección 2: Componente multimedia implementado**

**Qué debes incluir:**

1. **Tipo de componente:** [Galería / Video / Carrusel]
2. **Descripción breve:** Qué hace el componente (2-3 líneas)
3. **Características de accesibilidad implementadas:**
    - Lista de 3-4 características que lo hacen accesible
    - Ejemplo: "Todas las imágenes tienen alt descriptivo", "Se puede navegar con teclado"

**Criterio evaluado:** RA4.e, RA4.f

---

#### **Sección 3: Auditoría automatizada inicial**

**Qué debes hacer:**

1. **Ejecutar 3 herramientas de análisis:**

   **Lighthouse (Chrome DevTools):**
    - Abre tu proyecto en Chrome
    - Pulsa F12 → pestaña "Lighthouse"
    - Marca solo "Accessibility"
    - Click en "Analyze page load"
    - Guarda captura de pantalla del informe

   **WAVE (Extensión de navegador):**
    - Instala desde: https://wave.webaim.org/extension/
    - Abre tu proyecto
    - Activa la extensión WAVE
    - Guarda captura mostrando errores/alertas

   **TAW (Test de Accesibilidad Web):**
    - Accede a: https://www.tawdis.net/?lang=es
    - Introduce la URL de tu proyecto (si está publicado) o analiza el HTML
    - Guarda captura del informe

2. **Documentar en formato tabla:**

   ```markdown
   | Herramienta | Puntuación/Errores | Captura |
   |-------------|-------------------|---------|
   | Lighthouse | [X]/100 | ![Lighthouse inicial](./capturas/lighthouse-antes.png) |
   | WAVE | [X] errores, [X] alertas | ![WAVE inicial](./capturas/wave-antes.png) |
   | TAW | [X] problemas | ![TAW](./capturas/taw.png) |
   ```

3. **Listar los 3 problemas más graves** que han detectado las herramientas

**Criterios evaluados:** RA5.d, RA5.f

---

#### **Sección 4: Análisis y corrección de errores** 

**Qué debes hacer:**

1. **Crear tabla resumen de errores:**

   Identifica **mínimo 5 errores** encontrados por las herramientas y documéntalos:

   ```markdown
   | # | Error | Criterio WCAG | Herramienta | Solución aplicada |
   |---|-------|---------------|-------------|-------------------|
   | 1 | Imagen sin alt | 1.1.1 | WAVE | Añadido alt="..." |
   | 2 | Contraste bajo en botón | 1.4.3 | Lighthouse | Cambio color de #ccc a #666 |
   | 3 | ... | ... | ... | ... |
   ```

2. **Detalle de cada error:**

   Para **cada uno de los 5 errores**, documenta:

   ```markdown
   #### Error #1: [Título descriptivo]
   
   **Problema:** [Qué estaba mal - 1-2 líneas]
   **Impacto:** [A qué usuarios afecta - 1 línea]
   **Criterio WCAG:** [X.X.X - Nombre del criterio]
   
   **Código ANTES:**
   ```html
   <!-- Código con el error -->
   ```

   **Código DESPUÉS:**
   ```html
   <!-- Código corregido -->
   ```
   ```

**Criterios evaluados:** RA5.d, RA5.e

---

#### **Sección 5: Análisis de estructura semántica** 

**Qué debes incluir:**

1. **Landmarks HTML5 utilizados:**

   Marca los que uses en tu proyecto:
   ```markdown
   - [x] `<header>` - Cabecera del sitio
   - [x] `<nav>` - Menú de navegación
   - [x] `<main>` - Contenido principal
   - [ ] `<article>` - No usado / Usado para [descripción]
   - [ ] `<section>` - No usado / Usado para [descripción]
   - [ ] `<aside>` - No usado / Usado para [descripción]
   - [x] `<footer>` - Pie de página
   ```

2. **Jerarquía de encabezados:**

   Representa la estructura de tus encabezados:
   ```markdown
   H1: Título principal de la página
     H2: Sección Servicios
       H3: Servicio 1
       H3: Servicio 2
     H2: Sección Contacto
   ```

   Indica si hay errores (saltos de nivel) o está correcta.

3. **Análisis de imágenes:**
   ```markdown
   - Total de imágenes: [X]
   - Con texto alternativo: [X]
   - Decorativas (alt=""): [X]
   - Sin alt (corregidas): [X]
   ```

**Criterio evaluado:** RA5.b

---

#### **Sección 6: Verificación manual**

**Qué debes hacer:**

**6.1 Test de navegación por teclado**

Desconecta el ratón y navega tu web completa usando solo el teclado.

Completa este checklist:
```markdown
- [ ] Puedo llegar a todos los enlaces y botones con Tab
- [ ] El orden de navegación con Tab es lógico (no salta caóticamente)
- [ ] Veo claramente qué elemento tiene el focus (borde, sombra, color)
- [ ] Puedo usar mi componente multimedia solo con teclado
- [ ] No hay "trampas" de teclado donde quedo bloqueado
- [ ] Los menús/modals se pueden cerrar con Esc (si aplica)
```

**Problemas encontrados:** [Descripción de problemas o escribe "Ninguno"]

**Soluciones aplicadas:** [Qué hiciste para solucionarlos]

**6.2 Test con lector de pantalla**

**Herramienta:** NVDA (Windows) o VoiceOver (Mac)
- NVDA: https://www.nvaccess.org/
- VoiceOver: Cmd + F5 en Mac

**Pasos:**
1. Abre el lector de pantalla
2. Navega tu web completa usando Tab
3. Escucha qué anuncia el lector en cada elemento
4. Prueba específicamente tu componente multimedia

**Documenta en tabla:**

```markdown
| Aspecto evaluado | Resultado | Observación |
|------------------|-----------|-------------|
| ¿Se entiende la estructura sin ver la pantalla? | ✅ / ⚠️ / ❌ | [Comentario breve] |
| ¿Los landmarks se anuncian correctamente? | ✅ / ⚠️ / ❌ | [Comentario breve] |
| ¿Las imágenes tienen descripciones adecuadas? | ✅ / ⚠️ / ❌ | [Comentario breve] |
| ¿Los enlaces tienen textos descriptivos? | ✅ / ⚠️ / ❌ | [Comentario breve] |
| ¿El componente multimedia es accesible? | ✅ / ⚠️ / ❌ | [Comentario breve] |
```

**Principales problemas detectados:** [Lista de 2-3 problemas o "Ninguno"]

**Mejoras aplicadas:** [Qué cambiaste después del test]

**6.3 Verificación cross-browser**

Abre tu proyecto en **3 navegadores diferentes** y verifica que todo funciona.

**Documenta en tabla:**

```markdown
| Navegador | Versión | Layout correcto | Multimedia funciona | Observaciones |
|-----------|---------|-----------------|---------------------|---------------|
| Chrome | [120+] | ✅ | ✅ | [Problemas o "Sin problemas"] |
| Firefox | [121+] | ✅ | ✅ | [Problemas o "Sin problemas"] |
| Safari/Edge | [17+/120+] | ✅ | ✅ | [Problemas o "Sin problemas"] |
```

**Incluye capturas:** Una captura de pantalla de tu proyecto en cada navegador.
- `./capturas/chrome.png`
- `./capturas/firefox.png`
- `./capturas/safari.png`

**Criterios evaluados:** RA5.g, RA4.g

---

#### **Sección 7: Resultados finales después de correcciones** 

**Qué debes hacer:**

1. **Ejecuta de nuevo las 3 herramientas** (Lighthouse, WAVE, TAW) después de aplicar todas las correcciones

2. **Documenta la mejora en tabla:**

   ```markdown
   | Herramienta | Antes | Después | Mejora |
   |-------------|-------|---------|--------|
   | Lighthouse | [X]/100 | [X]/100 | +[X] puntos |
   | WAVE | [X] errores | [X] errores | -[X] errores |
   | TAW | [X] problemas | [X] problemas | -[X] problemas |
   ```

3. **Incluye capturas de los resultados finales:**
    - `./capturas/lighthouse-despues.png`
    - `./capturas/wave-despues.png`

4. **Checklist de conformidad WCAG 2.1 Nivel AA:**

   ```markdown
   **Perceptible:**
   - [ ] 1.1.1 - Contenido no textual (alt en imágenes)
   - [ ] 1.3.1 - Información y relaciones (HTML semántico)
   - [ ] 1.4.3 - Contraste mínimo (4.5:1 en texto normal)
   - [ ] 1.4.4 - Redimensionar texto (200% sin pérdida de funcionalidad)

   **Operable:**
   - [ ] 2.1.1 - Teclado (toda la funcionalidad accesible)
   - [ ] 2.1.2 - Sin trampas de teclado
   - [ ] 2.4.3 - Orden del foco (lógico y predecible)
   - [ ] 2.4.7 - Foco visible (se ve claramente)

   **Comprensible:**
   - [ ] 3.1.1 - Idioma de la página (atributo lang="es")
   - [ ] 3.2.3 - Navegación consistente
   - [ ] 3.3.2 - Etiquetas o instrucciones en formularios

   **Robusto:**
   - [ ] 4.1.2 - Nombre, función, valor (ARIA cuando necesario)
   ```

5. **Nivel de conformidad alcanzado:**

   Indica el nivel: **A / AA / AA parcial**

   Justifica en 2-3 líneas: ¿Qué criterios cumples completamente? ¿Cuáles no y por qué?

**Criterios evaluados:** RA5.e, RA5.f

---

#### **Sección 8: Conclusiones y reflexión** 

**Qué debes incluir:**

1. **¿Es accesible mi proyecto?** (100-150 palabras)

   Reflexiona de forma crítica y honesta sobre:
    - ¿Tu proyecto es realmente accesible después de las mejoras?
    - ¿Qué fue lo más difícil de corregir?
    - ¿Qué te sorprendió más al usar el lector de pantalla?
    - ¿Ha cambiado tu forma de pensar sobre el diseño web?

2. **Principales mejoras aplicadas**

   Lista las 5 mejoras más importantes que implementaste:
   ```markdown
   1. [Mejora concreta] - [Por qué era importante]
   2. [Mejora concreta] - [Por qué era importante]
   3. [Mejora concreta] - [Por qué era importante]
   4. [Mejora concreta] - [Por qué era importante]
   5. [Mejora concreta] - [Por qué era importante]
   ```

3. **Mejoras futuras**

   Si tuvieras más tiempo, ¿qué mejorarías?
   ```markdown
   1. [Mejora futura específica]
   2. [Mejora futura específica]
   3. [Mejora futura específica]
   ```

4. **Aprendizaje clave**

   En 2-3 frases: ¿Cuál es la lección más importante que te llevas sobre accesibilidad?

**Criterio evaluado:** RA5.b


### Tarea 3: README del proyecto 

**Objetivo:** Actualizar el README principal del repositorio con información del proyecto de accesibilidad.

**Ubicación:** `README.md` (en la raíz del proyecto)

**Contenido mínimo:**

```markdown
# Proyecto 4 - Accesibilidad y Multimedia

## Descripción
[Breve descripción de tu proyecto - 2-3 líneas]

## Componente multimedia añadido
**Tipo:** [Galería / Video / Carrusel]
**Descripción:** [Qué hace - 1 línea]

## Resultados de auditoría de accesibilidad

| Herramienta | Puntuación inicial | Puntuación final | Mejora |
|-------------|-------------------|------------------|--------|
| Lighthouse | [X]/100 | [X]/100 | +[X] |
| WAVE | [X] errores | [X] errores | -[X] |
| TAW | [X] problemas | [X] problemas | -[X] |

**Nivel de conformidad alcanzado:** WCAG 2.1 [A / AA / AA parcial]

## Documentación completa
📄 **[Ver análisis completo de accesibilidad](./docs/accesibilidad/README.md)**

## Verificación realizada
- ✅ Auditoría con Lighthouse, WAVE y TAW
- ✅ Test con lector de pantalla ([NVDA / VoiceOver])
- ✅ Test de navegación por teclado
- ✅ Verificación cross-browser (Chrome, Firefox, Safari/Edge)

## Tecnologías utilizadas
- HTML5 semántico
- CSS3 (con media queries de accesibilidad)
- JavaScript vanilla
- [Otras tecnologías]

## Instalación y uso

    git clone [url-repositorio]
    cd proyecto-4
    # Abrir index.html en navegador o usar Live Server

## Autor
**Nombre:** [Tu nombre]
**Curso:** 2º DAW - Desarrollo de Aplicaciones Web
**Módulo:** Diseño de Interfaces Web (DIW)
```

## Estructura final del repositorio

```
proyecto-4/
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── multimedia.js
├── media/
│   ├── images/
│   ├── videos/          # Solo si usas video
│   └── subtitles/       # Solo si usas video
├── docs/
│   └── accesibilidad/
│       ├── README.md    # Documento principal (TODO EN UNO)
│       └── capturas/
│           ├── lighthouse-antes.png
│           ├── lighthouse-despues.png
│           ├── wave-antes.png
│           ├── wave-despues.png
│           ├── taw.png
│           ├── chrome.png
│           ├── firefox.png
│           └── safari.png
└── README.md            # README principal del proyecto

```


## Rúbrica de evaluación

| Criterio | 10 puntos | 7.5 puntos | 5 puntos | 2.5 puntos | 0 puntos |
|----------|-----------|------------|----------|------------|----------|
| **RA5.a + RA5.c - Fundamentos** (Sección 1) | Intro completa 50-75 palabras. 4 principios WCAG con ejemplos propios claros. Niveles explicados. | Intro y 4 principios explicados correctamente. Niveles presentes. | Explicación básica de principios y niveles. | Explicación superficial o incompleta. | Sin fundamentos. |
| **RA4.e + RA4.f - Multimedia** (Sección 2 + implementación) | Multimedia funcional, accesible (alt/subtítulos/teclado). Bien documentado. Código limpio. | Multimedia funcional y accesible. Documentación correcta. | Multimedia básico funcional. Accesibilidad parcial. | Multimedia con errores de accesibilidad. | Sin multimedia o no funciona. |
| **RA5.d - Identificar errores** (Secciones 3 y 4) | Auditoría con 3 herramientas. Tabla resumen completa. 5 errores detallados con antes/después y criterio WCAG. | 3 herramientas ejecutadas. 5 errores documentados correctamente. | 2-3 herramientas. 3-4 errores documentados. | 1 herramienta o pocos errores. | Sin auditoría o sin errores. |
| **RA5.e - Conformidad** (Sección 7) | Lighthouse 85+, WAVE 0 errores. Checklist WCAG completo y justificado. Nivel AA alcanzado o cercano. | Lighthouse 75+. Errores corregidos. Checklist completo. Nivel AA parcial. | Lighthouse 65+. Checklist parcial. Algunas correcciones. | Baja conformidad. Checklist incompleto. | Sin conformidad o sin checklist. |
| **RA5.f - Test externos** (Secciones 3 y 7) | 3 herramientas antes/después. 8 capturas claras. Mejora cuantificada en tabla. | 3 herramientas con capturas antes/después. Mejora visible. | 2 herramientas con capturas. | 1 herramienta o capturas incompletas. | Sin test externos o sin capturas. |
| **RA5.b - Análisis estructura** (Sección 5) | Landmarks completos. Jerarquía H correcta. Análisis imágenes detallado. | Landmarks y encabezados analizados. Análisis de imágenes presente. | Análisis básico de estructura. | Análisis superficial. | Sin análisis de estructura. |
| **RA5.g + RA4.g - Verificación manual** (Sección 6) | Test teclado completo. Test NVDA/VO con tabla detallada. 3 navegadores con capturas y análisis. | Teclado + lector + 3 navegadores. Tabla y capturas presentes. | Teclado + lector O 2-3 navegadores. | Verificación superficial o incompleta. | Sin verificación manual. |
| **Calidad documental** (Secciones 8 + README) | Reflexión crítica 100-150 pal. 5 mejoras justificadas. README completo. Markdown perfecto. | Reflexión presente. Mejoras listadas. README correcto. Markdown correcto. | Reflexión básica. Algunas mejoras. README simple. | Conclusiones mínimas. README incompleto. | Sin conclusiones o README. |

**Nota:** Cada criterio se evalúa de forma independiente. La nota final es la media ponderada según los porcentajes de RA indicados.

## Recursos y herramientas

### Herramientas obligatorias

**Auditoría automatizada:**
- **Lighthouse:** Integrado en Chrome DevTools (F12 → pestaña Lighthouse)
- **WAVE:** Extensión de navegador - https://wave.webaim.org/extension/
- **TAW:** Test online - https://www.tawdis.net/?lang=es

**Test manual:**
- **NVDA (Windows):** Lector de pantalla gratuito - https://www.nvaccess.org/
- **VoiceOver (Mac):** Lector integrado - Activar con Cmd + F5

### Referencias de consulta

**Normativas y guías:**
- W3C WAI - Introducción: https://www.w3.org/WAI/fundamentals/accessibility-intro/es
- WCAG 2.1 Quick Reference: https://www.w3.org/WAI/WCAG21/quickref/
- Accesible.es: https://accesible.es (recurso en español)

**Herramientas complementarias:**
- Contrast Checker: https://webaim.org/resources/contrastchecker/
- HTML Validator: https://validator.w3.org/
- CSS Validator: https://jigsaw.w3.org/css-validator/
