# Teoría de grafos — Tratado (Entrega 1)

Nov 5, 2026 · @Anna Tchijova

## Índice maestro de volúmenes

El tratado se organiza en once volúmenes; esta primera entrega contiene el Volumen 0 completo, el Volumen I completo, la primera parte del glosario y el núcleo verificado de la bibliografía. Cada volumen es autónomo, pero las referencias cruzadas usan la notación **\[V.sección\]** (por ejemplo, \[II.3\] remite al Volumen II, sección 3).

| Vol. | Título | Cubre del pedido original | Entregables asociados | Estado |
| --- | --- | --- | --- | --- |
| 0 | Mapa del campo, diagnóstico y convenciones | Introducción solicitada | Mapa de dependencias (3) | En esta entrega |
| I | Fundamentos formales | Parte I | Glosario (2), primera parte | En esta entrega |
| II | Teoría intermedia y avanzada | Parte II (15 áreas) | Matriz de técnicas (9), parcial | Pendiente |
| III | Algoritmos y estructuras de datos | Parte III | Implementaciones de referencia | Pendiente |
| IV | Ciencia de redes y sociología relacional | Parte IV | — | Pendiente |
| V | Grafos, poder y epistemología; crítica de errores | Partes V y XIV | — | Pendiente |
| VI | Criminología, crimen organizado y derechos humanos | Parte VI | — | Pendiente |
| VII | Grafos de conocimiento, procedencia, evidencia y telemetría | Partes VII y VIII | — | Pendiente |
| VIII | Fronteras de investigación | Parte IX | Problemas abiertos (10) | Pendiente |
| IX | Biblioteca, cursos y videos | Parte X | Bibliografía (4), catálogo (5) | Núcleo en esta entrega |
| X | Evaluación, itinerarios y laboratorio | Partes XI, XII, XIII | Entregables 6, 7, 8 y matriz (9) completa | Pendiente |

La matriz de técnicas, aplicaciones y limitaciones (entregable 9) se construye de manera incremental: cada volumen técnico agrega sus filas y el Volumen X la consolida.

## Mapa integral del campo

Lo que se suele llamar "grafos" no es una disciplina sino al menos doce tradiciones con preguntas, estándares de prueba y comunidades distintas, que comparten un objeto formal mínimo: un conjunto y una relación binaria (o de mayor aridad) sobre él. Confundirlas es la fuente principal de errores interpretativos: un teorema de la tradición estructural no garantiza nada sobre una red empírica, y un hallazgo empírico de la ciencia de redes no es un teorema.

La forma más útil de distinguirlas es por **la pregunta que cada una considera respondida** y por **lo que cuenta como evidencia** en ella.

| Región | Pregunta típica | Qué cuenta como respuesta | Obras de entrada |
| --- | --- | --- | --- |
| 1. Teoría estructural (combinatoria) | ¿Qué propiedades globales se siguen de condiciones locales? ¿Cuándo existe cierta subestructura? | Demostración | Diestel; West; Bondy y Murty |
| 2. Teoría extremal y de Ramsey | ¿Cuántas aristas fuerzan una estructura? ¿Qué orden es inevitable en el desorden? | Demostración, cotas | Diestel cap. 7 y 9; Bollobás |
| 3. Teoría algebraica y espectral | ¿Qué revelan los autovalores de matrices asociadas al grafo? | Demostración, desigualdades | Chung; Brouwer y Haemers; Godsil y Royle |
| 4. Teoría probabilística | ¿Qué estructura tiene casi seguro un grafo aleatorio? ¿Existe un objeto con propiedad P? | Demostración en el límite, método probabilístico | Alon y Spencer; Bollobás; Frieze y Karoński |
| 5. Teoría topológica | ¿En qué superficies se puede dibujar un grafo sin cruces? | Demostración | Mohar y Thomassen |
| 6. Teoría algorítmica y de complejidad | ¿Se puede resolver eficientemente? ¿Qué cota inferior hay? | Algoritmo con prueba de corrección y cota; reducción | Cormen et al.; Kleinberg y Tardos; Cygan et al. |
| 7. Digrafos y órdenes | ¿Qué cambia cuando la relación no es simétrica? | Demostración | Bang-Jensen y Gutin |
| 8. Ciencia de redes (física estadística) | ¿Qué mecanismos generativos reproducen regularidades observadas? ¿Cómo se propagan procesos sobre redes? | Modelo + ajuste empírico + análisis asintótico, a menudo aproximado | Newman; Barabási |
| 9. Análisis de redes sociales (sociología) | ¿Cómo condiciona la posición relacional la acción, y cómo la acción reconfigura relaciones? | Teoría sustantiva + medición + inferencia | Wasserman y Faust; Borgatti, Everett y Johnson |
| 10. Estadística de redes | ¿Qué podemos inferir de una red observada con error, muestreo y dependencia entre observaciones? | Modelo estadístico con incertidumbre cuantificada | Kolaczyk; Lusher, Koskinen y Robins (ERGM) |
| 11. Datos, conocimiento y sistemas | ¿Cómo almacenar, consultar, razonar y rastrear procedencia sobre relaciones? | Especificación, semántica formal, rendimiento medido | Estándares W3C (RDF, OWL, PROV); Hogan et al. |
| 12. Aprendizaje sobre grafos | ¿Cómo aprender funciones de estructuras relacionales? | Rendimiento empírico en tareas; algunos resultados de expresividad | Hamilton; Bronstein et al. |

A esas doce regiones se superpone un eje transversal de **extensiones del objeto**: hipergrafos y complejos simpliciales (relaciones de orden superior), grafos temporales (relaciones fechadas), redes multicapa (varios tipos de relación sobre los mismos actores), grafos con incertidumbre (aristas y entidades con probabilidad). Cada extensión rompe supuestos de las regiones 1 a 7, de modo que muchos teoremas clásicos dejan de aplicarse tal cual. Por ejemplo, en un grafo temporal la alcanzabilidad no es transitiva: que A alcance a B y B alcance a C no implica que A alcance a C si los contactos ocurren en el orden equivocado. Esto se desarrolla en \[II.13\].

Dos distinciones atraviesan todo el tratado. Primero, **estructura matemática, representación de datos y fenómeno observado** son tres cosas distintas (\[I.9\]). Segundo, la diferencia entre **teorema** (vale para todo grafo que cumpla las hipótesis), **regularidad empírica** (se observó en ciertas redes medidas de cierta manera) e **interpretación sustantiva** (qué significa eso socialmente). Las obras de entrada mencionadas se verifican y anotan en la bibliografía y en el Volumen IX.

## Diagnóstico: lo que suele quedar fuera de una formación aplicada

