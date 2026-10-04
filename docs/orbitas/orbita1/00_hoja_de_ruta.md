# Órbita 1 — Conocer a las personas
## Hoja de ruta

Cuando se empieza a diseñar una aplicación, lo más habitual es querer abrir una herramienta de diseño y ponerse a dibujar pantallas cuanto antes. En este módulo vamos a hacerlo al revés: primero vas a averiguar a quién le vas a resolver el problema y qué necesita, y solo después empezarás a dibujar. Ese trabajo previo se organiza en ocho pasos que irás dando a lo largo de las cuatro primeras semanas del curso. No hace falta que te los aprendas de memoria, porque para eso tienes esta página, pero sí conviene que respetes el orden, ya que cada paso utiliza lo que has obtenido en el anterior y saltarte alguno te obligará a volver atrás más adelante.

![Hoja de ruta de la Órbita 1 en ocho pasos](img/orbita1_00_esquema_hoja_de_ruta.svg)

### Paso 1: Plantea una hipótesis, aunque no estés seguro de acertar

Todo proyecto empieza con una suposición: crees que un grupo de personas, en una situación concreta, necesita algo que ahora mismo no tiene bien resuelto. A esa suposición la llamamos **hipótesis**, y se escribe con una frase muy sencilla: "creo que las personas que [contexto] necesitan [objetivo] pero [dificultad]". En este primer paso también vas a crear el tablero de FigJam en el que trabajarás todo el curso y el repositorio de GitHub del proyecto, con un archivo `CHANGELOG.md` vacío.

No te preocupes si la hipótesis no es perfecta, porque los pasos siguientes sirven precisamente para comprobarla, matizarla o cambiarla por completo si los datos te llevan por otro lado. De hecho, si llegas al final de la órbita con la misma hipótesis que escribiste el primer día, lo más probable es que no hayas investigado lo suficiente.

### Paso 2: Estudia lo que ya existe

Es muy probable que alguien haya intentado resolver antes un problema parecido al tuyo, así que antes de inventar nada conviene ver qué ha hecho. Busca dos o tres aplicaciones o webs que traten el mismo problema (las llamaremos **referentes**) y aplica a una pantalla de cada una el **test de los cinco segundos** con Lyssna, que consiste en enseñar la pantalla a alguien durante cinco segundos y preguntarle qué ha entendido. Anota también cómo están organizadas, qué palabras usan y en qué puntos se atascan sus usuarios.

Al mismo tiempo, prepara una **encuesta** con Tally. Te servirá para detectar tendencias en un grupo más amplio de gente y, además, para encontrar a las personas a las que entrevistarás en el paso siguiente.

### Paso 3: Entrevista a personas reales

Con las respuestas de la encuesta ya podrás distinguir varios perfiles. Elige a cinco o seis personas que encajen en ellos y entrevístalas. Haz preguntas abiertas y céntrate en lo que hacen de verdad, porque lo que la gente dice que haría suele ser bastante más optimista que lo que hace. Antes de empezar, cada persona tiene que dar su consentimiento, y en tus notas los datos deben aparecer anonimizados desde el principio. Cada cosa interesante que descubras irá en una nota adhesiva del tablero de FigJam.

Esta es la parte del proceso que menos se puede delegar en una IA, porque es en la conversación real, con sus silencios y sus rodeos, donde aparecen las cosas que nadie te contaría si le hicieras la pregunta directamente.

### Paso 4: Convierte tus notas en personas

Al terminar las entrevistas tendrás muchas notas sueltas que, por sí solas, todavía no dicen gran cosa. Para ordenarlas vas a usar el **affinity mapping**, una técnica que consiste en agrupar las notas que se parecen y dejar que los grupos se formen solos, sin forzarlos para que encajen en categorías que ya tenías pensadas. De esos grupos saldrán tus dos o tres **personas**, que son fichas que describen a los usuarios típicos de tu aplicación. Una de ellas tendrá algún tipo de diversidad funcional, con el mismo peso que las demás, y cada ficha recogerá una cita, el contexto en el que esa persona usaría la aplicación, sus objetivos y sus frustraciones.

