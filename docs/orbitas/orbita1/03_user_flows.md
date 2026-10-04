# Órbita 1 — Conocer a las personas

## 3. User flows: del MVP al recorrido completo

Un **user flow** (flujo de usuario) es un diagrama que muestra el camino que sigue una persona para conseguir algo dentro de tu aplicación, con todos los pasos, decisiones y pantallas por los que pasa desde que aparece la necesidad hasta que la resuelve o abandona. Antes de dibujar ninguno, necesitas tener claro qué va a hacer tu aplicación en su primera versión, y para eso sirve el MVP.

### El MVP: qué entra en la primera versión

El **MVP** (producto mínimo viable) es la versión más pequeña de tu aplicación que ya resuelve de verdad el problema de tu persona principal. Hace pocas cosas, pero las hace completas. Una comparación que se usa mucho es la de un coche: si el producto final fuera un coche, el MVP sería un patinete, porque aunque es mucho más sencillo ya permite ir de un sitio a otro, mientras que una rueda suelta, por muy bien fabricada que esté, no le sirve a nadie para desplazarse.

En cuanto empiezas a pensar en tu aplicación del polideportivo, se te ocurren muchísimas ideas: un chat para el grupo, una clasificación de jugadores, un buscador de compañeros, avisos cuando quede una pista libre o la posibilidad de sincronizar las reservas con el calendario del móvil. Todas parecen buenas, pero el problema de Lucía es reservar la pista del jueves sin complicaciones, y para eso le basta con ver qué pistas están libres, reservar una, pagarla y poder cancelarla si hace falta. Eso sería el MVP, y el resto de ideas se apuntan para versiones posteriores.

Para definir tu MVP, abre la ficha de tu persona principal y busca su objetivo más importante. Después haz dos columnas, una con las funciones que entran y otra con las que se quedan fuera, y pasa cada función por tres preguntas: si tu persona principal la necesita para completar su tarea más importante, si puedes construirla con el tiempo y las herramientas del módulo, y si existe mientras tanto otra forma aceptable de resolverla. Cada respuesta tiene que apoyarse en un motivo concreto, y el simple hecho de que una función te guste no es suficiente. Si la respuesta a la primera pregunta es no, esa función se queda fuera de esta versión y la apuntas para la siguiente (RA1-c).

El resultado tiene que ser una lista corta y fácil de justificar, con lo que tendrá tu aplicación en esta versión y una frase por cada función que se ha quedado fuera explicando por qué puede esperar. Guárdala en el mismo tablero de FigJam donde tienes el resto de la investigación, porque a partir de ahora será tu referencia, empezando por los flujos que vas a dibujar en este mismo apartado.

### Cómo se dibuja un user flow

Los user flows usan unos símbolos muy sencillos: una píldora o una elipse para el principio y el final del recorrido, un rectángulo para cada pantalla o estado, un rombo para cada decisión (ya la tome la persona o el sistema) y flechas para indicar cómo se pasa de un elemento a otro.

El **punto de entrada**, es decir, el lugar desde el que la persona empieza el recorrido, merece más atención de la que se le suele dar. La gente puede llegar a un mismo flujo desde sitios muy distintos, como la pantalla de inicio, una notificación, un enlace que le ha pasado alguien por WhatsApp o un buscador, y según por dónde llegue sabrá más o menos de lo que está pasando. Por ejemplo, quien abre el enlace que un amigo ha enviado al grupo ("he reservado la pista 3, ¿os viene bien?") aparece directamente en medio de una reserva sin haber visto la pantalla de inicio, y el flujo también tiene que funcionar para esa persona.

De cada rombo salen al menos dos caminos, y cada uno de ellos tiene que terminar en algún sitio definido. Si un camino se queda sin final, estás dejando un hueco en el diseño que más adelante aparecerá como una pantalla de error que nadie ha pensado.

### El happy path y los casos límite

El **happy path** es el recorrido ideal, aquel en el que la persona hace exactamente lo que el diseño espera, todo funciona y el objetivo se cumple. Es el flujo más fácil de dibujar, pero también el que menos te enseña, porque describe justo la situación que menos problemas va a dar.

