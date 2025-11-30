## Fase 2: Mockups y biblioteca de componentes

### ¿Por qué importa esto?

Los mockups son la versión final de tu producto que se testeará con usuarios y se entregará a desarrollo. Los componentes reutilizables garantizan que cualquier cambio se propague automáticamente y mantienen la consistencia sin esfuerzo. Si has construido bien tu sistema en la Fase 1, esta fase es aplicar el sistema: rápido, eficiente, y completamente coherente.

### Qué tienes que hacer:

Para empezar, construye tu biblioteca de componentes. Antes de tocar ni una sola pantalla completa, crea todos los elementos base que vas a necesitar: botones en sus diferentes tipos (primario, secundario, terciario, destructivo) con todos sus estados (default, hover, focus, disabled), campos de formulario (inputs, textareas, selects) también con todos sus estados, checkboxes y radio buttons, cards, navegación, modales, y alertas/notificaciones. Para cada componente, diseña todas las variantes y estados que puedan existir en tu aplicación. Usa las variables de color y Text Styles que ya definiste en la Fase 1: no improvises nuevos tonos ni tamaños de texto. Documenta las medidas internas, el espaciado, y cualquier detalle que alguien de desarrollo necesite para implementarlo.

Una vez tu biblioteca esté lista, identifica las 5-7 pantallas más importantes de tu flujo principal: la landing o home, la pantalla donde ocurre la acción central de tu app, el formulario clave, la vista de resultados o contenido, y si aplica, perfil o configuración. Diseña cada una completamente, pero aquí es donde el sistema brilla: usa SOLO componentes de tu biblioteca. No diseñes elementos nuevos sobre la marcha. Aplica los Text Styles definidos, usa colores de tu paleta, respeta el espaciado que estableciste. Si necesitas algo que no existe en tu biblioteca, detente: conviértelo en componente primero, documéntalo, y luego úsalo. Esto mantiene todo coherente y escalable.

Reemplaza todo el contenido genérico con texto real o realista, imágenes de placeholder contextuales (Unsplash, UI Faces), y datos numéricos que tengan sentido. Esto revela problemas que el Lorem ipsum oculta: un nombre que se corta por ser muy largo, un texto que ocupa más espacio del esperado, cómo se comporta realmente el diseño con contenido real.

Diseña los estados especiales que suelen olvidarse pero son críticos: estado de carga (skeleton screens o spinners), estado vacío (primera vez en la app, sin datos guardados, búsqueda sin resultados), estado de error (conexión fallida, validación incorrecta), y estado de éxito (confirmaciones, feedback positivo). Cada uno debe estar diseñado completamente y aplicar tu sistema visual.

Verifica que en cada pantalla la jerarquía visual sea clara: el elemento más importante funcionalmente debe ser el más destacado visualmente, los grupos de información deben separarse claramente, el flujo debe guiar al usuario hacia la acción principal. Usa tu sistema de espaciado y tipografía para crear esa jerarquía: no colores aleatorios ni tamaños inventados.

Crea un prototipo navegable conectando tus pantallas. El usuario debería poder completar la tarea principal de tu app navegando el prototipo: hacer clic, seguir un flujo, llegar a un resultado. Incluye transiciones básicas que no distraigan de la funcionalidad, pero que muestren claramente cómo se conectan las pantallas.

Organiza tu archivo Figma de manera clara: una página para la guía de estilo, otra para componentes organizados por tipo, otra para mockups finales, y otra para el prototipo navegable. Usa nombres claros y jerarquía visual en tu estructura: alguien de desarrollo debe poder encontrar cualquier componente en segundos.

### Entregable:

Un archivo Figma con:

* Biblioteca de componentes completa y documentada con todos los estados 
* 5-7 pantallas clave (MVP) en mockup de alta fidelidad aplicando el sistema completo 
* Estados especiales diseñados (carga, vacío, error, éxito)
* Contenido real o realista en todas las pantallas 
* Prototipo navegable funcional del flujo principal 
* Archivo organizado, documentado y listo para handoff a desarrollo

### Tiempo estimado:

1 semana (5 sesiones)


