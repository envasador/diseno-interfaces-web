# Anexo: el sistema en JavaScript, React y Angular

En los apartados de esta órbita has construido el sistema del polideportivo con HTML, Sass, ITCSS y BEM, en un proyecto sin ningún framework. En DWEC y en tus prácticas en empresa trabajarás con JavaScript, React o Angular, y es normal que te preguntes qué pasa con todo esto cuando el HTML ya no se escribe en un fichero `.html`, sino dentro de componentes. La respuesta corta es que **casi todo sigue igual**: los tokens, las capas de ITCSS y los nombres de BEM funcionan en los tres, y lo que cambia es dónde se guarda cada fichero y cómo se eligen las variantes de un componente.

En este anexo vas a ver el mismo trozo de la aplicación (la pantalla "Elegir hora", con sus tarjetas de pista, sus etiquetas y el diálogo de cancelar la reserva) construido de las tres formas. Los tres proyectos se han creado con las herramientas oficiales, se han compilado y se han probado en el navegador, así que puedes usarlos como punto de partida.

## Lo que no cambia

Antes de ver cada framework, conviene tener claro qué parte del trabajo es independiente de la tecnología, porque es la parte que defiendes en la auditoría oral y la que más te va a durar:

| Pieza del sistema | En los tres frameworks |
|---|---|
| Tokens | Las mismas propiedades personalizadas en `:root`, generadas con Sass |
| Modo oscuro | El mismo `light-dark()` con `color-scheme` |
| Capas de ITCSS | Las mismas carpetas y el mismo orden de `@layer` |
| Nombres de BEM | Las mismas clases: `.card`, `.card__title`, `.button--danger` |
| Estados | Las mismas pseudoclases y los mismos atributos ARIA |
| Accesibilidad del HTML | Los mismos elementos: `<button>`, `<dialog>`, `<article>`, listas |

Lo que cambia es la forma de **escribir el HTML** (en una plantilla, en JSX o en un template de Angular), la forma de **pasar las variantes** (una clase en el HTML, una propiedad del componente) y el sitio donde vive **el SCSS de cada componente**.

## Preparar el proyecto

Los tres proyectos se crean con un comando y se les añade Sass con `npm`. Vanilla y React usan **Vite**, una herramienta que prepara el proyecto, lo sirve mientras programas y lo empaqueta para publicarlo, y que compila los ficheros `.scss` sin configurar nada. Angular tiene su propia herramienta, **Angular CLI**, que también entiende SCSS.

```bash
# JavaScript sin framework
npm create vite@latest polideportivo -- --template vanilla
cd polideportivo && npm install && npm install --save-dev sass

# React
npm create vite@latest polideportivo -- --template react
cd polideportivo && npm install && npm install --save-dev sass

# Angular
npx @angular/cli@latest new polideportivo --style=scss
```

En los tres casos, `npm run dev` (o `ng serve` en Angular) arranca el servidor de desarrollo, y `npm run build` (o `ng build`) genera la versión para publicar, con el CSS ya compilado y comprimido.

## JavaScript sin framework

Sin framework, el proyecto se parece mucho al de los apartados anteriores. La única diferencia es que el SCSS ya no se compila con un script de Sass, sino que lo importa el JavaScript principal y Vite se encarga de compilarlo.

```text
src/
├── main.js
├── components/
│   ├── card.js
│   └── dialog.js
└── scss/
    ├── main.scss
    ├── settings/ tools/ generic/ elements/ objects/
    ├── components/
    └── utilities/
```

```js
// src/main.js
import './scss/main.scss';
import { createCourtCard } from './components/card.js';
import { initDialogs } from './components/dialog.js';

const courts = [
  { name: 'Pista de pádel 1', price: 8, features: ['Exterior'], free: false },
  { name: 'Pista de pádel 2', price: 8, features: ['Cubierta', 'Iluminación incluida'], free: true, featured: true },
];

const list = document.querySelector('#court-list');
courts.forEach((court) => list.append(createCourtCard(court)));

initDialogs();
```

Cuando una parte de la pantalla se genera con JavaScript (por ejemplo, las tarjetas de las pistas, que llegarán de una base de datos), lo más limpio es escribir su HTML en un elemento **`<template>`**, que el navegador guarda sin mostrarlo, y copiarlo cada vez que haga falta. Así el HTML sigue estando en el fichero HTML, con sus clases de BEM, y el JavaScript solo rellena los textos y añade los modificadores.

