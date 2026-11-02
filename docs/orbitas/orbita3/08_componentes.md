# 8. Componentes: el set mínimo

Casi todas las aplicaciones, sean de reservas, de compras o de gestión, están construidas con los mismos tipos de pieza: botones, campos de formulario, tarjetas, una navegación, unos cuantos estilos de texto, etiquetas, cuadros de diálogo y avisos. Las diferencias entre una aplicación y otra están en cómo se ven esas piezas y en cómo se combinan, y eso es justo lo que decidiste en tu sistema de Figma. En este apartado vas a ver cómo se construye en código cada uno de esos componentes, juntando todo lo de los apartados anteriores: el HTML correcto, los tokens, la arquitectura ITCSS, los nombres de BEM y los estados.

Todos los ejemplos son los componentes del polideportivo, y todo el código compila con Sass y se ha probado en el navegador en modo claro, en modo oscuro y en un ancho de móvil. Tómalos como referencia y adáptalos a tu sistema: tus componentes tienen que salir de tus diseños de Figma, con tus tokens y tus variantes, y en la auditoría oral te puedo preguntar por qué cualquiera de ellos es como es (RA2-f, RA2-g).

![Los pasos para construir un componente: del componente de Figma al HTML, los nombres de BEM, los tokens, los estados y la comprobación final](img/orbita3_08_esquema_componente.svg)

## Cómo se construye un componente

Antes de ver cada componente, conviene que tengas un método, porque es el mismo para todos. Te recomiendo seguir estos pasos cada vez, en este orden:

1. **Abre el componente en Figma** con todas sus variantes a la vista y apunta su anatomía: qué partes tiene, qué tokens usa cada parte y qué variantes y estados existen.
2. **Escribe el HTML** eligiendo el elemento correcto para cada parte (un botón es un `<button>`, una tarjeta de pista un `<article>`), como viste en el repaso de HTML5.
3. **Pon los nombres de BEM**: el componente es el bloque, sus partes son elementos y sus variantes, modificadores.
4. **Escribe el SCSS** en su propio parcial de la capa de componentes, usando solo tokens semánticos y, si tiene variantes, tokens de componente.
5. **Añade los estados** con pseudoclases y atributos: hover, foco, pulsado, desactivado, seleccionado, error.
6. **Comprueba el componente** en modo claro y oscuro, con el teclado, con la letra al 200 % y en un ancho de móvil.

Una buena forma de hacer la última comprobación es tener en tu proyecto una página de prueba con todos tus componentes, en todas sus variantes y estados, uno debajo de otro. Es lo que hacen los equipos que mantienen un sistema de diseño, con herramientas como Storybook o con una página sencilla de HTML, y te permite ver de un vistazo si un cambio en un token ha estropeado algún componente.

## Botones

El botón es el componente más importante de cualquier interfaz y el que más estados tiene. En el polideportivo hay tres variantes: el principal ("Reservar"), el secundario ("Ver más horas") y el de peligro ("Cancelar reserva").

```html
<button class="button" type="submit">Reservar</button>
<button class="button button--secondary" type="button">Ver más horas</button>
<button class="button button--danger" type="button">Cancelar reserva</button>

<a class="button button--secondary" href="/reservas">Ver mis reservas</a>
```

Recuerda la regla del repaso de HTML5: si lleva a otra pantalla, es un enlace con aspecto de botón; si hace algo, es un `<button>`. El mismo componente sirve para los dos.

