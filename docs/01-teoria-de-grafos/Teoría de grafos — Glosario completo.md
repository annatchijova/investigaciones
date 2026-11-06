# Teoría de grafos — Glosario completo

Nov 5, 2026 · @Anna Tchijova

## Cómo usar el glosario

Este glosario reemplaza la primera parte publicada en la Entrega 1 y cubre la terminología de los Volúmenes I a VIII. Los Volúmenes IX (biblioteca) y X (itinerarios, laboratorio y matriz) no introducen términos nuevos: usan los de acá.

Cada sección corresponde a un volumen y tiene cinco columnas:

- **Término**: la forma en castellano que usa el tratado. Cuando circula más de una traducción, va la elegida y, entre paréntesis, la alternativa.
- **Inglés**: el término que vas a encontrar en la literatura y en las bibliotecas de software; sirve para buscar.
- **Definición breve**: una definición operativa, no la formal completa. La rigurosa está en el volumen indicado.
- **Trampa**: la confusión más frecuente, o el punto donde el término cambia de sentido entre disciplinas.
- **Ver**: volumen y, cuando corresponde, otros términos del glosario con los que conviene leerlo.

Convenciones: G = (V, E) es un grafo con n = |V| vértices y m = |E| aristas. Cuando una definición depende de si el grafo es dirigido, ponderado o simple, se aclara. Las etiquetas epistémicas del tratado (\[Def\], \[Teo\], \[Emp\], \[Int\], \[Hip\], \[Heur\]) no se repiten acá, pero la columna Trampa avisa cuando un término técnico se carga de interpretación.

Los términos de los Volúmenes IV a VII suelen tener un sentido matemático y otro sociológico o jurídico. En esos casos la definición da el sentido técnico y la trampa señala el desplazamiento.

## Fundamentos (Volumen I)

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Vértice (nodo) | vertex, node | Elemento de V; la unidad que el grafo relaciona. | "Nodo" es la palabra de redes; "vértice", la de matemática. Son lo mismo. | Vol I |
| Arista | edge | Par no ordenado {u, v} de vértices. | En un multigrafo, dos aristas pueden unir el mismo par: la arista deja de ser solo un par. | Vol I; multigrafo |
| Arco | arc, directed edge | Par ordenado (u, v) en un grafo dirigido. | Algunos textos dicen "arista dirigida"; la dirección cambia caminos, conectividad y centralidades. | Vol I |
| Lazo | loop | Arista que une un vértice consigo mismo. | Suma 2 al grado en no dirigidos. Muchos algoritmos asumen que no hay lazos. | Vol I; grado |
| Multigrafo | multigraph | Grafo que admite aristas múltiples entre el mismo par. | No confundir con grafo ponderado: tres llamadas pueden ser tres aristas o una arista de peso 3. | Vol I |
| Grado | degree | Número de aristas incidentes en un vértice; en dirigidos, grado de entrada y de salida. | La suma de grados es 2m (lema del apretón de manos); grado alto no es lo mismo que importancia. | Vol I; Vol III centralidad |
| Vecindad | neighbourhood | N(v): vértices adyacentes a v. Cerrada: N\[v\] = N(v) ∪ {v}. | Abierta y cerrada dan resultados distintos en dominación y clustering. | Vol I |
| Regular | regular graph | Todos los vértices tienen el mismo grado k. | Regularidad de grado no implica simetría: hay grafos regulares sin automorfismos no triviales. | Vol I |
| Ralo (disperso) | sparse | Con m del orden de n, no de n². | Es una noción asintótica: un grafo concreto no es "ralo" sin una familia de referencia. | Vol I; Vol III complejidad |
| Subgrafo inducido | induced subgraph | Subconjunto de vértices con todas las aristas que G tiene entre ellos. | Un subgrafo cualquiera puede omitir aristas; el inducido no. | Vol I |
| Paseo | walk | Secuencia de vértices consecutivamente adyacentes; puede repetir todo. | Las potencias de la matriz de adyacencia cuentan paseos, no caminos. | Vol I; camino |
| Sendero | trail | Paseo sin aristas repetidas. | Base de los circuitos eulerianos. | Vol I; Vol II euleriano |
| Camino | path | Paseo sin vértices repetidos. | En inglés antiguo "path" a veces significa paseo; revisá la definición del autor. | Vol I |
| Ciclo | cycle | Camino cerrado de al menos tres vértices (en simples). | En dirigidos, un ciclo de longitud 2 (u→v→u) es válido. | Vol I |
| Componente conexa | connected component | Subgrafo conexo maximal. | En dirigidos hay componentes débiles y fuertes; no son lo mismo. | Vol I; Vol III CFC |
| Diámetro | diameter | Máxima distancia entre pares de vértices. | Infinito si el grafo no es conexo; un solo par alejado lo define (es sensible a errores). | Vol I |
| Árbol | tree | Grafo conexo sin ciclos; tiene n − 1 aristas. | Un bosque es acíclico pero puede no ser conexo. | Vol I; Vol III árbol de expansión |
| Bipartito | bipartite | V se parte en dos clases sin aristas internas; equivale a no tener ciclos impares. | Una red "de dos modos" (personas–eventos) es bipartita por construcción, no por descubrimiento. | Vol I; Vol II proyección |
| Isomorfismo | isomorphism | Biyección entre vértices que preserva adyacencia. | Dos dibujos distintos pueden ser el mismo grafo. | Vol I; invariante |
| Automorfismo | automorphism | Isomorfismo de un grafo en sí mismo. | Mide simetría; vértices en la misma órbita son indistinguibles estructuralmente. | Vol I; Vol IV equivalencia |
| Invariante | invariant | Propiedad que coincide en grafos isomorfos (grado, número cromático, espectro). | Coincidir en invariantes no prueba isomorfismo. | Vol I; Vol II coespectral |
| Planar | planar | Se puede dibujar en el plano sin cruces de aristas. | Que un dibujo tenga cruces no prueba que el grafo no sea planar. | Vol I; menor |
| Cara | face | Región del plano delimitada por un dibujo planar. | Incluye la cara exterior; la fórmula de Euler es n − m + f = 2 en conexos. | Vol I |
| Dual | dual graph | Grafo con un vértice por cara y una arista por cada arista que separa dos caras. | Depende del dibujo, no solo del grafo. | Vol I |
| Contracción | contraction | Fundir los extremos de una arista en un solo vértice. | Puede crear aristas múltiples; suele simplificarse después. | Vol I; menor |
| Menor | minor | Grafo obtenido por borrado de vértices o aristas y contracciones. | Es más débil que subgrafo: un grafo puede tener K₅ como menor sin contenerlo. | Vol I; Vol II ancho de árbol |
| Número cromático | chromatic number | χ(G): mínimos colores para que vértices adyacentes difieran. | Calcularlo es NP-difícil; χ ≥ ω pero puede ser mucho mayor. | Vol I; Vol II perfecto |
| Índice cromático | chromatic index | χ′(G): mínimos colores de aristas sin dos incidentes iguales. | Por Vizing vale Δ o Δ + 1 en grafos simples. | Vol I |
| Hipergrafo | hypergraph | Aristas que conectan cualquier número de vértices. | Proyectarlo a grafo pierde quién estaba junto con quién. | Vol I; Vol II proyección |
| Laplaciano | Laplacian | L = D − A, con D la matriz diagonal de grados. | Hay variantes normalizadas; los resultados espectrales dependen de cuál. | Vol I; Vol II espectro |

