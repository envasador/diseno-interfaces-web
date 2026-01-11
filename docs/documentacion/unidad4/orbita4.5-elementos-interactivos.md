
# 4.5: Integrar para que interactúe

## 1. ¿Qué son los elementos interactivos?
### 1.1. De documentos a aplicaciones

Durante décadas, la web fue principalmente un medio para **leer**: documentos estáticos con texto, imágenes y enlaces. Hacías click, cargaba otra página, repetías.

Los **elementos interactivos** transforman esa experiencia pasiva en algo activo. Ya no solo lees: exploras, manipulas, juegas, descubres. La web deja de ser un libro digital y se convierte en una aplicación.

**Un ejemplo concreto:**

Imagina la página de producto de Apple para el iPhone. No es solo una imagen estática con texto descriptivo. Cuando haces scroll:
- El iPhone aparece desde el lateral y rota mientras bajas
- Las diferentes capas del dispositivo se separan mostrando el interior
- Los colores cambian según la sección en la que estés
- El texto aparece sincronizado con el movimiento del producto

Esto no es un vídeo pregrabado. Es **interactivo**: responde a tu velocidad de scroll, puedes ir hacia atrás y adelante, se adapta al tamaño de tu pantalla. Tú controlas la experiencia.

### 1.2. Diferencia fundamental: estático vs interactivo

**Contenido estático:**
- Una foto de un producto que siempre se ve igual
- Un párrafo que simplemente está ahí para leer
- Un vídeo que reproduce linealmente de principio a fin

**Contenido interactivo:**
- Una galería donde puedes deslizar entre fotos, hacer zoom, ver desde diferentes ángulos
- Un formulario que valida en tiempo real ("Este email ya está registrado") sin recargar la página
- Un gráfico donde puedes filtrar datos, cambiar rangos de fechas, y la visualización se actualiza al instante
- Un modelo 3D que puedes rotar con el ratón o arrastrar con el dedo
- Un menú que se expande cuando pasas el cursor por encima
- Animaciones que solo se activan cuando llegas a esa parte de la página

### 1.3. ¿Por qué añadir interactividad?

**Feedback inmediato:**
Cuando escribes mal tu email en un formulario, no necesitas enviarlo, esperar, y que la página te diga "error". La interactividad te avisa mientras escribes: "ese formato no es válido". Reduces frustración.

**Exploración sin fricción:**
En vez de tener 20 páginas diferentes de producto mostrando cada color, tienes una sola página donde puedes cambiar el color haciendo click. La transición es instantánea, fluida. No pierdes contexto.

**Experiencia memorable:**
Una web estática se olvida. Una web que responde a tus acciones de forma sorprendente o deliciosa se recuerda. La tienda de Stripe, la página de producto de Apple, los portfolios ganadores de Awwwards: todos usan interactividad para crear momentos "wow".

**El equilibrio:**
No todo necesita moverse. Demasiada interactividad distrae, ralentiza, marea. Un artículo de blog probablemente no necesita que cada palabra flote al pasar el cursor. Pero una landing page de producto se beneficia de mostrar el producto desde todos los ángulos.

## 2. Tipos de elementos interactivos comunes

### 2.1. Navegación y menús

**El menú hamburguesa:**
Ese ícono de tres líneas en móvil que al tocarlo despliega el menú completo. Es interactivo porque:
- Responde al toque/click
- Anima la transición (no aparece de golpe, se desliza)
- Cambia de estado: de ☰ a ✕
- A veces incluye un overlay oscuro que aparece detrás

**Menús dropdown:**
Pasas el cursor sobre "Productos" y aparece un submenú con todas las categorías. En móvil, haces tap y se expande. La interactividad te ahorra tener que ir a una página intermedia.

**Breadcrumbs (migas de pan):**
Esas rutas que dicen "Inicio > Productos > Zapatillas > Nike Air". Cada elemento es clickable, te permite volver atrás sin usar el botón del navegador.

### 2.2. Modales y diálogos

Un **modal** es esa ventana que aparece sobre el contenido actual. Ejemplos:
- Click en "Ver tallas disponibles" → aparece modal con tabla de tallas
- Click en una imagen pequeña → aparece modal con imagen grande (lightbox)
- "¿Estás seguro de eliminar?" → modal de confirmación

