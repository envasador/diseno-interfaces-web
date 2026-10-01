# Órbita 5 — Verificar con personas reales

## 1. Evaluación heurística de Nielsen

Llevas meses construyendo tu producto y ya no lo ves. Lo conoces tan bien que tus ojos pasan por encima de los fallos igual que pasan por encima de una mancha en la pared de tu cuarto: está ahí desde siempre, así que ha dejado de existir. Esta órbita te pide que cambies de silla y revises lo construido con la exigencia de alguien que llega de fuera.

El primer paso es la **evaluación heurística**, un método de Jakob Nielsen que consiste en recorrer tu propio proyecto contrastándolo con diez principios de usabilidad muy asentados. Se hace antes de ningún test con personas reales, y por un motivo práctico: encuentra los fallos evidentes deprisa y sin coste. Así, cuando en el apartado siguiente hagas el cognitive walkthrough con gente de verdad, el tiempo se va en los problemas que solo aparecen cuando alguien usa el producto, y nadie pierde veinte minutos atascado en un botón que tú podías haber arreglado solo (RA6-a).

### Las diez heurísticas

**1. Visibilidad del estado del sistema.** La persona tiene que saber en todo momento qué está pasando: si su acción se ha registrado, si algo está cargando, si el pago ha ido bien. Sin esa señal no sabe si pulsar otra vez, esperar o rendirse. Y si pulsa otra vez, en la app del polideportivo acaba de reservar dos pistas. Un cambio de estado en el botón, un indicador de carga o un mensaje de confirmación resuelven esto.

**2. Correspondencia entre el sistema y el mundo real.** La interfaz habla con las palabras y los conceptos que ya conoce quien la usa. La jerga interna del proyecto se queda en el repositorio. Un mensaje de error que solo entiende quien programó el sistema, o un color que contradice una convención (el rojo para decir que todo ha ido bien, por ejemplo), obliga a traducir antes de entender.

**3. Control y libertad.** Toda acción importante necesita una salida: deshacer, cancelar, confirmar antes de borrar. Gmail te deja recuperar un correo enviado durante unos segundos, y casi todas las redes sociales preguntan "¿Eliminar esta publicación?" antes de borrarla. Sin esas salidas, un toque equivocado es un error sin remedio.

**4. Consistencia y estándares.** Un mismo botón se comporta igual en toda la aplicación y un icono significa siempre lo mismo. Reinventar un patrón asentado (mover el carrito de la esquina donde todo el mundo lo busca, por ejemplo) exige una razón de peso, porque el coste de aprender lo nuevo lo paga la persona usuaria.

**5. Prevención de errores.** Mejor evitar el problema que explicarlo después. El autocompletado, el aviso antes de una acción irreversible o el recordatorio de que mencionas un adjunto que no has adjuntado son formas de prevención: el sistema se adelanta al error típico antes de que ocurra.

**6. Reconocer antes que recordar.** La interfaz enseña las opciones para que nadie tenga que memorizarlas. Un campo con autocompletado o una lista de "tus pistas habituales" reduce la carga mental, porque reconocer algo que tienes delante es mucho más fácil que sacarlo de la memoria.

**7. Flexibilidad y eficiencia de uso.** El mismo producto sirve igual de bien a quien lo abre por primera vez y a quien lo usa cada día. Atajos opcionales, un onboarding que se puede saltar o un botón de "repetir la última reserva" dejan que la persona experta vaya más rápido sin complicarle la vida a quien empieza.

**8. Diseño estético y minimalista.** Cada elemento en pantalla compite por la atención con el que de verdad importa. Mostrar solo lo necesario para la tarea en curso mantiene la interfaz legible. Lo que sería interesante tener, si no hace falta ahora, se queda para otra pantalla.

**9. Ayudar a reconocer y recuperarse de los errores.** Cuando algo falla, el mensaje explica qué ha pasado y qué se puede hacer, en lenguaje llano. "Error 402" deja a Manuel bloqueado justo en el peor momento. "No hemos podido cobrar la reserva. Tu tarjeta ha caducado: prueba con otra o paga en taquilla" le dice qué pasa y cómo seguir.

**10. Ayuda y documentación.** Las preguntas frecuentes o la explicación de un campo tienen que estar a mano cuando hacen falta. Eso sí, si se necesitan a menudo, casi siempre es síntoma de que algo anterior del diseño no quedó lo bastante claro.

### La IA y la heurística 9

Si tu proyecto incluye alguna funcionalidad con IA generativa, ten en cuenta que estos sistemas pueden dar una respuesta incorrecta con la misma seguridad aparente que una correcta. Eso convierte la heurística 9 en un punto crítico. El diseño tiene que dejar claro cuándo una respuesta viene de un modelo, facilitar que se pueda comprobar (citando fuentes, por ejemplo) y tratar un fallo del modelo con su propio mensaje, distinto del de un error de sistema cualquiera.

### Cómo aplicarlas: primero la gravedad, luego la lista

Si recorres tu interfaz pantalla por pantalla preguntándote si cumple cada heurística, acabarás con una lista de problemas. Larga, probablemente. Y una lista larga, sola, sirve de poco, porque no todos los fallos pesan igual ni cuesta lo mismo arreglarlos.

Para cada problema, anota tres cosas: qué heurística incumple, qué **gravedad** tiene (desde un detalle cosmético hasta algo que impide completar la tarea) y qué **dificultad** tendría corregirlo. Cruzando gravedad y dificultad sale el orden en el que merece la pena actuar. Lo grave y fácil va primero. Lo cosmético y costoso puede esperar, o quedar documentado como una decisión consciente de no tocarlo ahora, que también es una decisión defendible.

Ese informe de severidad es la materia prima del apartado 6 de esta órbita, junto con lo que salga del cognitive walkthrough y de las auditorías de patrones engañosos y de sostenibilidad. La evaluación heurística les despeja el camino a todas ellas quitando de en medio lo evidente (RA6-e).
