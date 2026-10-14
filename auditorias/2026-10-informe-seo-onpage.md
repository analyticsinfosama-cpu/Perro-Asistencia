# Informe SEO on-page: perroasistencia.es

**Destinatario:** responsable SEO, redacción y contenidos
**Fecha:** octubre de 2026
**Fuentes:** GSC (vía DinoRank), GA4, DinoRank (visibilidad, tracking de 44 keywords, canibalizaciones y content gap con noblecan.com, adiestramientoeducan.com y evolucank9.es) y rastreo propio de 265 URLs

> Este informe trata solo de contenido, metadatos, intención de búsqueda, enlazado editorial y E-E-A-T. Lo que requiere programación está en `2026-10-informe-tecnico-programacion.md`.

---

## 1. Situación de partida

| Métrica | Valor |
|---|---|
| Clics GSC al mes | 335 en abril de 2026 → ~256 en septiembre de 2026 (**−24 %**) |
| Impresiones al mes | 31.000–36.000 (estables) |
| CTR medio | **0,7 %**, muy bajo para una posición media de ~9 |
| Keywords en top 10 | 66 en mayo de 2025 → **36** |
| Keywords en páginas 2-5 | ~260 en julio de 2025 → **~17**: el long tail se perdió en octubre y noviembre de 2025 |
| Landings orgánicas (GA4) | 55 % del tráfico en posts informativos sin llamada a la acción de servicio; contacto 1 sesión, packs 4 |

**Diagnóstico on-page:**
1. Los titles y metas usan un patrón poco fiable («【 】▷», «lll➤ … ✅») y no responden a la intención de búsqueda, de ahí el CTR bajo.
2. Hay contenido duplicado: 58 entrevistas de radio repiten temas de posts.
3. Existen 12 canibalizaciones.
4. Las páginas que ya rankean están huérfanas de enlaces.
5. Las señales de E-E-A-T son débiles: los posts los firma «admin».

---

## 2. Quick wins de CTR: reescritura de title y meta

Son páginas en posiciones 1-6 con CTR inferior al 1 %. **Impacto estimado: +60-100 clics al mes.**

| URL | Pos. / Impr. / CTR | Title actual | **Title propuesto** | **Meta propuesta** |
|---|---|---|---|---|
| /friend-el-perro-guardian-agresivo/ | 1,9 / 606 / 0,5 % | Friend, El Perro Guardián Agresivo - Perro Asistencia | **Perro guardián: por qué se vuelve agresivo y cómo evitarlo (caso real)** | Friend aprendió a atacar paso a paso. Te explicamos qué convierte a un perro guardián en agresivo y qué hacer para reconducirlo, según un adiestrador profesional. |
| /el-collar-estrangulador/ | 3–4,8 / 500 / 0,4 % | 【 Collar Estrangulador 】▷ Método para educar al perro | **Collar estrangulador para perros: cuándo usarlo y riesgos reales** | ¿Es seguro el collar estrangulador? Cómo se coloca, cuándo tiene sentido, qué daños puede causar y qué alternativas recomendamos como adiestradores. |
| /el-instinto-depredador-del-perro/ | 4,8 / 185 / 0 % | 【El instinto depredador del perro: un caso por resolver】 | **Instinto depredador en perros: señales y cómo controlarlo** | Si tu perro persigue gatos, bicis o coches, es instinto de presa. Aprende a reconocer sus fases y los ejercicios para canalizarlo sin peligro. |
| /collar-educativo-de-impulsos-estaticos/ | 5–6,5 / 349 / 0,3 % | Collar Educativo para Perros: Shock Electroestático | **Collar de impulsos para perros: cómo funciona y cuándo NO usarlo** | Qué es el collar de impulsos estáticos, qué dice la ley, riesgos y en qué casos un adiestrador lo desaconseja. Guía honesta y sin venta. |
| /perros-incansables/ | 1,2 / 1.278 / 0,2 % | Perros **Icansables**: Lucas (Caso Real) | **Perros incansables: el caso real de Lucas (con fotos)** | Lucas no paraba nunca. Te contamos con fotos reales cómo canalizamos su energía y qué hacer si tu perro es incansable. |

