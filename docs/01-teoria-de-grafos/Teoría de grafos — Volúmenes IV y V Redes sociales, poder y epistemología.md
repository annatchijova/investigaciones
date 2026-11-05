# Teoría de grafos — Volúmenes IV y V: Redes sociales, poder y epistemología

Nov 5, 2026 · @Anna Tchijova

## Cómo leer estos volúmenes

El Volumen IV recorre la tradición del análisis de redes sociales y la ciencia de redes: qué conceptos produjo, con qué evidencia y con qué críticas. El Volumen V se pregunta por las condiciones de ese conocimiento: qué hace visible un grafo, qué oculta, quién decide qué cuenta como nodo o vínculo, y cómo se relaciona esa forma de mirar con las teorías del poder. Incluye la crítica epistemológica de la Parte XIV del pedido (V.5).

Las etiquetas son las del Volumen 0, y aquí la distinción entre ellas es especialmente importante: casi todos los conceptos sociológicos de esta sección tienen una **definición formal** (\[Def\], una métrica), una **hipótesis sustantiva** que la motivó (\[Hip\]), algunos **hallazgos empíricos** (\[Emp\]) y varias **interpretaciones** en disputa (\[Int\]). El error más común en la literatura aplicada es pasar de la primera a la última sin las intermedias.

**Prerrequisitos.** Volumen I y las secciones II.7 (modelos nulos), II.13 (temporales), II.15 (incertidumbre) y III.13–III.14 (centralidades y comunidades). La formación en ciencias sociales es la que más rinde aquí; lo técnico se recupera donde hace falta.

**Nota sobre las citas.** Se citan obras por autor, año, título y revista o editorial. Son obras clásicas o ampliamente citadas cuya existencia y contenido central están bien establecidos; los enlaces verificados se consolidan en el Volumen IX. Cuando un resultado empírico fue discutido o no se replicó, se dice.

## IV.1 Genealogía: de Simmel a Barabási, con sus críticas

La historia del análisis de redes no es lineal: hay al menos cuatro tradiciones que se ignoraron mutuamente durante décadas. Freeman, *The Development of Social Network Analysis: A Study in the Sociology of Science* (Empirical Press, 2004), es la historia de referencia.

**Georg Simmel (1858–1918): la forma de las relaciones.** En *Soziologie* (1908), Simmel propuso estudiar las **formas** de socialización con independencia de sus contenidos. Dos contribuciones son directamente formales: el análisis de la **díada y la tríada** (agregar un tercero cambia cualitativamente la relación: aparecen el mediador, el *tertius gaudens* que se beneficia del conflicto entre dos, y el *divide et impera*), y la idea de la intersección de círculos sociales (*Kreuzung sozialer Kreise*): la individualidad moderna como posición única en la intersección de muchas afiliaciones. Lo primero anticipa a Burt (IV.3); lo segundo, la dualidad persona–grupo de Breiger y los hipergrafos (II.14). *Límite:* Simmel no tenía un instrumento de medición ni una teoría de la evidencia; sus formas son tipos ideales.

**Jacob L. Moreno (1889–1974): el sociograma.** En *Who Shall Survive?* (1934), Moreno y Helen Jennings representaron con puntos y flechas las elecciones de compañía entre las internas de una institución para niñas en Hudson, Nueva York, y usaron el resultado para reorganizar las residencias. Introdujeron la **sociometría**: preguntar a cada persona a quién elige, y representar las respuestas. Mucho de lo que vino después nace aquí: estrellas, aislados, reciprocidad, la red como instrumento de intervención. *Crítica:* la escena fundacional es una intervención sobre personas institucionalizadas con fines de control; el análisis de redes nace, entonces, ligado a la gestión de poblaciones (V.2, Foucault).

**La antropología de Manchester.** John Barnes ("Class and Committees in a Norwegian Island Parish", *Human Relations*, 1954) usó "red social" para describir los lazos de parentesco, amistad y vecindad que atraviesan las instituciones formales. Elizabeth Bott (*Family and Social Network*, 1957) mostró que la densidad de la red de una pareja se asociaba con la división de roles conyugales. J. Clyde Mitchell (1969) sistematizó conceptos como densidad, alcance y multiplexidad. Esta tradición es etnográfica: las redes se reconstruían con observación prolongada, y el significado de cada vínculo era parte del dato. Es la contracara de la ciencia de redes posterior.

**La revolución de Harvard: Harrison White.** En los años setenta, White y sus estudiantes (Breiger, Boorman, Wellman, Granovetter, Schwartz) convirtieron el análisis de redes en un programa estructural. El concepto central es la **equivalencia estructural** (Lorrain y White, *Journal of Mathematical Sociology*, 1971): dos actores son equivalentes si tienen los mismos vínculos con los mismos terceros, aunque no estén vinculados entre sí. Los **modelos de bloques** (White, Boorman y Breiger, "Social Structure from Multiple Networks", *American Journal of Sociology*, 1976) agrupan actores equivalentes en posiciones y describen la estructura como relaciones entre posiciones, no entre personas. La idea es que los **roles** son patrones de relación, no atributos. White se volvió después muy crítico del estructuralismo puro: en *Identity and Control* (1992; 2.ª ed. 2008) propone que las redes son tramas de historias (*stories*) y significados, y que la estructura no puede separarse de las narrativas con que los actores buscan control. Es una autocrítica del propio programa que fundó.

**Granovetter y Burt.** Desarrollados en IV.2 y IV.3.

**La ciencia de redes de los físicos (1998 en adelante).** Watts y Strogatz ("Collective dynamics of 'small-world' networks", *Nature*, 1998) mostraron que reconectar al azar una pequeña fracción de las aristas de una grilla regular reduce mucho las distancias sin destruir el agrupamiento local: el **mundo pequeño** es compatible con la cohesión local. Barabási y Albert ("Emergence of scaling in random networks", *Science*, 1999) propusieron el **apego preferencial** (los vértices nuevos se conectan con probabilidad proporcional al grado) como mecanismo de las distribuciones de grado de ley de potencias, que llamaron **libres de escala**.

*Críticas a esta tradición, que conviene conocer como parte del canon:*

- **Universalidad discutida.** Broido y Clauset ("Scale-free networks are rare", *Nature Communications*, 2019) analizaron casi mil redes y encontraron que la evidencia fuerte de leyes de potencias es rara; las redes sociales en particular rara vez la muestran. Clauset, Shalizi y Newman ("Power-law distributions in empirical data", *SIAM Review*, 2009) ya habían mostrado que los ajustes por regresión lineal en escala logarítmica, habituales en la literatura, son estadísticamente inválidos. La respuesta de Barabási y colegas sostuvo que la definición de "libre de escala" usada era demasiado estricta; el debate sigue abierto, y se resume así: hay distribuciones de colas pesadas en muchas redes, y su forma exacta y su mecanismo generador están en disputa.
- **Equifinalidad.** Muchos mecanismos distintos generan colas pesadas (copia de vínculos, optimización, heterogeneidad de atributos). Que el apego preferencial las reproduzca no prueba que sea el mecanismo.
- **Pérdida de contenido.** Los modelos de la física estudian topología sin significado del vínculo, lo que choca con la tradición antropológica y con la autocrítica de White. Watts, que proviene de esa tradición, ha sido uno de los más cuidadosos en señalar los límites de explicar fenómenos sociales con modelos de red sin teoría de la acción.

**Otros nombres necesarios.** Linton Freeman (centralidad, 1978/79); Barry Wellman (comunidad personal y la "pregunta de la comunidad", 1979); Nan Lin (capital social, 2001); Ronald Breiger (dualidad persona–grupo, 1974); Mark Granovetter (embeddedness, 1985); y, en América Latina, Larissa Adler de Lomnitz (IV.6).

## IV.2 Vínculos fuertes y débiles; homofilia

### Vínculos fuertes y débiles

**\[Def\]** Granovetter ("The Strength of Weak Ties", *American Journal of Sociology*, 1973) definió la fuerza de un vínculo como una combinación de tiempo, intensidad emocional, intimidad y servicios recíprocos. En la práctica se operacionaliza por frecuencia de contacto, duración o cercanía declarada. Un **puente local** es una arista cuya remoción alarga mucho la distancia entre sus extremos.

**\[Hip\] El argumento.** (1) Si A tiene vínculos fuertes con B y con C, es muy probable que B y C se vinculen (la "tríada prohibida" es la ausencia de ese cierre). (2) Por lo tanto, un puente local casi nunca es fuerte. (3) Por lo tanto, la información nueva, que viene de otros círculos, viaja sobre todo por vínculos débiles.

