# Soluciones explicadas

Abrí cada bloque solo después de haber respondido y marcado tu confianza. Cada solución indica qué hace falta para obtener 3 puntos, que es lo que distingue una respuesta completa de una correcta pero incompleta.

## Bloque A — Fundamentos

**A1.** No existe. Por el lema del apretón de manos, la suma de grados es 2m y debe ser par, pero 7 × 3 = 21 es impar. *Para 3 puntos:* citar el lema o reproducir el doble conteo.

**A2.** Tiene 16 aristas. Cada componente es un árbol con nᵢ vértices y nᵢ − 1 aristas, así que el total es la suma de (nᵢ − 1) = n − c = 20 − 4. No depende de la forma porque cada árbol, cualquiera sea, tiene exactamente una arista menos que vértices.

**A3.** Falso. Ejemplo con ambos conexos: dos árboles de 6 vértices con secuencia (3, 2, 2, 1, 1, 1).

- *Árbol 1:* un vértice c de grado 3 unido a a, b y una hoja; a y b tienen una hoja cada uno.
- *Árbol 2:* c de grado 3 unido a x y a dos hojas; x unido a y; y unido a una hoja.

En el árbol 1, los dos vértices de grado 2 no son adyacentes; en el árbol 2, sí. La adyacencia entre vértices de grado 2 es un invariante, así que no son isomorfos. *Puntaje parcial:* el ejemplo C₆ y 2C₃ vale 2 puntos, porque no cumple la condición de conexión pedida.

**A4.** H es subgrafo si sus vértices y aristas están en G; es inducido si además contiene **todas** las aristas de G entre sus vértices. *Ejemplo con consecuencia:* se intervienen solo las comunicaciones de A. El grafo resultante muestra las aristas de A con sus contactos, pero no las aristas entre esos contactos, porque nadie las registró. Si se lo trata como inducido, se concluye que los contactos de A no se comunican entre sí y A aparece como intermediario exclusivo, con un agujero estructural artificial. Es el sesgo típico de las redes egocéntricas obtenidas desde una sola fuente.

**A5.** No es planar. K₃,₃ es bipartito y no tiene triángulos, así que si fuera planar cumpliría m ≤ 2n − 4 = 8; pero tiene 9 aristas.

**A6.** Un grafo es bipartito si y solo si no tiene ciclos de longitud impar. C₇ no es bipartito, porque es un ciclo impar. Q₄ sí lo es: las clases son los vectores con cantidad par y con cantidad impar de unos, y cada arista cambia exactamente un bit, es decir, la paridad.

**A7.** (A²)ᵢᵢ cuenta los paseos de longitud 2 de i a i, que son ir a un vecino y volver: es d(i). La traza de A³ es 6 veces el número de triángulos, porque cada triángulo da 3 vértices de inicio por 2 sentidos.

**A8.** Listas de adyacencia. La matriz tiene 10¹² entradas: un terabyte con un byte por entrada, o unos 125 GB con un bit. Las listas guardan 2m = 10⁷ entradas más los n desplazamientos; con enteros de 4 bytes son unos 44 MB. *Para 3 puntos:* explicar que la red es rala (m del orden de n) y estimar ambos órdenes de magnitud.

## Bloque B — Demostraciones

**B1.** En un grafo simple con n vértices los grados posibles son 0, 1, …, n − 1, que son n valores. Pero 0 y n − 1 no pueden aparecer a la vez: un vértice de grado n − 1 es adyacente a todos, así que ninguno puede ser aislado. Quedan a lo sumo n − 1 valores para n vértices y, por el principio del palomar, dos coinciden. ∎ *Para 3 puntos:* la observación sobre 0 y n − 1, que es la idea clave.

**B2.** Sea P un camino de longitud máxima en el árbol; como n ≥ 2, tiene al menos una arista. Su extremo x no puede tener un vecino fuera de P, porque se extendería el camino, ni un vecino dentro de P distinto del siguiente en el camino, porque se formaría un ciclo. Entonces x tiene grado 1, y lo mismo vale para el otro extremo. ∎

