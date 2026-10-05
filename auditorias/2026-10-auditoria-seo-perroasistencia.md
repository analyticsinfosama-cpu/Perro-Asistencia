# Auditoría SEO integral: perroasistencia.es

**Fecha:** 5 de octubre de 2026
**Fuentes:** Google Search Console y GA4 (vía DinoRank), módulos de DinoRank (visibilidad, tracking de 44 keywords, canibalizaciones, auditoría on-page de 601 URLs, enlaces externos y content gap) y rastreo propio de las 265 URLs del sitemap.
**Periodo principal:** del 7 de julio al 4 de octubre de 2026. La serie diaria de GSC cubre desde abril de 2026 y la de visibilidad de DinoRank, desde agosto de 2023.

> **Límites de los datos.** El mapa de enlazado interno de DinoRank está vacío, así que el grafo de enlaces se ha reconstruido con un rastreo propio. La API de PageSpeed agotó su cuota, por lo que no hay datos de campo de Core Web Vitals (CrUX): el rendimiento se ha medido con el TTFB real y los tiempos de carga que registra DinoRank. El proyecto no tiene prompts de LLM trackeados.

---

## 1. Resumen ejecutivo

### Diagnóstico general: salud SEO **baja-media (aproximadamente 42/100)**

| Indicador | Valor | Lectura |
|---|---|---|
| Clics GSC (julio, agosto y septiembre) | 214 / 261 / 256 | Estancados. En abril fueron **335**: **-24 %** |
| Impresiones GSC al mes | 31.000–36.000 | Visibilidad estable, pero no convierte en clics |
| CTR medio | **0,69–0,77 %** | Muy bajo para una posición media de ~9 |
| Posición media | 7,1 en abril → **8,9–10,3** desde finales de abril | Empeora a partir del 20 de abril de 2026 |
| Keywords en top 10 (DinoRank) | 66 en mayo de 2025 → **36** hoy | -45 % |
| Keywords en páginas 2-5 | ~260 en julio de 2025 → **~17** | **El long tail se perdió en octubre y noviembre de 2025** |
| Sesiones GA4 (90 días) | **151** frente a ~730 clics en GSC | GA4 registra solo el ~20 % del tráfico real |
| Conversiones GA4 | **0** (no hay ningún evento clave configurado) | No se puede medir el negocio |
| Dominios de referencia | **5** (7 enlaces), LBRank 1 | Autoridad casi nula |
| TTFB | **1,7–4,0 s** | Crítico: 338 de 601 URLs tardan más de 3 s y 70, más de 5 s |

### Principales cuellos de botella

1. **Medición rota.** GA4 pierde alrededor del 80 % de las sesiones (consentimiento de cookies o etiqueta) y no hay conversiones definidas, ni llamadas ni WhatsApp ni formulario. No se puede optimizar lo que no se mide.
2. **Pérdida del long tail en octubre y noviembre de 2025.** Los ~400 posts informativos dejaron de rankear en páginas 2-5. El patrón encaja con una devaluación por contenido poco útil o duplicado: 59 «entrevistas de radio» que repiten temas de posts, posts antiguos sin enlazar y un índice inflado con etiquetas, categorías y paginación.
3. **CTR muy bajo con buena posición.** Hay páginas en posiciones 1-5 con CTR inferior al 1 %. Los titles usan el patrón «【 】▷ lll➤ ✅», que Google suele reescribir y que resta confianza.
4. **Autoridad insuficiente para los términos principales.** «adiestrador de perros» (2.900–3.600 búsquedas) está en la posición 16-28. La competencia directa (Educan, Noblecan) tiene un perfil de enlaces muy superior.
5. **Arquitectura y enlazado débiles.** El 43 % de los posts no recibe ningún enlace editorial. Los activos que rankean (perro lazarillo, border collie, collar estrangulador) están **huérfanos**, y hay 105 enlaces internos que apuntan a URLs antiguas con 301.
6. **Servidor lento.** El TTFB supera los 2 s incluso en la home: no hay caché de página efectiva.

---

## 2. Análisis por áreas clave

### 2.1 Rendimiento y oportunidades en GSC (*low-hanging fruit*)

**A. Posición top 5 con CTR muy bajo: reescribir title y meta description**

