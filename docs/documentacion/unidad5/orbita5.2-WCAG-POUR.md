## 2. Principios fundamentales: WCAG y POUR

### 2.1. ¿Qué son las WCAG?

Las **Web Content Accessibility Guidelines (WCAG)** son el estándar internacional de accesibilidad web, desarrollado por el **W3C** (World Wide Web Consortium), la organización que define los estándares web.

**Versiones:**
- **WCAG 2.1 (junio 2018):** Versión actual consolidada, exigida legalmente
- **WCAG 2.2 (octubre 2023):** Actualización reciente, retrocompatible con 2.1
- **WCAG 3.0 (en borrador):** Futuro, no lista para producción

Para proyectos actuales: **enfócate en WCAG 2.1 nivel AA**, que es lo exigido legalmente y cubre la inmensa mayoría de necesidades.

### 2.2. Los cuatro principios: POUR

WCAG se organiza en torno a cuatro principios, recordados por el acrónimo **POUR**:

#### Perceptible

**"La información debe presentarse de forma que los usuarios puedan percibirla"**

No puedes interactuar con algo que no puedes percibir.

**Ejemplos:**
- **Alternativas textuales:** Toda imagen informativa tiene descripción textual (atributo `alt`). Una persona con ceguera usando lector de pantalla "escucha" la descripción en vez de ver la imagen.
- **Subtítulos en vídeos:** Personas con sordera o en contextos sin audio pueden seguir el contenido.
- **Contraste suficiente:** Texto con contraste bajo es invisible para personas con baja visión. Mínimo 4.5:1 para texto normal.
- **No solo color:** No transmitas información únicamente con color. "Los campos en rojo son obligatorios" → una persona con daltonismo no distingue rojo. Añade iconos o texto.

#### Operable

**"Los componentes de la interfaz y la navegación deben ser operables"**

Los usuarios deben poder interactuar con todos los elementos.

**Ejemplos:**
- **Todo accesible por teclado:** Personas con movilidad reducida o ceguera no usan ratón. Todos los botones, enlaces, menús deben funcionar con teclado (Tab, Enter, Escape, flechas).
- **Tiempo suficiente:** No uses timeouts automáticos sin opción de extender. Personas con discapacidad cognitiva o motora necesitan más tiempo.
- **Sin parpadeos rápidos:** Contenido que parpadea más de 3 veces por segundo puede causar ataques epilépticos.
- **Navegación clara:** Múltiples formas de encontrar contenido (menú, buscador, mapa del sitio). Indicadores de ubicación (estás en "Inicio > Productos > Zapatillas").

#### Comprensible

**"La información y el manejo de la interfaz deben ser comprensibles"**

No basta con percibir y operar. Debes **entender** qué estás viendo y cómo usarlo.

**Ejemplos:**
- **Lenguaje claro:** Evita jerga innecesaria. Explica acrónimos y términos técnicos.
- **Comportamiento predecible:** El foco no salta aleatoriamente. Los menús están en el mismo sitio en todas las páginas.
- **Ayuda en formularios:** Campos con etiquetas claras. Errores descriptivos: no solo "Error", sino "El email debe incluir @".
- **Identificación de idioma:** El navegador sabe en qué idioma está la página (`<html lang="es">`) para pronunciar correctamente con lectores de pantalla.

#### Robusto

**"El contenido debe funcionar en diferentes tecnologías, incluyendo tecnologías de asistencia"**

Tu web debe funcionar no solo en Chrome/Firefox actuales, sino también en lectores de pantalla, navegadores antiguos, dispositivos diversos.

**Ejemplos:**
- **HTML válido:** Código bien formado, sin errores. Elementos correctamente anidados.
- **Roles y estados claros:** El navegador/lector de pantalla entiende si algo es botón, enlace, menú, modal.
- **Compatible con tecnologías de asistencia:** Lectores de pantalla (NVDA, JAWS, VoiceOver), magnificadores de pantalla, software de dictado por voz.

### 2.3. Niveles de conformidad: A, AA, AAA

WCAG define tres niveles:

**Nivel A (Mínimo):**
Requisitos más básicos. Si no los cumples, hay barreras muy graves. Ejemplo: imágenes sin texto alternativo, imposible navegar con teclado.

**Nivel AA (Objetivo legal):**
El nivel exigido en legislación española y europea. Incluye criterios como contraste 4.5:1, subtítulos en vídeos, navegación consistente. **Este es tu objetivo**.

**Nivel AAA (Óptimo, opcional):**
El nivel más estricto. Difícil de alcanzar en todo un sitio. Incluye contraste 7:1, lenguaje simplificado máximo, ayuda contextual en todos los formularios. Apunta a AAA donde sea factible, pero no te obsesiones.

**En resumen:** Cumple **AA en toda tu web**. Es el estándar legal y práctico.


