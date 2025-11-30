## 2. Color en interfaces web

### Teoría del color: los fundamentos

Antes de hablar de sistemas de color para interfaces, necesitas entender cómo funcionan los colores y cómo se relacionan entre sí. La teoría del color no es magia ni arte abstracto, es ciencia aplicada a la percepción visual. Y existe desde hace siglos, desde que Isaac Newton publicó su rueda cromática en 1704.

**La rueda de colores y los modelos de color**

La base de todo es el círculo cromático, una representación visual donde los colores están organizados según su relación. Pero dependiendo del medio (impresión o pantalla), usamos diferentes modelos:

**Modelo CMYK** (Cyan, Magenta, Yellow, Black)
- Se usa para **impresión** (revistas, carteles, packaging)
- Funciona con pigmentos que absorben luz
- Colores primarios: Cian, Magenta, Amarillo
- Al mezclar todos los colores → Negro (síntesis sustractiva)

**Modelo RGB** (Red, Green, Blue)
- Se usa para **pantallas** (web, apps, televisión)
- Funciona con luz que emite color
- Colores primarios: Rojo, Verde, Azul
- Al mezclar todos los colores → Blanco (síntesis aditiva)
- **Este es el modelo que usarás en diseño web**

A partir de los colores primarios obtenemos:

- **Colores secundarios**: Se crean mezclando dos primarios
  - Rojo + Verde = Amarillo
  - Verde + Azul = Cian
  - Azul + Rojo = Magenta

- **Colores terciarios**: Se crean mezclando un primario con un secundario adyacente
  - Rojo-naranja, amarillo-naranja, amarillo-verde, azul-verde, azul-cian, magenta-violeta, etc.

**Propiedades del color: Tono, Saturación y Luminosidad**

Para trabajar eficientemente con color digital, necesitas entender el modelo **HSL** (Hue, Saturation, Lightness). Es mucho más intuitivo que RGB o HEX para crear variaciones de color, y una vez lo dominas, puedes construir paletas completas de forma sistemática.

**Tono (Hue) - ¿Qué color es?**

El tono es el color "puro" en sí mismo: rojo, azul, verde, amarillo, naranja, morado... Es lo que normalmente entiendes cuando dices "este es azul" o "este es rojo". Se representa en grados en la rueda cromática, de 0° a 360°, como si fuera un círculo completo:

- **0° / 360°** = Rojo
- **60°** = Amarillo
- **120°** = Verde
- **180°** = Cian
- **240°** = Azul
- **300°** = Magenta

Imagina la rueda cromática como un reloj circular. Si empiezas en el rojo (las 12 en punto = 0°) y vas girando en sentido horario, vas pasando por todos los colores del arcoíris hasta volver al rojo. Cambiar el tono es cambiar de color completamente: pasar de azul a verde, de rojo a naranja, etc.

**Ejemplo práctico:**
- `hsl(220, 80%, 50%)` → El tono es 220°, que corresponde a un azul
- `hsl(120, 80%, 50%)` → El tono es 120°, que corresponde a un verde
- `hsl(0, 80%, 50%)` → El tono es 0°, que corresponde a un rojo

Cambias el primer número (el tono), y cambia completamente el color base.

**Saturación (Saturation) - ¿Qué tan intenso es el color?**

La saturación mide la **pureza o intensidad** del color. Es qué tan "vivo" o "apagado" se ve. Se mide en porcentaje de 0% a 100%:

- **100%** = Color puro, vibrante, intenso, "gritón"
- **50%** = Color apagado, menos vivo, más grisáceo
- **0%** = Gris total, el color ha desaparecido completamente

Piensa en la saturación como si le quitaras o añadieras gris a un color. Con 100% de saturación, el color está "limpio", sin mezcla. Conforme bajas la saturación, es como si le añadieras más y más gris hasta que, en 0%, solo queda el gris.

