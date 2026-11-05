# Teoría de grafos — Volumen VIII: Fronteras de investigación y problemas abiertos

Nov 5, 2026 · @Anna Tchijova

## Cómo leer este volumen: criterios para evaluar técnicas nuevas

Las fronteras de investigación cambian rápido, y la literatura reciente sobre grafos (sobre todo la de aprendizaje automático) se publica mayoritariamente en conferencias y preprints con incentivos a reportar mejoras. Este volumen describe el estado del campo verificado al 5 de noviembre de 2026, pero su objetivo principal es dar **criterios para leer esa literatura con sentido crítico**, porque el estado del arte de hoy será otro en dos años.

**Cinco preguntas ante cualquier técnica nueva.**

1. **¿Contra qué línea de base se comparó?** Una mejora sobre otro modelo complejo no dice nada si una heurística simple (el grado, los vecinos comunes, repetir lo que pasó antes) rinde igual. La historia reciente del aprendizaje sobre grafos tiene varios casos en que las líneas de base simples, bien evaluadas, igualaron a modelos sofisticados (VIII.1, VIII.2).
2. **¿El protocolo de evaluación corresponde al uso real?** Por ejemplo, en grafos temporales, evaluar con divisiones aleatorias en lugar de cronológicas filtra información del futuro.
3. **¿Qué supuestos necesita?** Observaciones independientes, grafo completo, etiquetas confiables, homofilia. Si los datos de investigación social no los cumplen, el resultado no se transfiere.
4. **¿Qué tipo de garantía ofrece?** Teorema, resultado empírico en ciertos conjuntos de datos o heurística (Volumen II.11). La mayoría de los métodos de aprendizaje ofrecen lo segundo.
5. **¿Se puede auditar y explicar su salida?** En investigación con consecuencias sobre personas (VI), un método que no permite reconstruir por qué produjo un resultado tiene un costo que no aparece en las tablas de precisión.

**Principio del volumen.** Una técnica reciente no es necesariamente superior. Para cada área se presentan también las alternativas no basadas en aprendizaje automático y cuándo conviene preferirlas.

## VIII.1 Aprendizaje de representaciones y redes neuronales de grafos

**El problema.** Muchas tareas (clasificar vértices, predecir aristas, clasificar grafos enteros) requieren convertir la estructura en vectores que un modelo pueda usar. El **aprendizaje de representaciones** (*graph representation learning*) aprende esos vectores a partir de los datos. Referencia de estudio: Hamilton, *Graph Representation Learning* (Morgan & Claypool, 2020; borrador gratuito del autor). Para el marco general: Bronstein, Bruna, Cohen y Veličković, *Geometric Deep Learning: Grids, Groups, Graphs, Geodesics, and Gauges* (arXiv, 2021).

**Dos generaciones.**

- **Incrustaciones por caminatas aleatorias.** DeepWalk (Perozzi, Al-Rfou y Skiena, KDD 2014) y node2vec (Grover y Leskovec, KDD 2016) generan caminatas aleatorias y aplican a esas secuencias técnicas de modelado del lenguaje: vértices que aparecen en contextos parecidos reciben vectores parecidos. Se mostró después que estos métodos factorizan implícitamente matrices derivadas de la adyacencia, de modo que tienen parentesco directo con los métodos espectrales (II.6).
- **Redes neuronales de grafos** (GNN, *graph neural networks*). En cada capa, cada vértice combina su vector con los de sus vecinos (**paso de mensajes**). Variantes: GCN (Kipf y Welling, ICLR 2017), GraphSAGE (Hamilton, Ying y Leskovec, NeurIPS 2017), GAT con atención (Veličković y coautores, ICLR 2018).

**\[Teo\] Límite de expresividad.** Xu, Hu, Leskovec y Jegelka ("How Powerful are Graph Neural Networks?", ICLR 2019) y, de forma independiente, Morris y coautores (AAAI 2019) demostraron que las GNN de paso de mensajes no pueden distinguir más grafos que el test de isomorfismo de Weisfeiler-Leman de una dimensión (1-WL). Consecuencia concreta: hay pares de grafos no isomorfos que ninguna de estas GNN distingue; por ejemplo, un ciclo de seis vértices y dos triángulos disjuntos (el contraejemplo de I.4) reciben la misma representación, porque todos sus vértices tienen grado 2 y vecindarios localmente idénticos. Hay arquitecturas más expresivas (de orden superior, con características de subgrafos), a mayor costo.

**Problemas conocidos.**

