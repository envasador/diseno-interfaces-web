# Semana 4 — Cómo se organiza y se cierra

**Órbita 1 · 5 horas · 3 sesiones**

---

## Sesión A (2h) — Card sorting y sitemap

### Antes de clase
Tarjetas de card sorting listas en FigJam. Saber con qué dos compañeros se trabaja.

### En clase

**Primera parte (40 min) — Card sorting en grupos de tres**

Cada alumno pasa sus tarjetas a los otros dos miembros del grupo para que las agrupen de forma independiente y en silencio, y nombren cada grupo. El alumno propietario observa y toma nota sin intervenir. Con tres agrupamientos distintos ya se ven los puntos de consenso y los de divergencia.

**Segunda parte (80 min) — Construir el sitemap**

Con los datos del card sorting y los flujos de la semana anterior, cada alumno construye el sitemap en FigJam: pantallas principales, secundarias y de sistema, diferenciadas visualmente.

Verificación inmediata al terminar: ¿cada flujo crítico puede recorrerse en tres niveles o menos? Si un flujo exige saltar entre ramas alejadas, la arquitectura está penalizando una tarea importante.

### Para cerrar
El alumno señala en el sitemap qué secciones llegan al tercer nivel y anota si esa profundidad está justificada por sus personas o llegó por inercia.

### Entregable
Sitemap verificado contra los flujos.

---

## Sesión B (2h) — Cerrar el brief

### Antes de clase
Leer el apartado 6 de la Órbita 1.
Llegar con un borrador del brief escrito.

### En clase

**Primera parte (30 min) — Los cinco elementos del brief**

El profesor revisa con el grupo los cinco elementos: problema respaldado por datos, alcance, personas referenciadas, criterios de éxito verificables y restricciones.

Énfasis en los criterios de éxito: tienen que poder comprobarse. "La interfaz es fácil de usar" no es verificable. "[Persona primaria] puede completar [tarea crítica] sin ayuda en menos de [tiempo]" sí lo es. Y son exactamente los que usarás en la Órbita 5.

**Segunda parte (90 min) — Cerrar y ordenar**

Cada alumno cierra el brief en FigJam y ordena el tablero completo. El tablero tiene que poder leerse en 30 segundos sin que el alumno esté presente para explicarlo. Primera versión definitiva del `CHANGELOG.md` con todos los usos de herramientas de la Órbita 1.

### Para cerrar
La capa 0 está completa y ordenada.

### Entregable
Capa 0 completa: brief + personas + flujos + sitemap.

---

## Sesión C (1h) — Galería de la capa 0

### Antes de clase
El tablero terminado y ordenado. Brief legible en 30 segundos sin explicación oral.

### En clase

**Galería (25 min)**

Todos los tableros abiertos a la vez. Cada alumno recorre los proyectos de sus compañeros y deja exactamente dos comentarios escritos por tablero:

- Una pregunta de auditoría de decisión: "¿de dónde sale esta frustración?", "¿por qué esta sección está en el primer nivel?", "¿qué dato respalda este objetivo?"
- Una observación concreta: "la persona con diversidad funcional no tiene tecnología de apoyo definida", "el flujo de pago no tiene caso límite para error de tarjeta"

Los comentarios quedan en el tablero como registro permanente.

**Puesta en común (25 min)**

El profesor selecciona cuatro o cinco tableros para comentar con el grupo. No los mejores, sino los más útiles pedagógicamente: el que tiene la persona más específica, el flujo con los casos límite mejor resueltos, y alguna decisión que merece discutirse porque podría haberse tomado de otra manera.

### Para cerrar
Cada alumno lee los comentarios recibidos y anota en el `CHANGELOG.md` qué va a revisar y por qué. **Fin de la Órbita 1.**

### Entregable
Capa 0 evaluada con feedback incorporado. Órbita 1 cerrada ✓
