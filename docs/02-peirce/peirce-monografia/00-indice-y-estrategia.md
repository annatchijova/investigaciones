# 00 — Índice detallado y estrategia de verificación bibliográfica

[README](README.md) · Siguiente: [Parte I](01-parte-I-abc.md)

---

## 1. Propósito de este archivo

Este archivo cumple dos funciones que la consigna pidió explícitamente antes de desarrollar los capítulos:

1. Proponer un **índice detallado** de la monografía.
2. Explicitar una **estrategia de verificación bibliográfica**: qué fuentes se usan, cómo se citan, qué grado de verificación tiene cada referencia y qué queda pendiente.

El documento es material de estudio. No es una investigación sobre reward hacking ni reemplaza las conclusiones que la autora del proyecto `reward-hacking-social` redacte y evalúe.

---

## 2. Convenciones epistémicas usadas en todo el texto

Cada afirmación importante lleva, cuando corresponde, una de estas etiquetas entre corchetes. La consigna exige distinguir estos niveles y es el recurso principal para no atribuirle a Peirce lo que no dijo.

| Etiqueta | Significado | Ejemplo de uso |
|---|---|---|
| **[TEXTO]** | Formulación de Peirce, citada o parafraseada con referencia a un texto identificable. | La máxima pragmática de 1878 (CP 5.402). |
| **[INTERP]** | Interpretación académica: lo que especialistas sostienen sobre Peirce. Puede haber desacuerdo. | La tesis de "dos Peirce" de Goudge (1950). |
| **[HECHO]** | Hecho histórico o técnico documentado y no controvertido en lo esencial. | Peirce trabajó en el U.S. Coast Survey entre 1859 y 1891. |
| **[APLIC]** | Aplicación contemporánea propuesta en esta monografía. No es de Peirce ni de sus intérpretes salvo aclaración. | Leer un log como índice semiótico. |
| **[ANALOGÍA]** | Paralelismo metodológico útil, sin pretensión de derivación histórica. | Peirce y la revisión adversarial en DFIR. |
| **[ESPEC]** | Especulación: idea que vale explorar, sin respaldo suficiente todavía. | Hipótesis sobre convergencia falsa entre evaluadores LLM. |

Regla de lectura: cuando una sección dice "Peirce sostiene", se refiere a **[TEXTO]**. Cuando dice "puede leerse", "una interpretación posible" o "proponemos", se refiere a **[INTERP]**, **[APLIC]** o **[ESPEC]**. Las frases del tipo "Peirce demuestra que…" están evitadas a propósito.

---

## 3. Índice detallado

### Archivo 01 — Parte I. ABC: Peirce desde cero
1. Quién fue Peirce: biografía intelectual mínima y contexto (Cambridge, Coast Survey, Johns Hopkins, Metaphysical Club, Milford).
2. Por qué es difícil leerlo: dispersión de manuscritos, ediciones (CP, W, EP), evolución del pensamiento.
3. Mapa general: lógica, semiótica, pragmatismo/pragmaticismo, filosofía de la ciencia, fenomenología (faneroscopia), metafísica.
4. Catorce conceptos fundamentales, cada uno con: definición sencilla, definición rigurosa, ejemplo cotidiano, ejemplo de investigación, error frecuente.
   - signo, objeto, interpretante, inferencia, proposición, creencia, duda, investigación, verdad, realidad, falibilismo, comunidad de investigación, hábito, consecuencias prácticas.
5. Pragmatismo y pragmaticismo: la máxima de 1878 y su reformulación de 1905.

### Archivo 02 — Parte II. Abducción, deducción e inducción
1. La clasificación temprana (1865–1878): deducción, inducción e hipótesis como reordenamientos del silogismo.
2. El ejemplo de los porotos (1878): regla, caso, resultado.
3. La clasificación madura (c. 1900–1908): tres etapas de la investigación.
4. Abducción: esquema de 1903, función, límites, criterios de selección (economía de la investigación).
5. Deducción: explicación y derivación de consecuencias contrastables.
6. Inducción: tipos (cruda, cuantitativa, cualitativa), autocorrección, muestreo y predesignación.
7. Relación entre las tres: ciclo, no algoritmo lineal fijo.
8. Distinciones de vocabulario: hipótesis plausible, mejor explicación disponible, corroboración, confirmación, falsación, refutación, prueba concluyente.
9. Hipótesis rivales, subdeterminación, incertidumbre, carga teórica de la observación, sesgo de confirmación.
10. Advertencias de anacronismo: inferencia a la mejor explicación (Harman, Lipton), falsacionismo (Popper), bayesianismo.

