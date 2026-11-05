# Parte V — Peirce en investigación forense

[Índice](00-indice-y-estrategia.md) · Anterior: [Parte IV](04-parte-IV-epistemologia.md) · Siguiente: [Parte VI](06-parte-VI-limites-prueba.md)

---

## 0. Advertencia de estatus

Todo el contenido de esta parte es **[APLIC]** o **[ANALOGÍA]**: aplicación de categorías peirceanas a la práctica forense contemporánea. Peirce no escribió sobre forense digital. Algunas ideas suyas tienen una conexión histórica con la investigación indiciaria (escribió sobre la lógica de reconstruir la historia a partir de documentos antiguos en 1901, y la literatura lo asoció con el método detectivesco, por ejemplo en Eco y Sebeok 1983), pero eso no convierte a Peirce en teórico del peritaje.

Los doce casos son **sintéticos**: construidos con fines didácticos. No describen incidentes reales ni personas reales. Las IP usan rangos reservados para documentación (RFC 5737).

---

## 1. Cinco operaciones que no hay que mezclar

| Operación | Pregunta | Qué la sostiene | Qué **no** demuestra |
|---|---|---|---|
| **Preservación** | ¿Se conservó la evidencia sin alterarla desde que se recolectó? | Procedimientos de adquisición, cadena de custodia, copias verificadas, bloqueo de escritura. | Nada sobre lo que la evidencia significa. |
| **Integridad** | ¿La copia es idéntica al original recolectado? | Hashes criptográficos calculados en la adquisición y en cada verificación. | Que el original fuera auténtico o verdadero. |
| **Autenticidad** | ¿La evidencia es lo que se dice que es (proviene de la fuente que se afirma, no fue fabricada ni alterada antes de la recolección)? | Procedencia, coherencia interna, coherencia con fuentes independientes, conocimiento del sistema que la produjo. | Que lo que la evidencia dice haya ocurrido. |
| **Interpretación** | ¿Qué evento o estado del mundo representa la evidencia? | Conocimiento de la terceridad del sistema (formatos, semántica de campos, comportamiento del software), contraste con otras evidencias. | Quién es responsable. |
| **Atribución** | ¿Quién (persona, grupo, proceso) produjo el evento? | Conjunto de inferencias que conectan el evento con un agente, con hipótesis rivales descartadas. | Intención o motivo, salvo evidencia adicional. |

Relación con la semiótica (Parte III) [APLIC]:

- Preservación e integridad garantizan que el **signo** no cambió desde la recolección.
- Autenticidad examina la conexión entre el signo y su **fuente** (de qué proceso es índice).
- Interpretación trata la relación entre el signo y el **objeto dinámico** investigado.
- Atribución agrega otra inferencia: del evento al **agente**.

Cada paso exige inferencias nuevas. **Un hash válido no demuestra la veracidad de un relato ni la autoría de un hecho**: demuestra integridad de bytes desde un momento dado.

---

## 2. Plantilla de análisis

Cada caso sigue esta estructura:

1. **Observación inicial** — el hecho sorprendente.
2. **Procedencia** — de dónde viene la evidencia y por qué cadena llegó.
3. **Hipótesis abductivas rivales** — al menos tres.
4. **Predicciones deductivas** — qué debería observarse si cada hipótesis fuera verdadera.
5. **Procedimientos de contraste** — cómo se pone a prueba.
6. **Evidencia favorable y contraria** — resultados sintéticos.
7. **Condiciones de refutación** — qué haría abandonar la hipótesis preferida.
8. **Explicaciones alternativas** no consideradas al principio.
9. **Límites de la inferencia**.
10. **Errores de atribución posibles**.
11. **Conclusión epistemológicamente permitida** — lo que se puede afirmar, con alcance.

---

## Caso 1 — Inicio de sesión desde una IP extranjera (DFIR)

**1. Observación.** El servidor de correo de una cooperativa registra un inicio de sesión exitoso en la cuenta de la tesorera desde 198.51.100.23 a las 03:14 (hora del servidor), geolocalizada por una base comercial en otro continente. La tesorera vive en Buenos Aires.

**2. Procedencia.** Log del servidor de correo, exportado por el administrador de sistemas mediante la consola web del proveedor. Copia entregada en CSV. Hash calculado al recibir el CSV, no en el origen.

**3. Hipótesis rivales.**
- H1: Robo de credenciales y acceso por un tercero.
- H2: La tesorera usó una VPN comercial con salida en ese país.
- H3: La geolocalización de la IP es errónea o desactualizada.
- H4: El acceso fue de un cliente de correo o servicio automatizado autorizado (por ejemplo, una integración) alojado en la nube.
- H5: El log está mal interpretado: el campo es la IP de un proxy del proveedor, no del cliente.