```html
<!-- index.html -->
<ul class="o-grid" id="court-list" role="list"></ul>

<template id="court-card">
  <li>
    <article class="card">
      <div class="card__header">
        <h2 class="card__title"></h2>
        <p class="card__price"></p>
      </div>
      <p class="card__meta"></p>
      <span class="badge"></span>
    </article>
  </li>
</template>
```

```js
// src/components/card.js
const template = document.querySelector('#court-card');

export function createCourtCard(court) {
  const item = template.content.cloneNode(true);
  const card = item.querySelector('.card');

  card.querySelector('.card__title').textContent = court.name;
  card.querySelector('.card__price').textContent = `${court.price} € / hora`;
  card.querySelector('.card__meta').textContent = court.features.join(' · ');

  const badge = card.querySelector('.badge');
  badge.textContent = court.free ? 'Libre' : 'Completa';
  badge.classList.add(court.free ? 'badge--free' : 'badge--full');

  if (court.featured) card.classList.add('card--featured');

  return item;
}
```

Fíjate en que **las variantes se eligen añadiendo el modificador de BEM** con `classList.add()`, exactamente igual que harías a mano en el HTML. Para los textos se usa `textContent`, que trata todo como texto y evita que un nombre de pista con caracteres extraños se interprete como HTML.

Para el diálogo basta con una función que escuche los clics de toda la página y abra el diálogo cuyo `id` indique el botón. Así, cualquier botón con `data-dialog` funciona sin escribir más JavaScript:

```js
// src/components/dialog.js
export function initDialogs() {
  document.addEventListener('click', (event) => {
    const opener = event.target.closest('[data-dialog]');
    if (!opener) return;
    document.getElementById(opener.dataset.dialog)?.showModal();
  });
}
```

```html
<button class="button button--danger" type="button" data-dialog="cancel-dialog">Cancelar reserva</button>
```

## React

En React, cada componente es una función que devuelve su HTML escrito en **JSX**, una sintaxis muy parecida a HTML que se escribe dentro del JavaScript. La forma más habitual de organizar un proyecto es tener **una carpeta por componente**, con su JSX y su SCSS juntos, de modo que todo lo que pertenece al botón está en la carpeta del botón.

```text
src/
├── main.jsx
├── App.jsx
├── components/
│   ├── Button/
│   │   ├── Button.jsx
│   │   └── Button.scss
│   ├── Badge/
│   ├── CourtCard/
│   └── Dialog/
└── scss/
    ├── main.scss          ← todas las capas menos la de componentes
    └── settings/ tools/ generic/ elements/ objects/ utilities/
```

Con esta organización, la capa de componentes de ITCSS ya no es una carpeta dentro de `scss`, sino el conjunto de carpetas de `components`. Para que el orden de las capas se respete, hay dos detalles importantes. El primero es que `main.scss` **declara el orden de todas las capas** en su primera línea y se importa antes que cualquier componente:

```jsx
// src/main.jsx
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import './scss/main.scss';   // primero: declara el orden de las capas
import App from './App.jsx';

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>,
);
```

El segundo es que el SCSS de cada componente **se envuelve en `@layer components`**, para que quede en su capa aunque se cargue después que las utilidades:

```scss
// src/components/Button/Button.scss
@use "../../scss/tools" as *;

@layer components {
  .button {
    --button-bg: var(--color-primary);
    /* ...el mismo código del apartado 8... */

    &--secondary { /* ... */ }
    &--danger    { /* ... */ }
  }
}
```

La gran diferencia con el HTML a mano es que **las variantes de Figma se convierten en propiedades del componente** (en React se llaman *props*). Quien usa el botón escribe `variant="danger"`, y es el componente el que traduce esa propiedad al modificador de BEM:

```jsx
// src/components/Button/Button.jsx
import './Button.scss';

// variant: 'primary' | 'secondary' | 'danger', como la propiedad de variante en Figma
export function Button({ variant = 'primary', block = false, type = 'button', className = '', children, ...props }) {
  const classes = [
    'button',
    variant !== 'primary' && `button--${variant}`,
    block && 'button--block',
    className,
  ].filter(Boolean).join(' ');

  return (
    <button type={type} className={classes} {...props}>
      {children}
    </button>
  );
}
```

