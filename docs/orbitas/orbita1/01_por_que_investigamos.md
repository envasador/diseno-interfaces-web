# Órbita 1 — Conocer a las personas

## 1. Por qué investigamos antes de diseñar

<div style="background:#1F0318; border:3px solid #1F0318; box-shadow:6px 6px 0 #E93456; padding:28px 36px; display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:24px; margin:32px 0;">
  <div>
    <p style="margin:0 0 8px 0; color:#FFB8DE; font-weight:700; text-transform:uppercase; letter-spacing:1px; font-size:0.85rem;">Diapositivas del apartado</p>
    <p style="margin:0; color:#ffffff; font-size:1.1rem; font-weight:600;">Por qué investigar antes de diseñar, las leyes de UX y el papel de la IA en la investigación.</p>
  </div>
  <a href="../slides/orbita1_01_por_que_investigamos.pdf" target="_blank" rel="noopener" style="background:#E93456 !important; color:#ffffff !important; border:3px solid #1F0318 !important; box-shadow:4px 4px 0 #1F0318 !important; padding:14px 28px; font-weight:700; text-transform:uppercase; letter-spacing:1px; text-decoration:none !important; white-space:nowrap; border-bottom:none !important;">Descargar presentación →</a>
</div>


Cuando empiezas un proyecto de diseño, la tentación es abrir Figma y ponerte a dibujar pantallas. Lo entiendo: tienes una idea, quieres ver cómo queda, y el diseño visual da sensación de avance. El problema es que si no sabes bien para quién estás diseñando ni qué necesita esa persona, estás tomando decisiones sin información suficiente. Y esas decisiones cuestan tiempo después, cuando hay que cambiarlas.

La investigación sirve para tener esa información antes de tomar las decisiones, no después.

### Tú no eres el usuario

Cuando llevas días o semanas trabajando en un producto, conoces cada detalle de cómo funciona. Sabes dónde está cada opción, qué hace cada botón, cómo fluye la navegación. Eso es útil para construirlo, pero te pone en una posición muy diferente a la de alguien que lo ve por primera vez.

Don Norman lo explica en *La psicología de los objetos cotidianos*: cada persona construye un modelo mental de cómo funciona algo, y ese modelo suele ser diferente al de quien lo diseñó. Cuando coinciden, la interfaz parece intuitiva. Cuando no coinciden, el usuario se pierde, se frustra y se va. La investigación te ayuda a entender ese modelo mental antes de diseñar, para que tus decisiones partan de ahí y no de tus propias suposiciones.

### Para quién diseñas

Diseñar para todo el mundo a la vez suele terminar en un producto que no funciona especialmente bien para nadie. Una interfaz pensada para un perfil genérico e indefinido acaba siendo demasiado vaga para responder bien a las necesidades reales de nadie en concreto.

La investigación te permite elegir y definir perfiles reales de personas: con sus contextos, sus limitaciones, sus objetivos concretos. Cuando tienes eso claro, cada decisión de diseño tiene un criterio: ¿esto funciona para esta persona, en este contexto? (RA6-a).

En esta órbita vas a construir entre dos y tres personas. Una de ellas debe tener algún tipo de diversidad funcional, ya sea visual, motora, cognitiva o auditiva. La razón es práctica: si desde el principio tienes presente a alguien que usa un lector de pantalla o que navega solo con teclado, las decisiones de accesibilidad que tomes en las órbitas siguientes saldrán del proceso de diseño de forma natural, no como una corrección de última hora.

### Las leyes de UX como punto de partida

Antes de que empieces a investigar, hay un conjunto de principios sobre comportamiento humano que los profesionales del diseño usan como referencia. No son reglas absolutas, pero ayudan a entender por qué ciertas decisiones de diseño funcionan mejor que otras.

**Ley de Hick.** Cuantas más opciones tiene una persona, más tarda en decidir. Un menú con doce opciones es más lento de procesar que uno con cuatro. Simplificar significa organizar el contenido para que el usuario llegue a lo que necesita sin tener que procesar todo lo demás.

**Ley de Fitts.** El tiempo que tardas en pulsar algo depende de lo grande que sea y de lo cerca que esté. En móvil, los elementos interactivos que más se usan tienen que ser lo suficientemente grandes y estar en zonas cómodas para el pulgar. Lo que cuesta alcanzar, se usa menos.

**Ley de Jakob.** Los usuarios pasan la mayor parte de su tiempo en otras aplicaciones, no en la tuya. Eso significa que ya tienen expectativas formadas sobre cómo funcionan las cosas: dónde suele estar el carrito, qué hace la lupa, cómo funciona un formulario. Cuando tu diseño respeta esas convenciones, el usuario no tiene que aprender nada nuevo para usarlo.

**Ley de Tesler.** Todo sistema tiene una complejidad mínima que no se puede eliminar. Si el diseñador no la gestiona, la asume el usuario. Organizar bien esa complejidad —por pasos, por niveles, por contexto— es parte del trabajo de diseño.

**Ley de Miller.** El cerebro humano maneja con comodidad entre cinco y nueve elementos a la vez. Si una pantalla tiene demasiadas cosas activas al mismo tiempo, el usuario se bloquea. La jerarquía visual, el espacio y la agrupación sirven precisamente para evitar esa sobrecarga.

Estas leyes no dictan cómo tiene que ser tu diseño, pero sí te dan un vocabulario para justificar tus decisiones. Cuando en la auditoría oral te pregunten por qué tomaste una decisión concreta, poder apoyarla en un principio de comportamiento humano es mucho más sólido que decir que "quedaba mejor así" (RA1-a, RA6-a).

[Laws of UX](https://lawsofux.com/es/)


### La IA en la investigación

Las herramientas de IA pueden ayudarte en la fase de investigación: organizar notas de entrevistas, generar preguntas para un guión, identificar patrones en respuestas de encuesta. Lo que no pueden hacer es investigar por ti: hablar con las personas, observar cómo usan los productos, detectar la diferencia entre lo que alguien dice que hace y lo que realmente hace.

Si usas IA en cualquier parte de esta fase, lo documentas en el `CHANGELOG.md`: qué le pediste, qué generó, qué mantuviste y qué cambiaste. Eso es lo que demuestra que las decisiones son tuyas.

### Qué sale de esta órbita

Al terminar la Órbita 1 tendrás cuatro cosas listas para usar en el resto del módulo: el brief de proyecto, las personas, los user flows y el sitemap. Cada decisión de tipografía, color, componente o estructura de navegación que tomes después debería poder justificarse señalando algo de lo que construiste aquí.
