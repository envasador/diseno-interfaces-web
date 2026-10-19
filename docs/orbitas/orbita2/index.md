# Órbita 2 — Fundar el sistema visual

**Horas:** unas 15 · **RA principales:** RA1 (criterios a, b, d, e y f) · **Semanas:** de la 5 a la 7

En la Órbita 1 decidiste qué hace tu aplicación y cómo se recorre, y lo dibujaste todo en escala de grises. En esta órbita vas a decidir su aspecto, es decir, los colores, las tipografías, los iconos, los espacios entre elementos y la forma de los botones y las tarjetas, y para hacerlo con criterio vas a aprender antes cómo lee una persona una pantalla y qué patrones de interfaz ya conoce. Lo vas a hacer en un orden distinto al que seguramente esperas, porque antes de pintar ninguna pantalla vas a definir todos esos valores en Figma y a ponerle un nombre a cada uno, y solo cuando el sistema esté completo lo aplicarás a tus wireframes para convertirlos en las pantallas definitivas. Cada decisión visual que tomes tendrá que poder explicarse a partir de tus personas, porque un color o un tamaño de letra también ayudan (o estorban) a que Manuel y Lucía consigan lo que necesitan.

Lo que construyas aquí es la base de todo lo que viene después. En la Órbita 3 pasarás estos mismos valores a CSS, en la Órbita 4 comprobarás con ellos el contraste y la legibilidad de tu aplicación, y en la Órbita 6 los documentarás en el `DESIGN.md` del proyecto.

!!! warning "Antes de empezar: solicita el plan de Educación de Figma"
    El modo oscuro, que es obligatorio en esta órbita, se construye con los **modos** de las variables de Figma, y esa función no está disponible en el plan gratuito (Starter). Como estudiante puedes pedir sin coste el plan de Educación, que sí la incluye. Solicítalo desde la página de Figma for Education con tu correo del centro en cuanto empieces la órbita, porque la verificación puede tardar unos días.

---

## Qué vas a entregar

Todo el trabajo de esta órbita se hace en Figma Design, en el mismo archivo donde tienes los wireframes, y se organiza en dos partes. La primera es la **capa de foundations** de tu sistema de diseño, es decir, el conjunto de valores básicos (colores, tipografía, espaciado, radios y sombras) del que saldrá todo lo demás. La segunda son los **mockups**, que son tus wireframes con ese sistema aplicado.

| Documento | Herramienta | Qué es | Para qué lo usarás después |
|---|---|---|---|
| **Variables de color** | Figma Design | Una colección de tokens primitivos con tu paleta completa y otra de tokens semánticos (`primary`, `surface`, `on-surface`, `error`, `success`, `warning`...) con dos modos, claro y oscuro | Se convertirán en las propiedades personalizadas de CSS de tu proyecto en la Órbita 3 y serán la base de la auditoría de contraste de la Órbita 4 |
| **Escala tipográfica** | Figma Design | Entre seis y ocho niveles de texto con nombre (`display`, `heading`, `body`, `caption`...), definidos con variables y guardados como estilos de texto | Te dará los estilos de los títulos y los textos de toda la web |
| **Espaciado, retícula, radio y elevación** | Figma Design | Una escala de espacios basada en una cuadrícula de 4 u 8 píxeles, la retícula de columnas de cada tamaño de pantalla, los radios de las esquinas y los niveles de sombra | Decidirán los márgenes, el relleno, la colocación y la forma de todos los componentes que programes |
| **Iconos** | Figma Design | Los iconos que usa tu aplicación, de una única librería, convertidos en componentes y con un tamaño definido por la escala | Se exportarán en SVG para la maquetación de la Órbita 3 |
| **Guía de estilo** | Figma Design | Una página del archivo que muestra cada token y cada estilo con su nombre, su valor y el motivo de la decisión, junto a ejemplos de uso | Te servirá de referencia mientras maquetas en la Órbita 3 y será la base de la documentación de la Órbita 6 |
| **Mockups** | Figma Design | Todas las pantallas del recorrido de tu user flow con el sistema aplicado, en modo claro y oscuro, enlazadas en un prototipo | Serán el modelo que maquetarás con HTML y CSS en la Órbita 3 |

Además, como en la Órbita 1, cualquier uso de una IA quedará anotado en el `CHANGELOG.md` del repositorio.

## Apartados

1. [Por qué los tokens antes que las pantallas](01_tokens_antes_que_pantallas.md)
2. [Percepción visual y jerarquía](02_percepcion_visual.md)
3. Color: de la intuición al sistema (próximamente)
4. Tipografía: legibilidad, escala y jerarquía (próximamente)
5. Espaciado, retícula y composición (próximamente)
6. Iconos e imágenes (próximamente)
7. Patrones de interfaz (próximamente)
8. Variables en Figma: modo claro y oscuro (próximamente)
9. Del wireframe al mockup: guía de estilo y entregable (próximamente)