La interactividad:
- Aparece con animación (fade in, slide down)
- El fondo se oscurece (overlay)
- Puedes cerrar presionando ESC o clickeando fuera
- El foco del teclado queda atrapado dentro del modal (no puedes navegar fuera accidentalmente)

### 2.3. Acordeones y pestañas (tabs)

**Acordeones:**
Típico en FAQs. Una lista de preguntas, al hacer click en una se expande mostrando la respuesta. Click en otra, la anterior se colapsa. Ahorras espacio mostrando solo lo relevante.

**Pestañas (tabs):**
En vez de tener tres páginas separadas para "Descripción", "Especificaciones", "Opiniones" de un producto, las tienes en pestañas. Click en una, cambia el contenido. No recarga la página, es instantáneo.

### 2.4. Formularios inteligentes

**Validación en tiempo real:**
Mientras escribes tu email, un pequeño ícono verde aparece si es válido, o rojo con mensaje de error si no. No esperas a enviar para saber que algo está mal.

**Autocompletado:**
Empiezas a escribir tu ciudad y aparece un dropdown con sugerencias. Click en una y se rellena automáticamente.

**Campos dependientes:**
Seleccionas "España" en país → el campo de provincia se actualiza con provincias españolas. Seleccionas "Portugal" → cambian las opciones. Todo sin recargar.

**Mostrar/ocultar según contexto:**
Checkbox "Dirección de facturación es diferente" → aparecen campos adicionales solo si lo marcas.

### 2.5. Tooltips y ayuda contextual

Pasas el cursor sobre un ícono de interrogación → aparece un pequeño cuadro explicativo. Quitas el cursor → desaparece. Es información adicional que no ocupa espacio hasta que la necesitas.

## 3. Animaciones y efectos visuales modernos

### 3.1. Animaciones al hacer scroll

Uno de los efectos más populares en webs modernas. Mientras bajas por la página:
- Elementos aparecen desde abajo con fade (empiezan invisibles y opacos, terminan visibles)
- Títulos se deslizan desde el lateral
- Números cuentan desde 0 hasta el valor final ("Más de 10,000 clientes satisfechos" cuenta de 0 a 10,000)
- Barras de progreso se llenan

**Por qué funciona:**
Llama la atención del usuario hacia contenido nuevo. En vez de que todo esté ahí desde el inicio (abrumador), va apareciendo conforme avanzas (guiado, narrativo).

### 3.2. Parallax scrolling

El efecto donde diferentes capas de la página se mueven a **diferentes velocidades** al hacer scroll. Crea sensación de profundidad.

Ejemplo clásico:
- Fondo (montañas lejanas): se mueve lento
- Capa intermedia (árboles): se mueve normal
- Primer plano (texto): se mueve rápido

El cerebro interpreta esto como "las montañas están lejos, el texto está cerca". Efecto 3D con elementos 2D.

**Dónde lo ves:**
Landing pages de videojuegos, sitios de storytelling (periodismo interactivo), portfolios creativos.

**Precaución:**
Puede marear a algunas personas. Se debe poder desactivar (lo veremos en accesibilidad).

### 3.3. Hover effects (efectos al pasar el cursor)

Cuando pasas el cursor sobre un botón:
- Cambia de color
- Se eleva (sombra más pronunciada)
- El texto cambia
- Un ícono se anima

Es **feedback visual inmediato** de que ese elemento es interactivo.

En portfolios de diseño:
- Pasas sobre una imagen de proyecto → se oscurece y aparece título + descripción
- Pasas sobre un enlace → aparece una línea animada debajo
- Pasas sobre el logo → rota o cambia de forma

### 3.4. Cursor personalizado

En vez del cursor estándar del sistema, algunos sitios usan uno personalizado que:
- Es un círculo que sigue el ratón
- Se agranda al pasar sobre elementos clicables
- Cambia de color según la sección de la página
- Arrastra una "estela" detrás

**Cuándo usarlo:**
Portfolios creativos, agencias de diseño, sitios experimentales. No lo uses en e-commerce o sitios corporativos (puede confundir).

### 3.5. Transiciones de página

