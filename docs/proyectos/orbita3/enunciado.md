# Proyecto de la Órbita 3: Maquetar para dar forma

**Horas:** unas 25 · **Comienzo:** 4 de noviembre · **RA:** RA1 y RA2 · **Trabajo:** individual

## El encargo

Vas a maquetar en HTML y Sass tu aplicación: las pantallas del happy path que diseñaste en la Órbita 2 y las que necesiten las funcionalidades que añadas con JavaScript en DWEC y no tengas todavía, con tus tokens de Figma convertidos en propiedades personalizadas, tus componentes con todos sus estados y el modo oscuro. La aplicación se publica en GitHub Pages.

Condiciones técnicas:

- **Sass** es obligatorio para montar la arquitectura **ITCSS**: una carpeta de parciales por capa y un `main.scss` que lo compila todo en un solo `main.css`. Dentro de cada parcial puedes escribir CSS normal. Las variables, los mixins y los bucles de Sass son opcionales, y el criterio de los preprocesadores (RA2-j) se evalúa en el proyecto de Angular.
- Todas las clases se nombran con **BEM**.
- Todos los colores, tamaños y espacios salen de un token.
- No se pueden usar frameworks de CSS como Bootstrap o Tailwind.
- El JavaScript de la aplicación lo trabajarás en el módulo de DWEC.

---

## Qué tienes que hacer

Sigue los pasos en orden. Trabajas en el mismo repositorio y con el mismo `CHANGELOG.md` de las órbitas anteriores.

### Paso 1. Prepara el repositorio

Crea esta estructura, con un HTML por pantalla y un parcial de Sass por componente:

```text
mi-aplicacion/
├── index.html
├── elegir-hora.html
├── componentes.html
├── scss/            main.scss, settings/ tools/ generic/ elements/ objects/ components/ utilities/
├── css/main.css     (el CSS compilado, que es el que carga el HTML)
└── img/
```

Activa **GitHub Pages** desde el principio y pon la dirección al principio del `README.md`. Sube siempre el `main.css` compilado, porque es lo que se publica.

### Paso 2. Escribe el HTML

Escribe el HTML de todas las pantallas (las del happy path y las que necesiten las funcionalidades de DWEC), sin CSS: zonas semánticas, encabezados sin saltos y el elemento correcto para cada cosa (`<a>` si lleva a otra pantalla, `<button>` si hace algo). Valídalo en el W3C.

### Paso 3. Lleva los tokens al código

Convierte cada variable de Figma en una propiedad personalizada **con el mismo nombre** que su sintaxis de código: los primitivos con su valor, los semánticos apuntando a un primitivo y el modo oscuro con `light-dark()`. Incluye la tipografía (en `rem`), el espaciado, los radios y la elevación.

### Paso 4. Escribe la base

Escribe el reset, los estilos de las etiquetas y los objetos (contenedor, pila, cuadrícula).

### Paso 5. Construye los componentes

Construye los componentes de tu aplicación (botones, campos, tarjetas, navegación, textos, etiquetas, diálogos, avisos), cada uno en su parcial, con los mismos nombres que en Figma y con **todos sus estados**, incluido el foco del teclado.

Reúnelos en `componentes.html`, con todas sus variantes y estados en los dos modos.

### Paso 6. Maqueta las pantallas

Monta las pantallas solo con tus objetos y componentes, usando Flexbox y Grid. Si te falta algo, créalo como componente o como variante (y añádelo también en Figma).

Maqueta **mobile first**, con los breakpoints en `rem` y elegidos según los dispositivos de tus personas. Usa al menos una *container query* en un componente que aparezca en sitios de distinto ancho.

### Paso 7. Pon las imágenes

Sustituye los marcadores de los mockups por las imágenes reales: WebP para las fotos y SVG para los iconos, reducidas al tamaño de su hueco, con `width`, `height`, `alt` y `object-fit`. Usa imágenes propias, de bancos libres o con licencia abierta. La optimización, las versiones para cada ancho y las licencias se trabajan en la Órbita 4.

### Paso 8. Modo oscuro y movimiento