```scss
// components/_button.scss
@use "../tools" as *;

.button {
  // Tokens de componente
  --button-bg: var(--color-primary);
  --button-bg-hover: color-mix(in oklch, var(--color-primary), black 15%);
  --button-fg: var(--color-on-primary);
  --button-border: transparent;

  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-2);
  min-height: 2.75rem;                       // objetivo táctil de 44 px
  padding: var(--space-3) var(--space-6);
  border: 2px solid var(--button-border);
  border-radius: var(--radius-md);
  background-color: var(--button-bg);
  color: var(--button-fg);
  font: var(--font-label);
  text-decoration: none;
  cursor: pointer;
  transition: background-color var(--duration-fast) ease;

  &:hover { background-color: var(--button-bg-hover); }

  &:focus-visible { @include focus-ring; }

  &:active { translate: 0 1px; }

  &:disabled,
  &[aria-disabled="true"] {
    opacity: 0.5;
    cursor: not-allowed;
  }

  &__icon {
    inline-size: 1.25rem;
    block-size: 1.25rem;
  }

  &--secondary {
    --button-bg: transparent;
    --button-bg-hover: color-mix(in oklch, var(--color-primary), transparent 90%);
    --button-fg: var(--color-primary);
    --button-border: var(--color-primary);
  }

  &--danger {
    --button-bg: var(--color-error);
    --button-bg-hover: color-mix(in oklch, var(--color-error), black 15%);
    --button-fg: var(--color-on-error);
  }

  &--block { width: 100%; }
}
```

Fíjate en cómo están resueltos los estados. El `:hover` usa un token de componente, `--button-bg-hover`, y cada variante decide cuál es el suyo, de modo que la regla del hover se escribe una sola vez. El borde de 2 píxeles existe en todas las variantes (transparente en la principal), para que el secundario, que sí lo muestra, mida exactamente lo mismo que los demás. Y el foco usa el mixin común de todos los componentes.

Hay dos detalles de accesibilidad que conviene tener presentes. El primero es que un botón desactivado con `disabled` no recibe el foco ni se anuncia al recorrer la pantalla con el tabulador, así que la persona no sabe que existe ni por qué no puede pulsarlo. Si es importante que se sepa (por ejemplo, el botón "Reservar" antes de elegir hora), es mejor dejarlo activo y explicar qué falta al pulsarlo, o usar `aria-disabled="true"` y controlar la pulsación con JavaScript. El segundo es que un enlace no admite `disabled`, por eso el componente también responde a `aria-disabled`.

## Campos de formulario

Los campos de formulario son varios componentes que trabajan juntos. El bloque `.field` agrupa la etiqueta, el control, la ayuda y el mensaje de error; el bloque `.input` da estilo a los controles de texto, a las listas desplegables y a las áreas de texto; y el bloque `.choice`, a las casillas y a los botones de opción.

```html
<div class="field">
  <label class="field__label" for="phone">Teléfono de contacto</label>
  <input class="input" type="tel" id="phone" name="phone" required
         autocomplete="tel" aria-describedby="phone-hint phone-error">
  <p class="field__hint" id="phone-hint">Solo lo usaremos si hay que cancelar la pista.</p>
  <p class="field__error" id="phone-error">Escribe un teléfono para poder avisarte.</p>
</div>

<div class="field">
  <label class="field__label" for="sport">Deporte</label>
  <select class="input" id="sport" name="sport">
    <option>Pádel</option>
    <option>Tenis</option>
  </select>
</div>

<div class="field">
  <label class="field__label" for="notes">Observaciones</label>
  <textarea class="input input--textarea" id="notes" name="notes"></textarea>
</div>

<label class="choice">
  <input class="choice__control" type="checkbox" name="rules" required>
  He leído las normas de uso de la pista
</label>
```

```scss
// components/_field.scss
@use "../tools" as *;

.field {
  display: flex;
  flex-direction: column;
  gap: var(--space-1);

  &__label { font: var(--font-label); }

  &__hint,
  &__error {
    margin: 0;
    font: var(--font-caption);
    color: var(--color-on-surface-variant);
  }

  &__error {
    display: none;
    color: var(--color-error);
  }

  &:has(:user-invalid) &__error { display: block; }
}

.input {
  min-height: 2.75rem;
  padding: var(--space-2) var(--space-3);
  border: 1px solid var(--color-outline);
  border-radius: var(--radius-sm);
  background-color: var(--color-surface-raised);
  color: var(--color-on-surface);

  &:focus-visible {
    @include focus-ring;
    border-color: var(--color-primary);
  }

  &:user-invalid {
    border-color: var(--color-error);
    border-width: 2px;
  }

  &--textarea {
    min-height: 6rem;
    resize: vertical;
  }
}

.choice {
  display: flex;
  align-items: center;
  gap: var(--space-2);
  min-height: 2.75rem;
  cursor: pointer;

  &__control {
    inline-size: 1.25rem;
    block-size: 1.25rem;
    margin: 0;
    accent-color: var(--color-primary);
  }

  &:has(:focus-visible) { @include focus-ring; }
}
```

