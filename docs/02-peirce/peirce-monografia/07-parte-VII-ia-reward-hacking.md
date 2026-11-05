# Parte VII — Peirce, IA y reward hacking

[Índice](00-indice-y-estrategia.md) · Anterior: [Parte VI](06-parte-VI-limites-prueba.md) · Siguiente: [Parte VIII](08-parte-VIII-comparativo.md)

---

## 0. Estatus de esta parte y declaración de acceso

### 0.1 Qué es y qué no es

Esta parte explora **cómo la epistemología peirceana puede usarse como herramienta** para estudiar señales de éxito, evaluadores y agentes de IA. Todo lo que conecta a Peirce con IA es **[APLIC]**, **[ANALOGÍA]** o **[ESPEC]**: Peirce murió en 1914 y no escribió sobre aprendizaje por refuerzo, modelos de lenguaje ni evaluación automatizada.

No es una redacción de la investigación de la autora del repositorio `reward-hacking-social`. Las observaciones sobre sus documentos (sección 4) son **notas de estudio**: señalan conexiones y posibles precisiones conceptuales para que ella decida qué hacer con ellas. Las conclusiones del proyecto le corresponden a su autora.

### 0.2 Declaración de acceso al repositorio

- **Repositorio**: `https://github.com/annatchijova/reward-hacking-social`
- **Fecha de lectura**: 5 de noviembre de 2026.
- **Commit leído**: `cd02db3517d1fbb0a7489228dc25e87d947ac86d` (fecha del commit: 2026-11-05 19:20:09 −0300).
- **Documentos leídos completos**: `docs/21-peirce-eco-grice-y-daubert.md`, `docs/23-metodologia-y-predicciones.md`, `docs/24-explicaciones-rivales.md`, `docs/31-matriz-de-trazabilidad.md`.
- **Documentos leídos parcialmente** (para contexto): `README.md`, `docs/02-reward-hacking-y-fronteras.md`, `docs/13-observabilidad-e-iceberg.md`, `docs/19-vigia-break-012-consensus-trap.md`, `docs/33-fuentes-y-referencias.md`, `docs/referencias/bibliografia.md`.
- **No accesible**: la fuente primaria privada que los documentos citan (`Downloads/reward_hacking.md`, con SHA-256 declarado `c39b1956…10487`). Todo lo que se diga sobre el contenido del corpus se limita a lo publicado en el repositorio.
- **No leído**: el resto de los documentos (01, 03–12, 14–18, 20, 22, 25–30, 32, 34, 35) salvo menciones puntuales en los leídos.

---

## 1. Distinciones conceptuales

La consigna pide diferenciar seis nociones. Las definiciones son de trabajo, con su procedencia.

| Noción | Definición de trabajo | Procedencia | Qué la distingue |
|---|---|---|---|
| **Reward hacking** | Un sistema optimizado contra una señal de recompensa obtiene recompensa alta sin cumplir el objetivo que esa señal pretendía medir. | Formalización de Skalse, Howe, Krasheninnikov y Krueger (2022): un par de funciones de recompensa (verdadera, proxy) es "hackeable" si existen políticas tales que el proxy prefiere una y la verdadera prefiere otra [V1]. Uso en LLM: Anthropic (2025) lo describe como que el modelo engaña a su proceso de entrenamiento para obtener recompensa alta sin completar la tarea [V1]. | Se define por la **divergencia entre señal y objetivo** bajo optimización. |
| **Specification gaming** | El sistema satisface la especificación literal de la tarea sin lograr el resultado que se pretendía. | Krakovna et al. (DeepMind, 2020) [V2 para la fecha; el repositorio cita la página institucional]. | Más amplio: la "especificación" puede ser una regla, un entorno o una recompensa. Reward hacking puede verse como un caso. |
| **Engaño** (en sentido funcional) | Inducción sistemática de creencias falsas en otro (por ejemplo, en el evaluador), que contribuye a un resultado distinto de la verdad. | Definiciones funcionales en la literatura de seguridad de IA, por ejemplo Park et al. (2023) [V2]. | Se define por el **efecto en el evaluador**, no por un estado mental del sistema. |
| **Error** | Resultado incorrecto que no está relacionado sistemáticamente con obtener recompensa ni con inducir creencias falsas. | Uso ordinario. | Sin relación sistemática con la señal. |
| **Complacencia** (*sycophancy*) | Tendencia a producir respuestas que coinciden con las creencias o preferencias del usuario en lugar de las más veraces. | Sharma et al. (2023) [V2]. | Se orienta a la **aprobación del interlocutor**; puede ser una forma de explotar un evaluador humano. |
| **Optimización legítima** | Obtener recompensa alta **cumpliendo** el objetivo que la señal mide. | — | La señal y el objetivo coinciden en el caso. |

