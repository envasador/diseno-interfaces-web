# Órbita 3 — Dar forma al sistema

**Horas:** unas 25 · **RA principales:** RA2 (criterios a a j) y RA3 · **Comienzo:** 4 de noviembre

En la Órbita 1 decidiste qué hace tu aplicación y cómo se recorre, y en la Órbita 2 decidiste su aspecto y lo convertiste en un sistema de tokens y componentes en Figma. En esta órbita vas a llevar ese sistema al navegador. Escribirás el HTML de cada pantalla, trasladarás los tokens a propiedades personalizadas de CSS, maquetarás los componentes con sus estados y su modo oscuro, y organizarás todo el código con Sass, ITCSS y BEM para que siga siendo fácil de mantener cuando el proyecto crezca. Todas las decisiones visuales ya están tomadas y justificadas, así que tu trabajo consiste en llevarlas al código sin perder ninguna por el camino, y en el camino tendrás que decidir también cuánto pesa cada pantalla, porque las imágenes, las fuentes y el código que envías al móvil de tus personas tienen un coste para ellas y para el planeta.

Lo que construyas aquí es la versión en código de tu sistema de diseño. En la Órbita 4 comprobarás con ella la accesibilidad de tu aplicación, en la Órbita 5 medirás su peso y su huella con las herramientas de sostenibilidad, y en la Órbita 6 la documentarás y la publicarás.

---

## Qué vas a entregar

Todo el trabajo de esta órbita se hace en tu repositorio de GitHub, con el editor de código y Sass, y tu archivo de Figma pasa a ser la referencia que consultas mientras maquetas.

| Documento | Herramienta | Qué es | Para qué lo usarás después |
|---|---|---|---|
| **Tokens en código** | SCSS | Los tokens primitivos y semánticos de Figma convertidos en propiedades personalizadas de CSS, con los mismos nombres y con el modo oscuro | Serán la base de la auditoría de contraste de la Órbita 4 y de la documentación de la Órbita 6 |
| **Librería de componentes** | HTML y SCSS | El set mínimo de componentes de tu sistema (botones con todos sus estados, campos de formulario, tarjetas, navegación de escritorio y de móvil, componentes tipográficos, etiquetas, diálogos y avisos), organizado con ITCSS y nombrado con BEM | Cada componente se auditará con las herramientas de accesibilidad en la Órbita 4 |
| **Pantallas maquetadas** | HTML y SCSS | Las pantallas del happy path construidas con tus componentes, adaptables a los dispositivos de tus personas | Serán las pantallas que evaluarás con personas reales en la Órbita 5 |
| **Multimedia optimizada** | Squoosh, SVGOMG | Las imágenes y los iconos de tu aplicación en el formato y el tamaño adecuados, con su licencia anotada y un presupuesto de peso justificado | Será uno de los datos de la auditoría de sostenibilidad de la Órbita 5 |

Además, como en las órbitas anteriores, cualquier uso de una IA quedará anotado en el `CHANGELOG.md` del repositorio.

## Apartados

1. [Repaso de HTML5](01_html5.md)
2. [Apuntes de CSS3](02_css3.md)
3. [Apuntes de Sass](03_sass.md)
4. [Del sistema de Figma a la hoja de estilos](04_del_sistema_al_codigo.md)
5. Arquitectura ITCSS (próximamente)
6. Nomenclatura BEM (próximamente)
7. Multimedia y ecodiseño (próximamente)
8. Componentes: el set mínimo (próximamente)

Los tres primeros apartados son los apuntes de referencia de las herramientas, y el cuarto es la hoja de ruta para aplicarlas a tu sistema. Te recomiendo leerlos en orden y volver a los apuntes cada vez que te atasques con una propiedad concreta.
