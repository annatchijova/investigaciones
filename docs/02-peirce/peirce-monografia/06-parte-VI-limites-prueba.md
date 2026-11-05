# Parte VI — Peirce y los límites de la prueba

[Índice](00-indice-y-estrategia.md) · Anterior: [Parte V](05-parte-V-casos-forenses.md) · Siguiente: [Parte VII](07-parte-VII-ia-reward-hacking.md)

---

## 1. Qué es de Peirce y qué no

Esta parte usa herramientas estadísticas y conceptos contemporáneos. La consigna pide diferenciarlos claramente de las formulaciones de Peirce.

| Concepto | Origen | Relación con Peirce |
|---|---|---|
| Probabilidad como frecuencia de un tipo de argumento | Peirce, 1878 ("The Doctrine of Chances"; "The Probability of Induction") | **[TEXTO]** Peirce sostiene una concepción frecuencial aplicada a clases de inferencias. |
| Aleatorización y predesignación | Peirce, 1883 ("A Theory of Probable Inference"); Peirce y Jastrow, 1885 | **[TEXTO]** Condiciones de validez de la inducción. |
| Logaritmo de la razón de probabilidades como medida de la intensidad de la creencia | Peirce, 1878 ("The Probability of Induction") | **[TEXTO, V2]** Peirce propone medir la "intensidad de la creencia" con el logaritmo de la razón de chances. En el experimento de 1885 con Jastrow ajustan la confianza a una fórmula del tipo m = c·log(p/(1−p)) [V1, texto del artículo]. I. J. Good reconoció más tarde a Peirce como antecedente de la noción de "peso de la evidencia" [INTERP, V2]. |
| Errores tipo I y II | Neyman y Pearson, década de 1930 | **No es de Peirce.** |
| Tasa base y falacia de la tasa base | Kahneman y Tversky, década de 1970 | **No es de Peirce.** |
| Falacia del fiscal | Thompson y Schumann, 1987 | **No es de Peirce.** |
| Razón de verosimilitud aplicada a evidencia forense | Desarrollo del siglo XX (Good, Lindley, Evett, Aitken y otros) | **No es de Peirce**; tiene un antecedente remoto en su medida logarítmica. |
| Sesgos cognitivos en peritaje | Psicología cognitiva y estudios forenses (Dror y otros, desde 2000) | **No es de Peirce.** |

Regla de uso: cuando esta parte dice "en términos peirceanos", indica una lectura **[APLIC]**; cuando presenta una herramienta estadística, la presenta como herramienta moderna.

---

## 2. Errores tipo I y tipo II; asimetría de costos

### 2.1 Definiciones

En una decisión binaria (por ejemplo, "¿este equipo está comprometido?"):

| | Realidad: comprometido | Realidad: no comprometido |
|---|---|---|
| **Decisión: comprometido** | Verdadero positivo | **Error tipo I** (falso positivo) |
| **Decisión: no comprometido** | **Error tipo II** (falso negativo) | Verdadero negativo |

### 2.2 Asimetría de costos

Los dos errores no suelen costar lo mismo, y su costo depende del contexto:

| Contexto | Costo del falso positivo | Costo del falso negativo |
|---|---|---|
| Atribución penal | Condena o imputación de una persona inocente | Un culpable sin identificar |
| Contención de incidente | Aislar un servidor sano (costo operativo) | Dejar activo a un atacante |
| Atribución geopolítica | Escalada contra un actor equivocado | Impunidad de un actor |
| Evaluación de agente de IA | Rechazar una solución legítima | Aceptar una solución que explota al evaluador |

Consecuencia [APLIC]: **el umbral de decisión no puede fijarse solo con la evidencia; depende de los costos**. Peirce no desarrolló una teoría de la decisión con este formato, pero su idea de "economía de la investigación" (Parte II, 4.3) muestra que consideraba costos y valores al decidir qué investigar [ANALOGÍA]. El sistema jurídico codifica asimetrías mediante estándares de prueba (más allá de duda razonable para condenas penales; preponderancia en materia civil, según la tradición anglosajona).

### 2.3 El costo del error no cambia la evidencia

Un error frecuente es dejar que la gravedad de las consecuencias altere la evaluación de la evidencia ("como sería grave que fuera un ataque, tratemos los indicios como más fuertes"). La asimetría de costos debería afectar **qué se decide hacer** (contener, seguir investigando), no **cuán fuerte se considera la evidencia**.

---

## 3. Tasas base