En vez del efecto tradicional (click → página blanca → carga nueva página), algunas webs usan:
- Fade out de la página actual, fade in de la nueva
- Wipe effect (la nueva página entra deslizándose)
- Morphing: elementos de la página actual se transforman en los de la siguiente

## 4. Herramientas profesionales para interactividad

### 4.1. Three.js: Gráficos 3D en el navegador

**¿Qué es?**
Three.js es una librería JavaScript que permite crear gráficos 3D directamente en el navegador. Es lo que Apple usa para mostrar sus productos en 3D, lo que permite a Nike crear configuradores de zapatillas personalizadas, y lo que hace posibles los portfolios creativos con mundos 3D navegables.

**Para qué sirve:**
- Visualizar productos en 3D que el usuario puede rotar y explorar
- Crear backgrounds animados con partículas o geometrías abstractas
- Desarrollar experiencias inmersivas (recorridos virtuales, galerías 3D)
- Sincronizar animaciones 3D con el scroll (como hace Apple)
- Crear configuradores interactivos (cambiar colores, materiales, componentes de un producto)

**Nivel de complejidad:**
Alto. Requiere conocimientos de matemáticas 3D, conceptos de iluminación, materiales, cámaras. La curva de aprendizaje es de semanas/meses. Solo lo usas cuando el proyecto realmente lo justifica.

**Documentación y recursos:**
- Sitio oficial: https://threejs.org/
- Ejemplos oficiales: https://threejs.org/examples/
- Three.js Journey (curso completo): https://threejs-journey.com/

### 4.2. GSAP: Animaciones profesionales 2D

**¿Qué es?**
GSAP (GreenSock Animation Platform) es la librería de animaciones JavaScript más usada en la industria. Apple, Google, Nike, Adobe la usan. Es extremadamente potente para animar cualquier cosa: elementos HTML, propiedades CSS, SVG, valores numéricos, lo que sea.

**Para qué sirve:**
- Crear animaciones complejas sincronizadas con timing perfecto
- Efectos de scroll sofisticados (ScrollTrigger plugin)
- Transiciones suaves entre estados
- Secuencias de animaciones orquestadas
- Efectos de texto avanzados (revelar letra por letra, animaciones por palabra)
- Control total: pausar, revertir, acelerar, saltar a cualquier punto de la animación

**Ventaja sobre CSS:**
CSS animations son limitadas. GSAP ofrece control milimétrico, curvas de easing profesionales (bounce, elastic), y capacidad de animar absolutamente cualquier propiedad o valor numérico.

**Nivel de complejidad:**
Medio. Más fácil que Three.js, pero requiere práctica para dominarlo. La documentación es excelente.

**Documentación y recursos:**
- Sitio oficial: https://greensock.com/gsap/
- Documentación completa: https://greensock.com/docs/
- Showcase (inspírate): https://greensock.com/showcase/

### 4.3. Otras librerías útiles

**Lottie:**
Reproduce animaciones creadas en After Effects directamente en la web. Los diseñadores crean la animación en After Effects, la exportan como JSON, y Lottie la reproduce en el navegador.
- Sitio: https://airbnb.io/lottie/

**Barba.js:**
Especializada en transiciones entre páginas. Hace que la navegación entre páginas sea fluida, sin el típico "flash" de recarga.
- Sitio: https://barba.js.org/

**Swiper:**
Ya lo vimos en órbitas anteriores. Carruseles y galerías táctiles profesionales.
- Sitio: https://swiperjs.com/

**Locomotive Scroll:**
Smooth scroll avanzado con efectos parallax integrados.
- Sitio: https://locomotivemtl.github.io/locomotive-scroll/


## 5. Cuándo usar cada herramienta

### 5.1. Three.js

**Úsalo cuando:**
- El proyecto tiene presupuesto y tiempo suficiente
- Necesitas mostrar productos en 3D manipulables
- Quieres crear experiencias inmersivas o visualizaciones de datos 3D
- El cliente valora la innovación y la diferenciación visual
- La audiencia tiene dispositivos modernos (Three.js requiere GPU decente)

**No lo uses si:**
- Es un proyecto simple o con presupuesto limitado
- No tienes experiencia 3D y el deadline es ajustado
- La audiencia es principalmente móvil con dispositivos antiguos
- El valor no justifica la complejidad (a veces una buena foto funciona mejor)

