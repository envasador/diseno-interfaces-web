# Órbita 2 — Ayuda: Auto layout, responsive y variables en Figma

Cuando conviertas tus wireframes en mockups (paso 8 del proyecto), vas a colocar cada elemento dentro de **Auto layout**. Es la herramienta de Figma que reparte los elementos de un contenedor siguiendo unas reglas (en fila o en columna, con un espacio fijo entre ellos y un relleno alrededor) en lugar de dejarlos colocados a mano en una posición. Tiene tres ventajas para tu proyecto. La primera es que los espacios salen de tus variables de espaciado, así que todas las pantallas respetan la misma escala. La segunda es que, si un texto crece (un nombre de pista más largo o la letra aumentada al 200 %), el resto de elementos se recoloca solo. Y la tercera es que funciona igual que **Flexbox**, que es lo que vas a usar en la Órbita 3 para maquetar, así que lo que construyas aquí lo traducirás a CSS casi palabra por palabra (RA1-f).

En esta ayuda los nombres de las opciones aparecen como en Figma en inglés, que es como los encontrarás en la mayoría de tutoriales.

## Qué es el Auto layout

Selecciona varios elementos (o un frame) y pulsa **Shift + A**, o elige **Add auto layout** en el panel derecho. Figma los mete en un contenedor que los ordena con estas propiedades:

| Propiedad en Figma | Qué hace | Su equivalente en CSS (Órbita 3) |
|---|---|---|
| **Dirección** (vertical, horizontal o *wrap*) | Coloca los elementos uno debajo de otro, uno al lado de otro o en filas que saltan cuando no caben | `flex-direction` y `flex-wrap` |
| **Gap** (espacio entre elementos) | La separación entre cada elemento y el siguiente | `gap` |
| **Padding** (relleno) | El espacio entre el borde del contenedor y su contenido, en cada lado | `padding` |
| **Alignment** (alineación) | Dónde se colocan los elementos dentro del contenedor: arriba, al centro, a la izquierda... | `justify-content` y `align-items` |

La idea clave es que **cada contenedor solo decide en una dirección**. Una pantalla completa es un Auto layout vertical (cabecera, contenido y navegación, uno debajo de otro). Dentro de él, la cabecera es un Auto layout horizontal (botón de volver, título y acción). Y dentro del contenido, cada tarjeta es otro Auto layout vertical. Este anidamiento es lo que te permite construir cualquier pantalla con piezas sencillas.

En este vídeo verás el Auto layout en funcionamiento: cómo se crea, cómo se anidan los contenedores y cómo se comportan los elementos al cambiar su contenido.

<div style="position:relative; padding-bottom:56.25%; height:0; overflow:hidden; margin:24px 0;">
  <iframe src="https://www.youtube-nocookie.com/embed/rgbnAsmPaZk" title="Auto layout en Figma" style="position:absolute; top:0; left:0; width:100%; height:100%; border:0;" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen loading="lazy"></iframe>
</div>