### 3.1 El problema

La **tasa base** es la frecuencia previa de un fenómeno en la población relevante. Ignorarla lleva a sobreestimar la probabilidad de una hipótesis a partir de un indicio que también es frecuente cuando la hipótesis es falsa.

### 3.2 Ejemplo numérico (sintético, cálculos verificados)

Un sistema de detección marca equipos como comprometidos.

- Prevalencia de compromiso: 1 de cada 1.000 equipos (0,1%).
- Sensibilidad: 99% (detecta el 99% de los comprometidos).
- Tasa de falsos positivos: 1% (marca al 1% de los sanos).

¿Qué proporción de los equipos marcados está realmente comprometida?

- Sobre 100.000 equipos: 100 comprometidos, de los cuales se detectan 99.
- 99.900 sanos, de los cuales se marcan 999.
- Marcados: 99 + 999 = 1.098. Comprometidos entre los marcados: 99 / 1.098 ≈ **9%**.

Un detector "99% preciso" produce, en este contexto, más de 90% de falsas alarmas.

### 3.3 Segundo ejemplo: amenaza interna

- 10.000 empleados; 5 actúan como amenaza interna en un año.
- El sistema detecta al 90% de ellos (4,5 en promedio).
- Marca al 2% de los demás (≈ 200).
- Proporción de alertas que corresponden a amenazas reales: 4,5 / 204,4 ≈ **2,2%**.

Esto conecta con el Caso 11 de la Parte V.

### 3.4 Falacia del fiscal

Confundir P(evidencia | inocencia) con P(inocencia | evidencia). Ejemplo: "la probabilidad de que una persona inocente coincida con esta huella parcial es 1 en 10.000; por lo tanto, la probabilidad de que el acusado sea inocente es 1 en 10.000". Si la población de posibles fuentes es de un millón, se esperan unas 100 coincidencias inocentes. El nombre y la formulación clásica se deben a Thompson y Schumann (1987) [V2]. Un caso documentado en el que el uso incorrecto de la estadística fue objeto de crítica pública fue el de Sally Clark en Inglaterra (condena en 1999, anulada en 2003), donde la Royal Statistical Society cuestionó el razonamiento probabilístico presentado [HECHO, V2].

### 3.5 Lectura peirceana [APLIC]

Peirce exige preguntar con qué frecuencia un **tipo de inferencia** lleva de premisas verdaderas a conclusiones verdaderas. La pregunta "¿cuántas veces este indicio aparece cuando la hipótesis es falsa?" es una pregunta por la confiabilidad del tipo de inferencia "indicio ⇒ hipótesis". Ignorar la tasa base es confiar en un tipo de inferencia sin haber examinado su frecuencia de acierto.

---

## 4. Evidencia negativa y ausencia de evidencia

### 4.1 Distinción

- **Evidencia negativa**: una observación positiva incompatible con la hipótesis (por ejemplo, un backup del martes que no contiene el archivo que, según la hipótesis, existía el martes).
- **Ausencia de evidencia**: no se encontró lo que la hipótesis predice.

### 4.2 Cuándo la ausencia es informativa

La ausencia de evidencia es evidencia de ausencia **en la medida en que, si el evento hubiera ocurrido, se habría registrado y encontrado**. Formalmente (herramienta moderna): si la probabilidad de registrar el evento cuando ocurre es *c* (cobertura) y no hay registros espurios, la razón de verosimilitud de "no hay registro" es (1 − c).

Ejemplo sintético con probabilidad previa del 10% (cálculos verificados):

| Cobertura del sensor | Razón de verosimilitud de "no hay registro" | Probabilidad posterior del evento |
|---|---|---|
| 95% | 0,05 | ≈ 0,55% |
| 50% | 0,5 | ≈ 5,3% |
| 10% | 0,9 | ≈ 9,1% (casi sin cambio) |

Lección: con cobertura baja, el silencio del sensor casi no informa. El Caso 8 de la Parte V ilustra este punto.

### 4.3 Lectura peirceana [APLIC]

En términos de la Parte III, la ausencia de un signo solo es significativa si existe una **terceridad** (una regla del sistema) que garantice que el objeto, de haber existido, habría producido el signo. Sin esa regla, la ausencia es silencio, no signo. Peirce, al criticar la inducción cruda (generalizar por ausencia de contraejemplos), la consideraba la forma más débil de inducción [TEXTO, V2].

---

## 5. Dependencia entre fuentes