**Ejemplo práctico con el mismo azul (220°):**
- `hsl(220, 100%, 50%)` → Azul intenso, vibrante, puro
- `hsl(220, 70%, 50%)` → Azul todavía vivo pero menos chillón
- `hsl(220, 40%, 50%)` → Azul apagado, más grisáceo
- `hsl(220, 10%, 50%)` → Azul apenas perceptible, casi gris
- `hsl(220, 0%, 50%)` → Gris puro, el azul ha desaparecido

Mira cómo el tono (220°) y la luminosidad (50%) no cambian, solo la saturación. El color sigue siendo "azul" pero cada vez más apagado.

**Luminosidad (Lightness) - ¿Qué tan claro u oscuro es?**

La luminosidad controla qué tan claro u oscuro es el color, independientemente de su saturación. Se mide en porcentaje de 0% a 100%:

- **100%** = Blanco puro (máxima luz, todo iluminado)
- **50%** = El color en su versión "natural" o "media"
- **0%** = Negro puro (sin luz, todo oscuro)

Piensa en la luminosidad como si ajustaras el brillo de una lámpara que ilumina ese color. Con 100% de luminosidad, hay tanta luz que todo se vuelve blanco. Con 0%, no hay luz y todo es negro. El 50% es el punto medio donde el color se ve en su versión más reconocible.

**Ejemplo práctico con el mismo azul (220°, saturación 80%):**
- `hsl(220, 80%, 90%)` → Azul muy claro, casi celeste pastel
- `hsl(220, 80%, 70%)` → Azul claro, luminoso
- `hsl(220, 80%, 50%)` → Azul "normal", el que reconocerías como azul estándar
- `hsl(220, 80%, 30%)` → Azul oscuro, más profundo
- `hsl(220, 80%, 10%)` → Azul muy oscuro, casi negro azulado

El tono (220°) y la saturación (80%) siguen siendo los mismos, solo cambia cuánta luz hay. El color sigue siendo azul intenso, pero más claro o más oscuro.

**¿Por qué HSL es mejor que RGB o HEX para diseño web?**

Porque puedes crear variaciones coherentes de un mismo color cambiando solo un valor. Si tu color primario es `hsl(220, 80%, 50%)` (un azul), puedes crear toda una escala de azules solo modificando la luminosidad:

```
Primario 900: hsl(220, 80%, 20%)  ← Muy oscuro (tono y saturación iguales)
Primario 700: hsl(220, 80%, 35%)  ← Oscuro
Primario 500: hsl(220, 80%, 50%)  ← Base (tu color principal)
Primario 300: hsl(220, 80%, 70%)  ← Claro
Primario 100: hsl(220, 80%, 90%)  ← Muy claro
```

El tono (220°) y la saturación (80%) se mantienen constantes. Solo cambiaste el tercer valor (luminosidad). Resultado: todos se perciben como "de la misma familia", como variaciones del mismo azul. Esto es fundamental para construir sistemas de diseño escalables y mantener coherencia visual.

Con RGB o HEX tendrías que hacer cálculos complicados para crear estas variaciones, y probablemente no quedarían tan armónicas.

**Variaciones adicionales: tintes, sombras y tonos**

Además de jugar con HSL, existen conceptos tradicionales que describen otras formas de variar un color:

- **Tinte (Tint)**: Color base + blanco → versión más clara (equivale a aumentar luminosidad en HSL)
- **Sombra (Shade)**: Color base + negro → versión más oscura (equivale a reducir luminosidad en HSL)
- **Tono (Tone)**: Color base + gris → versión más apagada (equivale a reducir saturación en HSL)

Estos términos vienen de la pintura tradicional, donde literalmente mezclas pigmentos. En digital, HSL te da el control directo sobre estas propiedades.

**Esquemas de combinación de colores**

No puedes elegir colores al azar y esperar que funcionen bien juntos. Existen fórmulas probadas, esquemas de color que generan armonía visual:

**1. Colores complementarios**
- **Qué son**: Colores opuestos en la rueda cromática
- **Ejemplos**: Azul ↔ Naranja | Rojo ↔ Cian | Amarillo ↔ Violeta
- **Efecto**: Contraste máximo, muy impactante y vibrante
- **Cuándo usarlos**: Para hacer que algo destaque brutalmente (botones CTA, acentos)
- **Precaución**: En grandes superficies pueden cansar la vista. Uno debe dominar, el otro ser acento