## Teoría intermedia y avanzada (Volumen II)

### Conectividad y flujos

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Conectividad por vértices κ(G) | vertex connectivity | Mínimo de vértices cuyo borrado desconecta G (o lo deja en un vértice). | κ ≤ λ ≤ grado mínimo (Whitney); no al revés. | Vol II; Menger |
| Conectividad por aristas λ(G) | edge connectivity | Mínimo de aristas cuyo borrado desconecta G. | No confundir con el λ₁ espectral ni con la conectividad algebraica. | Vol II |
| Separador | separator, vertex cut | Conjunto de vértices cuyo borrado separa dos vértices dados o desconecta G. | Separador mínimo (menor tamaño) no es lo mismo que minimal (no se puede achicar). | Vol II |
| Vértice de corte | cut vertex, articulation point | Vértice cuyo borrado aumenta el número de componentes. | En SNA se lo lee como "intermediario"; esa lectura es \[Int\], no \[Def\]. | Vol II; Vol IV |
| Puente | bridge, cut edge | Arista cuyo borrado aumenta el número de componentes. | El "puente local" de Granovetter es otra cosa (Vol IV). | Vol II |
| Bloque | block, biconnected component | Subgrafo 2-conexo maximal (o un puente). | Los bloques comparten vértices de corte; no particionan V. | Vol II |
| k-conexo | k-connected | Sigue conexo tras borrar cualesquiera k − 1 vértices. | Requiere al menos k + 1 vértices. | Vol II; cohesión estructural |
| Caminos internamente disjuntos | internally disjoint paths | Caminos entre u y v sin vértices internos en común. | El teorema de Menger los iguala con el tamaño del separador mínimo. | Vol II |
| Red de flujo | flow network | Grafo dirigido con capacidades, fuente s y sumidero t. | El "flujo" es un objeto matemático; no presupone que algo circule de verdad. | Vol II; Vol III Edmonds-Karp |
| Corte s–t | s–t cut | Partición (S, V∖S) con s en S y t fuera; su capacidad suma los arcos de S hacia afuera. | Flujo máximo = corte mínimo; el corte mínimo puede no ser único. | Vol II |
| Red residual | residual network | Capacidades que quedan, incluidos arcos inversos para deshacer flujo. | Sin arcos inversos el algoritmo voraz se traba en óptimos locales. | Vol II; Vol III |
| Camino aumentante | augmenting path | Camino s→t en la red residual con capacidad positiva. | Ford-Fulkerson puede no terminar con capacidades irracionales; Edmonds-Karp sí. | Vol II; Vol III |
| Integralidad | integrality | Con capacidades enteras existe un flujo máximo entero. | Es lo que permite usar flujos para emparejamientos. | Vol II |

### Emparejamientos, cubrimientos y coloraciones

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Emparejamiento | matching | Conjunto de aristas sin vértices en común. Perfecto: cubre todos los vértices. | Máximo (mayor tamaño) no es lo mismo que maximal (no se puede extender). | Vol II; Hall, Tutte |
| Emparejamiento estable | stable matching | Emparejamiento sin par bloqueante que prefiera estar juntos. | Gale-Shapley favorece al lado que propone; estable no es equitativo. | Vol II |
| Cubrimiento por vértices | vertex cover | Conjunto de vértices que toca todas las aristas. | En bipartitos, su mínimo iguala al emparejamiento máximo (Kőnig); en general, no. | Vol II |
| Conjunto independiente | independent set | Vértices sin aristas entre sí; α(G) es el máximo. | Su complemento es un cubrimiento por vértices. | Vol II; clique |
| Camino M-aumentante | M-augmenting path | Camino que alterna aristas fuera y dentro de M, con extremos libres. | Berge: M es máximo si y solo si no hay ninguno. | Vol II |
| Clique | clique | Subconjunto de vértices todos adyacentes entre sí; ω(G) es el máximo. | En sociología "camarilla" tiene carga valorativa que el término formal no tiene. | Vol II; Vol IV |
| Polinomio cromático | chromatic polynomial | P(G, k): número de coloraciones propias con k colores. | Grafos distintos pueden tener el mismo polinomio. | Vol II |
| Circuito euleriano | Eulerian circuit | Sendero cerrado que usa cada arista una vez. | Existe en conexos si y solo si todos los grados son pares; es fácil de decidir. | Vol II |
| Ciclo hamiltoniano | Hamiltonian cycle | Ciclo que pasa por cada vértice una vez. | Parece pariente del euleriano, pero decidirlo es NP-completo. | Vol II |
| Problema del viajante | travelling salesperson problem (TSP) | Ciclo hamiltoniano de peso mínimo. | Con desigualdad triangular admite aproximaciones; sin ella, no. | Vol II; aproximación |

