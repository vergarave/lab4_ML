# Laboratorio 4: segmentación para DermAlpes

ISIS-2611, Universidad de los Andes. K-Means sobre RGB y posición con evaluación separada: 15 imágenes de ajuste y 5 de prueba. Referencias principales: prácticas oficiales P11, P12 y P13 de 202620.

## Archivos

- `Lab4_Segmentacion_Imagenes.ipynb`: implementación, ejecuciones, figuras y análisis.
- `Lab4_Segmentacion_Imagenes.html`: lectura del notebook sin Python.
- `resultados/`: CSV de los experimentos, configuración congelada y figuras.
- `consulta_IAG.md`: respuesta real de IA aportada por el integrante y preservada íntegramente; su recomendación se implementa y evalúa en el notebook.
- `Control_Calidad.md`: revisión criterio por criterio y pendientes.
- `Guion_Video.md`: guion; **no sustituye el video grabado**.
- `requirements.txt`: versiones usadas para reproducir.
- `solicitud_usuario.txt`: solicitud real de revisión, para transparencia de IA.

## Datos

Fuente: [ISIC 2016, segmentación de lesiones](https://challenge.isic-archive.com/landing/2016/37/), selección proporcionada por el curso. Colocar exactamente los 20 JPG en `data/images/` y las 20 máscaras en `data/masks/`, con nombres `ISIC_0000085.jpg` e `ISIC_0000085_Segmentation.png`, etc. La lista completa y la partición fija están en el notebook y el enunciado. Los 20 JPG y las 20 máscaras se conservan en `data/` y se incluyen en el repositorio para compartirlos con el compañero. `.gitignore` permite `data/images/` y `data/masks/`; los 40 archivos ya están rastreados por Git. El compañero los recibirá al hacer `git pull` después de que los cambios estén confirmados y publicados en la rama compartida.

## Ejecución en Windows (PowerShell, desde esta carpeta)

Se verificó Python 3.12.10. No se necesita GPU. Para instalar dependencias en un entorno aislado:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m ipykernel install --user --name lab4 --display-name "Python (Lab4)"
.\.venv\Scripts\python.exe -m nbconvert --to notebook --execute --inplace --ExecutePreprocessor.kernel_name=lab4 --ExecutePreprocessor.timeout=3600 Lab4_Segmentacion_Imagenes.ipynb
.\.venv\Scripts\python.exe -m nbconvert --to html --template classic Lab4_Segmentacion_Imagenes.ipynb
```

También se puede abrir el notebook en VS Code, seleccionar ese entorno y ejecutar todas las celdas en orden desde un kernel limpio. La ejecución recalcula los experimentos y sobrescribe los resultados derivados. Los resultados de prueba ya están visibles: repetir sirve para reproducir **el mismo método**, no para ajustar parámetros a prueba. Si se quiere conservar esta ejecución, copiar primero el notebook y `resultados/`.

El lado mayor se reduce a 160 píxeles conservando proporciones; K-Means usa todos los píxeles de trabajo, silueta usa 1000 (semilla 42). El barrido obligatorio explora 1050 modelos en ajuste; la consulta real añade 15 modelos con K=3 fijo. El barrido original tardó aproximadamente 219 segundos; los tiempos dependen del equipo y se limita el paralelismo a un hilo. Las métricas no equivalen a una evaluación en resolución original.

La recomendación real usa β=1, λ=0.35, K=3 y una regla con luminancia, centralidad y marco del 10 %. Obtiene Dice medio de ajuste **0.8061**, frente a **0.8615** de C05/central. La tabla ampliada compara 21 configuraciones. La integración de esta consulta se ejecutó como una corrección sobre las 15 imágenes de ajuste; conserva las ejecuciones originales del resto del notebook, incluida prueba. Por ello algunos contadores de celdas pueden repetirse. No se afirma que esta corrección hubiera estado incluida en la ejecución inicial.

## Antes de entregar

Revisar `Control_Calidad.md`, validar nombres y aportes de los integrantes y grabar un video de máximo tres minutos usando el guion. La respuesta real de IA y su evaluación ya están incorporadas; falta adjuntar el prompt y el historial originales para documentar las condiciones de la consulta y su secuencia. No sustituirlos por ejemplos reconstruidos ni inventar fechas. Entregar el `.ipynb`, el `.html` y el video según Bloque Neón; comprobar el registro de ambos integrantes. Los bonos están sujetos a completar las actividades obligatorias.