**4. Predicciones.**
- H1: probable actividad anómala posterior (reglas de reenvío, lectura masiva, envíos inusuales); posible fallo de MFA o ausencia de MFA; la tesorera no reconoce el acceso.
- H2: la tesorera tiene instalada una VPN; otros accesos suyos muestran IPs del mismo proveedor de VPN; horario coherente con su actividad.
- H3: otras bases de geolocalización discrepan; el bloque de IP fue reasignado recientemente.
- H4: el agente de usuario corresponde a un servicio; hay accesos periódicos desde rangos similares.
- H5: la documentación del proveedor indica que el campo es de proxy; todas las sesiones muestran IPs del mismo rango.

**5. Contraste.** Revisar el resto del log de la cuenta (no solo la línea); campo de agente de usuario; documentación del proveedor sobre el campo; consulta a la tesorera; inventario de integraciones; consultar varias bases de geolocalización; revisar reglas de buzón.

**6. Resultados sintéticos.**
- Favorable a H1: se creó una regla de reenvío a una dirección externa 6 minutos después del acceso.
- Contraria a H2: la tesorera no usa VPN y no hay otros accesos desde ese proveedor.
- Contraria a H5: otras sesiones muestran IPs residenciales locales; el campo es del cliente según la documentación.
- Neutral respecto de H3: dos bases coinciden en el país, una no.

**7. Refutación de H1.** Si la regla de reenvío fue creada por la propia tesorera desde otra sesión, o si se demuestra una integración autorizada que crea reglas, H1 se debilita mucho.

**8. Alternativas no consideradas.** Un familiar con acceso legítimo a la cuenta que viajaba; un asistente externo contratado.

**9. Límites.** El CSV no tiene hash de origen: su integridad está garantizada desde la recepción, no desde el servidor. La ubicación de la IP no identifica al operador.

**10. Errores de atribución posibles.** "Fue un actor del país X" (la IP es del último salto); "la tesorera mintió" (sin evidencia); confundir la cuenta con la persona.

**11. Conclusión permitida.** "Hay evidencia consistente con un acceso no autorizado a la cuenta de la tesorera el día D: un inicio de sesión desde una IP no asociada a su actividad habitual seguido de la creación de una regla de reenvío externa que ella no reconoce. No es posible, con la evidencia disponible, determinar la ubicación ni la identidad del operador. La integridad del log está verificada desde su recepción, no desde el origen."

---

## Caso 2 — Timestamps anteriores a la instalación del sistema (DFIR)

**1. Observación.** En la notebook de un empleado se encuentra `informe_final.docx` cuyo atributo de creación indica una fecha de 2019; el sistema operativo se instaló en 2023.

**2. Procedencia.** Imagen forense del disco, adquirida con bloqueador de escritura, con hash SHA-256 registrado. Timestamps obtenidos con una herramienta de análisis de NTFS (atributos `$STANDARD_INFORMATION`).

**3. Hipótesis rivales.**
- H1: Manipulación deliberada de timestamps (*timestomping*).
- H2: El archivo se copió o extrajo desde otro medio con un método que preserva fechas originales.
- H3: El reloj del sistema estaba mal configurado cuando se creó.
- H4: El campo leído no es el de creación del archivo en ese sistema sino un metadato interno del documento (propiedades de Office) que conserva la fecha del documento original.

**4. Predicciones.**
- H1: discrepancia entre `$STANDARD_INFORMATION` y `$FILE_NAME` (el segundo es más difícil de modificar con herramientas comunes); posibles rastros de herramientas de manipulación; valores con fracciones de segundo en cero.
- H2: rastros de extracción de un archivo comprimido o de un dispositivo externo; otros archivos con fechas antiguas en el mismo directorio.
- H3: otros archivos y eventos del mismo período con fechas desplazadas en la misma magnitud.
- H4: el metadato interno del documento y el atributo del sistema de archivos difieren.

**5. Contraste.** Comparar ambos atributos de NTFS; revisar el registro del sistema de archivos (`$UsnJrnl`, `$LogFile`) si está disponible; buscar archivos comprimidos y eventos de dispositivos USB; comparar con otros archivos del directorio.

**6. Resultados sintéticos.**
- `$FILE_NAME` indica creación en 2024; `$STANDARD_INFORMATION` indica 2019. Favorable a H1 **o** a ciertos métodos de copia (algunas herramientas actualizan uno y no otro).
- En el mismo directorio hay 40 archivos con fechas de 2019 a 2021, extraídos de un `.zip` según el journal. Favorable a H2.
- No hay rastro de herramientas de manipulación. Contrario (débil) a H1.

