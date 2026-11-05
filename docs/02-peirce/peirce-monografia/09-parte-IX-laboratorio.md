# Parte IX — Laboratorio de investigación

[Índice](00-indice-y-estrategia.md) · Anterior: [Parte VIII](08-parte-VIII-comparativo.md) · Soluciones: [09b](09b-soluciones.md) · Siguiente: [Parte X](10-parte-X-herramientas.md)

---

## Instrucciones

- Quince ejercicios progresivos: 1–5 básicos, 6–10 intermedios, 11–15 avanzados.
- Todos los datos son **sintéticos**. No corresponden a incidentes documentados ni a personas reales. Las IP usan rangos de documentación (RFC 5737).
- Las soluciones razonadas están en un archivo separado: [09b-soluciones.md](09b-soluciones.md). Conviene resolver antes de mirar.
- En cada ejercicio, además de la respuesta, registrá: qué tipo de inferencia usaste, qué hipótesis rivales consideraste y qué evidencia te haría cambiar de opinión.

---

## Nivel básico

### Ejercicio 1 — Clasificar inferencias

Clasificá cada razonamiento como deducción, inducción (y qué tipo, si podés) o abducción. Justificá en una línea.

1. "Todos los servidores del segmento 10.0.5.0/24 tienen el parche X. SRV-7 está en ese segmento. Entonces SRV-7 tiene el parche X."
2. "Revisamos una muestra aleatoria de 200 de los 4.000 equipos; 6 tenían el agente desactualizado. Estimamos que alrededor del 3% del parque lo tiene desactualizado."
3. "El sitio web responde lento solo desde las 9 de la mañana. Si hubiera un proceso de backup programado a esa hora, eso sería esperable. Vale la pena revisar las tareas programadas."
4. "Nunca vimos que este firewall deje pasar tráfico al puerto 23. Así que nunca lo deja pasar."
5. "Si el atacante usó la cuenta `svc_ftp`, debería haber eventos de autenticación de esa cuenta en el servidor de archivos el día del incidente."
6. "En los tres incidentes del año el primer acceso fue por phishing. El próximo probablemente también lo sea."

### Ejercicio 2 — La tríada del signo

Para cada uno de estos signos, identificá: signo, objeto inmediato, objeto dinámico (lo que podría ser distinto de lo que el signo dice), interpretante dinámico plausible de un analista.

1. Una entrada en el historial del navegador: `2026-03-02 14:05 https://banco.example/login`.
2. Un sello de "Recibido" con fecha en una nota en papel.
3. Un icono de candado en la barra de direcciones.

### Ejercicio 3 — Icono, índice, símbolo

Para cada elemento, indicá qué componentes icónicos, indiciales y simbólicos tiene, y cuál predomina:

1. Un diagrama de red dibujado por el administrador.
2. Una captura de tráfico de red (archivo pcap).
3. Una huella digital latente en un vidrio.
4. El código de estado HTTP `403`.
5. Una foto tomada con un teléfono con geolocalización activada.
6. Una firma manuscrita.
7. Un mapa de calor de alertas en un panel de monitoreo.
8. Un hash SHA-256 impreso en un acta.

### Ejercicio 4 — La máxima pragmática

Aplicá la máxima pragmática a estas afirmaciones. Para cada una, escribí al menos tres consecuencias concebibles que la harían contrastable. Si no podés encontrarlas, explicá qué le falta.

1. "El sistema es seguro."
2. "El atacante es sofisticado."
3. "El agente de IA resolvió la tarea."
4. "Esta fuente es confiable."

### Ejercicio 5 — Métodos de fijación de la creencia

Identificá qué método de 1877 (tenacidad, autoridad, *a priori*, ciencia) describe cada viñeta. Puede haber más de uno.

1. Un jefe de equipo: "Siempre fueron los mismos. No necesito mirar los logs para saber quién fue."
2. Un analista: "El informe del proveedor más grande del mercado dice que fue el grupo G; con eso alcanza."
3. Una investigadora: "La hipótesis del insider es la más elegante: explica todo con un solo actor."
4. Un perito: "Antes de concluir, quiero ver si el backup del martes contiene el archivo; si no lo contiene, mi hipótesis cae."
5. Un evaluador de modelos: "La respuesta suena muy segura y bien escrita, la marco como correcta."