Una formación aplicada típica (análisis de redes con NetworkX o Gephi, bases de grafos, algo de algoritmos) suele cubrir bien BFS, centralidades, comunidades y visualización, y dejar afuera justo lo que permite saber **cuándo esos resultados significan algo**. Este diagnóstico no presupone nada sobre tu formación: describe el patrón general, y la evaluación del Volumen X sirve para ver dónde te ubicás vos.

| Laguna frecuente | Por qué queda afuera | Qué se pierde | Dónde se trata |
| --- | --- | --- | --- |
| Demostraciones (inducción sobre grafos, argumentos de extremalidad, doble conteo) | Las bibliotecas dan resultados sin pruebas | No se distingue un teorema de una heurística; no se sabe qué hipótesis sostienen cada garantía | \[I\], \[II\] |
| Dualidades min-max (Menger, König, max-flow/min-cut, Hall) | Se enseñan como algoritmos sueltos | Se pierde la herramienta más potente para certificar optimalidad y para razonar sobre cuellos de botella | \[II.1\]–\[II.3\] |
| Teoría espectral | Requiere álgebra lineal | Clustering espectral y PageRank se usan como cajas negras; no se entiende por qué fallan en grafos desconectados o muy heterogéneos | \[II.6\] |
| Grafos aleatorios como modelos nulos | Se usan para "generar datos", no para contrastar | No se puede decir si una métrica observada es llamativa o simplemente esperable dado el número de aristas o la distribución de grados | \[II.7\], \[IV\] |
| Complejidad computacional y parametrizada | Se asume que "si la biblioteca lo hace, se puede" | Se aplican aproximaciones sin saber su garantía; se ignora que la detección de comunidades por modularidad es NP-difícil y que los algoritmos usados son heurísticas | \[II.10\]–\[II.12\] |
| Estadística de redes (ERGM, SBM, modelos orientados al actor) | Vive en departamentos de estadística y sociología | Se confunde descripción con inferencia; se ignora la dependencia entre observaciones, que invalida los tests estadísticos clásicos | \[IV\], \[V\] |
| Error de medición y datos faltantes | Rara vez se enseña | Centralidades y comunidades cambian mucho con pocas aristas faltantes; la ausencia de vínculo se lee como ausencia de relación | \[V\], \[XIV en V\] |
| Teoría de la medición y especificación de fronteras | Se toma el grafo como dado | Quién es nodo y qué es vínculo lo decide quien investiga; esas decisiones condicionan todo el resultado | \[V\] |
| Grafos temporales | Se agregan los eventos en un grafo estático | Aparecen caminos imposibles (que violan el orden temporal) y se sobreestima la alcanzabilidad | \[II.13\], \[VII\] |
| Relaciones de orden superior | Se proyectan sobre pares | Una reunión de cinco personas no es lo mismo que diez conversaciones de a dos; la proyección destruye la información | \[II.14\] |
| Semántica formal (RDF, OWL, suposición de mundo abierto) | Se usan bases de grafos como almacenamiento | No se distingue "no consta" de "es falso", que es exactamente el problema de ausencia de evidencia | \[VII\] |

La conclusión metodológica es que la mayor parte de los errores graves en el uso social de grafos no vienen de no saber un algoritmo, sino de no saber **qué supuestos garantizan su validez** y **qué modelo nulo correspondería para interpretar un número**. Por eso el tratado dedica tanto espacio a hipótesis, contraejemplos y modelos nulos.

## Convenciones epistémicas del tratado

Cada afirmación sustantiva lleva una etiqueta que indica su estatus. Las etiquetas no son decorativas: determinan qué tipo de objeción es pertinente contra cada enunciado.

| Etiqueta | Significa | Se refuta con |
| --- | --- | --- |
| **\[Def\]** | Definición: una convención. No es verdadera ni falsa, sino útil o inútil | Mostrar que no captura lo que se quiere estudiar |
| **\[Teo\]** | Teorema con demostración incluida o referida a una fuente primaria | Encontrar un error en la prueba (no un contraejemplo empírico) |
| **\[Emp\]** | Hallazgo empírico: se observó en datos determinados, medidos de cierta manera | Otros datos, otra medición, un problema de muestreo |
| **\[Int\]** | Interpretación sustantiva: atribuye significado social, político o causal a una estructura | Una interpretación alternativa compatible con los mismos datos |
| **\[Hip\]** | Hipótesis o conjetura abierta | Evidencia o contraejemplo |
| **\[Heur\]** | Heurística: procedimiento sin garantía de optimalidad o corrección | Instancias donde falla |

Otras convenciones:

- **Notación.** Seguimos la de Diestel salvo aviso: G = (V, E), n = |V|, m = |E|, N(v) la vecindad de v, d(v) su grado, δ(G) y Δ(G) los grados mínimo y máximo.
- **Terminología inglesa.** Cada término técnico se da en español con su original entre paréntesis la primera vez, porque la literatura de investigación está mayormente en inglés y porque las traducciones al español no están estandarizadas (por ejemplo, *walk* se traduce como "paseo" o "recorrido" según la escuela).
- **Prerrequisitos.** Cada sección declara qué necesita: \[PR: inducción\], \[PR: álgebra lineal\], \[PR: probabilidad discreta\], etc.
- **Citas.** Solo se citan obras verificadas. Cuando un resultado se atribuye a un autor, se indica la publicación original si fue posible confirmarla; si no, se remite a un libro de texto que lo demuestre.

## Mapa de dependencias entre conceptos

Las aplicaciones a problemas sociales están al final de la cadena: para usarlas con criterio hace falta haber pasado por la estructura formal, la estadística y la crítica epistemológica.

&#91;embedded content: mapa de dependencias · 6 niveles, de prerrequisitos a aplicaciones\]

Cada flecha indica que el bloque de abajo usa conceptos o resultados del de arriba. Las diagonales marcan dependencias cruzadas: el clustering espectral es un algoritmo, los modelos nulos sostienen la estadística de redes, la estadística alimenta la sociología relacional y los grafos temporales plantean problemas epistemológicos propios. Poder y epistemología se ubica en el centro de la penúltima fila porque es el filtro por el que tiene que pasar cualquier aplicación.

## Volumen I — Fundamentos formales

Este volumen construye el vocabulario y los resultados básicos con demostraciones completas. Prerrequisitos generales: lógica proposicional, conjuntos, inducción matemática; para I.8, multiplicación de matrices. Fuente principal de contraste: Diestel (6.ª ed., 2025), capítulo 1, cuyo texto se puede leer gratis en su sitio oficial (ver Bibliografía).

### I.1 Los objetos básicos

