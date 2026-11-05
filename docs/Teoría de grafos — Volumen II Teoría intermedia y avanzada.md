# Teoría de grafos — Volumen II: Teoría intermedia y avanzada

Nov 5, 2026 · @Anna Tchijova

## Cómo leer este volumen

Este volumen cubre las quince áreas de la Parte II del pedido. Cada sección sigue la misma estructura: definiciones, resultados centrales con demostración (o con referencia precisa cuando la prueba es larga), y un cierre con **qué pregunta permite responder**, **qué no permite responder** y **qué condiciones tienen que cumplirse**. Las etiquetas \[Def\], \[Teo\], \[Emp\], \[Int\], \[Hip\] y \[Heur\] se usan como en el Volumen 0.

**Prerrequisitos.** Volumen I completo. Para II.6, álgebra lineal (autovalores y autovectores de matrices simétricas). Para II.7, II.8 y II.15, probabilidad discreta (esperanza, linealidad, desigualdad de Markov). Para II.10 a II.12, la noción de algoritmo y de cota O grande.

**Fuentes de contraste.** Salvo indicación, las demostraciones siguen o pueden contrastarse con Diestel (6.ª ed.), Bondy y Murty (GTM 244) y West (2.ª ed.). Las referencias a artículos se dan por autor, año y revista; la verificación bibliográfica completa, con enlaces, se consolida en el Volumen IX.

## II.1 Conectividad, cortes y el teorema de Menger

**\[Def\]** Un **conjunto separador** de vértices es un S ⊆ V tal que G − S es desconectado. G es **k-conexo** si n > k y no tiene separadores de menos de k vértices. La **conectividad por vértices** κ(G) es el mayor k para el cual G es k-conexo. Análogamente, un **corte de aristas** es un F ⊆ E cuya remoción desconecta, y la **conectividad por aristas** λ(G) es el tamaño mínimo de uno. Un **vértice de corte** es un separador de tamaño 1; un **puente**, un corte de aristas de tamaño 1. Los **bloques** son los subgrafos maximales sin vértice de corte; se organizan en un árbol (el árbol de bloques), lo que permite estudiar cada bloque por separado.

**\[Teo\] (Whitney, 1932)** Para todo grafo G no trivial, κ(G) ≤ λ(G) ≤ δ(G).

*Demostración.* (λ ≤ δ) Las aristas incidentes en un vértice de grado mínimo forman un corte de tamaño δ. (κ ≤ λ) Sea F un corte mínimo de aristas, entre X y Y = V ∖ X. Si todo vértice de X es adyacente a todo vértice de Y, entonces |F| = |X|·|Y| ≥ n − 1 ≥ κ. Si no, existen x ∈ X e y ∈ Y no adyacentes. Construimos S tomando, por cada arista de F, su extremo en X, salvo que ese extremo sea x, en cuyo caso tomamos su extremo en Y. Entonces |S| ≤ |F| y x, y ∉ S (y no entra porque x e y no son adyacentes). Todo camino de x a y usa alguna arista ab de F con a ∈ X: si a ≠ x, el camino pasa por a ∈ S; si a = x, pasa por b ∈ S. Así S separa x de y, y κ ≤ |S| ≤ λ. ∎

Las desigualdades pueden ser estrictas: dos copias de K₄ que comparten un vértice tienen κ = 1, λ = 3, δ = 3.

**\[Teo\] (Menger, 1927)** Sean a y b vértices no adyacentes. El número mínimo de vértices que separan a de b es igual al número máximo de caminos de a a b **internamente disjuntos** (sin vértices interiores comunes). Versión por aristas: el número mínimo de aristas que separan a de b es igual al máximo de caminos a–b disjuntos en aristas. Versión por conjuntos: para A, B ⊆ V, el mínimo de un conjunto que separa A de B es igual al máximo de caminos A–B disjuntos.

*Estructura de la prueba.* La desigualdad "máximo ≤ mínimo" es fácil: cada uno de los caminos disjuntos tiene que pasar por un vértice distinto del separador. La dificultad está en la otra dirección. La prueba más instructiva para este tratado la obtiene como corolario del teorema de flujo máximo y corte mínimo (II.2): se reemplaza cada vértice v por dos copias v⁻ y v⁺ unidas por un arco de capacidad 1, cada arista por arcos de capacidad infinita, y se observa que un corte finito corresponde a un separador de vértices. Diestel (cap. 3) da tres pruebas combinatorias independientes.

*Corolario (Whitney).* G es k-conexo si y solo si entre todo par de vértices hay k caminos internamente disjuntos.

**Qué pregunta permite responder.** Cuán robusta es la conexión entre dos partes ante la eliminación de actores o vínculos, y cuáles son los conjuntos mínimos cuya eliminación las desconecta. El teorema transforma una pregunta sobre todos los separadores posibles en una sobre caminos, que son certificados verificables: si se exhiben k caminos disjuntos y un separador de tamaño k, ambos números quedan probados.

**Qué no permite responder.** Si esos caminos se usan, ni para qué. Un separador mínimo es un hecho estructural del grafo observado, no un rol social: decir "si se elimina a estas tres personas la red se desconecta" presupone que el grafo representa completamente las vías de comunicación posibles, lo cual casi nunca es cierto con datos parciales. Una red puede parecer frágil solo porque faltan aristas en los datos.

**Condiciones.** Grafo finito; para la versión por vértices, a y b no adyacentes; la conclusión vale para el grafo tal como está especificado, de modo que la validez sustantiva depende de la completitud de las aristas (ver II.15).

## II.2 Flujos, cortes mínimos y el teorema max-flow/min-cut

**\[Def\]** Una **red** es un digrafo con dos vértices distinguidos, fuente s y sumidero t, y capacidades c(u,v) ≥ 0 en los arcos. Un **flujo** es una función f sobre los arcos que cumple: (1) capacidad, 0 ≤ f(u,v) ≤ c(u,v); (2) conservación, en todo vértice distinto de s y t, lo que entra es igual a lo que sale. Su **valor** |f| es el flujo neto que sale de s. Un **corte s–t** es una partición (S, T) con s ∈ S y t ∈ T; su capacidad c(S,T) es la suma de capacidades de los arcos que van de S a T.

**\[Teo\] (Cota débil)** Para todo flujo f y todo corte (S,T), |f| ≤ c(S,T). *Prueba:* sumando la conservación sobre los vértices de S, |f| es igual al flujo de S a T menos el de T a S, que es a lo sumo c(S,T). ∎

**\[Def\] Red residual.** Dado f, la red residual G\_f tiene un arco (u,v) con capacidad residual c(u,v) − f(u,v) si es positiva, y un arco inverso (v,u) con capacidad f(u,v) si f(u,v) > 0 (permite "devolver" flujo). Un **camino aumentante** es un camino de s a t en G\_f.

**\[Teo\] (Ford y Fulkerson, 1956; también Elias, Feinstein y Shannon, 1956)** Son equivalentes: (a) f es un flujo máximo; (b) no existe camino aumentante en G\_f; (c) |f| = c(S,T) para algún corte. En particular, el valor máximo de un flujo es igual a la capacidad mínima de un corte.

*Demostración.* (a ⇒ b) Si hubiera un camino aumentante, se podría empujar a lo largo de él la mínima capacidad residual del camino y aumentar |f|. (c ⇒ a) Por la cota débil, ningún flujo supera c(S,T) = |f|. (b ⇒ c) Sea S el conjunto de vértices alcanzables desde s en G\_f, y T el resto; t ∈ T porque no hay camino aumentante. Todo arco de S a T está saturado (si no, su extremo en T sería alcanzable), y todo arco de T a S tiene flujo 0 (si no, el arco inverso residual haría alcanzable su origen). Entonces |f| = flujo de S a T − flujo de T a S = c(S,T). ∎

**\[Teo\] Integralidad.** Si todas las capacidades son enteras, existe un flujo máximo con valores enteros, y el método de Ford-Fulkerson lo encuentra. *Prueba:* cada aumento empuja una cantidad entera, y el valor está acotado. ∎ Esta propiedad es la que permite deducir resultados combinatorios (Menger, König, Hall) a partir de flujos.

**Algoritmos.** Ford-Fulkerson con caminos arbitrarios puede no terminar con capacidades irracionales. **Edmonds-Karp** (1972) elige siempre el camino aumentante más corto en número de arcos, y termina en O(n·m²). **Dinic** (1970) trabaja por fases con flujos bloqueantes, en O(n²·m). Existen algoritmos mucho más rápidos: Chen, Kyng, Liu, Peng, Probst Gutenberg y Sachdeva anunciaron en 2022 un algoritmo de tiempo casi lineal, m^(1+o(1)), de gran importancia teórica pero no de uso práctico corriente. Implementación y ejemplos trabajados en el Volumen III.

