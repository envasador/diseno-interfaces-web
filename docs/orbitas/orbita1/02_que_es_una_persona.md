# Órbita 1 — Conocer a las personas

## 2. Personas: qué son y cómo se construyen

<div style="background:#1F0318; border:3px solid #1F0318; box-shadow:6px 6px 0 #E93456; padding:28px 36px; display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:24px; margin:32px 0;">
  <div>
    <p style="margin:0 0 8px 0; color:#FFB8DE; font-weight:700; text-transform:uppercase; letter-spacing:1px; font-size:0.85rem;">Diapositivas del apartado</p>
    <p style="margin:0; color:#ffffff; font-size:1.1rem; font-weight:600;">Qué es una persona, cuándo sirve, cómo reconocer una que no funciona y los cuatro pasos para construirla.</p>
  </div>
  <a href="../slides/orbita1_02_que_es_una_persona.pdf" target="_blank" rel="noopener" style="background:#E93456 !important; color:#ffffff !important; border:3px solid #1F0318 !important; box-shadow:4px 4px 0 #1F0318 !important; padding:14px 28px; font-weight:700; text-transform:uppercase; letter-spacing:1px; text-decoration:none !important; white-space:nowrap; border-bottom:none !important;">Descargar presentación →</a>
</div>


Una persona es un perfil de usuario construido a partir de **investigación real**. Recoge los patrones de comportamiento, las motivaciones, las frustraciones y los contextos de uso que has encontrado en tus entrevistas y encuestas, y los sintetiza en un perfil concreto que puedas consultar mientras diseñas.

La demografía (nombre, edad, profesión, foto) puede estar si te ayuda a visualizar mejor el perfil, pero lo que realmente hace útil a una persona son los **detalles de comportamiento**: cuándo usa el producto, desde qué dispositivo, en qué condiciones, qué quiere conseguir y qué se lo impide ahora mismo.

### Cuándo una persona te sirve

Una persona te sirve cuando te obliga a tomar decisiones que no habrías tomado sin ella. Ese es el criterio.

Si sabes que tu persona principal usa la aplicación en el transporte público, con una sola mano y el brillo al mínimo para ahorrar batería, eso te dice cosas concretas: los elementos interactivos tienen que ser suficientemente grandes para pulsarlos con el pulgar, el contraste tiene que funcionar con pantalla oscurecida, la navegación no puede depender de gestos que requieren las dos manos.

Si tu persona solo dice que "es joven y usa el móvil", no te dice nada que no supieras ya. No tiene información de diseño suficiente.

Los detalles que más te van a ayudar son los de comportamiento y contexto, los que responden a preguntas como: ¿en qué momento del día usa esto? ¿Qué sabe hacer con facilidad y qué le cuesta? ¿Qué le genera desconfianza en una interfaz? ¿Qué quiere conseguir y por qué no lo consigue ya? (RA1-a, RA6-c).

### Cómo reconocer una persona que no funciona

Hay tres síntomas que delatan una persona mal construida:

1. **El usuario ideal.** Alguien cuyas motivaciones encajan perfectamente con lo que resuelve el producto, cuyas frustraciones son exactamente las que el producto soluciona, y que no tiene ningún comportamiento que complique el diseño. Esa persona sale de las hipótesis del diseñador, no de la investigación.
2. **Solo datos demográficos.** Nombre, foto, edad, profesión, aficiones... y nada que diga cómo usa el producto o qué le dificulta usarlo. Ese tipo de perfil no orienta ninguna decisión.
3. **Coherencia perfecta.** Las personas reales se contradicen: dicen que les importa la privacidad pero usan la misma contraseña para todo, dicen que no tienen tiempo pero pasan horas en redes sociales. Sin ninguna contradicción interna, sospecha.

### Personas primarias y secundarias

No todas las personas tienen el mismo peso. La **persona primaria** es para quien diseñas primero: sus necesidades determinan las decisiones fundamentales de navegación, estructura y componentes. Cuando algo funciona para la persona primaria pero no para otra, la primaria gana.

Las **personas secundarias** también usarán el producto, pero sus necesidades no pueden contradecir lo ya decidido para la primaria. Añaden matices, pero no rediseñan.

En esta órbita vas a construir entre dos y tres personas. Una tiene que incluir algún tipo de diversidad funcional —visual, motora, cognitiva o auditiva— con el mismo peso que cualquier otra. Si esta persona está bien construida, sus necesidades van a aparecer de forma natural cada vez que tomes una decisión sobre contraste, tamaño de elementos, estructura semántica o comportamiento del foco. Eso es exactamente lo que buscamos: que la accesibilidad entre por el proceso de diseño, no como revisión final (RA5-a).

### Cómo se construye una persona

Con las herramientas de IA actuales puedes generar una ficha de persona en treinta segundos. El problema es que esa ficha no viene de investigación, viene de los patrones más comunes que el modelo ha visto. Puede parecer completa y tener buen aspecto, pero no refleja a las personas reales que van a usar tu producto.

Lo que valida una persona es **su origen**: poder señalar qué dato de investigación respalda cada atributo de comportamiento. Si no puedes hacer eso, la persona no está terminada, da igual cómo se vea la ficha.

Construir una persona es un proceso de cuatro pasos: defines qué quieres entender, recoges datos, los sintetizas y redactas la ficha. El riesgo en cada paso es el mismo: atajar con suposiciones en lugar de observar.

