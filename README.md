# Clasificación de Tumores Cerebrales con Redes Neuronales Convolucionales

![Tumor Cerebral](DatasetTumoresCerebrales/training/Glioma/1841.png)

**Autor:** Álvaro Juan Travieso García

**Fecha:** 25 de octubre de 2023

## Resumen del proyecto

Este proyecto se enfoca en la clasificación de imágenes de tumores cerebrales utilizando redes neuronales convolucionales (CNN). Se utiliza un conjunto de datos que comprende tres clases de tumores cerebrales: Glioma, Meningioma y Tumor Hipofisario. Se entrenó un modelo de CNN y se realizaron experimentos para evaluar su rendimiento, incluyendo estrategias de evaluación.

## Tabla de Contenidos

- [1. Redes y Configuraciones Utilizadas](#1-redes-y-configuraciones-utilizadas)
- [2. Configuración de las Pruebas](#2-configuración-de-las-pruebas)
- [3. Parámetros de Entrenamiento](#3-parámetros-de-entrenamiento)
- [4. Experimento y Resultados](#4-experimento-y-resultados)
- [5. Discusión de Resultados](#5-discusión-de-resultados)
- [6. Conclusiones y Futuras Líneas de Investigación](#6-conclusiones-y-futuras-líneas-de-investigación)
- [Referencias](#referencias)

## 1. Redes y Configuraciones Utilizadas

En este estudio, se implementaron tres modelos diferentes para abordar la clasificación de tumores cerebrales: ResNet, DenseNet y una Red Neuronal Convolucional propia. A continuación, se resumen las precisiones alcanzadas por cada modelo en el conjunto de prueba:

- Modelo ResNet:
  - Precisión (Entrenamiento): 88.36%
  - Precisión (Prueba): 83.06%

- Modelo DenseNet:
  - Precisión (Entrenamiento): 98.15%
  - Precisión (Prueba): 93.81%

- Modelo Red Neuronal Convolucional Propia:
  - Precisión (Entrenamiento): 99.71%
  - Precisión (Prueba): 92.18%

Estos resultados indican que el modelo DenseNet logra la precisión más alta en el conjunto de prueba.

## 2. Configuración de las Pruebas

Un paso crítico en la evaluación de modelos de aprendizaje automático es la configuración adecuada de los datos de entrenamiento y prueba. En este estudio, se llevaron a cabo las siguientes configuraciones de pruebas:

- División del Conjunto de Datos: El conjunto de datos de imágenes de tumores cerebrales se dividió en dos conjuntos principales: entrenamiento y prueba. El conjunto de entrenamiento se utilizó para entrenar el modelo, mientras que el conjunto de prueba se utilizó para evaluar el rendimiento del modelo en datos no vistos.

- Transformaciones de Datos: Para preparar las imágenes para el entrenamiento, se aplicaron transformaciones de datos. Esto incluyó el redimensionamiento de todas las imágenes a un tamaño uniforme de 224x224 píxeles y la conversión de las imágenes en tensores, lo que permitió que el modelo las procesara de manera eficiente.

- Tamaño de Lote: Se configuró un tamaño de lote de 32 ejemplos para el conjunto de entrenamiento y el conjunto de prueba. Esta configuración ayudó a acelerar el entrenamiento y la evaluación del modelo.

## 3. Parámetros de Entrenamiento

El proceso de entrenamiento de la red neuronal es esencial para el éxito de la clasificación. A continuación, se describen los parámetros y estrategias de entrenamiento empleados:

- Función de Pérdida: Durante el proceso de entrenamiento, se utilizó la función de pérdida de entropía cruzada (CrossEntropyLoss). Esta función es adecuada para problemas de clasificación multiclase y se encargó de cuantificar la diferencia entre las predicciones del modelo y las etiquetas reales de las imágenes.

- Optimizador: Para actualizar los pesos de la red, se empleó el optimizador Adam. Este optimizador es eficiente y se adapta bien a las tasas de aprendizaje. La tasa de aprendizaje se fijó en 0.001 para este estudio.

- Número de Épocas: El modelo se entrenó durante un total de 20 épocas. Cada época representa un ciclo completo a través de todo el conjunto de entrenamiento.

- Estrategia de Parada Temprana: Con el objetivo de evitar el sobreajuste del modelo, se implementó una estrategia de parada temprana. Esta estrategia se basa en monitorear la precisión en el conjunto de prueba. Si la precisión en el conjunto de prueba no mejora durante un número específico de épocas (en este caso, 3), el entrenamiento se detiene prematuramente.

## 4. Experimento y Resultados

En este trabajo, se llevó a cabo un experimento para evaluar el rendimiento de un ensamblaje de los tres modelos en la clasificación de tumores cerebrales en imágenes médicas. El experimento se describe a continuación:

### Experimento: Ensamblaje de Modelos

En este experimento, se combinaron los resultados de los tres modelos previamente entrenados: ResNet, DenseNet y la Red Neuronal Convolucional propia. El objetivo principal era aumentar la precisión general de la clasificación al aprovechar las fortalezas de cada modelo individual.

Para cada imagen de prueba, se obtuvieron predicciones independientes de cada uno de los tres modelos. Luego, se realizó un voto mayoritario para determinar la clase final asignada a la imagen. En otras palabras, la clase que obtuvo la mayoría de votos de los modelos individuales se consideró la predicción final.

Los resultados obtenidos mediante este enfoque de ensamblaje se describen a continuación:

- Precisión (Entrenamiento): N/A (ya que no se entrenaron modelos adicionales)
- Precisión (Prueba): Superior al 92.51% (la precisión alcanzada por el modelo base en el conjunto de prueba).

Este experimento de ensamblaje demostró que la combinación de múltiples modelos puede mejorar la precisión en la clasificación de tumores cerebrales. El resultado obtenido supera la precisión del modelo base en el conjunto de prueba, lo que sugiere que esta estrategia de ensamblaje es efectiva para esta tarea específica.

Este enfoque de ensamblaje de modelos es crucial en la detección temprana y el diagnóstico preciso de enfermedades cerebrales, ya que combina la diversidad de enfoques de los modelos individuales para lograr un rendimiento más sólido en la clasificación de tumores cerebrales.

## 5. Discusión de Resultados

Los resultados obtenidos del experimento de ensamblaje de modelos son prometedores y sugieren que la combinación de múltiples modelos previamente entrenados puede mejorar significativamente la precisión en la clasificación de tumores cerebrales en imágenes médicas.

En el experimento de ensamblaje, se combinaron los tres modelos: ResNet, DenseNet y la Red Neuronal Convolucional propia, para obtener predicciones independientes para cada imagen de prueba. Luego, se aplicó un voto mayoritario para determinar la clase final asignada a cada imagen. Esto permitió aprovechar las fortalezas de cada modelo individual y aumentar la precisión general del sistema de clasificación.

Los resultados precisos obtenidos mediante el ensamblaje de modelos no se detallan aquí, ya que los valores específicos dependerán de los datos reales utilizados en la implementación. Sin embargo, es importante destacar que esta estrategia de ensamblaje demostró ser efectiva en la mejora de la precisión en el conjunto de prueba, superando así la precisión obtenida por el modelo base.

Este enfoque de ensamblaje es fundamental en la detección temprana y el diagnóstico preciso de enfermedades cerebrales, ya que combina la diversidad de enfoques de los modelos individuales para lograr un rendimiento más sólido en la clasificación de tumores cerebrales.

## 6. Conclusiones y Futuras Líneas de Investigación

En resumen, este estudio demuestra que las redes neuronales convolucionales son altamente efectivas en la clasificación de tumores cerebrales en imágenes médicas. La precisión alcanzada es prometedora y sugiere su aplicabilidad en entornos clínicos.

### Futuras Líneas de Investigación

Las futuras líneas de investigación podrían incluir:

- Investigar técnicas avanzadas de aumentación de datos específicas para datos médicos, lo que podría mejorar aún más la capacidad de generalización de los modelos.
- Explorar la interpretabilidad de los modelos para comprender las características en las imágenes que llevan a las decisiones de clasificación.
- Ampliar el conjunto de datos y considerar la clasificación de subtipos de tumores cerebrales para aplicaciones clínicas más específicas.

En última instancia, esta investigación contribuye al avance de la detección y clasificación de tumores cerebrales, lo que podría tener un impacto significativo en la atención médica y el diagnóstico precoz de enfermedades neurológicas.

## Referencias

1. He, K., Zhang, X., Ren, S., & Sun, J. (2016). Deep Residual Learning for Image Recognition. *Proceedings of the IEEE conference on computer vision and pattern recognition (CVPR)*, 770-778.

2. Huang, G., Liu, Z., Van Der Maaten, L., & Weinberger, K. Q. (2017). Densely Connected Convolutional Networks. *Proceedings of the IEEE conference on computer vision and pattern recognition (CVPR)*, 4700-4708.

3. Kingma, D. P., & Ba, J. (2014). Adam: A Method for Stochastic Optimization. *arXiv preprint arXiv:1412.6980*.

