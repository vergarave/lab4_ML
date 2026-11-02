# Control de calidad contra el enunciado y la rúbrica

Revisión del 2 de noviembre de 2026, actualizada al incorporar la **respuesta real de consulta_IAG.md** aportada por el integrante. Se contrastó el enunciado completo y se inspeccionaron las 14 páginas de la rúbrica, especialmente Nivel 4. Esta lista aporta evidencia de cumplimiento; no asigna una nota.

## Corrección sobre la consulta de IA

El archivo del proyecto contenía un aviso creado por el agente después de no localizar la respuesta fuera de la carpeta del laboratorio. Fue incorrecto convertir esa falta de localización en la afirmación de que el integrante no había aportado una consulta. Se sustituyó el aviso por una **copia exacta** de `C:\Users\daniv\Downloads\consulta_IAG.md`, sin modificar el documento aportado. La igualdad se comprobó mediante SHA-256.

La respuesta recomienda β=1, λ=0.35, K=3 fijo y la puntuación **0.5·D + 0.3·C + 0.2·(1−B)**, con luminancia ponderada y un marco del 10 %. B utiliza como denominador **todos los píxeles del marco**. La implementación y evaluación ya están completas para las quince imágenes de ajuste. El documento contiene una respuesta, pero no incluye el prompt original, las fechas ni los mensajes previos: falta adjuntar ese historial para acreditar las condiciones de envío y secuencia de la consulta. Los ejemplos reconstruidos de prompts siguen identificados como tales.

La evaluación de la respuesta se integró durante esta corrección, después de la ejecución original. El orden de las secciones del notebook permite reproducirla antes de seleccionar el método, pero no se afirma que ese haya sido el orden de la primera ejecución. La corrección solo leyó imágenes de ajuste; no modificó ni volvió a ejecutar la evaluación de prueba.

## Evidencia de ejecución y resultados

- Barrido obligatorio: **1050 modelos** = 15 imágenes × 10 combinaciones × 7 K, con 300 evaluaciones de máscaras sobre las agrupaciones seleccionadas.
- Consulta real: **15 modelos adicionales**, uno por imagen, con K=3 fijo. Total de modelos principales en ajuste: **1065**. La consulta no reemplaza ninguna combinación ni K exigidos.
- Tabla original: 20 configuraciones. Tabla ampliada: **21**, incluyendo la recomendación real.
- Consulta IAG: Dice **0.806085 ± 0.171746**, V-measure **0.395244**, silueta **0.385143**, precisión **0.877864**, recall **0.805471**; posición **11/21** por Dice medio.
- Mejor caso IAG: `ISIC_0000137`, Dice **0.939454**. Peor: `ISIC_0000094`, Dice **0.271045**, precisión **0.156941**, 6097 FP. Mejora cuatro imágenes respecto al método final y empeora once.
- El ganador sigue siendo **β=1, λ=0.75, criterio central**, con K por máximo de silueta entre 2 y 8. Dice medio de ajuste **0.861520** y de prueba **0.894093**. Diferencia respecto a la recomendación IAG en ajuste: **+0.055435**.
- Notebook: **14 celdas de código con ejecución visible**, sin errores registrados, y **32 figuras**: 30 originales y dos nuevas de la recomendación IAG.
- Las nuevas celdas se ejecutaron en un kernel auxiliar con las funciones del notebook y solo datos de ajuste. El resto conserva las ejecuciones originales; los contadores provienen de esos contextos y pueden repetirse. No se simula una ejecución completa nueva.
- `resultados/restauracion_consulta_IAG.json` conserva la fuente, hash, implementación y comprobación de integridad de la celda de prueba. `validacion_entrega.json` documenta la auditoría actualizada.

## Comprobación de los criterios de Nivel 4

