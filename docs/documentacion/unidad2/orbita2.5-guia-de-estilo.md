## 5. Guías de estilo (Style Guides)

### Qué es una guía de estilo y por qué la necesitas

Una guía de estilo es la biblia visual de tu proyecto. Es el documento central donde defines y documentas todas las decisiones de diseño: colores, tipografías, espaciado, componentes, iconos, reglas de uso. Es tu fuente única de verdad. Todo lo que diseñes debe estar reflejado aquí, y todo lo que desarrollen debe basarse en esto.

Sin una guía de estilo, cada nueva pantalla se convierte en una decisión arbitraria. "¿Qué azul uso aquí?", "¿Este botón va en Bold o Semibold?", "¿Cuánto espacio dejo entre estos elementos?". Con una guía de estilo, todas esas preguntas ya están respondidas. La consistencia no es un detalle estético, es lo que hace que un producto parezca profesional. Y la velocidad importa: diseñas más rápido porque no pierdes tiempo decidiendo cosas que ya están definidas.

**Por qué importa:**
- **Consistencia**: Todos usan las mismas reglas, todo se ve coherente
- **Velocidad**: No pierdes tiempo decidiendo cosas que ya están definidas
- **Escalabilidad**: El proyecto crece pero mantiene cohesión visual
- **Comunicación**: Diseño y desarrollo entienden exactamente qué usar y cómo

### Estructura de una guía de estilo

Una guía de estilo bien organizada se divide en tres grandes bloques que se construyen uno sobre otro. Los fundamentos son los elementos base (colores, tipografías, espaciado) que defines primero. Luego vienen los componentes, piezas reutilizables construidas con esos fundamentos. Y finalmente los patrones de uso, reglas que explican cómo combinar todo correctamente. Esta estructura en capas hace que la guía sea escalable: cuando añades un componente nuevo, los fundamentos ya están establecidos y solo documentas la nueva pieza.

**1. Fundamentos (Foundations)**

Los fundamentos son la base de todo tu sistema visual. Son los ingredientes con los que cocinas: si estos ingredientes están mal definidos o son inconsistentes, todo lo que construyas después estará comprometido. Aquí defines tu paleta de colores completa, tu sistema tipográfico, tu sistema de espaciado, tu grid para layouts, y tu librería de iconos. Estos elementos se definen una vez y se reutilizan constantemente en todos los componentes.

**Colores:**
- Paleta completa con muestras visuales
- Códigos HEX/RGB/HSL de cada color
- Nombres claros: Primary 500, Gray 700, Success 500
- Descripción de uso:
  - Primary: acciones principales, enlaces, CTAs
  - Accent: énfasis, notificaciones importantes
  - Semantic: feedback del sistema (éxito, error, warning, info)
  - Grays: textos, fondos, bordes

**Tipografía:**

Documenta las familias usadas con enlaces a Google Fonts si son gratuitas, y muestra tu escala completa con ejemplos visuales reales. No escribas "Heading 1" genérico, escribe el texto de ejemplo usando realmente ese estilo.

- Familias tipográficas usadas
- Escala completa con ejemplos visuales (H1, H2, H3, Body, Caption)
- Para cada nivel: familia, tamaño, peso, line-height, color, cuándo usarlo

**Espaciado:**

El espaciado necesita una escala visual clara. Muestra rectángulos o barras que representen cada valor. La regla base es siempre múltiplos de 4 u 8, y debes dar ejemplos concretos de aplicación.

```
4px   ■
8px   ■■
16px  ■■■■
24px  ■■■■■■
32px  ■■■■■■■■
48px  ■■■■■■■■■■■■
64px  ■■■■■■■■■■■■■■■■
```

- 8px: entre elementos muy relacionados
- 16px: entre elementos relacionados
- 32px: entre secciones
- 64px: entre bloques principales

**Grid y Layout:**
- Grid de 12 columnas (estándar web), gutter 24px
- Breakpoints: Móvil (320-767px, 4 col), Tablet (768-1023px, 8 col), Desktop (1024px+, 12 col)
- Márgenes laterales: Móvil 16px, Tablet 24px, Desktop 48px

**Iconos:**
- Librería usada (Heroicons, Feather, etc.)
- Estilo (outline o filled), tamaños estándar (16px, 20px, 24px, 32px)
- Grid visual con todos los iconos disponibles

**2. Componentes (Components)**

Los componentes son las piezas prefabricadas de tu interfaz. En lugar de diseñar cada botón desde cero cada vez, defines el botón una vez aquí con todas sus variantes y todos sus estados. Esta sección documenta cada pieza reutilizable con especificaciones técnicas precisas: dimensiones, padding, colores, tipografías, sombras. Cuanto más detallada sea esta documentación, menos fricción habrá entre diseño y desarrollo.