**\[Emp\] Evidencia.** El estudio de búsqueda de empleo de Granovetter (*Getting a Job*, 1974; muestra de profesionales, técnicos y gerentes de un suburbio de Boston) encontró que entre quienes consiguieron trabajo por contactos, la mayoría veía al contacto ocasional o raramente. Onnela y colegas (*PNAS*, 2007) observaron, en millones de usuarios de telefonía, que los vínculos de mayor intensidad tienden a estar dentro de grupos densos y los débiles entre grupos, como predice el argumento. Rajkumar y coautores (*Science*, 2022), en experimentos aleatorizados sobre la plataforma LinkedIn, encontraron que los vínculos **moderadamente** débiles fueron los más útiles para la movilidad laboral: los más débiles de todos ayudaban menos.

**\[Int\] Matices.** Bian (*American Sociological Review*, 1997) mostró que en la China urbana de la economía planificada los empleos se obtenían por vínculos **fuertes**, porque lo que circulaba no era información sino **influencia** sobre quien decidía. La utilidad de un tipo de vínculo depende de qué circula y del contexto institucional. Krackhardt (1992) defendió también la "fuerza de los vínculos fuertes" en contextos de crisis y cambio organizacional, donde la confianza importa más que la novedad.

**Métrica frente a interpretación.** La **métrica** ("esta arista es puente local y débil") se calcula. Que "por allí llega información nueva" es una **hipótesis** que requiere observar la información. Y que "esta persona obtuvo ventajas por sus vínculos débiles" es una afirmación **causal** que requiere un diseño que la sostenga.

### Homofilia

**\[Def\]** Tendencia a que los vínculos se den entre personas similares en algún atributo. Se mide comparando la proporción de vínculos entre iguales con la esperada sin preferencia (por ejemplo, el índice E-I de Krackhardt y Stern, 1988, o la asortatividad de Newman, 2003).

**\[Emp\]** La revisión de McPherson, Smith-Lovin y Cook ("Birds of a Feather: Homophily in Social Networks", *Annual Review of Sociology*, 2001) documenta homofilia fuerte por raza y etnia, seguida de edad, religión, educación, ocupación y género, en casi todo tipo de vínculo.

**Distinción fundamental.** Una correlación de atributos entre vecinos puede deberse a:

1. **Homofilia de base** (*baseline homophily*): el entorno disponible ya es homogéneo (escuela, barrio, trabajo). Feld ("The Focused Organization of Social Ties", *American Journal of Sociology*, 1981) llamó **focos** a esos contextos que organizan los encuentros.
2. **Homofilia de elección** (*inbreeding homophily*): se elige entre las opciones disponibles a los similares.
3. **Influencia:** los vinculados se vuelven similares.
4. **Exposición común:** algo externo afecta a ambos.

Kossinets y Watts ("Origins of Homophily in an Evolving Social Network", *American Journal of Sociology*, 2009) mostraron, con datos de correo de una universidad, que buena parte de la homofilia observada se explica por estructura (focos compartidos, cierre triádico) amplificada en el tiempo, más que por una preferencia fuerte.

**Consecuencias políticas.** La homofilia de base es producto de la segregación institucional (escuelas, barrios, mercados de trabajo). Tratar la homofilia como "preferencia" individual puede naturalizar estructuras de desigualdad. Esta tensión vuelve en IV.5.

**Problema inferencial.** Por Shalizi y Thomas (2011), homofilia e influencia están confundidas en datos observacionales (Evaluación, E3). Cualquier afirmación del tipo "X influyó en Y porque estaban vinculados y luego hicieron lo mismo" requiere un diseño causal (IV.4).

## IV.3 Capital social, intermediación y agujeros estructurales

"Capital social" designa al menos tres conceptos distintos, y en la literatura de redes se los mezcla con frecuencia.

| Autor | Qué es el capital social | Nivel | Relación con la red |
| --- | --- | --- | --- |
| Bourdieu ("Le capital social. Notes provisoires", Actes de la recherche en sciences sociales, 1980; "The Forms of Capital", 1986) | Recursos actuales o potenciales ligados a la pertenencia a un grupo con relaciones de reconocimiento mutuo, convertibles en otros capitales | Individual y de clase | La red es medio de acumulación y de **reproducción de la desigualdad** |
| Coleman ("Social Capital in the Creation of Human Capital", *American Journal of Sociology*, 1988) | Aspectos de la estructura social que facilitan la acción: obligaciones, confianza, normas | Grupo | **Cierre**: redes densas permiten sanciones y confianza |
| Putnam (*Bowling Alone*, 2000) | Redes, normas y confianza a nivel de comunidad | Comunidad, sociedad | Asociacionismo; distingue capital de unión (*bonding*) y de puente (*bridging*) |
| Lin (*Social Capital: A Theory of Social Structure and Action*, Cambridge, 2001) | Recursos incrustados en la red a los que se accede y se moviliza para fines | Individual | Generador de posiciones; acceso a recursos por alcance |
| Burt (*Structural Holes*, Harvard, 1992) | Ventajas que da una posición de intermediación | Individual | **Agujeros estructurales** |

**La tensión central: cierre contra intermediación.** Coleman sostiene que el capital social surge de redes densas y cerradas, donde todos se conocen y es posible sancionar. Burt sostiene lo contrario: la ventaja surge de ocupar el espacio entre grupos que no se conectan. Burt (*Brokerage and Closure*, Oxford, 2005) propuso que ambos operan: la intermediación produce valor (ideas, oportunidades) y el cierre permite capturarlo y ejecutarlo. *Lectura formal:* son dos regiones de la misma red, y la medida de una es casi la negación de la otra.

**Agujeros estructurales: definiciones formales.** Para un actor i con contactos j:

- **Tamaño efectivo:** número de contactos menos la redundancia media entre ellos.
- **Restricción** (*constraint*): suma, sobre cada contacto j, del cuadrado de la inversión directa e indirecta de i en j. Con pᵢⱼ la proporción del tiempo o la energía de la red de i invertida en j:

```latex
C_i = \sum_{j \neq i} \left( p_{ij} + \sum_{q \neq i,j} p_{iq}\, p_{qj} \right)^2
```

Una restricción baja indica una red de contactos no redundantes: muchos agujeros alrededor de i.

**\[Emp\] Evidencia.** Burt ("Structural Holes and Good Ideas", *American Journal of Sociology*, 2004) mostró, en gerentes de una empresa electrónica, que quienes tenían redes menos restringidas recibían mejores evaluaciones de sus ideas, más ascensos y mejores salarios. Hay replicaciones en contextos corporativos.

**Críticas.**

- **Género y legitimidad.** Burt mismo encontró que la intermediación beneficiaba menos a mujeres y gerentes jóvenes, que necesitaban "tomar prestada" la legitimidad de un patrocinador. La misma posición no rinde lo mismo para todos: la estructura no explica sola el resultado.
- **Causalidad inversa.** Quienes ya son exitosos atraen contactos de grupos diversos. Los diseños transversales no distinguen.
- **Intención y capacidad.** Obstfeld ("Social Networks, the Tertius Iungens Orientation, and Involvement in Innovation", *Administrative Science Quarterly*, 2005) contrapuso al *tertius gaudens* de Simmel el *tertius iungens*, quien conecta a los desconectados en lugar de explotar su separación. La misma posición admite estrategias opuestas.
- **Equivalencia con la intermediación de Freeman.** La centralidad de intermediación (III.13) y la restricción de Burt miden cosas relacionadas pero distintas: la primera depende de caminos mínimos globales; la segunda, solo de la red egocéntrica.

**Intermediarios: tipología.** Gould y Fernandez ("Structures of Mediation", *Sociological Methodology*, 1989) clasificaron la intermediación según la pertenencia de los tres actores a grupos: coordinador (los tres del mismo grupo), consultor (el intermediario de otro grupo), guardián (*gatekeeper*: controla la entrada a su grupo), representante (controla la salida) y enlace (los tres de grupos distintos). Esta tipología es mucho más informativa que un número de intermediación, y es la que el Volumen VI usa para el análisis de intermediarios en redes de corrupción.

**Lo que la métrica no dice.** Un valor bajo de restricción indica una **oportunidad estructural** de intermediar. No dice si la persona intermedia, ni qué controla, ni si obtiene beneficios, ni si lo hace por voluntad propia (un traductor, un abogado o un familiar pueden ocupar esa posición por funciones ajenas al poder).

## IV.4 Difusión y contagio social

**Modelos formales de difusión.** Cada uno corresponde a un supuesto distinto sobre cómo se adopta algo.