**\[Def\] Grafo (simple).** Un grafo es un par G = (V, E) donde V es un conjunto (los vértices o nodos, *vertices*) y E es un conjunto de pares no ordenados de elementos distintos de V (las aristas, *edges*). Una arista {u, v} se escribe uv. "Simple" significa: sin lazos (aristas de un vértice a sí mismo, *loops*) y sin aristas múltiples entre el mismo par.

**\[Def\] Multigrafo y pseudografo.** Un multigrafo admite varias aristas entre el mismo par; formalmente, E es un conjunto de objetos con una función que asigna a cada arista sus extremos. La terminología no está unificada: en algunos textos (West) "pseudografo" es el que admite lazos y aristas múltiples; Diestel llama "multigrafo" directamente al que admite ambas cosas. Antes de usar un teorema, conviene revisar qué definición asume el libro de donde viene.

**\[Def\] Grafo dirigido (digrafo).** E es un conjunto de pares ordenados (u, v), llamados arcos (*arcs*), con cola u y cabeza v. Un digrafo es **simétrico** si (u, v) ∈ E implica (v, u) ∈ E; un grafo no dirigido equivale a un digrafo simétrico sin lazos.

**Por qué importa la elección.** Elegir entre grafo simple, multigrafo o digrafo ya es una decisión de modelado. Si se registran llamadas telefónicas, un grafo simple pierde la frecuencia y la dirección: quién llama a quién y cuántas veces. Si se registran "conocidos", la dirección puede no estar definida, o puede ser asimétrica porque A declara conocer a B pero no al revés. Esa asimetría es un dato: puede ser reciprocidad efectiva ausente o un error de reporte. \[V\] desarrolla este problema.

**Contraejemplo instructivo.** "Todo grafo con n vértices tiene a lo sumo n(n−1)/2 aristas" es verdadero para grafos simples y falso para multigrafos, donde el número de aristas no está acotado por n.

### I.2 Variantes del objeto

- **\[Def\] Ponderado** (*weighted*): una función w: E → ℝ (o a otro conjunto). Advertencia: "peso" puede significar costo, capacidad, distancia, frecuencia o fuerza del vínculo, y los algoritmos tratan cada uno de modo distinto. Un camino "más corto" con pesos que representan intensidad del vínculo (cuanto más alto, más cercano) es un sinsentido si no se invierte o transforma el peso.
- **\[Def\] Etiquetado** (*labeled*): funciones que asignan etiquetas a vértices o aristas. "Grafo etiquetado" también se usa, en combinatoria enumerativa, para indicar que los vértices son distinguibles (se cuentan grafos sobre {1, …, n}).
- **\[Def\] Bipartito**: V se parte en dos clases A y B tales que toda arista va de A a B. **Multipartito** (r-partito): r clases sin aristas internas.
- **\[Def\] Heterogéneo**: vértices y aristas tienen tipos (persona, empresa, contrato; dirige, firma, contrata). Es el modelo de los grafos de conocimiento y los grafos de propiedades \[VII\].
- **\[Def\] Hipergrafo**: H = (V, E) con E una familia de subconjuntos de V de cualquier tamaño (hiperaristas). Una reunión de cinco personas es una sola hiperarista de tamaño 5. Un hipergrafo es k-uniforme si todas sus hiperaristas tienen k elementos; los grafos simples son los hipergrafos 2-uniformes.

**\[Teo\] (König, 1936) Un grafo es bipartito si y solo si no contiene ciclos de longitud impar.**

*Demostración.* (⇒) En un grafo bipartito, todo camino alterna entre A y B. Un ciclo vuelve al vértice de partida, que está en la misma clase, por lo que tiene que dar un número par de pasos. (⇐) Basta probarlo para cada componente conexa. Fijamos un vértice r y definimos A como los vértices a distancia par de r y B como los de distancia impar. Supongamos que hay una arista uv con u y v en la misma clase. Sean P y Q caminos mínimos de r a u y de r a v, y sea w el último vértice común a P y Q. Los tramos de w a u y de w a v, más la arista uv, forman un ciclo. Como d(r,u) y d(r,v) tienen la misma paridad y los tramos desde r hasta w coinciden en longitud, la longitud del ciclo es (d(r,u) − d(r,w)) + (d(r,v) − d(r,w)) + 1, que es impar. Contradicción. ∎

*Consecuencia algorítmica.* Esta prueba es un algoritmo: un recorrido en anchura (BFS) que colorea por paridad de distancia decide bipartición en tiempo O(n + m) y, si falla, entrega un ciclo impar como certificado \[III\].

### I.3 Vocabulario local y global

**\[Def\]** Dos vértices son **adyacentes** si forman una arista. La **vecindad** N(v) es el conjunto de vértices adyacentes a v; el **grado** d(v) = |N(v)| en grafos simples (en multigrafos se cuentan aristas, y un lazo suma 2). En digrafos se distinguen grado de entrada d⁻(v) y de salida d⁺(v).

La jerarquía de recorridos es fuente de confusiones de traducción:

| Español | Inglés | Se permite repetir vértices | Se permite repetir aristas |
| --- | --- | --- | --- |
| Paseo / recorrido | *walk* | Sí | Sí |
| Sendero / camino simple en aristas | *trail* | Sí | No |
| Camino | *path* | No | No |
| Circuito | *circuit* / *closed trail* | Sí (vuelve al inicio) | No |
| Ciclo | *cycle* | No (salvo inicio = fin) | No |

**\[Def\]** G es **conexo** si entre todo par de vértices hay un camino. Las **componentes conexas** son los subgrafos conexos maximales. La **distancia** d(u, v) es la longitud mínima de un camino u–v (∞ si no existe). La **excentricidad** de v es su máxima distancia a otro vértice; el **diámetro** es la máxima excentricidad y el **radio**, la mínima.

**\[Teo\] Lema del apretón de manos (*handshaking lemma*).** En todo grafo (también multigrafo), la suma de los grados es el doble del número de aristas.

```latex
\sum_{v \in V} d(v) = 2m
```

*Demostración (doble conteo).* Contamos los pares (v, e) con v extremo de e. Contando por vértice, obtenemos la suma de grados. Contando por arista, cada arista aporta exactamente 2 (un lazo, que tiene a v como ambos extremos, también aporta 2 por convención). ∎

*Corolario.* El número de vértices de grado impar es par. *Uso práctico:* si en un relevamiento cada persona declara cuántos contactos tiene y la suma resulta impar, los datos no pueden provenir de una relación simétrica completa: hay asimetría de reporte o faltantes. Es un control de consistencia simple y poco usado.

**\[Teo\] Todo paseo de u a v contiene un camino de u a v.**

*Demostración.* Tomamos un paseo u–v de longitud mínima. Si repitiera un vértice x, podríamos eliminar el tramo entre las dos apariciones de x y obtendríamos un paseo u–v más corto. Contradicción. ∎

