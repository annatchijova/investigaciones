# Teoría de grafos — Evaluación diagnóstica (Entrega 2)

Nov 5, 2026 · @Anna Tchijova

## Cómo usar la evaluación

Son 46 ítems en siete bloques. Sirven para ubicar qué sabés, qué sabés en parte y qué conviene estudiar, sin presuponer nada. No hay tiempo límite, y podés hacer los bloques por separado y en cualquier orden. Las soluciones están en la pestaña **Soluciones**: abrila recién cuando termines un bloque.

**Procedimiento por ítem.**

1. Antes de responder, marcá tu confianza: **S** (seguro), **D** (dudoso) o **N** (no sé). Esta marca es tan importante como la respuesta, porque permite detectar las lagunas que no se perciben como tales.
2. Respondé por escrito, aunque sea en dos líneas. Una respuesta solo pensada no se puede corregir.
3. Después de abrir la solución, ponete un puntaje de 0 a 3 con el criterio de abajo.

| Puntaje | Criterio |
| --- | --- |
| 0 | Sin respuesta, o respuesta con un error de fondo |
| 1 | Idea correcta, pero sin justificar o con errores importantes |
| 2 | Correcta e incompleta: falta un caso, una hipótesis o un paso de la prueba |
| 3 | Completa y justificada, incluyendo las condiciones de validez |

**Reglas.** Se permite consultar papel y lápiz, pero no libros ni buscadores: el objetivo es medir lo disponible, no lo encontrable. En los ítems de demostración vale cualquier prueba correcta, no solo la de la solución. En los ítems conceptuales (bloques E y G), la solución da los elementos esperados; si tu respuesta trae otros, igual de fundados, también suman.

Los ítems marcados con (★★★) son de nivel avanzado: no responderlos no indica laguna en lo básico.

## Bloque A — Fundamentos

Remite al Volumen I. Mide vocabulario, invariantes y representaciones.

- **A1.** ¿Existe un grafo simple con 7 vértices en el que todos tengan grado 3? Justificá.
- **A2.** Un bosque tiene 20 vértices y 4 componentes conexas. ¿Cuántas aristas tiene? Explicá por qué no depende de la forma del bosque.
- **A3.** Verdadero o falso, con justificación: "si dos grafos tienen la misma secuencia de grados, son isomorfos". Si es falso, dá un contraejemplo en el que **ambos grafos sean conexos**.
- **A4.** Definí subgrafo y subgrafo inducido. Dá un ejemplo de datos reales en el que confundirlos lleve a una conclusión equivocada.
- **A5.** ¿Es planar K₃,₃? Justificá en pocas líneas sin dibujar.
- **A6.** Enunciá una caracterización de los grafos bipartitos. ¿Es bipartito C₇? ¿Y el hipercubo Q₄?
- **A7.** Sea A la matriz de adyacencia de un grafo simple no dirigido. ¿Qué cuenta la entrada diagonal (A²)ᵢᵢ? ¿Y la traza de A³?
- **A8.** Tenés un grafo con un millón de vértices y cinco millones de aristas. ¿Usarías matriz de adyacencia o listas de adyacencia? Estimá el orden de magnitud de memoria de cada opción.

## Bloque B — Demostraciones

Mide la capacidad de producir y evaluar pruebas, que es lo que permite distinguir un teorema de una heurística. Escribí las pruebas completas.

- **B1.** Probá que en todo grafo simple con al menos dos vértices hay dos vértices con el mismo grado.
- **B2.** Probá que todo árbol con al menos dos vértices tiene al menos dos hojas.
- **B3.** Probá que si G es simple, tiene n vértices y su grado mínimo cumple δ(G) ≥ (n − 1)/2, entonces G es conexo. ¿La cota es ajustada? Dá un ejemplo.
- **B4.** Probá que si un grafo tiene un circuito euleriano (un circuito que usa cada arista exactamente una vez), todos sus vértices tienen grado par.
- **B5.** Usando la fórmula de Euler, probá que todo grafo planar simple tiene un vértice de grado a lo sumo 5.
- **B6.** (★★★) Encontrá el error de esta "demostración" y mostrá que la afirmación es falsa.
  - *Afirmación:* todo grafo conexo con n ≥ 3 vértices y grado mínimo δ ≥ n/3 tiene un ciclo hamiltoniano.
  - *"Prueba":* por inducción en n. Para n = 3, el único grafo es K₃, que es hamiltoniano. Supongamos que vale para n. Tomemos un grafo G con n vértices que cumple la hipótesis; por inducción tiene un ciclo hamiltoniano. Agreguemos un vértice v con al menos (n+1)/3 vecinos. Como v tiene dos vecinos consecutivos en el ciclo, se puede insertar entre ellos, y el nuevo grafo es hamiltoniano. ∎

## Bloque C — Algoritmos

Mide si se conocen las garantías y las precondiciones de los algoritmos, no solo su existencia. Remite al Volumen III.

