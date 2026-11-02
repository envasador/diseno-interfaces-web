# 4. Arquitectura ITCSS

Con Sass ya puedes repartir tu hoja de estilos en muchos ficheros pequeños, pero eso te deja con una pregunta que no tiene una respuesta obvia: **qué va en cada fichero y en qué orden se cargan**. Si cada persona del equipo (o tú mismo en semanas distintas) lo decide sobre la marcha, al cabo de un mes nadie sabe dónde está el estilo del botón de reservar, hay tres ficheros que tocan los enlaces y empiezan a aparecer los `!important` para ganar a reglas que no se sabe de dónde vienen. ITCSS es un criterio para tomar esas decisiones siempre igual, y en este módulo es la forma de organizar el código de tu sistema (RA2-e, RA2-j).

ITCSS significa *Inverted Triangle CSS*, CSS en triángulo invertido. Lo propuso Harry Roberts, un consultor británico de CSS, y consiste en una forma de ordenar el código, sin nada que instalar, que puedes aplicar con Sass, con las capas de cascada de CSS o con las dos cosas a la vez, como haremos aquí. Los ejemplos salen de la aplicación del polideportivo, y todo el código de este apartado compila con la versión actual de Sass.

![Las siete capas de ITCSS en forma de triángulo invertido: de arriba abajo, el alcance disminuye y la especificidad aumenta](img/orbita3_04_esquema_itcss.svg)

## Qué problema resuelve

En los apuntes de CSS3 viste que, cuando dos reglas compiten, el navegador decide primero por la especificidad y después por el orden de aparición. En una hoja de estilos pequeña eso se controla de memoria, pero en un proyecto con un reset, estilos para las etiquetas, una docena de componentes y unas cuantas clases de ayuda, las reglas de especificidad alta y baja acaban mezcladas por todo el fichero. El resultado es que una regla escrita al principio con un selector largo gana a otra escrita al final con una sola clase, y para arreglarlo se escribe un selector todavía más largo o un `!important`, y el problema crece.

Harry Roberts lo explicó con una imagen que te ayudará a entender todo el apartado, el **gráfico de especificidad**. Imagina que recorres tu `main.css` de arriba abajo y vas dibujando la especificidad de cada selector. En una hoja de estilos desordenada, la línea sube y baja sin parar, con picos en los sitios donde alguien usó un id o una cadena larga de selectores. En una hoja bien ordenada, **la línea empieza abajo y sube poco a poco**, sin picos, de modo que cada regla puede sobrescribir a las anteriores sin necesidad de trucos. ITCSS es una forma de conseguir esa línea.

## El triángulo invertido

ITCSS ordena el código en capas, y cada capa ocupa una franja de un triángulo puesto boca abajo. Las capas se ordenan según tres criterios que cambian a la vez de arriba abajo:

- **Alcance.** Las capas de arriba afectan a muchísimos elementos (el reset afecta a todos) y las de abajo a muy pocos (una clase de ayuda afecta solo al elemento que la lleva). Por eso el triángulo es ancho arriba y estrecho abajo.
- **Especificidad.** Las capas de arriba usan selectores de poca especificidad (etiquetas o incluso ninguno) y las de abajo, clases. La línea del gráfico de especificidad sube a medida que bajas por el triángulo.
- **Explicitud.** Las capas de arriba son genéricas (cómo es un párrafo en cualquier pantalla) y las de abajo, muy concretas (cómo es el botón de cancelar una reserva).

Cada capa solo puede contener reglas que encajen con su posición en los tres criterios. Si una regla afecta a muchos elementos, no puede ir abajo; si usa una clase, no puede ir arriba. Esa es toda la idea, y lo que queda del apartado es aprender qué va en cada capa.

## Las siete capas

### Settings: los ajustes

