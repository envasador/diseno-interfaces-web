## **7\. Componentes funcionales: construir piezas reutilizables**

Una vez tienes claro el MVP, los flujos y los wireframes, toca identificar qué partes se repiten y pueden convertirse en componentes reutilizables. Este paso es crucial en cualquier sistema de diseño moderno porque permite crear interfaces coherentes, mantenibles y escalables.

Aquí entra el **Atomic Design** de Brad Frost. Esta metodología organiza los elementos de interfaz como piezas de un sistema: desde los más simples a los más complejos, para poder reutilizarlos de forma lógica y eficiente.

### **¿Qué es Atomic Design?**

Atomic Design propone cinco niveles para dividir y estructurar cualquier interfaz de manera modular:

1. **Átomos**: elementos básicos e indivisibles, como un botón, campo de texto o etiqueta.
2. **Moléculas**: combinaciones simples de átomos que funcionan juntos. Ejemplo: buscador (input \+ botón).
3. **Organismos**: conjuntos complejos de moléculas y átomos. Ejemplo: cabecera con logo, menú y buscador.
4. **Templates**: estructuras de páginas con componentes distribuidos según jerarquía definida.
5. **Pages**: instancias reales del diseño con contenido definitivo.

Este enfoque aporta orden y permite detectar inconsistencias, reducir elementos redundantes y facilitar la colaboración entre diseñadores y desarrolladores.

### **¿Por qué aplicar Atomic Design antes de tener estilos visuales?**

Puede parecer raro construir una librería de componentes sin haber definido colores o tipografías. Pero este enfoque funcional tiene ventajas:

* **Permite iterar antes de definir estilos**, centrándose en cómo funciona, no en cómo se ve
* **Ayuda a validar interacciones y estructuras** de forma rápida
* **Fomenta mentalidad de diseño sistemático**, que facilita el trabajo colaborativo

Más adelante, cuando definas estilos (en la siguiente órbita), bastará aplicar esas decisiones al sistema ya creado, en lugar de rediseñar cada pantalla desde cero.

### **Construir una librería funcional en Figma**

Figma permite trabajar con componentes y variantes de forma nativa. Puedes crear, nombrar, organizar y reutilizar elementos fácilmente, agrupándolos según Atomic Design. Un botón puede tener varias variantes: normal, con icono, desactivado...

Mientras trabajas en tu app, puedes ir creando una página de componentes dentro del archivo. Esta página sirve como inventario funcional y base para el diseño visual futuro.

Es importante que cada componente tenga nombre claro, función definida y, si es posible, una pequeña documentación de uso.

### **Herramientas útiles**

Para organizar componentes en Figma:

* **Instance Finder**: localiza todas las instancias de un componente
* **Design System Organizer**: ayuda a categorizar y mantener jerarquía clara
* **Styler**: útil para auditar estilos y preparar la transición a diseño visual

Estas herramientas no son obligatorias, pero facilitan mantener un diseño funcional coherente.

### **Ejemplo práctico: app de recetas**

En las primeras pantallas de una app de recetas, observas que hay elementos que se repiten: botones, campos de búsqueda, tarjetas con imagen y texto, menús flotantes...

El primer paso sería hacer un inventario con estos elementos, clasificarlos por nivel (átomo, molécula, organismo) y construirlos como componentes reutilizables en Figma:

**Átomos**: botón, campo de texto, etiqueta **Moléculas**: buscador, tarjeta de receta **Organismos**: cabecera, listado de recetas, menú inferior

Estos elementos los usas en múltiples pantallas, garantizando coherencia funcional.

### **Actividad práctica**

**"Construcción del sistema de componentes"**

1. Cada persona revisa su prototipo funcional e identifica al menos cinco componentes reutilizables
2. En una nueva página de su archivo de Figma:
    * Construir esos componentes y clasificarlos según Atomic Design
    * Añadir etiquetas y descripción funcional breve
    * Definir al menos una variante para cada uno (ej: activo/inactivo)
3. Esta actividad no requiere estilo visual. Su objetivo es estructurar la interfaz funcional como sistema reutilizable

Este sistema servirá de base directa para la siguiente órbita, donde aplicaremos colores, tipografías y guías de estilo.
