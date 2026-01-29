# Órbita 6: Diseñar para conectar
## SEO - Optimización para motores de búsqueda

El diseño de interfaces no termina cuando la página se ve bien o funciona correctamente. Una interfaz invisible no puede cumplir su propósito. En esta órbita exploraremos cómo preparar tu aplicación web para que sea descubierta, rastreada e indexada por los motores de búsqueda, conectando tu trabajo con las personas que lo necesitan.

## 1. Entender el SEO: Haciendo visible lo invisible

Imagina que has diseñado la aplicación web más útil del mundo, con una interfaz impecable y una experiencia de usuario excepcional. Pero si Google no puede encontrarla, procesarla o entender su contenido, es como si no existiera. Aquí entra el SEO (Search Engine Optimization), que no es magia ni trucos oscuros, sino arquitectura de información pensada para dos públicos simultáneos: humanos y máquinas.

El SEO se articula en tres dimensiones complementarias:

- **SEO On-page**: Trabaja sobre el contenido y la estructura interna de tu sitio: el código HTML semántico, los metadatos que describen cada página, las URLs que comunican la jerarquía de contenido.
- **SEO Técnico**: Se ocupa de los aspectos infraestructurales: cómo se rastrea el sitio, su velocidad de carga, la arquitectura de información que permite a los bots navegar eficientemente.
- **SEO Off-page**: Construye la reputación y autoridad de tu sitio a través de enlaces externos, menciones y señales sociales.

Estas tres dimensiones no funcionan aisladas, se refuerzan mutuamente. Un sitio con HTML semántico perfecto pero que carga en 10 segundos perderá posiciones. Una página técnicamente impecable sin contenido relevante tampoco llegará lejos. Y un contenido extraordinario que nadie enlaza tendrá dificultades para ganar autoridad en su nicho.

## 2. SEO On-page con HTML: La arquitectura semántica

El HTML semántico no es solo buena práctica de desarrollo, es comunicación directa con los rastreadores de búsqueda. Cada etiqueta que eliges transmite significado sobre la estructura y relevancia de tu contenido.

### El poder de las etiquetas estructurales

Cuando usas `<header>`, `<main>`, `<article>`, `<section>` y `<footer>`, estás creando un mapa conceptual de tu página. Los motores de búsqueda entienden que el contenido dentro de `<main>` es central, que un `<article>` representa una unidad independiente de contenido, que una `<aside>` contiene información complementaria. Esta jerarquía semántica ayuda a los algoritmos a priorizar qué contenido es más relevante para indexar.

Considera este ejemplo de estructura semántica:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Aplicación web para gestionar tareas de manera eficiente, con sincronización en tiempo real y organización por proyectos">
  <title>TaskFlow - Gestor de Tareas Inteligente</title>
</head>
<body>
  <header>
    <h1>TaskFlow</h1>
    <nav>
      <ul>
        <li><a href="/">Inicio</a></li>
        <li><a href="/proyectos">Proyectos</a></li>
        <li><a href="/equipo">Equipo</a></li>
      </ul>
    </nav>
  </header>
  
  <main>
    <article>
      <h2>Organiza tu trabajo con claridad</h2>
      <p>TaskFlow te permite crear proyectos, asignar tareas y visualizar tu progreso en tiempo real. Prioriza lo importante, delega lo urgente y mantén tu equipo sincronizado.</p>
    </article>
    
    <section>
      <h3>Características principales</h3>
      <p>Sincronización automática entre dispositivos, gestión de dependencias entre tareas y reportes de productividad personalizados.</p>
    </section>
  </main>
  
  <footer>
    <p>&copy; 2025 TaskFlow - Todos los derechos reservados</p>
  </footer>
