# Proyecto de la Órbita 1: Diseñar para que funcione

**Horas:** unas 20 · **Semanas:** de la 1 a la 4 · **RA:** RA1 y RA6 · **Trabajo:** individual

## El encargo

Cualquier aplicación web empieza igual, sea cual sea su tamaño o su tecnología: averiguando para quién se hace y qué tiene que resolver. Este proyecto es esa primera fase. En él vas a averiguar quién lo va a usar, qué problema tiene esa persona y qué estructura necesita tu aplicación para resolverlo, y vas a comprobar con gente real que esa estructura funciona antes de dedicarle un minuto a su aspecto.

Por eso, durante estas cuatro semanas no vas a elegir colores, tipografías ni logotipos. Todo lo que dibujes será en escala de grises, porque el color y la tipografía pueden mejorar una aplicación que ya funciona, pero no arreglan una que no se entiende. Si al terminar la órbita tu proyecto se entiende y se puede recorrer sin ayuda, todo lo que venga después (el diseño visual, la maquetación o la programación) consistirá en darle forma con criterio.

El tema lo eliges tú, con una condición: tiene que ser un problema que conozcas de cerca, porque te afecta a ti, a tu familia, a tu equipo o a la gente de tu barrio. Una buena forma de comprobar si has acertado es preguntarte si tú usarías esa aplicación. Si la respuesta es que no, es mejor darse cuenta en la primera semana que cuando ya hayas construido buena parte de la aplicación. A este punto de partida lo llamamos **outside-in**: la idea sale de una necesidad que detectas a tu alrededor y de lo que averiguas investigándola, sin un encargo cerrado de partida.

En los apuntes de la órbita verás un ejemplo que se repite en todos los apartados, una aplicación para reservar las pistas del polideportivo municipal, con dos personas, Lucía y Manuel. Úsalo como referencia para entender qué se pide en cada paso, pero tu proyecto tiene que salir de tu propia investigación.

---

## Qué tienes que hacer

El proyecto se organiza en ocho pasos, los mismos de la [hoja de ruta](../../orbitas/orbita1/00_hoja_de_ruta.md). Respeta el orden, porque cada paso utiliza lo que has obtenido en el anterior. En cada uno tienes enlazado el apartado de los apuntes donde se explica cómo hacerlo.

Antes de empezar, crea dos cosas que vas a usar durante toda la órbita: un tablero de FigJam para el proyecto y un repositorio de GitHub con un archivo `CHANGELOG.md` vacío. Cada vez que uses una IA, anotarás en ese archivo qué le pediste, qué te devolvió, qué conservaste y qué cambiaste.

### Paso 1. Escribe la hipótesis

Escribe en el tablero tu punto de partida con esta estructura: "creo que las personas que [contexto] necesitan [objetivo] pero [dificultad]". Por ejemplo: "creo que las personas que juegan al pádel en el polideportivo municipal necesitan reservar pista con antelación, pero solo pueden hacerlo llamando por teléfono en horario de oficina". Es una suposición provisional, y los pasos siguientes sirven para confirmarla, matizarla o descartarla. Déjala en el tablero hasta el final, porque al cerrar el brief se tiene que ver cuánto ha cambiado.

Apuntes: [1. Por qué investigamos antes de diseñar](../../orbitas/orbita1/01_por_que_investigamos.md).

### Paso 2. Estudia los referentes

Elige dos o tres aplicaciones o webs que intenten resolver el mismo problema que el tuyo y anota cómo están organizadas, qué palabras usan y en qué puntos se atascan sus usuarios.

Si quieres ir un paso más allá, puedes aplicar a una pantalla de cada referente el **test de los cinco segundos** con Lyssna, que te dirá qué transmite a primera vista. Es optativo. Si lo haces, añade los resultados al tablero junto al análisis de referentes.

También puedes publicar una **encuesta** con Tally, que es optativa. Si la haces, las preguntas tienen que salir de lo que todavía no sabes sobre tu hipótesis (de contexto, de comportamiento y de dificultad), y conviene que al final incluyas una pregunta para pedir permiso para contactar con quien la responda, porque así encontrarás con más facilidad a las personas a las que vas a entrevistar.

Apuntes: [2. Personas: qué son y cómo se construyen](../../orbitas/orbita1/02_que_es_una_persona.md), pasos 1 y 2.

