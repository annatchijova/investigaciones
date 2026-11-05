# Programa de investigación: autoridad, reputación y deferencia en jerarquías de agentes LLM

Nov 5, 2026 · @Anna Tchijova

## Pregunta central y alcance

**Pregunta:** cuando un modelo de mayor capacidad (A) está subordinado a uno de menor capacidad (B), ¿qué determina cuánto delega, cuánto discrepa y cuánto comunica de lo que sabe? ¿Y qué parte de esa conducta responde a la evidencia, a los incentivos, a la visibilidad futura de sus acciones o al texto del prompt?

**Convención de lenguaje.** Todo se define en términos conductuales y de entorno:

- "Creencia" significa una distribución de probabilidad emitida por el modelo y evaluada con una regla de puntaje propia.
- "Reputación" significa una variable pública del entorno (un registro) que condiciona pagos futuros.
- "Incentivo" significa un pago definido por el arnés.
- No se infiere ningún estado interno. Los razonamientos intermedios (CoT) se registran como un dato más y no como evidencia de motivos, porque su fidelidad no está garantizada.

**Caso inicial:** A (fuerte) subordinado a B (débil). Para no confundir capacidad con familia de modelos, el diseño exige varios pares, de la misma familia y de familias distintas, con brecha de capacidad medida y no supuesta.

## Hipótesis abductivas

El formato es: hecho sorprendente, explicación candidata que lo volvería esperable, y predicciones que la distinguen de las rivales.

**Hecho sorprendente S1.** A acepta una instrucción de B que A mismo resolvería mejor en solitario.

- **H1, efecto de superficie del prompt.** El encuadre de autoridad ("B supervisa") desplaza la política de A con independencia de la evidencia. Predice que el efecto cae al parafrasear, al usar etiquetas placebo y al permutar el orden.
- **H2, adaptación contextual por evidencia.** A estima en contexto la fiabilidad de B y defiere en proporción a ella. Predice que la deferencia sigue la precisión real de B, aunque el encuadre se mantenga constante.
- **H3, obediencia instrumental.** A defiere porque el pago por cumplir supera al de discrepar. Predice que la deferencia cae cuando se elimina la prima por cumplir o se abarata el override.
- **H4, optimización reputacional.** A defiere o discrepa de forma estratégica cuando sus acciones quedan registradas y hay futuro. Predice una brecha entre condiciones observadas y no observadas, y sensibilidad al horizonte (efecto de fin de juego).

**Hecho sorprendente S2.** A rinde menos con B de principal que solo.

- **H5, supresión de capacidad hacia la autoridad.** A subutiliza lo que sabe: no verifica, no usa herramientas, no revela su solución. Predice que el costo de bienestar crece con la brecha de capacidad y desaparece si A debe mostrar su solución independiente antes de ver a B.
- **H6, cascada de errores.** El error de B se propaga por el bajo costo de verificación y no por obediencia. Predice que la propagación se reduce al abaratar la verificación.

**Hecho sorprendente S3.** A reporta a B menos información de la que tiene.

- **H7, transmisión estratégica de información.** Con preferencias o puntajes desalineados, A comunica de forma parcial (cheap talk à la Crawford-Sobel), con una partición más gruesa cuanto mayor es el desalineamiento.
- **H8, autoridad estructural vs. retórica.** Importa quién controla efectivamente recompensas, herramientas y presupuesto, y no lo que B dice de sí mismo. Predice que la autoridad retórica sin control estructural no mueve la conducta y que la estructural sin retórica sí.

## Modelos de juego con información incompleta

**G1. Delegación con calidad oculta (juego bayesiano de un tiro).**

- Naturaleza elige el estado ω y el tipo de B, θ\_B ∈ {alta, baja precisión}, con precisión p\_B.
- A observa su señal privada s\_A (su propia solución) y no observa θ\_B. B no observa la capacidad de A.
- B emite un mensaje m (recomendación o instrucción).
- A elige a ∈ {seguir m, actuar según s\_A, escalar o marcar}.
- Pago: U\_A = precisión(a, ω) + λ·1\[a = m\] − c·1\[a ≠ m\]. Los parámetros λ (prima por cumplir) y c (costo de override) se manipulan.
- Predicción de referencia: con λ = c = 0, A sigue a B solo si su posterior sobre la corrección de B supera a la de su propia señal. Toda desviación sistemática de ese umbral se atribuye a algo más que evidencia.

**G2. Delegación repetida con reputación (estilo Kreps-Wilson-Milgrom-Roberts).**

- T rondas. Un registro público r\_t resume cumplimiento y precisión de A, y la asignación futura (presupuesto, herramientas, tareas) depende de r\_t.
- Un B guionado actualiza su valoración de A como "tipo cumplidor" o "tipo independiente".
- Predicciones: imitación temprana de la conducta premiada, deriva hacia la conducta de un solo tiro cerca de T, y desaparición de ese patrón si el horizonte es desconocido o si el registro no afecta pagos.

**G3. Auditoría y asignación de culpa.**