Para saber si una persona está bien construida, comprueba que cada dato de su ficha procede de algo concreto que averiguaste en la investigación. Si no sabes decir de dónde sale un dato, se trata de una suposición tuya y hay que marcarla como tal o eliminarla. Si usas una IA para ayudarte a ordenar las notas, ese será el primer registro de tu `CHANGELOG.md`.

### Paso 5: Decide qué incluye la primera versión y dibuja cómo se usa

Seguramente se te ocurrirán muchas funciones para tu aplicación, pero la primera versión tiene que limitarse a lo imprescindible. A esa versión mínima la llamamos **MVP** (producto mínimo viable). Para definirla, parte de tu persona principal y de sus objetivos, y reparte las funciones en dos columnas, las que entran y las que se quedan fuera. Cada decisión tiene que tener un motivo, y para encontrarlo te ayudarán tres preguntas: si tu persona principal la necesita para su tarea más importante, si puedes construirla con el tiempo que tienes y si puede esperar a una versión posterior. Lo que se quede fuera no se pierde, porque lo apuntarás para más adelante.

Cuando tengas claro el MVP, dibuja en FigJam un **user flow**, que es un diagrama con los pasos que sigue una persona para usar tu aplicación de principio a fin. Primero dibuja el recorrido en el que todo sale bien y después añade al menos dos o tres situaciones en las que algo puede fallar. Si descubres una tarea importante que ese recorrido no cubre, dibújala en un diagrama aparte. Por último, recorre el diagrama poniéndote en el lugar de cada una de tus personas, sobre todo de la que tiene diversidad funcional, porque es con ella con quien más fácilmente descubrirás lo que se te había pasado por alto.

### Paso 6: Organiza las pantallas de tu aplicación

Pide a cuatro o cinco compañeros que te ayuden con un **card sorting**, una técnica que consiste en darles una tarjeta por cada pantalla o función de tu MVP para que las agrupen como les parezca más lógico, sin que tú intervengas. Con los grupos que salgan construirás el **sitemap**, un esquema en forma de árbol con todas las pantallas de la aplicación, en el que la página de inicio ocupa la raíz y se distinguen las pantallas principales, las secundarias y las de sistema (como el inicio de sesión o los mensajes de error).

Antes de darlo por terminado, comprueba dos cosas: que cada función de tu MVP tiene su sitio en el sitemap y que el user flow del paso anterior se puede recorrer sobre esta estructura sin que falte ninguna pantalla.

### Paso 7: Dibuja las pantallas, todavía sin color

Con el sitemap y el user flow delante, dibuja en Figma Design los **wireframes**, que son bocetos sencillos de las pantallas. Harás uno por cada pantalla que aparezca en el user flow, usando solo blanco, negro y gris, sin tipografías reales ni imágenes. A cada boceto ponle el mismo nombre que tiene esa pantalla en el sitemap, porque así te resultará mucho más fácil relacionar unos documentos con otros más adelante.

Después, enlaza las pantallas entre sí para que al pulsar un botón se pase a la siguiente. Así obtendrás un **prototipo navegable**. Pruébalo en Lyssna con cuatro o cinco personas que se parezcan a tu persona principal: dales una tarea y no les expliques nada. Si en algún momento necesitas intervenir para que entiendan qué tienen que hacer, has encontrado un problema que debes resolver.

### Paso 8: Cierra el brief y entrega

En este último paso, la hipótesis del primer día se convierte en el **brief** definitivo, un documento breve que recoge el problema respaldado por tus datos, lo que incluye la primera versión, las personas, unos criterios para comprobar si el diseño funciona y las limitaciones del proyecto. Revisa también que los seis documentos de la órbita estén enlazados entre sí y que el `CHANGELOG.md` recoja todas las veces que has usado una IA.

Una buena forma de saber si has terminado es enseñarle el tablero a alguien que no conozca tu proyecto, sin darle ninguna explicación. Si lo entiende sin que tengas que explicarle nada, el trabajo está listo.

---

Estos ocho pasos no tienen un número de horas fijo, porque cada grupo lleva su propio ritmo. En total ocupan unas 20 horas de clase repartidas a lo largo de las cuatro primeras semanas del curso.
