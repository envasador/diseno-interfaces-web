# **FASE 4: RESPONSIVE DESIGN Y LAYOUTS COMPLETOS**

**Criterios:** RA2.c, RA2.d, RA2.f  
**Entrega:** Después de Navidad

## **OBJETIVOS DE LA FASE**

En esta fase harás que tu aplicación funcione perfectamente en todos los dispositivos: mobile, tablet y desktop. No se trata solo de que "se vea bien" en diferentes pantallas, sino de aplicar una estrategia responsive profesional con breakpoints justificados.

Adaptarás todos los componentes que creaste en las Fases 2 y 3 para que funcionen correctamente en diferentes viewports. Cada componente debe verse y funcionar bien desde 320px hasta 1920px. También aplicarás Container Queries en algunos componentes para hacerlos verdaderamente independientes.

## **TAREAS**

### **1. Adaptación responsive de componentes layout**

Revisa y adapta los componentes de layout de Fase 2 para que funcionen correctamente en mobile, tablet y desktop:

**Header responsive:** Debe tener comportamiento diferente en mobile (botón hamburguesa + menú desplegable vertical) y desktop (navegación horizontal visible). Incluye transiciones suaves y overlay oscuro en mobile.

**Footer responsive:** Adapta la distribución del contenido: apilado verticalmente en mobile, distribuido en columnas en desktop.

**Main y Sidebar:** El sidebar debe ocultarse o convertirse en filtros desplegables en mobile, y mostrarse lateral en desktop.

### **2. Adaptación responsive de componentes UI**

Revisa y adapta los componentes UI de Fase 3:

**Botones:** Deben tener ancho completo en mobile dentro de formularios, y ancho automático en desktop.

**Cards:** Deben reorganizarse según el viewport: una columna en mobile, dos en tablet, tres o más en desktop.

**Formularios:** Los campos deben apilarse verticalmente en mobile con ancho completo. En desktop pueden organizarse en dos columnas cuando tenga sentido.

**Alerts y Notificaciones:** Deben adaptarse en posición y ancho según el dispositivo.

### **3. Container Queries en componentes clave**

Implementa Container Queries en al menos 2 componentes para hacerlos verdaderamente independientes del viewport. Elige componentes que se beneficien de esta técnica (cards que cambian de vertical a horizontal, componentes de producto que reorganizan imagen y texto, etc.).

### **4. Páginas principales responsive**

Crea o adapta las páginas principales de tu aplicación combinando los componentes ya creados:

**Página Home:** Combina tus componentes en un layout adaptable con hero section, grid de cards destacadas, y secciones de contenido.

**Página Listado:** Implementa grid de cards adaptable y filtros que funcionen en sidebar (desktop) o acordeón/modal (mobile).

**Página Detalle:** Crea layout con galería de imágenes adaptable e información reorganizada según viewport.

**Página con Formulario:** Formulario centrado con campos apilados en mobile o en grid en desktop.

### **5. Estrategia responsive consistente**

Asegúrate de usar consistentemente tu mixin responsive de Fase 1 en todos los componentes.

Elige y aplica una estrategia:
- **Mobile-first:** Estilos base para mobile (320px+), luego media queries con `min-width` para pantallas más grandes
- **Desktop-first:** Estilos base para desktop, luego media queries con `max-width` para pantallas más pequeñas

Documenta qué estrategia elegiste y por qué.

### **6. Testing responsive**

Prueba tu aplicación en diferentes viewports usando Chrome DevTools:
- 320px (mobile pequeño)
- 375px (mobile estándar)
- 768px (tablet)
- 1024px (desktop pequeño)
- 1280px (desktop estándar)

Prueba en Chrome/Edge y Firefox como mínimo.

### **7. Documentación en DOCUMENTACION.md**

Añade la **Sección 4: Estrategia Responsive** a tu archivo `docs/DOCUMENTACION.md`.

Esta sección debe incluir:

**4.1 Breakpoints definidos:** Lista tus breakpoints con los píxeles exactos y justifica por qué elegiste esos valores según tu diseño.

**4.2 Estrategia responsive elegida:** Explica si usaste mobile-first o desktop-first. Justifica tu decisión y muestra ejemplos de código de tus componentes aplicando la estrategia elegida.

**4.3 Container Queries:** Documenta en qué componentes usaste Container Queries, por qué esos componentes se benefician, y muestra código de ejemplo.

**4.4 Adaptaciones por componente:** Explica brevemente cómo se adapta cada tipo de componente (header, footer, cards, formularios) en mobile vs desktop.

**4.5 Screenshots comparativos:** Incluye capturas de pantalla de al menos 3 páginas mostrando mobile (375px), tablet (768px) y desktop (1280px).

## **ENTREGABLES FASE 4**

- Todos los componentes de layout adaptados a responsive
- Todos los componentes UI adaptados a responsive
- Container Queries implementadas en mínimo 2 componentes
- Mínimo 3 páginas completas responsive
- Navegación mobile completamente funcional
- Sección 4 del `docs/DOCUMENTACION.md` completada con capturas