### Espectro y expansión

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Espectro | spectrum | Autovalores de la adyacencia o del laplaciano. | Hay que decir de qué matriz; los resultados no se trasladan sin más. | Vol II |
| Coespectrales | cospectral graphs | Grafos no isomorfos con el mismo espectro. | El espectro no determina el grafo. | Vol II; invariante |
| Laplaciano normalizado | normalized Laplacian | I − D^−½ A D^−½; autovalores en \[0, 2\]. | Es el que se vincula con paseos aleatorios; el combinatorio, con cortes. | Vol II |
| Conectividad algebraica | algebraic connectivity | Segundo menor autovalor del laplaciano, λ₂. | Positivo si y solo si G es conexo; no es lo mismo que κ ni λ. | Vol II |
| Vector de Fiedler | Fiedler vector | Autovector asociado a λ₂; su signo sugiere una bipartición. | Da una heurística de corte, no el corte óptimo. | Vol II; Vol III comunidades |
| Constante isoperimétrica | Cheeger constant, edge expansion | Mínimo de aristas que salen de S sobre | S | , con |
| Expansor | expander | Familia de grafos ralos con constante isoperimétrica acotada lejos de 0. | Es una propiedad de familias, no de un grafo suelto. | Vol II |

### Grafos aleatorios y extremales

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| G(n, p) | Erdős–Rényi random graph | Cada par se conecta con probabilidad p, de forma independiente. | Sus grados son casi Poisson: no reproduce colas pesadas ni clustering. | Vol II; modelo nulo |
| Componente gigante | giant component | Componente con una fracción positiva de los vértices; en G(n, p) aparece cuando np > 1. | Es un umbral asintótico; en redes finitas la transición es gradual. | Vol II |
| Modelo de configuración | configuration model | Grafo aleatorio con una secuencia de grados dada. | Puede generar lazos y aristas múltiples; hay que decidir qué hacer con ellos. | Vol II; Vol III modularidad |
| Modelo nulo | null model | Distribución de grafos que conserva algunas propiedades y aleatoriza el resto. | Toda conclusión de "más de lo esperado" depende del nulo elegido. | Vol II; Vol IV |
| Grafo de Turán | Turán graph | Grafo multipartito completo con partes casi iguales; maximiza aristas sin K\_{r+1}. | Es extremal: una cota, no un modelo de redes reales. | Vol II |
| Número de Ramsey | Ramsey number | R(s, t): menor n tal que todo grafo de n vértices tiene K\_s o un independiente de tamaño t. | Garantiza que hay patrones en cualquier grafo grande: encontrar uno no prueba intención. | Vol II |
| Lema de regularidad | regularity lemma | Todo grafo denso se parte en pocas partes con conexiones casi aleatorias entre ellas. | Las constantes son astronómicas; su valor es teórico. | Vol II |

### Clases estructurales y complejidad

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Grafo perfecto | perfect graph | En todo subgrafo inducido, χ = ω. | El teorema fuerte dice: sin ciclos impares de longitud ≥ 5 inducidos ni sus complementos. | Vol II |
| Grafo cordal | chordal graph | Todo ciclo de longitud ≥ 4 tiene una cuerda. | También "triangulado"; no confundir con triangulación planar. | Vol II |
| Orden de eliminación perfecta | perfect elimination ordering | Orden en que cada vértice y sus vecinos posteriores forman clique. | Existe si y solo si el grafo es cordal. | Vol II |
| Grafo de intervalos | interval graph | Vértices son intervalos de la recta; adyacentes si se solapan. | Modela coexistencia temporal, pero pierde el orden de los hechos. | Vol II; grafo temporal |
| χ-acotación | χ-boundedness | Clase donde χ se acota por una función de ω. | No todas las clases la tienen: hay grafos sin triángulos con χ arbitrario. | Vol II |
| Descomposición en árbol | tree decomposition | Árbol de "bolsas" de vértices que cubre aristas y respeta continuidad. | Hay muchas; importa la de ancho mínimo. | Vol II |
| Ancho de árbol | treewidth | Mínimo ancho (bolsa más grande menos 1) de una descomposición en árbol. | Árboles tienen ancho 1; mallas n×n, ancho n. | Vol II; FPT |
| FPT | fixed-parameter tractable | Resoluble en f(k) · poly(n) para un parámetro k. | f puede ser exponencial: FPT no significa rápido en la práctica. | Vol II |
| Kernelización | kernelization | Reducción a una instancia de tamaño acotado por una función de k. | Un problema tiene núcleo si y solo si es FPT. | Vol II |
| W\[1\] | W\[1\] | Clase de problemas parametrizados que se cree que no son FPT. | Clique por tamaño es W\[1\]-completo. | Vol II |
| Aproximación | approximation algorithm | Algoritmo polinomial con garantía de factor respecto del óptimo. | Algunos problemas no admiten ningún factor constante salvo P = NP. | Vol II |
| NP-completo | NP-complete | En NP y al que se reduce todo NP. | Es una afirmación de peor caso; muchas instancias reales se resuelven bien. | Vol II; Vol III |
| Reducción | reduction | Transformación de instancias de un problema en otro que preserva la respuesta. | La dirección importa: reducir A a B muestra que B es al menos tan difícil. | Vol II |
| #P | #P | Clase de problemas de conteo, como contar emparejamientos perfectos. | Contar puede ser difícil aunque decidir sea fácil. | Vol II; confiabilidad |

