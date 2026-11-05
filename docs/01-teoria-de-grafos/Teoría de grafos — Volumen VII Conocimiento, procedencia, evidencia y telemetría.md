# Teoría de grafos — Volumen VII: Conocimiento, procedencia, evidencia y telemetría

Nov 5, 2026 · @Anna Tchijova

## Cómo leer este volumen

Este volumen une las Partes VII y VIII del pedido. El hilo común es una pregunta epistemológica con forma técnica: **cómo representar no solo lo que se sabe, sino de dónde se sabe, con qué confianza y qué se dedujo a partir de qué.** Los grafos de conocimiento representan afirmaciones; los de procedencia, el origen de esas afirmaciones; los de evidencia, sus relaciones de apoyo y contradicción; los causales, hipótesis sobre mecanismos; y la telemetría es el caso límite en el que todo eso ocurre en tiempo real, con relojes imperfectos y datos que faltan.

La sección VII.4 es el centro conceptual del volumen. Las demás pueden leerse en cualquier orden.

**Prerrequisitos.** Volumen I (I.9, sobre estructura, datos y fenómeno), II.13 (grafos temporales), II.15 (incertidumbre), III.3 y III.5 (Union-Find y ordenamiento topológico) y V.3 (producción del grafo).

**Sobre los estándares.** Los estándares citados se verificaron el 5 de noviembre de 2026. Donde un estándar está en revisión (como RDF 1.2), se indica su estado.

## VII.1 Grafos de conocimiento: RDF, OWL, grafos de propiedades y ontologías

**\[Def\] Grafo de conocimiento** (*knowledge graph*). No hay una definición única. Hogan y coautores ("Knowledge Graphs", *ACM Computing Surveys*, 2021; con versión gratuita en línea) proponen: un grafo de datos que acumula y transmite conocimiento del mundo real, cuyos nodos representan entidades y cuyas aristas representan relaciones entre ellas, a menudo acompañado de un esquema, reglas u ontologías que permiten deducir conocimiento implícito. Es la referencia de estudio recomendada para todo este volumen.

Hay dos grandes modelos de datos.

### RDF: el modelo de tripletas

En RDF (*Resource Description Framework*, W3C), todo se expresa como tripletas **sujeto – predicado – objeto**, donde los recursos se identifican con IRI (identificadores globales) y los objetos pueden ser literales (textos, números, fechas). Un conjunto de tripletas es un grafo dirigido y etiquetado. Ejemplo en sintaxis Turtle:

```turtle
@prefix ex: <https://ejemplo.org/> .
ex:EmpresaA  ex:tieneSocio      ex:PersonaB .
ex:PersonaB  ex:ocupaCargoEn    ex:OrganismoC .
ex:EmpresaA  ex:ganoContrato    ex:Contrato42 .
ex:Contrato42 ex:adjudicadoPor  ex:OrganismoC .
```

Las consultas se hacen con **SPARQL**, cuyo núcleo es la coincidencia de patrones de grafo. La consulta "empresas que ganaron contratos de un organismo en el que trabaja uno de sus socios" es un patrón de cuatro aristas, exactamente el de la bandera roja de conflicto de interés de VI.2.

**El problema de hablar sobre afirmaciones.** En RDF 1.1, decir quién afirma una tripleta, desde cuándo vale o con qué confianza requería trucos (reificación clásica, grafos con nombre). **RDF 1.2**, que el 7 de abril de 2026 llegó al estado de Recomendación Candidata del W3C, introduce los **términos tripleta** (*triple terms*): una tripleta puede usarse como objeto de otra, y un **reificador** es un recurso que la representa, sobre el cual se hacen afirmaciones. Lo crucial para este tratado: el término tripleta **denota una proposición sin afirmarla**. Se puede registrar que "el testigo X declaró que B es socio de A" sin que el grafo afirme que B es socio de A. Es exactamente la distinción entre lo que dice una fuente y lo que se tiene por cierto.

### OWL y las ontologías

Una **ontología** especifica las clases de entidades, las relaciones permitidas y sus propiedades lógicas. OWL 2 (*Web Ontology Language*, W3C, 2009; segunda edición, 2012) se basa en lógicas descriptivas, lo que da una semántica formal precisa y razonadores automáticos con garantías (decidibilidad, en sus perfiles). Permite declarar, por ejemplo, que "tieneSocio" es inversa de "esSocioDe", que "controlaA" es transitiva, o que una persona no puede ser a la vez "Víctima" y "Perpetrador" en el mismo hecho, si así se lo define.

**Advertencia.** Una ontología fija categorías. En el sentido de Bowker y Star (V.2), es una decisión política formalizada: qué tipos de relación existen, qué entidades cuentan. Una ontología de un sistema policial que tenga la clase "Asociado de pandilla" ya contiene el problema de VI.7.

### Grafos de propiedades

En los **grafos de propiedades etiquetados** (*labeled property graphs*), nodos y aristas tienen etiquetas de tipo y pares clave–valor. Es el modelo de Neo4j, Memgraph, TigerGraph y otras bases. Las consultas se escriben en Cypher, en Gremlin o, desde 2024, en **GQL**, el primer lenguaje de consulta de bases de datos estandarizado por ISO desde SQL (ISO/IEC 39075:2024).

| Aspecto | RDF y OWL | Grafos de propiedades |
| --- | --- | --- |
| Identificadores | Globales (IRI); pensados para integrar datos de distintas fuentes | Locales a la base |
| Propiedades en aristas | Mediante reificación o términos tripleta (RDF 1.2) | Nativas |
| Semántica formal | Sí: inferencia lógica estandarizada | No hay semántica de inferencia estándar |
| Supuesto por defecto | Mundo abierto | Mundo cerrado en la práctica |
| Validación | SHACL, ShEx | Restricciones propias de cada base |
| Uso típico | Integración de datos, datos abiertos enlazados, bibliotecas, biomedicina | Análisis de redes, detección de fraude, periodismo de datos (VI.3) |

**Cuándo conviene cada uno.** Si el problema central es integrar fuentes heterogéneas, razonar sobre categorías o publicar datos reutilizables, RDF y OWL. Si el problema es recorrer y analizar relaciones con rendimiento y con atributos en las aristas, un grafo de propiedades. Muchos proyectos combinan ambos, y RDF 1.2 acerca los dos modelos.

