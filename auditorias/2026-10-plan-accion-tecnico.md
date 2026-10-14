# Plan de acción técnico y de programación: perroasistencia.es

**Base:** `2026-10-informe-tecnico-programacion.md`
**Inicio previsto:** lunes 19 de octubre de 2026
**Responsable:** equipo de desarrollo y WordPress

**Criterio de prioridad**

| Prioridad | Qué tareas entran | Plazo |
|---|---|---|
| 🔴 P1 | Bloquean la medición o el rastreo, o tienen impacto inmediato | 0-15 días |
| 🟡 P2 | Mejoran la autoridad interna y la experiencia | 15-45 días |
| 🟢 P3 | Mantenimiento o dependen del equipo SEO | 45-90 días |

> Copia de seguridad completa (archivos + BD) antes de empezar y antes de cada tarea marcada con ⚠️.

---

## 🔴 Prioridad 1: inmediata (semanas 1-2)

| ID | Acción | Esfuerzo | Impacto | Depende de | Fecha límite | Criterio de «hecho» |
|---|---|---|---|---|---|---|
| T1.1 | Configurar Consent Mode v2: gtag siempre cargado con `default: denied` y `update` al aceptar el banner | Bajo (2 h) | Muy alto | — | 23 de octubre | Tag Assistant muestra el estado de consentimiento correcto antes y después de aceptar |
| T1.2 | Crear los eventos `click_tel`, `click_whatsapp` y `form_submit` y marcarlos como eventos clave en GA4 | Bajo (2 h) | Muy alto | T1.1 | 23 de octubre | Los 3 eventos aparecen en DebugView |
| T1.3 | Vincular GA4 con Search Console | Bajo (15 min) | Medio | — | 23 de octubre | El informe orgánico de GSC aparece en GA4 |
| T5.1 | Redirección 301 `/caniches-7-consejos-for-adiestrar-la-raza/` → `/caniches-7-consejos-para-adiestrar-la-raza/` y activar el monitor de 404 de Rank Math | Bajo (15 min) | Medio | — | 21 de octubre | `curl -I` devuelve 301 |
| T4.1 ⚠️ | Search-replace con regex de los 105 enlaces `/AAAA/MM/DD/slug/` → `/slug/` (primero `--dry-run`) | Bajo (1 h) | Alto | Copia de seguridad | 23 de octubre | Un nuevo rastreo da 0 enlaces internos 3xx (anexo CSV verificado) |
| T3.1 | `noindex, follow` en `/tag/`, `/author/`, `/category/sin-categoria/`, galerías y búsqueda interna, y sacarlos del sitemap | Bajo (1 h) | Alto | — | 28 de octubre | El sitemap no los incluye y el `<meta robots>` es correcto |
| T3.2 | Reasignar a una categoría real los posts que están en «Sin categoría» | Bajo (1 h) | Bajo | T3.1 | 28 de octubre | La categoría queda vacía |
| T2.1 ⚠️ | Activar la caché de página completa (LiteSpeed Cache o WP Rocket) + Redis Object Cache | Medio (4 h) | Muy alto | Copia de seguridad | 30 de octubre | Encabezado de caché HIT y TTFB < 0,8 s en la home |
| T2.2 | PHP 8.3+, OPcache y limpieza de `autoload` y transients en la BD | Medio (3 h) | Alto | T2.1 | 30 de octubre | Autoload < 800 KB |
| T2.3 | CDN (Cloudflare) con HTTP/3 y Brotli | Medio (2 h) | Alto | T2.1 | 30 de octubre | Estáticos servidos desde el CDN |
| T2.4 | Perfilar con Query Monitor `/tag/` (4 s) y `/pack-sesiones/` (5,9 s) y corregir el plugin o la consulta lenta | Medio (3 h) | Alto | T2.1 | 30 de octubre | `/pack-sesiones/` carga en < 2,5 s |
| T6.1 | Rank Math SEO local: `ProfessionalService` con la dirección completa de Ubrique, `geo`, horario y `areaServed` | Bajo (1 h) | Alto | **Dirección confirmada por el cliente** | 30 de octubre | Rich Results Test sin errores |
| T6.2 | Corregir `sameAs` de Twitter y añadir el resto de perfiles y la ficha de GBP | Bajo (15 min) | Medio | — | 30 de octubre | JSON-LD válido |
| T6.3 | Cambiar el schema de la home de `Article` a `WebPage` | Bajo (15 min) | Medio | — | 30 de octubre | Validator sin `Article` en la home |

**Hito P1 (30 de octubre):** medición operativa, TTFB < 0,8 s, índice limpio y 0 enlaces internos rotos o redirigidos.

---

## 🟡 Prioridad 2: corto plazo (semanas 3-6)

