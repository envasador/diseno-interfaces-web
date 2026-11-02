# 5. Nomenclatura BEM

Con ITCSS ya sabes en qué fichero va cada regla, pero queda otra decisión que vas a tomar cientos de veces durante la órbita: **cómo se llama cada clase**. Parece un detalle menor, y sin embargo es lo que más se nota cuando un proyecto crece. Si el título de la tarjeta se llama `.titulo`, chocará con el título del diálogo; si se llama `.card .title`, su especificidad será más alta que la de cualquier otra regla de una sola clase; y si se llama `.card-title-big`, dentro de un mes nadie sabrá si existe también un `.card-title-small` ni dónde está. BEM es una convención para poner nombres que resuelve esos tres problemas a la vez, y en este módulo es la forma de nombrar las clases de tus componentes (RA2-g).

BEM significa *Block, Element, Modifier* (bloque, elemento y modificador). Lo creó el equipo de Yandex, el buscador ruso, para mantener interfaces enormes con muchas personas trabajando a la vez, y hoy es la convención de nombres más extendida en CSS. Encaja de forma natural con lo que ya tienes: cada componente de tu sistema de Figma es un bloque, sus capas son elementos y sus variantes son modificadores.

![Anatomía de la tarjeta de pista con BEM: el bloque card, sus elementos y el modificador card--featured](img/orbita3_05_esquema_bem.svg)

## Qué problema resuelve

Las clases de CSS viven todas en un mismo espacio: si dos componentes usan una clase llamada `.title`, las dos reglas se aplican a los dos títulos y se pisan entre sí. La solución habitual cuando no hay convención es apoyarse en el contexto (`.card .title`, `.dialog .title`), pero eso tiene dos costes. El primero es que la especificidad sube y deja de ser uniforme, que es justo lo que ITCSS intenta evitar. El segundo es que el estilo queda atado a la estructura del HTML: si mañana el título de la tarjeta se mueve fuera del `<article>`, deja de tener estilo.

BEM evita las dos cosas con una idea sencilla: **cada parte de un componente tiene su propia clase, y el nombre de la clase ya dice a qué componente pertenece**. El título de la tarjeta se llama `.card__title` y el del diálogo `.dialog__title`, no pueden chocar, y los dos se seleccionan con una sola clase, con la misma especificidad (0, 1, 0) que cualquier otra regla de tus componentes.

## Bloque, elemento y modificador

### El bloque

Un **bloque** es un componente con sentido propio, que se puede colocar en cualquier sitio de la aplicación y seguir funcionando: `.button`, `.card`, `.slot`, `.alert`, `.main-nav`. El nombre del bloque es el del componente en tu sistema de Figma, y si el nombre tiene varias palabras, se separan con un guion (`.main-nav`, `.tab-bar`).

Los bloques pueden ir unos dentro de otros (una tarjeta puede contener un botón), pero cada uno sigue siendo independiente: el botón que hay dentro de la tarjeta es un `.button` normal, con su propio aspecto, y la tarjeta no le cambia nada.

### El elemento

Un **elemento** es una parte de un bloque que no tiene sentido fuera de él: el título de la tarjeta, su precio, su imagen, el icono de un botón. Se nombra con el nombre del bloque, **dos guiones bajos** y el nombre del elemento.

```html
<article class="card">
  <img class="card__media" src="img/pista-padel-2.webp" alt="" width="640" height="360">
  <div class="card__header">
    <h3 class="card__title">Pista de pádel 2</h3>
    <p class="card__price">8 € / hora</p>
  </div>
  <p class="card__meta">Cubierta · Iluminación incluida</p>
</article>
```

### El modificador

Un **modificador** es una variante o un estado de un bloque o de un elemento: la tarjeta destacada, el botón de peligro, el botón secundario. Se nombra con el nombre del bloque (o del elemento), **dos guiones** y el nombre de la variante, y **siempre acompaña a la clase base, nunca la sustituye**.

```html
<button class="button button--danger" type="button">Cancelar reserva</button>
<article class="card card--featured">...</article>
```

La razón de llevar las dos clases es que el modificador solo describe lo que cambia. Toda la estructura del botón (el relleno, la tipografía, el radio, los estados) está en `.button`, y `.button--danger` solo cambia el color. Si quitaras `.button`, el botón de cancelar perdería todo lo demás.

## La sintaxis

Resumiendo, un nombre de BEM tiene, como mucho, estas tres partes:

```text
bloque__elemento--modificador
card__title
button--danger
card__price--discount
```

