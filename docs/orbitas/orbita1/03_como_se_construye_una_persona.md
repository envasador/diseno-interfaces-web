# Órbita 1 — Conocer a las personas

## 3. Cómo se construye una persona

Construir una persona es un proceso de cuatro pasos: defines qué quieres entender, recoges datos, los sintetizas y redactas la ficha. El riesgo en cada paso es el mismo: atajar con suposiciones en lugar de observar.

### Paso 1: define qué quieres entender

Antes de hablar con nadie, acota qué información necesitas. Una investigación sin foco produce muchos datos que luego cuesta convertir en algo útil.

Las preguntas que orientan esta fase son de tres tipos. Las de contexto describen la vida del usuario en relación con el problema que resuelve tu producto: ¿en qué situaciones aparece esa necesidad?, ¿con qué frecuencia?, ¿qué hace ahora para resolverla? Las de comportamiento revelan lo que la gente hace, no lo que dice que hace —la diferencia importa—. Las de fricción identifican los momentos de dificultad o abandono, que son los más valiosos para el diseño (RA6-a).

### Paso 2: recoge datos

Para este módulo tienes tres métodos accesibles.

Las **encuestas** sirven para recoger volumen y detectar patrones. Con Tally puedes crear formularios sin límite de respuestas. Son útiles para confirmar o descartar hipótesis y para identificar perfiles que entrevistar después. Su limitación es que recogen respuestas declaradas, no comportamiento real.

Las **entrevistas** son el método que más información de calidad produce. Una conversación de veinte minutos con alguien que vive el problema que quieres resolver te da más que cien respuestas de encuesta. Las preguntas tienen que ser abiertas —"cuéntame la última vez que..."— y hay que resistir la tentación de sugerir respuestas. Con cinco o seis entrevistas bien hechas suelen aparecer los patrones principales.

Los **tests de los cinco segundos** permiten evaluar qué comunica una interfaz en una primera impresión. En esta órbita todavía no tienes interfaz propia, así que los aplicas sobre productos de referencia: las webs o aplicaciones que ya resuelven el problema que vas a abordar. Saber qué percibe la gente en cinco segundos ante tus referentes es información útil para el brief. Con Lyssna puedes montar uno en minutos. Esta herramienta volverá en la Órbita 2, ya sobre tus propios mockups (RA1-c, RA6-a).

Investigar con personas reales conlleva responsabilidades. Antes de cada entrevista o encuesta, la persona tiene que saber para qué se van a usar sus respuestas y dar su conformidad. En los datos que guardes y en la documentación del proyecto, las respuestas se anonimizan: lo que te interesa son los patrones, no las identidades. Este es tu primer contacto con el pilar de diseño responsable del módulo: antes de auditar la ética del producto en la Órbita 5, practicas la ética del proceso.

### Paso 3: sintetiza los hallazgos

Los datos en bruto son el punto de partida. Necesitas encontrar los patrones que se repiten entre varias personas entrevistadas para poder construir algo útil con ellos.

El método más directo es el affinity mapping: escribes cada hallazgo en una nota separada y los agrupas por afinidad en FigJam. Los grupos que emergen solos son los que señalan patrones reales. Los que tienes que forzar probablemente reflejan categorías tuyas, no del usuario.

De esa síntesis sacas los atributos que van a componer cada persona: comportamientos frecuentes, motivaciones principales, frustraciones recurrentes y contextos de uso. Cada atributo debería poder rastrearse hasta uno o varios datos concretos de la investigación. Si un atributo no tiene ese respaldo, es una hipótesis y hay que marcarlo como tal o quitarlo.

Puedes usar IA para organizar notas, identificar temas o reformular preguntas. Si lo haces, entra en el `CHANGELOG.md`: qué datos le pasaste, qué síntesis propuso, qué aceptaste y qué modificaste. El criterio de decisión siempre es tuyo (RA1-a).

### Paso 4: redacta la ficha

La ficha vive en Figma, vinculada al archivo principal del proyecto. Su función es hacer el perfil fácil de consultar mientras diseñas.

Una ficha bien construida incluye:

**Un nombre** y, si quieres, una ilustración que te ayude a visualizar el perfil. Nunca una foto de una persona real.

**Una cita** que capture la tensión central de esa persona en relación con el problema. Algo que alguien podría haber dicho realmente en una entrevista.

**El contexto de uso**: cuándo, dónde y en qué condiciones interactúa con el producto. Dispositivos habituales, nivel de conectividad, entorno físico, momento del día. El dato de conectividad merece atención: si una de tus personas accede con conexión lenta o desde un dispositivo modesto, ese dato determinará en la Órbita 3 cuánto puede pesar tu interfaz. Cada kilobyte tiene un coste de acceso para esa persona y un coste energético (C6.f).

**Objetivos**: qué quiere conseguir con el producto, tanto el objetivo inmediato como el de fondo.

**Frustraciones**: qué le impide conseguir esos objetivos ahora mismo. Estos son los que más directamente orientan las decisiones de diseño.

Para la persona con diversidad funcional, la ficha incluye también el tipo de diversidad funcional, las tecnologías de apoyo que usa si las hay, y los ajustes de sistema que tiene configurados. Con esa información, esa persona se convierte en un criterio activo de accesibilidad a lo largo de todo el módulo (RA5-a).

### Lo que no necesitas en la ficha

Los datos demográficos extensos —estado civil, ingresos, marca del móvil, aplicaciones favoritas— ocupan espacio sin orientar decisiones. Incluye solo lo que tenga consecuencias directas sobre cómo esa persona usa el producto.

Y una cosa que aprendes enseguida cuando empiezas a testear con personas reales: tu diseño no te pertenece. Puedes haber dedicado días a construir algo que tiene todo el sentido del mundo para ti, y la primera persona que lo ve desde fuera se pierde en el segundo paso. Eso es información. Te está diciendo dónde hay que mejorar. El trabajo de diseño consiste en usar esa información para tomar mejores decisiones.