**2. Colores análogos**
- **Qué son**: Colores adyacentes en la rueda cromática (3-4 colores seguidos)
- **Ejemplos**: Azul, azul-verde, verde | Rojo, rojo-naranja, naranja
- **Efecto**: Armonía suave, sensación de cohesión y unidad
- **Cuándo usarlos**: Interfaces tranquilas, diseños naturales, gradientes suaves
- **Precaución**: Pueden resultar monótonos sin contraste. Introduce neutrales o un toque complementario

**3. Tríada de colores**
- **Qué son**: Tres colores equidistantes en la rueda (forman un triángulo equilátero)
- **Ejemplos**: Rojo, amarillo, azul | Verde, naranja, púrpura
- **Efecto**: Contraste fuerte pero equilibrado, vibrante pero no agresivo
- **Cuándo usarlos**: Paletas con energía pero balanceadas, interfaces juveniles o creativas
- **Precaución**: Uno debe dominar, los otros dos como apoyo

**4. Complementarios divididos**
- **Qué son**: Un color base + los dos colores adyacentes a su complementario
- **Ejemplos**: Amarillo + azul-violeta + rojo-violeta (en lugar de amarillo + violeta puro)
- **Efecto**: Complementario sofisticado, menos tensión visual pero con contraste
- **Cuándo usarlos**: Cuando quieres contraste pero más refinado y menos obvio

**5. Esquema tetrádico (cuadrado o rectangular)**
- **Qué son**: Cuatro colores equidistantes en la rueda (dos pares de complementarios)
- **Ejemplos**: Amarillo, rojo-violeta, azul, amarillo-naranja
- **Efecto**: Paleta compleja, rica, con muchas posibilidades
- **Cuándo usarlos**: Proyectos grandes con muchas categorías o secciones
- **Precaución**: Requiere balance cuidadoso. Uno domina, los otros tres son apoyo. Mal usado es caótico

**6. Monocromático**
- **Qué son**: Un solo color base con todos sus tintes, sombras y tonos (variaciones de luminosidad)
- **Ejemplos**: Azul 900, 700, 500, 300, 100
- **Efecto**: Elegante, sofisticado, cohesivo, discreto
- **Cuándo usarlos**: Interfaces minimalistas, cuando el contenido es protagonista
- **Precaución**: Limitado en contraste. Funciona mejor combinado con neutrales (grises, blanco, negro)

**Temperatura del color**

La temperatura afecta la percepción emocional y espacial de los colores:

**Colores cálidos** (rojos, naranjas, amarillos)
- Avanzan visualmente, parecen más cercanos
- Transmiten: energía, pasión, urgencia, calidez, acción
- Sectores típicos: comida rápida, deporte, entretenimiento, ofertas

**Colores fríos** (azules, verdes, morados)
- Retroceden visualmente, parecen más lejanos
- Transmiten: calma, confianza, profesionalidad, estabilidad, frescura
- Sectores típicos: banca, tecnología, salud, corporativo

No es coincidencia que la mayoría de bancos y tecnológicas usen azul (confianza, estabilidad) y las marcas de comida rápida usen rojo y amarillo (urgencia, apetito, energía). La temperatura del color es comunicación, no decoración.

### El color no es decoración, es información

El color en diseño web no existe para "hacer bonito". Existe para comunicar, establecer jerarquía y crear identidad.

**Los tres trabajos del color:**

1. **Comunicar jerarquía**: Color primario para acciones principales, acento para elementos críticos, grises para información secundaria

2. **Transmitir significado**: Convenciones que no debes romper
  - Rojo = error, peligro
  - Verde = éxito, confirmación
  - Amarillo/Naranja = advertencia
  - Azul = información neutral

3. **Crear identidad**: Spotify es verde, Facebook es azul, Netflix es rojo. Los usuarios recuerdan colores, no logos.

### Crear un sistema de color funcional

**Estructura básica:**

