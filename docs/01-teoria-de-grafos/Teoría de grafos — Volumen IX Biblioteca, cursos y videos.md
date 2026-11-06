# Teoría de grafos — Volumen IX: Biblioteca, cursos y videos

Nov 5, 2026 · @Anna Tchijova

## Cómo usar la biblioteca y criterios de selección

Este volumen corresponde a la Parte X del pedido (entregables 4 y 5). Organiza los recursos en las nueve categorías pedidas (A a I) y en un catálogo de cursos y videos. Al final propone un orden de lectura.

**Criterios de inclusión.** Un recurso entra si cumple al menos uno de estos criterios: es la referencia técnica de su área, cubre un hueco que otros no cubren, tiene una perspectiva crítica valiosa, es de acceso libre y de calidad, o está en español. Ninguno se incluye solo por popularidad. Para cada uno se indican nivel, prerrequisitos, temas, utilidad específica, fortalezas, limitaciones, acceso y enlace.

**Verificación.** Los datos editoriales y los enlaces marcados con ✓ se verificaron el 5 de noviembre de 2026 en catálogos de bibliotecas, sitios editoriales o sitios de los autores. Los recursos sin enlace son obras académicas de referencia citadas en los volúmenes anteriores, cuya existencia está bien establecida, pero cuyo enlace no se comprobó en esta sesión; conviene buscarlos por DOI o en el catálogo de una biblioteca.

**Nivel.** (I) introductorio, sin prerrequisitos formales; (G) grado avanzado, con demostraciones y algo de álgebra lineal o probabilidad; (P) posgrado o investigación.

**Acceso.** "Libre" significa que el autor o la editorial ofrecen el texto completo gratis y de forma legal. No se incluyen enlaces a copias no autorizadas.

**Sobre el idioma.** La mayor parte de la literatura técnica está en inglés. Los recursos en español se marcan con \[ES\] y se priorizaron donde existen con buena calidad, sobre todo en análisis de redes sociales.

## A. Fundamentos