**\[Teo\] (Diestel, Prop. 1.3.1) Si δ(G) ≥ 2, entonces G contiene un camino de longitud al menos δ(G) y un ciclo de longitud al menos δ(G) + 1.**

*Demostración (argumento de extremalidad).* Sea P = x₀x₁…xₖ un camino de longitud máxima. Todos los vecinos de xₖ están en P, porque si no, podríamos extender P. Como xₖ tiene al menos δ vecinos, todos entre x₀,…,xₖ₋₁, resulta k ≥ δ. Sea i el menor índice tal que xᵢ es vecino de xₖ; entonces i ≤ k − δ, y el ciclo xᵢxᵢ₊₁…xₖxᵢ tiene longitud al menos δ + 1. ∎

Este patrón ("tomá el objeto máximo; si algo lo extendiera, contradicción") es una de las técnicas de prueba más usadas en el campo.

**\[Teo\] rad(G) ≤ diam(G) ≤ 2·rad(G)** para G conexo. *Prueba:* la primera desigualdad vale por definición. Para la segunda, sea c un vértice de excentricidad mínima; para cualesquiera u, v vale d(u,v) ≤ d(u,c) + d(c,v) ≤ 2·rad(G) por desigualdad triangular. ∎

**Contraejemplo: el paseo no es camino en datos reales.** En una traza de transferencias A→B→C→A→D, el dinero que llega a D "pasó" por A dos veces. Si se modela como camino, se pierde el ciclo, que puede ser justamente lo relevante (circularidad en operaciones). En grafos temporales, además, hay que respetar el orden de los eventos \[II.13\].

### I.4 Isomorfismo, automorfismo, subgrafos y menores

**\[Def\] Isomorfismo.** G y H son isomorfos si existe una biyección φ: V(G) → V(H) tal que uv ∈ E(G) si y solo si φ(u)φ(v) ∈ E(H). Un **automorfismo** es un isomorfismo de G en sí mismo; forman un grupo, Aut(G). Un **invariante** es una propiedad preservada por isomorfismos: n, m, la secuencia de grados, el número de triángulos, el espectro.

**Contraejemplo clave.** Coincidir en invariantes no implica isomorfismo. El ciclo C₆ y la unión disjunta de dos triángulos 2C₃ tienen 6 vértices, 6 aristas y todos sus vértices de grado 2, pero el primero es conexo y el segundo no. Ningún conjunto finito de los invariantes usuales caracteriza a todos los grafos salvo isomorfismo de forma eficiente conocida.

**\[Teo/estado del arte\] Complejidad del isomorfismo.** No se sabe si el problema de isomorfismo de grafos está en P ni si es NP-completo. Babai anunció en 2015 un algoritmo de tiempo cuasipolinomial; tras una corrección de 2017 hecha por el propio autor, el resultado se considera vigente en la comunidad. En la práctica, herramientas como nauty y Traces resuelven la mayoría de las instancias reales con rapidez. *Relevancia aplicada:* deduplicar subestructuras (por ejemplo, "patrones" de transacciones) requiere isomorfismo o una forma canónica, y su costo no es trivial.

**\[Def\] Subgrafos.** H es **subgrafo** de G si V(H) ⊆ V(G) y E(H) ⊆ E(G). Es **inducido** si contiene todas las aristas de G entre sus vértices: G\[S\]. Es **generador** (*spanning*) si V(H) = V(G). La diferencia importa: "no hay vínculo entre A y B en la muestra" significa algo distinto en un subgrafo inducido (se observó a ambos y no hay vínculo) que en uno no inducido (puede que no se haya relevado).

**\[Def\] Menores.** Contraer una arista uv es reemplazar u y v por un único vértice adyacente a la unión de sus vecindades. H es **menor** (*minor*) de G si se obtiene de un subgrafo de G mediante contracciones. Intuición: H "vive dentro" de G de manera difusa, con cada vértice de H representado por un subgrafo conexo de G (un "conjunto rama").

**\[Teo\] (Wagner, 1937)** Un grafo finito es planar si y solo si no tiene a K₅ ni a K₃,₃ como menor. *Prueba:* en Diestel, cap. 4.

**\[Teo\] (Robertson y Seymour, Teorema de los Menores)** En toda sucesión infinita de grafos finitos hay dos, Gᵢ y Gⱼ con i < j, tales que Gᵢ es menor de Gⱼ. Consecuencia: toda propiedad cerrada bajo menores se caracteriza por un conjunto **finito** de menores prohibidos. La prueba se completa en la serie Graph Minors I a XX, publicada entre 1983 y 2004 en el *Journal of Combinatorial Theory, Series B*. La 6.ª edición de Diestel actualiza este capítulo con la teoría de *tangles*.

### I.5 Árboles y bosques

**\[Def\]** Un **bosque** es un grafo acíclico; un **árbol** es un bosque conexo. Una **hoja** es un vértice de grado 1.

**\[Teo\] Caracterizaciones equivalentes.** Para un grafo T con n vértices, son equivalentes:

1. T es un árbol (conexo y acíclico).
2. Entre cada par de vértices hay exactamente un camino.
3. T es minimalmente conexo: es conexo, pero quitar cualquier arista lo desconecta.
4. T es maximalmente acíclico: es acíclico, pero agregar cualquier arista crea un ciclo.
5. T es conexo y tiene n − 1 aristas.
6. T es acíclico y tiene n − 1 aristas.

*Demostración (núcleo).* (1⇒2) Existe un camino por conexión; si hubiera dos caminos distintos entre u y v, su unión contendría un ciclo. (2⇒3) Si quitar uv no desconectara, quedaría otro camino u–v además de la arista. (3⇒1) Si hubiera un ciclo, quitar una de sus aristas no desconectaría. (1⇒4) Si se agrega uv, el camino único u–v más uv forman un ciclo. Para 5 y 6 se usa el lema siguiente. ∎

**\[Teo\] Todo árbol con n ≥ 2 vértices tiene al menos dos hojas, y m = n − 1.**

*Demostración.* Las puntas de un camino de longitud máxima son hojas: un vecino adicional extendería el camino o cerraría un ciclo. Quitando una hoja se obtiene un árbol con n − 1 vértices; por inducción, tiene n − 2 aristas, y el original tiene n − 1. ∎

*Corolario.* Un bosque con c componentes tiene exactamente n − c aristas. Así, el número de componentes de un grafo es al menos n − m. Esto da un control rápido para datos: un grafo con muchas menos aristas que vértices está necesariamente fragmentado.

