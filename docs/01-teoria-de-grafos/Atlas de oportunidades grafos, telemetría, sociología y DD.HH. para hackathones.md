# Atlas de oportunidades: grafos, telemetría, sociología y DD.HH. para hackathones

Nov 5, 2026 · @Anna Tchijova

## Índice maestro

Este documento reúne los nueve entregables pedidos (A a I) en un solo cuerpo, ordenado de lo general (problemas y técnicas) a lo particular (fichas de prototipo, skills). Cada idea del atlas lleva un código estable (G = grafos, T = telemetría, GT = combinadas, S = sociales/DD.HH./crimen organizado) que se usa en la shortlist, las fichas y la matriz de riesgos.

| Entregable | Sección | Contenido |
| --- | --- | --- |
| A | Metodología; Bloques I–V; Grafos; Telemetría | Informe de investigación: problemas documentados, marco teórico, técnicas |
| B, C | Atlas de 60 oportunidades | 60 fichas compactas con fuentes y alternativas existentes |
| D | Filtrado adversarial y shortlist | Descartes argumentados y 20 finalistas por categoría |
| E | Diez fichas de prototipo | Hipótesis, arquitectura, modelo de datos, pruebas, demos, criterio de abandono |
| F | Matriz de riesgos | Riesgos éticos, legales y de privacidad por finalista |
| (XI) | Relación con el portfolio | Reutilizaciones posibles, solo sobre lo que conozco de tus proyectos |
| G | Propuesta modular de skills | Diez skills con trigger, inputs, outputs, verificaciones, dependencias |
| H | Bibliografía | Fuentes consultadas con enlace |
| I | Preguntas abiertas | Lo que no pude resolver y qué lo resolvería |

Si alguna sección queda corta para tu uso, la ampliamos en una entrega posterior sin renumerar las ideas.

## Metodología

La investigación sigue el ciclo abductivo de Peirce: observación de una anomalía o necesidad, conjetura explicativa, deducción de consecuencias contrastables e inducción (prueba). En la práctica, cada idea del atlas se sostiene sobre una necesidad observada en una fuente, y termina con un criterio de falsación: el hallazgo que demostraría que no aporta valor.

### Convención de etiquetas

Cada afirmación relevante lleva una de estas marcas, entre corchetes:

- **\[D\] Documentado**: lo dice una fuente consultada y enlazada en este documento.
- **\[C\] Conocimiento general verificable**: hecho técnico o bibliográfico estable (un algoritmo, un autor, un estándar) que no requiere enlace específico, pero que podés comprobar.
- **\[I\] Inferencia**: conclusión mía a partir de hechos documentados; puede estar equivocada.
- **\[H\] Hipótesis de utilidad**: lo que el prototipo tendría que demostrar.
- **\[P\] Propuesta original**: diseño mío; no afirmo que no exista algo parecido salvo que lo diga con evidencia.

### Clasificación de novedad

Se usa la escala que pediste: A (problema poco atendido), B (nueva combinación de técnicas), C (mejora específica frente a herramientas existentes), D (adaptación a usuario o contexto desatendido), E (novedad no demostrada). Una búsqueda que no encuentra competidores no prueba que no existan: en esos casos la clasificación máxima es E con una nota de qué búsqueda se hizo.

### Alcance y límites honestos

- La búsqueda bibliográfica se hizo con buscador web durante esta sesión. No tuve acceso a bases académicas con suscripción (Scopus, Web of Science), así que la cobertura académica es la que está abierta en la web.
- No examiné tus repositorios en esta sesión. Lo que digo de tu portfolio sale solo de las descripciones que ya conozco de tus proyectos, y lo marco como tal.
- Los tiempos de prototipo suponen una persona con experiencia en Python o TypeScript y en bases de grafos; son estimaciones \[I\], no mediciones.
- No se proponen herramientas de atribución de culpabilidad, perfilado de personas vulnerables ni vigilancia. Donde una idea toca personas, el diseño parte de entidades jurídicas, documentos o sistemas, no de individuos.

### Principio de corte: cuándo un grafo o la telemetría no se justifican

Una idea se descarta o se penaliza si la pregunta central se responde igual de bien con un `GROUP BY`, un `JOIN` de dos tablas o un orden cronológico de eventos. El grafo se justifica cuando la pregunta depende de **caminos de longitud variable, conectividad, cortes, estructura de vecindario o cambios de topología**. La telemetría se justifica cuando hay un proceso en curso cuyo estado solo se conoce por emisiones periódicas o por eventos, y cuando importa la calidad, la completitud o el orden de esas emisiones.

## A. Problemas documentados (Bloques I, IV y V)

El hallazgo central es que los problemas mejor documentados no son de falta de datos, sino de **pérdida, cambio silencioso, fragmentación y baja verificabilidad** de datos que ya existen y son públicos. Eso favorece prototipos chicos que miden, preservan o reconcilian, y desfavorece plataformas que prometen "descubrir" algo nuevo.

### 1. Pérdida y degradación de evidencia digital

- &#91;D\] Pew Research (mayo 2024) midió que el 38% de las páginas que existían en 2013 ya no estaban accesibles en 2023, que el 21% de una muestra de \~500.000 páginas gubernamentales de EE.UU. tenía al menos un link roto, y que alrededor del 54% de los artículos de Wikipedia tenía al menos una referencia rota ([Pew, *When Online Content Disappears*](https://www.pewresearch.org/data-labs/2024/05/17/when-online-content-disappears/)). Según coberturas del mismo estudio, los posts en turco y árabe desaparecían más que el promedio ([NewsX](https://www.newsx.com/?p=794755)), un dato a verificar contra el informe original.
- &#91;D\] Desde 2017, la moderación automática de YouTube eliminó cientos de miles de videos de activistas sirios. Syrian Archive (hoy bajo Mnemonic) armó el proyecto *Lost & Found* comparando su colección con lo que seguía en línea, y esa comparación alimentó su incidencia regulatoria ([Kayyali, *Sociologica*, 2022](https://sociologica.unibo.it/article/download/15383/14818?inline=1); [Jordan Times/AFP](https://jordantimes.com/node/340988)).
- &#91;D\] El Protocolo de Berkeley (UC Berkeley + ACNUDH, 2020, actualizado 2022) fija estándares mínimos para identificar, recolectar, preservar, verificar y analizar información digital de fuente abierta; la preservación es una fase propia, no un detalle técnico ([Human Rights Center, Berkeley](https://humanrights.berkeley.edu/projects/berkeley-protocol-on-digital-open-source-investigations/)).
- &#91;I\] Hueco observable: las herramientas habituales detectan el 404, pero no el **cambio de contenido detrás de una URL que sigue respondiendo 200** ("soft 404", texto reescrito, documento reemplazado). Para un informe de DD.HH. o periodístico ese segundo caso es peor, porque la cita parece válida.

### 2. Cambios silenciosos en registros y páginas oficiales

- &#91;D\] EDGI monitorea miles de páginas federales de EE.UU. con software abierto y analistas voluntarios; publicó un dataset de \~1.500 cambios significativos en páginas ambientales entre 2017 y 2021 ([EDGI web-monitoring](https://github.com/edgi-govdata-archiving/web-monitoring); [freegovinfo](https://freegovinfo.info/node/14108/)). Su aporte metodológico es la validación humana de cada cambio, no solo el diff.
- &#91;D\] InfoLEG publica en datos abiertos la base de normativa nacional y dos bases complementarias: normas modificadas y normas modificatorias ([datos.gob.ar, Base Infoleg](https://datos.gob.ar/dataset/justicia-base-infoleg-normativa-nacional/archivo/justicia_bf0ec116-ad4e-4572-a476-e57167a84403)). Ya hay ejercicios de cargarlas en Neo4j para ver qué normas se modifican más ([Olmos, *On Regulatory Simplification*](https://martinolmos.github.io/data_ict/en/posts/on-regulatory-simplification/index.html)).
- &#91;D\] El Registro Único de Audiencias de Gestión de Intereses (Decreto 1172/2003) tiene dataset abierto ([datos.gob.ar](https://datos.gob.ar/hr/dataset/otros-registro-unico-audiencias-gestion-intereses)). Chequeado documentó una reunión presidencial confirmada oficialmente que no figuraba en el registro ([Chequeado](https://chequeado.com/el-explicador/registro-de-audiencias-de-funcionarios-como-funciona-y-por-que-hasta-el-estado-destaca-que-no-es-tan-util/)), y un proyecto de diputados de 2022 cuestionó audiencias registradas que serían "falsas" ([HCDN 7200-D-2022](https://www4.hcdn.gob.ar/dependencias/dsecretaria/Periodo2022/PDF2022/TP2022/7200-D-2022.pdf)).
- &#91;D\] El plan de Gobierno Abierto 2025–2027 de Argentina incluye un compromiso (AR0107) que reconoce baja calidad en la publicación de datos abiertos y propone una metodología nacional para evaluarla ([OGP, AR0107](https://www.opengovpartnership.org/members/argentina/commitments/AR0107/)).

### 3. Fragmentación entre fuentes: contrataciones, sociedades, funcionarios

- &#91;D\] Open Contracting Partnership publicó en 2024 una guía de 73 indicadores de riesgo (*red flags*) mapeados al estándar OCDS ([OCP, Red Flags](https://open-contracting.org/?p=26247)), y una librería abierta en Rust, Cardinal, que al lanzarse calculaba 10 indicadores ([OCP, Cardinal](https://www.open-contracting.org/2024/06/12/cardinal-an-open-source-library-to-calculate-public-procurement-red-flags/)).
- &#91;D\] Wachs, Fazekas y Kertész modelaron más de 4 millones de contratos europeos como redes bipartitas comprador–proveedor y encontraron que el riesgo de corrupción se agrupa, a veces en el núcleo y a veces en la periferia según el país ([arXiv 1909.08664](https://ar5iv.labs.arxiv.org/html/1909.08664)). Fazekas y Wachs mostraron que los compradores de alto riesgo tienen vecindarios más ralos de lo esperado y re-cablean sus proveedores entre 20% y 40% más que el resto cuando cambia el gobierno ([*Politics and Governance*, 2020](https://cogitatiopress.com/politicsandgovernance/article/view/2707)). Ese es un ejemplo limpio de pregunta que solo responde un grafo temporal.
- &#91;D\] Argentina: COMPR.AR publica convocatorias y adjudicaciones en datos.gob.ar ([dataset JGM](https://datos.gob.ar/zh_CN/dataset/jgm-sistema-contrataciones-electronicas/archivo/jgm_4.17)); CABA y Mendoza publican OCDS en el registro de OCP ([CABA](https://data.open-contracting.org/en/publication/17), [Mendoza](https://data.open-contracting.org/en/publication/137)). Hay que verificar cobertura temporal real antes de diseñar: la ficha de CABA muestra un rango acotado.
- &#91;D\] La IGJ publica datasets de entidades, domicilios, autoridades, asambleas y balances; no lleva registro de accionistas de sociedades anónimas, lo que limita cualquier grafo de propiedad ([fuente secundaria, InfobelPro](https://www.infobelpro.com/en/blog/argentina-company-lookup-guide)). La Oficina Anticorrupción publica declaraciones juradas en formato abierto desde el año fiscal 2012 ([ARCA](https://www.afip.gob.ar/transparencia/ddjj.asp); [datos.gob.ar](https://datos.gob.ar/dataset/justicia-declaraciones-juradas-patrimoniales-integrales-caracter-publico)).
- &#91;D\] Ya existen agregadores argentinos que cruzan sociedades, autoridades y funcionarios en un grafo (por ejemplo [indicadores.ar](https://indicadores.ar/empresa/30711010358) y [Socios.red](https://www.idealist.org/en/nonprofit/7042a6ed63d645338e8884d84c3634db-sociosred-bkm)). Cualquier idea de "grafo persona–empresa" para Argentina compite con ellos y debe diferenciarse en otra cosa.
- &#91;D\] Estándares y ecosistema: BODS v0.4 se declara "network-first" y hoy no está en desarrollo activo ([BODS](https://standard.openownership.org/es/main/about)); FollowTheMoney es el modelo de grafo de OpenSanctions, versión 4.0 en 2025 ([OpenSanctions](https://www.opensanctions.org/articles/2025-07-13-followthemoney)); OCCRP cerró el desarrollo abierto de Aleph al lanzar Aleph Pro en octubre de 2025, y DARC mantiene el fork abierto OpenAleph ([OCCRP FAQ](https://www.occrp.org/en/announcement/aleph-pro-frequently-asked-questions-on-the-future-of-occrps-investigative-data-platform); [OpenAleph](https://openaleph.org/blog/2025/openaleph-commits-to-the-commons/)).

### 4. Seguimiento de compromisos y respuestas institucionales

- &#91;D\] La Ley 27.275 obliga a cada responsable de acceso a informar cantidad de solicitudes, plazos y rechazos; la AAIP institucionalizó en 2025 un sistema de seguimiento de solicitudes con tablero estadístico (Res. 148/2025) ([argentina.gob.ar](https://www.argentina.gob.ar/node/474669)). Algunos organismos publican informes trimestrales en PDF con días hábiles de respuesta, por ejemplo el Consejo de la Magistratura ([informe jul–sep 2025](https://consejomagistratura.gov.ar/wp-content/uploads/2025/12/Informe-para-Agencia-de-Acceso-jul_ago_sep-2025.pdf)).
- &#91;D\] MuckRock, con más de 30.000 pedidos FOIA, encontró un promedio de \~70 días de respuesta, y advierte que su dato solo refleja pedidos hechos por su plataforma ([MuckRock](https://www.muckrock.com/news/archives/2017/mar/14/muckrock-foia-response-data/)). Ese sesgo de selección es exactamente el tipo de problema de telemetría institucional que interesa.
- &#91;D\] Para recomendaciones de órganos de DD.HH. existen el Índice Universal (UHRI), la base nacional NRTD de ACNUDH, SIMORE y la base de UPR Info con más de 100.000 recomendaciones, desarrollada con HURIDOCS ([Geneva Academy, directorio](https://archives.geneva-academy.ch/geneva-humanrights-platform/tracking-tools.html); [UPR Info](https://www.geneva-academy.ch/news/detail/695-in-highlight-upr-info-database)).
- &#91;I\] Hueco: estas bases registran la recomendación y el reporte estatal, pero no conectan automáticamente la recomendación con la **norma posterior** que la implementaría (o la contradice). InfoLEG permite intentar ese vínculo para Argentina.

### 5. Conteo, duplicación y sesgo de documentación

- &#91;D\] HRDAG combina vinculación de registros con *multiple systems estimation* para estimar violaciones no documentadas; esas estimaciones se usaron como prueba en el juicio a Ríos Montt ([arXiv 1510.07714](https://arxiv.org/pdf/1510.07714)) y en Filipinas estimaron cerca del triple de muertes que el conteo policial ([ICIJ](https://www.icij.org/inside-icij/2019/09/counting-the-dead-how-statistics-can-find-unreported-killings/)).
- &#91;I\] Consecuencia de diseño: cualquier herramienta que agregue listas de distintas organizaciones debe exponer el **solapamiento** entre fuentes; sumar listas es un error metodológico, y el solapamiento es información.

### 6. Redes criminales desde fuentes públicas: límites duros

- &#91;D\] La literatura de redes criminales (Morselli, *Inside Criminal Networks*) insiste en que la fuente condiciona la red; Berlusconi (2013) mostró que elegir escuchas u otro registro judicial cambia las medidas de centralidad ([Global Crime](https://econpapers.repec.org/RePEc:taf:fglcxx:v:14:y:2013:i:1:p:61-81)). Trabajos de 2025 proponen centralidad dinámica con análisis de sensibilidad a aristas faltantes ([arXiv 2509.08028](https://arxiv.org/html/2509.08028v1)) y advierten que la mala calidad de datos compromete las estrategias de intervención ([Yeung et al., *EPJ Data Science*](https://epjdatascience.springeropen.com/articles/10.1140/epjds/s13688-025-00553-x)).
- &#91;I\] Consecuencia: en este atlas no hay rankings de "actores clave" sobre personas. Lo útil y defendible es medir **cuánto depende una conclusión de los datos faltantes** y trabajar sobre entidades jurídicas, contratos y documentos.

### 7. Marco teórico aplicado (Bloque IV)

Solo se usan autores donde cambian el diseño de una idea:

- **Weber**: la dominación legal-racional se ejerce por expediente. Quien controla el registro escrito controla la trazabilidad; de ahí las ideas sobre expedientes, plazos y respuestas institucionales (S, T).
- **Goffman**: el registro oficial es una fachada (*front stage*); la brecha entre lo registrado y lo confirmado por otras vías (audiencias no cargadas) es el objeto de estudio, no un error de datos.
- **Granovetter y Burt**: los lazos débiles y los huecos estructurales explican la intermediación. Sirven para describir mercados de contratación, pero la centralidad no prueba conducta; por eso el atlas mide robustez, no culpas.
- **Bourdieu**: las trayectorias entre campos (Estado, empresa, estudio jurídico) son capital acumulado. El registro de actividades anteriores y posteriores a la función pública (MAPPAP) habilita estudiar puertas giratorias como grafo temporal, con cautela sobre personas.
- **Latour**: documentos y bases son *inscripciones* que circulan como "móviles inmutables"; un grafo de procedencia hace explícito ese recorrido y dónde dejó de ser inmutable.
- **Foucault** y estudios de vigilancia: toda infraestructura de visibilidad produce sujetos y riesgos. Criterio operativo: las ideas apuntan la visibilidad hacia instituciones y documentos, no hacia personas vulnerables.
- **Ostrom**: las herramientas abiertas de investigación son bienes comunes con problemas de gobernanza (el cierre de Aleph es un caso); también lo son las dependencias de software mantenidas por una o dos personas.
- **Campbell y Goodhart**: cuando un indicador se vuelve meta, se degrada. Hood y Piotrowska documentaron *gaming* por recategorización del gasto público británico ([ORA Oxford](https://ora.ox.ac.uk/objects/uuid:e5fe165e-18aa-4d38-b4b3-a24287be19e1/files/sqf85nb34z)). Toda métrica de este atlas se evalúa contra ese riesgo.
- **Sociología del conocimiento**: los datos faltantes no son aleatorios. Qué se registra, qué se borra y en qué idioma desaparece más rápido refleja relaciones de poder; varias ideas convierten la ausencia en dato.

### 8. Necesidades documentadas frente a inferidas

| Necesidad | Estado | Base |
| --- | --- | --- |
| Preservar evidencia antes del borrado | Documentada | Berkeley Protocol; Mnemonic |
| Detectar cambios silenciosos en páginas oficiales | Documentada | EDGI; Pew |
| Calcular red flags de contratación con datos OCDS | Documentada | OCP; Cardinal |
| Detectar cambio estructural en redes de contratación | Documentada (académica) | Fazekas y Wachs 2020 |
| Vincular recomendaciones de DD.HH. con normas posteriores | Inferida | UHRI/NRTD + InfoLEG |
| Medir completitud y sesgo de registros institucionales | Documentada parcialmente | MuckRock; caso audiencias |
| Medir robustez de conclusiones de redes ante faltantes | Documentada (académica) | Berlusconi; Catlin et al. |
| Telemetría de agentes de IA con semántica estándar | Documentada, inmadura | OTel GenAI, ver sección Telemetría |

## A. Grafos en profundidad (Bloque II)

Un grafo aporta algo que una tabla no aporta solo cuando la pregunta depende de **relaciones transitivas o de la forma del vecindario**: ¿existe un camino?, ¿qué se desconecta si quito esto?, ¿cambió la estructura?, ¿qué conclusiones dependen de un único eslabón? Si la pregunta es "cuántos", "cuál es el mayor" o "qué pasó primero", alcanza con SQL o con una lista ordenada.

### Prueba de pertinencia (aplicada a las 60 ideas)

1. ¿La consulta central recorre caminos de longitud variable o desconocida? Si no, probablemente es un `JOIN`.
2. ¿Importa la topología (cortes, puentes, componentes, comunidades) y no solo atributos de nodos?
3. ¿El resultado cambiaría si se reordenaran las filas de una tabla equivalente? Si no cambia, el grafo es decorativo.
4. ¿Hay una baseline tabular contra la que comparar? Si no se puede construir, la idea no es verificable.

### Tipos de grafo y cuándo se justifican

| Tipo | Qué responde que una tabla no | Algoritmos o mecanismos \[C\] | Riesgo interpretativo |
| --- | --- | --- | --- |
| Temporal | Alcanzabilidad respetando el orden del tiempo (un vínculo de 2024 no explica un hecho de 2020) | Caminos que respetan el tiempo (*time-respecting paths*), ventanas deslizantes, motivos temporales | Agregar todo en un grafo estático crea caminos imposibles |
| Heterogéneo / multicapa | Rutas que cruzan tipos de relación (contrato → sociedad → autoridad → audiencia) | Metacaminos, proyección de capas, recorridos tipados | Mezclar capas de distinta calidad como si valieran igual |
| Procedencia (W3C PROV) | De qué entidad, actividad y agente deriva un dato | Linaje hacia atrás, impacto hacia adelante, bundles | Procedencia declarada no es procedencia verificada |
| Eventos | Qué eventos comparten participantes, lugar o documento | Grafos bipartitos evento–entidad, proyección | Co-ocurrencia no implica relación |
| Evidencia | Qué afirmación se apoya en qué fuente, con qué independencia | Conteo de caminos independientes, cortes mínimos | Dos fuentes que citan a una tercera no son dos fuentes |
| Contradicciones / argumentación | Qué afirmaciones son mutuamente incompatibles y qué conjuntos son consistentes | Marcos de argumentación de Dung, extensiones, 2-SAT para restricciones binarias | Formalizar mal una contradicción crea falsos conflictos |
| Conocimiento | Integración de entidades con esquema explícito | Ontologías, SPARQL, reglas | Sobremodelado: ontologías enormes que nadie mantiene |
| Causal (DAG) | Qué ajustes son necesarios para estimar un efecto, bajo supuestos | d-separación, criterio de puerta trasera | El DAG codifica supuestos; no los prueba con datos observacionales |
| Confianza / autoridad | Cómo se propaga la credibilidad entre fuentes | PageRank personalizado, EigenTrust | Recompensa popularidad y es manipulable |
| Colaboración / dependencia | Riesgo de punto único de falla | Puntos de articulación, puentes, cortes mínimos, bus factor | Contar commits no es medir capacidad de mantenimiento |
| Resolución de entidades | Qué registros son la misma entidad, con qué probabilidad | Fellegi–Sunter, componentes conexos sobre aristas de *match*, clustering correlacional | La transitividad propaga errores: A≈B y B≈C no garantiza A≈C |

### Algoritmos clásicos que resuelven más de lo que parece

- **Cortes mínimos y puntos de articulación** \[C\]: miden fragilidad ("esta conclusión depende de una sola fuente"). Son deterministas, explicables y baratos.
- **Componentes conexos con aristas ponderadas por confianza** \[C\]: permiten mostrar cómo cambia la red al subir el umbral de confianza; es la forma honesta de presentar resolución de entidades.
- **Caminos que respetan el tiempo** \[C\]: eliminan explicaciones anacrónicas.
- **k-core y detección de núcleo–periferia** \[C\]: es lo que usaron Wachs, Fazekas y Kertész para ubicar el riesgo en mercados de contratación ([arXiv 1909.08664](https://ar5iv.labs.arxiv.org/html/1909.08664)).
- **Comparación de grafos entre ventanas** (Jaccard de vecindarios, tasa de re-cableado) \[C\]: es la métrica del hallazgo de Fazekas y Wachs sobre cambio de gobierno ([2020](https://cogitatiopress.com/politicsandgovernance/article/view/2707)).
- **Análisis de sensibilidad por remoción o adición aleatoria de aristas** \[D\]: la técnica de Catlin et al. para estimar cuánto cambian los rankings con datos faltantes ([arXiv 2509.08028](https://arxiv.org/html/2509.08028v1)).

### Centralidad: por qué se usa con cuidado

- &#91;D\] En redes criminales, los actores importantes no necesariamente tienen alta centralidad, y la fuente de datos cambia el ranking (Berlusconi 2013; ver sección anterior).
- &#91;I\] En redes de contratación, alta centralidad de un proveedor puede reflejar especialización legítima o un mercado chico. La centralidad describe posición, nunca conducta.
- Regla del atlas: toda métrica de centralidad se acompaña de su intervalo bajo perturbación y nunca se aplica a personas físicas como salida final.

### Resolución de entidades con incertidumbre

- &#91;D\] Splink implementa Fellegi–Sunter con estimación por EM, enlaza un millón de registros en una laptop en alrededor de un minuto y advierte que no está diseñado para enlazar una única columna de nombres sin otros atributos ([Splink, GitHub](https://github.com/JonnyShiUW/splink); [IJPDS 2022](https://doi.org/10.23889/ijpds.v7i3.1794)).
- &#91;D\] OpenSanctions resuelve duplicados registrando juicios positivos y negativos como un grafo de IDs y fusiona por componentes conexos; almacena entidades como conjuntos de *statements*, uno por valor de propiedad ([OpenSanctions, deduplicación](https://www.opensanctions.org/articles/2021-11-11-deduplication)).
- &#91;I\] Oportunidad recurrente: casi ninguna herramienta pública muestra **qué conclusiones del análisis posterior cambian si se revierte un match dudoso**. Esa propagación de incertidumbre es un problema de grafos bien delimitado.

### Herramientas de base (estado verificado)

| Herramienta | Uso | Nota |
| --- | --- | --- |
| [Raphtory](https://github.com/pometry/raphtory) | Grafos temporales en memoria, Rust con API Python, vistas en el tiempo y ventanas | Licencia GPL-3.0; [JOSS 2024](https://networkscienceinstitute.org/publications/raphtory-the-temporal-graph-engine-for-rust-and-python) |
| NetworkX / igraph \[C\] | Algoritmos clásicos | Suficientes para prototipos de hackathon |
| Neo4j \[C\] | Grafo de propiedades persistente, Cypher | Usado por OpenSanctions y C4ADS con FtM ([C4ADS](https://c4ads.org/tech-bulletin/bringing-follow-the-money-into-the-graph-a-new-neo4j-tool/)) |
| [FollowTheMoney](https://www.opensanctions.org/docs/entities/) | Ontología de grafo para anticorrupción | Base común de OpenSanctions y OpenAleph |
| [prov (Python)](https://prov.readthedocs.io/en/latest/readme.html) | W3C PROV en PROV-O, PROV-JSON, PROV-XML | Licencia MIT |
| [Splink](https://github.com/JonnyShiUW/splink) | Vinculación probabilística de registros | DuckDB por defecto |

Para un hackathon individual, la combinación más rendidora es **DuckDB + NetworkX (o Raphtory si el tiempo es central)**, con el grafo materializado solo para la consulta que lo necesita. Una base de grafos persistente rara vez se justifica en un prototipo de 48 horas \[I\].

## A. Telemetría en profundidad (Bloque III)

La oportunidad más clara en telemetría no está en recolectar más, sino en **medir la calidad, completitud y honestidad de la telemetría que ya existe**: feeds públicos con huecos, registros institucionales que se publican con demora, trazas de agentes sin semántica estable. La ausencia de una señal esperada es, en sí misma, un dato.

### Hallazgos documentados

- &#91;D\] **Huecos intencionales frente a huecos técnicos.** Global Fishing Watch y NOAA estimaron primero con qué frecuencia debería recibirse la señal AIS de cada barco y después clasificaron los huecos; identificaron más de 55.000 eventos sospechosos de apagado intencional entre 2017 y 2019, que ocultan hasta el 6% de la actividad pesquera ([Welch et al., *Science Advances* 2022](https://escholarship.org/content/qt3xs2q931/qt3xs2q931.pdf); [GFW](https://globalfishingwatch.org/?p=26412)). El estudio también muestra apagados legítimos, por ejemplo para evitar piratería. Es el modelo de referencia: tasa esperada de emisión, hueco observado, explicación alternativa explícita.
- &#91;D\] **Feeds públicos de baja calidad.** Una evaluación de 78 feeds GTFS-realtime encontró errores en 54 y advertencias en 58 ([NITC/CUTR](https://rosap.ntl.bts.gov/view/dot/37446/dot_37446_DS1.pdf)). Open Innovations encontró que hasta el 20% de las posiciones diarias del feed británico carecían de `trip_id`, y recuperó parte por orden temporal y agrupamiento por vehículo ([BODS forum](https://boduf.discourse.group/t/missing-trip-id-s-in-gtfs-rt-data/124)). Caltrans publica reportes mensuales de completitud por agencia ([Cal-ITP](https://reports.dds.dot.ca.gov/gtfs_schedule/2024/11/360/)).
- &#91;D\] **Telemetría de agentes inmadura.** A mediados de 2026, todos los atributos `gen_ai.*` de las convenciones semánticas de OpenTelemetry siguen en estado *Development*; en junio de 2026 (v1.42.0) se movieron a un repositorio propio, `semantic-conventions-genai`, sin releases etiquetados al momento del relevamiento ([dev.to, verificación contra el registro](https://dev.to/azena-ai/opentelemetrys-genai-semantic-conventions-are-not-stable-yet-heres-what-actually-shipped-in-2026-3mke); [Dash0](https://www.dash0.com/knowledge/opentelemetry-genai-semantic-conventions-explained)). Existen spans de `invoke_agent`, `execute_tool` y MCP, y métricas como cantidad de llamadas a herramientas y a modelo por ejecución. Hay fuentes secundarias que afirman lo contrario (que se estabilizaron); el atlas asume el estado *Development* y lo marca como pregunta abierta.
- &#91;D\] **Telemetría institucional con sesgo de selección.** Los promedios de respuesta FOIA de MuckRock reflejan solo los pedidos hechos por su plataforma ([MuckRock](https://www.muckrock.com/news/archives/2017/mar/14/muckrock-foia-response-data/)); en Argentina, los informes de acceso a la información se publican trimestralmente en PDF por organismo (ver sección anterior).
- &#91;D\] **Procedencia de medios.** C2PA firma metadatos de origen y edición, pero la mayoría de las plataformas los elimina al recodificar; según el Reuters Institute (citado por terceros), menos del 1% de las imágenes y videos de noticias publicados globalmente incluía C2PA, y un análisis formal sostiene que la especificación no cumple todas sus metas de seguridad ([SoftwareSeni, adopción 2026](https://www.softwareseni.com/c2pa-adoption-in-2026-hardware-platforms-and-verification-reality); [Rubin Lake, radar](https://rubinlake.com/en/technology-radar/ai-security-and-governance/digital-provenance)). Conclusión operativa \[I\]: la *ausencia* de credenciales no puede tratarse como indicio de falsedad.

### Tipología de pérdida de información en telemetría

| Tipo | Síntoma | Cómo se detecta \[C\] | Error interpretativo típico |
| --- | --- | --- | --- |
| Hueco de emisión | No llegan eventos en un intervalo | Tasa esperada por fuente; distribución de intervalos entre eventos | Leer el hueco como "no pasó nada" |
| Hueco de cobertura | El sensor existe pero el receptor no lo ve | Comparar con otra fuente de cobertura | Atribuir intención a una limitación técnica |
| Campo faltante | El evento llega incompleto | Tasa de nulos por campo y por emisor | Descartar filas y sesgar la muestra |
| Reordenamiento | Eventos fuera de orden | Relojes lógicos, número de secuencia | Inferir causalidad por orden de llegada |
| Deriva de reloj | Marcas de tiempo inconsistentes entre fuentes | Eventos de anclaje compartidos | Construir cronologías imposibles |
| Duplicación | Mismo evento contado varias veces | Claves idempotentes, hash de contenido | Inflar tasas |
| Publicación tardía | El dato existe pero se publica después | Diferencia entre fecha del hecho y fecha de publicación | Confundir latencia institucional con ausencia |
| Reescritura | Un registro cambia después de publicado | Hash por versión, cadena de versiones | Citar una versión que ya no existe |

### Principios de diseño adoptados

- **Datos reales o sintéticos rotulados**: cada demo declara qué parte del dataset es real, cuál es sintética y cómo se generó. Inyectar fallas conocidas sobre datos reales es preferible a inventar datos completos.
- **Minimización**: se registra lo necesario para la pregunta; nada de identificadores personales salvo que la pregunta lo requiera y haya base legal.
- **Retención explícita**: cada prototipo declara cuánto tiempo guarda qué.
- **Métricas no perversas**: se prefieren métricas de cobertura y calidad (completitud, latencia, consistencia) sobre métricas de rendimiento individual. Si una métrica puede convertirse en meta para quien es medido, se documenta cómo se la podría manipular (Campbell–Goodhart).
- **Anomalías interpretables**: una alerta debe traer su explicación y su alternativa benigna. Se descartan detectores que solo devuelven un puntaje.
- **Correlación ≠ causalidad**: la telemetría muestra co-ocurrencia temporal. Toda afirmación causal requiere un mecanismo y, si es posible, una intervención.

### Herramientas de base

| Herramienta | Uso | Estado |
| --- | --- | --- |
| OpenTelemetry (trazas, métricas, logs) \[C\] | Instrumentación estándar | Estable en lo general; GenAI en *Development* |
| [Timesketch](https://pypi.org/project/timesketch/20260617/) | Análisis colaborativo de líneas de tiempo forenses | Activo (release 2026) |
| [EDGI web-monitoring](https://github.com/edgi-govdata-archiving/web-monitoring) | Diff y anotación de cambios en páginas | Activo, orientado a EE.UU. |
| Validadores GTFS-RT de MobilityData \[D\] | Calidad de feeds de transporte | Usados por Cal-ITP |
| `ruptures` y detección de puntos de cambio \[C\] | Cambios estructurales en series | Librería Python madura |

Los tiempos de prototipo de las ideas T suponen OpenTelemetry Collector o, más simple, un esquema JSONL propio compatible con nombres OTel, para no atarse a un backend.

## B y C. Atlas de 60 oportunidades

Cada ficha cubre los 18 puntos pedidos en forma compacta; los campos "Dificultad" y "Tiempo" van juntos. La comparación con alternativas existentes (entregable C) está dentro de cada ficha, en "Alternativas" y "Diferenciación", porque separarla obligaba a leer cada idea dos veces. Las fuentes que respaldan la evidencia son las enlazadas en las secciones A; acá se repiten solo las específicas.

### Grafos (G01–G20)

#### G01 · Fuentes efectivamente independientes

- **Problema**: un dato parece confirmado por muchas notas, pero todas derivan de una sola fuente original.
- **Usuario y situación**: editora de verificación que debe decidir si una afirmación tiene "varias fuentes" antes de publicar.
- **Evidencia**: \[D\] el Protocolo de Berkeley trata la verificación como fase propia; \[I\] no encontré mediciones publicadas de este colapso de fuentes en medios argentinos.
- **Alternativas**: verificación manual; herramientas de difusión de enlaces (por ejemplo Media Cloud \[C\]) que muestran propagación, no independencia.
- **Diferenciación**: calcula el número máximo de caminos disjuntos en vértices entre la afirmación y fuentes primarias (teorema de Menger) en vez de contar menciones.
- **Datos**: enlaces salientes de notas públicas; un caso armado a mano con 15–30 notas.
- **Mecanismo**: grafo dirigido nota→fuente; flujo máximo con capacidad unitaria en vértices; corte mínimo como explicación.
- **Por qué grafo**: la independencia es una propiedad de caminos, no de filas.
- **MVP**: dado un conjunto de URLs, devuelve "fuentes independientes efectivas = k" y el corte que lo limita.
- **Demo**: caso público con anotación manual de dos verificadoras como referencia.
- **Métrica**: coincidencia exacta de k con la anotación en ≥80% de los casos.
- **Riesgos**: bajos; falsos positivos cuando una nota no enlaza su fuente.
- **Dificultad y tiempo**: media; 2–3 días.
- **Dependencias**: el MVP solo usa enlaces explícitos; citas sin link quedan fuera.
- **Falsación**: si en ≥70% de los casos las notas no enlazan sus fuentes, el grafo es demasiado incompleto.
- **Novedad**: B.

#### G02 · Radio de impacto normativo

- **Problema**: al modificarse una norma no es evidente qué otras quedan afectadas indirectamente ni qué modificaciones apuntan a normas ya derogadas.
- **Usuario y situación**: analista legislativa que evalúa el impacto de una ley ómnibus o un DNU.
- **Evidencia**: \[D\] InfoLEG publica normas, modificadas y modificatorias en abierto; \[D\] ejercicio previo en Neo4j (Olmos).
- **Alternativas**: consulta norma a norma en InfoLEG o SAIJ; texto actualizado disponible solo para algunas normas \[C\].
- **Diferenciación**: consultas transitivas y acotadas en el tiempo, detección de ciclos y de modificaciones sobre normas ya derogadas.
- **Datos**: bases InfoLEG (zip abierto).
- **Mecanismo**: DAG temporal, clausura transitiva por fecha, recorrido inverso, detección de ciclos.
- **Por qué grafo**: dependencia transitiva de longitud variable.
- **MVP**: `impacto <norma> --desde --hasta`.
- **Demo**: cascada de una ley ómnibus conocida.
- **Métrica**: precisión de relaciones sobre 50 aristas auditadas a mano.
- **Riesgos**: bajos; confundir modificación con derogación.
- **Dificultad y tiempo**: baja-media; 1–2 días.
- **Dependencias**: tipología de relaciones del esquema InfoLEG (a verificar).
- **Falsación**: si más del 20% de una muestra auditada tiene relaciones faltantes, el radio engaña.
- **Novedad**: D.

#### G03 · Recableado de proveedores tras cambio de gestión

- **Problema**: no hay una medición pública y replicable de cuánto cambiaron las redes comprador–proveedor del Estado nacional tras diciembre de 2023.
- **Usuario y situación**: periodista de datos o investigadora de una ONG anticorrupción.
- **Evidencia**: \[D\] Fazekas y Wachs (2020) midieron re-cableado de 20–40% mayor en compradores de alto riesgo tras cambios de gobierno; \[D\] datasets de adjudicaciones COMPR.AR.
- **Alternativas**: tableros por monto; Cardinal calcula indicadores por proceso, no por red.
- **Diferenciación**: adapta una métrica validada a Argentina con baseline explícita (años sin cambio de gobierno).
- **Datos**: adjudicaciones COMPR.AR por año, CUIT de proveedores, unidad compradora.
- **Mecanismo**: grafos bipartitos anuales; Jaccard del vecindario de cada comprador entre años; bootstrap.
- **Por qué grafo**: la unidad de análisis es el vecindario.
- **MVP**: tabla de compradores con tasa de re-cableado e intervalo.
- **Demo**: 2021→22 y 2022→23 (baseline) frente a 2023→24.
- **Métrica**: diferencia respecto de la baseline estable ante remuestreo.
- **Riesgos**: re-cablear no prueba corrupción; puede ser política legítima. Lenguaje descriptivo obligatorio.
- **Dificultad y tiempo**: media; 2–3 días.
- **Dependencias**: emparejar unidades compradoras tras reestructuraciones de ministerios (riesgo alto).
- **Falsación**: si la reestructuración impide emparejar compradores, la métrica mide reorganización y no re-cableado.
- **Novedad**: D.

#### G04 · Fragilidad de conclusiones ante coincidencias dudosas

- **Problema**: los informes que afirman "X está a dos pasos de Y" no muestran cuánto depende eso de una coincidencia de nombres incierta.
- **Usuario y situación**: periodista de datos que publica un grafo de vínculos societarios.
- **Evidencia**: \[D\] OpenSanctions fusiona por componentes conexos sobre juicios de match; \[D\] Splink produce probabilidades; \[I\] no encontré herramienta que propague esa incertidumbre a la conclusión final.
- **Alternativas**: revisión manual; tableros de clusters de Splink.
- **Diferenciación**: barrido de umbrales y reporte de "conclusiones que sobreviven".
- **Datos**: muestra FtM de OpenSanctions o registros sintéticos rotulados.
- **Mecanismo**: aristas de match con probabilidad; componentes por umbral; estabilidad de cada camino consultado.
- **Por qué grafo**: la transitividad del match es la fuente del error.
- **MVP**: para una lista de preguntas "¿A conectado con B?", tabla de estabilidad.
- **Demo**: dataset con errores sembrados; una conclusión llamativa que se cae.
- **Métrica**: detecta ≥90% de conclusiones que dependen de matches sembrados como falsos.
- **Riesgos**: con personas físicas exige cuidado; la demo usa entidades jurídicas o sintéticas.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: ninguna fuerte.
- **Falsación**: si en datos reales todas (o ninguna) de las conclusiones son estables, no discrimina.
- **Novedad**: B.

#### G05 · Marco de contradicciones en cronologías

- **Problema**: al cruzar testimonios, comunicados y registros de un hecho, las contradicciones se detectan a ojo y no se sabe qué conjuntos de afirmaciones son consistentes entre sí.
- **Usuario y situación**: investigadora de una misión de determinación de hechos.
- **Evidencia**: \[D\] Berkeley Protocol (verificación y análisis); \[I\] TimeMap y Timesketch visualizan pero no resuelven consistencia.
- **Alternativas**: [TimeMap](https://github.com/forensic-architecture/timemap), Timesketch, planillas.
- **Diferenciación**: formaliza afirmaciones (actor, lugar, intervalo) y calcula conjuntos máximos consistentes.
- **Datos**: afirmaciones extraídas a mano de un caso público cerrado.
- **Mecanismo**: grafo de ataque entre afirmaciones incompatibles (marco de Dung); álgebra de intervalos de Allen; MaxSAT para subconjuntos máximos.
- **Por qué grafo**: la consistencia es propiedad del grafo de conflictos.
- **MVP**: JSONL de afirmaciones → conflictos y 2–3 versiones consistentes.
- **Demo**: caso histórico con versiones oficiales contradictorias documentadas.
- **Métrica**: reproduce las contradicciones señaladas en el informe final del caso.
- **Riesgos**: exponer testigos; solo fuentes ya publicadas.
- **Dificultad y tiempo**: media-alta; 3 días.
- **Dependencias**: formalización manual de afirmaciones.
- **Falsación**: si formalizar un caso real lleva más tiempo que analizarlo a mano, no aporta.
- **Novedad**: B.

#### G06 · Puntos únicos de falla en el soporte probatorio

- **Problema**: algunas conclusiones de un informe se apoyan en una sola pieza de evidencia sin que el equipo lo sepa.
- **Usuario y situación**: revisora legal de un informe de ONG antes de publicarlo.
- **Evidencia**: \[D\] estándares probatorios de Berkeley; \[I\] práctica de revisión legal pre-publicación.
- **Alternativas**: revisión manual; Uwazi registra relaciones pero no calcula cortes.
- **Diferenciación**: corte mínimo entre cada conclusión y la evidencia primaria; ranking de evidencias críticas.
- **Datos**: ledger del propio equipo (afirmación→evidencia→fuente).
- **Mecanismo**: grafo en capas, flujo máximo, puntos de articulación.
- **Por qué grafo**: "depende de una sola pieza" es un corte.
- **MVP**: CLI sobre YAML de afirmaciones.
- **Demo**: informe ficticio con 20 conclusiones, algunas con soporte único sembrado.
- **Métrica**: identifica el 100% de los soportes únicos sembrados.
- **Riesgos**: bajos; datos internos.
- **Dificultad y tiempo**: baja; 1–2 días.
- **Dependencias**: que el equipo mantenga el ledger.
- **Falsación**: si crear el ledger cuesta más que revisar a mano, no se adopta.
- **Novedad**: C.

#### G07 · Bus factor de la infraestructura cívica

- **Problema**: organizaciones de DD.HH. y periodismo dependen de herramientas abiertas mantenidas por muy pocas personas u organizaciones.
- **Usuario y situación**: responsable técnica de una ONG o un financiador que decide qué adoptar o financiar.
- **Evidencia**: \[D\] cierre del desarrollo abierto de Aleph y fork OpenAleph; \[D\] el Criticality Score de OpenSSF mide actividad, no criticidad ([OpenSSF](https://openssf.org/?p=3208)).
- **Alternativas**: OpenSSF Scorecard, deps.dev, repo-trust.
- **Diferenciación**: grafo de dependencias de un stack cívico concreto, ponderado por concentración de mantenimiento, con puntos de articulación.
- **Datos**: manifiestos de dependencias, APIs de GitHub y deps.dev.
- **Mecanismo**: clausura transitiva de dependencias; Gini de commits; articulación ponderada.
- **Por qué grafo**: el riesgo se hereda transitivamente.
- **MVP**: reporte por herramienta con dependencias críticas de mantenimiento concentrado.
- **Demo**: Uwazi y Timesketch.
- **Métrica**: backtest contra paquetes que efectivamente fueron abandonados.
- **Riesgos**: bajos; reportar por paquete, no por persona.
- **Dificultad y tiempo**: media; 2–3 días.
- **Dependencias**: límites de API.
- **Falsación**: si el backtest no supera a "días desde el último commit", no aporta.
- **Novedad**: D.

#### G08 · Flujos institucionales de puertas giratorias

- **Problema**: no hay una vista agregada de qué organismos reciben y entregan funcionarios hacia qué sectores privados en el tiempo.
- **Usuario y situación**: investigadora en sociología política (tránsito entre campos en sentido de Bourdieu).
- **Evidencia**: \[D\] la OA mantiene el registro MAPPAP de actividades anteriores y posteriores; \[I\] no verifiqué formato ni acceso masivo.
- **Alternativas**: estudios académicos de élites caso a caso \[C\].
- **Diferenciación**: solo flujos agregados organismo↔sector, sin trayectorias individuales.
- **Datos**: MAPPAP (a verificar), DDJJ.
- **Mecanismo**: grafo bipartito temporal; supresión de celdas pequeñas (k-anonimato en aristas).
- **Por qué grafo**: flujos entre nodos institucionales en el tiempo.
- **MVP**: matriz de flujos con celdas menores a 5 suprimidas.
- **Demo**: sintética si el registro no es descargable.
- **Métrica**: flujos interpretables que sobreviven a la supresión.
- **Riesgos**: altos; reidentificación por desagregación.
- **Dificultad y tiempo**: alta; incierto.
- **Dependencias**: acceso masivo al MAPPAP (bloqueante).
- **Falsación**: si tras la supresión no quedan flujos interpretables.
- **Novedad**: D, condicionada.

#### G09 · Caminos honestos entre entidades

- **Problema**: los grafos societarios fabrican vínculos espurios a través de domicilios de estudios contables o apoderados compartidos por miles de sociedades.
- **Usuario y situación**: periodista que pregunta "¿cómo se conecta A con B?".
- **Evidencia**: \[D\] IGJ publica domicilios y autoridades; \[D\] agregadores argentinos ya muestran grafos persona–empresa; \[C\] los domicilios masivos son un problema conocido en registros societarios.
- **Alternativas**: indicadores.ar, Socios.red, `shortestPath` de Neo4j.
- **Diferenciación**: penaliza intermediarios de grado alto, devuelve varios caminos con costo y fuente por arista, y explica por qué descartó los que pasan por hubs.
- **Datos**: IGJ (domicilios, autoridades).
- **Mecanismo**: k caminos más cortos con costo log(grado) del intermediario.
- **Por qué grafo**: la pregunta es literalmente un camino.
- **MVP**: CLI con caminos justificados.
- **Demo**: un camino "sensacional" vía un estudio contable que la herramienta degrada.
- **Métrica**: proporción de caminos top-5 que una investigadora juzga informativos frente al camino más corto ingenuo.
- **Riesgos**: medios; autoridades societarias son personas físicas.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: descarga completa de IGJ.
- **Falsación**: si la evaluación manual no prefiere los caminos ponderados.
- **Novedad**: C.

#### G10 · Retracciones de segundo orden

- **Problema**: un informe de política pública cita estudios que se apoyan en papers retractados.
- **Usuario y situación**: analista que revisa un informe ministerial o de organismo internacional.
- **Evidencia**: \[D\] la base de Retraction Watch es abierta vía Crossref desde 2023 y superaba las 43.000 retracciones ([Retraction Watch](https://retractionwatch.com/2023/09/16/weekend-reads-crossref-acquires-the-retraction-watch-database-italy-ministers-papers-scrutinized-carlo-croce-goes-to-court-yet-again/)).
- **Alternativas**: gestores bibliográficos que marcan citas directas retractadas \[C\].
- **Diferenciación**: exposición a profundidad 2–3 en el grafo de citas.
- **Datos**: Crossref (incluye Retraction Watch), OpenAlex \[C\].
- **Mecanismo**: BFS acotado en el DAG de citas.
- **Por qué grafo**: dependencia transitiva.
- **MVP**: dado un listado de DOIs, reporte de exposición por profundidad.
- **Demo**: informe público con bibliografía extensa.
- **Métrica**: tasa de falsos positivos en revisión manual.
- **Riesgos**: no confundir exposición con error del autor.
- **Dificultad y tiempo**: baja-media; 2 días.
- **Dependencias**: cobertura de referencias en Crossref/OpenAlex.
- **Falsación**: si casi todo informe muestra exposición de segundo orden, la señal no discrimina.
- **Novedad**: C.

#### G11 · Aliados y competidores

- **Problema**: empresas que se presentan juntas en consorcios en unas licitaciones y como competidoras en otras pueden simular competencia.
- **Usuario y situación**: auditora u ONG anticorrupción.
- **Evidencia**: \[D\] la OCDE estudió colusión en obra pública argentina (citado en el Cuarto Plan de Gobierno Abierto, [documento](https://www.infoem.org.mx/doc/biblioteca/accesoytrans/accesinf/APERTURA%20DE%20INFORMACI%C3%93N%20EN%20EL%20SISTEMA%20DE%20CONTRATACIONES%20DE%20OBRA%20P%C3%9ABLICA.pdf)); \[D\] la guía de red flags de OCP incluye colusión.
- **Alternativas**: indicadores por proceso de Cardinal.
- **Diferenciación**: grafo con signo (alianza +, competencia −), triadas desbalanceadas y rotación de ganadores dentro de grupos.
- **Datos**: oferentes por proceso (COMPR.AR / CONTRAT.AR) — verificar que se publican todos, no solo adjudicatarios.
- **Mecanismo**: balance estructural; secuencias de ganadores por grupo.
- **Por qué grafo**: el patrón es relacional por definición.
- **MVP**: pares y grupos con relación mixta y su historial.
- **Demo**: datos reales o, si faltan oferentes, OCDS de otra jurisdicción.
- **Métrica**: recupera casos sembrados; compara con casos sancionados si los hay públicos.
- **Riesgos**: medios-altos; señala empresas. Lenguaje de "patrón a revisar".
- **Dificultad y tiempo**: media; 3 días.
- **Dependencias**: lista completa de oferentes (bloqueante).
- **Falsación**: si la relación mixta aparece en la mayoría de pares del mercado.
- **Novedad**: B.

#### G12 · Leyes sin reglamentar

- **Problema**: leyes que requieren reglamentación quedan años sin decreto y la demora no se mide de forma sistemática.
- **Usuario y situación**: periodista legislativa.
- **Evidencia**: \[D\] InfoLEG registra relaciones entre normas; \[I\] la relación "reglamenta" debe verificarse.
- **Alternativas**: seguimientos manuales de ONG legislativas \[C\].
- **Diferenciación**: cálculo continuo con curvas de supervivencia.
- **Datos**: InfoLEG.
- **Mecanismo**: Kaplan–Meier hasta la reglamentación.
- **Por qué grafo**: débil; es casi un `JOIN`.
- **MVP**: leyes vigentes sin reglamentar con días transcurridos.
- **Demo**: últimos diez años.
- **Métrica**: precisión sobre 30 leyes verificadas.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja; 1 día.
- **Dependencias**: saber qué leyes requieren reglamentación (difícil de automatizar).
- **Falsación**: si no se puede determinar qué leyes la requieren.
- **Novedad**: D.

#### G13 · Linaje de una cifra oficial

- **Problema**: una cifra en un comunicado no indica de qué dataset ni de qué versión sale, y los recursos se reemplazan sin versionado.
- **Usuario y situación**: periodista de datos que verifica una cifra.
- **Evidencia**: \[D\] compromiso AR0107 sobre calidad de datos; \[C\] CKAN registra fechas de modificación.
- **Alternativas**: Wayback; verificación manual.
- **Diferenciación**: grafo PROV cifra→dataset→recurso→versión con hash, que marca dónde se rompe la cadena.
- **Datos**: metadatos CKAN de datos.gob.ar.
- **Mecanismo**: PROV-O, snapshots con hash, recálculo.
- **Por qué grafo**: linaje multinivel.
- **MVP**: verificador que recalcula una cifra desde un recurso y registra su procedencia.
- **Demo**: una cifra de comunicado reproducida desde el CSV.
- **Métrica**: proporción de cifras de una muestra que resultan reproducibles.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: que el organismo publique los datos de base.
- **Falsación**: si casi ninguna cifra puede vincularse a un recurso (aunque eso ya es un hallazgo).
- **Novedad**: C.

#### G14 · Comunidades que sobreviven a la perturbación

- **Problema**: se publican "comunidades" detectadas en redes sin verificar si son estables o artefactos del algoritmo.
- **Usuario y situación**: investigadora social o periodista que publica análisis de redes.
- **Evidencia**: \[C\] inestabilidad de Louvain/Leiden ante semillas y resolución; \[D\] Catlin et al. sobre sensibilidad a faltantes.
- **Alternativas**: clustering de consenso en librerías académicas \[C\].
- **Diferenciación**: reporte listo para publicación con comunidades robustas y nodos ambiguos.
- **Datos**: cualquier red pública.
- **Mecanismo**: remuestreo de aristas, múltiples corridas de Leiden, matriz de co-asignación.
- **Por qué grafo**: problema de grafos puro.
- **MVP**: CLI que recibe una lista de aristas y devuelve robustez.
- **Demo**: red real y la misma con ruido.
- **Métrica**: recupera comunidades plantadas en grafos sintéticos LFR y descarta las espurias.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja-media; 1–2 días.
- **Dependencias**: ninguna.
- **Falsación**: si en redes reales coincide siempre con una corrida simple.
- **Novedad**: C.

#### G15 · Propiedad parcialmente observada

- **Problema**: los grafos de propiedad presentan como completos datos que en Argentina no lo son, porque el registro no publica accionistas de sociedades anónimas.
- **Usuario y situación**: investigadora de beneficiarios finales.
- **Evidencia**: \[D\] la IGJ no lleva registro de accionistas de SA; \[D\] BODS modela declaraciones con su fuente.
- **Alternativas**: BODS como modelo; OpenOwnership.
- **Diferenciación**: aristas observadas, declaradas por terceros y desconocidas (hueco explícito); cálculo de qué cadenas de control son verificables.
- **Datos**: IGJ, edictos del Boletín Oficial, registros extranjeros abiertos.
- **Mecanismo**: grafo con atributo de certeza; caminos con costo de incertidumbre.
- **Por qué grafo**: control indirecto.
- **MVP**: modelo de datos y visualización de huecos para un caso.
- **Demo**: caso sintético rotulado y un caso real público.
- **Métrica**: exactitud del cálculo de cadenas verificables; comprensión evaluada con tres usuarias.
- **Riesgos**: medios; socios personas físicas.
- **Dificultad y tiempo**: alta; 3–4 días.
- **Dependencias**: edictos parseables.
- **Falsación**: si en todo caso real los huecos dominan y el modelo solo dice "no se sabe".
- **Novedad**: A/D.

#### G16 · Doctrina abandonada

- **Problema**: no se sabe cuándo un precedente de la Corte Suprema deja de citarse, señal posible de cambio doctrinario no declarado.
- **Usuario y situación**: investigadora en derecho o periodista judicial.
- **Evidencia**: \[C\] el análisis de redes de citas judiciales es una línea académica establecida; \[I\] no verifiqué acceso masivo a fallos de la CSJN.
- **Alternativas**: buscadores jurídicos comerciales.
- **Diferenciación**: detección temporal de caída de citas contra una baseline de decaimiento normal.
- **Datos**: fallos de la CSJN (acceso y licencia a verificar).
- **Mecanismo**: grafo de citas temporal; detección de puntos de cambio por precedente.
- **Por qué grafo**: citas dirigidas en el tiempo.
- **MVP**: precedentes con caída abrupta en un tema acotado.
- **Demo**: un tema con cambio doctrinario reconocido.
- **Métrica**: concordancia con cambios señalados por la doctrina.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: alta; 4 días o más.
- **Dependencias**: corpus (bloqueante).
- **Falsación**: si las caídas coinciden con cambios de redacción o de base y no de doctrina.
- **Novedad**: D.

#### G17 · Trayectoria de expedientes en el Boletín Oficial

- **Problema**: los actos administrativos se publican aislados, aunque varios comparten expediente y se citan en sus "VISTO"; reconstruir la trayectoria de una decisión es manual.
- **Usuario y situación**: periodista o abogada que sigue una decisión estatal.
- **Evidencia**: \[D\] los actos citan expedientes con identificador estable (por ejemplo, la resolución de la AAIP que cita el EX-2024-27723894-APN-AAIP, [Boletín Oficial](https://www.boletinoficial.gob.ar/detalleAviso/primera/305397/1)); \[C\] Weber: dominación por expediente.
- **Alternativas**: buscador del Boletín por texto.
- **Diferenciación**: grafo acto–expediente–norma que reconstruye la cadena completa.
- **Datos**: primera sección del Boletín Oficial.
- **Mecanismo**: extracción por expresiones regulares de expedientes y normas citadas; componentes por expediente.
- **Por qué grafo**: vínculos de longitud variable entre actos.
- **MVP**: dado un expediente o un acto, devuelve la cadena ordenada.
- **Demo**: una política con varios actos encadenados.
- **Métrica**: recall frente a una reconstrucción manual.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: acceso masivo y términos de uso del Boletín.
- **Falsación**: si la mayoría de actos no reutiliza expedientes, los componentes son triviales.
- **Novedad**: A/D.

#### G18 · Intermediarios en el registro de audiencias

- **Problema**: consultoras y estudios que gestionan intereses para múltiples representados ante múltiples organismos son difíciles de ver.
- **Usuario y situación**: ONG de transparencia.
- **Evidencia**: \[D\] registro abierto; \[D\] subregistro documentado por Chequeado.
- **Alternativas**: lectura del registro; notas periodísticas.
- **Diferenciación**: índice de intermediación (restricción de Burt) por organización, con intervalo ante subregistro.
- **Datos**: registro de audiencias (verificar campo de representado).
- **Mecanismo**: grafo solicitante–representado–organismo; restricción de Burt; intermediación bajo perturbación.
- **Por qué grafo**: la intermediación es estructural.
- **MVP**: ranking de organizaciones intermediarias con intervalos.
- **Demo**: datos reales.
- **Métrica**: concordancia con intermediarios ya identificados por investigaciones publicadas.
- **Riesgos**: medios; filtrar a personas jurídicas.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: campo de representación presente y confiable.
- **Falsación**: si el campo está vacío en la mayoría de registros.
- **Novedad**: D.

#### G19 · Coherencia temporal de cargos en Wikidata

- **Problema**: los datos de cargos públicos en Wikidata contienen superposiciones y sucesiones incoherentes que se propagan a aplicaciones que los consumen.
- **Usuario y situación**: editora de Wikimedia o verificadora.
- **Evidencia**: \[C\] Wikidata tiene restricciones de propiedades con soporte temporal limitado; \[I\] no medí la tasa de error en cargos argentinos.
- **Alternativas**: reportes de restricciones de Wikidata; consultas SPARQL ad hoc.
- **Diferenciación**: verificación de un titular por cargo y período, y de coherencia bidireccional de sucesiones.
- **Datos**: Wikidata.
- **Mecanismo**: grafos de intervalos; superposición; cadenas de sucesión.
- **Por qué grafo**: la sucesión es una cadena con coherencia en ambos sentidos.
- **MVP**: reporte de inconsistencias para cargos nacionales.
- **Demo**: lista con enlaces a ítems y corrección sugerida.
- **Métrica**: precisión sobre 50 reportes verificados.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja; 1 día.
- **Dependencias**: ninguna.
- **Falsación**: si la tasa de error es ínfima.
- **Novedad**: C.

#### G20 · Priorización de preservación por criticidad

- **Problema**: con recursos limitados, un archivo de DD.HH. no sabe qué contenido preservar primero.
- **Usuario y situación**: archivista de una organización de documentación.
- **Evidencia**: \[D\] borrados masivos documentados por Mnemonic; \[D\] tasas de desaparición diferenciales (Pew).
- **Alternativas**: archivar todo con herramientas como el Auto Archiver de Bellingcat \[C\]; priorizar a mano.
- **Diferenciación**: prioriza evidencias cuya pérdida deja conclusiones sin soporte, ponderadas por el riesgo de remoción de cada plataforma.
- **Datos**: ledger del equipo y tasas de remoción (ver T08).
- **Mecanismo**: cortes con pesos; esperanza de pérdida de soporte.
- **Por qué grafo**: dependencia de soporte.
- **MVP**: cola de preservación ordenada con justificación.
- **Demo**: colección ficticia rotulada.
- **Métrica**: soporte retenido bajo un presupuesto fijo de capturas frente al orden cronológico.
- **Riesgos**: bajos-medios.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: tasas de remoción estimadas.
- **Falsación**: si la cola coincide con "archivar lo más reciente primero".
- **Novedad**: B.

### Telemetría (T01–T15)

#### T01 · Deriva de contenido detrás de las citas

- **Problema**: las citas de un informe publicado siguen respondiendo, pero el contenido detrás cambió o fue reemplazado, y nadie se entera.
- **Usuario y situación**: equipo de una ONG o redacción que mantiene informes publicados como referencia.
- **Evidencia**: \[D\] Pew: decaimiento de enlaces; \[I\] el caso de contenido reescrito con respuesta 200 no aparece en esas mediciones, que cuentan inaccesibilidad.
- **Alternativas**: verificadores de enlaces rotos; Wayback Machine manual; servicios comerciales de cambio de páginas.
- **Diferenciación**: mide deriva semántica y estructural por cita, contrasta con la captura en el momento de la publicación y distingue "caído", "redirigido", "reescrito" y "estable".
- **Datos**: URLs citadas por informes públicos; capturas de la Wayback Machine en la fecha de publicación.
- **Mecanismo**: sondeo periódico; normalización de HTML; similitud por shingles y por estructura; clasificación por reglas.
- **Por qué telemetría**: es un proceso en curso cuyo estado solo se conoce por sondeo periódico.
- **MVP**: dado un PDF o lista de URLs con fecha, tabla de estado por cita.
- **Demo**: un informe de 2018–2020 con 100+ citas.
- **Métrica**: precisión de la clase "reescrito" sobre 50 casos revisados a mano.
- **Riesgos**: bajos; respetar robots y tasas.
- **Dificultad y tiempo**: baja-media; 2 días.
- **Dependencias**: disponibilidad de capturas históricas.
- **Falsación**: si los cambios detectados son casi todos cosméticos (menús, banners) incluso tras normalizar.
- **Novedad**: C.

#### T02 · Latido esperado de datasets oficiales

- **Problema**: datasets que declaran actualización mensual dejan de actualizarse sin aviso.
- **Usuario y situación**: periodista de datos o equipo que evalúa calidad de datos abiertos (compromiso AR0107).
- **Evidencia**: \[D\] AR0107 reconoce baja calidad de publicación; \[C\] los catálogos DCAT/CKAN declaran periodicidad (`accrualPeriodicity`) y fecha de modificación.
- **Alternativas**: indicadores de datos.gob.ar; revisión manual.
- **Diferenciación**: compara periodicidad declarada con cadencia observada y emite estados (al día, atrasado, silencioso) con historial.
- **Datos**: API CKAN de datos.gob.ar y nodos.
- **Mecanismo**: tasa esperada por dataset; intervalo entre modificaciones; detección de silencio.
- **Por qué telemetría**: "no hubo actualización" solo se observa midiendo en el tiempo.
- **MVP**: tablero de datasets silenciosos con historia de 90 días.
- **Demo**: catálogo nacional real.
- **Métrica**: proporción de alertas confirmadas al revisar el recurso real (no solo el metadato).
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja; 1–2 días.
- **Dependencias**: que la fecha de modificación del metadato refleje cambios reales.
- **Falsación**: si los metadatos se actualizan sin cambios de contenido (o al revés) de forma generalizada, hay que medir el recurso y no el metadato.
- **Novedad**: D.

#### T03 · Huecos del tiempo real de colectivos en CABA

- **Problema**: no hay una medición pública de cuánto falta en el feed de tiempo real de colectivos y dónde se concentran los huecos.
- **Usuario y situación**: organización de usuarios de transporte o accesibilidad que necesita saber si la información en tiempo real es confiable en ciertos barrios.
- **Evidencia**: \[D\] la API de transporte de la Ciudad expone datos GTFS y en tiempo real con registro de credenciales ([portal](https://anypoint.mulesoft.com/exchange/portals/api-gcba/083c0681-d272-40f7-b1ff-90dd5952a0de/api-plataforma-datos-transporte/)); \[D\] estudios de calidad GTFS-RT en otros países (NITC, Open Innovations, Cal-ITP).
- **Alternativas**: validadores de MobilityData (validan formato, no completitud por zona).
- **Diferenciación**: completitud por línea, hora y zona; huecos clasificados como técnicos (feed caído para todos) o localizados.
- **Datos**: posiciones de vehículos muestreadas cada minuto durante una semana; GTFS estático.
- **Mecanismo**: tasa esperada según viajes programados; huecos por vehículo; agregación espacial.
- **Por qué telemetría**: es medición de un feed vivo.
- **MVP**: mapa de completitud por línea y franja horaria.
- **Demo**: una semana de muestreo real.
- **Métrica**: estabilidad de los indicadores entre días; concordancia con observación en parada (muestra chica).
- **Riesgos**: bajos; no involucra pasajeros.
- **Dificultad y tiempo**: media; 2 días más una semana de recolección previa.
- **Dependencias**: credenciales de la API (bloqueante si se demoran).
- **Falsación**: si la completitud es uniforme y alta, el problema no existe en esta ciudad.
- **Novedad**: D.

#### T04 · Patologías de agentes desde telemetría estándar

- **Problema**: los agentes de IA entran en bucles o "deliberan sin actuar", y se detecta tarde, por costo o por quejas.
- **Usuario y situación**: desarrolladora que opera agentes con herramientas.
- **Evidencia**: \[D\] convenciones GenAI de OTel con métricas de llamadas a herramientas y a modelo por ejecución, aún en *Development*; \[D\] la razón entre ambas se señala como síntoma temprano de bucles (Dash0).
- **Alternativas**: plataformas de observabilidad de LLM (Langfuse, Phoenix y otras \[C\]).
- **Diferenciación**: clasificador determinista de patologías (bucle de reintentos, deliberación sin acción, herramienta repetida con mismos argumentos) con benchmark de fallas sembradas y explicación por regla.
- **Datos**: trazas de agentes propios con fallas inyectadas, rotuladas como sintéticas.
- **Mecanismo**: reglas sobre secuencias de spans; n-gramas de llamadas; detección de ciclos en la secuencia.
- **Por qué telemetría**: trazas de proceso.
- **MVP**: CLI que lee JSONL estilo OTel y devuelve diagnósticos.
- **Demo**: diez corridas, tres con patologías sembradas.
- **Métrica**: precisión y exhaustividad sobre las patologías sembradas; falsos positivos en corridas sanas.
- **Riesgos**: las trazas pueden contener datos sensibles de prompts; minimizar.
- **Dificultad y tiempo**: baja-media; 2 días.
- **Dependencias**: inestabilidad de las convenciones.
- **Falsación**: si un umbral simple de "cantidad de pasos" detecta lo mismo.
- **Novedad**: C.

#### T05 · Bitácora de decisiones de agentes con cadena de hashes

- **Problema**: cuando un agente ejecuta acciones con efectos, no queda un registro verificable de qué se autorizó, quién y con qué entrada.
- **Usuario y situación**: auditora de un despliegue de agentes en una organización.
- **Evidencia**: \[D\] trazas OTel existen pero no son evidencia a prueba de alteraciones; \[C\] cadenas de hash y registros solo-anexión son técnicas conocidas.
- **Alternativas**: logs de plataforma; registros de transparencia generales \[C\].
- **Diferenciación**: cada llamada a herramienta con efectos se sella con hash de entrada, salida, política aplicada y aprobación humana; verificación offline.
- **Datos**: trazas propias.
- **Mecanismo**: cadena de hashes por sesión; anclaje periódico opcional.
- **Por qué telemetría**: es instrumentación de decisiones.
- **MVP**: wrapper de herramientas que escribe la bitácora y un verificador que detecta inserciones, borrados y reordenamientos.
- **Demo**: alterar una línea y mostrar el fallo de verificación.
- **Métrica**: detección del 100% de alteraciones sembradas de tres tipos.
- **Riesgos**: la bitácora concentra datos sensibles.
- **Dificultad y tiempo**: baja; 1–2 días.
- **Dependencias**: ninguna.
- **Falsación**: si el despliegue real no tiene una frontera clara de "acciones con efectos", la bitácora registra ruido.
- **Novedad**: C.

#### T06 · Plazos de acceso a la información como series temporales

- **Problema**: los informes de cumplimiento de la Ley 27.275 se publican en PDF por organismo y período, lo que impide comparar plazos en el tiempo.
- **Usuario y situación**: ONG de transparencia o periodista que pregunta si un organismo empeoró.
- **Evidencia**: \[D\] obligación de reportar plazos; informes trimestrales en PDF (Consejo de la Magistratura); sistema de seguimiento de la AAIP (Res. 148/2025).
- **Alternativas**: tablero de la AAIP (si es público y abarca a todos los sujetos obligados).
- **Diferenciación**: series comparables entre poderes y organismos que no están en el mismo sistema, con detección de cambios.
- **Datos**: PDFs de informes públicos.
- **Mecanismo**: extracción de tablas; normalización; detección de puntos de cambio.
- **Por qué telemetría**: medición periódica de un proceso institucional.
- **MVP**: series de dos o tres organismos con cambios marcados.
- **Demo**: Consejo de la Magistratura 2017–2025.
- **Métrica**: exactitud de extracción frente a carga manual.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja-media; 2 días.
- **Dependencias**: heterogeneidad de formatos.
- **Falsación**: si la AAIP ya publica estas series completas y abiertas, la idea se reduce a un visor.
- **Novedad**: D.

#### T07 · Silencios en el registro de audiencias

- **Problema**: la caída abrupta de audiencias registradas por un organismo puede indicar subregistro, pero nadie la monitorea.
- **Usuario y situación**: ONG de transparencia.
- **Evidencia**: \[D\] subregistro documentado (Chequeado); \[D\] nota de *El Cronista* sobre el bajo uso del registro.
- **Alternativas**: lectura manual.
- **Diferenciación**: modelo de cadencia esperada por organismo y alerta de silencio con contexto (cambios de autoridades, feriados).
- **Datos**: dataset del registro.
- **Mecanismo**: procesos de conteo con estacionalidad; detección de puntos de cambio.
- **Por qué telemetría**: la ausencia es la señal.
- **MVP**: lista de organismos con silencios anómalos.
- **Demo**: series históricas.
- **Métrica**: proporción de silencios explicables por cambio de gestión frente a no explicados.
- **Riesgos**: medios; los titulares son funcionarios públicos, se informa por organismo.
- **Dificultad y tiempo**: baja; 1–2 días.
- **Dependencias**: frecuencia de actualización del dataset.
- **Falsación**: si el dataset se publica con tanto retraso que el silencio es artefacto de publicación.
- **Novedad**: D.

#### T08 · Curvas de supervivencia de contenido de interés público

- **Problema**: no hay medición abierta y continua de cuánto tiempo sobrevive en cada plataforma el contenido citado por informes de DD.HH.
- **Usuario y situación**: investigadora de moderación de contenido o archivo de DD.HH.
- **Evidencia**: \[D\] Pew: tuits en turco y árabe desaparecían más (dato secundario); \[D\] Lost & Found de Mnemonic.
- **Alternativas**: estudios puntuales; Lost & Found.
- **Diferenciación**: curvas Kaplan–Meier abiertas por plataforma, idioma y tipo de contenido sobre un conjunto público de URLs.
- **Datos**: URLs citadas en informes públicos de ONG y organismos.
- **Mecanismo**: sondeo periódico; análisis de supervivencia con censura.
- **Por qué telemetría**: tiempo hasta un evento observado por sondeo.
- **MVP**: curvas iniciales con 6 meses retrospectivos usando fechas de captura de Wayback.
- **Demo**: informes de dos organizaciones.
- **Métrica**: intervalos de confianza estrechos para al menos dos plataformas.
- **Riesgos**: medios; no descargar contenido sensible, solo estado.
- **Dificultad y tiempo**: media; 2–3 días.
- **Dependencias**: plataformas que no distinguen "borrado" de "requiere login".
- **Falsación**: si las respuestas de las plataformas no permiten distinguir borrado de bloqueo.
- **Novedad**: C.

#### T09 · Completitud de capturas web como evidencia

- **Problema**: una captura web parece completa pero le faltan recursos cargados por JavaScript, imágenes o comentarios, y eso se descubre cuando se necesita.
- **Usuario y situación**: investigadora OSINT que preserva páginas según el Protocolo de Berkeley.
- **Evidencia**: \[D\] preservación como fase de Berkeley; \[C\] limitaciones conocidas de captura WARC en páginas dinámicas.
- **Alternativas**: ArchiveBox, Auto Archiver, Webrecorder \[C\].
- **Diferenciación**: puntaje de completitud por captura (recursos esperados vs. capturados, diferencia visual entre render en vivo y render archivado).
- **Datos**: capturas propias.
- **Mecanismo**: inventario de recursos; comparación de capturas de pantalla; hash.
- **Por qué telemetría**: es medición de calidad de evidencia.
- **MVP**: reporte por WARC con faltantes.
- **Demo**: tres páginas dinámicas y una estática.
- **Métrica**: detecta faltantes sembrados (recursos bloqueados).
- **Riesgos**: bajos.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: navegador sin interfaz.
- **Falsación**: si las herramientas existentes ya reportan esto (verificar Webrecorder y Browsertrix en detalle).
- **Novedad**: C/E.

#### T10 · Disponibilidad de trámites vinculados a derechos

- **Problema**: la indisponibilidad de portales de trámites (turnos, prestaciones) afecta derechos, y no hay medición independiente.
- **Usuario y situación**: defensoría o ONG que recibe reclamos y no puede probar la caída.
- **Evidencia**: \[I\] problema inferido; no encontré una medición pública independiente para Argentina.
- **Alternativas**: monitores de disponibilidad genéricos (por ejemplo Upptime \[C\]).
- **Diferenciación**: monitoreo sintético de flujos completos (no solo la home), con evidencia sellada en el tiempo utilizable en un reclamo.
- **Datos**: sondeos propios.
- **Mecanismo**: navegación sintética; capturas con hash; series de disponibilidad.
- **Por qué telemetría**: medición continua.
- **MVP**: tres trámites monitoreados con reporte semanal.
- **Demo**: dos semanas de datos.
- **Métrica**: concordancia con reclamos o anuncios oficiales de caídas.
- **Riesgos**: no automatizar logins ni datos personales; solo pantallas públicas.
- **Dificultad y tiempo**: baja-media; 2 días.
- **Dependencias**: captchas y bloqueos.
- **Falsación**: si los portales están disponibles casi siempre, no hay problema que medir.
- **Novedad**: D.

#### T11 · Ediciones silenciosas en avisos oficiales

- **Problema**: un aviso publicado puede modificarse después de su publicación sin fe de erratas visible.
- **Usuario y situación**: periodista o abogada que cita un aviso del Boletín Oficial.
- **Evidencia**: \[I\] no encontré evidencia documentada de ediciones silenciosas en el Boletín; \[D\] EDGI documentó cambios silenciosos en sitios gubernamentales de EE.UU.
- **Alternativas**: captura manual.
- **Diferenciación**: hash diario de cada aviso y de su PDF, con diferencias tipificadas.
- **Datos**: primera sección del Boletín.
- **Mecanismo**: recolección diaria; hash de contenido normalizado; diff.
- **Por qué telemetría**: monitoreo de un registro que debería ser inmutable.
- **MVP**: recolector y verificador con 30 días de historia.
- **Demo**: mostrar el método aunque no se encuentren cambios.
- **Métrica**: tasa de cambios detectados y su clase.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja; 1–2 días.
- **Dependencias**: tiempo de observación; un hackathon puede no alcanzar.
- **Falsación**: si en meses de observación no hay ediciones, el problema no existe (resultado válido, pero idea débil para hackathon).
- **Novedad**: E.

#### T12 · Deriva de sensores ambientales de bajo costo

- **Problema**: las redes ciudadanas de calidad del aire usan sensores baratos que derivan con el tiempo y la humedad, y las comunidades publican cifras sin saberlo.
- **Usuario y situación**: organización de justicia ambiental que mide en su barrio.
- **Evidencia**: \[C\] literatura sobre sensores de partículas de bajo costo y su sensibilidad a la humedad; \[I\] no verifiqué casos argentinos.
- **Alternativas**: correcciones publicadas por fabricantes y agencias \[C\]; OpenAQ como agregador \[C\].
- **Diferenciación**: alerta de deriva interpretable por sensor con referencia cercana y regla explicada.
- **Datos**: OpenAQ o datos de la propia red.
- **Mecanismo**: regresión móvil contra referencia; detección de cambio en residuos.
- **Por qué telemetría**: series de sensores.
- **MVP**: informe por sensor con estado (estable, derivando, revisar).
- **Demo**: datos públicos con deriva sembrada rotulada.
- **Métrica**: detección de deriva sembrada con demora mínima.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: estación de referencia cercana.
- **Falsación**: si sin referencia cercana no se puede separar deriva de contaminación real.
- **Novedad**: C.

#### T13 · Latencia administrativa por número de expediente

- **Problema**: no hay una medición de cuánto tarda un expediente desde su creación hasta el acto publicado, por organismo.
- **Usuario y situación**: investigadora en administración pública o periodista.
- **Evidencia**: \[D\] los expedientes electrónicos incluyen año y organismo en su identificador (por ejemplo EX-2024-…-APN-AAIP); \[C\] Weber.
- **Alternativas**: no encontré mediciones públicas.
- **Diferenciación**: usa un dato que ya está en los actos publicados: año (y a veces número correlativo) del expediente frente a fecha de publicación.
- **Datos**: Boletín Oficial.
- **Mecanismo**: extracción; latencia en años y estimación más fina si el correlativo es monótono en el tiempo; distribución por organismo.
- **Por qué telemetría**: el identificador funciona como marca temporal implícita.
- **MVP**: distribución de latencias por organismo para un año.
- **Demo**: dos organismos comparados.
- **Métrica**: validación con expedientes cuya fecha de creación sea pública.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: que el correlativo sea monótono (a verificar).
- **Falsación**: si el correlativo no es monótono y la resolución anual es demasiado gruesa.
- **Novedad**: A.

#### T14 · Registro de lo no recolectado en scrapers OSINT

- **Problema**: las herramientas de recolección reportan lo que obtuvieron, no lo que no pudieron obtener, y las investigaciones presentan como "todo" lo que es una muestra.
- **Usuario y situación**: desarrolladora y analista OSINT.
- **Evidencia**: \[D\] MuckRock advierte el sesgo de su propia base; \[I\] patrón general de sesgo de cobertura.
- **Alternativas**: logs de error ad hoc.
- **Diferenciación**: un "ledger de cobertura" estándar: solicitado, obtenido, fallido, bloqueado, no intentado, con causa.
- **Datos**: scrapers propios.
- **Mecanismo**: instrumentación; esquema de eventos; reporte de cobertura.
- **Por qué telemetría**: instrumentación de un proceso de recolección.
- **MVP**: librería con decorador y reporte.
- **Demo**: scraper contra un sitio con fallas sembradas.
- **Métrica**: el reporte refleja el 100% de fallas sembradas.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja; 1 día.
- **Dependencias**: ninguna.
- **Falsación**: si los usuarios no leen el ledger (medir adopción en prueba con dos personas).
- **Novedad**: C.

#### T15 · Deriva de descripciones de herramientas MCP

- **Problema**: un servidor MCP puede cambiar la descripción de una herramienta después de aprobada.
- **Usuario y situación**: equipo de seguridad que opera agentes.
- **Evidencia**: \[D\] el ataque está documentado y hay varias herramientas que fijan hashes de descripciones (mcp-scan, mcp-integrity, Oxvault y otras) ([AppSec Santa](https://appsecsanta.com/mcp-scan); [mcp-integrity](https://pypi.org/project/mcp-integrity/)).
- **Alternativas**: las mencionadas.
- **Diferenciación**: débil; el espacio está ocupado.
- **Datos**: servidores MCP de prueba.
- **Mecanismo**: hash de esquemas por sesión.
- **Por qué telemetría**: monitoreo de cambios.
- **MVP**: no se recomienda.
- **Demo**: n/a.
- **Métrica**: n/a.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja.
- **Dependencias**: ninguna.
- **Falsación**: ya falsada en cuanto a diferenciación.
- **Novedad**: E (incluida para mostrar el filtro).

### Grafos + telemetría (GT01–GT15)

#### GT01 · Cronología con relojes inciertos

- **Problema**: al ordenar videos, mensajes y registros de distintas fuentes, cada reloj tiene un desfase desconocido y las cronologías resultantes pueden ser imposibles sin que se note.
- **Usuario y situación**: verificadora OSINT o analista DFIR que reconstruye un hecho.
- **Evidencia**: \[D\] Timesketch y TimeMap son herramientas activas para líneas de tiempo, sin modelo explícito de incertidumbre de reloj; \[C\] el desfase entre fuentes es un problema conocido en forense.
- **Alternativas**: Timesketch, Plaso, TimeMap.
- **Diferenciación**: cada afirmación de orden ("A antes que B", "A y B dentro de 30 s") se vuelve una restricción de diferencia; el sistema calcula intervalos factibles y detecta contradicciones como ciclos negativos, señalando el subconjunto mínimo culpable.
- **Datos**: eventos de un caso público o un caso sintético con desfases sembrados.
- **Mecanismo**: grafo de restricciones de diferencia; Bellman–Ford o Floyd–Warshall; extracción del ciclo negativo.
- **Por qué grafo y telemetría**: los eventos son telemetría con relojes heterogéneos; la factibilidad es un problema de caminos.
- **MVP**: JSONL de eventos y restricciones → intervalos por evento y contradicciones explicadas.
- **Demo**: tres fuentes con desfase conocido; una restricción falsa que genera ciclo negativo.
- **Métrica**: los intervalos contienen el tiempo real en el 100% de los eventos sintéticos; detecta las contradicciones sembradas.
- **Riesgos**: bajos con datos públicos.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: ninguna.
- **Falsación**: si en casos reales los intervalos resultan tan amplios que no ordenan nada útil.
- **Novedad**: B.

#### GT02 · Trazas de agentes como grafo de procedencia

- **Problema**: cuando un agente ejecuta una acción sensible, no se puede responder qué entradas externas no confiables influyeron en ella.
- **Usuario y situación**: revisora de seguridad de un despliegue con agentes y herramientas MCP.
- **Evidencia**: \[D\] OTel GenAI ya modela agentes, herramientas y MCP como spans, en estado *Development*; \[D\] ataques de envenenamiento de herramientas documentados (ver T15); \[C\] W3C PROV.
- **Alternativas**: plataformas de observabilidad de LLM (muestran árboles de spans, no linaje de datos); escáneres estáticos de MCP.
- **Diferenciación**: convierte spans en un grafo PROV (entidad, actividad, agente) y busca caminos desde entradas marcadas como no confiables hasta herramientas con efectos (análisis de contaminación).
- **Datos**: trazas propias con inyecciones sembradas, rotuladas.
- **Mecanismo**: mapeo span→PROV; etiquetas de confianza; alcanzabilidad dirigida; caminos mínimos como explicación.
- **Por qué grafo y telemetría**: la traza es telemetría; la pregunta es de alcanzabilidad.
- **MVP**: CLI que lee trazas y devuelve caminos "no confiable → acción".
- **Demo**: un agente que lee una página con instrucción inyectada y llama una herramienta de escritura.
- **Métrica**: detecta el 100% de los caminos sembrados; falsos positivos en corridas limpias.
- **Riesgos**: trazas con contenido sensible; minimizar.
- **Dificultad y tiempo**: media; 2–3 días.
- **Dependencias**: que la traza registre qué salida alimenta qué entrada (si no, el linaje se aproxima por orden).
- **Falsación**: si sin dependencias de datos explícitas el grafo conecta todo con todo.
- **Novedad**: B.

#### GT03 · Latencia de publicación y estructura de mercado

- **Problema**: no se sabe si la publicación tardía de adjudicaciones se concentra en ciertas zonas de la red de contratación.
- **Usuario y situación**: investigadora en contratación pública.
- **Evidencia**: \[D\] OCP incluye indicadores de publicación; \[D\] Wachs et al. muestran que el riesgo se agrupa en la red.
- **Alternativas**: indicadores aislados de publicación.
- **Diferenciación**: cruza una señal temporal (demora) con posición estructural (núcleo/periferia, densidad de vecindario).
- **Datos**: OCDS con fechas de adjudicación y publicación (CABA, Mendoza u otra jurisdicción).
- **Mecanismo**: k-core; prueba de permutación sobre la asociación demora–posición.
- **Por qué grafo y telemetría**: combina latencia con estructura.
- **MVP**: análisis reproducible con resultado positivo o nulo.
- **Demo**: una jurisdicción completa.
- **Métrica**: tamaño de efecto e intervalo; robustez ante remuestreo.
- **Riesgos**: bajos; resultados agregados.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: que ambas fechas estén en los datos.
- **Falsación**: un efecto nulo robusto (también publicable, pero débil para un hackathon).
- **Novedad**: E.

#### GT04 · Copias sobrevivientes tras un borrado

- **Problema**: cuando un video original se borra, sus copias y re-subidas pueden sobrevivir, pero encontrarlas es manual.
- **Usuario y situación**: archivista de DD.HH. que perdió una pieza.
- **Evidencia**: \[D\] Syrian Archive restauró cientos de miles de videos y compara su colección con lo disponible en línea.
- **Alternativas**: búsqueda inversa de imágenes; fingerprinting comercial.
- **Diferenciación**: grafo de copias (original, re-subidas, recortes) con hash perceptual y estado de vida monitoreado; responde "¿qué copia viva más cercana al original existe?".
- **Datos**: colección propia o pública con copias conocidas.
- **Mecanismo**: hash perceptual; grafo de similitud; telemetría de disponibilidad por nodo.
- **Por qué grafo y telemetría**: relaciones de derivación más estado en el tiempo.
- **MVP**: para un ítem perdido, lista de copias vivas ordenadas por fidelidad.
- **Demo**: dataset sintético de copias con recortes y recodificación.
- **Métrica**: recall de copias conocidas.
- **Riesgos**: medios; contenido sensible; no redistribuir.
- **Dificultad y tiempo**: media-alta; 3 días.
- **Dependencias**: acceso a plataformas para buscar candidatas (limitado).
- **Falsación**: si la búsqueda de candidatas es el cuello de botella y el grafo no la resuelve.
- **Novedad**: C.

#### GT05 · Frescura del eslabón más débil

- **Problema**: un tablero público muestra una fecha de actualización, pero alguno de los datasets de los que depende está desactualizado.
- **Usuario y situación**: periodista que usa un tablero oficial.
- **Evidencia**: \[D\] AR0107; \[I\] los tableros rara vez exponen su linaje.
- **Alternativas**: verificación manual.
- **Diferenciación**: grafo de dependencias con frescura medida por nodo (T02) y propagación del mínimo hacia el tablero.
- **Datos**: tableros con fuentes declaradas; metadatos CKAN.
- **Mecanismo**: DAG; propagación de mínimos; camino crítico.
- **Por qué grafo y telemetría**: frescura medida más dependencia.
- **MVP**: para un tablero, frescura efectiva y dataset responsable.
- **Demo**: dos tableros oficiales.
- **Métrica**: coincidencia con revisión manual.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja-media; 2 días.
- **Dependencias**: que el tablero declare sus fuentes.
- **Falsación**: si casi ningún tablero declara fuentes.
- **Novedad**: C.

#### GT06 · Cadena de custodia sin huecos

- **Problema**: en la documentación de violaciones, los traspasos de evidencia entre personas y sistemas dejan intervalos sin custodio registrado.
- **Usuario y situación**: coordinadora de documentación de una ONG.
- **Evidencia**: \[D\] Berkeley pide integridad en recolección y preservación; \[C\] cadena de custodia en estándares forenses.
- **Alternativas**: registros manuales; plataformas de captura con hash (eyeWitness, Tella \[C\]).
- **Diferenciación**: grafo de custodia temporal que verifica cobertura total de intervalos y la integridad de hash en cada traspaso.
- **Datos**: eventos de custodia sintéticos rotulados.
- **Mecanismo**: intervalos por custodio; verificación de cobertura; hash por traspaso.
- **Por qué grafo y telemetría**: traspasos como aristas temporales; accesos como telemetría.
- **MVP**: verificador que reporta huecos y discontinuidades de hash.
- **Demo**: una pieza con un hueco sembrado.
- **Métrica**: detección del 100% de huecos sembrados.
- **Riesgos**: medios; metadatos de custodios.
- **Dificultad y tiempo**: baja; 1–2 días.
- **Dependencias**: adopción del registro.
- **Falsación**: si los equipos no registran traspasos de forma estructurada.
- **Novedad**: C.

#### GT07 · Cobertura de archivado de sitios gubernamentales

- **Problema**: antes de un cambio de gobierno se archivan sitios oficiales, pero no se sabe qué fracción del sitio quedó efectivamente capturada.
- **Usuario y situación**: colectivo de archivo web.
- **Evidencia**: \[D\] EDGI y los proyectos End of Term en EE.UU.; \[D\] Pew: 21% de páginas gubernamentales con enlaces rotos.
- **Alternativas**: informes de rastreo de Heritrix o Browsertrix \[C\].
- **Diferenciación**: estimación de cobertura sobre el grafo de enlaces con técnicas de captura–recaptura entre rastreos independientes.
- **Datos**: rastreos propios de un sitio oficial.
- **Mecanismo**: grafo del sitio; dos o tres rastreos con semillas distintas; estimadores de Lincoln–Petersen.
- **Por qué grafo y telemetría**: alcanzabilidad más registros de captura.
- **MVP**: estimación de páginas no capturadas con intervalo.
- **Demo**: un sitio de tamaño medio.
- **Métrica**: validación contra un sitemap completo conocido.
- **Riesgos**: bajos; respetar carga del servidor.
- **Dificultad y tiempo**: media; 2–3 días.
- **Dependencias**: rastreos que no son independientes (sesgo de captura).
- **Falsación**: si la dependencia entre rastreos invalida la estimación.
- **Novedad**: B.

#### GT08 · Cambios de esquema en datos abiertos y apps dependientes

- **Problema**: un organismo cambia columnas de un CSV y rompe aplicaciones cívicas que lo consumen, sin aviso.
- **Usuario y situación**: desarrolladora cívica.
- **Evidencia**: \[I\] patrón frecuente en datos abiertos; \[D\] AR0107 reconoce problemas de calidad.
- **Alternativas**: validadores tipo Frictionless \[C\].
- **Diferenciación**: monitorea esquemas y avisa a los proyectos registrados como dependientes de ese recurso.
- **Datos**: recursos de datos.gob.ar; registro de consumidores.
- **Mecanismo**: inferencia de esquema; diff; grafo recurso→consumidor.
- **Por qué grafo y telemetría**: dependencia más monitoreo.
- **MVP**: alerta de cambio de esquema para 50 recursos.
- **Demo**: cambio sembrado.
- **Métrica**: tasa de cambios reales detectados en un mes.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja; 1–2 días.
- **Dependencias**: que los consumidores se registren.
- **Falsación**: si los cambios de esquema son raros.
- **Novedad**: C.

#### GT09 · Repunteo de etiquetas en dependencias de CI

- **Problema**: las etiquetas de versión de una acción de CI pueden reapuntarse a otro commit, como en el compromiso de tj-actions/changed-files.
- **Usuario y situación**: mantenedora de proyectos abiertos.
- **Evidencia**: \[D\] en marzo de 2025 se reapuntaron las etiquetas de tj-actions/changed-files a un commit malicioso, afectando a unos 23.000 repositorios ([OSV](https://osv.dev/vulnerability/GHSA-mrrh-fwg8-r2c3); [oss-sec](https://seclists.org/oss-sec/2025/q1/227)).
- **Alternativas**: fijar acciones por hash; herramientas de pinning y de monitoreo de red en CI \[C\].
- **Diferenciación**: monitoreo histórico de etiqueta→commit en el grafo transitivo de acciones usadas por un conjunto de proyectos.
- **Datos**: workflows públicos; API de GitHub.
- **Mecanismo**: grafo de acciones; sondeo de etiquetas; alerta ante cambio.
- **Por qué grafo y telemetría**: dependencia transitiva más cambio en el tiempo.
- **MVP**: monitor para un conjunto de repositorios.
- **Demo**: repunteo simulado en un repositorio propio.
- **Métrica**: detección en minutos.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja-media; 2 días.
- **Dependencias**: límites de API.
- **Falsación**: si las herramientas existentes ya cubren el monitoreo histórico (probable).
- **Novedad**: C/E.

#### GT10 · Autoridad de fuentes con decaimiento temporal

- **Problema**: los verificadores no tienen una medida explícita de cómo cambió la confiabilidad de una fuente en el tiempo.
- **Usuario y situación**: redacción de verificación.
- **Evidencia**: \[I\] necesidad inferida.
- **Alternativas**: calificaciones de medios comerciales \[C\].
- **Diferenciación**: grafo de verificaciones con decaimiento temporal.
- **Datos**: verificaciones públicas.
- **Mecanismo**: PageRank personalizado con decaimiento.
- **Por qué grafo y telemetría**: propagación más tiempo.
- **MVP**: puntaje por fuente.
- **Demo**: datos públicos de verificación.
- **Métrica**: concordancia con juicio experto.
- **Riesgos**: altos; reputación de medios y manipulación del puntaje.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: corpus de verificaciones estructurado.
- **Falsación**: si el puntaje replica popularidad.
- **Novedad**: E.

#### GT11 · Trayectoria administrativa completa

- **Problema**: combina G17 y T13: además de reconstruir la cadena de actos, mide cuánto tardó cada tramo y dónde se detuvo.
- **Usuario y situación**: periodista que sigue una política pública.
- **Evidencia**: \[D\] ver G17 y T13.
- **Alternativas**: búsqueda manual.
- **Diferenciación**: línea de tiempo de una decisión con tramos y demoras por organismo.
- **Datos**: Boletín Oficial.
- **Mecanismo**: componentes por expediente; latencias entre actos; detección de tramos anómalos frente a la distribución del organismo.
- **Por qué grafo y telemetría**: estructura de actos más tiempos.
- **MVP**: vista de una trayectoria con tramos coloreados por demora relativa.
- **Demo**: una política con 5–10 actos.
- **Métrica**: coincidencia con una reconstrucción manual.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: media; 3 días.
- **Dependencias**: las de G17 y T13.
- **Falsación**: las de G17.
- **Novedad**: A/D.

#### GT12 · Reversiones en Wikidata sobre instituciones

- **Problema**: vandalismo o ediciones interesadas en ítems de instituciones públicas se propagan a aplicaciones antes de revertirse.
- **Usuario y situación**: comunidad Wikimedia local.
- **Evidencia**: \[C\] el historial de ediciones de Wikidata es público.
- **Alternativas**: herramientas de patrullaje de Wikimedia \[C\].
- **Diferenciación**: mide tiempo hasta reversión por subgrafo temático (instituciones argentinas) y exposición de vecinos.
- **Datos**: historial de ediciones.
- **Mecanismo**: subgrafo temático; detección de reversiones; tiempo de exposición.
- **Por qué grafo y telemetría**: estructura más eventos de edición.
- **MVP**: informe del subgrafo con tiempos de exposición.
- **Demo**: un año de historia.
- **Métrica**: concordancia con reversiones marcadas.
- **Riesgos**: no perfilar editores; agregar.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: volumen del historial.
- **Falsación**: si los tiempos de exposición son mínimos.
- **Novedad**: C.

#### GT13 · Sensores que discrepan con sus vecinos

- **Problema**: en una red ciudadana de sensores, un sensor defectuoso se confunde con un foco real de contaminación.
- **Usuario y situación**: organización comunitaria que publica mediciones.
- **Evidencia**: \[C\] literatura sobre detección de fallas en redes de sensores.
- **Alternativas**: correcciones por sensor (T12).
- **Diferenciación**: grafo espacial de vecindad; un sensor que diverge de todos sus vecinos es sospechoso; uno que diverge junto con sus vecinos sugiere un evento real.
- **Datos**: OpenAQ u otra red abierta.
- **Mecanismo**: grafo k-vecinos; residuos de consenso local; reglas explicables.
- **Por qué grafo y telemetría**: vecindad más series.
- **MVP**: clasificación por sensor y período.
- **Demo**: fallas y eventos sembrados.
- **Métrica**: separa fallas de eventos sembrados.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: densidad de sensores.
- **Falsación**: con baja densidad, no hay vecinos suficientes.
- **Novedad**: C.

#### GT14 · Resultados que dependen de intermedios viejos

- **Problema**: en análisis periodísticos o académicos, un gráfico final se calcula a partir de un archivo intermedio que no se regeneró tras cambiar los datos de origen.
- **Usuario y situación**: periodista de datos antes de publicar.
- **Evidencia**: \[C\] problema conocido de reproducibilidad; herramientas como noWorkflow o ReproZip \[C\].
- **Alternativas**: sistemas de flujos (Make, DVC, Snakemake \[C\]).
- **Diferenciación**: captura liviana de procedencia en notebooks existentes sin migrar a un sistema de flujos, con verificación de frescura por linaje.
- **Datos**: notebook propio.
- **Mecanismo**: hooks de lectura/escritura de archivos; grafo PROV; comparación de hashes y tiempos.
- **Por qué grafo y telemetría**: linaje más eventos de ejecución.
- **MVP**: extensión que marca celdas con insumos obsoletos.
- **Demo**: notebook con un intermedio desactualizado sembrado.
- **Métrica**: detección del 100% de casos sembrados.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: interceptar E/S de librerías comunes.
- **Falsación**: si DVC o similares ya cubren el caso sin fricción.
- **Novedad**: C.

#### GT15 · Co-ocurrencia de tácticas en incidentes contra organizaciones civiles

- **Problema**: organizaciones civiles sufren ataques digitales parecidos pero no comparten datos estructurados que permitan ver patrones.
- **Usuario y situación**: equipo de respuesta para sociedad civil.
- **Evidencia**: \[C\] existencia de CERTs para sociedad civil; \[I\] no verifiqué acceso a datos.
- **Alternativas**: MISP y plataformas de intercambio \[C\].
- **Diferenciación**: grafo de co-ocurrencia de tácticas sin datos de víctimas.
- **Datos**: requerirían acuerdos de intercambio.
- **Mecanismo**: grafo táctica–táctica ponderado en el tiempo.
- **Por qué grafo y telemetría**: co-ocurrencia más tiempo.
- **MVP**: no viable sin datos.
- **Demo**: sintética.
- **Métrica**: n/a sin datos reales.
- **Riesgos**: altos; reidentificación de organizaciones atacadas.
- **Dificultad y tiempo**: alta.
- **Dependencias**: acuerdos institucionales (bloqueante).
- **Falsación**: n/a.
- **Novedad**: E.

### Sociología, DD.HH. y crimen organizado (S01–S10)

#### S01 · Brecha del registro de audiencias por captura–recaptura

- **Problema**: no se sabe qué proporción de las reuniones de gestión de intereses queda fuera del registro oficial.
- **Usuario y situación**: ONG de transparencia que quiere un número defendible, no un caso anecdótico.
- **Evidencia**: \[D\] reunión presidencial confirmada que no figuraba en el registro (Chequeado); \[D\] HRDAG usa captura–recaptura para estimar lo no documentado.
- **Alternativas**: detección caso por caso.
- **Diferenciación**: estima el universo de reuniones combinando el registro con fuentes independientes (agendas oficiales publicadas, comunicados), al estilo MSE, con supuestos explícitos.
- **Datos**: registro de audiencias; agendas y comunicados públicos de un organismo durante un período.
- **Mecanismo**: vinculación de registros (fecha, organismo, contraparte); estimadores de dos o tres listas; análisis de sensibilidad a dependencia entre fuentes.
- **Tecnología**: telemetría institucional y estadística; grafo solo para la vinculación.
- **MVP**: estimación para un organismo y seis meses, con intervalo y supuestos.
- **Demo**: resultado con su explicación de supuestos.
- **Métrica**: estabilidad del estimador ante variaciones del criterio de vinculación.
- **Riesgos**: medios; afecta reputación de funcionarios; el resultado es institucional, no personal. Las fuentes no son independientes (los comunicados y el registro dependen del mismo organismo), lo que sesga la estimación.
- **Dificultad y tiempo**: media; 3 días.
- **Dependencias**: agendas publicadas con detalle suficiente.
- **Falsación**: si la dependencia entre fuentes es tan fuerte que el intervalo resulta inútil.
- **Novedad**: A.

#### S02 · De la recomendación a la norma

- **Problema**: las recomendaciones de órganos de DD.HH. a Argentina se registran, pero no se conectan con las normas posteriores que las implementan o contradicen.
- **Usuario y situación**: institución nacional de DD.HH. u ONG que redacta un informe sombra.
- **Evidencia**: \[D\] UHRI, NRTD y UPR Info registran recomendaciones y seguimiento estatal; \[D\] InfoLEG abierto.
- **Alternativas**: seguimiento manual; NRTD (de uso estatal).
- **Diferenciación**: vínculos recomendación→norma con evidencia textual y validación humana, y medición de latencia.
- **Datos**: exportaciones del UHRI para Argentina; InfoLEG.
- **Mecanismo**: candidatos por coincidencia de términos y referencias explícitas; cola de validación; grafo bipartito; supervivencia.
- **Tecnología**: grafo bipartito temporal.
- **MVP**: para un tema (por ejemplo, violencia institucional), recomendaciones con normas candidatas validadas.
- **Demo**: 30 recomendaciones de un ciclo del EPU.
- **Métrica**: precisión de candidatos; tiempo de validación por recomendación.
- **Riesgos**: bajos; el riesgo es interpretar "norma vinculada" como "recomendación cumplida".
- **Dificultad y tiempo**: media; 3 días.
- **Dependencias**: exportación del UHRI.
- **Falsación**: si la mayoría de recomendaciones no tiene correlato normativo identificable (porque piden prácticas, no normas).
- **Novedad**: A.

#### S03 · Solapamiento de listas de documentación

- **Problema**: organizaciones que documentan casos (por ejemplo, violencia institucional) publican listas que se suman en debates públicos, cuando en realidad se solapan.
- **Usuario y situación**: coalición de organizaciones que quiere un conteo conjunto sin entregar sus bases.
- **Evidencia**: \[D\] HRDAG: record linkage y MSE en Guatemala, Siria, Colombia, Filipinas.
- **Alternativas**: consultorías estadísticas especializadas; scripts propios.
- **Diferenciación**: herramienta local que calcula solapamientos sobre identificadores protegidos (hashes con sal compartida) sin centralizar datos, y produce el diagrama de solapamiento listo para MSE.
- **Datos**: listas propias de cada organización (consentidas); demo sintética.
- **Mecanismo**: normalización; vinculación por bloques; hashing con sal; conteo de patrones de captura.
- **Tecnología**: vinculación de registros; grafo de coincidencias.
- **MVP**: dos o tres listas sintéticas, tabla de patrones de captura.
- **Demo**: listas sintéticas con solapamientos conocidos.
- **Métrica**: recuperación de solapamientos sembrados con errores tipográficos.
- **Riesgos**: altos; datos de víctimas. El hashing de nombres es vulnerable a ataques de diccionario; requiere sal secreta y acuerdo entre organizaciones.
- **Dificultad y tiempo**: media; 3 días.
- **Dependencias**: acuerdo entre organizaciones para uso real (no para la demo).
- **Falsación**: si la vinculación por hash pierde tantos verdaderos positivos (variantes de nombre) que el solapamiento queda subestimado.
- **Novedad**: D.

#### S04 · Vacíos documentales frente a vacíos de cobertura

- **Problema**: en un mapa de hechos documentados, la ausencia de registros en una zona o período puede significar que no ocurrió nada o que nadie estaba mirando.
- **Usuario y situación**: investigadora que interpreta un mapa de violaciones o de violencia.
- **Evidencia**: \[D\] HRDAG advierte sobre muestras de conveniencia y lo no documentado; \[D\] el modelo de huecos de AIS distingue huecos técnicos de intencionales.
- **Alternativas**: mapas de eventos (TimeMap, ACLED \[C\]).
- **Diferenciación**: capa de cobertura: para cada zona y período, actividad de las fuentes (¿publicaron algo, sobre cualquier tema?). Se distingue "sin eventos con cobertura" de "sin cobertura".
- **Datos**: eventos públicos y actividad de las fuentes (fechas de publicación de medios locales u ONG).
- **Mecanismo**: tasa de actividad por fuente y celda; clasificación de celdas vacías.
- **Tecnología**: telemetría de fuentes.
- **MVP**: mapa con tres estados por celda.
- **Demo**: un dataset público de eventos.
- **Métrica**: concordancia con zonas de cobertura conocida.
- **Riesgos**: bajos con datos agregados.
- **Dificultad y tiempo**: media; 2–3 días.
- **Dependencias**: medir actividad de fuentes locales.
- **Falsación**: si la actividad de fuentes no se puede medir por zona.
- **Novedad**: B.

#### S05 · Compromisos de gobierno abierto con evidencia verificable

- **Problema**: el avance de compromisos de gobierno abierto se informa con hitos declarados, pero la evidencia enlazada se pierde o no prueba el hito.
- **Usuario y situación**: sociedad civil que co-crea y monitorea planes de acción.
- **Evidencia**: \[D\] los compromisos argentinos se publican con hitos y revisiones del IRM ([AR0107](https://www.opengovpartnership.org/members/argentina/commitments/AR0107/); [AR0081](https://www.opengovpartnership.org/members/argentina/commitments/AR0081/)); \[D\] decaimiento de enlaces (Pew).
- **Alternativas**: sitio de OGP; revisión del IRM.
- **Diferenciación**: verifica disponibilidad y contenido de cada enlace de evidencia y si prueba el hito (checklist humano).
- **Datos**: páginas de compromisos.
- **Mecanismo**: T01 aplicado a evidencias de hitos.
- **Tecnología**: telemetría de enlaces.
- **MVP**: estado de evidencia del plan vigente.
- **Demo**: plan 2025–2027.
- **Métrica**: proporción de hitos con evidencia viva y pertinente.
- **Riesgos**: bajos.
- **Dificultad y tiempo**: baja; 1–2 días.
- **Dependencias**: ninguna.
- **Falsación**: si la evidencia está en buen estado.
- **Novedad**: D.

#### S06 · Respuesta institucional en conflictos ambientales

- **Problema**: comunidades afectadas por contaminación no pueden medir cuánto tarda el Estado en responder denuncias e inspecciones.
- **Usuario y situación**: organización barrial en una cuenca contaminada.
- **Evidencia**: \[I\] no verifiqué qué datos de inspecciones y denuncias publica ACUMAR u otros organismos.
- **Alternativas**: informes de auditoría, causas judiciales.
- **Diferenciación**: línea de tiempo denuncia→inspección→sanción por establecimiento con demoras.
- **Datos**: a verificar (bloqueante).
- **Mecanismo**: grafo de eventos por establecimiento; latencias.
- **Tecnología**: grafo de eventos y telemetría institucional.
- **MVP**: depende de datos.
- **Demo**: sintética si no hay datos.
- **Métrica**: n/a sin datos.
- **Riesgos**: medios; expone denunciantes si hay datos personales.
- **Dificultad y tiempo**: incierta.
- **Dependencias**: datos públicos de inspecciones (bloqueante).
- **Falsación**: si los datos no existen públicamente.
- **Novedad**: D, condicionada.

#### S07 · Contratistas y aportes de campaña

- **Problema**: la Ley 26.215 prohíbe aportes de contratistas del Estado; los aportes indirectos vía gerentes o empleados se detectan a mano.
- **Usuario y situación**: periodista o auditora electoral.
- **Evidencia**: \[D\] Chequeado revisó a mano los 849 aportantes de una campaña y encontró aportes de gerentes de empresas contratistas ([Chequeado](https://chequeado.com/investigaciones/macri-recibio-3-millones-de-contratistas-del-estado-para-su-campana-electoral/)); \[D\] la CNE tiene una plataforma de aportantes (Directorio Legislativo).
- **Alternativas**: el cruce manual citado; en Colombia, Transparencia por Colombia hace estos cruces sistemáticamente.
- **Diferenciación**: débil; es un cruce tabular conocido.
- **Datos**: aportantes de la CNE; proveedores; autoridades societarias.
- **Mecanismo**: vinculación de registros; grafo persona–empresa para el aporte indirecto.
- **Tecnología**: tabla más vinculación; grafo marginal.
- **MVP**: lista de aportantes vinculados a contratistas.
- **Demo**: una campaña pasada.
- **Métrica**: replica el hallazgo de Chequeado.
- **Riesgos**: altos; personas físicas; un empleado puede aportar legítimamente con fondos propios.
- **Dificultad y tiempo**: media; 2 días.
- **Dependencias**: descarga masiva de la plataforma de la CNE.
- **Falsación**: si el grafo no agrega nada sobre el cruce directo.
- **Novedad**: C/E.

#### S08 · Causas de lesa humanidad detenidas

- **Problema**: los informes de la Procuraduría de Crímenes contra la Humanidad describen el estado de las causas en PDF por fecha de corte; no hay una serie que muestre qué causas no cambiaron de etapa en años.
- **Usuario y situación**: organismo de DD.HH. o periodista que sigue el proceso de juzgamiento.
- **Evidencia**: \[D\] la PCCH publica informes estadísticos anuales con tablas de debates en curso y señala demoras en la etapa recursiva ("espiral recursivo") ([informe 2024](https://www.fiscales.gob.ar/wp-content/uploads/2024/12/Informe-estadistico-de-diciembre-2024-de-la-PCCH.pdf); [informe 2025](https://www.fiscales.gob.ar/wp-content/uploads/2025/12/Lesa-Informe-estadistico-de-diciembre-2025-de-la-PCCH.pdf)).
- **Alternativas**: los propios informes; seguimientos de organismos de DD.HH.
- **Diferenciación**: serie por causa entre informes sucesivos, con tiempo en cada etapa y detección de causas estancadas.
- **Datos**: informes PCCH 2016–2025 (tablas en PDF).
- **Mecanismo**: extracción de tablas; vinculación de causas entre años (nombres cambian por acumulación); grafo de acumulaciones; supervivencia por etapa.
- **Tecnología**: telemetría institucional y grafo de acumulación de causas.
- **MVP**: causas con debate oral en curso en informes consecutivos y su duración.
- **Demo**: series 2020–2025.
- **Métrica**: exactitud de la vinculación de causas entre informes en una muestra revisada a mano.
- **Riesgos**: medios; datos sobre procesos judiciales en curso; trabajar a nivel causa, no a nivel imputado.
- **Dificultad y tiempo**: media; 3 días.
- **Dependencias**: consistencia de nombres de causa entre informes.
- **Falsación**: si las tablas publicadas no permiten seguir causas entre años.
- **Novedad**: D.

#### S09 · Reetiquetado presupuestario

- **Problema**: programas presupuestarios se fusionan, dividen o renombran entre ejercicios, y eso puede ocultar recortes o desplazamientos de gasto hacia categorías menos visibles.
- **Usuario y situación**: analista de presupuesto de una ONG (ACIJ, ASAP) o periodista.
- **Evidencia**: \[D\] Hood y Piotrowska documentaron *gaming* por recategorización del gasto público británico; \[D\] Presupuesto Abierto publica crédito y ejecución desde 1995 y existe una librería que arma series ([pysupuesto](https://pypi.org/project/pysupuesto)).
- **Alternativas**: análisis manual año a año; series del sitio oficial.
- **Diferenciación**: grafo de linaje de programas entre ejercicios (continuidad, fusión, división, baja, alta) y medición de cuánto gasto atraviesa reclasificaciones.
- **Datos**: Presupuesto Abierto, clasificaciones programáticas por año.
- **Mecanismo**: emparejamiento de programas entre años por código, nombre y actividades; grafo de linaje; flujo de crédito entre nodos.
- **Tecnología**: grafo temporal de clasificaciones.
- **MVP**: linaje de programas de una jurisdicción en cinco ejercicios.
- **Demo**: un ministerio con reestructuraciones conocidas.
- **Métrica**: concordancia del linaje con revisión manual; proporción de crédito con continuidad identificable.
- **Riesgos**: bajos; interpretar reclasificación como manipulación sin evidencia.
- **Dificultad y tiempo**: media; 3 días.
- **Dependencias**: disponibilidad de descripciones de actividades por año.
- **Falsación**: si casi todos los programas tienen continuidad trivial por código.
- **Novedad**: A/B.

#### S10 · Exposición de metadatos en publicaciones de ONG

- **Problema**: los PDFs y documentos que publican organizaciones de DD.HH. suelen filtrar nombres de usuario, rutas internas y software usado, que permiten mapear al equipo.
- **Usuario y situación**: responsable de seguridad de una ONG o redacción.
- **Evidencia**: \[C\] las herramientas de metadatos (exiftool, FOCA) existen y se usan ofensivamente; \[D\] Berkeley pide proteger la seguridad digital de investigadores.
- **Alternativas**: limpiadores de metadatos (mat2 \[C\]), escáneres ofensivos.
- **Diferenciación**: grafo de exposición agregado: qué identificadores internos aparecen en qué documentos y cómo conectan a personas del equipo, con recomendaciones de limpieza.
- **Datos**: documentos públicos de la propia organización.
- **Mecanismo**: extracción de metadatos; grafo documento–identificador; componentes.
- **Tecnología**: grafo bipartito.
- **MVP**: informe de exposición para un sitio propio.
- **Demo**: documentos sintéticos con metadatos sembrados.
- **Métrica**: cobertura de identificadores sembrados.
- **Riesgos**: uso dual; mitigado con uso solo sobre dominio propio verificado.
- **Dificultad y tiempo**: baja; 1–2 días.
- **Dependencias**: ninguna.
- **Falsación**: si las organizaciones ya limpian metadatos sistemáticamente.
- **Novedad**: C.

## D. Filtrado adversarial y shortlist de 20 finalistas

Quedan 20 finalistas, cinco por categoría; 40 ideas se descartan o pasan a reserva. El filtro se aplicó como un revisor hostil: para cada idea busqué la razón más fuerte para no hacerla y la conservé solo si esa razón no resistía.

### Criterios de descarte aplicados

1. **Dato bloqueante**: el MVP depende de un dataset cuya existencia o acceso no verifiqué (G08, G16, S06, GT15).
2. **Espacio ocupado**: existen varias herramientas que ya hacen lo mismo (T15, GT09, GT14, S07).
3. **Grafo o telemetría decorativos**: la pregunta se responde con una tabla (G12, S07).
4. **Riesgo desproporcionado**: posibilidad de reidentificación o de daño reputacional sin beneficio proporcional (G08, GT10, S07).
5. **Resultado probablemente nulo o no observable en un hackathon** (T11, GT03).
6. **Absorción**: otra idea cubre lo mismo mejor (G06→G01/G20, G13→GT05, T07→S01, S05→T01, GT11→G17).

### Finalistas

Los niveles son juicios argumentados, no puntajes: "Alta" en evidencia significa que hay una fuente que documenta el problema; "Media", que hay evidencia análoga en otro contexto; "Baja", que es inferencia mía.

| Código | Idea | Evidencia de necesidad | Diferenciación | Factibilidad individual | Datos | Riesgo ético | Argumento central |
| --- | --- | --- | --- | --- | --- | --- | --- |
| G01 | Fuentes efectivamente independientes | Media | Alta | Alta | Públicos, armado manual | Bajo | Convierte una regla editorial ("dos fuentes") en un cálculo verificable con un teorema clásico |
| G04 | Fragilidad ante coincidencias dudosas | Media | Alta | Alta | Sintéticos o FtM | Bajo con entidades | Nadie propaga la incertidumbre de vinculación hasta la conclusión publicada |
| G05 | Contradicciones en cronologías | Media | Alta | Media | Caso público formalizado | Medio | Pasa de visualizar contradicciones a calcular versiones consistentes |
| G09 | Caminos honestos entre entidades | Media | Media | Alta | IGJ | Medio | Ataca el error más común de los grafos societarios: el hub espurio |
| G17 | Trayectoria de expedientes del Boletín | Alta | Alta | Media | Boletín Oficial | Bajo | Usa un identificador que ya está en los actos y que nadie explota como grafo |
| T01 | Deriva de contenido detrás de citas | Alta | Media | Alta | Públicos | Bajo | Mide el caso que las mediciones de enlaces rotos no ven |
| T02 | Latido esperado de datasets | Alta | Media | Alta | CKAN | Bajo | Encaja con un compromiso oficial vigente (AR0107) |
| T04 | Patologías de agentes | Alta | Media | Alta | Sintéticos rotulados | Bajo | Benchmark de fallas sembradas sobre una convención estándar inmadura |
| T08 | Supervivencia de contenido de interés público | Alta | Media | Media | Públicos | Medio | Abre un dato que hoy solo producen pocas organizaciones |
| T13 | Latencia administrativa por expediente | Baja | Alta | Media | Boletín Oficial | Bajo | Telemetría implícita en un identificador; idea A en la escala |
| GT01 | Cronología con relojes inciertos | Media | Alta | Alta | Sintéticos y públicos | Bajo | Detecta cronologías imposibles con un algoritmo de libro |
| GT02 | Trazas de agentes como procedencia | Alta | Alta | Media | Sintéticos rotulados | Bajo | Une observabilidad de agentes con análisis de contaminación |
| GT06 | Cadena de custodia sin huecos | Alta | Media | Alta | Sintéticos | Medio | Traduce un requisito del Protocolo de Berkeley a una verificación automática |
| GT07 | Cobertura de archivado gubernamental | Alta | Alta | Media | Rastreos propios | Bajo | Responde "qué nos falta" con un intervalo, no con una lista |
| GT05 | Frescura del eslabón más débil | Media | Media | Alta | CKAN | Bajo | Extiende T02 a tableros y muestra el responsable del atraso |
| S01 | Brecha del registro de audiencias | Alta | Alta | Media | Públicos | Medio | Pasa del caso anecdótico a una estimación con supuestos explícitos |
| S02 | De la recomendación a la norma | Media | Alta | Media | UHRI + InfoLEG | Bajo | Conecta dos sistemas que hoy no se hablan |
| S03 | Solapamiento de listas de documentación | Alta | Media | Media | Sintéticos | Alto (mitigable) | Lleva una práctica de HRDAG a organizaciones sin estadísticos |
| S08 | Causas de lesa humanidad detenidas | Alta | Media | Media | Informes PCCH | Medio | La PCCH ya diagnostica demoras; falta la serie por causa |
| S09 | Reetiquetado presupuestario | Alta | Alta | Media | Presupuesto Abierto | Bajo | Aplica una tesis académica documentada (Hood) a datos argentinos de 30 años |

### Reservas (pueden subir si se resuelve una dependencia)

| Código | Qué falta para subir |
| --- | --- |
| G03 | Verificar que las unidades compradoras se puedan emparejar entre años |
| G11 | Confirmar que COMPR.AR/CONTRAT.AR publican todos los oferentes |
| G07 | Construir el backtest de abandono |
| G14, G10, G19 | Bajo riesgo y factibles; impacto menor que las finalistas |
| G18 | Verificar el campo de representado en el registro de audiencias |
| G20 | Depende de T08 |
| T03 | Credenciales de la API de transporte |
| T05, T14 | Útiles como componentes de otras ideas (GT02, T08) más que como proyecto propio |
| T06 | Verificar si la AAIP ya publica series completas |
| S04 | Medir actividad de fuentes locales por zona |
| S10 | Definir el control de uso dual |

### Descartes argumentados

| Código | Razón principal |
| --- | --- |
| G02 | Útil pero subsumida por G17 y S02, que usan las mismas bases con una pregunta más fuerte |
| G06 | Absorbida por G01 (independencia) y G20 (priorización) |
| G08 | Acceso al MAPPAP no verificado y riesgo de reidentificación alto |
| G12 | El grafo no se justifica; determinar qué leyes requieren reglamentación no es automatizable con confianza |
| G13 | Absorbida por GT05 |
| G15 | Demasiado trabajo de modelado y extracción para un prototipo individual |
| G16 | Corpus bloqueante |
| T07 | Absorbida por S01, que estima en vez de alertar |
| T09 | Probable superposición con herramientas de captura existentes que no verifiqué a fondo |
| T10 | Monitoreo de disponibilidad genérico; diferenciación débil |
| T11 | Puede no observarse ningún caso en el plazo de un hackathon |
| T12 | Requiere estación de referencia cercana; GT13 lo resuelve mejor y aun así queda fuera |
| T15 | Espacio ocupado por varias herramientas |
| GT03 | Resultado probablemente nulo; débil para demo |
| GT04 | El cuello de botella es buscar candidatas, no el grafo |
| GT08 | Baja novedad frente a validadores existentes |
| GT09 | Probable superposición con herramientas de seguridad de CI |
| GT10 | Riesgo reputacional y de manipulación; tiende a medir popularidad |
| GT11 | Se fusiona con G17 como su extensión natural |
| GT12 | Impacto bajo |
| GT13 | Requiere densidad de sensores poco común |
| GT14 | DVC y similares cubren gran parte del caso |
| GT15 | Requiere acuerdos institucionales previos |
| S05 | Es T01 aplicada a un caso; se usa como demo de T01 |
| S06 | Datos no verificados |
| S07 | Cruce tabular conocido y riesgo alto sobre personas físicas |

## E. Diez fichas de prototipo ejecutables

Las diez ideas mejor fundamentadas son G01, G04, G17, GT01, GT02, T01, T02, S02, S08 y S09. Se eligieron por combinar evidencia documentada, datos accesibles sin acuerdos y un criterio de abandono medible en pocos días. En las demos, toda cifra es un **formato de ejemplo**: ninguna sale de datos procesados en esta investigación.

Stack común sugerido \[I\]: Python 3.12, DuckDB, NetworkX (Raphtory solo si el tiempo es el eje), `httpx` con caché en disco, salida HTML estática. Todo dato sintético vive en una carpeta `synthetic/` con un README que explica cómo se generó.

### E1 · G01 Fuentes efectivamente independientes

- **Hipótesis de utilidad**: en casos reales, el número de fuentes independientes efectivas es menor que el de notas que "confirman", y esa diferencia cambiaría la decisión editorial en al menos uno de cada cinco casos.
- **Implementación mínima**: CLI que recibe una lista de URLs, extrae enlaces del cuerpo de cada nota, arma el grafo y calcula k con flujo máximo.
- **Arquitectura inicial**: recolector con caché → extractor de cuerpo y enlaces → canonicalizador de URLs → grafo → solver → reporte HTML.
- **Modelo de datos**: `Nodo(url_canónica, tipo ∈ {nota, intermedia, primaria}, medio, fecha)`; `Arista(origen, destino, texto_ancla, posición)`; `Anotación(url, es_primaria, anotadora)`.
- **Fuentes**: notas públicas; Wayback para las caídas.
- **Algoritmo central**: división de vértices (v\_in→v\_out con capacidad 1), flujo máximo desde la afirmación hasta un sumidero conectado a las primarias; el corte mínimo explica el resultado.
- **Pruebas**: grafos sintéticos con k conocido; pruebas de canonicalización (UTM, AMP, mayúsculas); caso límite sin primarias.
- **Baseline**: cantidad de notas distintas y cantidad de medios distintos.
- **Demo de 90 s**: "esta afirmación aparece en N notas; tiene k fuentes independientes; estos son los cuellos".
- **Demo de 3 min**: armado del caso, anotación, cálculo, comparación con baseline, limitación de citas sin enlace.
- **Riesgos**: atribuir dependencia a una nota que en realidad tuvo acceso propio a la fuente.
- **Criterio de abandono**: si en tres casos reales la extracción automática recupera menos del 60% de las dependencias anotadas a mano.

### E2 · G04 Fragilidad ante coincidencias dudosas

- **Hipótesis de utilidad**: en un grafo de vínculos con vinculación probabilística, una fracción relevante de las conclusiones de camino corto depende de coincidencias con probabilidad menor a 0,9.
- **Implementación mínima**: Splink sobre datos sintéticos; barrido de umbrales; reporte de estabilidad por pregunta.
- **Arquitectura inicial**: registros → Splink → aristas con probabilidad → motor de preguntas → barrido → reporte.
- **Modelo de datos**: `Registro(id, fuente, atributos)`; `Match(a, b, p, explicación)`; `Pregunta(origen, destino, max_saltos)`; `Resultado(pregunta, umbral, existe, camino)`.
- **Fuentes**: generador sintético de Splink o entidades FtM de OpenSanctions (verificar licencia de uso).
- **Algoritmo central**: para cada umbral, componentes conexos y BFS; estabilidad = fracción de umbrales donde la conclusión se mantiene; aristas críticas = puentes del camino con baja probabilidad.
- **Pruebas**: errores sembrados; propiedad monótona (subir el umbral nunca agrega caminos).
- **Baseline**: umbral único fijo (práctica habitual).
- **Demo de 90 s**: "esta conexión existe solo si aceptás que estos dos registros son la misma empresa, con p = 0,62".
- **Demo de 3 min**: pipeline, curva de estabilidad, aristas críticas, cómo redactar la conclusión con su incertidumbre.
- **Riesgos**: uso sobre personas físicas; la demo usa entidades jurídicas o sintéticas.
- **Criterio de abandono**: si en datos reales las probabilidades son casi todas 0 o 1, la fragilidad es trivial.

### E3 · G17 Trayectoria de expedientes del Boletín Oficial (con extensión GT11)

- **Hipótesis de utilidad**: una parte no trivial de los actos de primera sección comparte expediente con otro acto o lo cita, y los componentes reconstruyen trayectorias que la búsqueda por texto no muestra.
- **Implementación mínima**: recolector respetuoso de un año de primera sección; extracción por expresiones regulares de expedientes (`EX-AAAA-NNNNNNNN- -APN-…`) y normas citadas; DuckDB; NetworkX.
- **Arquitectura inicial**: recolector con caché → parser → tablas `acto`, `expediente`, `cita` → grafo → CLI y vista de línea de tiempo.
- **Modelo de datos**: `Acto(id_aviso, fecha, organismo, tipo, número, hash_texto)`; `Expediente(id, año, código_organismo)`; `Cita(acto, norma_referida)`.
- **Fuentes**: Boletín Oficial; InfoLEG para resolver normas citadas.
- **Algoritmo central**: normalización de identificadores; componentes conexos en el grafo acto–expediente; orden temporal y latencias entre actos (T13).
- **Pruebas**: 200 actos anotados a mano; pruebas de expresiones regulares con variantes reales de formato.
- **Baseline**: búsqueda del número de expediente en el buscador oficial.
- **Demo de 90 s**: "esta resolución es el acto 5 de una cadena de 7; el tramo más largo fue de X meses en este organismo".
- **Demo de 3 min**: componentes más grandes del año, latencias por organismo, una historia contada con la línea de tiempo.
- **Riesgos**: términos de uso y carga del sitio; recolectar con límites de tasa.
- **Criterio de abandono**: si menos del 10% de los actos comparte expediente, o si la extracción falla en más del 20%.

### E4 · GT01 Cronología con relojes inciertos

- **Hipótesis de utilidad**: con tres o más fuentes de reloj, el sistema detecta contradicciones que una analista pasa por alto y produce intervalos más angostos que los rangos individuales.
- **Implementación mínima**: CLI que lee eventos y restricciones en JSONL y devuelve intervalos factibles y contradicciones explicadas.
- **Arquitectura inicial**: cargador → constructor del grafo de restricciones → solver → explicador → reporte con diagrama de Gantt.
- **Modelo de datos**: `Evento(id, fuente, t_reportado, incertidumbre)`; `Fuente(id, cota_de_desfase)`; `Restricción(a, b, tipo, cota, justificación, origen)`.
- **Fuentes**: caso sintético; un caso público con varias fuentes temporales.
- **Algoritmo central**: variables por evento y desfase por fuente; restricciones x\_j − x\_i ≤ c; Bellman–Ford o Floyd–Warshall; ciclo negativo = contradicción; subconjunto mínimo inconsistente por eliminación iterativa.
- **Pruebas**: con restricciones generadas desde tiempos reales, los intervalos contienen la verdad; al sembrar una restricción falsa, el ciclo la incluye.
- **Baseline**: orden por marca temporal reportada; Timesketch.
- **Demo de 90 s**: "estos tres videos no pueden estar en este orden; esta afirmación es la que lo rompe".
- **Demo de 3 min**: carga, intervalos, contradicción, corrección justificada, cronología final con incertidumbre.
- **Riesgos**: casos con víctimas; usar solo material ya publicado.
- **Criterio de abandono**: si en el caso público los intervalos resultantes no son más angostos que los de partida.

### E5 · GT02 Trazas de agentes como grafo de procedencia

- **Hipótesis de utilidad**: con trazas que registren dependencias de datos entre spans, un análisis de alcanzabilidad detecta todas las rutas de inyección sembradas con menos falsos positivos que una regla temporal simple.
- **Implementación mínima**: agente de prueba con tres herramientas (leer URL, leer archivo, escribir archivo), instrumentado con OpenTelemetry y atributos propios de ids de entrada y salida; conversión a PROV; análisis.
- **Arquitectura inicial**: agente → exportador JSONL → conversor span→PROV → etiquetado de confianza → análisis → reporte.
- **Modelo de datos**: `Entity(hash_contenido, origen, confianza)`; `Activity(span, tipo ∈ {inferencia, herramienta})`; `Agent(nombre)`; relaciones `used`, `wasGeneratedBy`, `wasInformedBy`; política de sumideros (herramientas con efectos).
- **Fuentes**: trazas propias rotuladas como sintéticas.
- **Algoritmo central**: propagación de etiqueta de contaminación hacia adelante; caminos mínimos desde entradas no confiables a sumideros.
- **Pruebas**: 20 corridas, 6 con inyección sembrada.
- **Baseline**: "hubo lectura externa antes de una escritura en la misma sesión".
- **Demo de 90 s**: "el agente escribió este archivo; esta página leída tres pasos antes es el origen; este es el camino".
- **Demo de 3 min**: instrumentación, grafo, comparación con la baseline, límite honesto: el contexto del modelo mezcla entradas.
- **Riesgos**: las trazas pueden contener datos sensibles; guardar hashes, no contenido.
- **Criterio de abandono**: si sin atributos de dependencia explícitos todo queda marcado como contaminado y no se mejora la baseline.

### E6 · T01 Deriva de contenido detrás de las citas

- **Hipótesis de utilidad**: en informes de ONG de 2018–2021, la fracción de citas que siguen respondiendo pero cambiaron sustancialmente es comparable a la de enlaces caídos.
- **Implementación mínima**: extractor de URLs de PDF; estado actual; captura histórica cercana a la fecha del informe; comparación; clasificación por reglas.
- **Arquitectura inicial**: PDF → URLs con fecha → sondeo → API CDX de Wayback → normalización de texto → comparación → CSV y HTML.
- **Modelo de datos**: `Cita(url, informe, fecha)`; `Observación(url, t, status, url_final, hash_texto)`; `Captura(url, t_wayback, hash_texto)`; `Clase ∈ {caída, redirigida, reescrita, estable, sin_referencia}`.
- **Fuentes**: informes públicos (incluidos los de seguimiento de gobierno abierto, S05); Wayback Machine.
- **Algoritmo central**: Jaccard sobre shingles del texto principal; umbrales calibrados con 50 casos anotados.
- **Pruebas**: anotación manual; páginas sintéticas con cambios de plantilla y de contenido.
- **Baseline**: verificador de enlaces rotos por código de estado.
- **Demo de 90 s**: "este informe tiene N citas: A caídas y B que siguen vivas pero ya no dicen lo que decían".
- **Demo de 3 min**: método, tres ejemplos lado a lado, limitaciones (páginas dinámicas, capturas faltantes).
- **Riesgos**: cuotas de la API de Wayback.
- **Criterio de abandono**: si tras normalizar, la precisión de la clase "reescrita" queda por debajo del 70%.

### E7 · T02 Latido esperado de datasets oficiales

- **Hipótesis de utilidad**: una proporción relevante de datasets con periodicidad declarada está atrasada sin que el portal lo muestre.
- **Implementación mínima**: recolección diaria de metadatos CKAN y del ETag o hash del recurso; evaluación de atraso.
- **Arquitectura inicial**: recolector programado → DuckDB → evaluador → reporte por organismo.
- **Modelo de datos**: `Dataset(id, organismo, periodicidad_declarada)`; `Snapshot(dataset, t, meta_modificado, hash_recurso, etag)`; `Estado(dataset, t, clase)`.
- **Fuentes**: API CKAN de datos.gob.ar y de los nodos de la red.
- **Algoritmo central**: atraso = ahora − último cambio real del recurso − período declarado; clases al día, atrasado y silencioso; agregación por organismo.
- **Pruebas**: verificación manual de 30 datasets.
- **Baseline**: la fecha de "última actualización" que muestra el portal.
- **Demo de 90 s**: "de N datasets mensuales, M no cambian hace más de tres períodos, aunque el portal los muestra como actualizados".
- **Demo de 3 min**: método, organismos, diferencia entre metadato y recurso, vínculo con el compromiso AR0107.
- **Riesgos**: bajos.
- **Criterio de abandono**: si metadato y recurso coinciden y los atrasos son marginales.

### E8 · S02 De la recomendación a la norma

- **Hipótesis de utilidad**: en un tema acotado, al menos un tercio de las recomendaciones a Argentina tiene normas candidatas identificables, y el sistema reduce a la mitad el tiempo de vinculación manual.
- **Implementación mínima**: exportación del UHRI filtrada por Argentina y tema; InfoLEG; ranking de candidatos; interfaz local de validación.
- **Arquitectura inicial**: ingesta → generador de candidatos → validación humana → grafo → métricas de latencia.
- **Modelo de datos**: `Recomendación(id, mecanismo, fecha, tema, texto)`; `Norma(id, tipo, fecha, título, síntesis)`; `Vínculo(recomendación, norma, tipo ∈ {implementa, relacionada, contradice}, validadora, justificación, fecha)`.
- **Fuentes**: UHRI; InfoLEG.
- **Algoritmo central**: similitud léxica (TF-IDF) restringida a normas posteriores, más referencias explícitas; supervivencia hasta la primera norma vinculada.
- **Pruebas**: conjunto de referencia de 30 recomendaciones vinculadas a mano.
- **Baseline**: búsqueda manual por palabra clave en InfoLEG.
- **Demo de 90 s**: "esta recomendación tuvo su primera norma relacionada X años después; esta otra, ninguna".
- **Demo de 3 min**: tema elegido, validación en vivo, latencias, advertencia: norma no es cumplimiento.
- **Riesgos**: lectura de "vinculada" como "cumplida".
- **Criterio de abandono**: precisión en los cinco primeros candidatos por debajo del 30%.

### E9 · S08 Causas de lesa humanidad detenidas

- **Hipótesis de utilidad**: con informes anuales sucesivos se pueden seguir causas individuales y medir permanencia por etapa con al menos 90% de vínculos correctos.
- **Implementación mínima**: descarga de informes PCCH; extracción de tablas; normalización de nombres; vinculación entre años; grafo de acumulaciones.
- **Arquitectura inicial**: PDFs → extractor de tablas → normalizador → vinculador → grafo de acumulación → análisis de supervivencia → reporte.
- **Modelo de datos**: `Causa(nombre_normalizado, jurisdicción, tribunal)`; `Observación(causa, fecha_informe, etapa)`; `Acumulación(causa_a, causa_b, fecha)`.
- **Fuentes**: informes estadísticos de la PCCH.
- **Algoritmo central**: vinculación por similitud de nombre y jurisdicción; componentes por acumulación; duración por etapa con censura a la derecha.
- **Pruebas**: revisión manual de los vínculos entre dos informes.
- **Baseline**: totales agregados de los propios informes.
- **Demo de 90 s**: "estas N causas figuran con debate oral en curso en cinco informes seguidos".
- **Demo de 3 min**: método, causas acumuladas como grafo, distribución de permanencia, límites.
- **Riesgos**: trabajar solo a nivel causa; validar el lenguaje con organismos de DD.HH. antes de publicar.
- **Criterio de abandono**: si los informes no tienen tablas por causa para todos los años (solo totales).

### E10 · S09 Reetiquetado presupuestario

- **Hipótesis de utilidad**: en jurisdicciones con reestructuraciones, una parte significativa del crédito cambia de programa sin continuidad por código, y el grafo de linaje permite seguirla.
- **Implementación mínima**: crédito por programa y actividad en cinco ejercicios; emparejamiento entre años; grafo; diagrama de flujo.
- **Arquitectura inicial**: descarga (Presupuesto Abierto / pysupuesto) → normalización → emparejador → grafo de linaje → reporte con diagrama Sankey.
- **Modelo de datos**: `Programa(año, jurisdicción, código, nombre, actividades[])`; `Linaje(origen, destino, tipo ∈ {continuidad, fusión, división, alta, baja}, evidencia, peso)`; `Crédito(programa, vigente, devengado)`.
- **Fuentes**: Presupuesto Abierto.
- **Algoritmo central**: emparejamiento bipartito ponderado por código, nombre y Jaccard de actividades (asignación húngara para 1 a 1; umbrales para fusiones y divisiones).
- **Pruebas**: revisión manual de una jurisdicción completa.
- **Baseline**: continuidad por código.
- **Demo de 90 s**: "este programa 'desapareció' en el año X; la mayoría de sus actividades sigue en este otro, con otro nivel de crédito".
- **Demo de 3 min**: linaje completo de un ministerio, crédito reclasificado, cautela interpretativa.
- **Riesgos**: leer reclasificación como manipulación.
- **Criterio de abandono**: si la continuidad por código explica más del 95% del crédito.

### Mantenimiento, ampliación y encaje con jurados

| Ficha | Mantenimiento posterior | Ampliación natural | Encaje habitual con jurados |
| --- | --- | --- | --- |
| E1 G01 | Bajo: corre a demanda | Extensión de navegador para verificadores | Problema claro, algoritmo elegante |
| E2 G04 | Bajo | Plugin para OpenAleph o FtM | Técnico, rigor visible |
| E3 G17 | Medio: recolección diaria | Alertas por expediente; GT11 | Impacto cívico local, datos reales |
| E4 GT01 | Bajo | Integración con Timesketch | Demo muy visual |
| E5 GT02 | Medio: convenciones inestables | Política de bloqueo en tiempo real | Tema de agentes, alta demanda |
| E6 T01 | Medio: sondeo periódico | Servicio para ONG con alertas | Fácil de entender |
| E7 T02 | Medio | GT05 sobre tableros | Encaja con gobierno abierto |
| E8 S02 | Alto: validación humana | Otros países de la región | Impacto en DD.HH. |
| E9 S08 | Medio: anual | Tablero de seguimiento | Impacto en memoria y justicia |
| E10 S09 | Medio: anual | Provincias | Datos de 30 años, historia fuerte |

## F. Matriz de riesgos éticos y de privacidad

Las cuatro finalistas con riesgo más alto son S03, S01, S08 y G09, porque tocan personas (víctimas, funcionarios, imputados o autoridades societarias); todas tienen una mitigación de diseño que es condición para construirlas, no un agregado. El resto trabaja sobre documentos, sistemas o entidades jurídicas.

| Código | Datos personales | Daño a terceros | Uso dual | Riesgo legal | Riesgo para investigadoras | Mitigación obligatoria |
| --- | --- | --- | --- | --- | --- | --- |
| S03 | Alto (víctimas) | Alto si se filtra | Medio | Alto (Ley 25.326, datos sensibles) | Medio | Cálculo local; hash con sal secreta compartida; nunca centralizar; demo solo sintética |
| S01 | Medio (funcionarios) | Medio (reputación) | Bajo | Bajo | Bajo | Resultado por organismo; supuestos de dependencia explícitos; sin rankings personales |
| S08 | Medio (imputados en procesos públicos) | Medio | Bajo | Medio | Medio | Nivel causa; lenguaje revisado con organismos de DD.HH.; no publicar listados de personas |
| G09 | Medio (autoridades societarias) | Medio | Medio (doxxing de vínculos) | Medio | Bajo | Salida centrada en entidades; personas solo si ya son públicas por su rol; justificación por arista |
| G04 | Medio si se usa con personas | Medio | Bajo | Bajo | Bajo | Demo con entidades o sintéticos; la herramienta reduce falsos vínculos, que es protector |
| G05 | Medio (testimonios) | Medio | Bajo | Bajo | Medio | Solo fuentes publicadas; no reidentificar testigos anonimizados |
| GT06 | Medio (custodios) | Bajo | Bajo | Bajo | Medio | Seudónimos de custodios; registro local cifrado |
| GT01 | Bajo | Bajo | Medio (reconstruir movimientos) | Bajo | Bajo | Aplicar a eventos, no a seguimiento de personas |
| GT02 | Bajo-medio (contenido de prompts) | Bajo | Bajo | Bajo | Bajo | Guardar hashes, no contenido; retención corta |
| T04 | Bajo-medio | Bajo | Bajo | Bajo | Bajo | Igual que GT02 |
| T08 | Bajo (solo estado de URLs) | Bajo | Medio (mapear qué se borra) | Bajo | Bajo | No descargar contenido; publicar agregados |
| G01, G17, T01, T02, T13, GT05, GT07, S02, S09 | Bajos o nulos | Bajo | Bajo | Bajo (respetar términos y carga) | Bajo | Límites de tasa; caché; atribución de fuentes |

### Riesgos transversales

- **Pertenencia a una red no es culpabilidad**: ninguna salida usa adjetivos como "sospechoso" o "vinculado a" sin la arista concreta y su fuente.
- **Seguridad de quien investiga**: las herramientas que sondean sitios oficiales o plataformas deben poder correr sin identificar a la organización (agente de usuario neutral, sin cuentas personales), dentro de los términos de uso.
- **Retención**: cada prototipo declara qué guarda y cuánto tiempo; por defecto, 90 días para observaciones crudas y permanente para agregados.
- **Datos sintéticos**: rotulados en el nombre del archivo y en la interfaz; nunca mezclados con datos reales en la misma tabla sin columna de origen.

## Relación con tu portfolio (Bloque XI)

No examiné código en esta sesión. Lo que sigue se apoya solo en las descripciones que tengo de cada proyecto; cada reutilización es una hipótesis \[I\] a confirmar contra el repositorio. Donde no sé lo suficiente, lo digo.

### Reutilizaciones probables

| Proyecto (según su descripción) | Componente descrito | Ideas que podría acelerar | Qué habría que verificar |
| --- | --- | --- | --- |
| VIGÍA | Operaciones de cadena de custodia; salida STIX 2.1; veredicto ABSTAIN como estado de primera clase | GT06 (custodia sin huecos); GT01 y G05 (devolver "no determinable" en vez de forzar un orden) | Si el módulo de custodia modela traspasos con intervalos o solo hashes |
| Janus | Telemetría de eventos, *context graph*, motor de scoring determinístico, cadena SHA-256 con HMAC opcional y verificador externo independiente; el LLM narra pero no decide | T05 (bitácora de agentes), GT02 (telemetría + grafo), GT06 | Si la cadena y el verificador son separables como librería |
| STYLOMETRY-CI | Compuerta forense de autoría | G01: detectar notas que reproducen la misma gacetilla sin enlazarla, que es el principal riesgo de falsación de G01 | Si el núcleo funciona sobre textos periodísticos cortos en español |
| MUTANTE | Corredor de campañas con checkpoint, concurrencia asíncrona e indexación | T04 y GT02: correr lotes de trazas con fallas sembradas y medirlas | Acoplamiento con Elasticsearch y Vertex |
| KRAKADYL | Agente de investigación forense orientado a la disciplina previa (condiciones, tareas pendientes, supuestos no verificados) | T14 (ledger de lo no recolectado) y G06 (soportes únicos) encajan con su objetivo de evitar ABSTAIN evitables | Formato interno de tareas y supuestos |
| VELO | Atestación de conocimiento cero de veredictos forenses en Midnight | GT06 (atestar integridad de custodia sin publicar evidencia); posible extensión de S03 | Para S03 haría falta intersección privada de conjuntos, que no es lo mismo que atestar un veredicto |
| FORGE | Filosofía de "minimalismo probatorio" | No sé lo suficiente de su implementación para proponer reutilizaciones concretas | Qué componentes tiene |
| Colección de skills | En esta sesión figuran skills de reconstrucción de líneas de tiempo, cadenas de auditoría a prueba de alteraciones, procedencia de afirmaciones, degradación honesta y escritura defendible | GT01 ↔ reconstrucción de líneas de tiempo; T05/GT06 ↔ cadena de auditoría; G01/G06 ↔ procedencia de afirmaciones; T02/T14 ↔ degradación honesta; todos los informes ↔ escritura defendible | Vi nombres y descripciones, no el contenido |

### Ideas fuera de tus patrones habituales

Tu portfolio se concentra en forense, procedencia, agentes y seguridad. Estas finalistas y reservas salen de ese eje y te obligan a otro tipo de evidencia:

- **S09 Reetiquetado presupuestario**: economía pública y series largas; nada de forense.
- **S08 Causas de lesa humanidad**: trabajo documental sobre el proceso de memoria, verdad y justicia; exige diálogo con organismos.
- **GT07 Cobertura de archivado**: estadística de captura–recaptura aplicada a la web.
- **T03 Huecos del tiempo real de colectivos**: movilidad urbana y accesibilidad.
- **G10 Retracciones de segundo orden** y **G19 Coherencia en Wikidata**: integridad del conocimiento científico y enciclopédico.
- **S02 De la recomendación a la norma**: sistema internacional de DD.HH. y derecho interno, con validación humana como núcleo.

Si querés combinar las dos cosas, la pareja con más sentido es **G17 + S02**: una sola base técnica (Boletín Oficial e InfoLEG como grafo) sirve a un proyecto cívico (trayectorias administrativas) y a uno de DD.HH. (seguimiento de recomendaciones).

## G. Propuesta modular de skills

La propuesta son diez skills encadenadas en un ciclo abductivo: descubrir → contrastar con lo existente → modelar → elegir algoritmo o instrumentación → evaluar riesgos → diseñar el experimento → decidir. Los nombres van en inglés para que encajen con tu colección; la especificación está en español. Ninguna skill produce una afirmación sin su etiqueta epistémica (\[D\], \[C\], \[I\], \[H\], \[P\]).

### Orden de ejecución

1. `problem-discovery`
2. `prior-art-survey`
3. `differentiation-check` (puede devolver al paso 1)
4. `graph-modeling` y/o `telemetry-design`
5. `algorithm-selection`
6. `sociotechnical-analysis`
7. `rights-impact-review` (puede vetar)
8. `experiment-design`
9. `mvp-gate` (decide construir, reformular o abandonar)

### 1. `problem-discovery`

- **Propósito**: convertir una observación o un dominio en un problema delimitado con usuario, situación y evidencia.
- **Trigger**: "buscame problemas en…", "qué se podría construir para…", inicio de una investigación para hackathon.
- **Inputs**: dominio, restricciones (tiempo, país, datos), exclusiones éticas.
- **Outputs**: fichas de problema con los campos 1–5 del atlas y etiqueta de evidencia por afirmación.
- **Verificaciones**: cada problema tiene una fuente \[D\] o queda marcado \[I\]; el problema entra en una oración; existe un usuario nombrable con una situación concreta.
- **Dependencias**: búsqueda web; plantilla de ficha.

### 2. `prior-art-survey`

- **Propósito**: encontrar alternativas existentes y describir su alcance, licencia, mantenimiento y límites.
- **Trigger**: después de 1, o ante "¿esto ya existe?".
- **Inputs**: ficha de problema; palabras clave en varios idiomas.
- **Outputs**: tabla de alternativas con enlace, licencia, última actividad y limitación verificable.
- **Verificaciones**: al menos tres consultas distintas por idioma; estado de mantenimiento comprobado con fecha; prohibido concluir "no existe" (solo "no encontrado con estas consultas").
- **Dependencias**: búsqueda web, GitHub, PyPI/npm.

### 3. `differentiation-check`

- **Propósito**: decidir la clase de novedad (A–E) con argumento y evidencia.
- **Trigger**: después de 2.
- **Inputs**: ficha + tabla de alternativas.
- **Outputs**: clase de novedad, diferencia verificable en una oración y prueba que la demostraría.
- **Verificaciones**: la diferencia debe ser observable en una demo; si solo es de interfaz o de idioma, se marca D o E.
- **Dependencias**: 2.

### 4a. `graph-modeling`

- **Propósito**: decidir si un grafo se justifica y, si sí, qué tipo.
- **Trigger**: aparece "red", "vínculo", "conexión", "cadena", "dependencia".
- **Inputs**: pregunta central y datos disponibles.
- **Outputs**: prueba de pertinencia (las cuatro preguntas de la sección de grafos), esquema de nodos y aristas con atributos de fuente, tiempo y certeza, y baseline tabular.
- **Verificaciones**: existe una consulta que la baseline tabular no responde; cada arista tiene fuente; las aristas temporales respetan el orden del tiempo.
- **Dependencias**: 1.

### 4b. `telemetry-design`

- **Propósito**: diseñar qué emitir, con qué esquema, cadencia, retención y modelo de huecos.
- **Trigger**: "monitorear", "medir en el tiempo", "trazas", "logs".
- **Inputs**: proceso a observar; restricciones de privacidad.
- **Outputs**: esquema de eventos (compatible con nombres OTel cuando aplique), tasa esperada por fuente, tipología de pérdida (tabla de la sección de telemetría), política de retención.
- **Verificaciones**: cada métrica declara cómo podría manipularse (Campbell–Goodhart); los huecos tienen explicación alternativa; datos sintéticos rotulados.
- **Dependencias**: 1; skill de degradación honesta de tu colección.

### 5. `algorithm-selection`

- **Propósito**: elegir el algoritmo más simple que responda, con preferencia por métodos deterministas y explicables.
- **Trigger**: después de 4a o 4b.
- **Inputs**: modelo y pregunta.
- **Outputs**: algoritmo, complejidad, librería, y por qué no se usa aprendizaje automático (o por qué sí).
- **Verificaciones**: propiedad testeable del algoritmo (monotonía, invariantes, casos con respuesta conocida); costo en el tamaño real de los datos.
- **Dependencias**: 4a/4b.

### 6. `sociotechnical-analysis`

- **Propósito**: leer el problema con teoría social pertinente y detectar cómo el poder condiciona qué datos existen.
- **Trigger**: el problema involucra instituciones, registros oficiales, comunidades o redes sociales.
- **Inputs**: ficha, fuentes de datos.
- **Outputs**: quién produce el dato y con qué incentivo, qué queda invisible, qué autor o marco cambia el diseño (y cuáles no aportan).
- **Verificaciones**: cada referencia teórica modifica una decisión concreta del diseño; se descartan citas decorativas; se distingue observado, inferido, correlación y causalidad.
- **Dependencias**: 1, 4.

### 7. `rights-impact-review`

- **Propósito**: evaluar riesgos éticos, legales y de privacidad, con capacidad de veto.
- **Trigger**: siempre antes de 8; obligatoria si hay personas físicas, víctimas, testigos o comunidades.
- **Inputs**: modelo de datos, salidas previstas, usuarios.
- **Outputs**: fila de la matriz F, mitigaciones obligatorias y veredicto (seguir, seguir con condiciones, vetar).
- **Verificaciones**: ninguna salida atribuye culpabilidad por pertenencia a una red; no hay perfilado de personas vulnerables; se revisa uso dual; se identifica la norma de datos personales aplicable (en Argentina, Ley 25.326).
- **Dependencias**: 4, 6.

### 8. `experiment-design`

- **Propósito**: producir la ficha de prototipo (sección E) con hipótesis falsable.
- **Trigger**: después de 7 sin veto.
- **Inputs**: todo lo anterior.
- **Outputs**: hipótesis, implementación mínima, arquitectura, modelo, pruebas, baseline, demos de 90 s y 3 min, criterio de abandono.
- **Verificaciones**: la hipótesis puede fallar con datos obtenibles en el plazo; la baseline es construible; la demo no depende de datos inventados sin rotular.
- **Dependencias**: 1–7; skill de reconstrucción de líneas de tiempo cuando aplique.

### 9. `mvp-gate`

- **Propósito**: decidir con evidencia si construir, reformular o abandonar, y registrar la decisión.
- **Trigger**: al terminar un spike de 4–8 horas, o al acercarse la fecha de entrega.
- **Inputs**: resultados del spike frente al criterio de abandono.
- **Outputs**: decisión, evidencia, condición que la reabriría.
- **Verificaciones**: la decisión cita el resultado medido, no impresiones; si se abandona, queda registrado qué se aprendió.
- **Dependencias**: 8; skill de registro de decisiones de tu colección.

### Artefactos compartidos

- Plantilla de ficha del atlas (18 campos más novedad).
- Esquema de etiquetas epistémicas.
- Tabla de tipología de pérdida en telemetría.
- Prueba de pertinencia de grafos.
- Matriz de riesgos (columnas de la sección F).

## H. Bibliografía

Todas las fuentes se consultaron el 5 de noviembre de 2026 a través de un buscador web; leí los extractos devueltos, no siempre el documento completo. Las marcadas como secundarias reportan un dato de otra fuente que conviene verificar en el original. Las referencias clásicas sin enlace (Weber, Foucault, Bourdieu, Goffman, Granovetter, Burt, Latour, Ostrom, Dung, Allen, Menger, Fellegi–Sunter) se citan como conocimiento general \[C\].

### Evidencia, preservación y DD.HH.

- Human Rights Center UC Berkeley y ACNUDH, [*Berkeley Protocol on Digital Open Source Investigations*](https://humanrights.berkeley.edu/projects/berkeley-protocol-on-digital-open-source-investigations/) (2020, actualizado 2022).
- Kayyali, D. (2022). [Digital Memory, Evidence, and Social Media: Lessons Learned from Syria](https://sociologica.unibo.it/article/download/15383/14818?inline=1). *Sociologica*.
- AFP vía [Jordan Times](https://jordantimes.com/node/340988): borrados de videos sirios en YouTube.
- Chapekis, Bestvater, Remy y Rivero (2024). [*When Online Content Disappears*](https://www.pewresearch.org/data-labs/2024/05/17/when-online-content-disappears/). Pew Research Center.
- HRDAG: [blocking y MSE en Siria (arXiv 1510.07714)](https://arxiv.org/pdf/1510.07714); [ICIJ sobre MSE en Filipinas](https://www.icij.org/inside-icij/2019/09/counting-the-dead-how-statistics-can-find-unreported-killings/).
- HURIDOCS: [Uwazi](https://huridocs.org/?p=237); [directorio de herramientas de seguimiento](https://archives.geneva-academy.ch/geneva-humanrights-platform/tracking-tools.html) (Geneva Academy); [UPR Info Database](https://www.geneva-academy.ch/news/detail/695-in-highlight-upr-info-database).
- Procuraduría de Crímenes contra la Humanidad: [informe estadístico 2024](https://www.fiscales.gob.ar/wp-content/uploads/2024/12/Informe-estadistico-de-diciembre-2024-de-la-PCCH.pdf); [informe 2025](https://www.fiscales.gob.ar/wp-content/uploads/2025/12/Lesa-Informe-estadistico-de-diciembre-2025-de-la-PCCH.pdf).
- Forensic Architecture, [TimeMap](https://github.com/forensic-architecture/timemap).
- [Timesketch](https://pypi.org/project/timesketch/20260617/) (PyPI).

### Corrupción, contratación y redes

- Wachs, Fazekas y Kertész (2021). [Corruption risk in contracting markets: a network science perspective](https://ar5iv.labs.arxiv.org/html/1909.08664). *Int. J. Data Science and Analytics*.
- Fazekas y Wachs (2020). [Corruption and the Network Structure of Public Contracting Markets across Government Change](https://cogitatiopress.com/politicsandgovernance/article/view/2707). *Politics and Governance* 8(2).
- Open Contracting Partnership: [Red Flags in Public Procurement (2024)](https://open-contracting.org/?p=26247); [Cardinal](https://www.open-contracting.org/2024/06/12/cardinal-an-open-source-library-to-calculate-public-procurement-red-flags/).
- Open Ownership, [BODS v0.4](https://standard.openownership.org/es/main/about).
- OpenSanctions: [modelo de entidades](https://www.opensanctions.org/docs/entities/); [FollowTheMoney 4.0](https://www.opensanctions.org/articles/2025-07-13-followthemoney); [deduplicación](https://www.opensanctions.org/articles/2021-11-11-deduplication).
- OCCRP, [FAQ de Aleph Pro](https://www.occrp.org/en/announcement/aleph-pro-frequently-asked-questions-on-the-future-of-occrps-investigative-data-platform); DARC, [OpenAleph](https://openaleph.org/blog/2025/openaleph-commits-to-the-commons/).
- C4ADS, [followthemoney-neomodel](https://c4ads.org/tech-bulletin/bringing-follow-the-money-into-the-graph-a-new-neo4j-tool/).
- Berlusconi, G. (2013). [Artículo sobre fuentes judiciales y medidas de centralidad en redes criminales (título no verificado)](https://econpapers.repec.org/RePEc:taf:fglcxx:v:14:y:2013:i:1:p:61-81) *Global Crime* 14(1).
- Catlin et al. (2025). [The Game is the Game: dynamic network analysis in criminal networks](https://arxiv.org/html/2509.08028v1). arXiv.
- Yeung et al. (2025). [Artículo sobre intervención en redes criminales con datos incompletos (título no verificado)](https://epjdatascience.springeropen.com/articles/10.1140/epjds/s13688-025-00553-x). *EPJ Data Science* 14:37.
- Hood y Piotrowska (2021). [Goodhart's Law and the Gaming of UK Public Spending Numbers](https://ora.ox.ac.uk/objects/uuid:e5fe165e-18aa-4d38-b4b3-a24287be19e1/files/sqf85nb34z). *Public Performance & Management Review* 44(2).
- Manheim, D. (2018). [Building Less Flawed Metrics](https://mpra.ub.uni-muenchen.de/98288/). MPRA.

### Argentina: datos y normas

- datos.gob.ar: [Base InfoLEG](https://datos.gob.ar/dataset/justicia-base-infoleg-normativa-nacional/archivo/justicia_bf0ec116-ad4e-4572-a476-e57167a84403); [Registro de Audiencias](https://datos.gob.ar/hr/dataset/otros-registro-unico-audiencias-gestion-intereses); [COMPR.AR](https://datos.gob.ar/zh_CN/dataset/jgm-sistema-contrataciones-electronicas/archivo/jgm_4.17); [DDJJ OA](https://datos.gob.ar/dataset/justicia-declaraciones-juradas-patrimoniales-integrales-caracter-publico).
- Open Contracting Data Registry: [CABA](https://data.open-contracting.org/en/publication/17); [Mendoza](https://data.open-contracting.org/en/publication/137).
- Chequeado: [registro de audiencias](https://chequeado.com/el-explicador/registro-de-audiencias-de-funcionarios-como-funciona-y-por-que-hasta-el-estado-destaca-que-no-es-tan-util/); [aportes de contratistas](https://chequeado.com/investigaciones/macri-recibio-3-millones-de-contratistas-del-estado-para-su-campana-electoral/).
- HCDN, [Proyecto 7200-D-2022](https://www4.hcdn.gob.ar/dependencias/dsecretaria/Periodo2022/PDF2022/TP2022/7200-D-2022.pdf).
- OGP: [AR0107](https://www.opengovpartnership.org/members/argentina/commitments/AR0107/); [AR0081](https://www.opengovpartnership.org/members/argentina/commitments/AR0081/).
- AAIP, [Sistema de Seguimiento de Solicitudes (Res. 148/2025)](https://www.argentina.gob.ar/node/474669); Consejo de la Magistratura, [informe jul–sep 2025](https://consejomagistratura.gov.ar/wp-content/uploads/2025/12/Informe-para-Agencia-de-Acceso-jul_ago_sep-2025.pdf).
- Boletín Oficial, [aviso AAIP 305397](https://www.boletinoficial.gob.ar/detalleAviso/primera/305397/1).
- Olmos, M. [On Regulatory Simplification](https://martinolmos.github.io/data_ict/en/posts/on-regulatory-simplification/index.html).
- [pysupuesto](https://pypi.org/project/pysupuesto) (PyPI).
- GCBA, [API de transporte](https://anypoint.mulesoft.com/exchange/portals/api-gcba/083c0681-d272-40f7-b1ff-90dd5952a0de/api-plataforma-datos-transporte/).
- Secundarias: [InfobelPro sobre IGJ](https://www.infobelpro.com/en/blog/argentina-company-lookup-guide); [indicadores.ar](https://indicadores.ar/empresa/30711010358).

### Telemetría, procedencia y software

- Welch et al. (2022). [Hot spots of unseen fishing vessels](https://escholarship.org/content/qt3xs2q931/qt3xs2q931.pdf). *Science Advances*.
- Barbeau et al., [evaluación de feeds GTFS-realtime](https://rosap.ntl.bts.gov/view/dot/37446/dot_37446_DS1.pdf) (NITC); Open Innovations, [trip\_id faltantes](https://boduf.discourse.group/t/missing-trip-id-s-in-gtfs-rt-data/124); [Cal-ITP](https://reports.dds.dot.ca.gov/gtfs_schedule/2024/11/360/).
- MuckRock, [datos de tiempos de respuesta](https://www.muckrock.com/news/archives/2017/mar/14/muckrock-foia-response-data/).
- OpenTelemetry GenAI: [verificación de estado, dev.to](https://dev.to/azena-ai/opentelemetrys-genai-semantic-conventions-are-not-stable-yet-heres-what-actually-shipped-in-2026-3mke); [Dash0](https://www.dash0.com/knowledge/opentelemetry-genai-semantic-conventions-explained).
- EDGI, [web-monitoring](https://github.com/edgi-govdata-archiving/web-monitoring).
- W3C PROV y [prov (Python)](https://prov.readthedocs.io/en/latest/readme.html).
- Steer et al. (2024). [Raphtory](https://networkscienceinstitute.org/publications/raphtory-the-temporal-graph-engine-for-rust-and-python). *JOSS*.
- Linacre et al. (2022). [Splink](https://doi.org/10.23889/ijpds.v7i3.1794). *IJPDS* 7(3).
- Crossref y Retraction Watch, [apertura de la base](https://retractionwatch.com/2023/09/16/weekend-reads-crossref-acquires-the-retraction-watch-database-italy-ministers-papers-scrutinized-carlo-croce-goes-to-court-yet-again/).
- C2PA: [adopción 2026](https://www.softwareseni.com/c2pa-adoption-in-2026-hardware-platforms-and-verification-reality); [radar de procedencia digital](https://rubinlake.com/en/technology-radar/ai-security-and-governance/digital-provenance) (secundarias).
- tj-actions/changed-files: [OSV GHSA-mrrh-fwg8-r2c3](https://osv.dev/vulnerability/GHSA-mrrh-fwg8-r2c3); [oss-sec](https://seclists.org/oss-sec/2025/q1/227).
- MCP: [mcp-scan](https://appsecsanta.com/mcp-scan); [mcp-integrity](https://pypi.org/project/mcp-integrity/).
- OpenSSF, [Criticality Score](https://openssf.org/?p=3208).

## I. Preguntas abiertas

Las preguntas están ordenadas por cuánto cambian la shortlist si se responden. Las primeras cinco pueden cerrarse en una tarde cada una con una consulta directa a la fuente.

### Datos (pueden subir o bajar finalistas)

1. ¿Qué tipos de relación distingue el esquema de las bases complementarias de InfoLEG (modifica, deroga, reglamenta, complementa)? Afecta G02, G12, G17 y S02.
2. ¿COMPR.AR y CONTRAT.AR publican todos los oferentes por proceso o solo adjudicatarios? Decide si G11 sube.
3. ¿Las unidades compradoras de COMPR.AR mantienen identificadores tras las reestructuraciones ministeriales de 2023–2024? Decide G03.
4. ¿El dataset del registro de audiencias incluye un campo confiable de "representado"? Decide G18.
5. ¿Los informes de la PCCH traen tablas por causa todos los años o solo totales y debates en curso? Decide el alcance de S08.
6. ¿El número correlativo de los expedientes electrónicos es monótono en el tiempo? Decide la resolución de T13.
7. ¿El tablero de la AAIP (Res. 148/2025) es público y cubre a todos los poderes? Decide si T06 es redundante.
8. ¿Qué publica ACUMAR (u otro organismo ambiental) sobre denuncias e inspecciones? Decide S06.
9. ¿El registro MAPPAP permite consultas masivas? Decide G08.
10. ¿Cuál es la licencia de uso de los datos de OpenSanctions para un proyecto de hackathon?

### Estado del arte (pueden bajar la clase de novedad)

11. ¿Webrecorder o Browsertrix ya reportan completitud de captura por recurso? Afecta T09.
12. ¿Existe una herramienta abierta que propague la incertidumbre de vinculación a conclusiones de caminos? Afecta G04 (búsqueda en inglés, alemán y ruso).
13. ¿Hay trabajos que modelen cronologías forenses como restricciones de diferencia con desfase por fuente? Afecta GT01.
14. ¿Qué cubren hoy indicadores.ar y Socios.red sobre penalización de hubs? Afecta G09.
15. ¿Hay implementaciones abiertas de vínculo entre recomendaciones del UHRI y legislación nacional en otros países de la región? Afecta S02.

### Método

16. Para S01, ¿qué fuente independiente del registro de audiencias tiene detalle suficiente (agendas oficiales, comunicados, prensa) y cuánta dependencia hay entre ellas? Sin respuesta, el estimador no es defendible.
17. Para GT02, ¿qué atributos de dependencia de datos pueden emitirse sin modificar el framework del agente? Es lo que separa el éxito del fracaso de la hipótesis.
18. Para T08, ¿cómo distinguir de forma confiable "borrado" de "requiere sesión" en cada plataforma?
19. ¿Qué jurados y criterios tiene el próximo hackathon objetivo? Cambia el peso entre impacto cívico, rigor técnico y demo visual.

### Sobre vos (para afinar el orden, no para asumir)

20. ¿Querés priorizar ideas que reutilicen tus componentes existentes o ideas fuera de tu eje para ampliar el portfolio?
21. ¿Hay restricciones de idioma del hackathon (demo en inglés) que favorezcan ideas con datos no argentinos?

### Estado del documento

Entregables A a I completos en esta versión. Si hace falta profundizar, el siguiente paso natural es verificar las preguntas 1 a 5 y actualizar la shortlist sin renumerar las ideas.
