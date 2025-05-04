- #gan | #deep_learning | #neural_networks | #research
- [[notas whisper]]

# Contexto
- Este resumen aborda el trabajo seminal sobre las Redes Generativas Antagónicas (GANs) por Ian J. Goodfellow y sus coautores, publicado en $2014$. Este documento marcó un hito en la investigación de modelos generativos y ha influido en numerosos desarrollos posteriores en el campo del aprendizaje profundo.
- Se explorará la estructura y el funcionamiento de las GANs, así como su impacto en la generación de datos y la evolución de la investigación en este ámbito.

# Introducción a las GANs
- Las GANs son un marco para estimar modelos generativos mediante un proceso adversarial, donde se entrenan simultáneamente dos modelos: un modelo generativo *G* que captura la distribución de datos y un modelo discriminativo *D* que estima la probabilidad de que una muestra provenga de los datos de entrenamiento en lugar de *G*. Este enfoque fue innovador y sentó las bases para la investigación futura en modelos generativos.

# Estructura de las GANs
## Modelos Generativo y Discriminativo
- El modelo generativo *G* tiene la tarea de crear datos que el discriminador *D* clasifique como reales. El discriminador, por su parte, actúa como un clasificador de imágenes, determinando si una muestra es real o generada. Este proceso se basa en la idea de que, a medida que *G* mejora, *D* también debe hacerlo, creando un juego minimax entre ambos modelos.
## Proceso de Entrenamiento
- El entrenamiento de *G* se centra en maximizar la probabilidad de que *D* cometa un error. Esto se traduce en un juego de dos jugadores donde *G* intenta engañar a *D* mientras que *D* intenta no ser engañado. La formulación del problema se puede expresar como:

$$
\min_G \max_D V(D, G) = \mathbb{E}_{x \sim p_{data}(x)}[\log D(x)] + \mathbb{E}_{z \sim p_z(z)}[\log(1 - D(G(z)))]
$$

# Función de Pérdida
- La función de pérdida para las GANs se basa en la probabilidad logarítmica de los datos reales y generados. El discriminador intenta maximizar la probabilidad de los datos reales y minimizar la de los datos generados, mientras que el generador busca minimizar la probabilidad de que los datos generados sean clasificados como falsos.
## Problemas de Entrenamiento
- Uno de los desafíos en el entrenamiento de GANs es el colapso de modos, donde el generador puede concentrarse en generar un número limitado de muestras, ignorando otras partes de la distribución de datos. Este problema se deriva de la formulación de la función de pérdida y ha llevado a la investigación de diversas variantes de GANs para mitigar este efecto.

# Implementación y Resultados
## Algoritmo de Entrenamiento
- El algoritmo de entrenamiento implica alternar entre actualizar el discriminador y el generador. Se recomienda realizar múltiples pasos de optimización para *D* antes de actualizar *G*, lo que se traduce en un enfoque de optimización en bloque. Este método ha evolucionado, y hoy en día se utilizan enfoques más eficientes y variados.
## Evaluación de Modelos Generativos
- La evaluación de modelos generativos ha sido un desafío continuo. En el trabajo de Goodfellow et al., se utilizó un método de estimación de probabilidad basado en ajustar una ventana gaussiana a las muestras generadas. Aunque este método tiene limitaciones, ha sido un punto de partida para el desarrollo de métricas más sofisticadas en la evaluación de modelos generativos.

# Conclusiones y Futuras Direcciones
- El trabajo de Goodfellow et al. ha tenido un impacto duradero en el campo del aprendizaje profundo y la generación de datos. Las GANs han evolucionado y se han diversificado en múltiples variantes, cada una abordando diferentes aspectos del problema de generación de datos. La investigación futura se centrará en mejorar la estabilidad del entrenamiento, la calidad de las muestras generadas y la evaluación de modelos generativos.