**Corte mínimo global** (sin s y t fijos): Stoer-Wagner lo resuelve de forma determinística; el algoritmo de contracción aleatoria de Karger es un ejemplo clásico de algoritmo probabilístico con garantía de éxito con alta probabilidad.

**Qué pregunta permite responder.** Cuánto puede transportarse como máximo entre dos puntos dadas las capacidades, y dónde están los cuellos de botella estructurales. Sirve para asignación (emparejamientos), para robustez (Menger) y para segmentación de imágenes y de grafos.

**Qué no permite responder.** Cuánto fluyó efectivamente, ni por dónde. Un flujo máximo es un objeto óptimo, no una descripción de lo ocurrido: si se calcula sobre una red de transferencias, el resultado describe lo que **podría** pasar con esas capacidades, no lo que pasó. Además, el corte mínimo puede no ser único, y elegir uno para la interpretación es una decisión.

**Condiciones.** Capacidades no negativas y conocidas; conservación en vértices intermedios, lo cual no vale si los nodos acumulan, generan o pierden lo que fluye (dinero que se retira en efectivo, información que se replica). Para fenómenos con pérdidas o generación existen modelos de flujo generalizado; para fenómenos que se copian, como la información, el modelo de flujo es inadecuado y conviene pensar en difusión (Volumen IV).

## II.3 Emparejamientos: Hall, König, Berge y Tutte

**\[Def\]** Un **emparejamiento** (*matching*) es un conjunto de aristas sin extremos comunes. Es **perfecto** si cubre todos los vértices. ν(G) es el tamaño máximo de un emparejamiento. Un **cubrimiento por vértices** es un conjunto de vértices que toca todas las aristas; τ(G) es su tamaño mínimo. Un **conjunto independiente** no tiene aristas internas; α(G) es su tamaño máximo.

**\[Teo\] (Gallai)** α(G) + τ(G) = n. *Prueba:* S es independiente si y solo si V ∖ S es un cubrimiento. ∎ Por eso maximizar conjuntos independientes y minimizar cubrimientos son el mismo problema.

**\[Teo\] (Hall, 1935)** Un grafo bipartito con clases X e Y tiene un emparejamiento que cubre X si y solo si |N(S)| ≥ |S| para todo S ⊆ X.

*Demostración.* La necesidad es clara: los vértices de S necesitan compañeros distintos. Suficiencia, por inducción en |X|; el caso |X| = 1 es inmediato. *Caso 1:* todo subconjunto no vacío y propio S de X cumple |N(S)| ≥ |S| + 1. Emparejamos un x cualquiera con un vecino y, y quitamos ambos. En el grafo restante, cada S ⊆ X ∖ {x} perdió a lo sumo un vecino, así que sigue cumpliendo la condición, y por inducción se completa. *Caso 2:* existe S₀ no vacío y propio con |N(S₀)| = |S₀|. Por inducción, S₀ se empareja con N(S₀). Falta emparejar X ∖ S₀ dentro de Y ∖ N(S₀). Para T ⊆ X ∖ S₀, sus vecinos fuera de N(S₀) son al menos |N(T ∪ S₀)| − |N(S₀)| ≥ (|T| + |S₀|) − |S₀| = |T|. La condición de Hall vale en el grafo restante, y por inducción se completa. ∎

*Corolario.* Todo grafo bipartito k-regular con k ≥ 1 tiene un emparejamiento perfecto (contar aristas que salen de S y llegan a N(S)).

**\[Teo\] (König, 1931; Egerváry, 1931)** En un grafo bipartito, ν(G) = τ(G). Es otra dualidad min-max, y se deduce de max-flow/min-cut con integralidad. En grafos generales solo vale ν ≤ τ ≤ 2ν (el triángulo tiene ν = 1 y τ = 2).

**\[Teo\] (Berge, 1957)** Un emparejamiento M es máximo si y solo si no existe un camino **M-aumentante**: un camino que alterna aristas fuera y dentro de M y empieza y termina en vértices no cubiertos. *Idea de la prueba:* si M' es mayor que M, la diferencia simétrica M Δ M' se descompone en caminos y ciclos alternantes, y alguno de los caminos tiene más aristas de M' que de M: ese es un camino aumentante. ∎ Este teorema es la base de todos los algoritmos de emparejamiento.

**\[Teo\] (Tutte, 1947)** G tiene un emparejamiento perfecto si y solo si, para todo S ⊆ V, el número de componentes de G − S con cantidad impar de vértices es a lo sumo |S|. *Prueba:* Diestel, cap. 2.

**Algoritmos.** En bipartitos, Hopcroft-Karp en O(m·√n). En grafos generales, el algoritmo de las flores (*blossom*) de Edmonds (1965) fue el primero polinomial, y el artículo en que lo presentó es también un texto fundacional de la idea de "algoritmo eficiente" como algoritmo de tiempo polinomial.

**Emparejamientos estables.** Gale y Shapley (1962) mostraron que, con preferencias de ambos lados, siempre existe un emparejamiento estable (ningún par lo abandonaría de común acuerdo), y dieron un algoritmo para hallarlo. El algoritmo favorece sistemáticamente al lado que propone: es un ejemplo claro de que un procedimiento "óptimo" incorpora decisiones distributivas. Roth y Shapley recibieron el Premio Nobel de Economía en 2012 en parte por esta línea.

**Qué pregunta permite responder.** Si es posible una asignación uno a uno compatible con las restricciones (personas y tareas, causas y tribunales, revisores y artículos) y, si no, cuál es el obstáculo: el conjunto S que viola Hall es un certificado de imposibilidad.

**Qué no permite responder.** Si la asignación es justa o deseable. Un emparejamiento máximo puede ser uno cualquiera entre muchos; elegir entre ellos requiere pesos o preferencias, y esa elección es normativa.

**Condiciones.** Relación uno a uno; restricciones conocidas y binarias (compatible o no). Si hay capacidades (un tribunal recibe varias causas), el modelo adecuado es un flujo o un *b*-emparejamiento.

## II.4 Coloración, número cromático y optimización combinatoria

El Volumen I (I.7) introdujo χ, la cota voraz χ ≤ Δ + 1, Brooks y Vizing. Aquí se agregan las cotas inferiores, la distancia entre ellas y las cotas superiores, y la conexión con otros problemas de optimización.

**\[Teo\] Cotas inferiores.** ω(G) ≤ χ(G), donde ω es el tamaño de la mayor clique, porque los vértices de una clique necesitan colores distintos. También n/α(G) ≤ χ(G), porque cada clase de color es un conjunto independiente.

**\[Teo\] (Mycielski, 1955) La brecha entre ω y χ puede ser arbitraria:** para todo k existe un grafo sin triángulos (ω = 2) con χ = k. *Construcción:* dado G con vértices v₁,…,vₙ, se agregan copias u₁,…,uₙ, donde uᵢ es adyacente a los vecinos de vᵢ, y un vértice w adyacente a todos los uᵢ. La construcción no crea triángulos y aumenta χ en exactamente 1. Aplicada al pentágono C₅ (χ = 3), da el grafo de Grötzsch, con χ = 4. Erdős (1959) mostró algo más fuerte con el método probabilístico: existen grafos con cintura y número cromático ambos arbitrariamente grandes. **Moraleja:** el número cromático puede ser alto por razones globales que no se ven en ninguna región local del grafo.

**\[Def\] Polinomio cromático.** P(G, k) cuenta las k-coloraciones propias. Cumple la recurrencia de borrado y contracción, P(G, k) = P(G − e, k) − P(G / e, k), y χ(G) es el menor k con P(G, k) > 0. Para un árbol con n vértices, P = k(k − 1)ⁿ⁻¹.

**Complejidad.** Decidir χ ≤ 3 es NP-completo, incluso en grafos planares de grado máximo 4. Calcular χ es además difícil de aproximar: Zuckerman (2007) mostró que, salvo que P = NP, no existe aproximación polinomial con factor n^(1−ε) para ningún ε > 0. En cambio, decidir χ ≤ 2 es lineal (bipartición, I.2), y en clases especiales (grafos de intervalos, chordales, perfectos: II.9) χ se calcula en tiempo polinomial.

**Problemas emparentados.** Clique máxima, conjunto independiente máximo y cubrimiento mínimo por vértices son NP-difíciles y están conectados: S es independiente en G si y solo si es clique en el complemento, y por Gallai (II.3) α + τ = n. La coloración de listas (cada vértice tiene su lista de colores permitidos) generaliza la coloración y modela restricciones heterogéneas.

**Qué pregunta permite responder.** Cuántos recursos excluyentes hacen falta para que ningún par en conflicto comparta recurso: turnos, salas, frecuencias. Una cota inferior (una clique grande) certifica que no se puede hacer con menos.