En este componente hay tres decisiones que conviene entender:

- **El mensaje de error solo aparece cuando hace falta.** Gracias a `:user-invalid` y a `:has()`, el bloque del campo muestra su mensaje cuando la persona ha tocado el campo y el valor no es válido, sin una línea de JavaScript. Como el mensaje está asociado al campo con `aria-describedby`, el lector de pantalla lo lee al llegar a él. Fíjate también en que el error no depende solo del color: el borde se hace más grueso y aparece un texto.
- **El borde del campo cumple el contraste.** Las WCAG piden al menos 3:1 para los bordes que permiten identificar un control, y por eso `--color-outline` apunta a un gris más oscuro que el de las líneas decorativas.
- **Las casillas y los botones de opción usan el control nativo**, coloreado con **`accent-color`**. Es la forma más sencilla de darles el color de tu sistema manteniendo todo su funcionamiento, y en las listas desplegables ocurre algo parecido: se les cambia el borde, el relleno y la tipografía, pero se mantiene el desplegable del sistema, que en el móvil es mucho más cómodo que cualquiera hecho a mano.

### Las píldoras de hora

Las píldoras de hora del polideportivo son un caso especial de botón de opción. Visualmente son botones con forma de píldora, pero por dentro son botones de opción con el mismo `name`, porque solo se puede elegir una hora. El control nativo se oculta visualmente (sin quitarlo, para que siga funcionando con el teclado y con el lector de pantalla), y la etiqueta entera cambia de aspecto con `:has()`.

```html
<fieldset class="o-cluster">
  <legend class="field__label">Hora</legend>
  <label class="slot"><input class="slot__input" type="radio" name="time" value="18:00"> 18:00</label>
  <label class="slot"><input class="slot__input" type="radio" name="time" value="19:00"> 19:00</label>
  <label class="slot"><input class="slot__input" type="radio" name="time" value="20:00" disabled> 20:00</label>
</fieldset>
```

```scss
// components/_slot.scss
@use "../tools" as *;

.slot {
  display: inline-flex;
  align-items: center;
  min-height: 2.75rem;
  padding: var(--space-2) var(--space-4);
  border: 1px solid var(--color-primary);
  border-radius: var(--radius-full);
  font: var(--font-label);
  cursor: pointer;
  transition: background-color var(--duration-fast) ease;

  &__input { @include visually-hidden; }

  &:has(:checked) {
    background-color: var(--color-primary);
    color: var(--color-on-primary);
  }

  &:has(:focus-visible) { @include focus-ring; }

  &:has(:disabled) {
    opacity: 0.5;
    text-decoration: line-through;
    cursor: not-allowed;
  }
}
```

Con los botones de opción nativos, el teclado funciona exactamente como espera una persona que lo usa: el tabulador entra en el grupo, las flechas pasan de una hora a otra y las horas ocupadas se saltan solas. Si las píldoras fueran `<div>` con un evento de clic, habría que programar todo eso a mano.

## Tarjetas

La tarjeta de pista es el componente que más aparece en el polideportivo: en el listado, en el resumen de la reserva y en "Mis reservas". Por eso tiene que funcionar a cualquier ancho y no puede decidir dónde se coloca.

```html
<article class="card">
  <img class="card__media" src="img/pista-padel-2-800.webp" alt=""
       width="800" height="450" loading="lazy">
  <div class="card__header">
    <h3 class="card__title">Pista de pádel 2</h3>
    <p class="card__price">8 € / hora</p>
  </div>
  <p class="card__meta">Cubierta · Iluminación incluida</p>
  <span class="badge badge--free">Libre</span>
  <div class="card__actions">
    <a class="button button--block" href="/pistas/padel-2">Ver horarios</a>
  </div>
</article>
```