**\[Teo\] Fórmula de Cayley.** Hay n^(n−2) árboles distintos sobre n vértices etiquetados. Hay varias pruebas, entre ellas la biyección con las secuencias de Prüfer; se recomienda la colección de cuatro demostraciones de Aigner y Ziegler, *Proofs from THE BOOK*.

**Árboles generadores.** Todo grafo conexo tiene un árbol generador (tomá un subgrafo conexo generador minimal). El árbol de BFS preserva distancias desde la raíz; el de DFS tiene la propiedad de que toda arista no arbórea une un vértice con un ancestro suyo. Ambos hechos son la base de algoritmos del Volumen III.

**Advertencia aplicada.** Los organigramas y las jerarquías de mando se dibujan como árboles, pero las organizaciones reales casi nunca lo son: hay líneas cruzadas, dependencias funcionales y vínculos informales. Representar una organización criminal como árbol (la "pirámide") impone una estructura que la evidencia empírica suele contradecir; esta crítica se desarrolla en \[VI\].

### I.6 Familias clásicas

| Familia | Notación | Definición | n, m | Propiedades útiles |
| --- | --- | --- | --- | --- |
| Completo | Kₙ | todos los pares adyacentes | n, n(n−1)/2 | diámetro 1; χ = n |
| Bipartito completo | Kₐ,ᵦ | todas las aristas entre clases de tamaños a y b | a+b, ab | modelo de afiliación total |
| Camino | Pₙ | x₁x₂…xₙ | n, n−1 | diámetro n−1 |
| Ciclo | Cₙ (n ≥ 3) | camino más la arista xₙx₁ | n, n | bipartito si y solo si n es par |
| Estrella | K₁,ₙ | un centro unido a n hojas | n+1, n | centralidad extrema en un solo vértice |
| Rueda | Wₙ | Cₙ más un centro adyacente a todos | n+1, 2n |  |
| Hipercubo | Q\_d | vectores binarios de longitud d, adyacentes si difieren en un bit | 2^d, d·2^(d−1) | bipartito, d-regular, diámetro d |
| Petersen | P | 10 vértices, 15 aristas, 3-regular | 10, 15 | contraejemplo clásico: no es planar, no es hamiltoniano, χ' = 4 |

**\[Def\]** G es **k-regular** si todos sus vértices tienen grado k. El **complemento** Ḡ tiene los mismos vértices y exactamente las aristas que G no tiene.

El grafo de Petersen merece atención especial: Holton y Sheehan le dedicaron un libro entero (*The Petersen Graph*, Cambridge University Press, 1993) porque sirve de contraejemplo a numerosas conjeturas. Un buen hábito ante una conjetura plausible es probarla primero contra Petersen.

### I.7 Planaridad, coloreo y dualidad

&#91;PR: inducción; intuición topológica básica\]

**\[Def\]** Un grafo es **planar** si admite un dibujo en el plano sin cruces de aristas. Un dibujo así (un **grafo plano**, *plane graph*) divide el plano en regiones llamadas **caras**, una de ellas no acotada.

**\[Teo\] Fórmula de Euler.** Si G es un grafo plano conexo con n vértices, m aristas y f caras, entonces:

```latex
n - m + f = 2
```

*Demostración (inducción en m).* Si G es un árbol, m = n − 1 y hay una sola cara, así que n − (n−1) + 1 = 2. Si no es árbol, tiene un ciclo; sea e una arista del ciclo. En un dibujo plano, e separa dos caras distintas (por el teorema de la curva de Jordan aplicado al ciclo), así que quitarla preserva la conexión y fusiona dos caras: G − e tiene m − 1 aristas y f − 1 caras. Por hipótesis inductiva, n − (m−1) + (f−1) = 2, que es lo mismo. ∎

**\[Teo\] Si G es planar simple con n ≥ 3, entonces m ≤ 3n − 6. Si además no tiene triángulos, m ≤ 2n − 4.**

*Demostración.* Cada cara está bordeada por al menos 3 aristas, y cada arista borde de a lo sumo 2 caras: 3f ≤ 2m. Sustituyendo f = 2 − n + m en Euler se obtiene la cota. Sin triángulos, cada cara tiene al menos 4 aristas en su borde: 4f ≤ 2m. ∎

*Corolarios.* K₅ no es planar (10 > 3·5 − 6 = 9). K₃,₃ no es planar (es bipartito, sin triángulos, y 9 > 2·6 − 4 = 8). Todo grafo planar tiene un vértice de grado ≤ 5, porque si todos tuvieran grado ≥ 6, la suma de grados sería ≥ 6n > 2(3n − 6).

**\[Teo\] (Kuratowski, 1930)** G es planar si y solo si no contiene una subdivisión de K₅ ni de K₃,₃. (Wagner lo reformuló con menores; ver I.4.)

**\[Def\] Coloración.** Una k-coloración propia de vértices es una función c: V → {1,…,k} con c(u) ≠ c(v) para toda arista uv. El **número cromático** χ(G) es el menor k posible. La coloración de aristas y el **índice cromático** χ'(G) se definen análogamente.

**\[Teo\] χ(G) ≤ Δ(G) + 1.** *Prueba (algoritmo voraz):* recorrer los vértices en cualquier orden y asignar a cada uno el menor color no usado por sus vecinos ya coloreados. Como tiene a lo sumo Δ vecinos, alguno de los Δ + 1 colores queda libre. ∎

**\[Teo\] (Brooks, 1941)** Si G es conexo y no es completo ni ciclo impar, χ(G) ≤ Δ(G). **\[Teo\] (Vizing, 1964)** Para G simple, Δ(G) ≤ χ'(G) ≤ Δ(G) + 1.

**\[Teo\] Todo grafo planar es 6-coloreable.** *Prueba:* por inducción, quitar un vértice v de grado ≤ 5, colorear el resto y darle a v un color que no usen sus a lo sumo cinco vecinos. ∎ Con un argumento de cadenas de Kempe se llega a 5 colores (Heawood, 1890). El **Teorema de los Cuatro Colores** fue demostrado por Appel y Haken en 1976 con asistencia computacional; Robertson, Sanders, Seymour y Thomas dieron una prueba simplificada en 1997, y Gonthier la formalizó en el asistente de pruebas Coq en 2005. Es un caso histórico importante para la epistemología de la demostración: durante años se discutió si una prueba que nadie puede verificar a mano cuenta como prueba.

**Límite computacional.** Decidir si χ(G) ≤ 3 es NP-completo, incluso para grafos planares \[II.12\]. La coloración voraz es una heurística: su resultado depende del orden y puede ser muy malo. Por ejemplo, hay órdenes de un grafo bipartito que hacen que el voraz use n/2 colores.

