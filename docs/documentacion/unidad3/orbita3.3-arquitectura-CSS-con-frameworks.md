## 3. Arquitectura CSS en aplicaciones modernas: un enfoque práctico

Cuando desarrollamos interfaces web con frameworks como Angular, React o Vue, una de las decisiones más importantes es cómo organizar nuestros estilos. No existe una única respuesta correcta: cada proyecto, equipo y contexto requiere un enfoque diferente.

Tradicionalmente, CSS ha sido global por naturaleza. Esto significa que cualquier estilo que escribamos puede afectar a cualquier parte de nuestra aplicación, lo cual genera problemas de mantenibilidad a medida que los proyectos crecen. Para resolver esto, la comunidad ha desarrollado dos tipos de soluciones que abordan el problema desde ángulos distintos.

Por un lado, tenemos las **metodologías de organización** como BEM (Block Element Modifier) e ITCSS (Inverted Triangle CSS). Estas no modifican cómo funciona CSS, sino que establecen convenciones de nomenclatura y estructura que, si todo el equipo las sigue, evitan conflictos y mantienen la especificidad bajo control. Su ventaja es que funcionan en cualquier proyecto sin dependencias adicionales y permiten entender CSS en su forma más pura.

Por otro lado, los frameworks modernos ofrecen **mecanismos de encapsulación** que aíslan los estilos de cada componente automáticamente. Angular ofrece tres modos de encapsulación (None, Emulated y ShadowDom), Vue tiene su atributo `scoped`, y React cuenta con soluciones como CSS Modules o Styled Components. Estas herramientas modifican el comportamiento del CSS para garantizar que los estilos de un componente no afecten a otros, lo cual facilita el trabajo en equipos grandes donde no todos conocen el código de los demás.

Sin embargo, ninguno de estos enfoques es perfecto por sí solo. Las metodologías requieren disciplina y no ofrecen protección real contra errores. La encapsulación total puede generar duplicación de código y dificulta mantener una coherencia visual global.

Es aquí donde surge el **enfoque híbrido**: combinar lo mejor de ambos mundos. La idea es utilizar ITCSS + BEM para los estilos que deben ser globales (variables, reset, tipografía, layouts, componentes de estructura) y reservar la encapsulación para los componentes de UI que tienen múltiples variantes o que desarrollan diferentes personas del equipo.

La clave que hace posible esta combinación son las **custom properties de CSS** (variables CSS). A diferencia de las variables SASS, las custom properties existen en tiempo de ejecución y pueden atravesar cualquier tipo de encapsulación, incluido Shadow DOM. Esto nos permite definir nuestros tokens de diseño (colores, espaciados, tipografías) de forma global y utilizarlos dentro de componentes encapsulados sin ningún problema.

Las siguientes tablas resumen las diferentes opciones disponibles, cuándo usar cada una y cómo combinarlas de forma efectiva. El objetivo no es memorizar todas las posibilidades, sino entender los principios subyacentes para poder tomar decisiones informadas en cada proyecto.

### 1. Metodologías y tipo de DOM