La primera capa contiene **los datos del sistema**: los mapas de Sass con los tokens primitivos y semánticos, la escala de espaciado, los radios y los breakpoints. En el ITCSS original, esta capa no genera ningún CSS, porque solo tiene variables de Sass. En este módulo añadimos aquí un fichero que sí genera CSS, el que convierte esos mapas en las propiedades personalizadas de `:root`, porque los tokens son exactamente eso, los ajustes de todo el sistema, y tienen que estar disponibles antes que cualquier otra regla.

```scss
// settings/_breakpoints.scss
$breakpoints: (
  "md": 48rem,
  "lg": 64rem,
);
```

### Tools: las herramientas

La segunda capa contiene **las funciones y los mixins** de Sass: la función `rem()`, el mixin de breakpoint `from()`, el del anillo de foco o el del texto oculto visualmente. Tampoco genera CSS por sí misma, porque un mixin solo produce código cuando otro fichero lo incluye.

Settings y Tools son las dos capas que **cualquier otro fichero puede cargar con `@use`**. Por eso van arriba del todo, y por eso no deben generar CSS (salvo el fichero de las propiedades personalizadas, que solo se carga una vez desde `main.scss`).

### Generic: el reset

La tercera capa es la primera que genera CSS de verdad, y contiene **las reglas que afectan a todo el documento**: el reset, el `box-sizing`, la normalización de los formularios. Sus selectores son los de menor especificidad posible (`*`, `html`, `body`, etiquetas sueltas), y casi nunca cambia de un proyecto a otro.

```scss
// generic/_reset.scss
*, *::before, *::after { box-sizing: border-box; }
body { margin: 0; }
img, picture, video, svg { display: block; max-width: 100%; height: auto; }
input, button, textarea, select { font: inherit; }
```

### Elements: las etiquetas

La cuarta capa da **el estilo base de cada etiqueta de HTML**, sin ninguna clase: el color y la tipografía del `body`, el tamaño de los encabezados, el aspecto de los enlaces y de las tablas. La regla de esta capa es estricta y conviene que la respetes: **aquí solo hay selectores de etiqueta**. Un `h2` tiene en esta capa su estilo por defecto, el que tendrá en cualquier sitio donde nadie diga lo contrario.

```scss
// elements/_headings.scss
h1 { font: var(--font-heading-1); }
h2 { font: var(--font-heading-2); }
h3 { font: var(--font-heading-3); }
h1, h2, h3 { margin-block: 0; text-wrap: balance; }
```

Es la capa en la que se aplica la correspondencia de tu escala tipográfica de la Órbita 2 entre los niveles de título y los encabezados de HTML.

### Objects: los patrones de maquetación

La quinta capa es la primera con clases, y contiene **patrones de colocación sin aspecto propio**: contenedores, pilas de elementos, filas que se reparten el espacio, cuadrículas. Un objeto no tiene colores, ni bordes, ni sombras, ni tipografía, solo decide dónde van las cosas y cuánto espacio hay entre ellas. Si en Figma construiste tus pantallas con Auto layout, los objetos son el equivalente de esos marcos de Auto layout sin relleno de color que usabas para agrupar y separar elementos.

```scss
// objects/_stack.scss: elementos uno debajo de otro, con la misma separación
.o-stack {
  display: flex;
  flex-direction: column;
  gap: var(--stack-gap, var(--space-4));
}

// objects/_cluster.scss: elementos en fila que pasan a la línea siguiente si no caben
.o-cluster {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: var(--cluster-gap, var(--space-2));
}

// objects/_grid.scss: tantas columnas como quepan
.o-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(var(--grid-min, 16rem), 1fr));
  gap: var(--space-4);
}
```

Fíjate en el uso de las propiedades personalizadas con valor de reserva (`var(--stack-gap, var(--space-4))`). El objeto tiene una separación por defecto, pero quien lo usa puede cambiarla sin tocar el objeto. En el polideportivo, `.o-cluster` coloca las píldoras de hora, `.o-grid` el listado de pistas y `.o-stack` el formulario de reserva, y los tres se reutilizan en otras pantallas con otro contenido.

