# **FASE 5: MULTIMEDIA OPTIMIZADA**

**Criterios:** RA3.b, RA3.c, RA3.d, RA3.f, RA4.a, RA4.e  
**Entrega:** 14 de enero

## **OBJETIVOS DE LA FASE**

Optimizar todos los recursos multimedia de tu aplicación para que cargue rápido sin sacrificar calidad visual. Implementar técnicas modernas de imágenes responsive y crear animaciones CSS fluidas.

Esta fase se coordina con **DWEC Fase 5** donde implementas la carga dinámica de imágenes mediante servicios HTTP.

## **TAREAS**

### **1. Optimización de imágenes**

Optimiza todas las imágenes de tu aplicación. Todas las imágenes deben pesar menos de 200KB cada una.

**Formatos a usar:**
- AVIF, WebP y/o JPG

**Múltiples tamaños:**
Genera versiones de cada imagen en al menos 3 tamaños: small (400px), medium (800px), large (1200px).

**Herramientas:**
- Squoosh (https://squoosh.app/)
- TinyPNG (https://tinypng.com/)
- ImageOptim (Mac) o FileOptimizer (Windows)

### **2. Optimización de SVGs**

Optimiza todos los iconos y gráficos SVG usando SVGO (https://jakearchibald.github.io/svgomg/).

### **3. Imágenes responsive**

Implementa técnicas de imágenes responsive:
- `srcset` y `sizes` para imágenes que mantienen proporción
- Elemento `<picture>` para art direction (imagen diferente mobile/desktop)
- `loading` para la carga

### **4. Animaciones CSS optimizadas**

Crea al menos 3 animaciones CSS diferentes:
- Loading spinner para estados de carga
- Transiciones hover/focus en mínimo 5 elementos
- Micro-interacción (bounce, slide-in, fade-in, etc.)

**Reglas:**
- Anima solo `transform` y `opacity`
- Duración entre 150ms y 500ms

### **5. Documentación en DOCUMENTACION.md**

Añade la **Sección 5: Optimización multimedia** a tu archivo `docs/DOCUMENTACION.md`.

Esta sección debe incluir:

**5.1 Formatos elegidos:** Explica qué formatos usas y cuándo usas cada uno. Justifica el uso de AVIF vs WebP vs JPG.

**5.2 Herramientas utilizadas:** Lista herramientas usadas para optimizar.

**5.3 Resultados de optimización:** Tabla con al menos 5 imágenes mostrando nombre, tamaño original, tamaño optimizado y porcentaje de reducción.

**5.4 Tecnologías implementadas:** Documenta dónde y cómo usaste `<picture>`, `srcset`, `sizes`, y `loading="lazy"`. Incluye ejemplos de código.

**5.5 Animaciones CSS:** Lista animaciones implementadas con descripción y código. Explica por qué solo animas transform y opacity.

## **ENTREGABLES FASE 5**

- Todas las imágenes optimizadas (< 200KB cada una)
- Imágenes en formato AVIF, WebP y/o JPG
- Múltiples tamaños de cada imagen (mínimo 2-3)
- SVGs optimizados con SVGO
- Implementación de srcset + sizes
- Implementación de `<picture>` en al menos 2 imágenes
- Loading implementado
- Mínimo 3 animaciones CSS optimizadas
- Sección 5 del `docs/DOCUMENTACION.md` completada con tabla de optimización


