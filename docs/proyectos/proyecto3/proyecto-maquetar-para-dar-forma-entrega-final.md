## **Entrega final**

### **README.md obligatorio**
Tu README.md debe incluir:

---
# [Nombre de tu Proyecto]

**URL de la aplicación:** https://tu-proyecto.vercel.app

## Descripción
[Breve descripción de tu aplicación - 2-3 líneas]

## Tecnologías
- Angular [versión]
- SCSS
- TypeScript
- [Otras tecnologías relevantes]

## Arquitectura CSS
- **Metodología:** [BEM/SMACSS/otra]
- **Organización:** [ITCSS/otra]
- **Preprocesador:** SCSS

## Instalación local
```bash
git clone [tu-repositorio]
cd [tu-proyecto]
npm install
npm start
```

Aplicación disponible en: http://localhost:4200

## Despliegue

**URL producción:** https://tu-proyecto.vercel.app

## Sistema de diseño
- **Variables:** `src/styles/00-settings/`
- **Componentes:** `src/styles/05-components/`
- **Style Guide:** https://tu-proyecto.vercel.app/style-guide

## Performance
- First Contentful Paint: [tu medición]
- Largest Contentful Paint: [tu medición]
- Total page weight: [tu medición]

## Accesibilidad
- Lighthouse Accessibility Score: [tu puntuación]
- WCAG Level: A/AA
- Navegación por teclado: ✅
- Lector de pantalla: ✅

## Estructura del proyecto
```
src/
├── app/
├── assets/
└── styles/
    ├── 00-settings/
    ├── 01-tools/
    ...
```

## Documentación
Ver documentación técnica completa en [`docs/DOCUMENTACION.md`](docs/DOCUMENTACION.md)

## Autor/a
[Tu nombre]  
[Curso y año]
---


### DOCUMENTACION.md - Estructura del informe técnico
El archivo docs/DOCUMENTACION.md debe seguir esta estructura:
# Documentación Técnica - Órbita 3: Maquetar para dar forma

**Proyecto:** [Nombre del proyecto]  
**Autor:** [Tu nombre]  
**Fecha:** [Fecha de entrega]  
**Módulo:** Diseño de Interfaces Web (DIW)  
**URL Producción:** https://tu-proyecto.vercel.app

---

## Tabla de contenidos

