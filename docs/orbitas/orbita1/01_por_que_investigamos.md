# Órbita 1 — Conocer a las personas

## 1. Por qué investigamos antes de diseñar

<div style="background:#1F0318; border:3px solid #1F0318; box-shadow:6px 6px 0 #E93456; padding:28px 36px; display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:24px; margin:32px 0;">
  <div>
    <p style="margin:0 0 8px 0; color:#FFB8DE; font-weight:700; text-transform:uppercase; letter-spacing:1px; font-size:0.85rem;">Diapositivas del apartado</p>
    <p style="margin:0; color:#ffffff; font-size:1.1rem; font-weight:600;">Por qué investigar antes de diseñar, las leyes de UX y el papel de la IA en la investigación.</p>
  </div>


Abres Figma, creas un frame del tamaño de un móvil y en veinte minutos tienes una pantalla de inicio preciosa. Da gusto. Da tanto gusto que es fácil saltarse una pregunta pequeña: ¿para quién es esa pantalla? Si la respuesta es "para la gente", acabas de tomar veinte decisiones sin información. Cada una te la va a cobrar alguien más adelante. Normalmente tú, y normalmente en la semana de la entrega.

Investigar sirve para tener esa información **antes** de decidir. Cuesta unos días al principio del proyecto y ahorra semanas al final, que es el mejor negocio que vas a hacer en todo el curso.

### Tú no eres el usuario

Después de tres semanas con tu proyecto sabes dónde está cada botón, qué hace cada icono y por qué el menú se abre hacia la izquierda. Esa familiaridad te viene muy bien para construirlo y fatal para juzgarlo. Te has convertido en la única persona del mundo para quien tu interfaz es obvia.

Don Norman lo explica en *La psicología de los objetos cotidianos*: cada persona se construye un **modelo mental** de cómo funciona algo, y el de quien usa un producto casi nunca coincide con el de quien lo diseñó. Cuando coinciden, la interfaz parece intuitiva. Cuando no, la persona se pierde, se frustra y cierra la pestaña sin avisarte. Investigar te deja ver ese modelo mental antes de dibujar, para que tus decisiones salgan de ahí y tus suposiciones se queden donde estaban.

Hay una prueba sencilla, y bastante incómoda. Dale tu prototipo a alguien de tu casa, sin explicarle nada, y pídele que haga una tarea. No toques el ratón. No digas "es que ahí arriba...". Aguanta. Lo que pase en esos dos minutos vale más que cualquier opinión tuya sobre tu propio diseño.

### Para quién diseñas

Diseñar para todo el mundo a la vez produce interfaces tibias, que a nadie le estorban y a nadie le resuelven nada.

Pongamos que vas a diseñar una app para reservar las pistas del polideportivo municipal. "Para todo el mundo" no te da ni una pista (perdón). Ahora piensa en Manuel: 64 años, juega al pádel los martes con tres amigos, tiene baja visión y reserva desde el móvil con la letra al 200 %. De repente tienes preguntas útiles. ¿Cabe el calendario en la pantalla con ese tamaño de letra? ¿Distingue una pista libre de una ocupada si la única diferencia es el color? ¿Qué pasa cuando uno de los cuatro se cae del partido el martes a las siete? Con Manuel delante, cada decisión tiene un criterio: **¿esto le funciona a esta persona, en este contexto?** (RA6-a).

Manuel es inventado, eso sí. Los tuyos van a salir de entrevistas con gente real, y en el apartado siguiente verás cómo.

En esta órbita vas a construir dos o tres personas, y una de ellas tendrá algún tipo de diversidad funcional: visual, motora, cognitiva o auditiva. El motivo es práctico. Si alguien que usa lector de pantalla o navega solo con teclado está en tu proyecto desde el primer día, las decisiones de accesibilidad de las órbitas siguientes salen solas del proceso. Si aparece en la última semana, llega como un parche, y los parches siempre se notan.

### Las leyes de UX: lo que ya se sabe de cómo se comporta la gente

Antes de salir a investigar conviene saber lo que otros ya averiguaron. Hay un puñado de principios sobre comportamiento humano que el oficio usa como referencia. Son tendencias muy fiables (todas tienen sus excepciones) y te dan algo que vas a necesitar en la auditoría oral: vocabulario.

**Ley de Hick.** Cuantas más opciones, más se tarda en decidir. Un menú con doce entradas se procesa más despacio que uno con cuatro. Simplificar consiste en ordenar el contenido para que la persona llegue a lo suyo sin leerse todo lo demás.

**Ley de Fitts.** Lo grande y cercano se pulsa antes que lo pequeño y lejano. En móvil, las acciones frecuentes van donde el pulgar llega sin estirarse. Lo que cuesta alcanzar se usa menos, y lo que se usa menos acaba pareciendo que sobra.

**Ley de Jakob.** La gente pasa la mayor parte de su tiempo en otras webs. Llega a la tuya sabiendo dónde suele estar el carrito, qué hace la lupa y cómo se rellena un formulario. Si respetas esas convenciones, no tiene que aprender nada. Si te las saltas, más vale que tengas un motivo muy bueno.

**Ley de Tesler.** Todo sistema tiene una complejidad mínima que nadie puede eliminar, solo cambiar de sitio. Si el diseño no se encarga de ella, se la encuentra la persona usuaria. Repartirla por pasos, por niveles o por contexto es parte de tu trabajo.

**Ley de Miller.** La memoria de trabajo maneja con comodidad unos pocos elementos a la vez (la cifra clásica es siete, más o menos dos). Una pantalla con demasiadas cosas pidiendo atención bloquea a cualquiera. Para eso existen la jerarquía visual, el espacio en blanco y la agrupación.

Cuando en la auditoría oral te pregunte por qué el botón de reservar está abajo y ocupa todo el ancho, el gusto no te va a servir de argumento. Esto sí: "por la ley de Fitts; es la acción principal y Manuel la pulsa con el pulgar, con la letra ampliada". Una frase, un principio y una persona. Con eso la decisión queda defendida (RA1-a, RA6-a).

Las tienes todas, bien explicadas y con ejemplos, en [Laws of UX](https://lawsofux.com/es/).

### La IA en la investigación

Una IA te puede ayudar bastante en esta fase: ordenar las notas de seis entrevistas, proponerte preguntas para el guion, encontrar temas que se repiten en las respuestas de una encuesta. Lo que no puede hacer es sentarse delante de una persona y notar que tarda cuatro segundos en contestar cuando le preguntas cómo paga. Esos cuatro segundos son investigación, y para verlos hay que estar delante.

Si usas IA en cualquier parte de esta fase, apúntalo en el `CHANGELOG.md`: qué le pediste, qué te dio, qué conservaste y qué cambiaste. Ese registro es la prueba de que las decisiones son tuyas, y en la auditoría oral te lo voy a pedir.