> /perros-incansables/ rankea en la posición 1 por «perro real» o «imágenes de perros reales», que buscan imágenes. Hay que corregir la errata, poner ALT descriptivos en sus 6 imágenes sin `alt` y asumir que el tráfico de esa query es de bajo valor.

**Reglas para todos los titles del sitio** (aplicar en lotes de 20 URLs, empezando por las que más impresiones tienen en GSC):
- Keyword principal al principio. Entre 50 y 60 caracteres.
- Nada de «【 】», «▷», «lll➤» ni «✅».
- Marca opcional al final, solo en las páginas de servicio («| Perro Asistencia»).
- Meta description de 140-155 caracteres con un beneficio concreto y, en servicios, una llamada a la acción («Valoración gratuita por WhatsApp»).

---

## 3. URLs en posiciones 6-20: optimización on-page

| URL | Keyword objetivo (vol.) | Pos. actual | Acciones |
|---|---|---|---|
| /perro-lazarillo-asistencia-a-la-discapacidad/ | perro lazarillo (590), perros lazarillo (720), qué es un perro lazarillo | 11–12 (0 clics con 1.185 impresiones) | **H1 a «Perro lazarillo: qué es, cómo se entrena y cómo actuar si te cruzas con uno»**. Title «Perro lazarillo: qué es, razas y cómo se entrena». Añadir una definición en 40-60 palabras en el primer párrafo (para AI Overview), H2 con las PAA (razas, duración del entrenamiento, quién puede tenerlo, ley andaluza), tabla «perro guía frente a perro de asistencia» y FAQ. Enlazarla desde /perros-de-asistencia/ y /perro-de-asistencia-de-discapacidad-visual/ |
| /como-afecta-el-sarro-en-perro/ | sarro en perro (590) | 20–24 | Fusionar con /que-sintomas-provoca-el-sarro-en-perros/ (síntomas, causas, prevención, cuándo ir al veterinario, limpieza en casa). Title «Sarro en perros: síntomas, consecuencias y cómo quitarlo». Revisión veterinaria firmada (E-E-A-T) |
| /adiestramiento-border-collie-conduta-obsesiva/ | adiestramiento border collie (170), ejercicios border collie, border collie agresivo (70) | 12–17 | El H1 actual («Quinto, el Border Collie obsesivo») no contiene la keyword. **H1: «Adiestramiento del border collie: cómo gestionar su conducta obsesiva (caso real)»**. Añadir H2 de ejercicios mentales, juegos de olfato y rutina diaria por edad. Hoy no recibe ningún enlace interno |
| /los-instintos-desarrollado-en-el-perro/ | instinto de presa en perros | 11,5 | Corregir el título gramatical («Los instintos desarrollados…»). Enlazarla con /el-instinto-depredador-del-perro/ como pareja, o fusionarlas |
| /prevencion-miedos-doberman-cachorro/ | doberman cachorro miedos | 10,2 | Ampliar con ejercicios por semanas de edad y enlazar al futuro clúster de razas |
| /adiestramiento-canino-sevilla/ | adiestrador de perros sevilla (260–320) y 8 variantes (~2.000 en total) | 11–20 | Ver la sección 5 (landings locales) |
| /adiestramiento-canino-malaga/ | adiestramiento canino málaga (140) | 16–33 | Ver la sección 5 |
| /pack-sesiones/ | precios adiestramiento canino (170–590), cuánto cuesta adiestrar un perro | 49 / 16,6 | H1 «Precios de adiestramiento canino en Cádiz, Sevilla y Málaga». Tabla de precios visible (sesión suelta, packs, a domicilio, perros de asistencia), qué incluye cada pack, FAQ «¿cuánto cuesta adiestrar un perro?» y botón de WhatsApp |

**Método recomendado para cada URL:** ejecutar DinoRank TF-IDF con la keyword objetivo y la URL, y cubrir los términos que faltan de forma natural. Usar las PAA de la SERP como H2.

---

## 4. Canibalizaciones: resolución URL a URL

