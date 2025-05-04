- #pca | #tsne | #umap | #dataanalysis
- [[notas whisper]]

# Contexto
- En el análisis de datos, la reducción de dimensionalidad es una técnica crucial para visualizar y entender datos complejos. Este resumen explora tres métodos populares: PCA, t-SNE y UMAP.
- Cada técnica tiene sus propias características, ventajas y desventajas, que se detallan a continuación.

# PCA (Análisis de Componentes Principales)
- El *Principal Component Analysis* (PCA) es una técnica que reduce la dimensionalidad de los datos proyectándolos sobre los componentes principales. Se utiliza comúnmente para simplificar conjuntos de datos complejos.
## Cálculo de PCA
- Para calcular PCA, se siguen estos pasos:
  1. **Calcular la matriz de covarianza**: Se centra el conjunto de datos restando la media de cada variable.
  2. **Encontrar los eigenvectores**: Se obtienen los vectores que no cambian de dirección al aplicar la matriz de covarianza.
  3. **Ordenar los eigenvectores**: Se clasifican según sus eigenvalores en orden descendente.
  4. **Proyección de datos**: Se proyectan los datos sobre los componentes principales seleccionados.
- La complejidad temporal de PCA es lineal en relación al número de muestras, lo que lo hace eficiente. Sin embargo, PCA no maneja bien datos no lineales.

# t-SNE (T-Distributed Stochastic Neighbor Embedding)
- *t-SNE* es una técnica que mejora la visualización de datos en espacios de alta dimensión, conservando la estructura local.
## Funcionamiento de t-SNE
- Los pasos principales son:
  1. **Distribución de probabilidades**: Se convierte la distancia entre puntos en una distribución gaussiana.
  2. **Minimización de la divergencia KL**: Se utiliza la divergencia Kullback-Leibler para medir la similitud entre las distribuciones de alta y baja dimensión.
  3. **Optimización**: Se ajustan las representaciones de baja dimensión para que se asemejen a las de alta dimensión.
- t-SNE es efectivo para datos no lineales, pero su rendimiento puede ser lento y sensible al parámetro de *perplexity*.

# UMAP (Uniform Manifold Approximation and Projection)
- *UMAP* es una técnica más reciente que combina fundamentos matemáticos sólidos con un enfoque práctico para la reducción de dimensionalidad.
## Proceso de UMAP
- Los pasos incluyen:
  1. **Construcción de un gráfico de vecinos**: Se encuentran los vecinos más cercanos y se construye un gráfico ponderado.
  2. **Simetrización del gráfico**: Se combinan los gráficos de cada muestra en un único gráfico ponderado.
  3. **Minimización de la entropía cruzada**: Se ajustan las representaciones de baja dimensión para que coincidan con las de alta dimensión.
- UMAP es más rápido que t-SNE y mantiene mejor la estructura global de los datos, lo que lo convierte en una opción preferida para visualizaciones complejas.

# Comparación de Métodos
- **PCA**: Rápido y fácil de interpretar, pero limitado a datos lineales.
- **t-SNE**: Excelente para datos no lineales, pero lento y sensible a parámetros.
- **UMAP**: Rápido, efectivo en datos no lineales y mejor preservación de la estructura global.