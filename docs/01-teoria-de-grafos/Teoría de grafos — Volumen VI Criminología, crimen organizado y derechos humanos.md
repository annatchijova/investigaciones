# Teoría de grafos — Volumen VI: Criminología, crimen organizado y derechos humanos

Nov 5, 2026 · @Anna Tchijova

## Alcance, principios y cómo leer los casos

Este volumen examina usos documentados del análisis de redes en criminología, investigación de corrupción, periodismo de investigación y documentación de violaciones de derechos humanos. Los casos se eligieron porque son **públicos y verificables**, y porque cada uno enseña algo sobre lo que el método permite y lo que no. Los hechos de cada caso se verificaron el 5 de noviembre de 2026 contra las fuentes que se citan al final de cada sección.

**Cuatro principios que ordenan el volumen.**

1. **Ninguna posición en un grafo establece culpabilidad.** La responsabilidad penal es individual y exige prueba de conducta y de intención. La proximidad, la centralidad y la pertenencia a una comunidad detectada son, en el mejor caso, motivos para investigar; nunca conclusiones (IV.9).
2. **Las comunidades detectadas no son organizaciones.** Una partición que optimiza una función es una hipótesis estadística sobre densidad; una organización es un hecho social con fines, roles y reglas (III.14).
3. **El grafo hereda la mirada de quien produjo los datos.** Expedientes, escuchas y archivos represivos registran lo que sus productores necesitaron registrar, con sus categorías (V.3).
4. **El costo de los errores es asimétrico.** Un falso negativo en una investigación académica es una oportunidad perdida; un falso positivo en una base de datos policial puede significar detención, desalojo, pérdida de empleo o riesgo para la vida. Los métodos deben evaluarse según el daño de su peor error, no según su precisión media.

**Cómo leer cada caso.** Para cada uno: qué datos se usaron, qué técnica, qué se concluyó, y una lectura crítica que distingue \[Emp\] (lo que los datos mostraron) de \[Int\] (lo que se interpretó) y señala qué condiciones de los Volúmenes II a V se cumplían o no.

**Sobre la doble faz de estos métodos.** Las mismas técnicas sirven para reconstruir la cadena de mando de una desaparición forzada y para construir listas de sospechosos sin garantías. Este volumen no las trata como neutrales: la pregunta, el destinatario y los controles sobre el uso forman parte del método.

## VI.1 Organizaciones criminales: qué aprendió la investigación académica

