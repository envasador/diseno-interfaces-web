# **FASE 7: ACCESIBILIDAD WEB**

**Criterios:** RA5.a, RA5.b, RA5.c, RA5.g  
**Entrega:** Segunda semana después de Navidad

## **OBJETIVOS DE LA FASE**

En esta fase implementarás y verificarás la accesibilidad de tu aplicación según las pautas WCAG 2.2 nivel A. No se trata solo de "pasar tests automáticos", sino de garantizar que tu interfaz sea realmente usable por todas las personas, independientemente de sus capacidades.

Implementarás los criterios de accesibilidad fundamentales, verificarás todo con herramientas automáticas y con tests manuales (navegación por teclado, lector de pantalla).

Al final de esta fase entregarás tu aplicación completamente funcional, accesible, y **desplegada con URL pública**.

## **TAREAS**

### **1. Implementación de contraste WCAG**

Verifica y corrige el contraste de colores en toda la aplicación según los requisitos WCAG AA:
- Texto normal: ratio mínimo 4.5:1
- Texto grande: ratio mínimo 3:1
- Componentes UI: ratio mínimo 3:1

Verifica todos los textos, placeholders, iconos, y estados de componentes. Usa herramientas de verificación de contraste.

### **2. Navegación por teclado**

Asegura que toda la funcionalidad sea accesible usando solo el teclado (Tab, Shift+Tab, Enter, Espacio, Escape). Verifica que todos los enlaces, botones, inputs, menús, modales y elementos interactivos sean navegables. El orden de tabulación debe ser lógico.

### **3. Estados de foco visibles**

Asegura que todos los elementos interactivos tengan estados de foco claramente visibles con suficiente contraste. Implementa outline o alternativas visuales en todos los elementos navegables.

### **4. Textos alternativos**

Proporciona textos alternativos apropiados para todo el contenido no textual:
- Imágenes de contenido: atributo `alt` descriptivo
- Imágenes decorativas: `alt=""` vacío
- Iconos funcionales: `aria-label` descriptivo
- Iconos decorativos: `aria-hidden="true"`

### **5. Estructura de headings y landmarks**

Verifica y corrige:
- Jerarquía de headings: solo un h1, orden lógico sin saltos
- Landmarks HTML5: header, nav, main, aside, footer correctamente implementados
- Atributos ARIA necesarios: aria-label, aria-current, role, aria-live, aria-describedby

### **6. Formularios accesibles**

Verifica que todos los formularios cumplan con:
- Labels asociados a inputs (for + id)
- Campos requeridos indicados correctamente
- Mensajes de error asociados y anunciados
- Agrupación con fieldset y legend
- Estados de validación con aria-invalid

### **7. Testing con herramientas automáticas**

Realiza tests automáticos con al menos 2 herramientas:
- Lighthouse (Chrome DevTools): objetivo mínimo 90 puntos
- WAVE o axe DevTools: revisar errores y alertas

Documenta puntuaciones obtenidas, errores encontrados y soluciones aplicadas.

### **8. Testing manual**

**Test de navegación por teclado:** Navega toda la aplicación usando solo teclado. Documenta el flujo y problemas encontrados.

**Test con lector de pantalla:** Usa NVDA (Windows) o VoiceOver (Mac/iOS). Navega al menos por la página principal. Documenta la experiencia.

**Test multi-navegador:** Prueba en Chrome, Firefox, y Safari (si tienes acceso). Documenta compatibilidad.

### **9. Despliegue de la aplicación**

Despliega tu aplicación en producción con URL pública accesible. Plataformas recomendadas: Vercel, Netlify, Firebase Hosting, GitHub Pages.

La aplicación debe:
- Tener URL pública funcional
- Cargar correctamente
- Todas las funcionalidades operativas
- Performance aceptable (Lighthouse > 80)

Documenta la URL en README.md y DOCUMENTACION.md.

### **10. Documentación en DOCUMENTACION.md**

Añade la **Sección 7: Informe de accesibilidad** a tu archivo `docs/DOCUMENTACION.md`.

Esta sección debe incluir:

**7.1 Importancia de la accesibilidad:** Explica por qué es importante diseñar webs accesibles con ejemplos de beneficios para diferentes usuarios.

**7.2 Principios WCAG implementados:** Explica los 4 principios WCAG (Perceptible, Operable, Comprensible, Robusto) y cómo tu aplicación los cumple.

**7.3 Nivel de conformidad alcanzado:** Indica el nivel WCAG alcanzado (A, AA, o AAA) con checklist de criterios cubiertos.

**7.4 Tests de accesibilidad:** Capturas de Lighthouse y WAVE/axe con puntuaciones. Resume errores y soluciones.

**7.5 Problemas encontrados y soluciones:** Tabla con problemas de accesibilidad, criterio WCAG violado, y solución aplicada.

**7.6 Test de navegación por teclado:** Describe el test, lista elementos del orden de tabulación, documenta si funciona correctamente.

**7.7 Test con lector de pantalla:** Documenta qué lector usaste, qué páginas probaste, describe la experiencia y problemas encontrados.

**7.8 Verificación multi-navegador:** Tabla con navegadores probados (nombre, versión) y resultados.

**7.9 Checklist de verificación:** Lista completa cubriendo HTML semántico, contraste, navegación teclado, contenido, multimedia, y ARIA.

## **ENTREGABLES FASE 7**

- Contraste verificado y corregido (4.5:1 texto, 3:1 UI)
- Navegación por teclado completamente funcional
- Estados de foco visibles en todos los elementos
- Textos alternativos en todas las imágenes
- Estructura de headings correcta
- Atributos ARIA implementados
- Formularios accesibles
- Tests con Lighthouse (> 90) y WAVE/axe documentados
- Test navegación teclado documentado
- Test lector de pantalla documentado
- Verificación multi-navegador documentada
- **Aplicación desplegada con URL pública funcional**
- **URL visible en README.md y DOCUMENTACION.md**
- Sección 7 del `docs/DOCUMENTACION.md` completada


## **REQUISITO OBLIGATORIO FINAL**

Tu aplicación debe estar **desplegada y accesible mediante URL pública**. Sin el despliegue, el proyecto no se considera completado.

La URL debe aparecer claramente en README.md y docs/DOCUMENTACION.md.