| Metodología | Tipo de DOM | Encapsulación | Cómo funciona |
|-------------|-------------|---------------|---------------|
| ITCSS + BEM | Normal | ❌ No | Los estilos son globales. El contexto se define mediante la nomenclatura de clases (`.bloque__elemento--modificador`). No hay aislamiento real, solo convención de nombres. |
| Angular `ViewEncapsulation.None` | Normal | ❌ No | Angular no añade ningún atributo. Los estilos son completamente globales, igual que CSS tradicional. Ideal para usar con ITCSS + BEM. |
| Angular `ViewEncapsulation.Emulated` | Normal + atributos | ✅ Simulada | Angular añade atributos únicos (`_ngcontent-xxx`) a los elementos y selectores. Los estilos parecen encapsulados pero siguen en el DOM global. Es el comportamiento por defecto. |
| Angular `ViewEncapsulation.ShadowDom` | Shadow DOM | ✅ Nativa | Usa Shadow DOM real del navegador. Los estilos están completamente aislados y no pueden filtrarse hacia fuera ni hacia dentro. |
| **Híbrido: ITCSS + BEM + Emulated** | Normal + atributos | ✅ Parcial | Base global (variables, reset, elementos, objetos) con ITCSS. Componentes específicos encapsulados con Angular Emulated. Combina coherencia visual con aislamiento donde interesa. |
| **Híbrido: ITCSS + BEM + ShadowDom** | Normal + Shadow DOM | ✅ Parcial + Nativa | Base global con ITCSS para tokens y layouts. Componentes complejos o reutilizables usan Shadow DOM real. Máximo rendimiento en aislamiento crítico. |
| Web Components | Shadow DOM | ✅ Nativa | Estándar del navegador para componentes. Cada componente tiene su propio árbol DOM aislado con estilos que no afectan al resto de la página. |
| React (CSS Modules) | Normal | ✅ Por clase | Las clases se hashean en tiempo de compilación (`.card` → `.card_abc123`). Evita colisiones sin modificar el DOM, solo los nombres de clase. |
| React (Styled Components) | Normal | ✅ Por clase | Genera clases únicas dinámicamente en runtime. Los estilos se definen dentro de JavaScript usando template literals. |
| **Híbrido React: ITCSS + CSS Modules** | Normal | ✅ Parcial | Base global con ITCSS (variables, reset, layouts). Componentes específicos usan CSS Modules para aislamiento. Mejor de ambos mundos. |
| Vue (`scoped`) | Normal + atributos | ✅ Simulada | Vue añade atributos únicos (`data-v-xxx`) similar a Angular Emulated. Los estilos solo aplican a elementos con ese atributo. |
| **Híbrido Vue: ITCSS + scoped** | Normal + atributos | ✅ Parcial | Base global con ITCSS importada en `main.js`. Componentes específicos usan `<style scoped>` para extensiones locales. |

### 2. Estructura del enfoque híbrido

| Capa ITCSS | Ubicación | Encapsulación | Propósito |
|------------|-----------|---------------|-----------|
| Settings | `styles/settings/_variables.scss` | ❌ Global | Custom properties CSS accesibles desde cualquier lugar, incluso dentro de Shadow DOM. |
| Tools | `styles/tools/_mixins.scss` | ❌ Global | Mixins SCSS reutilizables. Se importan donde se necesiten con `@use`. |
| Generic | `styles/generic/_reset.scss` | ❌ Global | Reset y normalize. Debe ser global para afectar a todo el documento. |
| Elements | `styles/elements/_base.scss` | ❌ Global | Estilos base de elementos HTML (`body`, `a`, `h1`). Global por naturaleza. |
| Objects | `styles/objects/_layouts.scss` | ❌ Global | Patrones estructurales (`.container`, `.grid`). Globales para reutilizar en cualquier página. |
| Components (layout) | `styles/components/_header.scss` | ❌ Global | Componentes de layout únicos (header, footer). Globales porque solo existen una vez. |
| Components (UI) | `component.scss` del componente | ✅ Encapsulada | Componentes UI reutilizables (cards, modales, botones). Encapsulados para evitar conflictos. |
| Utilities | `styles/utilities/_helpers.scss` | ❌ Global | Clases de utilidad (`.visually-hidden`, `.text-center`). Globales para usar en cualquier lugar. |

### 3. Selectores especiales en enfoque híbrido