**\[Def\] Dual.** Dado un grafo plano G, su dual G\* tiene un vértice por cada cara de G y una arista que cruza cada arista de G. Advertencia: el dual depende del dibujo, no solo del grafo; un mismo grafo planar puede tener dibujos con duales no isomorfos. Los ciclos de G corresponden a cortes minimales de G\*; esta dualidad ciclo-corte reaparece en flujos planares \[II.2\].

**Aplicación clásica.** La coloración modela asignación sin conflictos: turnos, frecuencias de radio, horarios de exámenes. En investigación, sirve para planificar entrevistas evitando que dos personas en conflicto coincidan, o para asignar revisores sin conflicto de interés.

### I.8 Representaciones matriciales y computacionales

&#91;PR: multiplicación de matrices; notación O grande\]

**\[Def\]** Con V = {v₁,…,vₙ}:

- **Matriz de adyacencia** A: Aᵢⱼ = número de aristas entre vᵢ y vⱼ (en digrafos, de vᵢ a vⱼ). Para grafos no dirigidos es simétrica.
- **Matriz de incidencia** B (n × m): Bᵢₑ = 1 si vᵢ es extremo de e. En la versión orientada, ±1 según cola y cabeza.
- **Matriz de grados** D: diagonal con D\_ii = d(vᵢ).
- **Laplaciano** L = D − A.

**\[Teo\] (Aᵏ)ᵢⱼ cuenta los paseos de longitud k de vᵢ a vⱼ.**

*Demostración (inducción en k).* Para k = 1 es la definición. Un paseo de longitud k+1 de i a j es un paseo de longitud k de i a algún l seguido de una arista lj, así que su número es la suma sobre l de (Aᵏ)ᵢₗ·Aₗⱼ, que es exactamente (Aᵏ⁺¹)ᵢⱼ. ∎

*Corolarios.* La traza de A² es 2m. La traza de A³ es 6 veces el número de triángulos, porque cada triángulo se recorre desde 3 vértices de inicio en 2 sentidos. Advertencia: estos cuentan **paseos**, no caminos; para k ≥ 3 los paseos incluyen idas y vueltas por la misma arista. Por eso las centralidades basadas en potencias de A (Katz, autovector) premian ecos y redundancias \[II.6\], \[IV\].

**\[Teo\] Para todo vector x ∈ ℝⁿ:**

```latex
x^{\top} L x = \sum_{uv \in E} (x_u - x_v)^2
```

En consecuencia, L es semidefinida positiva, 0 es autovalor (con el vector constante) y la multiplicidad de 0 es igual al número de componentes conexas. La prueba completa y la conectividad algebraica (el segundo autovalor) se desarrollan en \[II.6\].

**Estructuras computacionales.** Comparación de costos para un grafo con n vértices y m aristas:

| Estructura | Memoria | ¿uv es arista? | Recorrer N(v) | Uso típico |
| --- | --- | --- | --- | --- |
| Matriz de adyacencia | O(n²) | O(1) | O(n) | grafos densos, álgebra lineal |
| Listas de adyacencia | O(n + m) | O(d(v)) | O(d(v)) | algoritmos de recorrido en general |
| Lista de aristas | O(m) | O(m) | O(m) | entrada/salida, Kruskal, streaming |
| CSR (*compressed sparse row*) | O(n + m) | O(log d(v)) con vecinos ordenados | O(d(v)), muy eficiente en caché | grafos grandes estáticos, cómputo científico |
| Hash de conjuntos de adyacencia | O(n + m) | O(1) esperado | O(d(v)) | grafos dinámicos |

Las redes sociales empíricas son casi siempre **ralas** (*sparse*): m es del orden de n y no de n². Con un millón de vértices, una matriz densa de bytes ocuparía un terabyte; las listas, unos pocos megabytes por cada millón de aristas. Esta elección determina qué algoritmos son viables.

### I.9 Estructura matemática, representación de datos y fenómeno observado

Esta sección es conceptual y sostiene todo lo que sigue. Hay tres niveles que el uso cotidiano de "la red" confunde.

1. **Fenómeno**: relaciones en el mundo (amistad, subordinación, deuda, cooperación, flujo de dinero). Son continuas, situadas, cambiantes, ambiguas, a menudo no observables directamente.
2. **Datos**: registros producidos por un procedimiento (encuesta, expediente, registro societario, log de un servidor, escucha telefónica). Cada procedimiento selecciona, distorsiona y omite de manera característica.
3. **Estructura matemática**: el grafo, un objeto abstracto con propiedades exactas.

Entre 1 y 2 media la **medición**; entre 2 y 3, la **operacionalización**: decidir qué es nodo, qué es vínculo, con qué umbral, en qué ventana de tiempo y con qué frontera. Un teorema vale sobre el nivel 3 sin condiciones. Su relevancia para el nivel 1 depende de la validez de ambas mediaciones.

**Tres ejemplos de que un mismo fenómeno da grafos distintos.**

- **Proyección de afiliación.** Personas que integran directorios de empresas forman un grafo bipartito persona–empresa. Proyectado sobre personas (dos personas vinculadas si comparten directorio), cada directorio de k miembros se vuelve un Kₖ completo: aparecen muchos triángulos y comunidades artificiales que vienen de la proyección y no de la interacción. Breiger formalizó esta dualidad entre personas y grupos en 1974 ("The Duality of Persons and Groups", *Social Forces*). Ver \[II.14\] y \[IV\].
- **Umbral.** Un grafo de llamadas con "vínculo si hubo al menos una llamada" y otro con "vínculo si hubo al menos diez" pueden tener estructuras de comunidad opuestas. No hay umbral "correcto" independiente de la pregunta.
- **Frontera.** Laumann, Marsden y Prensky (1983) llamaron *boundary specification problem* al problema de decidir quién entra en la red. Una red de "funcionarios de un ministerio" excluye a los intermediarios externos, que pueden ser justamente los actores relevantes. Esto se analiza en \[V\].

**Ausencia de arista.** En el nivel 3, la falta de una arista uv es un hecho definido. En el nivel 2, puede significar: no hay relación, no se preguntó, se preguntó y no se respondió, la fuente no lo registra, o se registró pero bajo otro identificador. Solo la primera lectura autoriza las inferencias que hacen los algoritmos. Esta distinción entre **mundo cerrado** (lo que no consta es falso) y **mundo abierto** (lo que no consta es desconocido) reaparece formalmente en RDF y OWL \[VII\] y es uno de los ejes de la crítica en \[V\].

### I.10 Ejercicios del Volumen I

Dificultad: (★) directo, (★★) requiere una idea, (★★★) desafiante. Las soluciones van en el Volumen X junto con la evaluación diagnóstica.

