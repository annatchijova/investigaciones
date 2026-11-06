# Teoría de grafos — Volumen X: Itinerarios, laboratorio y soluciones

Nov 5, 2026 · @Anna Tchijova

## Cómo usar este volumen

Este volumen cierra el tratado con los entregables 7 (itinerarios), 8 (laboratorio) y 9 (matriz consolidada), y en la pestaña **Soluciones**, las soluciones de los ejercicios de los volúmenes.

**Itinerarios.** Son tres recorridos, cada uno dividido en **módulos independientes y combinables**. No hay plazos: cada módulo tiene un **criterio verificable para avanzar**, es decir, algo que se puede hacer o demostrar y que indica que el módulo está dominado. Los módulos de distintos itinerarios se pueden intercalar; las dependencias se indican con flechas (→). Para elegir por dónde empezar, conviene usar la matriz de diagnóstico de la Evaluación (Entrega 2).

**Laboratorio.** Son 21 ejercicios de investigación, de problemas pequeños a experimentos avanzados. Cada uno define pregunta, hipótesis, datos identificados (públicos o sintéticos), técnica, implementación, resultado esperado, criterios de falsación y límites de interpretación. Todos son reproducibles en Linux con herramientas abiertas.

**Matriz consolidada.** Reúne en una tabla de síntesis las partes de la matriz distribuidas en los Volúmenes II a VIII, agrupadas por la pregunta que se quiere responder.

## Itinerario 1: de los fundamentos formales a la teoría avanzada

Para quien quiere poder leer y producir demostraciones, y entender las garantías de los métodos.

| Módulo | Contenido | Lecturas y videos | Ejercicios y proyecto | Criterio verificable para avanzar |
| --- | --- | --- | --- | --- |
| F1. Lenguaje y prueba | Definiciones, recorridos, apretón de manos, árboles (I.1–I.6) | Diestel cap. 1 (libre) o West cap. 1–2; Trudeau como apoyo | Ejercicios I.10, 1–5; Evaluación, bloques A y B | Escribir sin consultar las pruebas de las caracterizaciones de árboles y del teorema de König sobre bipartición, y que otra persona (o una revisión contra la solución) no encuentre huecos |
| F2. Planaridad y coloración (→ F1) | Euler, Kuratowski, coloración, dualidad (I.7) | Diestel cap. 4–5 | Ejercicios I.10, 6–7 | Probar que K₃,₃ y el grafo de Petersen no son planares, y construir un orden malo para el coloreo voraz |
| F3. Dualidades min-max (→ F1) | Menger, flujos, Hall, König, Tutte (II.1–II.3) | Diestel cap. 2–3 y 6; Bondy y Murty cap. 7–9 | Ejercicios II, 1–3 | Deducir König y Menger a partir de max-flow/min-cut, por escrito |
| F4. Espectral (→ F1; álgebra lineal) | Adyacencia, laplaciano, Cheeger (II.6) | Chung cap. 1–2; Brouwer y Haemers cap. 1 | Ejercicios II, 6–7; laboratorio 9 | Demostrar que la multiplicidad de 0 en L es el número de componentes y calcular a mano μ₂ de P₄ y C₄ |
| F5. Probabilidad y extremal (→ F1; probabilidad) | Grafos aleatorios, Turán, Ramsey, método probabilístico (II.7–II.8) | Frieze y Karoński cap. 1–4; Zhao cap. 1–2 y clases 1–6 de 18.217 | Ejercicios II, 8–9; I.10, 9 | Reproducir la prueba de Erdős de R(k,k) > 2^(k/2) y la de Mantel sin consultar |
| F6. Complejidad (→ F3) | NP-completitud, aproximación, parametrizada (II.10–II.12) | Kleinberg y Tardos cap. 8; Cygan y coautores cap. 1–3 y 7 | Ejercicios II, 11–12 | Escribir una reducción correcta de 3-SAT a conjunto independiente y el algoritmo FPT de cubrimiento por vértices con su análisis |
| F7. Clases estructurales (→ F6) | Perfectos, chordales, intervalos, ancho de árbol (II.9–II.10) | Golumbic cap. 4 y 8; bibliografía del seminario de la UBA | Ejercicio II, 10; laboratorio 14 | Implementar el reconocimiento de grafos chordales con un orden de eliminación perfecta y verificarlo contra NetworkX |
| F8. Investigación (→ F4, F5, F7) | Regularidad, límites de grafos, menores | Zhao (libro y curso completos); Lovász 2012; Diestel cap. 12 | Leer y presentar un artículo reciente de *Journal of Combinatorial Theory, Series B* o *Combinatorica* | Explicar a otra persona el enunciado y la estrategia de prueba de un resultado reciente, y señalar qué problema abierto toca |

**Variante rápida.** Quien busca solo las garantías necesarias para las aplicaciones puede hacer F1, F3, F4 y F6, y dejar el resto como consulta.

## Itinerario 2: grafos aplicados a ciencias sociales y análisis institucional

Para quien quiere investigar fenómenos sociales, de poder e institucionales con grafos, sin cometer los errores de V.5.