| Selector | ITCSS + BEM (global) | Híbrido (Emulated) | Híbrido (ShadowDom) | Para qué sirve |
|----------|---------------------|-------------------|--------------------|--------------| 
| `.clase` | ✅ Uso principal | ✅ En capas globales | ✅ En capas globales | Selector básico. Funciona en todos los contextos. |
| `var(--custom)` | ✅ | ✅ | ✅ Atraviesa Shadow DOM | Custom properties. La clave del híbrido: variables globales accesibles dentro de componentes encapsulados. |
| `:scope` | ❌ Innecesario | ⚠️ Limitado | ✅ En componentes Shadow | Selecciona raíz del contexto. Útil solo en Shadow DOM real. |
| `:host` | ❌ No aplica | ✅ En componentes encapsulados | ✅ En componentes Shadow | Estiliza el elemento host desde dentro. Esencial para componentes encapsulados. |
| `:host-context()` | ❌ No aplica | ✅ En componentes encapsulados | ✅ En componentes Shadow | Aplica estilos según contexto ancestro. Útil para temas (`.dark-theme`). |
| `::slotted()` | ❌ No aplica | ❌ No aplica | ✅ Solo en Shadow DOM | Estiliza contenido proyectado. Solo funciona con Shadow DOM real. |
| `@use` | ✅ Para importar mixins | ✅ En componentes que necesiten mixins | ✅ En componentes que necesiten mixins | Importa mixins y variables SCSS en componentes encapsulados. |


### 4. Cuándo usar cada capa en híbrido

| Tipo de estilo | ¿Global o encapsulado? | Razón | Ejemplo |
|----------------|------------------------|-------|---------|
| Variables CSS | ✅ Global | Las custom properties atraviesan Shadow DOM. Defínelas una vez, úsalas en todas partes. | `--color-primary`, `--spacing-md` |
| Reset/Normalize | ✅ Global | Debe aplicar a todo el documento base. | `*, *::before, *::after { box-sizing: border-box; }` |
| Tipografía base | ✅ Global | Consistencia en todo el sitio. | `body { font-family: var(--font-family-base); }` |
| Layouts | ✅ Global | Patrones reutilizables en cualquier página. | `.container`, `.grid`, `.flex` |
| Header/Footer | ✅ Global | Solo existen una vez. No hay riesgo de colisión. | `.site-header`, `.site-footer` |
| Cards | ⚠️ Depende | Si hay muchas variantes o equipos grandes → encapsulado. Si son pocas y controladas → global con BEM. | `.card`, `.card--blog`, `.card--product` |
| Modales/Diálogos | ✅ Encapsulado | Componentes complejos que pueden entrar en conflicto. Mejor aislar. | Estilos en `modal.component.scss` |
| Formularios complejos | ✅ Encapsulado | Muchos estados y variantes. El aislamiento previene bugs. | Estilos en `form.component.scss` |
| Botones simples | ✅ Global | Reutilizables en toda la app. BEM maneja las variantes bien. | `.btn`, `.btn--primary`, `.btn--large` |
| Utilidades | ✅ Global | Deben estar disponibles en cualquier lugar. | `.visually-hidden`, `.text-center` |


### 5. Estructura de archivos híbrida

```
src/
├── styles/                              # ITCSS Global
│   ├── settings/
│   │   └── _variables.scss              # ✅ Global - Custom properties
│   ├── tools/
│   │   └── _mixins.scss                 # ✅ Global - Se importa con @use
│   ├── generic/
│   │   └── _reset.scss                  # ✅ Global
│   ├── elements/
│   │   └── _base.scss                   # ✅ Global
│   ├── objects/
│   │   └── _layouts.scss                # ✅ Global
│   ├── components/
│   │   ├── _header.scss                 # ✅ Global - Layout único
│   │   ├── _footer.scss                 # ✅ Global - Layout único
│   │   └── _buttons.scss                # ✅ Global - Simples y reutilizables
│   ├── utilities/
│   │   └── _helpers.scss                # ✅ Global
│   └── main.scss                        # Punto de entrada
│
├── app/
│   ├── layout/
│   │   ├── header/
│   │   │   ├── header.component.ts      # ViewEncapsulation.None
│   │   │   ├── header.component.html
│   │   │   └── header.component.scss    # Vacío - estilos en global
│   │   └── footer/
│   │       └── ...                      # ViewEncapsulation.None
│   │
│   ├── components/
│   │   ├── card/
│   │   │   ├── card.component.ts        # ViewEncapsulation.Emulated (default)
│   │   │   ├── card.component.html
│   │   │   └── card.component.scss      # ✅ Encapsulado - Usa variables globales
│   │   └── modal/
│   │       ├── modal.component.ts       # ViewEncapsulation.Emulated
│   │       ├── modal.component.html
│   │       └── modal.component.scss     # ✅ Encapsulado
│   │
│   └── pages/
│       └── ...
│
└── styles.scss                          # @use 'styles/main'
```