| Modelo | Regla de adopción | Representante | Fenómeno típico |
| --- | --- | --- | --- |
| Contagio simple (SI, SIR, SIS) | Cada contacto con un adoptante transmite con probabilidad β, independientemente | Epidemiología; Kermack y McKendrick (1927); Pastor-Satorras y Vespignani (*Physical Review Letters*, 2001) en redes | Información, rumores, enfermedades |
| Umbral | Se adopta si la fracción (o el número) de vecinos adoptantes supera un umbral | Granovetter ("Threshold Models of Collective Behavior", *American Journal of Sociology*, 1978); Watts (*PNAS*, 2002) | Protestas, normas costosas |
| Contagio complejo | Hace falta exposición a **varias** fuentes distintas | Centola y Macy ("Complex Contagions and the Weakness of Long Ties", *American Journal of Sociology*, 2007) | Conductas riesgosas o costosas, movilización |
| Cascadas de información | Los actores observan las decisiones previas y las suman a su información privada | Bikhchandani, Hirshleifer y Welch (1992); Easley y Kleinberg, cap. 16 | Modas, mercados |
| Maximización de influencia | Elegir k semillas para maximizar la difusión esperada | Kempe, Kleinberg y Tardos (KDD, 2003) | Marketing; también campañas de salud |

**\[Teo\] Resultado clave para contagio simple.** En redes con distribución de grados de varianza muy grande, el umbral epidémico tiende a cero cuando la red crece (Pastor-Satorras y Vespignani, 2001): la heterogeneidad de grados facilita la propagación. El valor depende de ⟨k²⟩/⟨k⟩, la misma cantidad de la paradoja de la amistad (Evaluación, E7).

**\[Teo\] Kempe, Kleinberg y Tardos (2003).** Maximizar la influencia es NP-difícil, pero bajo modelos de cascada independiente y de umbral lineal, la función de influencia es submodular, y el algoritmo voraz garantiza una aproximación de factor 1 − 1/e ≈ 0,63. Es un ejemplo perfecto de garantía condicional: vale bajo el modelo, y el modelo es una hipótesis sobre el comportamiento humano.

**Contagio complejo y la inversión del argumento de Granovetter.** Centola y Macy mostraron que, si la adopción requiere refuerzo de varias fuentes, los vínculos largos (puentes) dejan de ser eficientes: un solo contacto a través de un puente no alcanza. Las redes con agrupamiento alto y canales anchos (varios vínculos entre grupos) difunden mejor. Centola ("The Spread of Behavior in an Online Social Network Experiment", *Science*, 2010) lo testeó con un experimento en línea de adopción de un registro de salud: la adopción se difundió más en redes con agrupamiento alto que en redes aleatorias. **La misma estructura facilita o frena la difusión según la regla de adopción.**

**El problema causal.** Christakis y Fowler ("The Spread of Obesity in a Large Social Network over 32 Years", *New England Journal of Medicine*, 2007) reportaron que la obesidad se "contagiaba" hasta tres grados de separación. La crítica fue intensa: Cohen-Cole y Fletcher (*BMJ*, 2008) encontraron efectos "contagiosos" similares en rasgos que no pueden contagiarse, como la altura y el acné, cuando no se controlaban adecuadamente los factores ambientales; Lyons (*Statistics, Politics, and Policy*, 2011) cuestionó los métodos; y Shalizi y Thomas (2011) mostraron la confusión genérica entre homofilia latente y contagio. El caso es hoy el ejemplo estándar de por qué la correlación en redes no identifica influencia.

**Diseños que sí permiten inferencia causal.**

- **Experimentos de campo en redes:** Bond y coautores ("A 61-million-person experiment in social influence and political mobilization", *Nature*, 2012) aleatorizaron mensajes el día de las elecciones de 2010 en Estados Unidos y estimaron efectos directos e indirectos sobre amigos cercanos. (Plantea a su vez preguntas éticas sobre experimentación con poblaciones sin consentimiento explícito.)
- **Asignación aleatoria de vínculos:** compañeros de cuarto en universidades asignados al azar (Sacerdote, *Quarterly Journal of Economics*, 2001).
- **Métodos de emparejamiento dinámico y análisis de sensibilidad:** Aral, Muchnik y Sundararajan (*PNAS*, 2009) estimaron que más de la mitad del aparente contagio en la adopción de una aplicación se explicaba por homofilia.
- **Inferencia causal con interferencia:** cuando el tratamiento de uno afecta el resultado de otro, se viola el supuesto de no interferencia (SUTVA) de la inferencia causal clásica. Hudgens y Halloran (*Journal of the American Statistical Association*, 2008) formalizaron efectos directos e indirectos bajo interferencia parcial; Aronow y Samii (*Annals of Applied Statistics*, 2017) generalizaron a interferencia arbitraria con mapeos de exposición.

**Qué permite afirmar un modelo de difusión.** Que **si** la regla de adopción fuera tal, la estructura produciría tal patrón. Ajustar un modelo a datos observados no identifica la regla: SI, umbral y contagio complejo pueden ajustar una misma curva de adopción agregada.

## IV.5 Cohesión, comunidades y segregación

### Cohesión

"Cohesión" tiene varias definiciones formales que no coinciden:

| Concepto | Definición | Comentario |
| --- | --- | --- |
| Clique | Subgrafo completo maximal | Demasiado estricto: una arista faltante lo rompe |
| n-clique, n-clan | Distancias acotadas por n | Los caminos pueden salir del grupo |
| k-plex | Cada miembro está unido a todos menos k | Relaja la clique de forma controlada |
| k-core | Subgrafo maximal con grado mínimo k | Polinomial (Seidman, 1983); muy usado para "núcleos" |
| Cohesión estructural | El grupo es k-conexo | Moody y White ("Structural Cohesion and Embeddedness", *American Sociological Review*, 2003): se mide por el número de actores que habría que quitar para desconectar el grupo (Menger, II.1) |

La propuesta de Moody y White es la que mejor conecta teoría formal y sociología: un grupo es más cohesivo cuantos más caminos independientes unen a sus miembros, porque su unidad no depende de pocas personas. Es una aplicación directa del teorema de Menger a un concepto durkheimiano.

### Comunidades

Los métodos están en III.14. Desde el punto de vista sociológico, el problema es que "comunidad" en la detección algorítmica significa "región más densa de lo esperado", mientras que en sociología puede significar pertenencia reconocida, identidad compartida, obligaciones mutuas o simplemente co-residencia. Wellman ("The Community Question", *American Journal of Sociology*, 1979) mostró que las comunidades personales de los habitantes de Toronto no eran grupos locales densos sino redes dispersas y especializadas: la comunidad no había "desaparecido" sino cambiado de forma. Un algoritmo de comunidades no habría detectado esas comunidades.

### Segregación

**\[Teo/modelo\] Schelling** ("Dynamic Models of Segregation", *Journal of Mathematical Sociology*, 1971) mostró, con un modelo de agentes en una grilla, que preferencias individuales moderadas (aceptar ser minoría en el vecindario hasta cierto punto) pueden producir segregación casi total. Es un resultado de **posibilidad**, no de explicación: muestra que no hace falta suponer preferencias extremas, no que la segregación real se deba a preferencias. La segregación residencial en Estados Unidos, por ejemplo, tiene causas institucionales documentadas (políticas de crédito hipotecario, *redlining*) que el modelo omite.

**\[Emp\] Moody** ("Race, School Integration, and Friendship Segregation in America", *American Journal of Sociology*, 2001), con datos de Add Health, mostró que escuelas racialmente diversas pueden tener redes de amistad muy segregadas, y que la segregación de amistades depende de la organización escolar (actividades extracurriculares integradas, agrupamiento por niveles). La integración formal no produce integración relacional por sí sola.

**Medidas.** Índice E-I; asortatividad; modularidad respecto de una partición dada por atributos; razón de probabilidades de vínculo intragrupo frente a intergrupo. Todas requieren un **modelo nulo** que fije qué segregación se esperaría por la composición y por las restricciones de oportunidad (los focos de Feld). Sin él, una escuela con 90 % de un grupo parece "segregada" para el grupo minoritario solo por aritmética.

**Advertencia política.** Medir segregación relacional requiere clasificar personas por categorías (raza, etnia, religión) y esas categorías son construidas, disputadas y a veces impuestas. El Volumen V.3 trata cómo las categorías del investigador condicionan el resultado, y el VI, los riesgos de compilar redes con atributos sensibles.

## IV.6 Redes de élites, institucionales e informales

### Élites

C. Wright Mills (*The Power Elite*, 1956) sostuvo que en Estados Unidos las cúpulas militar, empresarial y política formaban una élite unificada por circulación de personas, origen social y sociabilidad compartida. El análisis de redes dio a esa tesis un instrumento: los **directorios entrelazados** (*interlocking directorates*), redes de empresas unidas por consejeros compartidos. Mizruchi ("What Do Interlocks Do?", *Annual Review of Sociology*, 1996) revisó la evidencia: los entrelazamientos se asocian con difusión de prácticas corporativas y con cohesión política empresarial, pero la causalidad es difícil de establecer, porque los consejeros se eligen por razones (prestigio, experiencia, acceso a financiamiento) que también explican las conductas. Domhoff (*Who Rules America?*, con ediciones sucesivas desde 1967) combina redes, membresías en clubes y financiamiento político.

