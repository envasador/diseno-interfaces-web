## **Fase 6: Componentes reutilizables**

Identifica qué elementos se repiten para que en el módulo de DWEC puedas reutilizarlos.

#### **Qué tienes que hacer:**

El último paso es identificar todos los elementos que se repiten a lo largo de tu aplicación para convertirlos en componentes reutilizables. Esta fase es fundamental para la coordinación con el módulo de DWEC, que necesitarás implementar cada elemento una sola vez y luego reutilizarlo en diferentes pantallas.

Repasa todas las pantallas de tu prototipo y haz un inventario detallado de elementos repetidos. Fíjate en botones, campos de formulario, tarjetas de contenido, menús, cabeceras, elementos de navegación... cualquier cosa que aparezca más de una vez puede convertirse en un componente. Piensa también en las variaciones: por ejemplo, un botón puede tener estados normal, hover, desactivado, o de carga.

Organiza estos componentes siguiendo la metodología Atomic Design que has visto en la unidad. Clasifícalos en átomos como botones individuales, moléculas como buscadores que combinan input y botón, y organismos como cabeceras completas con logo, menú y usuario. Esta clasificación ayudará enormemente al equipo de desarrollo a entender las dependencias entre componentes.

Por último, documenta cada componente de forma clara. No hace falta que sea un manual exhaustivo, pero sí que incluya información básica sobre cuándo usar cada variante, qué contenido llevan, y cómo se comportan. Recuerda que esta documentación la van a leer personas que no han participado en el proceso de diseño.

#### **Entregable:**

El sistema de componentes funcionales desarrollado en Figma debe contener una librería organizada con mínimo 4 componentes clasificados según Atomic Design, las variantes funcionales necesarias para cada estado, y documentación básica que explique el propósito y uso de cada componente para el equipo de desarrollo.
