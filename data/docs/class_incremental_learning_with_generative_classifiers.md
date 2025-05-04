- #aprendizajeincremental | #clasificadoresgenerativos | #inteligenciaartificial | #aprendizajeprofundo
- [[notas whisper]]

# Contexto
- Esta presentación aborda el trabajo reciente sobre el aprendizaje incremental de clases utilizando clasificadores generativos, presentado por Guido van de Ven del Baylor College of Medicine.
- Se exploran las estrategias actuales en el aprendizaje continuo y se propone un nuevo enfoque conceptual que combina modelos discriminativos y generativos.

# Tipos de aprendizaje continuo
- Existen tres tipos fundamentales de aprendizaje continuo, cada uno con sus propios desafíos:
## Aprendizaje incremental de tareas
- En este tipo, un algoritmo debe aprender un conjunto de tareas claramente distintas. La característica definitoria es que siempre es claro qué tarea específica debe realizarse, lo que facilita la prevención del **catastrofismo del olvido**.
## Aprendizaje incremental de dominios
- Aquí, el algoritmo debe aprender el mismo tipo de tarea en contextos cambiantes o diferentes dominios. La prevención del catastrofismo del olvido es un desafío importante, ya que no es posible por diseño.
## Aprendizaje incremental de clases
- Este es el enfoque más desafiante, donde el algoritmo debe aprender a distinguir entre un número creciente de clases que no se observan simultáneamente. Este trabajo se centra en este tipo de aprendizaje.

# Desafíos del aprendizaje incremental de clases
- La dificultad principal radica en que el algoritmo debe aprender a distinguir entre clases que no se observan al mismo tiempo. Esto puede llevar a que se pierdan las reglas aprendidas en episodios anteriores.
- Se requiere una estrategia especial para abordar este problema, ya que las reglas aprendidas pueden no ser efectivas al aprender nuevas clases.

# Estrategias actuales en el aprendizaje incremental
- Las estrategias más comunes incluyen:
## Almacenamiento de datos
- Almacenar un subconjunto de datos pasados en un búfer de memoria para revisitarlo al encontrar nuevas clases. Este enfoque es efectivo pero no siempre es posible.
## Repetición generativa
- Aprender un modelo generativo que genere datos para ser reproducidos. Esto puede incluir la repetición de muestras generadas a nivel de entrada o representaciones de características de alto nivel.
## Métodos sin repetición
- Se han desarrollado enfoques sin repetición, como la regularización de parámetros y la corrección de sesgos, aunque estos métodos tienen limitaciones en su efectividad.

# Propuesta de un nuevo enfoque
- Se propone un enfoque que utiliza clasificadores generativos en lugar de discriminativos. 
- Un clasificador generativo aprende un modelo generativo para cada clase y realiza la clasificación utilizando la regla de Bayes, evitando así el problema de la comparación de clases durante el entrenamiento.

# Implementación y resultados
- Se utilizó un modelo de *variational autoencoder* (VAE) para cada clase, y durante la inferencia, se utilizó muestreo importante para estimar la verosimilitud de cada clase.
- Los resultados muestran que este enfoque supera a los métodos de repetición generativa en varios benchmarks, destacando su eficiencia en comparación con los enfoques tradicionales.

# Limitaciones y consideraciones futuras
- Aunque el entrenamiento de un clasificador generativo es menos costoso, la inferencia puede ser más costosa debido a la necesidad de calcular la verosimilitud para cada clase.
- Se sugiere que futuras investigaciones consideren técnicas del aprendizaje incremental de tareas para mejorar la escalabilidad y eficiencia de los modelos generativos en el aprendizaje incremental de clases.