| ID | Acción | Esfuerzo | Impacto | Depende de | Fecha límite | Criterio de «hecho» |
|---|---|---|---|---|---|---|
| T6.4 | JSON-LD `Service` + `areaServed` en las 4 landings locales (plantilla en el informe) | Bajo (2 h) | Alto | T6.1 | 6 de noviembre | Validación sin errores en las 4 URLs |
| T7.1 | Nuevo menú: Inicio · Adiestramiento (Sevilla, Cádiz, Málaga, Ubrique) · Perros de asistencia · Precios · Blog · Contacto | Bajo (2 h) | Alto | Visto bueno de SEO | 6 de noviembre | El menú no enlaza ningún post |
| T7.2 | Pie: quitar los 4 posts al azar, galerías y categorías; dejar servicios, ciudades y legales | Bajo (1 h) | Medio | T7.1 | 6 de noviembre | ≤ 25 enlaces sitewide (hoy 48) |
| T8.1 | Añadir `%page%` a title y meta de los archivos paginados y corregir la plantilla rota «…tu perro, . ✅» | Bajo (1 h) | Medio | — | 6 de noviembre | 0 metas duplicadas en DinoRank |
| T8.2 | Comprobar que las 44 URLs `/AAAA/MM/DD/` sin title devuelven 301 y no están en el sitemap | Bajo (1 h) | Medio | T4.1 | 6 de noviembre | Las 44 dan 301 |
| T10.1 | Redirección 301 `/que-sintomas-provoca-el-sarro-en-perros/` → `/como-afecta-el-sarro-en-perro/` | Bajo (15 min) | Alto | El equipo SEO ha fusionado el contenido | 6 de noviembre | `curl -I` devuelve 301 |
| T9.1 | Convertir imágenes a WebP/AVIF, añadir `width`/`height`, `lazy` fuera de la primera pantalla y `fetchpriority="high"` en la imagen LCP | Medio (4 h) | Alto | T2.3 | 20 de noviembre | CLS < 0,1 en Lighthouse |
| T9.2 | Fachada lite-youtube en las URLs `*-video/` y las galerías | Medio (3 h) | Medio | — | 20 de noviembre | Ningún iframe de YouTube carga al inicio |
| T9.3 | Cargar Hustle y los scripts no usados solo donde hacen falta (Perfmatters o Asset CleanUp) | Medio (3 h) | Medio | — | 20 de noviembre | Lighthouse móvil ≥ 70 en la home y `/pack-sesiones/` |
| T1.4 | Revisar que la ratio de sesiones orgánicas en GA4 frente a clics en GSC sea ≥ 0,85 | Bajo (30 min) | Alto | T1.1 + 14 días | 13 de noviembre | Ratio ≥ 0,85 |

**Hito P2 (20 de noviembre):** schema completo, arquitectura de menú orientada a servicios y Lighthouse móvil ≥ 70.

---

## 🟢 Prioridad 3: medio plazo (semanas 7-12)

| ID | Acción | Esfuerzo | Impacto | Depende de | Fecha límite | Criterio de «hecho» |
|---|---|---|---|---|---|---|
| T10.2 | Redirecciones 301 de las entrevistas de radio en lotes de 10 (lista en `anexos/entrevistas-radio.txt`) | Bajo (30 min/lote) | Alto | Hoja de fusión de SEO | 15 de enero | Sin cadenas de redirecciones y URLs fuera del sitemap |
| T10.3 | Crear las URLs nuevas que defina SEO (a domicilio, ansiedad, conducta…) con su plantilla y schema | Medio | Alto | Contenidos de SEO | 15 de enero | Publicadas e indexadas |
| T11.1 | Desactivar `xmlrpc`, quitar `wp_generator`, RSD, oEmbed, REST link y feeds de taxonomías del `<head>` | Bajo (30 min) | Bajo | — | 27 de noviembre | No aparecen en el HTML |
| T11.2 | Encabezados de seguridad: HSTS, `nosniff`, `Referrer-Policy` y `Permissions-Policy` | Bajo (1 h) | Bajo | — | 27 de noviembre | securityheaders.com con nota ≥ B |
| T11.3 | `robots.txt`: añadir `Disallow: /?s=` y `/*?replytocom=` | Bajo (10 min) | Bajo | — | 27 de noviembre | robots.txt actualizado |
| T11.4 | Actualizar `llms.txt` con los servicios y las landings | Bajo (30 min) | Bajo | T7.1 | 27 de noviembre | Archivo revisado |
| T2.5 | Validar Core Web Vitals en GSC (datos de campo de 28 días) | Bajo | Alto | T2 y T9 | 15 de diciembre | LCP < 2,5 s, INP < 200 ms y CLS < 0,1 en móvil |

---

## Calendario visual

| Semana | Del | P1 | P2 | P3 |
|---|---|---|---|---|
| 1 | 19 de octubre | T1.1-1.3 · T5.1 · T4.1 | | |
| 2 | 26 de octubre | T3.1-3.2 · T2.1-2.4 · T6.1-6.3 | | |
| 3 | 2 de noviembre | | T6.4 · T7.1-7.2 · T8.1-8.2 · T10.1 | |
| 4-5 | 9 de noviembre | | T1.4 · T9.1-9.3 | |
| 6 | 23 de noviembre | | | T11.1-11.4 |
| 7-12 | diciembre-enero | | | T10.2-10.3 · T2.5 |

## Bloqueos que hay que resolver antes de empezar

1. **Cliente:** confirmar la dirección física de la sede (Ubrique), el horario y la URL de la ficha de Google Business Profile (para T6.1).
2. **Hosting:** acceso a cPanel/SSH, versión de PHP y tipo de servidor (LiteSpeed/Apache/Nginx) (para T2).
3. **Accesos:** usuario administrador de GA4 y GTM (para T1).