#### Paso 1: define qué quieres entender

Antes de hablar con nadie, acota qué información necesitas. Una investigación sin foco produce muchos datos que luego cuesta convertir en algo útil.

Las preguntas que orientan esta fase son de tres tipos. Las de contexto describen la vida del usuario en relación con el problema que resuelve tu producto: ¿en qué situaciones aparece esa necesidad?, ¿con qué frecuencia?, ¿qué hace ahora para resolverla? Las de comportamiento revelan lo que la gente hace, no lo que dice que hace (la diferencia importa). Las de fricción identifican los momentos de dificultad o abandono, que son los más valiosos para el diseño (RA6-a).

#### Paso 2: recoge datos

Para este módulo tienes tres métodos accesibles.

Las **encuestas** sirven para recoger volumen y detectar patrones. Con Tally puedes crear formularios sin límite de respuestas. Son útiles para confirmar o descartar hipótesis y para identificar perfiles que entrevistar después. Su limitación es que recogen respuestas declaradas, no comportamiento real.

Las **entrevistas** son el método que más información de calidad produce. Una conversación de veinte minutos con alguien que vive el problema que quieres resolver te da más que cien respuestas de encuesta. Las preguntas tienen que ser abiertas ("cuéntame la última vez que...") y hay que resistir la tentación de sugerir respuestas. Con cinco o seis entrevistas bien hechas suelen aparecer los patrones principales.

Los **tests de los cinco segundos** permiten evaluar qué comunica una interfaz en una primera impresión. En esta órbita todavía no tienes interfaz propia, así que los aplicas sobre productos de referencia: las webs o aplicaciones que ya resuelven el problema que vas a abordar. Saber qué percibe la gente en cinco segundos ante tus referentes es información útil para el brief. Con Lyssna puedes montar uno en minutos. Esta herramienta volverá en la Órbita 2, ya sobre tus propios mockups (RA1-c, RA6-a).

Investigar con personas reales conlleva responsabilidades. Antes de cada entrevista o encuesta, la persona tiene que saber para qué se van a usar sus respuestas y dar su conformidad. En los datos que guardes y en la documentación del proyecto, las respuestas se anonimizan: lo que te interesa son los patrones, no las identidades. Este es tu primer contacto con el pilar de diseño responsable del módulo: antes de auditar la ética del producto en la Órbita 5, practicas la ética del proceso.

#### Paso 3: sintetiza los hallazgos

Los datos en bruto son el punto de partida. Necesitas encontrar los patrones que se repiten entre varias personas entrevistadas para poder construir algo útil con ellos.

El método más directo es el affinity mapping: escribes cada hallazgo en una nota separada y los agrupas por afinidad en FigJam. Los grupos que emergen solos son los que señalan patrones reales. Los que tienes que forzar probablemente reflejan categorías tuyas, no del usuario.

De esa síntesis sacas los atributos que van a componer cada persona: comportamientos frecuentes, motivaciones principales, frustraciones recurrentes y contextos de uso. Cada atributo debería poder rastrearse hasta uno o varios datos concretos de la investigación. Si un atributo no tiene ese respaldo, es una hipótesis y hay que marcarlo como tal o quitarlo.

Puedes usar IA para organizar notas, identificar temas o reformular preguntas. Si lo haces, entra en el `CHANGELOG.md`: qué datos le pasaste, qué síntesis propuso, qué aceptaste y qué modificaste. El criterio de decisión siempre es tuyo (RA1-a).

#### Paso 4: redacta la ficha

La ficha vive en Figma, vinculada al archivo principal del proyecto. Su función es hacer el perfil fácil de consultar mientras diseñas.

Una ficha bien construida incluye:

**Un nombre** y, si quieres, una ilustración que te ayude a visualizar el perfil. Nunca una foto de una persona real.

**Una cita** que capture la tensión central de esa persona en relación con el problema. Algo que alguien podría haber dicho realmente en una entrevista.

**El contexto de uso**: cuándo, dónde y en qué condiciones interactúa con el producto. Dispositivos habituales, nivel de conectividad, entorno físico, momento del día. El dato de conectividad merece atención: si una de tus personas accede con conexión lenta o desde un dispositivo modesto, ese dato determinará en la Órbita 3 cuánto puede pesar tu interfaz. Cada kilobyte tiene un coste de acceso para esa persona y un coste energético (C6.f).

**Objetivos**: qué quiere conseguir con el producto, tanto el objetivo inmediato como el de fondo.

**Frustraciones**: qué le impide conseguir esos objetivos ahora mismo. Estos son los que más directamente orientan las decisiones de diseño.

Para la persona con diversidad funcional, la ficha incluye también el tipo de diversidad funcional, las tecnologías de apoyo que usa si las hay, y los ajustes de sistema que tiene configurados. Con esa información, esa persona se convierte en un criterio activo de accesibilidad a lo largo de todo el módulo (RA5-a).

[Ejemplos de personas](ejemplos/personas.html).

### Lo que te llevas de este apartado

Una persona es una síntesis de investigación real: cada atributo tiene detrás un dato concreto que lo respalda, y ese origen es lo único que la valida. Se construye en cuatro pasos —definir qué quieres entender, recoger datos, sintetizar y redactar la ficha— y sirve si te obliga a tomar decisiones que no habrías tomado sin ella.
