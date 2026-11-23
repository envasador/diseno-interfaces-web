# 5.1 Sass, ITCSS y BEM juntos: dos ejemplos

Ya conoces las tres herramientas por separado. Cada una resuelve un problema distinto, y se entienden mejor viéndolas trabajar a la vez:

| Herramienta | Pregunta que responde | En el ejemplo |
|---|---|---|
| **Sass** | ¿Cómo reparto el código y evito repetirlo? | Parciales, `@use`, mixins y `&` |
| **ITCSS** | ¿En qué carpeta va y en qué orden se carga? | `settings`, `tools` y `components` |
| **BEM** | ¿Cómo se llama cada clase? | `.button`, `.card__title`, `.card--featured` |

## Ejemplo 1: el botón de reservar

Quieres un botón principal que use el color de tu sistema y un anillo de foco que se repetirá en otros componentes. Hay que decidir **dónde va cada cosa**, y las preguntas de ITCSS lo resuelven:

```text
scss/
├── settings/_custom-properties.scss   ← el color (es un dato)
├── tools/_mixins.scss                 ← el anillo de foco (se reutiliza)
└── components/_button.scss            ← el botón (una pieza de Figma)
```

**1. Settings: el dato.**

```scss
// settings/_custom-properties.scss
:root {
  --color-primary: #1A5FB4;
}
```

**2. Tools: lo que se reutiliza.** Un mixin de Sass guarda el anillo de foco para usarlo en cualquier componente:

```scss
// tools/_mixins.scss
@mixin focus-ring {
  outline: 3px solid var(--color-primary);
  outline-offset: 2px;
}
```

**3. Components: la pieza.** Aquí se juntan las tres herramientas: `@use` carga el mixin, la anidación con `&` forma los nombres de BEM, y el fichero está en la carpeta de componentes:

```scss
// components/_button.scss
@use "../tools/mixins" as *;

.button {
  padding: var(--space-3) var(--space-6);
  background-color: var(--color-primary);
  color: var(--color-on-primary);

  &:focus-visible { @include focus-ring; }
  &--secondary    { background-color: transparent; color: var(--color-primary); }
}
```

**4. El HTML** usa los nombres de BEM: la clase base y, si hace falta, el modificador.

```html
<button class="button" type="submit">Reservar</button>
<button class="button button--secondary" type="button">Ver más horas</button>
```

**Y esto es lo que llega al navegador.** Sass ha convertido el bloque en selectores de **una sola clase**, con la misma especificidad:

```css
.button { padding: var(--space-3) var(--space-6); background-color: var(--color-primary); color: var(--color-on-primary); }
.button:focus-visible { outline: 3px solid var(--color-primary); outline-offset: 2px; }
.button--secondary { background-color: transparent; color: var(--color-primary); }
```

## Ejemplo 2: dos tarjetas en una pantalla

Ahora quieres mostrar dos tarjetas de pista, una destacada, una al lado de la otra. Aquí se ve la regla clave: **el componente decide cómo es y el objeto decide dónde va**.

```scss
// objects/_grid.scss          ← coloca, sin aspecto
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr));
  gap: var(--space-4);
}
```

```scss
// components/_card.scss       ← aspecto, sin colocación
.card {
  padding: var(--space-4);
  border: 1px solid var(--color-outline);

  &__title    { margin: 0; font: var(--font-heading-3); }
  &--featured { border: 2px solid var(--color-primary); }
}
```

```html
<ul class="grid" role="list">
  <li><article class="card"><h3 class="card__title">Pista de pádel 2</h3></article></li>
  <li><article class="card card--featured"><h3 class="card__title">Pista de tenis 1</h3></article></li>
</ul>
```

Fíjate en cada decisión:

- **ITCSS:** `.grid` está en `objects` y `.card` en `components`. La tarjeta no lleva márgenes ni anchos, así que funciona en este listado y en cualquier otro sitio.
- **BEM:** `card__title` es una parte de la tarjeta, y `card--featured` es una variante que acompaña a `card`. Ninguna clase depende de dónde está.
- **Sass:** cada pieza está en su parcial, y `&__title` y `&--featured` se escriben dentro del bloque, sin repetir `.card`.

## Cuando dudes

Hazte las tres preguntas, en este orden:

1. **¿Qué es?** Un dato, una herramienta, una etiqueta, una colocación o una pieza: eso te dice **la carpeta** (ITCSS).
2. **¿Cómo se llama?** Bloque, elemento o modificador: eso te dice **el nombre** (BEM).
3. **¿Se repite o tiene partes?** Si se repite, es un mixin; si tiene partes o variantes, se anida con `&` (Sass).