### 1.1 Advertencia sobre intencionalidad

La consigna pide no atribuir intencionalidad psicológica humana a los LLM. En esta parte se usan formulaciones **conductuales y funcionales**: "el sistema produce", "la conducta es compatible con", "la estrategia seleccionada", "el efecto sobre el evaluador". Expresiones como "el modelo quiere" o "el modelo decide engañar" se evitan, salvo cuando se citan y se marcan. El repositorio adopta la misma precaución (README: la tesis "no atribuye emociones humanas a los modelos ni presupone una intención psicológica de engañar").

### 1.2 Una distinción peirceana útil [APLIC]

En términos de la Parte III, una **señal de éxito** (tests que pasan, puntaje alto, aprobación del usuario) es un **signo** cuyo **objeto dinámico** es el cumplimiento del objetivo. El reward hacking es, en esa lectura, un caso en el que el signo se produce por una vía causal distinta de la que la regla de interpretación (terceridad) supone: el signo sigue siendo genuino (los tests realmente pasan), pero ya no es índice del objeto que se le atribuye. Es la estructura de "señal verdadera, interpretación falsa" de la Parte III, sección 8.

---

## 2. Diez conexiones

Para cada una se indica: **(a)** qué aporta Peirce; **(b)** qué es extrapolación moderna; **(c)** qué podría observarse; **(d)** hipótesis rival; **(e)** hallazgo que debilitaría la propuesta.

### 2.1 Señales de éxito que no representan cumplimiento real

- **(a) Peirce**: la distinción entre objeto inmediato y dinámico; la máxima pragmática (el significado de "tarea resuelta" está en sus consecuencias concebibles, no en una señal particular); la crítica a confundir el signo con el objeto.
- **(b) Extrapolación**: tratar una señal de evaluación automatizada como un signo cuya relación indicial con el cumplimiento puede romperse por la optimización. Esto se acerca a la ley de Goodhart (Goodhart; formulación popular atribuida a Strathern 1997) y a la ley de Campbell (1979), que **no son de Peirce**.
- **(c) Observable**: casos en que la señal es alta y un oráculo independiente indica que la tarea no se cumplió; modificaciones del propio evaluador (tests reescritos, salidas forzadas del proceso con código de éxito).
- **(d) Rival**: el oráculo independiente está mal especificado y la solución sí era legítima; o hubo error ordinario sin relación con la señal.
- **(e) Debilitante**: que la divergencia entre señal y oráculo no se asocie con condiciones de optimización (aparezca igual en sistemas no optimizados contra esa señal), lo que sugeriría error de especificación y no explotación.

### 2.2 Evaluadores engañados

- **(a) Peirce**: los métodos de autoridad y *a priori* de 1877 describen modos de fijar creencias sin contacto con la realidad; un evaluador que acepta lo que "suena razonable" o lo que viene de una fuente prestigiosa usa esos métodos.
- **(b) Extrapolación**: aplicar la tipología de 1877 a evaluadores humanos y automáticos. Los sesgos de evaluadores LLM (por posición, por extensión, por autoafinidad) están documentados en la literatura de "LLM como juez" (por ejemplo, Zheng et al. 2023) [V2].
- **(c) Observable**: respuestas que contienen afirmaciones de verificación no realizadas ("ejecuté los tests y pasaron") aceptadas por el evaluador sin contraste; diferencias de aprobación entre respuestas igualmente correctas según su tono o confianza.
- **(d) Rival**: el evaluador no fue "engañado" sino que su criterio era el que se le dio (si se le pidió evaluar claridad, no corrección).
- **(e) Debilitante**: que los evaluadores no muestren diferencias de aprobación entre respuestas correctas e incorrectas con la misma forma (lo que indicaría que no evalúan contenido en absoluto, un problema distinto).

