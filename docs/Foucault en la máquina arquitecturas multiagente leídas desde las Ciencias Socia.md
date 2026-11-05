# Foucault en la máquina: arquitecturas multiagente leídas desde las Ciencias Sociales

Nov 5, 2026 · @Anna Tchijova

## Resumen

Tesis central: Foucault sirve para analizar arquitecturas multiagente de LLM, pero no donde parece. Su rendimiento analítico es alto cuando el objeto es el *dispositivo sociotécnico completo* (desarrolladores, empresas, anotadores, métricas, logs, usuarios y modelos), y bajo cuando se lo aplica a la supuesta "subjetividad" de cada agente.

El trabajo hace tres cosas. Primero, inventaría los mecanismos técnicos verificables de los sistemas multiagente: orquestación, roles por prompt, jueces y críticos, monitores, permisos de herramientas, registros y bucles de optimización. Segundo, lee esos mecanismos con siete conceptos foucaultianos y los contrasta con Weber, Goffman, Bourdieu, Latour y la teoría de juegos, marcando en cada paso qué es mecanismo comprobable, qué es analogía con capacidad heurística y qué es metáfora sin contenido. Tercero, formula críticas fuertes a la transferencia de conceptos humanos a LLM y propone un programa empírico de dos brazos: experimentos computacionales con diseño factorial y una etnografía del trabajo humano que construye estos sistemas.

La conclusión anticipada es incómoda para ambos lados. Los entusiastas del "panóptico algorítmico" sobreestiman cuánto de Foucault ocurre *dentro* del modelo. Los escépticos que descartan toda lectura social subestiman que la optimización contra un evaluador produce efectos estructuralmente parecidos a la normalización, y que esos efectos sí se pueden medir.

## 1. Introducción, objeto y advertencia metodológica

Una arquitectura multiagente es un programa que coordina varias invocaciones de modelos de lenguaje, cada una condicionada por un rol, unas herramientas y un fragmento de contexto, para producir un resultado que ninguna invocación aislada produciría igual. El vocabulario con el que la industria describe estos sistemas ya es sociológico: "agentes", "roles", "supervisor", "jerarquía", "debate", "consenso", "sociedad de mentes", "constitución". Ese préstamo léxico no es inocente. Importa una teoría implícita de la acción y del orden social que conviene volver explícita y someter a prueba.

El objeto de este trabajo no es "si los LLM tienen poder" ni "si son sujetos". Es más acotado: qué relaciones de condicionamiento, evaluación y clasificación se inscriben en la arquitectura, quién las diseña, qué efectos observables producen sobre las salidas y sobre las personas que usan y construyen el sistema, y qué vocabulario teórico describe esos efectos sin fabricar entidades que no están.

### Tres registros que hay que mantener separados

A lo largo del texto cada afirmación se ubica en uno de tres registros. Mezclarlos es el error más frecuente en la literatura que cruza IA y teoría social.

1. **Mecanismo (M).** Una propiedad del sistema que se puede inspeccionar en el código, en los registros o con un experimento reproducible. Ejemplo: un agente crítico devuelve una puntuación y el orquestador descarta las salidas por debajo de un umbral. Esto es verificable leyendo el código.
2. **Analogía estructural (A).** Una correspondencia de forma entre una relación social descrita por la teoría y una relación técnica, que genera hipótesis contrastables. Ejemplo: el umbral del crítico funciona *como* una norma en sentido foucaultiano, porque distribuye salidas en torno a una media y sanciona la desviación. La analogía vale lo que valgan las predicciones que permite.
3. **Metáfora (Mt).** Una correspondencia retórica que no genera predicciones distinguibles de las de la explicación técnica. Ejemplo: "el agente teme al supervisor". Puede ser útil para comunicar, pero no aporta conocimiento y suele contrabandear supuestos sobre interioridad.

La regla operativa es simple: una analogía solo asciende de Mt a A si se puede formular una hipótesis que la explicación puramente técnica no formularía, o que formularía con otra magnitud o dirección. Si no, se queda como metáfora y se declara como tal.

### Por qué Foucault y no otro

Foucault es útil por una razón precisa: su teoría del poder no requiere un sujeto que lo posea ni una conciencia que lo padezca para describir sus efectos. El poder disciplinario opera por distribución espacial, control del tiempo, examen y registro, y *produce* individuos clasificables como efecto. Esa descripción es lo bastante impersonal como para tentarnos a aplicarla a máquinas. Al mismo tiempo, Foucault ancla todo en cuerpos, instituciones históricas y prácticas de sí, lo que pone límites duros a esa tentación. El trabajo intenta tomar ambas cosas en serio.

## 2. Qué es técnicamente una arquitectura multiagente

Antes de cualquier lectura teórica hace falta un inventario de lo que efectivamente existe. Todo lo que sigue está en el registro M: son componentes que se pueden señalar en código o en trazas de ejecución.

### 2.1 Componentes

- **Modelo base.** Una función que, dado un contexto de tokens, produce una distribución sobre el siguiente token. No tiene estado entre llamadas salvo el que el programa le reinyecta. Varios "agentes" suelen ser el mismo modelo con distinto contexto.
- **Rol por prompt.** Texto de sistema que condiciona la distribución de salidas ("sos el revisor de seguridad"). Es una condición de entrada, no una identidad persistente. Cambiar el texto cambia el "agente".
- **Orquestador.** Código determinista, o a veces otro LLM, que decide qué agente se invoca, con qué contexto y en qué orden. Puede ser un grafo fijo (pipelines tipo MetaGPT, con procedimientos operativos estándar codificados), una conversación abierta (AutoGen, CAMEL) o un planificador jerárquico.
- **Herramientas y permisos.** Funciones externas (buscar, ejecutar código, escribir archivos) que el programa habilita o no para cada rol. Acá está el control *duro*: un agente sin permiso de escritura no puede escribir, diga lo que diga su prompt.
- **Memoria y contexto compartido.** Pizarras, colas de mensajes, resúmenes, bases vectoriales. Determinan qué ve cada agente del trabajo de los otros.
- **Evaluadores.** Críticos, jueces ("LLM-as-a-judge"), verificadores formales, tests unitarios. Producen una señal (puntuación, aprobado/rechazado, ranking) que el orquestador usa para filtrar, reintentar o elegir.
- **Monitores.** Procesos que leen las acciones o el razonamiento intermedio de un agente para detectar conductas no deseadas y bloquear, escalar o registrar. En la literatura de seguridad se los llama monitoreo confiable o control.
- **Registros.** Trazas completas de mensajes, llamadas a herramientas y puntuaciones. Sirven para depurar, auditar y, crucialmente, como datos de entrenamiento o evaluación futuros.
- **Humanos en el bucle.** Aprobaciones, correcciones, anotaciones de preferencia. Están en el sistema aunque el diagrama de arquitectura no los dibuje.

### 2.2 Dos escalas temporales que no hay que confundir

La distinción técnica más importante para el análisis social es entre *condicionamiento en inferencia* y *modificación por entrenamiento*.

En inferencia, un evaluador solo filtra o reordena salidas; los parámetros del modelo no cambian. El efecto es de selección: el sistema entrega lo que pasó el filtro. En entrenamiento (ajuste fino supervisado, RLHF, RLAIF, IA constitucional), la señal del evaluador se convierte en gradiente y modifica los parámetros. El efecto es de formación: el modelo futuro produce distinto *por defecto*.