```scss
// components/_card.scss
.card {
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
  padding: var(--space-4);
  border: 1px solid var(--color-outline);
  border-radius: var(--radius-md);
  background-color: var(--color-surface-raised);
  box-shadow: var(--elevation-1);

  &__media {
    aspect-ratio: 16 / 9;
    object-fit: cover;
    border-radius: var(--radius-sm);
  }

  &__header {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    gap: var(--space-2);
  }

  &__title { font: var(--font-heading-3); margin: 0; }

  &__price {
    margin: 0;
    font: var(--font-label);
    font-variant-numeric: tabular-nums;
  }

  &__meta {
    margin: 0;
    font: var(--font-caption);
    color: var(--color-on-surface-variant);
  }

  &__actions { margin-block-start: auto; }

  &--featured { border: 2px solid var(--color-primary); }
}
```

La imagen lleva `alt=""` porque en esta tarjeta es decorativa: el nombre de la pista ya está en el título, y anunciar "foto de una pista de pádel" no añadiría nada. Si la foto ayudara a reconocer la pista, el `alt` lo describiría. El precio usa cifras de ancho fijo para que los precios de varias tarjetas se alineen, y `card__actions` se empuja al final con `margin-block-start: auto`, de modo que, en una cuadrícula, los botones de todas las tarjetas quedan a la misma altura aunque sus textos tengan distinta longitud.

Si la tarjeta tiene que cambiar de composición según el espacio disponible (la foto a la izquierda cuando la tarjeta es ancha), declara el contenedor que la rodea con `container-type: inline-size` y usa una container query dentro del componente, como viste en los apuntes de CSS3.

## Navegación

Una aplicación como el polideportivo necesita dos navegaciones distintas: en escritorio, un menú horizontal en la cabecera, y en el móvil, una **barra de pestañas** en la parte inferior de la pantalla, que es el patrón que la mayoría de las personas conoce de las aplicaciones de su teléfono y que queda al alcance del pulgar.

```html
<nav class="main-nav" aria-label="Principal">
  <ul class="main-nav__list">
    <li><a class="main-nav__link" href="/pistas" aria-current="page">Pistas</a></li>
    <li><a class="main-nav__link" href="/reservas">Mis reservas</a></li>
    <li><a class="main-nav__link" href="/perfil">Perfil</a></li>
  </ul>
</nav>

<nav class="tab-bar" aria-label="Secciones">
  <ul class="tab-bar__list">
    <li>
      <a class="tab-bar__link" href="/pistas" aria-current="page">
        <svg class="tab-bar__icon" aria-hidden="true"><use href="img/iconos.svg#court"></use></svg>
        Pistas
      </a>
    </li>
    <!-- ... -->
  </ul>
</nav>
```

```scss
// components/_nav.scss
@use "../tools" as *;

.main-nav {
  display: none;

  @include from("md") { display: block; }

  &__list {
    display: flex;
    gap: var(--space-6);
    margin: 0;
    padding: 0;
    list-style: none;
  }

  &__link {
    display: inline-flex;
    align-items: center;
    min-height: 2.75rem;
    color: var(--color-on-surface);
    font: var(--font-label);
    text-decoration: none;

    &:hover { color: var(--color-primary); }
    &:focus-visible { @include focus-ring; }

    &[aria-current="page"] {
      color: var(--color-primary);
      text-decoration: underline;
      text-decoration-thickness: 3px;
      text-underline-offset: 0.4em;
    }
  }
}

.tab-bar {
  position: sticky;
  bottom: 0;
  background-color: var(--color-surface-raised);
  box-shadow: var(--elevation-2);

  @include from("md") { display: none; }

  &__list {
    display: grid;
    grid-auto-flow: column;
    grid-auto-columns: 1fr;
    margin: 0;
    padding: 0;
    list-style: none;
  }

  &__link {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--space-1);
    min-height: 3.5rem;
    padding-block: var(--space-2);
    color: var(--color-on-surface-variant);
    font: var(--font-caption);
    text-decoration: none;

    &:focus-visible { @include focus-ring; }

    &[aria-current="page"] {
      color: var(--color-primary);
      font-weight: 700;
    }
  }

  &__icon {
    inline-size: 1.5rem;
    block-size: 1.5rem;
  }
}
```

