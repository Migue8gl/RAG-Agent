- #inteligenciaartificial | #aprendizajeautomático | #modelosgenerativos | #vae
- [[notas whisper]]

# Contexto
- La inteligencia artificial generativa es un término que ha ganado popularidad, pero su verdadero significado a menudo se malinterpreta. Este resumen explora los variational autoencoders (VAEs), una técnica fundamental en la creación de datos nuevos, como imágenes.

# Introducción a los VAEs
- Los VAEs son modelos que permiten generar nuevos datos a partir de representaciones latentes. A diferencia de los autoencoders tradicionales, que solo reconstruyen datos, los VAEs crean nuevas muestras al muestrear de un espacio latente organizado.
## Concepto de Espacio Latente
- Un *autoencoder* toma datos, los comprime en una representación de baja dimensión y luego los reconstruye. Sin embargo, el espacio latente en un autoencoder tradicional puede ser desorganizado, lo que dificulta la generación de nuevas imágenes coherentes. Los VAEs abordan este problema al estructurar el espacio latente de manera que el muestreo produzca imágenes significativas.

# Fundamentos Teóricos
- Diederich Kingma introdujo los VAEs en $2013$ en su trabajo "Autoencoding Variational Bayes". La investigación de Kingma se centra en el aprendizaje profundo y la estadística bayesiana, que son esenciales para entender los VAEs.
## Distribuciones Probabilísticas
- Los VAEs utilizan dos distribuciones: la distribución de datos $p(x)$ y la distribución latente $p(z)$. La primera representa el conjunto de datos, mientras que la segunda captura las características esenciales en un espacio de menor dimensión. Para conectar estas distribuciones, se utilizan las distribuciones posterior y de verosimilitud.
## Aproximación de la Distribución Posterior
- Dado que no conocemos la forma exacta de la distribución posterior, se asume que es una distribución normal. Esto permite calcular la verosimilitud $p(x|z)$, que mide la probabilidad de reconstruir una imagen a partir de un vector latente.

# Entrenamiento de VAEs
- El objetivo de entrenamiento de un VAE se basa en maximizar el *evidence lower bound* (ELBO), que se descompone en dos términos: la verosimilitud de los datos y la divergencia de Kullback-Leibler (KL) entre la distribución posterior y la prior.
## Proceso de Entrenamiento
- Durante el entrenamiento, se utiliza el *trick de reparametrización* para permitir el muestreo de la distribución latente de manera diferenciable. Esto implica que en lugar de muestrear directamente de la distribución, se introduce una variable aleatoria que facilita el proceso de retropropagación.

# Aplicaciones y Limitaciones
- Los VAEs son capaces de generar imágenes nuevas y realistas, así como de interpolar entre imágenes existentes. Sin embargo, tienden a producir imágenes borrosas y carecen de la capacidad de imponer restricciones específicas en los datos generados.
## Variantes Avanzadas
- Existen modelos avanzados de VAEs que abordan sus limitaciones, como los *conditional VAEs*, que permiten la generación de imágenes específicas según clases, y los *beta VAEs*, que introducen un parámetro ajustable para controlar la calidad de reconstrucción y el desacoplamiento.