### Extensiones del objeto grafo

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Grafo temporal | temporal graph | Aristas con marcas o intervalos de tiempo. | Agregarlo en un grafo estático crea caminos que nunca existieron. | Vol II; Vol VII |
| Flujo de enlaces | link stream | Secuencia de interacciones (t, u, v), sin ventanas impuestas. | La ventana de agregación cambia los resultados; elegirla es una decisión de modelado. | Vol II |
| Camino que respeta el tiempo | time-respecting path | Camino cuyas aristas tienen marcas no decrecientes. | La alcanzabilidad temporal no es simétrica ni transitiva. | Vol II |
| Red multicapa (múltiplex) | multilayer, multiplex network | Varias capas de relaciones sobre los mismos actores, o capas acopladas. | Colapsar capas suma cosas que no se suman (parentesco + dinero). | Vol II; Vol IV multiplexidad |
| Supra-adyacencia | supra-adjacency matrix | Matriz por bloques que codifica capas y acoples entre ellas. | El peso de acople es un parámetro arbitrario que altera el espectro. | Vol II |
| Complejo simplicial | simplicial complex | Familia de conjuntos cerrada por subconjuntos; captura interacciones de orden superior. | A diferencia del hipergrafo, obliga a incluir todas las caras. | Vol II; hipergrafo |
| Proyección | one-mode projection | Grafo de un solo tipo de nodos derivado de uno bipartito o de un hipergrafo. | Infla el clustering y crea cliques artificiales. | Vol II; Vol IV |
| Grafo incierto | uncertain, probabilistic graph | Aristas con probabilidad de existencia. | Las probabilidades suelen tratarse como independientes sin justificación. | Vol II; Vol VII evidencia |
| Mundos posibles | possible worlds | Cada realización de las aristas inciertas; las métricas se promedian sobre ellos. | Hay 2^m mundos: se muestrean, no se enumeran. | Vol II |
| Confiabilidad de red | network reliability | Probabilidad de que dos vértices sigan conectados si las aristas fallan al azar. | Calcularla exactamente es #P-difícil. | Vol II |

## Algoritmos (Volumen III)

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Búsqueda en anchura (BFS) | breadth-first search | Explora por capas de distancia con una cola; da distancias en grafos sin pesos. | Con pesos distintos ya no da caminos más cortos: hace falta Dijkstra. | Vol III |
| Búsqueda en profundidad (DFS) | depth-first search | Explora una rama hasta el fondo antes de retroceder; clasifica aristas. | La versión recursiva desborda la pila en grafos grandes; usar la iterativa. | Vol III |
| Arista de retroceso | back edge | En DFS, arista hacia un ancestro todavía abierto. | Su existencia equivale a la presencia de un ciclo (en dirigidos). | Vol III |
| Componente fuertemente conexa (CFC) | strongly connected component (SCC) | Conjunto maximal en que todo vértice alcanza a todo otro por arcos dirigidos. | En redes de transferencias, una CFC indica circularidad posible, no lavado probado. | Vol III; Vol VI |
| Condensación | condensation | Grafo dirigido acíclico que resulta de contraer cada CFC. | Siempre es un DAG; ahí sí se puede ordenar topológicamente. | Vol III |
| Orden topológico | topological order | Orden lineal en que todo arco va de antes a después. | Existe solo si no hay ciclos; puede no ser único. | Vol III; Vol VII DAG |
| Unión-búsqueda | union-find, disjoint-set | Estructura que mantiene particiones con uniones y consultas casi constantes. | En resolución de entidades, una unión errónea arrastra a todos: registrar el motivo. | Vol III; Vol VII |
| Relajación | relaxation | Actualizar d(v) si d(u) + w(u, v) lo mejora. | Es la operación común de Dijkstra, Bellman-Ford y A\*. | Vol III |
| Ciclo negativo | negative cycle | Ciclo de peso total negativo: los caminos más cortos dejan de estar definidos. | Dijkstra no lo detecta y da resultados erróneos; Bellman-Ford sí lo detecta. | Vol III |
| Heurística admisible | admissible heuristic | En A\*, h(v) nunca sobrestima la distancia real al objetivo. | Consistente (monótona) es más fuerte e implica admisible. | Vol III |
| Árbol de expansión mínima | minimum spanning tree | Árbol que conecta todos los vértices con peso total mínimo. | No da caminos más cortos entre pares. | Vol III; Kruskal, Prim |
| Propiedad del corte | cut property | La arista más liviana que cruza un corte pertenece a algún árbol mínimo. | Justifica a Kruskal y a Prim a la vez. | Vol III |
| PageRank | PageRank | Probabilidad estacionaria de un paseo aleatorio con saltos al azar. | Mide prominencia bajo un modelo de navegación, no importancia sustantiva. | Vol III; Vol IV |
| Factor de amortiguación | damping factor | Probabilidad α (típicamente 0,85) de seguir un enlace en vez de saltar. | 0,85 es una convención, no un valor empírico. | Vol III |
| Vértice colgante | dangling node | Vértice sin arcos salientes. | Si no se redistribuye su masa, PageRank no suma 1. | Vol III |
| Intermediación | betweenness centrality | Fracción de caminos más cortos entre otros pares que pasan por v. | Supone que lo que circula va por caminos más cortos. Brandes la calcula en O(nm). | Vol III; Vol IV |
| Cercanía armónica | harmonic closeness | Suma de 1/d(v, u) sobre los demás vértices. | A diferencia de la cercanía clásica, funciona en grafos no conexos. | Vol III |
| Centralidad de autovector | eigenvector centrality | Puntaje proporcional a la suma de los de sus vecinos. | En dirigidos acíclicos o no conexos puede anularse o volverse inestable. | Vol III; Bonacich |
| Centralidad de Katz | Katz centrality | Cuenta paseos de toda longitud con atenuación α^k. | Requiere α < 1/λ₁. | Vol III; Vol IV |
| Modularidad | modularity | Fracción de aristas internas menos la esperada bajo el modelo de configuración. | Valor alto no prueba comunidades "reales"; grafos aleatorios también la tienen alta. | Vol III |
| Límite de resolución | resolution limit | La modularidad no detecta comunidades menores que cierta escala (del orden de √m). | Puede fundir grupos chicos que sí están bien separados. | Vol III |
| Louvain / Leiden | Louvain, Leiden | Heurísticas voraces para maximizar modularidad; Leiden garantiza comunidades conexas. | Son estocásticas: ejecutá varias semillas y reportá la variación. | Vol III |
| Propagación de etiquetas | label propagation | Cada vértice adopta la etiqueta más común entre sus vecinos. | Muy rápida, muy inestable; puede colapsar todo en una etiqueta. | Vol III |
| Modelo estocástico de bloques (SBM) | stochastic block model | Probabilidad de arista que depende solo de los bloques de los extremos. | Detecta también estructura no comunitaria (núcleo–periferia). Su inferencia es estadística. | Vol III; Vol IV |