</body>
</html>
```

Observa cómo cada elemento comunica propósito. El `<h1>` marca el tema principal de la página, los `<h2>` y `<h3>` establecen la jerarquía de subsecciones, el `<nav>` identifica la navegación principal, el `<article>` contiene el contenido central autocontenido.

### Los metadatos que cuentan tu historia

El elemento `<meta name="description">` es tu oportunidad de vender tu página en los resultados de búsqueda. No es solo una descripción técnica, es el fragmento que aparecerá bajo el título en Google. Debe ser claro, específico y convincente, comunicando en 150-160 caracteres qué problema resuelves o qué valor aportas.

La etiqueta `<title>` es aún más crítica. Es el factor On-page más importante para el ranking. Debe ser única en cada página, incluir las palabras clave relevantes de forma natural y no superar los 60 caracteres para que no se trunque en los resultados.

El atributo `lang` en la etiqueta `<html>` parece trivial pero es fundamental. Indica a los buscadores en qué idioma está el contenido, permitiendo que aparezca en las búsquedas del idioma correcto y mejorando la accesibilidad para lectores de pantalla.

### URLs que comunican estructura

Una URL no es un identificador técnico arbitrario, es parte de la arquitectura de información. La diferencia entre `/productos?id=847` y `/productos/zapatillas-running-trail` es abismal para el SEO y para la experiencia de usuario.

Las URLs descriptivas comunican jerarquía, contexto y relevancia. Cuando ves `/blog/desarrollo-web/seo-para-react`, entiendes inmediatamente que estás en la sección de blog, dentro de la categoría desarrollo web, leyendo un artículo sobre SEO para React. Los motores de búsqueda también lo entienden y valoran esa claridad.

Mantén las URLs simples, usa guiones para separar palabras, evita parámetros de consulta innecesarios y asegúrate de que la estructura refleje la jerarquía real de tu contenido.

### Canonical tags: Evitando la duplicación

Cuando el mismo contenido es accesible desde múltiples URLs (por filtros, parámetros de seguimiento, variantes móviles), Google no sabe cuál debe indexar y puede dividir la autoridad entre todas las versiones. Los canonical tags resuelven esto indicando explícitamente cuál es la URL preferida:

```html
<link rel="canonical" href="https://miweb.com/productos/zapatillas-deportivas">
```

Esto es especialmente importante en aplicaciones con filtros dinámicos, paginación o múltiples rutas que llegan al mismo contenido.


## 3. SEO On-page con CSS: Rendimiento visual

El CSS no afecta directamente al contenido indexable, pero tiene un impacto crítico en la experiencia de usuario y, por extensión, en el SEO. Google considera las métricas de experiencia de usuario (Core Web Vitals) como factor de ranking, y el CSS mal optimizado puede arruinar tu puntuación.

### Minificación y carga estratégica

Reduce el tamaño de tus archivos CSS eliminando espacios, comentarios y código redundante. Herramientas como CSSNano o el minificador incluido en build tools modernos hacen este trabajo automáticamente. Un archivo CSS que pasa de 150KB a 45KB después de minificar carga tres veces más rápido, mejorando la métrica de First Contentful Paint.

Pero más allá de minificar, carga estratégicamente. Identifica el CSS crítico (los estilos necesarios para renderizar el contenido visible en el viewport inicial) e inclúyelo inline en el `<head>`. El resto del CSS puede cargarse de forma diferida sin bloquear el renderizado inicial.

### Responsive como imperativo

El diseño responsive no es opcional para el SEO. Desde 2015, Google usa mobile-first indexing: rastrea e indexa la versión móvil de tu sitio como la principal. Si tu interfaz no funciona bien en móvil, no funciona para Google.

Usa media queries, unidades relativas, y diseña pensando primero en pantallas pequeñas. Verifica que los elementos táctiles tengan al menos 48x48 píxeles de área interactiva, que el texto sea legible sin zoom (mínimo 16px) y que el contenido se reorganice fluidamente sin scroll horizontal.

### Fuentes web optimizadas

Las fuentes custom pueden ralentizar significativamente el renderizado inicial. La propiedad `font-display: swap` es tu aliada aquí:

```css
@font-face {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  src: url('roboto.woff2') format('woff2');
  font-display: swap;
}
```

Con `swap`, el navegador muestra inmediatamente el texto con una fuente del sistema mientras se descarga tu fuente custom, evitando el temido FOIT (Flash Of Invisible Text). El contenido es accesible de inmediato aunque la fuente tarde en cargar.

## 4. SEO On-page con JavaScript: El desafío del contenido dinámico

JavaScript abre posibilidades infinitas para interfaces ricas e interactivas, pero también complica el SEO. Los motores de búsqueda han mejorado enormemente su capacidad de ejecutar JavaScript, pero todavía existen limitaciones y costos computacionales que debes considerar.

### Client-side vs Server-side rendering

Cuando React renderiza en el cliente (CSR), el servidor envía un HTML casi vacío con un bundle de JavaScript. El navegador descarga el JS, lo ejecuta, y genera el DOM dinámicamente. Esto es eficiente para aplicaciones interactivas, pero problemático para el SEO porque el contenido no existe hasta que JavaScript se ejecuta.

Google puede ejecutar JavaScript, pero es lento, costoso y no siempre funciona perfectamente. Si tu contenido crítico solo existe después de ejecutar JS, estás complicando innecesariamente el rastreo.

El Server-side rendering (SSR) resuelve esto generando el HTML en el servidor antes de enviarlo al cliente. Frameworks como Next.js hacen esto trivial:

```jsx
import React from 'react';
import Head from 'next/head';