### Components: los componentes

La sexta capa es donde vas a pasar la mayor parte del tiempo. Contiene **las piezas de tu sistema de diseño**, las mismas que tienes como componentes en Figma: el botón, la tarjeta de pista, la píldora de hora, el campo de formulario, el aviso, el diálogo. Cada componente va en su propio parcial, con su nombre, y lleva todo lo que lo define: su aspecto, sus elementos internos, sus variantes y sus estados.

```scss
// components/_badge.scss
.badge {
  --badge-color: var(--color-primary);

  display: inline-flex;
  width: fit-content;
  padding: var(--space-1) var(--space-3);
  border: 2px solid var(--badge-color);
  border-radius: var(--radius-full);
  color: var(--badge-color);
  font: var(--font-label);

  &--free { --badge-color: var(--color-success); }
  &--full { --badge-color: var(--color-error); }
}
```

Un componente **no decide dónde se coloca**, porque eso depende de dónde lo uses. La tarjeta de pista no lleva margen exterior ni ancho fijo: es el objeto que la contiene (la cuadrícula del listado o la pila del resumen) el que la coloca. Así, el mismo componente funciona en cualquier pantalla. Cómo se nombran las partes y las variantes de cada componente lo verás en el apartado siguiente, con BEM, y el conjunto de componentes que necesita casi cualquier aplicación, en el apartado 8.

### Utilities: las utilidades

La última capa contiene **clases de una sola función** que tienen que ganar siempre, como `.u-visually-hidden`, que oculta un texto a la vista pero lo deja disponible para los lectores de pantalla, o una clase que quita el margen de un elemento concreto. Son las reglas de mayor explicitud y menor alcance: solo afectan al elemento que las lleva, y cuando las pones es porque quieres exactamente ese efecto.

```scss
// utilities/_visually-hidden.scss
@use "../tools" as *;

.u-visually-hidden {
  @include visually-hidden;
}
```

En el ITCSS original esta capa se llamaba *Trumps* (triunfos, como en los juegos de cartas) y era el único sitio donde se aceptaba `!important`, para asegurar que una utilidad ganara siempre. Con las capas de cascada de CSS, que verás más abajo, no te hace falta, porque la capa de utilidades ya gana a todas las demás por ir la última. Úsalas con moderación: si una pantalla necesita cinco clases de utilidad para verse bien, lo que le falta probablemente es un componente.

## Dónde va cada cosa

La duda más habitual al empezar con ITCSS es en qué capa colocar una regla concreta. Esta tabla recoge los casos del polideportivo y te sirve como referencia:

| Quiero escribir... | Capa | Por qué |
|---|---|---|
| Los colores de la marca y los breakpoints | Settings | Son datos del sistema |
| La conversión de los tokens en propiedades personalizadas | Settings | Son los ajustes que usa todo lo demás |
| La función que pasa de píxeles a `rem` | Tools | No genera CSS por sí sola |
| `box-sizing: border-box` para todo | Generic | Afecta a todos los elementos |
| La tipografía del `body` y el tamaño de los `h1` | Elements | Es el estilo base de una etiqueta |
| El color de los enlaces dentro del texto | Elements | Es el estilo base de `<a>` |
| El contenedor centrado con ancho máximo | Objects | Coloca, pero no tiene aspecto |
| La fila de píldoras que pasa a la línea siguiente | Objects | Es un patrón de colocación |
| El botón de reservar con sus estados | Components | Es una pieza del sistema |
| La tarjeta de pista y su variante destacada | Components | Es una pieza del sistema |
| Ocultar el texto de un botón que solo muestra un icono | Utilities | Una sola función que tiene que ganar |

Cuando dudes entre dos capas, hazte estas preguntas en orden. ¿Genera CSS? Si no, es Settings o Tools. ¿Usa clases? Si no, es Generic o Elements. ¿Tiene aspecto (color, borde, tipografía) o solo coloca? Si solo coloca, es un objeto. ¿Es una pieza con nombre en tu sistema de Figma? Entonces es un componente.