Las dos navegaciones están en el HTML a la vez, y el CSS muestra una u otra según el ancho, con el mixin de breakpoint. Como cada una tiene su `aria-label`, un lector de pantalla puede distinguirlas, y como la que no se ve tiene `display: none`, tampoco se anuncia. La pantalla actual se marca con `aria-current="page"`, que sirve a la vez para el estilo y para que el lector de pantalla diga "página actual". Y la pestaña activa no se distingue solo por el color: también cambia el grosor de la letra.

El menú desplegable que se abre con un botón (el llamado "menú hamburguesa") necesita JavaScript para abrirse y cerrarse y para gestionar el foco, así que lo dejaremos para cuando trabajes la navegación por teclado en la Órbita 4. Para una aplicación con tres o cuatro secciones, como el polideportivo, la barra de pestañas es además más rápida de usar, porque todas las secciones están siempre a la vista.

## Componentes tipográficos

En el repaso de HTML5 viste que el nivel de un encabezado lo decide la estructura de la pantalla, y en ITCSS, que la capa Elements da a cada encabezado el estilo de su nivel en tu escala. Pero a veces un texto tiene que verse con un nivel de la escala distinto del que le corresponde por estructura: el título de una tarjeta es un `<h3>` y quizá tu diseño lo pide con el estilo de `body` en negrita, o un texto de bienvenida es un `<p>` que se ve como `display`. Para eso sirve el bloque `.text`, con un modificador por cada nivel de tu escala.

```html
<p class="text text--display">¿A qué jugamos hoy?</p>
<h2 class="text text--heading-3">Tus próximas reservas</h2>
<p class="text text--caption">Reserva hecha el 2 de noviembre</p>
```

```scss
// components/_text.scss
.text {
  margin: 0;

  &--display   { font: var(--font-display); }
  &--heading-1 { font: var(--font-heading-1); }
  &--heading-2 { font: var(--font-heading-2); }
  &--heading-3 { font: var(--font-heading-3); }
  &--body      { font: var(--font-body); }
  &--label     { font: var(--font-label); }
  &--caption   {
    font: var(--font-caption);
    color: var(--color-on-surface-variant);
  }
}

.prose {
  max-width: 65ch;

  > * + * { margin-block-start: var(--space-4); }
}
```

El bloque `.prose` resuelve otro caso habitual, el de los textos largos (las normas de uso de las pistas, la política de cancelación): limita el ancho de las líneas a unos 65 caracteres, que es lo cómodo para leer, y separa cada párrafo, lista o título del anterior con el selector `> * + *`, que selecciona todos los hijos menos el primero. Así no hace falta poner una clase a cada párrafo.

## Etiquetas

Las etiquetas (*badges*) son textos cortos que indican un estado o una categoría, como "Libre" o "Completa" en las tarjetas de pista. Son el ejemplo más claro de componente resuelto con un único token de componente.

```html
<span class="badge badge--free">Libre</span>
<span class="badge badge--full">Completa</span>
```

```scss
// components/_badge.scss
.badge {
  --badge-color: var(--color-primary);

  display: inline-flex;
  width: fit-content;                 // no se estira dentro de un contenedor flexible
  align-items: center;
  gap: var(--space-1);
  padding: var(--space-1) var(--space-3);
  border: 2px solid var(--badge-color);
  border-radius: var(--radius-full);
  color: var(--badge-color);
  font: var(--font-label);

  &--free { --badge-color: var(--color-success); }
  &--full { --badge-color: var(--color-error); }
}
```