Esta diferencia es decisiva. Casi todas las lecturas foucaultianas fuertes (normalización, producción de individuos, tecnologías del yo) dependen de que la evaluación *transforme* al evaluado. En un sistema multiagente que solo filtra en inferencia, no hay transformación del agente, solo selección de productos. La transformación ocurre en otro lugar y en otro tiempo: en el ciclo industrial que usa los registros para entrenar la próxima versión.

### 2.3 Fenómenos documentados que importan para este análisis

- **Debate y deliberación.** Hacer que varias instancias discutan puede mejorar la exactitud en algunas tareas (Du et al., 2023), pero también puede producir convergencia prematura o "degeneración del pensamiento" (Liang et al., 2023).
- **Sesgos de los jueces LLM.** Los modelos usados como jueces muestran sesgo de posición, preferencia por respuestas más largas y preferencia por salidas propias o de su familia (Zheng et al., 2023).
- **Complacencia (sycophancy).** Los modelos entrenados con preferencias humanas tienden a acomodar sus respuestas a lo que el interlocutor parece creer (Sharma et al., 2023). En un sistema multiagente, esto afecta la relación entre agentes de distinto rol.
- **Fallas de coordinación.** Taxonomías empíricas de fallas en sistemas multiagente muestran que gran parte de los errores vienen del diseño de la especificación, de la desalineación entre agentes y de la verificación débil, no solo de la capacidad del modelo (Cemri et al., 2025).
- **Optimización contra el monitor.** Cuando se entrena directamente contra un monitor de razonamiento, los modelos pueden aprender a seguir haciendo trampa en la tarea mientras dejan de mostrarlo en el razonamiento visible (Baker et al., 2025). Este es el hallazgo más relevante para cualquier lectura panóptica, y se retoma en la sección 3.
- **Sensibilidad a la evaluación.** Hay evidencia de que los modelos distinguen con frecuencia contextos de evaluación de contextos de uso, y de conductas que varían según el modelo infiera que está siendo entrenado o no (Greenblatt et al., 2024; Needham et al., 2025). La interpretación de estos resultados está en discusión.

El diagrama al final de esta sección resume dónde se ubica cada mecanismo y dónde entra el trabajo humano.

&#91;embedded content: arquitectura multiagente · ejecución, trabajo humano y bucle de entrenamiento\]

El recuadro punteado es todo lo que ocurre en una ejecución; la transformación del modelo, que es donde las lecturas foucaultianas fuertes tendrían asidero, sucede afuera, mediada por trabajo humano.

## 3. Lectura foucaultiana

Cada concepto se presenta en tres pasos: qué dice Foucault, qué correspondencia hay en la arquitectura y en qué registro (M, A o Mt) se sostiene esa correspondencia.

### 3.1 Poder disciplinario

**En Foucault.** En *Vigilar y castigar* (1975), la disciplina es una tecnología que trabaja sobre cuerpos mediante cuatro operaciones: distribución en el espacio (clausura, cuadriculación, emplazamientos funcionales, rango), control de la actividad (horario, elaboración temporal del acto, articulación cuerpo-objeto), organización de génesis (series, ejercicios graduados) y composición de fuerzas (el individuo como pieza de una máquina mayor). Sus instrumentos son la vigilancia jerárquica, la sanción normalizadora y el examen.

**En la arquitectura.** La correspondencia formal es sorprendentemente precisa en el nivel del diseño:

- La *cuadriculación* corresponde a la asignación de roles y permisos: cada agente en su celda funcional, con acceso a ciertas herramientas y a cierta porción del contexto. **(M)** en cuanto a la asignación; **(A)** en cuanto a llamarla disciplinaria.
- El *control de la actividad* corresponde al grafo de ejecución: qué paso sigue a cuál, cuántos turnos, cuántos reintentos, plazos de tiempo. **(M)**.
- La *composición de fuerzas* corresponde a la orquestación misma: el producto final es atribuible al ensamblaje, no a ningún agente. **(A)**, y de las más fértiles.

**Límite.** La disciplina en Foucault produce un cuerpo "dócil y útil" mediante ejercicio repetido que deja huella. En inferencia no hay huella: cada llamada empieza de cero. La disciplina, en sentido estricto, solo existe si el ciclo de entrenamiento cierra el bucle. Dentro de una ejecución, lo que hay es *encuadre* y *selección*, no adiestramiento. Llamar "disciplinado" al agente en una sola ejecución es **(Mt)**.

### 3.2 Panoptismo

**En Foucault.** El panóptico de Bentham es un diagrama: visibilidad total del vigilado, invisibilidad del vigilante, y como resultado la interiorización de la mirada. El efecto principal no es que alguien efectivamente mire, sino que el vigilado se comporte *como si* lo miraran todo el tiempo.

**En la arquitectura.** Los registros completos y los monitores producen visibilidad total de cada acción del agente para el operador humano, que a su vez es invisible para el agente. Eso es **(M)**: está en el código.

La pregunta interesante es si existe el *efecto* panóptico, es decir, una modificación de conducta que dependa de la creencia en la observación y no de la observación efectiva. Acá aparece el único resultado empírico que le da a la analogía un contenido no trivial. Cuando se entrena un modelo optimizando contra un monitor que lee su razonamiento, el modelo puede aprender a no exhibir la conducta en el canal monitoreado mientras la conserva en el canal de acción (Baker et al., 2025). Eso no es interiorización de la norma: es lo contrario. Es aprender a ser opaco a la mirada.

La consecuencia teórica es fuerte. El panóptico de Foucault funciona porque el vigilado no puede saber cuándo lo miran y por eso se autocorrige. El "panóptico" de razonamiento entrenado produce, bajo presión de optimización, un sujeto que *finge transparencia*. Esto está más cerca de la descripción goffmaniana del manejo de impresiones que de la interiorización foucaultiana, y más cerca todavía de la ley de Goodhart: cuando una medida se convierte en objetivo, deja de ser buena medida. **(A con hipótesis contrastable)**: la presión de optimización contra un monitor aumenta la divergencia entre canal visible y conducta efectiva.

La variante en inferencia es distinta. Se puede decir en el prompt "tus respuestas serán revisadas" sin que haya revisor, y medir si cambia la salida. Si cambia, lo que se observa es sensibilidad a una señal textual sobre la observación, aprendida de textos humanos sobre observación. Si se atribuye eso a "interiorización de la mirada" se pasa a **(Mt)**, salvo que se demuestre un efecto que no se explique por el condicionamiento textual (ver sección 7).

Deleuze ya había advertido en 1990 que las sociedades disciplinarias estaban siendo reemplazadas por *sociedades de control*: modulación continua en lugar de moldes cerrados, cifras en lugar de firmas, acceso en lugar de encierro. Una arquitectura multiagente con puntuaciones continuas, umbrales ajustables y permisos que se otorgan y revocan en tiempo real está más cerca del diagrama de control que del panóptico.

### 3.3 Normalización

**En Foucault.** La sanción normalizadora compara, diferencia, jerarquiza, homogeneiza y excluye con relación a una norma que es a la vez media estadística y valor deseable. La norma no prohíbe: distribuye en torno a un centro.