- **C1.** En un grafo no ponderado, ¿cuál de BFS o DFS calcula las distancias mínimas desde un vértice? Explicá por qué el otro no lo garantiza.
- **C2.** Dijkstra puede dar un resultado incorrecto con pesos negativos. Construí un contraejemplo con tres vértices y explicá en qué paso falla.
- **C3.** ¿Cuál es la complejidad temporal de Dijkstra con un heap binario, en función de n y m? ¿Cuándo convendría la versión con arreglo simple, de costo O(n²)?
- **C4.** ¿Para qué digrafos existe un ordenamiento topológico? Si el algoritmo de Kahn termina sin haber procesado todos los vértices, ¿qué te dice eso sobre los datos?
- **C5.** En el algoritmo de Kruskal, ¿qué estructura de datos permite detectar ciclos de forma eficiente y qué dos optimizaciones la hacen casi constante por operación?
- **C6.** En una red de llamadas, el peso de cada arista es el número de llamadas: cuanto más alto, más cercano el vínculo. Alguien corre Dijkstra directamente sobre esos pesos para encontrar "el camino más corto entre A y B". ¿Qué está mal? ¿Qué transformación usarías y qué supuesto introduce?
- **C7.** En PageRank, ¿qué función cumple el factor de amortiguación (*damping factor*)? ¿Qué problema generan los vértices sin enlaces salientes (*dangling nodes*) y cómo se resuelve?
- **C8.** ¿El método de Louvain garantiza encontrar la partición de máxima modularidad? ¿Qué es el límite de resolución (*resolution limit*) de la modularidad?

## Bloque D — Teoría intermedia y avanzada

Mide los resultados estructurales que sostienen las aplicaciones. Remite al Volumen II.

- **D1.** Enunciá el teorema de flujo máximo y corte mínimo. En un análisis de "cuellos de botella" (por ejemplo, por dónde pasa necesariamente un flujo de fondos), ¿qué te dice el corte mínimo y qué **no** te dice?
- **D2.** Enunciá el teorema de Hall. Dá un ejemplo de un grafo bipartito con clases del mismo tamaño que no tenga emparejamiento perfecto, y señalá el conjunto que viola la condición.
- **D3.** Sea L el laplaciano de un grafo. ¿Qué indica la multiplicidad del autovalor 0? ¿Qué mide, intuitivamente, el segundo autovalor más chico (conectividad algebraica)?
- **D4.** En el modelo de Erdős–Rényi G(n, p), ¿qué cambia cualitativamente cuando np pasa de ser menor que 1 a ser mayor que 1? ¿Aproximadamente para qué p el grafo pasa a ser conexo con alta probabilidad?
- **D5.** ¿Qué significa que un problema sea NP-completo? Nombrá dos problemas de grafos NP-completos y, para uno de ellos, un problema de aspecto parecido que se resuelva en tiempo polinomial.
- **D6.** (★★★) Explicá de manera intuitiva qué mide el ancho de árbol (*treewidth*) y por qué permite resolver eficientemente problemas que en general son NP-difíciles.

## Bloque E — Redes sociales

Mide el conocimiento de la tradición sociológica y, sobre todo, la separación entre métrica e interpretación. Remite al Volumen IV.

- **E1.** ¿Qué sostiene Granovetter sobre la "fuerza de los vínculos débiles"? ¿En qué evidencia empírica se apoyaba y qué mecanismo estructural propone?
- **E2.** ¿Qué son los agujeros estructurales (*structural holes*) en la obra de Burt? Nombrá al menos una métrica que los operacionalice.
- **E3.** Dos personas vinculadas tienen comportamientos parecidos. ¿Por qué es tan difícil distinguir, con datos observacionales, si eso se debe a homofilia o a influencia social?
- **E4.** En una red de comunicaciones, un actor tiene la mayor centralidad de intermediación (*betweenness*). Dá al menos cuatro interpretaciones alternativas a "es el líder" o "es quien manda".
- **E5.** Explicá la diferencia entre centralidad de grado y centralidad de autovector. Describí una red pequeña en la que ordenen a los actores de forma distinta.
- **E6.** ¿Qué es la multiplexidad? ¿Qué se pierde, o qué se distorsiona, cuando se colapsan varios tipos de relación en un solo grafo?
- **E7.** ¿Qué es la paradoja de la amistad (*friendship paradox*)? Explicá por qué ocurre y qué consecuencia tiene para el muestreo de redes.

## Bloque F — Grafos temporales y procedencia

Mide el manejo del tiempo y de la cadena de inferencias. Remite a los Volúmenes II.13 y VII.

- **F1.** Hay dos contactos registrados: A–B en el instante 3 y B–C en el instante 1. Suponiendo que algo (información, un archivo, un contagio) solo se transmite por contacto y hacia adelante en el tiempo, ¿puede llegar de A a C? ¿Y de C a A? Justificá.
- **F2.** ¿Por qué agregar un grafo temporal en un grafo estático (una arista si hubo algún contacto) tiende a sobreestimar la alcanzabilidad? ¿Qué propiedad de los caminos estáticos deja de valer?
- **F3.** Observás una red durante una ventana de seis meses. Describí dos sesgos que produce el corte de la ventana sobre los vínculos que empezaron antes o terminan después.
- **F4.** En un grafo de procedencia, distinguí con un ejemplo entre dato registrado, inferencia y reconstrucción hipotética. ¿Qué tres tipos de nodo centrales define el modelo W3C PROV?
- **F5.** Tenés logs de dos sistemas cuyos relojes difieren en un desplazamiento desconocido, de hasta 2 segundos. ¿Qué afirmaciones de orden entre eventos podés sostener y cuáles no? ¿Cómo lo representarías en el grafo?