<small>**Fuente:** vídeo publicado en YouTube ([ver en YouTube](https://www.youtube.com/watch?v=rgbnAsmPaZk), por si no se carga aquí). Se incluye con fines exclusivamente educativos; todos los derechos pertenecen a su autor.</small>

## Cómo cambia de tamaño cada elemento

Cada elemento que está dentro de un Auto layout tiene un comportamiento de tamaño en horizontal y otro en vertical. Son tres opciones, y entenderlas es lo que hace que una pantalla se adapte bien o se rompa:

- **Fixed** (fijo). El elemento mide siempre lo mismo, pase lo que pase. Úsalo para lo que tiene un tamaño decidido en tu sistema, como un icono de 24 × 24 píxeles o un botón de icono de 44 × 44.
- **Hug contents** (ajustarse al contenido). El elemento mide lo que mida su contenido más el relleno. Un botón con *hug* crece si su etiqueta es más larga, y por eso "Reservar pista" y "Cancelar reserva" tienen anchos distintos sin que tengas que tocarlos.
- **Fill container** (rellenar el contenedor). El elemento ocupa todo el espacio libre de su contenedor. Es la opción que hace que una tarjeta ocupe todo el ancho de la pantalla en el móvil y se estire si la pantalla es más ancha.

Además, puedes poner un **ancho mínimo y máximo** (*min width* y *max width*) a cualquier elemento. Son muy útiles para que un bloque de texto no pase de una longitud de línea cómoda en pantallas grandes (por ejemplo, un máximo de unos 680 píxeles para el texto de lectura) o para que un botón no quede ridículamente estrecho.

Una regla práctica para las pantallas de móvil: la pantalla y sus secciones van con **Fill** en horizontal y **Hug** en vertical, y los botones e iconos con **Hug** o **Fixed**. Si algo se sale de la pantalla o se aplasta, casi siempre es porque tiene un ancho **Fixed** donde debería tener **Fill**.

Si necesitas un elemento que flote por encima del resto (un distintivo en la esquina de una tarjeta, por ejemplo), selecciónalo y activa **Absolute position**. Ese elemento deja de seguir las reglas del Auto layout y se coloca con **restricciones** (*constraints*) respecto a los bordes del contenedor. Resérvalo para casos puntuales como ese.

## Aplicar tus variables al Auto layout

Aquí es donde se juntan el Auto layout y el sistema que has construido. Los campos de **gap**, **padding**, **radio de las esquinas**, **ancho** y **alto** admiten variables de número. Para aplicar una, pasa el ratón sobre el campo, haz clic en el icono de variable que aparece a su derecha y elige la variable de tu escala (`space/4`, `space/6`, `radius/md`...).

Si en el paso 7 configuraste bien el **ámbito** de cada variable, en el campo de *gap* solo te aparecerán las de espaciado, y en el del radio solo las de radio. Si te aparecen todas mezcladas, vuelve a revisar el ámbito, porque te ahorrará muchos errores.

Cuando todo el espaciado de una pantalla sale de variables, ocurren dos cosas. Por un lado, la proximidad que analizaste en el paso 2 queda fijada en el sistema (un `space/2` entre la etiqueta y su campo y un `space/6` entre un campo y el siguiente, por ejemplo). Por otro, en el modo de desarrollo de Figma aparecerá el nombre de la variable en lugar de un número suelto, y en la Órbita 3 sabrás exactamente qué propiedad de CSS tienes que escribir.

## Comprobar que la pantalla se adapta

Con la pantalla construida con Auto layout, haz esta prueba: selecciona el frame de la pantalla y estíralo en horizontal, de 360 a unos 1280 píxeles, y luego vuelve a dejarlo como estaba. Fíjate en tres cosas:

1. Que nada se sale del frame ni se monta encima de otro elemento.
2. Que las tarjetas y los campos se estiran (porque tienen **Fill**) y los botones y los iconos mantienen su tamaño.
3. Que los textos largos no forman líneas larguísimas, gracias al ancho máximo.

Si además le aplicas al frame tu estilo de retícula, verás si los elementos siguen alineados con las columnas. En el proyecto solo se pide el tamaño del dispositivo de tu persona principal, pero esta prueba te dice si tu pantalla está bien construida, y en la Órbita 3 te facilitará mucho el trabajo con las *media queries*.

Este vídeo muestra cómo se prepara en Figma una pantalla para distintos tamaños, que es justo lo que tienes que hacer con tu pantalla principal en el paso 8 del proyecto.

<div style="position:relative; padding-bottom:56.25%; height:0; overflow:hidden; margin:24px 0;">
  <iframe src="https://www.youtube-nocookie.com/embed/grKp_TVAaTE" title="Diseño responsive en Figma" style="position:absolute; top:0; left:0; width:100%; height:100%; border:0;" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen loading="lazy"></iframe>
</div>

<small>**Fuente:** vídeo publicado en YouTube ([ver en YouTube](https://www.youtube.com/watch?v=grKp_TVAaTE), por si no se carga aquí). Se incluye con fines exclusivamente educativos; todos los derechos pertenecen a su autor.</small>

Si en una zona tienes varias tarjetas que deberían colocarse en dos o tres columnas cuando la pantalla es más ancha, pon su contenedor en dirección **wrap**: las tarjetas se colocarán una al lado de otra mientras quepan y saltarán a la fila siguiente cuando no.

## Ampliación: variables con modos para cada tamaño de pantalla

Esto no se pide en el proyecto, pero si tus personas usan dos dispositivos distintos (Lucía el móvil y Manuel el portátil, por ejemplo) o quieres ir un paso más allá, puedes usar los **modos** de las variables para los tamaños de pantalla, igual que los usaste para el modo claro y el oscuro.

Crea una colección más, por ejemplo `layout`, con dos modos (**Móvil** y **Escritorio**), y define en ella las variables que cambian según el tamaño: el margen lateral de la pantalla, el relleno de las secciones, el tamaño de los títulos grandes o el ancho máximo del contenido. Las columnas, el medianil y el margen de la retícula también admiten variables de número. Después, duplica una pantalla, cambia su ancho y aplícale el modo **Escritorio** desde el panel derecho. Todos los valores de esa colección cambiarán a la vez, y la pantalla de escritorio quedará construida con los mismos componentes que la de móvil.

Este vídeo (en inglés) junta todo lo que has visto en esta ayuda: el Auto layout, la retícula y las variables con modos para cada tamaño de pantalla. Es el mejor resumen si quieres hacer la ampliación.

<div style="position:relative; padding-bottom:56.25%; height:0; overflow:hidden; margin:24px 0;">
  <iframe src="https://www.youtube-nocookie.com/embed/d0uFJA5OjBo" title="Figma responsive design using variables, layout grids and auto layout" style="position:absolute; top:0; left:0; width:100%; height:100%; border:0;" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen loading="lazy"></iframe>
</div>

<small>**Fuente:** vídeo publicado en YouTube ([ver en YouTube](https://www.youtube.com/watch?v=d0uFJA5OjBo), por si no se carga aquí). Se incluye con fines exclusivamente educativos; todos los derechos pertenecen a su autor.</small>

Esta forma de trabajar es la que más se parece a lo que harás en CSS, donde una propiedad personalizada como `--layout-margin` cambia de valor dentro de una *media query*.

## Errores frecuentes

- **Elementos colocados a mano dentro de un frame sin Auto layout.** En cuanto cambias un texto, todo se descoloca. Si al mover un elemento no "salta" a su sitio, ese contenedor no tiene Auto layout.
- **Números escritos a mano en el *gap* o el *padding*.** Funcionan, pero rompen el sistema. Selecciona la pantalla y revisa que cada espacio muestra el nombre de una variable.
- **Todo con ancho fijo.** La pantalla se ve bien a 360 píxeles y se rompe en cuanto cambia cualquier cosa. Revisa los anchos de las secciones y de las tarjetas.
- **Demasiados niveles de anidamiento.** Si para llegar a un texto tienes que hacer doble clic seis veces, probablemente sobra algún contenedor. Cada Auto layout tiene que agrupar algo que se perciba como un grupo.
- **Espacios entre grupos iguales a los espacios dentro de los grupos.** Es el error de proximidad del apartado 2, y con Auto layout se ve enseguida: el *gap* de dentro de una tarjeta tiene que ser menor que el *gap* entre tarjetas.

## Para saber más

Los artículos de [UI From Mars](https://uifrommars.com/categoria/diseno-ui/) sobre diseño de interfaces te servirán como apoyo mientras construyes los mockups. Para lo que se trata en esta ayuda, estos son los más útiles:

- [Aprende Auto Layout de Figma](https://uifrommars.com/auto-layout-figma/), con las opciones de tamaño, los mínimos y máximos y el *wrap*.
- [Variables en Figma: aprende a utilizarlas](https://uifrommars.com/variables-en-figma-aprende-a-utilizarlas/), con las colecciones, los grupos y el ámbito.
- [Variants en Figma: aprende a utilizarlas](https://uifrommars.com/variants-figma/), para los estados de tus componentes.
- [Guía para diseñar cards en UI](https://uifrommars.com/guia-diseno-cards/), con buenas prácticas para uno de los componentes más habituales.