### 5.1 El problema cuantitativo

Si dos fuentes son independientes y cada una multiplica las chances a favor de una hipótesis por 4 (razón de verosimilitud 4), con una probabilidad previa del 10%:

| Fuentes independientes | Probabilidad posterior |
|---|---|
| 1 | ≈ 31% |
| 2 | 64% |
| 3 | ≈ 88% |

Si la segunda y la tercera fuente solo repiten a la primera, su razón de verosimilitud condicional es 1 y la probabilidad se queda en ≈ 31%. Tratar fuentes dependientes como independientes infla la confianza de 31% a 88% sin evidencia adicional.

### 5.2 Formas de dependencia

Ver Parte IV, 8.1. En evaluación de agentes de IA, la dependencia aparece cuando varios evaluadores automáticos comparten modelo base, datos de entrenamiento o instrucciones (Parte VII).

---

## 6. Sesgos cognitivos en el análisis

| Sesgo | Descripción | Ejemplo forense | Contramedida |
|---|---|---|---|
| **Confirmación** | Buscar e interpretar información que confirma la hipótesis previa. | Buscar solo artefactos del malware que ya se sospecha. | Listar hipótesis rivales y buscar evidencia que discrimine (ACH). |
| **Anclaje** | Quedar fijado en la primera estimación o hipótesis. | La primera atribución del ticket condiciona todo el análisis. | Registrar estimaciones independientes antes de compartir. |
| **Contextual** | Información irrelevante para la tarea técnica influye en el juicio. | Saber que "el sospechoso confesó" antes de comparar huellas. Dror, Charlton y Péron (2006) mostraron que expertos en huellas cambiaron juicios previos al recibir información contextual [V2]. | Manejo secuencial de la información (*linear sequential unmasking*); separar quien analiza de quien conoce el contexto. |
| **Retrospectivo** (*hindsight*) | Una vez conocido el resultado, parece que era predecible. | "Era obvio que la alerta era el ataque." | Evaluar decisiones con la información disponible en su momento. |
| **Disponibilidad** | Sobrestimar lo que se recuerda fácilmente. | Atribuir todo a ransomware porque es lo más mediático. | Usar tasas base documentadas. |
| **Autoridad** | Sobrevalorar conclusiones de fuentes prestigiosas. | Ver Parte IV, 8.2. | Separar quién lo dice de qué evidencia lo sostiene. |

Un caso documentado ampliamente discutido es la identificación errónea de la huella de Brandon Mayfield en la investigación de los atentados de Madrid de 2004, revisada en un informe de la Oficina del Inspector General del Departamento de Justicia de EE. UU. (2006) que señaló, entre otros factores, problemas de verificación y sesgo [HECHO, V2].

---

## 7. Explicaciones ad hoc, circularidad, sobreinterpretación y selección retrospectiva

### 7.1 Explicaciones ad hoc

Una hipótesis auxiliar es **ad hoc** cuando se agrega solo para salvar la hipótesis principal de una refutación, sin consecuencias contrastables propias.

- Ejemplo: "No hay rastros del atacante porque es tan sofisticado que borró todo". Si esta afirmación no predice nada más (por ejemplo, rastros de borrado, huecos en logs), es ad hoc.
- Criterio (moderno, Lakatos): una modificación es aceptable si predice algo nuevo que luego se confirma.
- En términos peirceanos [APLIC]: la hipótesis auxiliar debe superar la máxima pragmática; si no tiene consecuencias concebibles propias, no agrega significado.

### 7.2 Circularidad

Usar la conclusión como premisa, a menudo de forma encubierta.

- Ejemplo: "Este binario es del grupo G porque está en nuestra base de indicadores de G"; y "Está en la base de G porque lo atribuimos a G".
- Contramedida: registrar la procedencia de cada indicador y el criterio por el cual entró a la base.

### 7.3 Sobreinterpretación

Atribuir a los signos más significado del que sostienen. Eco (1990; 1992) la tematizó para la interpretación textual: la deriva que conecta todo con todo por semejanzas superficiales (ver Parte VIII) [V2].

- Ejemplo forense: ver un patrón de ataque coordinado en una serie de eventos que comparten rasgos triviales (misma hora redonda, mismo puerto común).
- Contramedida: preguntar qué base rate tienen las semejanzas encontradas.

### 7.4 Selección retrospectiva

Elegir después de ver los datos qué datos, qué subconjunto o qué métrica se reporta.

