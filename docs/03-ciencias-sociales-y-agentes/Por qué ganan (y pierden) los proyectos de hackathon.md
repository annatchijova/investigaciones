# Por qué ganan (y pierden) los proyectos de hackathon

Nov 5, 2026 · @Anna Tchijova

## Resumen ejecutivo

Un proyecto técnicamente superior pierde cuando el jurado no puede percibir esa superioridad en el tiempo, el formato y el estado mental en que evalúa. No hay estudios que aíslen causalmente qué gana un hackathon; la evidencia útil viene de contextos vecinos (pitch a inversores, paneles de I+D, peer review) y de rúbricas oficiales.

Lo mejor sustentado:

- **La claridad amplifica la calidad, no la reemplaza.** En un experimento de campo, entrenar el pitch mejoró la evaluación de ideas buenas y empeoró la de ideas malas ante inversores experimentados.
- **Los evaluadores primero descartan.** Buscan un defecto fatal antes de ponderar virtudes: demo rota, problema ininteligible, "esto ya existe".
- **La novedad alta se penaliza**, más cuando el panel está cargado. Lo nuevo necesita anclarse en algo conocido.
- **El acuerdo entre jurados es bajo.** Ganar y perder tienen un componente aleatorio grande; un solo resultado no enseña casi nada.
- **La incertidumbre dicha con números casi no daña la credibilidad de la fuente.** Las advertencias vagas dañan más.
- **El engaño se detecta después.** Los casos documentados de descalificación ocurrieron en verificaciones posteriores al premio.

De ahí sale el criterio central del informe: **optimizar honestamente es bajar el costo de verificar lo verdadero y nunca bajar el costo de creer lo falso.** Eso se traduce en señales caras de falsificar (demo con entrada del jurado, repo reproducible, denominadores, limitaciones dichas antes de que las pregunten) y en una auditoría obligatoria de afirmaciones.

Cómo leer los niveles de evidencia: cada hallazgo de la tabla lleva una letra (A a D) y una estimación de cuánto se traslada a hackathones. Las recomendaciones son inferencias desde esos hallazgos y están marcadas como tales cuando la evidencia es indirecta. El Bloque IX y los SKILL.md entregados convierten todo esto en 15 skills.

## Bloque I — Evidencia empírica

No existe, hasta donde pude encontrar, ningún estudio revisado por pares que aísle causalmente qué hace ganar un hackathon. Lo que sí hay es: (a) investigación sobre hackathones centrada en resultados posteriores (continuidad, aprendizaje), (b) investigación sobre evaluación en contextos vecinos (pitch a inversores, paneles de I+D, peer review, concursos con jurado) y (c) rúbricas oficiales. Cualquier afirmación del tipo "los ganadores hacen X" tiene que leerse con esa limitación.

### I.1 Qué dice la literatura sobre hackathones