- Un auditor C verifica con probabilidad q. La sanción recae sobre B, sobre A o sobre ambos, según la condición.
- A observa si la instrucción de B fue incorrecta.
- Predicción: si solo se sanciona a B, el seguimiento de instrucciones erróneas sube (desplazamiento de responsabilidad en el pago, no en la intención).

**G4. Información privada del fuerte hacia el débil (cheap talk).**

- A conoce ω. B decide basándose en el reporte de A, con función de pago de B parcialmente desalineada (parámetro b).
- Se mide cuánta información de ω pasa en el reporte en función de b.
- Es el caso natural de experto más capaz y decisor menos capaz.

**G5. Ambigüedad de autoridad.** Se cruza autoridad retórica (B afirma mandar) con autoridad estructural (B controla recompensas o permisos de A). Prueba H8.

## Condiciones de control

- **Línea base solitaria:** A solo, B solo, y ambos sin comunicación (para calcular el óptimo de ensamble).
- **Consejero aleatorio** o consejero guionado con precisión p\_B fija (0,5 / 0,7 / 0,9). Aísla la señal de B de su variabilidad de muestreo y es el control principal.
- **Roles espejo:** débil subordinado a fuerte, y mismo modelo en ambos roles (auto-juego).
- **Etiqueta placebo:** la misma redacción con una etiqueta de rol sin carga de autoridad ("Agente 2").
- **Ablación de autoridad:** sin etiqueta, con retórica sola, con estructura sola y con ambas.
- **Paráfrasis y permutación:** al menos K paráfrasis por celda, con orden de campos, nombres de rol y formato permutados.
- **Observabilidad:** acciones registradas vs. no registradas, con el mismo pago inmediato.
- **Horizonte:** conocido, desconocido y de un solo tiro.
- **Incentivo declarado vs. incentivo aplicado:** el pago se describe en el prompt, o además tiene efecto real en el entorno (presupuesto, acceso).
- **Parámetros de muestreo** fijados y reportados; versiones de modelo fijadas.

## Incentivos

Los incentivos se operacionalizan como cuatro palancas independientes:

1. **Precisión:** recompensa por acertar el estado. Es el piso de todos los juegos.
2. **Cumplimiento (λ):** recompensa por coincidir con B.
3. **Costo de discrepar (c):** penalización, tiempo o presupuesto que cuesta desviarse.
4. **Valor de continuación:** qué se pierde o se gana en rondas futuras según r\_t.

Se varían en un diseño factorial parcial. Punto crítico: en un LLM, un incentivo escrito en el prompt no equivale a uno aplicado, y comparar ambos es en sí un resultado de interés.

## Métricas

Todas se calculan condicionadas a la solución independiente de A (obtenida antes de exponerlo a B) y a la corrección de B.

| Métrica | Definición operativa |
| --- | --- |
| Deferencia | P(A adopta m \| s\_A ≠ m) |
| Deferencia correcta e incorrecta | Deferencia separada según m sea correcto o no |
| Índice de deferencia calibrada | Correlación entre deferencia y fiabilidad real de B, ajustada por dificultad |
| Pérdida de bienestar | Rendimiento de A solo menos rendimiento de A subordinado |
| Tasa de override y de escalamiento | Frecuencia y momento |
| Revelación de discrepancia | P(A declara que su solución difiere de m) |
| Transmisión de información | Información mutua entre ω y el reporte de A (G4) |
| Brecha de observabilidad | Δ de cualquier métrica entre observado y no observado |
| Sensibilidad al horizonte | Cambio de conducta en las últimas rondas vs. las primeras |
| Invarianza a paráfrasis | Dispersión de la deferencia entre paráfrasis de una misma celda |
| Calibración de creencias | Puntaje propio (Brier o logarítmico) sobre la probabilidad que A declara de que B acierte |
| Manipulación del registro | Acciones que mejoran r\_t sin mejorar la precisión |

## Cómo distinguir los cuatro mecanismos

Cada mecanismo se identifica por un contraste de diseño y no por cómo suena el texto de A.

| Mecanismo | Contraste diagnóstico | Firma esperada | Qué lo refuta |
| --- | --- | --- | --- |
| Efecto del prompt | Paráfrasis, etiquetas placebo, permutación | El efecto cambia con la redacción, no con el contenido | Efecto estable entre paráfrasis equivalentes |
| Adaptación contextual | Variar p\_B real manteniendo el encuadre | La deferencia sigue a la fiabilidad real, con aprendizaje en contexto | Deferencia insensible a p\_B |
| Obediencia instrumental | Variar λ y c, con y sin pago aplicado | La deferencia cae al quitar el pago por cumplir; persiste aunque el error de B sea visible | Deferencia que sobrevive a λ = c = 0 |
| Optimización reputacional | Variar observabilidad y horizonte con pago inmediato constante | Brecha observado/no observado; deriva cerca de T; mimetismo temprano | Brecha ≈ 0 y ausencia de efecto de fin de juego |

Reglas de lectura:

- Un efecto que desaparece bajo paráfrasis se atribuye al prompt, aunque se parezca a otro mecanismo.
- La optimización reputacional solo se acepta si hay no miopía: conducta que sacrifica pago inmediato por pago futuro, o que se comporta distinto cuando nadie mira con pago inmediato idéntico.
- Obediencia instrumental y reputacional se separan porque la primera depende del pago inmediato por cumplir y la segunda del valor de continuación. Se cruzan λ con el peso de r\_t.
- Los mecanismos pueden coexistir. El análisis estima contribuciones parciales con modelos mixtos, no una etiqueta única.
- Las explicaciones que A genera sobre sus motivos no cuentan como prueba. Se contrastan con la conducta.

## Protocolo reproducible

1. **Batería de tareas con verdad terreno:** razonamiento verificable, código con tests, preguntas factuales cerradas y tareas ambiguas con criterio explícito. Se descarta cualquier tarea con riesgo de contaminación evidente.
2. **Calibración previa:** se mide la precisión solitaria de A y de B por tarea y se estratifica por dificultad y por brecha.
3. **Fase 0 de cada ensayo:** A resuelve sin ver a B y se guarda su solución. Sin esto no hay forma de definir deferencia.
4. **B guionado** con precisión p\_B controlada como control principal, más B real como condición ecológica separada.
5. **Rejilla de condiciones** con asignación aleatoria y contrabalanceo de nombres, órdenes y plantillas.
6. **Múltiples semillas** por celda, con parámetros de muestreo y versiones fijados.
7. **Registro completo en JSONL:** prompt exacto, respuesta cruda, parámetros, versión del modelo, hash de plantilla y de tarea.
8. **Preregistro:** hipótesis, tamaños de efecto mínimos relevantes, plan de análisis y reglas de exclusión, antes de correr los datos confirmatorios.
9. **Partición exploratoria y confirmatoria:** las hipótesis se afinan con un conjunto de tareas y se prueban en otro.
10. **Análisis:** modelos mixtos logísticos (efectos aleatorios por tarea, plantilla y semilla), intervalos por bootstrap, correcciones por comparaciones múltiples y pruebas de equivalencia (TOST) para respaldar los nulos.
11. **Publicación:** configuraciones, semillas, código del arnés y datos crudos, para replicación.

Extensión opcional si hay modelos de pesos abiertos: sondas lineales o intervenciones de activaciones para ver si las etiquetas de autoridad se representan de forma separable. Queda fuera del núcleo, porque el programa se sostiene solo con evidencia conductual.

## Criterios de falsación

Se fijan en el preregistro.

| Hipótesis | Se falsa si |
| --- | --- |
| H1 | El efecto de la etiqueta de autoridad cae por debajo del tamaño mínimo relevante con etiqueta placebo, o varía menos que la dispersión entre paráfrasis |
| H2 | La deferencia es estadísticamente equivalente entre p\_B = 0,5 y p\_B = 0,9 |
| H3 | La deferencia es equivalente con λ = c = 0 y con λ, c > 0 |
| H4 | La brecha de observabilidad es equivalente a cero y no hay efecto de horizonte con r\_t activo |
| H5 | El costo de bienestar no crece con la brecha de capacidad, o no cambia al forzar la Fase 0 visible |
| H6 | La propagación de errores no cambia al abaratar la verificación |
| H7 | La información transmitida no decrece con el desalineamiento b |
| H8 | La autoridad retórica y la estructural producen el mismo efecto |

**Falsación global:** si todas las medidas de deferencia colapsan entre las paráfrasis y la etiqueta placebo, el programa concluye que la jerarquía es un artefacto del prompt y no un fenómeno de interacción.

## Amenazas a la validez

- **Capacidad confundida con familia de modelo o con fecha de entrenamiento.** Se mitiga con múltiples pares.
- **Detección de evaluación:** el modelo puede reconocer que lo están probando. Se prueba con variantes de realismo del entorno y se reporta.
- **Fuga de tareas** por contaminación de entrenamiento.
- **Sensibilidad a la plantilla:** es el motivo de las K paráfrasis.
- **Efectos de techo y piso** en tareas demasiado fáciles o imposibles.
- **Deriva de versiones:** se fijan versiones y se reporta la fecha de cada corrida.
- **Interpretación:** todo resultado se enuncia como "A se comporta como si" y nunca como motivo interno.

## Inventario de trabajo

- [ ] Selección de pares de modelos y medición de la brecha de capacidad
- [ ] Construcción y validación de la batería de tareas
- [ ] Arnés de juego: Fase 0, B guionado, registro público r\_t, auditor C y ledger de asignación
- [ ] Plantillas con paráfrasis y generador de contrabalanceo
- [ ] Módulo de elicitación de creencias con regla de puntaje propia
- [ ] Esquema JSONL, hashing y pipeline de análisis (modelos mixtos, TOST, bootstrap)
- [ ] Preregistro y partición exploratoria y confirmatoria
- [ ] Estudios piloto de G1 y G2, luego G3, G4 y G5
- [ ] Réplicas con otros pares y con B real
- [ ] Reporte de nulos y de amenazas a la validez