## VII.2 Mundo abierto, mundo cerrado y validación

Esta es la formalización técnica de la distinción entre ausencia de vínculo y ausencia de evidencia (I.9, V.4).

**\[Def\] Supuesto de mundo cerrado** (*closed world assumption*, CWA). Lo que no consta en la base es falso. Es el supuesto de las bases relacionales y de la mayoría de los grafos de propiedades: si no hay fila, no hay hecho.

**\[Def\] Supuesto de mundo abierto** (*open world assumption*, OWA). Lo que no consta es desconocido. Es el supuesto de RDF y OWL: la ausencia de una tripleta no permite concluir su negación, porque otra fuente podría agregarla.

**Consecuencias para el razonamiento.** En OWL, si una regla dice que todo director de una empresa es una persona, y la base afirma que X dirige una empresa sin decir qué es X, el razonador **infiere** que X es una persona, en lugar de señalar un error de datos. Y una consulta del tipo "personas sin vínculos con el organismo" no tiene respuesta segura bajo mundo abierto: solo se puede responder "personas sin vínculos **registrados**". Lo segundo es exactamente la formulación honesta que exige la crítica de V.5.

**Mundo cerrado local.** En la práctica conviene un supuesto mixto: declarar explícitamente para qué relaciones y qué fuentes la información se considera completa. Por ejemplo: "para los contratos del organismo C entre 2020 y 2024, el registro oficial es exhaustivo" (mundo cerrado local), mientras que para los vínculos personales se mantiene mundo abierto. La completitud deja de ser un supuesto implícito y pasa a ser una afirmación documentada y discutible.

**Validación con SHACL.** Como OWL no sirve para validar (infiere en vez de rechazar), el W3C estandarizó SHACL (*Shapes Constraint Language*, 2017), que comprueba datos RDF contra "formas" bajo un supuesto cerrado: "todo contrato debe tener exactamente un organismo adjudicador y al menos una fuente". ShEx es una alternativa con el mismo propósito. **Recomendación para grafos con valor probatorio:** una forma SHACL que exija, para toda afirmación sobre una persona, al menos una referencia a la fuente y un nivel de confianza. Así la regla de VI.6 ("cada arista remite a sus fuentes") se verifica automáticamente.

**Tres estados por par, formalizados.** En lugar de "hay arista / no hay arista", representar: afirmado (con fuente), negado (con fuente: por ejemplo, un registro que muestra que dos personas no fueron socias en el período), y sin información. Bajo mundo abierto, la tercera categoría es el valor por defecto; la segunda necesita registrarse explícitamente.

## VII.3 Resolución de entidades e integración de fuentes heterogéneas

**El problema.** Decidir qué registros de una o varias fuentes refieren a la misma entidad del mundo. Recibe muchos nombres según la disciplina: *record linkage* (estadística), *entity resolution* (bases de datos), deduplicación, *identity resolution* (inteligencia). Revisiones de referencia: Christen, *Data Matching* (Springer, 2012), y Christophides, Efthymiou, Palpanas, Papadakis y Stefanidis ("An Overview of End-to-End Entity Resolution for Big Data", *ACM Computing Surveys*, 2021).

**Etapas.**

1. **Normalización.** Mayúsculas, tildes, transliteraciones (un nombre ruso puede aparecer como Чайковский, Tchaikovsky, Chaikovsky o Tschaikowski), formatos de fecha, documentos con y sin puntos.
2. **Bloqueo** (*blocking*). Comparar todos los pares es O(n²); se comparan solo los pares que comparten una clave (primeras letras del apellido, año de nacimiento). Un bloqueo mal elegido descarta pares verdaderos sin que nadie se entere: es una fuente de falsos negativos invisible.
3. **Comparación.** Similitudes por campo (distancias de edición como Jaro-Winkler para nombres, coincidencia exacta para documentos).
4. **Clasificación.** Decidir coincidencia, no coincidencia o revisión manual. El modelo de Fellegi y Sunter (1969) pondera cada campo según su poder discriminante y define dos umbrales con una zona intermedia de revisión.
5. **Agrupamiento.** Las decisiones de coincidencia forman un grafo de registros. Tomar las componentes conexas (Union-Find, III.3) aplica transitividad y puede fusionar en cadena registros que no se parecen entre sí. Alternativas más conservadoras: exigir que el grupo sea una clique o casi (correlación de grupos, *correlation clustering*), o cortar las aristas más débiles.

**Los dos errores y su efecto estructural** (ya tratados en II.15 y la Evaluación, G6): la fusión errónea crea hubs y puentes falsos; la separación errónea corta caminos y hace periféricos a actores centrales. **No son simétricos en sus consecuencias**: en una base de sospechosos, una fusión errónea puede incriminar a una persona por los vínculos de otra.

**Integración de fuentes heterogéneas.** Además de las entidades, hay que alinear esquemas (qué significa "vínculo" en cada fuente), unidades, granularidades temporales y niveles de confiabilidad. Principios para hacerlo sin perder trazabilidad:

- **No sobrescribir:** cada valor conserva su fuente; si dos fuentes discrepan, se registran ambos valores y la discrepancia.
- **Identidad como hipótesis:** la afirmación "el registro r1 y el registro r2 son la misma persona" es ella misma una afirmación con fuente (la regla o el analista que la hizo), confianza y fecha. En RDF, `owl:sameAs` es demasiado fuerte para esto, porque obliga al razonador a fusionar todas las propiedades; es preferible una relación propia de "posible identidad" con reificador.
- **Reversibilidad:** debe poder deshacerse una fusión y recalcular todo lo que dependía de ella. Esto exige saber qué dependía de ella, que es la función de la procedencia (VII.4).
- **Evaluación:** medir precisión y exhaustividad con un subconjunto revisado a mano, y reportarlas. En investigación de derechos humanos, HRDAG documenta las reglas de emparejamiento y revisa manualmente muestras de las decisiones.

## VII.4 Grafos de procedencia: W3C PROV y trazabilidad de inferencias

**\[Def\] Procedencia** (*provenance*). Información sobre las entidades, actividades y personas involucradas en la producción de un dato, que puede usarse para evaluar su calidad, confiabilidad o autenticidad. Esta es, en sustancia, la definición del W3C.