### 6. Ejemplo de componente encapsulado usando variables globales

#### card.component.ts

```typescript
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-card',
  standalone: true,
  templateUrl: './card.component.html',
  styleUrls: ['./card.component.scss']
  // Encapsulation.Emulated por defecto
})
export class CardComponent {
  @Input() title = '';
  @Input() image = '';
}
```

### card.component.scss

```scss
// Usa variables globales definidas en ITCSS
// Las custom properties atraviesan la encapsulación

:host {
  display: block;
}

.card {
  background-color: var(--color-surface);
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  overflow: hidden;
  
  &__image {
    width: 100%;
    aspect-ratio: 16/9;
    object-fit: cover;
  }
  
  &__body {
    padding: var(--spacing-md);
  }
  
  &__title {
    font-size: var(--font-size-lg);
    margin-bottom: var(--spacing-sm);
  }
}

// Tema oscuro usando :host-context
:host-context(.dark-theme) {
  .card {
    background-color: var(--color-surface-dark);
  }
}
```

### 7. Comparativa de rendimiento

| Enfoque | Tamaño CSS | Repintado | Especificidad | Mantenibilidad |
|---------|------------|-----------|---------------|----------------|
| ITCSS + BEM puro | ⭐ Menor | ⭐ Óptimo | ⭐ Controlada | ⚠️ Requiere disciplina |
| Todo encapsulado | ⚠️ Mayor (duplicación) | ⚠️ Más cálculos | ✅ Aislada | ✅ Fácil por componente |
| **Híbrido** | ✅ Equilibrado | ✅ Equilibrado | ✅ Controlada + aislada | ✅ Mejor de ambos mundos |
| Shadow DOM puro | ⚠️ Mayor | ⭐ Óptimo (aislado) | ✅ Totalmente aislada | ⚠️ Más complejo |
| **Híbrido con Shadow DOM** | ✅ Equilibrado | ⭐ Óptimo donde importa | ✅ Máximo control | ✅ Profesional |


### 8. Resumen: qué enfoque elegir

| Situación | Enfoque recomendado | Configuración |
|-----------|---------------------|---------------|
| Proyecto educativo | ITCSS + BEM puro | `ViewEncapsulation.None` en todo |
| Proyecto pequeño, equipo disciplinado | ITCSS + BEM puro | `ViewEncapsulation.None` en todo |
| Proyecto mediano, varios desarrolladores | **Híbrido con Emulated** | Layout global + componentes UI encapsulados |
| Proyecto grande, múltiples equipos | **Híbrido con Emulated** | ITCSS global + encapsulación por defecto |
| Librería de componentes | **Híbrido con Shadow DOM** | Variables globales + Shadow DOM en componentes |
| Microfrontends | Shadow DOM puro | Máximo aislamiento entre aplicaciones |


### 9. Regla práctica para decidir

| Pregunta | Si la respuesta es SÍ → | Si la respuesta es NO → |
|----------|-------------------------|-------------------------|
| ¿El componente se usa solo una vez? | Global con BEM | Evaluar encapsulación |
| ¿El componente tiene muchas variantes? | Encapsulado | Global con modificadores BEM |
| ¿Varios desarrolladores tocan este componente? | Encapsulado | Global está bien |
| ¿Es un componente de layout (header, footer)? | Global con BEM | Evaluar según complejidad |
| ¿Necesita funcionar en cualquier contexto externo? | Shadow DOM | Emulated o global |

