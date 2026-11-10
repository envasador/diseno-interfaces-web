# 2.1 CSS3 base

!!! info "De dónde salen estos apuntes"

    Son los apuntes de CSS3 del módulo de Lenguajes de Marcas de 1.º, tal cual. Cuando leas «UT2» piensa en HTML5 (tienes el repaso en el [apartado 1](01_html5.md)) y cuando leas «UT4», en JavaScript, que en 2.º verás en DWEC. Si ya los estudiaste, repásalos rápido y pasa a [CSS3 avanzado](02_css3_avanzado.md), donde está todo lo que se usa en tu proyecto y aquí no aparece.

En la UT2 construiste documentos con la etiqueta semántica correcta en cada sitio, y cada vez que algo "se veía feo" la respuesta era la misma: eso lo resuelve CSS. Ha llegado el momento. CSS es el lenguaje con el que decides el aspecto de todo lo que marcaste en HTML: colores, tipografías, espacios, cómo se reparten los bloques en la pantalla y cómo se adapta la página a un móvil, a un monitor enorme o a una persona que tiene activado el modo oscuro en su sistema.

El orden de esta unidad sigue, a grandes rasgos, el de [lenguajecss.com](https://lenguajecss.com/), la referencia de Manz que puedes usar también en los exámenes: primero la sintaxis y cómo conectar CSS con HTML, después cómo se seleccionan los elementos y cómo decide el navegador qué regla gana cuando dos se contradicen, luego los valores (unidades, colores, variables), el modelo de cajas, la tipografía y, por último, la maquetación con Flexbox y Grid, el diseño adaptable y el modo oscuro.

## Qué es CSS y por qué existe

CSS significa *Cascading Style Sheets*, hojas de estilo en cascada. Su idea central es la **separación entre contenido y presentación**: el HTML dice qué es cada cosa (un título, una navegación, un artículo) y el CSS dice cómo se ve. Esa separación tiene consecuencias muy prácticas. Puedes cambiar el aspecto de un sitio entero de cien páginas tocando un único fichero `.css`. Puedes ofrecer distintas presentaciones del mismo contenido según el dispositivo, sin duplicar el HTML. Y el HTML queda limpio, legible y accesible, porque no está lleno de atributos de aspecto como los `bgcolor` o `<font>` que viste retirados en la UT2.

### De CSS a CSS3 (y por qué no hay CSS4)

CSS1 se publicó en 1996 y CSS2 en 1998; ambos eran especificaciones únicas, un documento gordo con todo el lenguaje dentro. A partir de ahí el W3C cambió de estrategia: en lugar de sacar un CSS3 monolítico, dividió el lenguaje en **módulos** independientes (selectores, colores, fondos y bordes, Flexbox, Grid...), cada uno con su propio ritmo y su propio número de nivel. Por eso, cuando se habla de "CSS3", en realidad se habla de todo el CSS moderno, el que vino después de CSS2.1. No va a existir un "CSS4" como tal: el lenguaje evoluciona módulo a módulo, y cada año aparecen funcionalidades nuevas.

Esa evolución constante tiene una consecuencia: antes de usar una funcionalidad reciente conviene comprobar si todos los navegadores la soportan. Para eso tienes [Baseline](https://web.dev/baseline), que marca como "ampliamente disponible" lo que funciona en todos los navegadores principales, y [caniuse.com](https://caniuse.com/). Todo lo que vas a ver en esta unidad está disponible en los navegadores actuales.

## Anatomía de una regla CSS

Igual que en HTML todo gira en torno a la etiqueta, en CSS todo gira en torno a la **regla**:

```css
h1 {
  color: navy;
  font-size: 2rem;
}
```

- **Selector**: `h1`. Indica a qué elementos del documento se aplica la regla.
- **Bloque de declaraciones**: todo lo que va entre llaves `{ }`.
- **Declaración**: `color: navy;`, un par formado por una propiedad y un valor, terminado en punto y coma.
- **Propiedad**: `color`, la característica que quieres cambiar.
- **Valor**: `navy`, cómo quieres que quede.

El punto y coma de la última declaración es técnicamente opcional, pero ponlo siempre: el día que añadas otra declaración debajo y te olvides de ponerlo, la regla dejará de funcionar sin ningún aviso. Y esto es lo primero que tienes que asumir sobre CSS: **el navegador no da errores**. Si escribes una propiedad mal (`colr: red;`) o un valor que no existe, sencillamente ignora esa declaración y sigue con la siguiente. Lo verás funcionar "casi bien" y no sabrás por qué. Por eso el inspector del navegador y el validador, que verás más adelante, son imprescindibles.

Los **comentarios** en CSS se escriben entre `/*` y `*/`, pueden ocupar varias líneas y sirven para documentar la hoja de estilos o desactivar temporalmente un bloque. No existe el comentario de una línea con `//` que verás en JavaScript: en CSS, eso rompe la regla siguiente.

```css
/* =============================
   Cabecera del sitio
   ============================= */
.cabecera {
  background-color: #1d3557;
  /* padding: 2rem;  desactivado mientras pruebo */
}
```

## Cómo conectar CSS con HTML

Hay tres formas de aplicar CSS a un documento, y solo una es la recomendada.

La **hoja de estilos externa** es un fichero `.css` aparte, enlazado desde el `<head>` con un `<link>`. Es la forma correcta en prácticamente todos los casos: el mismo fichero sirve para todas las páginas del sitio, el navegador lo guarda en caché y el HTML no se mezcla con la presentación.

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Festival de Cortometrajes de la Bahía</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
```

La **hoja de estilos interna** es un bloque `<style>` dentro del `<head>`. Afecta solo a ese documento, así que tiene sentido para una página suelta de prueba o un ejemplo rápido, pero no en un proyecto con varias páginas.

Los **estilos en línea** se escriben en el atributo `style` de una etiqueta concreta: `<p style="color: red;">`. Mezclan contenido y presentación en el mismo sitio, no se pueden reutilizar y, como verás en el apartado de especificidad, ganan a casi cualquier regla de tu hoja de estilos, lo que los convierte en un dolor de cabeza. En este módulo no se usan, salvo cuando JavaScript los genere en la UT4.

!!! example "Ejemplo: estructura de carpetas de un proyecto"

    La hoja de estilos vive en su propia carpeta, y la ruta del `href` se calcula exactamente igual que las rutas relativas de la UT2: desde la ubicación del HTML que la enlaza.

    ```text
    festival/
    ├── index.html          → <link rel="stylesheet" href="css/estilos.css">
    ├── programa/
    │   └── viernes.html    → <link rel="stylesheet" href="../css/estilos.css">
    ├── css/
    │   └── estilos.css
    └── img/
        └── cartel.webp
    ```

    Dentro del CSS, las rutas se calculan **desde el fichero CSS**, no desde el HTML. Para usar `img/cartel.webp` como fondo desde `css/estilos.css`, la ruta es `url("../img/cartel.webp")`.

Existe también la regla `@import url("otro.css");`, que carga una hoja de estilos desde dentro de otra. Funciona, pero obliga al navegador a descargar los ficheros uno detrás de otro en lugar de en paralelo, así que si necesitas varias hojas, es preferible usar varios `<link>`.

## El inspector: tu herramienta principal

Antes de seguir, abre cualquier página, haz clic derecho sobre un elemento y elige **Inspeccionar** (o pulsa `F12`). En el panel de **Elementos** ves el árbol DOM que conociste en la UT2, y al seleccionar un nodo, el panel de **Estilos** te muestra todas las reglas CSS que le afectan, de la más prioritaria a la menos. Las declaraciones tachadas son las que han perdido frente a otra regla; las que tienen un icono de aviso tienen un error y el navegador las está ignorando. La pestaña **Calculado** (*Computed*) muestra el valor final de cada propiedad y un diagrama del modelo de cajas del elemento.

Desde ahí puedes editar valores en directo, activar y desactivar declaraciones con su casilla, y forzar estados como `:hover` o `:focus` para comprobar cómo se ven. Nada de eso se guarda en tu fichero, pero es la forma más rápida de probar cambios y, sobre todo, de entender por qué algo no se ve como esperabas. Cuando una regla "no funciona", la respuesta casi siempre está en el panel de Estilos.

## Selectores: decir a qué elementos afecta una regla

El selector es la mitad de cada regla, y elegir bien el selector es la mitad del trabajo con CSS. Lo que hace un selector es buscar nodos dentro del árbol DOM, exactamente la misma idea que usarás en la UT4 con `document.querySelector()`, que recibe como parámetro, precisamente, un selector CSS.

### Selectores básicos

Hay cuatro selectores básicos que vas a usar constantemente:

| Selector | Ejemplo | Selecciona |
|---|---|---|
| De etiqueta | `p` | Todos los `<p>` del documento |
| De clase | `.destacado` | Todos los elementos con `class="destacado"` |
| De id | `#programa` | El elemento con `id="programa"` |
| Universal | `*` | Todos los elementos |

El selector de clase es el que más vas a usar con diferencia. Recuerda de la UT2 que un elemento puede tener varias clases separadas por espacios (`class="tarjeta tarjeta--destacada"`), y que la misma clase puede repetirse en tantos elementos como quieras. El selector de id, en cambio, apunta a un único elemento, y como verás al hablar de especificidad, tiene tanta fuerza que conviene reservarlo para JavaScript y enlaces internos, no para dar estilo.

Los selectores se pueden **combinar sin espacio** para exigir varias condiciones a la vez: `p.destacado` selecciona los `<p>` que además tienen la clase `destacado`, y `.tarjeta.activa` los elementos que tienen las dos clases. Y se pueden **agrupar con comas** cuando varias reglas comparten las mismas declaraciones: `h1, h2, h3 { font-family: Georgia, serif; }`.

### Combinadores: seleccionar por la posición en el árbol

Los combinadores relacionan dos selectores según su posición en el árbol DOM.

- **Descendiente** (un espacio): `nav a` selecciona todos los `<a>` que estén dentro de un `<nav>`, a cualquier profundidad.
- **Hijo directo** (`>`): `ul > li` selecciona solo los `<li>` que son hijos directos de un `<ul>`, no los de una lista anidada dentro.
- **Hermano adyacente** (`+`): `h2 + p` selecciona el `<p>` que va inmediatamente después de un `<h2>`, al mismo nivel.
- **Hermanos generales** (`~`): `h2 ~ p` selecciona todos los `<p>` que vienen después de un `<h2>` al mismo nivel, no solo el primero.

!!! example "Ejemplo: combinadores sobre la misma estructura"

    ```html
    <article class="noticia">
      <h2>Abierto el plazo de inscripción</h2>
      <p>Primer párrafo, la entradilla.</p>
      <p>Segundo párrafo.</p>
      <ul>
        <li>Ficción <ul><li>Cortos de menos de 5 minutos</li></ul></li>
      </ul>
    </article>
    ```

    ```css
    .noticia p { line-height: 1.6; }        /* los dos párrafos */
    .noticia h2 + p { font-weight: bold; }  /* solo la entradilla */
    .noticia > ul > li { color: navy; }     /* solo "Ficción", no el li anidado... */
    ```

    ...aunque fíjate en un detalle: el `<li>` anidado también se verá azul, no porque el selector lo seleccione, sino porque `color` se **hereda** de su padre. Lo verás en el apartado de herencia.

### Selectores de atributo

Puedes seleccionar elementos según sus atributos, algo especialmente útil con formularios y enlaces. `[required]` selecciona los elementos que tienen ese atributo, sea cual sea su valor. `[type="email"]` exige un valor exacto. Y hay variantes para coincidencias parciales: `^=` (empieza por), `$=` (termina en) y `*=` (contiene).

```css
input[type="email"] { border-color: steelblue; }
a[href^="https://"] { text-decoration-style: dotted; }  /* enlaces externos */
a[href$=".pdf"]::after { content: " (PDF)"; }           /* avisa de que es un PDF */
```

### Pseudoclases: seleccionar por estado o por posición

Una **pseudoclase** empieza por dos puntos (`:`) y selecciona elementos según algo que no está escrito en el HTML: su estado o su posición entre sus hermanos. Son muchas, así que conviene verlas por familias.

Las **pseudoclases de interacción** reaccionan a lo que hace la persona usuaria. `:hover` se activa al pasar el ratón por encima, `:active` mientras se está pulsando y `:focus` cuando el elemento tiene el foco del teclado. De esta familia, la más importante para la accesibilidad es **`:focus-visible`**, que se activa solo cuando el foco llega por teclado, no al hacer clic con el ratón. Es la forma correcta de dar estilo al foco sin que aparezca un recuadro cada vez que alguien pulsa un botón con el ratón.

```css
.boton:hover { background-color: #457b9d; }
.boton:focus-visible {
  outline: 3px solid #e63946;
  outline-offset: 2px;
}
```

Las **pseudoclases estructurales** seleccionan según la posición entre hermanos: `:first-child`, `:last-child` y, sobre todo, `:nth-child()`, que acepta un número (`:nth-child(3)`), las palabras `odd` y `even` o una fórmula del tipo `an+b` (`:nth-child(3n)` selecciona el 3.º, 6.º, 9.º...). Son las que usarás para colorear filas alternas de una tabla o quitar el borde del último elemento de un menú.

```css
tbody tr:nth-child(even) { background-color: #f1f5f9; }
.menu li:last-child { border-right: none; }
```

Las **pseudoclases de formulario** aprovechan la validación nativa que viste en la UT2: `:valid` e `:invalid` según si el valor cumple las restricciones del campo, `:required` y `:optional`, `:checked` para casillas y radios marcados y `:disabled` para los campos desactivados.

```css
input:invalid { border-color: #c1121f; }
input:valid { border-color: #2a9d8f; }
```

Por último, **`:not()`** selecciona los elementos que **no** cumplen el selector que le pasas entre paréntesis: `a:not(.boton)` son los enlaces que no son botones, y `.menu li:not(:last-child)` todos los elementos del menú menos el último.

### Pseudoelementos: seleccionar partes de un elemento

Un **pseudoelemento** empieza por dos dobles puntos (`::`) y selecciona una parte de un elemento que no existe como nodo en el HTML. `::first-letter` y `::first-line` seleccionan la primera letra o la primera línea de un bloque de texto. `::placeholder` da estilo al texto de ejemplo de un campo. `::marker` da estilo a la viñeta o al número de un `<li>`. Y `::selection` cambia el color del texto que la persona selecciona con el ratón.

Los más usados son **`::before`** y **`::after`**, que crean un elemento hijo ficticio al principio o al final del contenido del elemento. Solo aparecen si tienen la propiedad `content`, aunque sea vacía (`content: ""`), y se usan para añadir decoración (comillas, iconos, líneas, flechas) sin ensuciar el HTML.

```css
.cita::before { content: "“"; font-size: 3rem; color: #e63946; }
.requerido::after { content: " *"; color: #c1121f; }
```

!!! warning "El contenido de `::before` y `::after` es decoración"

    El texto que generes con `content` no forma parte del HTML: no se puede seleccionar ni copiar de forma fiable, y los lectores de pantalla no siempre lo anuncian. Úsalo para decorar, nunca para información que la persona necesite. Si el asterisco de un campo obligatorio es la única pista de que es obligatorio, el campo tiene que llevar también el atributo `required` en el HTML.

## La cascada, la especificidad y la herencia

En cuanto tu hoja de estilos crezca un poco, vas a encontrarte con varias reglas que intentan cambiar la misma propiedad del mismo elemento. ¿Cuál gana? Responder a esa pregunta es exactamente lo que hace la **cascada**, la C de CSS, y entenderla es lo que distingue a quien "va probando hasta que sale" de quien sabe lo que está haciendo.

### Cómo decide el navegador

Cuando dos declaraciones compiten por la misma propiedad de un elemento, el navegador las compara siguiendo este orden, y en cuanto un criterio deshace el empate, ya no mira los siguientes:

1. **Importancia y origen.** Las declaraciones marcadas con `!important` ganan a las normales. Y tus estilos ganan a los estilos por defecto del navegador (lo que hace que un `<h1>` sea grande y un enlace sea azul y subrayado).
2. **Especificidad.** Gana el selector más específico.
3. **Orden de aparición.** Si todo lo anterior empata, gana la regla que aparece más tarde en el código.

El tercer criterio explica por qué el orden de tus `<link>` importa: si enlazas dos hojas de estilos, la segunda gana los empates a la primera.

### La especificidad

La especificidad es una puntuación que el navegador calcula para cada selector. Se expresa como tres números, (A, B, C), y se compara de izquierda a derecha, como si fueran las cifras de un número: un solo punto en A gana a cualquier cantidad en B.

- **A**: número de selectores de id.
- **B**: número de clases, selectores de atributo y pseudoclases.
- **C**: número de selectores de etiqueta y pseudoelementos.

El selector universal `*` y los combinadores no suman nada.

| Selector | Especificidad |
|---|---|
| `p` | (0, 0, 1) |
| `nav ul li a` | (0, 0, 4) |
| `.destacado` | (0, 1, 0) |
| `.menu a:hover` | (0, 2, 1) |
| `input[type="email"]` | (0, 1, 1) |
| `#programa` | (1, 0, 0) |

Por encima de cualquier selector están los estilos en línea (`style="..."`), y por encima de estos, `!important`.

!!! example "Ejemplo: ¿de qué color es el enlace?"

    ```html
    <nav id="principal">
      <a href="#" class="activo">Programa</a>
    </nav>
    ```

    ```css
    #principal a { color: navy; }   /* (1, 0, 1) */
    nav a.activo { color: crimson; } /* (0, 1, 2) */
    ```

    El enlace es azul marino. Aunque la segunda regla aparece después y parece "más concreta" para una persona, la primera tiene un id, y un id gana a cualquier número de clases y etiquetas. Este es el motivo por el que conviene **no usar ids para dar estilo**: suben tanto la especificidad que, para sobrescribir esa regla más adelante, te verás obligado a usar otro id o un `!important`.

La regla práctica que se deriva de todo esto es mantener la especificidad **baja y uniforme**: da estilo con clases, evita los ids y las cadenas largas de selectores (`body main section article div p`), y deja que el orden del código resuelva los empates. Y sobre `!important`: es una salida de emergencia, no una herramienta habitual. Cada `!important` que escribes para ganar una batalla te obliga a escribir otro para ganar la siguiente.

### La herencia

Algunas propiedades se **heredan**: si se las das a un elemento, todos sus descendientes las reciben automáticamente, salvo que una regla propia las cambie. Por eso basta con poner la tipografía y el color del texto en `body` para que afecten a toda la página. Como regla general, se heredan las propiedades relacionadas con el texto (`color`, `font-family`, `font-size`, `line-height`, `text-align`...) y no se heredan las relacionadas con la caja (`margin`, `padding`, `border`, `background`, `width`...). Tendría poco sentido que todos los hijos de una caja con borde tuvieran también su propio borde.

Si quieres que un elemento tome a la fuerza el valor de su padre en una propiedad que no lo haría por sí sola, o que ha cambiado otra regla, puedes usar el valor **`inherit`**, que funciona en cualquier propiedad.

```css
body {
  font-family: system-ui, sans-serif;
  color: #1f2937;
  line-height: 1.5;
}

/* Los enlaces dentro del pie toman el color del texto que los rodea */
footer a { color: inherit; }
```

### Partir de una base: el reset

Como cada navegador aplica sus propios estilos por defecto, y no todos son idénticos, es habitual empezar la hoja de estilos con un pequeño **reset** que elimina las diferencias más molestas. No hace falta uno exhaustivo; este es suficiente para empezar:

```css
*, *::before, *::after {
  box-sizing: border-box;
}

body {
  margin: 0;
}

img, video {
  display: block;
  max-width: 100%;
  height: auto;
}
```

La primera regla la entenderás en el apartado del modelo de cajas, y la última en el de diseño adaptable.

## Anidación de CSS

Desde 2023, CSS permite **anidar** reglas dentro de otras de forma nativa, algo que antes solo era posible con preprocesadores como Sass. Una regla anidada se aplica a los descendientes del selector que la contiene, lo que evita repetir el mismo prefijo una y otra vez y agrupa visualmente todo lo que afecta a un mismo componente.

El carácter **`&`** representa el selector padre. Es obligatorio cuando quieres pegar algo al selector sin espacio, como una pseudoclase (`&:hover`) o una clase añadida (`&.activa`), y opcional en los demás casos.

!!! example "Ejemplo: el mismo componente, con y sin anidación"

    ```css
    /* Sin anidación */
    .tarjeta { border: 1px solid #d1d5db; }
    .tarjeta:hover { border-color: #457b9d; }
    .tarjeta img { border-radius: 0.5rem; }
    ```

    ```css
    /* Con anidación: mismo resultado */
    .tarjeta {
      border: 1px solid #d1d5db;

      &:hover { border-color: #457b9d; }
      img { border-radius: 0.5rem; }
    }
    ```

La anidación es estándar y la puedes usar en tus proyectos, pero con una precaución: cada nivel de anidación es un selector más largo y más específico. Más de dos niveles es una señal de que estás atando el estilo a la estructura exacta del HTML, y el día que esa estructura cambie, el CSS dejará de funcionar. En la práctica, su mejor uso es agrupar dentro de cada componente sus estados (`&:hover`, `&:focus-visible`) y sus media queries, como verás en el apartado de diseño adaptable.

## Nombrar las clases: la metodología BEM

En una página de prueba, llamar a una clase `.titulo` no da problemas. En un sitio de seis páginas, con tarjetas, fichas, un formulario y un menú, acabarás teniendo tres cosas distintas que quieres llamar `.titulo`, y una regla pensada para una estropeará las otras dos. Para evitarlo, los equipos de desarrollo siguen **convenciones de nombres**, y la más extendida es **BEM**: *Bloque, Elemento, Modificador*.

- Un **bloque** es un componente con sentido propio, que podrías mover a otra página y seguiría funcionando: `.tarjeta`, `.menu`, `.formulario`.
- Un **elemento** es una parte de un bloque que no tiene sentido fuera de él. Se nombra con el bloque, dos guiones bajos y el nombre de la parte: `.tarjeta__imagen`, `.tarjeta__titulo`, `.menu__enlace`.
- Un **modificador** es una variante o un estado de un bloque o de un elemento. Se nombra añadiendo dos guiones y el nombre de la variante: `.tarjeta--destacada`, `.menu__enlace--activo`.

!!! example "Ejemplo: una tarjeta del catálogo con BEM"

    ```html
    <article class="tarjeta tarjeta--destacada">
      <img class="tarjeta__imagen" src="img/marea-baja.webp" alt="..." width="400" height="225">
      <h3 class="tarjeta__titulo">Marea baja</h3>
      <p class="tarjeta__texto">Mejor cortometraje 2025.</p>
      <a class="tarjeta__enlace" href="fichas/marea-baja.html">Ver ficha</a>
    </article>
    ```

    ```css
    .tarjeta {
      border: 1px solid #d1d5db;
      border-radius: 0.75rem;
      padding: 1rem;

      &:hover { border-color: #457b9d; }
    }

    .tarjeta--destacada { border-width: 3px; }
    .tarjeta__imagen { border-radius: 0.5rem; }
    .tarjeta__titulo { font-size: 1.25rem; }
    .tarjeta__enlace { font-weight: bold; }
    ```

Fíjate en tres cosas del ejemplo. El modificador **acompaña** a la clase del bloque en el HTML, no la sustituye (`class="tarjeta tarjeta--destacada"`): la tarjeta destacada es una tarjeta con algo más. Los nombres describen **qué es** cada parte, no cómo se ve, igual que pedías a las etiquetas en la UT2. Y todos los selectores del CSS son una única clase, así que todos tienen la misma especificidad, (0, 1, 0): no hay batallas entre reglas, y el orden del código resuelve los empates, que es justo lo que recomendaba el apartado de especificidad.

Hay dos reglas que conviene respetar desde el principio. La primera, que un elemento lleva siempre el nombre del bloque, aunque en el HTML esté metido dentro de otro elemento: el título que está dentro del cuerpo de la tarjeta es `.tarjeta__titulo`, no `.tarjeta__cuerpo__titulo`. BEM describe a qué componente pertenece cada parte, no cuántos niveles de anidación tiene el HTML. La segunda, que no hace falta poner clase a todo: si un bloque es tan sencillo que un selector como `.menu a` es claro y no choca con nada, no tienes por qué inventar un `.menu__enlace`.

!!! warning "BEM y la anidación nativa"

    Si buscas ejemplos de BEM en internet, verás muchos escritos con Sass, donde `.tarjeta { &__titulo { ... } }` genera la clase `.tarjeta__titulo`. **En CSS nativo eso no funciona**: el navegador no pega texto al selector padre para formar nombres de clase nuevos. Escribe cada elemento y cada modificador como una regla propia, con su nombre completo, y reserva la anidación para los estados (`&:hover`) y las media queries del bloque.

## Unidades y valores

Casi todas las propiedades que tienen que ver con tamaños aceptan un número con una unidad. Elegir la unidad adecuada es lo que hace que un diseño se adapte bien o se rompa en cuanto cambias el tamaño de la ventana o el tamaño de letra del navegador.

### Unidades absolutas y relativas

La única unidad absoluta que vas a usar en pantalla es el **píxel** (`px`). Es predecible y está bien para cosas que no deben escalar, como el grosor de un borde de `1px`. Las unidades de impresión (`cm`, `mm`, `pt`) solo tienen sentido en hojas de estilos para imprimir.

Las unidades relativas se calculan a partir de otra cosa, y son las que hacen que un diseño sea flexible:

| Unidad | Relativa a | Uso típico |
|---|---|---|
| `%` | El tamaño del elemento padre | Anchos de cajas |
| `em` | El tamaño de letra del propio elemento | Espaciados que deben crecer con el texto |
| `rem` | El tamaño de letra del elemento raíz (`<html>`) | Tamaños de letra y espaciados generales |
| `vw`, `vh` | El 1 % del ancho / alto de la ventana | Secciones a pantalla completa |
| `fr` | Una fracción del espacio libre | Solo en Grid, lo verás más adelante |

La diferencia entre `em` y `rem` suele despistar. El tamaño de letra por defecto de los navegadores es de 16 píxeles, así que `1rem` son 16 píxeles en todo el documento, estés donde estés. `1em`, en cambio, depende del tamaño de letra del elemento, y si anidas varios elementos con tamaños en `em`, los tamaños se multiplican entre sí. Por eso **`rem` es la unidad recomendada para los tamaños de letra**: es predecible y, a diferencia de `px`, respeta el tamaño de letra que la persona usuaria haya elegido en su navegador, algo importante para quien necesita la letra más grande para leer.

```css
h1 { font-size: 2.5rem; }          /* 40 px con la configuración por defecto */
.boton { padding: 0.5em 1em; }     /* el relleno crece si el botón tiene letra más grande */
.portada { min-height: 80vh; }     /* ocupa casi toda la altura de la pantalla */
```

### Cálculos con calc()

CSS permite hacer cálculos con valores, incluso mezclando unidades, con la función **`calc()`**: `width: calc(100% - 2rem)` hace que una caja ocupe todo el ancho de su padre menos 2rem. Los espacios alrededor de `+` y `-` son obligatorios; sin ellos, el cálculo no funciona.

!!! example "Ejemplo: un contenedor centrado con márgenes en el móvil"

    ```css
    .contenedor {
      width: calc(100% - 2rem);   /* 1rem libre a cada lado en el móvil */
      max-width: 70rem;           /* en pantallas grandes no pasa de aquí */
      margin: 0 auto;             /* centrado horizontal */
    }
    ```

    Este patrón lo vas a usar en casi todas las páginas: el contenido ocupa la pantalla del móvil sin pegarse a los bordes, y en un monitor grande no se estira hasta hacerse ilegible.

## Colores

CSS acepta los colores en varios formatos, y todos sirven para lo mismo: elige el que te resulte más cómodo, y sé coherente dentro de un mismo proyecto.

- **Palabras clave**: hay unos 140 nombres de color (`red`, `navy`, `tomato`, `rebeccapurple`). Son cómodos para pruebas, pero limitan mucho la paleta.
- **Hexadecimal**: `#e63946`, dos cifras hexadecimales para el rojo, el verde y el azul. Es el formato que te dará cualquier herramienta de diseño. Admite una forma corta (`#f00`) y un cuarto par para la transparencia (`#e6394680`).
- **`rgb()`**: los mismos tres canales en decimal, de 0 a 255: `rgb(230 57 70)`. La transparencia se añade tras una barra: `rgb(230 57 70 / 50%)`.
- **`hsl()`**: tono (un ángulo de 0 a 360 en la rueda de color), saturación y luminosidad: `hsl(355 78% 56%)`. Es mucho más intuitivo para crear variaciones de un color: para una versión más oscura, basta con bajar la luminosidad.

Verás también sintaxis antiguas con comas (`rgba(230, 57, 70, 0.5)`): siguen funcionando, pero la forma moderna separa los valores con espacios y usa `/` para la transparencia.

Hay dos valores especiales que conviene conocer. **`transparent`** es un color totalmente transparente. **`currentColor`** toma el valor de la propiedad `color` del propio elemento, lo que permite que un borde o un icono SVG cambie de color automáticamente con el texto.

```css
.aviso {
  color: hsl(30 90% 35%);
  background-color: hsl(30 90% 95%);
  border-left: 4px solid currentColor;  /* el borde usa el mismo color que el texto */
}
```

!!! tip "El contraste no es opcional"

    El color del texto y el del fondo tienen que contrastar lo suficiente para que el texto se lea bien, también para personas con baja visión o con la pantalla al sol. Las pautas de accesibilidad WCAG piden un contraste mínimo de **4.5:1** para el texto normal y de **3:1** para el texto grande. El inspector de Chrome y Firefox te muestra el contraste al seleccionar un color, y [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) lo calcula para cualquier pareja de colores.

## Variables CSS (propiedades personalizadas)

Una hoja de estilos real repite los mismos valores una y otra vez: el color principal de la marca aparece en botones, enlaces, bordes y títulos. Las **propiedades personalizadas**, que todo el mundo llama variables CSS, te permiten definir ese valor una sola vez y reutilizarlo en todas partes. Su nombre empieza siempre por dos guiones, y se leen con la función `var()`.

```css
:root {
  --color-primario: #1d3557;
  --color-acento: #e63946;
  --color-fondo: #fdfdfd;
  --radio: 0.5rem;
  --espacio: 1rem;
}

.boton {
  background-color: var(--color-acento);
  border-radius: var(--radio);
  padding: calc(var(--espacio) / 2) var(--espacio);
}
```

`:root` es una pseudoclase que selecciona el elemento raíz del documento, el `<html>`, y es el sitio habitual para declarar las variables globales. Como las variables se heredan, las declaradas ahí están disponibles en todo el documento. Pero también puedes redefinir una variable dentro de un selector concreto, y entonces cambia solo para ese elemento y sus descendientes. Esa es la clave del modo oscuro que verás al final de la unidad: no cambias cien reglas, cambias el valor de unas pocas variables.

`var()` admite un segundo parámetro como valor de reserva, por si la variable no existe: `var(--color-acento, crimson)`.

!!! example "Ejemplo: variantes de un componente cambiando una variable"

    ```css
    .etiqueta {
      --color: #457b9d;
      color: var(--color);
      border: 2px solid var(--color);
      padding: 0.25rem 0.75rem;
    }

    .etiqueta--ficcion { --color: #6a4c93; }
    .etiqueta--documental { --color: #2a9d8f; }
    ```

    Las variantes solo cambian el valor de la variable; las declaraciones del componente se escriben una única vez.

## El modelo de cajas

Este es el concepto más importante de toda la unidad. Para CSS, **cada elemento de la página es una caja rectangular**, también los que no lo parecen, como un enlace dentro de un párrafo o un círculo con bordes redondeados. Cada caja tiene cuatro capas, de dentro hacia fuera:

1. **Contenido** (*content*): el texto, la imagen o los elementos hijos. Su tamaño lo controlan `width` y `height`.
2. **Relleno** (`padding`): el espacio entre el contenido y el borde. Tiene el mismo fondo que la caja.
3. **Borde** (`border`): la línea que rodea el relleno.
4. **Margen** (`margin`): el espacio exterior, entre el borde y las cajas vecinas. Siempre es transparente.

```text
┌───────────────────── margin ─────────────────────┐
│  ┌────────────────── border ──────────────────┐  │
│  │  ┌─────────────── padding ──────────────┐  │  │
│  │  │                                      │  │  │
│  │  │        contenido (width × height)    │  │  │
│  │  │                                      │  │  │
│  │  └──────────────────────────────────────┘  │  │
│  └────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────┘
```

Abre el inspector, selecciona cualquier elemento y mira la pestaña **Calculado**: verás exactamente este diagrama con los valores reales de esa caja.

### Valores abreviados y lados

`padding`, `margin` y `border-width` aceptan de uno a cuatro valores, y el orden es siempre el de las agujas del reloj empezando por arriba:

```css
padding: 1rem;                 /* los cuatro lados */
padding: 1rem 2rem;            /* arriba y abajo | izquierda y derecha */
padding: 1rem 2rem 0.5rem;     /* arriba | izquierda y derecha | abajo */
padding: 1rem 2rem 0.5rem 0;   /* arriba | derecha | abajo | izquierda */
```

También puedes afectar a un solo lado con las propiedades individuales: `padding-top`, `margin-left`, `border-bottom`...

Un uso muy habitual de los márgenes es **centrar horizontalmente** una caja que tiene un ancho definido: con `margin: 0 auto`, el navegador reparte a partes iguales el espacio sobrante a izquierda y derecha.

### box-sizing: cómo se mide una caja

Aquí está la trampa clásica del modelo de cajas. Por defecto, `width` y `height` miden **solo el contenido**, así que el relleno y el borde se suman por fuera. Una caja con `width: 300px`, `padding: 20px` y un borde de `5px` mide en realidad 350 píxeles de ancho. Si pones dos cajas al 50 % y les añades relleno, ya no caben en la misma línea.

La propiedad **`box-sizing: border-box`** cambia ese cálculo para que `width` y `height` incluyan el relleno y el borde. La misma caja de antes mide exactamente 300 píxeles, y es el relleno el que se come espacio por dentro. Es tan útil que prácticamente todos los proyectos la aplican a todos los elementos desde el principio, que es justo lo que hacía la primera regla del reset que viste antes.

!!! example "Ejemplo: la misma caja con los dos modelos"

    ```css
    .caja {
      width: 300px;
      padding: 20px;
      border: 5px solid #1d3557;
    }

    .caja--content { box-sizing: content-box; } /* mide 350 px: 300 + 20×2 + 5×2 */
    .caja--border  { box-sizing: border-box; }  /* mide 300 px: el contenido se queda en 250 */
    ```

### Dimensiones y desbordamiento

`width` y `height` fijan las dimensiones, pero en la mayoría de los casos es mejor **no fijar la altura** y dejar que la caja crezca con su contenido: un texto que hoy cabe en 200 píxeles mañana puede ser más largo, o puede verse con la letra más grande. Para poner límites sin fijar el tamaño están **`min-width`**, **`max-width`**, **`min-height`** y **`max-height`**. `max-width` es especialmente útil: una caja con `max-width: 40rem` ocupa todo el ancho en un móvil, pero no se estira más allá en un monitor grande.

Cuando el contenido no cabe en la caja, **`overflow`** decide qué pasa: `visible` (por defecto) lo deja sobresalir, `hidden` lo recorta, `scroll` añade siempre barras de desplazamiento y `auto` las añade solo si hacen falta. Para que una tabla ancha no rompa el diseño en un móvil, lo habitual es envolverla en un contenedor con `overflow-x: auto`.

### Márgenes que colapsan

Hay un comportamiento de los márgenes que sorprende a todo el mundo la primera vez. Cuando dos cajas de bloque están una encima de otra, sus márgenes verticales **no se suman**: se fusionan, y el espacio resultante es el mayor de los dos. Si un párrafo tiene `margin-bottom: 20px` y el siguiente `margin-top: 30px`, entre ellos hay 30 píxeles, no 50. Esto se llama **colapso de márgenes**, y solo ocurre con márgenes verticales y en el flujo normal: dentro de un contenedor Flexbox o Grid no se produce. Si un espacio entre bloques no mide lo que esperas, comprueba esto primero.

### Bordes, esquinas y sombras

`border` es una propiedad abreviada que recibe el grosor, el estilo y el color: `border: 2px solid #1d3557`. El estilo es obligatorio (sin él, no se ve ningún borde) y puede ser `solid`, `dashed`, `dotted`, `double`, entre otros.

**`border-radius`** redondea las esquinas, y con `50%` sobre una caja cuadrada obtienes un círculo. **`box-shadow`** añade una sombra con un desplazamiento horizontal, uno vertical, un desenfoque y un color. Y **`outline`** dibuja una línea alrededor del borde que no ocupa espacio ni empuja a las cajas vecinas, que es justo por eso lo que usan los navegadores para marcar el foco del teclado.

```css
.tarjeta {
  border: 1px solid #e5e7eb;
  border-radius: 0.75rem;
  box-shadow: 0 4px 12px rgb(0 0 0 / 10%);
}
```

## Fondos

`background-color` pinta el fondo de la caja (contenido y relleno, por debajo del borde). Además del color, una caja puede llevar una imagen de fondo con **`background-image`**, y unas cuantas propiedades controlan cómo se coloca:

- **`background-size`**: `cover` hace que la imagen cubra toda la caja, recortando si hace falta; `contain` la muestra entera, aunque sobre espacio.
- **`background-position`**: dónde se ancla la imagen (`center`, `top right`, `50% 20%`).
- **`background-repeat`**: si la imagen se repite en mosaico (`repeat`, por defecto) o no (`no-repeat`).

Una imagen de fondo es **decoración**: no tiene `alt`, así que un lector de pantalla no sabe que existe. Si la imagen aporta información, tiene que ser un `<img>` en el HTML, no un fondo.

### Degradados

Los degradados en CSS no son imágenes que descargues, sino imágenes que genera el propio navegador, y se usan en `background-image`. **`linear-gradient()`** pasa de un color a otro en línea recta, con una dirección opcional; **`radial-gradient()`** lo hace en círculo desde un punto.

!!! example "Ejemplo: cabecera con imagen y degradado superpuestos"

    ```css
    .portada {
      min-height: 60vh;
      color: white;
      /* Se pueden apilar varios fondos separados por comas: el primero queda encima */
      background-image:
        linear-gradient(to bottom, rgb(0 0 0 / 20%), rgb(0 0 0 / 70%)),
        url("../img/bahia.webp");
      background-size: cover;
      background-position: center;
    }
    ```

    El degradado oscuro encima de la foto no es solo estética: garantiza que el texto blanco tenga contraste suficiente sea cual sea la zona de la imagen sobre la que cae.

## Tipografía y texto

La mayor parte de una página web es texto, y cuidarlo es lo que más mejora la experiencia de lectura con menos esfuerzo.

### Familias tipográficas

**`font-family`** recibe una lista de fuentes separadas por comas, llamada **pila tipográfica**. El navegador usa la primera que tenga disponible, y la última de la lista debe ser siempre una **familia genérica** (`serif`, `sans-serif`, `monospace`, `system-ui`) como último recurso. Los nombres con espacios van entre comillas.

```css
body { font-family: "Atkinson Hyperlegible", system-ui, sans-serif; }
code { font-family: Consolas, "Courier New", monospace; }
```

`system-ui` usa la fuente del sistema operativo de quien visita la página: San Francisco en un Mac, Segoe UI en Windows, Roboto en Android. Se ve bien, se lee bien y no hay que descargar nada.

### Fuentes de Google Fonts

Si quieres usar una fuente que no esté instalada en el equipo, la forma más sencilla es [Google Fonts](https://fonts.google.com/): eliges la fuente y los grosores, y te da los `<link>` listos para pegar en el `<head>`, incluidos los `preconnect` que viste en la UT2. Después, solo tienes que usar su nombre en `font-family`.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Atkinson+Hyperlegible:wght@400;700&display=swap" rel="stylesheet">
```

Cada fuente y cada grosor es un fichero más que descargar, así que limítate a lo que de verdad uses: dos familias y tres o cuatro grosores son más que suficientes para casi cualquier sitio.

### Propiedades de la fuente y del texto

| Propiedad | Para qué sirve | Ejemplo |
|---|---|---|
| `font-size` | Tamaño de la letra | `1.125rem` |
| `font-weight` | Grosor, de 100 a 900 | `700` (o `bold`) |
| `font-style` | Cursiva | `italic` |
| `line-height` | Altura de cada línea | `1.5` (sin unidad) |
| `text-align` | Alineación horizontal | `left`, `center`, `justify` |
| `text-decoration` | Subrayado y tachado | `underline`, `none` |
| `text-transform` | Mayúsculas y minúsculas | `uppercase` |
| `letter-spacing` | Espacio entre letras | `0.05em` |

Un detalle que marca la diferencia: `line-height` se escribe **sin unidad** (`1.5`, no `1.5rem` ni `24px`). Así se calcula a partir del tamaño de letra de cada elemento y se hereda bien. Para texto corrido, entre `1.4` y `1.7` es cómodo.

!!! warning "Ten cuidado con `text-align: justify` y `text-transform: uppercase`"

    El texto justificado en pantalla crea espacios irregulares entre palabras ("ríos" de blanco) que dificultan la lectura, sobre todo en columnas estrechas como las de un móvil; alinear a la izquierda es casi siempre mejor. Y si quieres un título en mayúsculas, escríbelo normal en el HTML y ponlo en mayúsculas con `text-transform`: algunos lectores de pantalla deletrean letra a letra las palabras escritas en mayúsculas, como si fueran siglas.

### Listas y enlaces

Las listas tienen sus propias propiedades. **`list-style-type`** cambia la viñeta o la numeración (`disc`, `square`, `decimal`, `upper-roman`, `none`), y el pseudoelemento `::marker` permite dar color o tamaño a la viñeta sin tocar el texto. Lo más habitual, en un menú de navegación, es quitar viñetas, márgenes y rellenos de la lista para construir el menú desde cero:

```css
.menu {
  list-style: none;
  margin: 0;
  padding: 0;
}
```

Los enlaces tienen cuatro estados que puedes estilizar por separado: `:link` (sin visitar), `:visited`, `:hover` y `:active`, además de `:focus-visible`. Si los defines todos, hazlo en ese orden; si no, por la regla de orden de aparición, unos pueden tapar a otros. Y si quitas el subrayado de los enlaces que están dentro de un texto, asegúrate de que se distinguen del resto por algo más que el color, porque una persona con daltonismo puede no apreciar la diferencia.

## Display: cómo se comporta cada caja

En la UT2 viste que hay elementos de bloque y elementos en línea, y que eso era un comportamiento visual que CSS podía cambiar. La propiedad que lo controla es **`display`**.

- **`block`**: la caja ocupa todo el ancho disponible y empieza en una línea nueva. Respeta `width`, `height` y todos los márgenes.
- **`inline`**: la caja se coloca dentro de la línea de texto, ocupando solo lo que mide su contenido. **Ignora `width` y `height`**, y sus márgenes verticales no empujan a las líneas de arriba y abajo.
- **`inline-block`**: se coloca en línea como `inline`, pero respeta `width`, `height` y márgenes como `block`. Útil, por ejemplo, para un enlace con aspecto de botón dentro de un texto.
- **`none`**: el elemento desaparece por completo, como si no estuviera en el HTML, y no ocupa espacio.
- **`flex`** y **`grid`**: convierten la caja en un contenedor con un sistema de maquetación propio. Son tan importantes que tienen sus propios apartados.

Cambiar `display` cambia el aspecto, **no el significado**. Un `<a>` con `display: block` sigue siendo un enlace, y un `<li>` con `display: inline` sigue siendo un elemento de lista. Por eso un menú horizontal sigue siendo una `<ul>`.

Hay una diferencia importante entre ocultar con `display: none` y con `visibility: hidden`: el segundo hace el elemento invisible, pero **sigue ocupando su hueco**. En ambos casos, el contenido deja de estar disponible para los lectores de pantalla.

## Posicionamiento

Por defecto, las cajas se colocan una detrás de otra siguiendo el **flujo normal** del documento: los bloques uno debajo de otro, los elementos en línea uno al lado de otro. La propiedad **`position`** permite sacar una caja de ese flujo o desplazarla, y se combina con las propiedades `top`, `right`, `bottom` y `left`, que indican la distancia.

- **`static`**: el valor por defecto. La caja sigue el flujo normal e ignora `top`, `left` y compañía.
- **`relative`**: la caja se desplaza respecto a su posición normal, pero su hueco original se mantiene. Su uso más habitual es otro: servir de **referencia** para los hijos con `position: absolute`.
- **`absolute`**: la caja sale del flujo (las demás se comportan como si no existiera) y se coloca respecto a su **ancestro posicionado** más cercano, es decir, el primer antepasado que tenga un `position` distinto de `static`. Si no hay ninguno, se coloca respecto a la página entera.
- **`fixed`**: sale del flujo y se coloca respecto a la ventana del navegador, así que no se mueve al hacer scroll. Es el de un botón de "volver arriba" o un aviso de cookies.
- **`sticky`**: se comporta como `relative` hasta que, al hacer scroll, llega a la distancia que le indiques; a partir de ahí se queda pegado como si fuera `fixed`, pero solo dentro de su contenedor. Es la forma más sencilla de tener una cabecera que se queda arriba.

!!! example "Ejemplo: una etiqueta sobre la esquina de una tarjeta"

    ```css
    .tarjeta {
      position: relative;   /* se convierte en la referencia */
    }

    .tarjeta__estreno {
      position: absolute;
      top: 0.75rem;
      right: 0.75rem;       /* esquina superior derecha de la tarjeta, no de la página */
    }

    .cabecera {
      position: sticky;
      top: 0;               /* se pega arriba al hacer scroll */
      z-index: 10;
    }
    ```

Cuando dos cajas posicionadas se solapan, **`z-index`** decide cuál queda encima: un número mayor queda delante. Solo funciona en elementos posicionados (y en los hijos de Flexbox y Grid). No te pongas a escribir `z-index: 9999`: con valores pequeños y ordenados (1, 10, 100) es mucho más fácil saber qué hay encima de qué.

`position` no es una herramienta para maquetar la página entera. Colocar todos los bloques con `absolute` y coordenadas produce diseños que se rompen en cuanto cambia el tamaño de la ventana o el largo del texto. Para repartir bloques en filas y columnas están Flexbox y Grid. Verás también, en tutoriales antiguos, que se usaba `float` para colocar columnas: hoy `float` queda reservado para su uso original, que el texto rodee una imagen.

## Flexbox: maquetación en una dimensión

**Flexbox** es un sistema de maquetación pensado para repartir elementos **en una sola dirección**, en fila o en columna, y controlar cómo se alinean y cómo se reparten el espacio sobrante. Es la herramienta ideal para un menú horizontal, una barra de botones, una cabecera con el logo a un lado y la navegación al otro, o centrar algo vertical y horizontalmente, algo que durante años fue sorprendentemente difícil en CSS.

Flexbox siempre implica dos niveles: el **contenedor flexible**, al que le das `display: flex`, y sus **hijos directos**, que se convierten automáticamente en **ítems flexibles**. Los nietos no se ven afectados.

### Los dos ejes

Todo Flexbox gira en torno a dos ejes. El **eje principal** es la dirección en la que se colocan los ítems, y lo decide **`flex-direction`**: `row` (en fila, por defecto) o `column` (en columna). El **eje secundario** es el perpendicular. Lo importante es que las propiedades de alineación no hablan de "horizontal" y "vertical", sino de estos ejes, así que si cambias `flex-direction`, también cambia el efecto de cada propiedad.

| Propiedad del contenedor | Qué hace |
|---|---|
| `flex-direction` | Dirección del eje principal: `row`, `column`, `row-reverse`, `column-reverse` |
| `justify-content` | Reparto en el **eje principal**: `flex-start`, `center`, `flex-end`, `space-between`, `space-around`, `space-evenly` |
| `align-items` | Alineación en el **eje secundario**: `stretch` (por defecto), `flex-start`, `center`, `flex-end`, `baseline` |
| `flex-wrap` | Si los ítems pasan a una línea nueva cuando no caben (`wrap`) o se aprietan en una sola (`nowrap`, por defecto) |
| `gap` | Espacio entre ítems, sin márgenes ni trucos |

!!! example "Ejemplo: cabecera con logo y menú"

    ```html
    <header class="cabecera">
      <a href="/" class="cabecera__logo">Festival de la Bahía</a>
      <nav>
        <ul class="menu">
          <li><a class="menu__enlace" href="#programa">Programa</a></li>
          <li><a class="menu__enlace" href="#sedes">Sedes</a></li>
          <li><a class="menu__enlace" href="#inscripcion">Inscripción</a></li>
        </ul>
      </nav>
    </header>
    ```

    ```css
    .cabecera {
      display: flex;
      justify-content: space-between;  /* logo a la izquierda, nav a la derecha */
      align-items: center;             /* centrados verticalmente entre sí */
      padding: 1rem;
    }

    .menu {
      display: flex;                   /* la lista también es un contenedor flexible */
      gap: 1.5rem;
      list-style: none;
      margin: 0;
      padding: 0;
    }
    ```

    Fíjate en que hay dos contenedores flexibles: la cabecera, cuyos ítems son el logo y el `<nav>`, y la lista, cuyos ítems son los `<li>`. Flexbox no atraviesa niveles.

### Cómo crecen y encogen los ítems

Las propiedades de los ítems controlan cómo se reparten el espacio. **`flex-grow`** indica cuánto crece un ítem para ocupar el espacio sobrante (0 por defecto: no crece). **`flex-shrink`** indica cuánto se encoge si falta espacio (1 por defecto: sí se encoge). **`flex-basis`** es su tamaño de partida antes de repartir. Las tres se resumen en la propiedad **`flex`**, y el valor que más vas a usar es `flex: 1`, que significa "crece para repartir el espacio a partes iguales con los demás ítems que también tengan `flex: 1`".

`align-self` permite que un ítem concreto se alinee distinto al resto en el eje secundario, y `order` cambia el orden visual de un ítem.

!!! warning "`order` cambia lo que se ve, no lo que se lee"

    `order` y `flex-direction: row-reverse` alteran el orden en pantalla, pero no el orden del HTML. Una persona que navega con el tabulador o con un lector de pantalla sigue el orden del HTML, así que el foco saltará de forma aparentemente aleatoria. Si el orden importa, cámbialo en el HTML.

!!! tip "Centrar cualquier cosa"

    El patrón más famoso de Flexbox centra un elemento en los dos ejes dentro de su contenedor:

    ```css
    .centrado {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }
    ```

## Grid: maquetación en dos dimensiones

Si Flexbox reparte elementos en una dirección, **Grid** reparte elementos **en filas y columnas a la vez**, como una cuadrícula. Es la herramienta para cualquier colección de elementos que deba alinearse en columnas, como una galería de tarjetas o un catálogo, y para organizar las zonas de una página.

La diferencia de enfoque es la clave para elegir entre los dos: con Flexbox, el **contenido** decide el tamaño y los ítems se reparten como pueden; con Grid, defines primero la **estructura** (cuántas columnas, de qué tamaño) y luego colocas el contenido en ella. No compiten: lo normal es usar Grid para la estructura general y Flexbox dentro de cada bloque.

### Definir la cuadrícula

Al contenedor le das `display: grid` y defines las columnas con **`grid-template-columns`**. Cada valor es el ancho de una columna. Aquí entra en juego la unidad **`fr`**, una fracción del espacio libre: `1fr 2fr` crea dos columnas en las que la segunda es el doble de ancha que la primera. `gap` funciona igual que en Flexbox.

```css
.galeria {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;   /* tres columnas iguales */
  gap: 1.5rem;
}
```

Para no repetir, **`repeat()`** genera varias columnas iguales: `repeat(3, 1fr)` es lo mismo que `1fr 1fr 1fr`. Y combinado con `minmax()` y la palabra clave `auto-fit`, produce uno de los patrones más útiles de todo CSS: una cuadrícula que decide sola cuántas columnas caben.

!!! example "Ejemplo: galería adaptable sin una sola media query"

    ```css
    .galeria {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr));
      gap: 1.5rem;
    }
    ```

    Se lee así: "crea tantas columnas como quepan, cada una de al menos 16rem, y reparte el espacio sobrante entre ellas". En un móvil cabe una columna; en una tableta, dos; en un monitor, cuatro o cinco. El navegador hace el cálculo cada vez que cambia el ancho.

### Elementos que ocupan varias celdas

Por defecto, cada hijo ocupa la siguiente celda libre. Para que un elemento ocupe varias, se usa **`grid-column`** o **`grid-row`** en el propio hijo, con la palabra `span` y el número de celdas: `grid-column: span 2` hace que ocupe dos columnas. Es la forma de destacar una tarjeta en un catálogo o de hacer que un título ocupe toda la fila.

```css
.tarjeta--destacada {
  grid-column: span 2;   /* ocupa el ancho de dos tarjetas */
}
```

## Diseño adaptable (responsive)

Tu página se va a ver en pantallas de 360 píxeles de ancho y de 2560, en vertical y en horizontal, con el ratón y con el dedo. El **diseño adaptable** (*responsive web design*) es el conjunto de técnicas para que la misma página funcione bien en todas ellas, y en este módulo es un requisito, no un extra.

Ya conoces dos piezas. La primera es la etiqueta `<meta name="viewport">` de la UT2: sin ella, el móvil finge ser una pantalla de escritorio y lo encoge todo, y nada de lo que sigue funciona. La segunda son las unidades relativas, `max-width` y las cuadrículas con `auto-fit`, que ya adaptan mucho sin ninguna regla especial. Antes de escribir una media query, pregúntate si un diseño fluido no lo resuelve ya.

### Imágenes fluidas

Una imagen con su ancho original se sale de la pantalla en un móvil. La regla `max-width: 100%` del reset hace que nunca sea más ancha que su contenedor, y `height: auto` hace que la altura se ajuste en proporción, de modo que la imagen nunca se deforma.

### Media queries

Una **media query** aplica un bloque de reglas solo cuando se cumple una condición sobre el dispositivo, normalmente el ancho de la ventana. La sintaxis moderna usa comparaciones de rango, mucho más legibles que la antigua:

```css
/* Sintaxis moderna */
@media (width >= 48rem) { ... }

/* Sintaxis clásica, equivalente, que verás en muchos tutoriales */
@media (min-width: 48rem) { ... }
```

El ancho a partir del cual cambia el diseño se llama **punto de ruptura** (*breakpoint*). No hay valores mágicos que copiar: el punto de ruptura correcto es aquel en el que tu diseño empieza a verse mal. Abre el inspector, activa el modo de dispositivo y estrecha la ventana poco a poco; donde algo se rompa, ahí va tu media query.

### Mobile first

Hay dos formas de organizar las media queries. Puedes escribir primero el diseño de escritorio y luego ir deshaciéndolo para pantallas pequeñas (con `max-width`), o escribir primero el diseño para móvil y luego ir añadiendo complejidad para pantallas más grandes (con `min-width`). La segunda se llama **mobile first** y es la recomendada: el diseño de móvil suele ser el más sencillo (todo en una columna, uno debajo de otro, que es casi el flujo normal), y es más fácil añadir columnas que quitarlas.

!!! example "Ejemplo: mobile first con anidación"

    ```css
    .programa {
      display: grid;
      gap: 1rem;                        /* móvil: una columna */

      @media (width >= 40rem) {
        grid-template-columns: repeat(2, 1fr);
      }

      @media (width >= 64rem) {
        grid-template-columns: repeat(3, 1fr);
        gap: 2rem;
      }
    }
    ```

    Las media queries se pueden anidar dentro de la regla a la que afectan, de modo que todo lo que tiene que ver con `.programa` queda en un mismo sitio. Si lo prefieres, también puedes escribirlas fuera, al final de la hoja de estilos, con el selector completo dentro.

Las media queries no solo preguntan por el ancho. `(orientation: landscape)` comprueba si la pantalla está en horizontal y `@media print` aplica reglas solo al imprimir. Y hay otra muy importante, `prefers-color-scheme`, que pregunta por una preferencia de la persona usuaria y es la base del apartado siguiente.

## Modo oscuro

Cada vez más personas usan el modo oscuro de su sistema operativo, y una página completamente blanca a medianoche es lo más parecido a una linterna en la cara. Una página bien hecha respeta esa preferencia, y gracias a las variables CSS, cuesta muy poco.

La pieza clave es la media query **`prefers-color-scheme`**, que vale `dark` o `light` según la preferencia del sistema. Si todos tus colores están en variables, basta con redefinir las variables:

```css
:root {
  color-scheme: light dark;
  --color-texto: #1f2937;
  --color-fondo: #fdfdfd;
  --color-superficie: #f1f5f9;
  --color-acento: #c1121f;
}

@media (prefers-color-scheme: dark) {
  :root {
    --color-texto: #e5e7eb;
    --color-fondo: #111827;
    --color-superficie: #1f2937;
    --color-acento: #ff6b6b;
  }
}

body {
  color: var(--color-texto);
  background-color: var(--color-fondo);
}
```

Fíjate en dos detalles. El color de acento también cambia, no solo el fondo y el texto: un rojo oscuro que contrasta bien sobre blanco puede ser ilegible sobre un fondo casi negro, así que cada color tiene que comprobarse con los dos fondos. Y la declaración **`color-scheme: light dark`** avisa al navegador de que tu página admite los dos esquemas, de modo que adapta solo los elementos que no estilizas tú: las barras de desplazamiento, los campos de formulario, el calendario de un `<input type="date">`.

!!! tip "Prueba el modo oscuro sin cambiar tu sistema"

    El inspector de Chrome permite emular `prefers-color-scheme` desde el panel **Renderizado** (*Rendering*), y Firefox tiene un botón con un sol y una luna en el panel de Estilos. Así puedes comprobar los dos modos sin tocar la configuración de tu ordenador.

!!! warning "No inviertas los colores sin más"

    Un modo oscuro no es el modo claro con los colores invertidos. El negro puro (`#000`) con texto blanco puro produce demasiado contraste y cansa la vista; los fondos gris muy oscuro funcionan mejor. Las sombras apenas se ven sobre fondos oscuros, así que las superficies elevadas (una tarjeta, un menú desplegable) se distinguen mejor con un fondo un poco más claro que el de la página.

## CSS y accesibilidad

La accesibilidad se decide en buena parte en el HTML, como viste en la UT2, pero CSS puede arruinar un HTML impecable. Estos son los puntos que más se olvidan:

- **El foco del teclado tiene que verse siempre.** No escribas nunca `outline: none` sin poner otro indicador de foco igual de visible en su lugar. Usa `:focus-visible` para darle el estilo que quieras.
- **El contraste se comprueba**, no se supone, y en los dos modos de color.
- **El color no puede ser la única pista.** Un campo con error marcado solo en rojo es invisible para una persona con daltonismo; añade un icono, un borde más grueso o un texto.
- **Los tamaños de letra en `rem`**, para que respeten la configuración del navegador. Prueba a subir el tamaño de letra del navegador al 200 % y comprueba que nada se corta ni se solapa.
- **Los objetivos táctiles, grandes.** Un enlace o un botón que se pulsa con el dedo debería medir al menos 24 × 24 píxeles, y mejor 44 × 44. Un poco de `padding` en los enlaces del menú lo resuelve.
- **El orden visual coincide con el del HTML.** Cuidado con `order` y `row-reverse`, que recolocan el contenido en pantalla pero no para el teclado.

## Buenas prácticas: errores que conviene evitar desde el principio

- **Ni estilos en línea ni bloques `<style>` en un proyecto con varias páginas.** Una hoja externa, enlazada desde todas.
- **Da estilo con clases, no con ids.** Los ids disparan la especificidad y te obligan a escalar con más ids o con `!important`.
- **`!important` es una salida de emergencia.** Si lo necesitas para que algo funcione, el problema está en la especificidad de tus selectores.
- **Nombra las clases con BEM, por lo que son y no por cómo se ven.** `.aviso--error` sigue teniendo sentido cuando cambies el rojo por otro color; `.texto-rojo`, no. Y un elemento lleva siempre el nombre de su bloque: `.tarjeta__titulo`, nunca `.tarjeta__cuerpo__titulo`.
- **No anides más de dos niveles.** Más profundidad es más especificidad y más dependencia de la estructura exacta del HTML.
- **Repetir un valor tres veces es una variable.** Colores, radios, espaciados y tipografías van en `:root`.
- **`box-sizing: border-box` desde el principio**, para que los tamaños midan lo que dicen.
- **No fijes alturas** si no es imprescindible: deja que el contenido decida y usa `min-height` cuando necesites un mínimo.
- **No uses `position: absolute` para maquetar.** La estructura se hace con Grid y Flexbox; `absolute` es para detalles sobre un elemento.
- **Mobile first.** Diseño de una columna por defecto y media queries con `min-width` (o `width >=`) para ir añadiendo.
- **Ordena la hoja de estilos**: variables y reset arriba, después los estilos base de etiquetas, después los componentes, y comenta cada bloque.
- **Revisa en el inspector antes de reescribir.** Si una regla "no funciona", el panel de Estilos te dice si está tachada, por qué regla, o si tiene un error.
- **Valida siempre.**

## Validar tu CSS

Igual que con HTML, el navegador es muy tolerante con los errores de CSS: una declaración mal escrita se ignora en silencio y el resto de la hoja sigue funcionando, así que el error puede pasar desapercibido durante semanas. El [validador de CSS del W3C](https://jigsaw.w3.org/css-validator/) comprueba tu hoja de estilos contra la especificación y te indica la línea exacta de cada error, además de una lista de avisos que conviene leer aunque no sean errores.

El validador va siempre un poco por detrás del lenguaje, así que puede que marque como error alguna funcionalidad muy reciente. Si te ocurre, no la quites sin más: compruébala en MDN y en Baseline, y si es estándar y está disponible en los navegadores, déjala y menciónalo en la documentación de tu entrega. Como con HTML, en este módulo la validación es un criterio que se evalúa, y tienes que aportar la evidencia de haberla hecho.

## Recursos complementarios

- [CSS by Manz](https://lenguajecss.com/css/)
- [Documentación de CSS (MDN Web Docs)](https://developer.mozilla.org/es/docs/Web/CSS)
- [Aprende CSS (web.dev)](https://web.dev/learn/css?hl=es)
- [Especificidad (MDN)](https://developer.mozilla.org/es/docs/Web/CSS/Specificity)
- [Guía completa de Flexbox (CSS-Tricks)](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Guía completa de Grid (CSS-Tricks)](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Validador de CSS del W3C](https://jigsaw.w3.org/css-validator/)
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Baseline: qué funciones web están disponibles en todos los navegadores](https://web.dev/baseline)
- [Can I use](https://caniuse.com/)

## Material de refuerzo y ampliación

Se recomienda completar el curso [Learn Basic CSS by Building a Cafe Menu](https://www.freecodecamp.org/learn/2022/responsive-web-design/learn-basic-css-by-building-a-cafe-menu/step-1) de freeCodeCamp, y practicar Flexbox y Grid con los juegos [Flexbox Froggy](https://flexboxfroggy.com/#es) y [Grid Garden](https://cssgridgarden.com/#es), ambos disponibles en español.

!!! info "Lo que viene ahora"

    En [CSS3 avanzado](02_css3_avanzado.md) ampliarás todo esto con transiciones y animaciones, tipografía fluida, áreas de Grid, *container queries*, capas de cascada, modo oscuro con `light-dark()` y selectores más potentes como `:has()`. Lo que has visto aquí es la base sobre la que se construye todo eso.