**El giro de la jerarquía a la red.** Durante décadas, el crimen organizado se representó como una pirámide burocrática (el modelo del informe Cressey de 1967 para la Mafia estadounidense). La investigación con datos de redes mostró estructuras más flexibles, descentralizadas y oportunistas, aunque con matices importantes: algunas organizaciones (como la 'Ndrangheta) combinan una estructura formal reconocida por sus miembros con redes operativas fluidas. La revisión de Campana ("Explaining Criminal Networks: Strategies and Potential Pitfalls", *Methodological Innovations*, 2016) advierte que la estructura de red y la organización no se identifican: muchos estudios llaman "red criminal" a lo que es una red de interacciones registrada por la policía.

**Fundamentos.** Sparrow ("The Application of Network Analysis to Criminal Intelligence: An Assessment of the Prospects", *Social Networks*, 1991) identificó tempranamente los problemas específicos de las redes criminales: datos incompletos, fronteras difusas y redes dinámicas. Sus advertencias siguen vigentes. Krebs ("Mapping Networks of Terrorist Cells", *Connections*, 2002) reconstruyó con fuentes periodísticas la red de los atacantes del 11 de septiembre de 2001 **después** de los hechos; el trabajo es útil para pensar estructura, pero su reconstrucción retrospectiva no muestra que la red hubiera podido identificarse antes.

### Caso 1: la red Caviar (Montreal)

*Datos.* Comunicaciones interceptadas por la policía durante la investigación del Proyecto Caviar (Montreal, 1994–1996), dirigida contra una red de importación de drogas. La policía usó una estrategia inusual: incautar cargamentos sin detener a nadie durante dos años, lo que permitió observar cómo la red respondía a las pérdidas. Morselli (*Inside Criminal Networks*, Springer, 2009; "Assessing Vulnerable and Strategic Positions in a Criminal Network", *Journal of Contemporary Criminal Justice*, 2010) construyó redes en once fases de la investigación.

*\[Emp\] Hallazgos.* Los traficantes identificados por la policía como líderes no eran los más centrales; ciertos intermediarios con alta intermediación eran estructuralmente más importantes para el funcionamiento. La red se reorganizó tras las incautaciones.

*Lectura crítica.* Es uno de los mejores casos de la literatura porque tiene datos longitudinales y un contraste explícito entre posición y rol conocido. Sus límites: los datos son las escuchas autorizadas, de modo que la red es la red de quienes fueron escuchados; y "importancia estructural" no equivale a poder. Los datos están disponibles para enseñanza en repositorios académicos de redes encubiertas (por ejemplo, el paquete de R `networkdata` incluye conjuntos de redes encubiertas).

### Caso 2: la 'Ndrangheta en Lombardía (Operazione Infinito)

*Datos.* La investigación judicial Infinito (Milán, con operativos en 2010) documentó reuniones de miembros de la 'Ndrangheta en Lombardía. Calderoni y Piccardi construyeron un grafo de co-participación en reuniones (bipartito persona–reunión proyectado sobre personas).

*\[Emp\] Hallazgo.* Aplicaron detección de comunidades y encontraron que la red está significativamente agrupada y que las comunidades se asocian **solo parcialmente** con las unidades organizativas reales (los *locali*), que se conocían por la investigación judicial. Publicaron el análisis como "Uncovering the Structure of Criminal Organizations by Community Analysis: The Infinito Network" (conferencia SITIS de IEEE, 2014).

*Lectura crítica.* Es un caso instructivo precisamente porque tenía "verdad de referencia": cuando se conoce la organización real, la detección de comunidades la recupera de forma imperfecta. Si eso pasa con datos judiciales de buena calidad y una organización con estructura formal, hay que ser mucho más cauto donde no hay referencia. Además, la proyección bipartita infla la densidad (II.14): cada reunión se vuelve una clique.

### Caso 3: exposición a la violencia letal en Chicago

*Datos.* Papachristos y Wildeman ("Network Exposure and Homicide Victimization in an African American Community", *American Journal of Public Health*, 2014, publicado en línea en 2013) construyeron una red de co-arrestos (personas detenidas juntas) con cinco años de registros policiales de un barrio de Chicago, con 3.718 personas de alto riesgo.

*\[Emp\] Hallazgos.* El 41 % de los homicidios con arma de fuego ocurrieron en una componente que reunía menos del 4 % de la población del barrio, y cada paso de distancia respecto de una víctima de homicidio reducía en 57 % las probabilidades de ser víctima. Los indicadores de red mejoraron la predicción respecto de los factores individuales.

*Lectura crítica.* El trabajo tiene un encuadre de **salud pública**: identificar a quiénes ofrecer protección y servicios porque están en riesgo de ser **víctimas**. Ese mismo tipo de análisis fue la base conceptual de la Lista de Sujetos Estratégicos de la policía de Chicago, que se usó con otros fines y tuvo resultados problemáticos (VI.7). El caso muestra que el uso, no solo el método, determina el efecto. También: la red de co-arrestos depende de las prácticas policiales de detención, que no son neutrales respecto del barrio ni de la raza.

**Otras referencias de este campo.** Varese (*Mafias on the Move*, Princeton, 2011) sobre la expansión territorial de mafias; Bright, Hughes y Chalmers ("Illuminating Dark Networks: A Social Network Analysis of an Australian Drug Trafficking Syndicate", *Crime, Law and Social Change*, 2012); y Bichler (*Understanding Criminal Networks: A Research Guide*, University of California Press, 2019), un manual metodológico útil.

*Fuentes verificadas:* [Calderoni y Piccardi, 2014](https://publires.unicatt.it/en/publications/uncovering-the-structure-of-criminal-organizations-by-community-a-9/); [Papachristos y Wildeman, ISPS Yale](https://isps.yale.edu/research/publications/isps13-021); [conjuntos de redes encubiertas en networkdata](https://www.rdocumentation.org/packages/networkdata/versions/0.1.6/topics/covert_10).

## VI.2 Redes de corrupción y contrataciones públicas

**Por qué las redes.** La corrupción es, por definición, relacional: un intercambio entre quien tiene poder público y quien obtiene un beneficio, a menudo mediado. Della Porta y Vannucci (*The Hidden Order of Corruption*, Ashgate, 2012) analizaron cómo las redes corruptas desarrollan reglas propias, mecanismos de confianza y garantes que las estabilizan. Pero la corrupción es también **oculta**: los vínculos relevantes rara vez aparecen en los datos. Por eso la investigación cuantitativa trabaja con **indicadores de riesgo** sobre datos administrativos, no con detección de casos.

### Caso 4: riesgo de corrupción en mercados de contratación europeos

*Datos.* Wachs, Fazekas y Kertész ("Corruption Risk in Contracting Markets: A Network Science Perspective", *International Journal of Data Science and Analytics*, 2021; versión preliminar en arXiv, 2019) usaron unos 4,1 millones de contratos de compras públicas de 26 estados de la Unión Europea, publicados entre 2008 y 2016 en el diario oficial de licitaciones (Tenders Electronic Daily).

*Técnica.* Cada mercado nacional se modeló como un grafo **bipartito** entre organismos compradores y empresas ganadoras. El indicador de riesgo fue la **licitación con un único oferente** (*single bidding*), que los autores presentan explícitamente como indicador de riesgo y no como prueba.

*\[Emp\] Hallazgos.* Los mercados con un núcleo más grande y centralizado mostraron mayor riesgo. El riesgo está agrupado en todos los países: el agrupamiento fue de 2 a 8 veces mayor que en un **modelo nulo** aleatorizado que preserva el sector. La localización del riesgo varía: en algunos países se concentra en el núcleo del mercado y en otros (Hungría, Eslovaquia, Estonia) en la periferia.

*Lectura crítica.* El estudio es metodológicamente ejemplar en tres puntos: usa un indicador de riesgo declarado como tal, compara con un modelo nulo que controla una explicación trivial (el sector) y no atribuye corrupción a ningún actor individual. Lo que **no** permite: decir que un contrato o una empresa concreta sea corrupta. Una licitación con un oferente puede deberse a mercados muy especializados, plazos mal diseñados o baja publicidad.

**Captura del Estado.** Fazekas y Tóth ("From Corruption to State Capture: A New Analytical Framework with Empirical Applications from Hungary", *Political Research Quarterly*, 2016) propusieron medir la captura del Estado como la densidad y centralización de redes de contratos con alto riesgo de corrupción entre organismos y empresas, siguiendo su evolución a través de cambios de gobierno. La idea central: la captura no es un acto sino una **estructura** que persiste y se reorganiza.

**Banderas rojas habituales** en datos de contratación, cada una con explicaciones legítimas posibles:

| Indicador | Por qué es sospechoso | Explicación legítima posible |
| --- | --- | --- |
| Un único oferente | Restricción de la competencia | Mercado especializado; baja publicidad no intencional |
| Plazo de presentación muy corto | Favorece a quien conocía de antemano | Urgencia real |
| Procedimiento no abierto | Discrecionalidad | Excepciones legales justificadas |
| Concentración de un proveedor en un organismo | Relación privilegiada | Proveedor único de un servicio |
| Coincidencias de domicilio, socios o directivos entre oferentes | Licitación colusiva simulada | Grupos empresariales legítimos |
| Vínculos entre funcionarios y socios | Conflicto de interés | Vínculo declarado y gestionado |

**Integración de datos.** El análisis más fértil combina el grafo de contratos con el de vínculos societarios (VI.3) y con declaraciones juradas de funcionarios. Esto multiplica los problemas de resolución de entidades (II.15): un mismo socio con nombre transliterado, un DNI mal cargado o un homónimo pueden crear o borrar el vínculo que sostiene toda la hipótesis.

**Datos abiertos.** El Estándar de Datos de Contrataciones Abiertas (*Open Contracting Data Standard*, OCDS) define un formato común que adoptaron varios países de América Latina, y facilita construir estos grafos con datos públicos.

*Fuentes verificadas:* [Wachs, Fazekas y Kertész, arXiv](https://arxiv.org/pdf/1909.08664); [Fazekas y Tóth, documento de trabajo](https://www.crcb.eu/wp-content/uploads/2014/11/Fazekas-Toth_State_capture_PP_2014Nov.pdf).

## VI.3 Vínculos societarios e investigación periodística

**El grafo societario.** Empresas, personas y domicilios unidos por relaciones como accionista de, director de, apoderado de, intermediario registrado de, y domiciliado en. Es un grafo heterogéneo y dirigido (I.2), y los propietarios finales quedan a menudo varios saltos detrás de capas de sociedades interpuestas en jurisdicciones distintas. Seguir esos caminos es exactamente un problema de alcanzabilidad con aristas tipadas.

### Caso 5: Panama Papers y la base Offshore Leaks

*Datos.* Unos 11,5 millones de documentos (aproximadamente 2,6 terabytes) filtrados del estudio panameño Mossack Fonseca, relativos a 214.488 estructuras offshore creadas o administradas entre 1977 y 2015. Los investigó el Consorcio Internacional de Periodistas de Investigación (ICIJ) con unos 370 periodistas de más de 100 medios en más de 80 países (publicación en 2016).

*Técnica.* La unidad de datos del ICIJ extrajo metadatos de los documentos con Apache Tika y Solr, y los organizó en un grafo de propiedades en **Neo4j**: nodos para entidades offshore, personas, intermediarios y domicilios, y aristas para sus relaciones. Los periodistas, en su mayoría sin formación técnica, exploraban el grafo con **Linkurious**, una interfaz visual con controles de acceso. El ICIJ publicó luego una versión de los datos estructurados como base pública consultable, Offshore Leaks, que hoy integra varias filtraciones.

*Lectura crítica.*

- **Lo que hace bien.** La base pública advierte que existen usos legítimos de sociedades offshore y que su inclusión no implica conducta ilegal. Es la aplicación correcta del principio 1 a la publicación de un grafo.
- **El grafo como herramienta de orientación.** El grafo permitió saber **dónde buscar**; la nota periodística se sostuvo en los documentos, no en la estructura. Es el uso epistémicamente adecuado: el grafo genera hipótesis y la verificación es documental.
- **Riesgos.** Homónimos (Juan Pérez en una sociedad de las Islas Vírgenes Británicas no es necesariamente el Juan Pérez que se investiga), domicilios compartidos por cientos de sociedades en una misma oficina de registro (crean hubs sin significado), y entidades que figuran por obligaciones formales (un agente registrado figura en miles de sociedades). Son exactamente los errores de fusión de entidades y de "funciones de servicio" de IV.9.

**Herramientas abiertas para periodismo de datos.** Aleph, la plataforma del Proyecto de Investigación sobre el Crimen Organizado y la Corrupción (OCCRP), integra documentos y registros con un modelo de entidades llamado FollowTheMoney, que normaliza personas, empresas, contratos y relaciones para cruzar fuentes. OpenSanctions publica listas de sanciones y personas políticamente expuestas con el mismo modelo. OpenCorporates y los registros de beneficiarios finales (donde existen y son públicos) proveen los datos societarios.

**Buenas prácticas propias del periodismo.** Verificación documental de cada arista que sostenga una afirmación publicada; derecho a réplica de las personas mencionadas; distinción explícita entre "figura en" y "es responsable de"; y seguridad de las fuentes (VI.8). La filtración misma es una fuente con sesgo: muestra los clientes de un estudio, no el universo de las sociedades offshore.

*Fuentes verificadas:* [Linkurious sobre los Panama Papers](https://linkurio.us/panama-papers-how-linkurious-enables-icij-to-investigate-the-massive-mossack-fonseca-leaks/); [ICIJ y Neo4j en los Paradise Papers](https://prnewswire.com/news-releases/the-international-consortium-of-investigative-journalists-uses-neo4js-native-graph-platform-to-unlock-explosive-13-million-files-paradise-papers-leak-300555204.html); [Bellingcat sobre Offshore Leaks](https://bellingcat.gitbook.io/toolkit/more/all-tools/icij-offshore-leaks-database).

## VI.4 Derechos humanos: documentación, desapariciones y fragmentación documental

En la documentación de violaciones masivas de derechos humanos, los grafos cumplen dos funciones muy distintas: **reconstruir estructuras de responsabilidad** (cadenas de mando, circulación de órdenes y documentos) y **integrar registros fragmentados de víctimas** (resolución de entidades entre listas de distintas fuentes). Ambas tienen un adversario: los perpetradores ocultaron, destruyeron o falsearon registros.

### Caso 6: el Archivo Histórico de la Policía Nacional de Guatemala

*Contexto.* En 2005 se descubrió en Ciudad de Guatemala el archivo de la antigua Policía Nacional: millones de documentos sobre operaciones policiales desde 1896, incluido el período del conflicto armado interno. El Human Rights Data Analysis Group (HRDAG) diseñó y dirigió el muestreo estadístico del archivo, porque era imposible leerlo completo.

*Técnica.* Para el caso de Fernando García, dirigente sindical estudiantil detenido y desaparecido en 1984, Patrick Ball y Daniel Guzmán analizaron miles de documentos internos intercambiados entre la Dirección General y las unidades subordinadas: quién enviaba documentos a quién, con qué frecuencia y por qué canales. Es, en sustancia, un análisis del **grafo de flujo documental** de una burocracia. El análisis mostró que la cadena de mando funcionaba en el momento de la captura: las órdenes y los informes circulaban regularmente por la jerarquía.

*Resultado.* En septiembre de 2013, el excoronel Héctor Rafael Bol de la Cruz, exdirector de la Policía Nacional, y Jorge Gómez, ex alto oficial, fueron condenados como autores intelectuales de la desaparición forzada, con penas de 40 años de prisión. Ball declaró como perito.

*Lectura crítica.* Es un uso ejemplar por cuatro razones:

1. **La pregunta es estructural, y el grafo responde exactamente eso.** No se usó el grafo para decir "el director ordenó la desaparición", sino para refutar la defensa típica de la autoría mediata: que los mandos no sabían lo que hacían los subordinados porque la cadena de comunicación estaba rota. El grafo muestra que no lo estaba.
2. **La inferencia sobre el archivo completo se basó en un muestreo probabilístico** con incertidumbre cuantificada, no en los documentos más llamativos.
3. **La evidencia de los actos concretos vino de otras fuentes** (testimonios y documentos específicos del caso). El grafo se combinó con ellas.
4. **Las fuentes eran del perpetrador**, y se trataron como tales: registran la burocracia represiva desde adentro, con sus categorías.

### Integración de listas de víctimas

Cuando las víctimas se registran en varias fuentes (organismos estatales, ONG, iglesias, prensa), cada lista es incompleta y las listas se solapan. HRDAG desarrolló dos técnicas que combinan grafos y estadística:

- **Resolución de entidades entre listas.** Determinar qué registros de distintas fuentes corresponden a la misma víctima, con nombres incompletos, variantes ortográficas y fechas aproximadas. Las decisiones de emparejamiento forman un grafo de registros, cuyas componentes son las personas (III.3). Un error de transitividad puede fusionar dos víctimas distintas.
- **Estimación por sistemas múltiples** (*multiple systems estimation*). A partir de los patrones de solapamiento entre listas, estima cuántas víctimas **no figuran en ninguna lista**. Es la versión estadística rigurosa del principio "ausencia de registro no es ausencia del hecho". HRDAG la aplicó, entre otros, en Perú (para la Comisión de la Verdad y Reconciliación), Colombia y Siria.

**El sesgo de los datos convenientes.** Las cifras documentadas no son una muestra aleatoria de las violaciones: los hechos en zonas con presencia de organizaciones de derechos humanos, prensa o comunicaciones quedan más registrados. Un mapa o un grafo de "casos documentados" muestra en parte dónde había quién documentara. Esto vale igual para la estructura: los centros de detención o unidades mejor documentados parecen más centrales.

### Argentina: archivos, juicios y fragmentación

En Argentina, la documentación de la represión de la última dictadura se apoya en fuentes heterogéneas: el informe *Nunca Más* de la CONADEP (1984), los legajos y testimonios reunidos en los juicios por crímenes de lesa humanidad reabiertos desde 2006, los archivos de inteligencia de la Dirección de Inteligencia de la Policía de la Provincia de Buenos Aires (DIPPBA), custodiados por la Comisión Provincial por la Memoria, el trabajo del Equipo Argentino de Antropología Forense y los acervos de organismos como Memoria Abierta. La documentación es fragmentaria por diseño: la represión clandestina evitó dejar rastros, y buena parte de los registros fue destruida.

En ese contexto, el análisis de redes puede aportar en dos planos, con las mismas cautelas que en Guatemala: reconstruir la articulación entre fuerzas, unidades y centros clandestinos a partir de los traslados de detenidos y de la circulación documental, y conectar registros dispersos de víctimas y testigos. Los juicios ya usan este tipo de reconstrucción en forma cualitativa (quién estaba destinado dónde y cuándo, qué unidad dependía de cuál). Formalizarla como grafo temporal (II.13) permite hacer explícitas las inferencias, sus fuentes y sus huecos.

*Fuentes verificadas:* [HRDAG sobre la condena de Bol de la Cruz](https://hrdag.org/2013/09/20/guatemalas-bol-de-la-cruz-found-guilty/); [HRDAG, diez años de datos del AHPN](https://hrdag.org/2015/07/06/celebrating-ten-years-of-data-from-the-ahpn/).

## VI.5 Intermediarios y redes institucionales

**Por qué importan los intermediarios.** En casi todos los fenómenos de este volumen hay actores que conectan mundos que no deberían estar conectados: el estudio contable que constituye sociedades, el gestor que tramita habilitaciones, el abogado que representa a ambas partes, el funcionario de enlace, el familiar que presta su nombre. Son el punto donde lo legal y lo ilegal se tocan, y por eso los estudios de crimen organizado y corrupción les prestan cada vez más atención. Morselli (Caso 1) mostró su importancia funcional; Della Porta y Vannucci (VI.2), su papel como garantes de la confianza en intercambios corruptos.

**Formalización.** La tipología de Gould y Fernandez (IV.3) es la herramienta adecuada, porque distingue intermediaciones según los grupos de los actores involucrados. Aplicada a una red de contratación con grupos definidos por sector (público, privado, profesional):

| Tipo | Configuración | Ejemplo en contrataciones |
| --- | --- | --- |
| Coordinador | Intermediario y extremos del mismo grupo | Un funcionario que conecta a dos áreas del mismo organismo |
| Guardián (*gatekeeper*) | El intermediario y el destino son del mismo grupo; el origen es externo | Un funcionario de compras por el que pasan todas las ofertas |
| Representante | El intermediario y el origen son del mismo grupo; el destino es externo | El gerente comercial que representa a la empresa ante el organismo |
| Consultor | Los extremos son del mismo grupo; el intermediario, de otro | Un estudio que asesora a dos empresas que compiten |
| Enlace | Los tres de grupos distintos | Un gestor independiente entre un organismo y una empresa |

El tipo **enlace** y el **consultor** que asesora a competidores son los que más interés tienen para la investigación de colusión, pero también son los perfiles de cualquier consultor legítimo. La tipología describe la posición; la evaluación de la conducta requiere documentos.

**Redes institucionales.** Para investigar instituciones (no individuos) conviene trabajar con redes multicapa donde los nodos son organismos, unidades, empresas y cargos, y las capas son relaciones distintas: dependencia jerárquica formal, transferencias de personal (puertas giratorias entre sector público y privado), contratos, financiamiento, y comunicaciones documentadas. Lo revelador suele ser el **desajuste entre capas**: una unidad formalmente subordinada que en la capa de contratos o de comunicaciones actúa con autonomía, o un organismo cuyos cargos directivos provienen sistemáticamente de las empresas que regula. Esto operacionaliza la distancia weberiana entre burocracia formal y patrimonialismo (V.2) y la de Lomnitz entre sistemas formales e intercambios informales (IV.6).

**Cuidado con los nodos de servicio.** Notarías, estudios contables, agentes de registro y bancos aparecen como intermediarios de enorme centralidad simplemente por su función. Antes de interpretar, conviene separarlos en una capa propia o usar modelos nulos que controlen el grado (II.7).

## VI.6 Preservación y reconstrucción de evidencia

Cuando un grafo se va a usar como evidencia (en un juicio, una comisión de la verdad o una investigación publicada), tiene que poder ser examinado por otros: de dónde salió cada nodo y cada arista, qué decisiones se tomaron y qué pasaría con otras decisiones. Esto convierte el problema en uno de **procedencia** (Volumen VII).

**Requisitos mínimos para un grafo con valor probatorio.**

1. **Cada arista remite a sus fuentes.** No "A y B están vinculados", sino "A y B figuran como socios en la escritura X, folio Y, consultada en tal fecha". Las aristas sin fuente se marcan como inferidas o se excluyen.
2. **Cada nodo tiene su historia de resolución.** Qué registros se fusionaron para formarlo, con qué regla y con qué grado de confianza. Las fusiones dudosas quedan reversibles.
3. **Los datos originales se preservan intactos**, con sumas de verificación criptográficas (hashes) que permitan demostrar que no se alteraron, y el grafo se construye a partir de ellos por un proceso reproducible (un script versionado, no ediciones manuales en una herramienta visual).
4. **Las transformaciones quedan registradas:** filtros, umbrales, agregaciones temporales, proyecciones.
5. **Las métricas se reportan con su sensibilidad** (V.6): qué conclusiones sobreviven a variaciones razonables en las decisiones anteriores.
6. **Se separan los tres estados epistémicos** de cada afirmación: registrado en la fuente, inferido por un procedimiento, o reconstrucción hipotética (Evaluación, F4).

**Estándares de referencia.** El Protocolo de Berkeley sobre Investigaciones Digitales de Fuentes Abiertas (Centro de Derechos Humanos de la Universidad de California en Berkeley y Oficina del Alto Comisionado de las Naciones Unidas para los Derechos Humanos, 2020; versión en español disponible) establece principios de identificación, preservación, verificación y análisis de información digital de fuentes abiertas para investigaciones de derechos humanos y penales internacionales. Sus exigencias de documentar la cadena de custodia y la metodología se aplican directamente a la construcción de grafos.

**Reconstrucción ante destrucción de registros.** Cuando faltan documentos de forma sistemática, la pregunta es qué puede inferirse y con qué incertidumbre:

- **Inferencia por redundancia:** un mismo hecho puede quedar registrado indirectamente en varias fuentes (la copia de un memorando en otra dependencia, una referencia en un registro de entrada). El grafo de flujo documental indica dónde buscar copias.
- **Estimación de lo no registrado** con sistemas múltiples (VI.4).
- **Patrones de ausencia:** la falta de documentos en un período o una unidad específica, cuando el resto del archivo es regular, es en sí misma un dato. Pero es un dato sobre el archivo, y su interpretación (destrucción deliberada, pérdida, otro circuito) requiere evidencia adicional.

**Integridad del registro de análisis.** Para que el propio proceso de investigación sea auditable, conviene llevar un registro de las operaciones que no se pueda alterar sin que se note: cada entrada incluye el hash de la anterior, como una cadena. Es la misma idea de los registros de auditoría a prueba de manipulaciones que el Volumen VII desarrolla para grafos de procedencia.

## VI.7 Daños: falsos positivos, bases de pandillas y policía predictiva

Tres casos documentados muestran cómo la lógica de redes, aplicada a listas policiales, produce daños concretos. Los tres comparten un patrón: **asociación tratada como evidencia, datos sin control de calidad y uso de la lista fuera de su propósito declarado.**

### Caso 7: la Lista de Sujetos Estratégicos de Chicago

*Qué era.* En 2013, la policía de Chicago puso en marcha un programa piloto que generó una lista de 426 personas estimadas con mayor riesgo de estar involucradas en violencia armada, como víctimas o como autores. El modelo usaba, entre otros factores, vínculos de co-arresto con víctimas de homicidio, inspirado en la investigación de redes del Caso 3. Las personas de la lista debían recibir intervenciones preventivas.

*Evaluación.* Saunders, Hunt y Hollywood, de la RAND Corporation ("Predictions Put into Practice: A Quasi-Experimental Evaluation of Chicago's Predictive Policing Pilot", *Journal of Experimental Criminology*, 2016), compararon a las personas de la lista con un grupo emparejado. **\[Emp\]** Las personas de la lista no tuvieron más ni menos probabilidades de ser víctimas de homicidio o de disparos, y el análisis a nivel ciudad tampoco mostró efecto. Pero sí tuvieron **más probabilidades de ser arrestadas por un tiroteo**. Los autores sugieren que algunos agentes usaron la lista como fuente de sospechosos para cerrar casos.

*Lectura.* Un análisis pensado para identificar posibles **víctimas** a quienes proteger se convirtió, en la práctica, en una lista de sospechosos. La proximidad en el grafo pasó a funcionar como indicio de autoría. La policía discontinuó el programa el 1 de noviembre de 2019, al terminar el financiamiento federal, y la [Oficina del Inspector General de Chicago](https://www.oversight.gov/reports/advisory-concerning-chicago-police-departments-predictive-risk-models) publicó luego un informe sobre las lecciones del caso.

### Caso 8: CalGang (California)

*Qué era.* Una base de datos compartida entre agencias policiales de California de personas consideradas miembros o asociados de pandillas.

*\[Emp\] Auditoría estatal de 2016.* La Auditoría del Estado de California encontró que la base incluía a 42 personas registradas como menores de un año, 28 de las cuales figuraban como habiendo "admitido" pertenecer a una pandilla (muy probablemente errores de carga); personas incorporadas sin evidencia suficiente; plazos de retención de hasta 100 años, muy superiores a los permitidos; y uso de la base por algunos departamentos para evaluar candidatos a empleo, fuera de su finalidad.

*Lectura.* Es el ejemplo más claro de errores de identidad y de calidad de datos en una base de asociaciones. Que un bebé "admita" pertenecer a una pandilla no es un problema estadístico: es la prueba de que nadie revisaba los registros. Y la base se usaba para decisiones con consecuencias sobre personas que no sabían que estaban incluidas ni podían impugnarlo.

### Caso 9: la Gangs Matrix (Londres)

*Qué era.* Una base de la Policía Metropolitana de Londres, creada en 2012, de presuntos integrantes de pandillas con puntajes automáticos de "daño".

*\[Emp\] Hallazgos.* El informe de Amnistía Internacional *Trapped in the Matrix* (2018) documentó que, a octubre de 2017, el 78 % de las 3.806 personas registradas eran negras, cuando según las propias cifras de la policía el 27 % de los responsables de violencia juvenil grave lo eran. Entre los criterios de inclusión figuraban compartir videos en redes sociales o aparecer en videos de música *grime* con referencias a pandillas, y **haber sido víctima** de un delito vinculado a pandillas. La base se compartía con agencias no policiales (oficinas de empleo, asociaciones de vivienda, escuelas), y se reportó su uso para presionar con desalojos que afectaban a familias enteras. La Oficina del Comisionado de Información (ICO) concluyó en 2018 que violaba la legislación de protección de datos. En 2022 se eliminaron más de mil personas, una impugnación de Liberty llevó a reconocer su uso ilegal, se dejó de usar en febrero de 2024 y se borró en febrero de 2025.

*Lectura.* Tres mecanismos de este tratado operan juntos: **asociación como evidencia** (aparecer en un video con alguien), **la víctima convertida en sospechosa** por proximidad, y **difusión de la etiqueta** a esferas ajenas (vivienda, empleo), donde produce exclusión. El sesgo racial no es un error aleatorio sino el resultado de qué barrios y qué expresiones culturales se vigilaban: el sesgo de observación de V.3, institucionalizado.

### Lecciones comunes

| Mecanismo | Chicago | CalGang | Gangs Matrix |
| --- | --- | --- | --- |
| Proximidad tratada como indicio | Sí | Sí (asociados) | Sí |
| Errores de datos sin control | No documentado | Sí, graves | Sí |
| Víctimas incluidas como riesgo | Sí, por diseño | No documentado | Sí |
| Uso fuera de propósito | Sí (identificar sospechosos) | Sí (empleo) | Sí (vivienda, empleo, escuelas) |
| Desigualdad racial en el resultado | Señalada en críticas públicas | Señalada en críticas públicas | Documentada con cifras |
| Posibilidad de impugnar la inclusión | Limitada | Limitada en el momento de la auditoría | No, hasta las reformas |

*Fuentes verificadas:* [RAND, Saunders, Hunt y Hollywood](https://www.rand.org/pubs/external_publications/EP67204.html); [KPBS sobre la auditoría de CalGang](https://www.kpbs.org/news/2016/aug/16/state-audit-finds-serious-lapses-calgang-database); [Amnistía Internacional Reino Unido sobre la Gangs Matrix](https://www.amnesty.org.uk/london-trident-gangs-matrix-metropolitan-police); [Gangs Matrix, cronología](https://en.wikipedia.org/wiki/Gangs_Matrix).

## VI.8 Privacidad, protección de fuentes y seguridad de testigos

Un grafo de personas es, en sí mismo, un dato sensible: aunque cada arista sea pública, la **agregación** revela lo que ninguna fuente aislada revela (con quién se relaciona alguien, qué grupos frecuenta, quiénes son sus contactos frecuentes). En investigación sobre crimen organizado, corrupción o represión, esa información puede costar vidas.

**Riesgos específicos de los datos relacionales.**

- **Reidentificación por estructura.** Backstrom, Dwork y Kleinberg ("Wherefore Art Thou R3579X? Anonymized Social Networks, Hidden Patterns, and Structural Steganography", WWW 2007) mostraron que en un grafo "anonimizado" (nombres reemplazados por identificadores) un atacante puede reidentificar personas a partir de patrones de vínculos. Narayanan y Shmatikov ("De-anonymizing Social Networks", IEEE Symposium on Security and Privacy, 2009) lo demostraron a gran escala cruzando dos redes sociales. **Quitar nombres no anonimiza un grafo.**
- **Exposición de terceros.** Cada persona entrevistada aporta datos sobre otras que no consintieron. En redes de testigos o de víctimas, publicar un vínculo puede exponer a alguien que no habló.
- **Inferencia de atributos.** Por homofilia, los atributos de los vecinos permiten inferir atributos sensibles de una persona (orientación sexual, afiliación política) que ella no reveló.
- **Mapa para el adversario.** Un grafo de una red de defensores de derechos humanos, periodistas o testigos es exactamente lo que un perpetrador necesitaría para identificar a quién silenciar. Los mismos algoritmos que buscan "puntos críticos" en una red criminal señalan, aplicados a una red de defensa, a quiénes atacar para desarticularla.

**Protección de fuentes.** En periodismo y en investigación de derechos humanos, los nodos que representan fuentes deben poder existir en el análisis sin quedar identificables en ninguna salida: seudónimos gestionados fuera del grafo de trabajo, separación física entre la tabla de identidades y el grafo, y revisión de cada visualización publicada para asegurar que la estructura no delate a nadie (un nodo con vínculos únicos es identificable aunque no tenga nombre).

**Seguridad de testigos.** En procesos judiciales, la estructura de una red de testimonios puede revelar quién aportó información. Si un dato solo pudo provenir de una persona por su posición, publicar el grafo equivale a nombrarla.

**Medidas técnicas.** Control de acceso por roles a los datos crudos; cifrado en reposo; registros de acceso; agregación antes de publicar (estructuras a nivel de grupo y no de individuo); y, cuando corresponde, técnicas de privacidad diferencial para estadísticas de grafos, que garantizan formalmente que la presencia o ausencia de una persona no cambia significativamente el resultado publicado (con costos de precisión que hay que evaluar caso por caso).

**Marco normativo.** En Argentina, la Ley 25.326 de Protección de los Datos Personales clasifica como datos sensibles los que revelan origen racial y étnico, opiniones políticas, convicciones religiosas, filosóficas o morales, afiliación sindical, salud o vida sexual, y restringe su tratamiento. El Reglamento General de Protección de Datos europeo establece principios análogos (minimización, limitación de la finalidad). Los casos de VI.7 muestran lo que ocurre cuando los grafos de personas se usan fuera de la finalidad para la que se construyeron. Este tratado no ofrece asesoramiento legal: aplicar estas normas a un proyecto concreto requiere consulta profesional.

**Principio rector.** Antes de construir un grafo de personas, preguntarse: ¿quién podría hacer daño con este grafo si lo obtuviera, y qué le estaríamos facilitando?

## VI.9 Protocolo de buenas prácticas

Una lista de verificación para investigaciones con grafos de personas en estos ámbitos. Sintetiza lo desarrollado en los Volúmenes II a VI; no reemplaza las normas éticas, legales y profesionales de cada campo.

**Antes de construir el grafo.**

1. Formular la pregunta por escrito y explicitar quién usará el resultado y para qué.
2. Evaluar el daño del peor error: ¿qué le pasa a una persona incluida por error? Si la respuesta es grave, exigir estándares de evidencia proporcionales.
3. Definir la frontera y justificarla. Registrar qué se dejó fuera.
4. Definir la unidad de nodo y el tipo de vínculo; separar tipos de relación en capas.
5. Evaluar el riesgo para fuentes, testigos y terceros, y diseñar la seguridad antes de recolectar.

**Durante la construcción.**

6. Vincular cada arista a su fuente; marcar las inferidas.
7. Documentar la resolución de entidades: reglas, umbrales, fusiones dudosas reversibles.
8. Representar tres estados por par (presente, ausente observado, no observado) o, como mínimo, estimar la fracción no observada.
9. Conservar los tiempos de cada vínculo; no agregar sin necesidad.
10. Separar nodos de servicio (notarías, estudios, bancos, agentes registrados) o controlarlos.

**Durante el análisis.**

11. Elegir cada métrica por su supuesto de flujo y explicitarlo.
12. Comparar contra modelos nulos pertinentes.
13. Correr detección de comunidades con varios métodos y semillas; reportar estabilidad; no nombrar a los grupos como organizaciones.
14. Hacer análisis de sensibilidad frente a faltantes, umbrales, ventanas y reglas de resolución.
15. Buscar activamente explicaciones legítimas para cada patrón llamativo.

**Al comunicar.**

16. Distinguir en el texto lo registrado, lo inferido y lo hipotético.
17. No presentar visualizaciones como prueba; acompañar cada afirmación con su métrica y su incertidumbre.
18. Usar formulaciones que no atribuyan conducta por posición ("figura vinculado en tal registro", no "está involucrado").
19. Revisar que ninguna salida publicada permita identificar fuentes o testigos.
20. Dar derecho a réplica a las personas mencionadas, cuando corresponda.

**Después.**

21. Preservar datos, código y registro de decisiones con integridad verificable.
22. Definir plazos de conservación y destrucción de los datos personales.
23. Limitar el uso del grafo a la finalidad declarada; no compartirlo para otros fines.

## Matriz de técnicas (parte VI)

| Aplicación | Técnica | Uso legítimo documentado | Riesgo principal | Condición para un uso defendible | Caso |
| --- | --- | --- | --- | --- | --- |
| Estructura de redes criminales | Centralidad, intermediación sobre escuchas | Comprender funcionamiento y resiliencia | Leer posición como jerarquía | Contraste con roles conocidos; datos longitudinales | 1 |
| Unidades organizativas | Detección de comunidades sobre co-participación | Hipótesis sobre subgrupos | Comunidad leída como organización | Verdad de referencia o evidencia independiente | 2 |
| Prevención de violencia | Distancia a víctimas en redes de co-arresto | Identificar a quién ofrecer protección | Conversión en lista de sospechosos | Finalidad restringida y controlada | 3, 7 |
| Riesgo de corrupción | Grafos bipartitos de contratación; banderas rojas | Priorizar auditorías a nivel de mercado | Atribuir corrupción a un actor | Indicadores declarados como riesgo; modelo nulo | 4 |
| Propiedad final | Alcanzabilidad en grafos societarios | Orientar investigación periodística | Homónimos; nodos de servicio | Verificación documental de cada arista | 5 |
| Cadena de mando | Grafo de flujo documental con muestreo | Refutar la ruptura de la cadena en juicios | Confundir funcionamiento con orden concreta | Muestreo probabilístico; combinación con otras pruebas | 6 |
| Listas de víctimas | Resolución de entidades; sistemas múltiples | Estimar lo no registrado | Fusiones erróneas | Reglas documentadas; incertidumbre reportada | 6 |
| Bases de "asociados" | Proximidad y atributos | Ninguno demostrado sin garantías | Falsos positivos, sesgo racial, uso fuera de finalidad | Auditoría, derecho a impugnar, finalidad limitada | 8, 9 |

## Ejercicios y fuentes del Volumen VI

### Ejercicios

1. (★★) Con una red encubierta pública (por ejemplo, las del paquete `networkdata` de R o del repositorio de redes encubiertas de UCINET), calculá grado, intermediación y restricción de Burt. Escribí qué afirmaciones sobre los roles permite cada métrica y cuáles no.
2. (★★) Tomá una red de co-participación en reuniones (bipartita) y comparala con su proyección sobre personas. Medí cuánto aumentan el agrupamiento y la modularidad por efecto de la proyección.
3. (★★) Con datos abiertos de contrataciones en formato OCDS de algún país de la región, construí el grafo bipartito organismo–proveedor de un sector, calculá la tasa de licitaciones con un único oferente por organismo y comparala con un modelo nulo que preserve el sector. Redactá el resultado sin atribuir corrupción a ningún actor.
4. (★★) Diseñá un conjunto sintético de registros de víctimas en tres listas con nombres con variantes ortográficas. Aplicá dos reglas de resolución (una estricta y una laxa) con Union-Find y compará el número de personas resultantes y el tamaño de la mayor clase.
5. (★★★) Simulá una base de "asociados" en una red aleatoria donde solo una pequeña fracción de nodos participa en un delito. Medí la tasa de falsos positivos si se marca a todos los vecinos a distancia 1 y a distancia 2. Relacioná el resultado con la paradoja de la amistad.
6. (★★★) Conceptual: escribí un protocolo de seguridad para un proyecto que construya un grafo de testigos de un caso de lesa humanidad, siguiendo VI.8 y VI.9.
7. (★★★) Conceptual: elegí un caso de VI.7 y escribí qué cambios de diseño (de datos, de método y de gobernanza) habrían evitado el daño principal.

### Fuentes verificadas de este volumen

- [Calderoni y Piccardi, "Uncovering the Structure of Criminal Organizations by Community Analysis: The Infinito Network" (2014)](https://publires.unicatt.it/en/publications/uncovering-the-structure-of-criminal-organizations-by-community-a-9/)
- [Papachristos y Wildeman, "Network Exposure and Homicide Victimization in an African American Community"](https://isps.yale.edu/research/publications/isps13-021)
- [Wachs, Fazekas y Kertész, "Corruption Risk in Contracting Markets" (arXiv)](https://arxiv.org/pdf/1909.08664)
- [Fazekas y Tóth, documento de trabajo sobre captura del Estado (2014)](https://www.crcb.eu/wp-content/uploads/2014/11/Fazekas-Toth_State_capture_PP_2014Nov.pdf)
- [Linkurious sobre el uso de grafos en los Panama Papers](https://linkurio.us/panama-papers-how-linkurious-enables-icij-to-investigate-the-massive-mossack-fonseca-leaks/)
- [Bellingcat: guía de la base Offshore Leaks](https://bellingcat.gitbook.io/toolkit/more/all-tools/icij-offshore-leaks-database)
- [HRDAG sobre la condena de Bol de la Cruz (2013)](https://hrdag.org/2013/09/20/guatemalas-bol-de-la-cruz-found-guilty/)
- [HRDAG, diez años de datos del Archivo Histórico de la Policía Nacional](https://hrdag.org/2015/07/06/celebrating-ten-years-of-data-from-the-ahpn/)
- [RAND: evaluación de la Lista de Sujetos Estratégicos de Chicago](https://www.rand.org/pubs/external_publications/EP67204.html)
- [Inspector General: modelos predictivos de riesgo de la policía de Chicago](https://www.oversight.gov/reports/advisory-concerning-chicago-police-departments-predictive-risk-models)
- [KPBS sobre la auditoría estatal de CalGang (2016)](https://www.kpbs.org/news/2016/aug/16/state-audit-finds-serious-lapses-calgang-database)
- [Amnistía Internacional Reino Unido sobre la Gangs Matrix](https://www.amnesty.org.uk/london-trident-gangs-matrix-metropolitan-police)
- [Gangs Matrix: cronología del cierre](https://en.wikipedia.org/wiki/Gangs_Matrix)

Las demás obras citadas (Sparrow, Krebs, Morselli, Campana, Varese, Della Porta y Vannucci, Backstrom y coautores, Narayanan y Shmatikov) son publicaciones académicas de referencia; sus enlaces se consolidan en el Volumen IX.