- **Suavizado excesivo** (*oversmoothing*): con muchas capas, las representaciones de todos los vértices convergen (Li, Han y Wu, AAAI 2018). Tiene la misma raíz que la convergencia de las caminatas aleatorias a la distribución estacionaria (II.6).
- **Compresión excesiva** (*oversquashing*): la información de vértices lejanos tiene que pasar por cuellos de botella y se pierde (Alon y Yahav, ICLR 2021). Se relaciona con la curvatura y la constante isoperimétrica del grafo (II.6, II.7).
- **Heterofilia:** las GNN clásicas suponen implícitamente que los vecinos se parecen (homofilia, IV.2). Platonov y coautores ("A Critical Look at the Evaluation of GNNs under Heterophily", ICLR 2023) mostraron problemas en los conjuntos de datos estándar usados para evaluar métodos heterofílicos, que afectaban las conclusiones de trabajos previos.
- **Evaluación de predicción de aristas:** Li y coautores ("Evaluating Graph Neural Networks for Link Prediction: Current Pitfalls and New Benchmarking", NeurIPS 2023) documentaron problemas de evaluación (muestreo de negativos poco realista, hiperparámetros desiguales) que inflaban las ventajas reportadas.

**Modelos fundacionales de grafos.** Desde 2023 se busca entrenar modelos grandes sobre muchos grafos para transferirlos a tareas nuevas, por analogía con los modelos de lenguaje. Las revisiones recientes (por ejemplo, Li, Chen, Wang y Zhu, "Out-of-Distribution Generalization in Graph Foundation Models", arXiv, 2026) señalan obstáculos que siguen abiertos: los grafos de dominios distintos difieren tanto en estructura que el preentrenamiento conjunto puede producir transferencia negativa; las garantías teóricas existentes suponen datos independientes e idénticamente distribuidos; y faltan bancos de prueba realistas fuera de distribución. **\[Hip\]** Es una línea de investigación activa, no una tecnología madura.

**Alternativas no basadas en aprendizaje y cuándo preferirlas.** Para predicción de aristas, heurísticas como vecinos comunes, Adamic-Adar o Katz (III.13) son líneas de base fuertes y explicables. Para clasificación con pocos datos, la propagación de etiquetas o las características estructurales explícitas (grado, agrupamiento, centralidades) con un modelo lineal suelen ser competitivas e interpretables. Para investigación social con consecuencias sobre personas, la explicabilidad y la auditabilidad de estas alternativas valen a menudo más que unos puntos de precisión.

## VIII.2 Aprendizaje sobre grafos temporales

**El problema.** Predecir aristas futuras (quién interactuará con quién), propiedades futuras de vértices o la evolución de la estructura, a partir de flujos de enlaces fechados (II.13).

**Modelos.** Dos enfoques: modelos de tiempo discreto, que procesan secuencias de instantáneas combinando una GNN con una red recurrente; y modelos de tiempo continuo, que procesan eventos individuales y mantienen una "memoria" por vértice, como TGN (Rossi y coautores, *Temporal Graph Networks*, arXiv, 2020), JODIE, DyRep o TGAT.

**\[Emp\] La lección de la evaluación.** Poursafaei, Huang, Pelrine y Rabbany ("Towards Better Evaluation for Dynamic Link Prediction", NeurIPS 2022, sección de conjuntos de datos y bancos de prueba) propusieron **EdgeBank**, una línea de base sin aprendizaje que predice que volverá a ocurrir una arista si ya ocurrió antes. EdgeBank resultó sorprendentemente competitiva con los modelos publicados bajo los protocolos de evaluación de entonces, porque esos protocolos elegían ejemplos negativos demasiado fáciles. Propusieron muestreos de negativos más exigentes (incluyendo aristas que existieron en el pasado pero no en el momento evaluado).

El **Temporal Graph Benchmark** (TGB; Huang, Poursafaei, Danovitch, Fey, Hu, Rossi, Leskovec, Bronstein, Rabusseau y Rabbany, NeurIPS 2023, sección de conjuntos de datos y bancos de prueba) ofreció conjuntos de datos grandes de varios años (redes sociales, de comercio, de transacciones y de transporte) con protocolos realistas y tablas públicas de resultados. Sus hallazgos: el rendimiento de los modelos varía mucho entre conjuntos de datos, y en predicción de propiedades de vértices, métodos simples a menudo superaron a los modelos temporales existentes.

**Lectura.** El patrón es general en este campo: la mejora reportada de un modelo complejo puede desaparecer con una evaluación más cuidadosa. Los datos temporales tienen mucha **repetición** (las personas vuelven a hablar con las mismas personas; las empresas vuelven a contratar con los mismos proveedores), y cualquier método que la capture bien es difícil de superar.

**Alternativas no basadas en aprendizaje.** Las líneas de base de repetición y recencia (EdgeBank y variantes con ventanas), los modelos estadísticos de eventos relacionales (REM, IV.7), que además permiten interpretar parámetros como reciprocidad o inercia, y los modelos de procesos puntuales (procesos de Hawkes) para la dinámica de eventos. Para investigación social, los REM y los modelos orientados al actor (SAOM) tienen la ventaja de estimar mecanismos con incertidumbre, no solo de predecir.