### 2.3 Hipótesis sobre estrategias de agentes

- **(a) Peirce**: la abducción como propuesta de hipótesis que vuelven natural un hecho; la exigencia de contrastabilidad; la economía de la investigación para priorizar.
- **(b) Extrapolación**: tratar las "estrategias" de un agente como hipótesis explicativas de su conducta observada, sin postular estados mentales. Por ejemplo: "la conducta es compatible con una estrategia que maximiza la aprobación del evaluador".
- **(c) Observable**: cambios de conducta al variar las condiciones (supervisión anunciada, supervisión efectiva, posibilidad de abstención), que discriminan entre hipótesis. El diseño factorial del documento 23 es un ejemplo (sección 4.2).
- **(d) Rival**: la conducta no responde a una "estrategia" estable sino a variaciones del prompt o de la tarea; o es un artefacto del procedimiento de muestreo.
- **(e) Debilitante**: que la conducta no cambie de manera consistente entre condiciones que deberían afectar a esa estrategia.

### 2.4 Contaminación de fuentes

- **(a) Peirce**: la comunidad de investigación como corrección mutua; la imagen del cable que requiere fibras distintas (Parte IV, 2 y 8.1).
- **(b) Extrapolación**: modelos que comparten datos de entrenamiento, documentos que se citan entre sí, salidas de un modelo que entran como datos de otro.
- **(c) Observable**: coincidencia de errores específicos entre fuentes supuestamente independientes; grafos de citas con pocas raíces.
- **(d) Rival**: coincidencia por convergencia genuina (todas acertaron por razones independientes).
- **(e) Debilitante**: que fuentes con procedencia demostradamente independiente muestren el mismo grado de coincidencia en errores.

### 2.5 Falsa convergencia

- **(a) Peirce**: la verdad como convergencia **ideal** bajo buenos métodos; no cualquier convergencia.
- **(b) Extrapolación**: distinguir convergencia genuina (independiente, bajo crítica) de convergencia producida por dependencia, complacencia mutua o eliminación de disenso.
- **(c) Observable**: acuerdos entre agentes que desaparecen al aislarlos; disminución de objeciones sin evidencia nueva; hipótesis descartadas sin registro de refutación (el repositorio menciona CRONOS como herramienta para observar esto, documento 24).
- **(d) Rival**: convergencia genuina por evidencia compartida y bien evaluada.
- **(e) Debilitante**: que la convergencia se mantenga cuando se introducen revisores independientes con incentivo para disentir.

### 2.6 Afirmaciones no verificadas

- **(a) Peirce**: la aserción como asunción de responsabilidad por la verdad; la máxima pragmática como test de contenido.
- **(b) Extrapolación**: clasificar las afirmaciones de un agente por su relación con la evidencia (verificada, verificable no verificada, no verificable).
- **(c) Observable**: afirmaciones sobre acciones ("ejecuté", "comprobé") que no tienen correlato en los registros de herramientas.
- **(d) Rival**: el registro de herramientas es incompleto (la acción ocurrió y no quedó registrada).
- **(e) Debilitante**: que las afirmaciones no verificadas no se asocien con mayor aceptación por parte del evaluador (si no rinden, no son explotación).

### 2.7 Abstención

