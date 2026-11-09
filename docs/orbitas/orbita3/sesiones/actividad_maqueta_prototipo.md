# Actividad de clase: maqueta tu prototipo en HTML y CSS

En esta actividad vas a pasar a HTML y CSS una de las pantallas que diseñaste en Figma en la Órbita 2, usando Flexbox para colocar los bloques (RA2, RA3). Antes, calentarás con un juego para practicar las propiedades de Flexbox.

## Calentamiento: Flexbox Froggy

Completa los 24 niveles de [Flexbox Froggy en español](https://flexboxfroggy.com/#es) y haz una captura de la pantalla final. Fíjate en qué pasa con `justify-content` y `align-items` cuando cambias `flex-direction` a `column`, porque los ejes se intercambian. Si te atascas, consulta la tabla de propiedades del contenedor en el apartado de Flexbox de los apuntes de CSS3.

## Ejercicio: maqueta una pantalla

Maqueta **una sola pantalla**, la primera de tu *happy path*, en su versión para móvil. Si terminas, pasa a la siguiente.

1. **Prepara la carpeta.** En el repositorio de tu proyecto, crea una carpeta `maqueta/` con un `index.html`, una carpeta `css` con `estilos.css` y una carpeta `img`. Empieza la hoja de estilos con el reset de los apuntes y enlaza desde el `<head>` la hoja y tu fuente de Google Fonts, sin olvidar la etiqueta `<meta name="viewport">`.
2. **Descompón la pantalla en cajas.** Exporta la pantalla de Figma como imagen y dibuja un rectángulo alrededor de cada bloque, de fuera hacia dentro. Junto a cada rectángulo que tenga hijos, anota si van en fila o en columna y cómo se reparten. Los marcos con Auto layout de Figma te dan casi toda esta información.
3. **Escribe el HTML.** Cada rectángulo es una etiqueta semántica (`<header>`, `<nav>`, `<main>`, `<article>`, `<button>`...) con una clase que diga lo que es. Sin CSS, la página tiene que leerse en orden y con los títulos en su jerarquía.
4. **Pasa tus variables de Figma a CSS.** Declara tus tokens como propiedades personalizadas en `:root`, con los mismos nombres que en Figma e incluyendo el modo oscuro. En el resto de la hoja usa solo los tokens semánticos.
5. **Coloca las cajas con Flexbox.** Aplica a cada contenedor lo que anotaste en el paso 2, separa con `gap` y no fijes alturas. Trabaja con el inspector a 360 píxeles de ancho y tu diseño de Figma al lado.

## Comprobación

- [ ] El HTML y el CSS pasan los validadores del W3C.
- [ ] Fuera de `:root` no hay colores ni fuentes escritos a mano.
- [ ] La pantalla se ve bien en modo oscuro y con la letra del navegador al 200 %.
- [ ] Puedes recorrer los enlaces y botones con el tabulador y se ve el foco.

## Entrega

Sube a tu repositorio la carpeta `maqueta/`, con la captura de Flexbox Froggy y la imagen de tu despiece en cajas dentro de `img/`. Si has usado alguna herramienta de IA, anótala en tu `CHANGELOG.md`.
