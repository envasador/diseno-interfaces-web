# Órbita 1 — Conocer a las personas

## 5. Del flujo al wireframe

<div style="background:#1F0318; border:3px solid #1F0318; box-shadow:6px 6px 0 #E93456; padding:28px 36px; display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:24px; margin:32px 0;">
  <div>
    <p style="margin:0 0 8px 0; color:#FFB8DE; font-weight:700; text-transform:uppercase; letter-spacing:1px; font-size:0.85rem;">Diapositivas del apartado</p>
    <p style="margin:0; color:#ffffff; font-size:1.1rem; font-weight:600;">Del user flow al wireframe lo-fi en Figma y el prototipo navegable.</p>
  </div>
  <a href="../slides/orbita1_05_wireframes.pdf" target="_blank" rel="noopener" style="background:#E93456 !important; color:#ffffff !important; border:3px solid #1F0318 !important; box-shadow:4px 4px 0 #1F0318 !important; padding:14px 28px; font-weight:700; text-transform:uppercase; letter-spacing:1px; text-decoration:none !important; white-space:nowrap; border-bottom:none !important;">Descargar presentación →</a>
</div>


Cuando terminas el user flow tienes algo valioso: sabes qué tiene que hacer la interfaz y en qué orden. Lo que no tienes todavía es una propuesta de cómo va a verse. El wireframe es ese paso intermedio. Traduce el flujo en pantallas concretas sin entrar todavía en diseño visual.

La distinción importa. Un wireframe es **una herramienta de decisión**: te permite validar que la estructura de cada pantalla resuelve lo que el flujo promete, antes de invertir tiempo en tipografía, color o estilos.

### Qué pantallas hay que wireframear

No todas. Las que necesitas son las que aparecen en el user flow del happy path más las pantallas de error o estado vacío que hayas identificado como críticas para tu persona. Si tu flujo tiene ocho pasos, necesitas wireframes para esos ocho pasos. No más.

Una pantalla que no está en el flujo no tiene justificación todavía. Si aparece más adelante, la añades entonces.

### Cómo se hace un wireframe lo-fi en Figma

La fidelidad baja tiene unas convenciones concretas. **Escala de grises**: negro, blanco y un gris medio. Sin tipografía real: los textos de cuerpo se representan con líneas horizontales de grosor uniforme. Los títulos sí pueden escribirse si ayudan a entender el contenido de la pantalla. Las imágenes van como rectángulos con una X dentro. Los botones, campos e iconos se representan como formas geométricas simples.

El objetivo es que quien mire el wireframe entienda qué hace cada elemento sin que el estilo visual distraiga la atención.

En Figma trabajas con un frame del tamaño del dispositivo de tu persona. Si tu persona primaria usa móvil Android, el frame de trabajo es 360×800. Si usa portátil, el frame es 1280×800. Si tienes ambos perfiles, wireframeas para los dos dispositivos desde el principio: las decisiones de layout que tomas en lo-fi son las que después condicionan el responsive en la Órbita 3.

Nombra cada frame con el nombre del paso del flujo al que corresponde. Eso mantiene la trazabilidad entre el user flow y los wireframes a lo largo de todo el módulo (RA1-a).

### Lo que no se decide todavía

Fuentes, colores, espaciado exacto, iconografía, imágenes. Esas decisiones son de la Órbita 2. Si en este punto te encuentras tomando decisiones visuales, para: estás saltando una fase.

La tentación más habitual es añadir color para distinguir elementos. Si necesitas distinguir algo, usa el gris medio. Si aun así no queda claro qué hace el elemento, el problema es estructural, no visual, y hay que resolverlo antes de añadir color.

### El prototipo navegable

Una vez tienes los wireframes de todas las pantallas del happy path, los conectas en Figma con **interacciones básicas**: un tap o click en un botón lleva a la siguiente pantalla. Nada más.

Este prototipo lo-fi sirve para una sola cosa: comprobar que el flujo funciona cuando alguien lo recorre sin que nadie le explique nada. Si necesitas explicar algo durante el test, hay un problema de diseño que resolver antes de pasar a alta fidelidad.

El test con el prototipo lo-fi es el mismo test de cinco segundos que usaste en la investigación, pero ahora sobre tu propio trabajo. Puedes hacerlo en Lyssna con el prototipo de Figma enlazado directamente. Con cuatro o cinco personas del perfil de tu persona principal es suficiente para detectar los problemas más graves (RA1-c, RA6-a).


### Lo que te llevas de este apartado

El wireframe traduce el user flow en pantallas sin entrar todavía en decisiones visuales. Wireframeas solo lo que aparece en el flujo, en escala de grises, y lo conectas en un prototipo navegable para validar que el camino funciona antes de invertir en diseño visual.