**B3.** Sean u y v no adyacentes. Sus vecindades están contenidas en V ∖ {u, v}, que tiene n − 2 elementos, y |N(u)| + |N(v)| ≥ n − 1 > n − 2. Por el palomar comparten un vecino, así que d(u, v) = 2. Todo par está a distancia a lo sumo 2: G es conexo y de diámetro ≤ 2. ∎ *Ajuste de la cota:* para n par, dos copias disjuntas de K\_{n/2} tienen δ = n/2 − 1 = (n − 2)/2 y no son conexas. La cota no se puede bajar ni un medio.

**B4.** Recorrer el circuito: cada vez que pasa por un vértice v sin ser el inicio, entra por una arista y sale por otra, consumiendo dos aristas incidentes en v. El inicio también se empareja: la primera arista de salida con la última de llegada. Como cada arista se usa exactamente una vez, las aristas incidentes en cada vértice se agrupan en pares: el grado es par. ∎ *Comentario:* la recíproca (grafo conexo con todos los grados pares tiene circuito euleriano) también es cierta, pero requiere otra prueba; no se pedía.

**B5.** Si n ≤ 2 es inmediato. Para n ≥ 3, un grafo planar simple cumple m ≤ 3n − 6. Si todos los vértices tuvieran grado ≥ 6, sería 2m ≥ 6n, es decir, m ≥ 3n > 3n − 6. Contradicción. ∎

**B6.** La afirmación es falsa y la "prueba" tiene tres errores.

1. *El caso base es falso.* Para n = 3, el camino P₃ es conexo y tiene δ = 1 ≥ 3/3, pero no tiene ciclo hamiltoniano. La afirmación no dice "K₃": todos los grafos de 3 vértices que cumplen la hipótesis tenían que considerarse.
2. *Error de construcción* (*build-up error*, así lo llama West). Agregar un vértice a un grafo de n vértices que cumple la hipótesis no genera todos los grafos de n + 1 vértices que la cumplen. El paso inductivo correcto parte de un grafo arbitrario de n + 1 vértices y le **quita** uno; y entonces hay que verificar que el grafo resultante siga cumpliendo la hipótesis, cosa que en general no ocurre.
3. *Paso no justificado.* Tener (n + 1)/3 vecinos en un ciclo de longitud n no obliga a que dos sean consecutivos: pueden estar todos separados.

*Contraejemplo de cualquier tamaño:* dos copias de Kₖ que comparten un único vértice. Tiene n = 2k − 1 vértices y δ = k − 1 ≥ n/3 para k ≥ 2, pero el vértice compartido es de corte, y ningún grafo con vértice de corte tiene ciclo hamiltoniano. *Versión correcta:* el teorema de Dirac (1952) dice que δ ≥ n/2 con n ≥ 3 garantiza un ciclo hamiltoniano, y el ejemplo anterior muestra que esa cota es casi óptima. *Para 3 puntos:* al menos el error 2 más un contraejemplo válido.

## Bloque C — Algoritmos

**C1.** BFS. Procesa los vértices por capas: primero todos los de distancia 1, luego los de distancia 2, etc. El invariante es que la cola está ordenada por distancia y sus valores difieren a lo sumo en 1, de modo que la primera vez que se descubre un vértice es por un camino mínimo. DFS puede llegar a un vértice primero por un camino largo y no lo corrige. *Para 3 puntos:* mencionar el invariante o el argumento por capas.

**C2.** Vértices s, a, b con aristas s→a de peso 2, s→b de peso 3 y b→a de peso −2. Dijkstra extrae a con distancia 2 y lo da por definitivo; después extrae b (3) y encuentra el camino s→b→a de costo 1, pero a ya estaba cerrado. Falla porque supone que extender un camino nunca lo acorta, lo que solo vale con pesos no negativos. Alternativas: Bellman-Ford, o Johnson para todos los pares.

**C3.** O((n + m) log n) con heap binario. La versión con arreglo cuesta O(n²) y conviene en grafos densos, donde m es del orden de n², porque entonces m log n supera a n².

**C4.** Existe si y solo si el digrafo es acíclico (DAG). Si Kahn termina sin procesar todos los vértices, los que quedan contienen un ciclo dirigido. En datos de dependencias o de procedencia, eso señala una inconsistencia: algo que, directa o indirectamente, deriva de sí mismo. Suele deberse a errores de registro, a timestamps incorrectos o a identificadores reutilizados.