1. [Arquitectura CSS y comunicación visual](#1-arquitectura-css-y-comunicación-visual)
2. [HTML semántico y estructura](#2-html-semántico-y-estructura)
3. [Sistema de componentes UI](#3-sistema-de-componentes-ui)
4. [Estrategia Responsive](#4-estrategia-responsive)
5. [Optimización multimedia](#5-optimización-multimedia)
6. [Sistema de temas](#6-sistema-de-temas)
7. [Informe de accesibilidad](#7-informe-de-accesibilidad)

---

## 1. Arquitectura CSS y comunicación visual

### 1.1 Principios de comunicación visual

[Explicación de los 5 principios básicos: jerarquía, contraste, alineación, proximidad, repetición]

[Ejemplos concretos de aplicación en tu proyecto con capturas de pantalla]

### 1.2 Metodología CSS

**Metodología elegida:** [BEM/SMACSS/otra]

**Justificación:** [Por qué elegiste esta metodología]

**Ejemplo de aplicación:**
```scss
// Ejemplo de código
```

### 1.3 Organización de archivos

[Explicación de la estructura de carpetas]
```
styles/
├── 00-settings/
│   ├── _variables.scss
│   └── _colors.scss
├── 01-tools/
...
```

### 1.4 Sistema de Design Tokens

**Variables de color:**
```scss
// Ejemplo de tus variables
```

**Escala tipográfica:**
```scss
// Ejemplo
```

**Sistema de espaciado:**
```scss
// Ejemplo
```

### 1.5 Mixins y funciones

[Documentación de tus mixins principales]
```scss
@mixin respond-to($breakpoint) {
  // código
}
```

### 1.6 ViewEncapsulation en Angular

[Explicación de tu estrategia]

---

## 2. HTML semántico y estructura

### 2.1 Elementos semánticos utilizados

[Explicación de cuándo y cómo usas article, section, nav, aside, header, footer]

**Ejemplo de estructura:**
```html
<!-- Código ejemplo -->
```

### 2.2 Jerarquía de headings

[Explicación de tu estrategia de headings]

[Diagrama o ejemplo de la jerarquía en tu proyecto]

### 2.3 Landmarks ARIA

[Lista de landmarks implementados y dónde]

### 2.4 Formularios accesibles

[Ejemplo de tu estructura de formularios]
```html
<!-- Código ejemplo de formulario -->
```

---

## 3. Sistema de componentes UI

### 3.1 Componentes implementados

Lista de componentes desarrollados:

1. **Botones**
    - Variantes: primary, secondary, ghost
    - Tamaños: sm, md, lg
    - Estados: hover, focus, active, disabled, loading

2. **Cards**
    - [Descripción]

[Continuar con los 8+ componentes]

### 3.2 Nomenclatura y metodología

[Ejemplos de nomenclatura BEM aplicada]
```scss
.card {
  &__header { }
  &__body { }
  &--featured { }
}
```

### 3.3 Style Guide

[Capturas de pantalla del Style Guide]

![Style Guide - Botones](ruta/a/imagen.png)

---

## 4. Estrategia Responsive

### 4.1 Breakpoints

**Breakpoints definidos:**
- Mobile: 320px - 767px
- Tablet: 768px - 1023px
- Desktop: 1024px+

**Justificación:** [Por qué estos breakpoints]

### 4.2 Mobile-first

[Explicación de tu implementación mobile-first]

**Ejemplo:**
```scss
// Código ejemplo
```

### 4.3 Container Queries

**Componentes con Container Queries:**

1. **[Componente 1]**
```scss
   // Código
```

2. **[Componente 2]**
```scss
   // Código
```

### 4.4 Screenshots comparativos

**Mobile:**
![Vista mobile](ruta/imagen-mobile.png)

**Tablet:**
![Vista tablet](ruta/imagen-tablet.png)

**Desktop:**
![Vista desktop](ruta/imagen-desktop.png)

---

## 5. Optimización multimedia

### 5.1 Formatos elegidos

| Tipo | Formato | Justificación |
|------|---------|---------------|
| Imágenes fotográficas | WebP + JPG fallback | [justificación] |
| Iconos | SVG | [justificación] |
| ... | ... | ... |

### 5.2 Herramientas utilizadas

- **Squoosh:** Para optimización de imágenes
- **SVGO:** Para optimización de SVGs
- [Otras herramientas]

### 5.3 Resultados de optimización

**Tabla comparativa:**

| Imagen | Antes | Después | Reducción |
|--------|-------|---------|-----------|
| hero.jpg | 850 KB | 180 KB | 78% |
| thumbnail.jpg | 120 KB | 35 KB | 71% |
| ... | ... | ... | ... |

### 5.4 Performance budget

- Imágenes hero: < 300KB ✅
- Thumbnails: < 50KB ✅
- Iconos SVG: < 5KB ✅
- Total página: < 2MB ✅

### 5.5 Tecnologías implementadas

**Picture con srcset:**
```html
<picture>
  <!-- Código ejemplo -->
</picture>
```

**Lazy loading:**
```html
<img loading="lazy" ... />
```

### 5.6 Animaciones CSS

[Descripción de las 3+ animaciones implementadas]
```scss
@keyframes spin {
  // código
}
```

---

## 6. Sistema de temas

### 6.1 Variables de tema
```scss
:root {
  --color-bg-primary: #ffffff;
  --color-text-primary: #1a1a1a;
  ...
}

[data-theme="dark"] {
  --color-bg-primary: #1a1a1a;
  --color-text-primary: #ffffff;
  ...
}
```

### 6.2 Implementación del Theme Switcher

[Explicación de cómo funciona]
```typescript
// Código del componente
```

### 6.3 Testing de contraste

**Modo claro:**
- Texto normal: 4.8:1 ✅
- Texto grande: 3.2:1 ✅

**Modo oscuro:**
- Texto normal: 5.1:1 ✅
- Texto grande: 3.5:1 ✅

### 6.4 Capturas de pantalla

**Tema claro:**
![Tema claro](ruta/tema-claro.png)

**Tema oscuro:**
![Tema oscuro](ruta/tema-oscuro.png)

---

## 7. Informe de accesibilidad

### 7.1 Importancia de la accesibilidad

[Explicación de por qué la accesibilidad es fundamental]

[Ejemplos de cómo beneficia a diferentes usuarios]

### 7.2 Principios WCAG implementados

#### Perceptible
- [Criterios implementados]

#### Operable
- [Criterios implementados]

#### Comprensible
- [Criterios implementados]

#### Robusto
- [Criterios implementados]

### 7.3 Nivel de conformidad

**Nivel alcanzado:** A / AA

**Criterios de nivel A cubiertos:**
- [ ] 1.1.1 Contenido no textual
- [ ] 1.2.1 Solo audio y solo video (pregrabado)
- [ ] 1.3.1 Información y relaciones
- [ ] 1.4.1 Uso del color
- [ ] 2.1.1 Teclado
- [Continuar con lista completa]

### 7.4 Tests de accesibilidad

#### Lighthouse
![Lighthouse Accessibility Score](ruta/lighthouse.png)

**Puntuación:** [tu puntuación]/100

#### WAVE / axe DevTools
![WAVE Report](ruta/wave.png)

**Resumen:**
- Errores: [número]
- Alertas: [número]
- Características: [número]

### 7.5 Problemas encontrados y soluciones

| Problema | Solución aplicada |
|----------|-------------------|
| Contraste insuficiente en botones secundarios | Ajustado color de fondo de #e0e0e0 a #d0d0d0 |
| ... | ... |

### 7.6 Navegación por teclado

**Elementos verificados:**
- [ ] Navegación principal (Tab, Enter)
- [ ] Formularios (Tab, Space, Enter)
- [ ] Modales (Esc para cerrar)
- [ ] Menú hamburguesa (Enter, Esc)
- [ ] Componentes interactivos

**Orden de tabulación:** Lógico y secuencial ✅

### 7.7 Test con lector de pantalla

**Herramienta:** NVDA / VoiceOver

**Páginas testeadas:**
- Página principal
- [Otras páginas]

**Resultados:**
- Landmarks correctamente anunciados ✅
- Formularios con labels claros ✅
- Imágenes con alt text descriptivo ✅
- [Otros resultados]

### 7.8 Verificación multi-navegador

| Navegador | Versión | Resultado |
|-----------|---------|-----------|
| Chrome | [versión] | ✅ |
| Firefox | [versión] | ✅ |
| Safari | [versión] | ✅ |
| Edge | [versión] | ✅ |

### 7.9 Checklist de verificación

**HTML semántico:**
- [x] Uso correcto de elementos semánticos
- [x] Jerarquía de headings sin saltos
- [x] Landmarks apropiados

**Contraste:**
- [x] Texto normal: mínimo 4.5:1
- [x] Texto grande: mínimo 3:1
- [x] Componentes UI: mínimo 3:1

**Navegación:**
- [x] Todos los elementos accesibles por teclado
- [x] Focus visible en todos los elementos
- [x] Skip links implementados (si aplica)

**Contenido:**
- [x] Alt text en todas las imágenes
- [x] Labels en todos los inputs
- [x] Errores de formulario descriptivos

**ARIA:**
- [x] Roles ARIA apropiados
- [x] Estados ARIA correctos
- [x] Propiedades ARIA necesarias

---

## Conclusiones

[Reflexión sobre el proyecto, aprendizajes, dificultades encontradas]

---

## Referencias

- [Lista de recursos consultados]
- [Documentación utilizada]
- [Herramientas empleadas]