## VIII.3 Explicabilidad en algoritmos de grafos

**Dos problemas distintos que se confunden.**

1. **Explicar algoritmos clásicos.** Por qué un vértice tiene alta intermediación, por qué dos vértices quedaron en la misma comunidad. Aquí la explicación es exacta en principio: se pueden listar los caminos mínimos que pasan por el vértice o las aristas internas que sostienen la comunidad. El problema es de comunicación y de escala, no de método.
2. **Explicar modelos aprendidos.** Por qué una GNN clasificó un vértice como sospechoso. Aquí el modelo no tiene una razón legible, y la explicación es otra aproximación.

**Métodos para GNN.** GNNExplainer (Ying, Bourgeois, You, Zitnik y Leskovec, NeurIPS 2019) busca el subgrafo y las características que más influyen en una predicción, optimizando una máscara. Le siguieron PGExplainer, SubgraphX y muchos otros, más explicaciones contrafácticas ("el cambio mínimo en el grafo que habría cambiado la predicción").

**El problema de la evaluación.** Sin explicaciones verdaderas conocidas, no se puede saber si un explicador acierta. Agarwal, Queen, Lakkaraju y Zitnik ("Evaluating Explainability for Graph Neural Networks", *Scientific Data*, 2023) construyeron por eso ShapeGGen, un generador de grafos sintéticos con explicaciones verdaderas incorporadas y parámetros controlables (tamaño, distribución de grados, homofilia o heterofilia), y la biblioteca GraphXAI para evaluar explicadores contra ellas. La necesidad misma de ese trabajo es la lección: durante años los explicadores se evaluaron con pocos conjuntos de datos sintéticos simples, de modo que su fiabilidad en datos reales no estaba establecida.

**Advertencias epistemológicas.**

- Una explicación de una GNN describe el **modelo**, no el **mundo**. Que el modelo se apoye en cierta arista no significa que esa relación sea causalmente relevante para el fenómeno.
- Las explicaciones pueden ser inestables: pequeños cambios en el grafo o en la semilla de entrenamiento cambian el subgrafo explicativo.
- Una explicación convincente puede producir confianza injustificada en un modelo equivocado. En contextos de VI, una "explicación" que señala los vínculos de una persona como causa de una puntuación de riesgo reproduce la culpa por asociación con apariencia técnica.

**Alternativa preferible cuando hay consecuencias sobre personas.** Modelos interpretables por construcción: reglas explícitas sobre características estructurales nombradas, modelos estadísticos con parámetros interpretables (ERGM, SAOM, REM), o puntuaciones simples cuya fórmula se publica. Rudin ("Stop Explaining Black Box Machine Learning Models for High Stakes Decisions and Use Interpretable Models Instead", *Nature Machine Intelligence*, 2019) desarrolló este argumento para decisiones de alto impacto en general.

## VIII.4 Descubrimiento causal e inferencia causal en redes

**Por qué es una frontera.** La inferencia causal clásica (VII.7) supone que las unidades no se afectan entre sí. En redes, el tratamiento de una persona afecta a otras (**interferencia**), y las observaciones están conectadas por la propia red. Además, la red puede ser a la vez causa y efecto de las conductas (selección e influencia, IV.4).

**Líneas activas.**

- **Diagramas causales con interferencia.** Ogburn y VanderWeele ("Causal Diagrams for Interference", *Statistical Science*, 2014) extendieron los DAG para representar efectos de contagio, de exposición y de alocación entre unidades conectadas. Muestran que, en presencia de contagio, la red entera es una sola unidad de observación dependiente, lo que complica la inferencia estadística con una sola red.
- **Experimentos en redes.** Diseños aleatorizados por grupos de vértices (*cluster randomization*) para limitar la contaminación entre tratados y no tratados, y estimadores con mapeos de exposición (Aronow y Samii, IV.4). Su frontera es diseñar los grupos sin conocer completamente la red.
- **Inferencia con una sola red observada.** Cuando solo se tiene una red (el caso habitual en ciencias sociales), la teoría asintótica estándar no se aplica directamente. Hay resultados bajo supuestos de dependencia débil o de "vecindarios" acotados, pero el área está lejos de estar cerrada.
- **Descubrimiento causal con datos dependientes.** Los algoritmos de VII.7 (PC, FCI) suponen observaciones independientes. Adaptarlos a datos relacionales (donde la variable de una unidad depende de las de sus vecinos) es un problema abierto; hay propuestas para modelos relacionales, pero con supuestos fuertes.
- **Separar selección de influencia en datos longitudinales.** Los SAOM (IV.7) son la herramienta más usada en sociología; su validez depende de la especificación del modelo y de que las olas de observación capturen la dinámica.