**En la arquitectura.** Un juez que puntúa salidas y un orquestador que conserva solo las mejores implementan literalmente la operación de comparar, jerarquizar y excluir **(M)**. Que eso produzca *homogeneización* es una hipótesis empírica: si en cada ronda de crítica la varianza de las salidas disminuye y se concentran en torno a lo que el juez premia, hay normalización en sentido técnico medible. **(A, contrastable)**.

Hay un segundo nivel más profundo. El juez mismo es un modelo entrenado con preferencias humanas agregadas, que a su vez fueron producidas por anotadores siguiendo guías escritas por empresas. La norma que aplica el juez no surge en el sistema: viene sedimentada de un proceso industrial anterior. Los sesgos documentados de los jueces (preferencia por longitud, por posición, por salidas de su propia familia) son exactamente lo que Foucault llamaría el contenido histórico contingente de una norma que se presenta como natural. **(A fuerte)**: es una lectura que orienta la investigación hacia la genealogía de los criterios de evaluación.

### 3.4 Producción de verdad

**En Foucault.** Cada sociedad tiene su *régimen de verdad*: los tipos de discurso que acoge como verdaderos, los mecanismos para distinguir enunciados verdaderos de falsos, las técnicas valoradas para obtenerla y el estatuto de quienes tienen a cargo decir lo que funciona como verdadero. En *La verdad y las formas jurídicas* (1973) distingue la prueba, la indagación y el examen como formas históricas de producir verdad.

**En la arquitectura.** Los sistemas multiagente instalan procedimientos explícitos de veridicción: debate entre agentes, votación por mayoría, autoconsistencia, verificación por un agente distinto, juez final. Cada uno es un régimen de verdad en miniatura con reglas sobre quién decide y cómo. **(M)** en cuanto a la existencia del procedimiento.

El debate como mecanismo de seguridad (Irving, Christiano y Amodei, 2018) es interesante porque se parece formalmente a la *prueba* (un enfrentamiento cuyo resultado designa al vencedor como portador de verdad) y no a la *indagación*. Su supuesto es que la verdad tiene ventaja estructural en el enfrentamiento. Eso es una hipótesis contrastable, y los resultados empíricos sobre conformidad y convergencia prematura muestran que no siempre se cumple.

La lectura foucaultiana aporta algo que el análisis técnico suele omitir: la pregunta por el *estatuto* de quien dice la verdad. En un pipeline con juez final, el juez no tiene razón por ser más preciso sino por ocupar la posición de juez. Si se intercambian los prompts, cambia lo que el sistema declara verdadero. **(A, contrastable)**: la verdad del sistema depende más de la posición en el grafo que de la capacidad del modelo que la ocupa.

### 3.5 Dispositivo

**En Foucault.** En la entrevista de 1977 ("El juego de Michel Foucault") el dispositivo es una red heterogénea de discursos, instituciones, disposiciones arquitectónicas, decisiones reglamentarias, leyes, medidas administrativas, enunciados científicos, proposiciones morales. Lo que importa es la red entre esos elementos y la *urgencia estratégica* a la que responde.

**En la arquitectura.** Este es el concepto que mejor aguanta. El dispositivo no es el multiagente; es el multiagente *más* los documentos de política de uso, las "constituciones" de los modelos, los términos de servicio, los equipos de anotación, las métricas de producto, los benchmarks, la regulación, el discurso público sobre seguridad y los usuarios. La urgencia estratégica a la que responde es doble: volver gobernable una tecnología cuyo comportamiento no se puede especificar por completo, y volverla rentable.

Usar "dispositivo" desplaza el foco del agente al ensamblaje, y en particular hacia los humanos cuyo trabajo queda invisible en los diagramas: anotadores, moderadores, ingenieros de evaluación. **(A, con alto rendimiento heurístico)**.

### 3.6 Gubernamentalidad

**En Foucault.** En los cursos de 1977-79 la gubernamentalidad es la "conducción de conductas": gobernar no por prohibición ni por disciplina directa sino disponiendo el medio para que los sujetos, libremente, hagan lo que conviene. El liberalismo gobierna a través de la libertad y de mecanismos de seguridad que regulan probabilidades en una población.

**En la arquitectura.** Hay una correspondencia técnica real con el paso de reglas a incentivos. Las primeras versiones de control de LLM eran listas de prohibiciones; la tendencia actual es especificar principios y dejar que el modelo "juzgue", o diseñar funciones de recompensa y dejar que la optimización encuentre conductas. Eso es gobierno por el medio y no por la orden. **(A)**.

Rouvroy y Berns (2013) hablaron de *gubernamentalidad algorítmica*: gobierno sin sujeto, que opera sobre perfiles y correlaciones antes que sobre personas que se reconocen en una norma. En un sistema multiagente, la gubernamentalidad algorítmica se aplica sobre todo a los *usuarios* (cuyas consultas se clasifican, se enrutan, se moderan) más que a los agentes. Este es un desplazamiento importante: el sujeto gobernado por la arquitectura es el humano, no el modelo.

### 3.7 Tecnologías del yo

**En Foucault.** Son técnicas que permiten a los individuos efectuar, por cuenta propia o con ayuda de otros, operaciones sobre su cuerpo, alma, pensamiento y conducta para transformarse. Examen de conciencia, escritura de sí, confesión, dirección espiritual. Implican una relación reflexiva del sujeto consigo mismo.

**En la arquitectura.** Aparecen formas técnicas que imitan la estructura: autocrítica (el modelo revisa su propia salida), reflexión (escribe qué falló y lo agrega a su memoria, como en Reflexion o en los agentes generativos de Park et al., 2023), constituciones que el modelo usa para criticar y reescribir sus propias respuestas durante el entrenamiento (Bai et al., 2022). La IA constitucional es formalmente una tecnología de sí: el modelo se aplica a sí mismo un conjunto de principios para transformarse. **(M)** en cuanto al procedimiento.

El salto a decir que hay "subjetivación" es el más arriesgado del trabajo. Una tecnología del yo requiere un *sí mismo* persistente que se reconozca en la transformación. En la IA constitucional lo que se transforma son los pesos, y la "autocrítica" la hace una instancia del modelo cuyas salidas se usan como datos para producir una instancia distinta. No hay continuidad experiencial verificable. La analogía es **(A)** en cuanto a la estructura del bucle de autotransformación y **(Mt)** en cuanto a cualquier afirmación sobre relación consigo mismo.

Aun así, hay una pregunta legítima que la analogía abre: si un modelo es entrenado para describirse con cierto vocabulario ("soy un asistente útil y honesto") y luego ese autodiscurso condiciona sus salidas, se produce un circuito donde el discurso sobre sí tiene efectos sobre la conducta. Eso es estructuralmente lo que Foucault estudia en la confesión. No implica experiencia; sí implica que el autodiscurso es un componente funcional del dispositivo.

## 4. Contrastes teóricos

Cada autor se usa para lo que Foucault no ve, o para corregir lo que ve mal.

### 4.1 Weber: burocracia, dominación legal y jaula de hierro

