# 1. Repaso de HTML5

En esta órbita vas a convertir tus mockups de Figma en una aplicación que funciona en el navegador, y lo primero que se escribe es el HTML. Parece el paso fácil, pero es el que más condiciona todo lo demás: **un buen CSS solo puede construirse sobre un buen HTML**. Si la lista de pistas está hecha con `<div>` sueltos, no se alinea bien; si la hora de la reserva es un `<div>` con un clic, no se puede elegir con el teclado; y si la pantalla no tiene encabezados, Manuel no puede recorrerla con el lector de pantalla del móvil.

Este apartado repasa lo que necesitas de HTML5 para maquetar tu sistema, con el foco en **elegir el elemento correcto** para cada parte de tus wireframes (RA2-a, RA6-b). En la Órbita 4 volverás sobre el HTML desde el punto de vista de la accesibilidad.

![De un wireframe de la Órbita 1 a los elementos de HTML que forman cada zona de la pantalla](img/orbita3_01_esquema_wireframe_html.svg)

## La plantilla de cada pantalla

Todas las pantallas de tu aplicación empiezan igual, así que conviene tener una plantilla correcta desde el primer día:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="color-scheme" content="light dark">
  <title>Elegir hora · Pádel · Polideportivo municipal</title>
  <meta name="description" content="Reserva una pista del polideportivo en menos de un minuto.">
  <link rel="stylesheet" href="css/main.css">
</head>
<body>
  <!-- contenido de la pantalla -->
</body>
</html>
```

| Línea | Para qué sirve |
|---|---|
| `<!DOCTYPE html>` | Hace que el navegador use el modo estándar |
| `lang="es"` | El lector de pantalla pronuncia en castellano |
| `charset="UTF-8"` | Las tildes y la eñe se ven bien |
| `viewport` | Sin ella, el móvil encoge la página y el diseño adaptable no funciona |
| `color-scheme` | Evita el destello blanco al cargar si la persona usa el modo oscuro |
| `<title>` | Lo primero que anuncia el lector de pantalla y lo que se ve en la pestaña; uno distinto por pantalla |
| `description` | El texto que muestran los buscadores (RA5-h) |

## Por qué importa la semántica

Casi todos los elementos de HTML sirven para decir **qué es** cada cosa, mientras que su aspecto lo decide el CSS. Un `<h2>` es el título de una sección aunque se vea pequeño, y un `<button>` es un control que hace algo, tenga la forma que tenga. Elegir el elemento por su significado tiene varias ventajas:

- **Accesibilidad.** Los lectores de pantalla anuncian cada elemento por su función ("botón", "encabezado de nivel 2") y permiten saltar de uno a otro (RA5-a).
- **Funcionamiento incluido en el navegador.** Un `<button>` ya se enfoca con el tabulador y se activa con Intro y con Espacio. Si lo haces con un `<div>`, tendrás que programarlo todo con JavaScript.
- **Menos código.** Los elementos nativos ya traen su comportamiento, y las **WSG** recomiendan usarlos antes que soluciones con JavaScript, porque pesan menos.
- **Un código que entiende todo el equipo.** Cualquiera que abra tu HTML sabe qué es cada parte sin mirar el diseño.

Para saber si estás usando bien la semántica, pregúntate ante cada elemento **qué es esto para quien no lo ve**. Si es un título, es un encabezado; si se pulsa para hacer algo, es un botón; y si es solo una caja para colocar cosas, entonces sí, es un `<div>`.

## Las zonas de una pantalla

HTML5 tiene elementos para las grandes zonas de una pantalla, y los lectores de pantalla los usan para saltar de una a otra:

| Elemento | Qué es | En el polideportivo |
|---|---|---|
| `<header>` | La cabecera | El logo y el menú |
| `<nav>` | Un bloque de navegación | El menú principal y la barra inferior del móvil |
| `<main>` | El contenido principal (**uno por página**) | El selector de pista y hora |
| `<aside>` | Contenido complementario | El resumen de la reserva |
| `<footer>` | El pie | El horario y el teléfono |
| `<section>` | Una parte temática, con su encabezado | "Horas libres" |
| `<article>` | Un contenido que se entiende por sí solo | Cada tarjeta de pista |

Un `<div>` es correcto cuando solo necesitas un contenedor para el CSS, como el envoltorio de una cuadrícula. Lo que hay que evitar es usarlo para algo que ya tiene un elemento propio. Si hay dos `<nav>`, ponle a cada uno un nombre con `aria-label` ("Principal", "Secciones") para que se puedan distinguir.

## Encabezados

Los encabezados, de `<h1>` a `<h6>`, forman **el índice de cada pantalla**, y siguen tres reglas:

1. **Un único `<h1>` por pantalla**, con su título ("Elegir hora").
2. **Sin saltos de nivel**: después de un `<h2>` viene otro `<h2>` o un `<h3>`, nunca un `<h4>`.
3. **El nivel lo decide la estructura.** El título de una tarjeta es un `<h3>` si le toca serlo, aunque en tu diseño se vea pequeño. El tamaño lo decides en el CSS con tu escala tipográfica.

Una forma rápida de comprobarlos es leer solo los encabezados, en orden, como el índice de un libro. Si se entiende qué hay en la pantalla, están bien.

## Texto y listas

Para el texto te bastan pocos elementos: **`<p>`** para los párrafos, **`<strong>`** para lo importante y **`<em>`** para el énfasis. Para las fechas y las horas, que en una aplicación de reservas aparecen en todas partes, usa **`<time>`** con el valor en formato estándar:

```html
<time datetime="2026-11-12T19:00">jueves 12 a las 19:00</time>
```

Casi cualquier grupo de elementos del mismo tipo es una **lista**: el menú, las pistas disponibles, las horas libres. Marcarlo como lista permite que el lector de pantalla diga "lista, 6 elementos" antes de empezar. Usa `<ul>` para las listas sin orden, `<ol>` para los pasos y `<dl>` para parejas de nombre y valor, como el resumen de una reserva:

```html
<dl class="booking-summary">
  <dt>Pista</dt> <dd>Pádel 2</dd>
  <dt>Hora</dt>  <dd><time datetime="19:00">19:00</time></dd>
