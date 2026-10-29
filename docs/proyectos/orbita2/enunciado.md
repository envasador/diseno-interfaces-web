# Proyecto de la Órbita 2: Diseñar para que se entienda

**Horas:** unas 15 · **Semanas:** de la 5 a la 7 · **RA:** RA1 y RA2 · **Trabajo:** individual

## El encargo

En la Órbita 1 averiguaste para quién es tu aplicación, qué tiene que resolver y cómo se recorre, y lo dibujaste todo en escala de grises. Ahora toca decidir su aspecto: los colores, las tipografías, los espacios entre elementos, los iconos y la forma de los botones y las tarjetas. Es la fase en la que una aplicación que ya funciona empieza a entenderse a primera vista.

Lo vas a hacer como se trabaja en cualquier equipo de producto. Antes de pintar ninguna pantalla, vas a construir en Figma un **sistema visual**: un conjunto de decisiones con nombre (los **tokens**) guardadas como variables, con un modo claro y otro oscuro. Cuando el sistema esté completo, lo aplicarás a todos tus wireframes de una vez para convertirlos en **mockups**, y escribirás una **guía de estilo** que explique el motivo de cada decisión. Si el sistema está bien hecho, cambiar el color principal de tu aplicación será cuestión de modificar una sola variable.

Cada decisión visual tiene que salir de tu proyecto. Un azul o un tamaño de letra se eligen porque ayudan a tus personas a conseguir lo que necesitan en el contexto en el que usan la aplicación (con el móvil en una mano, con poca luz, con la letra aumentada o con una conexión lenta). Si una decisión solo se puede justificar con "me gusta más", todavía no está tomada.

En los apuntes de la órbita sigue el ejemplo del polideportivo municipal, con Lucía y Manuel. Úsalo como referencia para entender qué se pide en cada paso, pero tu sistema tiene que salir de tus propias personas y de tu propio brief.

Lo que construyas aquí es la base del resto del curso: en la Órbita 3 convertirás tus tokens en propiedades personalizadas de CSS y maquetarás tus mockups, en la Órbita 4 comprobarás con ellos la accesibilidad y en la Órbita 6 tu guía de estilo se convertirá en el `DESIGN.md` del proyecto.

!!! warning "Antes de empezar: solicita el plan de Educación de Figma"
    El modo oscuro, que es obligatorio en este proyecto, se construye con los **modos** de las variables de Figma, y esa función no está disponible en el plan gratuito. Solicita el plan de Educación desde la página de Figma for Education con tu correo del centro el primer día de la órbita, porque la verificación puede tardar unos días.

---

## Qué tienes que hacer

El proyecto se organiza en ocho pasos, los mismos de la [hoja de ruta](../../orbitas/orbita2/00_hoja_de_ruta.md). Respeta el orden, porque cada paso utiliza las decisiones del anterior: no puedes comprobar el contraste de tus textos sin haber elegido antes los colores, ni crear las variables sin saber qué valores van a tener. En cada paso tienes enlazado el apartado de los apuntes donde se explica cómo hacerlo.

Trabajarás en el mismo archivo de Figma Design de la Órbita 1 y en el mismo repositorio de GitHub, con el mismo `CHANGELOG.md`. Cada vez que uses una IA, anotarás qué le pediste, qué te devolvió, qué conservaste y qué cambiaste.

### Paso 1. Prepara el archivo y haz el inventario de decisiones

Ordena el archivo de Figma en cinco páginas: **portada**, **guía de estilo**, **componentes**, **wireframes** y **mockups**. Los wireframes de la Órbita 1 se quedan tal como los entregaste, porque son la prueba de cómo ha evolucionado tu proyecto.

Después coge uno de tus wireframes y haz una lista con todas las decisiones visuales que necesitas para convertirlo en una pantalla terminada (el color del fondo, el de los textos, el del botón principal, el tamaño del título, el espacio entre tarjetas...). Junto a cada una, escribe el nombre del **token semántico** que le pondrías, en inglés y siguiendo la convención de los apuntes (`color/surface`, `color/on-surface`, `color/primary`...). Deja esta lista en la página de wireframes, al lado del frame que has analizado.