### Paso 3. Entrevista al menos a dos personas

Elige al menos a dos personas que vivan de cerca el problema de tu hipótesis. Pueden ser familiares, vecinos, compañeros de equipo o de trabajo, o quienes te dieron permiso para contactar en la encuesta, si la has hecho. Dos es el mínimo, y cada entrevista que añadas te ayudará a distinguir mejor los patrones de los casos aislados.

La entrevista puede hacerse de la forma que mejor te funcione con cada persona: una charla en persona o por videollamada que grabas y después transcribes, una conversación en la que tomas notas y las pasas a limpio ese mismo día, o un formulario con preguntas abiertas que la persona contesta por escrito. Lo importante es que al final la conversación o las respuestas queden en texto, porque ese texto es el material con el que vas a trabajar en el paso siguiente y el que te pediré en la auditoría oral.

Sea cual sea el formato, haz preguntas abiertas sobre situaciones reales ("cuéntame la última vez que...") y no sugieras respuestas. Antes de empezar, cada persona tiene que saber para qué vas a usar lo que te cuente y dar su consentimiento, y si vas a grabar, tiene que aceptar también la grabación. En el texto, los datos aparecerán anonimizados desde el principio (P1, P2, P3...). Después, pasa cada descubrimiento a una nota adhesiva del tablero.

Si usas una herramienta de IA para transcribir una grabación, anótalo en el `CHANGELOG.md` y revisa la transcripción con el audio delante, porque es fácil que cambie palabras o se coma frases.

### Paso 4. Construye las personas

Agrupa todas las notas (entrevistas, análisis de referentes y encuesta, si la has hecho) con un **affinity mapping** y deja que los grupos se formen solos. De esos grupos saldrán dos o tres **personas**. Cada ficha lleva un nombre, una cita verosímil, el contexto de uso (dispositivo, conexión, lugar y momento del día), los objetivos y las frustraciones. Indica cuál es la persona principal y cuáles son secundarias.

Cada rasgo de cada ficha tiene que poder relacionarse con un dato de tu investigación. Si no sabes de dónde sale, márcalo como suposición o elimínalo. Presta especial atención al dato de la conexión, porque en la Órbita 3 decidirá cuánto puede pesar tu web.

Apuntes: [2. Personas](../../orbitas/orbita1/02_que_es_una_persona.md), pasos 3 y 4, y los [ejemplos de personas](../../orbitas/orbita1/ejemplos/personas.html).

### Paso 5. Define el MVP y dibuja el user flow

Parte del objetivo más importante de tu persona principal y decide qué entra en la primera versión de tu aplicación. Haz dos columnas, las funciones que entran y las que se quedan fuera, y pasa cada función por tres preguntas: si tu persona principal la necesita para su tarea más importante, si puedes construirla con el tiempo y las herramientas del módulo y si existe mientras tanto otra forma aceptable de resolverla. Cada función que se queda fuera lleva una frase con el motivo. Recuerda que cada función que no entra también es contenido, código y datos que tu aplicación no va a gastar.

Con el MVP decidido, dibuja en FigJam un único **user flow** que lo recorra entero, con la notación habitual (píldora, rectángulo, rombo y flechas). Marca el punto de entrada, dibuja el happy path completo y añade al menos dos o tres casos límite en los momentos delicados, como el registro o el pago. Si aparece una tarea importante que este flujo no cubre, dibújala aparte como flujo complementario.

Después, recorre el flujo poniéndote en el lugar de cada persona, empezando por la principal, y anota las decisiones que queden pendientes.

Apuntes: [3. User flows: del MVP al recorrido completo](../../orbitas/orbita1/03_user_flows.md).

### Paso 6. Dibuja el sitemap

Haz el inventario de pantallas, funciones y contenidos a partir de los referentes y del MVP, y agrúpalos pensando en cómo hablan de sus tareas tus personas en las entrevistas. Con esos grupos, dibuja el **sitemap**, con la pantalla de inicio como raíz y las pantallas principales, secundarias y de sistema bien diferenciadas. Usa para cada sección las palabras que emplearon tus personas.

Si quieres contrastar tu agrupación con otras personas, puedes hacer un **card sorting**: preparas una tarjeta por cada elemento del inventario y pides a cuatro o cinco compañeros que se parezcan a tus personas que las agrupen y pongan nombre a cada grupo, mientras tú observas sin intervenir. Es optativo. Si lo haces, deja los resultados en el tablero y usa los grupos que se repiten para ajustar el sitemap.