| Obra | Nivel | Prerrequisitos | Utilidad específica | Fortalezas | Limitaciones | Acceso |
| --- | --- | --- | --- | --- | --- | --- |
| Douglas B. West, *Introduction to Graph Theory*, 2.ª ed., Prentice Hall, 2001 ✓ | G | Inducción, lógica | Aprender a demostrar en grafos; base de los Volúmenes I y II | Ejercicios graduados en enorme cantidad; explica técnicas de prueba y errores típicos (como el error de construcción de la Evaluación, B6) | Notación propia que difiere de Diestel; poco sobre redes y aplicaciones | Pago |
| Reinhard Diestel, *Graph Theory*, 6.ª ed., Springer GTM 173, 2025 ✓ ([sitio](https://diestel-graph-theory.com/)) | G–P | Madurez en demostraciones | Referencia formal de todo el tratado; notación adoptada | Pruebas concisas y completas; actualizado a la investigación (menores, *tangles*, χ-acotación) | Exigente como primer libro; casi sin algoritmos | Texto principal libre en el sitio; eBook y edición profesional pagos |
| J. A. Bondy y U. S. R. Murty, *Graph Theory*, Springer GTM 244, 2008 ✓ | G–P | Inducción, algo de álgebra lineal | Puente entre teoría, algoritmos y complejidad | Incluye flujos, complejidad, método probabilístico y problemas abiertos | Extenso; conviene leerlo por capítulos | Pago; disponible en bibliotecas universitarias |
| Richard J. Trudeau, *Introduction to Graph Theory*, Dover, 1993 (edición original de 1976) | I | Ninguno | Primer contacto para quien no viene de la matemática | Muy pedagógico, enseña a leer demostraciones | Cubre poco; no llega a temas intermedios | Pago, económico |
| Robin J. Wilson, *Introduction to Graph Theory*, 5.ª ed., Pearson, 2010 | I–G | Ninguno | Lectura breve antes de West | Claro y conciso | Pocos ejercicios difíciles | Pago |
| Martin Aigner y Günter M. Ziegler, *Proofs from THE BOOK*, Springer (6.ª ed., 2018) | G | Inducción | Ver demostraciones elegantes (incluye cuatro pruebas de la fórmula de Cayley, I.5) | Muestra cómo se piensa en matemática | No es un libro de texto de grafos | Pago |
| László Lovász, *Combinatorial Problems and Exercises*, 2.ª ed., AMS Chelsea, 2007 ✓ | G–P | Álgebra lineal, probabilidad | Práctica intensiva con pistas y soluciones completas | Todo el material en forma de problemas | Requiere constancia; poco texto expositivo | Pago |
| Kenneth H. Rosen, *Matemática discreta y sus aplicaciones* (traducción, McGraw-Hill) \[ES\] | I | Ninguno | Introducción en español con capítulos de grafos y árboles | Accesible; muchos ejemplos | Superficial en demostraciones | Pago |
| Ralph P. Grimaldi, *Matemáticas discreta y combinatoria* (traducción, Pearson) \[ES\] | I–G | Ninguno | Alternativa en español, más combinatoria | Buenos ejercicios | Grafos es solo una parte | Pago |

**Recomendación.** Para quien quiera aprender a demostrar: West, con Diestel como consulta. Para quien quiera un panorama riguroso pero rápido antes de las aplicaciones: los capítulos 1 a 5 de Diestel, que se leen gratis en el sitio del autor.

## B. Intermedio y C. Avanzado

### B. Intermedio

| Obra | Nivel | Temas | Utilidad específica | Limitaciones | Acceso |
| --- | --- | --- | --- | --- | --- |
| Fan R. K. Chung, *Spectral Graph Theory*, AMS, 1997 | G–P | Laplaciano normalizado, Cheeger, caminatas aleatorias | Base de II.6 y del clustering espectral | Denso; se recomienda empezar por los primeros capítulos | Pago; capítulos en el sitio de la autora |
| Andries E. Brouwer y Willem H. Haemers, *Spectra of Graphs*, Springer, 2012 | G–P | Espectros de familias de grafos, grafos coespectrales | Consulta sobre espectros concretos (II.6) | Más algebraico que aplicado | Pago; versión previa libre de los autores |
| Noga Alon y Joel H. Spencer, *The Probabilistic Method*, Wiley (4.ª ed., 2016) | G–P | Método probabilístico, desigualdades de concentración, grafos aleatorios | Entender pruebas de existencia (II.8) y técnicas de II.7 | Exige probabilidad sólida | Pago |
| Alan Frieze y Michał Karoński, *Introduction to Random Graphs*, Cambridge, 2015 ✓ | G–P | Erdős–Rényi, transición de fase, conexión, grafos aleatorios regulares | Referencia moderna de II.7 | Formal; poco sobre modelos de redes reales | Pago; versión gratuita en el sitio de Frieze |
| Martin C. Golumbic, *Algorithmic Graph Theory and Perfect Graphs*, Elsevier (2.ª ed., 2004) | G–P | Grafos perfectos, chordales, de intervalos | Base de II.9; citado en el seminario de posgrado de la UBA | Antiguo en notación, pero vigente | Pago |
| Michael R. Garey y David S. Johnson, *Computers and Intractability*, Freeman, 1979 | G | NP-completitud, catálogo de problemas | Reconocer problemas intratables (II.12) | No incluye avances posteriores (PCP, complejidad parametrizada) | Pago |
| Marek Cygan y coautores, *Parameterized Algorithms*, Springer, 2015 | G–P | FPT, kernelización, ancho de árbol | Base de II.10 | Exigente | Libre (versión de los autores) |

### C. Avanzado

| Obra | Nivel | Temas | Utilidad específica | Acceso |
| --- | --- | --- | --- | --- |
| Yufei Zhao, *Graph Theory and Additive Combinatorics: Exploring Structure and Randomness*, Cambridge, 2023 ✓ ([sitio](https://yufeizhao.com/gtacbook/)) | P | Teoría extremal, lema de regularidad, límites de grafos, métodos espectrales y combinatoria aditiva | La mejor puerta de entrada actual a la teoría extremal moderna (II.8); acompaña el curso del MIT con videos | Libre en el sitio del autor; impreso pago |
| László Lovász, *Large Networks and Graph Limits*, AMS Colloquium Publications 60, 2012 ✓ | P | Homomorfismos de grafos, límites de grafos densos (*graphons*) | Base teórica de la idea de "red muy grande" como objeto matemático | Pago |
| Béla Bollobás, *Random Graphs*, Cambridge (2.ª ed., 2001) | P | Grafos aleatorios en profundidad | Referencia clásica para II.7 | Pago |
| Neil Robertson y Paul Seymour, serie *Graph Minors* I–XX, *Journal of Combinatorial Theory, Series B*, 1983–2004 | P | Teorema de los menores | Fuente primaria de I.4; de lectura muy especializada | Acceso por suscripción |
| Andries Brandstädt, Van Bang Le y Jeremy Spinrad, *Graph Classes: A Survey*, SIAM, 1999 | P | Clases de grafos y relaciones entre ellas | Consulta enciclopédica de II.9 | Pago |

## D. Ciencia de redes

| Obra | Nivel | Utilidad específica | Fortalezas | Limitaciones | Acceso |
| --- | --- | --- | --- | --- | --- |
| Mark Newman, *Networks*, 2.ª ed., Oxford University Press, 2018 ✓ ([ficha](https://global.oup.com/academic/product/networks-9780198805090)) | G | El manual de referencia de la ciencia de redes; puente entre estructura, modelos y procesos dinámicos | Exposición clara aun en lo técnico; incluye comunidades, contagio complejo y redes multicapa | Perspectiva de física; poca teoría sociológica e inferencia estadística | Pago |
| Albert-László Barabási, *Network Science*, Cambridge University Press, 2016 ✓ ([libro libre](https://networksciencebook.com/)) | I–G | Introducción visual a redes complejas: estructura, evolución, difusión, modelos generativos | Libre bajo licencia Creative Commons; secciones avanzadas separadas; animaciones | Centrado en el grado y en la tesis libre de escala, que está discutida (IV.1); leer con Broido y Clauset (2019) | Libre (versión web) |
| David Easley y Jon Kleinberg, *Networks, Crowds, and Markets*, Cambridge University Press, 2010 ✓ ([borrador libre](https://www.cs.cornell.edu/home/kleinber/networks-book/)) | I | Conexión entre grafos, teoría de juegos, mercados, información y conducta estratégica | Sin prerrequisitos; capítulos sobre vínculos débiles, balance estructural, poder en negociación, cascadas | Poco riguroso en demostraciones; poco sobre datos reales y medición | Borrador completo libre |
| Eric D. Kolaczyk, *Statistical Analysis of Network Data*, Springer, 2009 (con Csárdi, *Statistical Analysis of Network Data with R*, 2.ª ed., 2020) | G | Estadística de redes: muestreo, modelos, inferencia | Cubre lo que la ciencia de redes suele omitir | Requiere estadística | Pago |
| Vito Latora, Vincenzo Nicosia y Giovanni Russo, *Complex Networks: Principles, Methods and Applications*, Cambridge, 2017 | G | Alternativa a Newman con más detalle en algunos modelos | Programas acompañantes | Misma perspectiva física | Pago |
| Aaron Clauset, Cosma Rohilla Shalizi y M. E. J. Newman, "Power-Law Distributions in Empirical Data", *SIAM Review*, 2009 | G | Cómo (no) ajustar leyes de potencias | Método estándar y crítica de prácticas erróneas | Específico | Libre en arXiv |
| Anna D. Broido y Aaron Clauset, "Scale-Free Networks Are Rare", *Nature Communications*, 2019 | G | Contrapeso empírico a la tesis libre de escala | Analiza casi mil redes | Debate abierto con réplicas | Libre (acceso abierto) |

## E. Sociología y redes sociales (con recursos en español)

### En español

| Recurso | Nivel | Utilidad específica | Fortalezas | Limitaciones | Acceso |
| --- | --- | --- | --- | --- | --- |
| *REDES. Revista Hispana para el Análisis de Redes Sociales* (Universitat Autònoma de Barcelona, desde 2002) \[ES\] ✓ ([DOAJ](https://doaj.org/toc/1579-0185); [archivo UAB](https://ddd.uab.cat/pub/redes/redes_a2004v6/vol6_1.htm)) | I–G | La revista de referencia del análisis de redes sociales en español y portugués; muchas aplicaciones latinoamericanas | Acceso abierto; artículos metodológicos y aplicados | Calidad variable entre números | Libre |
| Robert A. Hanneman y Mark Riddle, *Introducción a los métodos de análisis de redes sociales* (traducción del original de la Universidad de California en Riverside, 2005) \[ES\] ✓ ([LibreTexts en español](<https://espanol.libretexts.org/Bookshelves/Matematicas/Computacion_Cientifica_Simulaciones_y_Modelado/Libro%3A_Introducci%C3%B3n_a_los_m%C3%A9todos_de_redes_sociales_(Hanneman)>)) | I | Manual introductorio práctico de ARS: datos, centralidad, cohesión, equivalencia | Libre, en español, con ejemplos | Orientado a UCINET; no cubre modelos estadísticos modernos | Libre |
| José Luis Molina, *El análisis de redes sociales: una introducción*, Bellaterra, 2001 \[ES\] | I | Introducción breve escrita desde la antropología | Clara; perspectiva de ciencias sociales | Antigua en técnica | Pago |
| Larissa Adler de Lomnitz, *Cómo sobreviven los marginados*, Siglo XXI, 1975 \[ES\] | I | Clásico etnográfico sobre redes de intercambio recíproco (IV.6) | Muestra el valor de la etnografía de redes | No es metodología formal | Pago |
| Bruno Latour, *Reensamblar lo social*, Manantial, 2008 \[ES\] | G | Teoría del actor-red (V.2) | Crítica fundamental a la noción de "lo social" | No es análisis de redes en sentido técnico | Pago |

### Obras en inglés especialmente valiosas

| Obra | Nivel | Utilidad específica | Limitaciones | Acceso |
| --- | --- | --- | --- | --- |
| Stanley Wasserman y Katherine Faust, *Social Network Analysis: Methods and Applications*, Cambridge, 1994 ✓ | G | La referencia metodológica clásica: centralidad, equivalencia estructural, modelos de bloques, díadas y tríadas | Anterior a ERGM modernos y a datos digitales | Pago; en bibliotecas universitarias argentinas |
| Matthew O. Jackson, *Social and Economic Networks*, Princeton, 2008 ✓ | G | Formación estratégica de redes, difusión, aprendizaje, juegos en redes | Perspectiva económica; supuestos de racionalidad | Pago |
| Stephen P. Borgatti, Martin G. Everett, Jeffrey C. Johnson y Filip Agneessens, *Analyzing Social Networks Using R*, Sage, 2022 (sucesor de *Analyzing Social Networks*, 2013) | I–G | Manual práctico actualizado con R | Menos formal | Pago |
| Dean Lusher, Johan Koskinen y Garry Robins (eds.), *Exponential Random Graph Models for Social Networks*, Cambridge, 2013 | G–P | ERGM con teoría y aplicaciones (IV.7) | Especializado | Pago |
| Ronald S. Burt, *Structural Holes*, Harvard, 1992 | G | Fuente primaria de IV.3 | Ver críticas en IV.3 | Pago |
| Mustafa Emirbayer, "Manifesto for a Relational Sociology", *American Journal of Sociology*, 1997 | G | Base teórica de V.1 | Programático | Suscripción |
| Elisa Bellotti, *Qualitative Networks*, Routledge, 2015 | G | Métodos mixtos (V.6) | Específico | Pago |
| Linton C. Freeman, *The Development of Social Network Analysis*, Empirical Press, 2004 | I | Historia del campo (IV.1) | Centrado en Estados Unidos | Pago |

Artículos fundamentales citados en el Volumen IV (Granovetter 1973, Feld 1981, McPherson y coautores 2001, Centola y Macy 2007, Bonacich 1987, Cook y coautores 1983, Padgett y Ansell 1993, Moody y White 2003) completan esta sección; se recomienda leerlos en su versión original.

## F. Criminología y derechos humanos

| Obra o recurso | Nivel | Utilidad específica | Fortalezas | Limitaciones | Acceso |
| --- | --- | --- | --- | --- | --- |
| Carlo Morselli, *Inside Criminal Networks*, Springer, 2009 | G | El estudio más completo de redes criminales con datos de escuchas, incluido Caviar (VI.1) | Contrasta posición con rol; datos longitudinales | Datos policiales con su sesgo | Pago |
| Gisela Bichler, *Understanding Criminal Networks: A Research Guide*, University of California Press, 2019 | I–G | Manual metodológico para investigar redes criminales | Práctico; aborda problemas de datos | Enfoque angloamericano | Pago |
| Federico Varese, *Mafias on the Move*, Princeton, 2011 | G | Expansión territorial de mafias, con trabajo de campo | Combina estructura y contexto | No es metodología de redes | Pago |
| Donatella della Porta y Alberto Vannucci, *The Hidden Order of Corruption*, Ashgate, 2012 | G | Mecanismos de redes de corrupción (VI.2) | Teoría institucional de la corrupción | Pocos métodos formales | Pago |
| Johannes Wachs, Mihály Fazekas y János Kertész, "Corruption Risk in Contracting Markets: A Network Science Perspective" ✓ ([arXiv](https://arxiv.org/pdf/1909.08664)) | G | Modelo de análisis de riesgo de corrupción con datos abiertos (VI.2) | Modelo nulo; indicadores declarados como riesgo | No identifica casos individuales (por diseño) | Libre |
| Human Rights Data Analysis Group (HRDAG) ✓ ([sitio](https://hrdag.org/)) | G | Métodos estadísticos para derechos humanos: muestreo de archivos, enlace de registros, estimación por sistemas múltiples (VI.4) | Publicaciones técnicas y casos judiciales documentados | Muchos materiales en inglés | Libre |
| *Protocolo de Berkeley sobre Investigaciones Digitales de Fuentes Abiertas*, Centro de Derechos Humanos de la Universidad de California en Berkeley y Oficina del Alto Comisionado de las Naciones Unidas para los Derechos Humanos, 2020 \[ES disponible\] | I–G | Estándares de preservación, verificación y análisis de información digital (VI.6) | Guía reconocida internacionalmente | No específico de grafos | Libre |
| Amnistía Internacional, *Trapped in the Matrix*, 2018 ✓ ([resumen](https://www.amnesty.org.uk/london-trident-gangs-matrix-metropolitan-police)) | I | Caso documentado de daños por bases de "asociados" (VI.7) | Datos concretos y testimonios | Informe de incidencia, no académico | Libre |
| Jessica Saunders, Priscillia Hunt y John S. Hollywood, "Predictions Put into Practice", *Journal of Experimental Criminology*, 2016 ✓ ([RAND](https://www.rand.org/pubs/external_publications/EP67204.html)) | G | Evaluación de la lista de Chicago (VI.7) | Diseño cuasi-experimental | Un solo caso | Libre (resumen y versión de RAND) |
| Andrew V. Papachristos y Christopher Wildeman, "Network Exposure and Homicide Victimization in an African American Community", *American Journal of Public Health*, 2014 ✓ | G | Enfoque de salud pública sobre redes de violencia (VI.1) | Encuadre en víctimas | Datos de co-arresto | Libre (PMC) |
| Comisión Provincial por la Memoria (archivo de la DIPPBA) y Memoria Abierta \[ES\] | I | Acervos argentinos para investigación sobre la represión (VI.4) | Fuentes primarias | Acceso con condiciones según el fondo | Consulta institucional |

**Advertencia de uso.** Varias obras de esta sección tratan técnicas de análisis de redes criminales desde la perspectiva policial. Leerlas junto con los casos de daño de VI.7 y con la crítica de V.3 es parte de la formación, no un complemento opcional.

## G. Grafos de conocimiento y procedencia

| Obra o recurso | Nivel | Utilidad específica | Fortalezas | Limitaciones | Acceso |
| --- | --- | --- | --- | --- | --- |
| Aidan Hogan y coautores, *Knowledge Graphs*, Morgan & Claypool / Springer, 2021 (versión de revisión en *ACM Computing Surveys*, 2021) ✓ ([Springer](https://link.springer.com/book/9783031007903)) | G | La revisión de referencia de VII.1: modelos de datos, esquemas, razonamiento, calidad, aprendizaje | Exhaustiva y equilibrada entre RDF y grafos de propiedades | Extensa | Versión libre en arXiv (2003.02320) |
| W3C, *RDF 1.2 Concepts and Abstract Data Model* (Recomendación Candidata, abril de 2026) ✓ ([W3C](https://www.w3.org/TR/rdf12-concepts/)) | G | Términos tripleta para registrar afirmaciones atribuidas sin afirmarlas (VII.1) | Especificación primaria | Puede cambiar antes de ser Recomendación | Libre |
| W3C, *PROV-Overview* y familia PROV (PROV-DM, PROV-O, PROV-N, PROV-CONSTRAINTS), 2013 | G | El modelo de procedencia de VII.4 | Estándar estable | Abstracto; conviene leer primero el *PROV Primer* | Libre |
| W3C, *Shapes Constraint Language (SHACL)*, 2017 | G | Validación de grafos (VII.2) | Permite exigir fuentes en cada afirmación | Curva de aprendizaje | Libre |
| ISO/IEC 39075:2024, *GQL* ✓ ([IEC](https://webstore.iec.ch/publication/94107)) | G | Estándar de consulta de grafos de propiedades | Portabilidad entre bases | El texto del estándar es pago | Pago |
| Peter Christen, *Data Matching*, Springer, 2012 | G | Resolución de entidades (VII.3) | Completo y práctico | Anterior a métodos con aprendizaje profundo | Pago |
| Peter Buneman, Sanjeev Khanna y Wang-Chiew Tan, "Why and Where: A Characterization of Data Provenance", ICDT 2001; Todd J. Green, Grigoris Karvounarakis y Val Tannen, "Provenance Semirings", PODS 2007 | P | Fundamentos teóricos de la procedencia en bases de datos (VII.4, VII.6) | Formales y generales | Exigentes | Libres en sitios de los autores |
| Terence Anderson, David Schum y William Twining, *Analysis of Evidence*, Cambridge (2.ª ed., 2005) | G | Análisis de evidencia y diagramas de Wigmore (VII.5) | Puente entre derecho y razonamiento formal | Orientado al derecho anglosajón | Pago |
| Judea Pearl, Madelyn Glymour y Nicholas P. Jewell, *Causal Inference in Statistics: A Primer*, Wiley, 2016; Miguel A. Hernán y James M. Robins, *Causal Inference: What If*, CRC, 2020 | I–G | Grafos causales y d-separación (VII.7) | Introductorios y claros; el segundo es libre | No tratan interferencia en redes | Primer pago; *What If* libre en el sitio de los autores |
| Wil van der Aalst, *Process Mining: Data Science in Action*, Springer (2.ª ed., 2016); especificación OCEL 2.0 ✓ ([arXiv](https://arxiv.org/abs/2403.01975)) | G | Reconstrucción de procesos desde registros (VII.9, VII.11) | Herramientas abiertas (PM4Py) | Supone registros relativamente limpios | Libro pago; especificación libre |

## H. Algoritmos y programación (libros y software)

### Libros

| Obra | Nivel | Utilidad específica | Acceso |
| --- | --- | --- | --- |
| Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest y Clifford Stein, *Introduction to Algorithms*, MIT Press (4.ª ed., 2022) | G | Referencia de los algoritmos del Volumen III, con pruebas de corrección | Pago |
| Jon Kleinberg y Éva Tardos, *Algorithm Design*, Pearson, 2005 | G | Algoritmos de grafos, flujos y NP-completitud con énfasis en el modelado de problemas | Pago |
| Robert Sedgewick y Kevin Wayne, *Algorithms*, 4.ª ed., Addison-Wesley, 2011 | I–G | Implementaciones claras; materiales y videos en el sitio del libro | Pago; materiales libres en línea |
| Steven S. Skiena, *The Algorithm Design Manual*, Springer (3.ª ed., 2020) | G | Catálogo práctico para reconocer qué problema es el que se tiene | Pago |
| William L. Hamilton, *Graph Representation Learning*, Morgan & Claypool, 2020 ✓ ([borrador libre](https://www.cs.mcgill.ca/~wlh/grl_book/)) | G | Aprendizaje sobre grafos (VIII.1) | Borrador libre |

### Software abierto, priorizando Linux

| Herramienta | Lenguaje | Para qué | Fortalezas | Limitaciones |
| --- | --- | --- | --- | --- |
| NetworkX | Python | Exploración, enseñanza, prototipos; usada en el Volumen III para contrastar | Enorme cobertura de algoritmos; documentación excelente | Lenta para grafos de decenas de millones de aristas |
| igraph | Python, R, C | Análisis de redes medianas y grandes | Rápida; buen soporte de comunidades (Leiden) | API menos intuitiva |
| graph-tool | Python (núcleo en C++) | Grafos grandes; modelos de bloques estocásticos bayesianos (III.14, VIII.7) | Muy rápida; inferencia de Peixoto | Instalación más compleja |
| statnet (`ergm`, `network`, `sna`) | R | ERGM y estadística de redes (IV.7) | Estándar académico | Requiere R y estadística |
| RSiena | R | Modelos orientados al actor (IV.7) | Separa selección e influencia | Curva de aprendizaje alta |
| Gephi | Java (escritorio) | Visualización y exploración | Interactiva | Riesgo de leer visualizaciones como evidencia (V.5) |
| DuckDB | SQL | Tablas de aristas grandes y agregaciones | Rápida, sin servidor | No es una base de grafos |
| Neo4j Community, Memgraph | Cypher | Bases de grafos de propiedades (VII.1) | Consultas de patrones | Licencias a revisar para cada uso |
| Apache Jena (Fuseki), Oxigraph | SPARQL | Almacenes RDF (VII.1) | Estándares W3C | Rendimiento analítico limitado |
| pySHACL, `prov` (Python) | Python | Validación SHACL y modelos PROV (VII.2, VII.4) | Pequeñas y abiertas | Específicas |
| PM4Py | Python | Minería de procesos (VII.9) | Soporta OCEL | Requiere registros preparados |
| PyTorch Geometric, DGL | Python | Redes neuronales de grafos (VIII.1) | Amplia comunidad | Exigen GPU para escala |
| `grafos_ref.py` (entregado con el Volumen III) | Python | Implementaciones de referencia legibles con pruebas | Sin dependencias; pensada para estudiar | No pensada para rendimiento |

## I. Investigación contemporánea

Selección de revisiones y trabajos que sirven como puerta de entrada a cada frontera del Volumen VIII. Conviene leer primero las revisiones y después seguir las referencias.

| Trabajo | Frontera | Por qué leerlo | Acceso |
| --- | --- | --- | --- |
| Petter Holme y Jari Saramäki, "Temporal Networks", *Physics Reports*, 2012 | Grafos temporales (II.13) | Revisión fundacional del área | Libre en arXiv |
| Mikko Kivelä y coautores, "Multilayer Networks", *Journal of Complex Networks*, 2014 | Multicapa | Formalismo de referencia | Libre en arXiv |
| Federico Battiston y coautores, "Networks beyond Pairwise Interactions", *Physics Reports*, 2020; Christian Bick y coautores, "What Are Higher-Order Networks?", *SIAM Review*, 2023 ✓ ([arXiv](https://arxiv.org/abs/2104.11329v3)) | Orden superior (VIII.5) | Revisión amplia y clarificación conceptual | Libres en arXiv |
| Giulio Rossetti y Rémy Cazabet, "Community Discovery in Dynamic Networks: A Survey", *ACM Computing Surveys*, 2018 ✓ ([arXiv](https://arxiv.org/pdf/1707.03186)) | Comunidades dinámicas (VIII.6) | Clasificación de enfoques | Libre en arXiv |
| Santo Fortunato y Darko Hric, "Community Detection in Networks: A User Guide", *Physics Reports*, 2016 | Comunidades (III.14) | Guía crítica de uso | Libre en arXiv |
| Leto Peel, Daniel B. Larremore y Aaron Clauset, "The Ground Truth about Metadata and Community Detection in Networks", *Science Advances*, 2017 | Evaluación de comunidades | Teorema de "no hay almuerzo gratis" | Libre |
| Shenyang Huang y coautores, "Temporal Graph Benchmark for Machine Learning on Temporal Graphs", NeurIPS 2023 ✓ ([arXiv](https://arxiv.org/abs/2307.01026)) | Aprendizaje temporal (VIII.2) | Evaluación realista; líneas de base simples competitivas | Libre |
| Chirag Agarwal y coautores, "Evaluating Explainability for Graph Neural Networks", *Scientific Data*, 2023 ✓ ([GraphXAI](https://zitniklab.hms.harvard.edu/projects/GraphXAI)) | Explicabilidad (VIII.3) | Banco de prueba con explicaciones verdaderas | Libre |
| Elizabeth L. Ogburn y Tyler J. VanderWeele, "Causal Diagrams for Interference", *Statistical Science*, 2014 | Causalidad en redes (VIII.4) | Puente entre DAG e interferencia | Libre en arXiv |
| Tiago P. Peixoto, "Reconstructing Networks with Unknown and Heterogeneous Errors", *Physical Review X*, 2018 | Incertidumbre (VIII.7) | Reconstrucción bayesiana con errores por fuente | Libre (acceso abierto) |
| Haoyang Li y coautores, "Out-of-Distribution Generalization in Graph Foundation Models", arXiv, 2026 ✓ ([arXiv](https://arxiv.org/html/2601.21067)) | Modelos fundacionales (VIII.1) | Límites actuales | Libre |
| Darren Edge y coautores, "From Local to Global: A Graph RAG Approach to Query-Focused Summarization", arXiv, 2024 ✓ ([arXiv](https://arxiv.org/pdf/2404.16130)) | Grafos y LLM (VIII.8) | Arquitectura de referencia de GraphRAG | Libre |
| David Lazer y coautores, "Computational Social Science: Obstacles and Opportunities", *Science*, 2020; Matthew J. Salganik, *Bit by Bit*, Princeton, 2018 | Ciencias sociales computacionales (VIII.9) | Balance del campo y metodología | *Bit by Bit* libre en línea |
| Anna D. Broido y Aaron Clauset, "Scale-Free Networks Are Rare", *Nature Communications*, 2019 | Debate libre de escala (IV.1) | Ejemplo de revisión empírica de una tesis influyente | Libre |

## Catálogo de cursos, clases grabadas y videos

Se incluyen solo recursos cuya existencia y contenido se verificaron. Para los cursos en inglés se agrega una explicación de qué ofrecen, para decidir si vale la pena el esfuerzo del idioma.

### En español

| Recurso | Nivel | Prerrequisitos | Temas | Utilidad específica | Limitaciones | Acceso |
| --- | --- | --- | --- | --- | --- | --- |
| Universitat Politècnica de València, *Aplicaciones de la Teoría de Grafos a la Vida Real* (I y II), edX \[ES\] ✓ ([edX](https://edx.org/es/learn/math/universitat-politecnica-de-valencia-aplicaciones-de-la-teoria-de-grafos-a-la-vida-real-i)) | I | Ninguno | Modelado de problemas reales como grafos y algoritmos para resolverlos | El único curso en video en español de esta lista; bueno para la intuición algorítmica | Introductorio; no cubre redes sociales ni teoría avanzada | Auditoría gratuita habitual en edX; certificado pago (verificar condiciones vigentes) |
| Universidad de Buenos Aires, FCEN, Departamento de Computación, *Seminario de Posgrado de Teoría de Grafos* (programa 2021) \[ES\] ✓ ([programa](https://www.dc.uba.ar/wp-content/uploads/2021/09/Programa-Seminario-de-Posgrado-de-Teoria-de-grafos.pdf)) | P | Algoritmos y estructuras de datos | Grafos de intersección, clases definidas por subgrafos prohibidos, ancho de árbol y otros parámetros de ancho | Referencia local de nivel de investigación; su bibliografía es una lista de lectura para II.9 y II.10 | No hay clases grabadas; es un programa | Programa libre; cursada sujeta a inscripción |

### En inglés, especialmente valiosos

**MIT 18.217, *Graph Theory and Additive Combinatorics*, Yufei Zhao (otoño de 2019)** ✓ ([MIT OpenCourseWare](https://ocw.mit.edu/courses/18-217-graph-theory-and-additive-combinatorics-fall-2019)). Nivel P. Curso de posgrado completo con clases filmadas, apuntes y problemas. Cubre teoría extremal (Turán, Erdős-Stone), el lema de regularidad de Szemerédi y sus aplicaciones, límites de grafos, métodos espectrales y su relación con la combinatoria aditiva. Es el mejor complemento en video de II.8 y de la sección C de esta biblioteca, y se acompaña del libro de Zhao (libre). *Prerrequisitos:* demostraciones de nivel de grado, álgebra lineal y algo de probabilidad. *Limitación:* exigente; no trata aplicaciones. Hay una versión posterior, 18.225 (otoño de 2023), también en OpenCourseWare.

**Stanford CS224W, *Machine Learning with Graphs*, Jure Leskovec** ✓ ([clases de Leskovec](https://cs.stanford.edu/~jure/teaching.html); [diapositivas 2023](https://snap.stanford.edu/class/cs224w-2023/slides/02-tradition-ml.pdf)). Nivel G. Las clases de varias ediciones (por ejemplo, 2019 y 2021) están grabadas y publicadas por Stanford Online en YouTube. Cubre métodos clásicos de aprendizaje sobre grafos (características estructurales), incrustaciones de vértices, PageRank, GNN, grafos de conocimiento y modelos generativos. Es el curso de referencia para VIII.1. *Prerrequisitos:* Python, álgebra lineal, probabilidad y nociones de aprendizaje automático. *Limitación:* optimista sobre los métodos aprendidos; conviene verlo junto con VIII.1 y VIII.2, que discuten la evaluación.

**Coursera, *Social and Economic Networks: Models and Analysis*, Matthew O. Jackson (Stanford)** ✓ ([Coursera](https://www.coursera.org/learn/social-economic-networks/home/info)). Nivel I–G. Video del autor del libro de la sección E: medición de redes, modelos de formación aleatorios y estratégicos, difusión, aprendizaje y juegos en redes, incluidos ERGM y modelos de bloques. *Prerrequisitos:* matemática de grado básica. *Limitación:* perspectiva económica. *Acceso:* auditoría gratuita habitual; verificar condiciones vigentes.

**Albert-László Barabási, *Network Science* (libro en línea con videos)** ✓ ([sitio](https://networksciencebook.com/)). Nivel I. El libro en línea incluye animaciones y videos de modelos dinámicos. Útil como primer contacto visual con la ciencia de redes; con las cautelas de IV.1 sobre la tesis libre de escala.

### Otros espacios de formación

- **Talleres de la International Network for Social Network Analysis (INSNA)**, que se dictan en la conferencia anual Sunbelt: cursos breves sobre ERGM, SAOM (RSiena), análisis de redes egocéntricas y métodos mixtos, a cargo de los desarrolladores de las herramientas.
- **Materiales de statnet**: tutoriales de ERGM y del paquete `network` publicados por el equipo de desarrollo.
- **Escuelas de verano en ciencia de redes y en ciencias sociales computacionales** (por ejemplo, las Summer Institutes in Computational Social Science), con materiales y videos públicos en varias ediciones.

Estos últimos se mencionan como espacios a buscar; sus ediciones y materiales cambian cada año y no se verificaron uno por uno.

## Orden recomendado de lectura y visualización

No es un calendario: son tres secuencias de dependencia, coherentes con el mapa del Volumen 0 y con los itinerarios del Volumen X. Cada paso supone el anterior; dentro de un paso, el orden es libre.

**Secuencia 1: formal.**

1. Diestel, capítulos 1 a 3 (libres en el sitio) o West, capítulos 1 a 4.
2. Diestel, capítulos 4 a 6 (planaridad, coloración, flujos), con Bondy y Murty como alternativa más algorítmica.
3. Chung o Brouwer y Haemers para lo espectral; Frieze y Karoński para grafos aleatorios.
4. Zhao (libro y curso 18.217 del MIT) para teoría extremal moderna.
5. Cygan y coautores, y Golumbic, para complejidad parametrizada y clases de grafos.
6. Lovász, *Large Networks and Graph Limits*, como cierre de nivel de investigación.

**Secuencia 2: social e institucional.**

1. Hanneman y Riddle en español, o Easley y Kleinberg capítulos 1 a 5.
2. Wasserman y Faust por temas, con los artículos clásicos de IV (Granovetter, Burt, Feld, Bonacich).
3. Newman, partes I a III, para el lenguaje de la ciencia de redes, y Broido y Clauset como contrapeso.
4. Lusher, Koskinen y Robins (ERGM) y materiales de RSiena para inferencia.
5. Emirbayer, Erikson y Latour para la teoría relacional; Bellotti para métodos mixtos.
6. Morselli, Varese, della Porta y Vannucci, y los materiales de HRDAG para aplicaciones; Amnistía Internacional y RAND para los casos de daño.

**Secuencia 3: temporal, procedencia y sistemas.**

1. Cormen y coautores, o Kleinberg y Tardos, para los algoritmos del Volumen III.
2. Holme y Saramäki para grafos temporales.
3. Hogan y coautores para grafos de conocimiento; familia W3C PROV y SHACL.
4. Christen para resolución de entidades; Pearl, Glymour y Jewell, y Hernán y Robins, para causalidad.
5. Van der Aalst y OCEL 2.0 para reconstrucción de procesos.
6. Hamilton y el curso CS224W para aprendizaje sobre grafos, seguidos de los trabajos de evaluación de VIII.2 (TGB) y VIII.3 (GraphXAI).

**Si hubiera que elegir solo tres para empezar:** los capítulos 1 a 3 de Diestel (libres), Hanneman y Riddle en español (libre) y el artículo de Broido y Clauset (libre). Cubren el núcleo formal, el núcleo sociológico y un ejemplo de crítica empírica, sin costo.