**1. Color primario (tu marca)**

El color que más se repite: botones principales, enlaces, iconos destacados.

Necesitas crear una escala completa (mínimo 5 variaciones usando HSL):

```
Primario 900: hsl(220, 80%, 20%)  ← Muy oscuro (hover, contraste)
Primario 700: hsl(220, 80%, 35%)  ← Oscuro (estados active)
Primario 500: hsl(220, 80%, 50%)  ← BASE (tu color principal)
Primario 300: hsl(220, 80%, 70%)  ← Claro (hover suave)
Primario 100: hsl(220, 80%, 90%)  ← Muy claro (fondos)
```

**2. Color de acento**

Para destacar elementos críticos. Debe contrastar con el primario. Úsalo con moderación.

Ejemplos: Primario azul → Acento naranja | Primario verde → Acento rosa

**3. Colores semánticos (NO negociables)**

```
Éxito:      Verde #10b981   (confirmaciones, validaciones correctas)
Error:      Rojo #ef4444    (errores, validaciones fallidas)
Advertencia: Naranja #f59e0b (alertas no críticas)
Info:       Azul #3b82f6    (mensajes neutros, ayuda)
```

**4. Escala de grises (tu mejor aliado)**

Mínimo 6-8 valores para textos, bordes y fondos:

```
Negro:    hsl(220, 10%, 10%)  ← Textos principales
Gris 700: hsl(220, 10%, 30%)  ← Textos secundarios
Gris 500: hsl(220, 8%, 50%)   ← Textos terciarios
Gris 300: hsl(220, 6%, 75%)   ← Bordes sutiles
Gris 100: hsl(220, 5%, 95%)   ← Fondos alternativos
Blanco:   #FFFFFF             ← Fondo principal
```

**Truco profesional:** Usa tu color primario con saturación baja para los grises (mira el valor HSL). Genera cohesión visual sutil.

### Accesibilidad del color

**WCAG: ratios de contraste mínimos (requisitos legales):**

- Texto normal: **4.5:1** (Nivel AA)
- Texto grande (≥18pt): **3:1** (Nivel AA)
- Elementos interactivos: **3:1**

**Errores comunes:**
- ❌ Texto gris claro sobre blanco → falla contraste
- ✅ Texto gris oscuro `#4A4A4A` sobre blanco → pasa AAA