1. (★) Probá que en cualquier fiesta hay dos personas que conocen al mismo número de asistentes (suponé que conocer es simétrico).
2. (★) ¿Existe un grafo simple con secuencia de grados (3, 3, 3, 3, 3)? ¿Y (5, 5, 4, 3, 2, 1)? Justificá.
3. (★★) Probá que si G no es conexo, su complemento Ḡ es conexo y tiene diámetro a lo sumo 2.
4. (★★) Probá que todo árbol con un vértice de grado k tiene al menos k hojas.
5. (★★) Encontrá dos grafos no isomorfos con la misma secuencia de grados que sean ambos conexos.
6. (★★) Probá que el grafo de Petersen no es planar usando la fórmula de Euler. Pista: su cintura (longitud del ciclo más corto) es 5.
7. (★★) Mostrá un orden de los vértices de un grafo bipartito con 2k vértices en el que el coloreo voraz usa k colores.
8. (★★) Usando A³, escribí una fórmula para el coeficiente de agrupamiento global (transitividad) en términos de traza y sumas de entradas de A².
9. (★★★) Probá que un grafo con n vértices y más de n²/4 aristas contiene un triángulo (caso k = 3 del teorema de Turán, adelanto de \[II.8\]).
10. (★★★) Conceptual: elegí un fenómeno social que conozcas y describí tres operacionalizaciones distintas como grafo. Para cada una, indicá qué pregunta permite responder y qué inferencia volvería ilegítima.
11. (★★★) Conceptual: dado un grafo bipartito persona–evento, construí un ejemplo en que la proyección sobre personas tenga una comunidad muy densa que no corresponda a ninguna interacción directa entre esas personas.

## Glosario (primera parte)

