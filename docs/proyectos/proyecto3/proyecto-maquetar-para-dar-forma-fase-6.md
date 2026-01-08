# **FASE 6: TEMAS Y MODO OSCURO**

**Criterios:** RA2.d, RA2.e  
**Entrega:** 14 de enero

## **OBJETIVOS DE LA FASE**

Implementar un sistema completo de temas que permita cambiar entre modo claro y modo oscuro usando CSS Custom Properties, con theme switcher funcional y persistencia.

Esta fase se coordina con **DWEC Fase 1-2** donde implementas la funcionalidad JavaScript del theme switcher mediante eventos y servicios.

## **TAREAS**

### **1. Sistema de temas con CSS Custom Properties**

Define variables CSS en `:root` para tema claro y en `[data-theme="dark"]` para tema oscuro.

Variables requeridas:
- Colores de fondo
- Colores de texto
- Colores de borde
- Colores de sombra
- Estados (hover, active)

### **2. Theme Switcher**

Crea un componente theme-switcher que:
- Muestre toggle visual
- Cambie atributo `data-theme` en elemento `<html>`
- Guarde preferencia en `localStorage`
- Cargue preferencia al iniciar
- Se coloque en header, visible

**Nota:** La funcionalidad JavaScript se implementa en DWEC Fase 1-2.

### **3. Detección de preferencia del sistema**

Implementa detección automática usando `prefers-color-scheme`.

Prioridad:
1. Tema guardado en localStorage
2. Preferencia del sistema
3. Tema claro por defecto

### **4. Transiciones suaves entre temas**

Añade transiciones CSS (150-300ms) para cambio suave entre temas.


### **5. Documentación en DOCUMENTACION.md**

Añade la **Sección 6: Sistema de temas** a tu archivo `docs/DOCUMENTACION.md`.

Esta sección debe incluir:

**6.1 Variables de tema:** Muestra código de CSS Custom Properties para ambos temas.

**6.2 Implementación del Theme Switcher:** Documenta cómo funciona.

**6.3 Capturas de pantalla:** Capturas de al menos 3 páginas mostrando modo claro y modo oscuro.

## **ENTREGABLES FASE 6**

- Sistema completo de CSS Custom Properties para temas claro y oscuro
- Componente theme-switcher funcional con persistencia
- Detección de `prefers-color-scheme`
- Transiciones suaves entre temas
- Todos los componentes actualizados usando variables CSS
- Sección 6 del `docs/DOCUMENTACION.md` completada con capturas