Revísalo dos veces: cada función del MVP tiene que tener su pantalla, a tres niveles de navegación como máximo, y el user flow tiene que poder recorrerse sobre el sitemap sin huecos y con los mismos nombres.

Apuntes: [4. Arquitectura de la información y sitemap](../../orbitas/orbita1/04_arquitectura_informacion.md).

### Paso 7. Dibuja los wireframes y monta el prototipo

En Figma Design, dibuja un **wireframe de baja fidelidad** por cada pantalla del happy path, más las pantallas de error o de estado vacío que sean importantes para tus personas. Usa solo negro, blanco y un gris medio, líneas en lugar de textos largos y un rectángulo con una X en lugar de imágenes. El frame tiene el tamaño del dispositivo de tu persona principal (360 × 800 para un móvil, 1280 × 800 para un portátil), y si tienes personas de los dos tipos, dibuja los dos. Cada frame se llama exactamente igual que su pantalla en el sitemap.

Los elementos que se repiten en varias pantallas (la cabecera, el menú, el botón principal o una tarjeta) conviértelos en **componentes** de Figma, y monta una **plantilla de pantalla** con la estructura común que reutilices en todos los frames. Así, si cambias el menú, cambia en todas las pantallas a la vez, y empiezas a construir la base del sistema de diseño de la fase siguiente.

Conecta los wireframes con interacciones básicas para tener un **prototipo navegable**.

Probar el prototipo es optativo, pero es lo que te permite llegar al 10 en el criterio C5 de la rúbrica. Si lo haces, organiza la prueba en Lyssna con cuatro o cinco personas que se parezcan a tu persona principal: dales una tarea concreta y no les expliques nada. Anota dónde se atascan y qué cambias a partir de ello.

Apuntes: [5. Del flujo al wireframe](../../orbitas/orbita1/05_wireframes.md).

### Paso 8. Cierra el brief

Convierte la hipótesis del primer día en el **brief** del proyecto. Puedes hacer el borrador en FigJam, pero el brief final tiene que quedar escrito en el repositorio de GitHub, en un archivo `BRIEF.md`, con una extensión que se lea en unos cinco minutos y con sus cinco elementos: el problema respaldado por datos, el alcance que marca el MVP, las personas (con un enlace a cada ficha), unos criterios de éxito que se puedan comprobar sobre tus personas y las restricciones del proyecto. Entre las restricciones tiene que haber al menos una ambiental, por ejemplo un peso máximo por página pensado para la persona con peor conexión, tal como pide el criterio 2.4 de las Web Sustainability Guidelines del W3C.

Por último, enseña el tablero a alguien que no conozca tu proyecto, sin explicarle nada. Si en unos cinco minutos entiende de qué trata y cómo funciona tu aplicación, está listo para entregar.

Apuntes: [6. El brief de proyecto y el entregable](../../orbitas/orbita1/06_brief_y_entregable.md).

---

## Qué entregas

El entregable son seis documentos enlazados entre sí, repartidos entre dos archivos de Figma y el repositorio del proyecto.

| Documento | Dónde | Qué tiene que incluir |
|---|---|---|
| **Brief de proyecto** | GitHub (`BRIEF.md`) | Los cinco elementos, con al menos una restricción ambiental, enlazado desde el tablero junto a la hipótesis inicial |
| **Personas** | FigJam | Dos o tres fichas, con la principal señalada y cada rasgo trazable a la investigación |
| **MVP y user flow** | FigJam | Las dos columnas con el motivo de cada descarte, el flujo del MVP con happy path y casos límite y los flujos complementarios, si los hay |
| **Sitemap** | FigJam | El árbol con pantallas principales, secundarias y de sistema, revisado frente al MVP y al user flow |
| **Wireframes** | Figma Design | Las pantallas del happy path en escala de grises, con los mismos nombres que en el sitemap |
| **Prototipo navegable** | Figma Design | Los wireframes conectados y, si lo has probado, los resultados de la prueba en Lyssna |

