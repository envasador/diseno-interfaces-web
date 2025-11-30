## 2. CSS moderno: Arquitectura y organización

### El problema de CSS a escala

CSS es fácil de empezar pero difícil de mantener. Sin estructura, acabas con:

- Estilos globales que se pisan entre sí
- Especificidad fuera de control
- Código duplicado por todas partes
- Miedo a cambiar algo porque "no sé qué más se romperá"

La solución no es escribir más CSS, sino **organizarlo mejor**.

### Arquitectura: Pensando en capas

El CSS moderno nos da herramientas para organizar estilos en capas explícitas. Piensa en tu CSS como una cebolla con diferentes niveles de especificidad:

**Capa 1: Reset/Normalize**  
Neutraliza las diferencias entre navegadores y establece una base consistente.

**Capa 2: Tokens de diseño**  
Variables que definen tu sistema visual: colores, espaciado, tipografía, sombras.

**Capa 3: Estilos base**  
Estilos aplicados directamente a elementos HTML sin clases.

**Capa 4: Layouts**  
Estructuras de página reutilizables (grids, contenedores, regiones).

**Capa 5: Componentes**  
Bloques de interfaz independientes y reutilizables.

**Capa 6: Utilidades**  
Clases de propósito único para ajustes rápidos.

**Capa 7: Overrides**  
Estados especiales, temas, o excepciones controladas.

### Cascade Layers: Haciendo explícito el orden

CSS Cascade Layers (`@layer`) es una de las características más importantes añadidas a CSS en años. Te permite definir explícitamente el orden de prioridad de tus estilos:

```css
/* Definimos el orden de las capas */
@layer reset, tokens, base, layouts, components, utilities, overrides;

/* Cada capa tiene su archivo */
@layer reset {
  *, *::before, *::after {
    box-sizing: border-box;
    margin: 0;
  }
}

@layer tokens {
  :root {
    --color-primary: oklch(0.6 0.2 250);
    --spacing-sm: 0.5rem;
    --spacing-md: 1rem;
  }
}

@layer components {
  .button {
    padding: var(--spacing-sm) var(--spacing-md);
    background: var(--color-primary);
  }
}

@layer overrides {
  .button.is-disabled {
    opacity: 0.5;
    pointer-events: none;
  }
}
```

**Ventaja clave**: Los estilos en capas superiores SIEMPRE ganan, sin importar la especificidad. Esto elimina gran parte de la guerra de `!important`.

### Variables CSS (Custom Properties): Tu sistema de diseño en código

Las variables CSS son mucho más poderosas que las variables de preprocesadores porque:

1. **Son reactivas**: Puedes cambiarlas con JavaScript
2. **Heredan**: Puedes redefinirlas en contextos específicos
3. **Se inspeccionan en DevTools**: Ves los valores computados en tiempo real

```css
:root {
  /* Colores primitivos */
  --color-blue-50: oklch(0.95 0.02 250);
  --color-blue-500: oklch(0.6 0.2 250);
  --color-blue-900: oklch(0.3 0.15 250);
  
  /* Tokens semánticos */
  --color-primary: var(--color-blue-500);
  --color-surface: var(--color-blue-50);
  
  /* Espaciado con escala */
  --space-unit: 0.5rem;
  --space-1: calc(var(--space-unit) * 1);
  --space-2: calc(var(--space-unit) * 2);
  --space-3: calc(var(--space-unit) * 3);
}

/* Tema oscuro */
@media (prefers-color-scheme: dark) {
  :root {
    --color-surface: var(--color-blue-900);
    --color-primary: var(--color-blue-50);
  }
}

/* Contexto específico */
.card {
  --card-padding: var(--space-2);
  padding: var(--card-padding);
}

.card.is-compact {
  --card-padding: var(--space-1);
}
```

### @scope: CSS que sabe dónde vive

`@scope` te permite limitar el alcance de tus estilos a un contexto específico sin aumentar la especificidad:

```css
/* Sin @scope: colisiones globales */
.card .title { color: blue; }
.modal .title { color: red; }

/* Con @scope: contexto explícito */
@scope (.card) {
  .title {
    color: blue;
  }
}

@scope (.modal) {
  .title {
    color: red;
  }
}

/* Límites de scope: afecta dentro de .card pero no dentro de .nested */
@scope (.card) to (.nested) {
  .title {
    color: blue;
  }
}
```

**Caso de uso real**: Componentes de Angular o React que necesitan estilos aislados sin usar CSS Modules o styled-components.

### Container Queries: Componentes que se adaptan a su contenedor

Durante años, hemos usado media queries que miran el tamaño de la ventana. Pero los componentes realmente necesitan saber **su propio tamaño**, no el tamaño de la pantalla.

```css
/* Definir un contenedor */
.card-container {
  container-type: inline-size;
  container-name: card;
}

/* El componente se adapta a su contenedor */
@container card (min-width: 400px) {
  .card {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
  
  .card__image {
    aspect-ratio: 1;
  }
}

@container card (min-width: 600px) {
  .card {
    grid-template-columns: 300px 1fr;
  }
}
```

**Por qué es revolucionario**: Puedes reutilizar el mismo componente en una barra lateral estrecha y en el contenido principal, y se adaptará automáticamente sin saber dónde está.

### El selector :has() — CSS aprende a mirar hacia adelante

`:has()` es básicamente un "selector padre" que CSS nunca tuvo:

```css
/* Estilizar un formulario que contiene errores */
form:has(.error) {
  border: 2px solid red;
}

/* Card con imagen */
.card:has(img) {
  display: grid;
}

/* Card sin imagen */
.card:not(:has(img)) {
  display: flex;
}

/* Artículo seguido de otro artículo (no el primero) */
article:has(+ article) {
  border-bottom: 1px solid gray;
}

/* Lista con al menos 5 items */
ul:has(> li:nth-child(5)) {
  columns: 2;
}
```

**Caso de uso real**: Adaptar layouts según el contenido que realmente existe, sin JavaScript.

## 3. Sistemas de Layout: Grid y Flexbox

### Cuándo usar cada uno

**Flexbox**: Para layouts **unidimensionales** (fila O columna)
- Barras de navegación
- Botones con iconos
- Centrado de elementos
- Distribución de espacio entre items

**Grid**: Para layouts **bidimensionales** (filas Y columnas)
- Layouts de página completos
- Galerías de imágenes
- Formularios complejos
- Dashboards

### Flexbox: Los patrones que más usarás

```css
/* Centrado perfecto */
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Distribución espaciada */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}

/* Columnas de igual altura */
.card-grid {
  display: flex;
  gap: 1rem;
}

.card {
  flex: 1; /* Todos crecen igual */
}

/* Botón con icono */
.button {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
```

### Grid: Pensando en áreas

```css
/* Layout de página clásico */
.page {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar main aside"
    "footer footer footer";
  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  min-height: 100vh;
  gap: 1rem;
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.aside { grid-area: aside; }
.footer { grid-area: footer; }

/* Galería responsive sin media queries */
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}
```

**Patrón clave**: `auto-fit` + `minmax()` = Grid responsivo sin breakpoints.

### Subgrid: Alineación entre generaciones

```css
.card-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}

.card {
  display: grid;
  grid-template-rows: subgrid; /* Hereda las filas del padre */
  grid-row: span 3;
}

/* Ahora todos los títulos, contenidos y botones se alinean */
```

## 4. Diseño Responsive: Más allá de los breakpoints

### Mobile-first: Por qué y cómo

Empezar por móvil te obliga a priorizar. Si funciona en una pantalla pequeña, escalar hacia arriba es más fácil que lo contrario.

```css
/* Base: móvil */
.container {
  padding: 1rem;
}

.grid {
  display: grid;
  gap: 1rem;
}

/* Tablet */
@media (min-width: 768px) {
  .container {
    padding: 2rem;
  }
  
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .container {
    max-width: 1200px;
    margin-inline: auto;
  }
  
  .grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
  }
}
```

