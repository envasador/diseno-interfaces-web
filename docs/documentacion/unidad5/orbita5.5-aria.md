## 5. ARIA: Accessible Rich Internet Applications

### 5.1. ¿Qué es ARIA y cuándo usarla?

**ARIA** es un conjunto de atributos HTML que añaden información semántica adicional para tecnologías de asistencia cuando el HTML nativo no es suficiente.

**La regla de oro de ARIA:**
> "No uses ARIA si existe un elemento HTML nativo que hace lo mismo."

El `<button>` nativo ya tiene todo lo necesario. Solo usas ARIA cuando HTML no puede expresar lo que necesitas.

**ARIA es necesaria cuando:**
1. Creas widgets personalizados que no existen en HTML (tabs, acordeones complejos, tooltips)
2. Añades interactividad dinámica con JavaScript (contenido que cambia sin recargar)
3. Necesitas comunicar estados que HTML no expresa (loading, expandido/colapsado, seleccionado)

### 5.2. Los tres tipos de atributos ARIA

#### Roles
Definen **qué tipo de elemento es**:
- `role="navigation"` - Navegación
- `role="tab"` - Pestaña
- `role="dialog"` - Modal/diálogo
- `role="alert"` - Alerta importante
- `role="button"` - Botón (solo si no usas `<button>`)

#### Propiedades
Definen **características** que normalmente no cambian:
- `aria-label` - Da nombre al elemento
- `aria-labelledby` - Referencia a elemento que actúa como etiqueta
- `aria-describedby` - Descripción adicional
- `aria-required` - Campo obligatorio
- `aria-controls` - Qué elemento controla

#### Estados
Definen el **estado actual** que puede cambiar:
- `aria-expanded` - Expandido (true) o colapsado (false)
- `aria-pressed` - Botón toggle presionado o no
- `aria-selected` - Elemento seleccionado
- `aria-hidden` - Oculto de lectores de pantalla
- `aria-invalid` - Valor inválido
- `aria-busy` - Cargando

### 5.3. Usos fundamentales de ARIA

#### Etiquetar elementos sin texto visible

Botones con solo iconos necesitan nombre:
- `aria-label="Cerrar modal"` en un botón con solo "×"
- `aria-label="Buscar"` en botón con solo icono de lupa

#### Comunicar estados dinámicos

Cuando algo se expande/colapsa con JavaScript:
- `aria-expanded="false"` → cambia a `"true"` cuando se abre
- El lector anuncia: "colapsado" o "expandido"

Botones toggle (modo oscuro, favorito):
- `aria-pressed="false"` → cambia a `"true"` cuando se activa

#### Anunciar cambios dinámicos (live regions)

Cuando contenido cambia con JavaScript sin recargar:

**aria-live:**
- `aria-live="polite"` - Anuncia cuando el lector termine de hablar (notificaciones, confirmaciones)
- `aria-live="assertive"` - Anuncia inmediatamente interrumpiendo (errores críticos, alertas)

**Roles equivalentes:**
- `role="alert"` = `aria-live="assertive"` (urgente)
- `role="status"` = `aria-live="polite"` (normal)

Ejemplos:
- "Producto añadido al carrito" → `role="status"`
- "Error: sesión expirada" → `role="alert"`

#### Ocultar contenido decorativo

`aria-hidden="true"` oculta elementos de lectores de pantalla (pero siguen visibles):
- Iconos decorativos cuando hay texto explicativo
- Separadores visuales sin significado
- Contenido duplicado

**Cuidado:** Nunca en elementos interactivos o con contenido importante.

### 5.4. ARIA en componentes complejos

Para componentes como **tabs, modales, menús desplegables, tooltips**, ARIA es esencial. Cada tipo de componente tiene un patrón específico de roles, propiedades y estados que deben trabajar juntos.

**Dónde aprender los patrones:**

**Accesible.es - Componentes:**
https://accesible.es/componentes
Ejemplos en español de cómo implementar cada tipo de componente accesible.

**ARIA Authoring Practices Guide:**
https://www.w3.org/WAI/ARIA/apg/
Guía oficial del W3C con patrones detallados para cada tipo de widget. Muestra exactamente qué ARIA usar y cómo debe comportarse con teclado.

### 5.5. Errores comunes con ARIA

**Error 1: Usar ARIA innecesariamente**
Si HTML nativo existe, úsalo. `<button>` es mejor que `<div role="button">`.

**Error 2: ARIA contradictorio con HTML**
Un `<button>` no puede tener `role="link"`. Son conceptos opuestos.

**Error 3: aria-hidden en contenido enfocable**
Si un elemento puede recibir foco (botón, enlace, input), no lo ocultes con `aria-hidden="true"`. Crea confusión.

**Error 4: Olvidar actualizar estados**
Si un menú se abre pero no actualizas `aria-expanded` de `false` a `true`, el lector anuncia información incorrecta.

**Error 5: Live regions sobreutilizadas**
No uses `aria-live="assertive"` en contadores que cambian constantemente. Abrumarás al usuario interrumpiendo cada segundo.