**7. Refutación de H1.** Si se demuestra que todos los archivos del `.zip` muestran el mismo patrón de discrepancia, H1 deja de ser necesaria: H2 explica el patrón sin intervención deliberada.

**8. Alternativas.** Restauración desde backup; sincronización con un servicio en la nube que preserva fechas.

**9. Límites.** La ausencia de rastros de herramientas no excluye manipulación (pudo usarse otra herramienta o borrarse). El comportamiento de las fechas al extraer depende del software y la versión.

**10. Errores posibles.** "El empleado falsificó la fecha para aparentar que el informe era anterior" (atribución de intención sin evidencia); "la fecha de 2019 es la fecha real de redacción" (puede ser la de un borrador, una plantilla o de otro autor).

**11. Conclusión permitida.** "El archivo fue escrito en este disco en 2024 según el atributo `$FILE_NAME`, junto con otros 40 archivos extraídos de un archivo comprimido. La fecha de 2019 del atributo `$STANDARD_INFORMATION` es compatible con preservación de fechas al extraer. No hay evidencia de manipulación deliberada; tampoco puede excluirse por completo. La fecha de 2019 no permite, por sí sola, establecer cuándo fue redactado el contenido."

---

## Caso 3 — Coincidencia de hash en un pendrive (análisis documental / atribución)

**1. Observación.** Un documento confidencial filtrado a un medio tiene el mismo SHA-256 que un archivo hallado en un pendrive encontrado en el escritorio de la empleada E.

**2. Procedencia.** El documento filtrado fue entregado por el medio en respuesta a un pedido judicial (copia del archivo recibido). El pendrive fue secuestrado con acta y adquirido con bloqueador de escritura.

**3. Hipótesis rivales.**
- H1: E copió el documento al pendrive y lo filtró.
- H2: E tenía el documento por razones laborales legítimas; la filtración vino de otra persona con acceso al mismo archivo.
- H3: El pendrive no era de E o fue usado por varias personas.
- H4: El documento circuló ampliamente (por correo interno a una lista grande); muchas personas tenían copias idénticas.

**4. Predicciones.**
- H1: registros de copia al pendrive desde el equipo de E; posible contacto con el medio; momento de copia anterior a la filtración.
- H2: el documento está en el flujo de trabajo de E (correos, carpetas de proyecto); otras personas tienen copias.
- H3: el pendrive tiene archivos de varias personas; huellas o registros de conexión en otros equipos.
- H4: el documento fue enviado a una lista de N destinatarios con el mismo adjunto.

**5. Contraste.** Registro de dispositivos USB en el equipo de E y en otros equipos; registros de acceso al repositorio documental; cronología de la copia; lista de destinatarios del correo original.

**6. Resultados sintéticos.**
- El documento se envió como adjunto a 38 personas, entre ellas E. Favorable a H2/H4.
- El pendrive se conectó a dos equipos además del de E. Favorable a H3.
- La copia al pendrive ocurrió dos semanas antes de la filtración. Compatible con todas.

**7. Refutación de H1.** Si se identifica otra vía de filtración con evidencia más específica (por ejemplo, el archivo filtrado contiene una marca de agua o metadato que solo tiene la copia de otra persona), H1 queda muy debilitada.

**8. Alternativas.** El medio recibió el documento de una fuente externa a la organización que lo obtuvo por otra vía.

**9. Límites.** La coincidencia de hash prueba identidad de bytes. Con 38 copias idénticas, la coincidencia no discrimina entre destinatarios.

**10. Errores posibles.** "Hash coincidente ⇒ E filtró el documento". Es un error de los tipos "integridad ⇒ atribución" y "posesión ⇒ acción".

**11. Conclusión permitida.** "El pendrive contiene una copia idéntica en bytes al documento filtrado. El documento había sido distribuido a 38 personas. La evidencia no permite distinguir el origen de la filtración entre quienes tenían copias idénticas. **Atribución: NO DETERMINADA.**"

---

## Caso 4 — Ubicación por antenas de telefonía (investigación criminal)

**1. Observación.** Registros de una operadora indican que el teléfono asociado a la línea del sospechoso S se conectó a una antena a 600 m del lugar de un robo, en la franja horaria del hecho.

**2. Procedencia.** Informe de la operadora en respuesta a una orden judicial, con registros de eventos (llamadas, datos) y la celda asociada a cada uno.

**3. Hipótesis rivales.**
- H1: S estuvo en el lugar del hecho.
- H2: S estaba en otro lugar dentro del área de cobertura de esa antena (que puede abarcar kilómetros en zonas suburbanas).
- H3: El teléfono estaba en poder de otra persona.
- H4: La conexión a esa antena se debió a balanceo de carga o saturación de otra antena, y S estaba más lejos.