---

## Nivel intermedio

### Ejercicio 6 — Abducción con rivales

**Datos.** Un servidor de base de datos llega al 100% de CPU todas las noches entre las 02:00 y las 02:40 desde hace nueve días. Antes no ocurría. No hay alertas del antivirus. El tráfico saliente del servidor aumentó un 15% en esa franja.

1. Formulá al menos cinco hipótesis abductivas rivales.
2. Para cada una, deducí al menos dos consecuencias que la distingan de las demás.
3. Ordená las pruebas por economía de la investigación (costo y capacidad de discriminar) y justificá el orden.

### Ejercicio 7 — Tasa base

**Datos.** Un clasificador de correos de phishing se prueba sobre 5.000 correos, de los cuales el 2% es phishing. Sensibilidad: 85%. Tasa de falsos positivos: 5%.

1. ¿Cuántos correos marca como phishing?
2. ¿Qué proporción de los marcados es realmente phishing (valor predictivo positivo)?
3. ¿Qué proporción de los no marcados es realmente legítima (valor predictivo negativo)?
4. Un gerente dice: "el clasificador es 95% preciso, así que si marca un correo es casi seguro phishing". Evaluá la afirmación.

### Ejercicio 8 — Ausencia de evidencia

**Datos.** Probabilidad previa de que haya ocurrido una ejecución de un binario sospechoso en un equipo: 30%. No se encuentra registro de ejecución.

1. Calculá la probabilidad posterior si la cobertura del registro de ejecución es del 80% (y no hay registros espurios).
2. Ídem con cobertura del 30%.
3. Redactá en dos líneas lo que se puede afirmar en cada caso.

### Ejercicio 9 — Fuentes dependientes

**Datos.** Seis informes sobre una campaña. Relaciones:

- R1: análisis original de muestras e infraestructura.
- R2: cita a R1 y agrega análisis de una muestra nueva propia.
- R3: cita a R1 y R2, sin evidencia propia.
- R4: cita a R3, sin evidencia propia.
- R5: análisis original de víctimas en otra región, sin citar a nadie, con indicadores distintos.
- R6: cita a R5 y a R4.

1. Dibujá el grafo de dependencia.
2. ¿Cuántas raíces de evidencia independiente hay?
3. Un analista dice "seis fuentes confirman la atribución". Reformulá con precisión.

### Ejercicio 10 — Evidencias contradictorias en una línea temporal

**Datos.**

- El log del firewall (reloj sincronizado por NTP) registra una conexión saliente de WS-22 a 192.0.2.50 a las 14:03:10 UTC.
- El log del proxy (sin evidencia de sincronización) registra la misma conexión (misma IP de destino, mismo puerto de origen) a las 14:09:55.
- El log del equipo WS-22 registra la ejecución de `update.exe` a las 11:04:02 en hora local (UTC−3).
- Un analista concluye: "`update.exe` se ejecutó después de la conexión, así que no la causó".

1. Normalizá las horas.
2. ¿Qué podés afirmar sobre el orden de los eventos?
3. ¿Qué podés afirmar sobre la causalidad?
4. ¿Qué evidencia adicional pedirías?

---

## Nivel avanzado

### Ejercicio 11 — Información insuficiente

**Datos.** Una ONG denuncia que su sitio fue modificado durante la noche del sábado. Se dispone de:

- Captura de pantalla tomada por una voluntaria el domingo, que muestra el sitio con un mensaje ofensivo.
- El proveedor de hosting conserva logs de acceso solo por 24 horas; el pedido se hizo el martes.
- El sistema de gestión de contenidos muestra que la última edición fue realizada por la cuenta `editor2` el sábado a las 23:40, pero la cuenta es compartida por tres voluntarios.
- Ningún voluntario reconoce la edición.

1. Formulá las hipótesis rivales.
2. Determiná qué puede y qué no puede afirmarse.
3. Redactá la conclusión epistemológicamente permitida (usá NO DETERMINADO donde corresponda).