## La estructura de carpetas

En Sass, cada capa de ITCSS es una carpeta, y cada carpeta tiene un parcial por cada tema. Esta es la estructura del polideportivo, que puedes usar como punto de partida:

```text
scss/
├── main.scss
├── settings/
│   ├── _index.scss
│   ├── _tokens.scss
│   ├── _breakpoints.scss
│   └── _custom-properties.scss
├── tools/
│   ├── _index.scss
│   ├── _functions.scss
│   └── _mixins.scss
├── generic/
│   └── _reset.scss
├── elements/
│   ├── _page.scss
│   ├── _headings.scss
│   └── _links.scss
├── objects/
│   ├── _container.scss
│   ├── _stack.scss
│   ├── _cluster.scss
│   └── _grid.scss
├── components/
│   ├── _index.scss
│   ├── _button.scss
│   ├── _card.scss
│   ├── _field.scss
│   └── ...
└── utilities/
    └── _visually-hidden.scss
```

Los ficheros `_index.scss` de `settings` y `tools` reúnen sus parciales con `@forward`, como viste en los apuntes de Sass, para que cualquier componente pueda cargar todas las herramientas con una sola línea (`@use "../tools" as *;`). El de `components` carga todos los componentes con `@use`, y es el único sitio que tendrás que tocar cada vez que añadas uno nuevo.

## ITCSS y las capas de cascada

El orden de las capas de ITCSS se puede conseguir solo con el orden de los `@use` en `main.scss`, porque Sass escribe el CSS en el mismo orden en que carga los ficheros. Pero si además envuelves cada capa de ITCSS en una **capa de cascada** de CSS (`@layer`), el orden queda garantizado por el propio navegador: aunque un componente use un selector más específico de lo normal, nunca ganará a una utilidad, y un estilo de etiqueta nunca ganará a un componente, por mucha especificidad que tenga.

Como viste en los apuntes de Sass, una regla `@use` no se puede escribir dentro de un `@layer`, así que para cargar cada carpeta dentro de su capa se usa el mixin `meta.load-css()`:

```scss
// main.scss
@use "sass:meta";

@layer settings, generic, elements, objects, components, utilities;

@layer settings  { @include meta.load-css("settings/custom-properties"); }
@layer generic   { @include meta.load-css("generic/reset"); }

@layer elements {
  @include meta.load-css("elements/page");
  @include meta.load-css("elements/headings");
  @include meta.load-css("elements/links");
}

@layer objects {
  @include meta.load-css("objects/container");
  @include meta.load-css("objects/stack");
  @include meta.load-css("objects/cluster");
  @include meta.load-css("objects/grid");
}

@layer components { @include meta.load-css("components/index"); }
@layer utilities  { @include meta.load-css("utilities/visually-hidden"); }
```

Tools no aparece en la lista de capas porque no genera CSS: cada componente la carga por su cuenta con `@use`. La primera línea con `@layer` declara el orden de todas las capas antes de rellenarlas, y es la que manda.

!!! warning "Las capas y `!important` se llevan al revés"

    Con las capas de cascada, una declaración normal de una capa posterior gana a una de una capa anterior. Pero con `!important` ocurre lo contrario: **un `!important` de una capa anterior gana a todo lo que venga después**, incluidas las utilidades. Es un comportamiento pensado para que el reset o una librería puedan proteger ciertos estilos, y es otra buena razón para no usar `!important` en tu proyecto.

## Prefijos en los nombres

Cuando lees `class="o-stack"` en el HTML, el prefijo `o-` te dice de inmediato que esa clase es un objeto, que solo coloca y que puedes reutilizarla en cualquier sitio. Harry Roberts propone usar un prefijo por capa (`o-` para los objetos, `c-` para los componentes, `u-` para las utilidades), de modo que el HTML explique por sí mismo de dónde viene cada clase.