| Módulo | Contenido | Lecturas y videos | Ejercicios y proyecto | Criterio verificable para avanzar |
| --- | --- | --- | --- | --- |
| S1. Datos relacionales | Fronteras, unidades, tipos de vínculo, fuentes (I.9, V.3) | Hanneman y Riddle (español), cap. 1–3; Marsden (1990) | Laboratorio 1 y 2 | Escribir, para una investigación propia, la tabla de diez eslabones de V.3 completa |
| S2. Métricas y sus supuestos (→ S1) | Centralidades, cohesión, comunidades (III.13–III.14, IV.5) | Wasserman y Faust cap. 5 y 7; Borgatti (2005) | Laboratorio 3 y 4 | Para cada centralidad, nombrar el tipo de flujo que presupone y dar un fenómeno donde no corresponde |
| S3. Tradición sociológica (→ S1) | Simmel a Barabási; vínculos débiles, capital social, agujeros (IV.1–IV.3) | Granovetter (1973); Burt (1992); Easley y Kleinberg cap. 3–5 | Ejercicios IV–V, 1 | Explicar la diferencia entre la tesis de Coleman y la de Burt y cómo se operacionaliza cada una |
| S4. Poder relacional (→ S2, S3) | Emerson, Cook, Bonacich, Lukes (IV.8–IV.9) | Bonacich (1987); Cook y coautores (1983) | Ejercicios IV–V, 2; laboratorio 5 | Mostrar con una red concreta que la misma centralidad ordena a los actores de forma opuesta según el signo de β |
| S5. Inferencia (→ S2; estadística) | Modelos nulos, ERGM, SAOM, difusión e identificación causal (II.7, IV.4, IV.7) | Lusher, Koskinen y Robins; materiales de statnet y RSiena; curso de Jackson en Coursera | Laboratorio 10 y 11 | Ajustar un ERGM simple, interpretar sus parámetros y evaluar su bondad de ajuste por simulación |
| S6. Teoría y crítica (→ S3) | Weber, Foucault, Bourdieu, Latour; producción del grafo (V.1–V.5) | Emirbayer (1997); Erikson (2013); Healy (2015); Latour, *Reensamblar lo social* | Ejercicios IV–V, 11–12 | Escribir un análisis de un estudio publicado que identifique al menos tres de los ocho errores de V.5 o justifique por qué los evitó |
| S7. Instituciones, corrupción y derechos humanos (→ S4, S5, S6) | Casos de VI; protocolo de VI.9 | Volumen VI completo; materiales de HRDAG; Wachs, Fazekas y Kertész | Laboratorio 12, 13, 16 y 17 | Diseñar un proyecto completo con el protocolo de VI.9, incluida la evaluación del peor error y la seguridad de terceros |
| S8. Métodos mixtos (→ S6) | Redes cualitativas, etnografía, historia (V.6) | Bellotti (2015); Padgett y Ansell (1993); Lomnitz (1975) | Proyecto: combinar un grafo con entrevistas o documentos sobre el significado de los vínculos | Producir un análisis donde al menos una conclusión estructural se modifique por la evidencia cualitativa, y documentar el cambio |

## Itinerario 3: grafos temporales, procedencia, telemetría y sistemas

Para quien construye sistemas que registran, integran y razonan sobre eventos y evidencia.

| Módulo | Contenido | Lecturas y videos | Ejercicios y proyecto | Criterio verificable para avanzar |
| --- | --- | --- | --- | --- |
| T1. Algoritmos con garantías | BFS, DFS, CFC, topológico, caminos mínimos, flujo (III.1–III.11) | Volumen III; Cormen y coautores cap. 20–24; `grafos_ref.py` | Ejercicios del código de III; laboratorio 6 | Implementar desde cero Dijkstra y Kahn, y probarlos con casos que deben fallar (pesos negativos, ciclos) |
| T2. Tiempo (→ T1) | Grafos temporales, caminos que respetan el tiempo, relojes (II.13, VII.10) | Holme y Saramäki (2012); Lamport (1978) | Laboratorio 7 y 15 | Mostrar con datos reales cuánto sobreestima el grafo agregado la alcanzabilidad temporal |
| T3. Grafos de conocimiento (→ T1) | RDF, OWL, SPARQL, grafos de propiedades, mundo abierto (VII.1–VII.2) | Hogan y coautores cap. 1–5; especificación RDF 1.2 | Ejercicios VII, 1–3 | Representar dos testimonios contradictorios con términos tripleta y validarlos con SHACL |
| T4. Identidad (→ T3) | Resolución de entidades, integración (VII.3) | Christen cap. 1–6 | Laboratorio 8; ejercicio VI, 4 | Medir precisión y exhaustividad de un emparejamiento sobre una muestra etiquetada y reportar el tamaño de la mayor clase |
| T5. Procedencia y evidencia (→ T3) | PROV, argumentación, confianza (VII.4–VII.6) | Familia W3C PROV; Anderson, Schum y Twining; Dung (1995) | Ejercicios VII, 4–5; laboratorio 18 | Dada una fuente invalidada, listar automáticamente todas las conclusiones afectadas |
| T6. Causalidad (→ T5; probabilidad) | DAG, d-separación, sesgo de colisionador (VII.7) | Pearl, Glymour y Jewell; Hernán y Robins cap. 6–8 | Ejercicio VII, 6; laboratorio 19 | Construir un ejemplo simulado de sesgo de colisionador por selección de registros y explicarlo con el DAG |
| T7. Telemetría y reconstrucción (→ T2, T5) | Trazas, procedencia de sistema, minería de procesos, detección de cambios (VII.9–VII.11) | King y Chen (2003); van der Aalst; OCEL 2.0 | Ejercicios VII, 7–8; laboratorio 20 | Reconstruir una sesión a partir de registros de auditoría con el procedimiento de VII.11, marcando niveles epistémicos |
| T8. Arquitectura y calidad (→ T7) | Registro inmutable, proyecciones, métricas (VII.8, VII.12) | Volumen VII completo | Laboratorio 21 | Publicar un tablero de calidad con al menos cinco métricas de VII.12 para un grafo propio |
| T9. Aprendizaje, con crítica (→ T2) | GNN, aprendizaje temporal, explicabilidad (VIII.1–VIII.3) | Hamilton; CS224W; TGB; GraphXAI | Laboratorio 21 | Comparar un modelo aprendido con una línea de base simple bajo un protocolo cronológico y reportar honestamente el resultado |

