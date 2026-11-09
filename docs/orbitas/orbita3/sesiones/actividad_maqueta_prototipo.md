# Actividad de clase: maqueta tu prototipo de Figma en HTML y CSS

## Para qué sirve esta sesión

Hoy vas a convertir en una página web de verdad una de las pantallas que diseñaste en Figma durante la Órbita 2. Hasta ahora tu prototipo solo existía como dibujo, y en la Órbita 3 tiene que pasar a HTML y CSS, así que esta práctica es el primer paso de ese camino (RA2, RA3).

La sesión tiene dos partes. Primero calentarás con **Flexbox Froggy**, un juego que te obliga a usar las propiedades de Flexbox muchas veces seguidas hasta que dejas de tener que mirarlas. Después aplicarás eso mismo a tu pantalla, que es donde de verdad se aprende, porque un diseño real nunca está tan ordenado como los niveles del juego.

Todavía no vamos a usar ITCSS ni Sass (los veremos la semana del 16 de noviembre). Hoy basta con un HTML semántico limpio y una única hoja de estilos bien ordenada, y lo que hagas te servirá de base cuando reorganicemos el código con esas metodologías.

## Primera parte: Flexbox Froggy (unos 15-20 minutos)

Abre [Flexbox Froggy en español](https://flexboxfroggy.com/#es) y completa los 24 niveles. En cada uno tienes que llevar a las ranas hasta su nenúfar escribiendo propiedades de Flexbox en el contenedor (o, en algunos niveles, en una rana concreta). Cuando termines el último, haz una captura de la pantalla final y guárdala, porque te la voy a pedir.

Mientras juegas, fíjate en dos cosas que luego vas a necesitar en tu maqueta. La primera es qué pasa con `justify-content` y `align-items` cuando cambias `flex-direction` a `column`: los ejes se intercambian, y es el error que más verás en clase. La segunda es la diferencia entre las propiedades del contenedor y las de cada ítem (`order` y `align-self`).

Si te atascas en un nivel, vuelve primero a la tabla de propiedades del contenedor en el apartado de Flexbox de los apuntes de CSS3, y solo si sigues sin verlo pregunta a quien tengas al lado.

## Segunda parte: maqueta una pantalla de tu prototipo (el resto de la sesión hasta que llegue)

Vas a maquetar **una sola pantalla**, la primera de tu *happy path* (la de inicio o la que la persona ve nada más entrar), en su versión para móvil. Es mejor una pantalla bien hecha que tres a medias, y si te sobra tiempo pasarás a la siguiente. Para que veas cómo se hace, en cada fase uso como ejemplo la pantalla de inicio de la app del polideportivo, la que abre Lucía para ver sus próximas reservas.

Las fases 1, 2 y 3 las harás por tu cuenta mientras llego (entre las tres son unos 35 minutos, que junto con Flexbox Froggy cubren la primera hora). Las fases 4 y 5 las haremos juntos en clase, porque pasar los tokens de Figma a CSS es donde más dudas suelen salir. Si terminas la fase 3 antes de que llegue, revísala con la prueba de terminado del final del documento (los dos primeros puntos ya los puedes comprobar) y empieza a localizar en Figma los tokens que vas a necesitar.

### Fase 1. Prepara la carpeta (10 minutos)

En tu repositorio del proyecto, crea una carpeta `maqueta/` con un index.html, una carpeta css con el fichero estilos.css dentro y una carpeta img para las imágenes. El reset es el de los apuntes de CSS3 y va al principio de `estilos.css`.

Enlaza la hoja de estilos y la fuente de Google Fonts que elegiste en la Órbita 2 desde el `<head>`, y no te olvides de la etiqueta `<meta name="viewport">`, sin la cual nada de lo que hagas después se verá bien en el móvil.

### Fase 2. Descompón la pantalla en cajas (15 minutos)

Esta es la fase que más cuesta y la que más enseña, así que no te la saltes. Exporta tu pantalla de Figma como imagen, ábrela en FigJam o en papel y dibuja un rectángulo alrededor de cada bloque, de fuera hacia dentro: primero las zonas grandes (cabecera, contenido principal, barra de navegación inferior), después lo que hay dentro de cada una (una tarjeta de reserva, una fila de botones), y así hasta llegar a los textos e iconos sueltos.

Junto a cada rectángulo que tenga hijos, escribe dos cosas: si sus hijos van **en fila o en columna**, y cómo se reparten. En la pantalla de Lucía, la cabecera es una fila con el saludo a la izquierda y el avatar a la derecha (`row` y `space-between`), el listado de reservas es una columna con separación entre tarjetas (`column` y `gap`), y dentro de cada tarjeta hay otra fila con la fecha y el botón de cancelar. Si has usado Auto layout en Figma, ya tienes media fase hecha, porque cada marco con Auto layout es un contenedor flexible y su dirección y su separación se traducen casi directamente a CSS.

### Fase 3. Escribe el HTML sin una sola línea de CSS (10 minutos)

Cada rectángulo de la fase anterior es una etiqueta. Elige la semántica antes que el aspecto: la cabecera es un `<header>`, la barra inferior es un `<nav>` con una lista dentro, cada reserva es un `<article>` con su propio título, y los botones que hacen algo son `<button>`, mientras que los que llevan a otra página son `<a>`. Pon clases con nombres que digan lo que es cada cosa (`.tarjeta-reserva`, `.cabecera`), y no ids.

Antes de pasar a la siguiente fase, abre la página en el navegador tal cual. Tiene que leerse de arriba abajo en un orden que tenga sentido, con los títulos en su jerarquía, aunque sea fea. Si no se entiende sin estilos, el problema está en el HTML, y el CSS no lo va a arreglar. Pásala también por el [validador de HTML del W3C](https://validator.w3.org/).

### Fase 4. Traslada tus variables de Figma a CSS (15 minutos)

En la Órbita 2 creaste tus tokens como variables de Figma, primitivos y semánticos, con su modo oscuro. Ahora pasan a ser propiedades personalizadas en `:root`, con los mismos nombres que usaste en Figma (cambiando la barra por un guión), para que cualquier persona del equipo encuentre la correspondencia sin preguntar.

En el resto de la hoja de estilos usa solo los tokens semánticos. Si te encuentras escribiendo un color en hexadecimal fuera de `:root`, o te falta un token en Figma o te sobra ese color.

### Fase 5. Coloca las cajas con Flexbox (el tiempo que quede)

Ahora sí, recorre tu dibujo de la fase 2 y aplica a cada contenedor lo que anotaste: `display: flex`, la dirección, el reparto y el `gap`. Usa `gap` para separar ítems en lugar de márgenes, y no fijes alturas, deja que el contenido las decida.

Trabaja con el inspector abierto en modo dispositivo, a 360 píxeles de ancho, y con tu diseño de Figma al lado. Cuando una caja no se coloque donde esperas, actívale el resaltado de Flexbox en el panel de Elementos (la etiqueta `flex` que aparece junto al nodo) antes de cambiar nada, porque casi siempre la respuesta es que la propiedad está en el contenedor equivocado. Ya verás que no vas a clavar los píxeles de Figma, y no hace falta: lo que tiene que coincidir es la estructura, los espacios y los colores, que salen de los mismos tokens.

Si terminas la versión móvil, ensancha la ventana poco a poco y, donde el diseño empiece a verse mal, añade tu primera media query con `width >=`, siguiendo el enfoque *mobile first* de los apuntes.

## Antes de irte: prueba de terminado

Tu pantalla está terminada cuando, puesta al lado de tu diseño de Figma a 360 píxeles, una persona que no la ha hecho reconoce que es la misma, y además cumple todo lo de esta lista. Revísala tú antes de que lo haga yo, porque en la auditoría oral te preguntaré por qué cada contenedor va en fila o en columna, y la respuesta tiene que estar en tu despiece de la fase 2.

- [ ] Sin CSS, la página se lee en orden y los títulos siguen la jerarquía `h1`, `h2`, `h3`.
- [ ] El HTML y el CSS pasan los validadores del W3C sin errores.
- [ ] Fuera de `:root` no hay ningún color ni ninguna fuente escritos a mano, solo tokens semánticos.
- [ ] Con el modo oscuro emulado en el inspector (panel Renderizado), la pantalla se ve bien y el texto contrasta.
- [ ] Con la letra del navegador al 200 %, nada se corta ni se solapa.
- [ ] Puedes recorrer todos los enlaces y botones con el tabulador y ves dónde está el foco.

Al acabar la sesión, haz *commit* y *push* de la carpeta `maqueta/` con la captura del último nivel de Flexbox Froggy y la imagen de tu despiece en cajas dentro de `img/`. Si has usado alguna herramienta de IA, anótala en tu `CHANGELOG.md` como en las órbitas anteriores. Lo que no hayas terminado hoy lo retomaremos en la próxima clase, así que sube lo que tengas aunque esté a medias.