**C5.** Union-Find (conjuntos disjuntos) con **unión por rango** y **compresión de caminos**. Con ambas, el costo amortizado por operación es O(α(n)), donde α es la inversa de la función de Ackermann, que en la práctica es a lo sumo 4 (Tarjan, 1975). El costo total de Kruskal queda dominado por el ordenamiento: O(m log m).

**C6.** Dijkstra minimiza la suma de pesos, así que con pesos de "intensidad" prefiere los vínculos **más débiles**: el resultado es el camino menos cercano, lo contrario de lo buscado. Hay que transformar intensidad en distancia, por ejemplo con 1/w, o con −log p si los pesos se normalizan a una probabilidad de transmisión. Supuestos que se introducen: que la distancia es aditiva a lo largo del camino; con −log p, además, que los tramos son independientes. Distintas transformaciones dan caminos distintos y ninguna es neutral, así que la elección tiene que justificarse por la pregunta. *Para 3 puntos:* detectar la inversión, proponer una transformación y nombrar al menos un supuesto.

**C7.** El factor de amortiguación d (típicamente 0,85) es la probabilidad de que el "navegante aleatorio" siga un enlace; con probabilidad 1 − d salta a un vértice uniforme. Eso hace a la cadena de Markov irreducible y aperiódica, lo que garantiza que exista un único vector estacionario y que el método de potencias converja. Los vértices sin enlaces salientes absorben masa y la hacen desaparecer en cada iteración. La solución habitual es tratarlos como si enlazaran a todos los vértices, redistribuyendo su masa de manera uniforme.

**C8.** No. Maximizar la modularidad es NP-difícil (Brandes y otros, 2008), y Louvain es una heurística voraz cuyo resultado depende del orden de procesamiento; Traag, Waltman y van Eck (2019) mostraron además que puede producir comunidades internamente desconectadas, y propusieron el algoritmo Leiden. El límite de resolución (Fortunato y Barthélemy, 2007) indica que la modularidad puede no detectar comunidades menores que cierta escala que depende del tamaño total de la red, y fusionar grupos bien definidos. Además, grafos completamente aleatorios pueden tener modularidad alta (Guimerà y otros, 2004). *Para 3 puntos:* "heurística sin garantía" más el límite de resolución.

## Bloque D — Teoría intermedia y avanzada

**D1.** En una red con capacidades, el valor del flujo máximo de s a t es igual a la capacidad mínima de un corte que separe s de t (Ford y Fulkerson, 1956). El corte mínimo te dice qué conjunto de aristas, de menor capacidad total, limita lo que puede pasar de s a t: es una cota superior **estructural**. No te dice qué flujo pasó efectivamente, ni por dónde, ni con qué intención; puede haber varios cortes mínimos distintos; y el resultado depende por completo de las capacidades asumidas, que en datos sociales casi nunca se conocen. *Para 3 puntos:* enunciado correcto y al menos dos cosas que el corte no dice.

**D2.** Un grafo bipartito con clases X e Y tiene un emparejamiento que cubre todo X si y solo si |N(S)| ≥ |S| para todo S ⊆ X (Hall, 1935). Ejemplo: X = {x₁, x₂, x₃}, Y = {y₁, y₂, y₃}, con x₁ y x₂ adyacentes solo a y₁, y x₃ adyacente a y₂ e y₃. El conjunto S = {x₁, x₂} tiene N(S) = {y₁}, de tamaño 1 < 2.

**D3.** La multiplicidad del autovalor 0 es el número de componentes conexas. El segundo autovalor más chico, λ₂, es positivo si y solo si el grafo es conexo, y mide cuán difícil es partirlo en dos: un λ₂ chico indica un "cuello" con pocas aristas entre dos partes grandes (desigualdad de Cheeger). Su autovector, el vector de Fiedler, da una bipartición aproximada que es la base del particionamiento espectral. Detalles en \[II.6\].

**D4.** Con np < 1, casi seguramente todas las componentes tienen tamaño O(log n). Con np > 1 aparece una única componente gigante de tamaño proporcional a n. La transición en np = 1 es abrupta (Erdős y Rényi, 1960). El grafo es conexo con alta probabilidad cuando p supera aproximadamente ln n / n. *Para 3 puntos:* ambas transiciones.