**Qué no permite responder.** En instancias grandes, cuál es exactamente el óptimo: lo que se obtiene en la práctica son coloraciones heurísticas cuya calidad hay que reportar junto con la mejor cota inferior conocida, no como si fueran óptimas.

**Condiciones.** Conflictos binarios y simétricos. Si un conflicto involucra a tres o más elementos a la vez, el modelo correcto es la coloración de hipergrafos (II.14).

## II.5 Grafos eulerianos y hamiltonianos

Estos dos problemas parecen gemelos (recorrer todas las aristas, recorrer todos los vértices) y, sin embargo, uno es fácil y el otro es NP-completo. La comparación es la mejor introducción intuitiva a la complejidad computacional.

**\[Teo\] (Euler, 1736; prueba completa de Hierholzer, 1873)** Un grafo conexo tiene un circuito euleriano si y solo si todos sus vértices tienen grado par.

*Demostración de la suficiencia.* Sea W un sendero de longitud máxima. W es cerrado: si terminara en un vértice v distinto del inicial, W habría usado un número impar de aristas incidentes en v, y como d(v) es par quedaría una sin usar para extenderlo. Si W no usara todas las aristas, por conexión habría una arista no usada uw con u en W; recorriendo W a partir de u y agregando uw se obtiene un sendero más largo. Contradicción. ∎ (La necesidad está en la Evaluación, ítem B4.)

*Variantes.* Un sendero euleriano abierto existe si y solo si hay exactamente dos vértices de grado impar, que son sus extremos. En digrafos conexos, hay circuito euleriano si y solo si en cada vértice el grado de entrada es igual al de salida. El algoritmo de Hierholzer lo construye en O(m). El **problema del cartero chino** (recorrer todas las aristas con costo mínimo, repitiendo si hace falta) también es polinomial, vía emparejamientos de los vértices impares.

**\[Def\]** Un **ciclo hamiltoniano** pasa exactamente una vez por cada vértice. Decidir si existe es NP-completo (Karp, 1972).

**\[Teo\] (Ore, 1960)** Si n ≥ 3 y d(u) + d(v) ≥ n para todo par de vértices no adyacentes, G es hamiltoniano. *Corolario (Dirac, 1952):* basta δ ≥ n/2.

*Demostración.* Supongamos un contraejemplo y agreguemos aristas mientras siga sin ser hamiltoniano; la condición se preserva. Llegamos a un G maximal no hamiltoniano: agregar cualquier arista faltante uv crea un ciclo hamiltoniano, que necesariamente usa uv. Entonces G tiene un camino hamiltoniano u = x₁, x₂, …, xₙ = v. Sea I el conjunto de índices i con xᵢ₊₁ adyacente a u, y J el de índices i con xᵢ adyacente a v. Ambos están en {1, …, n − 1}, con |I| = d(u) y |J| = d(v), así que |I| + |J| ≥ n > n − 1 y comparten un índice i. Entonces u xᵢ₊₁ … xₙ xᵢ xᵢ₋₁ … x₁ es un ciclo hamiltoniano en G. Contradicción. ∎

El ejemplo de dos Kₖ que comparten un vértice (Evaluación, B6) muestra que las cotas son casi óptimas. Son condiciones **suficientes**, no necesarias: un ciclo Cₙ es hamiltoniano con δ = 2.

**El problema del viajante (TSP).** Encontrar el ciclo hamiltoniano de costo mínimo. Es NP-difícil; en el caso métrico (costos que cumplen la desigualdad triangular), el algoritmo de Christofides (1976) garantiza un factor 3/2, y Karlin, Klein y Oveis Gharan (2021) lo mejoraron por un margen ínfimo con un algoritmo aleatorizado. Sin desigualdad triangular, no hay aproximación con ningún factor constante salvo que P = NP. En la práctica, solvers exactos como Concorde resuelven instancias de decenas de miles de ciudades: NP-difícil no significa irresoluble en casos concretos.

**Qué pregunta permite responder.** Si existe un recorrido completo bajo restricciones, y cuánto cuesta como mínimo. En investigación, el caso euleriano modela la reconstrucción de secuencias a partir de fragmentos superpuestos (es la base del ensamblado de genomas con grafos de De Bruijn), lo cual sugiere un uso análogo para reconstruir trayectorias a partir de fragmentos de registros.

**Qué no permite responder.** Si el recorrido reconstruido es el que ocurrió: puede haber muchos circuitos eulerianos compatibles con los mismos fragmentos, y elegir uno es una hipótesis.

**Condiciones.** Conexión del grafo (para Euler), desigualdad triangular para las garantías de aproximación del viajante.

## II.6 Teoría espectral

&#91;PR: autovalores de matrices simétricas reales; teorema espectral: tienen autovalores reales y una base ortonormal de autovectores\]

La teoría espectral estudia un grafo a través de los autovalores de matrices asociadas. Es la base matemática de la centralidad de autovector, de PageRank, del clustering espectral y de buena parte del aprendizaje sobre grafos (Volumen VIII).

**Espectro de adyacencia.** Para G no dirigido, A es simétrica, con autovalores reales λ₁ ≥ λ₂ ≥ … ≥ λₙ.

- **\[Teo\]** El grado promedio d̄ cumple d̄ ≤ λ₁ ≤ Δ. *Prueba:* la cota inferior se obtiene evaluando el cociente de Rayleigh xᵀAx / xᵀx en el vector de unos, que da 2m/n; la superior, tomando el autovector de λ₁ y mirando su coordenada de mayor valor absoluto. ∎
- **\[Teo\] (Perron-Frobenius)** Si G es conexo, λ₁ es simple y tiene un autovector con todas sus coordenadas positivas. Ese vector es la **centralidad de autovector**.
- **\[Teo\]** G es bipartito si y solo si su espectro es simétrico respecto de 0.

**Contraejemplo: el espectro no determina el grafo.** K₁,₄ (una estrella de cinco vértices) y la unión de C₄ con un vértice aislado son **coespectrales**: ambos tienen autovalores 2, 0, 0, 0, −2. Uno es conexo y el otro no. El espectro es un invariante poderoso pero incompleto.

**El laplaciano L = D − A.** Para todo vector x, xᵀLx es la suma, sobre las aristas uv, de (xᵤ − xᵥ)², así que L es semidefinida positiva y sus autovalores cumplen 0 = μ₁ ≤ μ₂ ≤ … ≤ μₙ.

**\[Teo\] La multiplicidad de 0 en L es el número de componentes conexas.** *Prueba:* Lx = 0 equivale a xᵀLx = 0, es decir, xᵤ = xᵥ para toda arista: x es constante en cada componente. El espacio de esos vectores tiene dimensión igual al número de componentes. ∎

**Conectividad algebraica.** Fiedler (1973) llamó así a μ₂, que es positivo si y solo si G es conexo, y que cumple μ₂ ≤ κ(G) para grafos no completos. El autovector asociado, el **vector de Fiedler**, asigna a cada vértice un número; cortar por su signo da una bipartición que tiende a cortar pocas aristas.

**\[Teo\] (Desigualdad de Cheeger para grafos)** Sea h(G) la constante isoperimétrica: el mínimo, sobre los conjuntos S con a lo sumo la mitad del "volumen" del grafo, de la razón entre las aristas que salen de S y el volumen de S. Para el laplaciano normalizado, con segundo autovalor ν₂, vale ν₂/2 ≤ h(G) ≤ √(2ν₂). *Lectura:* un μ₂ chico garantiza que existe un cuello de botella, y un μ₂ grande garantiza que no existe. Prueba en Chung, *Spectral Graph Theory* (AMS, 1997).

**Clustering espectral.** Se toman los k autovectores de menor autovalor de un laplaciano (normalizado), se usa cada vértice como un punto en ℝᵏ y se aplica k-means. Von Luxburg ("A tutorial on spectral clustering", *Statistics and Computing*, 2007) es la referencia introductoria estándar. Es \[Heur\]: la relajación espectral aproxima un problema de corte NP-difícil, sin garantía general de recuperar la partición óptima; en modelos de bloques estocásticos (Volumen IV) sí hay garantías de recuperación bajo condiciones de separación.

**Caminatas aleatorias.** La matriz de transición P = D⁻¹A gobierna la caminata aleatoria. Si G es conexo y no bipartito, la distribución converge a la estacionaria, proporcional al grado, y la velocidad de convergencia depende de la brecha espectral. PageRank es una caminata aleatoria modificada con teletransporte (Volumen III).

**Qué pregunta permite responder.** Si un grafo tiene cuellos de botella, cuántas componentes tiene, qué tan rápido se mezcla una caminata aleatoria, y cómo partirlo de manera aproximada.