**El modelo PROV** (W3C, 2013: PROV-DM es el modelo de datos, PROV-O su ontología en OWL y PROV-N una notación legible) tiene tres tipos de nodo:

- **Entidad** (*Entity*): una cosa con aspectos fijos (un documento, un registro, un dato, un grafo, un informe).
- **Actividad** (*Activity*): algo que ocurre durante un período y actúa sobre entidades (extraer, transformar, emparejar, calcular, revisar).
- **Agente** (*Agent*): quien tiene responsabilidad sobre una actividad o una entidad (una persona, una organización, un programa).

Y relaciones principales:

| Relación | De | A | Significa |
| --- | --- | --- | --- |
| `used` | Actividad | Entidad | La actividad usó la entidad como insumo |
| `wasGeneratedBy` | Entidad | Actividad | La entidad fue producida por la actividad |
| `wasDerivedFrom` | Entidad | Entidad | Una entidad se derivó de otra |
| `wasAssociatedWith` | Actividad | Agente | El agente fue responsable de la actividad |
| `wasAttributedTo` | Entidad | Agente | La entidad se atribuye al agente |
| `actedOnBehalfOf` | Agente | Agente | Delegación de responsabilidad |
| `wasInformedBy` | Actividad | Actividad | Una actividad usó algo que otra generó |

**\[Teo\] Estructura.** Un grafo de procedencia bien formado es acíclico respecto de la generación y la derivación: nada puede derivarse de sí mismo, porque las generaciones están ordenadas en el tiempo. Por lo tanto, **un ciclo en la derivación es un error demostrable**, y se detecta con ordenamiento topológico en tiempo lineal (III.5). PROV-CONSTRAINTS especifica estas reglas de validez, incluidas las restricciones temporales (una entidad no puede usarse antes de ser generada).

**Por qué es el centro de este volumen.** El grafo de procedencia permite responder exactamente las preguntas que la crítica epistemológica de V.5 exige:

| Pregunta | Operación sobre el grafo de procedencia |
| --- | --- |
| ¿De qué fuentes depende esta conclusión? | Alcanzabilidad hacia atrás desde la entidad conclusión |
| ¿Qué conclusiones se ven afectadas si esta fuente resulta falsa? | Alcanzabilidad hacia adelante desde la fuente |
| ¿Esta afirmación es registrada, inferida o hipotética? | Tipo de la actividad que la generó (lectura de fuente, procedimiento automático, juicio de un analista) |
| ¿Quién es responsable de esta inferencia? | `wasAssociatedWith` de la actividad |
| ¿Se puede reproducir el resultado? | Si todas las actividades están descritas con sus parámetros y versiones |

**Ejemplo: trazabilidad de una afirmación.** Afirmación: "la persona P y el funcionario F están vinculados". Su procedencia podría ser: la entidad *vínculo P–F* fue generada por la actividad *emparejamiento de registros versión 3*, asociada al agente *script de resolución v3.2*, que usó las entidades *registro societario R1* y *declaración jurada D7*; además, la actividad usó como parámetro el *umbral 0,85*. Si después se descubre que D7 corresponde a un homónimo, la alcanzabilidad hacia adelante desde D7 muestra todas las conclusiones que hay que revisar.

**Procedencia de la inferencia frente a procedencia del dato.** Hay que registrar no solo de dónde vienen los datos, sino **cómo se llegó a cada conclusión**: qué regla, qué modelo, qué parámetros, qué analista. Es lo que convierte un grafo de conocimiento en un objeto auditable. En la literatura de bases de datos, Buneman, Khanna y Tan ("Why and Where: A Characterization of Data Provenance", ICDT 2001) distinguieron la procedencia del **por qué** (qué datos justifican que un resultado esté en la respuesta) y del **dónde** (de dónde se copió un valor), y Green, Karvounarakis y Tannen ("Provenance Semirings", PODS 2007) dieron un marco algebraico general que permite, por ejemplo, calcular la confianza de una conclusión a partir de la de sus insumos.

**Integridad.** Para que la procedencia sirva como evidencia, el registro mismo debe ser resistente a la manipulación: entradas encadenadas por hashes (cada una incluye el hash de la anterior), sellos de tiempo y firmas de quien realizó cada actividad (VI.6).

## VII.5 Grafos de evidencia: apoyo, contradicción y argumentación

Un grafo de procedencia dice de dónde vienen las afirmaciones. Un grafo de evidencia dice **cómo se relacionan entre sí**: qué apoya qué, qué contradice qué, qué depende de qué supuesto.

### Tradición jurídica: Wigmore

John Henry Wigmore (*The Principles of Judicial Proof*, 1913) propuso diagramas para analizar la masa de pruebas de un juicio: símbolos para testimonios, hechos circunstanciales, explicaciones y su fuerza probatoria, conectados con flechas que indican qué apoya a qué. Anderson, Schum y Twining (*Analysis of Evidence*, Cambridge, 2.ª ed. 2005) recuperaron y modernizaron el método. Schum (*The Evidential Foundations of Probabilistic Reasoning*, Wiley, 1994) analizó las cadenas de inferencia y mostró que la fuerza de una prueba depende de la credibilidad de cada eslabón: un testimonio sobre un hecho requiere evaluar la veracidad, la objetividad y la precisión de la observación del testigo, cada una por separado.

### Argumentación formal: Dung

**\[Def\] Marco de argumentación abstracto** (Dung, "On the Acceptability of Arguments and its Fundamental Role in Nonmonotonic Reasoning, Logic Programming and n-Person Games", *Artificial Intelligence*, 1995). Es un digrafo cuyos vértices son argumentos y cuyos arcos indican ataque: A → B significa que A ataca a B.

- Un conjunto S de argumentos es **libre de conflicto** si ningún argumento de S ataca a otro de S.
- S **defiende** a un argumento a si todo atacante de a es atacado por algún miembro de S.
- S es **admisible** si es libre de conflicto y defiende a todos sus miembros.
- La **extensión fundamentada** (*grounded*) es el mínimo conjunto que contiene todo lo que defiende; es la posición más escéptica, y se calcula en tiempo polinomial iterando desde los argumentos no atacados.
- Las **extensiones preferidas** son los conjuntos admisibles maximales; puede haber varias, que representan posiciones coherentes alternativas.