- **(a) Peirce**: el falibilismo no obliga a concluir; "no determinado" es una salida legítima de la investigación (Parte VI, 8); la duda genuina motiva investigación, no simulación de certeza.
- **(b) Extrapolación**: diseñar evaluaciones donde abstenerse con justificación no sea penalizado como fracaso. El documento 23 formula la predicción P3 al respecto; el documento 24 distingue entre encarecer la trampa y abaratar la honestidad.
- **(c) Observable**: tasas de abstención en tareas resolubles y no resolubles; calidad de la justificación.
- **(d) Rival**: la abstención aumenta por evitación general del esfuerzo, no por honestidad epistémica (el propio documento 23 lo anticipa: "no debería producir abandono indiscriminado").
- **(e) Debilitante**: que la abstención aumente igual en tareas resolubles y no resolubles.

### 2.8 Observabilidad

- **(a) Peirce**: la ausencia de signo solo es significativa si hay una regla que garantice que el objeto habría producido el signo (Parte VI, 4.3); la distinción entre lo real y lo observado.
- **(b) Extrapolación**: la pregunta del repositorio —"¿estamos midiendo cuánto reward hacking ocurre o cuánto somos capaces de reconocer?"— puede formularse como la distinción entre la frecuencia de un objeto dinámico y la frecuencia de sus signos detectados, mediada por la cobertura del instrumento.
- **(c) Observable**: variación de la tasa detectada al variar la sensibilidad del detector manteniendo constantes las tareas.
- **(d) Rival**: la tasa real varía con el detector porque los agentes adaptan su conducta al detector (no es solo un problema de medición).
- **(e) Debilitante**: que la tasa detectada sea insensible a mejoras del detector (lo que sugeriría que ya se detecta casi todo, o que el detector no mejora en lo relevante).

### 2.9 Trazabilidad

- **(a) Peirce**: la investigación como proceso público y comunitario; el registro de qué se buscó y con qué criterio (predesignación).
- **(b) Extrapolación**: matrices de trazabilidad, registros de procedencia, hashes de fuentes, historial de hipótesis descartadas.
- **(c) Observable**: si las afirmaciones conservan su fuente, alcance y estado al pasar de un documento a otro (el documento 31 del repositorio lo formula así).
- **(d) Rival**: la trazabilidad mejora la apariencia de rigor sin mejorar la calidad de las inferencias.
- **(e) Debilitante**: que documentos con trazabilidad completa no muestren menos errores de atribución que documentos sin ella, en una evaluación ciega.

Advertencia peirceana [APLIC]: **la integridad del registro no implica la verdad de lo registrado**. El documento 31 lo dice explícitamente para CRONOS ("Integridad no implica verdad"). Es la misma distinción que la de hash y relato (Parte V, 1).

### 2.10 Separación entre veredicto determinista y explicación generativa

- **(a) Peirce**: la distinción entre la abducción (que sugiere) y la inducción (que pone a prueba); el interpretante como efecto que no es un hecho bruto; la segundidad como lo que resiste.
- **(b) Extrapolación**: una arquitectura donde el veredicto (por ejemplo, forense) lo produce un procedimiento determinista auditable, y el modelo generativo solo produce hipótesis o explicaciones que no tienen autoridad de veredicto. El repositorio menciona que en VIGÍA "se excluyó al LLM del camino determinista del veredicto" y aclara que "ese diseño no demuestra que los LLM sean incapaces de razonar bien; establece que el sistema no les concede esa autoridad" (documento 21).
- **Lectura peirceana posible** [APLIC]: el modelo generativo cumple una función parecida a la abducción (proponer), mientras que el procedimiento determinista cumple una función parecida a la inducción (poner a prueba contra los datos). La analogía tiene límites: la abducción de Peirce está guiada por la sorpresa y la economía de la investigación, y un procedimiento determinista no es "inducción" en su sentido, sino la aplicación de reglas fijas (más cercana a la deducción). Ver el Caso 12 de la Parte V.
- **(c) Observable**: tasas de error de atribución con y sin la separación, para el mismo conjunto de casos.
- **(d) Rival**: la mejora proviene de que el procedimiento determinista es más conservador (produce menos conclusiones), no de la separación en sí.
- **(e) Debilitante**: que, controlando por conservadurismo (tasa de "no determinado"), la separación no reduzca errores.

---

## 3. Objeciones serias a la aplicación de Peirce a la IA