**4. Predicciones.**
- H1: eventos sucesivos en antenas compatibles con un trayecto hacia y desde el lugar; ausencia de coartada verificable.
- H2: S vive o trabaja dentro de la cobertura de la antena; eventos regulares en esa antena en días sin hechos.
- H3: testimonios o registros de que otra persona usaba el teléfono.
- H4: historial de conexiones de S a esa antena en condiciones similares desde lugares conocidos.

**5. Contraste.** Mapa de cobertura (no solo ubicación de la antena); historial de eventos de días previos; patrones de actividad; otras evidencias de ubicación (cámaras, transacciones).

**6. Resultados sintéticos.**
- S vive a 1,8 km del lugar, dentro de la cobertura estimada de la antena; su teléfono se conecta a esa antena casi todas las noches. Favorable a H2.
- No hay eventos que sugieran desplazamiento durante la franja.

**7. Refutación de H2.** Si otra evidencia independiente (cámara) ubica a S en el lugar, H2 deja de ser suficiente.

**8. Alternativas.** El teléfono pudo estar apagado durante parte del período (los registros solo muestran eventos, no presencia continua).

**9. Límites.** La antena es índice del teléfono, no de la persona; y su ubicación es índice de un área, no de un punto. La base rate (cuántas personas en esa área a esa hora) es enorme.

**10. Errores posibles.** Confundir "conectado a una antena cercana" con "estuvo en el lugar"; confundir teléfono con persona.

**11. Conclusión permitida.** "Durante la franja del hecho, el teléfono asociado a la línea de S registró eventos en una antena cuya área de cobertura incluye tanto el lugar del hecho como el domicilio de S. Este dato es compatible con la presencia de S en su domicilio y no permite ubicarlo en el lugar del hecho."

---

## Caso 5 — Verificación de un video en redes (OSINT)

**1. Observación.** Circula un video que muestra una represión violenta en una plaza, con la leyenda "Hoy en la ciudad C". Una cuenta con muchos seguidores lo difunde.

**2. Procedencia.** El video se descargó de una red social; los metadatos fueron eliminados por la plataforma. Se desconoce la fuente original.

**3. Hipótesis rivales.**
- H1: El video muestra un hecho real ocurrido hoy en C.
- H2: El video es real pero de otra fecha (reciclado).
- H3: El video es real pero de otro lugar.
- H4: El video fue editado o generado sintéticamente.

**4. Predicciones.**
- H1: elementos verificables coinciden con C (arquitectura, carteles, clima de hoy, sombras compatibles con la hora); no hay versiones anteriores del video en la web.
- H2: búsqueda inversa de fotogramas encuentra versiones anteriores.
- H3: los elementos visuales coinciden con otra ciudad.
- H4: artefactos visuales inconsistentes; ausencia de otras fuentes independientes.

**5. Contraste.** Búsqueda inversa de fotogramas clave; geolocalización por elementos visibles; comparación de condiciones climáticas con registros meteorológicos; búsqueda de otros videos independientes del mismo hecho; contacto con periodistas locales.

**6. Resultados sintéticos.**
- La búsqueda inversa encuentra el mismo video publicado tres años antes con otra leyenda. Favorable a H2.
- La arquitectura coincide con C. Compatible con H1 y H2.

**7. Refutación de H2.** Si se demuestra que la publicación de hace tres años es de otro video parecido y no del mismo.

**8. Alternativas.** El video original de hace tres años podría haber sido, a su vez, reciclado.

**9. Límites.** La primera aparición encontrada no es necesariamente la primera publicación. La geolocalización confirma el lugar, no la fecha.

**10. Errores posibles.** "La cuenta que lo difundió fabricó la desinformación" (pudo difundirlo de buena fe); "no hubo represión hoy en C" (el video reciclado no prueba que no haya ocurrido algo hoy).

**11. Conclusión permitida.** "El video muestra la ciudad C, pero circula en la web desde hace al menos tres años. No documenta hechos de hoy. Este hallazgo no permite afirmar ni negar que hoy hayan ocurrido hechos similares en C."

---

## Caso 6 — PDF con metadatos posteriores a la firma (análisis documental)

**1. Observación.** Un contrato firmado, presentado en un litigio, tiene fecha de firma 10 de marzo. El PDF tiene metadato de creación del 2 de junio.

**2. Procedencia.** PDF entregado por una de las partes por correo electrónico a su abogado; el abogado lo presentó. Hay hash del archivo presentado.