*Nota: esta primera parte quedó incorporada y ampliada en el [Glosario completo](https://claude.ai/artifact/1Tugi2iEmaGPB9mxasRy8M), que cubre los Volúmenes I a VIII. Si hay diferencias, vale la versión del glosario completo.*

Términos del Volumen I, en orden alfabético. La columna "Trampa" señala confusiones frecuentes de traducción o de uso.

| Término | Inglés | Definición breve | Trampa | Ver |
| --- | --- | --- | --- | --- |
| Árbol | tree | grafo conexo y acíclico | las jerarquías reales rara vez lo son | I.5 |
| Arista | edge | par de vértices relacionados | "link", "tie", "vínculo" se usan como sinónimos según la disciplina | I.1 |
| Arco | arc | arista dirigida | en algunos textos, "arc" es cualquier arista | I.1 |
| Automorfismo | automorphism | isomorfismo de un grafo en sí mismo |  | I.4 |
| Bipartito | bipartite | vértices en dos clases sin aristas internas | la proyección pierde información | I.2, I.9 |
| Camino | path | paseo sin vértices repetidos | en español a veces se usa "camino" para *walk* | I.3 |
| Ciclo | cycle | camino cerrado sin repeticiones salvo inicio y fin |  | I.3 |
| Componente conexa | connected component | subgrafo conexo maximal | en digrafos hay componentes débiles y fuertes | I.3, III |
| Contracción | contraction | fusionar los extremos de una arista |  | I.4 |
| Cara | face | región de un dibujo plano | depende del dibujo | I.7 |
| Diámetro | diameter | máxima distancia entre vértices | infinito si no es conexo; muchas herramientas lo calculan solo sobre la componente gigante | I.3 |
| Dual | dual | grafo de caras de un grafo plano | depende del dibujo | I.7 |
| Grado | degree | número de vecinos (o aristas incidentes) | en multigrafos, un lazo suma 2 | I.3 |
| Hipergrafo | hypergraph | aristas como subconjuntos de cualquier tamaño |  | I.2 |
| Índice cromático | chromatic index | mínimo de colores para las aristas |  | I.7 |
| Inducido (subgrafo) | induced subgraph | contiene todas las aristas entre sus vértices |  | I.4 |
| Invariante | invariant | propiedad preservada por isomorfismo | igualdad de invariantes no implica isomorfismo | I.4 |
| Isomorfismo | isomorphism | biyección que preserva adyacencia |  | I.4 |
| Laplaciano | Laplacian | L = D − A | hay versiones normalizadas distintas | I.8, II.6 |
| Lazo | loop | arista de un vértice a sí mismo |  | I.1 |
| Menor | minor | se obtiene por borrado y contracción | no es lo mismo que subgrafo | I.4 |
| Multigrafo | multigraph | admite aristas múltiples | la definición varía entre textos | I.1 |
| Número cromático | chromatic number | mínimo de colores propios de vértices | calcularlo es NP-difícil | I.7 |
| Paseo | walk | sucesión de aristas consecutivas, con repeticiones | también "recorrido" | I.3 |
| Planar | planar | dibujable sin cruces | "plano" es el dibujo concreto | I.7 |
| Ralo | sparse | m del orden de n |  | I.8 |
| Regular | regular | todos los vértices con el mismo grado |  | I.6 |
| Sendero | trail | paseo sin aristas repetidas |  | I.3 |
| Vecindad | neighbourhood | vértices adyacentes a v | N(v) abierta, N\[v\] cerrada (incluye a v) | I.3 |
| Vértice | vertex (pl. vertices) | elemento del conjunto base | "nodo", "actor", "entidad" según la disciplina | I.1 |

## Bibliografía central verificada

Núcleo de la biblioteca: diez obras cuyos datos editoriales se verificaron en catálogos de bibliotecas, la editorial o el sitio del autor el 5 de noviembre de 2026. La bibliografía completa, clasificada en las categorías A a I, con cursos y videos, va en el Volumen IX.

### Lecturas para tener en el radar

Estas cuatro abren el recorrido; cada una cubre una región distinta del mapa.

- **[Graph Theory](https://diestel-graph-theory.com/) — Reinhard Diestel.** Referencia rigurosa para la teoría formal: conectividad, menores, coloración y demostraciones. 6.ª edición, Springer, Graduate Texts in Mathematics 173, ISBN 978-3-662-70106-5, 455 páginas. Es una edición mayor: agrega herramientas para el lema de regularidad, actualiza la teoría de *tangles* de menores y suma temas como la χ-acotación en grafos perfectos. Capítulos: fundamentos, emparejamientos y cubrimientos, conectividad, planaridad, coloración, flujos, extremal, grafos infinitos, Ramsey, ciclos hamiltonianos, grafos aleatorios, menores. **Acceso:** el texto principal se lee gratis en el sitio del autor ([vista previa](https://www.diestel-graph-theory.com/basic.html)); el eBook estándar en PDF cuesta 17,99 € y la edición profesional, que incluye pistas para todos los ejercicios, 73,99 € ([precios](https://diestel-graph-theory.com/prices.html)). **Nivel:** posgrado inicial; requiere madurez en demostraciones. **Limitación:** casi nada de algoritmos ni aplicaciones.
- **[Networks](https://global.oup.com/academic/product/networks-9780198805090) — Mark Newman.** Excelente puente entre estructuras de grafos, modelos de redes y fenómenos empíricos. 2.ª edición, Oxford University Press, 2018, ISBN 978-0-19-880509-0, unas 800 páginas. La segunda edición agrega material sobre detección de comunidades, contagio complejo, estadística de redes y redes multicapa ([Santa Fe Institute](https://web-prod.santafe.edu/news-center/news/networks-second-edition)). **Acceso:** pago. **Nivel:** grado avanzado; cálculo y álgebra lineal. **Limitación:** perspectiva de física estadística; trata poco la teoría sociológica y la inferencia estadística en sentido estricto.
- **[Network Science](https://networksciencebook.com/) — Albert-László Barabási.** Un recorrido por redes complejas: estructura, evolución, difusión y modelos generativos. Cambridge University Press, 2016, ISBN 978-1-107-07626-6. **Acceso:** la versión web es gratuita bajo licencia Creative Commons (CC BY-NC). Diez capítulos: teoría de grafos, redes aleatorias, propiedad libre de escala, modelo de Barabási-Albert, redes en evolución, correlaciones de grado, robustez, comunidades, propagación. **Nivel:** introductorio, con secciones avanzadas separadas. **Limitación importante:** se centra en nociones basadas en el grado, y la universalidad de las redes "libres de escala" que el libro defiende está empíricamente discutida (ver Broido y Clauset, 2019, en el Volumen IV). Leelo junto con su crítica.
- **[Networks, Crowds, and Markets](https://www.cs.cornell.edu/home/kleinber/networks-book/) — David Easley y Jon Kleinberg.** Particularmente útil para conectar grafos con comportamiento estratégico, información, mercados y teoría de juegos. Cambridge University Press, 2010, ISBN 978-0-521-19533-1. **Acceso:** el borrador completo previo a la publicación se descarga gratis desde el sitio de Cornell. Incluye vínculos fuertes y débiles, relaciones positivas y negativas (balance estructural), poder en redes de negociación, cascadas, mundo pequeño y epidemias. **Nivel:** grado inicial, sin prerrequisitos formales, con secciones avanzadas opcionales. **Limitación:** demostraciones livianas; poco sobre medición y datos reales.

### Textos formales complementarios

| Obra | Datos verificados | Rol en el tratado | Acceso |
| --- | --- | --- | --- |
| [Introduction to Graph Theory](https://lmbp.uca.fr/biblio/notice.php?num=12652) — Douglas B. West | 2.ª ed., Prentice Hall, 2001, ISBN 0-13-014400-2, 588 p. | El mejor texto de grado para aprender a demostrar; ejercicios graduados en abundancia | Pago |
| [Graph Theory](https://link.springer.com/book/9781849966900) — J. A. Bondy y U. S. R. Murty | Springer, GTM 244, 2008, ISBN 978-1-84628-969-9 | Puente entre teoría y algoritmos; incluye flujos, complejidad, método probabilístico y problemas abiertos | Pago (accesible por bibliotecas universitarias vía SpringerLink) |
| [Combinatorial Problems and Exercises](https://www.lehmanns.ch/shop/mathematik-informatik/8054394-9780821842621-combinatorial-problems-and-exercises) — László Lovász | 2.ª ed., AMS Chelsea, 2007, ISBN 978-0-8218-4262-1 (primera edición 1979) | Todo el material como problemas, con pistas y soluciones completas; ideal para el Volumen X | Pago |
| [Large Networks and Graph Limits](https://bookstore.ams.org/COLL/60) — László Lovász | AMS Colloquium Publications 60, 2012, ISBN 978-0-8218-9085-1 | Teoría de límites de grafos y homomorfismos; nivel de investigación, para \[VIII\] | Pago |

### Análisis de redes sociales

| Obra | Datos verificados | Rol en el tratado | Acceso |
| --- | --- | --- | --- |
| [Social Network Analysis: Methods and Applications](https://doi.org/10.1017/CBO9780511815478) — Stanley Wasserman y Katherine Faust | Cambridge University Press, 1994, ISBN 0-521-38707-8 | Referencia metodológica clásica: centralidad, equivalencia estructural, modelos de bloques, díadas y tríadas, modelos estadísticos | Pago; disponible en varias bibliotecas universitarias argentinas |
| [Social and Economic Networks](https://www.schweitzer-online.de/en/buch/Jackson/Social-Economic-Networks/9780691134406/A3031884/) — Matthew O. Jackson | Princeton University Press, 2008, ISBN 978-0-691-13440-6 | Formación estratégica de redes, difusión, aprendizaje y juegos en redes; perspectiva económica | Pago |

**Nota de método.** Ninguna obra se incluye por popularidad. Cada una está ligada a volúmenes concretos del tratado. Las limitaciones se señalan para que se lean en diálogo con su crítica.

## Plan de próximas entregas

El orden propuesto prioriza la evaluación diagnóstica, porque sus resultados permiten decidir qué partes de los volúmenes siguientes conviene profundizar y cuáles alcanza con resumir. Los módulos son independientes: se puede pedir cualquier volumen en cualquier orden.

| Entrega | Contenido | Por qué en ese lugar |
| --- | --- | --- |
| 2 | Volumen X, parte 1: evaluación diagnóstica (40+ preguntas), soluciones separadas y matriz de fortalezas y lagunas | Calibra todo lo que sigue |
| 3 | Volumen II: conectividad, Menger, flujos, Hall, coloración, eulerianos y hamiltonianos, espectral | Las dualidades min-max son la base de casi todo el resto |
| 4 | Volumen II (cont.): aleatorios, extremal, perfectos y chordales, treewidth, complejidad, temporales, multicapa, hipergrafos, incertidumbre |  |
| 5 | Volumen III: algoritmos con pseudocódigo, pruebas de corrección e implementaciones de referencia en Python | Se apoya en II |
| 6 | Volúmenes IV y V: sociología relacional, poder, epistemología y crítica de errores | Requiere el vocabulario técnico de II y III para criticarlo con precisión |
| 7 | Volumen VI: criminología, crimen organizado y derechos humanos | Aplica IV y V a casos públicos verificables |
| 8 | Volumen VII: grafos de conocimiento, procedencia, evidencia y telemetría |  |
| 9 | Volumen VIII: fronteras de investigación y problemas abiertos |  |
| 10 | Volúmenes IX y X: biblioteca completa, catálogo de cursos y videos, itinerarios, laboratorio de 20+ ejercicios y matriz consolidada | Cierra con lo que se usa de forma continua |