### Archivo 03 — Parte III. Teoría de los signos
1. Las categorías: primeridad, segundidad, terceridad (desde "On a New List of Categories", 1867, hasta la faneroscopia de 1903).
2. La relación triádica signo–objeto–interpretante; objeto inmediato y dinámico; interpretante inmediato, dinámico y final.
3. Icono, índice y símbolo: definiciones y mezclas.
4. Semiosis y producción de conocimiento.
5. Por qué "índice semiótico" y "artefacto forense" no son equivalentes.
6. Aplicaciones: logs, metadatos, timestamps, hashes, testimonios, mensajes, capturas de pantalla, telemetría, documentación.
7. Cómo una señal verdadera puede sostener una interpretación falsa.

### Archivo 04 — Parte IV. Epistemología de la investigación
1. "The Fixation of Belief" (1877): duda, creencia, los cuatro métodos.
2. "How to Make Our Ideas Clear" (1878): tres grados de claridad, máxima pragmática, verdad y realidad.
3. Duda genuina versus duda de papel (1868).
4. Comunidad de investigación, falibilismo, autocorrección.
5. Verdad como convergencia: lecturas e interpretaciones simplificadas que conviene evitar.
6. Problemas prácticos: independencia de fuentes, autoridad, consenso, corroboración circular, selección de evidencia, revisión adversarial, observación versus conclusión.

### Archivo 05 — Parte V. Peirce en investigación forense
1. Cinco operaciones que no hay que mezclar: preservación, integridad, autenticidad, interpretación, atribución.
2. Plantilla de análisis de caso.
3. Doce casos didácticos sintéticos (DFIR, criminal, OSINT, documental, atribución, respuesta a incidentes).

### Archivo 06 — Parte VI. Peirce y los límites de la prueba
1. Qué es de Peirce y qué es estadística posterior.
2. Errores tipo I y II; asimetría de costos de error.
3. Tasas base (base rates) y falacia del fiscal.
4. Evidencia negativa y ausencia de evidencia.
5. Dependencia entre fuentes.
6. Sesgos cognitivos en análisis forense.
7. Explicaciones ad hoc, circularidad, sobreinterpretación, selección retrospectiva.
8. Casos donde la conclusión correcta es NO DETERMINADO.

### Archivo 07 — Parte VII. Peirce, IA y reward hacking
1. Declaración de acceso al repositorio y alcance de la lectura.
2. Distinciones conceptuales: reward hacking, specification gaming, engaño, error, complacencia, optimización legítima.
3. Diez conexiones (señales de éxito, evaluadores engañados, hipótesis sobre estrategias, contaminación de fuentes, falsa convergencia, afirmaciones no verificadas, abstención, observabilidad, trazabilidad, veredicto determinista vs. explicación generativa). Para cada una: qué aporta Peirce, qué es extrapolación moderna, qué podría observarse, hipótesis rival, hallazgo debilitante.
4. Notas de lectura sobre los documentos 21, 23, 24 y 31 del repositorio (observaciones para la autora, no conclusiones).

### Archivo 08 — Parte VIII. Análisis crítico y comparativo
1. Peirce y Popper. 2. Peirce y Kuhn. 3. Peirce y Lakatos. 4. Peirce y el bayesianismo. 5. Peirce y Eco.
6. Críticas al razonamiento abductivo; el problema de elegir entre explicaciones igualmente compatibles.
7. Problemas forenses que quedan sin resolver aun con una metodología peirceana.

### Archivos 09 y 09b — Parte IX. Laboratorio de investigación
Quince ejercicios progresivos con datos sintéticos (09) y soluciones razonadas en archivo separado (09b).

### Archivo 10 — Parte X. Herramientas de estudio
Glosario, cronología intelectual, mapa de conceptos, tabla de errores frecuentes, matriz de tipos de inferencia, fichas de lectura, preguntas de investigación abiertas, itinerario de lectura gradual.

### Archivo 11 — Bibliografía anotada
Primaria, secundaria, en español, forense, IA, con estado de verificación.

### Archivo 12 — Matriz de procedencia
Afirmaciones centrales de la monografía, su fuente, tipo epistémico y estado de verificación.

### Archivo 13 — Registro de pendientes
Secciones incompletas, fuentes no verificadas, límites de esta versión.

---

## 4. Estrategia de verificación bibliográfica

### 4.1 Jerarquía de fuentes

1. **Textos primarios de Peirce**, identificados por título, año y lugar de publicación original, con su localización en las ediciones de referencia:
   - **CP** — *Collected Papers of Charles Sanders Peirce*, 8 vols. Vols. 1–6 ed. Charles Hartshorne y Paul Weiss (1931–1935); vols. 7–8 ed. Arthur W. Burks (1958). Cambridge, MA: Harvard University Press. Cita: CP volumen.parágrafo (ej. CP 5.402).
   - **W** — *Writings of Charles S. Peirce: A Chronological Edition*. Bloomington: Indiana University Press, 1982–. Edición crítica cronológica del Peirce Edition Project. Cita: W volumen:página (ej. W3:257).
   - **EP** — *The Essential Peirce: Selected Philosophical Writings*. Vol. 1 (1867–1893), ed. Nathan Houser y Christian Kloesel, 1992; vol. 2 (1893–1913), ed. Peirce Edition Project, 1998. Bloomington: Indiana University Press. Cita: EP volumen:página.
   - **MS** — manuscritos según el catálogo de Richard Robin (1967), *Annotated Catalogue of the Papers of Charles S. Peirce*.
   - **NEM** — *The New Elements of Mathematics*, ed. Carolyn Eisele, 4 vols. La Haya: Mouton, 1976.
