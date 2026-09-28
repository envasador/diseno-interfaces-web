# Órbita 5 — Verificar con personas reales

## 1. Evaluación heurística de Nielsen

Hasta ahora has construido el producto apoyándote en las personas, los flujos y el sistema de diseño. Esta órbita cambia de posición: en vez de construir, revisas lo construido con la misma exigencia con la que lo haría alguien de fuera. El primer paso de esa revisión es la **evaluación heurística**, un método de Jakob Nielsen que consiste en recorrer tu propio proyecto contrastándolo con diez principios de usabilidad conocidos, antes de someterlo a ningún test con usuarios reales.

La evaluación heurística no sustituye al testing con personas reales que vas a hacer en el cognitive walkthrough del siguiente apartado. Cumple otra función: encuentra los fallos obvios rápido y sin coste, para que el test con personas se dedique a los problemas que solo aparecen cuando alguien de verdad usa el producto (RA6-a).

### Las diez heurísticas

**1. Visibilidad del estado del sistema.** El usuario tiene que saber en todo momento qué está pasando: si una acción se ha registrado, si algo está cargando, si un envío ha funcionado. Sin esa señal, la persona no sabe si pulsar otra vez, esperar o darse por vencida. Un cambio de color en un botón, un icono de carga o un mensaje de confirmación cumplen esta función.

**2. Correspondencia entre el sistema y el mundo real.** La interfaz habla con las palabras y los conceptos que ya conoce el usuario, no con la jerga interna del proyecto. Un mensaje de error que solo tiene sentido para quien programó el sistema, o un color que contradice una convención (el rojo para indicar éxito, por ejemplo) obliga al usuario a traducir en vez de entender.

**3. Control y libertad del usuario.** Toda acción importante necesita una salida: deshacer, cancelar, confirmar antes de borrar. Gmail permite recuperar un correo enviado durante unos segundos; la mayoría de redes sociales preguntan "¿Eliminar esta publicación?" antes de ejecutar el borrado. Sin esas salidas, un clic equivocado se convierte en un error sin remedio.

**4. Consistencia y estándares.** Un mismo botón se comporta igual en toda la aplicación, y un icono significa siempre lo mismo. Reinventar un patrón ya asentado (mover el carrito de la esquina donde el usuario lo espera, por ejemplo) exige una razón de peso, porque el coste de aprendizaje lo paga el usuario.

**5. Prevención de errores.** Mejor evitar el problema que explicarlo después. El autocompletado, los avisos de seguridad antes de una acción irreversible o un recordatorio de adjuntar el archivo que se menciona en el texto del correo son formas de prevención: el sistema anticipa el error típico antes de que ocurra.

**6. Reconocer antes que recordar.** La interfaz muestra las opciones en vez de obligar al usuario a memorizarlas. Un campo con autocompletado o una lista de productos recientes reduce la carga mental: reconocer algo visible es mucho más fácil que recuperarlo de memoria.

**7. Flexibilidad y eficiencia de uso.** El mismo producto sirve igual de bien a quien lo usa por primera vez que a quien lo usa cada día. Atajos de teclado opcionales, un onboarding que se puede saltar y opciones de personalización permiten que la persona experta vaya más rápido sin complicar la experiencia de quien empieza.

**8. Diseño estético y minimalista.** Cada elemento que aparece en pantalla compite por la atención del usuario con el elemento que de verdad importa. Mostrar solo lo necesario para la tarea en curso, y no lo que sería interesante tener, es lo que mantiene una interfaz legible en vez de saturada.

**9. Ayudar a reconocer y recuperarse de errores.** Cuando algo falla, el mensaje explica qué ha pasado y qué se puede hacer al respecto, en lenguaje llano y no en un código interno. Un error sin explicación ni salida deja al usuario bloqueado justo en el peor momento.

**10. Ayuda y documentación.** Un FAQ o una explicación de campo tienen que estar disponibles cuando hacen falta, aunque conviene recordar que su necesidad frecuente suele ser síntoma de que algo anterior en el diseño no quedó lo bastante claro.

### La IA y la heurística 9

Si tu proyecto integra alguna funcionalidad con IA generativa, ten en cuenta que estos sistemas pueden producir una respuesta incorrecta con la misma seguridad aparente que una correcta. Eso convierte la heurística 9 en un punto crítico: el diseño tiene que dejar claro cuándo una respuesta viene de un modelo, facilitar su verificación (citando fuentes, por ejemplo) y no tratar un fallo del modelo como si fuera un error de sistema cualquiera.

### Cómo aplicarlas: severidad antes que lista de fallos

Recorrer tu interfaz preguntando, pantalla por pantalla, si cumple cada una de las diez heurísticas produce una lista de problemas. Esa lista por sí sola no basta: no todos los fallos pesan igual, y arreglarlos todos no cuesta lo mismo. Para cada problema que detectes, anota qué heurística incumple, qué gravedad tiene (desde un detalle cosmético hasta algo que impide completar la tarea) y qué dificultad tendría corregirlo. Cruzando gravedad y dificultad sale el orden en el que merece la pena intervenir: lo grave y fácil de arreglar va primero, lo cosmético y costoso puede esperar o quedar documentado como decisión consciente de no abordarlo ahora.

Ese informe de severidad es lo que vas a usar como entrada del apartado 6 de esta órbita, junto con lo que salga del cognitive walkthrough y de las auditorías de patrones engañosos y sostenibilidad. La evaluación heurística no reemplaza esas auditorías: les allana el terreno resolviendo antes lo evidente (RA6-e).