**D5.** Un problema de decisión es NP-completo si está en NP (una solución propuesta se verifica en tiempo polinomial) y todo problema de NP se reduce a él en tiempo polinomial. Ejemplos de grafos: ciclo hamiltoniano, clique de tamaño k, 3-coloreo, cubrimiento por vértices. Contrapartes en P: circuito euleriano frente a ciclo hamiltoniano; 2-coloreo (bipartición) frente a 3-coloreo; cubrimiento por vértices en grafos bipartitos (por el teorema de König) frente al caso general. *Matiz importante:* NP-completo no significa imposible en la práctica; significa que no se conoce algoritmo polinomial para el peor caso.

**D6.** El ancho de árbol mide cuánto se parece un grafo a un árbol. Una descomposición en árbol organiza conjuntos de vértices ("bolsas") en un árbol de modo que cada arista quede en alguna bolsa y cada vértice ocupe un subárbol conexo; el ancho es el tamaño de la bolsa más grande menos uno. Los árboles tienen ancho 1 y Kₙ tiene ancho n − 1. Con ancho k acotado, se aplica programación dinámica sobre la descomposición con costo del tipo f(k)·n: exponencial solo en k. El teorema de Courcelle (1990) generaliza esto: toda propiedad expresable en lógica monádica de segundo orden se decide en tiempo lineal en grafos de ancho de árbol acotado.

## Bloque E — Redes sociales

**E1.** Granovetter ("The Strength of Weak Ties", *American Journal of Sociology*, 1973) sostiene que los vínculos débiles tienden a funcionar como puentes entre círculos sociales distintos y, por eso, transmiten información nueva que no circula dentro del propio grupo. El mecanismo es la "tríada prohibida": si A tiene vínculos fuertes con B y con C, es muy probable que B y C también estén vinculados, de modo que un puente local difícilmente sea un vínculo fuerte. La evidencia era su estudio sobre búsqueda de empleo en profesionales de un suburbio de Boston, publicado en *Getting a Job* (1974): quienes consiguieron trabajo por contactos los describían más a menudo como personas que veían ocasionalmente. Un experimento a gran escala sobre LinkedIn (Rajkumar y otros, *Science*, 2022) encontró que los vínculos más útiles eran los moderadamente débiles, lo que matiza la tesis original. *Para 3 puntos:* tesis, mecanismo y evidencia.

**E2.** En *Structural Holes* (1992), Burt llama agujero estructural a la ausencia de vínculo entre contactos de un actor. Quien ocupa la posición entre grupos no conectados accede a información no redundante y puede controlar lo que pasa de un lado al otro. Métricas: tamaño efectivo (*effective size*), eficiencia y restricción (*constraint*), esta última la más usada. *Crítica a tener presente:* la posición crea una oportunidad, no una ventaja garantizada, y el beneficio depende del contexto y de la capacidad de aprovecharla.

**E3.** Porque ambas producen el mismo patrón observable: vínculo más similitud de conducta. Una característica no observada puede causar a la vez la formación del vínculo y la conducta. Shalizi y Thomas (*Sociological Methods & Research*, 2011) mostraron que, sin supuestos adicionales fuertes, homofilia y contagio están confundidos de manera genérica en datos observacionales. Separarlos requiere variación exógena (experimentos o experimentos naturales), datos longitudinales con supuestos explícitos o análisis de sensibilidad.

**E4.** Interpretaciones alternativas, todas compatibles con una intermediación máxima:

- es un operador logístico o mensajero, subordinado y reemplazable;
- es un artefacto del muestreo: la investigación se centró en sus comunicaciones, y por eso aparece conectando todo;
- tiene un rol institucional ajeno al núcleo: contador, abogado, secretaria, chofer;
- su identificador es compartido: un teléfono o una cuenta que usan varias personas;
- es un vínculo externo: familiar, proveedor o vecino, en contacto con muchos por razones legítimas;
- la métrica asume que la comunicación fluye por caminos mínimos, lo que puede no ser cierto.

La literatura sobre redes criminales encontró además que los líderes a menudo se mantienen periféricos para protegerse, y que las posiciones de alta intermediación suelen ser las más expuestas (Morselli, *Inside Criminal Networks*, 2009). *Para 3 puntos:* cuatro alternativas bien distintas, con al menos una sobre el proceso de producción de datos.