| Criterio y página de rúbrica | Estado | Sección del notebook | Evidencia y límites |
|---|---|---|---|
| Pipeline y máscaras, p. 2 | Completo técnico | 1–3 | Cinco columnas, RGB/xy normalizados, set_params, casos extremos y pesos nulos rechazados, tamaños originales y finales, máscaras binarias con NEAREST. Métricas a resolución reducida. |
| Selección de K, p. 3 | Completo técnico | 4 y 6 | Diez razones distintas, solo color y solo posición; siete K por imagen; 1050 filas en `ajuste_exploracion_k.csv`; muestra de 1000 y semilla 42. La consulta adicional mantiene K=3 para evaluar fielmente su recomendación. |
| Regla automática, p. 4 | Completo técnico | 4 y 5 | Oscuro y central sin máscaras como entrada. Regla IAG independiente con fórmula, luminancia, normalización, marco y denominador explícitos. No se inventan filtros opcionales sin umbrales. |
| Ajuste y configuración final, p. 5 | Completo técnico | 6 | Comparación de 20 configuraciones y tabla ampliada de 21 con IAG, variabilidad, casos de fallo y máximo Dice de ajuste. Ganador conservado. La consulta se integró durante la corrección; secuencia real declarada. |
| Evaluación y presentación, p. 6 | Completo técnico | 6–7 | Dos mejores y extremos para las 15 imágenes de ajuste; cinco paneles de prueba y tabla con K, silueta, Dice, V-measure, precisión y recall. Prueba original intacta. |
| Preguntas 1–2, p. 7 | Completo técnico | 8 | Mejora con posición en 0000114 y deterioro en 0000094, cifras y mapas; distribución de K, correlaciones y contraejemplos. No es una comparación a K fijo. |
| Pregunta 3, p. 8 | Completo técnico | 8 | Medias, desviaciones, diferencia +0.0326 y precisión/recall; casos de prueba y explicación de por qué no reajustar con sus referencias. |
| Pregunta 4, p. 9 | Completo técnico | 8 | RGB y omisiones en 0000116; expansión geométrica en 0000094; relación con espacio y regla de máscara. Causas interpretadas sin diagnósticos. |
| Pregunta 5, p. 10 | Completo técnico | 8 | FN de 0000087 y FP de 0000123, área y contorno; tonos de piel, iluminación y equipo; falta de metadatos y validación independiente. |
| Video, p. 11 | Pendiente humano | 9 y `Guion_Video.md` | Guion preparado con cifras verificadas. Falta grabar, cronometrar y entregar el video. |
| Consulta y verificación IAG, p. 12 | Evaluación completa; historial parcial | 5, 6 y declaración final | Respuesta íntegra, código fiel, 15 resultados, comparación de 21 configuraciones, dos figuras y crítica de aciertos/fallos. Falta prompt e historial originales para documentar condiciones y secuencia de la consulta. |
| Declaración, prompts y aportes, p. 12 | Parcial documental | Última sección | Gemini 4 Argon y GPT 6 Astra según el integrante; asistencia efectiva de Codex declarada; respuesta real diferenciada de prompts reconstruidos. Falta registrar aportes personales reales. |
| Bono A, p. 13 | Ejecutado | Bonos | Dos PCA sobre los mismos píxeles, por grupo y referencia; 72.60 % de varianza y análisis de superposición. Calificación sujeta al cumplimiento obligatorio. |
| Bono B, p. 14 | Ejecutado | Bonos | Mean Shift: bandwidth 0.258085, comparación sobre la misma muestra, grupos/máscaras/Dice/tiempos y figuras. Solo una imagen y un ancho de banda; mismo condicionamiento de bonos. |

Las páginas 1 y 14 también incluyen portada/tabla global y se revisaron. El título del criterio de video dice “VuelaAlpes”, pero el caso y su descripción son DermAlpes: se sigue el enunciado.

## Correcciones técnicas conservadas

1. La plantilla abría prueba al inicio pese a indicar que solo verificaba archivos. Se separaron carga de imagen y máscara; prueba se utiliza después de congelar el método y la máscara se lee después de predecir.
2. Las dimensiones se comprobaban solo después de redimensionar. Se verifica también la coincidencia original.
3. La validación de pesos solo ocurría en fit. Se valida también después de set_params al transformar.
4. La consulta hipotética β=1, λ=0.5, K=3 no se presenta como respuesta real. La respuesta auténtica es β=1, λ=0.35, K=3 y ya está evaluada.
5. Se conservaron los transformadores y el barrido basados en P11/P13, y se simplificaron las reglas del método principal. La regla real de IAG se implementa por separado para no confundir fórmulas o denominadores.
6. Se conserva la relación de aspecto con lado mayor 160. Se justifican la resolución y el muestreo de silueta, sin atribuir precisión de bordes originales.
7. Se retiraron dependencias opcionales no utilizadas y conclusiones anticipadas. El análisis distingue cifras, observaciones visuales e hipótesis.

## Reproducibilidad y archivos

El notebook usa rutas relativas, versiones en `requirements.txt`, semilla 42, 10 inicializaciones, tolerancia 0.0001 y hasta 300 iteraciones. Las métricas se calculan sobre todos los píxeles de trabajo. Solo silueta usa una muestra. El documento real se muestra íntegro y el código de evaluación no depende de rutas de Downloads; esa ruta se conserva únicamente como procedencia en el informe.

Los nuevos archivos `iag_ajuste_detalle.csv`, `iag_clusters.csv`, `iag_comparacion_configuraciones.csv`, `iag_comparacion_por_imagen.csv`, `iag_etiquetas_ajuste.npz` y las figuras IAG permiten comprobar la evaluación. La elección de K del método principal y la tabla de prueba original permanecen intactas. Las fuentes y salidas de la celda de prueba se comprobaron mediante hash antes y después de integrar esta corrección.

La declaración de IA permanece en la última celda, después del bloque independiente de bonos, según la petición del integrante. Se preservan el enunciado, la rúbrica, datos originales y prácticas. `.gitignore` permite compartir los 20 JPG y las 20 máscaras, ya rastreados por Git.

## Acciones humanas pendientes

1. Adjuntar el prompt y el historial originales de la consulta, con la información de secuencia que exista. No sustituirlos por los ejemplos reconstruidos ni inventar fechas. La respuesta real y su evaluación ya están incorporadas.
2. Validar nombres, código y conclusiones, y registrar qué desarrolló, modificó o aprendió cada integrante.
3. Grabar un video de máximo tres minutos a partir de `Guion_Video.md`, revisar duración y entregarlo según el curso.
4. Registrar ambos integrantes en el grupo de Bloque Neón y entregar notebook, HTML, video e historial cuando corresponda. La fecha ordinaria del enunciado es el 2 de noviembre a las 8:00 p. m., Bogotá; comprobar anuncios del curso si hubiera cambios.

Las instrucciones exactas de ejecución y exportación están en `README.md`. Los resultados guardados permiten consultar la entrega sin repetir los experimentos.