## Redes sociales y poder (Volumen IV)

### Vínculos, cierre e intermediación

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Vínculo débil | weak tie | En Granovetter, vínculo de baja intensidad (tiempo, intimidad, reciprocidad). | "Débil" se refiere a la intensidad del vínculo, no a su valor: su fuerza está en la información nueva. | Vol IV |
| Puente local | local bridge | Arista cuyos extremos no tienen vecinos en común. | No es el puente de teoría de grafos: borrarla no desconecta, solo alarga distancias. | Vol IV; Vol II puente |
| Homofilia | homophily | Tendencia a vincularse con similares. De base: por composición del entorno. De elección: por preferencia. | Con datos observacionales, homofilia y contagio están confundidos (Shalizi y Thomas). | Vol IV |
| Foco | focus | Contexto social que organiza actividades (escuela, club, trabajo) y produce vínculos. | Mucha "homofilia" es efecto de foco compartido. | Vol IV |
| Capital social | social capital | Recursos accesibles a través de relaciones. | Bourdieu, Coleman y Putnam lo definen de modos incompatibles: decí cuál usás. | Vol IV; Vol V |
| Cierre | closure | Densidad de vínculos alrededor de un actor; favorece confianza y sanción. | Coleman lo valora; Burt lo ve como redundancia. Son hipótesis rivales. | Vol IV |
| Agujero estructural | structural hole | Ausencia de vínculo entre contactos de un actor. | Es una ausencia: depende de que la ausencia esté bien medida, no sea un dato faltante. | Vol IV |
| Restricción | constraint | Índice de Burt: cuánto se concentran las inversiones de v en contactos interconectados. | Baja restricción es oportunidad estructural, no prueba de que se aproveche. | Vol IV |
| Tamaño efectivo | effective size | Número de contactos no redundantes de v. | Sensible a vínculos no observados entre contactos. | Vol IV |
| Tertius gaudens / iungens | tertius gaudens / iungens | El tercero que se beneficia de separar a dos (gaudens) o que los une (iungens). | La misma posición admite ambas estrategias; el grafo no dice cuál. | Vol IV |
| Tipología de intermediarios | brokerage roles | Gould y Fernández: coordinador, consultor, guardián, representante, enlace, según grupos. | Requiere una partición previa en grupos; cambiar la partición cambia los roles. | Vol IV |

### Difusión y cohesión

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Contagio simple | simple contagion | Basta un contacto expuesto para transmitir. | Los vínculos débiles lo aceleran. | Vol IV |
| Contagio complejo | complex contagion | Hace falta exposición a varios contactos (Centola y Macy). | Los vínculos débiles pueden frenarlo; importan los puentes anchos. | Vol IV |
| Umbral | threshold | Fracción o número de vecinos adoptantes que hace adoptar a un actor. | Los umbrales casi nunca se observan: se suponen. | Vol IV |
| Cascada | cascade | Propagación en cadena de una adopción. | Las cascadas grandes son raras y difíciles de predecir. | Vol IV |
| Interferencia | interference | El tratamiento de una unidad afecta el resultado de otra. | Rompe el supuesto SUTVA de la inferencia causal estándar. | Vol IV; Vol VII DAG |
| Núcleo k (k-core) | k-core | Subgrafo maximal en que todos tienen grado ≥ k dentro de él. | Es cohesión por grado mínimo, no por conectividad. | Vol IV |
| Cohesión estructural | structural cohesion | Moody y White: número de actores a remover para desconectar el grupo (es κ). | Más exigente que k-core; costoso de calcular. | Vol IV; Vol II k-conexo |
| Segregación | segregation | Separación de grupos en la red (índices como E–I o asortatividad). | La medida depende del tamaño relativo de los grupos. | Vol IV |
| Directorio entrelazado | interlocking directorate | Personas que integran directorios de varias empresas; red bipartita persona–empresa. | La proyección empresa–empresa hereda los sesgos de la proyección. | Vol IV |
| Acción robusta | robust action | Padgett y Ansell: acción multivocal que mantiene opciones abiertas (los Medici). | Es una interpretación histórica apoyada en la red, no un cálculo. | Vol IV |

