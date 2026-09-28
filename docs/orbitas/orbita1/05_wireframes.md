# Órbita 1 — Conocer a las personas

## 5. Del flujo al wireframe

<div style="background:#1F0318; border:3px solid #1F0318; box-shadow:6px 6px 0 #E93456; padding:28px 36px; display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:24px; margin:32px 0;">
  <div>
    <p style="margin:0 0 8px 0; color:#FFB8DE; font-weight:700; text-transform:uppercase; letter-spacing:1px; font-size:0.85rem;">Diapositivas del apartado</p>
    <p style="margin:0; color:#ffffff; font-size:1.1rem; font-weight:600;">Del user flow al wireframe lo-fi en Figma y el prototipo navegable.</p>
  </div>
  <a href="../slides/orbita1_05_wireframes.pdf" target="_blank" rel="noopener" style="background:#E93456 !important; color:#ffffff !important; border:3px solid #1F0318 !important; box-shadow:4px 4px 0 #1F0318 !important; padding:14px 28px; font-weight:700; text-transform:uppercase; letter-spacing:1px; text-decoration:none !important; white-space:nowrap; border-bottom:none !important;">Descargar presentación →</a>
</div>


El wireframe traduce el user flow y el sitemap en pantallas concretas, sin entrar todavía en diseño visual. El user flow aporta el orden: qué pantalla sigue a cuál para completar una tarea. El sitemap aporta el contenido: qué pantallas existen, cómo se llaman y cómo se relacionan entre sí.

Un wireframe es **una herramienta de decisión**: valida que la estructura de cada pantalla resuelve lo que el flujo promete, antes de invertir tiempo en tipografía, color o estilos.

### Cómo se combinan el flujo y la arquitectura

Cada wireframe que vas a dibujar corresponde a un nodo del sitemap, y el orden en que los dibujas y los conectas lo marca el user flow. El sitemap te da el nombre exacto de cada pantalla (el mismo que usaste al construirlo) y te dice si es principal, secundaria o de sistema, lo que ayuda a decidir cuánto detalle necesita: una pantalla principal suele requerir más elementos que una de sistema como una confirmación o un error. El flujo te dice qué pantalla sigue a cuál dentro del happy path, y esa secuencia es la que vas a poder recorrer en el prototipo navegable.

Trabajar con las dos piezas a la vez evita dos errores típicos: wireframear una pantalla que no está en el sitemap (contenido inventado sobre la marcha) o conectar dos pantallas en un orden que el flujo no contempla (RA1-c).

### Qué pantallas hay que wireframear

Solo las que aparecen en el user flow del happy path, más las pantallas de error o estado vacío que hayas identificado como críticas para tu persona. Si tu flujo tiene ocho pasos, necesitas wireframes para exactamente esos ocho pasos.

Una pantalla que no está en el flujo no tiene justificación todavía, aunque exista en el sitemap. Si el flujo la necesita más adelante, la wireframeas entonces.

### Cómo se hace un wireframe lo-fi en Figma

La fidelidad baja tiene unas convenciones concretas. **Escala de grises**: negro, blanco y un gris medio. Sin tipografía real: los textos de cuerpo se representan con líneas horizontales de grosor uniforme. Los títulos sí pueden escribirse si ayudan a entender el contenido de la pantalla. Las imágenes van como rectángulos con una X dentro. Los botones, campos e iconos se representan como formas geométricas simples.

El objetivo es que quien mire el wireframe entienda qué hace cada elemento sin que el estilo visual distraiga la atención.

En Figma trabajas con un frame del tamaño del dispositivo de tu persona. Si tu persona primaria usa móvil Android, el frame de trabajo es 360×800. Si usa portátil, el frame es 1280×800. Si tienes ambos perfiles, wireframeas para los dos dispositivos desde el principio: las decisiones de layout que tomas en lo-fi son las que después condicionan el responsive en la Órbita 3.

Nombra cada frame con el mismo nombre que tiene esa pantalla en el sitemap. Un flujo puede pasar dos veces por la misma pantalla (por ejemplo, "Carrito" en dos momentos distintos de una compra), y el nombre del sitemap deja claro que se trata de la misma pantalla las dos veces. Esa disciplina mantiene la trazabilidad entre el sitemap, el user flow y los wireframes a lo largo de todo el módulo (RA1-a).

### Lo que no se decide todavía

Fuentes, colores, espaciado exacto, iconografía, imágenes. Esas decisiones son de la Órbita 2. Si en este punto te encuentras tomando decisiones visuales, para: estás saltando una fase.

La tentación más habitual es añadir color para distinguir elementos. Si necesitas distinguir algo, usa el gris medio. Si aun así no queda claro qué hace el elemento, el problema está en la estructura, y hay que resolverlo ahí antes de añadir color.

### El prototipo navegable

Una vez tienes los wireframes de todas las pantallas del happy path, los conectas en Figma con **interacciones básicas**: un tap o click en un botón lleva a la siguiente pantalla. Nada más.

Este prototipo lo-fi sirve para una sola cosa: comprobar que el flujo funciona cuando alguien lo recorre sin que nadie le explique nada. Si necesitas explicar algo durante el test, hay un problema de diseño que resolver antes de pasar a alta fidelidad.

El test con el prototipo lo-fi es el mismo test de cinco segundos que usaste en la investigación, pero ahora sobre tu propio trabajo. Puedes hacerlo en Lyssna con el prototipo de Figma enlazado directamente. Con cuatro o cinco personas del perfil de tu persona principal es suficiente para detectar los problemas más graves (RA1-c, RA6-a).
