# Órbita 1 — Conocer a las personas
## Hoja de ruta

<div style="background:#1F0318; border:3px solid #1F0318; box-shadow:6px 6px 0 #E93456; padding:28px 36px; display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:24px; margin:32px 0;">
  <div>
    <p style="margin:0 0 8px 0; color:#FFB8DE; font-weight:700; text-transform:uppercase; letter-spacing:1px; font-size:0.85rem;">Diapositivas del apartado</p>
    <p style="margin:0; color:#ffffff; font-size:1.1rem; font-weight:600;">Los ocho pasos de la Órbita 1: qué se hace, con qué herramienta y qué produce cada uno.</p>
  </div>
  <a href="../slides/orbita1_00_hoja_de_ruta.pdf" target="_blank" rel="noopener" style="background:#E93456 !important; color:#ffffff !important; border:3px solid #1F0318 !important; box-shadow:4px 4px 0 #1F0318 !important; padding:14px 28px; font-weight:700; text-transform:uppercase; letter-spacing:1px; text-decoration:none !important; white-space:nowrap; border-bottom:none !important;">Descargar presentación →</a>
</div>


Esta guía secuencia el trabajo de la órbita. Cada paso indica qué se hace, con qué herramienta y qué produce. Los apartados de los apuntes desarrollan el cómo de cada paso. El reparto de horas por sesión está en la programación de aula; aquí solo importa el orden.

![Hoja de ruta de la Órbita 1 en ocho pasos](img/orbita1_00_esquema_hoja_de_ruta.svg)

### Paso 1 — Definir la hipótesis de proyecto

Eliges el problema que tu producto va a resolver y lo formulas como **hipótesis**: "creo que las personas que [contexto] necesitan [objetivo] pero [fricción]". Abres el tablero de FigJam y el repositorio de GitHub con el `CHANGELOG.md` vacío. La hipótesis es provisional: los pasos siguientes la confirmarán, la matizarán o la desmontarán.

Produce: **hipótesis escrita en el tablero** + repositorio inicializado.

### Paso 2 — Investigar el terreno

Analizas dos o tres productos de referencia que ya operan sobre el mismo problema. Aplicas el **test de los cinco segundos** con Lyssna sobre una pantalla de cada uno para saber qué comunican en una primera impresión, y tomas nota de su estructura, su vocabulario y sus fricciones. En paralelo lanzas una **encuesta** con Tally para detectar patrones y reclutar entrevistados.

Produce: notas de análisis de referentes + resultados del test de 5 segundos + encuesta lanzada.

### Paso 3 — Entrevistar

Con las respuestas de la encuesta identificas perfiles y entrevistas a cinco o seis personas que encajen en ellos. Preguntas abiertas, foco en comportamiento real, **registro de consentimiento** y **datos anonimizados**. Las notas van al tablero de FigJam, una nota adhesiva por hallazgo.

Produce: notas de entrevista anonimizadas en FigJam.

### Paso 4 — Sintetizar y construir las personas

**Affinity mapping** sobre todas las notas: agrupas hallazgos por afinidad y los grupos que emergen revelan los patrones. De ahí salen tus dos o tres personas (una con diversidad funcional), cada una con su ficha: cita, contexto de uso, objetivos y frustraciones. Cada atributo debe poder rastrearse hasta un dato concreto. Si usas IA para la síntesis, primera entrada en el `CHANGELOG.md`.

Produce: fichas de personas en Figma, con jerarquía definida.

### Paso 5 — Definir el MVP y mapear el user flow

Partes de tu persona primaria y sus objetivos para separar las funcionalidades candidatas en dos columnas, dentro y fuera del MVP, con un criterio de decisión para cada una: si es necesaria para la tarea principal de tu persona primaria, si es viable en el tiempo del módulo y si tiene alternativa aceptable mientras tanto. El resultado es una lista corta y defendible.

Con el MVP acotado, mapeas en FigJam un único flujo que lo recorre de principio a fin, con el **happy path** completo y al menos dos o tres **casos límite** en los puntos más críticos. Si detectas una tarea crítica que ese flujo no cubre, mapeas un flujo complementario. Recorres el flujo con cada persona como filtro, especialmente la de diversidad funcional, y anotas las decisiones que quedan abiertas.

Produce: MVP definido, con lo que queda fuera justificado, y user flow completo del MVP (más flujos complementarios si procede) con casos límite anotados.

### Paso 6 — Card sorting y sitemap

**Card sorting** con cuatro o cinco compañeros. Con los agrupamientos resultantes y las funcionalidades de tu MVP, construyes el **sitemap**: pantallas principales, secundarias y de sistema. Verificación cruzada: todo lo que está dentro del MVP tiene dónde vivir en el sitemap, y el user flow del paso anterior se puede recorrer sobre él sin huecos.

Produce: sitemap verificado contra el MVP y el user flow.

### Paso 7 — Wireframear y prototipar

Con el sitemap y el user flow como referencia, produces los **wireframes lo-fi** en Figma: una pantalla por cada nodo del sitemap que aparece en el flujo, en escala de grises, sin tipografía real ni color. Nombras cada frame con el nombre que tiene esa pantalla en el sitemap. Una vez tienes todas las pantallas, las conectas con interacciones básicas para formar el **prototipo navegable**. Lo testeas con cuatro o cinco personas del perfil de tu persona principal usando Lyssna.

Produce: wireframes lo-fi + prototipo navegable en Figma, con resultados del test anotados.

### Paso 8 — Cerrar el brief y entregar

Conviertes la hipótesis del paso 1 en **brief definitivo**: problema respaldado por datos, alcance acotado por el MVP, personas referenciadas, criterios de éxito verificables y restricciones. Revisas que los seis artefactos estén vinculados entre sí y que el `CHANGELOG.md` recoja todos los usos de IA de la órbita.

Produce: entregable completo de la Órbita 1 — brief, personas, MVP con user flow, sitemap, wireframes y prototipo navegable.

---

Los pasos no llevan asignada una franja de horas fija: repártelos según el ritmo real del grupo. La Órbita 1 completa ocupa unas 20 horas de clase, repartidas a lo largo de las primeras cuatro semanas del curso.
