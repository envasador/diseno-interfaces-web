# Órbita 1 — Conocer a las personas

## 4. Arquitectura de la información y sitemap

En el supermercado de tu barrio vas directo a la leche sin pensar. En uno que no conoces das tres vueltas, preguntas a alguien con chaleco y acabas encontrándola junto a los yogures, que tiene su lógica, pero no la tuya. Las estanterías eran las mismas. Lo que cambiaba era cómo estaban ordenadas y qué ponía en los carteles.

Eso es la **arquitectura de la información**: cómo se organiza y cómo se nombra el contenido de tu producto. Qué pantallas y funcionalidades tiene, cómo se agrupan y cómo se llama cada cosa. El **sitemap** es el diagrama que la representa: un árbol con la home en la raíz, un nodo por pantalla y líneas que marcan la jerarquía (RA1-c).

### Para qué sirve

A la persona usuaria le sirve para encontrar las cosas sin perderse. Cuando la estructura y los nombres son predecibles, sabe dónde buscar y qué va a encontrar antes de pulsar. A ti te sirve para decidir dónde vive cada pieza de tu MVP antes de dibujar una sola pantalla, que es cuando mover cosas de sitio sale gratis.

### Cómo se crea

Se construye en tres pasos, y siempre después de tener personas, MVP y user flow. La organización correcta depende de cómo piensan tus personas, el MVP marca qué contenido entra y el flujo te da una primera pista de cómo se conecta todo.

**1. Inventario.** Haz la lista completa de pantallas, funcionalidades y tipos de contenido de tu producto. Sale de dos fuentes: los referentes que analizaste al principio de la órbita (qué incluyen los productos parecidos al tuyo) y las funcionalidades de tu MVP. En la app del polideportivo saldrían cosas como el calendario de pistas, el detalle de una reserva, el pago, tus reservas, las tarifas, las normas de uso y tu perfil. Si algo no aparece en ninguna de las dos fuentes, pregúntate si de verdad hace falta.

**2. Agrupación.** Averigua cómo agrupa ese contenido la cabeza de tus usuarios con un **card sorting**: das a varias personas una tarjeta por cada elemento del inventario, les pides que las agrupen como les parezca natural y que le pongan nombre a cada grupo. Hazlo en FigJam, con notas adhesivas como tarjetas, con cuatro o cinco compañeros que encajen en tus perfiles. Prepárate para sorpresas. Tú quizá pondrías "Tarifas" junto a "Pagar", y a lo mejor cuatro de cinco lo meten con "Normas de uso", porque para ellos el precio es información y pagar es una acción. Los agrupamientos que se repiten entre participantes marcan la estructura que debería tener tu producto.

**3. Mapeo.** Convierte los grupos en el sitemap: un nodo por pantalla, la home como raíz y líneas que marcan la jerarquía. Distingue tres tipos de nodo: **principales** (se llega desde la navegación), **secundarios** (se llega desde otras pantallas) y **de sistema** (inicio de sesión, errores, confirmaciones).

![Ejemplo de sitemap con tres tipos de nodo y flujo superpuesto](img/orbita1_04_esquema_sitemap.svg)

### Dos decisiones al construirlo

**Amplitud o profundidad.** Una estructura amplia pone muchas opciones en el primer nivel: todo queda a pocos clics, pero el menú inicial puede abrumar. Una estructura profunda pone pocas opciones de entrada y más niveles: cada pantalla es sencilla, pero llegar al contenido cuesta más pasos. Para este módulo hay una regla: las funcionalidades de tu MVP tienen que alcanzarse en **tres niveles de navegación como máximo** (RA6-c).

**Cómo se llama cada sección.** Usa las palabras que tus personas usaron en las entrevistas para hablar de sus tareas. Un nombre funciona cuando la persona adivina qué va a encontrar antes de pulsar. "Mis reservas" cumple. "Gestión de actividad" obliga a pulsar para averiguarlo, y mucha gente no pulsa. Cuanto más convencional es la navegación, mejor funciona (RA6-h).

### Antes de darlo por terminado

Comprueba el sitemap dos veces. Primero contra tu MVP: todo lo que está dentro tiene una pantalla donde vivir, y nada de lo que dejaste fuera se ha colado por la puerta de atrás. Después contra tu user flow: recórrelo sobre el sitemap y comprueba que cada paso encuentra su pantalla, sin huecos y con los mismos nombres en los dos sitios.

Si usas IA para proponer una estructura inicial, ten presente que te va a dar la arquitectura más habitual para ese tipo de producto. Es un punto de partida razonable, y tu card sorting y tus personas tienen que corregirlo. La distancia entre esa estructura genérica y tu sitemap final es la prueba de que hubo un proceso de diseño detrás (RA1-c).