**3. Hipótesis rivales.**
- H1: El documento fue creado o alterado después de la fecha de firma (falsificación o antedatado).
- H2: El documento original se firmó el 10 de marzo en papel o en otro formato, y el PDF es una exportación o escaneo posterior.
- H3: El PDF fue reprocesado (por ejemplo, comprimido, reexportado o "impreso a PDF") por una herramienta que reescribe la fecha de creación.

**4. Predicciones.**
- H1: el contenido difiere de otras copias; la firma digital (si existe) no valida o es posterior; hay inconsistencias tipográficas internas.
- H2: existe un original en papel o un archivo anterior; el PDF tiene características de escaneo o exportación.
- H3: el campo "productor" indica una herramienta de reprocesamiento; la estructura interna muestra una sola revisión generada por esa herramienta.

**5. Contraste.** Solicitar el original y otras copias (la de la contraparte, correos de marzo); analizar la estructura interna del PDF (revisiones incrementales, productor); validar firmas digitales si las hay.

**6. Resultados sintéticos.**
- La contraparte tiene una copia recibida por correo el 11 de marzo; su contenido textual coincide; sus metadatos indican creación el 10 de marzo.
- El PDF presentado tiene como productor una herramienta de compresión en línea.
- Favorable a H3; contrario a H1 en cuanto al contenido.

**7. Refutación de H3.** Si el texto del PDF presentado difiere en algún punto material de la copia de marzo.

**8. Alternativas.** Que ambas copias hayan sido alteradas de manera coordinada (improbable dado que las partes están en conflicto, pero no imposible).

**9. Límites.** Que el contenido coincida con la copia de marzo no prueba que la firma sea auténtica, solo que el documento no cambió entre marzo y junio en lo textual.

**10. Errores posibles.** "Metadato posterior ⇒ falsificación"; o el inverso, "contenido coincidente ⇒ firma auténtica".

**11. Conclusión permitida.** "El PDF presentado es una versión reprocesada en junio de un documento cuyo contenido textual coincide con una copia recibida por la contraparte el 11 de marzo. La fecha de creación del PDF presentado no indica alteración del contenido. Este análisis no evalúa la autenticidad de la firma."

---

## Caso 7 — Atribución por rasgos lingüísticos y horarios (atribución)

**1. Observación.** Un malware analizado contiene cadenas en un idioma determinado y sus marcas de compilación caen en horario laboral de una zona horaria UTC+3. Un proveedor lo atribuye al grupo G, conocido por operar desde un país con esa zona horaria y ese idioma.

**2. Procedencia.** Muestra obtenida de un servicio público de análisis de malware; análisis estático propio; informe del proveedor.

**3. Hipótesis rivales.**
- H1: El malware fue desarrollado por G.
- H2: Fue desarrollado por otro actor que reutilizó código o herramientas de G.
- H3: Fue desarrollado por otro actor que insertó deliberadamente indicios falsos (bandera falsa).
- H4: Fue desarrollado por un actor sin relación con G que comparte idioma y zona horaria.

**4. Predicciones.**
- H1: coincidencias de infraestructura (servidores de comando y control), técnicas y objetivos con operaciones previas atribuidas a G con evidencia independiente; consistencia en múltiples dimensiones.
- H2: código compartido con herramientas de G que circularon públicamente o en foros; diferencias en infraestructura y objetivos.
- H3: indicios contradictorios entre sí (por ejemplo, errores idiomáticos impropios de un hablante nativo); indicios "demasiado obvios".
- H4: el idioma y la zona horaria son compartidos por muchos actores.

**5. Contraste.** Análisis de infraestructura; comparación de código con muestras atribuidas de manera independiente; examen de la calidad lingüística; evaluación de cuántos actores conocidos comparten los rasgos.

**6. Resultados sintéticos.**
- Las marcas de compilación son modificables y no hay otra evidencia temporal. Débil.
- Una función de cifrado coincide con una herramienta de G que se filtró públicamente dos años antes. Favorable a H1 y a H2 por igual.
- No hay coincidencia de infraestructura.

**7. Refutación de H1.** Si la infraestructura se vincula con otro actor, o si se encuentran indicios inconsistentes con G.

**8. Alternativas.** Actores que deliberadamente imitaron indicios de otros; el uso de banderas falsas en operaciones ofensivas ha sido discutido públicamente en informes de la industria [V2].

**9. Límites.** Idioma y zona horaria son rasgos con base rate alta: muchos actores los comparten. El código filtrado rompe la conexión entre "código de G" y "operación de G".

**10. Errores posibles.** Atribuir por rasgos fácilmente imitables; tratar la atribución del proveedor como fuente independiente cuando se basa en los mismos indicios.