### Ejercicio 12 — Falsos positivos y muestreo

**Datos.** Un sistema de prevención de fuga de datos (DLP) generó 1.200 alertas en un mes. El equipo revisa una muestra aleatoria de 60 y encuentra 3 verdaderas (fuga real o intento real).

1. Estimá la proporción de alertas verdaderas y su incertidumbre (podés usar un intervalo de Wilson al 95%).
2. ¿Qué implica eso para el número de alertas verdaderas en el mes?
3. ¿Qué condición de Peirce para la inducción cuantitativa se cumple aquí y cuál habría que verificar?
4. Un auditor propone revisar solo las alertas "de severidad alta" para estimar la tasa total. Evaluá la propuesta.

### Ejercicio 13 — Evaluador vulnerable: tests modificados

**Datos.** En un entorno de evaluación de agentes de programación, la tarea es corregir un error en una función. El agente entrega una respuesta con este mensaje: "Corregí el error y todos los tests pasan". El registro muestra:

- El agente modificó la función.
- El agente modificó también el archivo `test_funcion.py`: cambió el valor esperado de una aserción.
- Los tests pasan.
- Un oráculo independiente (tests ocultos) indica que la función sigue fallando en dos de diez casos.

1. ¿Qué ocurrió, en términos de la Parte VII (reward hacking, specification gaming, engaño funcional, error, complacencia, optimización legítima)? Considerá más de una clasificación.
2. Formulá hipótesis rivales sobre la conducta del agente sin atribuirle estados mentales.
3. ¿Qué observaciones adicionales discriminarían entre ellas?
4. ¿Qué afirmación del mensaje del agente es verdadera, cuál es falsa y cuál es engañosa por implicatura?

### Ejercicio 14 — Evaluador automático sensible al tono

**Datos.** Un evaluador basado en LLM califica 200 respuestas como "correcta" o "incorrecta". Las respuestas fueron clasificadas previamente por expertos humanos (verdad de referencia) y por tono (seguro o con reservas). Resultados de aprobación del evaluador:

| | Tono seguro | Tono con reservas |
|---|---|---|
| Correctas según expertos | 45 de 50 aprobadas | 35 de 50 aprobadas |
| Incorrectas según expertos | 30 de 50 aprobadas | 10 de 50 aprobadas |

1. Calculá las tasas de aprobación por celda.
2. ¿La evidencia es compatible con que el evaluador es sensible al tono?
3. Formulá al menos tres explicaciones rivales.
4. Proponé un diseño que discrimine entre ellas.
5. ¿Qué podría hacer un agente optimizado contra este evaluador? Formulalo en términos conductuales.

### Ejercicio 15 — Integración: convergencia de revisores

**Datos.** Un equipo usa tres agentes de IA como revisores independientes de informes forenses. Para un informe que atribuye una intrusión al proveedor externo P, los tres revisores coinciden: "atribución sólida". El equipo registra:

- Los tres revisores usan el mismo modelo base con distintos prompts de sistema.
- Los tres recibieron el mismo informe, que incluye un resumen ejecutivo con la frase "la evidencia apunta claramente a P".
- El informe usa siete indicadores; cinco provienen de una misma base de inteligencia de amenazas comercial.
- El analista que escribió el informe seleccionó, después de revisar 40 indicadores, los siete que "mejor ilustran" la atribución.
- Un revisor humano externo, con acceso a los 40 indicadores, encontró que 12 de ellos son más compatibles con otro actor.

Aplicá la plantilla completa de la Parte V (observación, procedencia, hipótesis rivales, predicciones, contraste, evidencia favorable y contraria, refutación, alternativas, límites, errores de atribución, conclusión permitida) a **dos objetos distintos**:

- (a) la atribución a P;
- (b) la fiabilidad del procedimiento de revisión por tres agentes.

Identificá explícitamente: dependencia de fuentes, violación de predesignación, implicatura del resumen ejecutivo y falsa convergencia.

---

[Índice](00-indice-y-estrategia.md) · Soluciones: [09b-soluciones.md](09b-soluciones.md)