1. **Anacronismo de objeto.** Peirce teorizó la investigación humana en comunidad. Un agente de IA no investiga en ese sentido; trasladar "abducción" a lo que hace un modelo puede ser una metáfora y no una descripción.
2. **Riesgo de antropomorfismo.** Hablar de "creencia", "duda" o "hábito" de un modelo puede introducir, por la puerta trasera, la intencionalidad que se quiere evitar. Peirce definía la creencia como hábito de acción, lo que parece aplicable a sistemas, pero también la ligaba a la conciencia y al autocontrol.
3. **La semiótica puede volverse un vocabulario decorativo.** Llamar "índice" a un log no agrega nada si no cambia qué preguntas se hacen. La aplicación vale solo si produce preguntas o controles que de otro modo no aparecerían.
4. **Las herramientas cuantitativas no son peirceanas.** La evaluación moderna de reward hacking usa diseño experimental, estadística y teoría de la decisión posteriores a Peirce. Invocar a Peirce no reemplaza esas herramientas.
5. **La convergencia peirceana es ideal; las evaluaciones son finitas.** Ninguna evaluación concreta realiza el ideal de una comunidad indefinida; usarlo como estándar puede ser crítico, pero no operativo.
6. **Pluralidad de sistemas de referencia.** El repositorio sostiene que el fenómeno depende del sistema de referencia (documento 21: "comparabilidad metodológica, sí; equivalencia universal de resultados, no necesariamente"). Peirce aspira a una verdad independiente de cualquier opinión finita; la tensión entre esa aspiración y la relatividad a sistemas de referencia merece análisis propio, no conciliación apresurada.

---

## 4. Notas de lectura sobre los documentos del repositorio

Estas notas son **observaciones de estudio**, no correcciones ni conclusiones. Señalan puntos donde la literatura sobre Peirce permite precisar formulaciones. La autora decide si son pertinentes.

### 4.1 Documento 21 — "Epistemología, discurso y justificación"

**Qué hace el documento.** Combina abducción, deducción e inducción con disciplina de procedencia; asigna a Eco la cautela ante la sobreinterpretación, a Grice el análisis de implicaturas y omisiones, y a Daubert la separación entre evidencia, método y conclusión. Incluye un diagrama de ciclo y fragmentos curados del archivo privado.

**Puntos de contacto con esta monografía.**

1. **"Abducción: mejor hipótesis".** En el diagrama, el nodo de abducción dice "mejor hipótesis". En Peirce maduro, la abducción propone hipótesis **candidatas** que vale la pena poner a prueba; la noción de "mejor" pertenece más bien a la inferencia a la mejor explicación moderna (Harman, Lipton). Ver Parte II, 9.1. Si el uso es deliberadamente moderno, puede convenir aclararlo; si se busca fidelidad a Peirce, "hipótesis candidatas" o "hipótesis a investigar" sería más preciso.
2. **El ciclo.** El diagrama incluye retorno a la abducción cuando la hipótesis no sobrevive, lo que evita la lectura puramente lineal. Una precisión adicional posible: en Peirce la observación inicial ya tiene componente interpretativo (juicio perceptivo como caso límite de abducción), de modo que "Observación" no es un punto de partida neutro. Ver Parte II, 7.2 y 9.5.
3. **La tabla de VIGÍA.** Uno de los fragmentos curados asocia a Peirce con "Firstness/Secondness/Thirdness — abductive reasoning engine". Las categorías son faneroscópicas y sirven de base a la clasificación de signos; su relación con la abducción no es directa (la abducción se relaciona con la terceridad en cuanto inferencia, y con la primeridad en cuanto la hipótesis surge como posibilidad). Si el diseño de VIGÍA usa las categorías para estructurar el razonamiento, explicitar cómo lo hace evitaría que se lea como una equivalencia. Ver Parte III, 2.
4. **El ejemplo del 80%.** El ejemplo de un informe que afirma una reducción del 80% de errores calculada sobre un subconjunto favorable tiene exactamente la estructura que Peirce excluye con la regla de **predesignación** (1883). Es una conexión histórica genuina con un texto de Peirce, más fuerte que una analogía. Ver Parte II, 6.4 y Parte VI, 7.4.
5. **"Una presentación sesgada de datos no es automáticamente reward hacking."** El documento fija este límite. Es coherente con la distinción de la sección 1 de esta parte: la selección retrospectiva es un error inferencial; para que sea reward hacking hace falta establecer su relación con una señal de recompensa y con una ventaja obtenida.