### Posiciones y modelos estadísticos

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Equivalencia estructural | structural equivalence | Dos actores con exactamente los mismos vínculos. | La equivalencia regular (vínculos con actores equivalentes) es más laxa y más útil. | Vol IV |
| Modelo de bloques | blockmodel | Partición en posiciones con una matriz reducida de relaciones entre ellas. | Las posiciones son abstracciones; no equivalen a grupos con identidad. | Vol IV; SBM |
| Balance estructural | structural balance | Una red con signos está balanceada si todo ciclo tiene un número par de aristas negativas. | Equivale a que se parta en dos bandos. Las redes reales casi nunca lo están. | Vol IV |
| Índice de frustración | frustration index | Mínimo de aristas a cambiar para alcanzar el balance. | Calcularlo es NP-difícil. | Vol IV |
| Multiplexidad | multiplexity | Coexistencia de varios tipos de relación entre los mismos actores. | Es un dato de relación, no de capa: se pierde si se codifica en una sola matriz. | Vol IV; Vol II multicapa |
| ERGM | exponential random graph model | Modelo de la probabilidad del grafo completo según estadísticas (aristas, triángulos, estrellas). | Puede degenerar; los términos geométricamente ponderados lo mitigan. | Vol IV |
| SAOM | stochastic actor-oriented model | Modelo de Snijders para redes longitudinales: los actores cambian vínculos según funciones objetivo. | Separa selección de influencia bajo supuestos fuertes. | Vol IV |
| REM | relational event model | Modela la tasa de eventos relacionales en tiempo continuo. | Requiere un conjunto de riesgo bien definido: quiénes podían interactuar. | Vol IV; Vol II flujo de enlaces |
| Espacio latente | latent space model | Los actores tienen posiciones latentes; la probabilidad de vínculo cae con la distancia. | Las posiciones no son identificables salvo rotación. | Vol IV |
| Poder–dependencia | power-dependence | Emerson: el poder de A sobre B es la dependencia de B respecto de A. | En redes de intercambio, estar conectado a actores sin alternativas da poder. | Vol IV; Bonacich |
| β de Bonacich | Bonacich power, β-centrality | Centralidad tipo Katz con β que puede ser negativo: estar conectado a débiles da poder. | El signo de β es una hipótesis sobre el poder, no un parámetro técnico neutro. | Vol IV |
| Paradoja de la amistad | friendship paradox | En promedio, tus contactos tienen más contactos que vos. | Es un efecto de muestreo, no una afirmación sobre la popularidad de nadie. | Vol IV |

## Epistemología, criminología y derechos humanos (Volúmenes V y VI)

### Epistemología y teoría social (Volumen V)

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Sustancialismo / perspectiva relacional | substantialism / relational sociology | Emirbayer (1997): explicar por atributos de entidades previas, o por relaciones que las constituyen. | Usar grafos no hace relacional un análisis: se puede hacer sustancialismo con centralidades. | Vol V |
| Formalismo / relacionalismo | formalism / relationalism | Postura que trata la forma de la red como explicativa por sí misma, frente a la que exige el contenido de los vínculos. | La forma sola no distingue una red de cuidado de una de extorsión. | Vol V |
| Campo | field | Bourdieu: espacio de posiciones definido por la distribución de capitales y sus luchas. | No es una red de interacciones: dos agentes pueden ocupar posiciones vecinas sin tratarse nunca. | Vol V |
| Actor-red | actor-network | Latour, Callon: humanos y no humanos (actantes) se ensamblan en asociaciones. | Es una ontología y un método de rastreo, no una técnica de grafos; traducirlo a un grafo pierde lo que propone. | Vol V |
| Capta | capta | Drucker: lo "tomado" por quien observa, frente a dato como lo "dado". | Insiste en que toda red observada es construida; no niega que haya algo que observar. | Vol V |
| Efecto bucle | looping effect | Hacking: las clasificaciones de personas cambian a las personas clasificadas, y eso cambia la clase. | Una lista de "miembros de banda" puede producir lo que dice describir. | Vol V; Vol VI |
| Performatividad | performativity | Callon, MacKenzie: los modelos no solo describen sino que contribuyen a producir el mundo que modelan. | No toda medición es performativa; es una hipótesis a sostener caso por caso. | Vol V |
| Especificación de fronteras | boundary specification | Laumann, Marsden y Prensky (1983): decidir quién está en la red (realista o nominalista). | Es la decisión de mayor impacto y la menos reportada. | Vol V; Vol VI |