Apuntes: [1. Por qué los tokens antes que las pantallas](../../orbitas/orbita2/01_tokens_antes_que_pantallas.md).

### Paso 2. Replantea la jerarquía y rediseña tus wireframes

Tus wireframes de la Órbita 1 los dibujaste pensando en la estructura. Ahora, con lo que has visto sobre percepción visual, jerarquía y patrones de interfaz, toca mirarlos otra vez con ojos de diseñador y **rediseñar lo que haga falta** antes de ponerles color.

Duplica las pantallas del happy path en una sección nueva de la página de wireframes llamada "Wireframes rediseñados" (los originales se quedan como estaban) y repásalas una a una con estas preguntas:

- ¿Qué es lo primero que tiene que ver tu persona en esta pantalla? ¿Es lo que más destaca?
- ¿Hay un único botón principal, y dice lo que va a pasar ("Reservar pista" en lugar de "Aceptar")?
- ¿Están juntos los elementos que van juntos y separados los que no? Una etiqueta tiene que estar más cerca de su campo que del campo anterior.
- ¿El orden de la pantalla sigue el orden en que tu persona toma las decisiones?
- ¿Sobra algo que no ayuda a la tarea? ¿Usas un patrón que tu persona ya conoce, o uno que la obliga a pensar?

Cambia en la copia todo lo que no pase estas preguntas: reordena, agrupa, quita, cambia un patrón por otro. Sigue trabajando en escala de grises. Junto a cada pantalla que cambies, escribe una nota breve con **qué has cambiado y por qué**, apoyada en tus personas o en un principio de los apuntes. Si una pantalla no necesita cambios, indícalo también.

Si quieres comparar tu rediseño con otras propuestas, puedes usar **Google Stitch** para generar versiones alternativas de tus pantallas a partir de los wireframes. Úsalo como material de comparación: anota qué te parece acertado para tus personas y qué no, y lleva a tu rediseño solo lo que sepas justificar. **El rediseño lo dibujas tú, y las pantallas de Stitch no pueden usarse como wireframes ni como mockups**, ni importadas en Figma ni redibujadas tal cual. Si lo usas, guarda el enlace al proyecto de Stitch junto a tus wireframes rediseñados, entrégalo con el resto de enlaces y anótalo en el `CHANGELOG.md` como cualquier otro uso de IA.

Los mockups del paso 8 se construyen a partir de estos wireframes rediseñados.

Apuntes: [2. Percepción visual y jerarquía](../../orbitas/orbita2/02_percepcion_visual.md) y [7. Patrones de interfaz](../../orbitas/orbita2/07_patrones_interfaz.md).

### Paso 3. Construye el sistema de color

Elige el color principal, el secundario y los neutros a partir de tu brief, de tus personas y de lo que viste en los referentes. Convierte cada uno en una **escala** del 50 al 900 y añade los colores de estado (error, éxito y advertencia). Estos son tus **tokens primitivos**.

Con las escalas hechas, decide tus **tokens semánticos** (`primary`, `on-primary`, `surface`, `on-surface`, `error`...) y a qué tono de las escalas apunta cada uno en el modo claro y en el oscuro. Recoge en una tabla todas las parejas de fondo y texto con su contraste medido con Stark en los dos modos. Ningún texto normal puede bajar de **4,5:1**, y los bordes de los campos y los iconos tienen que llegar a **3:1**.

Por último, convierte una captura de la paleta aplicada a tu wireframe a escala de grises y comprueba qué información depende solo del color. Ningún estado (un error, una opción seleccionada, una pista ocupada) puede distinguirse únicamente por su color.

Apuntes: [3. Color: de la intuición al sistema](../../orbitas/orbita2/03_color.md).

### Paso 4. Elige la tipografía y define la escala

Elige **una o dos familias de Google Fonts** pensando en la legibilidad en pantalla y en el contexto de uso de tus personas. Usa solo los pesos que de verdad necesites (por ejemplo, el normal y la negrita), porque cada peso es un archivo más que el navegador tiene que descargar.