## Bloque G — Epistemología

Mide la capacidad de detectar inferencias ilegítimas. No hay una única respuesta correcta; se evalúa si se identifican los mecanismos. Remite a los Volúmenes V y VI.

- **G1.** En un grafo construido a partir de expedientes judiciales no hay arista entre dos personas. Dá al menos tres mecanismos de producción de datos que expliquen esa ausencia sin que falte la relación real.
- **G2.** Un algoritmo de detección de comunidades encuentra un grupo denso en un grafo de transacciones. ¿Qué tendrías que verificar antes de describir ese grupo como "una organización"?
- **G3.** Explicá el problema de especificación de fronteras (*boundary specification problem*) con un ejemplo de investigación institucional.
- **G4.** Dos visualizaciones del mismo grafo, con distintos algoritmos de disposición (*layout*), sugieren conclusiones distintas. ¿Por qué una visualización no es evidencia de estructura? ¿Qué sí lo sería?
- **G5.** Dos funcionarios conectados en un grafo de reuniones votan igual en un expediente. Dá tres explicaciones causales distintas compatibles con esos mismos datos.
- **G6.** Dá un ejemplo en el que un error de resolución de entidades (*entity resolution*) cambie radicalmente el resultado de un análisis. Considerá los dos errores posibles: fusionar entidades distintas y separar una misma entidad.

## Matriz de diagnóstico

El diagnóstico se lee en dos tablas: el puntaje por bloque indica dónde estás, y el cruce entre confianza y puntaje indica qué lagunas son peligrosas. Completá las celdas vacías directamente en esta página.

### 1. Puntaje por bloque

| Bloque | Ítems | Máximo | Tu puntaje | % | Diagnóstico | Si es laguna, empezar por |
| --- | --- | --- | --- | --- | --- | --- |
| A — Fundamentos | 8 | 24 |  |  |  | Vol. I completo |
| B — Demostraciones | 6 | 18 |  |  |  | Vol. I (pruebas) + West, cap. 1 |
| C — Algoritmos | 8 | 24 |  |  |  | Vol. III |
| D — Intermedia y avanzada | 6 | 18 |  |  |  | Vol. II |
| E — Redes sociales | 7 | 21 |  |  |  | Vol. IV |
| F — Temporales y procedencia | 5 | 15 |  |  |  | Vol. II.13 y VII |
| G — Epistemología | 6 | 18 |  |  |  | Vol. V |
| **Total** | **46** | **138** |  |  |  |  |

**Umbrales.** 80 % o más: fortaleza; ese volumen se puede leer en diagonal y concentrarse en los ítems (★★★). Entre 50 % y 79 %: dominio parcial; conviene leer el volumen completo pero saltear lo que ya salió bien. Menos de 50 %: laguna; empezar por ese volumen antes de los que dependen de él (ver el mapa de dependencias en la Entrega 1).

### 2. Cruce entre confianza y puntaje

Contá cuántos ítems caen en cada celda.

| Confianza marcada | Puntaje 0–1 | Puntaje 2–3 |
| --- | --- | --- |
| S (seguro) | **Laguna oculta**: prioridad máxima | Fortaleza real |
| D (dudoso) | Laguna reconocida | Conocimiento frágil: consolidar con ejercicios |
| N (no sé) | Laguna reconocida | Saber implícito: vale la pena formalizarlo |

La celda "laguna oculta" es la más importante del diagnóstico: son los conceptos que se usan con confianza y de forma incorrecta, que es donde se originan las inferencias erróneas en aplicaciones reales. Si un bloque concentra varias, se estudia primero aunque su puntaje total sea aceptable.

### 3. Perfiles y especialización

Los patrones de resultados sugieren por dónde profundizar:

- **Alto en E y G, bajo en B y D:** formación sustantiva sólida con base formal parcial. Conviene el itinerario 1 (fundamentos formales) del Volumen X antes de las aplicaciones.
- **Alto en C y F, bajo en E:** formación computacional con poca teoría sociológica de redes. Conviene el itinerario 2.
- **Alto en A, C y G, bajo en D:** buen uso aplicado, con lagunas en las garantías teóricas. Conviene el Volumen II, en especial dualidades y modelos nulos.
- **Alto en todo salvo los ítems (★★★):** el siguiente paso es el Volumen VIII (fronteras) y los problemas abiertos.

Si querés, pasame tus respuestas tal como las escribiste y las corrijo con el mismo criterio, señalando dónde un argumento está bien encaminado aunque no coincida con la solución.
