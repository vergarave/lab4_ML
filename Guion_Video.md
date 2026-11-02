# Guion para DermAlpes — máximo 3 minutos

**Uso:** guion de apoyo basado en resultados ejecutados. El entregable audiovisual es la grabación de máximo tres minutos. Aproximadamente 320 palabras; ensayar a ritmo natural y mantener el video bajo tres minutos. No leer títulos ni nombres de archivos.

## 0:00–0:25 · El problema

“DermAlpes necesita ayudar a sus especialistas a delimitar lesiones en fotografías de piel. Nuestra herramienta propone una región para revisar y medir; no determina si una lesión es benigna o maligna y no reemplaza al dermatólogo.

Trabajamos con veinte imágenes y sus delimitaciones de referencia: quince para elegir el método y cinco reservadas para evaluarlo.”

**Mostrar:** una imagen y su máscara de referencia.

## 0:25–1:05 · Cómo funciona

“Representamos cada píxel por su color y su posición. K-Means reúne píxeles parecidos en grupos. Probamos entre dos y ocho grupos y elegimos la separación más clara mediante una medida llamada silueta.

Después debemos decidir qué grupo representa la lesión. La regla seleccionada favorece grupos oscuros y centrales, y penaliza los que ocupan el borde de la fotografía. Ese grupo se convierte en la región blanca de la máscara.

Comparamos diez combinaciones de color y posición, y dos reglas, usando solamente las quince imágenes de ajuste.”

**Mostrar:** `resultados/ajuste_ISIC_0000133.png`, primera fila. Señalar original, grupos y máscara.

## 1:05–1:50 · Resultados reales

“Elegimos el método con mayor coincidencia promedio con las referencias. La medida Dice va de cero a uno: uno significa coincidencia perfecta. Obtuvimos 0,862 en ajuste y 0,894 en las cinco imágenes nuevas, sin cambiar el método después de evaluarlas.

El mejor caso de prueba alcanzó 0,937: la región central se recupera bien, aunque faltan algunos píxeles del borde. El peor alcanzó 0,837: la máscara omite una parte visible de la lesión. Estos promedios no garantizan el mismo resultado para cada paciente.”

**Mostrar:** `resultados/prueba_ISIC_0000128.png` y `resultados/prueba_ISIC_0000087.png`. Verde=aciertos; azul=lesión omitida.

## 1:50–2:40 · Errores y precauciones

“Si incluimos piel como lesión, podemos sobreestimar el área. Si dejamos lesión fuera, podemos subestimarla. También vimos regiones oscuras del fondo confundidas con lesión y cambios de resultado al dar más peso a la posición.

Las imágenes se redujeron para hacer viable el cálculo, por lo que no evaluamos el detalle de los bordes originales. Solo cinco imágenes de prueba son insuficientes para asegurar funcionamiento en otras poblaciones, tonos de piel, equipos o iluminación.

La propuesta es una ayuda visual que requiere revisión de cada contorno y validación independiente antes de otro uso.”

**Mostrar:** mapa de errores de `ISIC_0000123` y cerrar con “Delimitación de apoyo · No diagnóstico”.

## Fuera del guion: control de entrega

Revisar las cifras en `resultados/prueba_metricas.csv`. Los integrantes deben entender y validar personalmente el contenido. La respuesta real de `consulta_IAG.md` ya se implementó y evaluó en ajuste; su Dice medio fue 0.8061 y no desplazó al método final. Falta adjuntar el prompt y el historial originales para completar la evidencia de consulta. El video grabado debe ajustarse a la duración real, no solo a estos tiempos orientativos.