</dl>
```

## Enlaces y botones

Esta es la distinción más importante del apartado, porque en Figma un enlace y un botón pueden verse igual: **un enlace lleva a otro sitio y un botón hace algo**.

- **`<a href="...">`** cuando al pulsarlo cambias de pantalla. "Ver mis reservas" es un enlace, aunque parezca un botón.
- **`<button>`** cuando al pulsarlo pasa algo en la pantalla: enviar el formulario, abrir un diálogo. "Reservar" y "Cancelar reserva" son botones.

El aspecto lo decides después en el CSS, y tu componente `.button` se puede aplicar a los dos. Dentro de un formulario, ponle a cada botón su tipo: `type="submit"` al que envía y `type="button"` a los demás.

El texto de un enlace o un botón tiene que entenderse **fuera de contexto**. Un lector de pantalla puede listar todos los enlaces de la página, y en esa lista cinco "Ver más" no sirven de nada, mientras que "Ver horarios de la pista de pádel 2" se entiende sin ver la pantalla.

## Imágenes

Una imagen lleva siempre estos atributos:

```html
<img src="img/pista-padel-2.webp"
     alt="Pista de pádel cubierta con paredes de cristal"
     width="640" height="360"
     loading="lazy">
```

- **`alt`** describe lo que la imagen aporta. Si es decorativa, va vacío (`alt=""`), para que el lector de pantalla la ignore.
- **`width` y `height`** dicen la proporción, para que el navegador reserve el hueco y la página no salte al cargar.
- **`loading="lazy"`** hace que solo se descargue cuando va a aparecer en pantalla, y ahorra datos a Lucía, como piden las **WSG**. La imagen principal de la pantalla no lo lleva.

Los iconos que acompañan a un texto que dice lo mismo son decorativos y llevan `aria-hidden="true"`. Cómo elegir el formato y el tamaño de cada imagen lo verás en el apartado de multimedia.

## Formularios

La aplicación del polideportivo es, en el fondo, un formulario: se elige pista, día y hora, y se envía.

```html
<form action="/reservas" method="post">
  <label for="date">Día</label>
  <input type="date" id="date" name="date" required>

  <fieldset>
    <legend>Hora</legend>
    <label><input type="radio" name="time" value="18:00"> 18:00</label>
    <label><input type="radio" name="time" value="19:00"> 19:00</label>
  </fieldset>

  <label for="phone">Teléfono de contacto</label>
  <input type="tel" id="phone" name="phone" autocomplete="tel">

  <button type="submit">Reservar</button>
