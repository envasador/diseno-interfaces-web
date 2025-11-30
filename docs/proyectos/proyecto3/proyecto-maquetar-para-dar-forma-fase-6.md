# **FASE 6: TEMAS Y MODO OSCURO**

**Criterios:** RA2.d, RA2.e  
**Entrega:** Después de Navidad

## **OBJETIVOS DE LA FASE**

En esta fase implementarás un sistema completo de temas que permita cambiar entre modo claro y modo oscuro. No se trata solo de "invertir colores", sino de crear una experiencia visual coherente en ambos modos, respetando el contraste, manteniendo la jerarquía visual, y ofreciendo una transición suave entre temas.

Crearás un sistema basado en CSS Custom Properties (variables CSS) que permita cambiar todos los colores de la aplicación dinámicamente. Implementarás un theme switcher funcional con persistencia en localStorage, detectarás la preferencia del sistema operativo, y verificarás que ambos temas cumplan con los requisitos mínimos de contraste.

## **TAREAS**

### **1. Sistema de temas con CSS Custom Properties**

Expande el archivo `src/styles/00-settings/_css-variables.scss` que creaste en Fase 2:

Define todas las variables de color CSS que usarás en tu aplicación:
- Variables para tema claro en `:root` (colores de fondo, texto, bordes, sombras, estados)
- Variables para tema oscuro en `[data-theme="dark"]` (mismos nombres, valores diferentes)

### **2. Theme Switcher**

Crea un componente para cambiar entre temas: `ng generate component components/shared/theme-switcher`

El componente debe:
- Mostrar un toggle visual (botón, switch, iconos sol/luna, etc.)
- Cambiar el atributo `data-theme` en el elemento `<html>` al hacer clic
- Guardar la preferencia en `localStorage`
- Cargar la preferencia guardada al iniciar la aplicación
- Colocarse en el header, visible y accesible

### **3. Detección de preferencia del sistema**

Implementa detección automática de la preferencia del sistema operativo usando la media query `prefers-color-scheme`.

Define la prioridad:
1. Tema guardado en localStorage
2. Preferencia del sistema (`prefers-color-scheme`)
3. Tema claro por defecto

### **4. Transiciones suaves entre temas**

Añade transiciones CSS para que el cambio de tema sea suave pero rápido (150-300ms). Cuida el rendimiento evitando animar miles de elementos simultáneamente.

### **5. Verificación de contraste**

Verifica que ambos temas cumplan con requisitos mínimos de contraste WCAG AA:
- Texto normal: ratio 4.5:1
- Texto grande: ratio 3:1
- Componentes UI: ratio 3:1

Usa herramientas como WebAIM Contrast Checker, Chrome DevTools, o Lighthouse.

### **6. Aplicación del tema en todos los componentes**

Revisa TODOS los componentes creados en fases anteriores y reemplaza valores de color hardcoded por CSS Custom Properties. Asegúrate de que todos los componentes (header, footer, cards, botones, formularios, alerts, modales) usan las variables del tema.

### **7. Documentación en DOCUMENTACION.md**

Añade la **Sección 6: Sistema de temas** a tu archivo `docs/DOCUMENTACION.md`.

Esta sección debe incluir:

**6.1 Variables de tema:** Muestra el código de tus CSS Custom Properties para ambos temas. Explica la estructura y organización.

**6.2 Implementación del Theme Switcher:** Documenta cómo funciona: cambio de tema, persistencia, detección de preferencia del sistema.

**6.3 Testing de contraste:** Presenta una tabla con las combinaciones principales de colores mostrando el ratio de contraste en ambos temas. Indica si cumple WCAG AA.

**6.4 Capturas de pantalla:** Incluye capturas de al menos 3 páginas mostrando modo claro y modo oscuro lado a lado.

## **ENTREGABLES FASE 6**

- Sistema completo de CSS Custom Properties para temas claro y oscuro
- Componente theme-switcher funcional con persistencia
- Detección de `prefers-color-scheme`
- Transiciones suaves entre temas
- Todos los componentes actualizados usando variables CSS
- Verificación de contraste WCAG AA en ambos temas
- Sección 6 del `docs/DOCUMENTACION.md` completada con tabla de contraste y capturas