Después construye una **escala tipográfica** de entre seis y ocho niveles, cada uno con su nombre (`display`, `heading-1`, `body`, `caption`...), su tamaño, su altura de línea y su peso. Pruébala con un texto real de tu aplicación y simula la letra al 200 % duplicando los tamaños, para comprobar que nada se corta ni se solapa.

Para terminar, relaciona cada nivel con la **etiqueta HTML** a la que se aplicará cuando maquetes (`h1`, `h2`, `p`, `label`, `button`, `a`...). El navegador ya le da a cada etiqueta un aspecto por defecto (los `h1` grandes y en negrita, los enlaces azules y subrayados), y tu escala es la que va a sustituir ese aspecto en la Órbita 3. Recoge esta correspondencia en una tabla de tres columnas (nivel, etiqueta HTML y uso), teniendo en cuenta que la etiqueta la decide el significado del texto y el nivel decide su aspecto: un título de sección puede ser un `h2` aunque visualmente use el nivel `heading-3`.

Apuntes: [4. Tipografía: legibilidad, escala y jerarquía](../../orbitas/orbita2/04_tipografia.md).

### Paso 5. Fija el espaciado, la retícula, los radios y la elevación

Define una **escala de espaciado** sobre una cuadrícula de 4 u 8 píxeles, la **retícula** de columnas del dispositivo de tu persona principal (y de los demás tamaños de pantalla si tus personas los usan), una escala de **radios** y entre dos y cuatro niveles de **elevación**.

Coloca la retícula sobre tu wireframe más complejo y comprueba la alineación y las separaciones. Mide los elementos que se pueden pulsar: en el móvil tienen que llegar a **44 × 44 píxeles**.

Apuntes: [5. Espaciado, retícula y composición](../../orbitas/orbita2/05_espaciado_reticula.md).

### Paso 6. Elige los iconos y revisa tus componentes

Elige **una sola librería de iconos** que tenga todos los que necesitas, anota su licencia y decide los tamaños que vas a usar a partir de tu escala. Convierte cada icono en un componente de Figma. Salvo los de significado universal, todos llevan una etiqueta de texto.

Después haz el inventario de los **componentes** de tus wireframes: a qué nivel de Atomic Design pertenece cada uno (átomo, molécula u organismo), qué patrón conocido sigue y qué estados necesita (normal, *hover*, foco, pulsado, desactivado y error, según el caso). Recorre tu user flow buscando patrones engañosos, como una opción preseleccionada que beneficia a la empresa o un botón de cancelar que se ve menos que el de aceptar, y si encuentras alguno, anota cómo lo has corregido.

Apuntes: [6. Iconos e imágenes](../../orbitas/orbita2/06_iconos_imagenes.md) (la parte de iconos) y [7. Patrones de interfaz](../../orbitas/orbita2/07_patrones_interfaz.md).

### Paso 7. Monta el sistema en Figma: variables, estilos y componentes

Este es el paso en el que más se nota si dominas Figma, y es una parte central del proyecto. Todo lo que hagas a partir de aquí tiene que salir del sistema, sin valores escritos a mano.

**Variables.** Pasa todas tus decisiones a variables, en dos colecciones:

- Una colección de **primitivos**, con un solo modo y las variables ocultas al publicar.
- Una colección de **semánticos**, con los modos **claro** y **oscuro**, en la que todos los valores son alias de los primitivos.

Configura en cada variable semántica el **ámbito** (para que un color de texto no aparezca al elegir un fondo), una **descripción** que explique cuándo se usa y la **sintaxis de código** con el nombre que tendrá en CSS (por ejemplo, `var(--color-primary)`). Ese nombre es el que escribirás en la Órbita 3, así que piénsalo bien.

**Estilos.** Crea los estilos de texto de tu escala vinculados a las variables tipográficas, los estilos de efecto de la elevación y los estilos de retícula.

**Componentes.** Rehaz los componentes de tus wireframes (botones, campos de formulario, tarjetas, cabecera y navegación) para que estén construidos así:

- Con **Auto layout**, de modo que crezcan con su contenido (un botón con una etiqueta más larga se ensancha solo).
- Con tus **variables** en los colores, el relleno, el espacio entre elementos y el radio de las esquinas.
- Con **propiedades de componente**: una de texto para la etiqueta, una de mostrar u ocultar para el icono y una de cambio de instancia para elegir qué icono lleva.
- Con **variantes** para los estados. Como mínimo, el botón principal (normal, *hover*, foco, pulsado y desactivado) y los campos de formulario (normal, foco, error y desactivado).