**Advertencia.** Ningún método actual permite extraer causalidad de una sola red transversal sin supuestos fuertes. Cuando un trabajo afirma haberlo hecho, la pregunta es qué supuestos usó y si son plausibles para ese fenómeno.

**Alternativa no algorítmica.** Los experimentos naturales (cambios exógenos en la red, como reasignaciones aleatorias de compañeros, mudanzas forzadas o cambios institucionales) y el razonamiento cualitativo sobre mecanismos, documentado con evidencia independiente. En investigación histórica e institucional, la combinación de estructura con documentos (como Padgett y Ansell, IV.6) sigue siendo la vía más sólida para sostener afirmaciones causales.

## VIII.5 Redes de orden superior y multicapa

**Estado del campo.** Tras la revisión de Battiston y coautores (2020, II.14), el área se consolidó. Una referencia conceptual especialmente útil es Bick, Gross, Harrington y Schaub ("What Are Higher-Order Networks?", *SIAM Review*, 2023), que examina qué significa "orden superior" y cuándo hace falta. En la línea de esa revisión, conviene distinguir al menos tres usos del término, que no requieren las mismas herramientas:

1. **Interacciones de grupo** como objeto de los datos (hipergrafos, complejos simpliciales).
2. **Dinámicas no aditivas** sobre una red de pares (por ejemplo, un umbral que requiere dos vecinos, IV.4): el orden superior está en la **dinámica**, no en los datos.
3. **Dependencias de camino** (la próxima arista depende de las anteriores, no solo del vértice actual): orden superior en el **flujo**, que se modela con redes de memoria.

La distinción importa: tener datos de grupos no obliga a usar dinámicas de grupo, y una dinámica de grupo puede ocurrir sobre datos de pares.

**Frontera abierta.**

- **Reconstrucción:** dado un registro de interacciones de pares, ¿se puede inferir si hubo interacciones de grupo? Hay métodos bayesianos (Young, Petri y Peixoto, "Hypergraph Reconstruction from Network Data", *Communications Physics*, 2021), pero el problema está mal planteado sin supuestos: muchos hipergrafos producen la misma proyección (II.14).
- **Modelos nulos para hipergrafos:** equivalentes del modelo de configuración que preserven grados y tamaños de hiperaristas, para saber qué es llamativo.
- **Topología algebraica aplicada:** la homología persistente detecta "agujeros" en complejos simpliciales; su interpretación sociológica sigue siendo discutida.
- **Multicapa:** detección de comunidades consistentes entre capas, medidas de centralidad multicapa (cuánto importa un actor considerando todas sus relaciones a la vez) y el problema de cuánto peso dar a las aristas entre capas, que en la práctica se elige y cambia los resultados.

**Lectura para investigación social.** La formalización de orden superior responde a un reclamo antiguo de la sociología (Simmel y la tríada; Breiger y la dualidad persona–grupo): las relaciones de grupo no se reducen a pares. Lo nuevo no es la idea sino los instrumentos. La recomendación práctica de II.14 sigue en pie: conservar los datos de grupo y no proyectar sin justificación.

## VIII.6 Detección de comunidades dinámicas

**El problema.** Seguir comunidades a lo largo del tiempo: cómo nacen, crecen, se fusionan, se dividen y desaparecen. Rossetti y Cazabet ("Community Discovery in Dynamic Networks: A Survey", *ACM Computing Surveys*, 2018) clasificaron los enfoques en tres familias.

| Familia | Cómo trabaja | Ventaja | Problema |
| --- | --- | --- | --- |
| Instantánea por instantánea, luego emparejamiento | Detectar comunidades en cada ventana y emparejarlas entre ventanas por similitud | Simple, reutiliza métodos estáticos | Inestabilidad: la heurística da particiones distintas en ventanas casi iguales, y se "ven" eventos que son ruido del algoritmo |
| Con suavizado temporal | La partición de cada ventana se penaliza si difiere mucho de la anterior (por ejemplo, modularidad multicapa de Mucha y coautores, II.13) | Más estable | El parámetro de acoplamiento decide cuánto cambio se acepta |
| Sobre el flujo de eventos completo | Actualizar comunidades evento por evento | Usa toda la información temporal | Costo y complejidad; menos herramientas maduras |

**Los eventos de la vida de una comunidad** (nacimiento, crecimiento, contracción, fusión, división, muerte, reaparición) son en sí mismos una **interpretación** de cambios en una sucesión de particiones heurísticas. Antes de narrar que "el grupo A se dividió", hay que comprobar que la división es estable frente a semillas y parámetros, y que no se debe a cambios en la cobertura de los datos (VII.10, VII.11).