En el tablero de FigJam tiene que estar también la investigación que respalda todo lo anterior: el análisis de referentes (con los resultados del test de los cinco segundos, si lo has hecho), el resumen de la encuesta, si la has hecho, el texto de las entrevistas (transcripciones, notas pasadas a limpio o respuestas escritas), anonimizado y con el consentimiento registrado, y los resultados del card sorting, si lo has hecho. En el repositorio, el `CHANGELOG.md` tiene que recoger cada uso de IA de la órbita.

**Cómo se entrega.** En la tarea de Moodle Centros sube un documento con cuatro enlaces: el tablero de FigJam, el archivo de Figma Design, el prototipo en modo presentación y el repositorio de GitHub. Antes de subirlo, abre cada enlace en una ventana privada del navegador y comprueba que se ve sin iniciar sesión. Como vas a seguir trabajando en estos archivos en las fases siguientes, guarda en cada uno una versión con nombre en el historial de versiones de Figma ("Entrega Órbita 1"), que será la que se evalúe.

El brief final tiene que estar en el repositorio de GitHub, en el archivo `BRIEF.md`, y el `README.md` tiene que enlazarlo. Así lo tendrás a mano junto al código cuando empieces a programar.

**Cómo se presenta.** El tablero tiene que poder recorrerse sin que estés tú para explicarlo, así que ordénalo siguiendo los pasos del proyecto y pon un título a cada zona. Para que quede bien presentado, puedes partir de la plantilla de UI From Mars.

**Cuándo.** Al final de la semana 4. La fecha y la hora exactas están en la tarea de Moodle Centros.

---

## Resultados de aprendizaje y criterios de evaluación

Este proyecto trabaja el RA1 y el RA6. Los textos de los resultados de aprendizaje y de los criterios son los que fija la Orden de 16 de junio de 2011 (BOJA n.º 114), sin modificar.

**RA1. Planifica la creación de una interfaz web valorando y aplicando especificaciones de diseño.**

| CE | Texto del criterio | Dónde se trabaja en el proyecto |
|---|---|---|
| RA1-a | Se ha reconocido la importancia de la comunicación visual y sus principios básicos. | Personas, wireframes y presentación del tablero: decisiones justificadas con las leyes de UX y con una persona concreta, y documentos claros y ordenados |
| RA1-c | Se han analizado alternativas para la presentación de la información en documentos web. | MVP, user flow, sitemap y brief |
| RA1-e | Se han utilizado y valorado distintas tecnologías para el diseño de documentos web. | FigJam, Figma Design y Lyssna a lo largo de todo el proyecto, la presentación final del tablero y el uso documentado de la IA |
| RA1-f | Se han creado y utilizado plantillas de diseño. | Componentes y plantilla de pantalla de los wireframes en Figma Design, y plantillas del tablero (fichas de personas y presentación) |

**RA6. Desarrolla interfaces Web amigables analizando y aplicando las pautas de usabilidad establecidas.**

| CE | Texto del criterio | Dónde se trabaja en el proyecto |
|---|---|---|
| RA6-a | Se ha analizado la usabilidad de diferentes documentos web. | Análisis de referentes |
| RA6-c | Se ha modificado el interfaz web para adecuarlo al objetivo que persigue y a los usuarios a los que va dirigido. | Personas, MVP, user flow y sitemap construidos a partir de la investigación |
| RA6-e | Se han analizado diferentes técnicas para verificar la usabilidad de un documento web. | Entrevistas, criterios de éxito del brief y prueba del prototipo, si se hace |

Además de la rúbrica, algunos de estos criterios se completan con una prueba teórica o práctica, tal como recoge la programación del módulo.

---

## Rúbrica

La rúbrica tiene ocho criterios: seis corresponden a cada parte del trabajo, el séptimo a cómo está redactado, organizado y presentado el conjunto y el octavo al uso que has hecho de la IA. Cada uno está vinculado a los criterios de evaluación de la tabla anterior, y su nota es la que alimenta la de esos CE.

En este proyecto cuenta tanto lo que haces como la forma en que lo cuentas. Un brief con faltas de ortografía, unas fichas de personas escritas a medias o un tablero en el que hay que buscar las cosas transmiten un trabajo descuidado, por bueno que sea lo que hay detrás. Por eso la redacción, la organización y la presentación tienen un criterio propio (C7) y, además, pesan en todos los demás: **si un documento está tan mal redactado o tan desordenado que no se entiende sin que lo expliques tú, su criterio no pasa de Suficiente**, aunque el contenido sea correcto. Revisa la ortografía, escribe frases completas y claras, pon un título a cada zona del tablero y ordénalo siguiendo los pasos del proyecto.