## Laboratorio: formato y datos

**Formato de cada ejercicio.** Pregunta · Hipótesis · Datos · Técnica · Implementación · Resultado esperado · Falsación (qué resultado obligaría a rechazar la hipótesis) · Límites de interpretación.

**Entorno común (Linux).**

```bash
python3 -m venv lab && . lab/bin/activate
pip install networkx igraph leidenalg numpy scipy pandas matplotlib
# según el ejercicio: pip install prov pyshacl rdflib pm4py
# para ERGM y SAOM: R con los paquetes statnet y RSiena
```

El archivo `grafos_ref.py` del Volumen III se puede usar en todos los ejercicios para contrastar implementaciones.

**Fuentes de datos verificadas.**

| Datos | Contenido | Acceso |
| --- | --- | --- |
| Incluidos en NetworkX | Club de karate de Zachary, familias florentinas (red matrimonial), mujeres del sur de Davis (bipartita), Los Miserables | `networkx` (funciones `karate_club_graph`, `florentine_families_graph`, `davis_southern_women_graph`, `les_miserables_graph`) |
| SNAP, Stanford | email-Eu-core (con etiquetas de departamento) y su versión temporal (986 vértices, 332.334 aristas fechadas, 803 días); CollegeMsg (mensajes fechados en una red social universitaria) | ✓ [email-Eu-core-temporal](https://snap.stanford.edu/data/email-Eu-core-temporal.html), [CollegeMsg](https://snap.stanford.edu/data/CollegeMsg.html) |
| SocioPatterns | Contactos cara a cara medidos con sensores en una escuela secundaria de Marsella (Mastrandrea, Fournet y Barrat, 2015) | ✓ también en [Netzschleuder](https://networks.skewed.de/net/sp_high_school) |
| Netzschleuder (Tiago Peixoto) | Catálogo de cientos de redes con metadatos, descargables en varios formatos | ✓ [networks.skewed.de](https://networks.skewed.de/net/sp_high_school) |
| ICIJ Offshore Leaks | Entidades, personas, intermediarios y domicilios de cinco filtraciones; CSV o volcado de Neo4j; licencia Open Database License, contenido CC BY-SA 3.0, con obligación de citar al ICIJ | ✓ [descarga](https://offshoreleaks.icij.org/pages/database) |
| Open Contracting Data Standard | Datos de contrataciones públicas en formato OCDS publicados por distintos países | Registro de datos de la Open Contracting Partnership |
| Redes encubiertas | Conjuntos de redes delictivas y terroristas usados en la literatura académica | Paquete `networkdata` de R; repositorio de redes encubiertas de UCINET |
| Temporal Graph Benchmark | Conjuntos temporales grandes con protocolos de evaluación | ✓ [TGB](https://arxiv.org/abs/2307.01026) |
| Sintéticos | Modelo de bloques estocásticos, configuración, LFR, Watts-Strogatz | Generadores de NetworkX |

**Ética de los datos.** Varios conjuntos involucran personas reales. Aunque sean públicos, rigen VI.8 y VI.9: no publicar resultados que identifiquen personas sin necesidad, no inferir conductas individuales y citar las fuentes según sus licencias.

## Laboratorio I: ejercicios 1 a 7 (problemas pequeños)

### 1. ¿La red elegida cambia quién parece poderoso?

- **Pregunta.** ¿El liderazgo estructural de los Médici depende de qué relación se mide?
- **Hipótesis.** En la red matrimonial, los Médici ocupan la primera posición por intermediación; en la red de negocios, su ventaja es menor; en la unión de ambas, la ventaja se amplía (como sostienen Padgett y Ansell sobre la combinación de redes sin superposición).
- **Datos.** Red matrimonial en NetworkX (`florentine_families_graph`); redes matrimonial y de negocios completas en el conjunto de Padgett distribuido con UCINET (PADGM y PADGB).
- **Técnica.** Grado, intermediación y centralidad de autovector en tres redes: matrimonial, de negocios y unión.
- **Implementación.** NetworkX; tabla con el ranking de las cinco primeras familias en cada caso.
- **Resultado esperado.** Los Médici primeros por intermediación en la matrimonial y en la unión.
- **Falsación.** Si en la unión los Médici no superan a la segunda familia en intermediación por un margen mayor que en la matrimonial, la hipótesis de complementariedad no se sostiene con estas medidas.
- **Límites.** Datos reconstruidos de fuentes históricas parciales; la intermediación supone caminos mínimos; el resultado describe posición, no acción robusta, que Padgett y Ansell sustentan con documentos.

### 2. ¿Cuánto infla la proyección bipartita?

- **Pregunta.** ¿Qué parte del agrupamiento entre las mujeres del estudio de Davis se debe a la proyección y no a interacción directa?
- **Hipótesis.** La proyección persona–persona tiene un coeficiente de agrupamiento mucho mayor que el esperado en proyecciones de grafos bipartitos aleatorios con la misma secuencia de grados.
- **Datos.** `davis_southern_women_graph` (18 mujeres, 14 eventos).
- **Técnica.** Proyección sobre personas; modelo nulo bipartito de configuración (`networkx.bipartite.configuration_model`), 1.000 réplicas.
- **Implementación.** Comparar el agrupamiento observado de la proyección con la distribución nula.
- **Resultado esperado.** El agrupamiento observado es alto pero buena parte también aparece en las proyecciones nulas.
- **Falsación.** Si el agrupamiento de las proyecciones nulas es similar al observado, la estructura "de grupos" se explica por la proyección y los grados, no por patrones de co-asistencia.
- **Límites.** Datos de los años treinta; la co-asistencia a eventos no es interacción (II.14).

### 3. ¿Qué tan frágil es el ranking de intermediación?

- **Pregunta.** ¿Con qué fracción de aristas faltantes deja de ser estable el ranking de los cinco actores más intermediarios?
- **Hipótesis.** Con un 20 % de aristas faltantes al azar, al menos uno de los cinco primeros cambia en más de la mitad de las réplicas.
- **Datos.** Club de karate de Zachary; repetir con Los Miserables.
- **Técnica.** Eliminar al azar 10 %, 20 % y 30 % de aristas (100 réplicas cada uno) y medir correlación de rangos de Kendall y estabilidad de los cinco primeros.
- **Implementación.** NetworkX; gráfico de estabilidad contra fracción eliminada.
- **Resultado esperado.** Degradación rápida de los puestos intermedios; los dos primeros, más estables.
- **Falsación.** Si el conjunto de los cinco primeros se mantiene en más del 90 % de las réplicas con 30 % de faltantes, la hipótesis de fragilidad se rechaza para estas redes.
- **Límites.** Faltantes al azar; los faltantes reales no son aleatorios (V.3), así que este es el escenario optimista.

### 4. ¿Las comunidades son estables?

- **Pregunta.** ¿Distintos métodos y semillas recuperan la división conocida del club de karate?
- **Hipótesis.** Louvain y Leiden recuperan la división en dos facciones solo parcialmente y producen más de dos comunidades en la mayoría de las corridas.
- **Datos.** Club de karate (el atributo `club` registra la facción después de la escisión documentada por Zachary).
- **Técnica.** Louvain, Leiden y propagación de etiquetas, 50 semillas cada uno; información mutua normalizada (NMI) contra las facciones y entre corridas.
- **Implementación.** NetworkX, igraph y leidenalg.
- **Resultado esperado.** NMI moderada contra las facciones; variabilidad notable entre corridas de propagación de etiquetas.
- **Falsación.** Si todos los métodos producen exactamente dos comunidades que coinciden con las facciones en todas las corridas, la advertencia de III.14 no aplica a esta red.
- **Límites.** Las facciones son metadatos y no "verdad de fondo" (Peel, Larremore y Clauset, 2017).

### 5. Poder y signo de β

- **Pregunta.** ¿La centralidad de Bonacich invierte el ordenamiento al cambiar el signo de β en una red de intercambio?
- **Hipótesis.** En la cadena A–B–C–D–E, con β positivo C es el más central; con β negativo, B y D superan a C.
- **Datos.** Sintéticos: la cadena de cinco vértices y una estrella con hojas extendidas.
- **Técnica.** c(α, β) = α Σ βᵏ Aᵏ⁺¹ 𝟏, con |β| < 1/λ₁; normalización.
- **Implementación.** NumPy: resolver (I − βA)⁻¹ A 𝟏.
- **Resultado esperado.** Inversión del orden entre C y el par B, D. Verificado al preparar este ejercicio: con β = 0,5 (normalizando por el máximo) los valores son 0,5; 0,875; 1; 0,875; 0,5, y con β = −0,3 son 0,364; 1; 0,727; 1; 0,364.
- **Falsación.** Si el orden no cambia para ningún β negativo admisible, la hipótesis falla para esta red.
- **Límites.** Modelo de poder en intercambio excluyente; no se generaliza a otros tipos de relación.

### 6. ¿Qué transformación del peso elegir?

- **Pregunta.** ¿Cuánto cambian los caminos "más cortos" en una red de llamadas según cómo se transforme la intensidad en distancia?
- **Hipótesis.** Las transformaciones 1/w y −log(w/máx w) producen caminos distintos en una fracción apreciable de pares.
- **Datos.** Sintéticos: Watts-Strogatz con pesos de una distribución de colas pesadas; opcionalmente, la red de email-Eu-core con pesos por número de mensajes.
- **Técnica.** Dijkstra con cada transformación; fracción de pares con caminos distintos.
- **Implementación.** `grafos_ref.dijkstra` y NetworkX.
- **Resultado esperado.** Diferencias en un porcentaje no despreciable de pares; intermediación ponderada muy distinta.
- **Falsación.** Si menos del 1 % de los pares cambia, la elección es irrelevante para esta red.
- **Límites.** Ninguna transformación es "correcta"; el ejercicio muestra la sensibilidad, no cuál usar (Evaluación, C6).

### 7. ¿Cuánto miente el grafo agregado?

- **Pregunta.** ¿Qué fracción de los pares alcanzables en el grafo agregado no son alcanzables respetando el tiempo?
- **Hipótesis.** Más de un tercio de los pares alcanzables en el grafo agregado no lo son temporalmente.
- **Datos.** CollegeMsg (SNAP).
- **Técnica.** Alcanzabilidad estática por BFS; alcanzabilidad temporal por un barrido cronológico de los mensajes que propaga el instante más temprano de llegada.
- **Implementación.** Python; los eventos ordenados por tiempo y un diccionario de llegadas desde cada origen (o una muestra de orígenes).
- **Resultado esperado.** Brecha grande, que crece si se acorta la ventana.
- **Falsación.** Si la fracción es menor al 5 %, la agregación es inocua para esta red y esta ventana.
- **Límites.** Supone transmisión por mensaje dirigido, instantánea y sin pérdida.

## Laboratorio II: ejercicios 8 a 14 (intermedios)

### 8. Fusiones en cadena en la resolución de entidades

- **Pregunta.** ¿Cuánto crece la mayor entidad resultante cuando se relaja una regla de emparejamiento?
- **Hipótesis.** El tamaño de la mayor clase crece de forma no lineal (abrupta) al bajar el umbral de similitud, por la transitividad de Union-Find.
- **Datos.** Sintéticos: 5.000 personas con nombre, documento y domicilio; generar 2 a 4 registros por persona con variantes ortográficas, transliteraciones, documentos con errores y domicilios compartidos (estudios contables con muchas sociedades).
- **Técnica.** Similitud de Jaro-Winkler en nombres, coincidencia en documento o domicilio; Union-Find (`grafos_ref.UnionFind`) con umbrales de 0,95 a 0,75.
- **Implementación.** Python; registrar el motivo de cada unión; medir precisión, exhaustividad y tamaño de la mayor clase por umbral.
- **Resultado esperado.** Una transición: por debajo de cierto umbral aparece una mega-entidad que une a cientos de personas a través del domicilio compartido.
- **Falsación.** Si el tamaño de la mayor clase crece de forma lineal y suave, la hipótesis de transición no se sostiene para este generador.
- **Límites.** Resultado dependiente del generador; en datos reales, la estructura de los errores es otra.

### 9. ¿Hasta dónde ve el vector de Fiedler?

- **Pregunta.** ¿A partir de qué diferencia entre densidad interna y externa la bipartición espectral recupera dos grupos plantados?
- **Hipótesis.** Existe un umbral por debajo del cual la recuperación es equivalente al azar (en el modelo de bloques simétrico con grado medio constante, Decelle, Krzakala, Moore y Zdeborová, *Physical Review E*, 2011, establecieron un umbral de detectabilidad).
- **Datos.** Sintéticos: modelo de bloques estocásticos con dos grupos de 500 vértices, grado medio fijo y razón entre probabilidad interna y externa variable.
- **Técnica.** Signo del vector de Fiedler del laplaciano normalizado; fracción de vértices bien clasificados.
- **Implementación.** NetworkX (`stochastic_block_model`) y SciPy (autovectores ralos).
- **Resultado esperado.** Curva en forma de S, con caída cerca del umbral teórico.
- **Falsación.** Si la recuperación es buena muy por debajo del umbral teórico, revisar la implementación: el teorema se refiere al límite de grafos grandes y ralos.
- **Límites.** En grafos ralos y heterogéneos, el laplaciano estándar falla antes del umbral; existen operadores mejores (no retroceso).

### 10. ¿Cuánto del agrupamiento se explica por los grados?

- **Pregunta.** ¿El agrupamiento de la red de correo de email-Eu-core es mayor que el esperado dados sus grados?
- **Hipótesis.** El agrupamiento observado supera al del modelo de configuración en más de 10 desviaciones estándar.
- **Datos.** email-Eu-core (SNAP), versión estática no dirigida.
- **Técnica.** Modelo de configuración (1.000 réplicas, eliminando aristas múltiples y lazos), comparación de transitividad.
- **Implementación.** NetworkX.
- **Resultado esperado.** Exceso grande de agrupamiento.
- **Falsación.** Si el observado cae dentro de la distribución nula, el agrupamiento se explica por la heterogeneidad de grados.
- **Límites.** Eliminar aristas múltiples sesga ligeramente el nulo; preferir un muestreo por intercambio de aristas para mayor precisión.

### 11. Contagio aparente sin contagio

- **Pregunta.** ¿Una regresión ingenua detecta "influencia de los pares" en datos generados sin influencia?
- **Hipótesis.** Con homofilia por un atributo latente, la regresión de la conducta de un actor sobre la media de sus vecinos da un coeficiente positivo y estadísticamente significativo.
- **Datos.** Sintéticos: modelo de espacio latente o de bloques donde el atributo latente determina tanto los vínculos como la conducta.
- **Técnica.** Regresión lineal por mínimos cuadrados; después, repetir controlando por el atributo latente.
- **Implementación.** NumPy y statsmodels.
- **Resultado esperado.** Coeficiente significativo que desaparece al controlar por el latente.
- **Falsación.** Si el coeficiente no es significativo sin control, la homofilia generada es insuficiente para producir el artefacto con este diseño.
- **Límites.** En datos reales el latente no se observa; el ejercicio muestra por qué la identificación requiere diseño (IV.4).

### 12. Riesgo agrupado en contrataciones

- **Pregunta.** ¿Las licitaciones con un único oferente se agrupan en el grafo organismo–proveedor más de lo esperado dado el sector?
- **Hipótesis.** El agrupamiento del riesgo supera al de un modelo nulo que permuta la marca de riesgo dentro de cada sector.
- **Datos.** Contrataciones en formato OCDS de un país de la región, obtenidas del registro de la Open Contracting Partnership.
- **Técnica.** Grafo bipartito; por organismo, tasa de un oferente; asortatividad o autocorrelación de la tasa en la proyección; nulo por permutación dentro del sector (como Wachs, Fazekas y Kertész).
- **Implementación.** pandas, NetworkX.
- **Resultado esperado.** Agrupamiento mayor que el nulo, como en el estudio europeo.
- **Falsación.** Si el agrupamiento observado no supera el percentil 95 del nulo, el riesgo no está estructurado más allá del sector.
- **Límites.** Indicador de riesgo, no de corrupción; no se atribuye conducta a ningún organismo ni empresa (VI.2).

### 13. Nodos de servicio en Offshore Leaks

- **Pregunta.** ¿Cuánto de la conectividad del grafo de Offshore Leaks se debe a intermediarios y domicilios de registro?
- **Hipótesis.** Al eliminar los nodos de tipo intermediario y domicilio, la componente gigante se fragmenta en muchas componentes pequeñas.
- **Datos.** ICIJ Offshore Leaks (CSV; licencia ODbL; citar al ICIJ).
- **Técnica.** Componentes conexas antes y después de quitar los nodos de servicio; distribución de grados por tipo de nodo.
- **Implementación.** pandas e igraph (el grafo es grande).
- **Resultado esperado.** Fragmentación fuerte: la conectividad global es, en gran parte, artefacto de la función de registro.
- **Falsación.** Si la componente gigante conserva la mayoría de los vértices sin los nodos de servicio, la conectividad no depende de ellos.
- **Límites.** No se analizan personas concretas; el ejercicio es estructural. No publicar nombres (VI.8).

### 14. ¿Los testimonios son temporalmente compatibles?

- **Pregunta.** ¿Un conjunto de afirmaciones del tipo "A y B estuvieron juntos en el lugar" y "C y D nunca coincidieron" admite alguna asignación de períodos?
- **Hipótesis.** Si el grafo de coincidencias no es un grafo de intervalos (por ejemplo, contiene un ciclo de cuatro sin cuerdas), el conjunto es inconsistente.
- **Datos.** Sintéticos: generar períodos reales para 20 personas, derivar coincidencias, e introducir errores en una fracción de afirmaciones.
- **Técnica.** Test de cordalidad (`networkx.is_chordal`) como condición necesaria; búsqueda de ciclos sin cuerdas como certificado de inconsistencia.
- **Implementación.** NetworkX.
- **Resultado esperado.** Detección de las inconsistencias introducidas cuando producen ciclos sin cuerdas.
- **Falsación.** Si los errores introducidos casi nunca rompen la cordalidad, el test es poco sensible para este tipo de error.
- **Límites.** La cordalidad es necesaria pero no suficiente para ser grafo de intervalos; con información parcial, el problema completo es NP-completo (II.9).

## Laboratorio III: ejercicios 15 a 21 (avanzados)

### 15. Contagio en contactos reales: orden temporal frente a agregación

- **Pregunta.** ¿El orden temporal de los contactos cambia el alcance de un proceso de contagio respecto del grafo agregado?
- **Hipótesis.** Un proceso SI simulado sobre la secuencia real de contactos alcanza menos estudiantes, y más tarde, que el mismo proceso sobre el grafo agregado; y los modelos nulos que mezclan los tiempos muestran que la organización temporal (ráfagas, horarios) frena la difusión.
- **Datos.** SocioPatterns, escuela secundaria de Marsella (Netzschleuder `sp_high_school`).
- **Técnica.** Simulación SI con semilla aleatoria sobre: (a) la secuencia real; (b) el grafo agregado con tiempos uniformes; (c) nulo con tiempos permutados preservando las aristas; (d) nulo con aristas reasignadas preservando los tiempos.
- **Implementación.** Python; 1.000 simulaciones por condición; curvas de prevalencia.
- **Resultado esperado.** Diferencias claras entre (a) y (b); (c) y (d) separan el efecto del orden del efecto de la estructura.
- **Falsación.** Si las curvas de (a) y (c) coinciden dentro del margen de simulación, el orden temporal no importa para este proceso y esta red.
- **Límites.** El proceso SI es un modelo idealizado; los contactos por sensores tienen umbral de proximidad y no miden la interacción en sí.

### 16. ¿Las comunidades corresponden a los departamentos?

- **Pregunta.** ¿Las comunidades detectadas en el correo de una institución coinciden con sus departamentos formales?
- **Hipótesis.** La coincidencia es parcial (NMI menor a 0,7), y los desajustes se concentran en ciertos departamentos.
- **Datos.** email-Eu-core con etiquetas de departamento (SNAP).
- **Técnica.** Leiden con varias resoluciones y semillas; modelo de bloques estocásticos con corrección por grado (graph-tool); NMI contra departamentos y entre corridas.
- **Implementación.** igraph, leidenalg, graph-tool.
- **Resultado esperado.** Coincidencia parcial; comunidades que reúnen departamentos que colaboran.
- **Falsación.** Si todas las particiones coinciden casi exactamente con los departamentos, la estructura informal no se aparta de la formal en esta institución.
- **Límites.** Los departamentos son metadatos, no verdad de fondo (Peel, Larremore y Clauset); el correo es solo un canal; los datos están anonimizados y así deben quedar. Conecta con el desajuste formal–informal de VI.5.

### 17. Falsos positivos de una base de "asociados"

- **Pregunta.** ¿Cuántas personas sin participación quedarían marcadas si se marca a todos los contactos a distancia 1 y 2 de los participantes en un hecho?
- **Hipótesis.** Con un 1 % de participantes elegidos al azar, la regla de distancia 2 marca a más de la mitad de la red, con una tasa de falsos positivos superior al 95 %.
- **Datos.** email-Eu-core (estructura real, sin atributos); participantes simulados.
- **Técnica.** BFS desde los participantes; tasas de falsos positivos para distancia 1 y 2; variante con participantes concentrados en una comunidad.
- **Implementación.** `grafos_ref.bfs` o NetworkX.
- **Resultado esperado.** Marcado masivo a distancia 2, por el diámetro chico y la paradoja de la amistad.
- **Falsación.** Si la regla de distancia 2 marca menos del 20 % de la red, el argumento de V.5 (error 2) es débil para esta estructura.
- **Límites.** Simulación; ilustra un mecanismo documentado en VI.7, no estima su magnitud en un caso real.

### 18. Procedencia del propio laboratorio

- **Pregunta.** ¿Se puede reconstruir automáticamente qué resultados de los ejercicios anteriores dependen de cada archivo de datos y de cada parámetro?
- **Hipótesis.** Un grafo PROV construido durante la ejecución permite, ante la invalidación de un archivo, listar todas las figuras y conclusiones afectadas sin revisar el código a mano.
- **Datos.** Las ejecuciones de los ejercicios 3, 10 y 16.
- **Técnica.** Modelo PROV: entidades (archivos, parámetros, figuras), actividades (scripts con versión y hash), agentes; alcanzabilidad hacia adelante; validación de aciclicidad.
- **Implementación.** Biblioteca `prov` de Python; registrar hashes de entradas y salidas; exportar a PROV-N y a un grafo de NetworkX.
- **Resultado esperado.** Consulta "qué depende de X" en milisegundos; detección de un ciclo si se introduce uno artificialmente.
- **Falsación.** Si alguna figura afectada no aparece en la consulta, el registro de procedencia está incompleto: es el resultado a investigar.
- **Límites.** Registra lo que el código declara; las dependencias implícitas (variables globales, archivos leídos sin registrar) quedan fuera. **Extensión:** calcular para este grafo el tablero de calidad de VII.12.

### 19. Sesgo de colisionador por selección de registros

- **Pregunta.** ¿La selección de casos por haber sido registrados crea una correlación entre causas independientes?
- **Hipótesis.** Si el registro depende de vivir en una zona vigilada y de cometer una infracción, que son independientes en la población, dentro de los registrados aparecen correlacionadas negativamente.
- **Datos.** Sintéticos: 100.000 personas con dos atributos independientes y probabilidad de registro creciente en ambos.
- **Técnica.** Correlación en la población y en los registrados; DAG del mecanismo; d-separación.
- **Implementación.** NumPy; dibujar el DAG con NetworkX.
- **Resultado esperado.** Correlación nula en la población y negativa en los registrados.
- **Falsación.** Si la correlación entre registrados es cercana a cero, revisar la función de registro: el sesgo requiere que el registro dependa de ambos.
- **Límites.** Mecanismo ilustrativo; en datos reales, el proceso de registro debe documentarse (V.3, VII.7).

### 20. Reconstrucción de una sesión con hipótesis competidoras

- **Pregunta.** ¿Se puede reconstruir qué pasó en un sistema a partir de sus registros de auditoría, distinguiendo lo registrado de lo inferido?
- **Hipótesis.** El procedimiento de VII.11 permite reconstruir la secuencia de un escenario guionado y descartar al menos una hipótesis alternativa plausible.
- **Datos.** Generados por la propia investigadora: una máquina virtual Linux con auditd activado, donde se ejecuta un guion que crea, copia, comprime y transfiere archivos, junto con actividad de fondo.
- **Técnica.** Grafo proceso–archivo–conexión; recorrido hacia atrás desde el archivo transferido; formulación de dos hipótesis compatibles; búsqueda del evento discriminante.
- **Implementación.** auditd, scripts de Python para convertir los registros a un grafo, NetworkX.
- **Resultado esperado.** Reconstrucción correcta del guion, con explosión de dependencias si no se filtran los procesos de larga duración.
- **Falsación.** Si la reconstrucción no recupera algún paso del guion, documentar qué faltaba en el registro (cobertura) y por qué.
- **Límites.** Escenario controlado y conocido; en un incidente real no hay guion contra el cual comparar.

### 21. Línea de base frente a modelo aprendido

- **Pregunta.** ¿Un modelo de aprendizaje sobre grafos temporales supera a una línea de base de repetición en la predicción de mensajes futuros?
- **Hipótesis.** Con muestreo de negativos realista (incluyendo aristas que existieron en el pasado), la ventaja del modelo sobre EdgeBank es pequeña o nula.
- **Datos.** CollegeMsg (SNAP) o un conjunto de TGB.
- **Técnica.** División cronológica; EdgeBank con ventana infinita y con ventana fija; un modelo de TGB (por ejemplo, TGN) con la implementación de referencia del banco de prueba; métrica de ranking (MRR).
- **Implementación.** Paquete de TGB y PyTorch Geometric.
- **Resultado esperado.** Diferencias menores a las reportadas en los artículos originales que usaban evaluación aleatoria.
- **Falsación.** Si el modelo supera ampliamente a todas las líneas de base con el protocolo exigente, el aprendizaje aporta valor real en este conjunto.
- **Límites.** Un solo conjunto de datos; la conclusión no se generaliza (VIII.2). Reportar también el tablero de calidad de los datos usados (VII.12).

## Matriz consolidada de técnicas, aplicaciones y limitaciones

Las matrices de cada volumen detallan cada técnica. Esta tabla las reorganiza por la **pregunta que se quiere responder**, que es como se elige una técnica en la práctica. Para cada pregunta: qué usar, qué condición tiene que cumplirse, qué no se puede concluir, y dónde está el detalle.

| Pregunta | Técnica adecuada | Condición crítica | Lo que no se puede concluir | Detalle |
| --- | --- | --- | --- | --- |
| ¿Están conectados? ¿Por dónde? | BFS, componentes, caminos que respetan el tiempo | Completitud de aristas; orden temporal | Que haya circulado algo | III.1–III.4, II.13 |
| ¿Qué tan robusta es la conexión? | Menger, corte mínimo, conectividad algebraica | Aristas completas; capacidades conocidas | Roles de quienes forman el corte | II.1, II.2, II.6 |
| ¿Es posible una asignación? | Emparejamientos, flujos, coloración | Restricciones conocidas | Que la asignación sea justa | II.3, II.4 |
| ¿Qué posición ocupa un actor? | Centralidades, restricción de Burt, tipología de Gould y Fernandez | Supuesto de flujo compatible con el fenómeno | Poder, influencia, autoridad, culpa | III.13, IV.3, IV.9 |
| ¿Quién tiene ventaja de negociación? | Bonacich con β negativo; modelos de intercambio | Relación de intercambio excluyente | Legitimidad; poder sin interacción | IV.8 |
| ¿Hay grupos? | Modelos de bloques estocásticos (con selección de modelo), k-core, cohesión estructural | Modelo nulo; estabilidad entre métodos | Que el grupo sea una organización | III.14, IV.5 |
| ¿Es llamativa esta propiedad? | Modelo nulo pertinente (configuración, bipartito, temporal) | Elección justificada del nulo | El mecanismo generador | II.7, II.8 |
| ¿Por qué se forman los vínculos? | ERGM, SAOM, REM | Especificación y bondad de ajuste | Validez fuera de la frontera | IV.7 |
| ¿Hubo influencia? | Experimentos, experimentos naturales, SAOM longitudinales, análisis de sensibilidad | Diseño que rompa la confusión con homofilia | Influencia desde una sola red transversal | IV.4, VIII.4 |
| ¿Qué causa qué? | DAG causales, criterio de la puerta trasera | DAG justificado; sin selección por colisionador | Causalidad a partir de aristas de interacción | VII.7 |
| ¿Quién es quién? | Resolución de entidades con reglas documentadas | Muestra revisada; fusiones reversibles | Identidad cierta | VII.3, II.15 |
| ¿De dónde viene esta afirmación? | Grafos de procedencia (PROV), términos tripleta (RDF 1.2) | Registro completo e íntegro | Que la fuente sea veraz | VII.1, VII.4 |
| ¿Qué conclusiones sobreviven a las objeciones? | Marcos de argumentación, grafos de evidencia | Ataques y supuestos explícitos | Lo que nadie objetó | VII.5 |
| ¿Qué pasó y en qué orden? | Grafos de eventos con órdenes parciales, relojes lógicos, minería de procesos | Cobertura e incertidumbre temporal documentadas | Un orden total no justificado; intención | VII.9–VII.11 |
| ¿Cuánto puedo confiar en el grafo entero? | Tablero de calidad, reconstrucción bayesiana, análisis de sensibilidad | Mediciones o escenarios de error plausibles | Robustez frente a errores no modelados | VII.12, VIII.7, V.6 |
| ¿Conviene un modelo aprendido? | Comparación con líneas de base bajo protocolo realista | Evaluación cronológica, negativos exigentes | Superioridad general fuera de los datos evaluados | VIII.1–VIII.3 |
| ¿Puedo usar esto sobre personas sin dañar? | Protocolo de VI.9 | Evaluación del peor error; finalidad limitada | Ausencia de daño sin auditoría | VI.7–VI.9 |

## Cierre: inventario de entregables del tratado

| Entregable pedido | Dónde está | Estado |
| --- | --- | --- |
| 1. Tratado principal | Volúmenes 0 a VIII ([0 y I](https://claude.ai/artifact/HfZAvXDJ3Ms7Br9JG9TLTr), [II](https://claude.ai/artifact/8izmtNva411Sf9GHkLvxt7), [III](https://claude.ai/artifact/Asv5FtwzXJs26rWPF9BMpS), [IV y V](https://claude.ai/artifact/PjMNgKDEdgXUikXSG1vEZ5), [VI](https://claude.ai/artifact/LPtq3MCrSE2g3rWt1xcWm7), [VII](https://claude.ai/artifact/T36WLSYgJH2fJf4nEm2eK4), [VIII](https://claude.ai/artifact/FTzaZoMfUcNCwuZimSPkAk)) | Completo |
| 2. Glosario conceptual | Entrega 1, sección "Glosario (primera parte)" | Completo: el [Glosario completo](https://claude.ai/artifact/1Tugi2iEmaGPB9mxasRy8M) reúne la terminología de los Volúmenes I a VIII (unos 230 términos, con equivalente en inglés, definición breve, trampa frecuente y remisión) y reemplaza la primera parte de la Entrega 1 |
| 3. Mapa de dependencias | Entrega 1, Volumen 0 | Completo |
| 4. Bibliografía anotada y verificada | [Volumen IX](https://claude.ai/artifact/AeM6bTn8uLXa1R57SNouQn), con fuentes verificadas al final de cada volumen | Completo |
| 5. Catálogo de videos y cursos | Volumen IX | Completo |
| 6. Evaluación diagnóstica con soluciones | [Entrega 2](https://claude.ai/artifact/Fg66o6fnFhnnaCiZodWFcb) | Completo (46 ítems) |
| 7. Tres itinerarios | Este volumen | Completo |
| 8. Laboratorio | Este volumen | Completo (21 ejercicios) |
| 9. Matriz de técnicas | Por partes en los Volúmenes II a VIII; consolidada en este volumen | Completo |
| 10. Problemas abiertos | Volumen VIII, sección VIII.10 | Completo |
| Implementaciones de referencia | `grafos_ref.py` (Volumen III), con pruebas contrastadas con NetworkX | Completo |

**Nota para la publicación.** Las referencias y los estados de los estándares se verificaron entre el 5 y el 6 de noviembre de 2026; en particular, RDF 1.2 era Recomendación Candidata del W3C y puede haber cambiado de estado. Las afirmaciones marcadas como verificadas (✓) remiten a una fuente consultada en esa fecha; las obras sin marca son referencias académicas establecidas cuya cita conviene confirmar por DOI antes de reutilizarla en trabajos formales. Si se detecta un error, la forma más útil de corregirlo es abrir una incidencia en el repositorio con la sección y la fuente correcta.