Ordénalos en la página de componentes por niveles de Atomic Design.

Termina colocando un botón y una tarjeta en un frame y cambiando el modo a oscuro. Si algo no cambia, en algún sitio hay un valor escrito a mano que tienes que sustituir por una variable.

Ayuda: [variables en Figma](../../orbitas/orbita2/sesiones/ayuda_variables_figma.md) y [Auto layout, responsive y variables](../../orbitas/orbita2/sesiones/ayuda_autolayout_figma.md).

### Paso 8. Construye los mockups, el prototipo y la guía de estilo

Duplica tus **wireframes rediseñados** en la página de mockups y conviértelos en **mockups** con tus componentes, estilos y variables, pantalla a pantalla y siguiendo el orden del user flow. Tienen que estar **todas las pantallas del happy path** (las de error y estado vacío se quedan como wireframes por ahora), con textos reales en lugar de textos de relleno. Si alguna pantalla lleva fotos o ilustraciones, deja por ahora el marcador del wireframe; las imágenes las trabajarás en la Órbita 3. Como apoyo, en los artículos de [diseño de interfaces de UI From Mars](https://uifrommars.com/categoria/diseno-ui/) tienes muchos ejemplos de componentes y pantallas bien resueltos.

Cada pantalla se construye entera con **Auto layout**, igual que los componentes:

- La pantalla, sus secciones y las tarjetas ocupan el ancho disponible (**Fill**), y los botones e iconos se ajustan a su contenido (**Hug**) o tienen su tamaño fijo.
- Todos los espacios (*gap* y relleno) salen de tus variables de espaciado.
- No hay ningún elemento colocado a mano. Si cambias un texto o añades una tarjeta, el resto se recoloca solo.

Para comprobar que tus pantallas son **responsive**, duplica la pantalla principal y cámbiale el ancho al otro tipo de dispositivo: si tu persona principal usa el móvil (360 × 800), a escritorio (1280 × 800), y al revés. Con un buen Auto layout, solo tendrás que hacer pequeños ajustes (pasar unas tarjetas a dos columnas con *wrap* o poner un ancho máximo al texto), sin redibujar nada. Esa segunda versión forma parte del entregable.

Haz además una versión en **modo oscuro** de la pantalla principal y de al menos otra pantalla del recorrido, aplicando el modo desde el panel derecho y colocándola junto a la clara con el mismo nombre.

Cuando te falte un token o te sobre un nivel tipográfico, corrígelo en el sistema (nunca en la pantalla) y anótalo, porque es una decisión que tendrás que explicar.

Con todas las pantallas terminadas, revísalas:

- **Jerarquía.** Compara cada mockup con su wireframe rediseñado. El color y la tipografía tienen que reforzar lo que decidiste en el paso 2.
- **Contraste.** Comprueba con Stark los textos y los iconos, en los dos modos.
- **Color.** Ningún estado se distingue solo por el color.
- **Letra al 200 %.** Duplica la pantalla más importante con todos los textos al doble: nada se corta ni se solapa.
- **Objetivos táctiles.** Todo lo que se pulsa en el móvil mide al menos 44 × 44 píxeles.
- **Valores sueltos.** Todos los colores, tamaños y espacios vienen de una variable o de un estilo.

Enlaza las pantallas en un **prototipo** que recorra el happy path completo. Si añades transiciones, que sean breves, tal como pide el criterio 2.17 de las **Web Sustainability Guidelines (WSG)** del W3C. Si quieres, haz el **test de los cinco segundos** en Lyssna con la pantalla principal (es optativo) y deja los resultados en la página de mockups.

Por último, escribe la **guía de estilo** en su página del archivo, con cuatro de las secciones del apartado 8: **color**, **tipografía**, **componentes** y **decisiones que afectan al peso**. El resto (principios, espaciado y retícula, radio y elevación, iconos e imágenes) lo completarás en la Órbita 6, cuando conviertas la guía en el `DESIGN.md` del proyecto, aunque los motivos de esas decisiones te los puedo preguntar igualmente en la auditoría oral. En la sección de tipografía incluye la tabla de correspondencia con las etiquetas HTML del paso 4. Lo que se evalúa de la guía son los **motivos**: junto a cada decisión importante tiene que haber una frase que la justifique con tus personas, con las pautas de accesibilidad, con las WSG o con los principios de los apuntes.

Antes de entregar, haz las dos pruebas de terminado. Cambia `color/primary` para que apunte a otro color de tus primitivos y comprueba que cambia en todas las pantallas a la vez (después deshaz el cambio). Después cambia todos los mockups a modo oscuro y recórrelos para comprobar que nada desaparece contra el fondo. No tienes que entregar el resto de pantallas en oscuro, pero si algo falla al cambiar de modo, el problema está en tus variables y tienes que corregirlo.

Cuando lo tengas todo, rellena el resumen de la entrega en el archivo `ORBITA2.md` de tu repositorio, con la plantilla que tienes en el apartado "Qué entregas".

Apuntes: [8. Del wireframe al mockup: guía de estilo y entregable](../../orbitas/orbita2/08_mockups_entregable.md).

---

## Qué entregas

Casi todo el entregable está en el archivo de Figma Design del proyecto. En el repositorio están el resumen de la entrega (`ORBITA2.md`) y el `CHANGELOG.md`.

| Documento | Dónde | Qué tiene que incluir |
|---|---|---|
| **Inventario y wireframes rediseñados** | Figma Design (página de wireframes) | La lista de decisiones con sus tokens, los wireframes de la Órbita 1 sin modificar y, al lado, los rediseñados con una nota de qué cambia y por qué. El enlace al proyecto de Google Stitch, si lo has usado |
| **Variables** | Figma Design | Colección de primitivos y colección de semánticos con los modos claro y oscuro, con ámbito, descripción y sintaxis de código |
| **Estilos** | Figma Design | Estilos de texto de la escala tipográfica, estilos de efecto de la elevación y estilos de retícula |
| **Componentes** | Figma Design (página de componentes) | Iconos y componentes con Auto layout, variables, propiedades y variantes de estado, ordenados por niveles de Atomic Design |
| **Mockups y prototipo** | Figma Design (página de mockups) | Todas las pantallas del happy path en modo claro, construidas con Auto layout y enlazadas en un prototipo; la pantalla principal en un segundo ancho; y la pantalla principal y al menos otra en modo oscuro |
| **Guía de estilo** | Figma Design (página de guía de estilo) | Las secciones de color, tipografía, componentes y decisiones que afectan al peso, con el motivo de cada decisión, la tabla de contraste en los dos modos y la correspondencia entre niveles tipográficos y etiquetas HTML |
| **Resumen de la entrega** | GitHub (`ORBITA2.md`) | La plantilla del final de este apartado rellena: enlaces, dónde está cada cosa en Figma, lista de comprobación, resumen de decisiones, uso de IA y lo que ha quedado pendiente |
| **CHANGELOG** | GitHub (`CHANGELOG.md`) | Cada uso de IA de la órbita, con lo que se pidió, lo que devolvió, lo que se conservó y lo que se cambió |

### Lo que tiene que demostrar tu archivo de Figma

Una parte importante de la nota depende de cómo uses Figma. Antes de entregar, comprueba que tu archivo cumple esta lista:

1. **Variables** en dos colecciones (primitivos y semánticos), con alias, los modos claro y oscuro, ámbito, descripción y sintaxis de código.
2. **Estilos** de texto, efecto y retícula vinculados a las variables.
3. **Componentes** construidos con Auto layout y variables, con propiedades (texto, mostrar u ocultar icono, cambiar icono) y variantes de estado.
4. **Mockups** construidos enteros con Auto layout, con *Fill* y *Hug* bien usados y todos los espacios sacados de variables. Nada colocado a mano.
5. **Responsive**: la pantalla principal en un segundo ancho, hecha con los mismos componentes y sin redibujarla.
6. **Modo oscuro** aplicado con el selector de modo, sin duplicar componentes.
7. **Prototipo** que recorre el happy path completo.

### El resumen de la entrega: `ORBITA2.md`

Además del archivo de Figma, en la raíz de tu repositorio tiene que haber un archivo `ORBITA2.md` con el resumen de todo lo que has hecho en la órbita. **La corrección empieza por este documento**: en él dices dónde está cada cosa en Figma, qué has decidido y por qué, y qué te ha quedado pendiente. Lo que no aparezca en el resumen ni se encuentre en el archivo de Figma siguiendo sus indicaciones se considera no entregado. Enlázalo desde el `README.md`, igual que el `BRIEF.md`.

Copia esta plantilla y rellénala. Las respuestas tienen que ser tuyas y breves: unas pocas frases en cada apartado bastan, siempre que digan algo concreto de tu proyecto.

````markdown
# Órbita 2: sistema visual de [nombre de tu aplicación]

## Enlaces

| Qué | Enlace |
|---|---|
| Archivo de Figma (versión "Entrega Órbita 2") | |
| Prototipo (enlace que empieza por `figma.com/proto/`) | |
| Proyecto de Google Stitch (solo si lo has usado) | |

## Dónde está cada cosa en Figma

| Entregable | Página y sección del archivo |
|---|---|
| Inventario de decisiones | |
| Wireframes rediseñados con sus notas | |
| Componentes | |
| Mockups del happy path | |
| Pantalla principal en el segundo ancho | |
| Pantallas en modo oscuro | |
| Guía de estilo | |

## Lista de comprobación de Figma

- [ ] Variables en dos colecciones (primitivos y semánticos), con alias, modos claro y oscuro, ámbito, descripción y sintaxis de código.
- [ ] Estilos de texto, efecto y retícula vinculados a las variables.
- [ ] Componentes con Auto layout, variables, propiedades y variantes de estado.
- [ ] Mockups construidos enteros con Auto layout y espacios sacados de variables.
- [ ] Pantalla principal en un segundo ancho, con los mismos componentes.
- [ ] Modo oscuro aplicado con el selector de modo.
- [ ] Prototipo que recorre el happy path completo.
- [ ] Prueba 1 superada: al cambiar `color/primary`, cambian todas las pantallas a la vez.
- [ ] Prueba 2 superada: con todos los mockups en modo oscuro, nada desaparece contra el fondo.

## Resumen de decisiones

### Rediseño de los wireframes
Qué pantallas has cambiado, cuál es el cambio más importante y por qué (con tu persona o un principio de los apuntes).

### Color
Color principal y secundario, y por qué los elegiste. Pareja de texto y fondo con el contraste más bajo de tu sistema y su valor, en cada modo.

### Tipografía
Familias y pesos que usas, y por qué esas familias para tus personas.

### Espaciado y retícula
Base de la escala (4 u 8 píxeles), columnas, medianil y margen de la retícula del dispositivo de tu persona principal.

### Componentes
Lista de componentes con sus variantes de estado.

### Responsive y modo oscuro
Qué tuviste que ajustar al pasar la pantalla principal al segundo ancho, y qué corregiste en tus variables al pasar los mockups a modo oscuro.

## Uso de IA
Resumen en dos o tres frases de cómo has usado la IA en la órbita (o "no he usado ninguna herramienta de IA"). El detalle está en el [CHANGELOG.md](CHANGELOG.md).

## Lo que ha quedado pendiente
Lo que no has terminado o sabes que no funciona del todo, y por qué. Si está todo terminado, indícalo.
````

### Entrega y plazo

**Cómo se entrega.** En la tarea de Moodle Centros sube el enlace al archivo `ORBITA2.md` de tu repositorio de GitHub. Desde él tienen que poder abrirse el archivo de Figma Design (con permiso de visualización), el prototipo y, si lo has usado, tu proyecto de Google Stitch.

El enlace del prototipo es distinto del enlace del archivo. Para conseguirlo, abre el prototipo con el botón de reproducir (▶) y copia el enlace desde **Compartir prototipo**: tiene que empezar por `figma.com/proto/`. Configura el acceso para que cualquiera con el enlace pueda verlo y elige como punto de partida la primera pantalla de tu happy path. Así puedo recorrerlo de principio a fin sin entrar en tu archivo, igual que lo haría una persona usuaria. Antes de subirlo, abre cada enlace en una ventana privada del navegador y comprueba que se ve sin iniciar sesión. Como vas a seguir trabajando en el archivo en la Órbita 3, guarda una versión con nombre en el historial de versiones de Figma ("Entrega Órbita 2"), que será la que se evalúe.

**Cómo se presenta.** El archivo tiene que poder recorrerse sin que estés tú para explicarlo. Pon en la portada el nombre del proyecto, tu nombre y la fecha de la entrega, ordena cada página en secciones con título y usa los mismos nombres de pantalla que en el sitemap y en los wireframes.

**Cuándo.** Al final de la semana 7. La fecha y la hora exactas están en la tarea de Moodle Centros.

---

## Resultados de aprendizaje y criterios de evaluación

Este proyecto trabaja el RA1 y el RA2. Los textos de los resultados de aprendizaje y de los criterios son los que fija la Orden de 16 de junio de 2011 (BOJA n.º 114), sin modificar.

**RA1. Planifica la creación de una interfaz web valorando y aplicando especificaciones de diseño.**

| CE | Texto del criterio | Dónde se trabaja en el proyecto |
|---|---|---|
| RA1-a | Se ha reconocido la importancia de la comunicación visual y sus principios básicos. | Rediseño de los wireframes (paso 2), espaciado y retícula (paso 5) y composición de los mockups (paso 8) |
| RA1-b | Se han analizado y seleccionado los colores y tipografías adecuados para su visualización en pantalla. | Sistema de color con su tabla de contraste (paso 3) y familias y escala tipográfica (paso 4) |
| RA1-d | Se ha valorado la importancia de definir y aplicar la guía de estilo en el desarrollo de una aplicación web. | Guía de estilo y pruebas de terminado (paso 8) |
| RA1-f | Se han creado y utilizado plantillas de diseño. | Variables, estilos y componentes (paso 7), y mockups responsive, modo oscuro y prototipo (paso 8) |

**RA2. Crea interfaces web homogéneos definiendo y aplicando estilos.**

| CE | Texto del criterio | Dónde se trabaja en el proyecto |
|---|---|---|
| RA2-a | Se han reconocido las posibilidades de modificar las etiquetas HTML. | Tabla de niveles tipográficos y etiquetas HTML (paso 4) y sintaxis de código de las variables (paso 7) |

---

## Rúbrica

La rúbrica tiene una fila por cada criterio de evaluación, y la nota de cada fila es la parte de rúbrica de ese CE. Tal como recoge la programación del módulo, cada CE se completa con una prueba teórica (RA1-a, RA1-b, RA1-d y RA2-a) o práctica (RA1-f), y los dos instrumentos cuentan lo mismo.

| CE | Muy insuficiente (0–2,5) | Insuficiente (2,5–4,9) | Suficiente (5–6) | Notable (7–8) | Sobresaliente (9–10) |
|---|---|---|---|---|---|
| **RA1-a. Comunicación visual** | No hay wireframes rediseñados ni escala de espaciado. | Los wireframes no se han replanteado, o los cambios no se explican. Los espacios están puestos a ojo. | Hay rediseño con notas, pero con pocos cambios o sin relación con las personas. La retícula y el espaciado se aplican a medias. | Rediseño del happy path con un motivo para cada cambio, un solo botón principal por pantalla, elementos relacionados agrupados, retícula aplicada y objetivos táctiles de 44 × 44 píxeles. | Los mockups mantienen la jerarquía del rediseño y la refuerzan con el color y la tipografía. Cada cambio se defiende con una persona y un principio de los apuntes. |
| **RA1-b. Colores y tipografías** | No hay paleta ni escala tipográfica. | Colores sueltos sin escalas, textos por debajo de 4,5:1, o más de dos familias. | Escalas de color y escala tipográfica hechas, pero falta la tabla de contraste o la prueba al 200 %. | Escalas del 50 al 900 con colores de estado, tokens semánticos en los dos modos con todo el contraste por encima del mínimo, una o dos familias de Google Fonts con los pesos justos, y escala de seis a ocho niveles probada al 200 %. | Cada color y cada familia se justifican con el brief o las personas, y ningún nivel de la escala sobra. |
| **RA1-d. Guía de estilo** | No hay guía de estilo. | La guía solo muestra valores, sin motivos. | Están las cuatro secciones, pero con motivos genéricos ("queda bien", "es moderno"). | Las cuatro secciones con un motivo comprobable para cada decisión importante, y las dos pruebas de terminado superadas. | Alguien que no conoce el proyecto podría aplicar el sistema solo con la guía: los componentes tienen ejemplos de uso correcto e incorrecto y se explica también lo que se descartó. |
| **RA1-f. Plantillas de diseño (uso de Figma)** | No hay variables ni componentes. | Mockups hechos con valores a mano o sin Auto layout, o sin modo oscuro. | Hay variables, componentes y Auto layout, pero con fallos: espacios sin variables, anchos fijos que rompen la pantalla, componentes sin variantes, falta la versión en segundo ancho o el prototipo se rompe. | Se cumplen los siete puntos de la lista "Lo que tiene que demostrar tu archivo de Figma". | Además, el responsive se resuelve con una colección de modos para cada tamaño de pantalla, o la pantalla principal funciona en un tercer ancho, y los componentes tienen propiedades pensadas para reutilizarse en cualquier pantalla. |
| **RA2-a. Etiquetas HTML** | No hay tabla de etiquetas. | La tabla está incompleta, o las etiquetas se eligen por el tamaño del texto. | Tabla completa, pero sin el uso de cada nivel, o variables sin sintaxis de código. | Tabla con nivel, etiqueta y uso, que separa lo que significa un texto de cómo se ve, y sintaxis de código en todas las variables semánticas. | Se explica qué aspecto da el navegador por defecto a cada etiqueta y cómo lo cambiará tu sistema en CSS. |

Hay tres condiciones que afectan a toda la rúbrica:

- **El `ORBITA2.md` es el punto de partida de la corrección.** Si falta, o si no dice dónde está cada cosa, lo que no se encuentre en el archivo de Figma se considera no entregado.
- **La redacción y el orden cuentan.** Si una parte del archivo está tan mal redactada o tan desordenada que no se entiende sin que la expliques tú, su criterio no pasa de Suficiente.
- **El sistema tiene que estar en Figma.** Si los mockups usan colores, tamaños o espacios escritos a mano, o si algún mockup reproduce una pantalla generada con Google Stitch, RA1-f no pasa de Insuficiente. Lo mismo ocurre si has usado Stitch y no has entregado el enlace.
- **Cada uso de IA tiene que estar en el `CHANGELOG.md`**, con lo que pediste, lo que te devolvió, lo que conservaste y lo que cambiaste. Si una decisión tiene un uso de IA sin anotar, el criterio al que pertenece se queda en Insuficiente.

Si no has usado ninguna IA durante la órbita, indícalo en el `CHANGELOG.md` con una entrada al cerrarla:

```markdown
## AAAA-MM-DD · Cierre de la Órbita 2

No he usado ninguna herramienta de IA durante esta órbita.
```

### La auditoría de decisión oral

Igual que en la Órbita 1, cada fila de la rúbrica se confirma en la **auditoría de decisión oral**. Te puedo preguntar, durante la órbita o más adelante, por qué tu color de error es ese tono, por qué el título de la pantalla de reserva usa ese nivel de la escala, qué pesos tipográficos usas o por qué tu barra de navegación tiene esos destinos. Una respuesta válida remite a tus personas, a tu brief, a tu user flow, a las pautas de accesibilidad, a las WSG o a los principios de percepción. Respuestas como "es lo que se lleva" o "me lo sugirió la IA" indican que esa decisión todavía no es tuya, y en ese caso el criterio correspondiente se queda en Insuficiente, por bien hecho que esté el archivo.

Si tu guía de estilo recoge los motivos, en la auditoría solo tendrás que contarme lo que ya escribiste. Tenlo en cuenta al repartir el tiempo antes de la entrega: un mockup con algún detalle por pulir, pero con un sistema que sabes defender, vale más que unas pantallas impecables que no sabes explicar.