export default function Home() {
  return (
    <div>
      <Head>
        <title>TaskFlow - Gestor de Tareas Inteligente</title>
        <meta name="description" content="Organiza tu trabajo con claridad. Gestión de tareas con sincronización en tiempo real." />
      </Head>
      <main>
        <h1>Bienvenido a TaskFlow</h1>
        <p>Tu productividad comienza aquí. Crea proyectos, asigna tareas y colabora con tu equipo.</p>
      </main>
    </div>
  );
}
```

Cuando un rastreador visita esta página, recibe HTML completo inmediatamente. No necesita ejecutar JavaScript para ver el contenido. Cuando un usuario visita la misma página, recibe el mismo HTML y luego React se hidrata para añadir interactividad.

### Metadatos dinámicos con React Helmet

Si estás en una aplicación puramente client-side, React Helmet te permite modificar el `<head>` dinámicamente:

```jsx
import { Helmet } from 'react-helmet';

function ProductPage({ product }) {
  return (
    <div>
      <Helmet>
        <title>{product.name} - TaskFlow Store</title>
        <meta name="description" content={product.description} />
        <meta property="og:image" content={product.image} />
      </Helmet>
      <article>
        <h1>{product.name}</h1>
        <p>{product.description}</p>
      </article>
    </div>
  );
}
```

Cada página de producto puede tener su propio título y descripción únicos, mejorando la relevancia en búsquedas específicas.

### Contenido crítico sin JavaScript

Asegúrate de que tu contenido esencial sea accesible aunque JavaScript falle o se deshabilite. No estamos en 2005, pero la progressive enhancement sigue siendo relevante. El contenido textual principal, la navegación básica y la estructura deben existir en el HTML inicial.

## 5. SEO Técnico: La infraestructura invisible

El SEO técnico trabaja bajo la superficie, optimizando cómo los rastreadores descubren, navegan e indexan tu sitio. Es la fontanería del SEO, invisible pero esencial.

### robots.txt: Dirigiendo el tráfico de bots

El archivo `robots.txt` vive en la raíz de tu dominio (`https://tudominio.com/robots.txt`) y le dice a los rastreadores qué pueden y qué no pueden visitar:

```
User-agent: *
Disallow: /admin/
Disallow: /api/
Disallow: /usuarios/*/privado
Allow: /api/docs

Sitemap: https://miweb.com/sitemap.xml
```

Aquí estás diciendo: todos los rastreadores (`User-agent: *`) pueden visitar todo excepto el directorio admin, los endpoints de API (salvo la documentación pública) y las secciones privadas de usuarios. También indicas dónde está el sitemap para facilitar el rastreo.

No uses `robots.txt` como método de seguridad. No bloquear el acceso real, solo le pide educadamente a los rastreadores que no visiten ciertas rutas. Para contenido sensible, usa autenticación real.

### Sitemap XML: El mapa de tu territorio

Un sitemap es un índice completo de todas las URLs importantes de tu sitio. Es como entregarle a Google un mapa detallado en lugar de esperar que explore por su cuenta:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://miweb.com/</loc>
    <lastmod>2025-01-28</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://miweb.com/productos/zapatillas-trail</loc>
    <lastmod>2025-01-25</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://miweb.com/blog/guia-seo-2025</loc>
    <lastmod>2025-01-20</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.7</priority>
  </url>
