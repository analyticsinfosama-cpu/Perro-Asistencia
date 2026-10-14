# Informe técnico y de programación: perroasistencia.es

**Destinatario:** equipo de desarrollo y WordPress
**Fecha:** octubre de 2026
**Stack detectado:** WordPress 7.1.2, Rank Math (SEO), Hustle (popups) y GA4 con gtag
**Fuentes:** auditoría on-page de DinoRank (601 URLs), GA4, GSC y rastreo propio de las 265 URLs del sitemap (`curl`)

> Este informe recoge solo lo que requiere tocar servidor, código, plugins o configuración. Lo editorial y on-page va en `2026-10-informe-seo-onpage.md`.

---

## Resumen de incidencias

| # | Incidencia | Gravedad | Esfuerzo |
|---|---|---|---|
| T1 | GA4 mide ~20 % de las sesiones y tiene 0 conversiones | 🔴 Crítica | Bajo |
| T2 | TTFB de 1,7–4,0 s sin caché de página | 🔴 Crítica | Medio |
| T3 | ~300 URLs de relleno indexables (tags, author, galerías, sin-categoría) | 🔴 Alta | Bajo |
| T4 | 105 enlaces internos hacia URLs con redirección 301 | 🔴 Alta | Bajo |
| T5 | URL 404 recibiendo tráfico | 🔴 Alta | Bajo |
| T6 | Schema global incorrecto (`Article` en home, `sameAs` roto, sin datos locales) | 🔴 Alta | Bajo |
| T7 | Menú y pie de página con enlaces sitewide sin valor | 🟡 Media | Bajo |
| T8 | 44 URLs sin `<title>` y metas duplicadas en paginación | 🟡 Media | Bajo |
| T9 | Peso de página y recursos (imágenes, popups, vídeos) | 🟡 Media | Medio |
| T10 | Redirecciones 301 de fusiones de contenido (las define SEO) | 🟢 Según calendario | Bajo |
| T11 | Seguridad y limpieza (`xmlrpc.php`, `wp-json`, feeds) | 🟢 Baja | Bajo |

---

## T1. Medición: GA4 y conversiones 🔴

**Evidencia**
- GA4 registró **151 sesiones** entre el 7 de julio y el 4 de octubre. GSC registró **~730 clics orgánicos** en el mismo periodo, así que GA4 captura alrededor del 20 % de las visitas.
- Solo se registran los eventos automáticos (`page_view`, `session_start`, `first_visit`, `user_engagement`).
- **0 eventos clave**, aunque la home tiene 12 enlaces `tel:`/WhatsApp y un formulario.

**Tareas**
1. **Revisar el banner de cookies y Consent Mode v2.**
   - El tag de GA4 debe cargarse siempre, con `default` en `denied`, y actualizarse con `update` al aceptar. Así Google modela las sesiones no consentidas.
   - Comprobar que el plugin de cookies no bloquea `gtag.js` por completo antes del consentimiento.
   ```html
   <script>
   window.dataLayer = window.dataLayer || [];
   function gtag(){dataLayer.push(arguments);}
   gtag('consent','default',{
     ad_storage:'denied', analytics_storage:'denied',
     ad_user_data:'denied', ad_personalization:'denied',
     wait_for_update: 500
   });
   </script>
   <!-- después: gtag.js + config G-XXXX -->
   <!-- al aceptar en el banner: gtag('consent','update',{analytics_storage:'granted', ...}) -->
   ```
2. **Crear eventos de conversión** (GTM recomendado, o JS propio):
   ```js
   document.addEventListener('click', function(e){
     const a = e.target.closest('a'); if(!a) return;
     const h = a.getAttribute('href') || '';
     if (h.startsWith('tel:'))      gtag('event','click_tel',      {link_url:h, page:location.pathname});
     if (/wa\.me|whatsapp/i.test(h)) gtag('event','click_whatsapp',{link_url:h, page:location.pathname});
   });
   // formulario: en el callback de envío correcto del plugin (CF7: 'wpcf7mailsent')
   document.addEventListener('wpcf7mailsent', () => gtag('event','form_submit',{page:location.pathname}));
   ```
3. En GA4 → Administrar → Eventos, marcar `click_tel`, `click_whatsapp` y `form_submit` como **eventos clave**.
4. Vincular GA4 con GSC (Administrar → Vinculaciones de productos).
5. **Validación:** usar DebugView, y a los 7 días comprobar que la ratio de sesiones orgánicas de GA4 frente a clics de GSC es **≥ 0,85**.