En JSX el atributo `class` se escribe **`className`**, porque `class` es una palabra reservada de JavaScript. El botón tiene `type="button"` por defecto, para que no envíe ningún formulario sin querer, y `{...props}` pasa al `<button>` nativo cualquier otro atributo que reciba (`onClick`, `disabled`, `aria-label`...). Así se usa:

```jsx
<Button variant="danger" onClick={() => setCancelOpen(true)}>Cancelar reserva</Button>
```

La tarjeta de pista recibe los datos de una pista y elige sus variantes a partir de ellos:

```jsx
// src/components/CourtCard/CourtCard.jsx
import { Badge } from '../Badge/Badge.jsx';
import './CourtCard.scss';

export function CourtCard({ name, price, features, free, featured = false }) {
  return (
    <article className={featured ? 'card card--featured' : 'card'}>
      <div className="card__header">
        <h2 className="card__title">{name}</h2>
        <p className="card__price">{price} € / hora</p>
      </div>
      <p className="card__meta">{features.join(' · ')}</p>
      <Badge variant={free ? 'free' : 'full'}>{free ? 'Libre' : 'Completa'}</Badge>
    </article>
  );
}
```

El diálogo sigue usando el `<dialog>` nativo, pero en React no se llama directamente a `showModal()` desde un botón, sino que el componente recibe una propiedad `open` y la sincroniza con el elemento. Para tocar el elemento del DOM se usa una **referencia** (`useRef`), y para reaccionar a los cambios de `open`, un **efecto** (`useEffect`):

```jsx
// src/components/Dialog/Dialog.jsx
import { useEffect, useRef } from 'react';
import './Dialog.scss';

export function Dialog({ open, heading, onClose, children, actions }) {
  const ref = useRef(null);

  useEffect(() => {
    const dialog = ref.current;
    if (open && !dialog.open) dialog.showModal();
    if (!open && dialog.open) dialog.close();
  }, [open]);

  return (
    <dialog ref={ref} className="dialog" aria-labelledby="dialog-title" onClose={onClose}>
      <h2 className="dialog__title" id="dialog-title">{heading}</h2>
      <div className="dialog__body">{children}</div>
      <form className="dialog__actions" method="dialog">{actions}</form>
    </dialog>
  );
}
```

```jsx
// src/App.jsx (fragmento)
const [cancelOpen, setCancelOpen] = useState(false);

<Dialog
  open={cancelOpen}
  heading="¿Cancelar la reserva?"
  onClose={() => setCancelOpen(false)}
  actions={<>
    <Button variant="secondary" type="submit" value="back">Mantener la reserva</Button>
    <Button variant="danger" type="submit" value="confirm">Sí, cancelar</Button>
  </>}
>
  Esta acción no se puede deshacer.
</Dialog>
```

El evento `onClose` avisa al componente padre cuando el diálogo se cierra por cualquier motivo (un botón, la tecla Escape), para que el estado `cancelOpen` vuelva a `false` y los dos estén siempre de acuerdo.

??? info "Para saber más: CSS Modules"

    En muchos proyectos de React verás ficheros llamados `Button.module.scss`. Son **CSS Modules**: al compilar, Vite cambia cada nombre de clase por uno único (`.button` pasa a ser algo como `._button_x7f2a`), de modo que dos componentes nunca pueden chocar aunque usen el mismo nombre. Resuelven el mismo problema que BEM, pero de forma automática. En este módulo seguimos con BEM porque los nombres se ven tal cual en el HTML y en el inspector, y se corresponden con las capas y variantes de Figma. Si en tus prácticas el equipo usa CSS Modules, todo lo demás (tokens, capas, estados) se aplica igual.

## Angular

Angular organiza cada componente en una clase de TypeScript con su plantilla y su hoja de estilos, y al crear un componente con `ng generate component` te genera los ficheros por separado. La estructura es parecida a la de React, con una carpeta por componente:

```text
src/
├── styles.scss            ← todas las capas menos la de componentes
├── scss/
│   └── settings/ tools/ generic/ elements/ objects/ utilities/
└── app/
    ├── app.ts
    ├── app.html
    └── components/
        ├── button/        button.ts, button.scss
        ├── badge/
        ├── court-card/    court-card.ts, court-card.html, court-card.scss
        └── dialog/
```

