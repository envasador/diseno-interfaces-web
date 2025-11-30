# **FASE 2: HTML SEMÁNTICO Y COMPONENTES DE LAYOUT**

**Criterios:** RA2.f, RA2.a  
**Entrega:** 18 de diciembre

## **OBJETIVOS DE LA FASE**

En esta fase crearás la estructura semántica de tu aplicación y los componentes de layout que enmarcan todo el contenido. No estamos haciendo páginas completas todavía, sino construyendo los "contenedores principales" que se usarán en toda la aplicación: el header, el footer, la navegación principal, y cualquier sidebar o estructura fija.

Estos componentes de layout son especiales porque aparecen en (casi) todas las páginas y definen la estructura general. Un header bien hecho se usa igual en home, en listados, en detalle. Por eso es crítico hacerlos bien desde el principio, con HTML semántico impecable y pensando en que sean reutilizables.

## **TAREAS**

### **1. Componentes de layout semánticos**

Crea los siguientes componentes usando `ng generate component components/layout/nombre-componente`:

**Header (app-header):** Usa la etiqueta semántica `<header>`. Debe incluir logo (enlace a home), navegación principal (`<nav>`), y elementos de utilidad según tu aplicación (búsqueda, usuario, carrito, etc.).

**Main (app-main):** Usa `<main>`. Este componente actúa como contenedor del contenido principal. Usa `<ng-content></ng-content>` para proyectar contenido dentro del componente.

**Footer (app-footer):** Usa `<footer>`. Incluye enlaces legales (términos, privacidad, cookies), enlaces a redes sociales, y copyright.

**Sidebar (app-sidebar) - OPCIONAL:** Solo si tu diseño lo necesita. Usa `<aside>` para contenido secundario (filtros, navegación secundaria, widgets).

### **2. Componentes funcionales HTML semántico**

Crea un componente `form-input` reutilizable usando `ng generate component components/shared/form-input`.

Este componente debe poder usarse para cualquier tipo de input (text, email, password, etc.). El HTML debe incluir:
- Label siempre asociado al input mediante atributos `for` (en label) e `id` (en input), o como hemos visto en clase.
- Input con los atributos necesarios (type, name, placeholder, required)
- Indicador visual de campo requerido (asterisco)
- Mensaje de error opcional
- Texto de ayuda opcional

### **3. Formularios estructurados**

Crea un formulario completo (login, registro o contacto según tu aplicación) usando `ng generate component components/shared/nombre-form`.

El formulario debe usar:
- `<form>` con método apropiado
- `<fieldset>` para agrupar campos relacionados
- `<legend>` para describir el grupo de campos
- Tus componentes `<app-form-input>` para los campos
- Botón de submit con texto descriptivo

### **4. Estilos de componentes de layout**

Para cada componente de layout, crea sus estilos siguiendo BEM en su archivo `.scss` correspondiente.

Los componentes de layout normalmente necesitan:
- Ancho completo o max-width contenido
- Padding lateral consistente
- Flex o Grid para distribución interna
- Z-index si son sticky o fixed
- Transiciones para interacciones

Usa las variables SCSS que definiste en Fase 1 (spacing, colores, etc.).

### **5. CSS Custom Properties para temas**

En `src/styles/00-settings/` crea un nuevo archivo `_css-variables.scss`:

Define variables CSS (Custom Properties) en `:root` para los valores que cambiarán con el tema:
- Colores de fondo (bg-primary, bg-secondary)
- Colores de texto (text-primary, text-secondary)
- Color de borde

Usa la sintaxis `#{$variable-scss}` para convertir tus variables SCSS a valores CSS.

Importa este archivo en `styles.scss` después de las variables SCSS.

### **6. Documentación en DOCUMENTACION.md**

Añade la **Sección 2: HTML semántico y estructura** a tu archivo `docs/DOCUMENTACION.md`.

Esta sección debe incluir:

**2.1 Elementos semánticos utilizados:** Explica qué elementos semánticos usas y cuándo: header, nav, main, article, section, aside, footer. Muestra ejemplos de tu código.

**2.2 Jerarquía de headings:** Documenta tu estrategia de headings (h1 a h6). Reglas: solo un h1 por página, h2 para secciones principales, h3 para subsecciones. NUNCA saltes niveles. Muestra un diagrama de tu jerarquía.

**2.3 Estructura de formularios:** Muestra tu estructura de formularios explicando el uso de fieldset, legend, y la asociación de labels con inputs (for e id) o como hemos visto en clase. Incluye un ejemplo de código de tu componente form-input.


## **ENTREGABLES FASE 2**

- Componentes layout: header, main, footer (+ sidebar si aplica) con HTML semántico
- Componente form-input reutilizable
- Un formulario completo estructurado
- Estilos SCSS para todos los componentes siguiendo BEM
- CSS Custom Properties básicas en `_css-variables.scss`
- Sección 2 del `docs/DOCUMENTACION.md` completada