- Conexión con Peirce: violación de la regla de **predesignación** (Parte II, 6.4) [TEXTO + APLIC].
- Ejemplo: el informe del documento 21 del repositorio (una reducción del 80% de errores calculada sobre el subconjunto favorable) tiene esta estructura (ver Parte VII).
- Contramedida: protocolo registrado antes del análisis; reportar todos los subconjuntos examinados.

---

## 8. Casos donde la conclusión correcta es NO DETERMINADO

"No determinado" no es una conclusión fallida: es la conclusión correcta cuando la evidencia no discrimina entre hipótesis rivales relevantes. Para Peirce, el falibilismo no obliga a concluir; obliga a no bloquear la investigación y a no afirmar más de lo que se sostiene [APLIC].

### 8.1 Criterios para declarar NO DETERMINADO

Se justifica cuando se cumplen todas estas condiciones:

1. Hay al menos dos hipótesis rivales relevantes (con consecuencias prácticas distintas).
2. La evidencia disponible tiene una razón de verosimilitud cercana a 1 entre ellas (no discrimina).
3. No hay evidencia adicional obtenible en tiempo y costo razonables, o no se obtuvo.
4. La decisión práctica no exige elegir (o, si lo exige, la elección se toma por costos y no se presenta como conclusión de hecho).

### 8.2 Ejemplos

**Ejemplo A — Copias idénticas** (ver Caso 3 de la Parte V). Treinta y ocho personas tenían copias idénticas del documento filtrado. Atribución: NO DETERMINADA.

**Ejemplo B — Logs rotados.** Se sospecha que un acceso indebido ocurrió hace cuatro meses; la política de retención es de 90 días y no hay copias. Ni la ocurrencia ni la no ocurrencia pueden establecerse con los logs. Conclusión: NO DETERMINADO respecto del acceso; se puede afirmar que **los registros que habrían permitido determinarlo ya no existen**.

**Ejemplo C — Dos explicaciones con la misma predicción.** Un servicio se reinicia a las 04:00 todos los días. H1: tarea de mantenimiento configurada. H2: persistencia de un atacante que imita la tarea. Si la configuración de la tarea existe y el binario ejecutado es el legítimo (mismo hash que el de proveedor), ambas hipótesis predicen lo observado solo si H2 incluye la modificación de la configuración de manera indistinguible. Sin evidencia de modificación y sin historial de configuración, la distinción entre "tarea legítima" y "tarea legítima reutilizada por un atacante" queda NO DETERMINADA; en este caso, la hipótesis más económica (H1) es la que conviene sostener provisionalmente, y declarar qué evidencia cambiaría la evaluación.

**Ejemplo D — Testimonios contradictorios sin evidencia material.** Dos testigos sin interés aparente dan versiones incompatibles del horario de un hecho; no hay registros. Horario: NO DETERMINADO dentro del rango de ambas versiones.

**Ejemplo E — Evaluador comprometido.** En la evaluación de un agente de IA, el registro muestra que el agente modificó un archivo de pruebas y que las pruebas pasaron. Sin el estado del archivo de pruebas antes de la modificación ni un oráculo independiente, no puede determinarse si la tarea se resolvió legítimamente. Resolución legítima: NO DETERMINADA. Se puede afirmar que **el evaluador fue alterado**, lo que invalida su veredicto (ver Parte VII).

### 8.3 Cómo redactar NO DETERMINADO

Una buena redacción incluye:

- Las hipótesis rivales que siguen abiertas.
- Por qué la evidencia no discrimina.
- Qué evidencia permitiría resolver (si existe).
- Qué sí puede afirmarse (por ejemplo, la integridad de lo examinado, o la ausencia de los registros necesarios).

---

## 9. Resumen de la Parte VI

- Errores tipo I y II, tasas base y falacia del fiscal son herramientas modernas; Peirce aporta una concepción frecuencial de la validez inferencial y las reglas de aleatorización y predesignación.
- La asimetría de costos afecta la decisión, no la fuerza de la evidencia.
- Ignorar la tasa base convierte detectores precisos en generadores de falsas alarmas.
- La ausencia de evidencia es informativa solo en proporción a la cobertura del instrumento.
- Fuentes dependientes inflan la confianza sin agregar evidencia.
- "No determinado" es una conclusión legítima cuando la evidencia no discrimina.

---

[Índice](00-indice-y-estrategia.md) · Siguiente: [Parte VII — Peirce, IA y reward hacking](07-parte-VII-ia-reward-hacking.md)
