# Guion para DermAlpes — máximo 3 minutos

**Cómo usarlo:** lee únicamente los bloques entre comillas. Las instrucciones de pantalla y puntero no se leen. La secuencia está pensada para unos 2:50, con diez segundos de margen; comprueba la duración al ensayar.

## Antes de grabar

Ten abiertas, en este orden, estas cuatro imágenes:

1. `resultados/ajuste_ISIC_0000133.png`: amplía **solo la primera fila**, identificada como «Top 1: β=1, λ=0.75 / central». No señales las filas Top 2, solo color o solo posición.
2. `resultados/prueba_ISIC_0000128.png`: ejemplo con mejor Dice de prueba.
3. `resultados/prueba_ISIC_0000087.png`: ejemplo con menor Dice de prueba.
4. `resultados/prueba_ISIC_0000123.png`: ejemplo de piel incluida por error.

En todas, las cinco columnas se leen de izquierda a derecha: **1. Original · 2. Grupos · 3. Máscara estimada · 4. Referencia · 5. Errores**. Si ya preparaste recortes, identifica los paneles por esos títulos.

**Atención a los colores:** en la columna 2 solo distinguen grupos; no significan acierto o error. Únicamente en la columna 5, verde = lesión identificada correctamente, azul = lesión omitida y rojo = píxeles incluidos por error.

## 0:00–0:25 · Problema y objetivo

**Pantalla:** primera fila de `ajuste_ISIC_0000133.png`.

**Señala la lesión marrón de la original, columna 1. Di:**

> “DermAlpes necesita delimitar lesiones como esta para apoyar la revisión del especialista. Nuestra herramienta propone una región para medir; no realiza diagnósticos ni reemplaza al dermatólogo.”

**Pasa a la región blanca de referencia, columna 4. Di:**

> “Esta máscara de referencia indica la zona que buscamos recuperar. Trabajamos con veinte imágenes: quince para elegir el método y cinco para evaluarlo.”

## 0:25–1:00 · De los grupos a la máscara

**Mantén la misma imagen. Señala primero la original y después el mapa de colores de la columna 2. Di:**

> “Representamos cada píxel por su color y posición. K-Means reúne píxeles parecidos en grupos. Probamos entre dos y ocho grupos y elegimos K mediante una medida de separación llamada silueta.”

**En la columna 2, señala el grupo azul del centro y luego las regiones de las esquinas. Di:**

> “Después elegimos un grupo oscuro y central, penalizando su presencia en el borde.”

**Muévete a la zona blanca central de la máscara estimada, columna 3, y compárala con la columna 4. Di:**

> “Ese grupo se convierte en la región blanca de nuestra máscara. Aquí se aproxima a la referencia, aunque todavía presenta errores.”

No digas que el azul del mapa de grupos representa lesión omitida: esa leyenda solo corresponde al último panel.

## 1:00–1:20 · Resultado global

**Pantalla:** mantén la imagen anterior. Puedes colocar como texto sobre la pantalla: «Dice medio: ajuste 0,862 · prueba 0,894». Estas son cifras globales; no señales el Dice 0,878 de este caso como si fuera el promedio.

**Di:**

> “Comparamos diez combinaciones de color y posición y dos reglas. Elegimos por Dice promedio, que vale uno cuando la coincidencia es perfecta. Obtuvimos 0,862 en ajuste y 0,894 en prueba, sin cambiar el método tras evaluarlo.”

## 1:20–1:40 · Ejemplo de mejor resultado

**Pantalla:** `prueba_ISIC_0000128.png`.

**Señala la máscara estimada, columna 3, y después la referencia, columna 4. Di:**

> “Este fue el mejor caso de prueba, con Dice 0,937. La región estimada y la referencia son parecidas.”

**Pasa al mapa de errores, columna 5. Recorre el centro verde y la franja azul fina del borde. Di:**

> “El verde muestra la lesión identificada correctamente; la franja azul señala lo que quedó fuera.”

## 1:40–2:05 · Ejemplo de lesión omitida

**Pantalla:** `prueba_ISIC_0000087.png`.

**Alterna el puntero entre la máscara estimada, columna 3, y la referencia, columna 4. Di:**

> “Este fue el caso de menor coincidencia en prueba: Dice 0,837. La máscara estimada es más pequeña que la referencia.”

**En el último panel, señala la zona azul amplia del borde derecho e inferior. Di:**

> “Aquí el azul es más extenso: estamos omitiendo parte de la lesión. Si midiéramos con esta máscara, subestimaríamos su área.”

## 2:05–2:25 · Ejemplo de piel incluida

**Pantalla:** `prueba_ISIC_0000123.png`.

**Señala directamente la franja roja inferior del mapa de errores, columna 5; luego compara el borde inferior de las columnas 3 y 4. Di:**

> “También puede ocurrir lo contrario. Esta franja roja corresponde a píxeles que incluimos como lesión y que la referencia considera fondo. El contorno se extiende demasiado y puede sobreestimar el área. Por eso hay que revisar cada delimitación, incluso cuando el Dice es alto.”

## 2:25–2:50 · Limitaciones y cierre

**Pantalla:** mantén el último mapa de errores durante la primera frase. Después muestra el texto «Delimitación de apoyo · No diagnóstico».

**Di:**

> “Reducimos las imágenes para hacer viable el cálculo, perdiendo detalle en los bordes. Cinco imágenes de prueba no garantizan el mismo desempeño con otros tonos de piel, equipos o iluminación. La herramienta necesita validación con datos de DermAlpes y revisión del especialista. Su función es apoyar la delimitación, no diagnosticar.”

## Indicaciones de grabación — no se leen

- Mueve el puntero cuando digas «esta», «aquí» o «esa franja» y déjalo quieto uno o dos segundos sobre la región correspondiente.
- En los ejemplos de prueba, amplía las columnas 3, 4 y 5 si no se distinguen los bordes. No tapes el mapa con la cámara del presentador.
- No leas identificadores, nombres de archivos, títulos ni todos los números de cada panel. Usa las cifras del texto hablado.
- Ensaya con cronómetro. Si hay que recortar, acorta las transiciones entre imágenes y conserva la explicación de verde, azul y rojo, los resultados y el cierre.