**E5.** El grado cuenta vecinos. La centralidad de autovector asigna a cada vértice un valor proporcional a la suma de los valores de sus vecinos: importa estar conectado a vértices importantes. Ejemplo: A está unido a cinco hojas y a un vértice C; B está unido solo a C y a D, y C y D son centros de estrellas de diez hojas cada uno. A tiene grado 6 y B tiene grado 2, pero B puede tener mayor centralidad de autovector porque sus dos vecinos son centrales. Conviene verificarlo calculándolo; el ejercicio de calcularlo es parte del laboratorio.

**E6.** La multiplexidad es la coexistencia de varios tipos de relación entre los mismos actores: parentesco, negocios, amistad, comunicación. Al colapsarlos en un grafo, se suman vínculos con significados incompatibles, las centralidades mezclan roles distintos y aparecen caminos que combinan tipos de relación que no transmiten lo mismo (un rumor no circula igual por un vínculo de parentesco que por uno comercial). Además se pierde la superposición, que es en sí misma información: los vínculos multiplex suelen ser más estables y de más confianza.

**E7.** En promedio, los contactos de una persona tienen más contactos que ella (Feld, *American Journal of Sociology*, 1991). Ocurre porque los vértices de grado alto aparecen en muchas listas de contactos: el grado promedio de un vecino es E\[d²\]/E\[d\], que es mayor o igual que E\[d\], con igualdad solo si todos los grados son iguales. Consecuencia para el muestreo: los métodos por referencias (bola de nieve, muestreo dirigido por respondentes) sobrerrepresentan a los actores muy conectados. Eso puede aprovecharse para detección temprana, pero sesga las estimaciones si no se corrige.

## Bloque F — Grafos temporales y procedencia

**F1.** De A a C, no: A llega a B en el instante 3, y el único contacto de B con C ocurrió antes, en el instante 1. De C a A, sí: C alcanza a B en 1 y B alcanza a A en 3. Aunque los contactos no sean dirigidos, la alcanzabilidad temporal es asimétrica. *Supuestos que conviene explicitar:* transmisión instantánea, contactos sin duración y timestamps exactos. *Para 3 puntos:* ambas respuestas y la observación sobre la asimetría.

**F2.** El grafo agregado admite caminos que violan el orden temporal, como A–B–C en F1, y por eso cuenta como alcanzables pares que no lo son. Deja de valer la transitividad: que A alcance a B y B alcance a C no implica que A alcance a C. También dejan de valer las distancias: el camino estático más corto puede no existir en el tiempo, o puede existir solo con esperas largas.

**F3.** *Censura por izquierda:* los vínculos que empezaron antes de la ventana aparecen como si fueran nuevos, y se subestima su antigüedad. *Censura por derecha:* los que siguen activos después del cierre parecen terminados o más cortos de lo que son. Hay además un *sesgo por duración*: los vínculos largos tienen más probabilidad de caer en cualquier ventana que los breves, así que estos últimos quedan subrepresentados. *Para 3 puntos:* dos sesgos distintos, bien explicados.

**F4.** Ejemplo:

- *Dato registrado:* "el log del servidor X registra una conexión desde la IP Y a las 10:02".
- *Inferencia:* "la IP Y corresponde a la persona Z", basada en otro registro y en una regla de asignación que puede fallar.
- *Reconstrucción hipotética:* "Z accedió para copiar el archivo", que atribuye un propósito sin registro directo.

W3C PROV define tres tipos de nodo centrales: **Entidad** (*Entity*), **Actividad** (*Activity*) y **Agente** (*Agent*), unidos por relaciones como *wasGeneratedBy*, *used*, *wasDerivedFrom*, *wasAttributedTo* y *wasAssociatedWith*. Cada inferencia debería ser ella misma una actividad con sus insumos y su responsable, de modo que la cadena quede auditable.

**F5.** Dentro de un mismo sistema, el orden local es confiable si su reloj es monótono. Entre sistemas distintos, solo se puede afirmar que un evento precede a otro si la diferencia entre sus timestamps supera los 2 segundos del desplazamiento posible, más la resolución de los relojes. Si no, el orden es indeterminado. Representación: se toma el reloj de un sistema como referencia, y cada evento del otro sistema se expresa como un intervalo \[t − 2, t + 2\] en esa escala; una arista "anterior a" se agrega solo cuando el punto y el intervalo no se solapan; si se solapan, "orden indeterminado". El resultado es un **orden parcial**, no total. Alternativa complementaria: los relojes lógicos de Lamport (1978), que ordenan por causalidad, como envío y recepción de mensajes, en vez de por tiempo físico. *Para 3 puntos:* distinguir orden intra-sistema de orden entre sistemas y no forzar un orden total.