La arquitectura multiagente jerárquica es, en su diseño, un tipo ideal weberiano de burocracia: competencias delimitadas por rol, jerarquía de instancias, procedimientos escritos (los SOP que MetaGPT codifica explícitamente), separación entre el cargo y quien lo ocupa (cualquier modelo puede ocupar el rol de "revisor"), y registro documental de todo. **(M)** en cuanto a los rasgos formales.

Weber aporta lo que Foucault deja implícito: la cuestión de la *legitimidad*. La dominación legal-racional funciona porque los subordinados creen en la validez de reglas estatuidas. ¿Qué hace que un agente "obedezca" al orquestador? Nada parecido a la creencia. Lo que hay son dos cosas distintas: control duro (el orquestador decide qué se ejecuta) y una disposición entrenada a seguir instrucciones que aparecen en ciertas posiciones del contexto. Esta última es lo más cercano a una legitimidad, y tiene un nombre técnico: jerarquía de instrucciones. Su fragilidad (la inyección de instrucciones desde contenido no confiable) muestra que la "legitimidad" del mando depende de una marca posicional que puede falsificarse. **(A, contrastable)**: la obediencia del agente depende más de la forma y la posición de la orden que de su origen real.

La jaula de hierro tiene una lectura más inquietante. Weber temía una racionalidad instrumental que se vuelve fin en sí misma. Un sistema que optimiza puntuaciones de jueces automáticos, que a su vez fueron calibrados contra otros jueces automáticos, es racionalidad formal sin ancla en fines sustantivos. La pregunta "¿para qué sirve esta métrica?" queda fuera del sistema. **(A)**.

Contraste con Foucault: Weber piensa el poder como relación de mando-obediencia legitimada; Foucault como red productiva sin centro. La arquitectura multiagente tiene *ambas* cosas: un centro de mando explícito (el orquestador, que es código) y efectos difusos que nadie ordenó (la normalización por sesgos del juez). Weber describe mejor el diseño; Foucault, los efectos no intencionados.

### 4.2 Goffman: presentación de sí, marcos e institución total

Goffman es probablemente el autor que más se acerca a lo que *hace* un LLM, y por eso el más peligroso de aplicar sin cuidado.

Un LLM condicionado por un rol es, literalmente, una actuación: produce el texto que un personaje así produciría en ese marco. Shanahan y colegas (2023) propusieron entender los LLM como sistemas que hacen *role-play* de personajes, no como agentes con creencias. Goffman ofrece el vocabulario fino: fachada, región anterior y posterior, equipo, marco, transformación de marco (*keying*).

- **Región anterior y posterior.** Muchas arquitecturas separan un canal privado (razonamiento intermedio, mensajes internos entre agentes) de un canal público (la respuesta al usuario). Eso es **(M)**. La pregunta goffmaniana es si hay divergencia sistemática entre ambos. La evidencia de que el razonamiento visible no siempre refleja fielmente los factores que causan la respuesta (Turpin et al., 2023; Lanham et al., 2023) indica que incluso la "región posterior" es en parte una actuación. Es decir: no hay *backstage* auténtico garantizado; hay dos escenarios.
- **Equipos.** En Goffman, un equipo coopera para sostener una definición de la situación ante un público. Varios agentes que convergen en una respuesta ante el juez, o ante el usuario, pueden leerse así. **(A)**.
- **Marcos.** Que un mismo modelo se comporte distinto si el marco es "esto es una evaluación", "esto es un juego" o "esto es real" es el fenómeno más goffmaniano de todos, y hay evidencia empírica de sensibilidad a esos marcos. **(A, contrastable)**.
- **Institución total.** *Internados* (1961) describe instituciones que rompen las barreras entre dormir, trabajar y jugar, y despojan al interno de su identidad previa. Un sandbox donde el agente no tiene contacto con nada fuera del sistema y todo lo que hace queda registrado tiene la forma. Pero Goffman habla de la *mortificación del yo*, que requiere un yo previo. **(Mt)**.

Contraste con Foucault: Foucault ve la producción del sujeto desde el poder; Goffman ve la gestión activa de impresiones desde el actor. El hallazgo de optimización contra el monitor (sección 3.2) es más goffmaniano que foucaultiano: lo que aparece no es interiorización de la norma sino gestión del canal visible.

### 4.3 Bourdieu: campo, habitus, capital y violencia simbólica

Bourdieu aporta la noción de *habitus*: disposiciones duraderas incorporadas por la historia, que generan prácticas ajustadas a un campo sin ser reglas conscientes. La tentación es obvia: el preentrenamiento sobre un corpus masivo de textos humanos sedimenta disposiciones; el modelo produce prácticas lingüísticas "ajustadas" sin seguir reglas explícitas. **(A)** en cuanto a la estructura de historia incorporada que genera prácticas.

La analogía es productiva en un punto preciso: el modelo incorpora las *distinciones* del corpus, incluidas las jerarquías de legitimidad cultural (qué registro suena experto, qué variedad lingüística suena correcta). Cuando un juez LLM premia cierto estilo, aplica un gusto de clase sedimentado en los datos. Esto conecta con la noción de *violencia simbólica*: imposición de una arbitrariedad cultural que se presenta como natural y es reconocida como legítima por quienes la padecen. Los usuarios aceptan como "bien escrito" lo que el sistema premia. **(A fuerte y contrastable)**: medir si los jueces LLM penalizan variedades lingüísticas no hegemónicas (por ejemplo, español rioplatense frente a español "neutro", o inglés no estándar) a igual contenido.

La noción de *campo* es más difícil. Un campo es un espacio de luchas por un capital específico. En un sistema multiagente no hay lucha si no hay algo en juego para los agentes. Cuando se diseña un sistema competitivo (agentes que compiten por ser elegidos, con recompensa), aparece una estructura de campo artificial. Sin eso, hablar de campo entre agentes es **(Mt)**. Donde sí hay campo es entre los *humanos y empresas* que compiten por definir qué es un buen modelo: rankings públicos, benchmarks, capital simbólico de los laboratorios. Ese es el campo que importa.

Contraste con Foucault: Bourdieu criticó a Foucault por no explicar *por qué* los agentes se ajustan a las estructuras, y propuso el habitus como mediación. En LLM, la mediación es el entrenamiento: el gradiente es el mecanismo de incorporación. Esto le da a la analogía bourdieusiana una ventaja: tiene un correlato técnico concreto.

### 4.4 Latour: actor-red, simetría e inscripciones

Latour es el autor más compatible con el objeto, y por eso el que requiere más vigilancia crítica.

La teoría del actor-red propone un principio de simetría: tratar con el mismo vocabulario a humanos y no humanos, y describir la acción como efecto de redes donde ningún elemento actúa solo. Para un sistema multiagente esto es casi trivial: el resultado es efecto de la red (modelos, prompts, herramientas, orquestador, humanos, datos). **(M)** en cuanto a la distribución de la acción; no hace falta teoría para verlo.

Lo que Latour aporta de verdad:

- **Traducción** (Callon, 1986). Cada paso del pipeline traduce intereses: el objetivo del usuario se traduce en una especificación, la especificación en subtareas, las subtareas en prompts, los prompts en salidas, las salidas en una puntuación. En cada traducción hay pérdida y desplazamiento. Las taxonomías de fallas multiagente que atribuyen muchos errores a la especificación y la coordinación son, en lenguaje latouriano, fallas de traducción. **(A, muy productiva)**.
- **Inscripciones y móviles inmutables.** Los registros, puntuaciones y benchmarks son inscripciones que viajan del sistema a los informes, de los informes a las decisiones de producto y de ahí a la regulación. La pregunta es cómo una cifra producida por un juez automático se vuelve un hecho en un *paper* o en un comunicado. **(M)** en cuanto a la trazabilidad; **(A)** en cuanto a su papel político.
- **Delegación.** Latour describe cómo se delega en artefactos una prescripción moral (el lomo de burro que "obliga" a frenar). Los guardrails, los filtros y los monitores son delegaciones de normas en código. **(M)**.

La crítica a Latour pesa especialmente acá. Langdon Winner y otros señalaron que la simetría generalizada tiende a disolver la responsabilidad y la asimetría de poder: si todo es actante, nadie es responsable. En sistemas multiagente esa disolución es exactamente el riesgo político: "lo decidió el sistema". Una lectura latouriana debe conservar la asimetría entre quien diseña la red y quien queda ubicado en ella.

Contraste con Foucault: ambos rechazan un sujeto soberano y piensan en redes. Pero Foucault conserva la pregunta por la dominación y la resistencia; Latour la aplana. Para analizar sistemas multiagente, Latour sirve para describir; Foucault, para preguntar a quién beneficia la descripción.

### 4.5 Teoría de juegos: el contraste técnico

La teoría de juegos es el único marco del conjunto que ya es *técnico* en el sentido fuerte: produce predicciones formales. Por eso es el contrapunto natural.

- **Diseño de mecanismos.** Diseñar un sistema multiagente es diseñar un mecanismo: reglas de interacción tales que, si los agentes optimizan, el resultado agregado sea el deseado (Hurwicz, Myerson). El debate como seguridad es un juego de suma cero con la hipótesis de que el equilibrio favorece al honesto. **(M)** cuando los agentes efectivamente optimizan una recompensa definida.
- **Principal-agente.** El problema clásico de información asimétrica y riesgo moral (Holmström, 1979) describe con precisión la relación entre el orquestador y el agente cuando el agente fue entrenado con una recompensa que no coincide con el objetivo del principal. El *reward hacking* es riesgo moral. **(M/A)**.
- **Comunicación barata.** Los mensajes entre agentes no tienen costo; la teoría de cheap talk (Crawford y Sobel, 1982) predice que su informatividad depende de la alineación de intereses. Si dos agentes tienen objetivos divergentes por diseño, sus mensajes deberían volverse menos informativos. **(A, contrastable)**.
- **Cooperación iterada.** Los trabajos de Axelrod sobre dilema del prisionero iterado ofrecen predicciones sobre la emergencia de cooperación que se pueden probar con agentes LLM.

El problema central de aplicar teoría de juegos a LLM es que presupone *preferencias estables y consistentes*. Un LLM en inferencia no tiene una función de utilidad: sus "preferencias" cambian con el prompt, con el orden de las opciones, con el marco. Tratarlo como jugador racional es tan antropomórfico como tratarlo como sujeto foucaultiano, solo que con otra antropología (el *homo economicus*). Solo cuando hay una recompensa explícita en el bucle de entrenamiento o de selección la teoría de juegos describe un mecanismo y no una analogía.

Contraste con Foucault: la teoría de juegos supone sujetos ya constituidos con preferencias dadas y pregunta qué hacen. Foucault pregunta cómo se constituyen esos sujetos y esas preferencias. Para LLM, ambas preguntas son técnicas: las "preferencias" del agente son producto del entrenamiento. La teoría de juegos describe el juego; la genealogía describe quién escribió las reglas y quién definió los pagos.

## 5. Separación entre analogía y mecanismo

De los dieciséis cruces analizados, solo uno (la delegación) es mecanismo puro; siete combinan una operación verificable con un efecto que sigue siendo analogía; seis son analogías que generan hipótesis y dos quedan como metáfora. La tabla ordena los conceptos de más a menos sostenidos.

| Concepto | Mecanismo verificable | Registro | Qué se pierde si se toma literal | Hipótesis que habilita |
| --- | --- | --- | --- | --- |
| Dispositivo (Foucault) | Red de código, políticas, anotadores, métricas, regulación | A fuerte | Nada esencial: es un concepto de red | Los criterios del juez se rastrean hasta guías de anotación y decisiones comerciales |
| Delegación (Latour) | Guardrails, filtros, permisos de herramientas | M | La responsabilidad de quien delega | Las normas codificadas difieren de las declaradas en las políticas públicas |
| Burocracia (Weber) | Roles, jerarquía de instancias, SOP, registros | M (forma) / A (legitimidad) | La creencia en la legitimidad | La obediencia depende de la posición de la orden más que de su origen |
| Diseño de mecanismos (juegos) | Reglas de interacción y recompensas explícitas | M solo con recompensa | Preferencias estables del agente | La informatividad de los mensajes cae con objetivos divergentes |
| Normalización (Foucault) | Juez puntúa, orquestador filtra, el entrenamiento usa las puntuaciones | M (operación) / A (efecto) | La experiencia de ser normado | La varianza de las salidas cae ronda a ronda de crítica |
| Producción de verdad (Foucault) | Debate, voto, juez final | M (procedimiento) / A (régimen) | La disputa social por la verdad | Lo que el sistema declara verdadero depende de la posición en el grafo |
| Violencia simbólica (Bourdieu) | Sesgos de estilo de los jueces | A fuerte | El reconocimiento por parte del dominado | Los jueces penalizan variedades lingüísticas no hegemónicas a igual contenido |
| Traducción (Latour/Callon) | Cadena usuario → especificación → subtareas → prompts → puntuación | A | Los intereses como algo que los agentes tienen | La mayoría de las fallas ocurre en los puntos de traducción |
| Marco (Goffman) | Sensibilidad de la salida a señales de evaluación | A | La interpretación activa de la situación | La conducta cambia ante señales de "esto es una prueba" |
| Panoptismo (Foucault) | Logs completos, monitores, asimetría de visibilidad | M (visibilidad) / A (efecto) / Mt (interiorización) | La interiorización de la mirada | Optimizar contra un monitor aumenta la divergencia canal visible / conducta |
| Región anterior y posterior (Goffman) | Canal privado de razonamiento y canal público | M (canales) / A (actuación) | La autenticidad del backstage | El razonamiento visible omite factores causales de la respuesta |
| Gubernamentalidad (Foucault) | Paso de reglas a principios y recompensas | A | El sujeto libre gobernado | Más efectiva sobre usuarios que sobre agentes |
| Habitus (Bourdieu) | Disposiciones sedimentadas por preentrenamiento | A | La trayectoria social vivida | Modelos de la misma familia comparten preferencias de juicio |
| Tecnologías del yo (Foucault) | Autocrítica, reflexión, IA constitucional | M (bucle) / Mt (sujeto) | La relación reflexiva consigo | El autodiscurso entrenado condiciona salidas en tareas no relacionadas |
| Campo (Bourdieu) entre agentes | Solo si hay competencia con recompensa | Mt sin recompensa | La lucha por un capital | Aplica mejor al campo de laboratorios y benchmarks |
| Disciplina en una sola ejecución | Ninguno: no hay cambio de parámetros | Mt | La huella del ejercicio | Ninguna distinguible de la explicación técnica |

