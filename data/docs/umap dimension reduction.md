- #umap | #dimensionalityreduction | #dataanalysis | #machinelearning
- [[notas whisper]]

# Contexto
- UMAP (Uniform Manifold Approximation and Projection) es una técnica de reducción de dimensionalidad que permite visualizar datos de alta dimensión en un espacio de menor dimensión.
- Este método es útil para identificar patrones, similitudes y outliers en conjuntos de datos complejos.

# Introducción a UMAP
- UMAP toma datos de alta dimensión y los proyecta en un espacio de menor dimensión, facilitando su visualización. A diferencia de PCA, UMAP es más efectivo en conjuntos de datos complejos donde las relaciones no son lineales.

# Funcionamiento de UMAP
- UMAP comienza calculando las distancias entre cada par de puntos en el espacio de alta dimensión. Luego, utiliza estas distancias para calcular puntajes de similitud que ayudan a identificar agrupaciones de puntos similares.
## Cálculo de similitud
- Para calcular la similitud de un punto, UMAP dibuja una curva que representa la distancia a sus vecinos más cercanos. El número de vecinos se puede ajustar, siendo un valor común $15$.
- Por ejemplo, si se establece el número de vecinos en $3$, UMAP calculará la similitud de un punto con sus $2$ vecinos más cercanos.

# Proceso de reducción
- UMAP inicializa un gráfico de baja dimensión y ajusta las posiciones de los puntos iterativamente para preservar las relaciones de agrupamiento observadas en los datos de alta dimensión.
## Movimiento de puntos
- UMAP selecciona pares de puntos en función de sus puntajes de similitud y ajusta sus posiciones. Por ejemplo, si los puntos A y B están en la misma agrupación, se moverán más cerca uno del otro, mientras que se alejarán de puntos en diferentes agrupaciones.

# Comparación con T-SNE
- Aunque UMAP y T-SNE son similares en su enfoque, UMAP utiliza un método de inicialización diferente llamado *spectral embedding*, lo que permite que el gráfico de baja dimensión sea consistente en cada ejecución.
- Además, UMAP puede mover solo un punto o un pequeño subconjunto de puntos en cada iteración, lo que mejora su escalabilidad con grandes conjuntos de datos.

# Ajuste de parámetros
- El número de vecinos es un parámetro crucial que afecta la forma en que UMAP agrupa los datos. Un valor bajo puede resultar en agrupaciones pequeñas y detalladas, mientras que un valor alto puede ofrecer una visión más general de los datos.
- Es recomendable experimentar con diferentes valores para encontrar el que mejor se adapte a los datos específicos.

## Ejemplo de código
```python
import umap
import numpy as np

# Generar datos aleatorios de alta dimensión
data = np.random.rand(100, 10)

# Aplicar UMAP
umap_model = umap.UMAP(n_neighbors=3, n_components=2)
reduced_data = umap_model.fit_transform(data)

# Visualizar resultados
import matplotlib.pyplot as plt
plt.scatter(reduced_data[:, 0], reduced_data[:, 1])
plt.title('UMAP Dimensionality Reduction')
plt.show()
```