**11. Conclusión permitida.** "La muestra contiene código coincidente con una herramienta atribuida a G que se filtró públicamente, y rasgos lingüísticos y horarios compatibles con G y con otros actores. Sin evidencia de infraestructura u operativa independiente, la atribución a G es **posible pero no determinada**."

---

## Caso 8 — Ausencia de alertas del EDR (respuesta a incidentes)

**1. Observación.** Tras una notificación externa de que datos de la empresa aparecieron en un foro, el gerente de seguridad informa que "el EDR no registró ninguna alerta en los últimos 90 días, por lo tanto no hubo compromiso interno".

**2. Procedencia.** Consola del EDR; reporte del gerente.

**3. Hipótesis rivales.**
- H1: No hubo compromiso interno; los datos salieron por un tercero (proveedor).
- H2: Hubo compromiso interno no detectado por el EDR (técnicas que no generan alerta, equipos sin agente).
- H3: Hubo compromiso detectado, pero las alertas fueron descartadas o no conservadas.
- H4: Los datos del foro no son de la empresa o son datos públicos reempaquetados.

**4. Predicciones.**
- H1: los datos del foro coinciden con un subconjunto que solo tenía el proveedor.
- H2: hay equipos sin agente o con agente desactivado; hay telemetría de bajo nivel (no alertas) con actividad anómala.
- H3: hay alertas en estado "cerrada" o la retención de alertas es menor a 90 días.
- H4: los datos del foro contienen información desactualizada o pública.

**5. Contraste.** Inventario de cobertura del agente; política de retención de alertas; búsqueda en telemetría cruda, no solo en alertas; análisis del contenido de los datos filtrados.

**6. Resultados sintéticos.**
- El 22% de los servidores no tiene agente.
- La retención de alertas cerradas es de 30 días.
- Los datos filtrados incluyen un campo que solo existe en la base interna.

**7. Refutación de H1.** El campo exclusivo de la base interna debilita mucho H1 y H4.

**8. Alternativas.** Exfiltración por un empleado con acceso legítimo (no requiere malware que el EDR detecte).

**9. Límites.** **Ausencia de alertas ≠ ausencia de eventos.** El valor de la ausencia depende de la cobertura y la sensibilidad del sensor.

**10. Errores posibles.** Concluir negación de compromiso por silencio del instrumento; luego, por reacción, atribuir el compromiso a un empleado sin evidencia.

**11. Conclusión permitida.** "La ausencia de alertas del EDR no es informativa sobre el 22% de los servidores sin agente, ni sobre alertas cerradas hace más de 30 días. Los datos filtrados contienen un campo propio de la base interna. **Origen de la filtración: NO DETERMINADO**; la hipótesis de ausencia de compromiso interno no está sostenida."

---

## Caso 9 — Captura de pantalla de un chat amenazante (análisis documental / judicial)

**1. Observación.** Una persona presenta una captura de pantalla de un chat en el que el contacto "Martín" envía una amenaza.

**2. Procedencia.** Imagen PNG enviada por la denunciante. Sin acceso inicial al teléfono.

**3. Hipótesis rivales.**
- H1: La captura reproduce fielmente un mensaje enviado por la persona M.
- H2: La captura reproduce un mensaje real, pero enviado desde una cuenta de M usada por otra persona.
- H3: La captura es una composición o edición.
- H4: El mensaje es real pero fuera de contexto (cita, broma, respuesta a otro mensaje).
- H5: El contacto "Martín" en el teléfono de la denunciante no corresponde a M (nombre de contacto asignado localmente).

**4. Predicciones.**
- H1: el mensaje existe en el teléfono de la denunciante y en el de M (o en el servidor si es recuperable); el número asociado al contacto es el de M.
- H3: inconsistencias de interfaz (tipografías, márgenes, hora del sistema), ausencia del mensaje en el dispositivo.
- H4: mensajes anteriores y posteriores cambian el sentido.
- H5: el número del contacto no es el de M.

**5. Contraste.** Extracción forense del teléfono de la denunciante (con consentimiento o autorización); verificación del número; examen de la conversación completa; eventualmente, del dispositivo de M.

**6. Resultados sintéticos.**
- El mensaje existe en el teléfono; el número es el de M; los mensajes previos muestran una discusión escalando.
- Contrario a H3 y H5; H4 no explica el contenido amenazante.

**7. Refutación de H2.** Evidencia de que el teléfono de M estaba en poder de otra persona en ese momento.

**8. Alternativas.** Mensaje programado o enviado por un tercero con acceso al teléfono de M.

