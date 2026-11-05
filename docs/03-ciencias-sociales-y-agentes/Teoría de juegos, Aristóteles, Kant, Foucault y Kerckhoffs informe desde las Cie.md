# Teoría de juegos, Aristóteles, Kant, Foucault y Kerckhoffs: informe desde las Ciencias Sociales

Nov 5, 2026 · @Anna Tchijova

## Introducción: cuatro maneras de pensar a un sujeto que actúa entre otros

Las cuatro tradiciones de este informe responden, desde ángulos distintos, a una misma pregunta: qué pasa cuando alguien actúa sabiendo que otros también actúan, saben, juzgan o miran. La teoría de juegos la formula como un problema de **decisión estratégica**. Aristóteles y Kant la formulan como un problema de **cómo se debe actuar** y qué hace buena a una acción. Foucault la formula como un problema de **poder**: cómo se conducen las conductas de otros y cómo se producen los sujetos que después "eligen". Kerckhoffs, desde la criptografía militar del siglo XIX, la formula como un problema de **secreto**: qué conviene esconder y qué conviene mostrar cuando hay un adversario.

El informe está pensado para leerse de corrido, pero cada parte funciona sola. Cada una arranca por las bases y sube de nivel. La Parte V cruza los cuatro bloques: ahí está, probablemente, lo más útil para investigación social aplicada.

Hay cuatro ejes que atraviesan todo el texto y conviene tener en mente desde el principio:

- **Racionalidad.** Para la teoría de juegos es cálculo de medios para fines dados. Para Aristóteles es *phronesis*, saber práctico que también juzga los fines. Para Kant es la capacidad de darse una ley universal. Para Foucault es siempre una racionalidad situada, una forma histórica de pensar y gobernar.
- **Información y visibilidad.** Quién sabe qué, quién ve a quién. Es el centro de los juegos de información incompleta, del panóptico y del principio de Kerckhoffs.
- **Instituciones.** Las reglas del juego, la *polis*, el Estado de derecho, los dispositivos. Todas las tradiciones discuten cuánto pueden hacer las instituciones con sujetos imperfectos.
- **Publicidad y secreto.** Kant propone un test de publicidad para la justicia; Kerckhoffs, uno para la seguridad técnica; Foucault muestra que la visibilidad también es una técnica de dominación.

Convenciones: los términos técnicos aparecen en su idioma original entre paréntesis o en cursiva la primera vez. Las traducciones de textos antiguos y clásicos (Aristóteles, Kant, Kerckhoffs) son paráfrasis propias, no citas de ediciones publicadas. Los ejemplos numéricos están construidos para que puedas rehacer las cuentas a mano.

## Parte I. Teoría de juegos: bases iniciales

La teoría de juegos estudia situaciones de **interdependencia estratégica**: casos en que lo que me conviene hacer depende de lo que hagan otros, y ellos razonan lo mismo sobre mí. No trata de juegos en sentido lúdico. Trata de guerras, elecciones, negociaciones salariales, mercados, normas sociales, vigilancia y seguridad informática.

### Orígenes

- **Antoine Augustin Cournot (1838)** analizó cómo dos productores eligen cantidades sabiendo que el precio depende de ambos. Su solución es, en el fondo, un equilibrio de Nash avant la lettre.
- **Ernst Zermelo (1913)** probó que en el ajedrez uno de los dos jugadores tiene una estrategia que le garantiza al menos el empate, o ganar.
- **John von Neumann (1928)** demostró el teorema minimax para juegos de suma cero entre dos jugadores.
- **Von Neumann y Oskar Morgenstern (1944)**, *Theory of Games and Economic Behavior*, fundan la disciplina y una teoría de la utilidad esperada.
- **John Nash (1950–1951)** generaliza la noción de equilibrio a juegos con cualquier número de jugadores y sin suma cero.
- Durante la Guerra Fría, la RAND Corporation convierte la teoría en herramienta de estrategia nuclear. Ese origen importa para una lectura desde las Ciencias Sociales (ver Partes I avanzada y V).

### Los elementos de un juego

Todo juego se define por cinco componentes:

1. **Jugadores**: quiénes deciden. Pueden ser personas, Estados, empresas, partidos o incluso genes.
2. **Estrategias**: planes completos de acción. Una estrategia dice qué hacer en *cada* situación posible, incluso en las que nunca van a ocurrir.
3. **Pagos** (*payoffs*): cuánto valora cada jugador cada resultado. Son utilidades, no necesariamente dinero. Pueden incluir altruismo, odio, honor o culpa.
4. **Información**: qué sabe cada jugador al decidir, sobre los otros y sobre el juego.
5. **Orden de las jugadas**: si se decide a la vez o por turnos.

El supuesto de partida es la **racionalidad**: cada jugador elige lo que maximiza su utilidad esperada, dadas sus creencias. Se agrega el **conocimiento común** de la racionalidad: todos son racionales, todos saben que todos lo son, todos saben que todos saben, y así al infinito. Este supuesto es mucho más fuerte de lo que parece, y la Parte I avanzada lo discute.

### Dos distinciones que conviene no confundir

- **Información perfecta vs. imperfecta.** Es perfecta si, al mover, cada jugador sabe todo lo que pasó antes (ajedrez). Es imperfecta si hay jugadas que no vio (póker, o cualquier juego simultáneo).
- **Información completa vs. incompleta.** Es completa si todos conocen los pagos de todos. Es incompleta si alguien no sabe qué prefiere el otro: si el rival es duro o blando, si el candidato es honesto, si el comprador valora mucho el bien.

Un juego puede tener información completa pero imperfecta (el dilema del prisionero), o perfecta pero incompleta (un juego secuencial donde no sabés el tipo del otro).

### Forma normal y forma extensiva

La **forma normal** (o estratégica) es una matriz: filas para las estrategias de un jugador, columnas para las del otro, y en cada celda los pagos de ambos (primero el de fila, después el de columna). Sirve para juegos simultáneos.

La **forma extensiva** es un árbol: cada nodo es un momento de decisión, cada rama una acción, y las hojas son resultados con pagos. Sirve para juegos secuenciales. Cuando un jugador no sabe en qué nodo está, esos nodos se agrupan en un **conjunto de información**.

Todo juego extensivo se puede escribir en forma normal, pero se pierde información sobre el tiempo y la credibilidad de las amenazas. Por eso hacen falta conceptos más finos para juegos dinámicos.

### Dominancia

Una estrategia es **estrictamente dominante** si da un pago mayor que cualquier otra, haga lo que haga el rival. Si existe, un jugador racional la juega sin pensar en el otro.

Una estrategia es **estrictamente dominada** si hay otra que siempre paga más. Un jugador racional nunca la juega. La **eliminación iterada de estrategias dominadas** consiste en tachar las dominadas, mirar de nuevo la matriz reducida y volver a tachar. Cada ronda exige un nivel más de conocimiento común de la racionalidad: "yo sé que vos no vas a jugar eso, y vos sabés que yo lo sé".

### Mejor respuesta y equilibrio de Nash

Una **mejor respuesta** es la estrategia que maximiza mi pago dado lo que hace el otro. Un **equilibrio de Nash** es un perfil de estrategias, una por jugador, en el que cada una es mejor respuesta a las demás. Dicho de otro modo: nadie gana cambiando solo su estrategia.

```latex
s^* = (s_1^*, \dots, s_n^*) \text{ es equilibrio de Nash si } u_i(s_i^*, s_{-i}^*) \ge u_i(s_i, s_{-i}^*) \quad \forall i, \; \forall s_i
```

Acá u\_i es el pago del jugador i y s\_{-i} son las estrategias de todos los demás. Tres advertencias que se olvidan seguido:

- **No es óptimo social.** Un equilibrio puede ser malo para todos.
- **Puede haber varios.** Entonces la teoría sola no dice cuál ocurre; hace falta historia, cultura, instituciones o puntos focales.
- **No es una predicción mecánica.** Es una condición de estabilidad: si se llega ahí, nadie tiene incentivos individuales para salir.

El criterio complementario es la **eficiencia de Pareto**: un resultado es Pareto-eficiente si no se puede mejorar a nadie sin empeorar a alguien. Gran parte de la teoría social de la teoría de juegos vive en la brecha entre equilibrio y eficiencia.

### Los juegos clásicos

Cada juego clásico es un tipo ideal, en el sentido weberiano: un modelo de la *estructura* de una situación, no de las personas. En todas las matrices, el primer número es el pago de Fila y el segundo el de Columna.

#### Dilema del prisionero: cooperación que se destruye sola

Dos sospechosos están incomunicados. Si ambos callan (cooperan entre sí), reciben pena leve. Si uno delata y el otro calla, el delator sale libre y el otro recibe la pena máxima. Si ambos delatan, pena intermedia. En puntos (más es mejor):

| Fila \\ Columna | Cooperar | Defeccionar |
| --- | --- | --- |
| Cooperar | 3, 3 | 0, 5 |
| Defeccionar | 5, 0 | 1, 1 |

Defeccionar es dominante para ambos: si el otro coopera, 5 es más que 3; si defecciona, 1 es más que 0. El único equilibrio es (Defeccionar, Defeccionar), con pagos 1 y 1, aunque (Cooperar, Cooperar) da 3 y 3 a cada uno. La estructura general exige T > R > P > S, donde T es la tentación (5), R la recompensa de cooperar (3), P el castigo mutuo (1) y S el pago del ingenuo (0).

Es el modelo canónico de los **problemas de acción colectiva**: bienes públicos, contaminación, carreras armamentistas, sobrepesca, evasión fiscal, huelgas. También es la versión formal del estado de naturaleza de Hobbes: sin un tercero que garantice los acuerdos, la desconfianza es racional.

#### Caza del ciervo: el problema es la confianza

El ejemplo viene de Rousseau (*Discurso sobre el origen de la desigualdad*, 1755). Dos cazadores pueden cazar juntos un ciervo, que solo se logra entre ambos, o ir cada uno por una liebre, que se consigue solo.

| Fila \\ Columna | Ciervo | Liebre |
| --- | --- | --- |
| Ciervo | 4, 4 | 0, 3 |
| Liebre | 3, 0 | 3, 3 |

Hay dos equilibrios: (Ciervo, Ciervo) y (Liebre, Liebre). El primero es mejor para ambos (**dominancia en pagos**). El segundo es más seguro: la liebre garantiza 3 pase lo que pase (**dominancia en riesgo**). A diferencia del dilema del prisionero, acá nadie quiere traicionar; el problema es no estar seguro de que el otro confíe. Brian Skyrms lo propuso como mejor modelo del contrato social que el dilema del prisionero: muchas instituciones no corrigen tentaciones, sino que producen la confianza que hace posible la cooperación.

#### Gallina (o halcón-paloma): quién cede primero

Dos autos van de frente. El que se desvía es "gallina". Si nadie se desvía, chocan.

| Fila \\ Columna | Desviarse | Seguir |
| --- | --- | --- |
| Desviarse | 0, 0 | −1, 1 |
| Seguir | 1, −1 | −10, −10 |

Hay dos equilibrios en estrategias puras, (Seguir, Desviarse) y (Desviarse, Seguir), y uno en estrategias mixtas (se calcula en la parte avanzada). Cada uno prefiere el equilibrio en el que cede el otro. Es el modelo del **juego al borde del abismo** (*brinkmanship*): la crisis de los misiles de 1962, las huelgas generales, las negociaciones de deuda, los cierres de gobierno por presupuesto. La biología lo llama **halcón-paloma** (Maynard Smith): dos animales disputan un recurso de valor V; pelear cuesta C. Si C > V, la población converge a una mezcla de halcones y palomas.

La lección central, desarrollada por Thomas Schelling, es contraintuitiva: en estos juegos gana quien logra **comprometerse** de forma creíble a no ceder. Tirar el volante por la ventana es una jugada racional.

#### Coordinación con conflicto (la llamada "batalla de los sexos")

Dos personas quieren pasar la noche juntas, pero una prefiere la ópera y la otra el fútbol.

| Fila \\ Columna | Ópera | Fútbol |
| --- | --- | --- |
| Ópera | 2, 1 | 0, 0 |
| Fútbol | 0, 0 | 1, 2 |

Hay dos equilibrios puros: ambos coordinan, pero cada uno prefiere uno distinto. Modela la elección de estándares técnicos (VHS contra Betamax, formatos de archivo, protocolos), las alianzas políticas y la distribución desigual de los beneficios de coordinarse. La pregunta sociológica es quién impone su equilibrio, y casi siempre la respuesta es poder previo, no racionalidad.

#### Coordinación pura y puntos focales

Si solo importa coincidir (manejar por la derecha o por la izquierda), hay tantos equilibrios como alternativas y ninguno es mejor. Schelling preguntó a sus estudiantes dónde encontrarían a un desconocido en Nueva York sin haberse puesto de acuerdo: la mayoría eligió la estación Grand Central, al mediodía. Un **punto focal** es una solución que se destaca por razones culturales, históricas o perceptivas, no matemáticas. Es una entrada directa de la cultura en la teoría de juegos.

#### Suma cero y minimax

En un juego de **suma cero** lo que gana uno lo pierde el otro. El ejemplo mínimo es *matching pennies*: cada uno muestra una moneda; si coinciden, gana Fila; si no, gana Columna.

| Fila \\ Columna | Cara | Ceca |
| --- | --- | --- |
| Cara | 1, −1 | −1, 1 |
| Ceca | −1, 1 | 1, −1 |

No hay equilibrio en estrategias puras: cualquier patrón predecible es explotable. La solución es aleatorizar 50/50. El **teorema minimax** de von Neumann dice que en todo juego finito de suma cero entre dos jugadores, si se permiten estrategias mixtas, lo mejor que Fila puede garantizarse es exactamente lo peor que Columna puede imponerle:

```latex
\max_{p} \min_{q} \; p^{\top} A q \;=\; \min_{q} \max_{p} \; p^{\top} A q
```

A es la matriz de pagos de Fila, p y q son las estrategias mixtas. Los juegos de suma cero son la excepción en la vida social, pero son la regla en ciertos dominios: penales de fútbol, auditorías contra fraudes, criptografía, patrullaje policial, ataque y defensa de redes.

### Lo que estas bases ya enseñan a las Ciencias Sociales

- **El individualismo no garantiza buenos resultados colectivos.** La "mano invisible" es un caso particular, no la regla.
- **La estructura de la situación explica conducta.** El mismo actor coopera en una caza del ciervo y defecciona en un dilema del prisionero. Cambiar instituciones es cambiar matrices.
- **La información y la credibilidad son recursos de poder.** Quien puede comprometerse, quien sabe más o quien puede ocultar mejor, gana.
- **La multiplicidad de equilibrios abre la puerta a la historia y la cultura.** Cuando hay varios equilibrios, el modelo necesita a la sociología para cerrar.

## Parte I. Teoría de juegos: bases avanzadas

El nivel avanzado agrega tres cosas: el tiempo (juegos dinámicos y repetidos), la información privada (juegos bayesianos y señalización) y la pregunta inversa (diseñar reglas para obtener resultados). A eso se suman las versiones sin racionalidad perfecta: evolutiva, conductual y experimental.

### 1. Estrategias mixtas y el teorema de existencia

Una **estrategia mixta** es una distribución de probabilidad sobre las estrategias puras. Nash probó que **todo juego finito tiene al menos un equilibrio**, si se admiten estrategias mixtas. La demostración usa un teorema de punto fijo (Brouwer o Kakutani).

El método de cálculo es el **principio de indiferencia**: en un equilibrio mixto, cada jugador aleatoriza de modo que el *otro* quede indiferente entre sus opciones. Si no lo estuviera, el otro jugaría la mejor en forma pura.

Ejemplo con el juego de la gallina de la parte inicial. Sea p la probabilidad con que Columna sigue de largo. Para Fila:

- Si se desvía, gana 0 con probabilidad 1 − p y pierde 1 con probabilidad p: su pago esperado es −p.
- Si sigue, gana 1 con probabilidad 1 − p y pierde 10 con probabilidad p: su pago esperado es 1 − 11p.

```latex
-p = 1 - 11p \;\Rightarrow\; 10p = 1 \;\Rightarrow\; p = 0{,}1
```

En el equilibrio mixto cada uno sigue de largo el 10% de las veces, y chocan con probabilidad 0,1 × 0,1 = 1%. Un resultado típico y perturbador: si el choque se vuelve más costoso, la probabilidad de seguir de largo *baja*, pero no llega a cero.

Hay dos interpretaciones de lo mixto que importan para las Ciencias Sociales:

- **Poblacional**: no es que cada persona tire una moneda, sino que en la población hay una proporción de cada tipo de conducta.
- **De purificación** (Harsanyi, 1973): cada jugador juega en forma pura, pero tiene pequeñas variaciones privadas en sus pagos que los demás no conocen. Desde afuera, su conducta parece aleatoria.

### 2. Juegos dinámicos: credibilidad y amenazas vacías

En juegos secuenciales, el equilibrio de Nash admite resultados absurdos sostenidos por **amenazas no creíbles**. El ejemplo estándar es el **juego de entrada**:

1. Una empresa entrante decide si entra o no a un mercado.
2. Si entra, la incumbente decide si pelea (guerra de precios, costosa para ambas) o acomoda (comparte el mercado).

Si pelear le cuesta más que acomodar, la amenaza de pelear es vacía: una vez que el otro entró, la incumbente no la va a cumplir. Pero "No entrar / Pelear si entra" es un equilibrio de Nash, porque la amenaza nunca se pone a prueba.

Reinhard Selten (1965, 1975) propuso el **equilibrio perfecto en subjuegos**: un perfil es equilibrio en *cada* subjuego, incluidos los que no se alcanzan. Se encuentra por **inducción hacia atrás** (*backward induction*): se resuelve el último nodo, se reemplaza por su resultado y se sube. Así se eliminan las amenazas vacías.

Tres paradojas muestran los límites de la inducción hacia atrás:

- **Juego del ciempiés** (Rosenthal, 1981). Dos jugadores se alternan; en cada turno pueden cortar y llevarse una parte algo mayor de un pozo, o pasar y dejar que el pozo crezca. La inducción hacia atrás predice que el primero corta de entrada, aunque si ambos pasaran ganarían mucho más. En experimentos (McKelvey y Palfrey, 1992) casi nadie corta en el primer turno.
- **Paradoja de la cadena de tiendas** (Selten, 1978). Una cadena con tiendas en veinte ciudades enfrenta veinte posibles entrantes en sucesión. La inducción hacia atrás dice que nunca le conviene pelear, porque en la última ciudad no vale la pena, y eso se propaga hacia atrás. Intuitivamente, pelear al principio para crear reputación parece racional. La solución llegó con los modelos de reputación (ver juegos repetidos).
- **Juego del ultimátum** (Güth, Schmittberger y Schwarze, 1982). Uno propone cómo repartir una suma; el otro acepta o rechaza, y si rechaza nadie cobra. La teoría predice que se ofrece lo mínimo y se acepta. En los experimentos, las ofertas típicas rondan el 40–50% y las ofertas bajas (menos del 20%) se rechazan con frecuencia. Joseph Henrich y colegas compararon quince sociedades de pequeña escala (2001–2004): las ofertas variaron mucho y se correlacionaron con el grado de integración al mercado y de cooperación cotidiana. Es una de las demostraciones empíricas más claras de que las "preferencias" están socialmente formadas.

#### Compromiso estratégico

Thomas Schelling (*La estrategia del conflicto*, 1960) mostró que en juegos dinámicos **reducir las propias opciones puede aumentar el poder**. Hernán Cortés quemando las naves, un sindicato que se ata públicamente a un piso salarial, un banco central independiente, una ley que prohíbe negociar con secuestradores: todos hacen creíble una conducta que sin compromiso no lo sería. Jon Elster tomó la figura de Ulises atado al mástil para pensar el **precompromiso** individual y constitucional: las constituciones como mecanismos con que una sociedad se ata a sí misma.

### 3. Información incompleta: juegos bayesianos

John Harsanyi (1967–1968) resolvió cómo modelar juegos donde no se conocen los pagos del otro. Su truco: agregar un jugador ficticio, la **Naturaleza**, que sortea al principio el **tipo** de cada jugador (duro o blando, honesto o corrupto, alto o bajo costo) según una distribución conocida por todos (**prior común**). Cada jugador conoce su tipo pero no el de los demás.

Un **equilibrio bayesiano de Nash** es un perfil en el que cada *tipo* de cada jugador maximiza su pago esperado, dadas sus creencias sobre los tipos ajenos. Las creencias se actualizan con la regla de Bayes:

```latex
P(\theta \mid m) = \frac{P(m \mid \theta)\, P(\theta)}{\sum_{\theta'} P(m \mid \theta')\, P(\theta')}
```

θ es el tipo y m lo observado (un mensaje, una acción). En juegos dinámicos con información incompleta se usa el **equilibrio bayesiano perfecto**: estrategias racionales en cada punto, dadas creencias que se actualizan con Bayes siempre que sea posible.

### 4. Señalización, selección adversa y *screening*

Cuando una parte sabe algo que la otra no, aparecen tres familias de problemas:

- **Selección adversa** (George Akerlof, "The Market for Lemons", 1970). En el mercado de autos usados, el comprador no distingue los buenos de los malos (*lemons*) y paga un promedio. Los dueños de autos buenos se retiran, el promedio baja, y el mercado puede colapsar. Explica problemas de seguros, crédito y mercados laborales.
- **Señalización** (Michael Spence, 1973). La parte informada actúa para revelar su tipo. La clave es que la señal sea **costosa de manera diferencial**: más barata para el tipo bueno que para el malo. En el modelo de Spence, la educación puede servir como señal de productividad aunque no la aumente. En biología, el **principio del handicap** (Amotz Zahavi, 1975) explica la cola del pavo real; en sociología, el **consumo conspicuo** de Thorstein Veblen (1899) es una señal costosa de estatus.
- ***Screening*** (Rothschild y Stiglitz, 1976). La parte no informada diseña un menú de opciones para que cada tipo se autoseleccione: planes de seguro con distinta franquicia, tarifas de transporte con o sin restricciones.

Los juegos de señalización tienen equilibrios de tres clases:

- **Separadores**: cada tipo envía una señal distinta y el receptor aprende el tipo.
- **Agrupadores** (*pooling*): todos los tipos envían la misma señal y no se aprende nada.
- **Semiseparadores**: algunos tipos mezclan.

Como suele haber muchos equilibrios, se usan **refinamientos** que descartan creencias implausibles fuera del equilibrio; el más conocido es el **criterio intuitivo** de Cho y Kreps (1987).

Un caso límite es la **charla barata** (*cheap talk*, Crawford y Sobel, 1982): mensajes sin costo. La comunicación creíble solo es posible si los intereses están suficientemente alineados, y cuanto más divergen, más gruesa se vuelve la información transmitida. Es un modelo útil para asesores, lobbies, expertos y fuentes periodísticas.

El **riesgo moral** y el **problema principal-agente** completan el cuadro: el principal no observa el esfuerzo del agente y debe diseñar incentivos. De ahí salen buena parte de la economía de los contratos y la ciencia política de la delegación (votantes y representantes, Congreso y burocracias).

### 5. Juegos repetidos: la sombra del futuro

Si el dilema del prisionero se repite un número **finito y conocido** de veces, la inducción hacia atrás predice defección en todas las rondas: en la última no hay futuro, en la anteúltima tampoco, y así.

Si se repite **indefinidamente** (o el final es incierto), el futuro pesa. Sea δ el factor de descuento: cuánto vale hoy un punto de la ronda siguiente (también puede leerse como la probabilidad de que haya otra ronda). Con la estrategia **gatillo** (*grim trigger*: cooperar hasta la primera traición, y desde ahí defeccionar para siempre), cooperar es equilibrio si el valor de cooperar siempre supera el de traicionar una vez y ser castigado para siempre:

```latex
\frac{R}{1-\delta} \;\ge\; T + \frac{\delta P}{1-\delta} \quad\Longleftrightarrow\quad \delta \;\ge\; \frac{T-R}{T-P}
```

Con los pagos de la parte inicial (T = 5, R = 3, P = 1), la condición es δ ≥ 2/4 = 0,5. La lectura social: la cooperación se sostiene cuando la relación es estable, la tentación es baja y el castigo mutuo es duro.

El **teorema popular** (*folk theorem*, llamado así porque circulaba entre teóricos antes de publicarse formalmente) generaliza: con δ suficientemente alto, **cualquier** resultado factible que dé a cada jugador al menos lo que puede asegurarse solo puede sostenerse como equilibrio. Es a la vez una buena y una mala noticia. Buena: la cooperación sin Estado es posible. Mala: casi cualquier cosa es posible, incluso equilibrios muy desiguales, y la teoría no dice cuál ocurre.

#### Los torneos de Axelrod

Robert Axelrod (1980; *La evolución de la cooperación*, 1984) organizó torneos de computadora con estrategias enviadas por especialistas para el dilema del prisionero repetido. Ganó la más simple: **Tit for Tat** ("donde las dan las toman"), enviada por Anatol Rapoport: cooperar en la primera ronda y después copiar lo que hizo el otro en la ronda anterior. Axelrod atribuyó su éxito a cuatro propiedades: es **amable** (nunca traiciona primero), **vengativa** (castiga enseguida), **indulgente** (vuelve a cooperar si el otro vuelve) y **clara** (fácil de reconocer).

Su ejemplo histórico más famoso es el sistema de "vivir y dejar vivir" en las trincheras de la Primera Guerra Mundial: unidades enfrentadas durante meses desarrollaron treguas tácitas, disparos rituales y castigos medidos, hasta que los mandos rotaron tropas y ordenaron incursiones para romper la repetición.

Con **ruido** (errores de percepción o ejecución), Tit for Tat entra en espirales de venganza. Funcionan mejor variantes como Tit for Tat generoso o **Win-Stay, Lose-Shift** (Nowak y Sigmund, 1993): repetir la acción si salió bien, cambiarla si salió mal.

#### Reputación

Kreps, Milgrom, Roberts y Wilson (1982) resolvieron la paradoja de la cadena de tiendas y la cooperación en juegos finitos: si hay una pequeña probabilidad de que un jugador sea de un tipo "irracional" (que siempre pelea, o que siempre coopera), a los racionales les conviene imitarlo durante mucho tiempo para cultivar esa reputación. La **reputación** es, formalmente, una creencia ajena sobre tu tipo, y vale como un activo.

### 6. Teoría de juegos evolutiva

John Maynard Smith y George Price (1973) llevaron la teoría a la biología, quitándole la racionalidad. Las estrategias son rasgos heredables; los pagos, éxito reproductivo. Una **estrategia evolutivamente estable** (ESS) es una que, adoptada por casi toda la población, no puede ser invadida por un mutante raro.

La **dinámica del replicador** (Taylor y Jonker, 1978) describe cómo crece la proporción de cada estrategia según su pago relativo al promedio. En el juego halcón-paloma con V < C, la población converge a una proporción V/C de halcones.

Para las Ciencias Sociales, el giro evolutivo permite modelar **normas y convenciones** como estrategias que se difunden por imitación, aprendizaje o presión social, sin suponer que nadie las calculó. Son centrales Brian Skyrms (*Evolution of the Social Contract*, 1996), H. Peyton Young (*Individual Strategy and Social Structure*, 1998), Cristina Bicchieri (*The Grammar of Society*, 2006; las normas como expectativas empíricas y normativas condicionales) y Samuel Bowles y Herbert Gintis (*A Cooperative Species*, 2011).

### 7. Conocimiento común, convenciones y revoluciones

El **conocimiento común** no es saber algo, sino que todos sepan que todos lo saben, al infinito. David Lewis (*Convention*, 1969) lo usó para definir las convenciones. Robert Aumann (1976) mostró que dos personas con el mismo prior y conocimiento común de sus creencias posteriores no pueden "acordar estar en desacuerdo".

Dos rompecabezas muestran lo exigente que es:

- **Los niños embarrados.** Varios niños tienen barro en la frente; cada uno ve a los demás pero no a sí mismo. Todos saben que hay al menos uno embarrado. Cuando un adulto lo dice en voz alta, no informa nada nuevo a nadie, pero vuelve el hecho *conocimiento común*, y eso desencadena una cadena de razonamientos que termina con todos los embarrados identificándose.
- **Los dos generales** (problema del ataque coordinado). Dos ejércitos deben atacar juntos, y solo se comunican por mensajeros que pueden ser capturados. Ningún número finito de confirmaciones produce conocimiento común. Es un resultado clásico en sistemas distribuidos y en protocolos de red.

En sociología política, el conocimiento común explica por qué importan los actos **públicos**:

- Michael Chwe (*Rational Ritual*, 2001): los rituales, las ceremonias y los avisos en el Super Bowl sirven para generar conocimiento común, no solo información.
- Mark Granovetter (1978): modelos de **umbrales**. Cada persona se suma a una protesta si ya se sumaron suficientes otras. Pequeñas diferencias en la distribución de umbrales generan revueltas masivas o nada.
- Timur Kuran (*Private Truths, Public Lies*, 1995): la **falsificación de preferencias**. Bajo regímenes represivos la gente oculta su opinión; el descontento puede ser mayoritario y aun así invisible, hasta que un evento lo vuelve público y se produce una cascada. Por eso las revoluciones son tan difíciles de predecir. Y por eso la censura no apunta solo a la información, sino a impedir el conocimiento común.

### 8. Acción colectiva y bienes comunes

- **Mancur Olson** (*La lógica de la acción colectiva*, 1965): los grupos grandes tienen dificultades para proveerse bienes colectivos por el **problema del polizón** (*free rider*). Los grupos pequeños y los que ofrecen **incentivos selectivos** (beneficios solo para miembros) se organizan mejor. Explica por qué lobbies concentrados le ganan a mayorías dispersas.
- **Garrett Hardin** ("La tragedia de los comunes", 1968): un recurso de acceso abierto tiende a sobreexplotarse. Hardin concluía que solo el Estado o la propiedad privada podían evitarlo.
- **Elinor Ostrom** (*El gobierno de los bienes comunes*, 1990; Nobel 2009) desmontó esa dicotomía con estudios de campo en pesquerías, sistemas de riego, bosques y pasturas de todo el mundo. Muchas comunidades sostienen durante siglos el uso de recursos comunes con instituciones propias. Identificó ocho **principios de diseño** de las instituciones duraderas:
  1. Límites claros sobre quién usa y qué recurso.
  2. Reglas adaptadas a las condiciones locales.
  3. Arreglos de elección colectiva: los afectados participan en cambiar las reglas.
  4. Monitoreo por parte de los usuarios o de quienes les rinden cuentas.
  5. Sanciones graduadas.
  6. Mecanismos accesibles de resolución de conflictos.
  7. Reconocimiento mínimo, por parte de autoridades externas, del derecho a organizarse.
  8. Para sistemas grandes, organizaciones anidadas en varios niveles.

Los **juegos de bienes públicos** en laboratorio confirman y matizan esto. Cada participante decide cuánto aportar a un fondo común que se multiplica y se reparte. Los aportes empiezan en torno a la mitad de la dotación y decaen con las rondas. Si se permite **castigar** a costo propio, la cooperación se sostiene (Fehr y Gächter, 2000). Pero en algunas sociedades aparece el **castigo antisocial** a los que más aportan (Herrmann, Thöni y Gächter, 2008), y su frecuencia se asocia con normas cívicas y Estado de derecho débiles.

### 9. Teoría de juegos cooperativa: coaliciones y poder

La teoría cooperativa no modela jugadas individuales sino **qué puede lograr cada coalición**, descripta por una **función característica** v(S).

- El **núcleo** (*core*) es el conjunto de repartos que ninguna coalición puede mejorar por su cuenta. Puede estar vacío: ahí ninguna distribución es estable y siempre hay un grupo con incentivos para desertar.
- El **valor de Shapley** (1953) asigna a cada jugador su contribución marginal promedio sobre todos los órdenes posibles de llegada a la coalición:

```latex
\phi_i(v) = \sum_{S \subseteq N \setminus \{i\}} \frac{|S|!\,(n-|S|-1)!}{n!}\,\big[v(S \cup \{i\}) - v(S)\big]
```

Aplicado a votaciones, da el **índice de poder de Shapley-Shubik** (1954); una variante es el **índice de Banzhaf**. Muestran que el poder no es proporcional a los votos. Ejemplo: un parlamento de 100 bancas con mayoría de 51 y tres partidos con 49, 49 y 2 bancas. Cualquier par de partidos forma mayoría, así que los tres tienen exactamente el mismo poder: un tercio cada uno. El partido de 2 bancas pesa lo mismo que los grandes.

En **negociación** hay dos aportes centrales:

- La **solución de Nash** (1950): el reparto que maximiza el producto de las ganancias de cada parte sobre su punto de desacuerdo. Quien tiene mejor alternativa si no hay acuerdo (mejor "punto de amenaza") obtiene más.
- El modelo de **ofertas alternantes** de Ariel Rubinstein (1982): con ofertas y contraofertas por turnos, el acuerdo es inmediato y la parte más **paciente** se lleva más. La paciencia (poder esperar) es poder de negociación.

### 10. Diseño de mecanismos: la teoría al revés

En lugar de tomar las reglas y predecir resultados, el **diseño de mecanismos** fija el resultado deseado y busca reglas que lo produzcan en equilibrio, aunque los jugadores tengan información privada y busquen su propio interés. Leonid Hurwicz, Eric Maskin y Roger Myerson recibieron el Nobel en 2007 por fundarlo.

- **Compatibilidad de incentivos**: un mecanismo lo es si a cada uno le conviene decir la verdad sobre su tipo.
- **Principio de revelación**: cualquier resultado alcanzable con algún mecanismo puede alcanzarse con uno directo en el que decir la verdad es óptimo. Simplifica enormemente la búsqueda.
- **Subasta de Vickrey** (1961, segundo precio en sobre cerrado): gana quien ofrece más, pero paga la segunda oferta. Ofrecer exactamente lo que el bien vale para uno es estrategia dominante.
- **Teorema de Gibbard-Satterthwaite** (1973, 1975): con tres o más alternativas, todo sistema de votación que no sea dictatorial es manipulable por voto estratégico. Es primo del **teorema de imposibilidad de Arrow** (1951): ninguna regla de agregación de preferencias cumple a la vez un conjunto mínimo de condiciones razonables.
- **Emparejamiento estable**: el algoritmo de aceptación diferida de Gale y Shapley (1962) produce emparejamientos estables. Alvin Roth lo aplicó a la asignación de residencias médicas, escuelas y donaciones cruzadas de riñón (Nobel 2012, con Shapley).

Para las Ciencias Sociales, el diseño de mecanismos es la versión técnica de una vieja pregunta de la filosofía política: cómo hacer instituciones que funcionen aunque las personas no sean virtuosas. Kant la planteó con su "pueblo de demonios" (ver Partes II y V).

### 11. Racionalidad acotada, economía conductual y experimental

- **Herbert Simon**: la racionalidad real es **acotada**; las personas buscan soluciones satisfactorias (*satisficing*), no óptimas.
- **Kahneman y Tversky** (teoría prospectiva, 1979): las pérdidas pesan más que las ganancias equivalentes (**aversión a la pérdida**), los resultados se evalúan contra un punto de referencia y las probabilidades se distorsionan.
- **Modelos de nivel k.** En el "concurso de belleza" de Rosemarie Nagel (1995), cada participante elige un número de 0 a 100 y gana quien se acerque a 2/3 del promedio. El equilibrio de Nash es 0. La mayoría elige alrededor de 33 (nivel 1) o 22 (nivel 2). La metáfora viene de Keynes: en la bolsa no se elige lo que uno cree mejor, sino lo que uno cree que los demás creen mejor.
- **Equilibrio de respuesta cuántica** (McKelvey y Palfrey, 1995): los jugadores cometen errores, pero los más costosos son menos probables.
- **Preferencias sociales**: aversión a la desigualdad (Fehr y Schmidt, 1999), reciprocidad basada en intenciones (Rabin, 1993). Explican el ultimátum y el castigo en bienes públicos sin abandonar el formalismo: cambian la función de utilidad.

### 12. Usos en ciencia política y relaciones internacionales

- **James Fearon** ("Rationalist Explanations for War", 1995): si la guerra es costosa, siempre existe un acuerdo que ambas partes preferirían. Que igual ocurra se explica por tres mecanismos: **información privada con incentivos para mentir** sobre la propia fuerza o determinación, **problemas de compromiso** (no poder prometer creíblemente no aprovechar ventajas futuras) e **indivisibilidad** de lo disputado.
- **Adam Przeworski** (*Democracia y mercado*, 1991): la democracia como equilibrio en el que las fuerzas que pierden elecciones prefieren esperar la próxima a patear el tablero. Las transiciones como juegos entre duros y blandos del régimen y moderados y radicales de la oposición.
- **George Tsebelis** (*Veto Players*, 2002): la estabilidad de las políticas depende del número y la distancia ideológica de los actores con poder de veto.
- **Juegos anidados** (Tsebelis, 1990): conductas que parecen irracionales en un juego son racionales en otro superior (por ejemplo, un dirigente que pierde en el parlamento para ganar en su partido).

### 13. Críticas desde las Ciencias Sociales

La teoría de juegos es poderosa, pero sus supuestos son materia de debate. Las críticas más serias:

- **Preferencias exógenas.** La teoría toma las preferencias como dadas. Pero la sociología, la antropología y los experimentos transculturales muestran que se forman socialmente. La pregunta de cómo se producen los sujetos que tienen esas preferencias queda fuera del modelo; es la pregunta de Foucault (Parte III).
- **El sujeto atomizado.** Amartya Sen ("Rational Fools", 1977) distingue **simpatía** (el bienestar ajeno entra en mi utilidad) y **compromiso** (actúo por un principio aunque me perjudique). El compromiso rompe la equivalencia entre elección y bienestar; reducirlo todo a utilidad produce "tontos racionales".
- **Habitus y práctica.** Pierre Bourdieu criticó la ilusión escolástica de proyectar el cálculo del teórico sobre agentes que actúan desde un *habitus*, un sentido práctico del juego incorporado, sin calcular. Paradójicamente, Bourdieu también usó la palabra *estrategia*, pero sin cálculo consciente.
- **Patologías empíricas.** Donald Green e Ian Shapiro (*Pathologies of Rational Choice Theory*, 1994) acusaron a la elección racional en ciencia política de producir pocos hallazgos empíricos sólidos, de ajustar los modelos después de los hechos y de buscar confirmaciones en vez de pruebas.
- **Mecanismos, no leyes.** Jon Elster, que pasó de entusiasta a crítico, propuso entender las ciencias sociales como colecciones de **mecanismos** (*Tuercas y tornillos*, 1989): patrones causales frecuentes que se activan en condiciones no siempre especificables. La teoría de juegos provee mecanismos, no leyes generales.
- **Historia del saber.** Philip Mirowski (*Machine Dreams*, 2002) y S. M. Amadae (*Rationalizing Capitalist Democracy*, 2003) reconstruyeron cómo la teoría de juegos y la elección racional se formaron en el complejo militar-académico de la Guerra Fría y cómo moldearon una imagen del ciudadano como maximizador. Es una crítica genealógica, en clave foucaultiana: el modelo no solo describe sujetos, también ayuda a producirlos y gobernarlos.
- **Defensa razonable.** Schelling (*Micromotives and Macrobehavior*, 1978) mostró con su modelo de segregación que preferencias individuales moderadas (no querer ser minoría extrema en el barrio) producen segregación intensa a nivel agregado. Es un ejemplo de lo que la teoría hace mejor: revelar consecuencias agregadas no queridas de acciones individuales, algo que las Ciencias Sociales buscan desde Merton y su análisis de las consecuencias no anticipadas.

## Parte II. Aristóteles: la ética como arte de vivir bien en la polis

Para Aristóteles la pregunta ética no es "qué regla debo cumplir" sino **qué tipo de persona conviene llegar a ser** para vivir una vida lograda, y esa pregunta es inseparable de la política: solo en una comunidad bien ordenada se forma un buen carácter.

### Contexto y obra

Aristóteles nació en Estagira, Macedonia, en 384 a. C. y murió en Calcis en 322 a. C. Estudió veinte años en la Academia de Platón, fue tutor de Alejandro Magno y fundó su propia escuela, el Liceo (sus seguidores se llamaron *peripatéticos*). Lo que conservamos son sobre todo textos de enseñanza, apuntes de curso más que obras pulidas; los diálogos publicados se perdieron. Para este informe importan:

- **Ética nicomáquea** (EN, diez libros): la obra central. También la *Ética eudemia* y la *Gran moral*, de autoría discutida.
- **Política** (ocho libros).
- **Retórica** (tres libros).
- Como fondo: *Física* y *Metafísica* (causas, acto y potencia), *De anima* (el alma), *Organon* (lógica).

### El marco: naturaleza y finalidad

Aristóteles piensa todo con una **teleología**: cada cosa natural tiende a un fin (*telos*) que realiza su naturaleza. La bellota tiende a ser roble. Explicar algo es dar sus **cuatro causas**: material (de qué está hecho), formal (qué es), eficiente (qué lo produjo) y final (para qué es). La distinción entre **potencia** y **acto** completa el cuadro: el ser humano nace con capacidades que deben actualizarse. La ética es la ciencia de cómo actualizar bien las capacidades humanas.

Aristóteles advierte que la ética no admite la exactitud de la matemática: es un saber de lo que sucede "la mayoría de las veces". Exigirle más precisión de la que su objeto permite es un error de método. Esta advertencia anticipa debates actuales sobre la cuantificación en Ciencias Sociales.

### Eudaimonía: el bien supremo

El libro I de la *Ética nicomáquea* arranca constatando que toda acción apunta a un bien. Los bienes se ordenan: la rienda sirve a la equitación, la equitación a la estrategia militar, y así. Tiene que haber un bien último, buscado por sí mismo y no por otra cosa. Todos lo llaman **eudaimonía**.

Traducirla como "felicidad" engaña, porque hoy felicidad suena a estado de ánimo. Eudaimonía es más bien **florecimiento**, **vida lograda**: una actividad, no una sensación.

Para definirla, Aristóteles usa el **argumento de la función** (*ergon*). El bien del flautista está en tocar bien la flauta. El bien humano debe estar en ejercer bien lo propio del ser humano. Lo propio no es nutrirse (lo comparten las plantas) ni sentir (lo comparten los animales), sino la actividad racional. Conclusión: la eudaimonía es **actividad del alma conforme a la virtud**, y si hay varias, conforme a la mejor y más completa, **en una vida entera**. Una golondrina no hace verano, ni un buen día hace una vida lograda.

Dos matices que lo separan de un idealismo ingenuo:

- **Los bienes exteriores importan.** Sin amigos, recursos, salud, ciudadanía y algo de buena fortuna, la eudaimonía es difícil. El ejemplo es Príamo, rey de Troya, virtuoso pero arruinado por desgracias al final: nadie lo llamaría plenamente dichoso.
- **Las tres vidas.** La vida de placer (propia de animales), la vida política (orientada al honor, pero el honor depende de otros) y la vida contemplativa (dedicada al conocimiento). El libro X dirá que la contemplativa es la más alta, lo que abre una tensión con la vida política que nunca se resuelve del todo.

### Virtudes: carácter formado por hábito

El alma tiene una parte racional y otra que no lo es pero puede escuchar a la razón (deseos, emociones). De ahí dos clases de virtudes (*aretai*, excelencias):

- **Virtudes intelectuales (dianoéticas)**: se adquieren por enseñanza y experiencia.
- **Virtudes éticas (del carácter)**: se adquieren por **hábito**. La palabra *ēthos* (carácter) viene de *ethos* (costumbre).

La tesis es fuerte: **nos hacemos justos haciendo cosas justas, valientes haciendo cosas valientes**, igual que nos hacemos citaristas tocando la cítara. La virtud no es natural ni antinatural: tenemos la capacidad, y la práctica la forma. Por eso la educación moral es temprana, práctica y política, y por eso el legislador tiene un rol en formar hábitos.

Técnicamente, la virtud es una ***hexis***: una disposición estable adquirida a actuar y a sentir de cierta manera. No es una emoción ni una capacidad, sino una manera estable de relacionarse con las emociones. El virtuoso no solo hace lo correcto: **siente placer** en hacerlo y siente las emociones adecuadas, en el momento, hacia las personas y en la medida adecuados.

### El término medio (*mesotēs*)

La virtud ética es un **término medio** entre dos vicios, uno por exceso y otro por defecto, **relativo a nosotros** y determinado por la razón tal como lo determinaría la persona prudente. Tres aclaraciones evitan malentendidos habituales:

- **No es mediocridad ni promedio aritmético.** Es lo adecuado a la situación: a veces el medio es una ira intensa, si la ofensa es grave.
- **Es relativo a la persona y al caso**, como la dieta de un atleta no es la de un principiante.
- **Algunas acciones y pasiones no tienen medio**: el adulterio, el robo, el homicidio, la envidia, el regocijo por el mal ajeno. Son malas en sí.

| Ámbito | Vicio por defecto | Virtud | Vicio por exceso |
| --- | --- | --- | --- |
| Miedo y confianza | Cobardía | Coraje | Temeridad |
| Placeres corporales | Insensibilidad | Templanza | Desenfreno |
| Dar y recibir dinero | Avaricia | Liberalidad | Prodigalidad |
| Gastos públicos grandes | Mezquindad | Magnificencia | Ostentación vulgar |
| Honor en gran escala | Pusilanimidad | Magnanimidad | Vanidad |
| Ira | Indolencia | Mansedumbre | Irascibilidad |
| Decir la verdad sobre uno mismo | Falsa modestia (*eironeia*) | Veracidad | Jactancia |
| Trato social | Hosquedad | Amabilidad | Adulación (o servilismo) |
| Humor | Rusticidad | Ingenio | Bufonería |

La magnanimidad (*megalopsychia*) es la virtud más incómoda para lectores modernos: el magnánimo se considera digno de grandes honores y lo es. Muestra que la ética aristotélica es también una ética aristocrática de la excelencia, no de la humildad cristiana.

### Acción voluntaria, elección y responsabilidad

El libro III es una pequeña teoría de la acción con consecuencias jurídicas evidentes:

- Es **involuntario** lo que se hace por **fuerza** (el origen de la acción es externo y el agente no aporta nada) o por **ignorancia** de las circunstancias particulares (no saber que el arma estaba cargada), si después el agente lo lamenta.
- Hay casos **mixtos**: tirar la carga por la borda en una tormenta para salvar el barco. Son voluntarios en el momento, aunque nadie los elegiría en abstracto.
- La ignorancia de lo que uno debería saber, o la que uno mismo causó (el ebrio), no excusa. El legislador de entonces duplicaba la pena al ebrio; Aristóteles lo aprueba porque el origen estaba en él.
- La **elección deliberada** (*proairesis*) es un deseo deliberado de algo que está en nuestro poder. Se delibera sobre los **medios**, no sobre los fines: el médico no delibera si curar, sino cómo. (Es un punto discutido: muchos intérpretes sostienen que la *phronesis* también especifica qué cuenta como fin en el caso concreto.)
- Somos **responsables de nuestro carácter**, porque lo formamos con actos. El injusto no puede alegar que "es así": se hizo así.

### *Phronesis*: la sabiduría práctica

El libro VI distingue las virtudes intelectuales:

| Virtud | Objeto | Ejemplo |
| --- | --- | --- |
| *Epistēmē* (ciencia) | Lo necesario y universal, demostrable | Geometría |
| *Technē* (arte, técnica) | Producir algo que puede ser de otro modo | Carpintería, medicina |
| *Phronēsis* (prudencia, sabiduría práctica) | Actuar bien en lo particular y variable | Decidir qué hacer ahora, con estas personas |
| *Nous* (intelecto) | Captar los primeros principios | Axiomas |
| *Sophia* (sabiduría teórica) | Ciencia más intelecto sobre lo más alto | Metafísica |

Dos distinciones son decisivas:

- **Producción (*poiesis*) y acción (*praxis*).** La técnica produce algo cuyo fin está fuera de la actividad (la casa). La acción tiene su fin en sí misma: actuar bien es el fin. Por eso la ética no es una técnica: no hay un manual que aplicar.
- ***Phronesis* y astucia (*deinotēs*).** La astucia es la habilidad de encontrar medios eficaces para cualquier fin. La *phronesis* es astucia **puesta al servicio de fines buenos**. Sin virtud ética, la habilidad estratégica es mera astucia, incluso maldad competente. Este punto es clave para la Parte V: la teoría de juegos formaliza la *deinotēs*, no la *phronesis*.

La *phronesis* requiere **experiencia**. Por eso los jóvenes pueden ser buenos matemáticos pero rara vez prudentes. El criterio último no es una regla sino una persona: el **prudente** (*phronimos*) es la medida de lo correcto. Y prudencia y virtud ética se necesitan mutuamente: la virtud fija el fin correcto; la prudencia, el camino.

### La *akrasia*: saber lo correcto y no hacerlo

Sócrates sostenía que nadie hace el mal a sabiendas. Aristóteles responde con el libro VII: existe la ***akrasia*** (incontinencia, debilidad de la voluntad). El incontinente sabe lo que debe hacer y su deseo lo arrastra; el continente (*enkratēs*) también siente el deseo, pero lo domina; el templado ya no lo siente desordenadamente. La explicación usa el **silogismo práctico**: la premisa universal ("no hay que comer dulces") está presente, pero la premisa particular ("esto es un dulce") queda oscurecida por el deseo, como en el que duerme o está ebrio. El debate sobre la debilidad de la voluntad llega hasta Donald Davidson y Jon Elster.

### La justicia (libro V)

El libro V es probablemente el texto más leído por juristas y es central para pensar desigualdad.

- **Justicia general o legal**: cumplir las leyes, en la medida en que buscan el bien común. Es la virtud completa en relación con otros.
- **Justicia particular**: tener la parte que corresponde, ni más ni menos. Su vicio es la *pleonexia*, el querer más de lo debido.

La particular se divide en dos:

1. **Justicia distributiva**: reparto de honores, bienes y cargos comunes. Sigue una **proporción geométrica**: a cada uno según su mérito (*axia*). Si A merece el doble que B, debe recibir el doble. El punto políticamente explosivo es que **todos aceptan la proporción, pero discuten qué cuenta como mérito**: los demócratas dicen libertad, los oligarcas riqueza, los aristócratas virtud. El conflicto político es, en el fondo, un conflicto sobre el criterio de mérito.
2. **Justicia correctiva o rectificadora**: rige en las transacciones, voluntarias (compraventa, préstamo) e involuntarias (robo, agresión). Sigue una **proporción aritmética**: no importa quién es cada uno; el juez restablece la igualdad quitando la ganancia al que la obtuvo y compensando la pérdida del otro.

Aristóteles agrega la **reciprocidad proporcional** en el intercambio y una teoría de la **moneda** (*nomisma*): su nombre viene de *nomos* (ley, convención), porque su valor no es natural sino convencional, y sirve para hacer conmensurables cosas distintas a partir de la necesidad (*chreia*). Es una de las fuentes de la teoría económica del valor.

Por último, la **equidad** (*epieikeia*): corrige la ley allí donde falla por su generalidad. El legislador habla en universal, pero hay casos que no previó; el juez equitativo decide como el legislador habría decidido si hubiera estado presente. Aristóteles usa la imagen de la regla de plomo de los constructores de Lesbos, que se adapta a la forma de la piedra. Es el antecedente directo de la discusión jurídica sobre interpretación, lagunas y principios.

### La amistad (libros VIII y IX)

Dos libros enteros, casi un quinto de la obra, se dedican a la ***philia***, que abarca amistad, vínculo familiar y lazo cívico. Hay tres especies según su motivo: por **utilidad**, por **placer** y por **virtud**. Las dos primeras son accidentales y se disuelven cuando cesa el beneficio. La tercera es la perfecta: se quiere al otro por lo que es, y es estable. El amigo es "otro yo", y a través de él uno se conoce mejor.

La **concordia** (*homonoia*) es la amistad política: acuerdo sobre lo que conviene a la ciudad. Aristóteles sostiene que si los ciudadanos fueran amigos no harían falta leyes de justicia, pero que siendo justos todavía necesitarían amistad. El lazo social no se reduce al contrato.

### Libro X: placer y contemplación

El placer no es el bien, pero acompaña y **completa la actividad** cuando se ejerce bien, "como la lozanía a la juventud". La vida más alta es la contemplativa, la más autosuficiente y continua, casi divina. La vida según las otras virtudes es dichosa en segundo grado. Y la obra termina pasando la posta a la *Política*: como la virtud se forma por hábitos y las leyes forman hábitos, quien quiera hacer mejores a los demás debe ser **legislador**.

### La *Política*