</form>
```

Las reglas que necesitas están todas en el ejemplo:

- **Cada campo tiene su `<label>`**, unido con `for` e `id`. Un `placeholder` no la sustituye, porque desaparece al escribir.
- **Los grupos de opciones van en un `<fieldset>` con su `<legend>`.** Las horas son botones de opción con el mismo `name`, porque solo se puede elegir una.
- **El tipo de campo correcto** (`date`, `time`, `email`, `tel`) muestra el teclado o el selector adecuado en el móvil y valida el formato sin JavaScript.
- **`required`** y el resto de atributos de validación le dicen al navegador qué es un valor correcto.
- **Pide solo lo imprescindible.** Cada campo de más es tiempo y datos guardados, y las **WSG** y el diseño ético lo desaconsejan.

## Elementos interactivos nativos

Antes de construir algo con `<div>` y JavaScript, comprueba si HTML ya lo tiene. Dos elementos te van a servir:

- **`<details>` y `<summary>`** forman un bloque que se abre y se cierra, útil para las preguntas frecuentes o las condiciones de la reserva.
- **`<dialog>`** es un cuadro de diálogo, como el de "¿Seguro que quieres cancelar la reserva?". El navegador se encarga del foco, de la tecla Escape y del fondo oscuro.

??? info "Para saber más: tablas"

    Las tablas sirven para **datos con filas y columnas**, como el historial de reservas, y nunca para colocar elementos en la pantalla. Una tabla bien hecha tiene un título en `<caption>` y sus encabezados en `<th>` con `scope="col"` o `scope="row"`, para que el lector de pantalla diga a qué fila y columna pertenece cada celda.

## Del wireframe al HTML

Te recomiendo traducir cada pantalla en este orden, y **escribir el HTML completo antes de escribir CSS**:

1. **Las zonas**: cabecera, navegación, contenido principal, pie.
2. **Los encabezados**: el `<h1>` y los de cada sección.
3. **Los componentes**: qué elemento es cada uno (la tarjeta es un `<article>` dentro de un `<li>`, la hora es un botón de opción, "Reservar" es un `<button>`).
4. **El contenido real**, con su longitud de verdad.
5. **Las clases**, al final.

Cuando termines, haz la **prueba sin estilos**: desactiva el CSS desde el inspector y lee la pantalla de arriba abajo. Tiene que parecer un documento ordenado, con su título, sus secciones, sus listas y sus formularios con etiquetas. Si algo no se entiende así, tampoco lo entenderá un lector de pantalla.

## Validar

El navegador corrige en silencio los errores de HTML, y a veces de una forma que no esperas. Pasa cada pantalla por el [validador del W3C](https://validator.w3.org/) y guarda la evidencia, porque el uso de estándares se evalúa (RA6-b).

## Antes de seguir

Comprueba en tu pantalla principal que:

1. La plantilla tiene `lang`, `viewport`, `color-scheme` y un `<title>` propio.
2. Hay un único `<main>` y un único `<h1>`, y los encabezados no se saltan niveles.
3. Lo que lleva a otro sitio es un `<a>` y lo que hace algo es un `<button>`.
4. Cada campo tiene su `<label>`, y cada grupo de opciones su `<fieldset>`.
5. Las imágenes tienen `alt`, `width` y `height`.
6. La pantalla se entiende con el CSS desactivado.
7. El validador no da errores.

Si usas una IA o una herramienta que convierte diseños en código (como el modo Dev de Figma o Google Stitch), anótalo en el `CHANGELOG.md` y revisa su resultado con esta lista: suelen generar `<div>` para todo, botones sin nombre e imágenes sin `alt`.

## Recursos

- [HTML en español, de Manz (lenguajehtml.com)](https://lenguajehtml.com/)
- [Referencia de elementos HTML (MDN Web Docs)](https://developer.mozilla.org/es/docs/Web/HTML/Element)
- [Validador del W3C](https://validator.w3.org/)
