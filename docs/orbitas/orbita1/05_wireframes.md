# Órbita 1 — Conocer a las personas

## 5. Del flujo al wireframe

Antes de elegir los azulejos del baño, alguien dibujó el plano de la casa: dónde va cada habitación, por dónde se entra y qué puerta da a qué pasillo. Nadie discute el color de los azulejos con el arquitecto si el baño todavía no tiene puerta. El **wireframe** es ese plano para tu interfaz.

Convierte el user flow y el sitemap en pantallas concretas, todavía sin diseño visual. El flujo pone el orden: qué pantalla viene después de cuál para completar una tarea. El sitemap pone el contenido: qué pantallas existen, cómo se llaman y cómo se relacionan. Y el wireframe comprueba que la estructura de cada pantalla cumple lo que el flujo promete, antes de que inviertas una sola hora en tipografía o color. Es una **herramienta de decisión**, y como tal se juzga.

### Cómo se combinan el flujo y la arquitectura

Cada wireframe corresponde a un nodo del sitemap, y el orden en que los dibujas y los conectas lo marca el user flow. El sitemap te da el nombre exacto de cada pantalla y te dice si es principal, secundaria o de sistema, lo que te orienta sobre cuánto detalle necesita: una pantalla principal suele llevar bastantes más elementos que una confirmación o un error. El flujo te dice qué pantalla sigue a cuál dentro del happy path, y esa secuencia es la que luego podrás recorrer en el prototipo.

Trabajar con las dos piezas delante te protege de dos errores muy típicos: dibujar una pantalla que no está en el sitemap (contenido inventado sobre la marcha) y conectar dos pantallas en un orden que el flujo no contempla (RA1-c).

### Qué pantallas hay que dibujar

Las del happy path de tu user flow, más las pantallas de error o de estado vacío que hayas marcado como críticas para tus personas. Si tu flujo tiene ocho pasos, necesitas ocho wireframes. Ni siete ni doce.

Una pantalla que existe en el sitemap pero no aparece en el flujo puede esperar. Cuando el flujo la necesite, la dibujas.

### Cómo se hace un wireframe lo-fi en Figma

La baja fidelidad tiene unas convenciones bastante concretas. **Escala de grises**: negro, blanco y un gris medio. Nada de tipografía real: los textos de cuerpo se representan con líneas horizontales del mismo grosor, y los títulos solo se escriben si ayudan a entender qué hay en la pantalla. Las imágenes son rectángulos con una X dentro. Botones, campos e iconos, formas geométricas simples.

La idea es que quien lo mire entienda qué hace cada elemento sin que nada le distraiga de la pregunta importante, que es si la pantalla funciona.

Trabajas en un frame del tamaño del dispositivo de tu persona. Lucía reserva desde un Android, así que su frame es de 360×800. Si tu persona primaria trabaja con portátil, 1280×800. Si tienes los dos perfiles, dibujas para los dos dispositivos desde el principio, porque las decisiones de layout que tomas aquí son las que luego condicionan el responsive de la Órbita 3.

Ponle a cada frame el mismo nombre que tiene esa pantalla en el sitemap. Un flujo puede pasar dos veces por la misma pantalla (el "Detalle de reserva" antes de pagar y después de cancelar, por ejemplo), y el nombre deja claro que es la misma las dos veces. Parece una manía. Es lo que mantiene unidos el sitemap, el flujo y los wireframes durante todo el módulo (RA1-a).

### Lo que todavía no se decide

Fuentes, colores, espaciados exactos, iconografía, imágenes. Todo eso es de la Órbita 2. Si te sorprendes eligiendo un tono de azul, para: te estás saltando una fase.

La tentación más frecuente es meter color para distinguir elementos. Si necesitas distinguir algo, usa el gris medio. Y si aun así no se entiende qué hace ese elemento, el problema está en la estructura, que es donde hay que arreglarlo. Si en grises no funciona, el color no lo va a rescatar.

### El prototipo navegable

Cuando tengas los wireframes de todo el happy path, conéctalos en Figma con **interacciones básicas**: un toque o un clic en un botón lleva a la pantalla siguiente. Nada más. Ni animaciones ni transiciones bonitas.

Este prototipo sirve para una sola cosa: comprobar que el flujo funciona cuando alguien lo recorre sin que nadie le explique nada. Y aquí vuelve la prueba incómoda del primer apartado. Si durante el test te pillas diciendo "no, eso es el botón de...", acabas de encontrar un problema de diseño, y hay que resolverlo antes de pasar a alta fidelidad.

Puedes montar el test en Lyssna enlazando directamente el prototipo de Figma, igual que hiciste con los referentes en la investigación, pero ahora sobre tu propio trabajo. Con cuatro o cinco personas que encajen con tu persona primaria tienes suficiente para detectar los problemas más graves (RA1-c, RA6-a).