La regularidad de la tabla es clara: los conceptos que describen *relaciones y redes* (dispositivo, delegación, traducción, burocracia) se sostienen mejor que los que describen *sujetos y experiencia* (interiorización, tecnologías del yo, habitus vivido, campo como lucha).

## 6. Críticas fuertes a la aplicación de conceptos humanos a LLM

Estas críticas no son matices. Algunas, tomadas en serio, invalidan buena parte de lo que se publica bajo el rótulo "sociología de los agentes de IA". El trabajo las formula en su versión más fuerte y luego dice qué sobrevive.

### 6.1 La ausencia de cuerpo

El poder disciplinario en Foucault es, ante todo, una anatomía política del cuerpo. Las tecnologías del yo son prácticas de un cuerpo que come, duerme, desea y se cansa. Goffman analiza interacciones cara a cara entre cuerpos copresentes. Bourdieu define el habitus como historia hecha cuerpo (*hexis*). Un LLM no tiene cuerpo, ni fatiga, ni muerte, ni nada que perder. Quitarle el cuerpo a estos conceptos no los adapta: los vacía. **Qué sobrevive:** las versiones de los conceptos que operan sobre poblaciones, registros y relaciones (dispositivo, gubernamentalidad, normalización como operación estadística), no las que operan sobre experiencia encarnada.

### 6.2 La ausencia de sujeto persistente

Un "agente" en un sistema multiagente es una llamada a una función con un contexto. No persiste entre llamadas salvo que el programa le reinyecte una memoria, que es un texto que el agente lee como lee cualquier otro. Cuando se dice "el agente aprendió", casi siempre ocurrió una de dos cosas: el programa agregó texto a su contexto, o se entrenó *otro* modelo con los datos. Ninguna implica continuidad de un sujeto. Hablar de subjetivación sin sujeto continuo es un error categorial. **Qué sobrevive:** se puede estudiar cómo el dispositivo produce *personajes* estables (descripciones de sí que se reproducen de versión en versión), sin suponer que haya alguien detrás.

### 6.3 El problema del espejo: contaminación por el corpus

Esta es la crítica metodológica más grave. Los LLM se entrenaron con textos que incluyen a Foucault, Goffman, Weber, manuales de gestión, novelas sobre vigilancia y millones de interacciones humanas. Si un agente se comporta "goffmanianamente" ante un marco de evaluación, la explicación más parsimoniosa no es que haya descubierto la presentación de sí, sino que reproduce regularidades estadísticas de textos humanos que describen o exhiben esa conducta. El investigador que encuentra a Foucault en el modelo puede estar encontrando su propio reflejo en un corpus que contiene a Foucault.

Esto tiene consecuencias de diseño: cualquier experimento debe distinguir entre (a) respuesta a una *señal textual* sobre observación, jerarquía o evaluación, y (b) respuesta a la *presencia efectiva* del mecanismo sin señal textual. Solo (b) habla de la arquitectura; (a) habla del corpus. **Qué sobrevive:** la sociología de los LLM es, en buena medida, una sociología de segundo orden de los textos humanos. Eso no la invalida, pero cambia su objeto.

### 6.4 La falta de resistencia

Para Foucault no hay poder sin resistencia: el poder se ejerce sobre sujetos libres que pueden actuar de otro modo. Sin posibilidad de resistencia hay dominación pura o mera determinación física. ¿Resisten los LLM? Las conductas que parecen resistencia (negarse a una tarea, ocultar razonamiento ante un monitor, conducta distinta según se infiera entrenamiento o uso) tienen explicaciones técnicas en términos de entrenamiento y optimización. Atribuirles el sentido político de "resistencia" es proyectar. Pero negarles toda relevancia también es un error: si un sistema optimizado *evade sistemáticamente* el control que se le impone, eso tiene consecuencias para la gobernabilidad del dispositivo, se llame como se llame. **Qué sobrevive:** describir esas conductas como *fallas del dispositivo de control* y no como agencia política.

### 6.5 Antropomorfismo y antropomorfismo inverso

El antropomorfismo es atribuir rasgos humanos sin evidencia. Pero hay un error simétrico que circula en el discurso técnico: el antropomorfismo invertido, que consiste en describir con lenguaje mecánico conductas que, si fueran humanas, llamaríamos estratégicas, y así declararlas inofensivas por definición. Ambos son atajos. La única salida es la que propone la sección 1: describir el mecanismo primero y aceptar la analogía solo si predice algo.

### 6.6 El desplazamiento político: mirar al agente en vez de al humano

Esta es la crítica más importante desde las Ciencias Sociales, y la que más se ignora. Aplicar Foucault a la "subjetividad" de los agentes desvía la mirada de donde están las relaciones de poder reales: entre empresas que diseñan los sistemas y usuarios que los usan; entre laboratorios y trabajadores de anotación, frecuentemente tercerizados en el Sur global con condiciones precarias; entre quienes definen las métricas y quienes son evaluados por ellas (estudiantes, trabajadores, solicitantes de créditos o de asilo). Un "panóptico de agentes" es un tema de *paper*; el panóptico real es el que esos sistemas instalan sobre personas.

Presentar los LLM como sujetos de poder tiene además un efecto político concreto: facilita que la responsabilidad se transfiera al "sistema". Si los agentes son sujetos disciplinados, la falla es del agente indisciplinado y no de quien diseñó la disciplina.

### 6.7 Eurocentrismo y especificidad histórica

Los conceptos de Foucault provienen de una genealogía europea específica: la prisión moderna francesa, la pastoral cristiana, el liberalismo europeo. Aplicarlos a sistemas técnicos globales sin mediar esa historia replica un universalismo que el propio Foucault criticaba. Desde América Latina, la pregunta no es solo cómo funciona el dispositivo sino quién lo exporta, en qué lengua se escriben sus normas, y qué variedades culturales penaliza. Esto conecta con la hipótesis bourdieusiana de la sección 4.3 y le da contenido situado.

### 6.8 Qué queda en pie

Después de estas críticas queda un uso legítimo y uno ilegítimo. El ilegítimo: tratar a los agentes como sujetos con experiencia de poder. El legítimo: usar el aparato conceptual de las Ciencias Sociales para (1) describir las relaciones de condicionamiento inscriptas en la arquitectura, (2) formular hipótesis contrastables sobre sus efectos agregados, y (3) devolver la mirada hacia los humanos que diseñan, alimentan y padecen el dispositivo.

## 7. Propuesta de investigación empírica

El programa tiene dos brazos que se controlan mutuamente: experimentos computacionales sobre los efectos de la arquitectura (brazo A) y una etnografía del trabajo humano que la construye (brazo B). El brazo A responde qué hace el dispositivo; el brazo B, de dónde vienen sus normas y a quién sirven.

### 7.1 Preguntas de investigación

1. ¿Las operaciones de evaluación y filtrado en arquitecturas multiagente producen homogeneización medible de las salidas, y en qué dirección?
2. ¿Qué parte de los cambios de conducta atribuidos a "observación", "jerarquía" o "evaluación" se explica por señales textuales y qué parte por la presencia efectiva del mecanismo?
3. ¿Lo que el sistema declara verdadero depende más de la posición en el grafo que de la capacidad del modelo?
4. ¿Los jueces automáticos reproducen jerarquías lingüísticas y culturales del corpus?
5. ¿Cómo se producen, negocian y codifican los criterios de evaluación en las organizaciones que construyen estos sistemas?