**Qué no permite responder.** Qué significan socialmente los grupos que surgen. La partición espectral optimiza una relajación de un criterio de corte; que coincida con grupos sociales reales es una hipótesis empírica.

**Condiciones.** Las garantías valen para grafos no dirigidos (en digrafos las matrices no son simétricas y la teoría es distinta). En grafos con grados muy heterogéneos, el laplaciano sin normalizar tiende a aislar vértices de grado bajo; suele preferirse el normalizado. Los resultados son sensibles a la presencia de pocas aristas que conecten regiones: un error de datos puede cambiar el vector de Fiedler.

## II.7 Grafos aleatorios y expansores

Los grafos aleatorios cumplen dos funciones distintas que conviene no confundir: son **objetos matemáticos** cuyas propiedades típicas se demuestran, y son **modelos nulos** contra los cuales se decide si una red observada tiene algo llamativo. La segunda función es la más importante para la investigación social, y la más descuidada.

**\[Def\] Modelos de Erdős–Rényi.** G(n, m): se elige uniformemente un grafo con n vértices y m aristas. G(n, p): cada uno de los n(n−1)/2 pares es arista con probabilidad p, de forma independiente. Para m ≈ p·n(n−1)/2 ambos modelos se comportan casi igual. "Casi seguramente" (*asymptotically almost surely*) significa con probabilidad que tiende a 1 cuando n → ∞.

**\[Teo\] Propiedades de G(n, p) con p = c/n.**

1. *Grados:* el grado de un vértice es binomial y se aproxima a una Poisson de media c. No hay vértices de grado muy alto: la distribución decae más rápido que exponencialmente.
2. *Transición de fase (Erdős y Rényi, 1960):* si c < 1, todas las componentes tienen O(log n) vértices; si c > 1, hay una única componente gigante con una fracción positiva de los vértices.
3. *Conexión:* el grafo es conexo casi seguramente si p ≥ (ln n + ω(1))/n y desconectado si p ≤ (ln n − ω(1))/n.
4. *Agrupamiento:* la probabilidad de que dos vecinos de un vértice sean adyacentes es p = c/n, que tiende a 0.
5. *Distancias:* el diámetro de la componente gigante es del orden de log n.

*Técnicas de prueba:* el método del primer momento (si la esperanza del número de objetos tiende a 0, casi seguramente no hay ninguno, por Markov) y el del segundo momento (si la varianza es pequeña respecto de la esperanza al cuadrado, casi seguramente hay alguno, por Chebyshev). Referencias: Bollobás, *Random Graphs* (2.ª ed., 2001); Frieze y Karoński, *Introduction to Random Graphs* (2015, con versión gratuita del autor); Alon y Spencer, *The Probabilistic Method*.

**\[Emp\] Las redes sociales no se parecen a G(n, p).** Tienen agrupamiento alto, grados muy heterogéneos y correlaciones de grado. Por eso G(n, p) es un mal modelo de redes sociales, pero un buen **punto de comparación**: medir cuánto se aparta la red observada es informativo.

**Modelos nulos más adecuados.** El **modelo de configuración** genera grafos aleatorios con una secuencia de grados dada; preserva los grados y aleatoriza todo lo demás. Comparar contra él responde "¿esto se explica solo por la distribución de grados?". Es, por ejemplo, el modelo nulo implícito en la modularidad. El modelo de Watts y Strogatz (1998) y el de Barabási y Albert (1999) se tratan en el Volumen IV como modelos generativos, no como nulos.

**\[Def\] Expansores.** Una familia de grafos d-regulares con d fijo es de **expansores** si su constante isoperimétrica h(G) está acotada inferiormente por una constante positiva: todo conjunto de a lo sumo la mitad de los vértices tiene proporcionalmente muchas aristas hacia afuera. Por Cheeger (II.6), equivale a una brecha espectral acotada. Son ralos y a la vez muy conectados.

**\[Teo\]** Para d ≥ 3 fijo, un grafo d-regular aleatorio es un expansor casi seguramente. Construcciones explícitas: los grafos de Ramanujan (Lubotzky, Phillips y Sarnak, 1988; Margulis, 1988) alcanzan la brecha espectral óptima, que es d − 2√(d−1).

*Usos:* códigos correctores de errores, desaleatorización, redes de comunicación robustas, criptografía. Un resultado de interés epistemológico: en un expansor, todo conjunto mediano "se mezcla" con el resto, de modo que no hay comunidades bien definidas; si un algoritmo encuentra comunidades en un expansor, está inventando estructura.

**Qué pregunta permite responder.** Qué propiedades son esperables por azar dadas ciertas restricciones (número de aristas, secuencia de grados), y por tanto si una propiedad observada requiere una explicación adicional.

**Qué no permite responder.** Qué mecanismo generó la red. Que un modelo reproduzca una propiedad no prueba que sea el mecanismo real: muchos mecanismos distintos producen las mismas regularidades.

**Condiciones.** Los resultados son asintóticos; para redes de cientos de nodos hay que simular el modelo nulo en lugar de usar fórmulas límite. Y la elección del modelo nulo es una decisión sustantiva: cambia qué cuenta como "llamativo".

## II.8 Teoría extremal y teoría de Ramsey

La teoría extremal pregunta cuánto de algo (aristas, grado mínimo) obliga a que aparezca una estructura. La de Ramsey, que todo objeto suficientemente grande contiene orden, por desordenado que sea. Ambas tienen una consecuencia metodológica directa: **en datos grandes, ciertas estructuras aparecen necesariamente, sin que signifiquen nada.**

**\[Teo\] (Mantel, 1907)** Un grafo con n vértices sin triángulos tiene a lo sumo n²/4 aristas, y la cota se alcanza con K\_{n/2, n/2}.

*Demostración.* Sin triángulos, los extremos de una arista uv no tienen vecinos comunes, así que d(u) + d(v) ≤ n. Sumando sobre todas las aristas, cada vértice v aparece d(v) veces, y la suma es Σ d(v)². Por Cauchy-Schwarz, Σ d(v)² ≥ (Σ d(v))²/n = 4m²/n. Entonces 4m²/n ≤ m·n, es decir, m ≤ n²/4. ∎

**\[Teo\] (Turán, 1941)** Entre los grafos de n vértices sin K\_{r+1}, el que tiene más aristas es el **grafo de Turán** T(n, r): r clases de tamaños lo más parejos posible, con todas las aristas entre clases. Su número de aristas es aproximadamente (1 − 1/r)·n²/2.

**\[Teo\] (Erdős y Stone, 1946; Erdős y Simonovits, 1966)** Para todo grafo H con número cromático χ(H) = r + 1, el máximo de aristas de un grafo de n vértices sin H es (1 − 1/r + o(1))·n²/2. *Lectura:* para grafos H no bipartitos, el número cromático determina el comportamiento extremal; para H bipartito el máximo es o(n²) y el problema está en gran parte abierto (problema de Zarankiewicz).

**\[Teo\] (Ramsey, 1930)** Para todo k existe R(k, k) tal que todo grafo con al menos R(k, k) vértices contiene una clique de k vértices o un conjunto independiente de k vértices.

*Caso R(3, 3) = 6.* Sea v un vértice de un grafo con 6 vértices. Entre los otros 5, v es adyacente a al menos 3 o no adyacente a al menos 3. En el primer caso, si dos de esos 3 son adyacentes hay triángulo con v; si no, los 3 forman un independiente. El segundo caso es simétrico. Además, C₅ muestra que con 5 vértices no alcanza. ∎

**\[Teo\] (Erdős, 1947) R(k, k) > 2^(k/2) para k ≥ 3.** *Demostración (método probabilístico):* en G(n, 1/2), la esperanza del número de conjuntos de k vértices que son clique o independientes es (n sobre k)·2^(1 − k(k−1)/2). Si n ≤ 2^(k/2), esa esperanza es menor que 1, de modo que existe un grafo sin ninguno de los dos. ∎ Es uno de los primeros usos del método probabilístico: prueba la existencia sin construir el objeto, y todavía no se conoce una construcción explícita que alcance esa cota. La mejor cota superior clásica era 4^k; Campos, Griffiths, Morris y Sahasrabudhe (2023) la mejoraron a (4 − ε)^k, el primer avance exponencial en casi noventa años.

**\[Teo\] Lema de regularidad de Szemerédi (1975, enunciado informal).** Todo grafo denso suficientemente grande puede partirse en un número acotado de partes de modo que casi todos los pares de partes se comporten como grafos bipartitos aleatorios. Es la herramienta central de la teoría extremal moderna y la base de los límites de grafos de Lovász. La 6.ª edición de Diestel le agrega herramientas de aplicación.