El fichero `styles.scss` es la hoja de estilos global de Angular, y hace el papel de `main.scss`: declara el orden de las capas y carga todas las capas de ITCSS salvo la de componentes. Para que los componentes puedan cargar las herramientas de Sass con una ruta corta (`@use "tools" as *;`), se añade la carpeta `scss` a las rutas de Sass en el `angular.json`:

```json
"build": {
  "options": {
    "styles": ["src/styles.scss"],
    "stylePreprocessorOptions": {
      "includePaths": ["src/scss"]
    }
  }
}
```

### La encapsulación de estilos

Angular tiene una característica que conviene entender antes de escribir el primer componente. Por defecto, **los estilos de cada componente quedan encapsulados**: al compilar, Angular añade un atributo propio a cada elemento de la plantilla (algo como `_ngcontent-abc-1`) y otro a cada selector del SCSS, de modo que las reglas de un componente solo afectan a su plantilla. Es otra forma de resolver el mismo problema que BEM y `@scope`, y para un componente aislado funciona bien. Para un sistema de diseño tiene dos inconvenientes: los selectores ganan especificidad (el atributo cuenta como una clase más) y las clases de un componente no se pueden aplicar a elementos de otro.

Como tus componentes ya usan nombres de BEM, que no pueden chocar, en este anexo la encapsulación se desactiva con **`ViewEncapsulation.None`**, y los estilos de cada componente se envuelven en `@layer components`, igual que en React. Así el CSS que genera Angular es exactamente el de tu sistema. Las propiedades personalizadas, por cierto, funcionan con cualquier tipo de encapsulación, porque se heredan por el árbol del documento.

### El botón como atributo

En Angular, un componente normalmente es una etiqueta nueva (`<app-button>`), pero para un botón eso tiene un problema: la etiqueta `<app-button>` no es un botón, así que habría que meter un `<button>` dentro y pasarle todos los atributos. Angular permite que el selector de un componente sea **un atributo sobre un elemento nativo**, y es la forma recomendada para botones y enlaces. Así, el componente se aplica sobre el `<button>` de verdad, que conserva todo su comportamiento:

```ts
// src/app/components/button/button.ts
import { Component, ViewEncapsulation, input } from '@angular/core';

@Component({
  // El componente se aplica sobre el <button> o el <a> nativo
  selector: 'button[appButton], a[appButton]',
  template: '<ng-content />',
  styleUrl: './button.scss',
  encapsulation: ViewEncapsulation.None,
  host: {
    class: 'button',
    '[class.button--secondary]': "variant() === 'secondary'",
    '[class.button--danger]': "variant() === 'danger'",
    '[class.button--block]': 'block()',
  },
})
export class Button {
  variant = input<'primary' | 'secondary' | 'danger'>('primary');
  block = input(false);
}
```

```html
<button appButton variant="danger" type="button" (click)="cancelOpen.set(true)">
  Cancelar reserva
</button>
```

La propiedad `host` añade clases al propio elemento: la clase de bloque siempre, y cada modificador cuando se cumple su condición. Las variantes de Figma vuelven a ser propiedades del componente, que en Angular se declaran con **`input()`**.

### La tarjeta y el diálogo

La tarjeta de pista recibe una pista entera como entrada, y su plantilla es el mismo HTML de BEM de siempre, con los datos y los modificadores enlazados:

```html
<!-- src/app/components/court-card/court-card.html -->
<article class="card" [class.card--featured]="court().featured">
  <div class="card__header">
    <h2 class="card__title">{{ court().name }}</h2>
    <p class="card__price">{{ court().price }} € / hora</p>
  </div>
  <p class="card__meta">{{ court().features.join(' · ') }}</p>
  <app-badge [variant]="court().free ? 'free' : 'full'">
    {{ court().free ? 'Libre' : 'Completa' }}
  </app-badge>
</article>
```

El diálogo funciona igual que en React: recibe una entrada `open`, y un **efecto** (`effect()`) abre o cierra el `<dialog>` nativo cada vez que esa entrada cambia. Para llegar al elemento se usa `viewChild()`:

```ts
// src/app/components/dialog/dialog.ts
import { Component, ElementRef, ViewEncapsulation, effect, input, output, viewChild } from '@angular/core';

@Component({
  selector: 'app-dialog',
  templateUrl: './dialog.html',
  styleUrl: './dialog.scss',
  encapsulation: ViewEncapsulation.None,
})
export class Dialog {
  open = input(false);
  heading = input.required<string>();
  closed = output<string>();

  private dialog = viewChild.required<ElementRef<HTMLDialogElement>>('dialog');

  constructor() {
    effect(() => {
      const element = this.dialog().nativeElement;
      if (this.open() && !element.open) element.showModal();
      if (!this.open() && element.open) element.close();
    });
  }
}
```

```html
<!-- src/app/components/dialog/dialog.html -->
<dialog #dialog class="dialog" aria-labelledby="dialog-title" (close)="closed.emit(dialog.returnValue)">
  <h2 class="dialog__title" id="dialog-title">{{ heading() }}</h2>
  <div class="dialog__body"><ng-content /></div>
  <form class="dialog__actions" method="dialog">
    <ng-content select="[actions]" />
  </form>
</dialog>
```

Un detalle que salió al probar este código: la primera versión llamaba `title` a la entrada con el título del diálogo, y como `title` es también un atributo de HTML, el navegador lo mostraba como una etiqueta flotante al pasar el ratón sobre el componente. Por eso se llama `heading`. Es un buen ejemplo de por qué **los nombres de las propiedades de un componente no deben coincidir con atributos de HTML** salvo que quieras ese comportamiento.

## Comparación

| | JavaScript sin framework | React | Angular |
|---|---|---|---|
| Dónde está el HTML | En el `.html`, con `<template>` para lo repetido | En JSX, dentro de cada componente | En la plantilla de cada componente |
| Atributo de clase | `class` | `className` | `class`, y `[class.x]` para los modificadores |
| Cómo se elige una variante | Añadiendo el modificador | Una *prop* (`variant="danger"`) | Un `input()` (`variant="danger"`) |
| Dónde está el SCSS de un componente | `scss/components/` | En la carpeta del componente | En la carpeta del componente |
| Cómo se respeta el orden de ITCSS | `main.scss` carga todo | `main.scss` primero y `@layer components` en cada componente | `styles.scss` primero y `@layer components` en cada componente |
| Abrir el diálogo | `showModal()` desde un evento | `useEffect` sincronizado con `open` | `effect()` sincronizado con `open` |

## Trabajar en equipo

Tu proyecto es individual, pero en una empresa este sistema lo mantiene un equipo, y casi todo lo que has visto en la órbita existe para que varias personas puedan trabajar a la vez sin estorbarse. Con cualquiera de los tres frameworks, los equipos suelen ponerse de acuerdo en unas pocas reglas, y conviene que trabajes como si las tuvieras:

- **Un componente, una carpeta, una persona.** Como cada componente está aislado en su carpeta y sus nombres no chocan, dos personas pueden construir el botón y la tarjeta a la vez, en dos ramas de Git distintas, sin conflictos.
- **Los tokens no se tocan sin acuerdo.** Cambiar un token afecta a toda la aplicación, así que cualquier cambio en `settings` se revisa entre todos y se refleja también en Figma.
- **Las mismas convenciones en todo el código.** BEM, el orden de las capas y los nombres de las variantes se deciden una vez y se documentan en el `README.md`, para que cualquiera que llegue nuevo al proyecto sepa cómo escribir un componente.
- **Revisión antes de unir.** Antes de unir una rama a la principal, otra persona revisa que el componente cumple la lista del apartado 8: los tokens, los estados, el teclado, los dos modos.

En tu proyecto individual puedes practicarlo igual: crea una rama de Git para cada componente, haz commits pequeños con mensajes claros y repasa tú mismo la lista antes de unirla.

## Recursos

- [Vite: primeros pasos](https://vite.dev/guide/)
- [React: describir la interfaz de usuario (react.dev)](https://es.react.dev/learn/describing-the-ui)
- [Angular: estilos de los componentes (angular.dev)](https://angular.dev/guide/components/styling)
- [Angular: selectores de componentes (angular.dev)](https://angular.dev/guide/components/selectors)
- [El elemento `<template>` (MDN Web Docs)](https://developer.mozilla.org/es/docs/Web/HTML/Element/template)