| Keyword(s) | URLs en conflicto (pos.) | URL ganadora | Acción |
|---|---|---|---|
| adiestrador de perros · adiestramiento canino · entrenador canino | / (11–20) · /sevilla/ (4–8) · /cadiz/ (4,7) | **Home** para la búsqueda genérica; cada ciudad para «… + ciudad» | La home no debe mencionar Sevilla, Cádiz ni Málaga en H1 ni H2: solo un bloque «Dónde trabajamos» con enlaces de anchor local. Cada landing local, con keyword + ciudad en title, H1 y primer párrafo |
| perros de asistencia (390–590) | / (21,7) · /perros-de-asistencia/ (41,8) | **/perros-de-asistencia/** | Quitar «perros de asistencia» del H1 y H2 de la home y dejar una mención con enlace. Ampliar la página dedicada: tipos, proceso, requisitos legales (Ley 4/2017 de Andalucía), plazos, precio orientativo y FAQ |
| adiestramiento respetuoso perros · adiestramiento canino respetuoso | / (29–33) · /adiestramiento-social/ (33–55) | **/adiestramiento-social/** | Retitular como «Adiestramiento canino respetuoso (en positivo)», explicar el método y enlazarla desde la home con ese anchor |
| adiestramiento de perros a domicilio · clases particulares a domicilio | / (42–58) · /sevilla/ (71–85) | **Nueva** /adiestramiento-canino-a-domicilio/ | Crear la landing (sección 7) |
| consejos para controlar la ansiedad de tu perro | /ansiedad-en-perros-por-separacion/ (13) · /ansiedad-por-la-comida…/ (44,8) | **Nuevo pilar** /ansiedad-en-perros/ | El pilar enlaza a separación, comida, coche y miedo-ansiedad-fobia. Cada post enlaza de vuelta al pilar. Valorar fusionar /la-ansiedad-en-el-perro/ con el pilar |
| sarro en perros | /como-afecta-el-sarro…/ · /que-sintomas-provoca-el-sarro…/ | **/como-afecta-el-sarro-en-perro/** | Fusionar el contenido y aplicar 301 (lo hace programación) |
| curso de adiestramiento canino en cádiz | /cadiz/ (5,75) · / (9,3) | **/adiestramiento-canino-cadiz/** | Enlace desde la home con el anchor «adiestramiento canino en Cádiz» |
| adiestradores de perros cerca de mí | /cadiz/ (58) · /sevilla/ (76) | Ficha de GBP + landing de Ubrique | Depende sobre todo de Google Business Profile. Reforzar la landing de la sede |

### Duplicidad editorial: entrevistas de radio (58 URLs)
Listado en `anexos/entrevistas-radio.txt`. Muchas repiten temas que ya tienen post:

| Tema | Post principal (conservar) | Entrevistas o duplicados (fusionar) |
|---|---|---|
| Agorafobia | /la-agorafobia-en-el-perro/ | /la-agorafobia-en-el-perro-cuadragesima-entrevista-de-radio/ |
| Síndrome de furia | /el-sindrome-de-furia-en-el-perro/ | /sindrome-de-la-furia-cuadragesima-segunda-entrevista-de-radio/ |
| Ansiedad en el coche | /ansiedad-en-el-coche/ | /ansiedad-en-el-coche-cuadragesima-primera-entrevista-de-radio/ |
| Conducta de alzada y frotamientos | /los-frotamientos-la-conducta-de-hacer-la-monta/ | /la-conducta-de-alzada-hacia-los-frotamientos/, /conducta-de-alzada-frotamientos-cuadragesima-tercera…/, /perro-salta-conducta-alzada/ |
| La nariz del perro | /la-nariz-del-perro/ | /la-nariz-del-perro-septima-entrevista-de-radio/ |
| La llamada | /la-llamada-en-el-perro/ | /llamada-en-el-perro-decimo-tercera…/, /video-educativo-la-llamada/ |
| Perro excitable | /perro-excitable-o-impulsivo/ | /perro-excitable-cuadragesima-octava…/, /excitabilidad-y-conductas-derivadas…/ |
| Agresividad | /la-agresividad-en-el-perro/ | /la-agresividad-en-el-perro-decima-octava…/, /agresividad-en-perros-vigesimo-cuarta…/ |
| Dependencia | /la-dependencia-caso-real/ | /dependencia-del-perro-decimo-novena…/, /dependencia-hacia-el-perro-decimo-sexta…/, /desarrollo-de-la-dependencia…/ |
| Alergias | /guia-sobre-alergias-en-perros-identificacion-y-cuidados/ | /entrevista-sobre-las-alergias-en-el-perro/, /alergias-en-perro-ambientales-o-alimenticias/ |
| COVID | (valorar `noindex`, contenido caducado) | /covid-19-y-perros/, /los-perros-y-el-covid19…/, /covid-19-y-el-perro-quinta…/ |

**Proceso para cada tema:**
1. Integrar en el post principal lo que aporte la entrevista: el audio incrustado y la transcripción resumida, como sección «Lo explicamos en la radio».
2. Pedir a programación el 301 de la entrevista al post.
3. Las entrevistas sin post equivalente y con contenido útil se transcriben y se reconvierten en post. Las que no tienen texto ni tráfico se pasan a `noindex`.

---

## 5. Landings locales

| Landing | Keyword (vol.) | Pos. | Estado |
|---|---|---|---|
| Sevilla | adiestrador de perros sevilla (260–320) | 11–16 | Evolucank9 ocupa el top 1-3 en las 8 variantes |
| Cádiz | adiestrador canino cádiz (30) | 9 | Es la mejor posicionada |
| Málaga | adiestramiento canino málaga (140) | 16–28 | Débil |
| **Ubrique (sede)** | adiestramiento canino ubrique | **No rankea** (ni en el top 100) | Le ganan /quienes-somos/ (17-20) y /perro-de-asistencia-de-discapacidad-visual/ (26) |

**Plantilla de contenido para cada landing local** (≥ 1.200 palabras de texto **único**; hoy la similitud entre landings es del 25-46 %):
1. **H1** «Adiestrador de perros en [Ciudad]», con el primer párrafo respondiendo directamente qué se ofrece, a quién y dónde.
2. **Zonas atendidas** (barrios o municipios cercanos), si es servicio a domicilio, y mapa.
3. **Problemas que resolvemos**: agresividad, ansiedad, tirones, cachorros… Cada uno enlaza al post o pilar del blog.
4. **Método y proceso** en 3-4 pasos, con precio orientativo y enlace a /pack-sesiones/.
5. **Casos reales de la ciudad**: testimonios con nombre del perro y barrio, y fotos de sesiones reales.
6. **FAQ local**: «¿vais a domicilio en [ciudad]?», «¿cuánto cuesta?».
7. **CTA** de WhatsApp y llamada arriba, a mitad y al final.

**Ubrique:**
- Reescribir el title: «Adiestrador canino en Ubrique | Perro Asistencia (centro y residencia)».
- Añadir la dirección física y la vinculación con la residencia canina (la keyword «residencia canina los parejos», con 210 búsquedas, apunta hoy a /quienes-somos/).
- Enlazarla desde /quienes-somos/ y la home.

---

## 6. Enlazado interno editorial

**Datos del rastreo:**
- 109 de 255 posts (43 %) no reciben **ningún enlace editorial**; 86 están totalmente huérfanos.
- Las landings de servicio reciben solo el enlace del menú (2-5 enlaces editoriales).

### 6.1 Prioridad 1: activos huérfanos con impresiones
Cada uno debe recibir entre 3 y 5 enlaces contextuales desde posts del mismo tema:

| URL destino | Enlazar desde | Anchor sugerido |
|---|---|---|
| /perro-lazarillo-asistencia-a-la-discapacidad/ | /perros-de-asistencia/, /perro-de-asistencia-de-discapacidad-visual/, /seleccion-del-perro-guia/, /reciclaje-del-perro-de-asistencia…/, /caracteristicas-del-perro-guia…/ | «perro lazarillo» |
| /adiestramiento-border-collie-conduta-obsesiva/ | /obsesion-por-el-juego/, /perro-persigue-la-cola/, /duna-y-la-neurosis-de-la-cola-caso-real/, /perros-incansables/ | «adiestramiento del border collie» |
| /el-collar-estrangulador/ | /collar-de-adiestramiento-de-puas/, /collar-cabezal-para-perros-halti/, /arnes-para-perros-como-y-cuando-usarlo/, /el-tiro-de-la-correa/, /correas-para-perros/ | «collar estrangulador» |
| /el-instinto-depredador-del-perro/ | /los-instintos-desarrollado-en-el-perro/, /por-que-los-perros-callejeros-persiguen-a-las-personas/, /las-fugas-en-el-perro/, /impulsos-hacia-el-movimiento…/ | «instinto depredador» |
| /ansiedad-en-perros-por-separacion/ | /ladridos-en-la-soledad/, /el-perro-destructivo/, /la-dependencia-caso-real/, /miedo-ansiedad-fobia/ | «ansiedad por separación» |
| /como-afecta-el-sarro-en-perro/ | /que-pienso-debo-dar-a-mi-perro/, /envejecimiento-canino…/, /alimentacion-y-comportamiento-del-perro/ | «sarro en perros» |

### 6.2 Prioridad 2: blog → servicios
- **Todo post** de conducta enlaza al menos a 1 servicio, con el anchor adaptado al tema. Por ejemplo: «si tu perro muestra agresividad, nuestro **adiestrador de perros** puede ayudarte» → home o landing local.
- Bloque de CTA reutilizable al final de cada post: «¿Tu perro tiene este problema? Valoración gratuita por WhatsApp» → /contacto/ + /pack-sesiones/.

### 6.3 Arquitectura de pilares (hub & spoke)

| Pilar (URL hub) | Posts satélite (ejemplos) |
|---|---|
| **Problemas de conducta** (/problemas-de-conducta-en-perros/, nuevo) | agresividad, rencor, síndrome de furia, excitabilidad, alzada, marcaje, coprofagia, perro destructivo |
| **Ansiedad y miedos** (/ansiedad-en-perros/, nuevo) | separación, comida, coche, agorafobia, petardos, miedos generalizados, perro tímido |
| **Cachorros** (/plan-de-actuacion-para-cachorros/) | socialización, nuevo cachorro, empapador, mordidas, FRAP, inseguridad inicial |
| **Material de adiestramiento** (nuevo) | collares (estrangulador, púas, impulsos, antiladridos, halti), arnés, correas, bozal, jaula |
| **Razas** (nuevo) | border collie, caniche, rottweiler, doberman, american stafford |
| **Perros de asistencia** (/perros-de-asistencia/) | lazarillo, discapacidad visual, movilidad reducida, selección del perro guía, perro de alerta |
| **Salud** (/salud/) | sarro, coccidiosis, procesionaria, alergias, desparasitación, displasia |

Regla: cada satélite enlaza a su pilar (anchor exacto) y a 2 satélites hermanos, y cada pilar enlaza a todos sus satélites y a 1 servicio.

---

## 7. Contenido nuevo (gaps de DinoRank)

| Prioridad | URL nueva | Keywords (vol.) | Competidor que la captura |
|---|---|---|---|
| Alta | /adiestramiento-canino-a-domicilio/ | adiestrador canino a domicilio (170), adiestramiento canino a domicilio (170), adiestrador de perros a domicilio (70) | Noblecan (pos. 1), Educan |
| Alta | /ansiedad-en-perros/ (pilar) | ansiedad en perros, consejos ansiedad perro | — |
| Media | /modificacion-de-conducta-canina/ (+ variante Sevilla) | psicólogo canino (140), psicólogo perro (170), reactividad canina, etólogo canino (90) | Evolucank9, Noblecan |
| Media | /residencia-canina-ubrique/ (o reconvertir /estancia-para-perros/) | residencia canina + Ubrique/Sierra de Cádiz, residencia canina los parejos (210) | — |
| Media | Clúster de razas (5-8 posts) | adiestramiento border collie (170), cómo educar un caniche toy (70), rottweiler agresivo (210) | Noblecan (border collie pos. 2) |
| Baja | /adiestramiento-canino-online/ | curso de adiestramiento canino online (390), adiestrador canino online (390) | Noblecan |
| Baja | /olores-que-odian-los-perros/ | olores que odian los perros (390) | Noblecan (pos. 1) |

---

## 8. E-E-A-T

- **Autor real:** sustituir «admin» por el adiestrador, con nombre, foto, titulaciones, años de experiencia, nº de perros atendidos y participación en radio. Crear la página /autor/[nombre]/ y una caja de autor en cada post.
- **Revisión experta** en los posts de salud (sarro, coccidiosis, procesionaria, alergias): «Revisado por [veterinario colegiado]» con fecha.
- **Casos reales:** ya existen («caso real») y son el mejor activo de experiencia. Hay que unificarlos con la etiqueta visual «Caso real», con fotos propias y el resultado obtenido.
- **Fecha de actualización** visible en los posts revisados.
- **Prueba social:** reseñas de Google embebidas en la home, las landings y /pack-sesiones/.

---

## 9. GEO: visibilidad en IA (AI Overviews, ChatGPT)

- La mayoría de las SERP trackeadas muestran AI Overview (dato de DinoRank).
- **Abrir cada post y pilar con una respuesta directa** de 40-60 palabras a la pregunta principal, antes de la introducción.
- Usar listas y tablas para pasos, comparativas y precios, porque son fáciles de citar.
- En DinoRank LLMs, dar de alta prompts como «mejor adiestrador de perros en Cádiz», «adiestrador canino en Sevilla», «qué es un perro de asistencia» y «cómo entrenar a un perro lazarillo». Hoy hay 0 prompts trackeados.

---

## 10. Plan de acción on-page

### 🔴 Prioridad alta (0-30 días)
| Acción | Fuente | Impacto | Esfuerzo |
|---|---|---|---|
| Reescribir title y meta de las 5 URLs del punto 2 | GSC | +60-100 clics al mes | Bajo |
| Fusionar los posts de sarro y optimizar la URL ganadora | DinoRank + GSC | «sarro en perro» (590) al top 10 | Bajo |
| Enlazar los 6 activos huérfanos (6.1) | Rastreo + GSC | Lazarillo y border collie al top 10 | Bajo |
| Optimizar perro lazarillo (H1, definición, PAA, FAQ) | GSC | 1.185 impresiones con 0 clics → 30-50 clics al mes | Bajo |
| CTA de servicio en todos los posts | GA4 | Camino de conversión para el 55 % del tráfico | Bajo |

### 🟡 Prioridad media (1-3 meses)
| Acción | Fuente | Impacto | Esfuerzo |
|---|---|---|---|
| Resolver las canibalizaciones de home, landings, asistencia y respetuoso (punto 4) | DinoRank | 5 clústeres resueltos | Medio |
| Rehacer las 4 landings locales con la plantilla del punto 5 (Ubrique primero) | DinoRank tracking | Sevilla al top 5; Ubrique en el top 3 | Medio |
| Convertir /pack-sesiones/ en la página de precios | DinoRank gap | 170-590 búsquedas al mes | Medio |
| Reescribir titles y metas del resto del sitio en lotes de 20 | GSC | CTR medio del 0,7 % al 1,5 % | Medio |
| Optimizar en lotes las URLs en posiciones 6-20 (punto 3) | GSC + TF-IDF | +5-8 keywords en el top 10 | Medio |
| Página y caja de autor; revisión veterinaria en los posts de salud | Auditoría | Señales de E-E-A-T | Bajo |

### 🟢 Prioridad baja (3-12 meses)
| Acción | Fuente | Impacto | Esfuerzo |
|---|---|---|---|
| Consolidar las 58 entrevistas de radio (punto 4) | DinoRank visibilidad | Recuperar el long tail perdido | Alto |
| Crear pilares y arquitectura hub & spoke (6.3) | Rastreo | Autoridad temática | Alto |
| Contenido nuevo del content gap (punto 7) | DinoRank | Nuevas familias de keywords transaccionales | Alto |
| Optimización GEO y tracking de prompts en DinoRank LLMs | DinoRank | Visibilidad en AI Overviews | Medio |

### KPIs a 6 meses
| KPI | Hoy | Objetivo |
|---|---|---|
| Clics orgánicos al mes | ~256 | 450-550 |
| CTR medio | 0,7 % | 1,5 % |
| Keywords en top 10 | 36 | 60+ |
| Canibalizaciones (DinoRank) | 12 | ≤ 3 |
| Posts sin enlaces editoriales | 109 | < 20 |