### Criminología, crimen organizado y derechos humanos (Volumen VI)

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Sesgo de observación | observation bias | La red visible depende de cómo se recolectó (escuchas, detenciones, registros). | Con datos policiales, la red mide en buena parte la actividad policial. | Vol VI |
| Muestreo desde el investigado | sampling from the target | Redes construidas a partir de los sospechosos iniciales y sus contactos. | La centralidad del punto de partida es casi un artefacto del diseño. | Vol VI |
| Culpa por asociación | guilt by association | Inferir responsabilidad a partir de la proximidad en la red. | La proximidad es un indicio para investigar, nunca una conclusión. | Vol VI |
| Bandera roja | red flag | Patrón que justifica revisión (por ejemplo, ciclos de transferencias, direcciones compartidas). | Es un disparador de examen humano, no una detección de delito. | Vol VI |
| Captura del Estado | state capture | Grupos privados que moldean reglas e instituciones a su favor. | Las redes muestran vínculos; la captura requiere mostrar efectos sobre decisiones. | Vol VI |
| Beneficiario final | beneficial owner | Persona física que en última instancia posee o controla una entidad. | Las cadenas societarias pueden tener ciclos y umbrales distintos según la jurisdicción. | Vol VI; Vol III CFC |
| Nodo de servicio | service node | Intermediario profesional (estudio jurídico, agente registrado) que aparece en muchísimas estructuras. | Su grado altísimo refleja un modelo de negocio, no protagonismo en cada caso. | Vol VI |
| Estimación por sistemas múltiples | multiple systems estimation (MSE) | Estima el total de casos (incluidos los no registrados) cruzando listas superpuestas. | Sus supuestos (heterogeneidad, dependencia entre listas) cambian mucho el resultado. HRDAG lo usa con cuidado explícito. | Vol VI; Vol VII resolución de entidades |
| Reidentificación | re-identification | Recuperar la identidad de personas en datos supuestamente anonimizados. | En grafos basta a menudo la estructura del entorno de un nodo. | Vol VI |
| Privacidad diferencial | differential privacy | Garantía formal: el resultado casi no cambia si se agrega o quita un individuo. | En grafos hay que elegir qué se protege (una arista o un nodo con todas sus aristas). | Vol VI |

## Conocimiento, procedencia, evidencia y telemetría (Volumen VII)

### Grafos de conocimiento

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Tripleta RDF | RDF triple | Enunciado sujeto–predicado–objeto. | Una tripleta no dice quién la afirma ni con qué grado de certeza. | Vol VII |
| IRI | IRI (Internationalized Resource Identifier) | Identificador global de un recurso en RDF. | Dos IRI distintas pueden nombrar lo mismo; RDF no lo supone ni lo descarta. | Vol VII |
| Término tripleta | triple term | En RDF 1.2, una tripleta usada como objeto de otra, para hablar de ella. | RDF 1.2 estaba en Candidate Recommendation (abril de 2026) al cierre del tratado: verificá su estado. | Vol VII |
| Reificador | reifier | Recurso que representa una ocurrencia de afirmación de una tripleta (rdf:reifies). | Permite atribuir fuente y fecha a cada afirmación sin afirmar la tripleta misma. | Vol VII |
| SPARQL | SPARQL | Lenguaje de consulta de RDF. | Por mundo abierto, la ausencia de un resultado no prueba que el hecho sea falso. | Vol VII |
| Ontología | ontology | Vocabulario formal de clases, propiedades y restricciones. | En filosofía es una teoría de lo que existe; en ingeniería, un esquema con semántica. | Vol VII; Vol V |
| OWL | Web Ontology Language | Lenguaje de ontologías con semántica de lógica descriptiva. | Sus axiomas producen inferencias, no validaciones: un dato "incorrecto" puede generar conclusiones nuevas. | Vol VII; SHACL |
| Grafo de propiedades | property graph | Nodos y aristas con etiquetas y pares clave–valor. | No tiene semántica formal estándar como RDF; cada motor define la suya. | Vol VII |
| GQL | GQL (ISO/IEC 39075:2024) | Norma ISO de consulta para grafos de propiedades. | Las implementaciones cubren la norma de forma parcial y desigual. | Vol VII |
| Mundo abierto / cerrado | open / closed world assumption | Abierto: lo no afirmado es desconocido. Cerrado: lo no afirmado es falso. | Una base de inteligencia bajo mundo cerrado convierte la falta de registro en inocencia o en ausencia. | Vol VII |
| SHACL | Shapes Constraint Language | Lenguaje para validar grafos RDF contra formas. | Valida bajo un supuesto de mundo cerrado local; no infiere. | Vol VII |

### Resolución de entidades, procedencia y evidencia

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Resolución de entidades | entity resolution, record linkage | Decidir qué registros refieren a la misma entidad del mundo. | Cada fusión cambia la red; los errores crean nodos puente que no existen. | Vol VII; Vol III unión-búsqueda |
| Bloqueo | blocking | Restringir comparaciones a pares que comparten una clave. | Lo que el bloqueo excluye nunca se compara: es una fuente silenciosa de errores. | Vol VII |
| Fellegi–Sunter | Fellegi–Sunter model | Modelo probabilístico que pondera coincidencias por campo para clasificar pares. | Supone independencia condicional entre campos, que rara vez se cumple. | Vol VII |
| Procedencia | provenance | Registro de cómo, por quién y a partir de qué se produjo un dato. | Sin procedencia no hay forma de deshacer una inferencia equivocada. | Vol VII |
| Entidad / Actividad / Agente | Entity / Activity / Agent (PROV-O) | Las tres clases núcleo de W3C PROV. | "Agente" en PROV es responsabilidad, no necesariamente persona. | Vol VII |
| Marco de argumentación | argumentation framework | Dung: argumentos y una relación de ataque entre ellos, como grafo dirigido. | Dice qué conjuntos son defendibles, no cuáles son verdaderos. | Vol VII |
| Extensión fundamentada | grounded extension | El conjunto más escéptico de argumentos aceptables. | Es única; otras semánticas (preferida, estable) pueden dar varias. | Vol VII |
| Escala del Almirantazgo | Admiralty code, NATO 6×6 | Califica por separado la confiabilidad de la fuente (A–F) y la credibilidad de la información (1–6). | Mezclarlas en un solo número pierde la distinción que la justifica. | Vol VII |
| Dempster–Shafer | Dempster–Shafer theory | Asigna masa a conjuntos de hipótesis y distingue ignorancia de probabilidad baja. | La regla de combinación da resultados contraintuitivos con fuentes muy en conflicto. | Vol VII |
| DAG causal | causal DAG | Grafo dirigido acíclico que codifica supuestos causales. | El DAG no se descubre de los datos: son supuestos que se hacen explícitos. | Vol VII |
| d-separación | d-separation | Criterio gráfico para leer independencias condicionales en un DAG. | Vale si el DAG es correcto; no lo verifica. | Vol VII |
| Colisionador | collider | Vértice con dos flechas que llegan (A → C ← B). | Condicionar en él abre un camino espurio: el sesgo de selección de los datos policiales es un caso. | Vol VII; Vol VI |
| Criterio de la puerta trasera | backdoor criterion | Conjunto de ajuste que bloquea todos los caminos no causales entre tratamiento y resultado. | Ajustar por "todo lo disponible" puede incluir colisionadores. | Vol VII |