| Criterio | Muy insuficiente (0–2,5) | Insuficiente (2,5–4,9) | Suficiente (5–6) | Notable (7–8) | Sobresaliente (9–10) | CE |
|---|---|---|---|---|---|---|
| **C1. Investigación** | No hay análisis de referentes ni entrevistas, o las entrevistas no se han hecho con personas reales. | Falta el análisis de referentes, hay menos de dos entrevistas o no están en texto. | Análisis de referentes y al menos dos entrevistas en texto, con notas escasas, preguntas que sugieren la respuesta o sin consentimiento registrado. | Referentes analizados (organización, vocabulario y puntos de bloqueo) y entrevistas en texto, anonimizadas, con consentimiento registrado y preguntas abiertas sobre situaciones reales. | Investigación completa y bien ordenada cuyos hallazgos cambian de forma visible la hipótesis inicial. Las entrevistas adicionales o los métodos optativos (encuesta, test de los cinco segundos), si los hay, aportan datos que se usan después. | RA6-a, RA6-e |
| **C2. Personas** | No hay fichas de personas, o son inventadas sin ninguna relación con la investigación. | Fichas con solo datos demográficos o con rasgos que no se pueden relacionar con las entrevistas. | Dos o tres fichas con algunos rasgos respaldados por datos, con apartados vacíos o redactados a medias. | Fichas completas (nombre, cita, contexto de uso, objetivos y frustraciones), con la mayoría de rasgos trazables a la investigación y la persona principal señalada. | Cada rasgo es trazable a un dato, las suposiciones están marcadas y las personas explican decisiones concretas del diseño. Fichas claras y con el mismo formato. | RA1-a, RA6-c |
| **C3. MVP y user flow** | No hay MVP ni user flow. | Falta el MVP, o el flujo solo describe el happy path o no usa la notación habitual. | MVP sin motivos claros para lo que se queda fuera y flujo con casos límite poco desarrollados. | MVP justificado con las tres preguntas y un motivo por cada función descartada. Flujo con punto de entrada, happy path y al menos dos o tres casos límite, con todos los caminos cerrados y la notación correcta. | Flujo recorrido desde cada persona, con las decisiones pendientes anotadas, legible de un vistazo y listo para usarse como guion de prueba de la aplicación terminada. | RA1-c, RA6-c |
| **C4. Arquitectura de la información y sitemap** | No hay sitemap. | Sitemap con una estructura que no sale de ningún dato o que no cubre el MVP. | Sitemap sin inventario detrás, con tipos de pantalla sin distinguir o con nombres que no coinciden con el user flow. | Sitemap construido a partir del inventario, con pantallas principales, secundarias y de sistema diferenciadas y todo el MVP a tres niveles como máximo. | Estructura y nombres justificados con el vocabulario de las entrevistas (y con el card sorting, si se ha hecho), coherentes con el MVP y el user flow. | RA1-c, RA6-c |
| **C5. Wireframes y prototipo** | No hay wireframes ni prototipo. | Wireframes con color o tipografías reales, sin conexión entre pantallas o que no cubren el happy path. | Wireframes del happy path con nombres distintos a los del sitemap, pantallas que faltan, elementos repetidos dibujados a mano en cada pantalla o un prototipo que se rompe. | Wireframes de baja fidelidad correctos, con el tamaño del dispositivo de la persona principal, componentes para los elementos que se repiten y una plantilla de pantalla común, y un prototipo que se recorre de principio a fin, con cada pantalla trazable al sitemap y al user flow. | Prototipo probado en Lyssna con cuatro o cinco personas, con los resultados anotados y los cambios hechos y documentados a partir de la prueba. Sin esta prueba, el criterio no pasa de Notable. | RA1-a, RA1-e, RA1-f, RA6-e |
| **C6. Brief** | No hay brief en el repositorio, o se limita a repetir la hipótesis inicial. | Brief al que le faltan elementos o basado en suposiciones. | Brief con los cinco elementos, poco desarrollados o difíciles de leer. | Brief completo en el `BRIEF.md` del repositorio, con el problema respaldado por datos, el alcance del MVP, enlaces a las personas, criterios de éxito y al menos una restricción ambiental. | Brief que se lee en cinco minutos, con criterios de éxito comprobables sobre las personas y que ancla cada decisión del proyecto. | RA1-c, RA6-e |
| **C7. Redacción, organización y presentación** | Documentos que no se pueden leer ni recorrer: textos inexistentes o ininteligibles, tablero caótico o enlaces que no abren. | Faltas de ortografía frecuentes, frases que no se entienden o tablero desordenado que no se puede recorrer sin explicación. | Se entiende, pero con errores de ortografía o de redacción, zonas sin título o documentos mezclados que obligan a buscar. | Textos claros y sin faltas, tablero ordenado siguiendo los pasos del proyecto con un título en cada zona, nombres coherentes entre todos los documentos y enlaces que funcionan. | Presentación cuidada (por ejemplo, a partir de la plantilla de UI From Mars), con una jerarquía visual clara y textos breves y precisos. Cualquiera entiende el proyecto en cinco minutos sin ninguna explicación. | RA1-a, RA1-e, RA1-f |
| **C8. Uso de la IA y trazabilidad** | No hay `CHANGELOG.md`, o hay un uso de IA evidente que no aparece en él. | Las entradas solo dicen qué herramienta se usó, sin qué se pidió ni qué se hizo con el resultado. | Entradas con lo que se pidió y lo que devolvió la IA, pero sin explicar qué se conservó, qué se cambió o por qué. | Cada uso de IA anotado con lo que se pidió, lo que devolvió, lo que se conservó y lo que se cambió, con el motivo de cada cambio. | Los cambios sobre lo que propuso la IA se justifican con datos de la propia investigación, y el registro permite reconstruir cómo se tomó cada decisión. | RA1-e |

