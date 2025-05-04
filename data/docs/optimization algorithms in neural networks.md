- #neuralnetworks | #optimization | #gradientdescent | #machinelearning
- [[notas whisper]]

# Sección de contexto
- En este video se exploran varios algoritmos de optimización utilizados en redes neuronales, centrándose en cómo se puede aplicar el *gradient descent* para minimizar la función de pérdida.
- Se discuten las ventajas y desventajas de diferentes métodos, así como la importancia de la tasa de aprendizaje.

# Introducción al *gradient descent*
- El *gradient descent* es un proceso utilizado para encontrar el mínimo global de una función de pérdida en el espacio de parámetros de una red neuronal. 
- Se basa en calcular el gradiente de la función de pérdida con respecto a los pesos de la red y ajustar estos pesos en consecuencia.

# Algoritmos de optimización
- Existen varios algoritmos de optimización que se pueden aplicar, entre ellos el *stochastic gradient descent* (SGD), que utiliza lotes de datos para calcular el gradiente y actualizar los pesos.
## *Stochastic Gradient Descent*
- El SGD presenta un paisaje de pérdida estocástico, donde cada lote de datos puede llevar a un paisaje de pérdida ligeramente diferente.
- La tasa de aprendizaje, denotada como $\eta$, es un hiperparámetro crucial que afecta la convergencia del algoritmo.

# Métodos con momento
- Se introducen métodos que incorporan un término de momento para mejorar la convergencia.
## *Nesterov Momentum*
- Este método calcula el gradiente en un punto anticipado, lo que permite una mejor adaptación a la topología del paisaje de pérdida.

# Métodos adaptativos
- Se presentan métodos que ajustan la tasa de aprendizaje durante el entrenamiento, como *AdaGrad* y *RMSProp*.
## *AdaGrad*
- Este método escala el paso de gradiente según la raíz cuadrada de la suma de los gradientes anteriores, permitiendo un ajuste más fino de cada parámetro.
## *RMSProp*
- A diferencia de *AdaGrad*, *RMSProp* permite que la tasa de aprendizaje se ajuste tanto hacia arriba como hacia abajo, manteniendo un equilibrio en la adaptación.

# *Adam* y su efectividad
- El algoritmo *Adam* combina las ventajas de *RMSProp* y el *momentum*, ajustando la tasa de aprendizaje y utilizando un término de velocidad.
- Se discute cómo *Adam* puede ser menos efectivo en términos de generalización en comparación con SGD, que tiende a encontrar mínimos más planos y, por ende, modelos más generalizables.