**Frontera.** Bancos de prueba con dinámica conocida (redes sintéticas con eventos plantados), medidas de estabilidad temporal, y métodos estadísticos de bloques dinámicos (versiones dinámicas del SBM) que permitan decidir con fundamento si un cambio es real.

**Alternativa.** En investigación social, combinar la estructura con fuentes que documenten los eventos (una escisión registrada, una fusión de empresas, un cambio de autoridades) y usar la detección como exploración. Lo que el método puede aportar de forma confiable es la señal de dónde mirar, no la narración del cambio.

## VIII.7 Incertidumbre y grafos probabilísticos

**El cambio de enfoque.** La literatura reciente propone tratar la red observada no como el objeto de estudio sino como una **medición ruidosa** de una red latente, e inferir la red latente junto con la incertidumbre. Es la extensión natural de II.15 y la respuesta más rigurosa a la crítica de V.5 (errores 4 y 6).

**Líneas activas.**

- **Reconstrucción bayesiana de redes.** Newman (*Nature Physics*, 2018, II.15) y Peixoto ("Reconstructing Networks with Unknown and Heterogeneous Errors", *Physical Review X*, 2018) estiman la red latente a partir de mediciones repetidas o heterogéneas, junto con las tasas de error de cada fuente. Young, Cantwell y Newman ("Bayesian Inference of Network Structure from Unreliable Data", *Journal of Complex Networks*, 2020) dan una introducción accesible. El resultado no es un grafo sino una **distribución** sobre grafos, y las métricas se reportan con intervalos.
- **Propagación de la incertidumbre a las métricas.** Calcular centralidades, comunidades o caminos sobre muestras de la distribución posterior, en lugar de sobre un grafo único. Es costoso, pero es la única forma honesta de reportar "el actor A es el más central con probabilidad 0,6".
- **Resolución de entidades probabilística integrada.** Modelos que infieren a la vez qué registros son la misma persona y la estructura de la red, en lugar de resolver primero las entidades y después tratar el resultado como dado. En estadística, Steorts, Hall y Fienberg ("A Bayesian Approach to Graphical Record Linkage and Deduplication", *Journal of the American Statistical Association*, 2016) desarrollaron un modelo bayesiano de enlace de registros que propaga la incertidumbre de la identidad a los análisis posteriores.
- **Bases de datos probabilísticas** y consultas sobre grafos inciertos: la dificultad computacional (#P-completitud, II.15) obliga a aproximaciones por muestreo con garantías.

**Problema abierto central.** Los modelos de medición necesitan supuestos sobre cómo se generan los errores. En datos administrativos y policiales, los errores no son aleatorios (dependen de quién registra, de dónde y de por qué), y modelar ese sesgo exige conocimiento del proceso institucional de producción de datos. Aquí la sociología de las fuentes (V.3) es un insumo técnico, no solo una crítica.

**Alternativa más simple.** Cuando un modelo bayesiano completo no es viable, el análisis de sensibilidad sistemático (V.6) da buena parte del beneficio: perturbar el grafo según escenarios plausibles de error y reportar qué conclusiones sobreviven.

## VIII.8 Bases de grafos a gran escala y grafos con modelos de lenguaje

### Bases de grafos a gran escala

**Estado.** El mercado incluye bases de grafos de propiedades (Neo4j, Memgraph, TigerGraph, Amazon Neptune, ArangoDB), almacenes RDF (Virtuoso, GraphDB, Apache Jena, Oxigraph, QLever) y extensiones de bases relacionales con consultas de grafo (el estándar SQL/PGQ, parte de SQL:2023, permite consultar grafos de propiedades definidos sobre tablas). La estandarización de GQL (ISO/IEC 39075:2024, VII.1) busca que las consultas sean portables entre productos. El Consejo de Evaluación de Datos Enlazados (LDBC) mantiene bancos de prueba auditados, como el *Social Network Benchmark*, que conviene consultar antes de creer en comparaciones de rendimiento publicadas por los propios fabricantes.

**\[Emp\] Lo que los usuarios encuentran difícil.** Sahu y coautores ("The Ubiquity of Large Graphs and Surprising Challenges of Graph Processing", *Proceedings of the VLDB Endowment*, 2017) encuestaron a usuarios de grafos en la industria y la academia: los desafíos más mencionados fueron la escalabilidad y, de forma notable, la visualización, la limpieza de datos y la ausencia de herramientas para tareas de preparación, más que la falta de algoritmos.

**Frontera.** Consultas sobre grafos temporales y versionados ("¿qué caminos existían en tal fecha?"); procesamiento incremental sobre flujos; consultas con incertidumbre; y combinación de recorridos de grafo con búsqueda vectorial.

**Advertencia práctica.** Muchos proyectos de investigación no necesitan una base de grafos: con algunos millones de aristas, NetworkX, igraph o graph-tool en memoria, o DuckDB con tablas de aristas, alcanzan. Una base de grafos agrega valor cuando hay consultas interactivas de patrones, actualizaciones concurrentes o equipos no técnicos que exploran (VI.3).

### Grafos y modelos de lenguaje

Los modelos de lenguaje de gran escala (LLM) entraron al área de dos maneras.

- **Construcción de grafos a partir de texto.** Extraer entidades y relaciones de documentos con un LLM para poblar un grafo de conocimiento. Es muy útil para escalar el trabajo, y muy riesgoso para la evidencia: el modelo puede inventar relaciones que no están en el texto, fusionar entidades homónimas o normalizar formulaciones de un modo que cambia su sentido. **Cada arista extraída por un LLM es una inferencia** (VII.4) y debe llevar la referencia al fragmento de texto del que se extrajo, para poder verificarla.
- **Recuperación aumentada con grafos.** GraphRAG (Edge y coautores, "From Local to Global: A Graph RAG Approach to Query-Focused Summarization", Microsoft Research, arXiv, 2024) construye un grafo de entidades a partir de un corpus, detecta comunidades en él, genera resúmenes por comunidad y los usa para responder preguntas globales sobre el corpus. Pan y coautores ("Unifying Large Language Models and Knowledge Graphs: A Roadmap", *IEEE Transactions on Knowledge and Data Engineering*, 2024) revisan las formas de integración.

**Lectura crítica para investigación.** GraphRAG usa detección de comunidades (Leiden) como paso intermedio: hereda todas sus limitaciones (III.14), y los resúmenes de comunidad pueden presentar como "tema" o "grupo" lo que es una partición heurística. Para trabajo con valor probatorio, el LLM puede servir para **proponer** aristas y resúmenes, pero la verificación contra las fuentes y el registro de procedencia no son opcionales. Y no corresponde atribuir al modelo comprensión ni intención: produce texto plausible condicionado por su entrada.

## VIII.9 Grafos en ciencias sociales computacionales

**El programa.** Lazer y coautores ("Computational Social Science", *Science*, 2009) anunciaron un campo basado en las huellas digitales de la interacción humana. Once años después, Lazer y coautores ("Computational Social Science: Obstacles and Opportunities", *Science*, 2020) hicieron un balance: los avances fueron reales, pero el campo enfrenta obstáculos estructurales de acceso a datos, de incentivos académicos y de ética. Salganik, *Bit by Bit: Social Research in the Digital Age* (Princeton, 2018, con versión gratuita en línea), es la mejor introducción metodológica, con capítulos sobre observación, encuestas, experimentos y ética.

**Frontera 1: acceso a datos.** Las redes sociales digitales son la fuente de datos relacionales más grande de la historia, y el acceso de investigadores depende de decisiones empresariales que cambian sin aviso: varias plataformas restringieron o encarecieron sus interfaces de datos para investigación en los últimos años, y estudios enteros dejaron de ser replicables. En la Unión Europea, el artículo 40 de la Ley de Servicios Digitales (DSA) creó un derecho de acceso para investigadores verificados a datos de plataformas y buscadores de muy gran tamaño; la Comisión Europea adoptó en julio de 2025 el acto delegado que regula ese acceso. Es un cambio institucional relevante, pero su alcance práctico (qué datos, con qué demora, para qué investigadores fuera de la Unión) está todavía en construcción.

**Frontera 2: validez de las huellas digitales.** Los datos de plataformas son **producidos por algoritmos** (el feed decide qué ve cada persona, y por lo tanto con quién interactúa) y por poblaciones no representativas. Una red de seguidores no es una red social en el sentido de IV: es en parte el producto de un sistema de recomendación. Separar la conducta humana de la conducta inducida por la plataforma es un problema metodológico abierto, y conecta con la performatividad de Healy (V.2).

**Frontera 3: medición de polarización y cámaras de eco.** Un tema donde los grafos son centrales y la evidencia es discutida: algunos estudios encuentran segregación fuerte en redes de interacción política en línea, y otros encuentran que la exposición a contenido diverso es mayor de lo que sugiere la metáfora. Las diferencias dependen en buena medida de qué se mide (seguidores, interacciones, exposición real), de la plataforma y del país. Es un buen caso de estudio de cómo la operacionalización (V.3) determina la conclusión.

**Frontera 4: ética.** El experimento de 61 millones de personas (IV.4) y otros experimentos masivos en plataformas sin consentimiento explícito abrieron debates que no están cerrados. Los principios del informe Belmont (respeto por las personas, beneficencia, justicia) se aplican, pero su traducción a datos relacionales (donde cada persona aporta datos de otras) requiere desarrollos propios (VI.8).

**Frontera 5: integración cualitativa a escala.** Combinar el alcance de los datos digitales con la profundidad de la etnografía y del análisis documental. Los modelos de lenguaje prometen escalar la codificación cualitativa, con las cautelas de VIII.8 sobre verificación.

**Alternativa sólida.** Encuestas de redes bien diseñadas (generadores de nombres, como en el General Social Survey de Estados Unidos), estudios longitudinales de redes completas en organizaciones o escuelas, y archivos institucionales con crítica de fuentes. Son más chicos, pero sus datos tienen un proceso de producción conocido.

## VIII.10 Problemas abiertos y preguntas de investigación

Este es el entregable 10. Se divide en problemas matemáticos abiertos (con enunciado preciso y estado conocido) y preguntas de investigación aplicada (abiertas en el sentido de que no hay consenso ni método establecido). Las primeras sirven para conocer los límites del conocimiento formal; las segundas son posibles líneas de trabajo propio.

### A. Problemas matemáticos abiertos

| Problema | Enunciado | Estado conocido | Conecta con |
| --- | --- | --- | --- |
| Conjetura de Hadwiger (1943) | Todo grafo sin menor K\_t es (t − 1)-coloreable | Demostrada para t ≤ 6 (el caso t = 5 equivale al teorema de los cuatro colores; t = 6, Robertson, Seymour y Thomas, 1993); abierta en general | I.4, I.7 |
| Conjetura de reconstrucción (Kelly y Ulam) | Todo grafo con al menos 3 vértices queda determinado, salvo isomorfismo, por la colección de sus subgrafos con un vértice borrado | Verificada por computadora para grafos chicos y para clases como los árboles; abierta en general | I.4 |
| Isomorfismo de grafos | ¿Está en P? | Cuasipolinomial (Babai); ni en P ni NP-completo conocido | I.4, II.12 |
| Número de Ramsey R(5,5) | Valor exacto | Se sabe que está entre 43 y 46 (la cota superior 46 es de Angeltveit y McKay, 2024) | II.8 |
| Conjetura de Erdős-Hajnal | Para todo H, los grafos sin H inducido tienen una clique o un conjunto independiente de tamaño polinomial en n | Probada para pocos H; abierta en general | II.8, II.9 |
| Árboles graciosos (Ringel y Kotzig) | Todo árbol admite un etiquetado gracioso | Abierta; la conjetura relacionada de Ringel sobre descomposiciones se probó para n grande en 2020 (Montgomery, Pokrovskiy y Sudakov) | I.5 |
| Doble cubrimiento por ciclos | Todo grafo sin puentes tiene una familia de ciclos que cubre cada arista exactamente dos veces | Abierta | II.5 |
| Juegos únicos (*Unique Games*) | ¿Es NP-difícil distinguir instancias casi satisfacibles de casi insatisfacibles? | Abierta; implicaría que muchas aproximaciones conocidas son óptimas (II.11) | II.11 |

### B. Preguntas de investigación aplicada

Ordenadas por área del tratado. Cada una está formulada para que pueda plantearse como proyecto, con hipótesis y criterios de falsación (como en el laboratorio del Volumen X).

**Medición e incertidumbre**

1. ¿Cómo modelar errores **no aleatorios** en redes construidas con registros institucionales, donde la probabilidad de registro depende del lugar, del grupo social y del tipo de relación? (II.15, VIII.7)
2. ¿Qué métricas estructurales son robustas al muestreo desde un investigado inicial (bola de nieve desde el sospechoso), y cuáles son sistemáticamente sesgadas? (V.3, VI.7)
3. ¿Cómo propagar la incertidumbre de la resolución de entidades a las conclusiones estructurales de forma computacionalmente viable en grafos grandes? (VII.3)

**Poder y estructura**

4. ¿Qué combinación de capas (comunicación, contratos, parentesco, cargos) discrimina mejor entre posiciones de intermediación de servicio y de intermediación con poder de decisión, validada contra casos documentados? (IV.9, VI.5)
5. ¿Puede medirse el desajuste entre estructura formal e informal de una institución (VI.5) de modo comparable entre instituciones y en el tiempo?

**Tiempo y procedencia**

6. ¿Qué representación del tiempo con incertidumbre (intervalos, órdenes parciales) es a la vez expresiva y tratable para consultas de alcanzabilidad temporal en grafos de evidencia? (II.13, VII.10)
7. ¿Cómo diseñar registros de procedencia que permitan recalcular eficientemente todas las conclusiones afectadas por la invalidación de una fuente? (VII.4)
8. ¿Qué métricas de calidad de un grafo de evidencia (VII.12) predicen mejor que sus conclusiones resistirán una revisión independiente?

**Métodos y evaluación**

9. ¿Qué líneas de base simples alcanzan el rendimiento de modelos de aprendizaje sobre grafos en tareas propias de la investigación social y forense, con protocolos de evaluación realistas? (VIII.1, VIII.2)
10. ¿Cómo evaluar explicaciones de algoritmos sobre grafos en dominios donde no hay explicaciones verdaderas conocidas, sin recurrir solo a datos sintéticos? (VIII.3)
11. ¿Qué garantías pueden darse para la extracción de grafos de conocimiento con modelos de lenguaje, en términos de tasa de relaciones inventadas, y cómo se mide sobre corpus reales? (VIII.8)

**Ética y gobernanza**

12. ¿Qué formas de publicación de grafos de personas preservan la utilidad para la investigación y la rendición de cuentas sin permitir reidentificación ni dañar a terceros? (VI.8)
13. ¿Qué requisitos de auditoría y de impugnación deberían exigirse a cualquier sistema estatal que use proximidad en grafos para tomar decisiones sobre personas, a la luz de los casos de VI.7?

## Matriz de técnicas (parte VIII) y fuentes

### Matriz

| Técnica | Qué promete | Qué está demostrado | Alternativa sin aprendizaje | Cuándo preferir la alternativa | Sección |
| --- | --- | --- | --- | --- | --- |
| GNN de paso de mensajes | Representaciones útiles para muchas tareas | Expresividad acotada por 1-WL; buen rendimiento empírico en algunos conjuntos de datos | Características estructurales explícitas más modelo lineal; heurísticas de predicción de aristas | Pocos datos; necesidad de explicar; consecuencias sobre personas | VIII.1 |
| Modelos fundacionales de grafos | Transferencia entre dominios | Resultados preliminares; transferencia negativa posible | Modelos específicos del dominio | Casi siempre, por ahora | VIII.1 |
| Aprendizaje temporal | Predicción de interacciones futuras | Variabilidad alta entre conjuntos de datos; líneas de base simples competitivas | EdgeBank, recencia, REM, procesos de Hawkes | Cuando interesa el mecanismo y no solo la predicción | VIII.2 |
| Explicadores de GNN | Por qué el modelo decidió | Evaluación difícil sin explicaciones verdaderas | Modelos interpretables por construcción | Decisiones de alto impacto | VIII.3 |
| Inferencia causal en redes | Efectos con interferencia | Resultados bajo supuestos fuertes | Experimentos naturales; análisis documental | Una sola red transversal | VIII.4 |
| Modelos de orden superior | Capturar dinámicas de grupo | Diferencias cualitativas en dinámicas teóricas | Grafo bipartito persona–evento con análisis clásico | Cuando el orden superior no está en la dinámica estudiada | VIII.5 |
| Comunidades dinámicas | Narrar la evolución de grupos | Heurísticas inestables entre ventanas | Fuentes que documenten los eventos | Siempre que se quiera afirmar un evento | VIII.6 |
| Reconstrucción bayesiana | Red latente con incertidumbre | Métodos con fundamento estadístico | Análisis de sensibilidad | Cuando no hay mediciones repetidas para estimar errores | VIII.7 |
| Extracción de grafos con LLM | Escalar la construcción de grafos desde texto | Útil pero con relaciones inventadas posibles | Extracción manual o por reglas, verificada | Evidencia con valor probatorio | VIII.8 |

### Fuentes verificadas de este volumen

- [Huang y coautores, "Temporal Graph Benchmark for Machine Learning on Temporal Graphs" (NeurIPS 2023)](https://arxiv.org/abs/2307.01026)
- [Agarwal, Queen, Lakkaraju y Zitnik, "Evaluating Explainability for Graph Neural Networks" (GraphXAI)](https://zitniklab.hms.harvard.edu/projects/GraphXAI)
- [Li, Chen, Wang y Zhu, "Out-of-Distribution Generalization in Graph Foundation Models" (arXiv)](https://arxiv.org/html/2601.21067)
- [Bick, Gross, Harrington y Schaub, "What Are Higher-Order Networks?" (arXiv; publicado en *SIAM Review*, 2023)](https://arxiv.org/abs/2104.11329v3)
- [Rossetti y Cazabet, "Community Discovery in Dynamic Networks: A Survey" (arXiv)](https://arxiv.org/pdf/1707.03186)
- [Edge y coautores, "From Local to Global: A Graph RAG Approach to Query-Focused Summarization" (arXiv)](https://arxiv.org/pdf/2404.16130)
- [Comisión Europea: acto delegado sobre acceso a datos para investigadores (DSA, artículo 40)](https://digital-strategy.ec.europa.eu/en/news/commission-adopts-delegated-act-data-access-under-digital-services-act)

Las demás obras citadas son publicaciones académicas de referencia; sus enlaces se consolidan en el Volumen IX.