**\[Int\] Consecuencia metodológica.** Ramsey implica que en una red suficientemente grande aparecen subestructuras muy regulares (cliques o grupos sin vínculos) por pura combinatoria, sin mecanismo social que las produzca. Calude y Longo ("The Deluge of Spurious Correlations in Big Data", *Foundations of Science*, 2017) usaron este tipo de argumentos para mostrar que en bases de datos suficientemente grandes las correlaciones arbitrarias son inevitables. Encontrar un patrón en un grafo grande no es por sí solo evidencia de nada: hay que mostrar que es improbable bajo un modelo nulo pertinente.

**Qué pregunta permite responder.** Qué estructuras son inevitables dado el tamaño o la densidad; y, al revés, cuándo la ausencia de una estructura es en sí misma una restricción fuerte (un grafo sin triángulos no puede ser muy denso).

**Qué no permite responder.** Cuántas veces aparece una estructura en una red concreta, ni por qué. Las cotas son de peor caso o asintóticas.

**Condiciones.** Las cotas de Ramsey crecen exponencialmente: el argumento "es inevitable" es serio para estructuras pequeñas (cliques de 4 o 5) en redes grandes, y no para estructuras de tamaño comparable a la red.

## II.9 Grafos perfectos, chordales y clases especiales

Muchos problemas NP-difíciles en general se vuelven polinomiales en clases estructuradas de grafos. Reconocer que los datos pertenecen a una de esas clases puede convertir un problema intratable en uno exacto.

**\[Def\] Grafo perfecto.** G es perfecto si χ(H) = ω(H) para todo subgrafo inducido H. En ellos, la cota inferior trivial de la coloración (II.4) es exacta.

**\[Teo\] (Teorema débil de los grafos perfectos; Lovász, 1972)** G es perfecto si y solo si su complemento lo es.

**\[Teo\] (Teorema fuerte; Chudnovsky, Robertson, Seymour y Thomas, *Annals of Mathematics*, 2006)** G es perfecto si y solo si no contiene como subgrafo inducido un ciclo impar de longitud al menos 5 ni el complemento de uno. Esta caracterización había sido conjeturada por Berge en 1961. Chudnovsky, Cornuéjols, Liu, Seymour y Vušković (2005) dieron un algoritmo polinomial de reconocimiento. En grafos perfectos, χ, ω y α se calculan en tiempo polinomial (Grötschel, Lovász y Schrijver, con el método del elipsoide).

**\[Def\] Grafo chordal** (o triangulado): todo ciclo de longitud al menos 4 tiene una cuerda, es decir, una arista que une dos vértices no consecutivos del ciclo.

**\[Teo\] Caracterizaciones de los chordales.** Son equivalentes:

1. G es chordal.
2. G tiene un **orden de eliminación perfecta**: un orden de los vértices en el que cada vértice forma una clique con sus vecinos posteriores.
3. Todo separador minimal de vértices es una clique.
4. G es el grafo de intersección de subárboles de un árbol (Gavril, 1974).

Los chordales son perfectos. Se reconocen en tiempo lineal con búsqueda lexicográfica en anchura, LexBFS (Rose, Tarjan y Lueker, 1976). Con el orden de eliminación perfecta se obtienen en tiempo lineal la clique máxima, la coloración óptima y el conjunto independiente máximo.

**Subclases útiles.**

- **Grafos de intervalos:** vértices = intervalos en la recta, aristas = intervalos que se superponen. Son chordales. Modelan coexistencia temporal: dos personas "pudieron encontrarse" si sus períodos en un lugar se superponen. Reconocer que un conjunto de relaciones es (o no es) un grafo de intervalos permite verificar la consistencia temporal de testimonios: si los solapamientos declarados no forman un grafo de intervalos, no existe ninguna asignación de períodos que los haga compatibles a todos. Esto exige conocer tanto los solapamientos como los no solapamientos; si solo se sabe una parte y el resto es desconocido, el problema pasa a ser el de "sándwich" de intervalos, que es NP-completo (Golumbic, Kaplan y Shamir, 1995). Esta es la base del problema de Benzer en genética y de usos análogos en arqueología (seriación).
- **Grafos de comparabilidad:** aristas entre elementos comparables de un orden parcial; son perfectos. Sus complementos modelan incomparabilidad.
- **Cografos:** se construyen con unión disjunta y complemento; tienen ancho de clique acotado y casi todo es polinomial en ellos.

**χ-acotación.** Una clase es χ-acotada si χ está acotado por una función de ω. Es una generalización de la perfección que la 6.ª edición de Diestel incorpora como tema nuevo, y un área de investigación muy activa.

**Qué pregunta permite responder.** Si un problema que en general es intratable puede resolverse exactamente en estos datos; y, para grafos de intervalos, si un conjunto de relaciones temporales es internamente consistente.

**Qué no permite responder.** Nada sobre datos que no pertenecen a la clase: una sola arista faltante o espuria puede sacar un grafo de la clase chordal. Con datos ruidosos se usan versiones "casi" de la clase (distancia de edición a la clase), que suelen ser NP-difíciles.

**Condiciones.** Pertenencia exacta a la clase; conviene verificarla algorítmicamente antes de aplicar los algoritmos especializados, que pueden dar resultados incorrectos sin aviso si el grafo no pertenece.

## II.10 Treewidth, descomposiciones y complejidad parametrizada

La complejidad clásica mide el costo solo en función del tamaño n. La complejidad parametrizada agrega un segundo parámetro k (el tamaño de la solución buscada, o una medida de estructura) y pregunta si la explosión exponencial puede confinarse a k.

**\[Def\] Descomposición en árbol.** Es un árbol T cuyos nodos llevan "bolsas" Bₜ ⊆ V tales que: (1) todo vértice está en alguna bolsa; (2) toda arista tiene ambos extremos en alguna bolsa; (3) para cada vértice, las bolsas que lo contienen forman un subárbol conexo de T. El **ancho** es el tamaño de la mayor bolsa menos uno, y el **ancho de árbol** tw(G) es el mínimo ancho posible.

Valores de referencia: los árboles tienen tw = 1; los ciclos, 2; Kₙ, n − 1; la grilla de k × k, exactamente k. Los grafos de tw ≤ k son subgrafos de grafos chordales con cliques de a lo sumo k + 1 vértices (II.9).

**\[Def\] Tratabilidad con parámetro fijo (FPT).** Un problema parametrizado es FPT si se resuelve en tiempo f(k)·n^c, con f cualquier función computable y c una constante independiente de k.

**\[Teo\] Cubrimiento por vértices de tamaño k es FPT: tiempo O(2^k·(n + m)).**

*Demostración (árbol de búsqueda acotado).* Tomamos cualquier arista uv; todo cubrimiento contiene a u o a v. Ramificamos: en una rama ponemos u en el cubrimiento y lo borramos del grafo con k − 1; en la otra, lo mismo con v. El árbol de ramificación tiene profundidad a lo sumo k y, por tanto, a lo sumo 2^k hojas, cada una procesada en tiempo lineal. ∎

**\[Teo\] Núcleo (*kernel*) de Buss.** Todo vértice de grado mayor que k debe estar en un cubrimiento de tamaño k (si no, harían falta todos sus vecinos). Tras incluirlos y borrarlos, si quedan más de k² aristas, la respuesta es no. Así, en tiempo polinomial se reduce la instancia a una de tamaño O(k²). La **kernelización** es la versión rigurosa del preprocesamiento: garantiza cuánto se puede reducir sin perder la respuesta.

**\[Teo\] Dureza parametrizada.** Clique de tamaño k es W\[1\]-completo: bajo la hipótesis estándar de que FPT ≠ W\[1\], no admite algoritmo f(k)·n^c. La jerarquía W cumple, para los problemas parametrizados, el papel que cumple NP en la teoría clásica.

**\[Teo\] (Courcelle, 1990)** Toda propiedad de grafos expresable en lógica monádica de segundo orden se decide en tiempo f(tw, φ)·n en grafos de ancho de árbol acotado. Incluye 3-coloreo, ciclo hamiltoniano y muchas más. La función f es astronómica, de modo que el teorema clasifica más de lo que permite computar; para cada problema concreto se diseñan programas dinámicos específicos.

**Calcular el ancho de árbol** es NP-difícil en general, pero FPT: Bodlaender (1996) dio un algoritmo lineal para k fijo. En la práctica se usan heurísticas de eliminación (grado mínimo, relleno mínimo) que dan cotas superiores.

**\[Emp\]** Las redes sociales y de información grandes suelen tener un ancho de árbol alto, aunque a menudo con un "núcleo" denso y una periferia de ancho bajo (Maniu, Senellart y Jog, estudio experimental presentado en ICDT 2019). Por eso las técnicas de ancho de árbol se aplican con éxito a subredes, a grafos de procedencia y a grafos derivados de programas, más que a redes sociales completas.