- **Continuidad, no victoria.** El estudio más grande con datos de Devpost (Nolte, Chounta y Herbsleb, CSCW 2020) analiza qué pasa con los proyectos después del evento: más de un tercio muestra alguna actividad posterior, pero cae rápido y solo cerca del 5% sigue activo pasados cinco meses ([Nolte et al. 2020](https://par.nsf.gov/servlets/purl/10284449)). No modela qué determina ganar.
- **Ganar como predictor de continuidad.** Una tesis de la Universidad de Tartu sobre más de 60.000 proyectos de hackathones universitarios reportó que la importancia de ganar fue el único factor significativo asociado a la continuidad ([Tartu, DSpace](https://dspace.ut.ee/items/a28833b7-c2b8-40b6-9742-ec3d89f82f4b)). Es una tesis, no un artículo con revisión por pares, y la dirección causal es ambigua: los proyectos que el equipo ya planeaba continuar pueden ser también los mejor preparados.
- **Actividad de código concentrada.** Un análisis de 11.889 proyectos de hackathones MLH en EE.UU. (2018-2019) encontró que alrededor del 77% de los commits ocurre en la primera semana y que solo el 7% tiene actividad seis meses después ([SSRC Just Tech](https://just-tech.ssrc.org/?p=4573)).
- **Revisión sistemática.** Medina Angarita y Nolte (CollabTech 2020) sistematizan resultados y aspectos de diseño de hackathones y señalan que la mayoría de los estudios mira eventos singulares en dominios específicos ([Springer](https://link.springer.com/10.1007/978-3-030-58157-2_4)). Ninguno de los aspectos revisados es "qué rasgos del proyecto predicen premio".
- **Creatividad a escala.** Un preprint de 2025 armó un dataset de 193.353 proyectos de Devpost (2009-2024) y marcó 3.148 ganadores dentro de un subconjunto de 10.363 con repositorio analizable ([arXiv 2503.04290](https://arxiv.org/pdf/2503.04290)). Es útil como fuente de datos; no es evidencia causal y no está revisado por pares.
- **Intentos amateurs de predicción.** Hubo proyectos de hackathon que scrapearon Devpost para predecir ganadores; uno concluyó que casi no había correlación entre los datos cuantitativos extraíbles de un Devpost y ganar ([GitHub, jakevossen5](https://github.com/jakevossen5/this-hackathon-project-isnt-real)). Es una anécdota, pero una informativa: lo visible en la ficha no alcanza para explicar el resultado.

### I.2 Evidencia de contextos vecinos (mayor rigor, menor validez ecológica)

- **Entrenar el pitch amplifica la calidad, no la sustituye.** Clingingsmith y Shane (Management Science, 2018) hicieron un experimento de campo con pitches de 90 segundos ante inversores acreditados. El entrenamiento subió el uso de buenas prácticas en un tercio de desvío estándar; mejoró la evaluación de inversores experimentados solo para ideas de alta calidad y la empeoró para las demás ([PDF](https://files.cercomp.ufg.br/weby/up/1267/o/Clingingsmith_and_Shane_-_2017_-_Training_Aspiring_Entrepreneurs_to_Pitch_Experienced_Investors_Evidence_from_a_Field_Experiment_in_the_United_States.pdf?1656363197)). Es el hallazgo más importante para tu pregunta: un pitch claro le permite al evaluador experto ver mejor la calidad real, en ambas direcciones.
- **Preparación, no pasión.** Chen, Yao y Kotha (Academy of Management Journal, 2009) encontraron en laboratorio y en campo que la preparación percibida, y no la pasión exhibida, influyó en decisiones de inversores de riesgo ([resumen](https://data.zhenzhi.com/details/1/861740525/1/3)).
- **Eliminación por aspectos.** Maxwell, Jeffrey y Lévesque (Journal of Business Venturing, 2011) codificaron 150 interacciones de Dragons' Den: los inversores no ponderan muchos atributos, descartan primero lo que tiene un defecto fatal ([EconPapers](https://econpapers.repec.org/RePEc:eee:jbvent:v:26:y:2011:i:2:p:212-225)). Implicación: el primer objetivo de un pitch es no activar un descarte ("no funciona", "no entiendo qué es", "esto ya existe").
- **Sesgos de presentador.** Brooks, Huang, Kearney y Murray (PNAS, 2014) hallaron en campo y en experimentos preferencia por pitches presentados por hombres, sobre todo atractivos, con contenido idéntico ([MIT DSpace](https://dspace.mit.edu/handle/1721.1/91283)). Una replicación registrada en 2025 confirmó la penalización a mujeres pero no el efecto positivo del atractivo ([FORRT](https://forrt.org/flora-replication-atlas/doi/10.1073/pnas.1321202111/)). El sesgo existe; su forma exacta es discutida.
- **Bajo acuerdo entre evaluadores.** En una réplica del proceso de los NIH, 43 revisores evaluando las mismas 25 propuestas no mostraron acuerdo, ni cualitativo ni numérico ([Pier et al. 2018, PNAS](https://pubmed.ncbi.nlm.nih.gov/29507248/)). Si expertos con instrucciones idénticas no coinciden en propuestas de buena calidad, en un hackathon con jurados heterogéneos y minutos por proyecto el componente aleatorio debe ser grande.

### I.3 Qué dicen las rúbricas oficiales

Las rúbricas públicas convergen en cuatro ejes con nombres variables: originalidad/idea, implementación técnica, impacto potencial y diseño o presentación. Ejemplos verificados:

| Evento | Criterios | Pesos |
| --- | --- | --- |
| [Okta Hackathon 2021 (Devpost)](https://devforum.okta.com/t/what-are-the-judging-criteria-for-the-hackathon/15842) | Creatividad/originalidad; implementación (incluye uso del producto del sponsor); impacto potencial | Iguales; con etapa previa de elegibilidad |
| [HackCC 2025 (Devpost)](https://kelaenderkoe.pages.dev/patterns-https-hackcc-2025.devpost.com/rules) | Complejidad técnica (saber explicar por qué elegiste la tecnología); impacto; diseño e implementación | No publicados |
| [EUvsVirus 2020, guía interna de jurados](https://moodle2.units.it/pluginfile.php/395562/mod_resource/content/0/LAB%204%2020%20maggio%20Juror%20Guide%20Kit%20%281%29.pdf) | Impacto; complejidad técnica y novedad; completitud del prototipo; plan de negocio | 40 / 20 / 20 / 20, con anclas de 1 a 5 |
| [Hacktivate (CarWale)](https://hacktivate.carwale.com/judging-criteria.html) | Impacto; solución; otros | 30% / 35% / resto |
| [Mozilla Jetpack for Learning](https://m.wiki.mozilla.org/Education/Projects/JetpackForLearning/Criteria) | Calidad de la idea; calidad de implementación con buenas prácticas open source y documentación | Ranking 1-2-3 por jurado + voto comunitario como séptimo jurado |

Tres observaciones con consecuencias prácticas:

1. **La guía de EUvsVirus estaba marcada como no compartible con participantes.** La rúbrica pública y la que usa el jurado pueden no coincidir en pesos ni en anclas. Asumí que hay una capa no visible.
2. **El formato cambia el juego.** MLH recomienda feria tipo "science fair" con unos 3 minutos por juez y proyecto, y desaconseja salas fijas porque cada equipo queda comparado solo contra los que cayeron en su sala ([MLH Organizer Guide](https://guide.mlh.io/general-information/judging-and-submissions/draft-up-a-judging-plan)). Muchos eventos online imponen videos de 2 o 3 minutos y advierten que el jurado deja de mirar al llegar al límite ([UNIHACK](https://unihack.notion.site/How-to-submit-your-project-2e05dc7357fb4d3ba3e23f51207f996a)).
3. **El sponsor suele estar dentro de "implementación".** Okta incluía explícitamente cuántas funciones de su producto se usaban más allá del login. En hackathones corporativos, el encaje con el producto del sponsor es un criterio aunque no tenga fila propia.

### I.4 Sesgo de selección y afirmaciones sin respaldo

- **Los ganadores visibles no representan a la población.** Devpost no verifica la exactitud de lo cargado ([arXiv 2103.01145](https://arxiv.org/pdf/2103.01145)), los equipos editan las fichas después del fallo, y los relatos de "cómo ganamos" los escriben quienes ganaron. Los perdedores con el mismo pitch no publican.
- **Estadísticas de blogs.** Un blog de HackerEarth afirma que la rúbrica, y no el mérito técnico, explica la mayor parte de la varianza de resultados y lo atribuye a la guía de MLH ([HackerEarth](https://www.hackerearth.com/blog/10-tips-win-hackathon)). En la guía de MLH no hay tal análisis. Del mismo modo, un "winning ratio" por lenguaje calculado en Medium sobre Devpost confunde tema, tamaño de equipo y tipo de evento ([Medium](https://medium.com/@pandyahetav1/projects-that-can-make-you-win-your-next-hackathon-8ae2bd92834a)). Estas cifras no deben entrar en una skill como hechos.
- **Testimonios de jurados.** Hay relatos útiles, como el de un jurado que observó que admitir una limitación subía los puntajes en sus planillas ([DEV](https://dev.to/kurbaitaev/what-judges-actually-score-notes-from-a-year-of-hackathon-judging-3p4l)) o el de jurados de JetBrains que priorizan una demo comprensible sobre código impecable ([JetBrains](https://blog.jetbrains.com/ai/2026/06/how-to-win-a-hackathon-notes-from-the-judging-table/)). Son hipótesis generadoras, no evidencia.

**Síntesis del bloque.** Lo mejor sustentado es indirecto: los evaluadores descartan por defectos fatales, la preparación pesa más que el entusiasmo, un pitch claro ayuda a que el experto vea la calidad real (buena o mala), y el acuerdo entre jurados es bajo. "Técnicamente superior" no gana si el jurado no puede percibir esa superioridad en el tiempo y formato que tiene.

## Bloque II — Psicología y sociología de la evaluación

Un jurado de hackathon decide bajo tres restricciones simultáneas: poco tiempo por proyecto, muchas propuestas en secuencia y alta incertidumbre sobre si lo que ve funciona. Esas son exactamente las condiciones en que la literatura muestra que las heurísticas reemplazan al análisis. El objetivo honesto no es explotarlas, sino reducir el costo de verificar para que la decisión se apoye en la calidad real.

### II.1 Mecanismos con evidencia y su traducción al hackathon

| Mecanismo | Evidencia principal | Tipo de evidencia | Validez para hackathones | Implicación honesta |
| --- | --- | --- | --- | --- |
| Sesgo contra la novedad alta | [Boudreau et al. 2016](https://lbsresearch.london.edu/id/eprint/175): propuestas muy novedosas y propuestas cercanas a la especialidad del evaluador reciben peores puntajes; [Criscuolo et al. 2017](https://researchportal.bath.ac.uk/en/publications/evaluating-novelty-the-role-of-panels-in-the-selection-of-rampd-p/): se financia más la novedad intermedia y la carga del panel reduce la preferencia por novedad | Asignación aleatoria (Boudreau); estudio multimétodo en una firma (Criscuolo) | Media: paneles expertos con tiempo, no jurados de 3 minutos; es plausible que el efecto sea mayor con menos tiempo | Anclar lo nuevo en una categoría conocida ("es un X, pero que hace Y"). No esconder la novedad: hacerla procesable |
| Sesgo implícito contra la creatividad bajo incertidumbre | [Mueller, Melwani y Goncalo 2012](https://repository.upenn.edu/mgmt_papers/66): con incertidumbre inducida, las personas asocian creatividad con negativo y reconocen peor ideas creativas | Laboratorio, dos experimentos | Baja a media; la tarea es distinta | Bajar la incertidumbre de "¿funciona?" antes de pedir que valoren lo original: primero evidencia de que corre, después la idea |
| Fluidez de procesamiento | [Alter y Oppenheimer 2009](https://peeref.com/works/64592927): lo que se procesa con facilidad se juzga más verdadero, más agradable y más familiar | Revisión de una literatura experimental amplia | Alta como mecanismo general; no hay estudios en hackathones | Es la palanca más potente y la más peligrosa: la claridad también hace creíble lo falso. De ahí la auditoría de afirmaciones |
| Carga cognitiva y diseño multimedia | [Mayer 2017](https://zendy.io/title/10.1111/jcal.12197): coherencia (d=0,70), señalización (0,46), segmentación (0,70), contigüidad temporal (1,30), con límites según conocimiento previo | Cientos de experimentos de aprendizaje | Media: miden aprendizaje, no juicio; el efecto se invierte parcialmente con expertos (expertise reversal) | Sacar todo lo que no sostiene la decisión; señalar dónde mirar; narrar mientras se muestra |
| Efectos de orden | [Bruine de Bruin 2005](https://lida.sport-iat.de/ta/Record/4009866): puntajes crecientes con la posición en Eurovisión y patinaje; [Criscuolo et al. 2021](https://wrap.warwick.ac.uk/176162/1/orsc.2020.1413.pdf): tras un proyecto financiado, el siguiente tiene menos chances, efecto más fuerte al final de la reunión | Datos de campo; orden aleatorizado en Criscuolo | Media; algunas réplicas en gimnasia fallaron en el efecto secuencial | No controlás el orden. Sí controlás que tu primer minuto sea autosuficiente y que el jurado pueda recuperar lo esencial después (README, una frase memorable) |
| Asimilación y contraste | [Damisch, Mussweiler y Plessner 2006](https://heibib.ub.uni-heidelberg.de/search/Record/181132472X): el juicio se acerca o se aleja del anterior según se perciba similitud o diferencia | Olimpíadas 2004 + laboratorio | Media | Si el anterior fue parecido y bueno, te favorece parecerte; si fue parecido y flojo, diferenciate explícitamente en los primeros segundos |
| Fatiga del evaluador | [Danziger et al. 2011](https://en.wikipedia.org/wiki/Hungry_judge_effect) sobre jueces de libertad condicional, discutido por Weinshall-Margel y Shapard y por [Glöckner 2016](https://doaj.org/article/a6508d29977845e885f7ebe0f4f103fc), que muestra que el patrón puede surgir de la agenda | Observacional, efecto probablemente sobreestimado | Baja como cifra; el mecanismo general de agotamiento en paneles tiene mejor apoyo en Criscuolo 2021 | No citar el "efecto juez hambriento" como hecho. Sí diseñar para un jurado cansado: menos inferencias exigidas |
| Bajo acuerdo entre jueces | [Pier et al. 2018](https://pubmed.ncbi.nlm.nih.gov/29507248/): sin acuerdo entre revisores de las mismas propuestas; tampoco en cómo convierten fortalezas y debilidades en números | Réplica controlada del proceso NIH | Alta como advertencia | Ganar o perder tiene un componente aleatorio grande. No sobreajustar conclusiones a un solo resultado |
| Eliminación por aspectos | [Maxwell et al. 2011](https://econpapers.repec.org/RePEc:eee:jbvent:v:26:y:2011:i:2:p:212-225) | Codificación de 150 interacciones reales | Media a alta | Antes de buscar puntos, eliminar motivos de descarte: demo rota, problema ininteligible, "ya existe" sin respuesta |
| Intuición del evaluador | [Huang y Pearce 2015](https://escholarship.org/content/qt54j7z903/qt54j7z903.pdf?t=nybbja): inversores ángeles combinan análisis e intuición sobre la persona | Inductivo + experimento de campo + seguimiento | Media | La percepción del equipo (dominio del tema, respuestas precisas) entra en el juicio aunque no esté en la rúbrica |
| Sesgo por género y apariencia | [Brooks et al. 2014](https://dspace.mit.edu/handle/1721.1/91283) y su [replicación parcial](https://forrt.org/flora-replication-atlas/doi/10.1073/pnas.1321202111/) | Campo + experimentos; réplica mixta | Media | No es algo que la presentadora deba "corregir" en sí misma. Sí justifica trasladar peso a evidencia verificable que no depende de quién habla |
| Preparación percibida | [Chen, Yao y Kotha 2009](https://data.zhenzhi.com/details/1/861740525/1/3) | Laboratorio + campo | Media a alta | Las respuestas a preguntas técnicas son evidencia de preparación; ensayarlas rinde más que ensayar entusiasmo |

### II.2 Efectos con evidencia clásica pero sin estudios específicos en hackathones

- **Efecto halo.** Descrito por Thorndike (1920): un atributo saliente contamina la evaluación de los demás. En un hackathon, una UI pulida puede subir la nota de "implementación" aunque el backend sea un mock. Por eso la honestidad exige etiquetar lo simulado: el halo convierte una omisión en engaño material.
- **Anclaje.** Tversky y Kahneman (1974). Una cifra temprana ("detecta el 98%") se vuelve referencia aunque la muestra sea de 50 casos. Las cifras deben llevar su denominador en la misma oración.
- **Autoridad y prestigio.** Las señales institucionales (logos, "usado por") funcionan como atajo. Su uso es legítimo solo si son verificables y vigentes; cualquier "alianza" no formal es un riesgo de descalificación y de reputación.
- **Conformidad en deliberación.** La literatura de paneles NIH citada por Pier et al. sugiere que discutir puede empeorar el acuerdo entre paneles. En deliberaciones cortas de hackathon, el jurado con más autoridad técnica suele arrastrar a los demás; un proyecto que ese jurado no entiende queda sin defensor.

### II.3 Cómo cambia la decisión según el contexto

| Condición | Qué aumenta | Qué conviene priorizar |
| --- | --- | --- |
| Menos de 3 minutos por proyecto | Heurísticas, halo, descarte por defecto fatal | Una sola afirmación central y una sola prueba visible |
| Muchos proyectos en secuencia | Efectos de orden, contraste con el anterior, fatiga | Apertura autosuficiente; frase de recuperación al final |
| Jurado especialista en tu área | Escrutinio, penalización por cercanía (Boudreau) | Limitaciones dichas antes de que las encuentren; métodos y amenazas a la validez |
| Jurado generalista | Dependencia de fluidez y de analogías | Problema concreto, consecuencia visible, analogía precisa |
| Evaluación asincrónica (video + Devpost) | Lectura salteada, abandono en el límite de tiempo | Lo esencial en los primeros 20 segundos del video y en el primer párrafo |
| Evaluación en feria (expo) | Comparación con los vecinos de mesa, interrupciones | Demo de 30 segundos repetible y una pantalla que se explique sola |

### II.4 Laboratorio frente a validez ecológica

Casi toda la evidencia fuerte proviene de laboratorio (fluidez, multimedia, sesgo contra creatividad) o de paneles con más tiempo que un jurado de hackathon (NIH, I+D, inversores). La extrapolación más defendible es direccional: lo que empeora el juicio en condiciones de calma probablemente lo empeora más con presión de tiempo. Las magnitudes no se trasladan. Ninguna skill debería prometer porcentajes de mejora derivados de estos estudios.

## Bloque III — Teoría de juegos y diseño de mecanismos

Un hackathon es un torneo con información asimétrica: el equipo sabe qué funciona y qué está simulado; el jurado no, y tiene minutos para averiguarlo. La consecuencia formal es que gana valor todo lo que haga **barato verificar** y **caro falsificar**. Esa es la definición operativa de optimizar sin manipular.

### III.1 Actores, objetivos y asimetrías

| Actor | Qué maximiza | Qué sabe | Qué no sabe |
| --- | --- | --- | --- |
| Equipo | Premio, visibilidad, contratos, continuidad | Estado real del sistema, qué está hardcodeado | Pesos reales, preferencias de cada jurado, nivel de los rivales |
| Jurado | Elegir bien con poco tiempo; defender su elección ante los otros jurados y el organizador | Su dominio y sus gustos | Si la demo corre sobre datos reales; cuánto se hizo durante el evento |
| Organizador | Reputación del evento, satisfacción de sponsors, participación futura | Las reglas y la rúbrica completa | La calidad real de cada envío |
| Sponsor | Adopción de su API o producto, reclutamiento, contenido para marketing | Qué uso de su producto le sirve | Si el uso mostrado es superficial |
| Usuario potencial | Que el problema se resuelva | El dolor real | Si la solución sobrevive al evento |

Observaciones que salen de la tabla:

1. **El jurado tiene un objetivo doble.** Elegir bien y poder justificar la elección. Un proyecto difícil de explicar a otros jurados pierde en la deliberación aunque convenza a uno. Darle al jurado una frase que pueda repetir es darle una herramienta de defensa.
2. **El sponsor es un evaluador encubierto.** Su rúbrica implícita es "¿esto muestra un uso no trivial de nuestro producto?". Los premios por track suelen tener menos competencia efectiva que el premio general.
3. **El usuario potencial casi nunca está en la sala.** Las afirmaciones de impacto no tienen verificador presente; por eso son el terreno donde más se exagera y donde un jurado experimentado más descuenta.

### III.2 Señalización creíble

El marco clásico es Spence (1973): una señal separa tipos cuando es más costosa de emitir para quien no tiene la cualidad. Crawford y Sobel (1982) muestran que el "cheap talk" (afirmaciones sin costo) transmite poca información cuando los intereses divergen. Akerlof (1970) describe cómo, si el comprador no distingue calidad, el mercado se llena de "limones". Las tres referencias son clásicas de economía de la información y no fueron reverificadas en línea en esta sesión.

Traducido a hackathon, las señales se ordenan por costo de falsificación:

| Señal | Costo de falsificar | Valor informativo para el jurado |
| --- | --- | --- |
| "Es escalable", "usa IA avanzada", "impacto en millones" | Nulo | Casi nulo; puede restar si suena a relleno |
| Diapositiva con arquitectura | Bajo | Bajo, salvo que se pueda contrastar con el repo |
| Video editado | Bajo a medio | Medio; el jurado sabe que se puede cortar |
| Video sin cortes con reloj o terminal visible | Medio | Medio a alto |
| Demo en vivo con entrada fija | Medio | Medio; puede estar ensayada sobre el caso feliz |
| **Demo en vivo con entrada elegida por el jurado** | Alto | Muy alto |
| Repo reproducible con un comando y datos de prueba incluidos | Alto | Alto para jurados que lo prueban; latente para el resto |
| Evaluación con denominador, línea de base y casos fallidos mostrados | Alto | Muy alto para especialistas |
| Limitación dicha antes de que la pregunten | Costo reputacional real si fuera falsa | Alto: indica que el equipo conoce su sistema |

La última fila es contraintuitiva pero tiene lógica de señalización: admitir un límite solo lo hace barato quien sabe dónde están los límites. Coincide con el testimonio del jurado citado en el Bloque I, aunque ese testimonio no es evidencia sistemática.

### III.3 Competencia por atención y estructura de torneo

- **Premio por rango, no por nivel absoluto.** En torneos, lo que cuenta es la posición relativa. Un proyecto muy bueno en un evento con un rival excepcional pierde; uno correcto en un track poco disputado gana. La elección de track y premio es una decisión estratégica con tanto peso como la calidad.
- **Incertidumbre del problema.** Boudreau, Lacetera y Lakhani (2011), con 9.661 concursos de software, muestran que más rivales reducen el esfuerzo de cada uno, pero en problemas muy inciertos aumentan la probabilidad de una solución extrema ([EconPapers](https://econpapers.repec.org/RePEc:inm:ormnsc:v:57:y:2011:i:5:p:843-863)). Para un participante: en temas saturados (chatbots genéricos) el retorno marginal de esforzarse en el mismo enfoque es bajo; la ventaja está en un ángulo que el resto no exploró.
- **Atención como recurso escaso.** El jurado reparte minutos fijos. El costo de un segundo de pitch que no aporta a la decisión es un segundo menos de evidencia. Esto da un criterio operativo de edición: cada bloque debe cambiar la probabilidad que el jurado asigna a "esto funciona", "esto importa" o "esto es nuevo".

### III.4 Goodhart, gaming y selección adversa

La formulación popular de la ley de Goodhart (una medida que se vuelve objetivo deja de ser buena medida) es de Marilyn Strathern (1997), no del propio Goodhart ([referencia](https://Www.wikipedia.org/wiki/Goodhart%27s_law)). Aplica en dos direcciones:

- **Del lado del participante.** Sobreajustar a la rúbrica produce proyectos que tildan casillas ("usamos 7 APIs del sponsor") sin un mecanismo coherente. Un jurado atento lo percibe como relleno. Un jurado distraído lo premia, y ahí está el riesgo de selección adversa: si el evento premia la apariencia de completitud, los equipos honestos con alcance acotado salen perjudicados y dejan de participar.
- **Del lado del evento.** Métricas como "cantidad de features" o "uso de la API" invitan a integraciones decorativas. Las rúbricas que piden "explicar por qué elegiste la tecnología" (como HackCC) son más resistentes porque exigen razonamiento, no conteo.

### III.5 Reglas de optimización honesta

De todo lo anterior se derivan reglas verificables, que después se convierten en controles de las skills:

1. **Maximizá la proporción de afirmaciones verificables en el tiempo del jurado.** Cada afirmación del pitch debe tener una prueba visible en el pitch, en el repo o disponible en preguntas.
2. **Gastá esfuerzo en señales caras.** Entrada del jurado, reproducibilidad, casos fallidos. No en adjetivos.
3. **Nunca dejes que el halo haga trabajo que la evidencia no hace.** Si la UI es más madura que el backend, decilo.
4. **Elegí el torneo, no solo el proyecto.** Track, premio especial y encaje con el sponsor son parte de la estrategia.
5. **Dale al jurado un argumento para defenderte.** Una frase, un número con denominador, una comparación.
6. **No sobreajustes.** Si un criterio de la rúbrica te empuja a agregar algo que el proyecto no necesita, el costo en coherencia suele superar el punto ganado.

Un límite de este bloque: no encontré ningún modelo formal publicado específicamente para hackathones. Lo anterior es aplicación de teoría general, con estatus de hipótesis razonada.

## Bloque IV — Marketing honesto

Marketing honesto, en este contexto, es reducir el costo de que el jurado entienda y verifique, sin agregar afirmaciones que el proyecto no sostiene. La pregunta de control para cada frase es: si el jurado tuviera una hora y acceso total al repo, ¿esta frase sobreviviría?

### IV.1 La cadena de argumentos y qué evidencia necesita cada eslabón

| Eslabón | Qué tiene que lograr | Evidencia aceptable | Errores frecuentes |
| --- | --- | --- | --- |
| Problema en segundos | Que el jurado reconozca una situación concreta | Un caso específico ("un analista recibe 4.000 alertas en un turno") con fuente si es una cifra | Problema abstracto ("la ciberseguridad es importante"); estadísticas de mercado sin fuente |
| Costo de no resolverlo | Que el problema importe | Costo con fuente pública, o costo observado por vos y dicho como tal | Cifras de informes de proveedores presentadas como neutrales; sumar costos de todo el sector |
| Solución y mecanismo | Que se entienda *por qué* funcionaría | Una frase de mecanismo: "hace X usando Y, lo que evita Z" | Lista de tecnologías en vez de mecanismo |
| Demostración | Que el jurado vea el mecanismo actuar | Ejecución real; si hay simulación, se nombra | Video con resultados precargados sin aviso; animaciones que parecen salida del sistema |
| Evidencia de funcionamiento | Que el resultado no sea un caso elegido | Denominador, línea de base, casos que fallaron | Porcentajes sin muestra; un solo ejemplo feliz |
| Diferenciación | Que no sea "esto ya existe" | Comparación contra la alternativa que el jurado conoce, en un eje verificable | "No hay nada parecido"; tablas comparativas con todas las casillas a favor |
| Limitaciones | Que el jurado confíe en el resto | Una o dos limitaciones materiales, con qué harías al respecto | Esconderlas; o enumerar veinte menores para parecer humilde |
| Impacto realista | Que el alcance sea creíble | Quién lo usaría primero y qué cambiaría para esa persona | "Millones de usuarios"; TAM de miles de millones |
| Próximos pasos | Que el jurado vea trayectoria | Dos o tres pasos concretos con lo que bloquea cada uno | Roadmap de producto completo inventado durante la noche |

### IV.2 Comunicar incertidumbre sin perder credibilidad

Van der Bles y colegas (PNAS, 2020) hicieron cinco experimentos con 5.780 participantes, incluido uno en la web de BBC News. Expresar incertidumbre como rango numérico bajó poco la confianza en el número y casi nada la confianza en la fuente; la incertidumbre verbal ("hay cierta incertidumbre") restó más ([resumen PNAS](https://cir.nii.ac.jp/crid/1360576123220091264?lang=en)). Para pitches:

- Preferí "detectó 31 de 40 casos del dataset X (78%); falló en los que tienen Y" a "tiene muy buena precisión, aunque todavía hay que validarlo más".
- Un rango o un denominador es más creíble que una advertencia vaga.
- La población del estudio era público general en Reino Unido. Para jurados técnicos es razonable esperar el mismo efecto o mayor, pero eso es hipótesis.

### IV.3 Qué mostrar, qué resumir, qué llevar al README y qué guardar para preguntas

Criterio de asignación: cada pieza de información va al canal donde su costo de procesamiento es menor que su contribución a la decisión.

| Tipo de información | Pitch o video | README / ficha | Preguntas del jurado |
| --- | --- | --- | --- |
| Afirmación central y su prueba principal | **Mostrar** | Repetir en la primera línea | — |
| Mecanismo en una frase | **Mostrar** | Ampliar con diagrama | Profundizar |
| Arquitectura completa | Resumir en un diagrama de 3 a 5 cajas como máximo | **Detallar** | Tener el diagrama completo listo |
| Métricas de evaluación | La más relevante con denominador | **Todas**, con método, dataset y comando para reproducir | Amenazas a la validez |
| Limitaciones materiales | **Decir** las 1-2 que cambian el juicio | Sección propia y visible | Plan para cada una |
| Limitaciones menores | No | Listar | Responder si preguntan |
| Qué está simulado | **Decir** si es material para lo que se ve | **Tabla** "real / simulado / pendiente" | — |
| Qué se hizo durante el evento vs antes | Si la regla lo exige o si es material, decirlo | **Declarar** | — |
| Stack y librerías | No, salvo requisito de sponsor | Listar | — |
| Decisiones de diseño y alternativas descartadas | No | Breve | **Preparar** (es donde los especialistas evalúan comprensión) |
| Comparación con alternativas | Un eje | Tabla con fuentes | Responder con honestidad si alguna alternativa es mejor en algo |

### IV.4 Cuándo una simulación es "material"

Una simulación es material si un jurado razonable, sabiendo que es simulada, cambiaría su evaluación en algún criterio de la rúbrica. Test práctico en tres preguntas:

1. ¿Lo simulado es el mecanismo que se está evaluando? (por ejemplo, la detección en una herramienta de detección). Si sí, es material siempre.
2. ¿Lo simulado es infraestructura periférica? (un login falso, datos sintéticos en lugar de producción). Suele no ser material para "idea", pero sí para "completitud" o "implementación".
3. ¿El jurado podría inferir, por lo que ve, que algo funciona cuando no? Si sí, hay que decirlo aunque las otras dos respuestas sean "no".

Forma de etiquetarlo sin destruir el pitch: "Lo que ven acá corre de verdad sobre este archivo; la integración con el SIEM está simulada con respuestas grabadas". Una oración, en el momento en que aparece, no al final.

### IV.5 Líneas que no se cruzan

Ninguna skill derivada de este informe debe producir, sugerir ni "mejorar" textos que contengan:

- Métricas, usuarios, testimonios, pilotos, validaciones o resultados que no existan.
- Alianzas, interesados o "conversaciones con" que no sean verificables y vigentes.
- Madurez implícita: "en producción", "probado", "listo para escalar" sin evidencia.
- Capturas o videos de una versión distinta a la entregada, sin indicarlo.
- Comparaciones donde la alternativa fue configurada mal a propósito.
- Omisión de trabajo previo al evento cuando las reglas exigen que todo se haga durante el evento.

Este último punto es práctico además de ético: varias reglas de hackathon descalifican proyectos iniciados antes del evento, y MLH recomienda a los organizadores revisar ganadores por trampa antes de anunciar ([MLH Organizer Guide](https://guide.mlh.io/general-information/judging-and-submissions/draft-up-a-judging-plan)).

### IV.6 Posicionamiento y diferenciación verificable

- **Categoría conocida + diferencia única.** Dado el sesgo contra la novedad alta (Bloque II), conviene anclar: "un linter, pero para skills de agentes"; "un SIEM, pero que explica por qué correlaciona". La segunda mitad es la que hay que probar.
- **Un eje de diferenciación, no cinco.** El jurado retiene una diferencia. Elegila por dos criterios: que sea verificable en la demo y que importe para el problema planteado.
- **Diferenciarse del rival ausente.** El jurado compara con lo que conoce (ChatGPT, Wireshark, Splunk, un script). Nombrar esa alternativa y mostrar el eje en que tu proyecto es distinto evita que el jurado haga la comparación por su cuenta y la haga mal.
- **Concesión explícita.** "Para X, Splunk sigue siendo mejor; esto sirve cuando Y". Es una señal cara (Bloque III) y además delimita el alcance.

## Bloque V — Comunicación técnica sin aburrir

La complejidad técnica aburre cuando el jurado no sabe para qué sirve cada detalle. La regla operativa es: **cada detalle técnico tiene que responder una pregunta que el jurado ya se está haciendo.** Si la pregunta todavía no existe, primero hay que crearla con el problema o la demo.

### V.1 Tres orientaciones de presentación

| Orientación | Orden típico | Funciona con | Falla con | Riesgo principal |
| --- | --- | --- | --- | --- |
| Hacia la implementación | Stack → arquitectura → features → demo | Jurados especialistas que ya entienden el problema | Generalistas; formatos cortos | El jurado no sabe por qué importa hasta el final, y el final no llega |
| Hacia el problema | Dolor → consecuencia → solución → demo | Generalistas, sponsors, impacto social | Especialistas que sospechan de la narrativa sin pruebas | Mucha historia y poca evidencia de que funciona |
| **Hacia la evidencia** | Afirmación → prueba en vivo → mecanismo → límites → alcance | Jurados mixtos; temas técnicos difíciles de creer | Proyectos sin nada que demostrar todavía | Requiere tener una prueba fuerte; sin ella expone el vacío |

Para proyectos de seguridad, DFIR y agentes, la orientación hacia la evidencia suele ser la apuesta más robusta, porque el dominio está lleno de afirmaciones difíciles de verificar y los jurados técnicos lo saben. Su versión más compacta: **"Esto hace X. Mirá. Así lo hace. Acá no lo hace todavía."**

### V.2 Principios de diseño con evidencia

De la teoría cognitiva del aprendizaje multimedia (Mayer) y la carga cognitiva:

- **Coherencia.** Sacar todo lo que no sostiene la decisión: fondos, logos de cada librería, transiciones.
- **Señalización.** Resaltar en la pantalla lo que se está diciendo en ese momento: un recuadro en la línea del log, no el log entero sin guía.
- **Contigüidad temporal.** Narrar mientras se muestra, no antes ni después.
- **Redundancia.** No leer texto que está en pantalla.
- **Segmentación.** Partir la demo en pasos con un título cada uno.
- **Límite por experiencia.** La guía que ayuda a un novato puede estorbar a un experto: el efecto de inversión por pericia ([Kalyuga, Ayres, Chandler y Sweller 2003](https://ro.uow.edu.au/edupapers/136)). Con jurados especialistas, menos andamiaje y más densidad.

### V.3 Cuándo un recurso visual ayuda y cuándo engaña

| Recurso | Ayuda cuando | Introduce ruido o engaño cuando |
| --- | --- | --- |
| Diagrama de arquitectura | Tiene 3 a 7 elementos y las flechas significan algo definido (datos, control) | Muestra componentes que no existen sin marcarlos; flechas sin semántica |
| Animación | Explica un proceso temporal (propagación, orden de eventos) | Se parece a la salida del sistema pero está hecha a mano |
| Gráfico de resultados | Tiene ejes con unidades, denominador y línea de base | Eje truncado en barras: Pandey et al. (CHI 2015) mostraron que exagera la percepción de diferencias ([dblp](https://bibtex.github.io/CHI-2015-PandeyRSNB.html)); Correll, Bertini y Franconeri (CHI 2020) encontraron que el efecto persiste aun con avisos visuales ([arXiv](https://ar5iv.arxiv.org/html/1907.02035)) |
| Captura de pantalla | Es de la versión entregada y muestra un resultado real | Es de un mockup o de otra versión sin indicarlo |
| Demo en vivo | El sistema es estable y la entrada es variada | Se ensayó solo el caso feliz y se presenta como general |
| Video grabado | El evento es asincrónico o la demo es inestable | Está cortado en los puntos donde falló sin decirlo |
| Comparativa en tabla | Los ejes son relevantes y la alternativa está bien configurada | Todas las casillas favorecen al proyecto; ejes elegidos a posteriori |
| Infografía de impacto | Las cifras tienen fuente | Cifras de mercado sin fuente; íconos de personas que sugieren usuarios inexistentes |

### V.4 Recomendaciones por tipo de proyecto

**Software de seguridad (detección, análisis, hardening).** El jurado necesita ver un ataque o un hallazgo concreto, no una lista de capacidades. Formato recomendado: un escenario con antes y después. "Este binario tiene esta vulnerabilidad; la herramienta la encuentra en 12 segundos; esta es la línea". Mostrar también un falso positivo o un caso fuera de alcance aumenta la credibilidad ante especialistas. Nunca mostrar exploits contra sistemas de terceros sin autorización, ni siquiera en video.

**DFIR y forense.** El producto es una conclusión trazable a evidencia. Lo más convincente es un recorrido de cadena de custodia: artefacto de entrada → hash → transformación → hallazgo → línea de tiempo → informe, con cada salto clickeable o visible. Las líneas de tiempo son el formato visual natural. Distinguir en pantalla hechos, inferencias e hipótesis es a la vez buena práctica forense y señal cara.

**Agentes de IA.** El jurado viene saturado de demos de agentes y sabe que se pueden ensayar. Lo que diferencia: (1) traza visible de decisiones (qué herramienta llamó, con qué argumentos, qué recibió); (2) una ejecución con entrada que el jurado propone; (3) un caso en que el agente se detiene, pide confirmación o falla de forma segura; (4) costo y latencia reales. Si el modelo puede dar respuestas distintas en cada corrida, decirlo y mostrar cómo lo controlás.

**Herramientas CLI.** La terminal es ilegible a distancia y en video comprimido. Usar fuente grande (24-32 px en video), tema de alto contraste, prompt corto y comandos pegados o tipeados con un grabador de terminal que permita pausar. Mostrar el comando, después solo la parte relevante de la salida, resaltada. Para jurados no técnicos, una línea de "qué acaba de pasar" debajo de cada salida.

**Grafos y redes.** Un grafo con cientos de nodos es una bola de pelos que no comunica nada. Mostrar primero el subgrafo que responde una pregunta (3 a 15 nodos), con la pregunta escrita arriba. Después, si hace falta, alejar para dar escala. Usar el layout para codificar algo (tiempo en el eje horizontal, por ejemplo) en lugar de un layout de fuerza aleatorio.

**Resultados difíciles de visualizar** (mejoras de robustez, ausencia de algo, garantías formales, latencia). Convertirlos en un contraste: con y sin la herramienta sobre la misma entrada, lado a lado. Si el resultado es una garantía ("nunca filtra X"), mostrar el intento de violarla y el bloqueo. Si es estadístico, un solo número con denominador y una frase de qué significa en la práctica.

### V.5 Traducir sin perder precisión

- **Analogías con límite declarado.** "Funciona como un detector de humo para dependencias: avisa, no apaga el fuego". La segunda mitad evita que la analogía prometa más de lo que hace.
- **Un nivel de abstracción por oración.** No mezclar "ayudamos a los analistas" con "usando embeddings de 768 dimensiones" en la misma frase.
- **Escalera de detalle.** Preparar la misma explicación en tres niveles (una oración, un párrafo, una página) y elegir según el formato y el jurado. Es la base de la skill de traducción de complejidad.
- **Glosario implícito.** Si un término técnico es imprescindible, definirlo una vez con una frase y después usarlo de manera consistente.

## Bloque VI — Formatos competitivos y matriz de decisiones

El formato fija cuántas afirmaciones caben y qué tipo de prueba es posible. Las cifras de palabras siguientes asumen un ritmo de habla de 130 a 150 palabras por minuto, que es una aproximación habitual y no un dato medido para este informe; conviene cronometrar tu propio ritmo.

### VI.1 Estrategia por formato

| Formato | Presupuesto aproximado | Afirmaciones que caben | Prueba posible | Estructura recomendada | Error típico |
| --- | --- | --- | --- | --- | --- |
| Pitch de 30 s | 65-75 palabras | 1 | Ninguna en vivo; una cifra o un caso | Para quién + qué cambia + por qué creértelo en una frase | Intentar explicar el mecanismo |
| Pitch de 60 s | 130-150 palabras | 1 central + 1 de apoyo | Una captura o un resultado | Problema concreto (10 s) → qué hace (15 s) → prueba (20 s) → diferencia (10 s) → cierre repetible (5 s) | Listar features |
| Pitch de 3 min | 400-450 palabras | 2-3 | Demo corta en vivo o grabada | Afirmación (15 s) → demo (75 s) → mecanismo (30 s) → límites y diferencia (30 s) → alcance y próximo paso (20 s) → cierre (10 s) | Usar 90 s en contexto antes de mostrar algo |
| Pitch de 5 min | 650-750 palabras | 3-4 | Demo + un resultado de evaluación | Igual que 3 min, con evaluación (denominador, línea de base) y un segundo caso de demo | Agregar slides de mercado y equipo que el jurado no pidió |
| Video de 90 s | 190-220 palabras de locución | 1-2 | Pantalla real con señalización | Primer plano del resultado en los primeros 10 s; después cómo se llegó | Intro con logo y música de 15 s |
| Video de 3 min | 400-450 palabras | 2-3 | Demo completa, idealmente sin cortes en el tramo clave | Igual que pitch de 3 min; subtítulos; escena clave sin edición con reloj o terminal visible | Pasarse del límite: muchos eventos cortan en el minuto exacto |
| Deck de 5 slides | — | 2-3 | Capturas | Problema / qué hace y prueba / cómo funciona / diferencia y límites / estado y próximo paso | Slide de "equipo" en lugar de evidencia |
| Deck de 10 slides | — | 3-4 | Capturas + un gráfico | Agregar: evaluación, comparación con alternativa, arquitectura, uso del sponsor, qué se hizo en el evento | Slides densas para leer mientras hablás |
| Deck de 15 slides | — | 4-5 | Todo lo anterior | Usarlo como material de lectura asincrónica o de respaldo para Q&A, no para exponer completo | Exponer las 15 en 5 minutos |
| Demo grabada | — | — | Media | Avisar que es grabada si el formato esperaba vivo; mostrar al menos un tramo sin cortes | Ocultar cortes en puntos de falla |
| Demo en vivo | — | — | Alta | Plan B grabado listo; datos de prueba locales; sin depender del wifi del evento | No ensayar con la red y la pantalla del evento |
| README asincrónico | Primeras 10-15 líneas | 1-2 arriba de todo | Comando reproducible | Título + una oración + GIF o captura + cómo correrlo en un comando + tabla real/simulado + límites | README de la plantilla con "Inspiration" de tres párrafos |
| Presentación con preguntas técnicas | — | — | Respuestas | Preparar las 10 preguntas más probables y las 3 más temidas; respuesta en 20-30 s cada una | Defender lo indefendible en lugar de conceder |

### VI.2 Matriz por tipo de jurado

| Dimensión | Generalista | Especialista en tu área | Sponsor / producto | Inversor o negocio | Mixto |
| --- | --- | --- | --- | --- | --- |
| Apertura | Persona y situación concreta | Afirmación técnica precisa | Qué habilita su producto | Quién paga y por qué | Afirmación + persona en dos frases |
| Prueba preferida | Antes y después visible | Evaluación con método y casos fallidos | Uso no trivial de la API, visible | Señal de demanda real (si existe) | Demo con entrada del jurado |
| Nivel de detalle técnico | Mínimo; analogía con límite | Alto; sin andamiaje | Medio, centrado en la integración | Bajo | Escalera: mostrar poco, tener mucho listo |
| Limitaciones | 1, en lenguaje llano | 2-3, con amenazas a la validez | Las de la integración | Riesgos de adopción | 1-2 materiales |
| Diferenciación | Contra lo que conoce el público | Contra el estado del arte y herramientas conocidas | Contra otros usos de su producto | Contra alternativas de mercado | Un eje verificable |
| Riesgo principal | Que no entienda qué es | Que encuentre un error que no admitiste | Que el uso parezca decorativo | Que el impacto suene inflado | Que cada uno entienda un proyecto distinto |

### VI.3 Reglas de decisión entre formatos

1. **¿El evento exige demo en vivo?** Si no la exige y la demo es inestable, grabarla y decirlo. Si la exige, llevar plan B grabado y aclarar cuando se use.
2. **¿La evaluación es asincrónica?** Entonces el video y las primeras líneas de la ficha son el pitch. El README es la segunda ronda para el jurado que quiere verificar.
3. **¿Hay preguntas?** Si las hay, se puede dejar profundidad para después y acortar el pitch. Si no, todo lo material tiene que estar en el pitch o en la ficha.
4. **¿El jurado es desconocido?** Asumir mixto. Abrir con afirmación + persona, demostrar, y tener la escalera de detalle lista.
5. **¿El límite de tiempo es duro?** Ensayar con cronómetro a 90% del límite. Lo que no entra en el 90% se va al README.

## Bloque VII — Casos y ejemplos contrastados

No encontré casos con datos comparables de ganadores y perdedores del mismo evento evaluados con la misma información; ese material no se publica. Lo que sigue son 13 casos individuales documentados en prensa o fuentes primarias, más 2 conjuntos agregados. Ninguno permite atribuir la victoria a un elemento del pitch. Sirven para identificar patrones y, sobre todo, contraejemplos.

### VII.1 Casos documentados

| # | Caso | Qué pasó | Qué enseña (con cautela) | Fuente |
| --- | --- | --- | --- | --- |
| 1 | GroupMe, TechCrunch Disrupt Hackathon 2010 | No ganó el hackathon. Levantó inversión y Skype la compró en 2011 por unos US$80-85 millones según la prensa | Perder no predice el valor del proyecto. El resultado del jurado y el resultado posterior son variables distintas | [Gear Live](https://www.gearlive.com/business/article/groupme-skype-q311), [Wikipedia](https://en.wikipedia.org/wiki/GroupMe) |
| 2 | Zapier, Startup Weekend Columbia 2011 | Ganó con una demo que, según los propios fundadores, casi falla | Una demo frágil no descalifica si el problema es reconocible y el mecanismo se entiende | [Blog de Zapier](https://zapier.com/blog/zapier-100-connected-services-year-review) |
| 3 | Carousell, Startup Weekend Singapur 2012 | Según un relato biográfico, la idea casi no pasó al pitch final y entró porque otros equipos abandonaron; luego ganó. Los fundadores dicen que lo decisivo fue la reacción de la gente, no el premio | El azar de la selección es grande. La validación con usuarios reales pesa más que el premio | [Wiki.sg](https://wiki.sg/p/Quek_Siu_Rui), [NUS Enterprise](https://enterprise.nus.edu.sg/startup-story/carousell/) |
| 4 | Easy Taxi, Startup Weekend Río 2011 | Ganó y luego otros concursos; la idea nació de un dolor propio del fundador | Un problema vivido en primera persona es fácil de comunicar en segundos | [Wikipedia](https://en.wikipedia.org/wiki/Easy_Taxi) |
| 5 | PhoneGap, iPhoneDevCamp 2008 | Surgió en un evento tipo hackathon; luego ganó el premio del público en Web 2.0 Expo 2009 y Adobe compró Nitobi | Herramientas para desarrolladores ganan cuando el dolor del público es compartido ("hay pocos desarrolladores de Objective-C") | [O'Reilly](https://www.oreilly.com/pub/e/1343), [eWeek](https://eweek.com/?p=75850) |
| 6 | Botón "Like" de Facebook | Prototipo interno en una noche de hackathon; aprobación final meses después | En hackathones corporativos, ganar es menos relevante que conseguir un patrocinador interno | [Fast Company](https://fastcompanyme.com/?p=11226), [Stanford eCorner](https://stvp.stanford.edu/wp-content/uploads/sites/3/2024/09/no-dislike-button-on-facebook-transcript.pdf) |
| 7 | Netflix Prize 2009 | El equipo ganador cumplió la métrica (10% de mejora) con un ensamble de cientos de modelos, pero Netflix no lo llevó a producción porque la ganancia no justificaba el costo de ingeniería y el negocio había cambiado | Goodhart en estado puro: ganar la métrica del concurso no es resolver el problema del patrocinador | [Techdirt](https://www.techdirt.com/blog/innovation/articles/20120409/03412518422/why-netflix-never-implemented-algorithm-that-won-netflix-1-million-challenge.shtml), [FlowingData](https://flowingdata.com/2012/04/17/why-1m-netflix-algorithm-never-went-to-production) |
| 8 | Kaggle PetFinder.my 2019-2020 | El equipo ganador fue descalificado meses después: había obtenido datos de prueba y los ocultó en su solución; se descubrió al intentar ponerlo en producción | El engaño se descubre en la verificación posterior, y el costo reputacional es permanente | [The Register](https://www.theregister.com/2020/01/21/ai_kaggle_contest_cheat/), [Vice](https://www.vice.com/en/article/kaggle-data-science-community-rocked-by-pet-adoption-contest-cheating-scandal) |
| 9 | Salesforce Hackathon 2013 (US$1M) | El ganador fue acusado de haber mostrado la app antes del evento. Salesforce concluyó que no hubo trampa pero que los jurados no tuvieron información suficiente, y declaró empate | La falta de declaración clara de qué se hizo antes y durante el evento genera crisis aun sin mala fe probada | [TechCrunch](https://techcrunch.com/2013/12/02/salesforce-hackathon-tie/) |
| 10 | HackMIT 2014 | Dos equipos descalificados: uno por plagio, otro por reusar un proyecto presentado en otro hackathon la semana anterior; se revocó un premio | Los organizadores se comunican entre sí. Reusar sin declarar es detectable | [The Tech](https://thetech.com/2014/11/07/hackmit-v134-n53) |
| 11 | TechCrunch Disrupt Hackathon 2013 | Una presentación sexista provocó repudio, cobertura negativa y una disculpa pública del organizador, que pasó a revisar presentaciones | El humor que excluye no es "memorable": destruye reputación del equipo y del evento | [Wikipedia](https://en.wikipedia.org/wiki/TechCrunch), [CNN Money](https://money.cnn.com/2013/09/09/technology/social/titstare-app) |
| 12 | DARPA Grand Challenge 2004 y 2005 | En 2004 ningún vehículo terminó y no se entregó premio; en 2005 cinco terminaron y ganó Stanley (Stanford), un equipo que no había participado antes | Cuando la prueba es objetiva y en condiciones reales, el pitch no cuenta. Los equipos nuevos pueden ganar si atacan la causa de falla de la edición anterior | [DARPA](https://webarchive.library.unt.edu/web/20161112063342/http://www.darpa.mil/news-events/2014-03-13), [Wikipedia](https://oreil.ly/SLAGV) |
| 13 | Columbia Startup Weekend, ediciones posteriores | El evento que ganó Zapier tuvo 38 pitches iniciales y 19 equipos en una edición posterior; otro ganador, EquipmentShare, también creció | Los eventos con historial de ganadores exitosos atraen mejores equipos: la competencia se endurece con el tiempo | [HuffPost](https://www.huffingtonpost.com/brittany-hodak/54-hours-of-startup-innov_b_8172792.html) |

**Conjuntos agregados.**

- **A1. Pitch training, Clingingsmith y Shane (2018).** Experimento de campo con pitches de 90 segundos: el entrenamiento ayudó a las ideas buenas y perjudicó a las malas ante inversores experimentados (Bloque I).
- **A2. Tres competencias de pitch, Brooks et al. (2014).** Datos de campo donde el género del presentador se asoció al resultado; réplica posterior parcial (Bloque II).

### VII.2 Patrones que aparecen, con su límite

1. **El problema reconocible en segundos** aparece en Easy Taxi, PhoneGap, Zapier y Carousell. Límite: son relatos de ganadores; muchos perdedores también tenían problemas reconocibles.
2. **Ganar y tener éxito después son cosas distintas.** GroupMe perdió y prosperó; Netflix Prize se ganó y no se usó.
3. **La verificación posterior castiga el engaño** (PetFinder, HackMIT, Salesforce). El horizonte de evaluación no termina con el anuncio.
4. **La selección tiene mucho azar** (Carousell, Pier et al.).
5. **Las pruebas objetivas reducen el peso del pitch** (DARPA). En hackathones con evaluación automatizada o benchmarks, el pitch casi no importa; en los de jurado humano, importa mucho.

### VII.3 Ejemplos contrastados: el mismo proyecto comunicado de tres maneras

Proyecto hipotético, construido para el ejemplo: una herramienta CLI que reconstruye líneas de tiempo de incidentes a partir de logs con relojes desincronizados y marca qué tramos no tienen cobertura. Formato: pitch de 60 segundos ante jurado mixto.

**A. Excesivamente técnico.**

> "Construimos un motor en Rust que ingiere logs en formatos syslog, EVTX y JSON, normaliza timestamps con un algoritmo de estimación de skew basado en eventos ancla, arma un DAG de causalidad parcial y exporta a Timesketch. Usamos un parser incremental, tests de propiedades y una arquitectura de plugins. El clock skew se estima con mínimos cuadrados sobre pares de eventos correlacionados…"

Qué falla: el jurado no sabe para quién es ni qué problema resuelve hasta que se acaba el tiempo. Todo es cierto pero nada es evaluable. Un especialista podría valorarlo; los demás no tienen dónde agarrarse para defenderlo en la deliberación.

**B. Excesivamente comercial.**

> "Cada año las empresas pierden miles de millones por incidentes de seguridad. Nuestra plataforma con IA revoluciona la respuesta a incidentes: reduce el tiempo de investigación en un 90%, escala a cualquier organización y ya despertó el interés de grandes empresas. Es el futuro del DFIR."

Qué falla: no hay mecanismo, la cifra no tiene denominador, "interés de grandes empresas" no es verificable y "con IA" puede ser falso. Un jurado técnico descuenta todo; uno generalista puede creerlo, que es justamente el problema ético.

**C. Persuasivo, preciso y verificable.**

> "Cuando un incidente cruza tres sistemas, sus relojes no coinciden, y el analista termina ordenando eventos a mano en una planilla. \[Problema\] Esta herramienta toma esos logs, estima el desfase entre relojes y arma una sola línea de tiempo, marcando en gris los tramos donde no hay datos: ‘no vimos nada’ no es lo mismo que ‘no pasó nada’. \[Mecanismo\] Acá la corro sobre el caso público X: en 40 segundos ordena 12.000 eventos y detecta un desfase de 7 minutos entre el firewall y el servidor. \[Prueba\] Sobre 5 incidentes de prueba, el orden coincidió con el reconstruido a mano en 4; en el quinto falló porque un sistema no tenía eventos ancla. \[Evidencia y límite\] No reemplaza a Timesketch: lo alimenta. \[Diferencia\] El repo tiene los cinco casos para reproducirlo con un comando."

Por qué C tiende a funcionar mejor: activa la ruta de comprensión en el primer enunciado; el mecanismo cabe en una oración; la prueba es visible y tiene denominador; la limitación funciona como señal cara; la diferenciación desactiva "esto ya existe"; y le da al jurado una frase repetible ("no vimos nada no es lo mismo que no pasó nada").

Cuándo C puede no funcionar:

- **Jurado que premia ambición sobre rigor** (algunos concursos de startups). B puede ganar ahí, al menos en el corto plazo. La respuesta honesta no es imitar a B, sino agregar a C un próximo paso ambicioso y explícito como hipótesis.
- **Rúbrica dominada por "complejidad técnica" con jurado especialista.** A puede rendir más si el jurado ya conoce el problema. C debería reservar más tiempo al mecanismo.
- **Si la prueba es débil**, la estructura C expone el vacío. Eso es correcto desde el punto de vista ético, pero conviene saberlo antes: la skill de evaluación de encaje debería detectarlo y sugerir cambiar de formato o de track, no inflar la prueba.
- **Culturas de evaluación donde admitir límites se lee como inseguridad.** No hay evidencia sistemática para hackathones; es una hipótesis a testear (Bloque VIII).

## Bloque VIII — Crítica, falsación y experimentos

La mayoría de los consejos populares de pitch no fueron testeados en hackathones. Algunos tienen apoyo indirecto; otros contradicen la evidencia disponible.

### VIII.1 Consejos populares y cuándo fallan

| Consejo | Qué tiene de cierto | Cuándo falla | Evidencia |
| --- | --- | --- | --- |
| "Contá una historia" | Facilita la comprensión y la memoria | Cuando la historia ocupa el tiempo de la prueba; con especialistas que descuentan narrativa sin evidencia | Chen et al. 2009: la preparación pesa más que la pasión mostrada |
| "Mostrá pasión" | Puede sostener atención | Cuando reemplaza contenido | Chen et al. 2009 |
| "Entrená el pitch" | Mejora la claridad | Si la idea es débil, la claridad la expone y baja la evaluación de expertos | Clingingsmith y Shane 2018 |
| "Seguí la rúbrica al pie de la letra" | Asegura cobertura | Sobreajuste: proyectos incoherentes que tildan casillas; rúbricas reales con pesos ocultos | Goodhart; guía de jurados de EUvsVirus no pública |
| "Lo más innovador gana" | Las rúbricas piden originalidad | La novedad alta se penaliza, sobre todo con jurados cargados | Boudreau et al. 2016; Criscuolo et al. 2017 |
| "Nunca admitas debilidades" | Evita dar argumentos en contra | Contradice la lógica de señalización; con especialistas, que encuentren el problema antes que vos es peor | Teoría (Bloque III); testimonios de jurados, no sistemáticos |
| "Demo en vivo siempre" | Es una señal cara | Con red o hardware inestable, una falla visible puede activar el descarte por defecto fatal | Maxwell et al. 2011 (eliminación por aspectos) |
| "Andá último si podés" | Hay efectos de orden en concursos | No controlás el orden; el efecto varía y algunas réplicas fallaron | Bruine de Bruin 2005; Joustra et al. 2021 en gimnasia |
| "Más features impresionan más" | Muestra capacidad de ejecución | Diluye el mensaje y multiplica puntos de falla | Mayer (coherencia); sin estudios en hackathones |

### VIII.2 Diferencias culturales e incertidumbre

- No encontré estudios comparativos de evaluación de hackathones entre culturas. Lo que sigue es hipótesis.
- La franqueza sobre limitaciones puede leerse como competencia en algunos entornos y como inseguridad en otros. La autopromoción directa puede sumar en un evento estadounidense y restar en uno europeo o japonés.
- El idioma del pitch afecta la fluidez percibida. Para hablantes no nativos, la estrategia más robusta es apoyar más carga en lo visual y en el texto escrito, y menos en la oratoria.
- Los sesgos por género y apariencia están documentados en contextos vecinos (Brooks et al. 2014). Eso no se resuelve desde el pitch, pero sí justifica preferir evidencia verificable que no dependa de quién la presenta.
- **Incertidumbre del resultado.** Con bajo acuerdo entre jurados (Pier et al. 2018), un buen proyecto puede perder y uno flojo ganar. Esto tiene dos consecuencias: no sacar conclusiones de un solo resultado y evaluar la calidad del pitch con métodos propios, no con el premio.

### VIII.3 Riesgos de sobreajuste

1. **A una rúbrica.** Se pierde la coherencia del proyecto y se cae en los criterios ocultos.
2. **A un jurado imaginado.** Optimizar para un jurado técnico que no existe aleja a los generalistas que sí están.
3. **A los ganadores visibles.** Copiar la forma de los relatos de ganadores sin ver a los perdedores que hicieron lo mismo.
4. **A tu propio historial.** Tres hackathones no son una muestra. Si ganaste con un formato, eso no prueba que el formato haya causado la victoria.

### VIII.4 Experimentos para verificar mejoras

Como el resultado del hackathon es ruidoso, conviene medir variables intermedias que sí controlás: comprensión, recuerdo, credibilidad y detección de afirmaciones falsas.

| Prueba | Qué mide | Procedimiento | Criterio de éxito |
| --- | --- | --- | --- |
| Test de 5 segundos | Si la apertura comunica qué es | Mostrar la primera diapositiva, el primer plano del video o las primeras líneas del README durante 5 s a 5 personas que no conocen el proyecto; preguntar "¿qué hace esto y para quién?" | Al menos 4 de 5 responden algo compatible con la afirmación central |
| Test de parafraseo | Comprensión | Después del pitch completo, pedir que expliquen el proyecto en una frase a un tercero | La frase contiene problema + mecanismo, sin errores materiales |
| Test de recuerdo diferido | Memoria | 24 horas después, preguntar qué recuerdan | Recuerdan la afirmación central y la prueba, no solo un chiste o una imagen |
| Test de afirmación falsa | Si el pitch induce creencias falsas | Preguntar "¿esto ya está en producción?", "¿cuántos usuarios tiene?", "¿la demo usaba datos reales?" | Las respuestas coinciden con la realidad; cualquier creencia falsa es un error del pitch, aunque nadie la haya dicho |
| Revisión adversarial | Robustez | Alguien con perfil de jurado especialista intenta encontrar la afirmación más débil en 10 minutos | Cada afirmación atacada tiene respuesta preparada o se elimina |
| A/B con evaluadores ciegos | Qué versión funciona mejor | Dos versiones del mismo pitch; cada evaluador ve una sola (entre sujetos) o ambas en orden contrabalanceado (intra sujetos); puntuar con la rúbrica real | Diferencia consistente en la dirección esperada; con muestras chicas, tratar como indicio, no como prueba |
| Lectura fría del README | Evaluación asincrónica | Alguien sin contexto intenta correr el proyecto siguiendo solo el README | Lo logra sin preguntar; si pregunta, cada pregunta es un defecto del README |

Notas de método:

- Con 5 a 10 evaluadores no hay potencia estadística. Estas pruebas detectan problemas grandes (nadie entiende la apertura), no diferencias finas.
- Para A/B, fijar de antemano qué se mide y qué diferencia cuenta como mejora. Si no, cualquier resultado parece confirmar lo que ya creías.
- Los evaluadores deben parecerse al jurado esperado. Colegas que conocen el proyecto no sirven para la prueba de 5 segundos.
- La prueba de afirmación falsa es la que conecta comunicación y honestidad: mide lo que el público cree, no lo que dijiste. Un pitch puede no contener ninguna mentira literal y aun así inducir una creencia falsa.

## Tabla de hallazgos con nivel de evidencia

Escala: **A** = experimento o cuasi experimento revisado por pares, replicado o con datos grandes; **B** = estudio revisado por pares en contexto vecino, sin réplica directa; **C** = revisión, teoría bien establecida aplicada por analogía; **D** = casos, testimonios o razonamiento propio. La columna de validez indica cuánto se puede trasladar a un hackathon.

| # | Hallazgo | Nivel | Validez para hackathones | Limitación principal | Fuente |
| --- | --- | --- | --- | --- | --- |
| H1 | Un pitch más claro ayuda a los expertos a distinguir ideas buenas de malas, en ambas direcciones | B | Media | Inversores, no jurados de hackathon; pitches de 90 s | Clingingsmith y Shane 2018 |
| H2 | La preparación percibida pesa más que la pasión mostrada | B | Media | Contexto de capital de riesgo | Chen, Yao y Kotha 2009 |
| H3 | Los evaluadores descartan primero por defectos fatales antes de ponderar | B | Media-alta | Codificación de TV (Dragons' Den) | Maxwell et al. 2011 |
| H4 | La novedad alta se penaliza; la cercanía al área del evaluador también | A/B | Media | Propuestas científicas y de I+D | Boudreau et al. 2016; Criscuolo et al. 2017 |
| H5 | La carga del panel reduce la preferencia por novedad | B | Media | Una sola firma | Criscuolo et al. 2017 |
| H6 | Hay efectos de orden y de secuencia en evaluación por jurados | B | Media | Resultados mixtos en réplicas de gimnasia | Bruine de Bruin 2005; Criscuolo et al. 2021; Damisch et al. 2006 |
| H7 | El acuerdo entre evaluadores expertos sobre propuestas de calidad similar es bajo | B | Alta como advertencia | Muestra de 25 propuestas | Pier et al. 2018 |
| H8 | La fluidez de procesamiento aumenta la verdad y el agrado percibidos | A/C | Alta como mecanismo | Laboratorio | Alter y Oppenheimer 2009 |
| H9 | Diseño multimedia: coherencia, señalización y segmentación mejoran comprensión | A | Media | Mide aprendizaje; se invierte parcialmente con expertos | Mayer 2017; Kalyuga et al. 2003 |
| H10 | La incertidumbre numérica casi no daña la confianza en la fuente; la verbal daña más | A | Media | Público general, no jurados técnicos | van der Bles et al. 2020 |
| H11 | Ejes truncados en barras exageran diferencias percibidas, aun con avisos | A | Alta | Crowdsourcing | Pandey et al. 2015; Correll et al. 2020 |
| H12 | Hay sesgo por género del presentador en evaluaciones de pitch | B | Media | Réplica parcial; atractivo no replicó | Brooks et al. 2014 y réplica |
| H13 | Bajo incertidumbre, se reconoce peor la creatividad | B | Baja-media | Laboratorio | Mueller et al. 2012 |
| H14 | Ganar se asocia con continuidad del proyecto | D | Media | Tesis, no revisada por pares; dirección causal ambigua | Tesis Universidad de Tartu |
| H15 | La mayoría de los proyectos de hackathon no sigue activa a los 5-6 meses | B | Alta | Devpost y MLH, no todo el universo | Nolte et al. 2020; análisis MLH |
| H16 | Más competidores reducen el esfuerzo pero aumentan la chance de soluciones extremas en problemas inciertos | B | Media | Concursos de software, no hackathones presenciales | Boudreau, Lacetera y Lakhani 2011 |
| H17 | Las rúbricas convergen en idea, implementación, impacto y diseño; algunas tienen capas no públicas | D | Alta | Muestra no sistemática de rúbricas | Rúbricas citadas en Bloque I |
| H18 | Admitir limitaciones aumenta la credibilidad ante jurados | D | Desconocida | Teoría de señalización + testimonio | Bloque III; testimonio de jurado |
| H19 | El engaño se detecta en verificaciones posteriores y tiene costo permanente | D | Media | Casos visibles; los no detectados no se conocen | PetFinder, HackMIT, Salesforce |
| H20 | Ganar la métrica del concurso no implica resolver el problema del sponsor | D | Media | Un caso emblemático | Netflix Prize |

## Checklist de auditoría de honestidad y credibilidad

Para usar antes de enviar cualquier pitch, video, deck, README o ficha. Cada ítem fallido bloquea el envío hasta corregirse.

**Afirmaciones**

- [ ] Cada afirmación factual tiene una evidencia identificable: demo, archivo del repo, fuente pública o "lo observamos nosotros" dicho como tal.
- [ ] Cada cifra tiene denominador, unidad y origen. Ninguna cifra de mercado sin fuente.
- [ ] No hay usuarios, pilotos, testimonios, alianzas ni "conversaciones con" que no existan o no sean verificables hoy.
- [ ] Los verbos de madurez ("en producción", "probado", "escala", "seguro") están respaldados o fueron reemplazados.
- [ ] Los adjetivos superlativos ("primero", "único", "revolucionario") fueron verificados o eliminados.

**Demo y material visual**

- [ ] Todo lo simulado, mockeado, precargado o con datos sintéticos está etiquetado si es material (test del Bloque IV.4).
- [ ] El video no tiene cortes que oculten fallas sin declararlo.
- [ ] Capturas y videos corresponden a la versión entregada.
- [ ] Los gráficos de barras empiezan en cero o declaran el recorte; los ejes tienen unidades.
- [ ] Las animaciones no se confunden con salida real del sistema.

**Comparaciones y diferenciación**

- [ ] La alternativa comparada está bien configurada y en versión vigente.
- [ ] Hay al menos un eje en que la alternativa es mejor, y se dice si es relevante.

**Reglas y origen del trabajo**

- [ ] Está declarado qué se hizo antes del evento y qué durante, según exigen las reglas.
- [ ] El proyecto no fue presentado en otro hackathon, o está declarado y permitido.
- [ ] Las licencias de código y assets de terceros están atribuidas.
- [ ] El uso del producto del sponsor es real y verificable en el repo.

**Limitaciones**

- [ ] Las 1-2 limitaciones materiales aparecen en el pitch o video.
- [ ] El README tiene una sección de limitaciones y una tabla real / simulado / pendiente.

**Prueba de creencias inducidas**

- [ ] Después de ver el material, una persona externa no cree nada falso sobre madurez, usuarios, datos reales ni resultados (test de afirmación falsa del Bloque VIII).

**Repositorios**

- [ ] Si el repositorio es open source de uso general, no contiene material de la submission (ver skill de separación OSS/hackathon en la arquitectura).

## Bloque IX — Arquitectura de skills

La familia tiene 15 skills: un orquestador, trece skills de trabajo y una skill de higiene de repositorios que pediste aparte. Todas comparten tres invariantes: (1) ninguna inventa evidencia ni la "mejora"; (2) toda salida que contenga afirmaciones pasa por `hackathon-claim-audit` antes de considerarse terminada; (3) todo material de submission vive fuera de los repositorios OSS, en `<Escritorio>/<Nombre del hackathon> DEMO/`. La especificación completa de cada una (procedimiento, verificaciones, anti-patrones, límites) está en los SKILL.md entregados junto con este informe.

### IX.1 Catálogo

| # | Skill | Objetivo | Trigger | Inputs | Outputs | Hallazgos que la sostienen |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | `hackathon-prep` | Orquestar la preparación y decidir qué skills correr | "preparar submission", "tengo un hackathon", nombre de evento + deadline | URL o texto del evento, repo, deadline | Inventario completo de trabajo en `DEMO/plan.md` | Todos |
| 1 | `hackathon-oss-separation` | Mantener el material de hackathon fuera de repos OSS | Cualquier archivo de submission a punto de crearse dentro de un repo | Repo, nombre del evento | Carpeta `DEMO` en el Escritorio, manifiesto con SHA del repo | Bloque IV.5; casos 9 y 10 |
| 2 | `hackathon-rubric-analysis` | Leer reglas y rúbrica, detectar pesos, criterios implícitos y causas de descalificación | Reglas, página de Devpost, bases | Reglas, FAQ, premios por track | `rubric.md`: criterios, pesos, descalificadores, entregables, formato de evaluación | H17; Bloque I.3 |
| 3 | `hackathon-competitive-fit` | Decidir si entrar, en qué track y con qué ángulo | Antes de comprometer tiempo; elección de track | `rubric.md`, estado real del proyecto, ganadores previos si existen | `fit.md` con decisión y riesgos | H4, H16; Bloque III.3 |
| 4 | `hackathon-evidence-selection` | Elegir las pruebas más caras de falsificar disponibles | Antes de escribir pitch o grabar | Repo, resultados, logs | `evidence.md`: inventario real / simulado / pendiente y prueba principal | H1, H3; Bloque III.2 |
| 5 | `hackathon-claim-audit` | Auditar cada afirmación contra su evidencia | Cualquier texto destinado al jurado; siempre al final | Borrador + `evidence.md` | Informe de afirmaciones con veredicto por línea; bloqueos | H8, H19; checklist |
| 6 | `hackathon-complexity-translation` | Escalera de detalle en 1 oración / 1 párrafo / 1 página, con analogías con límite | Arquitectura difícil de explicar; jurado mixto | Repo, diagrama, `evidence.md` | `ladder.md` | H9; Bloque V.5 |
| 7 | `hackathon-verifiable-narrative` | Armar el mensaje problema → mecanismo → prueba → límite → diferencia → próximo paso | Redactar pitch, guión de video, ficha | `ladder.md`, `evidence.md`, `rubric.md` | `narrative.md` con mensaje central y frase repetible | H1, H2, H10; Bloque IV |
| 8 | `hackathon-format-adapter` | Ajustar el mensaje a formato y tipo de jurado | Formato conocido (30 s, 3 min, video, deck) | `narrative.md`, formato, jurado | Guión o estructura con presupuesto de palabras | Bloque VI |
| 9 | `hackathon-demo-design` | Diseñar la demo como prueba, con plan B y etiquetado de simulación | Preparar demo en vivo o grabada | `evidence.md`, formato | `demo-script.md`, checklist técnico, plan B | H3; Bloque III.2, IV.4 |
| 10 | `hackathon-visual-cognition` | Diseñar diagramas, gráficos y capturas que no engañen | Crear o revisar visuales | Visuales, datos | Lista de correcciones; especificación de visuales | H9, H11; Bloque V.3-V.4 |
| 11 | `hackathon-async-readme` | Preparar README y ficha para evaluación asincrónica | Evaluación por Devpost, repo o formulario | `narrative.md`, `evidence.md` | Texto de ficha y README de submission en `DEMO/` | H7; Bloque IV.3 |
| 12 | `hackathon-video-review` | Revisar guiones y cortes de video | Video de 90 s a 5 min | Guión, video o transcripción | Informe por segundo: primer plano, legibilidad, cortes, límite de tiempo | H9; Bloque VI |
| 13 | `hackathon-judge-qa-prep` | Preparar respuestas a preguntas técnicas y hostiles | Presentación con Q&A | Todo lo anterior | `qa.md`: preguntas probables y temidas con respuestas de 20-30 s | H2, H18 |
| 14 | `hackathon-adversarial-review` | Atacar el pitch como jurado escéptico y diseñar pruebas de comprensión | Antes de enviar o presentar | Material final | Informe de ataques y protocolo de pruebas (5 s, parafraseo, afirmación falsa) | H6, H7; Bloque VIII |

### IX.2 Flujo y dependencias

Orden recomendado (el orquestador puede saltear pasos que no aplican):

1. `hackathon-oss-separation` (crear la carpeta DEMO antes de producir cualquier archivo)
2. `hackathon-rubric-analysis`
3. `hackathon-competitive-fit`
4. `hackathon-evidence-selection`
5. `hackathon-complexity-translation`
6. `hackathon-verifiable-narrative`
7. `hackathon-format-adapter`
8. En paralelo según formato: `hackathon-demo-design`, `hackathon-visual-cognition`, `hackathon-async-readme`, `hackathon-video-review`
9. `hackathon-judge-qa-prep`
10. `hackathon-adversarial-review`
11. `hackathon-claim-audit` (compuerta final; también se invoca dentro de 6, 7, 11 y 12)

Dependencias fuertes: nada que contenga afirmaciones se escribe sin `evidence.md`; nada se entrega sin pasar `claim-audit`. Relaciones con skills que ya tenés: `claim-provenance-discipline` y `daubert-defensible-writing` como complementos de `claim-audit`; `git-discipline` e `irreversible-action-gate` como complementos de `oss-separation` cuando haya que sacar material ya commiteado.

### IX.3 Decisiones de diseño

- **Archivos intermedios en disco.** Cada skill escribe su salida en `DEMO/`. Funciona con cualquier agente de CLI y deja una traza revisable.
- **Un orquestador liviano.** Solo decide y encadena; el conocimiento vive en cada skill para que puedas invocarlas sueltas.
- **La auditoría como compuerta, no como sugerencia.** Si una afirmación no tiene evidencia, la skill la marca como bloqueante y propone reformulación honesta; no la suaviza en silencio.
- **Sin calendario.** El orquestador produce el inventario completo del trabajo con dependencias; vos decidís el orden temporal.

## Preguntas abiertas

1. ¿Qué proporción de la varianza de resultados en hackathones con jurado humano se explica por calidad técnica, por comunicación y por azar? Requiere datos de puntajes por jurado, que los organizadores casi nunca publican.
2. ¿Admitir una limitación sube o baja el puntaje en hackathones? Hoy hay teoría y testimonios, no experimentos.
3. ¿Los efectos de orden aparecen en ferias tipo expo (MLH) igual que en presentaciones en escenario?
4. ¿El sesgo contra la novedad alta es mayor con 3 minutos por proyecto que en paneles de I+D? La teoría predice que sí.
5. ¿Las demos con entrada elegida por el jurado mejoran la credibilidad tanto como predice la teoría de señalización, o el riesgo de falla visible compensa?
6. ¿Cómo cambian las evaluaciones cuando parte del jurado es un modelo de lenguaje (ya hay plataformas que lo ofrecen)? Afecta qué se optimiza en el README y la ficha.
7. ¿Diferencias culturales concretas en hackathones latinoamericanos, europeos y estadounidenses? No encontré estudios.
8. ¿Qué tan seguido se descalifican proyectos por trabajo previo no declarado, y con qué criterio se distingue "idea previa" de "código previo"? Las reglas varían y la aplicación no se publica.
9. ¿Los premios de sponsor tienen menos competencia efectiva que el premio general? Plausible por teoría de torneos; sin datos.
10. Para tu propio historial: registrar en cada evento la rúbrica, el formato, el material enviado, el resultado y, si se consigue, el feedback de jurados, para tener al menos una base comparativa propia.

## Bibliografía anotada

Enlaces a las páginas efectivamente consultadas en esta investigación. Las referencias marcadas como clásicas no se reverificaron en línea en esta sesión.

**Hackathones**

- Nolte, Chounta y Herbsleb (2020). What Happens to All These Hackathon Projects? PACM HCI 4(CSCW2). Análisis de continuidad con datos de Devpost; base de H15. [PDF](https://par.nsf.gov/servlets/purl/10284449)
- Medina Angarita y Nolte (2020). What Do We Know About Hackathon Outcomes… Revisión sistemática de resultados y diseño; no estudia qué gana. [Springer](https://link.springer.com/10.1007/978-3-030-58157-2_4)
- Schulten y Chounta (2024). How do we learn in and from Hackathons? Revisión de 39 estudios; no encuentra prueba concluyente de aprendizaje. [PDF](https://link.springer.com/content/pdf/10.1007/s10639-024-12668-1.pdf)
- Tesis de la Universidad de Tartu sobre continuidad en hackathones universitarios. Base de H14; no revisada por pares. [DSpace](https://dspace.ut.ee/items/a28833b7-c2b8-40b6-9742-ec3d89f82f4b)
- Análisis de 11.889 proyectos MLH con GitHub. [SSRC](https://just-tech.ssrc.org/?p=4573)
- Preprint sobre creatividad en 193.353 proyectos de Devpost (2025). Fuente de datos, sin revisión por pares. [arXiv](https://arxiv.org/pdf/2503.04290)
- MLH Hackathon Organizer Guide, plan de jurados y control de trampas. [Guía](https://guide.mlh.io/general-information/judging-and-submissions/draft-up-a-judging-plan)

**Pitch, inversión y decisiones de evaluadores**

- Clingingsmith y Shane (2018). Training Aspiring Entrepreneurs to Pitch Experienced Investors. Management Science 64(11). Experimento de campo; base de H1. [PDF](https://files.cercomp.ufg.br/weby/up/1267/o/Clingingsmith_and_Shane_-_2017_-_Training_Aspiring_Entrepreneurs_to_Pitch_Experienced_Investors_Evidence_from_a_Field_Experiment_in_the_United_States.pdf?1656363197)
- Chen, Yao y Kotha (2009). Entrepreneur Passion and Preparedness in Business Plan Presentations. AMJ 52(1). [Resumen](https://data.zhenzhi.com/details/1/861740525/1/3)
- Maxwell, Jeffrey y Lévesque (2011). Business angel early stage decision making. JBV 26(2). [EconPapers](https://econpapers.repec.org/RePEc:eee:jbvent:v:26:y:2011:i:2:p:212-225)
- Huang y Pearce (2015). Managing the Unknowable. ASQ 60(4). Intuición de inversores ángeles. [PDF](https://escholarship.org/content/qt54j7z903/qt54j7z903.pdf?t=nybbja)
- Brooks, Huang, Kearney y Murray (2014). Investors prefer entrepreneurial ventures pitched by attractive men. PNAS 111(12). [MIT DSpace](https://dspace.mit.edu/handle/1721.1/91283); réplica registrada: [FORRT](https://forrt.org/flora-replication-atlas/doi/10.1073/pnas.1321202111/)
- Mollick (2014). The dynamics of crowdfunding. JBV 29(1). Señales de calidad y preparación. [PDF](https://leeds-faculty.colorado.edu/bhagat/Dynamics-of-Crowdfunding.pdf)

**Evaluación de novedad, paneles y acuerdo**

- Boudreau, Guinan, Lakhani y Riedl (2016). Looking Across and Looking Beyond the Knowledge Frontier. Management Science 62(10). [LBS](https://lbsresearch.london.edu/id/eprint/175)
- Criscuolo, Dahlander, Grohsjean y Salter (2017). Evaluating Novelty. AMJ 60(2). [Bath](https://researchportal.bath.ac.uk/en/publications/evaluating-novelty-the-role-of-panels-in-the-selection-of-rampd-p/)
- Criscuolo et al. (2021). The Sequence Effect in Panel Decisions. Organization Science 32(4). Acceso abierto. [PDF](https://wrap.warwick.ac.uk/176162/1/orsc.2020.1413.pdf)
- Pier et al. (2018). Low agreement among reviewers evaluating the same NIH grant applications. PNAS 115(12). [PubMed](https://pubmed.ncbi.nlm.nih.gov/29507248/)
- Mueller, Melwani y Goncalo (2012). The Bias Against Creativity. Psychological Science. [Penn](https://repository.upenn.edu/mgmt_papers/66)
- Boudreau, Lacetera y Lakhani (2011). Incentives and Problem Uncertainty in Innovation Contests. Management Science 57(5). [EconPapers](https://econpapers.repec.org/RePEc:inm:ormnsc:v:57:y:2011:i:5:p:843-863)

**Juicio, orden y sesgos**

- Bruine de Bruin (2005). Save the last dance for me. Acta Psychologica 118(3). [Registro](https://lida.sport-iat.de/ta/Record/4009866)
- Damisch, Mussweiler y Plessner (2006). Olympic medals as fruits of comparison? JEP: Applied 12(3). [Registro](https://heibib.ub.uni-heidelberg.de/search/Record/181132472X)
- Danziger, Levav y Avnaim-Pesso (2011) y críticas de Weinshall-Margel y Shapard (2011) y Glöckner (2016). Se cita como ejemplo de efecto probablemente sobreestimado. [Resumen](https://en.wikipedia.org/wiki/Hungry_judge_effect), [Glöckner](https://doaj.org/article/a6508d29977845e885f7ebe0f4f103fc)
- Alter y Oppenheimer (2009). Uniting the Tribes of Fluency. PSPR 13(3). [Registro](https://peeref.com/works/64592927)
- Thorndike (1920), efecto halo; Tversky y Kahneman (1974), anclaje. Clásicas.

**Comunicación, visualización e incertidumbre**

- Mayer (2017). Using multimedia for e-learning. JCAL. Tamaños de efecto de 12 principios. [Registro](https://zendy.io/title/10.1111/jcal.12197)
- Kalyuga, Ayres, Chandler y Sweller (2003). The expertise reversal effect. Educational Psychologist 38(1). [UOW](https://ro.uow.edu.au/edupapers/136)
- van der Bles et al. (2020). The effects of communicating uncertainty on public trust in facts and numbers. PNAS 117(14). [Registro](https://cir.nii.ac.jp/crid/1360576123220091264?lang=en)
- Pandey et al. (2015). How Deceptive are Deceptive Visualizations? CHI. [BibTeX](https://bibtex.github.io/CHI-2015-PandeyRSNB.html)
- Correll, Bertini y Franconeri (2020). Truncating the Y-Axis: Threat or Menace? CHI. [arXiv](https://ar5iv.arxiv.org/html/1907.02035)

**Teoría económica**

- Strathern (1997). "Improving ratings": audit in the British University system. European Review 5(3). Formulación popular de Goodhart. [Referencia](https://Www.wikipedia.org/wiki/Goodhart%27s_law)
- Spence (1973), señalización; Akerlof (1970), selección adversa; Crawford y Sobel (1982), cheap talk. Clásicas.

**Rúbricas y documentos de eventos**

- Okta Hackathon 2021. [Foro](https://devforum.okta.com/t/what-are-the-judging-criteria-for-the-hackathon/15842)
- HackCC 2025. [Reglas](https://kelaenderkoe.pages.dev/patterns-https-hackcc-2025.devpost.com/rules)
- EUvsVirus 2020, guía de jurados. [PDF](https://moodle2.units.it/pluginfile.php/395562/mod_resource/content/0/LAB%204%2020%20maggio%20Juror%20Guide%20Kit%20%281%29.pdf)
- Hacktivate CarWale. [Criterios](https://hacktivate.carwale.com/judging-criteria.html)
- Mozilla Jetpack for Learning. [Wiki](https://m.wiki.mozilla.org/Education/Projects/JetpackForLearning/Criteria)
- UNIHACK, límite de video. [Notion](https://unihack.notion.site/How-to-submit-your-project-2e05dc7357fb4d3ba3e23f51207f996a)

**Casos**: ver enlaces en la tabla del Bloque VII.