2. **Traducciones al español** de referencia (para lectura, no para citar páginas del original):
   - *Obra filosófica reunida*, tomo I (1867–1893) y tomo II (1893–1913). Ed. Nathan Houser y Christian Kloesel; trad. Darin McNabb; rev. Sara Barrena. México: Fondo de Cultura Económica, 2012. Es la traducción de EP.
   - Traducciones del Grupo de Estudios Peirceanos (GEP), Universidad de Navarra.
   - *La ciencia de la semiótica*. Buenos Aires: Nueva Visión, 1974 (trad. Beatriz Bugni).
3. **Obras de referencia académica**: *Stanford Encyclopedia of Philosophy* (SEP) e *Internet Encyclopedia of Philosophy* (IEP). Se usan como orientación y para rastrear debates, **nunca como sustituto del texto primario**.
4. **Literatura especializada** (monografías y artículos revisados por pares).
5. **Literatura técnica contemporánea** (forense digital, análisis de inteligencia, IA), claramente separada del corpus peirceano.

### 4.2 Distinción entre tipos de texto de Peirce

La consigna pide diferenciar textos publicados en vida, manuscritos y compilaciones póstumas. Se adopta esta marca:

| Marca | Tipo | Ejemplos |
|---|---|---|
| **(P)** | Publicado en vida | "The Fixation of Belief" (1877), "What Pragmatism Is" (1905) |
| **(C)** | Conferencia (dictada en vida, publicada póstumamente en general) | Conferencias de Harvard sobre pragmatismo (1903) |
| **(M)** | Manuscrito no publicado en vida | "The Logic of Drawing History from Ancient Documents" (1901, MS 690) |
| **(L)** | Carta | Cartas a Lady Welby (1904–1911) |

Advertencia sobre los CP: los editores de los *Collected Papers* combinaron a veces fragmentos de períodos distintos en una misma sección. Un número de CP no garantiza fecha ni unidad del texto. Para fechar, conviene usar W o EP, que respetan la cronología.

### 4.3 Códigos de estado de verificación

Cada referencia de la bibliografía (archivo 11) y de la matriz de procedencia (archivo 12) lleva uno de estos códigos:

| Código | Significado |
|---|---|
| **V1** | Verificado durante la elaboración de este documento contra una fuente en línea identificable (catálogo editorial, registro de arXiv, página de la revista, ficha bibliotecaria o el propio texto). |
| **V2** | Referencia estándar en la literatura, consignada a partir de conocimiento bibliográfico previo. Autor, título y año son de alta confianza; **las páginas, los parágrafos de CP y las correspondencias CP↔EP deben cotejarse** antes de usarse en un trabajo propio. |
| **N** | No verificada o con datos parciales. No debe citarse sin cotejo. |

Limitación declarada: durante esta sesión **no fue posible acceder directamente** a las páginas de la SEP (el acceso automático estuvo bloqueado), a los textos completos de CP o EP ni a bases con paginación. Las afirmaciones sobre el contenido de esas obras proceden de conocimiento previo y de fragmentos indirectos (archivos de la SEP, bibliografías vinculadas de PhilPapers, catálogos). Por eso muchas referencias primarias quedan en **V2**.

### 4.4 Política de citas

- Las citas textuales de Peirce se dan en inglés (el original), seguidas de una **traducción de trabajo** propia, marcada como tal. No se reproducen traducciones publicadas protegidas.
- Solo se citan textualmente pasajes breves y muy conocidos cuya formulación es estable en la literatura. Aun así, figuran como V2: **cotejá la redacción exacta en EP o W antes de citarla en un trabajo propio**.
- No se inventan citas, páginas, DOI ni enlaces. Donde no hay dato verificado, se omite.
- Los textos de autores contemporáneos se parafrasean.

### 4.5 Procedimiento recomendado para quien estudie con este material

1. Para cada concepto, localizá el texto primario en EP (o en la traducción de FCE) usando la referencia dada.
2. Leé el pasaje completo, no solo la frase citada: Peirce suele matizar en el párrafo siguiente.
3. Compará con la entrada correspondiente de la SEP o IEP para ver qué intérpretes discuten esa lectura.
4. Registrá en tu propia matriz: cita, edición, página, fecha del texto, tipo (P/C/M/L) y si tu uso es [TEXTO], [INTERP] o [APLIC].
5. Antes de usar una idea de Peirce en tu investigación, preguntate: ¿esto lo dijo Peirce, lo dice un intérprete, o lo estoy proponiendo yo?

---

[README](README.md) · Siguiente: [Parte I](01-parte-I-abc.md)