## Bloque G — Epistemología

En este bloque se puntúa por mecanismos identificados, no por coincidencia con una lista cerrada.

**G1.** Mecanismos que producen ausencia de arista con relación existente:

- *no se investigó*: la causa no incluyó medidas sobre esa relación;
- *selección de la fuente*: el expediente registra solo lo relevante para la imputación;
- *fragmentación de identidad*: la relación consta, pero bajo un alias, otra grafía o un identificador distinto;
- *reserva*: piezas en secreto de sumario o fuera del expediente digitalizado;
- *informalidad*: la relación no deja rastro documental;
- *selección de casos*: solo se cargaron las causas elevadas a juicio;
- *errores de carga o digitalización*.

La formulación correcta es de mundo abierto: "no consta", no "no existe". *Para 3 puntos:* tres mecanismos distintos y la distinción explícita.

**G2.** Antes de hablar de "organización" habría que verificar:

1. *Robustez:* si el grupo aparece con otros algoritmos, otras semillas y otros parámetros de resolución.
2. *Modelo nulo:* si una densidad así es esperable dado el grado de los nodos; los grafos aleatorios pueden tener modularidad alta.
3. *Explicaciones estructurales triviales:* actividad compartida con un mismo banco, proveedor, plataforma o domicilio, o un artefacto de proyección bipartita.
4. *Calidad de entidades:* fusiones o separaciones erróneas.
5. *Temporalidad:* si los vínculos coexistieron en el tiempo o se agregaron años distintos.
6. *Evidencia independiente de coordinación:* fines comunes, roles, reglas, que es lo que define a una organización y que una partición estadística no contiene.
7. *Explicaciones legítimas alternativas:* familia, cooperativa, empresa, consorcio.

Una comunidad detectada es una partición que optimiza una función; una organización es un hecho social con fines y reglas. Lo primero puede ser indicio de lo segundo, nunca prueba.

**G3.** Laumann, Marsden y Prensky (1983) plantearon que la definición de quién integra la red es una decisión del investigador, con criterios posicionales (pertenencia formal), reputacionales (quién es nombrado) o relacionales (quién interactúa). Ejemplo: al estudiar las compras de un ministerio, una red limitada a funcionarios excluye a proveedores, consultoras, estudios jurídicos e intermediarios, que pueden ser los actores decisivos. La estructura y las centralidades cambian según la frontera, y la frontera elegida debe justificarse por la pregunta.

**G4.** Los algoritmos de disposición por fuerzas son optimizaciones heurísticas con componentes aleatorias. La distancia en el dibujo no es la distancia en el grafo, la cercanía visual puede ser un artefacto, y colores, tamaños y recortes los decide quien dibuja. Evidencia sería: métricas calculadas con su incertidumbre, comparación contra modelos nulos, robustez frente a datos faltantes y la remisión a las fuentes de cada arista. La visualización sirve para explorar y comunicar, no para probar.

**G5.** Explicaciones compatibles con los mismos datos:

- *influencia*: uno persuadió al otro en las reuniones;
- *homofilia*: comparten ideología o pertenencia partidaria, que explica tanto que se reúnan como que voten igual;
- *causa común externa*: una instrucción de un superior o la presión de un tercero sobre ambos;
- *causalidad inversa*: se reúnen porque ya coincidían;
- *tasa base*: si casi todos votaron igual, la coincidencia no es informativa.

*Para 3 puntos:* tres explicaciones con mecanismos causales distintos, y alguna mención de la tasa base.

**G6.** *Fusión errónea:* dos homónimos ("Juan Pérez") o varias sociedades con el mismo domicilio legal de un estudio contable se unifican en un solo nodo. Aparece un hub falso con centralidad enorme que une comunidades sin relación. *Separación errónea:* una misma persona registrada con variantes de nombre, transliteraciones o un número de documento mal cargado queda partida en varios nodos. Los caminos se cortan y el actor parece periférico. Consecuencia general: los nodos son el resultado de un proceso de inferencia con error. Hay que documentar las reglas y umbrales de resolución y hacer análisis de sensibilidad. *Para 3 puntos:* ambos tipos de error con su efecto sobre alguna métrica.