| URL | Query principal | Impr. | Pos. | CTR |
|---|---|---|---|---|
| /friend-el-perro-guardian-agresivo/ | perro guardián / el perro guardián | 606 | 1,9–4,1 | 0,5 % |
| /el-collar-estrangulador/ | collar estrangulador perro (+ variantes) | 500 | 3,0–4,8 | 0,4 % |
| /el-instinto-depredador-del-perro/ | instinto depredador | 185 | 4,8 | 0 % |
| /collar-educativo-de-impulsos-estaticos/ | collar de impulsos perro | 349 | 5,1–6,5 | 0,3 % |
| /perros-incansables/ | perro real / imágenes de perros reales | 1.278 | 1,2 | 0,2 % |

> El caso de /perros-incansables/ es un *mismatch* de intención: quien busca «perros reales» quiere imágenes. Además, title y H1 tienen la errata **«Icansables»**. Conviene corregirla y aprovechar las imágenes con buen ALT, pero el tráfico seguirá siendo de bajo valor.

**B. Posiciones 6-20 con muchas impresiones: optimización on-page y enlazado**

| URL | Queries | Impr. | Pos. | Clics |
|---|---|---|---|---|
| / (home) | adiestrador, adiestrador de perros, adiestramiento canino, educador de perros | 19.558 | 9–15 | 24 |
| /perro-lazarillo-asistencia-a-la-discapacidad/ | perro lazarillo (590/mes), perros lazarillos, lazarillo perro | 1.185 | 11–12 | **0** |
| /como-afecta-el-sarro-en-perro/ | sarro en perro (590/mes) | 952 | 20–24 | 0 |
| /adiestramiento-border-collie-conduta-obsesiva/ | adiestramiento border collie (170), ejercicios border collie | 604 | 12–17 | 2 |
| /los-instintos-desarrollado-en-el-perro/ | instinto de presa en perros | 184 | 11,5 | 0 |
| /prevencion-miedos-doberman-cachorro/ | — | 178 | 10,2 | 1 |
| /adiestramiento-canino-sevilla/ | adiestrador de perros sevilla (260–320/mes) | 1.447 | 11–16 | 7 |
| /adiestramiento-canino-malaga/ | adiestramiento canino málaga (140) | 158 | 16–33 | 1 |

**C. «adiestrador» (7.254 impresiones, posición 9,1, CTR 0,2 %).** Es una consulta genérica con intención local, donde el *local pack* se lleva el clic. La palanca es la ficha de Google Business Profile y las landings locales, no la home.

### 2.2 Palabras clave y canibalizaciones (DinoRank + GSC)

DinoRank detecta **12 clústeres canibalizados**. Se agrupan así:

| Tipo | Keywords | URLs en conflicto | Diagnóstico | Acción |
|---|---|---|---|---|
| **Home frente a landings locales** | adiestrador de perros, adiestramiento canino, entrenador canino | / (11–20) · /sevilla/ (4–8) · /cadiz/ (4,7) | En parte es geolocalización legítima: en móvil, desde Sevilla o Cádiz, Google muestra la landing local. Aun así, la home no tiene un foco claro | Home = marca + servicio general + «a domicilio»; ciudades = solo la keyword local con su modificador. Enlace con anchor «adiestrador de perros en Sevilla» desde la home |
| **Home frente a página de servicio** | perros de asistencia (390–590/mes) | / (21,7) frente a /perros-de-asistencia/ (41,8) | La home le quita relevancia a la página dedicada | Reforzar /perros-de-asistencia/ (contenido, FAQ, enlaces internos) y quitar el foco de la home |
| **Home frente a /adiestramiento-social/** | adiestramiento respetuoso perros, adiestramiento canino respetuoso | 33 frente a 33,25 | Las dos se quedan en la página 3-4 | Definir /adiestramiento-social/ como landing de «adiestramiento canino respetuoso / positivo» |
| **A domicilio** | adiestramiento de perros a domicilio, clases particulares a domicilio | / (42–58) frente a /sevilla/ (71–85) | No existe una landing «a domicilio» (los competidores la tienen: Noblecan en posición 1) | **Crear** /adiestramiento-canino-a-domicilio/ |
| **Blog frente a blog** | consejos para controlar la ansiedad de tu perro | /ansiedad-en-perros-por-separacion/ (13) frente a /ansiedad-por-la-comida…/ (44,8) | Hay otros 3 posts de ansiedad más (coche, miedo-ansiedad-fobia, la-ansiedad-en-el-perro) | Crear un pilar «ansiedad en perros» y enlazar las variantes hacia él |
| **Blog frente a blog** | sarro en perros | /como-afecta-el-sarro-en-perro/ frente a /que-sintomas-provoca-el-sarro-en-perros/ | Dos posts sobre la misma intención | **Fusionar** con un 301 hacia /como-afecta-el-sarro-en-perro/ |
| **Cádiz frente a home** | curso de adiestramiento canino en cádiz | /cadiz/ (5,75) frente a / (9,3) | Leve | Enlace interno home → Cádiz |

**Canibalización estructural no detectada por la herramienta:** 59 URLs de «entrevista de radio» duplican temas de posts escritos. Algunos ejemplos: agorafobia (post + entrevista), síndrome de furia (post + entrevista), ansiedad en el coche, conducta de alzada y frotamientos (×3), la nariz del perro (×2), la llamada (×3) y el perro excitable (×3). Es la causa más probable de la caída del long tail.

**Keywords perdidas (histórico de DinoRank):** «adiestradores de perros» (3.600/mes) estaba en la posición 3 con 93 visitas estimadas y ya no aparece en el top. «educador de perros» bajó de 9 a fuera del top 10, «educador canino» de 15 a 17+, «perros lazarillo» de 10 a fuera del top 100 en el tracking y «de perro a perro» de 3 a fuera.

### 2.3 Enlazado interno y arquitectura (rastreo propio de 265 URLs)

| Métrica | Valor |
|---|---|
| URLs de contenido (posts + páginas) | 255 |
| URLs que rastrea DinoRank | 601 → **~57 % es relleno indexable**: 160 etiquetas, 116 URLs de categoría y 237 de paginación (los grupos se solapan) |
| Posts sin ningún enlace editorial entrante | **109 / 255 (43 %)** |
| URLs totalmente huérfanas (ni editorial ni menú) | **86** |
| Enlaces internos hacia URLs antiguas /AAAA/MM/DD/ (301) | **105 enlaces / 64 URLs** |
| Enlaces sitewide (menú y pie) | 48, de los cuales 9 son categorías, 5 galerías, `xmlrpc.php`, `wp-json` y 4 posts al azar (agorafobia, síndrome de furia, baño, ansiedad por la comida) |

**Activos huérfanos que hoy generan impresiones:** /perro-lazarillo-…/ (1.185 impresiones), /adiestramiento-border-collie…/ (604), /el-collar-estrangulador/ (500), /el-instinto-depredador-del-perro/, /ansiedad-en-perros-por-separacion/ y /la-oruga-procesionaria…/.

**Distribución del PageRank interno:** la home acumula 61 enlaces editoriales y las landings locales y de servicio reciben solo el enlace del menú (2-5 editoriales cada una). El flujo de autoridad se pierde en categorías, etiquetas, galerías y 4 posts de menú sin valor comercial.

**Arquitectura propuesta (hub & spoke):**
- **Servicios:** Adiestramiento canino (home) → Sevilla · Cádiz · Málaga · Ubrique · A domicilio (nueva) · Precios/Packs · Perros de asistencia → (discapacidad visual, movilidad reducida, lazarillo).
- **Pilares del blog:** Problemas de conducta (agresividad, ansiedad, miedos, excitabilidad) · Cachorros · Razas (border collie, caniche, rottweiler, doberman, american stafford) · Material (collares, arnés, correas, bozal) · Salud.
- Cada post enlaza a su pilar y a 1 servicio, con un CTA de «¿Tu perro tiene este problema? Consulta con nuestro adiestrador».

### 2.4 On-page, técnico y datos estructurados

- **Titles y metas:** patrón «【 】▷» y metas que empiezan por «lll➤ … ✅». Hay 2 grupos de titles y H1 duplicados y 10 metas duplicadas (paginaciones de /salud/ y /blog/). 44 URLs no tienen title (URLs antiguas con fecha).
- **Indexación:** las etiquetas (/tag/) y /category/sin-categoria/ están en `index, follow` (Rank Math). /salud/2/ tiene canonical a /salud/: es correcto, pero esas URLs siguen apareciendo en el rastreo.
- **Schema:**
  - La home se marca como `Article`; debería ser `WebPage` más `LocalBusiness` o `ProfessionalService`.
  - La organización no incluye `addressLocality`, `geo`, `areaServed` ni `aggregateRating`.
  - El `sameAs` de Twitter está mal formado (`https://twitter.com/https://twitter.com/AsistenciaPerro`).
  - Las landings locales no llevan schema local.
  - `FAQPage` no genera rich results para este tipo de sitio desde 2023. Se puede mantener, pero no aporta a la SERP.
- **E-E-A-T:** el autor es «admin». No hay biografía del adiestrador, titulaciones ni años de experiencia en los posts. Es un punto crítico en un sector YMYL ligero (salud y comportamiento animal).
- **Landings locales:** similitud de texto del 25–46 % entre ellas, aceptable. Sin embargo, no tienen dirección, mapa, zona de servicio, testimonios locales ni fotos locales. Ubrique, que parece la sede, **no rankea** para «adiestramiento canino ubrique».
- **URLs con errores tipográficos** que se mantienen: `conduta-obsesiva`, `american-stanfford`, `testimomio`. No conviene cambiarlas (el riesgo supera al beneficio) salvo que se haga junto a otra migración.

### 2.5 Rendimiento, Core Web Vitals y UX

- **TTFB medido:** home 2,0 s; Sevilla 1,9 s; /tag/ 4,0 s. El objetivo es < 0,8 s.
- **DinoRank:** tiempo de carga mediano de 3,2 s; 338 URLs > 3 s y 70 > 5 s. Las peores son /collar-cabezal-para-perros-halti/ (8,5 s), /galeria-programas-de-radio/ (7,1 s) y /pack-sesiones/ (5,9 s, **página de conversión**).
- **Peso HTML de la home:** 191 KB, con 35 imágenes. Se cargan los plugins Hustle (popup) y varios embeds de vídeo.
- **CrUX/INP:** no disponible (cuota de PSI). Hay que validarlo en GSC → Experiencia → Core Web Vitals.

### 2.6 Comportamiento y conversión (GA4)

- **151 sesiones en 90 días** frente a ~730 clics orgánicos: es un problema de consentimiento (Consent Mode v2 sin modelado) o de etiqueta. Hay que revisar el banner y la integración de gtag.
- **Eventos registrados:** solo los automáticos (`page_view`, `session_start`, `first_visit`, `user_engagement`). **No hay ningún evento clave** de llamada (`tel:`), WhatsApp o envío de formulario, aunque la home tiene 12 enlaces de teléfono/WhatsApp y un formulario.
- **Landings orgánicas principales (GA4):** caniches (22), ansiedad por la comida (21), home (20), Sevilla (10), Ubrique (10), Cádiz (8). **El 55 % del tráfico entra por posts informativos sin un CTA de servicio visible**.
- /contacto/ y /pack-sesiones/ reciben 1 y 4 sesiones respectivamente: el embudo blog → servicio no funciona.
- GA4 registra una URL con un 404 real: `/caniches-7-consejos-for-adiestrar-la-raza/` (slug mal traducido, probablemente por un plugin o un enlace externo). Conviene redirigirla con un 301.

### 2.7 Autoridad y competencia (DinoRank)

| Dominio | Keywords | Tráfico est./mes |
|---|---|---|
| noblecan.com | 101 | 1.600 |
| adiestramientoeducan.com | 101 | 847 |
| **perroasistencia.es** | **53** | **328** |
| evolucank9.es (Sevilla) | 23 | 141, pero en el **top 1-3 en las 8 variantes de «adiestrador… sevilla»** |

**Gaps relevantes:** adiestrador canino a domicilio, adiestramiento canino a domicilio, psicólogo/etólogo canino, reactividad canina, modificación de conducta (Sevilla), curso de adiestramiento canino online, olores que odian los perros (390), precios de adiestramiento canino (170–590, hoy en la posición 49 con /pack-sesiones/) y residencia o guardería canina (existe /estancia-para-perros/, pero no rankea).

---

## 3. Plan de acción priorizado (impacto / esfuerzo)

### 🔴 Prioridad alta: acciones inmediatas (0-30 días)

| # | Acción concreta | Fuente | Impacto esperado | Esfuerzo |
|---|---|---|---|---|
| 1 | **Arreglar la medición de GA4:** revisar Consent Mode v2 y el banner, verificar que gtag se dispara antes del consentimiento en modo «denied» con modelado, y crear eventos clave `click_tel`, `click_whatsapp` y `form_submit` (GTM o gtag) marcados como conversión | Analytics | Pasar de ver el 20 % del tráfico a ~90 % y medir los leads. Requisito para todo lo demás | Bajo |
| 2 | **Activar caché de página y bajar el TTFB por debajo de 0,8 s** (LiteSpeed Cache/WP Rocket + CDN; revisar el plan de hosting y PHP 8.3). Prioridad: /pack-sesiones/, home y landings locales | DinoRank | Mejor rastreo, CWV y conversión. Afecta a las 601 URLs | Medio |
| 3 | **Reescribir title y meta** de las 5 URLs en top 5 con CTR < 1 % (perro guardián, collar estrangulador, instinto depredador, collar de impulsos y perros incansables, corrigiendo «Icansables»). Quitar «【 】▷ lll➤ ✅» y usar un beneficio claro con la keyword al inicio | GSC | Pasar del 0,3 % al 3-5 % de CTR: **+60-100 clics al mes** | Bajo |
| 4 | **Poner `noindex, follow` en /tag/, /category/sin-categoria/, /author/ y galerías**, y quitarlos del sitemap | DinoRank | -300 URLs de relleno en el índice; el presupuesto de rastreo se concentra en el contenido | Bajo |
| 5 | **Actualizar los 105 enlaces internos que apuntan a URLs /AAAA/MM/DD/** para que vayan a la URL final (Better Search Replace), y redirigir con 301 el 404 `…-for-adiestrar-la-raza/` | Rastreo + GA4 | Se recupera el PageRank que pierden las cadenas 301 | Bajo |
| 6 | **Fusionar los posts de sarro** (301 de /que-sintomas-provoca-el-sarro-en-perros/ → /como-afecta-el-sarro-en-perro/) y ampliar la URL ganadora | DinoRank canibalizaciones + GSC | «sarro en perro» (590/mes): de la posición 20-24 al top 10 | Bajo |
| 7 | **Corregir el schema global** (Rank Math): home como `WebPage`, `LocalBusiness` con dirección de Ubrique, `geo`, `areaServed` (Cádiz, Sevilla, Málaga), `sameAs` de Twitter arreglado y enlace a la ficha de GBP | Auditoría | Mejor entidad local y elegibilidad en el *local pack* y la IA | Bajo |
| 8 | **Enlazar los activos huérfanos** que ya tienen impresiones (lazarillo, border collie, collar estrangulador, instinto depredador, ansiedad por separación) desde 3-5 posts relacionados cada uno y desde /perros-de-asistencia/ | Rastreo + GSC | Lazarillo (1.185 impresiones, posición 11, 0 clics) y border collie (posición 12-17) entrarían en el top 10 | Bajo |

### 🟡 Prioridad media: optimización a medio plazo (1-3 meses)

| # | Acción concreta | Fuente | Impacto esperado | Esfuerzo |
|---|---|---|---|---|
| 9 | **Reasignar la intención de la home** frente a las landings: home = «adiestrador de perros» genérico + marca; landings locales con un enlace contextual desde la home y desde 10+ posts con anchor local | DinoRank canibalizaciones | Resolver 5 clústeres canibalizados. Sevilla (posición 11-16) → top 5 | Medio |
| 10 | **Reforzar /perros-de-asistencia/** como hub (tipos, proceso, legislación andaluza, precio, FAQ) y enlazar a visual, movilidad y lazarillo. Quitar «perros de asistencia» del foco de la home | DinoRank + GSC | «perros de asistencia» (390–590/mes): de la posición 27-29 a la 10-15 | Medio |
| 11 | **Optimizar on-page las URLs en posiciones 6-20** (lazarillo, border collie, instintos, doberman, Málaga, Sevilla): H2 según las PAA, TF-IDF de DinoRank, FAQ visible e imágenes con ALT | GSC + DinoRank TF-IDF | +5-8 keywords en el top 10 | Medio |
| 12 | **Hacer local de verdad las landings locales:** dirección o zona de servicio, mapa, testimonios con nombre de la ciudad, fotos de sesiones reales, precios orientativos y schema `Service` + `areaServed`. Rehacer Ubrique (sede): hoy no rankea en su propia ciudad | DinoRank tracking | Captar el *local pack* y las 8 variantes de «adiestrador … sevilla» (~2.000 búsquedas/mes en total) | Medio |
| 13 | **CTA de servicio en todos los posts** (bloque reutilizable al final y a mitad del texto: «¿Tu perro tiene [problema]? Valoración gratuita por WhatsApp») | Analytics | El 55 % del tráfico orgánico pasa a tener un camino de conversión | Bajo |
| 14 | **Pilar «ansiedad en perros»** que consolide separación, comida, coche y miedo-ansiedad-fobia (enlazado y canonical cuando haya duplicación) | DinoRank canibalizaciones | Resolver la canibalización y captar el término principal | Medio |
| 15 | **Limpiar el menú y el pie de página:** quitar las 4 entradas de blog al azar, galerías y categorías del pie; incluir servicios, ciudades y precios | Rastreo | Más PageRank interno hacia las páginas que convierten | Bajo |
| 16 | **E-E-A-T:** página de autor real (nombre, titulación, años, casos) en lugar de «admin», firma y caja de autor en los posts, y fecha de actualización | Auditoría | Señales de experiencia para recuperar el long tail | Bajo |
| 17 | **Optimizar /pack-sesiones/ como «precios de adiestramiento canino»** (tabla de precios, qué incluye, FAQ, schema `Offer`) y aligerar su carga (5,9 s) | DinoRank gap + GSC | 170–590 búsquedas al mes; hoy en la posición 49 | Medio |

### 🟢 Prioridad baja: estrategia a largo plazo (3-12 meses)

| # | Acción concreta | Fuente | Impacto esperado | Esfuerzo |
|---|---|---|---|---|
| 18 | **Consolidar las 59 «entrevistas de radio»:** fusionar con el post del mismo tema (audio incrustado y 301), y aplicar `noindex` o eliminar las que no tengan transcripción ni tráfico | DinoRank visibilidad + rastreo | Principal palanca para revertir la pérdida del long tail de octubre y noviembre de 2025 | Alto |
| 19 | **Crear las landings del gap competitivo:** adiestramiento canino a domicilio, modificación de conducta / psicólogo canino (Sevilla y Cádiz), adiestramiento online y residencia/guardería canina (Ubrique) | DinoRank content gap | Nuevas familias de keywords transaccionales que la competencia ya captura | Alto |
| 20 | **Clúster de razas** (border collie, caniche, rottweiler, doberman, american stafford, pastor alemán, etc.) con la plantilla «carácter + problemas típicos + adiestramiento» y enlace al servicio | GSC + DinoRank | Long tail de razas con intención mixta, donde ya hay tracción (caniche top 3) | Medio |
| 21 | **Linkbuilding local y sectorial:** directorios locales (Ubrique, Sierra de Cádiz), veterinarias y protectoras colaboradoras, prensa y radio local (ya hay relación con la radio: pedir enlace desde la web de la emisora), asociaciones de perros de asistencia | DinoRank linkbuilding | Pasar de 5 a 30+ dominios de referencia: requisito para «adiestrador de perros» (2.900–3.600 búsquedas al mes) | Alto |
| 22 | **GEO/IA:** dar de alta prompts en DinoRank LLMs («mejor adiestrador de perros en Cádiz/Sevilla», «qué es un perro de asistencia»), redactar respuestas directas de 40-60 palabras al inicio de los pilares y revisar el `llms.txt` existente | DinoRank LLMs | Visibilidad en AI Overviews, que ya aparecen en la mayoría de las SERP trackeadas | Medio |
| 23 | **Monitorización:** tracking de las ~25 keywords nuevas, panel mensual GSC + GA4 + DinoRank y revisión de canibalizaciones cada 30 días | Todas | Control del ROI del plan | Bajo |

---

### KPIs objetivo a 6 meses

| KPI | Hoy | Objetivo |
|---|---|---|
| Clics orgánicos al mes (GSC) | ~256 | **450-550** |
| CTR medio | 0,7 % | **1,5 %** |
| Keywords en top 10 (DinoRank) | 36 | **60+** |
| Sesiones medidas en GA4 / clics GSC | 20 % | **≥ 85 %** |
| Leads medidos (tel + WhatsApp + formulario) | 0 (sin medición) | Línea base el mes 1, después +30 % trimestral |
| Dominios de referencia | 5 | **25-30** |
| TTFB | 1,7–4 s | **< 0,8 s** |