---

## T2. Rendimiento del servidor (TTFB) 🔴

**Evidencia (medida con `curl`)**

| URL | TTFB |
|---|---|
| / | 2,0 s |
| /adiestramiento-canino-sevilla/ | 1,9 s |
| /category/salud/ | 1,8 s |
| /tag/socializacion/ | **4,0 s** |

- Según DinoRank, la carga mediana es de 3,2 s. **338 de 601 URLs tardan más de 3 s y 70, más de 5 s.**
- Las peores son /collar-cabezal-para-perros-halti/ (8,5 s), /galeria-programas-de-radio/ (7,1 s), /collar-de-adiestramiento-de-puas/ (6,7 s) y **/pack-sesiones/ (5,9 s, página de conversión)**.
- No hay CrUX ni Lighthouse porque la cuota de la API de PSI estaba agotada. Hay que validarlo en GSC → Core Web Vitals.

**Tareas**
1. **Caché de página completa:** LiteSpeed Cache si el servidor es LiteSpeed; si no, WP Rocket o W3TC + Redis Object Cache. Comprobar el encabezado `x-cache: HIT` (o equivalente) en la segunda petición.
2. **PHP 8.3+, OPcache activo** y, si el hosting es compartido, valorar subir de plan o migrar a un VPS gestionado. **Objetivo: TTFB < 0,8 s.**
3. **CDN** (Cloudflare gratuito o el del hosting) para estáticos, con HTTP/3 y Brotli.
4. Revisar la **base de datos**: autoloaded options > 1 MB, transients caducados y revisiones (`wp_options`, `wp_postmeta`).
   ```sql
   SELECT SUM(LENGTH(option_value))/1024 AS kb FROM wp_options WHERE autoload IN ('yes','on');
   ```
5. Hacer un perfilado con Query Monitor en /tag/ y /pack-sesiones/ para localizar el plugin o la consulta lenta.

**Validación:** `curl -o /dev/null -s -w "%{time_starttransfer}\n" URL` debe dar < 0,8 s en la home, las landings y /pack-sesiones/.

---

## T3. Index bloat: URLs de relleno indexables 🔴

**Evidencia:** DinoRank rastrea 601 URLs, pero solo 255 son contenido real (posts + páginas). Hay 160 URLs de `/tag/`, 116 de `/category/`, 237 de paginación (se solapan) y archivos de autor. Todas tienen `index, follow`.

**Tareas (Rank Math → Títulos y Metas)**

| Tipo | Acción |
|---|---|
| Etiquetas (`/tag/`) | `noindex, follow` + quitarlas del sitemap |
| Archivo de autor (`/author/admin/`) | `noindex` (o desactivar el archivo de autor) |
| `/category/sin-categoria/` | `noindex`, y reasignar los posts a una categoría real |
| Galerías (`/galeria*`, `/nuestra-galeria/`) | `noindex, follow` si no tienen texto propio |
| Paginación `/page/N/` y `/salud/N/` | Mantener `index, follow` con canonical autorreferente (no apuntando a la página 1). Hoy /salud/2/ tiene canonical a /salud/: cambiarlo a autorreferente o dejarlo, pero de forma coherente en todo el sitio |
| Búsqueda interna `?s=` | `noindex` (comprobar) |
| URLs con parámetros (`?fbclid=` detectado en /suscribete/) | Canonical limpio (ya lo pone Rank Math; verificarlo) |

- Las categorías se quedan **indexables**, pero cada una necesita un texto introductorio propio (lo redacta SEO).
- **Validación:** GSC → Páginas → «Excluida por etiqueta noindex» debe crecer en ~300 en 4-6 semanas.

---

## T4. Enlaces internos que apuntan a redirecciones 301 🔴

**Evidencia:** hay **105 enlaces internos** en 64 URLs de destino que apuntan al formato antiguo `/AAAA/MM/DD/slug/`. Ese formato redirige con 301 a `/slug/`.
**Listado completo:** `auditorias/anexos/enlaces-internos-a-corregir.csv` (origen, enlace actual, enlace correcto).