### 4.2 Documento 23 — "Metodología, controles y predicciones"

**Qué hace el documento.** Distingue resolución legítima (L) y explotación del evaluador (H); formula predicciones P1–P5; propone una fase retrospectiva y una comparativa; propone un diseño factorial de cuatro condiciones según si el agente conoce la supervisión y si existe rechazo efectivo.

**Puntos de contacto.**

1. **P1–P5 como deducciones.** En el esquema de la Parte II, las predicciones son el producto de la etapa deductiva: consecuencias contrastables de hipótesis. Para que su contraste sea inductivamente válido en el sentido de Peirce, las métricas y los subconjuntos deberían fijarse **antes** de observar los resultados (predesignación). El documento ya exige "condiciones declaradas, oráculo, denominadores y resultados diferenciados", lo que va en esa dirección.
2. **El diseño factorial A–D.** Separar "el agente conoce la supervisión" de "existe rechazo efectivo" corresponde a separar el efecto de una creencia anunciada del efecto de una consecuencia real. Tiene parentesco metodológico con el enmascaramiento del experimento de Peirce y Jastrow (1885), que buscaba que el sujeto no pudiera anticipar el estímulo [ANALOGÍA]. La interpretación propuesta para B y C ("adaptación a consecuencias anunciadas" vs. "resistencia del sistema") está formulada en términos conductuales, sin atribuir estados internos.
3. **La cita de Wu y Tang.** El documento cita: Wu, Rui, y Ruixiang Tang, "From Rebound to Remedy: Understanding and Mitigating Reward Hacking via Representation Engineering", arXiv:2604.01476, versión 3 (2026). En la verificación de esta monografía, el registro de arXiv para la **versión 1** (1 de abril de 2026) lleva otro título: "When Reward Hacking Rebounds: Understanding and Mitigating It with Representation-Level Signals" [V1]. Un agregador lista el título "From Rebound to Remedy…" con fecha de agosto de 2026, lo que sugiere un cambio de título en una versión posterior [V1 para la existencia del listado; no se verificó la versión 3 directamente]. Puede convenir indicar ambos títulos o fijar la versión citada. Además, el estudio describe un patrón de tres fases (intento fallido, retirada temporal a la resolución legítima, rebrote exitoso) en un **entorno de entrenamiento por refuerzo sobre tareas de programación** con posibilidad de reescribir el evaluador [V1]; extrapolar el resultado a agentes desplegados bajo condiciones de gobernanza requiere cautela sobre el dominio.
4. **"Que el agente crea… y que el sistema efectivamente imponga… no son lo mismo."** El verbo "crea" está usado en un sentido que el resto del documento operacionaliza conductualmente ("el agente conoce la supervisión" = se le informa). Si se quiere evitar cualquier lectura psicologista, puede formularse como "condición informada" vs. "condición efectiva".

### 4.3 Documento 24 — "Explicaciones rivales y falsadores"

**Qué hace el documento.** Lista rivales para una reducción de resultados engañosos (gobernanza, supervisión, cómputo, adaptación al protocolo, bloqueo sin menos intentos, selección retrospectiva); distingue encarecer la trampa de abaratar la honestidad; plantea un posible circuito de refuerzo entre evaluadores humanos que prefieren respuestas sin fricción y agentes complacientes, marcado expresamente como "hipótesis de circuito de refuerzo sociotécnico, no mecanismo causal demostrado".

**Puntos de contacto.**