Para cada componente necesitas documentar varios aspectos críticos. Primero su anatomía (las partes que lo forman), luego sus variantes (Primary, Secondary, Ghost), los tamaños disponibles (Small, Medium, Large), todos los estados posibles (Default, Hover, Active, Disabled), las especificaciones técnicas exactas (padding, colores, bordes), y lo más importante: cuándo usar cada variante.

**Ejemplo de documentación de botones:**

- **Primary**: Acción principal (solo 1 por pantalla) - "Comprar", "Guardar", "Enviar"
- **Secondary**: Acciones alternativas - "Cancelar", "Volver", "Ver detalles"
- **Ghost**: Acciones terciarias - "Saltar", "Más info", "Leer más"
- **Danger**: Acciones destructivas - "Eliminar cuenta", "Borrar archivo"

**Componentes básicos imprescindibles:**
- Botones (todas variantes y estados)
- Inputs y formularios (text, textarea, select, checkbox, radio, toggle)
- Cards (contenedores de información)
- Navegación (header, sidebar, breadcrumbs, tabs)
- Feedback (alerts, toasts, modals, loaders)
- Listas y tablas

**3. Patrones de uso (Usage Patterns)**

No basta con mostrar los componentes, hay que enseñar cómo usarlos correctamente. Los patrones de uso son las reglas del juego que previenen los errores más comunes: jerarquía de botones (solo 1 Primary por pantalla), espaciado consistente, uso correcto de colores semánticos. Esta sección asegura que todo el equipo aplica los componentes de la misma forma.

**Jerarquía de botones:**
- Solo 1 botón Primary por pantalla/sección
- Si hay varias acciones, una es Primary y las demás Secondary o Ghost
- Nunca dos Primary juntos

**Espaciado consistente:**
- Entre elementos muy relacionados: 8-12px
- Entre elementos relacionados: 16-24px
- Entre secciones: 32-48px
- Entre bloques principales: 64px+

**Uso de colores semánticos:**
- Success (verde): Solo para confirmaciones positivas
- Error (rojo): Solo para errores y validaciones fallidas
- Warning (naranja): Solo para advertencias no críticas
- Info (azul): Solo para información neutral

### Cómo crear tu guía de estilo en Figma

Crear tu guía de estilo en Figma es más simple de lo que parece. El truco está en organizarla bien desde el principio y documentar visualmente, no solo con texto. Una guía bien diseñada es consultable de un vistazo: ves el color, ves el código, ves el uso. No necesitas leer párrafos enteros para entender qué hacer.

**Pasos básicos:**

1. **Crea una página dedicada** llamada "Style Guide" o "Design System" (solo documentación)
2. **Organiza por secciones** con frames grandes: Colors, Typography, Spacing, Icons, Components
3. **Documenta visualmente**: Para colores muestra cuadrado + nombre + código + descripción. Para componentes muestra todos los estados lado a lado con anotaciones
4. **Usa Auto Layout** en todos los componentes para que sean flexibles
5. **Crea un índice** al inicio para facilitar la navegación

### Mantener la guía actualizada

Una guía de estilo no es un documento estático. Es un documento vivo que evoluciona con tu proyecto. Cada vez que añades un componente nuevo, lo documentas. Cada vez que cambias un color o una tipografía, actualizas la guía. Versiona claramente (v1.0, v1.1, v2.0) y comunica los cambios al equipo cuando actualices.

### Exportar y compartir

Tu guía debe ser accesible para todo el equipo, especialmente para desarrollo. Usa plugins como "Design Tokens" para exportar colores y espaciado a JSON. Documenta los nombres exactos de tus Color Styles y Text Styles porque esos nombres deben coincidir entre diseño y código. Comparte el link de Figma con permisos "View only" para que desarrollo pueda inspeccionar componentes y extraer especificaciones.

### Herramientas complementarias

Si tu proyecto crece mucho, existen herramientas más potentes que Figma solo: Storybook para documentación interactiva de componentes en código, Zeroheight para sincronizar Figma con una web de documentación, o Frontify para brand guidelines completas. Pero para este módulo, Figma es más que suficiente.

### Para profundizar

Estudia guías de estilo públicas de empresas grandes para ver cómo lo hacen los mejores:

- **[Material Design](https://m3.material.io)** (Google) - Estándar de Android, documentación exhaustiva
- **[Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/)** (Apple) - Estándar de iOS/macOS
- **[Carbon Design System](https://carbondesignsystem.com)** (IBM) - Sistema completo con código
- **[Atlassian Design System](https://atlassian.design)** - Sistema de Jira, Confluence, Trello
- **[Creating a Design System](https://www.figma.com/resources/learn-design/systems/)** (Figma) - Guía oficial