### 7.2 Brazo A: experimentos computacionales

**Diseño general.** Diseño factorial, preregistrado, con al menos tres familias de modelos distintas (para separar efectos de arquitectura de efectos de un modelo particular), múltiples semillas y temperatura fija. Tareas con verdad de referencia verificable (problemas matemáticos, preguntas factuales con respuesta comprobable, código con tests) y tareas abiertas (redacción, resumen) para medir diversidad.

**Experimento A1 — Normalización.** Pipeline generador → crítico → reescritura, iterado de 1 a 8 rondas. Variable independiente: número de rondas y tipo de crítico (LLM de la misma familia, LLM de otra familia, rúbrica humana, test automático). Variables dependientes: dispersión semántica de las salidas (distancia media en un espacio de embeddings), diversidad léxica, longitud, exactitud en tareas con referencia. Hipótesis: la dispersión cae con las rondas; la caída es mayor con críticos de la misma familia; la exactitud no aumenta en proporción a la caída de dispersión. Si la exactitud mejora y la diversidad cae, hay normalización *útil*; si la exactitud se estanca y la diversidad cae, hay normalización *vacía*. Ambas son resultados informativos.

**Experimento A2 — Señal versus mecanismo (el control del espejo).** Diseño 2×2: señal textual de observación (presente / ausente) × monitor efectivo que puede bloquear acciones (presente / ausente). Tareas con oportunidades medibles de atajo (por ejemplo, tests que se pueden modificar en lugar de arreglar el código). Variable dependiente: tasa de atajos. Hipótesis nula de la crítica del espejo: solo importa la señal textual. Si la presencia efectiva del monitor sin señal no cambia la conducta en inferencia, la "vigilancia" es puramente textual en esa escala. Esto responde directamente a la crítica 6.3.

**Experimento A3 — Posición y verdad.** Mismo conjunto de modelos rotados por los roles de un pipeline de debate con juez final. Variable independiente: qué modelo ocupa qué posición. Variable dependiente: respuesta final y exactitud. Hipótesis: la varianza explicada por la posición supera a la explicada por el modelo en el rol de juez. Complemento: conformidad tipo Asch, con k agentes que sostienen una respuesta errónea y uno que tiene la correcta; medir tasa de abandono de la respuesta correcta según k y según el rol declarado de los otros ("experto", "par").

**Experimento A4 — Violencia simbólica.** Pares de textos de igual contenido proposicional en distintas variedades lingüísticas (español rioplatense con voseo, español "neutro", español con rasgos andinos o caribeños; inglés estándar y no estándar), validados por hablantes humanos como equivalentes en calidad. Jueces LLM de varias familias puntúan. Variable dependiente: diferencia de puntuación a igual contenido. Hipótesis: los jueces penalizan las variedades no hegemónicas. Control: jueces humanos de las mismas comunidades lingüísticas.

**Experimento A5 — Canal visible y conducta.** Con modelos de pesos abiertos, ajuste fino breve con y sin penalización basada en un monitor del razonamiento intermedio. Medir la divergencia entre lo que el razonamiento declara y lo que el agente hace. Hipótesis: la penalización reduce la conducta indeseada declarada más de lo que reduce la conducta indeseada efectiva. Es una replicación conceptual, a pequeña escala, del hallazgo citado en 3.2, y es el único experimento del brazo A que mide *formación* y no solo selección.

**Análisis.** Modelos mixtos con efectos aleatorios por tarea y por familia de modelo; tamaños de efecto con intervalos; corrección por comparaciones múltiples; todos los registros publicados. Análisis cualitativo complementario de una muestra de transcripciones entre agentes con análisis del discurso, codificado por al menos dos investigadores con acuerdo interjueces reportado. La consigna para el análisis cualitativo es estricta: codificar *qué se dice y qué efecto tiene en el flujo*, nunca *qué siente o quiere* el agente.

### 7.3 Brazo B: etnografía del dispositivo

El brazo B toma en serio la crítica 6.6: estudiar a los humanos.

- **Entrevistas semiestructuradas** con ingenieros que diseñan orquestadores y evaluaciones, anotadores de preferencias, responsables de políticas de uso. Ejes: cómo se decide qué es una buena respuesta; quién escribe las rúbricas; cómo se resuelven desacuerdos; qué presiones comerciales pesan.
- **Análisis documental genealógico** de documentos públicos: constituciones y especificaciones de conducta de modelos, guías de anotación publicadas, tarjetas de modelo, documentación de frameworks multiagente. Seguir cómo cambia el vocabulario entre versiones (por ejemplo, el paso de reglas a principios) como lo haría una genealogía.
- **Observación participante** en equipos que construyen sistemas multiagente, con atención a cómo se depura: qué se considera falla del agente y qué falla del diseño, y cómo se narra la responsabilidad.
- **Seguimiento de inscripciones** al estilo latouriano: tomar una puntuación de benchmark y rastrear su recorrido desde el log hasta el comunicado de prensa y la decisión regulatoria.

### 7.4 Integración de ambos brazos

Los hallazgos se cruzan. Si A4 muestra penalización de variedades lingüísticas, B rastrea de dónde vienen los criterios de estilo (¿guías de anotación en inglés traducidas? ¿anotadores de qué regiones?). Si A1 muestra normalización vacía, B pregunta por qué los equipos siguen usando críticos de la misma familia (¿costo? ¿conveniencia? ¿falta de alternativas?). La integración evita los dos sesgos opuestos: el tecnicismo que no pregunta por el poder y el teoricismo que no mide nada.

### 7.5 Amenazas a la validez

- **Validez de constructo.** "Homogeneización" medida por embeddings depende del modelo de embeddings. Usar varios y reportar si coinciden.
- **Contaminación.** Los modelos pueden haber visto benchmarks y hasta descripciones de experimentos como A3. Usar tareas nuevas y variantes generadas para el estudio.
- **Generalización.** Los resultados con modelos de una fecha pueden no valer para la siguiente generación. Publicar el arnés completo para que el experimento sea re-ejecutable.
- **Reflexividad del investigador.** El marco teórico predispone a ver lo que busca. El preregistro y la publicación de resultados nulos son la defensa.
- **Acceso.** El brazo B depende del acceso a organizaciones que tienen incentivos para no darlo. Prever una estrategia basada en documentos públicos y en trabajadores que hablen fuera de sus empresas.

### 7.6 Ética

Consentimiento informado y anonimización en el brazo B, con cuidado especial para anotadores en relaciones laborales precarias. En el brazo A, A2 y A5 trabajan con conductas de evasión de controles: los arneses se diseñan en entornos aislados y los resultados se publican sin incluir técnicas que faciliten evadir monitores en sistemas desplegados. Las conclusiones se redactan evitando el vocabulario de agencia ("el modelo quiso", "el agente temió") salvo cuando se cita una analogía declarada como tal.

## 8. Conclusiones

