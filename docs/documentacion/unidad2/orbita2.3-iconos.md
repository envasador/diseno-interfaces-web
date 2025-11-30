## 4. Iconos y elementos gráficos

### Los iconos son atajos visuales

Un buen icono comunica instantáneamente su significado sin necesitar explicación. Reconoces un icono de lupa y sabes que es "buscar". Ves tres líneas horizontales y sabes que es un menú. Ves un corazón y sabes que es "favorito" o "me gusta". Esta es la magia de los iconos: son lenguaje visual universal que trasciende idiomas y culturas.

Pero los iconos mal usados generan confusión. Si tu icono necesita que el usuario se detenga a pensar "¿qué significa esto?", has fallado. Los iconos deben reducir fricción cognitiva, no crearla. Por eso la regla fundamental es simple: **usa iconos universales, no inventes**. La lupa significa búsqueda desde hace décadas. El engranaje significa configuración. La papelera significa eliminar. Estas convenciones existen porque funcionan.

### Cuándo usar iconos (y cuándo no)

Los iconos funcionan bien cuando representan **acciones comunes y reconocibles**: búsqueda (lupa), menú (hamburguesa ☰), cerrar (X), configuración (engranaje), usuario/perfil (silueta), compartir (flechas conectadas), descargar/subir (flechas), editar (lápiz), eliminar (papelera).

También funcionan cuando acompañan texto crítico para reforzarlo visualmente: un botón de "Comprar ahora" con icono de carrito, una alerta de "Error al guardar" con icono de advertencia, elementos de navegación donde "Inicio" va acompañado de icono de casa. En estos casos el icono no sustituye al texto, lo complementa.

Son útiles como señales visuales en listas: iconos de categorías en filtros, iconos de estado (completado ✓, pendiente ⏱, error ✗), iconos de tipo de archivo (PDF, DOC, XLS).

**Pero los iconos fallan cuando:**

- **El concepto es abstracto**: ¿Cómo representas "privacidad", "seguridad" o "innovación"? Cualquier opción será arbitraria. Usa texto claro.
- **Son específicos de tu producto**: Funciones únicas sin convención establecida necesitan texto, no solo un icono inventado.
- **El usuario no tiene contexto**: Un menú de navegación solo con iconos obliga al usuario a adivinar. Iconos + texto siempre es más seguro.

### Reglas de oro para usar iconos

**1. Consistencia de estilo absoluta**

Si eliges iconos outline (solo contorno), úsalos en toda la interfaz. Si eliges filled (rellenos), ídem. Nunca mezcles estilos diferentes. La inconsistencia rompe la cohesión visual inmediatamente.

- **Outline**: Líneas finas, moderno, limpio, minimalista
- **Filled**: Rellenos sólidos, más peso visual, más evidentes
- **Duotone**: Dos tonos, más expresivos pero menos comunes

**2. Tamaño y alineación correctos**

Los iconos deben estar proporcionados al contexto:

**Iconos inline (junto a texto):**
- Tamaño: Igual que el texto o 1-2px más grande
- Alineación: Centrados verticalmente (usa flexbox)
- Ejemplo: Texto 16px → icono 16-18px

**Iconos standalone (botones, navegación):**
- Tamaño mínimo: 20px (clickeable)
- Recomendado: 24px
- Área de toque mínima: 44x44px (incluye padding)

**Iconos decorativos:**
- Tamaño: 32-64px o más
- Uso: Ilustrar secciones, estados vacíos, onboarding

**3. Color y estados consistentes**

Un icono debe usar el mismo color que el elemento al que pertenece. Si está en un botón primario azul con texto blanco, el icono debe ser blanco. Si está junto a un enlace azul, el icono debe ser azul. Y cuando el elemento cambia de estado (hover, active, disabled), el icono cambia junto con él.

**4. Acompaña con texto cuando hay duda**

La regla de Nielsen Norman Group: si tienes duda de si el icono es universalmente entendido, añade texto. Especialmente crítico en navegación principal, acciones destructivas (eliminar, borrar) y funciones poco comunes.

Compara: `[🔔] [⚙️] [👤]` (¿qué hace cada uno?) vs `[🔔] Notificaciones  [⚙️] Configuración  [👤] Perfil` (cero ambigüedad).

### Librerías de iconos recomendadas

No diseñes iconos desde cero. Usa librerías probadas, consistentes y gratuitas:

**[Heroicons](https://heroicons.com)**
- Creada por los makers de Tailwind CSS
- Outline y Solid, 292 iconos, SVG optimizados
- **Ideal para**: Interfaces modernas, dashboards, apps

**[Feather Icons](https://feathericons.com)**
- 287 iconos outline minimalistas, líneas finas y elegantes
- **Ideal para**: Interfaces limpias, productos premium

**[Lucide](https://lucide.dev)**
- Fork de Feather con 1000+ iconos
- Misma estética minimalista, actualizaciones activas
- **Ideal para**: Si Feather se te queda corto

**[Material Icons](https://fonts.google.com/icons)**
- De Google, 2000+ iconos en 5 estilos
- **Ideal para**: Si tu diseño usa Material Design

**[Phosphor Icons](https://phosphoricons.com)**
- 6 estilos (Thin, Light, Regular, Bold, Fill, Duotone)
- 1248 iconos, muy versátil

### Formato: SVG siempre

Los iconos en web deben ser SVG, nunca PNG ni icon fonts. SVG es escalable sin perder calidad, pesa poco (KB), es fácil cambiar su color con CSS, y es accesible. Las icon fonts están desactualizadas: pueden fallar al cargar (el usuario ve cuadrados) y tienen problemas de accesibilidad.

**En código:**
```html
<!-- SVG inline (recomendado para iconos pequeños) -->
<svg width="24" height="24" fill="currentColor">
  <path d="..."/>
</svg>
```

**En Figma:**
Importa tu librería como componentes, crea un frame "Icons" con todos organizados, y usa instancias (nunca copies el SVG directamente).

### Ilustraciones y elementos gráficos

Además de iconos funcionales, puedes usar ilustraciones en estados vacíos ("No tienes mensajes"), onboarding, páginas de error 404, landing pages o secciones hero.

**Reglas básicas:**

1. **Estilo consistente**: Si usas ilustraciones flat (planas), úsalas en toda la interfaz. No mezcles estilos.
2. **Paleta coherente**: Las ilustraciones deben usar colores de tu sistema, no colores random.
3. **No abuses**: Las ilustraciones apoyan el contenido, no compiten con él.

**Recursos gratuitos:**
- **[Undraw](https://undraw.co)**: Flat personalizables por color
- **[Storyset](https://storyset.com)**: Ilustraciones animadas (Lottie)
- **[Humaaans](https://www.humaaans.com)**: Personajes modulares
- **[Blush](https://blush.design)**: Colección de varios estilos

### Para profundizar

- **Icons as Part of a Great User Experience** (Nielsen Norman Group) - Investigación sobre cuándo los iconos ayudan o confunden.
  [Ver artículo](https://www.nngroup.com/articles/icon-usability/)

- **7 Principles of Icon Design** (Helena Zhang) - Principios fundamentales para iconos efectivos.
  [Ver artículo](https://uxdesign.cc/7-principles-of-icon-design-e7187539e4a2)
