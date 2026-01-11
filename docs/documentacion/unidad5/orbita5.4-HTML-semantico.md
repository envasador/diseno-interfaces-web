## 4. HTML semántico: la base fundamental

### 4.1. Por qué HTML semántico es el 80% de la accesibilidad

El HTML semántico usa etiquetas que describen el **significado** del contenido, no solo su apariencia. Esta semántica es la que leen los lectores de pantalla, los navegadores, los buscadores.

**Beneficios:**
* Lectores de pantalla pueden navegar eficientemente (saltar entre encabezados, ir directo a navegación, etc.)
* Navegadores aplican comportamientos nativos correctos (botones son clicables con Enter, checkboxes con Espacio)
* SEO mejorado (Google entiende la estructura)
* Mantenibilidad del código

### 4.2. Estructura de página con landmarks

Los **landmarks** son regiones semánticas de la página:

* `<header>` * Encabezado del sitio o sección
* `<nav>` * Navegación principal, secundaria, breadcrumbs
* `<main>` * Contenido principal (solo uno por página)
* `<article>` * Contenido autocontenido (post, producto, noticia)
* `<section>` * Sección temática del documento
* `<aside>` * Contenido complementario (sidebar, widgets)
* `<footer>` * Pie de página o sección

**Por qué importan:**
Una persona con ceguera puede presionar una tecla y saltar entre landmarks: header → nav → main → aside → footer. Sin landmarks, tiene que escuchar todo linealmente.

### 4.3. Jerarquía de encabezados

Los encabezados (`<h1>` a `<h6>`) crean el índice del documento.

**Reglas:**
1. Un solo `<h1>` por página (título principal)
2. No saltar niveles (después de `<h2>` viene `<h3>`, no `<h5>`)
3. Reflejar jerarquía real del contenido

**Por qué importan:**
Los lectores de pantalla pueden listar todos los encabezados, permitiendo navegar por secciones.

### 4.4. Botones vs enlaces: cuándo usar cada uno

**`<button>`:** Para acciones en la misma página (enviar formulario, abrir modal, toggle)

**`<a>` (enlace):** Para navegación (ir a otra página, saltar a sección)

**Por qué importa:**
Los lectores de pantalla anuncian diferente: "botón Enviar" vs "enlace Productos". Usuarios saben qué esperar.

### 4.5. Formularios semánticos

**Cada campo con su `<label>`:**
Asociar explícitamente con atributo `for`.

**Agrupación con `<fieldset>` y `<legend>`:**
Para grupos de campos relacionados.

**Por qué importa:**
Un lector de pantalla anuncia: "Correo electrónico, campo de edición". Sin label, solo anuncia "campo de edición", sin contexto.


