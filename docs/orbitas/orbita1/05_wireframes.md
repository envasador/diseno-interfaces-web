# Órbita 1 — Conocer a las personas

## 5. Del flujo al wireframe

Antes de construir una casa, alguien dibuja el plano: dónde va cada habitación, por dónde se entra y qué puerta comunica con qué pasillo. En ese momento nadie se preocupa todavía del color de los azulejos, porque primero hay que asegurarse de que la casa se puede recorrer bien. El **wireframe** cumple esa misma función en una aplicación: es un boceto sencillo de una pantalla, en el que se ve qué elementos tiene y dónde está colocado cada uno, sin colores ni imágenes.

Para dibujar los wireframes vas a usar los dos documentos de los apartados anteriores. El user flow te indica el orden, es decir, qué pantalla viene después de cuál para completar una tarea, y el sitemap te indica el contenido, es decir, qué pantallas existen, cómo se llaman y cómo se relacionan entre sí. Con los wireframes comprobarás que la estructura de cada pantalla permite hacer lo que el user flow promete, antes de dedicar tiempo a elegir tipografías o colores. Por eso los consideramos una **herramienta para tomar decisiones**, y así es como se evalúan.

### Cómo se combinan el user flow y el sitemap

Cada wireframe corresponde a una pantalla del sitemap, y el orden en que los dibujas y los conectas lo marca el user flow. El sitemap te da el nombre exacto de cada pantalla y te dice si es principal, secundaria o de sistema, lo que te orienta sobre cuánto detalle necesita, ya que una pantalla principal suele tener bastantes más elementos que un mensaje de confirmación o de error. El user flow, por su parte, te dice qué pantalla sigue a cuál dentro del happy path, y esa secuencia es la que luego podrás recorrer en el prototipo.

Trabajar con los dos documentos delante te protege de dos errores muy habituales: dibujar una pantalla que no está en el sitemap (con contenido que te inventas sobre la marcha) y conectar dos pantallas en un orden que el user flow no contempla (RA1-c).

### Qué pantallas hay que dibujar

Tienes que dibujar las pantallas que aparecen en el happy path de tu user flow y, además, las pantallas de error o de estado vacío (por ejemplo, la lista de reservas cuando todavía no has hecho ninguna) que hayas considerado importantes para tus personas. Si tu user flow tiene ocho pasos, necesitarás exactamente ocho wireframes.

Puede que en el sitemap haya pantallas que no aparecen en el user flow. Esas pantallas pueden esperar, y las dibujarás cuando algún flujo las necesite.

### Cómo se hace un wireframe de baja fidelidad en Figma Design

Los wireframes de esta órbita son de **baja fidelidad** (en inglés, *lo-fi*), lo que significa que se parecen poco al aspecto final de la aplicación y siguen unas convenciones muy concretas. Se dibujan en **escala de grises**, usando solo negro, blanco y un gris medio. No se usan tipografías reales: los textos largos se representan con líneas horizontales del mismo grosor, y los títulos solo se escriben si ayudan a entender qué hay en la pantalla. Las imágenes se representan con un rectángulo con una X dentro, y los botones, los campos de formulario y los iconos, con formas geométricas sencillas.

La idea es que cualquiera que mire el wireframe entienda para qué sirve cada elemento sin que nada le distraiga de lo que importa en esta fase, que es comprobar si la pantalla funciona.

En Figma Design trabajarás sobre un **frame** (el lienzo que representa la pantalla) del tamaño del dispositivo que usa tu persona. Lucía reserva desde un móvil Android, así que su frame mediría 360 × 800 píxeles, mientras que si tu persona principal usara un portátil trabajarías con un frame de 1280 × 800. Si tienes personas de los dos tipos, dibuja para los dos dispositivos desde el principio, porque la forma en que coloques los elementos ahora condicionará cómo se adapta tu web a cada pantalla en la Órbita 3.

Pon a cada frame el mismo nombre que tiene esa pantalla en el sitemap. Un user flow puede pasar dos veces por la misma pantalla (por ejemplo, por el "Detalle de reserva" antes de pagar y después de cancelar), y si usas siempre el mismo nombre quedará claro que se trata de la misma pantalla. Aunque parezca un detalle sin importancia, es lo que permite relacionar el sitemap, el user flow y los wireframes durante todo el módulo (RA1-a).

### Lo que todavía no se decide

Las tipografías, los colores, los espacios exactos entre elementos, los iconos y las imágenes son decisiones que tomarás en la Órbita 2. Si te das cuenta de que estás eligiendo un tono de azul, para, porque te estás adelantando a una fase que todavía no toca.

Es muy habitual sentir la tentación de usar colores para distinguir unos elementos de otros. Si necesitas diferenciar algo, usa el gris medio, y si aun así no se entiende para qué sirve ese elemento, el problema está en la estructura de la pantalla, que es donde tendrás que resolverlo. Cuando una pantalla no se entiende en escala de grises, añadirle color no la hará más clara.

### El prototipo navegable

Cuando tengas los wireframes de todo el happy path, conéctalos en Figma Design con **interacciones básicas**, de modo que al pulsar un botón se pase a la pantalla siguiente. No hace falta añadir animaciones ni transiciones, porque en esta fase solo necesitas que se pueda navegar.

Este prototipo sirve para comprobar si el user flow funciona cuando alguien lo recorre sin que nadie le explique nada. Aquí puedes repetir la prueba que se proponía en el primer apartado: si durante el test te sorprendes explicando para qué sirve un botón, has encontrado un problema de diseño que tendrás que resolver antes de pasar a diseñar el aspecto definitivo.

Puedes organizar la prueba en Lyssna enlazando directamente el prototipo de Figma Design, igual que hiciste con los referentes durante la investigación, aunque esta vez sobre tu propio trabajo. Con cuatro o cinco personas que se parezcan a tu persona principal tendrás suficiente para detectar los problemas más graves (RA1-c, RA6-a).