Si no has usado ninguna IA durante el proyecto, indícalo en el `CHANGELOG.md` y el criterio C8 no se tendrá en cuenta en tu nota.

### La auditoría de decisión oral

Cada criterio de la rúbrica se confirma en la **auditoría de decisión oral**, que consiste en que te pregunte por qué tomaste una decisión concreta. Puede ser durante el proyecto o más adelante. Una respuesta válida remite a tu investigación, a tus personas, a tu user flow o a un principio de usabilidad. Respuestas como "es lo que se suele hacer" o "me lo sugirió la IA" indican que esa decisión todavía no es tuya, y en ese caso el criterio correspondiente se queda en Insuficiente, por bien hecho que esté el documento. Por la misma razón, si aparece un uso de IA que no está anotado en el `CHANGELOG.md`, la decisión afectada no se da por justificada.

Guarda bien el texto de tus entrevistas, porque te lo pediré más adelante. Y tenlo en cuenta cuando tengas que decidir en qué emplear el tiempo antes de entregar: un wireframe con algún fallo de forma, pero con decisiones que sabes defender, vale más que uno impecable que no sabes explicar.

---

## Antes de entregar

* La hipótesis inicial sigue en el tablero, con un enlace al `BRIEF.md` del repositorio.
* Hay al menos dos entrevistas en texto, anonimizadas y con el consentimiento registrado.
* Cada rasgo de cada persona tiene su dato, y las suposiciones están marcadas.
* Cada función descartada del MVP lleva su motivo.
* El user flow tiene punto de entrada, happy path y al menos dos o tres casos límite.
* El user flow se recorre sobre el sitemap sin huecos y con los mismos nombres.
* Cada frame de Figma Design se llama igual que su pantalla en el sitemap.
* El prototipo se recorre de principio a fin y, si lo has probado, los resultados de la prueba están anotados.
* El brief final está en el `BRIEF.md` del repositorio, enlazado desde el `README.md`, con sus cinco elementos, incluida la restricción ambiental.
* Has revisado la ortografía y la redacción de todos los textos: brief, fichas, notas y anotaciones del flujo.
* El tablero está ordenado siguiendo los pasos del proyecto y cada zona tiene su título.
* Los elementos que se repiten en los wireframes son componentes y todas las pantallas parten de la misma plantilla.
* El `CHANGELOG.md` recoge cada uso de IA del proyecto, con lo que pediste, lo que conservaste, lo que cambiaste y por qué.
* Los dos archivos de Figma tienen guardada la versión "Entrega Órbita 1" y todos los enlaces se abren en una ventana privada.
