## 8. Checklist de accesibilidad

Antes de lanzar una aplicación debes tener en cuenta este checklist:

### HTML y estructura

* [ ] HTML válido (validador W3C)
* [ ] Un solo `<h1>` por página
* [ ] Jerarquía de encabezados sin saltos
* [ ] Landmarks usados (`<header>`, `<nav>`, `<main>`, `<footer>`)
* [ ] `lang` en `<html>`

### ARIA

* [ ] ARIA solo cuando HTML nativo no basta
* [ ] Roles correctos y consistentes
* [ ] Estados actualizados dinámicamente
* [ ] Live regions para cambios importantes
* [ ] Sin aria-hidden en elementos enfocables

### Teclado

* [ ] Todo accesible con teclado
* [ ] Orden de foco lógico
* [ ] Indicador de foco visible
* [ ] Modales atrapan foco y cierran con Escape
* [ ] Sin trampas de teclado

### Color y contraste

* [ ] Contraste ≥4.5:1 (texto normal)
* [ ] Información no solo por color

### Multimedia

* [ ] Vídeos con subtítulos
* [ ] Audio con transcripción
* [ ] Imágenes con alt apropiado

### Formularios

* [ ] Cada campo con `<label>`
* [ ] Campos obligatorios indicados
* [ ] Errores descriptivos

### Testing

* [ ] Lighthouse >90
* [ ] Probado con teclado completo
* [ ] Probado con lector de pantalla (básico)

**Recursos clave para llevar:**

* **Guía de referencia:** https://www.w3.org/WAI/WCAG21/quickref/
* **Aprende con ejemplos:** https://accesible.es/
* **Patrones ARIA:** https://www.w3.org/WAI/ARIA/apg/
* **Audita tu sitio:** Lighthouse + axe DevTools + teclado + lector de pantalla
* **Objetivo mínimo:** WCAG 2.1 nivel AA