Como el color de la etiqueta se usa para el texto, tiene que llegar a 4,5:1 de contraste con el fondo de la tarjeta, en los dos modos. Y como el texto ya dice el estado ("Libre", "Completa"), el color nunca es la única pista.

## Diálogos

Un cuadro de diálogo interrumpe lo que la persona está haciendo para pedirle una confirmación o enseñarle algo importante, así que conviene usarlo poco: en el polideportivo solo aparece al cancelar una reserva, porque es una acción que no se puede deshacer. El elemento **`<dialog>`** de HTML resuelve casi todo el comportamiento: al abrirlo con `showModal()`, el navegador lo coloca por encima de todo, oscurece el fondo, impide interactuar con el resto de la página, lleva el foco al diálogo y lo cierra con la tecla Escape.

```html
<button class="button button--danger" type="button" data-dialog="cancel-dialog">
  Cancelar reserva
</button>

<dialog class="dialog" id="cancel-dialog" aria-labelledby="cancel-title">
  <h2 class="dialog__title" id="cancel-title">¿Cancelar la reserva?</h2>
  <p class="dialog__body">Se liberará la pista de pádel 2 el jueves 12 a las 19:00. Esta acción no se puede deshacer.</p>
  <form class="dialog__actions" method="dialog">
    <button class="button button--secondary" value="back">Mantener la reserva</button>
    <button class="button button--danger" value="confirm">Sí, cancelar</button>
  </form>
</dialog>

<script>
  document.querySelector('[data-dialog="cancel-dialog"]')
    .addEventListener('click', () => document.getElementById('cancel-dialog').showModal());
</script>
```

```scss
// components/_dialog.scss
.dialog {
  width: min(100% - 2 * var(--space-4), 28rem);
  padding: var(--space-6);
  border: none;
  border-radius: var(--radius-lg);
  background-color: var(--color-surface-raised);
  color: var(--color-on-surface);
  box-shadow: var(--elevation-3);

  &::backdrop { background-color: rgb(0 0 0 / 50%); }

  &__title { font: var(--font-heading-2); margin: 0; }

  &__body { margin-block: var(--space-4); }

  &__actions {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-end;
    gap: var(--space-2);
  }
}
```

Las tres líneas de JavaScript solo abren el diálogo, y cerrarlo no necesita ninguna: un formulario con `method="dialog"` cierra el diálogo al pulsar cualquiera de sus botones, y el `value` del botón pulsado queda disponible para saber qué eligió la persona. El pseudoelemento **`::backdrop`** es la capa que oscurece el fondo. El diálogo se nombra con `aria-labelledby`, que apunta a su título, para que el lector de pantalla lo anuncie al abrirse.

Fíjate también en los textos de los botones. "Mantener la reserva" y "Sí, cancelar" dicen exactamente lo que pasará al pulsarlos, a diferencia de un "Aceptar" y un "Cancelar" que, en un diálogo para cancelar algo, se prestan a confusión. Y el botón que no destruye nada no está escondido ni tiene un texto que haga sentir mal a quien lo pulsa, algo que revisarás con más detalle en la auditoría de patrones engañosos de la Órbita 5.

## Avisos

Los avisos (*alerts*) comunican el resultado de una acción o una información importante: que la reserva se ha confirmado, que no se ha podido guardar o que el polideportivo cierra antes en festivos. Tienen variantes para cada tipo de mensaje, y todas usan los colores de estado de tu sistema.

```html
<div class="alert alert--success" role="status">
  <svg class="alert__icon" aria-hidden="true"><use href="img/iconos.svg#check"></use></svg>
  <div>
    <p class="alert__title">Reserva confirmada</p>
    <p class="alert__text">Pádel 2, jueves 12 de noviembre a las 19:00.</p>
  </div>
</div>
```