</urlset>
```

Cada `<url>` contiene la ubicación de la página (`<loc>`), la última fecha de modificación (`<lastmod>`), una sugerencia de frecuencia de cambio (`<changefreq>`) y la prioridad relativa dentro de tu sitio (`<priority>`).

Para sitios grandes, los sitemaps se pueden dividir en múltiples archivos e incluso generar dinámicamente. En un proyecto Next.js, puedes generar el sitemap automáticamente en cada build consultando tu base de datos de contenido.

### Velocidad de carga: Cada milisegundo cuenta

Google incorpora las Core Web Vitals como factores de ranking. Estas métricas miden aspectos concretos de la experiencia de carga:

- **Largest Contentful Paint (LCP)**: Mide cuánto tarda en cargar el elemento visual más grande del viewport inicial. Debe ocurrir en menos de 2.5 segundos. Para optimizar LCP, prioriza la carga de recursos críticos, usa imágenes optimizadas con dimensiones correctas, implementa lazy loading para contenido fuera del viewport inicial.

- **First Input Delay (FID)**: Mide el tiempo desde que el usuario interactúa por primera vez hasta que el navegador puede responder. Debe ser inferior a 100ms. Para mejorarlo, reduce la ejecución de JavaScript durante la carga inicial, divide el código en chunks más pequeños, usa workers para tareas pesadas.

- **Cumulative Layout Shift (CLS)**: Mide la estabilidad visual durante la carga. Debe ser inferior a 0.1. Evítalo reservando espacio para imágenes y anuncios con atributos `width` y `height`, evitando insertar contenido dinámicamente sobre contenido existente, usando fuentes con `font-display: swap`.

Para mejorar todas estas métricas:

- **Compresión de imágenes**: Usa formatos modernos como WebP o AVIF que ofrecen mejor compresión que JPEG o PNG. Herramientas como Squoosh o servicios CDN automatizan esto. Una imagen de 2MB que se reduce a 200KB mejora drásticamente el LCP.

- **Compresión Gzip/Brotli**: Configura tu servidor para comprimir respuestas HTTP. Brotli ofrece aproximadamente 20% mejor compresión que Gzip. La mayoría de servidores modernos lo soportan:

```
# En Nginx
gzip on;
gzip_types text/plain text/css application/json application/javascript;
brotli on;
brotli_types text/plain text/css application/json application/javascript;
```

- **Minificación de assets**: Elimina espacios, comentarios y código innecesario de CSS, JavaScript y HTML. Las build tools modernas (Vite, Webpack, Parcel) lo hacen automáticamente en producción.

- **CDN y caching**: Sirve assets estáticos desde una CDN geográficamente cercana al usuario. Configura headers de cache agresivos para contenido que no cambia frecuentemente:

```
Cache-Control: public, max-age=31536000, immutable
```

## 6. SEO Off-page: Construyendo autoridad

El SEO Off-page construye la reputación de tu sitio fuera de tu dominio. Principalmente se trata de conseguir backlinks de calidad, enlaces desde otros sitios web hacia el tuyo.

### Por qué importan los backlinks

Google nació con PageRank, un algoritmo que interpretaba los enlaces como votos de confianza. Aunque el algoritmo ha evolucionado exponencialmente, los enlaces siguen siendo uno de los factores de ranking más importantes. Un enlace desde un sitio autoritativo en tu nicho es una señal potente de que tu contenido vale la pena.

Pero no todos los enlaces valen igual. Un enlace desde el New York Times tiene más peso que cien enlaces desde directorios spam. Google evalúa la autoridad de dominio del sitio que enlaza, la relevancia temática, el contexto del enlace y si es dofollow o nofollow.

### Estrategias para conseguir enlaces naturales

- **Crear contenido enlazable**: Guías definitivas, estudios originales con datos propios, herramientas gratuitas, recursos visuales como infografías. Contenido que otros sitios quieran referenciar porque añade valor a sus propios artículos. Por ejemplo, si creas una guía exhaustiva sobre "Arquitectura CSS escalable para aplicaciones React", blogs de desarrollo web pueden enlazarte cuando hablen de mejores prácticas de CSS o React.

- **Participación en comunidades**: Responde preguntas en Stack Overflow, Reddit, foros especializados. Cuando sea relevante y aporte valor, menciona tu contenido. No es spam si genuinamente resuelve el problema que plantean.

- **Colaboraciones y guest posting**: Escribe artículos para otros blogs de tu sector. Esto no solo te da un enlace, te expone a su audiencia. Busca sitios con audiencias complementarias, no competidores directos.

- **Menciones no enlazadas**: Busca menciones de tu marca o contenido que no incluyen enlace. Contacta cortésmente pidiendo que conviertan la mención en enlace. Herramientas como Google Alerts o Mention facilitan encontrar estas menciones.

- **Contenido en plataformas externas**: Publica en Medium, Dev.to, LinkedIn. Incluye enlaces estratégicos hacia contenido relevante de tu sitio. Estas plataformas tienen autoridad de dominio alta, y aunque los enlaces suelen ser nofollow, generan tráfico directo y visibilidad.

### Lo que debes evitar

No compres enlaces. Google penaliza esquemas de enlaces pagados. No participes en redes de intercambio de enlaces. No uses text spinning o contenido duplicado solo para generar enlaces. Estas prácticas pueden funcionar brevemente, pero las penalizaciones son severas y duraderas.

Construir autoridad Off-page es lento. Requiere crear contenido genuinamente valioso y construir relaciones reales en tu sector. No hay atajos sostenibles.

---

## Conclusión: SEO como parte del diseño

El SEO no es algo que añades al final del proceso de diseño. Es una consideración arquitectónica que influye en cómo estructuras la información, cómo diseñas las URLs, cómo optimizas el rendimiento, cómo redactas el contenido.

