# Órbita 1 — Conocer a las personas

## 1. Por qué investigamos antes de diseñar

Cuando tienes una idea para una aplicación, lo normal es querer verla cuanto antes en una pantalla. Abres una herramienta de diseño, dibujas la página de inicio y en un rato tienes algo que parece una aplicación de verdad, lo que da mucha sensación de avance. El problema es que, si todavía no sabes bien para quién estás diseñando ni qué necesita esa persona, cada botón que colocas y cada texto que escribes es una decisión tomada a ciegas. Muchas de esas decisiones habrá que cambiarlas más adelante, y cuanto más avanzado esté el proyecto, más trabajo costará hacerlo.

Investigar sirve para tener esa información **antes** de decidir. Te llevará unos días al principio del proyecto, pero te ahorrará semanas de correcciones al final.

### Tú no eres el usuario

Después de varias semanas trabajando en tu proyecto conocerás cada detalle de cómo funciona: dónde está cada opción, qué hace cada botón y por qué el menú está colocado donde está. Ese conocimiento te viene muy bien para construirlo, pero te pone en una situación muy distinta a la de alguien que abre tu aplicación por primera vez. Sin darte cuenta, te habrás convertido en la persona para la que todo resulta evidente.

Don Norman lo explica en su libro *La psicología de los objetos cotidianos*. Cada persona se construye un **modelo mental**, es decir, una idea propia de cómo funciona algo, y el modelo mental de quien usa un producto casi nunca coincide con el de quien lo ha diseñado. Si coinciden, la interfaz resulta intuitiva. El problema aparece cuando no coinciden, porque entonces la persona se pierde, se frustra y acaba cerrando la aplicación. Investigar te permite conocer ese modelo mental antes de dibujar, de modo que tus decisiones partan de cómo piensan las personas que van a usar tu aplicación y no de tus propias suposiciones.

Hay una prueba muy sencilla que puedes hacer en cualquier momento del curso. Dale tu prototipo a alguien de tu familia, sin explicarle nada, y pídele que haga una tarea concreta. Mientras lo intenta, no toques el ratón ni le des pistas, aunque te cueste. Lo que ocurra en esos dos minutos te enseñará más sobre tu diseño que cualquier opinión tuya.

### Para quién diseñas

Cuando intentas diseñar para todo el mundo a la vez, el resultado suele ser una aplicación que no molesta a nadie pero que tampoco le resuelve bien el problema a nadie en concreto.

Para verlo con un ejemplo, imagina que vas a diseñar una aplicación para reservar las pistas del polideportivo municipal. Si piensas en "todo el mundo", no tienes ninguna pista sobre qué decidir (y perdón por el juego de palabras). En cambio, si piensas en Manuel, que tiene 64 años, juega al pádel los martes con tres amigos, tiene baja visión y reserva desde el móvil con la letra ampliada al 200 %, enseguida te surgen preguntas útiles. ¿Cabe el calendario en la pantalla con ese tamaño de letra? ¿Distinguirá una pista libre de una ocupada si la única diferencia es el color? ¿Qué pasa si uno de los cuatro amigos no puede ir al partido el mismo martes por la tarde? Con Manuel en mente, cada decisión de diseño tiene un criterio claro: **¿esto le funciona a esta persona, en esta situación?** (RA6-a).

Manuel es un personaje inventado para el ejemplo. Las personas de tu proyecto saldrán de entrevistas con gente real, y en el apartado siguiente verás cómo se construyen.

En esta órbita vas a crear dos o tres personas, y una de ellas tendrá algún tipo de diversidad funcional (visual, motora, cognitiva o auditiva). Lo hacemos por un motivo práctico, porque si desde el primer día tienes presente a alguien que usa un lector de pantalla o que navega solo con el teclado, las decisiones de accesibilidad de las órbitas siguientes saldrán de forma natural durante el diseño. Si lo dejas para la última semana, tendrás que añadirlas como un parche, y los parches casi siempre se notan.

### Las leyes de UX: lo que ya se sabe sobre cómo se comporta la gente

Antes de salir a investigar, conviene que conozcas algunos principios sobre el comportamiento de las personas que los profesionales del diseño utilizan como referencia. Se conocen como **leyes de UX** (de *user experience*, experiencia de usuario). No son reglas exactas y todas tienen excepciones, pero describen tendencias muy fiables y te darán un vocabulario muy útil para explicar tus decisiones en la auditoría oral.

**Ley de Hick.** Cuantas más opciones tiene una persona delante, más tarda en decidirse. Un menú con doce opciones se lee más despacio que uno con cuatro, así que simplificar consiste en ordenar el contenido para que cada persona llegue a lo que busca sin tener que leer todo lo demás.

**Ley de Fitts.** Un elemento grande y cercano se pulsa antes y con menos errores que uno pequeño y lejano. En el móvil, esto significa que las acciones que más se usan deben estar en las zonas a las que el pulgar llega sin esfuerzo, porque lo que cuesta alcanzar se acaba usando menos.

**Ley de Jakob.** La gente pasa la mayor parte de su tiempo en otras webs y aplicaciones, de modo que llega a la tuya sabiendo ya dónde suele estar el carrito, qué hace el icono de la lupa o cómo se rellena un formulario. Si respetas esas costumbres, nadie tendrá que aprender nada nuevo para usar tu aplicación, así que cambiarlas solo tiene sentido cuando hay un motivo de peso.

**Ley de Tesler.** Todo sistema tiene una parte de complejidad que no se puede eliminar, solo trasladar de un sitio a otro. Si el diseño no se ocupa de ella, acaba recayendo en quien usa la aplicación. Repartir esa complejidad en pasos, en niveles o según el contexto forma parte de tu trabajo como diseñador.

**Ley de Miller.** Nuestra memoria a corto plazo solo puede manejar con comodidad unos pocos elementos a la vez (la cifra clásica es siete, más o menos dos). Por eso una pantalla con demasiadas cosas reclamando atención acaba bloqueando a cualquiera, y para evitarlo existen recursos como la jerarquía visual, el espacio en blanco y la agrupación.

Imagina que en la auditoría oral te pregunto por qué has puesto el botón de reservar en la parte de abajo de la pantalla y ocupando todo el ancho. Para que tu respuesta sea válida tendrás que apoyarla en algo más que el gusto personal, por ejemplo explicando que lo has hecho por la ley de Fitts, porque es la acción principal y Manuel la pulsa con el pulgar y con la letra ampliada. Así la decisión queda justificada con un principio y con una persona concreta (RA1-a, RA6-a).

Puedes consultar todas estas leyes, con explicaciones y ejemplos, en [Laws of UX](https://lawsofux.com/es/).

### La IA en la investigación

Las herramientas de IA te pueden ayudar bastante en esta fase, por ejemplo a ordenar las notas de tus entrevistas, a proponerte preguntas para el guion o a encontrar temas que se repiten en las respuestas de una encuesta. Lo que no pueden hacer es sentarse delante de una persona y darse cuenta de que tarda varios segundos en contestar cuando le preguntas cómo paga, un detalle que puede decirte mucho sobre lo que le preocupa. Ese tipo de información solo se obtiene hablando con la gente.

Si usas IA en cualquier momento de esta fase, anótalo en el `CHANGELOG.md`: qué le pediste, qué te devolvió, qué conservaste y qué cambiaste. Ese registro demuestra que las decisiones son tuyas, y te lo pediré en la auditoría oral.