**9. Límites.** La captura sola era un icono con indicialidad desconocida; la extracción del dispositivo aporta la conexión indicial con la cuenta, no con la persona.

**10. Errores posibles.** Tratar la captura como prueba suficiente por su iconicidad ("se ve real"); o descartarla por ser "solo una captura" cuando hay corroboración.

**11. Conclusión permitida.** "El mensaje de la captura existe en el teléfono de la denunciante, en una conversación con el número de M. La autoría personal de M es compatible con la evidencia; la evidencia no excluye que otra persona usara su teléfono."

---

## Caso 10 — Cinco informes coinciden (inteligencia / OSINT)

**1. Observación.** Cinco informes públicos de distintas organizaciones atribuyen una campaña al actor A. Un analista escribe "atribución corroborada por cinco fuentes independientes".

**2. Procedencia.** Informes públicos en sitios de las organizaciones.

**3. Hipótesis rivales.**
- H1: Las cinco organizaciones llegaron a la atribución por evidencia independiente.
- H2: Una organización hizo el análisis original y las demás lo replicaron o citaron.
- H3: Todas usan el mismo proveedor de telemetría o la misma base de indicadores.

**4. Predicciones.**
- H1: cada informe aporta evidencia técnica distinta (muestras, infraestructura, víctimas) no presente en los demás.
- H2: los informes posteriores citan al primero, repiten sus indicadores y no agregan evidencia propia.
- H3: los indicadores coinciden exactamente y provienen de la misma fuente.

**5. Contraste.** Construir un grafo de citas; comparar indicadores; identificar qué evidencia original aporta cada informe; ordenar por fecha.

**6. Resultados sintéticos.**
- El informe 1 aporta análisis de muestras e infraestructura. Los informes 2, 3 y 4 lo citan y repiten sus indicadores. El informe 5 aporta una muestra nueva, pero su atribución se apoya en la del informe 1.
- Raíces independientes de evidencia de atribución: 1 (con un aporte parcial del 5).

**7. Refutación de H2.** Si los informes 2–4 contienen evidencia técnica propia no derivada del 1.

**8. Alternativas.** El informe 1 pudo apoyarse, a su vez, en información no publicada de otra fuente.

**9. Límites.** La cantidad de fuentes no mide la cantidad de evidencia independiente.

**10. Errores posibles.** Corroboración circular; falso consenso.

**11. Conclusión permitida.** "La atribución a A se apoya esencialmente en un análisis original (informe 1), replicado por otros tres y complementado parcialmente por un quinto. El nivel de corroboración independiente es bajo. La atribución depende de la solidez del análisis original, que debe evaluarse por sí mismo."

---

## Caso 11 — Descarga masiva antes de una renuncia (insider / base rates)

**1. Observación.** La cuenta del empleado R descargó 9 GB del repositorio de documentos la noche anterior a presentar su renuncia. Un sistema de alerta lo marca como "posible exfiltración por insider".

**2. Procedencia.** Logs del repositorio documental; alerta de un sistema de análisis de comportamiento.

**3. Hipótesis rivales.**
- H1: R exfiltró información para uso no autorizado.
- H2: R descargó sus propios materiales de trabajo (permitidos) o hizo una copia de traspaso.
- H3: Un proceso automático (sincronización de cliente de escritorio) descargó los archivos con la cuenta de R.
- H4: Otra persona usó la cuenta de R.

**4. Predicciones.**
- H1: los archivos descargados incluyen material fuera de su área; hay transferencia posterior a medios externos o servicios personales.
- H2: los archivos son de su área; hay instrucciones de traspaso; se entregaron a su reemplazo.
- H3: el agente de usuario es el cliente de sincronización; hay patrones similares en otras fechas.
- H4: inicio de sesión desde un dispositivo no habitual.

**5. Contraste.** Revisar agente de usuario y dispositivo; listar los archivos; buscar transferencias posteriores; consultar con la jefatura sobre el traspaso; revisar descargas de otros empleados en contextos similares.

**6. Resultados sintéticos.**
- El agente de usuario es el cliente de sincronización recién reinstalado en una notebook nueva de R.
- En el último año, el 70% de las alertas de este tipo en la empresa correspondieron a reinstalaciones del cliente.
- No hay transferencias a medios externos registradas (el equipo tiene control de USB y proxy).

**7. Refutación de H3.** Evidencia de que los archivos se copiaron luego a un destino externo.

**8. Alternativas.** Exfiltración por medios no registrados (fotografías de pantalla, otro dispositivo).

**9. Límites.** La alerta tiene una tasa de falsos positivos alta en este contexto (base rate). La ausencia de transferencias registradas depende de la cobertura de controles.

