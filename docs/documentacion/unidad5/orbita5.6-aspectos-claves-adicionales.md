## 6. Aspectos clave adicionales

### 6.1. Navegación por teclado

**Principio:** Todo accesible con ratón debe ser accesible con teclado.

**Teclas estándar:**
- Tab / Shift+Tab - Navegar elementos
- Enter - Activar enlace/botón
- Espacio - Activar botón, checkbox
- Escape - Cerrar modal/dropdown
- Flechas - Navegar dentro de componentes

**Orden de foco lógico:**
El orden con Tab debe seguir el flujo visual. Nunca uses `tabindex` positivo.

**Indicador de foco visible:**
Nunca `outline: none` sin alternativa clara. Es crítico para saber dónde estás.

### 6.2. Contraste y color

**Ratios mínimos (WCAG 2.1 AA):**
- Texto normal: 4.5:1
- Texto grande (≥24px o ≥19px bold): 3:1
- Iconos/gráficos: 3:1

**No solo color:**
Nunca transmitas información únicamente con color. Añade iconos, patrones, texto.

### 6.3. Multimedia accesible

**Vídeo:**
- Subtítulos (para personas con sordera y contextos sin audio)
- Transcripción completa
- Audiodescripción si hay contenido visual importante no explicado en audio

**Audio (podcasts):**
- Transcripción completa
- Controles accesibles por teclado

**Imágenes:**
- Informativas: `alt` descriptivo de qué información aporta
- Decorativas: `alt=""` (vacío, no omitir el atributo)
- Complejas (gráficos): descripción detallada adicional

*
