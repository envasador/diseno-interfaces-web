## Fase 1: Moodboard y guía de estilo

### ¿Por qué importa esto?

Sin un sistema visual claro, cada pantalla se diseña desde cero y surgen inconsistencias. El moodboard te ayuda a capturar la dirección estética de tu proyecto y justificar cada decisión visual. La guía de estilo elimina decisiones innecesarias, acelera el diseño, y garantiza que cualquier elemento en tu interfaz sea coherente, accesible y reconocible.

### Qué tienes que hacer:

Para empezar, necesitas construir un moodboard que capture la esencia visual de tu proyecto. No se trata de buscar imágenes bonitas, sino de definir una dirección estética clara que hable a tu usuario y encaje con el propósito de tu producto. Recopila referencias visuales: capturas de apps o webs con una estética que funcione para tu contexto (no copies, inspírate). Añade paletas de color, ejemplos tipográficos que transmitan personalidad, y texturas o ilustraciones que definan el tono. Agrupa todo en un frame de Figma y escribe 2-3 palabras clave que definan el estilo: eso será tu brújula para todas las decisiones que vienen después.

Una vez tengas clara la dirección estética, toca construir tu sistema de color. Crea una paleta funcional: elige un color primario para acciones principales, añade colores funcionales (verde para éxito, rojo para error, amarillo para advertencias, azul para información), y construye escalas completas de tonos para cada color. Para los textos, fondos y bordes, crea una escala de grises de 9 tonos. Verifica que todo cumpla con accesibilidad: usa WebAIM Contrast Checker o el plugin Stark en Figma para asegurar que el contraste texto-fondo sea mínimo 4.5:1. Que tu paleta sea bonita no significa nada si los usuarios no pueden leerla.

Ahora diseña tu tipografía. Elige máximo dos familias tipográficas: una para textos (Inter, Roboto, Open Sans priorizan legibilidad en pantalla) y opcionalmente una para títulos si quieres diferenciación. Define una escala tipográfica clara: H1 (32-40px para títulos de página), H2 (24-28px para secciones), H3 (20-24px para subsecciones), Body (16px para texto principal), Body Small (14px para metadata) y Caption (12px para notas). Para cada nivel especifica el peso, la altura de línea (mínimo 1.5 para párrafos), y el color. Crea Text Styles en Figma para cada variante y documenta cuándo usar cada uno: esto evita que diseñadores inventen tamaños custom en cada pantalla.

Selecciona un sistema de iconos y úsalo consistentemente. Elige UNA librería (Lucide, Heroicons, Material Symbols, Phosphor) y define tamaños estándar: 16px para iconos inline, 20px para botones, 24px para navegación. Establece si usas filled o outlined, y marca cuáles son los iconos que siempre necesitan etiqueta de texto porque solos pueden no ser claros.

Define tu espaciado base: una escala simple como 4px, 8px, 16px, 24px, 32px, 48px, 64px. Esto te permite mantener proporciones armónicas en toda la interfaz. Establece reglas claras: espacios pequeños (8-16px) para agrupar elementos relacionados, espacios grandes (32-48px) para separar secciones. Esto ayuda al usuario a entender visualmente qué está relacionado y qué es independiente.

Por último, documenta todo en Figma en una página llamada "Guía de estilo". Organiza secciones para cada componente del sistema: paleta de colores con nombres y códigos hex, escala tipográfica con todos los Text Styles, librería de iconos documentada, escala de espaciado, y ejemplos de jerarquía visual. Para cada elemento añade ejemplos de "✅ Hacer" y "❌ No hacer" para que otros (o tú mismo en el futuro) tengan claridad sobre cuándo y cómo usar cada componente.

### Entregable:

Un archivo Figma con:

* Moodboard visual con dirección estética clara y palabras clave 
* Sistema de color completo con paletas de tonos y verificación de accesibilidad documentada 
* Escala tipográfica definida con todos los Text Styles y ejemplos de uso 
* Librería de iconos seleccionada y casos de uso documentados 
* Escala de espaciado definida con ejemplos aplicados 
* Guía de estilos en Figma organizada y completa que sirva como referencia única para todo el diseño posterior. Con Variables y Estilos.

### Tiempo estimado:

1 semanas (5 sesiones)