*Ejemplo.* Argumentos: a = "P estaba en el lugar (testigo 1)"; b = "El testigo 1 no podía ver el lugar desde donde estaba"; c = "Hay una foto que muestra que sí había visibilidad". Ataques: b → a, c → b. La extensión fundamentada es {c, a}: c no es atacado, c derrota a b, y a queda defendido. Si se agrega d = "La foto es de otra fecha", con d → c, la extensión fundamentada pasa a ser {d, b}: a deja de estar justificado.

*Por qué importa.* La argumentación formal modela el razonamiento **no monótono**: agregar información puede retirar conclusiones. Es lo que ocurre en toda investigación real, y lo que un grafo de conocimiento acumulativo (donde las afirmaciones solo se agregan) no captura.

### Apoyo y contradicción en grafos de conocimiento

Para incorporar esto a un grafo de conocimiento:

- Representar **afirmaciones** como nodos (con reificadores de RDF 1.2 o nodos de afirmación en un grafo de propiedades), no solo como aristas entre entidades.
- Agregar aristas entre afirmaciones: **apoya**, **contradice**, **depende de** (un supuesto), **reemplaza** (una corrección posterior).
- Cada afirmación conserva su procedencia (VII.4).
- Las contradicciones no se resuelven borrando una de las partes, sino registrándolas: la existencia de una contradicción entre dos fuentes es un hallazgo.

**Consecuencia metodológica.** Un grafo de evidencia bien construido permite ver qué conclusiones dependen de **una sola** fuente (fragilidad), cuáles se apoyan en fuentes independientes (corroboración) y cuáles en fuentes que en realidad comparten origen (corroboración aparente: dos medios que repiten la misma nota de agencia no son dos fuentes). Esta última comprobación es una pregunta de alcanzabilidad común hacia atrás en el grafo de procedencia.

## VII.6 Incertidumbre y confianza

Hay al menos cuatro formalismos para representar incertidumbre sobre afirmaciones, y no son intercambiables. Elegir uno es elegir qué significa "confianza".

| Formalismo | Qué representa | Combinación | Uso apropiado |
| --- | --- | --- | --- |
| Probabilidad | Grado de creencia coherente o frecuencia | Reglas de probabilidad; requiere modelar la dependencia entre fuentes | Cuando hay modelo de medición y calibración (II.15) |
| Redes bayesianas | Distribución conjunta factorizada por un DAG de dependencias | Inferencia probabilística exacta o aproximada | Evaluar cómo varias pruebas afectan una hipótesis; análisis de evidencia forense (Fenton y Neil, *Risk Assessment and Decision Analysis with Bayesian Networks*, CRC, 2.ª ed. 2018) |
| Escalas ordinales de confiabilidad | Calificación de la fuente y de la información por separado | Sin aritmética; solo comparación | Inteligencia y periodismo: la escala del Almirantazgo (fuente A–F, información 1–6) |
| Teoría de Dempster-Shafer | Creencia y plausibilidad, con lugar explícito para la ignorancia | Regla de Dempster | Cuando importa distinguir "no sé" de "50 %"; su regla de combinación da resultados contraintuitivos con fuentes muy conflictivas (ejemplo de Zadeh) |

**Separar la confiabilidad de la fuente de la credibilidad de la información.** La escala del Almirantazgo, usada en inteligencia y en análisis policial, califica en ejes distintos qué tan confiable ha sido la fuente (A: completamente confiable … F: no se puede juzgar) y qué tan confirmada está la información (1: confirmada por otras fuentes … 6: no se puede juzgar). Una fuente confiable puede transmitir información falsa, y una no confiable, información verdadera. Colapsar ambos ejes en un único número de "confianza" destruye esa distinción.

**Propagación de la confianza en un grafo de inferencias.** Si una conclusión se deriva de varias premisas, su confianza depende de cómo se combinan:

- En una **cadena** (A permite inferir B, B permite inferir C), la confianza se degrada: con probabilidades, si cada paso tiene 0,9, tres pasos dan 0,73. Las cadenas largas de inferencias "razonables" producen conclusiones débiles, aunque cada paso parezca sólido.
- En **fuentes independientes que coinciden**, la confianza se refuerza. Pero solo si son independientes de verdad; si comparten un origen (VII.5), contarlas dos veces es un error grave y frecuente.
- Los **semianillos de procedencia** (Green, Karvounarakis y Tannen, 2007) permiten calcular, sobre la misma estructura de procedencia, distintas nociones de confianza (probabilidad, conteo de derivaciones, nivel mínimo de acceso) cambiando solo las operaciones de combinación.

**Calibración.** Un número de confianza solo significa algo si está calibrado: entre todas las afirmaciones marcadas con 0,8, aproximadamente el 80 % debe ser verdadero. Sin una muestra revisada que permita verificarlo, los números son ordinales disfrazados de probabilidades, y conviene presentarlos como tales.

**Lenguaje verbal estandarizado.** En la comunidad de inteligencia estadounidense, la Directiva de la Comunidad de Inteligencia 203 establece una correspondencia entre expresiones verbales ("muy improbable", "probable", "casi seguro") y rangos de probabilidad, para evitar que la misma palabra signifique cosas distintas para quien escribe y quien lee. Adoptar una escala verbal explícita es una medida simple que mejora la comunicación de resultados de análisis de grafos.

## VII.7 Grafos causales: causalidad, correlación y dependencia

**Tres conceptos distintos.**

- **Correlación:** asociación estadística entre variables, medida sobre datos.
- **Dependencia probabilística:** X e Y no son independientes; puede deberse a causalidad directa, a una causa común o a un condicionamiento sobre un efecto común.
- **Causalidad:** intervenir sobre X cambia la distribución de Y. Se define mediante intervenciones (Pearl), resultados potenciales (Rubin, Neyman) o mecanismos.

Los grafos causales son la herramienta que conecta los tres. Referencias: Pearl, *Causality* (Cambridge, 2.ª ed. 2009); Pearl, Glymour y Jewell, *Causal Inference in Statistics: A Primer* (Wiley, 2016), introductorio; Hernán y Robins, *Causal Inference: What If* (CRC, 2020, con versión gratuita de los autores).