Revisa todas las pantallas en modo oscuro (puedes simularlo desde el panel Renderizado del inspector) y ajusta los colores que no funcionen. Las transiciones, cortas y con `prefers-reduced-motion`.

---

## Qué entregas

En el repositorio y en GitHub Pages: la aplicación, el código, `componentes.html`, las imágenes, el `CHANGELOG.md` con cada uso de IA y el `ORBITA3.md`.

La corrección empieza por el **`ORBITA3.md`**, enlazado desde el `README.md`. Lo que no esté en él ni se encuentre siguiendo sus indicaciones se considera no entregado. Usa esta plantilla:

````markdown
# Órbita 3: maquetación de [nombre de tu aplicación]

## Enlaces

| Qué | Enlace |
|---|---|
| Aplicación publicada | |
| Página de componentes | |
| Archivo de Figma (versión "Entrega Órbita 2") | |

## Decisiones

**Sass.** Qué usas además de los parciales, o por qué no lo has necesitado.

**Del sistema al código.** Qué token te faltaba o te sobraba, y qué cambiaste también en Figma.

**Componentes.** Cuáles tienes, con sus variantes y estados.

**Diseño adaptable.** Dónde están tus breakpoints y por qué, y qué componente usa la container query.

**Modo oscuro.** Qué colores ajustaste al comprobar las pantallas en oscuro.

## Uso de IA y pendientes

Cómo has usado la IA (el detalle, en el `CHANGELOG.md`) y qué ha quedado sin terminar.
````

**Cómo y cuándo.** Sube a la tarea de Moodle Centros el enlace a tu `ORBITA3.md`. Comprueba antes que la aplicación se abre en una ventana privada. La fecha estará en la tarea.

---

## Resultados de aprendizaje y criterios de evaluación

Los textos son los de la Orden de 16 de junio de 2011 (BOJA n.º 114).

| CE | Texto del criterio | Dónde se trabaja |
|---|---|---|
| RA1-a | Se ha reconocido la importancia de la comunicación visual y sus principios básicos. | Pasos 4 y 6 |
| RA1-b | Se han analizado y seleccionado los colores y tipografías adecuados para su visualización en pantalla. | Paso 3 |
| RA1-f | Se han creado y utilizado plantillas de diseño. | Pasos 4 y 5 |
| RA2-a | Se han reconocido las posibilidades de modificar las etiquetas HTML. | Pasos 2 y 4 |
| RA2-c | Se han definido y asociado estilos globales en hojas externas. | Pasos 1, 3 y 4 |
| RA2-d | Se han definido hojas de estilos alternativas. | Pasos 3 y 7 |
| RA2-e | Se han redefinido estilos. | Pasos 4 y 5 |
| RA2-f | Se han identificado las distintas propiedades de cada elemento. | Pasos 5 y 6 |
| RA2-g | Se han creado clases de estilos. | Paso 5 |

Las imágenes se ponen en este proyecto, pero su optimización, los formatos y las licencias (RA3 y RA4) se evalúan en la Órbita 4.

---

## Rúbrica

Cada fila es la parte de rúbrica de su CE, que se completa con una prueba teórica o práctica con el mismo peso.