**Herramientas:**
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Coolors](https://coolors.co/contrast-checker)
- Plugin Stark para Figma

### Implementación en Figma

1. **Crea Color Styles** para cada color
  - Primary 500, Gray 700, Success 500, etc.
2. **Organiza en carpetas** (Primary, Accent, Semantic, Neutral)
3. **Usa SOLO estos estilos** (nunca colores a mano)

**Ventaja:** Si cambias de opinión, actualizas un valor y se propaga automáticamente.do en gris, ha perdido completamente su intensidad. Y la luminosidad es qué tan claro u oscuro es: 100% es blanco puro, 0% es negro puro, y 50% es el color en su versión más "natural".

¿Por qué importa todo esto? Porque HSL es infinitamente mejor que RGB o HEX para crear variaciones de un mismo color. Si tu color principal es `hsl(220, 80%, 50%)`, que es un azul intenso, puedes crear una versión más clara simplemente cambiando el tercer valor: `hsl(220, 80%, 70%)`. Misma familia de color, mismo tono, solo cambia la luminosidad. Esto es fundamental cuando construyes sistemas de diseño, porque necesitas variaciones claras y oscuras de tu color principal que sigan siendo reconocibles como parte de la misma familia.

También es importante entender la temperatura del color. Los colores cálidos (rojos, naranjas, amarillos) transmiten energía, urgencia, cercanía, acción inmediata. Los colores fríos (azules, verdes, morados) transmiten calma, confianza, profesionalidad, estabilidad. No es arbitrario. Una app de fitness usará naranjas y rojos porque quiere transmitir energía y motivación. Una app bancaria usará azules porque necesita transmitir confianza y seguridad. La temperatura del color tiene que estar alineada con lo que tu producto necesita comunicar.

### Crear un sistema de color funcional

No necesitas cincuenta colores. Necesitas un sistema pequeño, consistente, escalable. La mayoría de interfaces profesionales funcionan con menos de diez colores base, y luego sus variaciones. Aquí la estructura que realmente funciona.

**Color primario: tu marca**

Es el color que más se va a repetir en tu interfaz. Lo verás en botones principales, enlaces, iconos destacados, elementos interactivos clave. Debe representar la personalidad de tu producto y ser suficientemente versátil para funcionar en diferentes contextos. No puede ser un color que solo funcione sobre fondo blanco, porque eventualmente necesitarás usarlo sobre otros fondos.

Lo importante es que este color no vive solo. Necesitas crear una escala completa de variaciones: muy oscuro, oscuro, base, claro, muy claro. Como mínimo cinco valores. Si tu primario es un azul `#2563eb`, necesitas generar variaciones más oscuras (para estados hover, para versiones más intensas) y más claras (para fondos sutiles, para estados disabled). Esta escala se convierte en tu paleta primaria completa.

**Color de acento: el énfasis**

Este es el color que usas para destacar elementos críticos. Botones de llamada a la acción muy específicos, notificaciones importantes, elementos que necesitan atención inmediata. Debe contrastar visualmente con tu primario, pero no tanto que parezcan de productos diferentes. Y úsalo con moderación extrema. Si todo es de color de acento, nada es de color de acento.

Un error común es elegir el acento porque "combina bien" con el primario. Mal. El acento debe contrastar, debe destacar, debe llamar la atención. Si tu primario es azul, tu acento puede ser naranja. Si tu primario es verde, tu acento puede ser rosa o morado. Busca contraste, no armonía suave.

**Colores semánticos: feedback del sistema**

Estos no son negociables. El usuario ya sabe qué significan, y si intentas cambiarlos solo vas a generar confusión. Verde para éxito, rojo para error, amarillo o naranja para advertencia, azul para información neutral. No inventes aquí. No uses verde para errores porque "es tu color de marca". Romper convenciones establecidas es sabotear tu propia interfaz.

Estos colores también necesitan su escala de variaciones, pero menos valores que el primario. Con tres suele bastar: una versión intensa para textos y bordes, una versión media para fondos sutiles, y una versión muy clara para fondos amplios.

**Escala de grises: tu mejor aliado**

Este es el secreto de las interfaces que funcionan bien. Necesitas una escala de grises completa, con al menos ocho a diez valores diferentes. Gris muy oscuro para textos principales, gris oscuro para textos secundarios, gris medio para textos terciarios, gris claro para bordes sutiles, gris muy claro para fondos alternativos, casi blanco para fondos principales.

Un truco profesional que cambia completamente el resultado visual: no uses grises neutros puros. Usa tu color primario con saturación muy baja. Si tu azul primario es `hsl(220, 80%, 50%)`, tu gris oscuro puede ser `hsl(220, 10%, 20%)`. Mismo tono, saturación mínima, luminosidad baja. Esto genera una cohesión visual sutil pero potente. Tus grises "tiran" ligeramente hacia tu color de marca, y eso da una sensación de diseño mucho más cuidado.

### Accesibilidad del color: no es opcional

WCAG (Web Content Accessibility Guidelines) establece ratios de contraste mínimos entre texto y fondo. No son sugerencias, son requisitos legales en muchos contextos. Para texto normal (menos de 18pt o 14pt en negrita), necesitas un ratio de contraste de al menos 4.5:1 para cumplir el nivel AA. Para texto grande (18pt o más, o 14pt en negrita), el ratio mínimo es 3:1. Y si quieres cumplir el nivel AAA, los ratios suben a 7:1 y 4.5:1 respectivamente.

Esto significa que no puedes poner texto gris claro sobre fondo blanco solo porque "se ve más moderno" o "más limpio". Si no pasa el ratio de contraste, estás excluyendo activamente a personas con problemas de visión. Y son muchas más de las que imaginas: no solo personas con discapacidad visual severa, también personas mayores, personas con fatiga visual, personas usando pantallas en exteriores con mucha luz.

Herramientas imprescindibles para verificar contraste: WebAIM Contrast Checker es la más directa y simple. Introduces color de texto y color de fondo, te dice el ratio y si pasa AA o AAA. Coolors.co tiene un generador de paletas con verificación de contraste integrada. Y si trabajas en Figma, el plugin Stark revisa contraste en tiempo real mientras diseñas, marcándote qué textos fallan y por cuánto.

El error más común es diseñar con una pantalla de alta gama, bien calibrada, en un entorno con iluminación perfecta, y asumir que todos los usuarios verán lo mismo. No. Muchos usuarios tienen pantallas baratas, mal calibradas, con brillo bajo para ahorrar batería, usándolas en condiciones de luz complicadas. Tu contraste tiene que funcionar incluso en esos contextos.

### Aplicación práctica a tu proyecto

Cuando te pongas a definir tu sistema de color, esta es la estructura mínima que necesitas:

Tu color primario con cinco variaciones como mínimo: primario 900 (muy oscuro, casi negro), primario 700 (oscuro), primario 500 (tu color base, el principal), primario 300 (claro), primario 100 (muy claro, casi blanco). Estos números (100, 300, 500, 700, 900) son convención de muchos sistemas de diseño y frameworks CSS como Tailwind, así que usarlos facilita la comunicación con desarrollo.

Tu color de acento con dos o tres variaciones: acento 500 (base), acento 300 (claro), y opcionalmente acento 700 (oscuro) si lo necesitas.

Tus colores semánticos, uno por tipo: éxito 500, error 500, advertencia 500, info 500. Con sus versiones claras si las necesitas para fondos.

Y tu escala de grises completa: negro (para textos principales, 100% opacidad), gris 700 (para textos secundarios), gris 500 (para bordes y separadores), gris 300 (para fondos alternativos sutiles), gris 100 (para fondos principales amplios), blanco.

Todo esto lo defines ahora, antes de diseñar una sola pantalla. Y lo defines en Figma usando Color Styles o variables de color. ¿Por qué? Porque si dentro de dos semanas decides que tu azul no funciona y quieres cambiarlo, solo cambias el valor del estilo y se actualiza automáticamente en toda tu interfaz. Si no usas estilos y vas poniendo colores a mano, tendrás que cambiar manualmente cada elemento. Y créeme, nunca encontrarás todos.

Define tu sistema de color, documéntalo visualmente, y úsalo consistentemente. Nada de "este azul me gusta más aquí" o "voy a probar un verde diferente en esta pantalla". El sistema existe precisamente para evitar esas decisiones arbitrarias que destrozan la coherencia visual.

### Para profundizar

**Artículos en español:**

- **Teoría del color en diseño web** (40 de Fiebre) - Explica los fundamentos de la teoría del color aplicada específicamente a diseño web, con ejemplos prácticos de combinaciones.
  [Ver artículo](https://www.40defiebre.com/teoria-color-diseno-web)

- **Psicología del color en diseño web** (Thinking for Innovation) - Cómo cada color afecta emocionalmente al usuario y cómo elegir según tu sector y público objetivo.
  [Ver artículo](https://www.iebschool.com/blog/psicologia-color-diseno-web-marketing-digital/)

**Artículos en inglés:**

- **Building Your Color Palette** (Refactoring UI) - Guía práctica paso a paso para construir un sistema de color funcional, no solo "bonito". Muy recomendado.
  [Ver artículo](https://www.refactoringui.com/previews/building-your-color-palette)

**Herramientas imprescindibles:**

- **WebAIM Contrast Checker** - Verifica el contraste entre dos colores y te dice si cumple WCAG.
  [Usar herramienta](https://webaim.org/resources/contrastchecker/)

- **Coolors** - Generador de paletas de color con opciones de accesibilidad y exportación.
  [Usar herramienta](https://coolors.co)

- **Palettte App** - Genera automáticamente escalas de variaciones de un color base.
  [Usar herramienta](https://palettte.app)