En este módulo vamos a usar **los prefijos `o-` y `u-`**, y a dejar los componentes sin prefijo, porque son la mayoría de las clases que escribirás y así su nombre coincide exactamente con el del componente de Figma (`button`, `card`, `slot`). Si en tu proyecto prefieres poner también `c-` a los componentes, es una decisión válida, siempre que la apliques en todo el código.

## Errores frecuentes

Hay unos cuantos errores que aparecen casi siempre en los primeros proyectos con ITCSS, y que es mejor que conozcas antes de cometerlos:

- **Clases en la capa Elements.** Si escribes `.card h3` en `elements/_headings.scss`, has metido un componente en la capa de las etiquetas. El estilo del título de la tarjeta va en el componente, con su propia clase.
- **Aspecto en los objetos.** Un `.o-stack` con color de fondo deja de ser reutilizable, porque cada vez que lo uses arrastrará ese fondo. Si necesitas una caja con fondo y separación, es un componente.
- **Componentes que se colocan solos.** Un `margin-top` en la tarjeta funciona en el listado, pero estorba en el resumen lateral. La separación entre componentes la pone el objeto que los contiene.
- **Componentes que dependen de otros.** Si `_card.scss` cambia el aspecto de los botones que tiene dentro (`.card .button`), los dos componentes quedan atados. La variante del botón se elige en el HTML con un modificador, como verás en BEM.
- **Ficheros gigantes.** Un `_components.scss` con todos los componentes dentro anula la ventaja de la arquitectura. Un componente, un fichero.

## Cuánto pesa la arquitectura

Una arquitectura ordenada no solo es más fácil de mantener, también genera menos código. Cuando cada componente está en un único fichero y cada patrón de colocación es un objeto reutilizable, no aparecen reglas duplicadas, y las **WSG** del W3C insisten precisamente en que el sistema de diseño sirva para no repetir estilos ni componentes. El CSS completo del polideportivo, con los tokens, el reset, los objetos y todos los componentes del apartado 8, ocupa unos 10 KB comprimido, bastante menos que una sola fotografía.

Esto también explica por qué en este módulo no usamos un framework de CSS completo. Un framework trae cientos de componentes y miles de clases de utilidad pensadas para cualquier proyecto, y si no se configura con cuidado, la mayor parte de ese código llega al navegador sin usarse. Con ITCSS y tus propios tokens, solo escribes lo que tu sistema necesita.

## Antes de seguir

Antes de pasar a BEM, comprueba que tu proyecto cumple estas condiciones:

1. Tu carpeta `scss` tiene **una carpeta por capa** de ITCSS, y `main.scss` las carga en el orden del triángulo.
2. Settings y Tools **no generan CSS**, salvo el fichero de las propiedades personalizadas.
3. En Generic y Elements **no hay ninguna clase**.
4. Los objetos **solo colocan** y llevan el prefijo `o-`.
5. Cada componente está **en su propio fichero** y no tiene márgenes exteriores ni anchos fijos.
6. No hay ningún `!important` fuera de la regla de `prefers-reduced-motion`.

Si en algún momento usas una IA para generar la estructura de carpetas o para repartir tu CSS en capas, anótalo en el `CHANGELOG.md`, y revisa con las preguntas de la tabla anterior que cada regla ha quedado en la capa que le corresponde.

## Recursos

- [ITCSS: Scalable and Maintainable CSS Architecture (Xfive)](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/)
- [The Specificity Graph, de Harry Roberts (CSS Wizardry)](https://csswizardry.com/2014/10/the-specificity-graph/)
- [Capas de cascada, `@layer` (MDN Web Docs)](https://developer.mozilla.org/es/docs/Web/CSS/@layer)
- [`meta.load-css()` (documentación de Sass)](https://sass-lang.com/documentation/modules/meta/#load-css)