### 5.2. GSAP

**Úsalo cuando:**
- El diseño incluye animaciones complejas o efectos de scroll sofisticados
- Necesitas timing preciso y control total sobre las animaciones
- Quieres crear experiencias fluidas y pulidas estilo Apple/Nike
- El proyecto es profesional y la experiencia visual importa

**NO lo uses si:**
- Las animaciones son muy simples (CSS animations pueden bastar)
- Quieres minimizar dependencias de JavaScript
- Es un proyecto de aprendizaje básico (empieza con CSS)

### 5.3. CSS + JavaScript vanilla

**Úsalo cuando:**
- Las animaciones son simples (fade, slide, rotate básicos)
- Quieres evitar dependencias externas
- Performance es crítica y el sitio debe ser ultra ligero
- Estás aprendiendo y quieres entender los fundamentos


## 6. Inspiración y aprendizaje

### 6.1. Sitios donde inspirarte

**Awwwards:**
Los mejores sitios web del mundo, premiados por diseño, interactividad y experiencia. Filtra por "Developer Award" para ver sitios técnicamente impresionantes.
- https://www.awwwards.com/

**Codrops:**
Tutoriales y demos de efectos específicos. "Cómo hacer este efecto de cursor personalizado", "Cómo crear esta transición de página".
- https://tympanus.net/codrops/

**CodePen:**
Miles de ejemplos de la comunidad. Busca "three.js", "gsap", "scroll animation" y encuentra demos interactivos que puedes explorar y modificar.
- https://codepen.io/

### 6.2. Comunidades

**Discord de Three.js:**
Ayuda de la comunidad, compartir proyectos, resolver dudas técnicas.

**Foros de GSAP:**
GreenSock tiene foros muy activos donde los desarrolladores (incluso el creador de GSAP) responden preguntas.

**Twitter/X:**
Sigue hashtags #webgl #threejs #gsap #creativecoding. Desarrolladores creativos comparten sus trabajos en progreso, tutoriales, tips.

## 7. El equilibrio: interactividad con propósito

### 7.1. Menos es más (a veces)

La tentación del desarrollador que aprende Three.js o GSAP es usarlo en todo. Resultado: sitios sobrecargados, lentos, mareantes.

**Pregúntate siempre:**
- ¿Esta animación **comunica** algo o solo es decoración?
- ¿Mejora la **comprensión** del contenido o distrae?
- ¿El usuario lo va a **valorar** o solo pensará "qué lento carga esto"?

**Buenos usos de interactividad:**
- Visualizar un producto 3D porque realmente ayuda a entenderlo (muebles en AR, dispositivos electrónicos)
- Animar datos para contar una historia (periodismo de datos)
- Guiar la atención mediante animaciones sutiles hacia CTAs importantes
- Crear momentos memorables en páginas de marca/producto premium

**Malos usos:**
- Animar cada elemento solo porque puedes
- Parallax extremo que desorienta
- Cursores personalizados en sitios corporativos serios
- Animaciones de carga que tardan más que el contenido en cargar

### 7.2. El portfolio paradox

Los portfolios creativos premiados en Awwwards están llenos de interactividad experimental extrema. **Pero esos sitios son su propio producto**: demuestran capacidades técnicas.

Un e-commerce, un blog, un sitio corporativo, una web gubernamental: no necesitan ni deben tener ese nivel de interactividad. Necesitan claridad, rapidez, accesibilidad.

**Usa la herramienta apropiada para el contexto.**



## **Conclusión **

Has comprendido qué son los elementos interactivos y por qué transforman la web de documentos a aplicaciones. Conoces los tipos comunes (menús, modales, formularios inteligentes, animaciones) y las herramientas profesionales (Three.js para 3D, GSAP para animaciones 2D avanzadas).

Sabes dónde buscar inspiración, dónde aprender, y lo más importante: **cuándo** usar cada herramienta y cuándo no. La interactividad bien ejecutada comunica, guía, deleita. La interactividad mal ejecutada distrae, ralentiza, frustra.

En la siguiente órbita veremos cómo garantizar que toda esta magia interactiva sea accesible para todas las personas, cumpliendo con estándares internacionales y mejores prácticas de inclusión.