**Qué pregunta permite responder.** Si la dificultad de un problema está concentrada en un parámetro que en mis datos es chico, y por tanto si existe un algoritmo exacto viable aunque el problema sea NP-difícil en general.

**Qué no permite responder.** Si un problema es fácil "en la práctica" sin medir el parámetro en los datos reales.

**Condiciones.** Parámetro efectivamente pequeño en la instancia. Referencia de estudio: Cygan, Fomin, Kowalik, Lokshtanov, Marx, Pilipczuk, Pilipczuk y Saurabh, *Parameterized Algorithms* (Springer, 2015), con versión gratuita autorizada por los autores.

## II.11 Algoritmos exactos, aproximados y heurísticos

Ante un problema NP-difícil hay tres estrategias, con garantías de naturaleza distinta. Confundirlas es uno de los errores más frecuentes al reportar resultados.

| Tipo | Qué garantiza | Costo típico | Ejemplo |
| --- | --- | --- | --- |
| Exacto | El óptimo | Exponencial en el peor caso | Held-Karp para el viajante |
| De aproximación | Una solución a factor ρ del óptimo, en todas las instancias | Polinomial | Cubrimiento por vértices con factor 2 |
| Heurístico | Nada en general; se evalúa empíricamente | Variable, habitualmente rápido | Louvain, recocido simulado, búsqueda local |

**Exactos.** Además de la ramificación acotada (II.10), la programación dinámica sobre subconjuntos reduce muchos problemas de n! a 2ⁿ. *Ejemplo:* el algoritmo de Held y Karp (1962) resuelve el viajante en O(2ⁿ·n²), calculando para cada subconjunto S y cada vértice final v el costo mínimo de un camino que recorre S y termina en v. Para n = 30 son unos 10¹² pasos: viable con paciencia; para n = 60, no. La programación lineal entera con planos de corte y ramificación (lo que hacen Concorde o los solvers comerciales) resuelve instancias reales mucho mayores, sin garantía de tiempo.

**Aproximación: la idea de certificado.** Un algoritmo es una ρ-aproximación si su solución nunca es peor que ρ veces el óptimo. Para demostrarlo hace falta una **cota inferior** del óptimo que se pueda comparar con la solución.

**\[Teo\] El cubrimiento por vértices tiene una 2-aproximación.** *Algoritmo:* hallar un emparejamiento maximal M (agregando aristas mientras se pueda) y devolver los 2|M| extremos. *Prueba:* el resultado es un cubrimiento, porque una arista no cubierta podría agregarse a M, que era maximal. Y todo cubrimiento debe incluir al menos un extremo de cada arista de M, que son disjuntas, así que el óptimo es al menos |M|. Por lo tanto la solución, de tamaño 2|M|, es a lo sumo el doble del óptimo. ∎ Bajo la conjetura de los juegos únicos (*Unique Games Conjecture*), no puede mejorarse a 2 − ε.

**\[Teo\] Cubrimiento de conjuntos voraz.** Elegir siempre el conjunto que cubre más elementos nuevos da una aproximación con factor H(n) ≈ ln n, y eso es esencialmente lo mejor posible en tiempo polinomial (Feige, 1998; Dinur y Steurer, 2014, bajo P ≠ NP).

**Inaproximabilidad.** El teorema PCP (Arora, Lund, Motwani, Sudan y Szegedy; Arora y Safra, 1998) permite probar que ciertos problemas no admiten buenas aproximaciones: clique y coloración no admiten factor n^(1−ε) (Håstad, 1999; Zuckerman, 2007), y el viajante general no admite ningún factor constante.

**Heurísticas.** Búsqueda local, recocido simulado (*simulated annealing*), algoritmos genéticos, búsqueda tabú, y algoritmos voraces específicos como Louvain y Leiden para comunidades. Son \[Heur\]: pueden funcionar muy bien en datos reales, pero sin garantía. Su evaluación honesta exige: varias corridas con semillas distintas, reporte de la variabilidad, comparación con cotas inferiores cuando existan y con instancias de referencia con solución conocida (por ejemplo, redes sintéticas con comunidades plantadas, como el banco LFR de Lancichinetti, Fortunato y Radicchi, 2008).

**Qué pregunta permite responder.** Qué tipo de afirmación se puede hacer sobre un resultado: "es el óptimo", "está a menos del doble del óptimo" o "es una buena solución encontrada, sin garantía".

**Qué no permite responder.** Una heurística no permite afirmar que no existe una solución mejor ni que la solución hallada sea la única razonable. Este punto es crítico al presentar resultados como evidencia: "el algoritmo encontró estos grupos" no equivale a "estos son los grupos".

**Condiciones.** Las garantías de aproximación valen para el problema formal exacto; si el problema real difiere (pesos inciertos, restricciones adicionales), la garantía no se transfiere automáticamente.

## II.12 Complejidad computacional, NP-completitud y límites prácticos

**\[Def\]** **P** es la clase de problemas de decisión resolubles en tiempo polinomial. **NP**, la de problemas cuyas respuestas "sí" tienen un certificado verificable en tiempo polinomial (por ejemplo, el ciclo hamiltoniano mismo). Un problema es **NP-difícil** si todo problema de NP se reduce a él en tiempo polinomial, y **NP-completo** si además está en NP. Si un solo problema NP-completo estuviera en P, todos lo estarían; se conjetura que P ≠ NP.

**Reducciones: la herramienta.** Para probar que un problema B es NP-difícil, se toma uno A ya conocido como NP-difícil y se muestra cómo transformar cualquier instancia de A en una de B con la misma respuesta. *Ejemplo:* de 3-SAT a conjunto independiente. Por cada cláusula de tres literales se crea un triángulo, y se unen con aristas los literales contradictorios (x y no-x) entre triángulos. La fórmula es satisfacible si y solo si el grafo tiene un conjunto independiente de tamaño igual al número de cláusulas: se elige un literal verdadero por cláusula, y las aristas impiden elegir contradicciones.

**Mapa de problemas de grafos.**

| En P | NP-completos (versión de decisión) |
| --- | --- |
| Camino mínimo, árbol generador mínimo | Camino más largo simple, árbol de Steiner |
| Circuito euleriano | Ciclo hamiltoniano |
| 2-coloreo | 3-coloreo |
| Emparejamiento máximo | Emparejamiento tridimensional |
| Corte mínimo | Corte máximo |
| Cubrimiento por vértices en bipartitos | Cubrimiento por vértices general, clique, conjunto independiente |
| Componentes conexas, fuertemente conexas | Maximización de modularidad (Brandes y otros, 2008) |

La referencia clásica es Garey y Johnson, *Computers and Intractability: A Guide to the Theory of NP-Completeness* (1979), con un catálogo de problemas que se sigue usando.

**Otras clases relevantes.**

- **#P (conteo).** Contar es a menudo más difícil que decidir. Contar emparejamientos perfectos es #P-completo (Valiant, 1979), aunque decidir si existe uno es polinomial. Calcular la probabilidad de que dos vértices estén conectados en un grafo con aristas inciertas también es #P-completo (II.15).
- **Isomorfismo de grafos.** Ni conocido en P ni NP-completo; tiempo cuasipolinomial (Babai, 2015–2017; ver I.4).
- **Complejidad de grano fino.** Para problemas en P, pregunta si las cotas conocidas se pueden mejorar. Por ejemplo, no se conoce algoritmo para caminos mínimos entre todos los pares en tiempo O(n^(3−ε)) para grafos densos con pesos generales, y se conjetura que no existe.

**Límites prácticos: qué significa "intratable" para quien investiga.**

1. NP-difícil es una afirmación sobre el **peor caso**. Instancias reales pueden ser fáciles (estructura especial, parámetro chico).
2. Polinomial no significa rápido: O(n³) con n = 10⁶ son 10¹⁸ operaciones, inviable. Para grafos grandes, lo viable en la práctica es casi lineal en m.
3. Cuando una herramienta resuelve rápido un problema NP-difícil en un grafo grande, casi seguro usa una heurística, y su resultado no es el óptimo. Conviene saber cuál usa.

**Qué pregunta permite responder.** Si conviene buscar un algoritmo exacto eficiente o es mejor buscar estructura, parámetros chicos, aproximaciones o heurísticas.

**Qué no permite responder.** Cuánto tardará una instancia concreta: la complejidad del peor caso no predice el tiempo en un caso particular.

**Condiciones.** Los resultados de dureza suponen P ≠ NP (u otras hipótesis estándar). Se mantienen como teoremas condicionales.

## II.13 Grafos temporales, dinámicos y multicapa