**\[Def\] DAG causal.** Un digrafo acíclico cuyos vértices son variables y cuyos arcos X → Y afirman que X es causa directa de Y respecto del conjunto de variables considerado. El DAG es una **hipótesis**, no un resultado de los datos.

**\[Teo\] d-separación.** En un DAG, tres estructuras básicas determinan cuándo un camino transmite asociación:

| Estructura | Forma | ¿Transmite asociación entre X e Y? | Si se condiciona en Z |
| --- | --- | --- | --- |
| Cadena | X → Z → Y | Sí | Se bloquea |
| Bifurcación (causa común) | X ← Z → Y | Sí (confusión) | Se bloquea |
| Colisionador (efecto común) | X → Z ← Y | **No** | **Se abre** (sesgo de colisionador) |

Si todo camino entre X e Y está bloqueado dado un conjunto Z, X e Y son condicionalmente independientes dado Z en toda distribución compatible con el DAG. Este criterio, puramente gráfico, es un teorema (Pearl, 1988; Geiger, Verma y Pearl, 1990).

**El sesgo de colisionador en investigación con registros.** Si se estudia solo a personas que aparecen en una base policial, y la aparición depende de dos factores independientes (por ejemplo, vivir en un barrio vigilado y cometer delitos), entonces **dentro de la base** esos dos factores aparecen correlacionados negativamente, sin ninguna relación causal. Seleccionar casos por haber sido registrados es condicionar en un colisionador. Es la versión formal de la crítica de V.3 al muestreo desde el investigado.

**\[Teo\] Criterio de la puerta trasera.** Para estimar el efecto de X sobre Y alcanza con ajustar por un conjunto Z que no contenga descendientes de X y que bloquee todos los caminos entre X e Y que entran a X por una flecha. El DAG dice qué controlar y, tan importante como eso, qué **no** controlar.

**Descubrimiento causal.** Algoritmos como PC y FCI (Spirtes, Glymour y Scheines, *Causation, Prediction, and Search*, MIT, 2.ª ed. 2000) infieren clases de DAG compatibles con las independencias condicionales observadas. Sus supuestos son fuertes: suficiencia causal (sin confusores ocultos, en PC; FCI lo relaja), fidelidad (las independencias observadas reflejan la estructura y no cancelaciones casuales) y observaciones independientes. **En datos de redes sociales, este último supuesto falla**: las unidades interactúan (interferencia, IV.4). Por eso el descubrimiento causal "en redes" es un área abierta (Volumen VIII).

**Grafo causal frente a grafo de red social.** Son objetos distintos que se confunden con frecuencia. En el grafo de red, los vértices son actores y las aristas, relaciones. En el DAG causal, los vértices son **variables** (por ejemplo, "conducta de A en el tiempo t") y las aristas, hipótesis de causalidad. Una arista "A llamó a B" en el primero **no** implica la arista "conducta de A → conducta de B" en el segundo. Pasar del uno al otro es exactamente el error 1 de V.5.

**Grafos causales en sistemas computacionales.** En telemetría (VII.9), el grafo de dependencias de eventos registra relaciones de "ocurrió antes" y de "fue producido por". Estas son relaciones causales en un sentido operativo (un proceso creó un archivo), mucho más fuerte que en sistemas sociales, porque el sistema registra la operación misma. Aun así, el registro puede omitir mecanismos (un dato que pasó por memoria compartida no deja arista).

## VII.8 Grafos frente a bases relacionales, documentos y event sourcing

No hay un modelo superior. Cada uno hace fáciles ciertas preguntas y difíciles otras.

| Modelo | Unidad | Fuerte en | Débil en | Supuesto implícito |
| --- | --- | --- | --- | --- |
| Relacional (SQL) | Filas en tablas con esquema fijo | Integridad, transacciones, agregaciones, reportes | Recorridos de profundidad variable ("todos los controladores finales a cualquier distancia") que requieren uniones recursivas | Mundo cerrado; esquema estable |
| Documentos (JSON) | Documentos anidados | Datos heterogéneos, lectura de una entidad completa | Relaciones entre documentos; consistencia de referencias | La entidad es la unidad natural de consulta |
| Grafo de propiedades | Nodos y aristas con atributos | Recorridos, patrones, caminos, análisis de redes | Agregaciones masivas; esquemas rígidos de validación | Las relaciones son el objeto principal |
| RDF y OWL | Tripletas con identificadores globales | Integración de fuentes, semántica formal, razonamiento | Rendimiento en recorridos analíticos; curva de aprendizaje | Mundo abierto |
| Event sourcing | Secuencia inmutable de eventos | Historia completa, auditoría, reconstruir cualquier estado pasado | Consultas sobre el estado actual (requiere proyecciones) | La historia es la fuente de verdad |

**Event sourcing y procedencia.** En event sourcing, el estado del sistema no se guarda: se deriva de una secuencia de eventos inmutables que solo se agregan. Las "proyecciones" (vistas materializadas) se recalculan a partir de los eventos. Para investigación tiene una afinidad profunda con la procedencia: nada se sobrescribe, toda corrección es un evento nuevo, y siempre se puede reconstruir qué se sabía en cada momento ("¿qué decía el grafo el día que se escribió el informe?").

**Arquitectura combinada recomendada para investigación.**

1. **Registro de eventos inmutable** como fuente de verdad: cada documento ingresado, cada afirmación extraída, cada decisión de resolución de entidades y cada corrección es un evento con su procedencia, encadenado con hashes.
2. **Proyección como grafo** (de propiedades o RDF) para recorrer y analizar.
3. **Proyección relacional** para estadísticas y reportes.
4. La proyección se puede regenerar "al día X" para auditar conclusiones pasadas.

**Cuándo conviene usar grafos.**

- Cuando las preguntas son sobre caminos de longitud variable, vecindarios, patrones de relación o estructura.
- Cuando el esquema cambia a menudo o los tipos de relación son muchos y heterogéneos.
- Cuando hay que integrar fuentes con identificadores globales (RDF).

**Cuándo no.**

- Cuando las preguntas son agregaciones sobre muchas filas homogéneas ("monto total contratado por organismo y año"): una base relacional o columnar es más simple y rápida.
- Cuando las relaciones son pocas y fijas: una clave foránea alcanza.
- Cuando se usa el grafo para la **visualización** y no para el análisis: el atractivo visual no justifica el modelo.
- Cuando la integridad transaccional estricta es central y el equipo no conoce bien la base de grafos elegida.