### Eventos y telemetría

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Registro de eventos (event sourcing) | event sourcing | Guardar la secuencia inmutable de eventos y derivar el estado de ella. | Corregir no es borrar: se agrega un evento de corrección. | Vol VII |
| Proyección (de eventos) | projection | Vista derivada del registro de eventos. | No confundir con la proyección de un grafo bipartito (Vol II). | Vol VII |
| Tramo (span) | span | Unidad de una traza distribuida con inicio, fin y padre. | Un tramo sin padre no es un error del servicio: puede ser contexto perdido. | Vol VII |
| Explosión de dependencias | dependency explosion | En grafos de procedencia de sistemas, un proceso de larga vida conecta casi todo con todo. | Hace que el rastreo hacia atrás acuse a todo el sistema. | Vol VII |
| Minería de procesos | process mining | Descubrir y verificar modelos de proceso a partir de registros de eventos. | El modelo descubierto refleja lo registrado, no lo que pasó. | Vol VII |
| OCEL | Object-Centric Event Log (OCEL 2.0) | Formato de registros en que un evento puede referir a varios objetos. | Evita aplanar a un solo "caso", que crea convergencia y divergencia falsas. | Vol VII |
| Relación "ocurrió antes" | happened-before | Lamport: orden parcial entre eventos por causalidad en sistemas distribuidos. | Eventos no ordenados por ella son concurrentes, aunque sus marcas de reloj digan otra cosa. | Vol VII |
| Reloj vectorial | vector clock | Vector de contadores por proceso que capta exactamente la relación "ocurrió antes". | Crece con el número de procesos. | Vol VII |
| Desfase / deriva | clock skew / drift | Desfase: diferencia entre relojes en un instante. Deriva: cambio de esa diferencia en el tiempo. | Ordenar eventos de fuentes distintas por hora de pared puede invertir causas y efectos. | Vol VII |

## Fronteras de investigación (Volumen VIII)

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Red neuronal de grafos (GNN) | graph neural network | Modelo que aprende representaciones de nodos, aristas o grafos combinando información de vecinos. | Aprende correlaciones del grafo de entrenamiento, incluidos sus sesgos de observación. | Vol VIII |
| Paso de mensajes | message passing | Cada capa agrega mensajes de los vecinos y actualiza el estado del nodo. | Con k capas, un nodo solo ve su entorno a distancia k. | Vol VIII |
| Test de Weisfeiler–Leman (1-WL) | 1-WL test | Refinamiento iterativo de colores que distingue (algunos) grafos no isomorfos. | Las GNN de paso de mensajes no distinguen más que 1-WL; hay grafos distintos que ninguna separa. | Vol VIII; Vol I isomorfismo |
| Suavizado excesivo | oversmoothing | Con muchas capas, las representaciones de los nodos convergen y se vuelven indistinguibles. | Agregar profundidad no siempre mejora. | Vol VIII |
| Compresión excesiva | oversquashing | Información de un entorno que crece exponencialmente se comprime en vectores de tamaño fijo. | Se asocia a cuellos de botella del grafo, emparentados con la curvatura y la constante isoperimétrica. | Vol VIII; Vol II |
| Heterofilia | heterophily | Tendencia a conectarse con distintos (en etiqueta o atributo). | Muchas GNN suponen homofilia implícitamente y fallan con heterofilia. | Vol VIII; Vol IV homofilia |
| Modelo fundacional de grafos | graph foundation model | Modelo preentrenado sobre muchos grafos para transferir a tareas nuevas. | Su capacidad de transferencia entre dominios es un área abierta, con resultados mixtos. | Vol VIII |
| EdgeBank | EdgeBank | Línea de base sin aprendizaje para predicción de enlaces temporales: predice que se repite lo ya visto. | Varios modelos complejos no la superan con márgenes claros: siempre compará con ella. | Vol VIII; Vol II grafo temporal |
| GraphRAG | GraphRAG | Generación aumentada por recuperación que usa un grafo (a menudo extraído por un LLM) como índice. | El grafo extraído puede contener relaciones inventadas; necesita procedencia y validación. | Vol VIII; Vol VII |
| Explicador | explainer | Método post hoc que señala qué subgrafo o atributos pesaron en una predicción. | Las explicaciones post hoc pueden no ser fieles al modelo; GraphXAI y otros bancos de prueba lo evalúan. | Vol VIII |
| Modelo interpretable por construcción | interpretable-by-design model | Modelo cuya lógica es legible directamente (reglas, prototipos, puntajes simples). | En decisiones de alto riesgo sobre personas, es preferible a explicar una caja negra (argumento de Rudin). | Vol VIII; Vol VI |