*Un hallazgo que matiza la tesis de la élite cohesiva:* Mizruchi (*The Fracturing of the American Corporate Elite*, Harvard, 2013) y estudios de Chu y Davis (*American Journal of Sociology*, 2016) documentaron que la red de directorios entrelazados de grandes empresas estadounidenses se dispersó desde fines del siglo XX. Las redes de élites cambian, y su estructura no es un rasgo permanente.

**Robust action: los Médici.** Padgett y Ansell ("Robust Action and the Rise of the Medici, 1400–1434", *American Journal of Sociology*, 1993) reconstruyeron redes de matrimonio y de negocios entre familias florentinas. Los Médici ocupaban una posición de intermediación entre familias que no se conectaban entre sí, con vínculos matrimoniales hacia las familias patricias y vínculos económicos hacia familias nuevas, sin superposición. Esa estructura les permitió una **acción robusta**: actuar de manera multívoca, interpretable de distintas formas por cada grupo, sin comprometerse. El trabajo es ejemplar por tres razones: usa redes múltiples (multiplex), combina estructura con interpretación histórica documental, y no reduce el poder a una métrica.

### Redes institucionales

Las redes entre organizaciones (contratos, consorcios, alianzas, transferencias de personal) estudian cómo se difunden formas organizativas y cómo se coordinan campos institucionales. Powell, White, Koput y Owen-Smith ("Network Dynamics and Field Evolution", *American Journal of Sociology*, 2005) estudiaron la biotecnología como un campo organizado por redes de colaboración. Para la investigación sobre Estado y contrataciones públicas, este enfoque es la base del Volumen VI: proveedores, organismos y funcionarios como una red multiplex, donde los vínculos institucionales formales (contratos) y los personales (parentesco, sociedades) se superponen.

### Redes informales

**Larissa Adler de Lomnitz.** En *Cómo sobreviven los marginados* (Siglo XXI, 1975), estudio etnográfico de una barriada de la Ciudad de México, mostró que las redes de intercambio recíproco entre parientes y vecinos eran el mecanismo central de supervivencia económica de los pobladores marginados. Su obra posterior ("Informal Exchange Networks in Formal Systems", *American Anthropologist*, 1988) analizó cómo las redes informales operan **dentro** de las instituciones formales: el intercambio de favores (en Chile, el "compadrazgo"; en el sistema soviético, el *blat*) sostiene el funcionamiento de burocracias que formalmente no los admiten. Es una referencia central en español, y un antídoto contra la idea de que lo formal y lo informal son esferas separadas.