**Tarea:** reemplazo masivo en `post_content`, primero en simulación (*dry run*):
```bash
# WP-CLI (recomendado). Hacer copia de seguridad antes.
wp search-replace 'https://perroasistencia\.es/20[0-9]{2}/[0-9]{2}/[0-9]{2}/' 'https://perroasistencia.es/' wp_posts \
  --include-columns=post_content --regex --dry-run
# si el recuento es ≈105, repetir sin --dry-run
```
Alternativa sin consola: el plugin Better Search Replace con expresión regular.

**Validación:** volver a rastrear (Screaming Frog o DinoRank) y comprobar que hay **0 enlaces internos con 3xx**.

---

## T5. URL 404 con tráfico 🔴

`/caniches-7-consejos-for-adiestrar-la-raza/` devuelve **404** y aparece en GA4 como landing. Es un slug mal traducido («for» en lugar de «para»).

```apache
# .htaccess (o Rank Math → Redirecciones)
Redirect 301 /caniches-7-consejos-for-adiestrar-la-raza/ https://perroasistencia.es/caniches-7-consejos-para-adiestrar-la-raza/
```

- Revisar si hay un plugin de traducción automática generando slugs.
- Activar en Rank Math el **Monitor 404** y revisarlo cada mes.

---

## T6. Datos estructurados (schema) 🔴

**Problemas detectados en el JSON-LD actual (Rank Math)**
- La home se marca como **`Article`** y debería ser `WebPage` (subtipo `AboutPage` o `ContactPage` según la página).
- `sameAs` de Twitter mal formado: `"https://twitter.com/https://twitter.com/AsistenciaPerro"`.
- `PostalAddress` contiene solo `addressCountry: "Spain"`. Faltan `streetAddress`, `addressLocality`, `postalCode` y `geo`.
- No hay `areaServed`, `priceRange`, `aggregateRating` ni enlace a la ficha de Google Business Profile.
- Las landings locales (Sevilla, Cádiz, Málaga, Ubrique) no tienen schema `Service`.
- El schema `FAQPage` es válido, pero Google ya no lo muestra como resultado enriquecido para este tipo de sitio. Se puede mantener.

**Tareas**
1. Rank Math → SEO local: tipo `ProfessionalService` (o `LocalBusiness`), con la dirección completa de la sede (Ubrique, a confirmar con el cliente), teléfono, horario y coordenadas.
2. Corregir `sameAs` (Facebook, Twitter, YouTube, Instagram y GBP).
3. Home: cambiar el tipo de schema de la página de «Artículo» a «Ninguno/WebPage».
4. Landings locales: añadir un bloque JSON-LD personalizado. Plantilla para Sevilla:
```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "@id": "https://perroasistencia.es/adiestramiento-canino-sevilla/#service",
  "name": "Adiestramiento canino en Sevilla",
  "serviceType": "Adiestramiento canino y modificación de conducta",
  "provider": { "@id": "https://perroasistencia.es/#organization" },
  "areaServed": { "@type": "City", "name": "Sevilla" },
  "url": "https://perroasistencia.es/adiestramiento-canino-sevilla/",
  "offers": { "@type": "Offer", "url": "https://perroasistencia.es/pack-sesiones/", "priceCurrency": "EUR" }
}
```
5. Organización: `ProfessionalService` con `areaServed` (Ubrique, provincia de Cádiz, Sevilla y Málaga), `priceRange` e `image`.

**Validación:** Rich Results Test y validator.schema.org en la home y las 4 landings, sin errores.

---

## T7. Menú y pie de página (PageRank interno) 🟡

**Evidencia:** hay **48 enlaces sitewide** en todas las páginas. Entre ellos:
- 9 categorías y 5 galerías.
- `xmlrpc.php` y `wp-json`.
- 4 posts sin intención comercial: /la-agorafobia-en-el-perro/, /el-sindrome-de-furia-en-el-perro/, /el-bano-del-perro-y-su-falta-de-autocontrol/ y /ansiedad-por-la-comida-y-torsion-de-estomago/.

**Tareas**
- **Menú principal:** Inicio · Adiestramiento (desplegable con Sevilla, Cádiz, Málaga, Ubrique y A domicilio, esta última cuando exista) · Perros de asistencia · Precios (/pack-sesiones/) · Blog · Contacto.
- **Pie:** quitar las 4 entradas al azar y las galerías. Dejar servicios, ciudades, contacto y los textos legales.
- Eliminar del HTML el enlace a `xmlrpc.php` (`remove_action('wp_head','rsd_link')`) y los enlaces `wp-json`/oEmbed del `<head>` (más abajo, en T11).

---

## T8. Titles vacíos y metas duplicadas 🟡

