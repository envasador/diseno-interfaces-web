# Órbita 5 — Verificar con personas reales

## 1. Evaluación heurística de Nielsen

Cuando llevas meses trabajando en un proyecto, te acostumbras tanto a él que dejas de ver sus fallos, igual que dejas de ver una mancha en la pared de tu habitación cuando lleva ahí mucho tiempo. Por eso, en esta órbita vas a cambiar de papel: en lugar de construir, vas a revisar lo que has construido con la misma exigencia con la que lo haría alguien que lo ve por primera vez.

El primer paso de esa revisión es la **evaluación heurística**, un método creado por Jakob Nielsen que consiste en recorrer tu propio proyecto comparándolo con diez principios de usabilidad muy conocidos, a los que se llama heurísticas. Se hace antes de cualquier prueba con personas reales por un motivo práctico, y es que permite encontrar los fallos más evidentes de forma rápida y sin coste. Así, cuando en el apartado siguiente hagas el cognitive walkthrough con personas reales, el tiempo se dedicará a los problemas que solo aparecen cuando alguien usa de verdad la aplicación, y nadie perderá veinte minutos atascado en un botón que podrías haber arreglado tú antes (RA6-a).

### Las diez heurísticas

**1. Visibilidad del estado del sistema.** La persona tiene que saber en todo momento qué está pasando, por ejemplo si su acción se ha registrado, si algo se está cargando o si el pago se ha completado. Si no recibe ninguna señal, no sabrá si debe pulsar otra vez, esperar o abandonar, y en la aplicación del polideportivo, pulsar dos veces podría suponer reservar dos pistas. Un cambio en el aspecto del botón, un indicador de carga o un mensaje de confirmación resuelven este problema.

**2. Correspondencia entre el sistema y el mundo real.** La interfaz tiene que usar las palabras y los conceptos que ya conoce quien la utiliza, y dejar los términos técnicos internos del proyecto para el código. Un mensaje de error que solo entiende quien programó la aplicación, o un color que va en contra de una convención (como usar el rojo para indicar que todo ha ido bien), obliga a la persona a interpretar lo que ve antes de poder entenderlo.

**3. Control y libertad del usuario.** Toda acción importante necesita una forma de deshacerla, cancelarla o confirmarla antes de que sea definitiva. Gmail, por ejemplo, permite anular el envío de un correo durante unos segundos, y casi todas las redes sociales preguntan "¿Eliminar esta publicación?" antes de borrarla. Sin esas opciones, un toque equivocado se convierte en un error que no tiene arreglo.

**4. Coherencia y estándares.** (En muchas traducciones aparece como "consistencia".) Un mismo botón tiene que comportarse igual en toda la aplicación, y un icono tiene que significar siempre lo mismo. Cambiar un patrón que todo el mundo conoce, como mover el carrito de la esquina en la que la gente suele buscarlo, exige un motivo de peso, porque el esfuerzo de aprender algo nuevo recae sobre quien usa la aplicación.

**5. Prevención de errores.** Siempre es mejor evitar un problema que explicarlo cuando ya ha ocurrido. El autocompletado, los avisos antes de una acción que no se puede deshacer o el recordatorio que aparece cuando mencionas un archivo adjunto en un correo y se te ha olvidado adjuntarlo son formas de prevención, porque el sistema se anticipa a los errores más habituales.

**6. Reconocer antes que recordar.** La interfaz tiene que mostrar las opciones disponibles para que nadie tenga que memorizarlas. Un campo con autocompletado o una lista con "tus pistas habituales" reducen el esfuerzo mental, porque reconocer algo que tienes delante es mucho más fácil que recordarlo.

**7. Flexibilidad y eficiencia de uso.** La aplicación tiene que servir igual de bien a quien la abre por primera vez que a quien la usa todos los días. Los atajos opcionales, las pantallas de bienvenida que se pueden saltar o un botón para "repetir la última reserva" permiten que quien ya tiene experiencia vaya más rápido sin complicarle las cosas a quien está empezando.

**8. Diseño estético y minimalista.** Cada elemento que aparece en pantalla compite por la atención con el que de verdad importa en ese momento. Mostrar solo lo necesario para la tarea que se está haciendo mantiene la interfaz fácil de leer, y lo que sería interesante pero no hace falta ahora puede llevarse a otra pantalla.

**9. Ayudar a reconocer, diagnosticar y recuperarse de los errores.** Cuando algo falla, el mensaje tiene que explicar en un lenguaje sencillo qué ha pasado y qué se puede hacer. Un mensaje como "Error 402" deja a Manuel bloqueado justo en el peor momento, mientras que "No hemos podido cobrar la reserva porque tu tarjeta ha caducado. Prueba con otra tarjeta o paga en taquilla" le explica qué ocurre y cómo puede continuar.

**10. Ayuda y documentación.** Las preguntas frecuentes o las explicaciones de un campo tienen que estar disponibles cuando se necesitan. Aun así, si la gente tiene que consultarlas a menudo, suele ser una señal de que alguna parte del diseño no ha quedado lo bastante clara.

### La IA y la heurística 9

Si tu proyecto incluye alguna función con IA generativa, ten en cuenta que estos sistemas pueden dar una respuesta incorrecta con la misma seguridad aparente que una correcta. Eso hace que la heurística 9 sea especialmente importante en estos casos. El diseño tiene que dejar claro cuándo una respuesta la ha generado un modelo de IA, facilitar que se pueda comprobar (por ejemplo, indicando las fuentes) y tratar los fallos del modelo con mensajes propios, distintos de los de un error técnico cualquiera.

### Cómo aplicarlas: primero la gravedad, después la lista

Si recorres tu aplicación pantalla por pantalla preguntándote si cumple cada una de las diez heurísticas, acabarás con una lista de problemas que probablemente será larga. Esa lista, por sí sola, sirve de poco, porque no todos los fallos tienen la misma importancia ni cuesta lo mismo corregirlos.

Por eso, para cada problema que encuentres tendrás que anotar tres cosas: qué heurística incumple, qué **gravedad** tiene (desde un detalle estético sin importancia hasta algo que impide completar una tarea) y qué **dificultad** supondría corregirlo. Al cruzar la gravedad con la dificultad obtendrás el orden en el que conviene resolverlos. Lo que es grave y fácil de arreglar va primero, mientras que lo que es menor y costoso puede esperar o quedar documentado como una decisión consciente de no abordarlo por ahora, que también es una decisión que se puede defender.

Ese informe, ordenado por gravedad, será uno de los materiales de partida del apartado 6 de esta órbita, junto con los resultados del cognitive walkthrough y de las revisiones de patrones engañosos y de sostenibilidad. La evaluación heurística prepara el terreno para todas esas pruebas, porque elimina antes los problemas más evidentes (RA6-e).
