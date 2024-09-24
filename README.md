# Descripción General
El proyecto cat_dog_classifier tiene como objetivo desarrollar un modelo de clasificación de imágenes que pueda diferenciar entre gatos y perros utilizando redes neuronales profundas (Deep Learning) y técnicas avanzadas de visión por computadora. El flujo del proyecto se divide en tres notebooks principales: Feature Pipeline, Training Pipeline, y Batch Inference Pipeline. Juntas, estas notebooks forman un pipeline completo que abarca desde el procesamiento de las imágenes hasta la clasificación en lotes.

1. Feature Pipeline Notebook
La notebook de Feature Pipeline se centra en la preparación y procesamiento de las imágenes de gatos y perros para que sean adecuadas como entrada al modelo de deep learning.

Pasos principales:

- Carga de datos: Se cargan las imágenes de gatos y perros desde dos carpetas.
- Redimensionamiento de imágenes: Todas las imágenes se redimensionan a un tamaño uniforme (por ejemplo, 128x128 píxeles) para garantizar que el modelo pueda procesarlas eficientemente.
- Normalización: Se normalizan los valores de píxeles para que estén en un rango entre 0 y 1, lo que mejora la eficiencia del entrenamiento.
- Etiquetado: Se asignan etiquetas a las imágenes: 0 para gatos y 1 para perros, generando un conjunto de datos balanceado para la clasificación.
- Almacenamiento de características: Las imágenes procesadas y sus etiquetas se guardan en un formato adecuado (como .npy o .pkl) para su posterior uso en el modelo de entrenamiento.

2. Training Pipeline Notebook
En esta notebook se entrena un modelo de deep learning utilizando las imágenes de gatos y perros preprocesadas.

Pasos principales:

- Carga de datos preprocesados: Se cargan las imágenes y etiquetas generadas en la notebook de Feature Pipeline.
- División de datos: Los datos se dividen en conjuntos de entrenamiento y validación (por ejemplo, 80% para entrenamiento y 20% para validación).
- Construcción del modelo de deep learning: Se utiliza una arquitectura de Red Neuronal Convolucional (CNN), que es adecuada para la clasificación de imágenes. La arquitectura incluye capas de convolución, capas de pooling, y capas densas completamente conectadas, con la función de activación ReLU en las capas intermedias y Softmax en la salida.
- Entrenamiento del modelo: Se entrena el modelo utilizando el conjunto de datos de entrenamiento. Se utiliza una función de pérdida como Categorical Crossentropy y el optimizador Adam. El modelo se entrena durante varias épocas (por ejemplo, 20-30 épocas), ajustando los pesos para minimizar la pérdida.
- Evaluación del modelo: El rendimiento del modelo se evalúa utilizando el conjunto de validación, con métricas como la precisión (accuracy) y la pérdida (loss).
- Registro en MLFlow: Se registran las métricas y el modelo entrenado en MLFlow para permitir un seguimiento adecuado del rendimiento y la posibilidad de comparar futuros experimentos.
- Guardado del modelo entrenado: El modelo entrenado se guarda en un archivo .h5 para su uso en la inferencia por lotes.

3. Batch Inference Pipeline Notebook
La notebook de Batch Inference Pipeline permite aplicar el modelo entrenado para clasificar imágenes en lotes.

Pasos principales:

- Carga del modelo entrenado: Se carga el modelo entrenado guardado en formato .h5 desde la notebook de entrenamiento.
- Carga de nuevas imágenes: Se cargan imágenes nuevas de gatos y perros (o cualquier otro conjunto de imágenes para clasificar) que no fueron vistas durante el entrenamiento.
- Preprocesamiento de las nuevas imágenes: Se procesan las imágenes de la misma manera que en la notebook de Feature Pipeline (redimensionamiento, normalización, etc.) para que sean compatibles con el modelo.
- Predicciones en lote: Se aplican las predicciones del modelo a las nuevas imágenes, clasificando cada imagen como gato o perro.
- Almacenamiento de predicciones: Las predicciones generadas (por ejemplo, las etiquetas 0 para gatos y 1 para perros) se guardan en un archivo CSV o en otro formato adecuado para su análisis o uso posterior.

Resultados Esperados

a) Modelo de Clasificación de Gatos y Perros: El proyecto debe generar un modelo de deep learning capaz de clasificar imágenes de gatos y perros con alta precisión. Se espera que el modelo sea robusto y generalice bien en imágenes nuevas.

b) Métricas de Desempeño: Las métricas clave para evaluar el desempeño del modelo incluyen la precisión (accuracy), la pérdida (loss) y el F1-score en el conjunto de validación. Se espera que el modelo obtenga una precisión alta, idealmente por encima del 90%.

c) Pipeline de Inferencia por Lotes: Se espera tener un pipeline que permita la clasificación de imágenes en lotes de manera eficiente y precisa, facilitando la aplicación del modelo a datos nuevos o sin etiquetar.

Este proyecto muestra un flujo completo de trabajo de clasificación de imágenes utilizando deep learning, desde la preparación y procesamiento de imágenes, el entrenamiento de un modelo robusto, hasta la aplicación del modelo para inferencia en tiempo real o en lotes. Además, permite un seguimiento adecuado del rendimiento utilizando MLFlow, facilitando la comparación y mejora continua del modelo.

Base de datos empleada en el proyecto: [Kaggle Link](https://www.kaggle.com/datasets/shaunthesheep/microsoft-catsvsdogs-dataset/data?select=PetImages)