```scss
// components/_alert.scss
.alert {
  --alert-bg: var(--color-surface-raised);
  --alert-accent: var(--color-primary);

  display: flex;
  align-items: flex-start;
  gap: var(--space-3);
  padding: var(--space-4);
  border-inline-start: 4px solid var(--alert-accent);
  border-radius: var(--radius-sm);
  background-color: var(--alert-bg);

  &__icon {
    flex-shrink: 0;
    inline-size: 1.5rem;
    block-size: 1.5rem;
    color: var(--alert-accent);
  }

  &__title { margin: 0; font: var(--font-label); }
  &__text  { margin: 0; }

  &--success { --alert-accent: var(--color-success); }
  &--error   { --alert-accent: var(--color-error); }
  &--warning { --alert-accent: var(--color-warning); }
}
```

El atributo **`role`** decide cómo se anuncia el aviso cuando aparece en pantalla después de una acción. Con `role="status"`, el lector de pantalla lo lee cuando termina lo que estaba diciendo, que es lo adecuado para las confirmaciones. Con `role="alert"`, lo lee inmediatamente, interrumpiendo, y solo se usa para errores que la persona tiene que conocer en ese momento. Verás estos atributos con detalle en la Órbita 4. Como en todos los componentes, el tipo de aviso no depende solo del color: el título y el icono dicen también qué ha pasado.

## Los objetos que los colocan

Ninguno de estos componentes decide dónde se coloca ni cuánto espacio deja a su alrededor, y eso es lo que permite reutilizarlos. La colocación la hacen los objetos de ITCSS: `.o-container` centra el contenido con un ancho máximo, `.o-stack` coloca los elementos uno debajo de otro con la separación de tu escala, `.o-cluster` los pone en fila y los pasa a la línea siguiente si no caben, y `.o-grid` reparte las tarjetas en tantas columnas como quepan.

```html
<main class="o-container o-stack">
  <h1>Elegir hora</h1>
  <div class="alert alert--success" role="status">...</div>
  <ul class="o-grid" role="list">
    <li><article class="card">...</article></li>
    <li><article class="card card--featured">...</article></li>
  </ul>
  <form class="o-stack">...</form>
</main>
```

Con unos pocos objetos y una docena de componentes puedes construir todas las pantallas del polideportivo, y si una pantalla nueva necesita algo que no tienes, la pregunta que hay que hacerse es si es un componente nuevo de tu sistema (y entonces tiene que existir también en Figma) o una variante de uno que ya tienes.

## Antes de seguir

Antes de dar un componente por terminado, comprueba que cumple todo esto:

1. Tiene **el mismo nombre, las mismas partes y las mismas variantes** que en Figma.
2. Su HTML usa **el elemento correcto** para cada parte.
3. Su SCSS está **en su propio parcial**, usa **solo tokens semánticos** y sus selectores tienen **una sola clase**.
4. Todos sus **estados** funcionan: hover, foco visible, pulsado, desactivado y, si los tiene, seleccionado y error.
5. Se ve bien en **modo claro y en modo oscuro**, con el contraste comprobado en los dos.
6. Se puede usar **solo con el teclado**, y los objetivos táctiles miden al menos 44 × 44 píxeles.
7. Aguanta **la letra al 200 %** y un **ancho de móvil** sin cortarse ni solaparse.
8. **No decide dónde se coloca**: ni márgenes exteriores ni anchos fijos.

Si en algún momento usas una IA para generar el código de un componente, anótalo en el `CHANGELOG.md` y revísalo con esta misma lista. Las herramientas que generan componentes a partir de una descripción suelen usar `<div>` en lugar de botones, valores escritos a mano en lugar de tus tokens y nombres de clase que no siguen BEM, y adaptarlo a tu sistema es parte del trabajo.

## Recursos

- [El elemento `<dialog>` (MDN Web Docs)](https://developer.mozilla.org/es/docs/Web/HTML/Element/dialog)
- [`accent-color` (MDN Web Docs)](https://developer.mozilla.org/es/docs/Web/CSS/accent-color)
- [GOV.UK Design System](https://design-system.service.gov.uk/components/), un sistema de diseño público con componentes accesibles muy bien documentados
- [Open UI](https://open-ui.org/), donde se estudia cómo están construidos los componentes en los sistemas de diseño más conocidos