### Unidades fluidas: Tipografía que escala

```css
:root {
  /* Escala entre 16px y 24px según el viewport */
  --font-size-fluid: clamp(1rem, 0.8rem + 1vw, 1.5rem);
}

h1 {
  font-size: clamp(2rem, 5vw, 4rem);
}

.container {
  /* Padding fluido entre 1rem y 3rem */
  padding-inline: clamp(1rem, 5%, 3rem);
}
```

**Función clave**: `clamp(mínimo, preferido, máximo)` — tu nueva mejor amiga.

### Aspect Ratio: Imágenes que no saltan

```css
.video-container {
  aspect-ratio: 16 / 9;
  width: 100%;
}

.thumbnail {
  aspect-ratio: 1;
  object-fit: cover;
}

/* Fallback para navegadores antiguos */
@supports not (aspect-ratio: 1) {
  .thumbnail {
    padding-bottom: 100%; /* Hack del padding */
  }
}
```

## 5. SCSS y Preprocesadores: Organización a escala

### ¿Necesitas SCSS en 2024?

CSS nativo ha incorporado muchas características que antes requerían preprocesadores (variables, nesting). Sin embargo, SCSS sigue siendo valioso por:

- **Mixins**: Reutilización de bloques de código
- **Funciones**: Lógica en tiempo de compilación
- **Partials**: Organización en archivos
- **Ecosistema**: Herramientas maduras y bien documentadas

### Estructura de archivos escalable

```
styles/
├── abstracts/
│   ├── _variables.scss
│   ├── _functions.scss
│   └── _mixins.scss
├── base/
│   ├── _reset.scss
│   └── _typography.scss
├── layouts/
│   ├── _grid.scss
│   └── _containers.scss
├── components/
│   ├── _buttons.scss
│   ├── _cards.scss
│   └── _forms.scss
├── utilities/
│   └── _helpers.scss
└── main.scss
```

### Mixins útiles para proyectos reales

```scss
// Responsive breakpoints
@mixin respond-to($breakpoint) {
  @if $breakpoint == tablet {
    @media (min-width: 768px) { @content; }
  } @else if $breakpoint == desktop {
    @media (min-width: 1024px) { @content; }
  }
}

// Uso
.card {
  padding: 1rem;
  
  @include respond-to(tablet) {
    padding: 2rem;
  }
}

// Truncate text
@mixin truncate($lines: 1) {
  @if $lines == 1 {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  } @else {
    display: -webkit-box;
    -webkit-line-clamp: $lines;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }
}

// Focus visible accesible
@mixin focus-visible {
  &:focus-visible {
    outline: 2px solid var(--color-primary);
    outline-offset: 2px;
  }
}
```

### Funciones para sistemas de diseño

```scss
// Escala de espaciado
@function spacing($multiplier) {
  @return calc(var(--space-unit) * #{$multiplier});
}

// Uso
.card {
  padding: spacing(2); // 1rem
  margin-bottom: spacing(4); // 2rem
}

// Colores con transparencia
@function alpha($color, $opacity) {
  @return rgba($color, $opacity);
}
```


## Conclusión

La maquetación moderna no se trata de memorizar propiedades CSS, sino de:

1. **Entender la plataforma web**: HTML semántico, cascada, herencia
2. **Pensar en sistemas**: Tokens, componentes, arquitectura escalable
3. **Usar las herramientas modernas**: Grid, Flexbox, Container Queries, Layers
4. **Optimizar para usuarios reales**: Performance, accesibilidad, responsive

El código que escribes hoy será leído (y maldecido o bendecido) por alguien mañana, posiblemente tú mismo. Escribe CSS como si fueras a volver a él en 6 meses sin recordar nada. Tu yo futuro te lo agradecerá.

Ahora ve y construye interfaces que no solo se vean bien, sino que **funcionen bien**, **se mantengan bien**, y **escalen bien**.