Casi todos los fenómenos que interesan en este tratado (comunicaciones, transacciones, trazas de sistemas, carreras institucionales) son temporales. Sin embargo, la mayor parte de la teoría clásica es estática. Esta sección muestra qué se rompe al agregar el tiempo y qué teoría lo reemplaza.

**\[Def\] Representaciones del tiempo.**

- **Secuencia de instantáneas** (*snapshots*): G₁, G₂, …, Gₜ, cada una un grafo en una ventana. Simple, pero depende de la elección del ancho de ventana.
- **Flujo de enlaces** (*link stream*): conjunto de triplas (u, v, t), o de intervalos (u, v, \[t₁, t₂\]) si los contactos duran. No pierde información; Latapy, Viard y Magnien (*Social Network Analysis and Mining*, 2018) desarrollaron un formalismo que generaliza las nociones de grafo a esta representación.
- **Grafo agregado:** una arista si hubo al menos un contacto. Es lo que se hace por defecto, y pierde el orden.

Revisiones de referencia: Holme y Saramäki, "Temporal networks" (*Physics Reports*, 2012); Casteigts, Flocchini, Quattrociocchi y Santoro, "Time-varying graphs and dynamic networks" (2012).

**\[Def\] Camino que respeta el tiempo** (*time-respecting path*): sucesión de contactos con tiempos no decrecientes (o estrictamente crecientes, según el fenómeno). Hay tres nociones de "mejor" camino que ya no coinciden: el que **llega primero** (*foremost*), el **más rápido** (menor duración entre partida y llegada) y el de **menos saltos**. Los tres se calculan en tiempo casi lineal en el número de contactos, pero dan respuestas distintas.

**\[Teo\] Lo que deja de valer.**

1. *Transitividad de la alcanzabilidad:* A alcanza a B y B alcanza a C no implica que A alcance a C (Evaluación, F1).
2. *Simetría:* aun con contactos no dirigidos, la alcanzabilidad temporal es asimétrica.
3. *Menger:* Kempe, Kleinberg y Kumar (*Journal of Computer and System Sciences*, 2002) mostraron que la versión por vértices del teorema de Menger falla en grafos temporales: el máximo de caminos temporales disjuntos puede ser menor que el mínimo separador.
4. *Componentes:* las componentes fuertemente conexas temporales ya no forman una partición, y encontrar la mayor es NP-completo (Bhadra y Ferreira, 2003), cuando en el caso estático es lineal.

**Agregación y sesgo.** El grafo agregado sobreestima la alcanzabilidad y subestima las distancias. Además, la elección de la ventana de agregación cambia las métricas de forma no monótona. Los modelos nulos temporales (permutar los tiempos manteniendo las aristas, o permutar las aristas manteniendo los tiempos) permiten separar el efecto de la estructura del efecto del orden temporal.

**\[Def\] Redes multicapa.** Kivelä, Arenas, Barthelemy, Gleeson, Moreno y Porter ("Multilayer networks", *Journal of Complex Networks*, 2014) dieron un formalismo general: los mismos actores aparecen en varias capas (tipos de relación, períodos, plataformas), con aristas dentro de cada capa y aristas entre capas. Una **red multiplex** es el caso en que las aristas entre capas solo conectan las copias del mismo actor. Se representa con una **matriz de supra-adyacencia** por bloques. Mucha, Richardson, Macon, Porter y Onnela (*Science*, 2010) extendieron la modularidad para detectar comunidades consistentes a lo largo de capas y del tiempo.

**Grafos dinámicos en sentido algorítmico.** Otra acepción: estructuras de datos que mantienen una propiedad (conexión, caminos mínimos) mientras se agregan y quitan aristas, sin recalcular todo. Es central para telemetría y monitoreo en tiempo real (Volumen VII).

**Qué pregunta permite responder.** Quién pudo haber influido o transmitido algo a quién, en qué orden y con qué demora; cómo cambia la estructura; qué relaciones de distinto tipo se refuerzan o se sustituyen.

**Qué no permite responder.** Que una transmisión ocurrió. Un camino temporal muestra que fue posible, dada la información registrada.

**Condiciones.** Timestamps confiables y comparables (ver la Evaluación, F5, sobre relojes); claridad sobre si los contactos son instantáneos o duran; y conciencia de los efectos de borde de la ventana de observación.

## II.14 Hipergrafos y relaciones de orden superior

Muchas relaciones sociales no son entre pares: una reunión, un contrato con varias partes, un directorio, una causa judicial con varios imputados, un chat grupal. Reducirlas a pares es una decisión de modelado con consecuencias, no un detalle técnico.

**\[Def\]** Un **hipergrafo** H = (V, E) tiene hiperaristas que son subconjuntos de V de cualquier tamaño. Un **complejo simplicial** es un hipergrafo cerrado hacia abajo: si un conjunto está, todos sus subconjuntos también. La diferencia es sustantiva: un complejo simplicial afirma que si cinco personas interactuaron juntas, cada subgrupo también lo hizo; un hipergrafo no afirma eso.

**Tres representaciones y lo que pierden.**

| Representación | ¿Pierde información? | Comentario |
| --- | --- | --- |
| Grafo bipartito de incidencia (actores–eventos) | No | Equivalente exacto del hipergrafo; es la representación de afiliación de Breiger (1974) |
| Proyección sobre pares (dos actores vinculados si comparten evento) | Sí | Una reunión de 5 se vuelve un K₅ indistinguible de 10 reuniones de a dos; infla triángulos y agrupamiento |
| Proyección ponderada (peso = eventos compartidos) | Sí, menos | Conserva frecuencia, no la composición de cada grupo |

*Contraejemplo clave:* tres reuniones de a dos (A–B, B–C, A–C) y una única reunión de los tres (A, B, C) producen la misma proyección, un triángulo, pero describen situaciones sociales completamente distintas. En la primera nadie estuvo con los otros dos a la vez.

**Teoría disponible.** Grado, caminos (sucesiones de hiperaristas que se intersectan), conexión, coloración (ningún hiperarista monocromática) y emparejamientos se generalizan, pero muchos resultados cambian: por ejemplo, decidir si un hipergrafo 3-uniforme es 2-coloreable es NP-completo, mientras que para grafos es lineal. Textos: Berge, *Hypergraphs* (North-Holland, 1989); Bretto, *Hypergraph Theory: An Introduction* (Springer, 2013).

**Investigación reciente.** Battiston, Cencetti, Iacopini, Latora, Lucas, Patania, Young y Petri ("Networks beyond pairwise interactions: Structure and dynamics", *Physics Reports*, 2020) revisan el área. Un resultado conceptual importante: en modelos de contagio con interacciones grupales (Iacopini, Petri, Barrat y Latora, *Nature Communications*, 2019), pueden aparecer transiciones abruptas que ningún modelo de pares produce. Es decir, la proyección no solo pierde detalle: puede cambiar la dinámica cualitativa. La topología algebraica (homología persistente) estudia "agujeros" en complejos simpliciales y es la base del análisis topológico de datos.

**Qué pregunta permite responder.** Quién participó junto con quién en el mismo evento, qué grupos se repiten, y cómo procesos que requieren varias fuentes a la vez (presión grupal, decisiones colegiadas) se propagan.

**Qué no permite responder.** Qué pasó dentro de cada evento: una hiperarista dice que cinco personas estuvieron en la reunión, no quién habló con quién ni con qué peso.

**Condiciones.** Hay que definir qué es un evento (¿una reunión de dos horas o una jornada?) y si las relaciones son de grupo o de pares observados en grupo. Recomendación práctica: conservar siempre la representación bipartita original y derivar proyecciones solo para preguntas que las justifiquen, documentando la elección.

## II.15 Redes probabilísticas e incertidumbre sobre aristas y entidades

La teoría clásica supone que el grafo es conocido. En investigación, tanto las aristas como los propios vértices son el resultado de un proceso de inferencia con error. Esta sección reúne las herramientas para tratar esa incertidumbre de forma explícita, en lugar de esconderla.

**\[Def\] Grafo incierto.** Cada arista e tiene una probabilidad pₑ de existir. Bajo la **semántica de mundos posibles**, el grafo incierto representa una distribución sobre todos los grafos determinísticos que se obtienen eligiendo cada arista según su probabilidad (habitualmente, con independencia entre aristas, lo cual es en sí un supuesto fuerte).

**\[Teo\] (Valiant, 1979)** Calcular la probabilidad de que s y t estén conectados en un grafo incierto (confiabilidad de red) es #P-completo. Consecuencia práctica: incluso preguntas simples sobre grafos inciertos se responden por muestreo de Monte Carlo, con intervalos de error, no de forma exacta.