Dentro de cada parte, las palabras se escriben **en minúsculas y separadas por un guion** (`main-nav__link`, `tab-bar__icon`). En este módulo los nombres van en inglés, igual que los tokens de la Órbita 2, para que el sistema use un único idioma en Figma, en las propiedades personalizadas y en las clases.

Al principio los dobles guiones resultan raros de leer y de escribir. Se acostumbra uno en un par de días, y a cambio puedes saber qué es cada clase con solo leerla en el HTML, y encontrar todo lo que pertenece a un componente buscando `card__` o `card--` en el proyecto.

## Reglas que conviene no romper

BEM es una convención y nada impide saltársela, pero cada una de estas reglas evita un problema concreto que acabarías encontrando:

1. **Un elemento pertenece al bloque, nunca a otro elemento.** Aunque el título esté dentro de la cabecera de la tarjeta, se llama `.card__title` y no `.card__header__title`. El nombre no refleja el árbol del HTML, solo a qué bloque pertenece la pieza, y así puedes mover el título fuera de la cabecera sin cambiarle el nombre.
2. **Un modificador nunca va solo.** Siempre `class="button button--danger"`, nunca `class="button--danger"`.
3. **Un bloque no depende de dónde está.** Nada de `.sidebar .card` para cambiar la tarjeta cuando está en la barra lateral. Si la tarjeta necesita verse distinta, es una variante (`.card--compact`) o una container query, como viste en los apuntes de CSS3.
4. **Un elemento no se usa fuera de su bloque.** Un `.card__title` suelto, fuera de una tarjeta, es una señal de que esa pieza debería ser un bloque propio.
5. **Una sola clase por selector.** Los selectores de tus componentes son siempre de una clase (`.card__title`), con las únicas excepciones de las pseudoclases y los atributos de estado (`.button:hover`, `.main-nav__link[aria-current="page"]`).

## Mezclar bloques en un mismo elemento

A veces un mismo nodo de HTML es a la vez una parte de un bloque y un bloque en sí mismo. En la pantalla de reserva, el resumen lateral es un elemento de la pantalla (`booking__summary`), porque su posición la decide la cuadrícula de la pantalla, y al mismo tiempo es una tarjeta (`card`), porque tiene su aspecto. BEM lo resuelve con una **mezcla**: el nodo lleva las clases de los dos.

```html
<aside class="booking__summary card">...</aside>
```

```scss
.booking__summary { grid-area: summary; }   // la pantalla decide dónde va
.card { /* aspecto de la tarjeta */ }       // la tarjeta decide cómo se ve
```

Las mezclas son la forma correcta de que un bloque coloque a otro sin tocar su aspecto, y encajan con la regla de ITCSS de que un componente no se coloca solo.

## Estados: modificadores, atributos y pseudoclases

Hay variantes que se eligen al escribir el HTML (el botón de peligro siempre es de peligro) y estados que cambian mientras la persona usa la aplicación (una hora seleccionada, un menú abierto, un campo con error). Para los primeros se usan modificadores, y para los segundos tienes tres opciones, que conviene usar en este orden de preferencia:

1. **Una pseudoclase nativa**, si existe: `:checked`, `:disabled`, `:user-invalid`, `:focus-visible`, `:hover`. El navegador lleva la cuenta del estado sin que tengas que hacer nada.
2. **Un atributo de HTML o de ARIA**, si el estado tiene que anunciarse: `[aria-current="page"]` para la pantalla actual del menú, `[aria-expanded="true"]` para un desplegable abierto, `[aria-pressed="true"]` para un botón de dos posiciones. Así, la misma información sirve para el CSS y para los lectores de pantalla.
3. **Una clase de estado** con el prefijo `is-` o `has-` (`.is-loading`), solo cuando no hay ni pseudoclase ni atributo que lo exprese, y siempre añadida por JavaScript.

```scss
.main-nav__link {
  color: var(--color-on-surface);

  &[aria-current="page"] {
    color: var(--color-primary);
    text-decoration: underline;
  }
}
```

Si para marcar la pantalla actual usas una clase `.main-nav__link--active`, el menú se ve bien, pero un lector de pantalla no sabe cuál es la pantalla actual. Con `aria-current`, lo sabe, y el CSS sigue siendo de una sola regla.

## De Figma a BEM

Si construiste tus componentes en Figma con nombres claros y con propiedades de variante, ya tienes casi todos los nombres de BEM decididos. La correspondencia es directa:

| En Figma | En BEM | Ejemplo |
|---|---|---|
| Nombre del componente | Bloque | `Card` → `.card` |
| Capas con nombre dentro del componente | Elementos | `Title`, `Price` → `.card__title`, `.card__price` |
| Propiedad de variante de tipo o tamaño | Modificador | `Type=Danger` → `.button--danger` |
| Propiedad de variante de estado | Pseudoclase o atributo | `State=Hover` → `:hover`, `State=Selected` → `:checked` |
| Propiedad booleana (mostrar u ocultar) | Elemento presente o ausente en el HTML | `Show icon` → `.button__icon` |

Para que esta tabla funcione, **las capas de tus componentes en Figma tienen que tener nombre**. Un componente con capas llamadas `Frame 12` y `Text 3` no te dice nada al maquetarlo. Merece la pena dedicar un rato a renombrar las capas de tus componentes con los mismos nombres que tendrán sus elementos de BEM, porque así el diseño y el código usan el mismo vocabulario, igual que pasó con los tokens.

## BEM con Sass

En los apuntes de Sass viste que `&` se sustituye por el selector padre antes de compilar, y que por eso puedes pegarle detrás cualquier texto. Con BEM, eso significa que **cada componente se escribe en un único bloque de Sass**, con todos sus elementos y modificadores dentro, y el CSS compilado tiene selectores de una sola clase:

```scss
.card {
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
  padding: var(--space-4);
  border-radius: var(--radius-md);
  background-color: var(--color-surface-raised);

  &__title { font: var(--font-heading-3); margin: 0; }
  &__price { font: var(--font-label); font-variant-numeric: tabular-nums; }
  &__meta  { font: var(--font-caption); color: var(--color-on-surface-variant); }

  &--featured { border: 2px solid var(--color-primary); }
}
```

Usa `&__` y `&--` para las partes completas del nombre, pero evita trocear los nombres para ahorrarte letras (`.card { &__head { &er { ... } } }` para escribir `card__header`). Funciona, pero nadie encontrará `card__header` al buscarlo en el proyecto.

## BEM y los tokens de componente

Los modificadores y los tokens de componente del apartado 7 están hechos para ir juntos. El bloque declara sus tokens y los usa, y cada modificador cambia solo los tokens que necesita:

```scss
.button {
  --button-bg: var(--color-primary);
  --button-fg: var(--color-on-primary);

  background-color: var(--button-bg);
  color: var(--button-fg);

  &--danger {
    --button-bg: var(--color-error);
    --button-fg: var(--color-on-error);
  }
}
```

Así, un modificador ocupa dos o tres líneas, nunca repite declaraciones del bloque, y si el botón cambia de estructura, todas sus variantes cambian con él.

## Errores frecuentes

| Así no | Así sí | Por qué |
|---|---|---|
| `.card__header__title` | `.card__title` | Los elementos no se anidan en el nombre |
| `class="button--danger"` | `class="button button--danger"` | El modificador acompaña a la clase base |
| `.sidebar .card { ... }` | `.card--compact` o una container query | Un bloque no depende de dónde está |
| `.button-red` | `.button--danger` | Se nombra la función, no el aspecto |
| `.card h3 { ... }` | `.card__title { ... }` | Cada parte tiene su clase, con la misma especificidad |
| `.main-nav__link--active` | `.main-nav__link[aria-current="page"]` | El estado lo entienden también las tecnologías de apoyo |
| `.Card__Title`, `.card_title` | `.card__title` | Minúsculas, guion entre palabras, dos guiones bajos |

## Antes de seguir

Antes de pasar al apartado de multimedia, revisa el HTML y el SCSS de tus componentes:

1. Cada componente de Figma tiene **un bloque con el mismo nombre**.
2. Ningún nombre de clase tiene **dos elementos encadenados** (`__algo__otro`).
3. Todos los modificadores van **junto a su clase base**.
4. Ningún componente cambia el aspecto de otro desde fuera.
5. Los estados usan **pseudoclases o atributos** siempre que existan.
6. Todos los selectores de tus componentes tienen **una sola clase**, salvo las pseudoclases y los atributos de estado.

## Recursos

- [BEM: introducción y guía rápida (getbem.com)](https://getbem.com/introduction/)
- [Documentación oficial de la metodología BEM (bem.info)](https://en.bem.info/methodology/)
- [BEMIT: ITCSS y BEM juntos, de Harry Roberts (CSS Wizardry)](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/)