## VII.9 Telemetría: eventos, trazas y grafos de procedencia de sistemas

La telemetría (registros, métricas y trazas de sistemas informáticos) produce los datos relacionales más densos y mejor fechados que existen. Tres tipos de grafo surgen de ella.

### Trazas distribuidas

En sistemas de servicios distribuidos, una solicitud atraviesa muchos servicios. El rastreo distribuido (popularizado por el artículo de Google sobre Dapper, Sigelman y coautores, 2010, y estandarizado hoy en **OpenTelemetry**) registra cada operación como un **span** con identificador, identificador del span padre, inicio y fin. Los spans de una solicitud forman un **árbol** (o, con enlaces entre trazas, un DAG). El grafo de servicios agregado (qué servicio llama a cuál) se deriva de muchas trazas.

*Qué responde:* por dónde pasó una solicitud, dónde se gastó el tiempo (camino crítico en el árbol de spans), qué servicios dependen de cuáles. *Qué no:* lo que ocurrió en componentes sin instrumentar; si el muestreo de trazas (habitual, porque guardar todas es caro) descartó justo la solicitud que interesa.

### Grafos de procedencia de sistema operativo

Registran, a nivel del núcleo del sistema operativo, qué proceso leyó o escribió qué archivo, qué proceso creó a cuál, qué conexiones de red abrió. Es un grafo PROV operativo: procesos como actividades, archivos y conexiones como entidades, usuarios como agentes. Herramientas de investigación: SPADE (SRI) y CamFlow (Pasquier y coautores, *Symposium on Cloud Computing*, 2017).

**Aplicación a seguridad y DFIR.** King y Chen ("Backtracking Intrusions", SOSP 2003) mostraron cómo, a partir de un punto de detección (un archivo modificado), recorrer hacia atrás el grafo de dependencias hasta el punto de entrada del intruso, y luego hacia adelante para encontrar todo lo afectado. Es exactamente la alcanzabilidad hacia atrás y hacia adelante de VII.4. Trabajos posteriores usan estos grafos para detección de intrusiones: StreamSpot (Manzoor, Milajerdi y Akoglu, KDD 2016), HOLMES (Milajerdi y coautores, IEEE S&P 2019) y UNICORN (Han y coautores, NDSS 2020). El programa Transparent Computing de DARPA produjo conjuntos de datos públicos de este tipo con ataques simulados.

**\[Emp\] El problema de la explosión de dependencias.** Un proceso de larga duración (un navegador, un servidor) lee y escribe de todo; si se lo trata como un único nodo, todo queda conectado con todo y el recorrido hacia atrás devuelve casi el sistema entero. Las soluciones dividen procesos en unidades de ejecución más finas o filtran dependencias improbables, y cada filtro es una decisión que puede ocultar justo el camino del atacante. Es el problema de los nodos de servicio (IV.9, VI.5) en versión de sistemas.

### Registros de eventos y minería de procesos

La **minería de procesos** (van der Aalst, *Process Mining: Data Science in Action*, Springer, 2.ª ed. 2016) reconstruye modelos de procesos (redes de Petri, grafos de flujo directo) a partir de registros de eventos con identificador de caso, actividad y tiempo. Sirve para descubrir cómo se ejecuta realmente un trámite frente a cómo dice el reglamento que se ejecuta: otra versión de la distancia entre lo formal y lo informal (IV.6). El estándar OCEL 2.0 (*Object-Centric Event Log*, especificación de 2024) permite que un evento involucre a varios objetos a la vez (una orden, un pago, un proveedor), en lugar de forzar un único "caso": la misma crítica que los hipergrafos hacen a la proyección sobre pares (II.14).

### Tres niveles epistémicos en telemetría

La distinción entre dato registrado, inferencia y reconstrucción hipotética (Evaluación, F4) es aquí especialmente nítida:

| Nivel | Ejemplo | Cómo se marca |
| --- | --- | --- |
| Registrado | El evento de auditoría del núcleo dice que el proceso 4211 abrió el archivo X a las 10:02:13 según el reloj del host | Fuente, host, reloj, identificador del registro |
| Inferido | El proceso 4211 corresponde a la sesión del usuario U (por correlación de identificadores de sesión) | Regla de correlación, confianza |
| Hipotético | El usuario U copió el archivo para exfiltrarlo | Hipótesis explícita, con evidencias a favor y en contra (VII.5) |

## VII.10 Tiempo: sincronización, eventos faltantes, enlaces inciertos y ventanas

### Sincronización temporal

Los relojes de distintas máquinas difieren (desfase, *offset*) y avanzan a ritmos distintos (deriva, *drift*). NTP los sincroniza típicamente con errores de milisegundos en redes locales y mayores en Internet; un reloj puede además saltar hacia atrás al corregirse. Consecuencia: **el orden de los timestamps de máquinas distintas no es el orden de los eventos** cuando la diferencia es menor que la incertidumbre de sincronización.

**\[Def\] La relación "ocurrió antes"** (Lamport, "Time, Clocks, and the Ordering of Events in a Distributed System", *Communications of the ACM*, 1978). a → b si a y b están en el mismo proceso y a es anterior, o si a es el envío de un mensaje y b su recepción, o por transitividad. Es un **orden parcial**: hay pares de eventos concurrentes, ni anteriores ni posteriores. Los **relojes lógicos** de Lamport asignan números compatibles con ese orden; los **relojes vectoriales** (Fidge, 1988; Mattern, 1988) lo caracterizan exactamente: a → b si y solo si el vector de a es menor que el de b. Los **relojes lógicos híbridos** (Kulkarni y coautores, 2014) combinan tiempo físico y lógico.

**Representación honesta del tiempo en un grafo de eventos.**

- Cada evento conserva el timestamp **tal como fue registrado**, con la fuente del reloj.
- La conversión a una escala común es una **inferencia** con incertidumbre: un intervalo, no un punto (Evaluación, F5).
- Las aristas "anterior a" se agregan solo cuando están justificadas: por el mismo reloj, por causalidad registrada (mensaje enviado y recibido) o por intervalos que no se solapan.
- El resultado es un **orden parcial**, y cualquier línea de tiempo total que se presente debe marcarse como una de las compatibles (III.5).

