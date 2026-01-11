## 3. Cómo gestionar la accesibilidad en un proyecto

### 3.1. Accesibilidad desde el diseño (no como parche)

**El error común:**
Diseñar toda la web, desarrollarla, y al final "añadir accesibilidad". Resultado: trabajo duplicado, frustraciones, compromisos de calidad.

**La forma correcta:**
La accesibilidad se integra **desde el inicio**, en cada fase:

#### Fase de diseño (Figma/Sketch)

**Contraste de color:**
Mientras eliges la paleta, verifica contraste. Herramientas:
- Plugin de Figma "Contrast" o "Stark"
- WebAIM Contrast Checker: https://webaim.org/resources/contrastchecker/

**Tamaño de elementos interactivos:**
Botones, enlaces, campos de formulario: mínimo 24×24 píxeles (WCAG 2.2), idealmente 44×44px.

**No solo color para información:**
Si diseñas un gráfico donde "verde = positivo, rojo = negativo", añade también iconos (✓ y ✗) o patrones.

**Orden visual = orden del código:**
Si diseñas un layout donde visualmente el elemento A está arriba del B, asegúrate de que en el código HTML A esté antes que B. El orden lógico importa para teclado y lectores de pantalla.

#### Fase de contenido (copywriting)

**Textos alternativos informativos:**
No escribas `alt="imagen"`. Escribe qué **información aporta** la imagen. "Gráfico de barras mostrando 45% de crecimiento en ventas Q4 respecto a Q3".

**Encabezados jerárquicos:**
Estructura el contenido con H1, H2, H3 lógicos. No uses H3 porque "se ve bien en tamaño", úsalo porque es una subsección de H2.

**Lenguaje claro:**
Evita jerga innecesaria. Si tu audiencia es general, escribe para nivel de lectura de secundaria.

**Enlaces descriptivos:**
No "click aquí". Sí "descarga la guía completa de accesibilidad web (PDF, 2MB)".

#### Fase de desarrollo

**HTML semántico:**
Usa `<button>` para botones, `<nav>` para navegación, `<main>` para contenido principal, `<article>` para artículos. No todo son `<div>`.

**Formularios con `<label>`:**
Cada campo con su etiqueta asociada. Mensajes de error claros y asociados con `aria-describedby`.

**Navegación por teclado:**
Prueba constantemente con Tab. ¿Puedes hacer todo sin ratón?

**ARIA solo cuando es necesario:**
HTML nativo es preferible. Solo usa ARIA cuando HTML no ofrece la semántica necesaria (widgets complejos como tabs, acordeones personalizados).

### 3.2. El rol del equipo

**Diseñador:**
- Verifica contraste
- Diseña estados de foco visibles
- Documenta comportamientos interactivos (¿cómo se navega este menú con teclado?)

**Desarrollador frontend:**
- Implementa HTML semántico
- Asegura navegación por teclado
- Añade ARIA cuando corresponde
- Prueba con lectores de pantalla

**Creador de contenido:**
- Escribe textos alternativos descriptivos
- Crea estructura de encabezados lógica
- Proporciona transcripciones para multimedia

**QA (testing):**
- Auditorías automáticas (Lighthouse, axe)
- Testing manual con teclado
- Testing con lectores de pantalla
- Testing con usuarios reales con discapacidad (ideal)

### 3.3. Herramientas de auditoría

#### Herramientas automáticas

**Lighthouse (Chrome DevTools):**
Integrado en Chrome. Audita accesibilidad, performance, SEO. Da puntuación y lista problemas concretos.
- Abre DevTools → pestaña Lighthouse → Generate report

**axe DevTools:**
Extensión de navegador. Más detallada que Lighthouse. Explica cada problema y cómo solucionarlo.
- Chrome/Firefox extension: https://www.deque.com/axe/devtools/

**WAVE:**
Herramienta visual que muestra directamente en la página dónde están los problemas de accesibilidad.
- Web: https://wave.webaim.org/
- Extensión de navegador disponible

**Importante:** Las herramientas automáticas detectan ~30-40% de problemas. El resto requiere testing manual.

#### Testing manual esencial

**Navegación por teclado:**
Desconecta el ratón. Usa solo teclado:
- Tab: siguiente elemento interactivo
- Shift+Tab: anterior
- Enter: activar botón/enlace
- Espacio: activar botón, checkbox
- Escape: cerrar modal

¿Funciona todo? ¿Ves dónde está el foco? ¿Quedas atrapado en algún sitio?

**Zoom de texto:**
Navegador → Zoom texto al 200%. ¿Todo sigue visible y funcional? ¿Aparecen scrolls horizontales? ¿Se superpone texto?

**Lectores de pantalla (básico):**
Activa el lector de pantalla nativo:
- Windows: NVDA (descargar gratis: https://www.nvaccess.org/)
- macOS: VoiceOver (Cmd+F5)
- iOS: VoiceOver en Settings → Accessibility
- Android: TalkBack en Settings → Accessibility

Navega tu sitio. ¿Se anuncia todo correctamente? ¿Los nombres de botones tienen sentido? ¿Se leen las imágenes?

**Contraste:**
Usa la herramienta de contraste de DevTools o WebAIM Contrast Checker. Verifica todo texto/iconografía contra su fondo.

### 3.4. Documentación de accesibilidad

En proyectos profesionales, documenta:

**Declaración de accesibilidad:**
Página pública explicando:
- Nivel de conformidad alcanzado (WCAG 2.1 AA)
- Fecha de la última evaluación
- Problemas conocidos y timeline de solución
- Forma de contacto para reportar problemas

**Guía de implementación interna:**
Para el equipo:
- Checklist de accesibilidad (qué verificar antes de cada release)
- Ejemplos de código accesible (componentes reutilizables)
- Procesos de testing

**Informe de auditoría:**
Después de cada auditoría:
- Qué se probó
- Problemas encontrados (priorizados por severidad)
- Soluciones propuestas
- Estado (pendiente, en progreso, resuelto)