- **El ser humano es un animal político** (*zōon politikon*) por naturaleza, más que las abejas, porque tiene ***logos***: palabra y razón, con la que expresa lo conveniente y lo dañino, lo justo y lo injusto. Quien vive fuera de la *polis* es bestia o dios.
- **La *polis* es anterior por naturaleza al individuo**, como el todo es anterior a la parte: una mano separada del cuerpo ya no es mano. Esto no es cronológico sino teleológico: la *polis* surge de la familia y la aldea para satisfacer necesidades, pero existe para **vivir bien**. Su ideal es la autarquía.
- **Economía y crematística.** La *oikonomia* (administración del hogar) busca lo necesario y tiene un límite. La **crematística** comercial busca acumular dinero sin límite, y la **usura** es la forma más antinatural porque hace que el dinero engendre dinero. Marx retomará esta distinción en *El capital* (fórmula M-D-M frente a D-M-D').
- **Esclavitud natural.** En el libro I Aristóteles defiende que hay personas esclavas por naturaleza, y subordina a las mujeres. Es indefendible, y él mismo deja ver tensiones (reconoce que hay esclavos por convención y que la guerra no garantiza justicia). Una lectura desde las Ciencias Sociales lo toma como ejemplo de cómo un pensamiento naturaliza la jerarquía de su tiempo: la "naturaleza" funciona como justificación del orden social.
- **Crítica a Platón** (libro II). La comunidad de bienes y de mujeres de la *República* destruiría el cuidado: lo que es de todos no lo cuida nadie. Es una formulación temprana de la tragedia de los comunes.
- **Ciudadano** (libro III): quien participa en deliberar y juzgar. Ser buen ciudadano depende del régimen; ser buen ser humano no. Solo coinciden en el régimen mejor.
- **Clasificación de los regímenes.** Dos criterios: cuántos gobiernan y en interés de quién.

| Gobiernan | Rectos (bien común) | Desviados (interés de quien gobierna) |
| --- | --- | --- |
| Uno | Monarquía | Tiranía |
| Pocos | Aristocracia | Oligarquía |
| Muchos | *Politeia* (república) | Democracia (en su forma extrema) |

Aristóteles corrige enseguida el esquema con sociología: lo que realmente distingue oligarquía de democracia no es el número sino la **clase**. Oligarquía es el gobierno de los ricos; democracia, el de los pobres, que casualmente son muchos. La ***politeia*** es una mezcla de ambos y funciona mejor cuando hay una **clase media** amplia, que no envidia como los pobres ni desprecia como los ricos. Es la primera teoría sociológica de la estabilidad política.

- **Sabiduría de la multitud** (libro III). Muchos, individualmente mediocres, pueden juzgar mejor juntos que unos pocos excelentes, como un banquete al que todos aportan es mejor que uno pagado por uno solo. Es un antecedente del teorema del jurado de Condorcet y de las discusiones sobre inteligencia colectiva.
- **Revoluciones** (libro V): causas del cambio de régimen, sobre todo la desigualdad percibida como injusta, el miedo, el desprecio y el crecimiento desproporcionado de un sector.
- **Educación** (libros VII y VIII): debe ser pública y común, porque el fin de la ciudad es uno solo.

### La *Retórica*

Aristóteles define la retórica como la capacidad de ver, en cada caso, lo que puede persuadir. Es contraparte de la dialéctica: ambas tratan sobre lo opinable, no sobre lo demostrable.

- **Tres pruebas técnicas**: ***ethos*** (el carácter del orador, su credibilidad), ***pathos*** (la disposición emocional del auditorio) y ***logos*** (el argumento mismo).
- **El entimema**: un silogismo retórico que parte de premisas probables y suele omitir alguna que el público completa. Por eso persuade: el público participa.
- **Tres géneros**: deliberativo (asamblea, sobre el futuro, lo conveniente), judicial (tribunal, sobre el pasado, lo justo) y epidíctico (ceremonias, sobre el presente, lo noble o vergonzoso).
- **Tópicos**: lugares comunes de argumentación.

El libro II es un tratado sobre las emociones (ira, calma, miedo, vergüenza, compasión, indignación, envidia) que todavía se lee en psicología social y en estudios de comunicación política. Para el periodismo y el análisis del discurso, la *Retórica* sigue siendo la primera caja de herramientas.

### Recepción y usos actuales

- **Edad Media**: transmitido por comentaristas árabes (Averroes) y sintetizado con el cristianismo por Tomás de Aquino, se vuelve "el Filósofo".
- **Modernidad**: Maquiavelo y Hobbes rompen con la teleología; Hobbes niega explícitamente que el hombre sea animal político por naturaleza.
- **Siglo XX**: Hannah Arendt (*La condición humana*, 1958) recupera la distinción entre labor, trabajo y acción, y la *praxis* como espacio de libertad. Hans-Georg Gadamer hace de la *phronesis* el modelo de la comprensión hermenéutica. Alasdair MacIntyre y Martha Nussbaum la reactivan en ética (Parte II, contraste).
- **Ciencias Sociales phronéticas**: Bent Flyvbjerg (*Making Social Science Matter*, 2001) propone que las Ciencias Sociales no compitan con las naturales en *epistēmē*, sino que se piensen como *phronesis*: conocimiento contextual que ayuda a deliberar sobre valores y poder, con preguntas como "¿hacia dónde vamos?, ¿quién gana y quién pierde, y con qué mecanismos de poder?, ¿es deseable?, ¿qué deberíamos hacer?". Flyvbjerg combina explícitamente a Aristóteles con Foucault.
- **Bourdieu** tomó de la *hexis* aristotélica (vía la escolástica) su noción de *habitus*: disposiciones duraderas incorporadas, que se expresan hasta en la postura del cuerpo (*hexis* corporal).

## Parte II. Kant: autonomía, deber y derecho

Para Kant una acción tiene valor moral cuando se hace **por deber**, siguiendo una máxima que uno podría querer como ley para todos, y el núcleo de esa moral es la **autonomía**: darse a uno mismo la ley racional, en vez de recibirla de la naturaleza, la autoridad o el deseo. De esa misma idea de libertad deriva su teoría del derecho, del Estado republicano y de la paz entre Estados.

### Contexto y obra

Immanuel Kant (1724–1804) vivió toda su vida en Königsberg, Prusia Oriental (hoy Kaliningrado, Rusia). Se suele dividir su obra en un período precrítico y uno crítico, que empieza con la *Crítica de la razón pura* (1781). Para este informe importan:

| Año | Obra | Tema central |
| --- | --- | --- |
| 1781 / 1787 | *Crítica de la razón pura* | Límites del conocimiento; libertad y causalidad |
| 1784 | *Respuesta a la pregunta: ¿qué es la Ilustración?* | Autonomía intelectual, uso público de la razón |
| 1784 | *Idea de una historia universal en sentido cosmopolita* | Insociable sociabilidad, progreso |
| 1785 | *Fundamentación de la metafísica de las costumbres* | Imperativo categórico |
| 1788 | *Crítica de la razón práctica* | Libertad, ley moral, sumo bien |
| 1790 | *Crítica del juicio* | Juicio estético y teleológico |
| 1793 | *Sobre el dicho común: esto puede ser correcto en teoría pero no sirve para la práctica* | Derecho político, contrato originario |
| 1795 | *Hacia la paz perpetua* | Derecho internacional y cosmopolita, publicidad |
| 1797 | *Metafísica de las costumbres* (Doctrina del derecho y Doctrina de la virtud) | Sistema del derecho y de la ética |
| 1797 | *Sobre un supuesto derecho a mentir por filantropía* | El caso del asesino en la puerta |
| 1798 | *El conflicto de las facultades* | Revolución francesa como signo de progreso |
| 1798 | *Antropología en sentido pragmático* | Conocimiento empírico del ser humano |

### El giro copernicano y la libertad

Antes de Kant, el conocimiento se pensaba como adecuación de la mente al objeto. Kant invierte la relación: conocemos los objetos según las **formas de nuestra sensibilidad** (espacio y tiempo) y las **categorías del entendimiento** (causalidad, sustancia, unidad, etc.). Conocemos **fenómenos**, cosas tal como se nos aparecen, no **cosas en sí** (noúmenos). La razón que intenta ir más allá de toda experiencia posible cae en contradicciones (**antinomias**).

La tercera antinomia es decisiva para la ética: la razón puede argumentar tanto que todo ocurre por causas naturales como que hay una causalidad por libertad. Kant la resuelve así: como fenómenos estamos sometidos a la causalidad natural; pero no hay contradicción en pensarnos, como seres racionales, libres. La libertad **no se puede probar teóricamente**, pero se nos impone en la experiencia moral: la conciencia de la ley moral (que Kant llama un "hecho de la razón") nos revela que somos libres. "Debes, luego puedes."

### La buena voluntad y el deber

La *Fundamentación* empieza con una tesis rotunda: nada es bueno sin restricción, salvo una **buena voluntad**. El talento, el coraje, la riqueza, incluso la felicidad, pueden servir al mal. La buena voluntad vale por sí, aunque no logre su objetivo, como una joya que brilla por luz propia.

Para aislar la buena voluntad, Kant analiza el **deber** y distingue:

- Acciones **contrarias al deber**.
- Acciones **conformes al deber pero por inclinación o interés**. El ejemplo es el comerciante que no estafa a un niño porque le conviene mantener su reputación: hace lo correcto, pero por cálculo.
- Acciones **por deber**. Solo estas tienen valor moral propiamente dicho.

El ejemplo más incómodo: quien ayuda a otros por simpatía natural actúa bien y merece aprecio, pero su acción no tiene todavía valor moral; quien, sin sentir simpatía, ayuda por deber, muestra el valor moral con claridad. La lectura caricaturesca dice que Kant prefiere a los fríos; la lectura cuidadosa dice que busca el **principio** que hace valiosa la acción, y que en el caso puro es más visible. (Friedrich Schiller se burló con un epigrama: ayudo con gusto a mis amigos, y me inquieta no ser virtuoso por eso.)

De ahí tres tesis:

1. El valor moral está en la **máxima** (el principio subjetivo de la acción), no en el resultado.
2. El deber es la **necesidad de una acción por respeto a la ley**.
3. El **respeto** es el único sentimiento producido por la razón misma, no por la inclinación.

### Máximas, imperativos y el imperativo categórico

Una **máxima** es el principio que de hecho sigue quien actúa: "cuando necesite dinero, voy a pedir prestado prometiendo devolverlo, aunque sepa que no voy a poder". Una **ley** es un principio objetivo, válido para todo ser racional.

Para seres como nosotros, que no seguimos espontáneamente la razón, la ley se presenta como **imperativo**. Hay dos clases:

- **Hipotéticos**: mandan algo como medio para un fin. Pueden ser de **habilidad** ("si querés construir un puente, calculá las cargas") o de **prudencia** ("si querés ser feliz, cuidá tu salud"). Su fuerza depende de que quieras el fin.
- **Categórico**: manda algo incondicionalmente, sin depender de ningún fin deseado. Es el imperativo de la moralidad.

Esta distinción es fundamental para la Parte V: toda la teoría de juegos se mueve en el terreno de los imperativos hipotéticos.

Kant da varias formulaciones del imperativo categórico, que según él expresan la misma ley desde ángulos distintos. En paráfrasis:

1. **Fórmula de la ley universal (FLU).** Actuá solo según la máxima que puedas querer, al mismo tiempo, que se convierta en ley universal.
2. **Fórmula de la ley de la naturaleza (FLN).** Actuá como si tu máxima fuera a convertirse, por tu voluntad, en una ley universal de la naturaleza.
3. **Fórmula de la humanidad (FH).** Tratá a la humanidad, tanto en tu persona como en la de cualquier otro, siempre al mismo tiempo como fin y nunca solamente como medio.
4. **Fórmula de la autonomía (FA).** Actuá de modo que tu voluntad pueda considerarse a sí misma como legisladora universal a través de sus máximas.
5. **Fórmula del reino de los fines (FRF).** Actuá como miembro legislador de un reino posible de fines, es decir, una comunidad de seres racionales unidos por leyes comunes que cada uno se da.

### Cómo se aplica la ley universal: dos tipos de contradicción

Kant aplica la FLU a cuatro ejemplos y obtiene dos clases de deberes:

| Ejemplo | Prueba | Resultado | Tipo de deber |
| --- | --- | --- | --- |
| Promesa falsa para obtener dinero | Si todos prometieran en falso cuando les conviene, nadie creería en las promesas y la máxima no podría ni siquiera cumplirse | **Contradicción en la concepción**: la máxima universalizada se destruye a sí misma | Perfecto, hacia otros |
| Suicidio por hastío de la vida | Usar el amor a uno mismo, que sirve para preservar la vida, para destruirla | Contradicción en la concepción (argumento muy discutido) | Perfecto, hacia uno mismo |
| No cultivar los propios talentos | Un mundo así es pensable, pero un ser racional no puede quererlo | **Contradicción en la voluntad** | Imperfecto, hacia uno mismo |
| No ayudar nunca a nadie | Un mundo así es pensable, pero quien lo quisiera se privaría de la ayuda que podría necesitar | Contradicción en la voluntad | Imperfecto, hacia otros |

Los **deberes perfectos** no admiten excepciones a favor de la inclinación. Los **imperfectos** dejan margen sobre cuándo, cómo y a quién: hay que ayudar, pero no a todos siempre.

El ejemplo de la promesa falsa tiene una estructura notable: la máxima del mentiroso es **parasitaria** de una práctica que solo existe porque la mayoría no actúa así. El que defecciona en un dilema del prisionero hace exactamente lo mismo. Volveremos sobre esto.

### La humanidad como fin: dignidad y no instrumentalización

En el reino de los fines, todo tiene **precio** o **dignidad**. Lo que tiene precio puede reemplazarse por un equivalente. Lo que tiene dignidad está por encima de todo precio y no admite equivalente. Los seres racionales, por su capacidad de autonomía, tienen dignidad.

La fórmula de la humanidad no prohíbe usar a otros como medios (lo hacemos al pedirle un café a alguien), sino tratarlos **solo** como medios: engañarlos o forzarlos de modo que no puedan consentir ni compartir el fin de la acción. Christine Korsgaard y Onora O'Neill lo leyeron así: instrumentalizar es actuar sobre otro de una manera a la que no podría prestar consentimiento posible.

Es la base filosófica más directa del lenguaje contemporáneo de los derechos humanos. La Ley Fundamental alemana de 1949 empieza declarando intangible la dignidad humana. La doctrina alemana desarrolló la **fórmula del objeto** (Günter Dürig): se viola la dignidad cuando la persona es reducida a mero objeto de la acción estatal. Con ese criterio, el Tribunal Constitucional Federal alemán declaró inconstitucional en 2006 la norma de la Ley de Seguridad Aérea que autorizaba derribar un avión de pasajeros secuestrado para salvar a más personas en tierra: el Estado no puede disponer de las vidas de los pasajeros como medio, aunque el cálculo de vidas favorezca derribarlo. Es un caso de laboratorio del choque entre deontología y consecuencialismo.

### Autonomía y heteronomía

La voluntad es **autónoma** cuando se da a sí misma su ley por razón. Es **heterónoma** cuando la ley le viene de afuera: de los deseos, de la naturaleza, de Dios entendido como legislador externo, de la autoridad o de la búsqueda de felicidad.

Esto tiene una consecuencia filosófica fuerte: para Kant **toda ética de la felicidad es heterónoma**, incluida la de Aristóteles. Si la moral se fundara en lo que nos hace florecer, dependería de hechos empíricos variables sobre la naturaleza humana y no podría obligar incondicionalmente. Este es el punto de choque central de la Parte II.

### El asesino en la puerta

En 1797 Benjamin Constant objetó que un deber absoluto de veracidad haría imposible la vida social: tendríamos que decirle la verdad al asesino que pregunta dónde se esconde nuestro amigo. Kant respondió (*Sobre un supuesto derecho a mentir por filantropía*) sosteniendo que no hay derecho a mentir, ni siquiera en ese caso, porque la veracidad es un deber hacia la humanidad en general y la mentira socava la confianza en las declaraciones, que es la base del derecho. Agregó que, si uno miente y el amigo, sin que lo sepamos, había salido y el asesino lo encuentra, uno es responsable de las consecuencias.

El caso es el ejemplo favorito contra Kant. Las respuestas kantianas contemporáneas son variadas: Korsgaard sostiene que la fórmula de la humanidad permite mentirle a quien ya se ha puesto fuera de la relación de confianza; otros distinguen la ética del derecho; otros notan que Kant discutía el plano jurídico de las declaraciones, no un deber de delatar. Para un lector desde Derecho o periodismo, el caso abre una pregunta legítima: ¿cuándo el secreto y el engaño protegen a terceros, y quién decide?

### Crítica de la razón práctica: el sumo bien y los postulados

La virtud (merecer ser feliz) no garantiza la felicidad en este mundo. Pero la razón exige pensar como posible el **sumo bien**: la unión de virtud y felicidad proporcional. Para que sea pensable, Kant **postula** tres cosas que no puede probar teóricamente: la **libertad**, la **inmortalidad del alma** (para un progreso moral infinito) y la **existencia de Dios** (como garante de la proporción). Es moral fundando religión, no al revés.

### La doctrina del derecho

Kant distingue nítidamente **moralidad** y **legalidad**:

- La **ética** exige actuar por deber; se ocupa de la intención y no puede imponerse por coacción.
- El **derecho** solo exige la conformidad externa de la acción, y es compatible con la coacción.

El **principio universal del derecho**, parafraseado: es justa toda acción que, o cuya máxima, permite que la libertad del arbitrio de cada uno coexista con la libertad de todos según una ley universal. El derecho no se ocupa de los deseos ni del bienestar, sino de la compatibilidad de las libertades externas.

La **coacción** es legítima cuando es un "impedimento de un impedimento de la libertad": si alguien obstaculiza mi libertad legítima, impedirlo restablece la libertad. Por eso derecho y facultad de coaccionar son lo mismo.

Hay un único **derecho innato**: la libertad, entendida como independencia respecto del arbitrio coactivo de otro, en tanto pueda coexistir con la libertad de todos. Contiene la igualdad innata y el derecho a ser considerado irreprochable mientras no se haya dañado a nadie (una raíz de la presunción de inocencia).

**Derecho privado.** La propiedad, los contratos y las relaciones domésticas pueden existir en el estado de naturaleza, pero solo de modo **provisional**, porque nadie tiene autoridad para garantizarlos frente a otros. (Kant incluye una figura hoy inaceptable, el "derecho personal de carácter real", que trata a cónyuges, hijos y servidumbre como posesiones con ciertas protecciones.)

**Derecho público.** Hay un **deber jurídico de salir del estado de naturaleza** y entrar en un estado civil, aunque los hombres fueran buenos, porque en el estado de naturaleza cada uno juzga por sí lo justo y nadie está seguro. El **contrato originario** no es un hecho histórico sino una **idea de la razón** con función de prueba: una ley es legítima si **pudiera** haber surgido de la voluntad unida de todo un pueblo. Si es imposible que todo un pueblo la acepte (por ejemplo, privilegios hereditarios para una clase), es injusta.

El Estado justo es **republicano**: separación de poderes (legislativo, ejecutivo, judicial), soberanía legislativa del pueblo unido y ciudadanos con tres atributos: **libertad legal**, **igualdad civil** e **independencia civil**. Este último atributo lleva a Kant a distinguir ciudadanos **activos** y **pasivos** y a excluir del voto a mujeres, asalariados y dependientes. La exclusión contradice su propio principio de que nadie puede ser obligado a lo que no podría consentir, y la crítica feminista y republicana lo marcó como síntoma de cómo un universalismo formal arrastra jerarquías sociales.

Dos tesis polémicas:

- **No hay derecho de resistencia** ni de rebelión contra el soberano, incluso injusto: solo libertad de pluma. Sin embargo, en *El conflicto de las facultades* Kant celebra el **entusiasmo** del público europeo ante la Revolución francesa como "signo histórico" de una disposición moral de la humanidad hacia el progreso. La tensión entre ambos textos sigue discutiéndose.
- **Pena retributiva.** Castigar no es un medio para otro fin (disuadir, rehabilitar) sino lo que el delito merece; usar al condenado solo como medio violaría su dignidad. Su ejemplo extremo: una sociedad que se disolviera debería ejecutar antes al último asesino en prisión, para que la culpa no recaiga sobre el pueblo.

### Hacia la paz perpetua (1795)

El texto imita la forma de un tratado de paz, con artículos. Contiene seis **artículos preliminares**, que prohíben prácticas que hacen imposible la paz:

1. Ningún tratado de paz vale como tal si se hizo con **reserva secreta** de materia para una guerra futura.
2. Ningún Estado independiente puede ser adquirido por otro (por herencia, compra, permuta o donación).
3. Los ejércitos permanentes deben desaparecer con el tiempo.
4. No deben contraerse deudas públicas para conflictos exteriores.
5. Ningún Estado debe inmiscuirse por la fuerza en la constitución y el gobierno de otro.
6. En una guerra no deben permitirse hostilidades que hagan imposible la confianza mutua en una paz futura: emplear asesinos o envenenadores, romper capitulaciones, incitar a la traición, **usar espías** en el Estado enemigo.

Y tres **artículos definitivos**:

1. La constitución de cada Estado debe ser **republicana**. Kant argumenta que si los ciudadanos deciden sobre la guerra, dudarán, porque pagan sus costos. Es el antecedente filosófico de la teoría de la **paz democrática**.
2. El derecho de gentes debe fundarse en una **federación de Estados libres**, no en un Estado mundial que sería un despotismo sin alma.
3. El **derecho cosmopolita** debe limitarse a la **hospitalidad universal**: el derecho de todo extranjero a no ser tratado con hostilidad al llegar a otro territorio, y a ofrecerse al trato con los demás. No es un derecho a instalarse. Kant usa este artículo para condenar el colonialismo de las potencias comerciales europeas, que llaman "visitar" a lo que es conquistar.

Un suplemento sobre la **garantía** de la paz dice que la naturaleza misma, mediante la **insociable sociabilidad** (la tendencia humana a asociarse y a la vez a resistirse a los demás), empuja hacia instituciones justas. Ahí aparece la frase más "teórico-juegos" de Kant: el problema de establecer un Estado tiene solución **incluso para un pueblo de demonios**, siempre que tengan entendimiento. No se trata de mejorar moralmente a las personas, sino de organizar las fuerzas de modo que los intereses egoístas se neutralicen mutuamente y el resultado público sea el mismo que si fueran buenos.

Hay también un **artículo secreto**, una ironía deliberada: que los Estados consulten a los filósofos sobre la guerra y la paz, en secreto, para no herir el orgullo de los gobernantes.

### El principio de publicidad

El segundo apéndice de *Hacia la paz perpetua* contiene la idea más relevante para este informe. Kant propone una **fórmula trascendental del derecho público**, parafraseada así: **son injustas todas las acciones referidas al derecho de otros cuya máxima no soporta la publicidad**.

El razonamiento: si una máxima solo puede tener éxito si se oculta, porque hacerla pública provocaría la resistencia de todos contra el propósito, entonces esa máxima no podría ser aceptada por todos, y por lo tanto viola el derecho. Ejemplos de Kant:

- Un pueblo no puede declarar públicamente que se rebelará si el gobierno abusa, porque eso haría imposible la constitución; por eso, para Kant, la máxima de rebelión es injusta.
- Un Estado no puede declarar de antemano que romperá los tratados cuando le convenga, porque nadie volvería a pactar con él.
- Un Estado poderoso no puede anunciar que someterá a los pequeños, porque estos se unirían en su contra.

Es una **prueba negativa**: lo que no soporta la publicidad es injusto, pero lo que la soporta no es necesariamente justo (un poder abrumador podría anunciar sus planes sin miedo). Kant agrega una formulación afirmativa: las máximas que **necesitan** de la publicidad para cumplir su fin concuerdan a la vez con el derecho y con la política.

Este test reaparece en el siglo XX en la condición de publicidad de Rawls, en el principio de discurso de Habermas y en las discusiones sobre secreto de Estado, inteligencia y vigilancia. En la Parte V se compara con el principio de Kerckhoffs.

### ¿Qué es la Ilustración? Uso público y privado de la razón

Kant define la Ilustración como la **salida del ser humano de su minoría de edad autoculpable**: la incapacidad de servirse del propio entendimiento sin la guía de otro, no por falta de entendimiento sino por falta de decisión y coraje. El lema es ***sapere aude***: atrevete a saber. La pereza y la cobardía mantienen la tutela, y los tutores se encargan de que el paso parezca peligroso.

La distinción entre usos de la razón invierte el sentido común:

- **Uso privado**: el que alguien hace en un cargo o función (el oficial, el recaudador, el pastor). Ahí puede limitarse: el oficial obedece la orden.
- **Uso público**: el que alguien hace como **docto ante el público lector**, como miembro de la sociedad cosmopolita. Este debe ser **libre siempre**: el mismo oficial puede escribir criticando la orden.

La fórmula atribuida a Federico el Grande, "razonad cuanto queráis y sobre lo que queráis, pero obedeced", resume el pacto. Foucault, dos siglos después, toma este texto como punto de partida de su propia idea de crítica (Parte III).

### Filosofía de la historia

En *Idea de una historia universal* (1784), Kant piensa la historia como si la naturaleza tuviera un plan: desarrollar todas las disposiciones racionales de la especie, cosa que solo puede lograrse en la especie y no en el individuo. El medio es el **antagonismo**: la insociable sociabilidad. Sin la ambición, la envidia y el deseo de dominar, los talentos dormirían en una vida pastoril de armonía. Es una teoría del conflicto como motor del progreso institucional, con eco en Hegel, Marx y, de otro modo, en la teoría de juegos evolutiva.

### Críticas

- **Formalismo vacío** (Hegel). El imperativo categórico solo dice que la máxima no se contradiga, pero no da contenido; cualquier máxima bien formulada pasa la prueba. Hegel opone a la *Moralität* abstracta la *Sittlichkeit*: la eticidad concreta de familia, sociedad civil y Estado.
- **Rigorismo**: el asesino en la puerta, la imposibilidad de excepciones.
- **Desprecio de las emociones** y de las relaciones particulares. Bernard Williams criticó que alguien que salva a su esposa en lugar de a un desconocido no debería necesitar una justificación imparcial: tener ese pensamiento ya es "un pensamiento de más".
- **Ética del cuidado.** Carol Gilligan (*In a Different Voice*, 1982) y la tradición del cuidado cuestionaron que la madurez moral sea la abstracción de principios universales, frente a la atención a relaciones y contextos.
- **Raza y colonialismo.** En sus escritos de antropología y geografía física, Kant elaboró una de las primeras teorías de las "razas" humanas con jerarquías explícitas. Emmanuel Chukwudi Eze y Charles Mills sostuvieron que esas tesis comprometen su universalismo, que de hecho sería un universalismo restringido a varones blancos. Pauline Kleingeld argumentó que en la década de 1790, con *Hacia la paz perpetua* y su crítica al colonialismo, Kant revisó esas posiciones. El debate es si el universalismo kantiano puede corregirse con sus propias herramientas o si arrastra un sesgo estructural.
- **Consecuencialismo**: ignorar resultados lleva a la complicidad con desastres evitables.

### Herencia

- **John Rawls** (*Teoría de la justicia*, 1971): la posición original bajo el velo de ignorancia es una interpretación procedimental de la autonomía kantiana. El "constructivismo kantiano" fundamenta principios en un procedimiento de elección razonable.
- **Jürgen Habermas**: la **ética del discurso** reemplaza la prueba monológica de universalización por una prueba dialógica: una norma es válida si todos los afectados podrían aceptarla como participantes de un discurso libre.
- **Christine Korsgaard, Onora O'Neill, Barbara Herman**: lecturas que muestran un Kant más atento al juicio, la vulnerabilidad y la acción en contexto.
- **Derecho internacional y derechos humanos**: dignidad, federación de Estados, derecho cosmopolita, hospitalidad (que Derrida y Seyla Benhabib reactivaron para pensar migraciones y refugio).
- **Constitucionalismo**: la idea de que la legitimidad depende de que una ley pueda ser aceptada por todos es el núcleo normativo de buena parte del constitucionalismo liberal.

## Parte II. Aristóteles frente a Kant: dos gramáticas de la vida moral

Aristóteles pregunta **qué vida es buena** y responde con el carácter; Kant pregunta **qué acción es correcta** y responde con la ley. La mayor parte de la filosofía moral y política de los últimos setenta años puede leerse como un ir y venir entre estas dos gramáticas.

### Contraste sistemático

| Dimensión | Aristóteles | Kant |
| --- | --- | --- |
| Pregunta central | ¿Cómo vivir bien? ¿Qué persona llegar a ser? | ¿Qué debo hacer? ¿Qué máxima puedo querer como ley universal? |
| Concepto básico | Bien (*eudaimonía*), virtud | Deber, ley, autonomía |
| Fundamento | La naturaleza humana y su fin | La razón pura práctica, independiente de la experiencia |
| Estatuto de la felicidad | Es el fin último de la acción | No funda la moral; buscarla como fundamento es heteronomía |
| Emociones | Deben estar educadas; el virtuoso siente lo adecuado y con placer | No dan valor moral; solo el respeto a la ley lo da |
| Rol del contexto | Central: la *phronesis* decide en lo particular | Secundario: el juicio aplica principios, pero el principio no cambia |
| Universalidad | Lo que sucede la mayoría de las veces; no hay reglas sin excepción | Ley válida para todo ser racional; deberes perfectos sin excepción |
| Criterio último | El prudente (*phronimos*), una persona | Una prueba formal (universalización, humanidad como fin) |
| Cómo se aprende | Por hábito, en comunidad, desde la infancia | Por la conciencia de la ley, accesible a cualquier ser racional |
| Ética y política | Continuas: la ética es parte de la política | Separadas: el derecho regula lo externo; la ética, lo interno |
| Sujeto | Animal político, situado, con una función | Ser racional autónomo, potencialmente cualquier persona |
| Desigualdad | Jerarquías naturalizadas (esclavos, mujeres) | Igualdad formal, con exclusiones (ciudadanos pasivos, jerarquías raciales en textos antropológicos) |
| Punto ciego típico | Particularismo conservador: "lo que hace la comunidad virtuosa" | Formalismo y rigorismo: principios ciegos al caso |

La tabla exagera para clarificar. Dos matices impiden la caricatura:

- **Kant también tiene una teoría de la virtud.** La *Doctrina de la virtud* (1797) define la virtud como fortaleza de la voluntad para cumplir el deber frente a las inclinaciones, y desarrolla deberes de perfeccionarse a uno mismo y de procurar la felicidad ajena. Kant también atiende al juicio (la *Crítica del juicio*) y a la educación moral.
- **Aristóteles también reconoce absolutos.** Hay acciones que no admiten término medio y son malas siempre. Y su justicia distributiva supone un principio formal universal (tratar igual a los iguales, desigual a los desiguales, en proporción) aunque el contenido del mérito se dispute.

### Cuatro lugares donde chocan de verdad

1. **Motivación.** Para Aristóteles, quien hace lo justo con dificultad y a disgusto es solo continente, todavía no virtuoso. Para Kant, el que vence a la inclinación muestra con más claridad el valor moral. Uno valora la armonía del carácter; el otro, la firmeza de la voluntad.
2. **Fuente de la norma.** Para Aristóteles, la naturaleza humana y la *polis* dan contenido a lo bueno. Para Kant, cualquier contenido empírico contamina la moral con heteronomía.
3. **Particular y universal.** El prudente aristotélico ve lo que la situación pide; el agente kantiano somete su máxima a una prueba universal. La equidad aristotélica (corregir la ley en el caso) tiene poco lugar en la ética kantiana, aunque sí en su teoría del juicio.
4. **Comunidad e individuo.** Para Aristóteles la *polis* es anterior al individuo. Para Kant, la comunidad legítima se construye desde la libertad de cada uno, como si todos pudieran consentir.

### Max Weber: convicción y responsabilidad

En *La política como vocación* (1919), Weber distingue la **ética de la convicción** (actuar según principios, sin hacerse cargo de las consecuencias: "el cristiano obra bien y deja el resultado en manos de Dios") y la **ética de la responsabilidad** (responder por las consecuencias previsibles de los propios actos). No es exactamente Kant contra Aristóteles, pero el político weberiano maduro, que sabe cuándo decir "no puedo hacer otra cosa", se parece mucho al *phronimos*: alguien que integra principio y juicio de consecuencias en el caso concreto.

### El debate contemporáneo

- **Elizabeth Anscombe**, "Modern Moral Philosophy" (1958): los conceptos de "deber moral" y "obligación" son restos de una ética de la ley divina que ya no tiene legislador; propone volver a una ética de la virtud y a una filosofía de la psicología. Es el punto de partida del renacimiento de la ética de las virtudes.
- **Alasdair MacIntyre**, *Tras la virtud* (1981): el proyecto ilustrado de fundar la moral en la razón universal fracasó, y por eso el debate moral moderno es interminable (emotivismo). Propone recuperar la virtud ligada a **prácticas** (actividades cooperativas con bienes internos, como el ajedrez, la ciencia o la medicina), a la **unidad narrativa de una vida** y a **tradiciones**. Termina diciendo que esperamos no a Godot, sino a un nuevo san Benito: comunidades locales que preserven la vida moral.
- **Liberalismo frente a comunitarismo** (décadas de 1980 y 1990): Rawls, neokantiano, prioriza lo justo sobre lo bueno; el Estado no debe tomar partido entre concepciones de la vida buena. Michael Sandel (el "yo desvinculado" de Rawls no existe), Charles Taylor (la identidad se forma en marcos de valor compartidos) y Michael Walzer (esferas de la justicia: cada bien tiene su criterio de distribución, una idea muy aristotélica) responden desde la comunidad. Rawls, en *Liberalismo político* (1993), retrocede hacia un liberalismo "político", no metafísico.
- **Habermas** reformula la oposición como **moralidad** (lo justo, universalizable por discurso) y **eticidad** (lo bueno para una forma de vida concreta) y sostiene que ambas tienen su lugar, pero que en sociedades plurales la moralidad debe tener primacía para regular conflictos entre formas de vida.
- **Enfoque de las capacidades**: Amartya Sen y Martha Nussbaum (*Las mujeres y el desarrollo humano*, 2000; *Crear capacidades*, 2011) reformulan el florecimiento aristotélico como un conjunto de **capacidades** básicas que toda persona debe poder ejercer (vida, salud, integridad corporal, imaginación, emociones, razón práctica, afiliación, juego, control sobre el entorno, entre otras). Combinan el contenido sustantivo de Aristóteles con el universalismo y el respeto por la elección de Kant. Influyó en el Índice de Desarrollo Humano del PNUD.
- **Convergencias**: Korsgaard, Barbara Herman y otros muestran que Kant deja amplio lugar al juicio situado; Rosalind Hursthouse y otros muestran que una ética de virtudes puede orientar acciones ("hacé lo que haría una persona virtuosa") y admitir principios.

### Por qué importa para las Ciencias Sociales

- **Teorías de la acción.** La acción por hábito (Aristóteles, Bourdieu) y la acción por regla (Kant, en otro plano Durkheim) son dos modelos de lo que hace un actor social. La teoría de juegos agrega un tercero: la acción por cálculo de consecuencias. Las Ciencias Sociales oscilan entre los tres.
- **Normas.** Para una perspectiva aristotélica, las normas se aprenden encarnadas en prácticas; para una kantiana, se justifican por su universalizabilidad. La investigación empírica sobre normas (Bicchieri, Elster) muestra que ambas dimensiones operan.
- **Instituciones.** Aristóteles quiere instituciones que formen buenos ciudadanos; Kant, en su teoría política, quiere instituciones que funcionen aun con un pueblo de demonios. Las políticas públicas debaten hoy exactamente eso: ¿formar virtudes cívicas o diseñar incentivos? (Samuel Bowles, *The Moral Economy*, 2016, muestra que los incentivos materiales a veces **desplazan** las motivaciones morales: el ejemplo clásico es la guardería de Haifa donde una multa por llegar tarde a buscar a los chicos **aumentó** las llegadas tarde, porque convirtió una obligación moral en un precio.)

## Parte III. Foucault: bases avanzadas

El proyecto de Foucault no es una teoría general del poder sino una **historia de los modos en que los seres humanos se vuelven sujetos**: sujetos de conocimiento, sujetos sometidos a otros y sujetos que se constituyen a sí mismos. Él mismo lo dijo así en "El sujeto y el poder" (1982), corrigiendo la imagen de "filósofo del poder". Leerlo a nivel avanzado exige seguir cómo cambian sus herramientas: saber, poder, gobierno y ética.

### Coordenadas biográficas

Michel Foucault nació en Poitiers en 1926 y murió en París en 1984, por complicaciones del sida. Se formó en la École Normale Supérieure, cerca de Jean Hyppolite, Louis Althusser y, sobre todo, Georges Canguilhem, historiador de las ciencias de quien hereda la atención a los conceptos, las normas y las rupturas. Trabajó en Uppsala, Varsovia, Hamburgo y Túnez (1966–1968, donde vivió de cerca la represión estudiantil), dirigió el departamento de filosofía de Vincennes y desde 1970 ocupó en el Collège de France la cátedra "Historia de los sistemas de pensamiento". En 1971 fundó con otros el **Grupo de Información sobre las Prisiones** (GIP), que buscaba que los presos hablaran por sí mismos, sin portavoces. Escribió reportajes sobre la revolución iraní (1978) que le valieron fuertes críticas. En sus últimos años enseñó con frecuencia en Berkeley.

### Mapa de la obra

| Período | Libros | Cursos en el Collège de France | Pregunta central |
| --- | --- | --- | --- |
| Arqueología (1961–1969) | *Historia de la locura* (1961), *El nacimiento de la clínica* (1963), *Las palabras y las cosas* (1966), *La arqueología del saber* (1969) | — | ¿Qué reglas hacen posible que algo se diga como verdadero en una época? |
| Transición | *El orden del discurso* (1970), "Nietzsche, la genealogía, la historia" (1971), *La verdad y las formas jurídicas* (conferencias en Río, 1973) | *Lecciones sobre la voluntad de saber* (1970–71), *Teorías e instituciones penales* (1971–72) | ¿Qué relación hay entre verdad, poder y derecho? |
| Genealogía del poder (1971–1976) | *Vigilar y castigar* (1975), *Historia de la sexualidad I: La voluntad de saber* (1976) | *La sociedad punitiva* (1972–73), *El poder psiquiátrico* (1973–74), *Los anormales* (1974–75), *Hay que defender la sociedad* (1975–76) | ¿Cómo se ejerce el poder sobre cuerpos y poblaciones? |
| Gubernamentalidad (1977–1980) | — | *Seguridad, territorio, población* (1977–78), *Nacimiento de la biopolítica* (1978–79), *Del gobierno de los vivos* (1979–80) | ¿Cómo se gobierna? ¿Qué racionalidades orientan el gobierno? |
| Ética y subjetivación (1980–1984) | *Historia de la sexualidad II: El uso de los placeres* y *III: La inquietud de sí* (1984); *IV: Las confesiones de la carne* (póstumo, 2018) | *Subjetividad y verdad* (1980–81), *La hermenéutica del sujeto* (1981–82), *El gobierno de sí y de los otros* (1982–83), *El coraje de la verdad* (1983–84) | ¿Cómo se constituye uno como sujeto moral? ¿Qué es decir la verdad? |

Los cursos, publicados recién desde 1997, cambiaron la recepción: muestran un Foucault mucho más ocupado del Estado, la economía política y el liberalismo de lo que sugerían los libros. Un cuarto bloque son los ***Dits et écrits***: entrevistas, artículos y conferencias, donde están muchas de sus definiciones más claras.

### 1. Arqueología: las condiciones de posibilidad del saber

La arqueología no hace historia de las ideas (quién influyó en quién, cómo progresó una ciencia) ni interpretación hermenéutica (qué quiso decir un autor). Describe el **nivel de los enunciados efectivamente dichos** y las reglas anónimas que regulan su aparición.

- **Episteme.** En *Las palabras y las cosas*, cada época tiene una configuración que define qué cuenta como conocimiento. En el **Renacimiento**, el saber se organiza por **semejanza**: conocer es descifrar signaturas en el mundo. En la **época clásica** (siglos XVII y XVIII), por **representación** y **tabla**: la gramática general, la historia natural y el análisis de las riquezas clasifican en un cuadro ordenado. En la **modernidad** (desde fines del XVIII), por **historicidad** y profundidad: aparecen la filología, la biología y la economía política, y con ellas el **hombre** como figura doble, objeto empírico y fundamento trascendental del conocimiento a la vez. Las ciencias humanas nacen en ese pliegue inestable. El libro termina con su imagen más citada: el hombre podría borrarse como un rostro dibujado en la arena a la orilla del mar. No anuncia el fin de la humanidad, sino de una configuración del saber.
- **Discontinuidad.** Siguiendo a Gaston Bachelard y Canguilhem, la arqueología busca rupturas, no evolución continua. Una época no "perfecciona" a la anterior: reorganiza el suelo.
- **Herramientas de *La arqueología del saber*.** El **enunciado** es la unidad básica: no una proposición lógica ni un acto de habla, sino una función de existencia de los signos en un campo. Una **formación discursiva** es un sistema de dispersión regular de enunciados, definido por reglas de formación de cuatro cosas: **objetos** (de qué se habla: la locura, la enfermedad), **modalidades enunciativas** (quién habla, desde qué lugar institucional y con qué estatus: el médico en el hospital), **conceptos** y **estrategias** (las opciones teóricas). El **archivo** es el sistema que rige la aparición, conservación y transformación de los enunciados. El **a priori histórico** es la condición de realidad de los enunciados en una época: un a priori, pero no trascendental ni eterno, sino histórico.

Para la investigación social, la arqueología es un método de análisis del discurso que pregunta por **condiciones de posibilidad**: por qué este enunciado y no otro en su lugar.

### 2. *El orden del discurso*: cómo se controla lo que se puede decir

En su lección inaugural en el Collège de France (1970), Foucault sostiene que en toda sociedad la producción del discurso está controlada, seleccionada y redistribuida por procedimientos que conjuran sus poderes y peligros. Los agrupa en tres familias:

1. **Procedimientos de exclusión** (externos): la **prohibición** (no se puede decir cualquier cosa, en cualquier circunstancia, cualquiera), la **separación** razón/locura (la palabra del loco no cuenta, o cuenta como verdad oculta) y la **voluntad de verdad** (la división entre lo verdadero y lo falso, institucionalmente sostenida, que ejerce presión sobre los demás discursos).
2. **Procedimientos internos**: el **comentario** (los textos que se repiten y glosan), el **autor** (principio de agrupación y de unidad del discurso) y las **disciplinas** (sistemas anónimos que fijan qué proposiciones pueden ser verdaderas o falsas dentro de su campo; una proposición puede ser verdadera y no estar "en la verdad" de su época, como Mendel).
3. **Condiciones de utilización**: el **ritual** (cualificación de quienes hablan, gestos y circunstancias), las **sociedades de discurso**, las **doctrinas** (que vinculan a los individuos con ciertos enunciados y les prohíben otros) y la **adecuación social del discurso**, sobre todo la educación.

Es una de las fuentes de los estudios críticos del discurso y una caja de herramientas directa para pensar **censura** y **controles de información**: la censura explícita (prohibición) es solo uno de varios mecanismos, y no el más eficaz.

### 3. Genealogía: historia del presente

En "Nietzsche, la genealogía, la historia" (1971), Foucault toma de Nietzsche un método:

- **Contra el origen** (*Ursprung*): buscar un origen puro supone que hay una esencia detrás de las cosas. La genealogía muestra que detrás de las cosas hay disparidad, accidentes, invenciones.
- **Procedencia** (*Herkunft*): rastrear la multiplicidad de acontecimientos, errores y desvíos que dieron lugar a algo, y su inscripción en el **cuerpo**.
- **Emergencia** (*Entstehung*): el momento en que algo surge en un **juego de fuerzas**, como resultado de luchas y dominaciones.
- **Historia efectiva**: una historia que no se apoya en ninguna constante y que se sabe perspectiva.

Foucault llama a esto **historia del presente**: no se trata de explicar el pasado, sino de mostrar que lo que hoy parece natural, necesario o evidente (la prisión, la sexualidad, la locura como enfermedad mental) tiene una historia contingente, y por eso podría ser de otro modo. Es un trabajo de **desnaturalización**.

### 4. La concepción del poder

Este es el núcleo más citado y más malinterpretado. Foucault critica el **modelo jurídico-discursivo** del poder, que lo piensa como ley, prohibición, soberanía y represión, concentrado en el Estado y poseído por alguien. Su consigna: en la teoría política todavía no se le cortó la cabeza al rey.

En *La voluntad de saber* (1976) propone, en cambio, estas tesis:

1. El poder **no se posee**, se ejerce; no es una cosa, es una **relación**.
2. Las relaciones de poder no son exteriores a otras relaciones (económicas, de conocimiento, sexuales): son inmanentes a ellas.
3. El poder **viene de abajo**: no hay una oposición binaria global entre dominadores y dominados que se difunda hacia abajo, sino múltiples relaciones locales que sostienen efectos de conjunto.
4. Las relaciones de poder son **intencionales y no subjetivas**: tienen objetivos y cálculos, pero no hay un sujeto central que los decida. Hay **estrategias sin estratega**.
5. **Donde hay poder hay resistencia**, y la resistencia nunca está en posición de exterioridad. Los puntos de resistencia están presentes en toda la red.

Y, sobre todo, el poder es **productivo**: no solo reprime, sino que produce saberes, discursos, placeres, cuerpos, identidades. Esa es la crítica a la **hipótesis represiva**: la idea de que desde el siglo XVII la sexualidad fue reprimida y silenciada. Foucault muestra lo contrario: una **incitación** constante a hablar de sexo, en la confesión, la medicina, la pedagogía, la demografía, la psiquiatría. El poder no calló al sexo; lo hizo hablar y lo convirtió en la verdad del sujeto.

En el curso *Hay que defender la sociedad* (clase del 14 de enero de 1976) da **precauciones de método**:

- Estudiar el poder en sus **extremidades**, en sus formas locales y capilares, no en su centro.
- Estudiarlo en sus **efectos** y prácticas reales, no en la intención o la decisión.
- Verlo **circular en red**: los individuos no son solo blancos del poder, también sus relevos.
- Hacer un **análisis ascendente**: de los mecanismos infinitesimales hacia los efectos de conjunto, no deducir todo desde arriba.
- Atender a los **aparatos de saber** que el poder forma y pone en circulación, más que a las ideologías.

En ese mismo curso ensaya la **hipótesis de la guerra**: invertir a Clausewitz y pensar la política como la guerra continuada por otros medios. Rastrea un "discurso histórico-político" de la guerra de razas (luchas entre pueblos, conquistados y conquistadores) que luego se recodifica como lucha de clases y como racismo biológico. Más adelante abandona la guerra como modelo general y la reemplaza por el **gobierno**.

### 5. Saber-poder y regímenes de verdad

Foucault no dice "saber es poder", que es una fórmula de Bacon. Dice que saber y poder **se implican directamente**: no hay relación de poder sin constitución correlativa de un campo de saber, ni saber que no suponga y constituya relaciones de poder. Por eso escribe "saber-poder" con guión.

Cada sociedad tiene su **régimen de verdad**, su "política general de la verdad" (entrevista "Verdad y poder", 1977): qué tipos de discurso acoge como verdaderos, qué mecanismos permiten distinguir lo verdadero de lo falso, qué técnicas se valoran para obtener la verdad, y qué estatus tienen quienes dicen lo que funciona como verdadero. En nuestras sociedades, la verdad está centrada en el discurso científico y en las instituciones que lo producen, y es objeto de una inmensa difusión y consumo y de luchas políticas.

De ahí surge su figura del **intelectual específico**, frente al intelectual universal (el que habla en nombre de la verdad y la justicia de todos): el que interviene desde un saber particular (el físico atómico, el psiquiatra, el informático) en las luchas sobre el régimen de verdad del que forma parte.

**Formas jurídicas de la verdad.** En las conferencias de Río (*La verdad y las formas jurídicas*, 1973), Foucault muestra cómo las prácticas judiciales inventaron formas de establecer la verdad que luego se extendieron a todo el saber:

- **La prueba** (griega arcaica y germánica medieval): una lucha ritual, un desafío o una ordalía, que decide quién tiene razón, no qué pasó.
- **La indagación** (*enquête*): surge con el Estado medieval y la Iglesia; un poder centralizado reconstruye lo ocurrido a partir de testimonios. Se convierte en matriz de las ciencias empíricas y de la investigación histórica y periodística.
- **El examen**: surge en el siglo XIX con las disciplinas; ya no pregunta qué pasó, sino si el individuo se comporta como debe, qué es, qué puede llegar a hacer. Matriz de la psicología, la psiquiatría, la criminología y la sociología del individuo peligroso.

### 6. *Vigilar y castigar* y la sociedad disciplinaria

El libro empieza con dos escenas separadas por ochenta años: el suplicio público de Damiens, regicida frustrado, en 1757, y un reglamento de horarios minuciosos para una casa de jóvenes detenidos en París, de la década de 1830. En ese intervalo cambió el objeto del castigo: del cuerpo supliciado al **alma**, entendida como correlato de un poder que vigila, corrige y normaliza. El alma, dice Foucault, es la prisión del cuerpo.

Tres modelos de castigo:

| Modelo | Época | Lógica | Escena |
| --- | --- | --- | --- |
| Suplicio | Antiguo régimen | El crimen ofende al soberano; el castigo es venganza y manifestación pública de su fuerza | La plaza pública, el cuerpo marcado |
| Reforma humanista | Fines del siglo XVIII | Castigar mejor, no menos: penas como **signos** que disuaden, proporcionadas, legibles para todos | La "ciudad punitiva", con escenas didácticas de castigo |
| Disciplina | Siglo XIX en adelante | Corregir y transformar al individuo mediante encierro, horario, trabajo y vigilancia | La prisión, el cuartel, la escuela, la fábrica |

Lo sorprendente es que la prisión no estaba en el programa de los reformistas: se impuso porque condensaba técnicas disciplinarias que ya se desarrollaban en otros lados.

**Los cuerpos dóciles.** La disciplina produce cuerpos a la vez más útiles y más obedientes. Sus técnicas:

- **Distribución en el espacio**: clausura, cuadriculado (cada individuo en su lugar, cada lugar con su individuo), emplazamientos funcionales, rango (el lugar en una clasificación).
- **Control de la actividad**: el horario, la descomposición temporal del gesto, la correlación entre cuerpo y gesto, la articulación cuerpo-objeto (manejo del fusil, de la pluma), la utilización exhaustiva del tiempo.
- **Organización de las génesis**: series y ejercicios graduados en el tiempo.
- **Composición de fuerzas**: los cuerpos como piezas de una máquina colectiva.

**Los instrumentos del buen encauzamiento**:

1. **Vigilancia jerárquica**: arquitecturas que permiten ver sin ser visto, relevos de vigilantes vigilados.
2. **Sanción normalizadora**: una microjusticia de la puntualidad, la actitud y el cuerpo, que compara, diferencia, jerarquiza, homogeneiza y excluye respecto de una **norma**.
3. **El examen**: combina vigilancia y sanción. Hace visibles a los individuos, los inscribe en una red de **escritura** (expedientes, registros, fichas) y convierte a cada uno en un **caso** documentable.

Una consecuencia que suele pasarse por alto: en el sistema feudal, el que más poder tenía era el más visible e individualizado (el rey, sus ceremonias, su genealogía). En el sistema disciplinario la **individualización es descendente**: los más individualizados y documentados son el niño, el enfermo, el loco, el delincuente. El poder se vuelve anónimo; el sometido, visible.

**El panóptico.** Jeremy Bentham diseñó en 1791 una prisión ideal: un edificio anular dividido en celdas, con una torre central desde la que un inspector puede ver a cada preso sin ser visto. Foucault lo lee como **diagrama** de un mecanismo de poder reducido a su forma ideal:

- Invierte el calabozo: de las tres funciones del encierro (encerrar, privar de luz, ocultar), conserva solo la primera. La **visibilidad es una trampa**.
- El efecto principal es inducir en el detenido un **estado consciente y permanente de visibilidad** que garantiza el funcionamiento automático del poder. Como no sabe si lo miran, debe comportarse siempre como si lo miraran. Se convierte en su propio vigilante.
- **Desindividualiza el poder**: no importa quién esté en la torre, ni siquiera si hay alguien. Cualquiera puede hacer funcionar la máquina.
- Es **económico**: obtiene el máximo efecto con un mínimo de fuerza y de personal.
- Es un **laboratorio**: permite experimentar, comparar, entrenar.
- Es **generalizable**: el panoptismo se extiende a escuelas, hospitales, fábricas y cuarteles. De ahí la idea de una **sociedad disciplinaria**.

**El éxito del fracaso.** Desde el comienzo se supo que la prisión no reduce el delito, produce reincidencia, fabrica delincuentes y empobrece a las familias. ¿Por qué persiste? Foucault responde que su función real no es suprimir los **ilegalismos** sino **gestionarlos diferencialmente**: separar una delincuencia popular, visible, controlable y políticamente inofensiva, de los ilegalismos de los sectores dominantes (fraudes, evasión, negocios ilícitos), que se tratan con otros medios. La delincuencia es útil: provee informantes, justifica la policía, divide a las clases populares. El cierre del libro es el **archipiélago carcelario**: un continuo de instituciones que se extiende desde la prisión hasta el tejido social (la colonia penitenciaria de Mettray, abierta en 1840, es su emblema).

**Norma y ley.** La disciplina funciona por la **norma**, no por la ley. La ley divide lo permitido de lo prohibido; la norma distribuye a los individuos alrededor de un promedio, a lo largo de un continuo de normal a anormal. Foucault sigue aquí a Canguilhem (*Lo normal y lo patológico*, 1943). Una sociedad de normalización no elimina el derecho, pero lo coloniza: el juez pide informes psiquiátricos, el castigo se ajusta a la peligrosidad.

### 7. Biopoder y biopolítica

En el último capítulo de *La voluntad de saber* y en la clase del 17 de marzo de 1976 de *Hay que defender la sociedad*, Foucault formula la transformación más influyente de su obra:

- El **poder soberano** clásico se definía por el derecho de **hacer morir o dejar vivir**: el soberano ejercía su poder sobre la vida al poder quitarla.
- Desde los siglos XVII y XVIII emerge un poder que busca **hacer vivir o dejar morir**: gestionar la vida, administrarla, multiplicarla, regularla.

Este **biopoder** tiene dos polos:

1. Una **anatomopolítica del cuerpo humano**: las disciplinas, centradas en el cuerpo individual como máquina.
2. Una **biopolítica de la población**: los mecanismos reguladores centrados en el cuerpo-especie, en los procesos biológicos de conjunto: natalidad, mortalidad, morbilidad, longevidad, higiene, salud pública, migraciones, endemias. Sus herramientas son la **estadística**, la demografía, la previsión, los seguros, la medicina social.

La **sexualidad** está en la bisagra: es conducta individual (disciplinable) y reproducción de la población (regulable). Por eso el dispositivo de sexualidad se volvió tan importante en el siglo XIX: la histerización del cuerpo de la mujer, la pedagogización del sexo del niño, la socialización de las conductas procreadoras, la psiquiatrización del placer "perverso".

Y el problema más grave: si el poder es poder de hacer vivir, ¿cómo puede matar? La respuesta es el **racismo de Estado**. El racismo introduce un **corte en el continuo biológico** de la especie (razas superiores e inferiores, normales y degenerados) y establece una relación de tipo biológico, no militar, entre mi vida y la muerte del otro: la muerte del otro, de la raza mala, inferior o degenerada, hará la vida en general más sana. "Matar" incluye también exponer a la muerte, multiplicar el riesgo, la muerte política, la expulsión, el rechazo. El nazismo fue la exacerbación de la combinación de biopoder y poder soberano; Foucault también señaló el racismo en los socialismos de Estado.

**Dispositivo de alianza y dispositivo de sexualidad.** La alianza (sistema de matrimonio, parentesco, transmisión de nombres y bienes) se rige por lo permitido y lo prohibido; la sexualidad, por las sensaciones del cuerpo, la calidad de los placeres y la naturaleza de las impresiones. Foucault contrapone también el ***ars erotica*** (un saber del placer transmitido por maestros, en culturas antiguas y orientales) a la ***scientia sexualis*** occidental, organizada alrededor de la **confesión**: hacer decir la verdad del sexo a un otro que escucha, interpreta y juzga.

### 8. El concepto de dispositivo

En la entrevista "El juego de Michel Foucault" (1977) define el **dispositivo** en tres niveles:

1. Un **conjunto heterogéneo** de discursos, instituciones, disposiciones arquitectónicas, decisiones reglamentarias, leyes, medidas administrativas, enunciados científicos, proposiciones filosóficas, morales y filantrópicas. Lo dicho y lo no dicho.
2. La **red** que se establece entre esos elementos, la naturaleza de sus vínculos.
3. Una **función estratégica dominante**: el dispositivo nace para responder a una **urgencia** en un momento histórico (por ejemplo, la reabsorción de una masa de población flotante que resultaba molesta para la economía mercantilista). Después tiene **sobredeterminación funcional** (sus efectos se reacomodan entre sí) y **relleno estratégico** (usa efectos no buscados; por ejemplo, la prisión produce un medio delincuente que luego se aprovecha políticamente).

Gilles Deleuze ("¿Qué es un dispositivo?", 1988) lo describió como una madeja de líneas de visibilidad, de enunciación, de fuerza y de subjetivación. Giorgio Agamben ("¿Qué es un dispositivo?", 2006) amplió el concepto a todo lo que captura, orienta, modela o controla conductas: desde la prisión hasta el celular. Para la investigación social, el dispositivo es una unidad de análisis muy útil porque obliga a mirar juntos discursos, normas, arquitecturas y técnicas.

### 9. Seguridad, territorio, población: los dispositivos de seguridad

En el curso de 1977–1978, Foucault distingue tres tecnologías de poder que coexisten, aunque predominan en distintos momentos:

| Tecnología | Cómo trata un problema | Ejemplo con el robo | Ejemplo con la epidemia |
| --- | --- | --- | --- |
| **Legal (soberanía)** | Prohíbe y castiga | Ley: está prohibido robar, pena tal | Lepra: exclusión de los enfermos |
| **Disciplinaria** | Vigila, corrige, normaliza al individuo | Prisión, vigilancia, corrección del delincuente | Peste: cuadriculado de la ciudad, inspección casa por casa |
| **De seguridad** | Gestiona una distribución dentro de un rango aceptable, calculando costos | ¿Cuál es la tasa media de robo? ¿Cuánto cuesta reducirla? ¿Qué nivel es tolerable? | Viruela: inoculación y vacuna, cálculo estadístico de riesgos por edad y lugar |

Los dispositivos de seguridad tienen rasgos propios:

- Trabajan sobre un **medio** (un espacio de circulación de cosas y personas) más que sobre un territorio cerrado.
- Tratan lo **aleatorio**: no buscan eliminar el fenómeno, sino mantenerlo dentro de límites.
- Operan con un **dejar hacer** calculado: el ejemplo es la escasez de granos, donde los fisiócratas propusieron dejar que el precio suba para que la escasez se corrija sola, aceptando que algunos sufran.
- Funcionan por **normalización** en un sentido distinto al disciplinario. Foucault propone llamar **normación** a la técnica disciplinaria (primero se fija la norma y luego se clasifica a la gente respecto de ella) y **normalización** a la de seguridad (primero se observan las curvas reales de distribución, y la norma surge de ellas).

El nuevo objeto del poder es la **población**: no una suma de súbditos, sino un fenómeno natural con regularidades propias (tasas, epidemias, costumbres) que el gobierno no puede ordenar por decreto, sino conocer y manejar. La población es a la vez sujeto de necesidades y objeto de intervención.

### 10. Gubernamentalidad

En la clase del 1 de febrero de 1978, Foucault da tres sentidos de **gubernamentalidad**:

1. El conjunto de instituciones, procedimientos, análisis, cálculos y tácticas que permiten ejercer una forma de poder que tiene como blanco la **población**, como forma principal de saber la **economía política** y como instrumento técnico los **dispositivos de seguridad**.
2. La tendencia que, en Occidente, condujo a la preeminencia de este tipo de poder, el **gobierno**, sobre la soberanía y la disciplina.
3. El proceso por el cual el Estado de justicia medieval, convertido en Estado administrativo en los siglos XV y XVI, se fue **gubernamentalizando**.

La clave es el sentido amplio de **gobierno**: no solo el gobierno del Estado, sino toda forma de **conducir conductas**: gobernar niños, almas, enfermos, familias, a uno mismo. El poder ya no se analiza como prohibición o como guerra, sino como **conducción de la conducta** (*conduite des conduites*), un juego de palabras en francés entre *conduire* (conducir) y *se conduire* (comportarse).

Genealogía de la gubernamentalidad:

- **El poder pastoral** (de origen hebreo, desarrollado por el cristianismo): el pastor guía a un rebaño en movimiento, no a un territorio; cuida de **todos y de cada uno** (*omnes et singulatim*); conoce el interior de cada oveja mediante la **dirección de conciencia** y la confesión; exige obediencia integral. Foucault identifica también las **contraconductas**: luchas no contra el poder en general sino contra ser conducido de cierta manera (ascetismo, comunidades, mística, retorno a las Escrituras).
- **La razón de Estado** (siglos XVI y XVII): el Estado como fin de sí mismo, que debe conocer y fortalecer sus fuerzas. Sus instrumentos son la **diplomacia** y el aparato militar (para el equilibrio europeo) y la **policía** (*Polizeiwissenschaft*): no la policía actual, sino la administración integral del buen orden, la salud, el abastecimiento, los caminos, las costumbres y la prosperidad. La **estadística** nace literalmente como "saber del Estado".
- **El liberalismo** (siglo XVIII): una crítica de la razón de Estado desde dentro del arte de gobernar. Su pregunta es si no se gobierna demasiado. El **mercado** deja de ser un lugar de justicia (precio justo) y se convierte en un lugar de **veridicción**: el lugar donde se verifica si el gobierno gobierna bien. El liberalismo produce la libertad que necesita y, a la vez, mecanismos de seguridad para administrar sus riesgos.

### 11. *Nacimiento de la biopolítica*: el neoliberalismo como racionalidad de gobierno

El curso de 1978–1979 anunciaba estudiar la biopolítica, pero se dedicó casi entero al **neoliberalismo**, en una lectura muy temprana y sorprendentemente actual:

- **Ordoliberalismo alemán** (escuela de Friburgo: Walter Eucken, Franz Böhm; también Wilhelm Röpke, Alexander Rüstow, Alfred Müller-Armack). Lección: el mercado competitivo **no es natural**; es una estructura frágil que el Estado debe construir y sostener activamente, con una **política de sociedad** (*Gesellschaftspolitik*). El Estado no corrige al mercado: actúa sobre las condiciones del mercado. La legitimidad del Estado alemán de posguerra se funda en la libertad económica.
- **Neoliberalismo norteamericano** (escuela de Chicago: Theodore Schultz, Gary Becker). Extiende el análisis económico a dominios no económicos: familia, educación, criminalidad, matrimonio. La noción clave es el **capital humano**: el trabajador no vende su fuerza de trabajo, sino que es un empresario que invierte en sí mismo para obtener ingresos. El ***homo oeconomicus*** deja de ser socio del intercambio y se vuelve **empresario de sí mismo**.
- **Criminalidad**: siguiendo a Becker ("Crime and Punishment: An Economic Approach", 1968), el delincuente es cualquiera que hace un cálculo de costos y beneficios. La política penal ya no busca corregir almas, sino actuar sobre el **medio** y sobre los costos esperados, aceptando una tasa "óptima" de delito. Foucault llama a esto una gubernamentalidad **ambiental**: no disciplina individuos, modifica las variables del entorno.
- El *homo oeconomicus* es, para Foucault, el sujeto **eminentemente gobernable**: como responde sistemáticamente a modificaciones en su entorno, se lo puede conducir modificando incentivos. Este punto conecta directamente con la teoría de juegos y el diseño de mecanismos (Parte V).

Wendy Brown (*El pueblo sin atributos*, 2015), Pierre Dardot y Christian Laval (*La nueva razón del mundo*, 2009) y la escuela de los *governmentality studies* (Nikolas Rose, Peter Miller, Mitchell Dean) desarrollaron estas pistas.

### 12. Sujeto y poder: el poder como acción sobre acciones

En "El sujeto y el poder" (1982), Foucault sintetiza su concepto:

- Una relación de poder es un modo de acción que no actúa directamente sobre los otros (eso sería violencia), sino **sobre sus acciones**: incita, induce, desvía, facilita o dificulta, amplía o limita, hace más o menos probable.
- Por eso el poder **supone libertad**: solo se ejerce sobre sujetos libres, que tienen ante sí un campo de posibles conductas. Un esclavo encadenado no está en una relación de poder sino de coacción física.
- Hay que distinguir **relaciones de poder** (móviles, reversibles, presentes en toda relación social), **estados de dominación** (relaciones bloqueadas, fijadas, asimétricas, donde el margen de libertad es mínimo) y **tecnologías de gobierno** (que median entre ambos).
- **Estrategia** tiene tres sentidos: elegir medios para un fin; la manera en que alguien juega en un juego según lo que piensa que harán los demás; los procedimientos para privar al adversario de sus medios de combate. Foucault dice explícitamente que las relaciones de poder pueden analizarse como **juegos estratégicos entre libertades**. El vocabulario de la teoría de juegos aparece en el propio Foucault, aunque con otros fines.
- Propone analizar las **luchas** contemporáneas como luchas "transversales" e "inmediatas" contra efectos de poder sobre el cuerpo y la vida (de mujeres contra hombres, de pacientes contra la medicina, de niños contra padres), que cuestionan el estatus del individuo y los privilegios del saber. Su tarea política no sería descubrir lo que somos, sino **rechazar lo que somos**: imaginar formas nuevas de subjetividad frente a la doble presión de la individualización y la totalización del poder moderno.

### 13. Ética, tecnologías del yo y cuidado de sí

En los últimos años Foucault estudia la Antigüedad grecorromana y el cristianismo temprano, no por nostalgia sino para encontrar formas de relación consigo distintas de la moderna. Define la **ética** como la relación que uno establece consigo mismo para constituirse como sujeto moral de sus acciones, y la analiza en cuatro aspectos:

1. **Sustancia ética**: qué parte de uno mismo es objeto de la moral (los deseos, los actos, los sentimientos).
2. **Modo de sujeción**: por qué uno se obliga (ley divina, razón, convención, belleza de la vida).
3. **Trabajo ético** o **ascesis**: qué hace uno sobre sí mismo para transformarse.
4. **Teleología**: qué tipo de ser se aspira a ser.

En *El uso de los placeres* estudia los ***aphrodisia*** griegos (actos, deseos y placeres) y la ***enkrateia***, el dominio de sí, un concepto que viene directamente de Aristóteles (Parte II). La moral griega no era un código universal sino una **estética de la existencia**: hacer de la propia vida una obra bella, con un uso medido de los placeres.

En *La hermenéutica del sujeto* (1981–82) recupera la ***epimeleia heautou***, el **cuidado de sí**, que en la Antigüedad era la condición del "conócete a ti mismo" y no al revés. Sostiene que en la modernidad, desde un "**momento cartesiano**", el acceso a la verdad dejó de exigir una transformación del sujeto: basta con el método. En la Antigüedad, en cambio, el sujeto debía transformarse (por ejercicios, meditación, examen de sí, escritura) para acceder a la verdad.

En el seminario de Vermont "Tecnologías del yo" (1982) distingue cuatro tipos de tecnologías: de **producción** (manipular cosas), de **sistemas de signos**, de **poder** (que determinan la conducta de los individuos) y **del yo** (que permiten a los individuos efectuar operaciones sobre su cuerpo, alma, pensamientos y conducta para transformarse). La gubernamentalidad es el punto de contacto entre las tecnologías de dominación de los otros y las tecnologías del yo.

### 14. Parrhesía: el coraje de decir la verdad

En sus dos últimos cursos, Foucault estudia la ***parrhesía***, que puede traducirse como "decirlo todo" o "hablar franco". Tiene cinco rasgos:

- **Franqueza**: el hablante dice claramente lo que piensa.
- **Verdad**: dice lo que cree verdadero, y hay coincidencia entre creencia y verdad.
- **Peligro**: decirlo implica un **riesgo** para el hablante (perder el favor del poderoso, el exilio, la muerte).
- **Crítica**: se dirige hacia alguien con más poder, o hacia uno mismo, o hacia la mayoría.
- **Deber**: el hablante siente que es su deber decirlo, aunque pudiera callar.

La parrhesía se opone a la **retórica**, que busca persuadir por técnica sin compromiso con la verdad, y a la adulación. Foucault distingue cuatro modalidades de decir verdadero: la **profecía** (habla en nombre de otro), la **sabiduría** (habla del ser, pero puede callar), la **técnica** (enseña un saber, sin riesgo) y la **parrhesía** (habla de la situación presente, con riesgo). Estudia su crisis en la democracia ateniense (si todos pueden hablar, ¿cómo distinguir al que dice la verdad del demagogo?), su desplazamiento hacia la relación entre filósofo y príncipe, y su forma más radical: el **cinismo** de Diógenes, que hace de la propia vida un escándalo de la verdad, una "vida otra" que denuncia el mundo.

Para periodismo, activismo y divulgación de información de interés público, la parrhesía es probablemente la categoría foucaultiana más directamente aplicable.

### 15. Foucault lee a Kant: la crítica como arte de no ser gobernado

Dos textos cierran el círculo con la Parte II:

- **"¿Qué es la crítica?"** (conferencia de 1978): la crítica nace como contrapartida del arte de gobernar. Foucault la define como el arte de **no ser gobernado de tal modo**, en nombre de tales principios, con tales fines, por tales personas. No es rechazo de todo gobierno, sino interrogación de cada forma de ser conducido.
- **"¿Qué es la Ilustración?"** (1984): Foucault relee el texto de Kant de 1784 como el primer gesto de una **ontología crítica del presente**: preguntarse por la propia actualidad. Propone una crítica que ya no busca, como Kant, límites universales y necesarios del conocimiento, sino una **actitud límite**: investigar en lo que se nos da como universal, necesario y obligatorio qué parte es singular, contingente y producto de restricciones arbitrarias. Es una crítica **genealógica en su finalidad y arqueológica en su método**. Y rechaza el "chantaje de la Ilustración": la exigencia de estar a favor o en contra de ella en bloque.

### 16. Críticas y debates

- **Jürgen Habermas** (*El discurso filosófico de la modernidad*, 1985) le reprocha **criptonormatividad**: Foucault denuncia la dominación, pero rechaza los fundamentos normativos (derechos, verdad, razón) que le permitirían decir por qué es mala. También, presentismo y relativismo.
- **Nancy Fraser** (1981) lo resumió en una fórmula célebre: empíricamente revelador, normativamente confuso.
- **Charles Taylor** (1984): si no hay verdad ni libertad más allá del poder, la noción misma de dominación pierde sentido, porque supone algo dominado o distorsionado.
- **Noam Chomsky**, en el debate televisivo de 1971, defendió una naturaleza humana creativa y una idea de justicia como base de la lucha política; Foucault respondió que esas nociones también son productos históricos de nuestra civilización y no pueden fundar la lucha desde afuera.
- **Feminismos**: Judith Butler usó a Foucault para pensar el género como efecto performativo de normas. Sandra Bartky, Susan Bordo y Lois McNay aplicaron la disciplina al cuerpo femenino, y criticaron que Foucault ignorara el género en *Vigilar y castigar*. Nancy Hartsock señaló que, justo cuando los grupos subordinados empezaban a hablar como sujetos, aparecía una teoría que disolvía al sujeto.
- **Poscolonialismo**: Gayatri Spivak ("¿Puede hablar el subalterno?", 1988) criticó a Foucault y Deleuze por presumir que los oprimidos pueden hablar por sí mismos y por ignorar la división internacional del trabajo. Edward Said, que usó el concepto de discurso para *Orientalismo*, señaló el eurocentrismo de su archivo. Ann Laura Stoler (*Race and the Education of Desire*, 1995) mostró que la historia de la sexualidad burguesa europea se formó también en las colonias.
- **Historiadores**: discutieron su periodización (el paso del suplicio a la prisión fue más gradual y desigual) y su uso de fuentes normativas (reglamentos, proyectos) como si describieran prácticas efectivas. David Garland (*Castigo y sociedad moderna*, 1990) le reprochó reducir el castigo al poder, dejando afuera la cultura y la sensibilidad.
- **Jacques Derrida** discutió su lectura de Descartes en *Historia de la locura*; **Jean Baudrillard** publicó *Olvidar a Foucault* (1977), sosteniendo que su teoría del poder era ya un espejo de un poder que se había vuelto simulación.

Una respuesta foucaultiana posible a la crítica normativa: el objetivo no es fundar una teoría de la justicia, sino ampliar la libertad mostrando la contingencia de lo que parece necesario. La crítica no necesita un fundamento último para funcionar como práctica.

### 17. Extensiones contemporáneas: vigilancia, datos y control

- **Gilles Deleuze, "Posdata sobre las sociedades de control"** (1990): las disciplinas (moldes fijos, encierros) dan paso a sociedades de **control** (modulaciones continuas, cifras, contraseñas). El individuo se vuelve **dividual**, un conjunto de datos, muestras y mercados. La empresa reemplaza a la fábrica, la formación permanente a la escuela, la deuda al encierro.
- **Thomas Mathiesen** (1997) propuso el **sinóptico**: los medios masivos permiten que muchos miren a pocos, como complemento del panóptico, en el que pocos miran a muchos.
- **Kevin Haggerty y Richard Ericson, "The Surveillant Assemblage"** (2000): la vigilancia ya no es una torre sino un **ensamblaje** de sistemas heterogéneos que descompone el cuerpo en flujos de información y lo recompone como **doble de datos**, sobre el que se toman decisiones.
- **Didier Bigo**: el **ban-óptico**, la vigilancia como técnica de exclusión y perfilamiento de poblaciones "de riesgo" en fronteras y migraciones, más que de normalización de todos.
- **Antoinette Rouvroy y Thomas Berns** (2013): la **gubernamentalidad algorítmica**, que no se dirige a sujetos ni a normas, sino que anticipa comportamientos a partir de correlaciones en datos masivos, sin pasar por la reflexión ni la conciencia del gobernado.
- **Shoshana Zuboff** (*La era del capitalismo de la vigilancia*, 2019): extracción de datos conductuales como materia prima para predecir y modificar conducta. Aunque no es foucaultiana en sentido estricto, su objeto es lo que Foucault llamaría una tecnología de conducción de conductas.
- **Biopolítica más allá de Foucault**: Giorgio Agamben (*Homo sacer*, 1995: la nuda vida y el estado de excepción), Roberto Esposito (inmunidad y comunidad), Achille Mbembe ("Necropolítica", 2003: poder de decidir quién puede vivir y quién debe morir en contextos coloniales y poscoloniales).
- **En América Latina**: Santiago Castro-Gómez (*Historia de la gubernamentalidad*, 2010) y, en Argentina, Edgardo Castro, autor del *Diccionario Foucault*, una de las herramientas de referencia para leerlo con precisión.

### 18. Foucault como método: preguntas operativas para investigar

Foucault desconfiaba de que lo convirtieran en un sistema y decía que sus libros eran una caja de herramientas. Traducido a un protocolo de investigación social, eso da preguntas como:

1. **Problematización**: ¿desde cuándo y por qué algo empezó a ser un problema que había que pensar y gestionar? ¿Qué urgencia respondía?
2. **Discurso**: ¿quiénes están autorizados a decir la verdad sobre esto? ¿Desde qué instituciones? ¿Qué enunciados son posibles y cuáles impensables?
3. **Técnicas**: ¿con qué instrumentos concretos se actúa (registros, formularios, bases de datos, arquitecturas, horarios, algoritmos, indicadores)?
4. **Racionalidad**: ¿qué fines, cálculos y saberes orientan esas técnicas? ¿Soberanía, disciplina, seguridad, mercado?
5. **Sujetos**: ¿qué tipos de sujeto se producen (el delincuente, el usuario, el emprendedor, el paciente de riesgo)? ¿Qué se les pide que hagan consigo mismos?
6. **Visibilidad**: ¿quién ve a quién? ¿Quién es documentado y quién permanece anónimo?
7. **Resistencias y contraconductas**: ¿quién rechaza ser conducido así, y cómo? ¿Qué parrhesías aparecen y qué les cuesta?
8. **Contingencia**: ¿qué parte de esto se presenta como natural o necesario y es, en realidad, histórico y modificable?

## Parte IV. El principio de Kerckhoffs: la seguridad no puede depender del secreto del sistema

El principio de Kerckhoffs dice que **un sistema criptográfico debe seguir siendo seguro aunque el adversario conozca todo sobre él, salvo la clave**. Lo único secreto debe ser algo pequeño, fácil de cambiar y bajo control de quienes se protegen. Formulado en 1883 para la criptografía militar, hoy es un principio general de ingeniería de seguridad y, leído desde las Ciencias Sociales, una teoría de dónde poner la confianza.

### Contexto histórico

Auguste Kerckhoffs (1835–1903) fue un lingüista neerlandés, nacido en Nuth (Limburgo), que enseñó alemán en París y fue además un gran promotor del volapük, una lengua artificial anterior al esperanto. En enero y febrero de 1883 publicó "La cryptographie militaire" en el *Journal des sciences militaires*.

El contexto importa. Francia acababa de perder la guerra de 1870–1871 contra Prusia. El **telégrafo** había transformado la guerra: las órdenes viajaban por cables que podían interceptarse, y el cifrado ya no era tarea de unos pocos especialistas en una cancillería, sino de oficiales de campo, con apuro, bajo fuego, en grandes volúmenes. En ese escenario, cualquier sistema iba a terminar en manos del enemigo: por captura, por deserción, por un libro de códigos perdido. Kerckhoffs razonó como sociólogo de la organización militar: la pregunta no es si el sistema se va a filtrar, sino qué pasa cuando se filtre.

Su distinción decisiva es entre **sistema** (el método general de cifrado, compartido por todo un ejército) y **clave** (el parámetro particular acordado entre corresponsales).

### Los seis principios

Kerckhoffs propuso seis requisitos para un sistema de cifrado de campaña. En paráfrasis propia:

1. El sistema debe ser **prácticamente indescifrable**, si no matemáticamente.
2. **No debe exigir secreto**, y debe poder caer en manos del enemigo sin inconveniente.
3. La **clave** debe poder comunicarse y retenerse sin notas escritas, y poder **cambiarse o modificarse** a voluntad de los corresponsales.
4. Debe ser aplicable a la **correspondencia telegráfica**.
5. Debe ser **portátil**, y su uso no debe requerir varias personas.
6. Debe ser **fácil de usar**, sin tensión mental ni el conocimiento de una larga serie de reglas.

Solo el segundo pasó a la historia como "el principio de Kerckhoffs". Pero los otros cinco son igualmente modernos: el 3 es la gestión de claves y la rotación de credenciales; el 4, la adecuación al medio de comunicación; el 5 y el 6 son **usabilidad**. Kerckhoffs entendió que un sistema perfecto que los usuarios no pueden usar correctamente será usado mal, y la seguridad real depende de cómo lo usan personas cansadas y apuradas. Un siglo después, Alma Whitten y J. D. Tygar lo confirmaron con "Why Johnny Can't Encrypt" (1999), un estudio sobre lo difícil que resultaba para usuarios comunes usar correctamente PGP.

### Shannon: el enemigo conoce el sistema

Claude Shannon, en "Communication Theory of Secrecy Systems" (1949), reformuló el principio con la frase que se conoce como **máxima de Shannon**: hay que suponer que el enemigo conoce el sistema. En ese mismo trabajo dio la primera teoría matemática del secreto:

- Un sistema tiene **secreto perfecto** si el texto cifrado no da ninguna información sobre el mensaje: la probabilidad de cada mensaje es la misma antes y después de ver el cifrado.
- Para lograrlo, la incertidumbre sobre la clave debe ser al menos tan grande como la del mensaje:

```latex
H(K) \ge H(M)
```

H es la entropía de Shannon (la cantidad de incertidumbre, medida en bits). El único sistema que lo cumple en la práctica es el **cuaderno de un solo uso** (*one-time pad*): una clave aleatoria tan larga como el mensaje, usada una sola vez (Gilbert Vernam y Joseph Mauborgne, 1917–1918). Es seguro sin importar el poder de cómputo del adversario, pero distribuir tantas claves es costosísimo. Toda la criptografía práctica posterior renuncia al secreto perfecto y se conforma con la **seguridad computacional**: romperla es posible en teoría, pero requeriría más cómputo del que existe.

### Por qué el principio funciona

Hay cinco razones, y casi todas son sociales, no matemáticas:

1. **Los sistemas se filtran.** Se capturan máquinas, se roban documentos, se hace ingeniería inversa de chips, los empleados se van, los proveedores se venden. Un secreto compartido por miles de personas o grabado en millones de dispositivos no es un secreto, es una demora.
2. **Cambiar una clave es barato; cambiar un sistema es carísimo.** Si la seguridad depende del diseño y el diseño se filtra, hay que reemplazar todo el equipamiento y reentrenar a todos. Si depende de la clave, se cambia la clave.
3. **El escrutinio público encuentra fallas.** Un algoritmo publicado es atacado por miles de investigadores. Si sobrevive años de ataques, hay evidencia de su solidez. Un algoritmo secreto solo fue revisado por sus autores, que tienen todos los incentivos para creer que es bueno.
4. **Minimizar la superficie del secreto.** Cuanto menos haya que proteger, mejor se lo protege. Una clave de 256 bits se puede guardar en un módulo de hardware; el diseño de un sistema entero, no.
5. **Permite estándares e interoperabilidad.** Solo un sistema público puede ser usado por actores que no se conocen ni confían entre sí. Internet no podría funcionar sin criptografía pública.

### Casos históricos y contemporáneos

**Enigma.** La máquina alemana tenía un diseño que los alemanes creían seguro en parte por desconocido. Los criptólogos polacos, con Marian Rejewski a la cabeza, reconstruyeron su cableado interno hacia 1932, ayudados por documentos que obtuvo la inteligencia francesa de un espía. Después, en Bletchley Park, la ruptura sistemática no dependió de conocer la máquina (eso ya se sabía) sino de **fallas de procedimiento**: mensajes con fórmulas repetidas, claves mal elegidas, reglas de uso que reducían el espacio de búsqueda. Lección kerckhoffsiana: la seguridad dependía del sistema y de la disciplina humana, y ambas fallaron.

Una tabla de casos posteriores:

| Caso | Año | Qué se mantuvo secreto | Qué pasó |
| --- | --- | --- | --- |
| Clipper Chip (EE. UU.) | 1993–1996 | Algoritmo Skipjack clasificado, más un sistema de depósito de claves para el gobierno | Matt Blaze (1994) mostró que el mecanismo de acceso gubernamental podía eludirse; el proyecto fracasó política y técnicamente |
| CSS de los DVD | 1999 | Algoritmo de protección anticopia | Se hizo ingeniería inversa y se publicó DeCSS; el algoritmo resultó débil |
| A5/1 y A5/2 de GSM | Fines de los 90 en adelante | Algoritmos de cifrado de telefonía móvil | Reconstruidos por ingeniería inversa y rotos por investigadores académicos |
| MIFARE Classic (Crypto-1) | 2008 | Cifrado propietario de tarjetas de transporte y acceso | Investigadores (entre ellos Karsten Nohl) reconstruyeron el algoritmo examinando el chip y mostraron ataques prácticos |
| Dual\_EC\_DRBG | 2006–2013 | El algoritmo era público, pero sus constantes no tenían justificación | Las revelaciones de 2013 reforzaron la sospecha de una puerta trasera de la NSA; NIST lo retiró |
| TETRA (TEA1) | 2023 | Algoritmos de radio usados por policías y servicios críticos | Investigadores de Midnight Blue ("TETRA:BURST") mostraron que TEA1 reducía la clave efectiva a 32 bits, rompible en minutos |

El contraejemplo exitoso son los **concursos abiertos**: AES (NIST, 1997–2001, ganó Rijndael, de los belgas Joan Daemen y Vincent Rijmen), SHA-3 (ganó Keccak en 2012) y el proceso de criptografía poscuántica de NIST, que en agosto de 2024 publicó sus primeros estándares (FIPS 203, 204 y 205, con los esquemas ML-KEM, ML-DSA y SLH-DSA). En todos los casos, los candidatos se publicaron completos y se sometieron durante años al ataque de la comunidad internacional.

El caso **Dual\_EC\_DRBG** agrega un matiz importante: **publicar el algoritmo no basta**. Si un diseño contiene parámetros que nadie puede verificar cómo se eligieron, el secreto se esconde en esos parámetros. De ahí la práctica de los números "nada en la manga" (*nothing-up-my-sleeve numbers*): constantes derivadas de cifras conocidas (como los dígitos de pi) para demostrar que no fueron elegidas con intención oculta. Kerckhoffs bien entendido exige **transparencia verificable de todo el diseño**, incluido cómo se tomaron las decisiones.

### Seguridad por oscuridad: matices

Lo opuesto al principio se llama **seguridad por oscuridad** (*security through obscurity*): confiar en que el atacante no conoce el diseño. El consenso profesional no dice que la oscuridad sea inútil, sino que **no puede ser la única ni la principal defensa**.

- **Oscuridad como capa adicional.** Ocultar versiones de software, no publicar la topología de una red, usar puertos no estándar o desplegar señuelos (*honeypots*) puede aumentar el costo del atacante. Es legítimo dentro de una **defensa en profundidad**, siempre que el sistema siga siendo seguro si la capa cae.
- **Secreto de diseño y secreto de configuración.** No es lo mismo ocultar cómo funciona el cifrado (malo) que no publicar qué servidores contienen qué datos (razonable).
- **Los Estados mantienen algoritmos clasificados.** Algunas agencias usan algoritmos no publicados para información muy sensible. No contradice del todo a Kerckhoffs: lo diseñan y evalúan equipos enormes de criptógrafos propios, y el secreto es una capa más. Pero el costo es que nadie de afuera puede verificar su calidad ni la ausencia de puertas traseras.

Dos trabajos analizaron el debate con modelos formales:

- **Ross Anderson** ("Security in Open versus Closed Systems", 2002) mostró que, en un modelo simple de búsqueda de fallas, abrir el código ayuda por igual a atacantes y defensores, y que la ventaja de uno u otro depende de factores concretos: cuántos ojos miran realmente, quién tiene incentivos para buscar, qué tan rápido se corrige.
- **Peter Swire** ("A Model for When Disclosure Helps Security", 2004) propuso que la divulgación ayuda más cuando el ataque es repetido, cuando los atacantes aprenden de cada intento y cuando se comunican entre sí, y que la oscuridad funciona mejor en situaciones de **ataque único** (como un plan militar de sorpresa). Es, en el fondo, un análisis de teoría de juegos.

### Kerckhoffs fuera de la criptografía

- **Software libre y "muchos ojos".** Eric Raymond formuló la "ley de Linus": con suficientes ojos, todos los errores son superficiales. Casos como Heartbleed (2014, en OpenSSL) o la puerta trasera en la biblioteca xz (2024, descubierta por casualidad por un ingeniero que notó una demora) muestran que el código abierto no garantiza que alguien mire: los ojos tienen que existir y tener recursos. El caso xz, además, fue una operación de **ingeniería social** de años sobre un mantenedor voluntario agotado: el eslabón débil fue organizacional.
- **Voto electrónico.** El principio se aplica directamente: un sistema de votación cuya seguridad dependa de que nadie conozca su software es inaceptable para una institución democrática, porque la legitimidad exige verificabilidad pública. En las elecciones porteñas de 2015, con el sistema de boleta única electrónica, investigadores independientes señalaron fallas, incluida la posibilidad de cargar varios votos en una sola boleta (el "multivoto"), y un programador que había reportado una filtración de certificados del sistema sufrió un allanamiento. El episodio muestra el aspecto político del principio: quién tiene derecho a examinar un sistema público y qué le pasa a quien encuentra fallas.
- **Divulgación de vulnerabilidades.** La práctica de la **divulgación coordinada** (avisar al fabricante, dar un plazo, publicar después) es una institución que aplica Kerckhoffs a escala social: asume que las fallas se van a conocer y organiza cómo y cuándo. El plazo funciona como mecanismo de compromiso: si el fabricante no corrige, la información se publica igual.
- **Moderación de contenidos y detección de fraude.** Las plataformas y los bancos mantienen en secreto sus reglas de detección para que no se las eluda (la **ley de Goodhart**: cuando una medida se convierte en objetivo, deja de ser buena medida). Es un caso donde la oscuridad tiene una razón legítima, porque el adversario se adapta. Pero choca con la **rendición de cuentas**: el usuario sancionado no puede saber por qué. Es uno de los conflictos centrales en la regulación de plataformas y sistemas de IA.
- **Puertas traseras y "crypto wars".** En la década de 1990, Estados Unidos restringía la exportación de criptografía fuerte como si fuera armamento; el caso Bernstein contra el Departamento de Justicia llevó a que un tribunal federal de apelaciones reconociera en 1999 que el código fuente podía estar protegido como expresión. En 2016, el FBI exigió a Apple ayuda para desbloquear un iPhone en el caso San Bernardino. El informe colectivo "Keys Under Doormats" (2015) argumentó que no existe una puerta trasera solo para "los buenos": cualquier acceso excepcional es una vulnerabilidad que otros pueden encontrar. Es Kerckhoffs aplicado al Estado: un secreto que comparten muchas agencias y proveedores termina filtrándose.

### Lectura desde las Ciencias Sociales

El principio de Kerckhoffs es, debajo de su apariencia técnica, una **teoría sobre la confianza**:

- **Desplaza la confianza** de las personas e instituciones que guardan secretos hacia **procedimientos públicamente verificables**. Se parece a lo que Weber llamó dominación **legal-racional**: se obedece a reglas impersonales y conocidas, no a personas. Anthony Giddens llamó **sistemas expertos** a estas estructuras en las que confiamos sin entenderlas; Kerckhoffs pide que sean, al menos, examinables por quien quiera.
- **Se parece a las normas de la ciencia** que describió Robert Merton (1942): comunalismo (el conocimiento es común), universalismo (se juzga sin importar quién lo propone), desinterés y **escepticismo organizado** (todo se somete a crítica). La criptografía moderna es seguridad sometida al ethos científico.
- **Redistribuye el secreto.** En el diseño kerckhoffsiano, lo público es el sistema que afecta a todos, y lo secreto es la clave, que está en manos de cada persona que se protege. En el panóptico ocurre exactamente lo contrario: el sistema de vigilancia es opaco (no se sabe si alguien mira) y lo visible es cada persona. Kerckhoffs es, estructuralmente, un principio **antipanóptico**. Esta inversión se desarrolla en la Parte V.
- **Es un principio sobre el poder de examinar.** Un sistema "abierto" solo es seguro si hay gente con capacidad, tiempo, recursos y protección legal para examinarlo. Donde investigar sistemas está criminalizado, el principio se vacía: el código puede ser público, pero nadie se anima a mirarlo.

## Parte V. Cruces: estrategia, deber, poder y secreto

Leídos juntos, los cuatro bloques convergen en una tesis: **la distribución de la visibilidad y del secreto es una cuestión a la vez estratégica, moral, política y técnica**. La teoría de juegos mide qué cambia cuando cambia la información; Kant juzga qué secretos son ilegítimos; Foucault muestra cómo la visibilidad produce sujetos; Kerckhoffs indica dónde conviene poner el secreto para que un sistema resista. Los ocho cruces que siguen desarrollan esa tesis.

### 1. La publicidad kantiana y el principio de Kerckhoffs

La fórmula trascendental del derecho público y el principio de Kerckhoffs tienen la misma estructura: **un diseño que solo funciona si permanece oculto es sospechoso**.

|  | Kant (1795) | Kerckhoffs (1883) |
| --- | --- | --- |
| Objeto | Máximas de acción política referidas al derecho de otros | Sistemas de cifrado |
| Test | ¿Fracasaría la máxima si se hiciera pública? | ¿Fracasaría el sistema si el enemigo lo conociera? |
| Si falla el test | La máxima es **injusta** | El sistema es **frágil** |
| Tipo de juicio | Normativo, sobre legitimidad | Prudencial, sobre robustez (en términos kantianos, un imperativo hipotético) |
| Qué puede seguir siendo secreto | Lo que no afecta el derecho de otros (la vida privada) | La clave, en manos de quien se protege |

La diferencia entre ambos es la diferencia kantiana entre imperativo categórico e hipotético: Kerckhoffs dice "si querés un sistema seguro, no dependas del secreto"; Kant dice "si tu política depende del secreto, es injusta". Pero convergen en una regla práctica muy potente para pensar instituciones:

> **Publicidad del sistema, secreto de la persona.** Las reglas, los algoritmos y los procedimientos que se aplican a muchos deben poder conocerse y examinarse; el secreto legítimo es pequeño, individual y está en manos de quien se protege.

Jeremy Bentham, el inventor del panóptico, es la figura que muestra lo que está en juego. Bentham fue a la vez un gran defensor de la **publicidad del gobierno** (sostenía que los funcionarios se comportan mejor cuanto más estrictamente los vigila el público) y el diseñador de una prisión de **visibilidad total de los presos**. La misma tecnología, la inspección, sirve para controlar al poder o para controlar a los sometidos. La pregunta política no es si hay visibilidad, sino **quién ve a quién**.

El panóptico invierte exactamente la regla kerckhoffsiana-kantiana: **opacidad del sistema, transparencia de la persona**. El inspector no se ve; el preso, sí. Por eso puede decirse que la vigilancia masiva opaca falla los dos tests a la vez: es injusta según Kant, si sus máximas no soportarían ser publicadas, y frágil según Kerckhoffs, si su eficacia depende de que nadie sepa cómo funciona.

En el siglo XX, John Rawls retoma el test como **condición de publicidad** de los principios de justicia (deben poder ser conocidos y reconocidos por todos), y Habermas lo radicaliza en su teoría de la esfera pública y la ética del discurso.

### 2. El panóptico como juego de inspección

La teoría de juegos tiene un modelo preciso para la vigilancia: el **juego de inspección** (desarrollado desde los años sesenta para el control de armas y la verificación de tratados nucleares). Un agente decide si cumplir o violar una norma; un inspector decide si inspeccionar, con un costo c. Si el agente viola y no lo inspeccionan, gana g; si lo inspeccionan, paga una multa f. Si la violación pasa sin detectar, el inspector sufre un daño h (con h > c).

| Agente \\ Inspector | Inspeccionar | No inspeccionar |
| --- | --- | --- |
| Cumplir | 0, −c | 0, 0 |
| Violar | −f, −c | g, −h |

No hay equilibrio en estrategias puras: si el agente siempre cumple, el inspector deja de inspeccionar; entonces conviene violar; entonces conviene inspeccionar. En el equilibrio mixto (por el principio de indiferencia de la Parte I avanzada):

```latex
q^* = \frac{g}{g+f} \qquad\qquad p^* = \frac{c}{h}
```

q\* es la probabilidad de inspeccionar y p\* la de violar. El resultado es contraintuitivo y fue señalado por George Tsebelis (1989): **la tasa de violación no depende de la multa**. Aumentar f no reduce p\*; reduce q\*, la frecuencia con que el inspector inspecciona. Endurecer las penas, en este modelo, ahorra vigilancia pero no reduce el delito. Lo único que baja la violación es abaratar la inspección (c) o aumentar el daño que el inspector sufre si no inspecciona (h).

Ahora miremos el panóptico con este lente:

- **Bentham reduce c casi a cero.** Un solo inspector, en una torre, cubre a todos. Según el modelo, eso baja la violación.
- **El agente no observa q.** No sabe si lo miran. Ante esa incertidumbre, si tiene aversión al riesgo o a la ambigüedad, actúa como si q fuera alto. La torre ni siquiera necesita estar ocupada.
- **Pero el panóptico busca algo que el modelo no captura:** que el agente deje de **querer** violar. La disciplina no solo cambia las probabilidades; cambia la función de utilidad: trabaja para que g tienda a cero, para que el sujeto se vuelva "su propio vigilante".

Ahí está el límite y el punto de contacto entre ambas tradiciones. **La teoría de juegos toma las preferencias como dadas; Foucault estudia cómo se producen.** Un análisis completo de la vigilancia necesita las dos cosas: el cálculo estratégico, para entender cómo responden actores con preferencias dadas, y la genealogía, para entender cómo esas preferencias, esa conciencia de ser visto, esa autocensura, se forman históricamente.

La versión contemporánea es el **efecto inhibidor** (*chilling effect*) de la vigilancia masiva: personas que dejan de buscar, leer o escribir ciertas cosas porque no saben si las miran. En términos de juego, es un agente que sobreestima q; en términos de Foucault, es la interiorización de la mirada; en términos de Kuran, es falsificación de preferencias.

### 3. Censura, conocimiento común y orden del discurso

Tres aportes se combinan para entender los controles de información:

- **Foucault** (*El orden del discurso*): la censura explícita es solo un procedimiento entre muchos; el control más eficaz está en quién puede hablar, desde dónde y con qué legitimidad.
- **Kuran, Chwe y Granovetter** (Parte I avanzada): un régimen no necesita impedir que la gente sepa algo; le alcanza con impedir que **sepan que los demás lo saben**. La censura apunta al **conocimiento común**, porque es el que permite la coordinación. Por eso los regímenes reprimen especialmente las manifestaciones públicas, los símbolos compartidos y los canales de comunicación masiva, más que la opinión privada.
- **Kant**: el uso público de la razón (hablar ante el público como docto) es exactamente lo que produce conocimiento común. Su defensa de la libertad de pluma es, en lenguaje de teoría de juegos, una defensa de la infraestructura de coordinación de una sociedad.

### 4. El pueblo de demonios y el diseño de mecanismos

Kant sostuvo que el problema del Estado tiene solución incluso para un pueblo de demonios, siempre que tengan entendimiento. Antes, David Hume ("Sobre la independencia del Parlamento", 1742) había propuesto que, al diseñar instituciones, hay que suponer que cada persona es un bribón que solo busca su interés. James Madison (*El Federalista* 51, 1788) lo resumió diciendo que si los hombres fueran ángeles no haría falta gobierno, y que hay que oponer la ambición a la ambición.

El **diseño de mecanismos** es la versión matemática de esta tradición: reglas tales que, aunque cada uno busque su interés con información privada, el resultado sea el deseado. La subasta de Vickrey, que hace óptimo decir la verdad, es literalmente una institución para demonios.

Pero las otras tradiciones plantean tres objeciones:

1. **Aristóteles**: las leyes no solo regulan conductas, **forman hábitos**. Una institución diseñada para demonios puede producir demonios. La evidencia de Bowles sobre el efecto de desplazamiento (la guardería de Haifa, Parte II) va en esa dirección: los incentivos materiales pueden erosionar las motivaciones morales que ya existían.
2. **Foucault**: el *homo oeconomicus* no es un dato natural sino un sujeto producido por una racionalidad de gobierno, el neoliberalismo. Diseñar todas las instituciones como si las personas fueran maximizadoras contribuye a que lo sean, y las vuelve **eminentemente gobernables** por medio de incentivos.
3. **Kant mismo**: el pueblo de demonios resuelve el problema del **derecho** (la coexistencia externa de libertades), no el de la **moral**. Una sociedad justa puede funcionar con demonios; una sociedad moral, no. La distinción entre legalidad y moralidad marca el alcance y el límite del diseño institucional.

### 5. Racionalidad estratégica, *phronesis* e imperativos hipotéticos

Las tres tradiciones normativas ubican a la teoría de juegos en un lugar preciso:

- Para **Aristóteles**, la habilidad de encontrar medios eficaces para cualquier fin es ***deinotēs***, astucia. Solo se vuelve *phronesis* si está al servicio de fines buenos, cosa que la astucia sola no puede juzgar.
- Para **Kant**, el cálculo de medios para fines es el terreno de los **imperativos hipotéticos** (de habilidad y de prudencia). La moralidad empieza donde termina ese cálculo.
- Para **Habermas** (*Teoría de la acción comunicativa*, 1981), la **acción estratégica** (influir en otros para lograr fines propios) se distingue de la **acción comunicativa** (coordinarse buscando entendimiento mediante razones). La teoría de juegos modela la primera; la segunda requiere otra racionalidad.
- Para **Foucault**, la racionalidad estratégica no es neutral: es una racionalidad histórica, con una genealogía que pasa por la razón de Estado, la economía política, la Guerra Fría y el neoliberalismo.

Nada de esto invalida la teoría de juegos: delimita qué pregunta responde. Responde muy bien "dadas estas preferencias y estas reglas, ¿qué va a pasar?" No responde "¿son buenas estas preferencias?", "¿son justas estas reglas?" ni "¿cómo llegamos a tener estas preferencias?".

### 6. ¿Qué pasa si los jugadores son kantianos?

Una pregunta tentadora: ¿qué haría un jugador kantiano en el dilema del prisionero? Si se pregunta qué máxima podría querer que todos siguieran, la respuesta es cooperar. La promesa falsa de Kant (Parte II) y la defección en el dilema del prisionero tienen la misma estructura: la máxima del que defecciona es **parasitaria** de que los demás cooperen.

Dos formalizaciones exploran esta idea:

- **Douglas Hofstadter** (1983) propuso la **superracionalidad**: si todos los jugadores son igualmente racionales y lo saben, deben llegar a la misma decisión, y entonces solo hay que comparar (Cooperar, Cooperar) con (Defeccionar, Defeccionar). Gana cooperar.
- **John Roemer** (*How We Cooperate*, 2019) definió el **equilibrio kantiano**: cada jugador elige la acción que querría que todos adoptaran, y nadie desea cambiar si ese cambio se aplicara a todos por igual. En problemas de bienes comunes, el equilibrio kantiano produce resultados eficientes donde el de Nash produce sobreexplotación. Roemer lo propone como modelo de cómo cooperan efectivamente muchas sociedades.

La lección es que el "egoísmo racional" no es la única forma de racionalidad formalizable. Cambiar el criterio de optimización cambia los equilibrios, y cuál criterio usan las personas es una pregunta empírica y cultural, no una verdad de la lógica.

### 7. Foucault y la teoría de juegos: dos ideas de "juego"

Foucault habla de "juegos estratégicos entre libertades" y de "juegos de verdad". La coincidencia de vocabulario es real pero engañosa.

|  | Teoría de juegos | Foucault |
| --- | --- | --- |
| Jugadores | Dados, con preferencias fijas | Producidos por las relaciones de poder |
| Reglas | Fijas y conocidas | En disputa; cambiarlas es parte del juego |
| Racionalidad | Universal (maximizar utilidad esperada) | Histórica y situada |
| Poder | Recursos, información, capacidad de compromiso | Acción sobre acciones; producción de sujetos y verdades |
| Equilibrio | Estado estable donde nadie quiere desviarse | Estado de dominación: relaciones fijadas, bloqueadas |
| Pregunta típica | ¿Qué va a pasar con estas reglas? | ¿Cómo llegamos a jugar este juego, y quién lo inventó? |

El punto de contacto más fértil es el concepto foucaultiano de **estado de dominación**: relaciones de poder que se han fijado y ya no se mueven. En lenguaje de juegos, es un equilibrio del que nadie puede salir unilateralmente aunque sea injusto (como la caza de liebres, o la coordinación con conflicto donde un grupo siempre impone su equilibrio). Las **contraconductas** y la **resistencia** serían, entonces, intentos de cambiar el juego mismo: crear conocimiento común, cambiar los pagos, transformar las preferencias, inventar nuevos jugadores colectivos.

### 8. Decir la verdad sobre un sistema: parrhesía, uso público de la razón y divulgación

Un caso concreto reúne los cuatro bloques: alguien descubre una falla en un sistema que afecta a muchos (un sistema de votación, un algoritmo estatal, una plataforma, un dispositivo médico) y decide hacerla pública.

- **Kerckhoffs**: el sistema no debería depender de que la falla permanezca oculta; si depende, ya era frágil. La divulgación no crea la vulnerabilidad: la revela.
- **Kant**: quien publica su análisis ante el público hace **uso público de la razón**, que debe ser libre. Y si el responsable del sistema solo puede sostenerlo ocultando cómo funciona, su máxima no soporta la publicidad.
- **Foucault**: es un acto de **parrhesía**: franqueza, verdad, crítica hacia quien tiene más poder, sentido de deber y, sobre todo, **riesgo**. Cuando el sistema legal criminaliza al que examina, se ve con claridad que decir la verdad es una relación de poder.
- **Teoría de juegos**: la **divulgación coordinada** con plazo es un **mecanismo de compromiso**. Sin plazo, el fabricante tiene incentivos para no corregir (es un juego donde la amenaza de publicar no es creíble). Con plazo público, la amenaza se vuelve creíble. Los programas de recompensas por fallas (*bug bounties*) son diseño de mecanismos: cambian los pagos para que reportar sea mejor que vender o callar.

### Matriz de síntesis

| Tradición | Pregunta central | Concepto de racionalidad | Visibilidad y secreto | Qué aporta a la investigación social |
| --- | --- | --- | --- | --- |
| Teoría de juegos | ¿Qué resulta de la interacción de actores estratégicos? | Maximización de utilidad dadas las creencias | La información es un recurso estratégico; el secreto puede dar poder o destruir la confianza | Mecanismos, consecuencias no queridas, efectos de cambiar reglas e información |
| Aristóteles | ¿Qué vida es buena y qué instituciones la forman? | *Phronesis*: juicio práctico sobre medios y fines en lo particular | La vida política es pública: la *polis* es un espacio de aparición y deliberación | Hábitos, carácter, juicio situado, desigualdad y estabilidad política |
| Kant | ¿Qué acción es correcta y qué orden político es legítimo? | Razón práctica autónoma; universalizabilidad | Test de publicidad: lo que no soporta ser público es injusto | Criterios de legitimidad, dignidad, derechos, esfera pública |
| Foucault | ¿Cómo se producen los sujetos y cómo se conducen las conductas? | Racionalidades históricas de gobierno | La visibilidad es una técnica de poder; quien es visible es controlable | Genealogía, análisis de dispositivos, crítica de lo que parece natural |
| Kerckhoffs | ¿Dónde conviene poner el secreto para que un sistema resista? | Racionalidad de ingeniería frente a un adversario adaptativo | Sistema público, clave secreta en manos de quien se protege | Teoría de la confianza en procedimientos verificables; evaluación de sistemas de poder |

## Glosario y bibliografía comentada

El glosario reúne los términos que más se repiten en el informe; la bibliografía prioriza ediciones en castellano y obras de entrada. Las referencias están armadas sin consulta en línea: los títulos y años son confiables, pero conviene verificar editorial y edición antes de citarlas formalmente.

### Glosario

| Término | Tradición | Definición breve |
| --- | --- | --- |
| A priori histórico | Foucault | Condiciones de posibilidad de los enunciados en una época; no universales sino históricas |
| *Akrasia* | Aristóteles | Debilidad de la voluntad: saber lo correcto y hacer otra cosa |
| Autonomía | Kant | Darse a uno mismo la ley racional; fundamento de la dignidad |
| Biopolítica | Foucault | Gestión de la vida de la población: natalidad, salud, mortalidad, estadística |
| Clave | Kerckhoffs | Parámetro secreto, pequeño y cambiable, del que debe depender toda la seguridad |
| Conocimiento común | Teoría de juegos | Todos saben algo, todos saben que todos lo saben, y así al infinito |
| Contraconducta | Foucault | Rechazo a ser conducido de cierto modo, por ciertas personas, con ciertos fines |
| *Deinotēs* | Aristóteles | Astucia: habilidad para encontrar medios eficaces para cualquier fin |
| Diseño de mecanismos | Teoría de juegos | Elegir reglas para que, en equilibrio, se obtenga un resultado deseado |
| Dispositivo | Foucault | Red heterogénea de discursos, instituciones, normas y técnicas con una función estratégica |
| Equidad (*epieikeia*) | Aristóteles | Corrección de la ley allí donde falla por su generalidad |
| Equilibrio de Nash | Teoría de juegos | Perfil de estrategias en el que nadie gana desviándose solo |
| Equilibrio perfecto en subjuegos | Teoría de juegos | Equilibrio que excluye amenazas no creíbles; se halla por inducción hacia atrás |
| Estado de dominación | Foucault | Relaciones de poder fijadas y bloqueadas, con margen mínimo de libertad |
| *Eudaimonía* | Aristóteles | Florecimiento o vida lograda: actividad conforme a la virtud en una vida completa |
| Gubernamentalidad | Foucault | Racionalidades y técnicas para conducir conductas, con la población como blanco |
| Heteronomía | Kant | Voluntad determinada por algo externo a la razón (deseos, autoridad, felicidad) |
| *Hexis* | Aristóteles | Disposición estable adquirida; raíz del *habitus* de Bourdieu |
| Imperativo categórico | Kant | Mandato incondicional de la moral: universalizar la máxima, tratar a la humanidad como fin |
| Imperativo hipotético | Kant | Mandato condicionado a un fin deseado (habilidad, prudencia) |
| Máxima | Kant | Principio subjetivo con el que alguien actúa |
| Normación / normalización | Foucault | Fijar una norma y clasificar respecto de ella / derivar la norma de distribuciones observadas |
| Panóptico | Bentham, Foucault | Dispositivo de visibilidad asimétrica que induce autovigilancia |
| Parrhesía | Foucault | Decir la verdad con franqueza, deber y riesgo ante alguien con más poder |
| *Phronesis* | Aristóteles | Sabiduría práctica: juicio sobre cómo actuar bien en lo particular |
| Principio de publicidad | Kant | Son injustas las máximas referidas al derecho de otros que no soportan ser publicadas |
| Problema del polizón | Teoría de juegos | Incentivo a beneficiarse de un bien colectivo sin contribuir |
| Régimen de verdad | Foucault | Mecanismos y autoridades que, en una sociedad, definen lo que funciona como verdadero |
| Secreto perfecto | Shannon | El cifrado no aporta ninguna información sobre el mensaje; exige una clave tan grande como el mensaje |
| Seguridad por oscuridad | Seguridad informática | Depender de que el adversario desconozca el diseño |
| Señal costosa | Teoría de juegos | Acción que revela el tipo porque es más barata para unos que para otros |
| Término medio (*mesotēs*) | Aristóteles | Virtud como punto adecuado entre exceso y defecto, relativo a la persona y al caso |

### Bibliografía comentada

#### Teoría de juegos

- **Robert Gibbons**, *Un primer curso de teoría de juegos* (1992). El manual clásico de nivel intermedio: forma normal, juegos dinámicos, información incompleta y señalización, con aplicaciones económicas.
- **Martin J. Osborne**, *An Introduction to Game Theory* (2004). Más gradual y con muchos ejemplos de ciencia política; buen complemento.
- **Ken Binmore**, *La teoría de juegos: una breve introducción* (2007). Corto y muy claro, por uno de los teóricos más influyentes.
- **Avinash Dixit y Barry Nalebuff**, *El arte de la estrategia* (2008). Divulgación seria, sin matemática pesada.
- **Thomas Schelling**, *La estrategia del conflicto* (1960) y *Micromotives and Macrobehavior* (1978). Lecturas fundamentales para Ciencias Sociales: compromiso, puntos focales, segregación.
- **Robert Axelrod**, *La evolución de la cooperación* (1984). Los torneos y Tit for Tat.
- **Elinor Ostrom**, *El gobierno de los bienes comunes* (1990). Indispensable para salir de la falsa dicotomía Estado-mercado.
- **Mancur Olson**, *La lógica de la acción colectiva* (1965).
- **Jon Elster**, *Tuercas y tornillos* (1989) y *Ulises y las sirenas* (1979). Teoría de juegos leída con ojo crítico de científico social.
- **Timur Kuran**, *Private Truths, Public Lies* (1995) y **Michael Chwe**, *Rational Ritual* (2001). Conocimiento común, censura y revoluciones.
- **Cristina Bicchieri**, *The Grammar of Society* (2006). Normas sociales con herramientas de teoría de juegos.
- **Herbert Gintis**, *Game Theory Evolving* (2.ª ed., 2009). Para quien quiera hacer los ejercicios: evolutiva y experimental.
- **Donald Green e Ian Shapiro**, *Pathologies of Rational Choice Theory* (1994), y **S. M. Amadae**, *Rationalizing Capitalist Democracy* (2003). Críticas metodológica e histórica.
- **James Fearon**, "Rationalist Explanations for War", *International Organization* (1995).

#### Aristóteles

- ***Ética nicomáquea*** y ***Política***, Biblioteca Clásica Gredos. Traducciones de referencia, con introducciones y notas.
- ***Retórica***, Gredos (traducción de Quintín Racionero), con un estudio preliminar extenso.
- **Pierre Aubenque**, *La prudencia en Aristóteles* (1963). El estudio clásico sobre la *phronesis*.
- **Martha Nussbaum**, *La fragilidad del bien* (1986). Suerte, tragedia y ética en los griegos.
- **Bent Flyvbjerg**, *Making Social Science Matter* (2001). La propuesta de Ciencias Sociales phronéticas.

#### Kant

- ***Fundamentación de la metafísica de las costumbres*** y ***Crítica de la razón práctica***, en ediciones de Alianza (traducción de Roberto R. Aramayo) u otras.
- ***La metafísica de las costumbres***, Tecnos (traducción de Adela Cortina y Jesús Conill).
- ***Hacia la paz perpetua*** y ***¿Qué es la Ilustración?***, disponibles en varias ediciones breves (Tecnos, Alianza).
- **Allen Wood**, *Kantian Ethics* (2008), y **Christine Korsgaard**, *Creating the Kingdom of Ends* (1996). Lecturas contemporáneas que corrigen la caricatura rigorista.
- **Arthur Ripstein**, *Force and Freedom* (2009). La mejor reconstrucción moderna de la filosofía del derecho de Kant.
- **Pauline Kleingeld**, *Kant and Cosmopolitanism* (2012). Cosmopolitismo y el debate sobre raza.

#### Aristóteles frente a Kant y debate contemporáneo

- **Alasdair MacIntyre**, *Tras la virtud* (1981).
- **John Rawls**, *Teoría de la justicia* (1971) y *Liberalismo político* (1993).
- **Jürgen Habermas**, *Conciencia moral y acción comunicativa* (1983).
- **Martha Nussbaum**, *Crear capacidades* (2011).
- **Max Weber**, *La política como vocación* (1919).
- **Samuel Bowles**, *The Moral Economy* (2016). Incentivos y desplazamiento de motivaciones morales.

#### Foucault

- **Obras principales**: *Vigilar y castigar* (Siglo XXI), *Historia de la sexualidad* (Siglo XXI), *El orden del discurso* (Tusquets), *La verdad y las formas jurídicas* (Gedisa), *Las palabras y las cosas* y *La arqueología del saber* (Siglo XXI).
- **Cursos del Collège de France** (Fondo de Cultura Económica): para el nivel avanzado, empezar por *Hay que defender la sociedad*, *Seguridad, territorio, población* y *Nacimiento de la biopolítica*; después *La hermenéutica del sujeto* y *El coraje de la verdad*.
- **"El sujeto y el poder"** (1982), en Dreyfus y Rabinow (abajo). El texto más útil para entender su concepto maduro de poder.
- **Edgardo Castro**, *Diccionario Foucault* (Siglo XXI). Herramienta de consulta imprescindible, de un investigador argentino.
- **Hubert Dreyfus y Paul Rabinow**, *Michel Foucault: más allá del estructuralismo y la hermenéutica* (1982). La mejor introducción sistemática.
- **Gilles Deleuze**, *Foucault* (1986), y "Posdata sobre las sociedades de control" (1990).
- **Didier Eribon**, *Michel Foucault* (1989). La biografía de referencia.
- **Mitchell Dean**, *Governmentality* (1999). Manual de los estudios de gubernamentalidad.
- **Santiago Castro-Gómez**, *Historia de la gubernamentalidad* (2010).
- **David Lyon**, *Surveillance Studies: An Overview* (2007), y **Haggerty y Ericson**, "The Surveillant Assemblage" (2000).

#### Kerckhoffs y criptografía

- **Auguste Kerckhoffs**, "La cryptographie militaire", *Journal des sciences militaires* (1883). Texto breve, en dominio público y fácil de encontrar digitalizado.
- **Claude Shannon**, "Communication Theory of Secrecy Systems", *Bell System Technical Journal* (1949).
- **David Kahn**, *The Codebreakers* (1967, edición revisada 1996). La gran historia de la criptografía.
- **Simon Singh**, *Los códigos secretos* (1999). Divulgación accesible, con buenos capítulos sobre Enigma y la criptografía de clave pública.
- **Ross Anderson**, *Security Engineering* (3.ª ed., 2020). El manual de ingeniería de seguridad con mayor atención a factores humanos, económicos e institucionales.
- **Bruce Schneier**, *Secrets and Lies* (2000). Seguridad como proceso social, no solo técnico.
- **Harold Abelson y otros**, "Keys Under Doormats" (2015). El argumento técnico contra las puertas traseras de acceso excepcional.
- **Peter Swire**, "A Model for When Disclosure Helps Security" (2004). El análisis formal de cuándo conviene la apertura.