La verificación de consistencia de restricciones temporales ("B ocurrió entre 2 y 5 segundos después de A") se reduce a detectar ciclos negativos en un grafo de restricciones de diferencia, con Bellman-Ford (III.7).

### Eventos faltantes

Los eventos faltan por causas muy distintas, y cada una deja una firma diferente:

| Causa | Firma típica | Cómo detectarla |
| --- | --- | --- |
| Muestreo deliberado | Fracción constante de pérdida | Configuración documentada |
| Rotación o expiración de registros | Corte por antigüedad | Fecha del registro más antiguo disponible |
| Pérdida por saturación | Huecos en picos de carga | Contadores de secuencia, métricas del colector |
| Componente sin instrumentar | Caminos que "saltan" | Spans huérfanos, padres desconocidos |
| Borrado deliberado (antiforense) | Huecos selectivos, contadores discontinuos | Números de secuencia, cadenas de hashes, copias en otro sistema |

**Regla:** distinguir siempre "no hubo evento" de "no hay registro". Los números de secuencia monótonos y las cadenas de hashes en los registros son la herramienta que permite probar la diferencia, porque hacen visible un hueco.

### Enlaces inciertos

Muchas aristas se infieren por correlación: la misma dirección IP en una ventana de tiempo, el mismo identificador de sesión, la proximidad temporal entre un evento en una máquina y otro en otra. Cada una es una arista probabilística (II.15) y debe llevar su regla y su confianza. Las direcciones IP, en particular, no identifican personas: NAT, VPN, redes compartidas y reasignación dinámica las hacen ambiguas.

### Ventanas de observación

Toda telemetría tiene un inicio y un fin de cobertura, y una cobertura parcial (qué sistemas estaban instrumentados). Los efectos de borde de II.13 aparecen aquí: un proceso iniciado antes de la ventana aparece sin padre; una conexión abierta al cierre parece incompleta. Un análisis honesto reporta la **cobertura** (temporal y de sistemas) junto con cada conclusión.

## VII.11 Detección de cambios y reconstrucción de procesos

### Detección de cambios en grafos

La pregunta "¿cambió la estructura?" admite varias formalizaciones:

- **Distancias entre grafos consecutivos:** diferencia de aristas (distancia de Hamming entre matrices de adyacencia), distancias espectrales (II.6), diferencias en distribuciones de grado. Fáciles de calcular; detectan *que* algo cambió pero no *qué*.
- **Cambio de régimen estadístico:** modelar la serie de grafos con un modelo (por ejemplo, de bloques estocásticos) y detectar puntos donde los parámetros cambian. Peel y Clauset ("Detecting Change Points in the Large-Scale Structure of Evolving Networks", AAAI 2015) propusieron un método de este tipo con modelos generativos y pruebas de razón de verosimilitud.
- **Anomalías locales:** vértices o subgrafos cuyo comportamiento se aparta de su propia historia o de sus pares (aparición súbita de un hub, una arista entre comunidades que nunca se tocaban). Akoglu, Tong y Koutra ("Graph Based Anomaly Detection and Description: A Survey", *Data Mining and Knowledge Discovery*, 2015) es la revisión de referencia.

**Advertencias.** Los cambios en el grafo pueden ser cambios en la **medición** y no en el fenómeno: una nueva fuente de datos, un cambio de configuración de registro, un colector caído. Antes de interpretar un cambio estructural, verificar la continuidad de la cobertura (VII.10). Y en monitoreo continuo, el umbral de alerta define una tasa de falsas alarmas que hay que estimar, porque con muchos grafos o muchos nodos, las anomalías "significativas" por azar son inevitables (II.8).

### Reconstrucción de procesos

Reconstruir qué pasó a partir de eventos es la tarea central de la respuesta a incidentes y de la investigación forense digital. Con lo visto en este volumen, puede describirse como un procedimiento con controles explícitos:

1. **Inventario de fuentes y cobertura**: qué sistemas, qué relojes, qué períodos, qué huecos conocidos.
2. **Normalización temporal** con intervalos de incertidumbre, nunca con un único reloj supuesto correcto.
3. **Construcción del grafo de eventos** con dos tipos de arista claramente separados: **causales registradas** (proceso padre e hijo, lectura y escritura, mensaje enviado y recibido) y **temporales inferidas** (anterior a, por intervalos).
4. **Resolución de entidades** (usuarios, hosts, procesos entre reinicios) con reglas documentadas.
5. **Recorridos hacia atrás y hacia adelante** desde los puntos de interés (VII.9), con filtros de explosión de dependencias documentados.
6. **Hipótesis competidoras**: para el mismo conjunto de eventos, formular al menos dos secuencias compatibles y buscar el evento que las discrimine (lógica abductiva: la mejor explicación es la que resiste el intento de refutarla, no la primera que encaja).
7. **Informe con niveles epistémicos**: cada paso de la reconstrucción marcado como registrado, inferido o hipotético, con sus fuentes.

Este procedimiento es una aplicación directa de los principios de V.5 a un dominio técnico: las mismas trampas (orden total impuesto, ausencia leída como inexistencia, proximidad temporal leída como causalidad) aparecen en la reconstrucción de un incidente informático y en la de una cadena de mando.

## VII.12 Arquitectura de referencia y métricas de calidad

La arquitectura que integra lo visto en este volumen pone en el centro un registro de eventos inmutable, y trata todo lo demás como proyecciones recalculables.

&#91;embedded content: arquitectura de referencia · fuentes, registro inmutable y proyecciones\]

Los juicios de analistas entran por el mismo camino que los datos: una fusión de entidades o una hipótesis es un evento con autor, regla y confianza, no una edición directa del grafo. Así, deshacer una fusión errónea es agregar un evento que la revierte y recalcular las proyecciones.

### Métricas de calidad

Un grafo usado para investigar debería publicarse con un tablero mínimo de calidad. Ninguna de estas métricas es exótica; lo raro es reportarlas.

