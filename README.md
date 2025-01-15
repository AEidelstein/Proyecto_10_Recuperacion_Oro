# Proyecto_10_Recuperacion_Oro / Gold recovery
Recuperación de Oro / Gold recovery


# Descripción del ejercicio / Exercise description

SPA:

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

EN:

Prepare a prototype of a machine learning model for Zyfra. The company develops efficiency solutions for heavy industry.

The model should predict the amount of gold extracted from the gold ore. You have the extraction and purification data.

The model will help to optimise production and eliminate unprofitable parameters.

You will need to:

   1. prepare the data;
   2. perform data analysis;
   3. develop a model and train it.

To complete the project, you can use the pandas documentation, matplotlib and sklearn.

The next lesson is about the ore purification process.
You will have to select the important information for the development of the model.

# Proceso tecnológico / Technological process

SPA:

¿Cómo se extrae el oro del mineral? Veamos las etapas de este proceso.

El mineral extraído se somete a un tratamiento primario para obtener la mezcla de mineral, o alimentación rougher, que es la materia prima utilizada para la flotación (también conocida como proceso rougher). Después de la flotación, el material se somete al proceso de purificación en dos etapas.

image_1  -> Ver adjunto

Veamos el proceso paso a paso:

1. Flotación

La mezcla de mineral de oro se introduce en las plantas de flotación para obtener un concentrado de oro rougher y colas rougher (es decir, residuos del producto con una baja concentración de metales valiosos).

La estabilidad de este proceso se ve afectada por la volatilidad y el estado físico-químico desfavorable de la pulpa de flotación (una mezcla de partículas sólidas y líquido).

2. Purificación

El concentrado rougher se somete a dos etapas de purificación. Luego de esto, tenemos el concentrado final y las nuevas colas.


EN:

How is gold extracted from ore? Let's look at the stages of this process.

The mined ore undergoes primary treatment to obtain the ore slurry, or rougher feed, which is the raw material used for flotation (also known as the rougher process). After flotation, the material undergoes a two-stage purification process.

image_1  -> see attachment

Let's look at the process step by step:

1. Flotation

The gold ore mixture is fed into the flotation plants to obtain a rougher gold concentrate and rougher tails (i.e. product residues with a low concentration of valuable metals).

The stability of this process is affected by the volatility and unfavourable physico-chemical state of the flotation slurry (a mixture of solid particles and liquid).

2. Purification

The rougher concentrate undergoes two stages of purification. After this, we have the final concentrate and the new tails.

# Descripción de datos / Data description

## Proceso tecnológico / Technological process

   - Rougher feed — materia prima / raw materials
   - Rougher additions (o adiciones de reactivos) - reactivos de flotación: xantato, sulfato, depresante / flotation reagents: xanthate, sulphate, depressant
       - Xantato — promotor o activador de la flotación / flotation promoter or activator
       - Sulfato — sulfuro de sodio para este proceso en particular / sodium sulphide for this particular process
       - Depresante — silicato de sodio / sodium silicate
   - Rougher process — flotación / flotation
   - Rougher tails — residuos del producto / product waste
   - Float banks — instalación de flotación / floatation plant
   - Cleaner process — purificación / purification(cleaning process)
   - Rougher Au — concentrado de oro rougher / gold rougher concentrate
   - Final Au — concentrado de oro final / final gold concentrate

## Parámetros de las etapas / Stage parameters

   - air amount — volumen de aire / air volume
   - fluid levels
   - feed size — tamaño de las partículas de la alimentación / feed particle size
   - feed rate

# Denominación de las características / Description of the features

SPA:

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


EN:

This is how the features are named:

[stage].[parameter_type].[parameter_name]

Example: rougher.input.feed_ag

Possible values for [stage]:

   - rougher - flotation
   - primary_cleaner - primary purification
   - secondary_cleaner - secondary purification
   - final - final characteristics

Possible values for [parameter_type]:

   - input - raw material parameters
   - output - product parameters
   - state - parameters characterising the current state of the stage
   - calculation - calculation characteristics

image_2 -> See attachment

# Cálculo de la recuperación / Recovery calculations

SPA:

Tienes que simular el proceso de recuperación del oro del mineral de oro.

Utiliza la siguiente fórmula para simular el proceso de recuperación:

image_3  -> Ver adjunto

dónde:

   - C — proporción de oro en el concentrado justo después de la flotación (para saber la recuperación del concentrado rougher)/después de la purificación (para saber la recuperación del concentrado final)
   - F — la proporción de oro en la alimentación antes de la flotación (para saber la recuperación del concentrado rougher)/en el concentrado justo después de la flotación (para saber la recuperación del concentrado final)
   - T — la proporción de oro en las colas rougher justo después de la flotación (para saber la recuperación del concentrado rougher)/después de la purificación (para saber la recuperación del concentrado final)

Para predecir el coeficiente, hay que encontrar la proporción de oro en el concentrado y en las colas. Ten en cuenta que tanto el concentrado final como el concentrado rougher tienen importancia.

EN:

You have to simulate the process of gold recovery from gold ore.

Use the following formula to simulate the recovery process:

image_3  -> See attachment

Where: 

   - C - proportion of gold in the concentrate just after flotation (for rougher concentrate recovery)/after purification (for final concentrate recovery).
   - F - the proportion of gold in the feed before flotation (for rougher concentrate recovery)/in the concentrate just after flotation (for final concentrate recovery)
   - T - the proportion of gold in the rougher tails just after flotation (for rougher concentrate recovery)/after purification (for final concentrate recovery)

To predict the ratio, the proportion of gold in the concentrate and in the tails must be found. Note that both the final concentrate and the rougher concentrate are important.


# Métricas de evaluación / Metrics for evaluation

SPA:

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

   1. La recuperación del concentrado rougher 'rougher.output.recovery'.
   2. La recuperación final del concentrado 'final.output.recovery'.

La métrica final incluye los dos valores:

image_9  -> Ver adjunto

EN:

To solve the problem, we will need a new metric. It is called sMAPE, or symmetric mean absolute percentage error.

It is similar to the MAE, but is expressed in relative rather than absolute values. Why is it symmetric? Because it takes into account the scale of both the target and the prediction.

This is how sMAPE is calculated:

image_4  -> See attachment

Designation:

image_5  -> See attachment

   - Target value for the observation with index i in the set used to measure quality.

image_6  -> See attachment

  - Prediction value for the observation with index i, e.g. in the test sample.

image_7 -> See attachment

 - Number of sample observations.

image_8 -> See attachment

- Sum of all observations in the sample (i takes values from 1 to N).

We need to predict two values:

   1. The recovery of the rougher concentrate ‘rougher.output.recovery’.
   2. The final concentrate recovery ‘final.output.recovery’.

The final metric includes both values:

image_9 -> See attachment