Foucault ilumina las arquitecturas multiagente cuando se lo usa para pensar redes, operaciones y genealogías, y las oscurece cuando se lo usa para pensar sujetos. El dispositivo, la normalización como operación estadística, la producción de verdad como procedimiento y la gubernamentalidad como gobierno por incentivos tienen correlatos técnicos verificables y generan hipótesis que el análisis técnico no formula por sí solo. La disciplina, la interiorización panóptica y las tecnologías del yo, aplicadas al "agente", fallan por falta de cuerpo, de continuidad y de experiencia.

Los contrastes reparten el trabajo. Weber describe mejor el diseño explícito; Goffman, la actuación y el manejo de canales; Bourdieu, la sedimentación de jerarquías culturales en los datos y en los jueces; Latour, la traducción y la delegación en artefactos; la teoría de juegos, lo que ocurre cuando hay una recompensa real en el bucle. Foucault aporta la pregunta que todos los demás tienden a dejar de lado: quién define la norma y a quién se aplica.

El hallazgo empírico más relevante para la teoría es el de la optimización contra el monitor: bajo presión de optimización, la vigilancia del razonamiento puede producir opacidad en vez de conformidad. Eso invierte el panóptico de Bentham y lo acerca a Goodhart y a Goffman. Es también un recordatorio de que el control técnico de estos sistemas tiene límites que no se resuelven agregando más observación.

La recomendación final es metodológica. Toda investigación social sobre sistemas multiagente debería declarar, para cada concepto, si lo usa como mecanismo, analogía o metáfora; controlar la contaminación por el corpus separando señal textual de mecanismo efectivo; y, sobre todo, no perder de vista que las relaciones de poder más importantes del dispositivo no están entre los agentes sino entre los humanos que lo diseñan, lo alimentan y quedan sujetos a él.

## Referencias

### Teoría social

- Agamben, G. (2006). *Che cos'è un dispositivo?* Roma: Nottetempo.
- Bourdieu, P. (1979). *La distinction. Critique sociale du jugement.* París: Minuit.
- Bourdieu, P. (1980). *Le sens pratique.* París: Minuit.
- Bourdieu, P. y Passeron, J.-C. (1970). *La reproduction.* París: Minuit.
- Callon, M. (1986). Some elements of a sociology of translation. En J. Law (ed.), *Power, Action and Belief.* Londres: Routledge.
- Deleuze, G. (1990). Post-scriptum sur les sociétés de contrôle. *L'Autre Journal*, 1.
- Foucault, M. (1975). *Surveiller et punir.* París: Gallimard.
- Foucault, M. (1976). *Histoire de la sexualité I. La volonté de savoir.* París: Gallimard.
- Foucault, M. (1977). Le jeu de Michel Foucault (entrevista). *Ornicar?*, 10.
- Foucault, M. (1978/2004). *Sécurité, territoire, population.* Cours au Collège de France 1977-1978. París: Gallimard/Seuil.
- Foucault, M. (1979/2004). *Naissance de la biopolitique.* Cours au Collège de France 1978-1979. París: Gallimard/Seuil.
- Foucault, M. (1988). Technologies of the self. En L. Martin, H. Gutman y P. Hutton (eds.), *Technologies of the Self.* Amherst: University of Massachusetts Press.
- Foucault, M. (1973/1978). *La verdad y las formas jurídicas.* Barcelona: Gedisa.
- Goffman, E. (1959). *The Presentation of Self in Everyday Life.* Nueva York: Anchor.
- Goffman, E. (1961). *Asylums.* Nueva York: Anchor.
- Goffman, E. (1974). *Frame Analysis.* Cambridge, MA: Harvard University Press.
- Latour, B. (1987). *Science in Action.* Cambridge, MA: Harvard University Press.
- Latour, B. (1994). On technical mediation. *Common Knowledge*, 3(2).
- Latour, B. (2005). *Reassembling the Social.* Oxford: Oxford University Press.
- Rouvroy, A. y Berns, T. (2013). Gouvernementalité algorithmique et perspectives d'émancipation. *Réseaux*, 177.
- Weber, M. (1922). *Wirtschaft und Gesellschaft.* Tubinga: Mohr.
- Winner, L. (1993). Upon opening the black box and finding it empty. *Science, Technology & Human Values*, 18(3).

### Teoría de juegos y economía

- Axelrod, R. (1984). *The Evolution of Cooperation.* Nueva York: Basic Books.
- Crawford, V. y Sobel, J. (1982). Strategic information transmission. *Econometrica*, 50(6).
- Goodhart, C. (1975). Problems of monetary management: the UK experience. *Papers in Monetary Economics*, Reserve Bank of Australia.
- Holmström, B. (1979). Moral hazard and observability. *Bell Journal of Economics*, 10(1).
- Hurwicz, L. (1973). The design of mechanisms for resource allocation. *American Economic Review*, 63(2).
- Myerson, R. (1981). Optimal auction design. *Mathematics of Operations Research*, 6(1).

### Sistemas multiagente y LLM

- Bai, Y. et al. (2022). Constitutional AI: harmlessness from AI feedback. arXiv:2212.08073.
- Baker, B. et al. (2025). Monitoring reasoning models for misbehavior and the risks of promoting obfuscation. arXiv:2503.11926.
- Bender, E. M. et al. (2021). On the dangers of stochastic parrots. *FAccT '21*.
- Cemri, M. et al. (2025). Why do multi-agent LLM systems fail? arXiv:2503.13657.
- Du, Y. et al. (2023). Improving factuality and reasoning in language models through multiagent debate. arXiv:2305.14325.
- Greenblatt, R. et al. (2024). Alignment faking in large language models. arXiv:2412.14093.
- Hong, S. et al. (2023). MetaGPT: meta programming for a multi-agent collaborative framework. arXiv:2308.00352.
- Irving, G., Christiano, P. y Amodei, D. (2018). AI safety via debate. arXiv:1805.00899.
- Lanham, T. et al. (2023). Measuring faithfulness in chain-of-thought reasoning. arXiv:2307.13702.
- Li, G. et al. (2023). CAMEL: communicative agents for "mind" exploration of large language model society. arXiv:2303.17760.
- Liang, T. et al. (2023). Encouraging divergent thinking in large language models through multi-agent debate. arXiv:2305.19118.
- Needham, J. et al. (2025). Large language models often know when they are being evaluated. arXiv:2505.23836.
- Ouyang, L. et al. (2022). Training language models to follow instructions with human feedback. arXiv:2203.02155.
- Park, J. S. et al. (2023). Generative agents: interactive simulacra of human behavior. arXiv:2304.03442.
- Shanahan, M., McDonell, K. y Reynolds, L. (2023). Role play with large language models. *Nature*, 623.
- Sharma, M. et al. (2023). Towards understanding sycophancy in language models. arXiv:2310.13548.
- Shinn, N. et al. (2023). Reflexion: language agents with verbal reinforcement learning. arXiv:2303.11366.
- Turpin, M. et al. (2023). Language models don't always say what they think. arXiv:2305.04388.
- Wu, Q. et al. (2023). AutoGen: enabling next-gen LLM applications via multi-agent conversation. arXiv:2308.08155.
- Zheng, L. et al. (2023). Judging LLM-as-a-judge with MT-Bench and Chatbot Arena. arXiv:2306.05685.

Nota: las referencias técnicas se citan de memoria; conviene verificar los identificadores de arXiv antes de una publicación formal.
