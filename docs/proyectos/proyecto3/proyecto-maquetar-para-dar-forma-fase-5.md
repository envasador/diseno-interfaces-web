# **FASE 5: MULTIMEDIA OPTIMIZADA**

**Criterios:** RA3.b, RA3.c, RA3.d, RA3.f, RA4.a, RA4.e  
**Entrega:** Después de Navidad

## **OBJETIVOS DE LA FASE**

En esta fase optimizarás todos los recursos multimedia de tu aplicación para que cargue rápido sin sacrificar calidad visual. Aprenderás a elegir los formatos correctos, usar herramientas de optimización profesionales, implementar imágenes responsive con técnicas modernas, y crear animaciones CSS fluidas.

No se trata solo de "meter imágenes", sino de hacerlo bien: formato WebP con fallback, múltiples tamaños para diferentes dispositivos, lazy loading para mejorar el rendimiento, SVGs optimizados, y animaciones que corren a 60fps usando transform y opacity.

## **TAREAS**

### **1. Optimización de imágenes**

Optimiza todas las imágenes de tu aplicación:

**Formatos modernos:**
- Convierte imágenes a formato WebP para mejor compresión
- Mantén fallback en JPG o PNG para navegadores antiguos
- Todas las imágenes deben pesar menos de 200KB

**Múltiples tamaños:**
- Genera versiones de cada imagen en al menos 3 tamaños: small (400px), medium (800px), large (1200px)
- Usa nombres descriptivos: `hero-400w.webp`, `hero-800w.webp`, `hero-1200w.webp`

**Herramientas recomendadas:**
- Squoosh (https://squoosh.app/) - online, fácil de usar
- TinyPNG (https://tinypng.com/) - compresión automática
- ImageOptim (Mac) o FileOptimizer (Windows) - apps desktop

Documenta el proceso y crea una tabla antes/después mostrando el tamaño original vs optimizado.

### **2. Optimización de SVGs**

Optimiza todos los iconos y gráficos SVG:

**Proceso de optimización:**
- Usa SVGO (https://jakearchibald.github.io/svgomg/) para limpiar código innecesario
- Elimina metadatos, comentarios, y elementos ocultos
- Simplifica paths cuando sea posible
- Reduce decimales en coordenadas

**Implementación:**
- SVGs inline para iconos pequeños que usas frecuentemente
- SVGs como archivos externos para ilustraciones grandes
- Considera crear un sprite SVG si tienes muchos iconos

### **3. Imágenes responsive con picture y srcset**

Implementa imágenes responsive usando las técnicas modernas:

**Usando srcset y sizes:**
Para imágenes que mantienen la misma proporción en todos los viewports, usa `srcset` con `sizes` para que el navegador elija la mejor imagen según el ancho del viewport y densidad de píxeles.

**Usando picture para art direction:**
Para imágenes que cambian completamente en mobile vs desktop (diferentes crops, diferentes imágenes), usa el elemento `<picture>` con múltiples `<source>`.

**Lazy loading:**
Añade el atributo `loading="lazy"` a todas las imágenes que no están en el viewport inicial (above the fold).

Implementa esto en todas las imágenes principales de tus páginas (home, listado, detalle).

### **4. Animaciones CSS optimizadas**

Crea al menos 3 animaciones CSS diferentes:

**Tipos de animaciones requeridas:**

**Loading spinner:** Animación de carga para estados loading de botones o mientras se cargan datos. Debe usar `@keyframes` y animar solo `transform` (rotate) para 60fps.

**Transiciones hover/focus:** Implementa transiciones suaves en al menos 5 elementos diferentes (botones, cards, enlaces, inputs, etc.). Usa propiedades animables de alto rendimiento (transform, opacity).

**Micro-interacciones:** Añade al menos una micro-interacción (ejemplo: botón que hace "bounce" al hacer clic, notificación que se desliza desde el lateral, modal que aparece con fade + scale).

**Reglas de optimización:**
- SOLO anima `transform` y `opacity` para 60fps constantes
- NUNCA animes `width`, `height`, `top`, `left` (causan reflow)
- Usa `will-change` solo cuando sea absolutamente necesario
- Todas las animaciones deben durar entre 150ms y 500ms

### **5. Performance budget**

Define y verifica un presupuesto de rendimiento:

**Límites máximos:**
- Peso total de la página: < 2MB
- Peso de imágenes: < 1MB por página
- Número de requests: < 50
- First Contentful Paint (FCP): < 1.5s
- Largest Contentful Paint (LCP): < 2.5s

Usa Lighthouse en Chrome DevTools para medir. Documenta las métricas actuales.

### **6. Integración en componentes**

Integra las optimizaciones en tus componentes existentes:

**En componentes cards:** Usa imágenes WebP con srcset y lazy loading.

**En hero sections:** Usa picture para art direction (imagen diferente mobile/desktop).

**En botones:** Añade spinner animado para estado loading.

**En navegación:** Añade transiciones suaves al abrir/cerrar menú mobile.

**En modales/alerts:** Añade animaciones de entrada/salida.

### **7. Documentación en DOCUMENTACION.md**

Añade la **Sección 5: Optimización multimedia** a tu archivo `docs/DOCUMENTACION.md`.

Esta sección debe incluir:

**5.1 Formatos elegidos:** Explica qué formatos usas (WebP, JPG, PNG, SVG) y justifica cuándo usas cada uno. Incluye tabla comparativa de soporte de navegadores si usas formatos modernos.

**5.2 Herramientas utilizadas:** Lista las herramientas que usaste para optimizar (Squoosh, TinyPNG, SVGO, etc.) y describe brevemente el proceso.

**5.3 Resultados de optimización:** Crea una tabla mostrando al menos 5 imágenes con tamaño antes/después de optimizar y porcentaje de reducción.

**5.4 Performance budget:** Documenta tus límites definidos y las métricas actuales medidas con Lighthouse. Si alguna métrica está por encima del límite, explica qué harás para mejorarla.

**5.5 Tecnologías implementadas:** Documenta dónde y cómo usaste picture, srcset, sizes, y lazy loading. Incluye ejemplos de código.

**5.6 Animaciones CSS:** Lista las animaciones implementadas, describe cada una, y muestra el código de los `@keyframes`. Explica por qué solo animas transform y opacity.


## **ENTREGABLES FASE 5**

- Todas las imágenes optimizadas (< 200KB cada una)
- Imágenes en formato WebP con fallback JPG/PNG
- Múltiples tamaños de cada imagen (mínimo 3)
- SVGs optimizados con SVGO
- Implementación de srcset + sizes en imágenes principales
- Implementación de picture en al menos 2 imágenes (art direction)
- Lazy loading en todas las imágenes below the fold
- Mínimo 3 animaciones CSS: spinner + transiciones + micro-interacción
- Performance budget definido y verificado con Lighthouse
- Sección 5 del `docs/DOCUMENTACION.md` completada con tabla de optimización y capturas