Lo realmente interesante son los **casos límite**, que son las situaciones en las que algo se sale de lo previsto. Por ejemplo, qué pasa cuando alguien se equivoca tres veces al escribir la contraseña, cuando se corta la conexión a mitad del pago, cuando dos personas intentan reservar la misma pista en el mismo momento o cuando Manuel vuelve a una reserva que dejó a medias el día anterior. Cada una de esas situaciones necesita una respuesta pensada en el diseño.

Descubrir estos casos ahora, sobre un diagrama, te lleva unos minutos, mientras que descubrirlos cuando la aplicación ya está publicada te costará usuarios que se van y no vuelven.

En este punto es donde tus personas empiezan a resultarte realmente útiles. Recorre cada flujo poniéndote en el lugar de cada una y pregúntate dónde se quedaría atascada. En el caso de Lucía, que reserva en el autobús con una sola mano, puedes preguntarte si podrá terminar la reserva aunque la interrumpan dos veces o si se guardará lo que llevaba hecho si cierra la aplicación para contestar un mensaje. En el caso de una persona que usa un lector de pantalla, tendrás que comprobar si hay algún paso que dependa solo de información visual, como una pista libre que únicamente se distingue por estar pintada de verde. Hacerte estas preguntas ahora, sobre un diagrama, te evitará tener que rediseñar pantallas enteras dentro de unos meses (RA5-a, RA6-c).

### El flujo del MVP y los flujos complementarios

Empieza dibujando un único flujo que recorra el MVP de principio a fin, desde que la persona entra en la aplicación hasta que sale, pasando por cada función del MVP en el orden en que se usaría de verdad. Ese flujo debe incluir el happy path completo y al menos dos o tres casos límite en los momentos más delicados, como el pago, el registro o cualquier paso en el que algo pueda salir mal. Este será el flujo de referencia durante todo el módulo.

Si mientras lo dibujas descubres una tarea importante que ese flujo no cubre bien (por ejemplo, la tarea principal de una persona secundaria o una situación que se aparta del camino principal pero que tu aplicación tiene que resolver igualmente), dibújala aparte como un flujo complementario. Solo merece la pena hacer un flujo complementario cuando te obliga a tomar decisiones de diseño que el flujo del MVP no te plantea, así que no hagas flujos solo para tener más.

El nivel de detalle adecuado es el que te permite tomar decisiones. Un flujo que solo dice "el usuario se registra" no te ayuda a diseñar nada, y uno que describe cada campo del formulario ya se parece más a un boceto de pantalla. Lo ideal es un punto intermedio, con las pantallas como unidades, las decisiones bien marcadas y las situaciones de error y de éxito identificadas.

### El flujo como guion para evaluar

El user flow que hagas ahora volverá a aparecer en la Órbita 5, donde servirá de guion para el **cognitive walkthrough** (recorrido cognitivo), una prueba en la que se recorre la aplicación terminada paso a paso para comprobar si una persona podría completar cada tarea sin ayuda. Si ahora documentas bien tu flujo, dentro de unos meses tendrás preparada buena parte de esa prueba (RA6-e).

### Formato y herramienta

El flujo se dibuja en FigJam, en el mismo tablero que las personas y el MVP, con las formas estándar y los conectores automáticos de la herramienta. Debe llevar un título que indique qué parte de la aplicación recorre, a qué persona o personas sirve y una anotación en cada punto donde haya quedado alguna decisión de diseño pendiente.

Si usas IA para hacer un primer borrador del flujo o para buscar casos límite, el procedimiento es el mismo de siempre: lo anotas en el `CHANGELOG.md`. Ten en cuenta, además, que si la IA te sugiere un caso límite y no eres capaz de explicarlo, todavía no lo has analizado de verdad.

El esquema siguiente muestra un flujo completo de otro tipo de aplicación, una compra en una tienda online sin registrarse, con su happy path y los caminos que se abren cuando algo falla.

![Ejemplo de user flow: compra como invitado](img/orbita1_03_esquema_user_flow.svg)
