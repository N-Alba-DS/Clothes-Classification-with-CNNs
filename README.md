# Clothes-Classification-with-CNNs
El siguiente repositorio contiene el trabajo de especialización presentado en la UBA Facultad de Ciencias exactas para obtener el título de especialista en Explotación de Datos y Descubrimiento del Conocimiento. 

Este trabajo de especialización tiene como objetivo aplicar redes neuronales convolucionales a problemas de clasificación multiclase y clusterización.

## Dataset

El objeto de análisis es el dataset Apparel Images Dataset (licencia CC0 - Public Domain), creado por Aleksandr Antonov.

## Modelo y Transfer Learning

Se aplica transfer learning utilizando una red VGG16 preentrenada. La arquitectura original se modifica agregando una nueva capa de clasificación adaptada al problema abordado.

### Etapas del entrenamiento

1. Red con capas congeladas: se entrena la nueva capa de clasificación manteniendo congeladas las capas preentrenadas.
2. Fine-tuning: se descongelan las dos capas fully connected anteriores a la capa de salida.
3. Ajuste del learning rate: se optimiza la tasa de aprendizaje para maximizar la performance.

Resultado: Se alcanza una accuracy máxima de 0.84 sobre el conjunto de test.

## Extracción de Características y Clustering

Luego de entrenar el modelo, se utiliza la penúltima capa fully connected como extractor de características, generando vectores de 4096 dimensiones (arrays unidimensionales de NumPy).

Sobre dichos vectores se aplican algoritmos de:

- Reducción de dimensionalidad: UMAP
- Clusterización: K-Medoids (PAM) y DBSCAN

La calidad de los clusters se evaluó utilizando la métrica Silhouette global, obteniendo valores satisfactorios. Los clusters encontrados revelan características latentes que trascienden las etiquetas originales de clasificación.