**10. Errores posibles.** Tratar la alerta como hallazgo; inferir intención por coincidencia temporal con la renuncia. **Coincidencia temporal no es causalidad.**

**11. Conclusión permitida.** "La descarga fue realizada por el cliente de sincronización en un dispositivo nuevo de R, patrón que en la organización corresponde mayoritariamente a reinstalaciones. No hay evidencia de transferencia a destinos externos dentro de la cobertura de los controles. La alerta no está sostenida como exfiltración."

---

## Caso 12 — Resumen generado por un LLM en un triage (respuesta a incidentes asistida por IA)

**1. Observación.** Un asistente basado en un modelo de lenguaje, integrado en la consola del SOC, resume 2.000 líneas de logs y concluye: "Se detectó movimiento lateral desde WS-14 hacia SRV-DB usando credenciales de administrador. Severidad: crítica."

**2. Procedencia.** Salida generada por el modelo a partir de los logs que le pasó la consola; el prompt y la versión del modelo están registrados; los logs de entrada están disponibles.

**3. Hipótesis rivales.**
- H1: El resumen describe correctamente un movimiento lateral presente en los logs.
- H2: Los logs contienen accesos administrativos legítimos (tareas programadas, herramientas de gestión) que el modelo interpretó como movimiento lateral.
- H3: El modelo combinó eventos no relacionados en una narrativa coherente (confabulación).
- H4: El resumen está influido por el contenido de los logs que contiene texto con instrucciones o sugerencias (por ejemplo, un nombre de archivo o un comentario manipulado).

**4. Predicciones.**
- H1: existen eventos de autenticación de red desde WS-14 a SRV-DB con una cuenta administrativa, en una secuencia temporal coherente, y atípicos respecto del historial.
- H2: esos eventos existen pero coinciden con tareas documentadas y se repiten en días normales.
- H3: los eventos citados no existen o no están relacionados temporalmente.
- H4: hay cadenas de texto en los logs que coinciden con la narrativa del resumen.

**5. Contraste.** Reconstruir, con consultas deterministas sobre los logs, cada afirmación del resumen; comparar con el historial; verificar cada entidad (equipo, cuenta, hora) mencionada.

**6. Resultados sintéticos.**
- Hay inicios de sesión de red desde WS-14 a SRV-DB con la cuenta `svc_admin`, los mismos días y horas desde hace seis meses (tarea de backup). Favorable a H2.
- No hay evidencia de ejecución de herramientas en SRV-DB.

**7. Refutación de H2.** Eventos fuera del patrón habitual (otro horario, otra cuenta, ejecución de procesos no habituales).

**8. Alternativas.** Que el patrón regular oculte actividad maliciosa que imita la tarea (posible pero no sostenido por evidencia adicional).

**9. Límites.** El resumen generativo es un **interpretante** producido por un sistema cuya relación con el objeto (los eventos) no es directamente verificable sin reconstrucción. No es una observación.

**10. Errores posibles.** Tratar el resumen como hallazgo; escalar severidad sin verificación; o, inversamente, descartar todo lo que dice un LLM sin examinarlo.

**11. Conclusión permitida.** "Los eventos que el resumen describe como movimiento lateral corresponden, en la verificación determinista, a una tarea de backup recurrente. No se sostiene la conclusión del resumen. Se recomienda que los resúmenes generativos se traten como hipótesis a verificar y no como veredictos." (Esta conclusión anticipa la discusión de la Parte VII sobre separación entre veredicto determinista y explicación generativa.)

---

## 3. Patrones transversales

| Patrón | Casos | Lección peirceana [APLIC] |
|---|---|---|
| Índice del último salto, no del origen | 1, 4 | Preguntar de qué es índice con seguridad. |
| Integridad confundida con atribución | 3 | El hash es índice de bytes. |
| Regla de interpretación equivocada (terceridad) | 2, 6, 12 | Conocer el legisigno del sistema. |
| Ausencia de registro tratada como ausencia de evento | 8 | La ausencia vale según la cobertura. |
| Iconicidad confundida con autenticidad | 5, 9 | Una imagen convincente puede tener indicialidad débil. |
| Fuentes dependientes como corroboración | 10 | Contar raíces independientes. |
| Base rate ignorada | 4, 7, 11 | Preguntar cuántos otros casos producen el mismo indicio. |
| Coincidencia temporal tomada por causalidad | 11 | Proximidad no es conexión real. |
| Explicación generativa tomada por observación | 12 | Un interpretante no es un hecho bruto. |

---

[Índice](00-indice-y-estrategia.md) · Siguiente: [Parte VI — Peirce y los límites de la prueba](06-parte-VI-limites-prueba.md)
