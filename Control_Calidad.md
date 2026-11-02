# Revisión de entrega del Laboratorio 4

Documento interno de organización; no forma parte del ZIP mínimo exigido por el enunciado.

## Comprobación técnica y documental

Se revisaron el enunciado y los criterios de Nivel 4 de la rúbrica de catorce páginas frente a la versión actual del notebook, que incorpora los cambios del compañero. La ejecución guardada contiene **14 celdas de código en orden, de 1 a 14, y 32 figuras**. Esta revisión editorial conserva los fuentes de código, las salidas numéricas y los PNG; no vuelve a entrenar ni evaluar prueba.

| Criterio | Evidencia actual |
|---|---|
| Pipeline y máscaras | RGB y xy normalizados, cinco características, pesos modificables, casos solo color/posición y pesos nulos rechazados, comprobaciones de tamaños y NEAREST. |
| Selección de K | Diez razones distintas y siete K entre 2 y 8 para las quince imágenes de ajuste: 1050 registros; silueta sobre 1000 píxeles, semilla 42. |
| Construcción de máscara | Reglas oscuro y central con fórmulas explícitas y sin referencias como entrada; comparación de los tres casos en que eligen grupos diferentes. |
| Ajuste | Veinte configuraciones del barrido y recomendación IAG adicional, con Dice y V-measure, variabilidad, K y análisis de fallos. |
| Configuración final | C05/central, β=1 y λ=0.75, seleccionada por Dice medio 0.8615; procedimiento de K fijado por silueta. |
| Prueba | Cinco imágenes, seis métricas exigidas, paneles y comparación con ajuste. Dice medio 0.8941. |
| Análisis 1 y 2 | Efecto de posición con mejoras y deterioros identificados; comparación de K, silueta, Dice y V-measure con valores reales. |
| Análisis 3 | Diferencia ajuste/prueba, precisión y recall, mejores/peores casos y explicación del protocolo. |
| Análisis 4 | Dos limitaciones vinculadas a RGB, posición, K-Means y mapas de errores. |
| Análisis 5 | FP/FN con casos concretos, riesgos para DermAlpes, generalización y referencia verificable sobre representatividad. |
| Verificación IAG | Respuesta completa e implementación fiel de β=1, λ=0.35, K=3 y su regla de máscara; quince evaluaciones y análisis. Dice medio 0.8061. La documentación contiene un resumen de la consulta; la exportación original con seguimientos no está en el repositorio. |
| Declaración y aportes | Herramientas, usos, prompts resumidos, evaluación crítica y aportes personales documentados por el equipo en la última sección. No corresponde mantener la antigua nota de aportes por registrar. |
| Bono A | PCA por grupo y referencia, 72.60 % de varianza retenida e interpretación. |
| Bono B | Mean Shift con bandwidth explícito, misma muestra para comparación, grupos, máscaras, Dice y tiempos. |
| Video | El guion es un recurso interno. La guía exige la grabación de máximo tres minutos; no hay archivo audiovisual en el repositorio. |

## Limpieza de esta revisión

- Se actualizaron los documentos internos que describían una evaluación parcial de IA o aportes humanos sin registrar; la versión actual ya contiene esas secciones y una ejecución completa.
- Se retiraron etiquetas de metadatos que describían kernels auxiliares antiguos. Se mantuvieron los tiempos y contadores de la ejecución completa actual.
- Se archivaron los informes JSON de revisiones anteriores en `tmp/auditoria_historica/`, para que no se confundan con la verificación vigente.
- Se precisaron afirmaciones sobre el puntaje de borde, la diferencia entre configuraciones y el efecto de la posición. No se afirma un empate estadístico ni se extrapola un caso a todas las lesiones pequeñas.
- La representatividad de pacientes de DermAlpes se presenta como riesgo de transferencia, no como una diferencia demográfica medida. La referencia de Wen et al. (2022) incluye DOI y distingue sus conjuntos de las veinte imágenes del laboratorio.
- Se resumió un prompt histórico que estaba redactado como solicitud de trabajo sin terminar. Se conserva el análisis crítico de errores iniciales y la declaración de IA, que exige la guía.
- Se regeneró el HTML y se verificaron sus imágenes incrustadas. No requiere la carpeta de PNG externos para visualizarse.

## Archivos de entrega

El ZIP mínimo contiene el notebook `.ipynb`, su `.html`, la respuesta `consulta_IAG.md`, el historial real de la consulta (en ese archivo o como adjunto) y el video grabado. Si la plataforma recibe el video aparte, se entrega en ese espacio.

No se incluyen `solicitud_usuario.txt`, `Guion_Video.md`, `Control_Calidad.md`, README, requirements, Git, temporales, informes JSON, figuras/CSV externos, enunciado, rúbrica o archivos `.DS_Store`. La guía no solicita esos elementos como entregables. `data/` y `requirements.txt` se necesitan para ejecutar desde cero, pero no para leer el notebook ejecutado o el HTML, y no aparecen como entregables explícitos en el enunciado.

## Comprobaciones antes de subir

1. Incluir el video desde su ubicación real y comprobar que dura como máximo tres minutos.
2. Adjuntar el historial real de Gemini con prompt, respuesta y mensajes de seguimiento si se conserva. El resumen y la respuesta evaluada están disponibles, pero no equivalen a la exportación íntegra que pide la actividad de verificación.
3. Confirmar el registro de ambos integrantes en el grupo de Bloque Neón y cargar los archivos en los campos que disponga la plataforma.

No se inventan conversaciones ni se marca como entregado un archivo audiovisual que no está en esta carpeta.