| CE | Muy insuficiente (0–2,5) | Insuficiente (2,5–4,9) | Suficiente (5–6) | Notable (7–8) | Sobresaliente (9–10) |
|---|---|---|---|---|---|
| **RA1-a. Comunicación visual** | Las pantallas no se parecen a los mockups. | Se reconoce el diseño, pero la jerarquía o los espacios cambian mucho respecto a Figma. | Pantallas parecidas a los mockups, con espacios o alineaciones que no salen de la escala ni de la retícula. | Todas las pantallas, con sus imágenes reales, mantienen la jerarquía, el espaciado y la retícula de los mockups en los dos anchos, y las que no tenían mockup siguen el mismo sistema. | Las diferencias con Figma están justificadas y corregidas también en Figma, y la jerarquía se mantiene con la letra al 200 %. |
| **RA1-b. Colores y tipografías** | Colores y tipografías distintos de los del sistema. | Colores o tamaños escritos a mano, tamaños en `px` o textos por debajo del contraste mínimo. | Escala tipográfica y colores pasados a tokens, con algún valor suelto o sin comprobar el contraste en modo oscuro. | Todos los colores y textos salen de tokens, con tamaños en `rem`, alturas de línea sin unidad y el contraste comprobado en los dos modos. | Además, los títulos grandes usan tipografía fluida con `clamp()` y la fuente se carga solo con los pesos que se usan. |
| **RA1-f. Plantillas de diseño** | No hay componentes reutilizables. | Cada pantalla tiene sus propios estilos, o los elementos repetidos están escritos de nuevo en cada sitio. | Hay componentes y objetos, pero alguna pantalla tiene estilos propios, o la página de componentes está incompleta. | Todas las pantallas se construyen con la misma plantilla, los objetos y los componentes, y la página de componentes los muestra todos con sus variantes y estados en los dos modos. | Con los componentes que tienes se podría montar una pantalla nueva sin escribir CSS. |
| **RA2-a. Etiquetas HTML** | El HTML está hecho de `<div>` y `<span>`. | Faltan las zonas semánticas, hay saltos en los encabezados o botones hechos con enlaces o `<div>`. | HTML mayoritariamente semántico, con algún elemento mal elegido o errores en el validador. | HTML semántico y validado en todas las pantallas, con el elemento correcto para cada cosa y las etiquetas con estilo propio en la capa Elements. | La página se lee en orden y se entiende sin CSS, y los atributos de ARIA que usas sirven a la vez como selectores de estado. |
| **RA2-c. Estilos globales** | Estilos en línea o dentro de cada HTML. | Una hoja externa sin organizar, o tokens que no coinciden con las variables de Figma. | Tokens y capas de ITCSS presentes, con reglas en la capa equivocada o tokens con nombres distintos de los de Figma. | Hoja externa organizada en las capas de ITCSS, con los tokens en Settings y los mismos nombres que en Figma, y la prueba del color principal superada. | Las capas se garantizan con `@layer`, y los componentes usan tokens de componente para sus variantes. |
| **RA2-d. Hojas alternativas** | Solo hay modo claro. | El modo oscuro está incompleto o deja textos ilegibles. | Modo oscuro completo, con algún color sin ajustar. | Modo oscuro con `light-dark()` comprobado en todas las pantallas. | Además, la aplicación respeta `prefers-reduced-motion` y los colores del modo oscuro están ajustados (superficies elevadas más claras, sin negro puro). |
| **RA2-e. Redefinir estilos** | No hay reset ni estados. | Reset copiado sin usar, o componentes sin estados. | Reset y estados principales (hover y foco), con estados que faltan o `!important` para ganar a otras reglas. | Reset, estilos de las etiquetas y todos los estados de Figma en cada componente, con los modificadores de BEM y sin `!important`. | Los estados se escriben con pseudoclases y atributos de ARIA, sin clases de estado que sobren. |
| **RA2-f. Propiedades de los elementos** | La maquetación está hecha con posiciones absolutas o con alturas fijas. | Las pantallas se rompen al cambiar el ancho o el tamaño de la letra. | Flexbox y Grid bien usados en general, con alturas fijas o márgenes donde iría `gap`. | Cada pantalla se construye con Flexbox y Grid, sin alturas fijas, mobile first, con breakpoints en `rem` y al menos una container query. | En la auditoría oral sabes decir de qué token sale cada valor de cualquier componente y por qué cada breakpoint está donde está. |
| **RA2-g. Clases de estilos** | No hay clases o se da estilo con ids. | Nombres sin metodología, o selectores largos que dependen de la estructura del HTML. | BEM con inconsistencias o algún selector anidado de más. | Todos los componentes con BEM coherente, selectores de una sola clase y un fichero por componente. | Los nombres de los componentes, sus partes y sus variantes coinciden con los de Figma. |

### La auditoría oral

Como en las órbitas anteriores, te puedo preguntar por cualquier decisión de tu código. Vale cualquier respuesta que remita a tu sistema, a tus personas, a los apuntes, a las pautas de accesibilidad o a las WSG. Un componente sencillo que sabes defender vale más que uno espectacular que no sabes explicar.