**\[Teo\] La métrica del grafo esperado no es la métrica esperada.** Calcular una centralidad sobre el grafo con pesos pₑ no da, en general, la esperanza de esa centralidad sobre los mundos posibles. *Ejemplo mínimo:* camino s–a–t con ambas aristas de probabilidad 1/2. En el grafo "esperado" (las dos aristas presentes, con peso 1/2), s alcanza a t a distancia 2. En los mundos posibles, s alcanza a t solo con probabilidad 1/4; en los 3/4 restantes la distancia es infinita, de modo que la distancia esperada ni siquiera es finita. Ningún peso asignado a las aristas reproduce esa distribución. Si la métrica es no lineal (como casi todas), hay que muestrear mundos y reportar la distribución.

**\[Emp\] Sensibilidad de las métricas al error de datos.**

- Borgatti, Carley y Krackhardt ("On the robustness of centrality measures under conditions of imperfect data", *Social Networks*, 2006) mostraron que la precisión de las centralidades se degrada de manera predecible con aristas o nodos faltantes, y que con errores moderados los rankings de los actores más centrales dejan de ser confiables.
- Kossinets ("Effects of missing data in social networks", *Social Networks*, 2006) analizó cómo distintos mecanismos de faltantes (falta de respuesta, especificación de fronteras, límite fijo de nominaciones) sesgan las métricas de forma distinta.

**Modelos de medición.** Butts ("Network inference, error, and informant (in)accuracy: a Bayesian approach", *Social Networks*, 2003) propuso tratar la red real como latente y los reportes de informantes como observaciones con tasas de error propias, estimadas conjuntamente. Newman ("Network structure from rich but noisy data", *Nature Physics*, 2018) desarrolló una idea análoga con varias mediciones repetidas. La lógica es la misma que en cualquier medición científica: separar el objeto del instrumento.

**Incertidumbre sobre entidades.** Los nodos surgen de un proceso de resolución de entidades (*entity resolution*, *record linkage*) que decide qué registros corresponden al mismo actor. El modelo probabilístico clásico es el de Fellegi y Sunter (*Journal of the American Statistical Association*, 1969). Los dos errores tienen efectos estructurales distintos: fusionar entidades distintas crea hubs falsos y puentes falsos entre comunidades; separar una misma entidad corta caminos y vuelve periféricos a actores centrales (Evaluación, G6). Lo correcto es tratar la identidad como hipótesis con nivel de confianza, conservar los registros originales y hacer análisis de sensibilidad con distintos umbrales.

**Ausencia de arista y mundo abierto.** En un grafo incierto, "no hay arista" debe distinguirse de "arista con probabilidad baja" y de "par no observado". Una representación honesta tiene al menos tres estados por par: observado presente, observado ausente y no observado. El Volumen VII desarrolla esto con la semántica de RDF y OWL, y el Volumen V con su crítica.

**Qué pregunta permite responder.** Cuán confiable es una conclusión estructural dada la calidad de los datos, y qué conclusiones sobreviven a variaciones plausibles del grafo.

**Qué no permite responder.** Las probabilidades mismas no se infieren de la nada: un grafo incierto con probabilidades inventadas o mal calibradas da una falsa sensación de rigor. Las probabilidades necesitan un modelo de medición y, si es posible, validación.

**Condiciones.** Probabilidades calibradas; un supuesto explícito sobre la dependencia entre aristas (la independencia rara vez es realista: las aristas de una misma fuente fallan juntas); y reporte de resultados como distribuciones o intervalos, no como valores puntuales.

## Matriz de técnicas (parte II)

Primera parte de la matriz del entregable 9; los Volúmenes III a VII agregan filas. Cada fila resume el cierre de su sección.

| Técnica o resultado | Pregunta que responde | Lo que no responde | Condición crítica | Sección |
| --- | --- | --- | --- | --- |
| Menger, separadores mínimos | Robustez de la conexión ante eliminaciones | Si los caminos se usan; roles sociales | Completitud de las aristas | II.1 |
| Flujo máximo, corte mínimo | Capacidad máxima entre dos puntos; cuellos de botella | Qué fluyó efectivamente | Capacidades conocidas; conservación | II.2 |
| Hall, König, emparejamientos | Factibilidad de asignaciones uno a uno; certificado de imposibilidad | Si la asignación es justa | Restricciones binarias conocidas | II.3 |
| Coloración | Recursos excluyentes mínimos | Óptimo exacto en instancias grandes | Conflictos binarios | II.4 |
| Euler, Hamilton, viajante | Existencia y costo de recorridos completos | Cuál recorrido ocurrió | Conexión; desigualdad triangular para aproximar | II.5 |
| Espectro, laplaciano, Fiedler | Cuellos de botella, componentes, partición aproximada | Significado social de los grupos | Grafo no dirigido; normalización adecuada | II.6 |
| Modelos nulos aleatorios | Si una propiedad observada es esperable por azar | El mecanismo generador | Elección pertinente del modelo nulo | II.7 |
| Turán, Ramsey | Qué estructuras son inevitables | Por qué aparece una estructura concreta | Escala de la estructura frente a la red | II.8 |
| Clases chordal, intervalos, perfectos | Solución exacta de problemas difíciles; consistencia temporal | Nada fuera de la clase | Pertenencia exacta, verificada | II.9 |
| Ancho de árbol, FPT | Si la dificultad se concentra en un parámetro chico | Facilidad práctica sin medir el parámetro | Parámetro efectivamente chico | II.10 |
| Aproximación, heurísticas | Qué tipo de afirmación permite un resultado | Optimalidad o unicidad (heurísticas) | Problema formal idéntico al real | II.11 |
| NP-completitud | Si buscar un algoritmo exacto eficiente | Tiempo en una instancia concreta | P ≠ NP (condicional) | II.12 |
| Caminos temporales, multicapa | Quién pudo influir a quién y en qué orden | Que la transmisión ocurrió | Timestamps confiables; efectos de ventana | II.13 |
| Hipergrafos, complejos simpliciales | Participación conjunta; dinámica de grupo | Qué pasó dentro de cada evento | Definición explícita de evento | II.14 |
| Grafos inciertos, modelos de medición | Robustez de conclusiones ante error | Probabilidades no calibradas | Calibración; supuesto de dependencia | II.15 |

## Ejercicios del Volumen II

Dificultad: (★) directo, (★★) requiere una idea, (★★★) desafiante. Las soluciones se publican con el Volumen X.

1. (★) Encontrá un grafo con κ = 1, λ = 2 y δ = 3.
2. (★★) Deducí el teorema de König a partir de max-flow/min-cut: construí la red y explicá por qué un corte finito corresponde a un cubrimiento por vértices.
3. (★★) Probá que todo grafo bipartito k-regular (k ≥ 1) tiene un emparejamiento perfecto usando Hall.
4. (★) Dá un grafo con χ = 4 y sin K₄. Pista: el grafo de Grötzsch, o una rueda con borde impar.
5. (★★) Probá que si G es conexo y tiene exactamente 2k vértices de grado impar, sus aristas se pueden cubrir con k senderos disjuntos en aristas, y no con menos.
6. (★★) Calculá el espectro de adyacencia de Kₙ y de K\_{a,b}. Verificá la simetría del espectro en el caso bipartito.
7. (★★) Calculá a mano μ₂ (conectividad algebraica) de P₄ y de C₄, y comparalos. ¿Qué intuición confirma?
8. (★★) En G(n, p) con p = c/n, calculá la esperanza del número de triángulos y mostrá que tiende a c³/6.
9. (★★) Probá que R(3, 4) ≤ 10 con un argumento como el de R(3, 3).
10. (★★) Encontrá un orden de eliminación perfecta en un grafo de intervalos de seis intervalos que elijas, y usalo para colorearlo con ω colores.
11. (★★) Construí una descomposición en árbol de ancho 2 para un ciclo C₆.
12. (★★) Mostrá que la 2-aproximación del cubrimiento por vértices es ajustada: dá una familia de grafos en la que devuelve exactamente el doble del óptimo.
13. (★★★) Dá un grafo temporal pequeño en el que el número máximo de caminos temporales internamente disjuntos de s a t sea menor que el tamaño mínimo de un separador temporal.
14. (★★) Construí dos hipergrafos distintos con la misma proyección sobre pares y una pregunta sustantiva que distinga uno del otro.
15. (★★) Simulá en Python (con NetworkX) un grafo incierto pequeño, estimá por Monte Carlo la probabilidad de conexión entre dos vértices con 10.000 muestras, y compará con el cálculo exacto por enumeración de mundos posibles.
16. (★★★) Conceptual: elegí un caso público de investigación sobre redes de corrupción o crimen organizado y señalá qué resultados de este volumen se usaron implícitamente, y cuáles de sus condiciones podrían no cumplirse en esos datos.
