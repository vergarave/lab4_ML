# Laboratorio 4 — Segmentación de lesiones para DermAlpes

ISIS-2611, Universidad de los Andes. Integrantes: Julian Pinto y Daniel Vergara.

Se representan los píxeles mediante RGB y posición normalizados, se agrupan con K-Means y se construye una máscara automática. La partición oficial contiene 15 imágenes de ajuste y 5 de prueba. Las prácticas P11, P12 y P13 son las referencias metodológicas.

## Resultados

La configuración elegida es β=1, λ=0.75 y criterio central, con K por máximo de silueta entre 2 y 8. Dice medio: **0.8615 en ajuste** y **0.8941 en prueba**. La recomendación de IA, evaluada con β=1, λ=0.35 y K=3 fijo, obtiene **0.8061** en ajuste. El notebook contiene las tablas, 32 figuras, las cinco respuestas de análisis, la declaración de IA y ambos bonos.

## Entrega exigida por la guía

Para el ZIP de entrega:

1. `Lab4_Segmentacion_Imagenes.ipynb`, con ejecuciones y nombres de ambos integrantes.
2. `Lab4_Segmentacion_Imagenes.html`, con los mismos resultados y figuras visibles.
3. `consulta_IAG.md`, que conserva la respuesta evaluada.
4. El historial original de esa consulta, con prompt, respuesta y mensajes posteriores. Puede estar incorporado al documento de consulta o adjuntarse como exportación/capturas legibles. Actualmente el notebook contiene un resumen del prompt y `consulta_IAG.md` contiene la respuesta, pero el historial original no está en el repositorio.
5. El video explicativo de máximo tres minutos, dirigido a DermAlpes. No se encontró un archivo de video en este repositorio; si está guardado en otro lugar, se adjunta desde allí. Si Bloque Neón lo recibe en un campo independiente, se entrega en ese campo.

La guía no establece un nombre obligatorio para el ZIP. No exige entregar el repositorio entero. También debe estar registrado el grupo de ambos integrantes en Bloque Neón.

**Archivos internos que se excluyen del ZIP mínimo:** `solicitud_usuario.txt`, `Guion_Video.md`, `Control_Calidad.md`, este README, `requirements.txt`, `.gitignore`, `gitignore.txt`, `.git/`, `tmp/`, `resultados/`, `.DS_Store`, la guía y la rúbrica.

Los datos y `requirements.txt` son recursos para reproducir el cálculo, no entregables explícitos de la guía. **Para abrir los resultados ya ejecutados no se necesita `data/` ni `resultados/`. Para ejecutar desde cero sí se necesita `data/`** con las veinte imágenes y sus máscaras. Si el docente pide un paquete autosuficiente para ejecución, se incorporan `data/` y `requirements.txt`; esa exigencia adicional no aparece en el enunciado local.

## Datos y reproducción local

Fuente: [ISIC 2016, segmentación de lesiones](https://challenge.isic-archive.com/landing/2016/37/), selección suministrada por el curso. Los JPG están en `data/images/` y las máscaras en `data/masks/`, con nombres como `ISIC_0000085.jpg` e `ISIC_0000085_Segmentation.png`. La partición y los identificadores completos están en el notebook. Los cuarenta archivos están rastreados por Git para compartirlos con el compañero.

El lado mayor de cada imagen se reduce a 160 píxeles manteniendo proporciones. K-Means usa todos los píxeles de trabajo; silueta usa 1000 sin reemplazo, semilla 42. El barrido obligatorio contiene 1050 modelos y la recomendación de IA añade quince. No se necesita GPU.

Desde esta carpeta, en PowerShell con Python 3.12:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m ipykernel install --user --name lab4 --display-name "Python (Lab4)"
.\.venv\Scripts\python.exe -m nbconvert --to notebook --execute --inplace --ExecutePreprocessor.kernel_name=lab4 --ExecutePreprocessor.timeout=3600 Lab4_Segmentacion_Imagenes.ipynb
.\.venv\Scripts\python.exe -m nbconvert --to html --template classic Lab4_Segmentacion_Imagenes.ipynb
```

También puede ejecutarse en VS Code seleccionando el entorno y ejecutando todas las celdas en orden. El notebook genera `resultados/` automáticamente y sobrescribe los archivos derivados. Reproducir el método fijo no autoriza reajustarlo usando las máscaras de prueba.