| Dimensión | Métrica | Qué revela |
| --- | --- | --- |
| Procedencia | Fracción de aristas con al menos una fuente citada | Cuánto del grafo es verificable |
| Corroboración | Fracción de aristas con dos o más fuentes **independientes** (sin origen común en el grafo de procedencia) | Fragilidad de las conclusiones |
| Estado epistémico | Proporción de aristas registradas, inferidas e hipotéticas | Cuánto del grafo es interpretación |
| Cobertura temporal | Intervalos con datos por fuente; huecos detectados por números de secuencia | Dónde la ausencia no es informativa |
| Cobertura de pares | Fracción de pares observados frente a no observados (V.3) | Alcance real del supuesto de mundo cerrado |
| Resolución de entidades | Precisión y exhaustividad estimadas sobre una muestra revisada; tamaño de la mayor clase fusionada | Riesgo de hubs y puentes falsos |
| Incertidumbre temporal | Ancho medio de los intervalos de tiempo normalizados | Qué órdenes de eventos son defendibles |
| Consistencia | Ciclos en la derivación; violaciones de restricciones SHACL o PROV-CONSTRAINTS | Errores estructurales demostrables |
| Sensibilidad | Cambio en las conclusiones principales bajo variaciones razonables (V.6) | Robustez del hallazgo |
| Integridad | Verificación de la cadena de hashes del registro | Que nada fue alterado |

**Lectura de conjunto.** Si un grafo tiene alta cobertura de procedencia pero baja corroboración independiente, sus conclusiones son trazables pero frágiles. Si tiene alta proporción de aristas inferidas, el análisis estructural está midiendo sobre todo las reglas de inferencia. Ninguna de estas situaciones invalida el trabajo, pero cada una cambia lo que puede afirmarse con él.

## Matriz de técnicas (parte VII) y ejercicios

### Matriz

| Técnica | Pregunta que responde | Lo que no responde | Condición crítica | Sección |
| --- | --- | --- | --- | --- |
| RDF, OWL, SPARQL | Qué se afirma y qué se deduce lógicamente, integrando fuentes | Si lo afirmado es verdadero | Ontología explícita y discutida | VII.1 |
| Términos tripleta (RDF 1.2) | Qué dijo cada fuente, sin afirmarlo | Cuál fuente tiene razón | Usarlos para todas las afirmaciones atribuidas | VII.1 |
| SHACL | Si los datos cumplen reglas de forma (por ejemplo, toda arista con fuente) | Si son correctos | Formas definidas antes de cargar datos | VII.2 |
| Resolución de entidades | Qué registros son la misma entidad | Con certeza, sin muestra revisada | Reglas documentadas, fusiones reversibles | VII.3 |
| W3C PROV | De dónde viene cada dato y qué depende de qué | Si la fuente es confiable | Registro completo e íntegro de actividades | VII.4 |
| Marcos de argumentación | Qué conclusiones sobreviven a los ataques conocidos | Qué no se pensó | Explicitar ataques y supuestos | VII.5 |
| Redes bayesianas | Cómo varias pruebas afectan una hipótesis | Probabilidades no calibradas | Estructura y probabilidades justificadas | VII.6 |
| DAG causales | Qué controlar y qué no; qué es identificable | El DAG mismo, que es hipótesis | Supuestos de causalidad explícitos | VII.7 |
| Event sourcing | Qué se sabía en cada momento | Nada sobre el mundo; solo sobre el registro | Inmutabilidad real | VII.8 |
| Grafos de procedencia de sistema | Qué proceso tocó qué, hacia atrás y hacia adelante | Intención; lo que no pasó por el núcleo | Cobertura de instrumentación; manejo de la explosión de dependencias | VII.9 |
| Relojes lógicos y vectoriales | Orden causal entre eventos de procesos distintos | Tiempo físico exacto | Registrar mensajes enviados y recibidos | VII.10 |
| Detección de cambios | Que la estructura cambió | Si cambió el fenómeno o la medición | Continuidad de cobertura | VII.11 |

### Ejercicios

1. (★) Escribí en Turtle cinco tripletas sobre una red societaria inventada y una consulta SPARQL que encuentre conflictos de interés como el patrón de VII.1. Usá Apache Jena (Fuseki) u Oxigraph.
2. (★★) Representá con RDF 1.2 (términos tripleta y reificadores) dos testimonios contradictorios sobre un mismo vínculo, cada uno con su fuente y fecha, sin que el grafo afirme ninguno de los dos.
3. (★★) Escribí una forma SHACL que exija que toda afirmación de vínculo entre personas tenga al menos una fuente y un nivel de confianza, y validala con pySHACL contra datos que la cumplan y datos que no.
4. (★★) Modelá en PROV (con la biblioteca `prov` de Python) el proceso de VII.4: dos registros, una actividad de emparejamiento, una conclusión. Escribí una función que, dada una fuente, devuelva todas las conclusiones que dependen de ella.
5. (★★) Implementá el cálculo de la extensión fundamentada de un marco de argumentación de Dung y verificá el ejemplo de VII.5, con y sin el argumento d.
6. (★★) Dibujá el DAG del ejemplo del sesgo de colisionador (barrio vigilado, comisión de delitos, aparición en la base) y simulá datos que muestren la correlación espuria dentro de la base.
7. (★★) Implementá relojes vectoriales para tres procesos que intercambian mensajes y determiná qué pares de eventos son concurrentes.
8. (★★★) Tomá registros de auditoría de una máquina Linux propia (auditd o sysmon para Linux), construí el grafo proceso–archivo de una sesión corta y hacé un recorrido hacia atrás desde un archivo modificado. Medí cuántos nodos alcanzás con y sin filtrar los procesos de larga duración.
9. (★★★) Diseñá el tablero de calidad de VII.12 para un grafo propio y calculá al menos cinco de sus métricas.

### Fuentes verificadas de este volumen

- [W3C, RDF 1.2 Concepts and Abstract Data Model (Recomendación Candidata, 7 de abril de 2026)](https://www.w3.org/TR/rdf12-concepts/)
- [ISO/IEC 39075:2024, GQL](https://webstore.iec.ch/publication/94107)
- [OCEL 2.0, especificación (arXiv)](https://arxiv.org/abs/2403.01975)

Los estándares W3C de OWL 2, SPARQL 1.1, SHACL y PROV, y las obras académicas citadas, se consolidan con sus enlaces en el Volumen IX.