**Ledeneva** (*Russia's Economy of Favours: Blat, Networking and Informal Exchange*, Cambridge, 1998) desarrolló el análisis del *blat* soviético y postsoviético como sistema de favores que hacía funcionar una economía de escasez. La comparación entre Lomnitz y Ledeneva muestra que la informalidad no es un "residuo" premoderno sino una respuesta a configuraciones institucionales específicas.

**Problema de medición.** Las redes informales son, por definición, poco documentadas. Los registros formales (contratos, organigramas, actas) capturan sistemáticamente lo formal, y por eso un grafo construido con fuentes documentales sobrerrepresenta las relaciones que el poder decidió registrar. Esto es central para V.3 y para el Volumen VI.

## IV.7 Formación y disolución de vínculos, multiplexidad y modelos estadísticos

### Mecanismos de formación

| Mecanismo | Formulación | Firma estructural |
| --- | --- | --- |
| Reciprocidad | Si A elige a B, B tiende a elegir a A | Exceso de díadas mutuas |
| Cierre triádico | Amigos de amigos se vuelven amigos (Simmel; Granovetter; Rapoport, 1953) | Agrupamiento alto; tríadas transitivas |
| Focos | Compartir contextos produce vínculos (Feld, 1981) | Homofilia de base; comunidades alineadas con instituciones |
| Homofilia | Similitud aumenta la probabilidad de vínculo | Asortatividad por atributos |
| Apego preferencial | Los populares atraen más vínculos | Colas pesadas en la distribución de grados |
| Balance estructural | "El amigo de mi enemigo es mi enemigo" (Heider, 1946; Cartwright y Harary, *Psychological Review*, 1956) | En grafos con signo, ciclos con número par de aristas negativas |

**\[Teo\] Balance estructural (Cartwright y Harary).** Un grafo completo con signos es balanceado (todo triángulo tiene un número par de aristas negativas) si y solo si sus vértices pueden partirse en dos bandos con aristas positivas dentro de cada bando y negativas entre ellos. Es uno de los raros casos de teorema de grafos formulado para responder una pregunta sociológica. Davis (1967) generalizó a **clusterabilidad** (varios bandos) cuando no hay triángulos con exactamente una arista negativa.

### Disolución

La disolución de vínculos está menos estudiada que la formación, en parte porque los datos transversales no la ven. Burt ("Decay Functions", *Social Networks*, 2000) documentó que los vínculos nuevos y débiles se disuelven muy rápido, y que la integración en la red de terceros protege contra la disolución. La disolución también depende de eventos (mudanzas, cambios de trabajo, conflictos) y de la inversión necesaria para mantener el vínculo. **Consecuencia metodológica:** un grafo de un período es una fotografía que no distingue vínculos estables de vínculos en proceso de disolución (II.13).

### Multiplexidad

Un vínculo multiplex combina varios contenidos (parentesco y negocios, amistad y trabajo). La literatura antropológica (Gluckman, Mitchell) lo asoció con relaciones más densas en obligaciones; la literatura sobre crimen organizado y corrupción encuentra que los vínculos de parentesco superpuestos con vínculos de negocios aumentan la confianza y la resistencia a la delación. Formalmente, la multiplexidad se representa con redes multicapa (II.13) o con grafos de aristas etiquetadas. **Colapsar las capas** produce los errores de la Evaluación, E6.

### Modelos estadísticos de redes

La razón para usar modelos estadísticos específicos es que las observaciones de una red **no son independientes**: la presencia de un vínculo cambia la probabilidad de otros. Una regresión logística ordinaria sobre pares de actores subestima los errores estándar y produce significancia espuria.

- **ERGM (modelos de grafos aleatorios exponenciales).** Especifican la probabilidad de toda la red como función de estadísticos (número de aristas, triángulos, reciprocidad, homofilia). Frank y Strauss (1986) los introdujeron en forma de modelos de Markov; Snijders, Pattison, Robins y Handcock (*Sociological Methodology*, 2006) resolvieron el problema de **degeneración** (los modelos ingenuos concentran la probabilidad en grafos vacíos o completos) con especificaciones curvas. Libro de referencia: Lusher, Koskinen y Robins (eds.), *Exponential Random Graph Models for Social Networks* (Cambridge, 2013). Implementación: paquete `ergm` del proyecto statnet en R.
- **SAOM (modelos orientados al actor).** Snijders ("Stochastic Actor-Oriented Models for Network Change", *Journal of Mathematical Sociology*, 1996; desarrollos posteriores con van de Bunt y Steglich, *Social Networks*, 2010) modela la evolución de una red observada en varios momentos como resultado de decisiones de actores, y permite separar **selección** (homofilia) de **influencia** si se observan red y comportamiento en varias olas. Implementación: RSiena.
- **Modelos de bloques estocásticos (SBM).** Holland, Laskey y Leinhardt (1983) los formularon; la variante con corrección por grado (Karrer y Newman, 2011) es la base de la detección de comunidades por inferencia (III.14). Peixoto desarrolló inferencia bayesiana no paramétrica con selección de modelo (`graph-tool`).
- **Modelos de espacio latente.** Hoff, Raftery y Handcock (*Journal of the American Statistical Association*, 2002): cada actor tiene una posición latente, y la probabilidad de vínculo decrece con la distancia. Capturan homofilia no observada.
- **Modelos relacionales de eventos (REM).** Butts (*Sociological Methodology*, 2008) modela secuencias fechadas de interacciones, en lugar de vínculos agregados. Es el modelo natural para datos de comunicaciones o transacciones, y conecta con II.13.

**Qué ganan y qué cuestan.** Estos modelos permiten afirmaciones inferenciales ("hay más reciprocidad de la esperada dado lo demás"), con incertidumbre. A cambio, exigen especificar el modelo, verificar el ajuste (bondad de ajuste por simulación) y aceptar que sus resultados son condicionales a la red observada y a su frontera. No resuelven la falta de datos: si la red está incompleta, el modelo modela la red incompleta.

## IV.8 Dependencia, asimetría y poder relacional

**\[Def\] Teoría de poder-dependencia (Emerson, "Power-Dependence Relations", *American Sociological Review*, 1962).** El poder de A sobre B es igual a la dependencia de B respecto de A, y esa dependencia crece con el valor que B asigna a lo que A controla y decrece con las alternativas que B tiene fuera de la relación. El poder es una **propiedad de la relación**, no del actor, y depende de las **alternativas**, es decir, de la estructura de la red alrededor de la díada.

**\[Emp\] Experimentos de intercambio en redes.** Cook, Emerson, Gillmore y Yamagishi ("The Distribution of Power in Exchange Networks: Theory and Experimental Results", *American Journal of Sociology*, 1983) hicieron negociar a sujetos en redes de estructura controlada. El resultado contradijo la intuición de la centralidad: en ciertas redes, el actor más central **no** obtenía la mayor ventaja. La ventaja la obtenían quienes negociaban con actores que a su vez tenían pocas alternativas. Ejemplo canónico: en una cadena A–B–C–D–E de intercambio excluyente (cada actor puede cerrar un solo trato por ronda), C es el más central por intermediación, pero B y D tienen más poder, porque cada uno negocia con un extremo (A o E) que no tiene alternativas, mientras C negocia con quienes sí las tienen.

**\[Teo/Int\] Bonacich** ("Power and Centrality: A Family of Measures", *American Journal of Sociology*, 1987) formalizó esto con una centralidad paramétrica:

```latex
c(\alpha, \beta) = \alpha \sum_{k=0}^{\infty} \beta^{k} A^{k+1} \mathbf{1}
```

Con β > 0, estar conectado a actores bien conectados suma (como Katz). Con β **negativo**, estar conectado a actores bien conectados **resta**: es ventajoso estar ligado a quienes dependen de uno, porque tienen menos alternativas. Bonacich mostró que la misma red produce ordenamientos opuestos según el signo de β, y que el signo correcto depende del tipo de relación: positivo para comunicación e influencia, negativo para negociación e intercambio excluyente. **Es la demostración formal más clara de que no hay una centralidad que mida "el poder".**

**Teorías de intercambio en redes.** Willer y Markovsky desarrollaron la teoría de elementos (*Network Exchange Theory*), con predicciones exactas sobre qué posiciones son fuertes y débiles en redes de intercambio excluyente. Easley y Kleinberg (cap. 12) presentan una versión accesible con soluciones de negociación equilibradas, conectadas con emparejamientos estables (II.3).

**Asimetría y dirección.** Muchas relaciones de poder son asimétricas por definición (subordinación, deuda, dependencia de un recurso). Representarlas como aristas no dirigidas destruye exactamente la información relevante. Incluso las relaciones dirigidas pueden ser engañosas: "A llama a B" no dice quién manda; en algunas organizaciones el subordinado reporta (llama más) y en otras el superior da órdenes (llama más). La dirección del flujo de comunicación no es la dirección de la autoridad.

**Poder como capacidad, no como ejercicio.** Siguiendo a Lukes (*Power: A Radical View*, 1974; 2.ª ed. 2005), el poder tiene una dimensión visible (ganar decisiones), una oculta (controlar la agenda: qué se decide) y una tercera (moldear las preferencias, de modo que el conflicto no aparezca). Un grafo de interacciones observables captura, en el mejor caso, parte de la primera dimensión. La segunda y la tercera dejan rastros indirectos o ninguno. Esta es la base de la crítica de V.2.

## IV.9 Por qué centralidad no es poder, influencia, autoridad ni culpa

Esta sección reúne en un solo lugar los argumentos dispersos en los Volúmenes III y IV. Cada distinción tiene un fundamento formal o empírico, no solo una advertencia de prudencia.

| Confusión | Por qué es inválida | Fundamento |
| --- | --- | --- |
| Centralidad = poder | El poder depende de las alternativas de los demás y del tipo de relación; una misma red ordena a los actores de forma opuesta según el signo de β | Emerson (1962); Cook et al. (1983); Bonacich (1987) |
| Centralidad = influencia | La influencia es causal y debe identificarse; la posición describe exposición potencial | Shalizi y Thomas (2011); IV.4 |
| Centralidad = autoridad | La autoridad es legitimidad reconocida (Weber); se ejerce a menudo con poca comunicación y a través de intermediarios | V.2; literatura sobre redes encubiertas |
| Centralidad = culpabilidad | La culpa es individual, requiere conducta y dolo, y se prueba con evidencia de actos; la posición en un grafo resulta en parte de cómo se recolectaron los datos | Volumen VI; garantías procesales |
| Centralidad = importancia general | Cada medida presupone un tipo de flujo; aplicada a otro flujo, describe una circulación inexistente | Borgatti (2005); III.13 |

**Cinco mecanismos que separan posición y poder.**

1. **Protección por periferia.** En organizaciones clandestinas hay un dilema entre eficiencia y seguridad: más comunicación coordina mejor pero expone más. Morselli, Giguère y Petit ("The Efficiency/Security Trade-off in Criminal Networks", *Social Networks*, 2007) mostraron que las posiciones más expuestas tienden a ocuparlas actores de nivel operativo, mientras quienes dirigen se mantienen a distancia y operan a través de intermediarios. Un análisis de centralidad sobre escuchas los ubica en la periferia.
2. **Delegación.** El poder se ejerce a través de otros: quien da una orden una vez a una persona de confianza puede aparecer con un solo vínculo.
3. **Sesgo de observación.** La centralidad en datos de vigilancia depende de a quién se vigiló. El investigado inicial casi siempre resulta central porque la red se construyó a partir de él (A4 de la Evaluación; Volumen VI).
4. **Funciones de servicio.** Contadores, abogados, choferes, secretarias, operadores logísticos, parientes: personas en contacto con muchos por la naturaleza de su tarea, sin poder de decisión. En los análisis de redes delictivas aparecen sistemáticamente como hubs.
5. **Poder sin interacción.** La tercera dimensión de Lukes y el poder disciplinario de Foucault (V.2) operan sin contacto directo observable.

**Lo que sí puede afirmarse con una centralidad.** Que, en el grafo construido con tales datos y tal frontera, bajo el supuesto de flujo de la medida, el actor ocupa una posición con tal propiedad. Es una descripción condicional. Puede orientar hipótesis ("conviene examinar el rol de esta persona") y es incompatible con conclusiones ("esta persona dirige").

## V.1 Sociología relacional y sus tensiones

**El manifiesto.** Emirbayer ("Manifesto for a Relational Sociology", *American Journal of Sociology*, 1997) contrapuso dos ontologías. La **sustancialista** parte de entidades (individuos, sociedades) con atributos propios que luego entran en relación. La **relacional** sostiene que las entidades se constituyen en sus relaciones: los términos derivan su identidad de los vínculos que los unen. El análisis de redes parecía la metodología natural de la segunda, pero Emirbayer y Goodwin ("Network Analysis, Culture, and the Problem of Agency", *American Journal of Sociology*, 1994) ya habían criticado que buena parte del análisis de redes era **estructuralismo determinista**: trataba la posición como causa de la conducta e ignoraba la cultura y la agencia.

**Formalismo frente a relacionalismo.** Erikson ("Formalist and Relationalist Theory in Social Network Analysis", *Sociological Theory*, 2013) distinguió dos tradiciones dentro del análisis de redes:

- **Formalista** (de raíz simmeliana): las formas de relación tienen efectos independientes de su contenido; una tríada abierta produce intermediación sea cual sea el vínculo. Permite generalizar entre contextos.
- **Relacionalista** (de raíz pragmatista y en parte de White tardío): el significado de un vínculo es constitutivo; dos vínculos con la misma forma pero distinto significado no son equivalentes. Exige interpretación y métodos cualitativos.

La tensión no se resuelve eligiendo uno: el formalismo da comparabilidad al costo de descontextualizar; el relacionalismo da validez situada al costo de generalizar. Para investigar fenómenos sociales con grafos, la posición sensata es formalista en el cálculo y relacionalista en la interpretación, y explícita sobre el paso de uno a otro.

**Problemas abiertos de la sociología relacional.**

- **Agencia.** Si la posición determina, no hay actores; si los actores eligen sus vínculos, la posición es resultado y no causa. Los modelos orientados al actor (IV.7) son un intento técnico de articular ambos, al costo de suponer actores que optimizan una función de utilidad.
- **Cultura.** Mische (*Partisan Publics*, Princeton, 2008) estudió redes de militancia juvenil en Brasil mostrando que los vínculos se construyen en conversaciones donde se negocian identidades; la red y el discurso se coproducen.
- **Historia.** Las redes tienen trayectorias, y una misma estructura puede tener significados opuestos según el proceso que la produjo (Padgett y Powell, *The Emergence of Organizations and Markets*, Princeton, 2012).
- **Escala.** Las relaciones entre individuos y las relaciones entre instituciones no son el mismo tipo de objeto, aunque ambas se dibujen como grafos.

## V.2 Weber, Foucault, Bourdieu y Latour frente a los grafos

Ninguno de estos autores fue analista de redes, y la relación de sus teorías con los grafos es de tensión productiva, no de aplicación. Para cada uno: qué ilumina y qué el grafo no puede capturar.

### Max Weber: dominación y legitimidad

En *Economía y sociedad* (póstumo, 1922), Weber distingue **poder** (*Macht*: la probabilidad de imponer la propia voluntad aun contra resistencia) de **dominación** (*Herrschaft*: la probabilidad de encontrar obediencia a un mandato), y clasifica la dominación por su fundamento de legitimidad: racional-legal, tradicional y carismática.

- *Qué ilumina en clave de grafos.* La burocracia racional-legal es una estructura formal (jerarquía, competencias) que se puede representar como árbol o como digrafo de subordinación. El patrimonialismo, en cambio, es una red de lealtades personales que atraviesa y vacía la estructura formal: es exactamente la distancia entre el organigrama y la red informal (IV.6). La comparación entre ambos grafos sobre una misma institución es una operacionalización weberiana fértil.
- *Qué no puede capturar.* La **legitimidad**: la creencia en la validez del orden. Dos estructuras de comunicación idénticas pueden corresponder a una autoridad aceptada o a una imposición por coerción. La obediencia observada no revela su fundamento.

### Michel Foucault: poder disciplinario, saber y visibilidad

En *Vigilar y castigar* (1975) y en "El sujeto y el poder" (1982), Foucault describe el poder no como una sustancia que alguien posee sino como una relación que se ejerce, distribuido en dispositivos, prácticas y saberes; y vincula estrechamente poder y producción de conocimiento: clasificar, registrar, examinar y hacer visible son operaciones de poder.

- *Qué ilumina.* La afinidad con una concepción relacional es evidente: el poder circula en redes. Pero la lección más importante para quien investiga con grafos es reflexiva: **el propio grafo es un dispositivo de visibilidad**. Construir el grafo de una población (sus comunicaciones, sus vínculos) es una operación de saber-poder; la sociometría de Moreno nació para reorganizar internas (IV.1), y los análisis de redes contemporáneos alimentan sistemas policiales de "puntuación de riesgo" que convierten la proximidad en sospecha.
- *Qué no puede capturar.* El poder productivo (que forma subjetividades) y el poder normalizador, que operan a través de normas internalizadas, sin contacto directo entre quien ejerce y quien es sujeto. No dejan aristas.

### Pierre Bourdieu: campos, capitales y la crítica del interaccionismo

Para Bourdieu (con Wacquant, *Réponses*, 1992), un **campo** es un espacio de **posiciones objetivas** definidas por la distribución de capitales (económico, cultural, social, simbólico), y las relaciones que importan son relaciones objetivas entre posiciones, no interacciones efectivas.

- *La crítica explícita.* Bourdieu sostuvo que el análisis de redes confunde la estructura con las interacciones visibles: dos agentes ocupan posiciones relacionadas en un campo aunque nunca se hayan cruzado. Su instrumento preferido fue el **análisis de correspondencias múltiples**, no el grafo.
- *El diálogo posterior.* De Nooy ("Fields and Networks: Correspondence Analysis and Social Network Analysis in the Framework of Field Theory", *Poetics*, 2003) mostró que ambas técnicas pueden articularse: el campo da el espacio de posiciones; la red, las interacciones efectivas que reproducen o desafían esas posiciones. Bourdieu también aporta al análisis de redes el concepto de capital social como mecanismo de reproducción de la desigualdad (IV.3).
- *Qué no puede capturar el grafo.* Las relaciones de homología estructural sin interacción, y el *habitus*: las disposiciones incorporadas que hacen que ciertos vínculos parezcan naturales y otros impensables.

### Bruno Latour: actor-red

La teoría del actor-red (Latour, *Reassembling the Social*, Oxford, 2005; en español, *Reensamblar lo social*, Manantial, 2008) sostiene que lo social no es un dominio previo sino el resultado de asociaciones entre actantes humanos y no humanos (documentos, instrumentos, bases de datos, leyes), y que la tarea es rastrear esas asociaciones sin presuponer escalas ni categorías.

- *Qué ilumina.* Los **no humanos** como nodos: un formulario, un software de registro, una base de datos o un algoritmo median relaciones y tienen efectos. En investigación sobre vigilancia o procedencia (Volumen VII), esto es directamente útil: el grafo debe incluir los dispositivos de registro, porque son parte de lo que produce la evidencia.
- *La tensión.* Latour advirtió que el actor-red no es una red en el sentido técnico: "red" designa un trabajo de traducción y asociación, no un conjunto de nodos y aristas estables. Venturini, Munk y Jacomy ("Actor-Network versus Network Analysis versus Digital Networks: Are We Talking about the Same Networks?", en *DigitalSTS*, Princeton, 2019) analizan las diferencias y los usos posibles. El grafo estabiliza lo que la teoría quiere mostrar como un proceso.

### Otras perspectivas pertinentes

- **Estudios de clasificación:** Bowker y Star, *Sorting Things Out: Classification and Its Consequences* (MIT, 1999): las categorías de una infraestructura de información son decisiones políticas que se vuelven invisibles al estandarizarse. Las categorías de nodo y arista de un grafo son exactamente eso.
- **Datos como construcción:** Gitelman (ed.), *"Raw Data" Is an Oxymoron* (MIT, 2013); Drucker ("Humanities Approaches to Graphical Display", *Digital Humanities Quarterly*, 2011) propone hablar de *capta* (lo tomado) en lugar de *data* (lo dado).
- **Feminismo de datos:** D'Ignazio y Klein, *Data Feminism* (MIT, 2020, con acceso abierto): quién recolecta, para quién y qué cuerpos y relaciones quedan fuera de los conjuntos de datos.
- **Performatividad:** Healy ("The Performativity of Networks", *European Journal of Sociology*, 2015) muestra que las teorías de redes, al ser adoptadas por empresas y gobiernos, transforman las redes que describen. Las métricas de red se vuelven objetivos, y entonces dejan de medir lo que medían.

## V.3 La producción del grafo: categorías, fronteras y datos

Entre el fenómeno y el grafo hay una cadena de decisiones. Cada eslabón puede introducir sesgos que el análisis posterior hereda sin poder detectarlos. Marsden ("Network Data and Measurement", *Annual Review of Sociology*, 1990) es la revisión clásica de estos problemas de medición.

| Eslabón | Decisión | Sesgo típico |
| --- | --- | --- |
| 1. Pregunta | Qué se quiere saber, y para quién | Una pregunta policial produce un grafo de sospecha; una pregunta de derechos humanos, uno de responsabilidad institucional |
| 2. Frontera | Quién entra en la red (posicional, reputacional, relacional; Laumann, Marsden y Prensky, 1983) | Excluir a intermediarios externos; incluir solo a los ya investigados |
| 3. Unidad de nodo | Persona, rol, cuenta, teléfono, organización | Un teléfono compartido o una persona con varias cuentas distorsionan todo (II.15) |
| 4. Tipo de vínculo | Qué relación se registra, con qué umbral y en qué ventana | Elegir la relación disponible en vez de la pertinente |
| 5. Fuente | Encuesta, registro administrativo, expediente, escucha, scraping | Cada fuente registra lo que su productor necesitó registrar |
| 6. Instrumento | Formato de la pregunta (lista libre o fija, límite de nominaciones) | Un límite de 5 nominaciones trunca los grados (Holland y Leinhardt, 1973) |
| 7. Resolución de entidades | Qué registros son la misma entidad | Fusiones y separaciones erróneas (II.15; III.3) |
| 8. Agregación | Temporal, por tipo, por peso | Caminos imposibles; multiplexidad destruida (II.13) |
| 9. Análisis | Métrica y algoritmo | Supuestos de flujo; heurísticas presentadas como hallazgos (III) |
| 10. Representación | Visualización y narrativa | Disposición visual leída como estructura |

**Las categorías del investigador.** Clasificar a los nodos (por etnia, por organización, por "rol") requiere categorías previas, y esas categorías organizan el resultado. Si se clasifica a las personas como "integrantes" o "no integrantes" de una organización antes de analizar la red, la red confirmará la clasificación porque los vínculos se interpretarán a la luz de ella. Hacking llamó **efecto bucle** (*looping effect*) a cómo las clasificaciones de personas cambian a las personas clasificadas (*The Social Construction of What?*, Harvard, 1999); en el caso de listas de sospechosos, la clasificación produce vigilancia, que produce más datos, que confirman la clasificación.

**Fuentes producidas por el poder.** Los archivos institucionales (policiales, militares, judiciales) son producidos por instituciones con objetivos propios. En investigación de derechos humanos, los archivos de los perpetradores son a la vez la mejor fuente y la más sesgada: registran a las víctimas desde la mirada de quien las perseguía, con las categorías de quien las perseguía ("subversivo", "enlace", "contacto"). Reconstruir una red a partir de ellos sin crítica de fuentes reproduce esas categorías. El Volumen VI desarrolla este punto con casos.

**Ausencia de vínculo y ausencia de evidencia.** Ya está formalizado en I.9 y II.15: la ausencia de una arista puede significar no relación, no observación, no registro o error de resolución. Una práctica concreta: representar explícitamente tres estados por par (presente observado, ausente observado, no observado) y reportar qué fracción de los pares está en cada uno. En la mayoría de los grafos construidos con fuentes documentales, la enorme mayoría de los pares está "no observado", aunque la herramienta los trate como ausentes.

## V.4 Las ocho preguntas centrales

Respuestas sintéticas a las preguntas de la Parte V del pedido, con remisión a donde se desarrollan.

**1. ¿Qué relaciones se vuelven visibles al modelarlas como grafos?** Las relaciones diádicas, discretas y registrables: quién se comunica, transfiere, contrata o co-participa con quién. Se vuelven visibles también propiedades que ninguna relación individual muestra: caminos indirectos, intermediaciones, cuellos de botella, regiones densas, posiciones equivalentes. Esa es la contribución genuina: la estructura como objeto (IV.1, White).

**2. ¿Qué relaciones quedan fuera?** Las no registradas (informales, clandestinas, verbales), las de orden superior proyectadas sobre pares (II.14), las relaciones objetivas sin interacción (Bourdieu), las de legitimidad (Weber), el poder sin contacto (Lukes, Foucault), las relaciones con no humanos si no se las incluye deliberadamente (Latour), y el significado y la intensidad de cada vínculo, salvo que se los codifique.

**3. ¿Quién decide qué cuenta como nodo o vínculo?** Quien investiga, quien produjo la fuente y quien diseñó el instrumento. La decisión debe ser explícita, justificada por la pregunta y documentada como parte de la evidencia (V.3, tabla de eslabones).

**4. ¿Cómo influyen las categorías del investigador?** Organizan los nodos, definen qué vínculo es pertinente y orientan la interpretación. Pueden autoconfirmarse (efecto bucle de Hacking). Remedio parcial: definir las categorías antes de ver los resultados, probar análisis con categorías alternativas y reportar cuánto cambian las conclusiones.

**5. ¿Cómo representar relaciones de poder sin reducirlas a una sola métrica?** Con varias medidas que presuponen flujos distintos y se reportan juntas; con redes multicapa que separen tipos de relación; con dirección y signo; con modelos de intercambio que incorporen alternativas (IV.8); con la tipología de intermediación de Gould y Fernandez (IV.3); y, sobre todo, combinando la estructura con evidencia documental o etnográfica del ejercicio efectivo del poder, como hicieron Padgett y Ansell (IV.6).

**6. ¿Qué ocurre cuando un vínculo observado se interpreta como causal?** Se comete el error de suponer que la co-ocurrencia o el contacto explican el resultado. El vínculo puede ser efecto (causalidad inversa), puede compartir causa con el resultado (homofilia latente, exposición común) o puede no tener relación con él. La identificación causal requiere diseño: aleatorización, variación exógena, modelos longitudinales con supuestos explícitos o análisis de sensibilidad (IV.4).

**7. ¿Cómo se introducen sesgos mediante la recolección de datos?** Por la frontera, el instrumento, la fuente, la resolución de entidades y la agregación (V.3). El más importante en contextos de seguridad e investigación penal: **el muestreo a partir del investigado**, que vuelve central a quien ya era sospechoso.

**8. ¿Qué diferencias existen entre ausencia de vínculo y ausencia de evidencia?** La primera es un hecho sobre el mundo; la segunda, un hecho sobre el registro. Solo la primera autoriza las inferencias que hacen los algoritmos. Formalmente: semántica de mundo cerrado frente a mundo abierto (I.9; Volumen VII), y tres estados por par en lugar de dos (V.3).

## V.5 Crítica epistemológica: ocho errores frecuentes

Esta sección corresponde a la Parte XIV del pedido. Para cada error: en qué consiste, por qué ocurre, un ejemplo y una prueba concreta para detectarlo en el propio trabajo.

### 1. Confundir correlación con causalidad

*En qué consiste.* Leer como efecto de los vínculos lo que solo co-ocurre con ellos. *Por qué ocurre.* La estructura de red produce correlaciones por homofilia, focos compartidos y exposición común, sin causalidad (IV.2, IV.4). *Ejemplo.* El caso Christakis y Fowler sobre obesidad y sus críticas. *Prueba.* Preguntarse qué patrón observaría si **no** hubiera influencia: si la homofilia sola lo produce, el dato no discrimina. Aplicar un test placebo con un rasgo que no puede contagiarse (como hicieron Cohen-Cole y Fletcher).

### 2. Confundir cercanía con pertenencia

*En qué consiste.* Inferir que alguien es parte de un grupo porque está cerca de sus miembros. *Por qué ocurre.* La distancia en el grafo es fácil de calcular, y el pensamiento asociativo convierte proximidad en afinidad. *Ejemplo.* En redes de diámetro chico (casi todas las redes sociales grandes), casi cualquier persona está a dos o tres pasos de cualquier grupo. La práctica de vigilancia de "saltos" (analizar contactos de contactos de un sospechoso) incorpora a miles de personas sin relación con el hecho: con un grado medio de 100, tres saltos alcanzan del orden de un millón de personas. *Prueba.* Calcular cuántas personas quedan a la misma distancia del grupo; si son muchas, la cercanía no discrimina.

### 3. Interpretar centralidad como poder

Desarrollado en IV.9. *Prueba.* Explicitar el supuesto de flujo de la medida (Borgatti) y preguntarse si el fenómeno lo cumple; calcular la centralidad de Bonacich con β positivo y negativo y ver si el ordenamiento se invierte.

### 4. Tratar ausencia de datos como ausencia de relaciones

*Por qué ocurre.* Las estructuras de datos y los algoritmos representan solo dos estados por par. *Ejemplo.* En una red construida con expedientes, la falta de vínculo entre dos funcionarios se lee como independencia, cuando nadie investigó su relación. *Prueba.* Estimar la fracción de pares observados; correr el análisis con aristas faltantes imputadas bajo distintos supuestos y ver qué conclusiones sobreviven (Borgatti, Carley y Krackhardt, 2006; II.15).

### 5. Ignorar cambios temporales

*Por qué ocurre.* Agregar es más simple que modelar el tiempo, y las fuentes llegan como listas de vínculos sin fecha. *Ejemplo.* Concluir que A transmitió algo a C a través de B cuando el contacto B–C ocurrió antes que el A–B (II.13). *Prueba.* Calcular caminos que respetan el tiempo y comparar la alcanzabilidad con la del grafo agregado; correr el análisis en ventanas distintas y verificar la estabilidad.

### 6. Convertir inferencias probabilísticas en afirmaciones categóricas

*En qué consiste.* Presentar la salida de un modelo (una probabilidad de vínculo, una asignación a una comunidad, una coincidencia de identidades) como un hecho. *Por qué ocurre.* La narrativa y los informes favorecen afirmaciones simples; la incertidumbre se pierde al copiar un resultado de un documento a otro. *Ejemplo.* Un sistema de resolución de entidades con 95 % de precisión aplicado a 100.000 pares produce 5.000 fusiones erróneas; reportar los vínculos resultantes sin marca de incertidumbre los convierte en hechos. *Prueba.* Para cada afirmación, poder señalar si es dato registrado, inferencia (con su incertidumbre) o reconstrucción hipotética, y conservar esa marca en todas las versiones del documento.

### 7. Presentar visualizaciones llamativas como evidencia

*Por qué ocurre.* Los grafos dibujados tienen gran poder retórico: parecen mostrar la estructura "directamente". *Qué ocurre en realidad.* Los algoritmos de disposición por fuerzas (Fruchterman-Reingold, ForceAtlas2) son optimizaciones heurísticas con componentes aleatorias, y la cercanía en el dibujo no equivale a distancia en el grafo. Venturini, Jacomy y Jensen ("What Do We See When We Look at Networks: Visual Network Analysis, Relational Ambiguity, and Force-Directed Layouts", *Big Data & Society*, 2021) analizan qué puede y qué no puede leerse en estos dibujos. Además, en redes de miles de nodos, todo parece una "bola de pelos" (*hairball*) cuyo aspecto depende de los parámetros. *Prueba.* Dibujar el mismo grafo con dos disposiciones y dos semillas; si la conclusión cambia, no venía del grafo. Toda afirmación debe poder sostenerse con una métrica y su incertidumbre, sin la imagen.

### 8. Asumir que el grafo es una representación neutral de la realidad

*En qué consiste.* Olvidar la cadena de decisiones de V.3 y tratar el grafo como el fenómeno. *Por qué ocurre.* La formalización matemática transmite objetividad, y la estructura de datos oculta las decisiones que la produjeron. *Consecuencia.* Los resultados heredan sin advertencia las categorías, las fronteras y los sesgos de las fuentes; y, por performatividad (Healy, 2015), el grafo puede transformar lo que describe. *Prueba.* Documentar, junto con cada grafo, la pregunta, la frontera, las fuentes, las reglas de resolución de entidades, la ventana temporal y las decisiones de agregación, como parte inseparable del resultado: un **registro de procedencia del grafo** (Volumen VII).

## V.6 Alternativas metodológicas

La crítica no conduce a abandonar los grafos sino a usarlos dentro de diseños que compensen sus límites.

**Métodos mixtos y análisis cualitativo de redes.** Crossley, Bellotti, Edwards, Everett, Koskinen y Tranmer (*Social Network Analysis for Ego-Nets*, Sage, 2015) y Bellotti (*Qualitative Networks: Mixed Methods in Sociological Research*, Routledge, 2015) proponen combinar la medición formal con entrevistas sobre el significado de cada vínculo, historias de los vínculos y mapas de red dibujados con los propios entrevistados. Domínguez y Hollstein (eds.), *Mixed Methods Social Networks Research* (Cambridge, 2014), reúne diseños concretos.

**Etnografía de redes.** La tradición de Manchester (IV.1) y la obra de Lomnitz (IV.6) muestran que la observación prolongada permite saber qué circula por cada vínculo, algo que ningún registro documental da.

**Análisis de redes históricas con crítica de fuentes.** Padgett y Ansell (IV.6) y la red de investigadores en análisis histórico de redes (*Historical Network Research*) trabajan con archivos y combinan la reconstrucción estructural con la crítica documental propia de la historia. Para investigación sobre archivos represivos, es el modelo a seguir.

**Redes cognitivas.** Krackhardt ("Cognitive Social Structures", *Social Networks*, 1987) preguntó a cada miembro de una organización cómo percibía **toda** la red. Las percepciones difieren entre sí y de los reportes de los involucrados, y la exactitud de la percepción se asocia con la posición y el poder. La red no es solo un hecho observable sino también una representación que los actores usan para actuar.

**Análisis de sensibilidad como norma.** Cualquier resultado estructural debería reportarse junto con su robustez frente a: aristas faltantes, umbrales alternativos, ventanas temporales distintas, reglas alternativas de resolución de entidades y fronteras ampliadas. Si la conclusión cambia, el hallazgo es la sensibilidad, no la conclusión.

**Participación y devolución.** En investigación con comunidades afectadas (derechos humanos, organizaciones sociales), construir y validar el grafo con las personas representadas corrige errores y redistribuye el control sobre el conocimiento producido. Plantea a su vez problemas de seguridad, que el Volumen VI trata con detalle.

## Matriz de técnicas (partes IV y V)

Continúa la matriz de los Volúmenes II y III. Aquí cada fila separa la **métrica** de su **interpretación**.

| Concepto | Métrica u operacionalización | Interpretación habitual | Lo que la métrica no sostiene sola | Sección |
| --- | --- | --- | --- | --- |
| Vínculo débil | Puente local con baja frecuencia o cercanía | Canal de información nueva | Que la información circule; el efecto sobre resultados | IV.2 |
| Homofilia | Asortatividad, índice E-I | Preferencia por similares | Distinguir preferencia, focos e influencia | IV.2 |
| Agujero estructural | Restricción, tamaño efectivo | Ventaja por intermediación | Que la persona intermedie o se beneficie | IV.3 |
| Intermediario | Tipología de Gould y Fernandez | Rol de control o enlace | Intención, legitimidad, beneficio | IV.3 |
| Difusión | Curva de adopción, modelos SI, umbral, complejo | Contagio | Identificar la regla de adopción o la influencia | IV.4 |
| Cohesión | k-core, k-conectividad (Moody y White) | Grupo unido | Identidad, obligaciones, pertenencia | IV.5 |
| Segregación | Índices de segregación relacional con modelo nulo | Exclusión | Mecanismos (preferencia, institución, coerción) | IV.5 |
| Directorios entrelazados | Proyección de afiliación empresa–consejero | Cohesión de élite | Coordinación efectiva | IV.6 |
| Equivalencia estructural | Modelos de bloques | Rol social | Significado del rol para los actores | IV.1 |
| ERGM, SAOM | Parámetros con incertidumbre | Mecanismos de formación | Validez fuera de la frontera; datos faltantes | IV.7 |
| Poder relacional | Bonacich con β negativo; modelos de intercambio | Ventaja de negociación | Legitimidad, poder sin interacción | IV.8 |
| Visualización | Disposición por fuerzas | Estructura visible | Cualquier conclusión sin métrica | V.5 |

## Ejercicios de los Volúmenes IV y V

Dificultad: (★) directo, (★★) requiere una idea, (★★★) desafiante. Los ejercicios prácticos usan datos públicos incluidos en NetworkX o en el paquete `networkdata`/statnet de R; el laboratorio completo con criterios de falsación está en el Volumen X.

1. (★) Con la red de familias florentinas de Padgett (`networkx.florentine_families_graph()`, que corresponde a la red matrimonial), calculá grado, intermediación y autovector. ¿Qué familia queda primera en cada una? ¿Qué agregaría la red de negocios, que no está en esa función?
2. (★★) En la cadena de intercambio A–B–C–D–E, calculá la centralidad de Bonacich con β = 0,5 y con β = −0,5 (normalizá). Verificá que el ordenamiento cambia y relacionalo con los experimentos de Cook y colegas.
3. (★★) Construí un grafo con signos de seis personas que no sea balanceado y encontrá el mínimo de aristas cuyo signo habría que cambiar para balancearlo.
4. (★★) Con el modelo de configuración (`networkx.configuration_model`), generá 1.000 grafos con la misma secuencia de grados que una red real y compará su agrupamiento con el observado. ¿Cuánto del agrupamiento se explica solo por los grados?
5. (★★) Simulá contagio simple y contagio complejo (umbral de dos vecinos) sobre un grafo de Watts-Strogatz con distintas probabilidades de reconexión. Reproducí cualitativamente el resultado de Centola y Macy.
6. (★★) Implementá el modelo de Schelling en una grilla y encontrá la tolerancia mínima que produce más de 80 % de vecinos iguales en promedio. Escribí qué conclusión permite y cuál no.
7. (★★★) Generá una red sintética con homofilia por un atributo latente y sin ninguna influencia. Mostrá que una regresión ingenua de la conducta de un actor sobre la de sus vecinos encuentra un "efecto de contagio" significativo.
8. (★★) Tomá una red, quitá al azar el 10 %, el 20 % y el 30 % de las aristas cien veces cada vez, y medí la correlación de rangos entre la intermediación original y la degradada. ¿A partir de qué nivel de faltantes el ranking de los cinco primeros deja de ser estable?
9. (★★) Dibujá una misma red con ForceAtlas2 (Gephi) y con Fruchterman-Reingold con tres semillas cada una. Anotá qué "grupos" parecen aparecer en cada dibujo y contrastalos con una partición por modularidad.
10. (★★★) Conceptual: elegí una investigación periodística pública que use un grafo de vínculos (por ejemplo, sobre sociedades offshore o contrataciones). Reconstruí la cadena de decisiones de V.3 a partir de lo que el trabajo publica, e identificá qué eslabones no están documentados.
11. (★★★) Conceptual: escribí un párrafo que describa la posición de un actor en una red en lenguaje estrictamente formal y otro que la interprete sociológicamente. Marcá con las etiquetas \[Def\], \[Emp\], \[Int\] e \[Hip\] cada afirmación del segundo párrafo.
12. (★★★) Conceptual: elegí uno de los cuatro autores de V.2 y escribí qué cambiaría en el diseño de un estudio de redes sobre una institución que conozcas si se tomara en serio su crítica.
