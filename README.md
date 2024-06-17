# Proyecto_10_Recuperacion_Oro
Recuperación de Oro / Gold recovery


# Descripción del ejercicio

Prepara un prototipo de un modelo de machine learning para Zyfra. La empresa desarrolla soluciones de eficiencia para la industria pesada.

El modelo debe predecir la cantidad de oro extraído del mineral de oro. Dispones de los datos de extracción y purificación.

El modelo ayudará a optimizar la producción y a eliminar los parámetros no rentables.

Tendrás que:

   1. preparar los datos;
   2. realizar el análisis de datos;
   3. desarrollar un modelo y entrenarlo.

Para completar el proyecto, puedes utilizar la documentación de pandas, matplotlib y sklearn.

La siguiente lección trata sobre el proceso de depuración del mineral.
Te tocará seleccionar la información importante para el desarrollo del modelo. 

# Proceso tecnológico
¿Cómo se extrae el oro del mineral? Veamos las etapas de este proceso.

El mineral extraído se somete a un tratamiento primario para obtener la mezcla de mineral, o alimentación rougher, que es la materia prima utilizada para la flotación (también conocida como proceso rougher). Después de la flotación, el material se somete al proceso de purificación en dos etapas.

image_1  -> Ver adjunto

Veamos el proceso paso a paso:

1. Flotación

La mezcla de mineral de oro se introduce en las plantas de flotación para obtener un concentrado de oro rougher y colas rougher (es decir, residuos del producto con una baja concentración de metales valiosos).

La estabilidad de este proceso se ve afectada por la volatilidad y el estado físico-químico desfavorable de la pulpa de flotación (una mezcla de partículas sólidas y líquido).

2. Purificación

El concentrado rougher se somete a dos etapas de purificación. Luego de esto, tenemos el concentrado final y las nuevas colas.

# Descripción de datos

## Proceso tecnológico

   - Rougher feed — materia prima
   - Rougher additions (o adiciones de reactivos) - reactivos de flotación: xantato, sulfato, depresante
       - Xantato — promotor o activador de la flotación
       - Sulfato — sulfuro de sodio para este proceso en particular
       - Depresante — silicato de sodio
   - Rougher process — flotación
   - Rougher tails — residuos del producto
   - Float banks — instalación de flotación
   - Cleaner process — purificación
   - Rougher Au — concentrado de oro rougher
   - Final Au — concentrado de oro final

## Parámetros de las etapas

   - air amount — volumen de aire
   - fluid levels
   - feed size — tamaño de las partículas de la alimentación
   - feed rate

# Denominación de las características

Así es como se denominan las características:

[stage].[parameter_type].[parameter_name]

Ejemplo: rougher.input.feed_ag

Valores posibles para [stage]:

   - rougher — flotación
   - primary_cleaner — purificación primaria
   - secondary_cleaner — purificación secundaria
   - final — características finales

Valores posibles para [parameter_type]:

   - input — parámetros de la materia prima
   - output — parámetros del producto
   - state — parámetros que caracterizan el estado actual de la etapa
   - calculation — características de cálculo

image_2  -> Ver adjunto

# Cálculo de la recuperación

Tienes que simular el proceso de recuperación del oro del mineral de oro.

Utiliza la siguiente fórmula para simular el proceso de recuperación:

image_3  -> Ver adjunto

dónde:

   - C — proporción de oro en el concentrado justo después de la flotación (para saber la recuperación del concentrado rougher)/después de la purificación (para saber la recuperación del concentrado final)
   - F — la proporción de oro en la alimentación antes de la flotación (para saber la recuperación del concentrado rougher)/en el concentrado justo después de la flotación (para saber la recuperación del concentrado final)
   - T — la proporción de oro en las colas rougher justo después de la flotación (para saber la recuperación del concentrado rougher)/después de la purificación (para saber la recuperación del concentrado final)

Para predecir el coeficiente, hay que encontrar la proporción de oro en el concentrado y en las colas. Ten en cuenta que tanto el concentrado final como el concentrado rougher tienen importancia.

# Métricas de evaluación

Para resolver el problema, necesitaremos una nueva métrica. Se llama sMAPE, o error medio absoluto porcentual simétrico.

Es similar al MAE, pero se expresa en valores relativos en lugar de absolutos. ¿Por qué es simétrico? Porque tiene en cuenta la escala tanto del objetivo como de la predicción.

Así es como se calcula el sMAPE:

image_4  -> Ver adjunto

Designación:

image_5  -> Ver adjunto

   - Valor del objetivo para la observación con el índice i en el conjunto utilizado para medir la calidad.

image_6  -> Ver adjunto

   - Valor de la predicción para la observación con el índice i, por ejemplo, en la muestra de prueba.

image_7  -> Ver adjunto

   - Número de observaciones de la muestra.

image_8  -> Ver adjunto

   - Suma de todas las observaciones de la muestra (i toma valores de 1 a N).

Necesitamos predecir dos valores:

   1. La recuperación del concentrado rougher rougher.output.recovery.
   2. La recuperación final del concentrado final.output.recovery.

La métrica final incluye los dos valores:

image_9  -> Ver adjunto