- **44 URLs sin `<title>`:** son las URLs antiguas `/AAAA/MM/DD/…` que DinoRank todavía rastrea. Confirmar que **todas** redirigen con 301 (la que se comprobó, `/2019/08/08/juguetes-para-perros/`, sí lo hace) y que no aparecen en ningún sitemap.
- **Metas duplicadas en paginación** (/blog/page/N/ y /salud/N/): en Rank Math, añadir la variable `%page%` a title y meta de los archivos («– Página 2»).
- Las plantillas globales de meta de archivos tienen un texto roto: `«…calidad de vida de tu perro, . ✅»`. Hay que corregir la plantilla de categorías y etiquetas.

---

## T9. Peso de página y recursos 🟡

- **Home:** 191 KB de HTML, 35 `<img>`, 2 sin `alt`. Perros incansables: 6 imágenes sin `alt`.
- **Tareas:**
  - Convertir las imágenes a WebP/AVIF.
  - Poner `loading="lazy"` en las imágenes que no están en la primera pantalla y `fetchpriority="high"` en la imagen LCP.
  - Añadir `width` y `height` a todas las imágenes para evitar CLS.
  - Cargar los vídeos de YouTube con una fachada (lite-youtube) en las URLs `*-video/` y en las galerías.
  - Cargar Hustle (popup) solo en las páginas donde se usa, o diferirlo.
  - Desactivar los scripts que no se usan por página (Perfmatters o Asset CleanUp).
- **Validación:** Lighthouse móvil ≥ 70 en la home y /pack-sesiones/. LCP < 2,5 s, INP < 200 ms y CLS < 0,1 en GSC.

---

## T10. Redirecciones por consolidación de contenido 🟢

El informe on-page define las fusiones. Programación solo tiene que aplicar los 301 cuando SEO lo indique:

| Origen | Destino | Cuándo |
|---|---|---|
| /que-sintomas-provoca-el-sarro-en-perros/ | /como-afecta-el-sarro-en-perro/ | Semana 2 |
| Entrevistas de radio fusionadas (58 URLs; listado en `anexos/entrevistas-radio.txt`) | Post del mismo tema | Por lotes, según la hoja de SEO |

**Reglas:**
- Usar 301 de una sola redirección, sin cadenas.
- Actualizar los enlaces internos al destino final.
- Quitar las URLs redirigidas del sitemap.

---

## T11. Seguridad y limpieza 🟢

```php
// functions.php (tema hijo) o plugin de utilidades
add_filter('xmlrpc_enabled', '__return_false');
remove_action('wp_head', 'rsd_link');
remove_action('wp_head', 'wlwmanifest_link');
remove_action('wp_head', 'wp_generator');            // oculta "WordPress 7.1.2"
remove_action('wp_head', 'rest_output_link_wp_head');
remove_action('wp_head', 'wp_oembed_add_discovery_links');
remove_action('wp_head', 'feed_links_extra', 3);     // feeds de categorías y etiquetas
```

- Encabezados de seguridad: `Strict-Transport-Security`, `X-Content-Type-Options: nosniff`, `Referrer-Policy: strict-origin-when-cross-origin` y `Permissions-Policy`.
- `robots.txt` es correcto. Añadir solo `Disallow: /?s=` y `Disallow: /*?replytocom=`.
- `llms.txt` existe (200). Revisar que liste los servicios y las landings principales.

---

## Calendario propuesto

| Semana | Tareas |
|---|---|
| 1 | T1 (GA4 + conversiones), T5 (404), T4 (search-replace), T11 |
| 2 | T2 (caché + CDN + PHP), T3 (noindex), T6 (schema) |
| 3 | T7 (menú y pie), T8 (plantillas meta), T10 (redirecciones de sarro) |
| 4-6 | T9 (imágenes, vídeos, scripts), redirecciones por lotes de las entrevistas de radio |

## Checklist de validación final

- [ ] GA4: ratio de sesiones orgánicas frente a clics de GSC ≥ 0,85 y 3 eventos clave registrando datos
- [ ] TTFB < 0,8 s en home, landings y /pack-sesiones/
- [ ] 0 enlaces internos con 3xx o 4xx
- [ ] Tags, author y galerías con `noindex` y fuera del sitemap
- [ ] Schema sin errores en home y landings, y `sameAs` correcto
- [ ] Core Web Vitals en verde en GSC (móvil) a los 28 días
