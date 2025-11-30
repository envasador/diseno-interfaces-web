## **5\. Prototipado navegable: simular antes de construir**

Una vez tienes wireframes que representan la estructura funcional de tu app, el paso siguiente es **hacerlos interactivos**. Convertir esos bocetos estáticos en un **prototipo navegable** que simule cómo sería usar realmente la app.

Estos prototipos no son productos terminados ni tienen estilos definitivos. Son maquetas funcionales que ayudan a comprobar si los flujos tienen sentido, si las acciones están claras y si la navegación es intuitiva.

Antes de escribir una línea de código, debes tener claro que la estructura funciona. Y la mejor forma de comprobarlo es navegándola.

### **¿Qué es un prototipo navegable?**

Un prototipo navegable es una simulación interactiva donde puedes hacer clic en botones, cambiar de pantalla o simular interacciones básicas.

No es una app real, pero **se comporta como si lo fuera**, permitiendo recorrer pantallas como haría un usuario final.

### **¿Para qué sirve?**

* **Validar la experiencia** sin necesidad de desarrollo
* **Detectar errores en el flujo** o confusiones en la interacción
* **Testear con usuarios reales** o con otros grupos
* **Comunicar la propuesta** de forma clara a personas no técnicas

### **¿Cómo se hace?**

En **Figma** es sencillo:

1. Crear frames con cada pantalla (tus wireframes)
2. Ir a la pestaña **Prototype** y enlazar elementos:
    * Botones que llevan a otras pantallas
    * Iconos que abren menús
    * Áreas clicables que simulan navegación
3. Ajustar transiciones o animaciones básicas si es necesario
4. Compartir el prototipo con un **link interactivo**

#### **Buenas prácticas**

* No añadas estilos visuales si no están definidos: **céntrate en la lógica**
* Usa nombres claros: "Login", "Home", "Carrito"
* Asegúrate de que **todas las acciones** estén conectadas a algún resultado
* Simula solo lo necesario: **menos es más** en esta fase
* Si algo no funciona aún, indícalo como "en desarrollo"

### **Ejemplo práctico: app de recetas**

Tienes wireframes para:

* Pantalla de inicio (buscar recetas)
* Ficha de receta
* Registro de usuario
* Crear receta

En Figma enlazas:

* Botón "Buscar" → lista de resultados
* Cada resultado → ficha de receta
* Desde cualquier pantalla → registro
* Botón "Crear receta" → formulario básico

El resultado es un flujo navegable que puedes **probar, enseñar y corregir** antes de programar.

### **Recursos útiles**

* [Figma: crear prototipos](https://help.figma.com/hc/en-us/articles/360040451373-Create-interactive-prototypes)
* [LearnUX.io – Curso básico de Figma](https://learnux.io/course/figma)

### **Actividad práctica**

**"Prototipa tu proyecto"**

Esta actividad ejecuta la **Fase 4** del proyecto intermodular:

1. Cada persona parte de sus wireframes testeados de la actividad anterior
2. Usar Figma para convertir esos wireframes en un prototipo navegable
3. **Requisitos mínimos** para alinear con el proyecto:
    * Enlazar las 6 pantallas mínimas del proyecto
    * Simular **dos flujos completos** de usuario de principio a fin
    * Incluir estados de error o validación en formularios
4. **Testing obligatorio**: Probar el prototipo con usuarios reales siguiendo la metodología que aplicaréis en el proyecto
5. Documentar feedback específico y cambios implementados

**Para el proyecto**: Este prototipo será directamente vuestra entrega de la Fase 4, así que aseguraos de que cumple los criterios de evaluación del proyecto.
