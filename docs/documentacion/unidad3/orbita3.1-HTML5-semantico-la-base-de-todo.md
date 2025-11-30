## 1. HTML5 semántico: La base de todo

### ¿Por qué importa la semántica?

Cuando escribes HTML, no solo estás diciéndole al navegador "pon esto en pantalla". Estás comunicando **significado**: qué es cada cosa, cómo se relaciona con lo demás, y cómo debe interpretarse. Esto es crucial para:

- **Accesibilidad**: Los lectores de pantalla navegan por la estructura semántica
- **SEO**: Los buscadores entienden mejor el contenido estructurado
- **Mantenibilidad**: Otro desarrollador (o tú mismo en 6 meses) entiende qué hace cada parte
- **CSS más limpio**: Puedes seleccionar elementos por su significado, no solo por clases arbitrarias

### Elementos estructurales modernos

HTML5 nos dio elementos que describen la función de cada parte de la página:

```html
<header>
  <nav>
    <!-- Navegación principal -->
  </nav>
</header>

<main>
  <section>
    <h1>Título de la sección</h1>
    <p>Contenido de la sección...</p>
  </section>
  
  <aside>
    <!-- Información complementaria -->
  </aside>
</main>

<footer>
  <!-- Pie de página -->
</footer>
```

**`<article>`** → Contenido independiente y reutilizable (blog post, tarjeta de producto):
```html
<article>
  <h2>Cómo aprender CSS</h2>
  <p>Contenido del post...</p>
</article>
```

**`<section>`** → Agrupación temática que contiene varios elementos:
```html
<section>
  <h2>Productos destacados</h2>
  
  <article>
    <h3>Producto A</h3>
    <p>Descripción...</p>
  </article>
  
  <article>
    <h3>Producto B</h3>
    <p>Descripción...</p>
  </article>
</section>
```

**Regla práctica**: Si estás tentado a escribir `<div class="header">`, probablemente existe un elemento semántico más apropiado.

### Patrones comunes que debes dominar

**Listas de navegación:**
```html
<nav aria-label="Navegación principal">
  <ul>
    <li><a href="/">Inicio</a></li>
    <li><a href="/productos">Productos</a></li>
    <li><a href="/contacto">Contacto</a></li>
  </ul>
</nav>
```

**Formularios accesibles:**
```html
<form>
  <fieldset>
    <legend>Datos de contacto</legend>
    
    <label>
      Correo electrónico
      <input 
        type="email" 
        name="email"
        required
        aria-describedby="email-hint"
      >
      <small id="email-hint">Nunca compartiremos tu email</small>
    </label>
    
    <label>
      Teléfono
      <input type="tel" name="phone">
    </label>
  </fieldset>
</form>
```

**Contenido multimedia con fallbacks:**
```html
<picture>
  <source srcset="imagen.webp" type="image/webp">
  <source srcset="imagen.jpg" type="image/jpeg">
  <img src="imagen.jpg" alt="Descripción significativa" loading="lazy">
</picture>
```

### Lo que NO debes hacer

❌ Usar `<div>` y `<span>` para todo  
❌ Escribir HTML que solo tenga sentido visualmente  
❌ Omitir atributos `alt`, `aria-label`, o roles ARIA cuando son necesarios  
❌ Usar elementos por su apariencia predeterminada (`<h1>` porque es grande)