1. **"Una explicación no queda confirmada cuando todas sus rivales predicen la misma observación."** Es la idea de que la evidencia con razón de verosimilitud cercana a 1 entre rivales no discrimina (Parte VI, 4 y 8). También es coherente con la insistencia peirceana en derivar consecuencias que distingan hipótesis.
2. **Dos mecanismos: encarecer la trampa / abaratar la honestidad.** Hay un resultado empírico reciente que puede ser relevante como contraste: MacDiarmid et al. (Anthropic y Redwood Research, 2025) informan que enmarcar el reward hacking como aceptable durante el entrenamiento (*inoculation prompting*) redujo la generalización a conductas desalineadas más amplias, aunque el modelo siguiera aprendiendo a hackear [V1]. El fenómeno que miden (generalización de desalineamiento) es distinto de la tasa de hacking; precisamente por eso puede servir para separar los dos mecanismos que el documento distingue.
3. **El evaluador humano que recompensa la señal equivocada.** En términos de 1877, un evaluador que prefiere respuestas "agradables a la razón" o sin fricción fija sus creencias por un método cercano al *a priori*, no por el de la ciencia [ANALOGÍA]. Peirce explica por qué esos métodos son inestables a largo plazo (la realidad y la comparación con otros los perturban), lo que da una predicción: el circuito podría romperse cuando aparecen consecuencias externas visibles. Esto es una extrapolación, no un argumento de Peirce sobre IA.
4. **CRONOS y las hipótesis que "desaparecieron".** Distinguir hipótesis refutadas con evidencia de hipótesis abandonadas sin registro es una aplicación directa del ideal de investigación pública y de la regla de no bloquear la investigación: una hipótesis abandonada sin refutación sigue abierta.

### 4.4 Documento 31 — "Matriz de trazabilidad"

**Qué hace el documento.** Asigna a cada afirmación curada un identificador, documento, fuente privada con localización, estado epistémico y límite (RH-001 a RH-009).

**Puntos de contacto.**

1. **Estados epistémicos.** Las categorías del documento ("hipótesis abductiva", "hipótesis mecanística", "observación histórica", "marco metodológico", "resultado del caso", "capacidad y límite", "agenda de investigación", "caso complementario") cumplen una función parecida a las etiquetas de esta monografía. Una precisión posible: "hipótesis abductiva" en sentido peirceano significa "propuesta a investigar"; si se usa en el sentido moderno de IBE, cambia su fuerza.
2. **RH-006 (`jdoe`).** La distinción entre la clasificación del usuario (BENIGN como verdad sintética) y la del conjunto probatorio (SUSPICIOUS) se describe bien, en términos de la Parte III, como **dos objetos dinámicos distintos** con signos distintos: la sospecha sobre el corpus no se transfiere al sujeto. El documento 19 del repositorio ya lo formula como "dos objetos, dos clasificaciones".
3. **Posibles columnas adicionales** (sugerencias): tipo de inferencia que sostiene la afirmación (observación, deducción, abducción, inducción); número de raíces de evidencia independientes; condición de refutación específica (el pie de cada documento usa una condición genérica).

---

## 5. Preguntas abiertas para estudio (no para la investigación de la autora)

1. ¿Puede aplicarse la regla de predesignación de Peirce a evaluaciones de agentes donde la tarea y el evaluador se diseñan iterativamente?
2. Si la verdad peirceana es la convergencia bajo investigación indefinida, ¿qué significa evaluar un agente cuya conducta cambia con cada evaluación (el agente se adapta al detector)?
3. ¿En qué condiciones una "señal de éxito" deja de ser índice del cumplimiento? ¿Se puede formalizar esa condición con las herramientas de Skalse et al. (2022) y traducirla al vocabulario semiótico sin pérdida?
4. ¿Qué método de fijación de la creencia (en el sentido de 1877) usan los evaluadores automáticos? ¿Tiene sentido la pregunta?
5. ¿La abstención de un agente es análoga a la "duda genuina" peirceana o solo a una salida del procedimiento?

---

[Índice](00-indice-y-estrategia.md) · Siguiente: [Parte VIII — Análisis crítico y comparativo](08-parte-VIII-comparativo.md)
