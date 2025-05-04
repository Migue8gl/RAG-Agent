- #vectores | #algebra_lineal | #combinaciones_lineales | #espacios_vectoriales
- [[notas whisper]]

# Contexto
- En esta transcripción se exploran conceptos fundamentales de álgebra lineal, centrándose en la adición de vectores y la multiplicación escalar. Se discuten las coordenadas de los vectores y su relación con los vectores base en un sistema de coordenadas.

# Vectores y coordenadas
- Se introduce la idea de que cada coordenada de un vector puede ser vista como un escalar que estira o comprime los vectores base, *i-hat* y *j-hat*. Por ejemplo, un vector con coordenadas $(3, -2)$ se puede interpretar como la suma de dos vectores escalados: $3 \cdot \textbf{i}$ y $-2 \cdot \textbf{j}$.
## Combinaciones lineales
- La combinación lineal de dos vectores se refiere a la suma de estos vectores escalados. Este concepto es crucial en álgebra lineal, ya que permite describir cualquier vector en el plano 2D. La combinación lineal se define como:
$$\textbf{v} = a \cdot \textbf{u} + b \cdot \textbf{w}$$
donde $a$ y $b$ son escalares.

# Span de vectores
- El *span* de un par de vectores es el conjunto de todos los vectores que se pueden alcanzar mediante combinaciones lineales de esos vectores. Para la mayoría de los pares de vectores en 2D, el *span* es todo el espacio 2D, mientras que si los vectores están alineados, el *span* es solo una línea.
## Dimensiones y dependencia lineal
- Al agregar un tercer vector, si este se encuentra en el *span* de los dos primeros, no se añade nueva información. En este caso, se dice que los vectores son **dependientes lineales**. Si cada vector añade una nueva dimensión, son **independientes lineales**.

# Bases de un espacio vectorial
- Una base de un espacio es un conjunto de vectores linealmente independientes que abarcan ese espacio. Esta definición es fundamental para entender la estructura de los espacios vectoriales y cómo se relacionan entre sí.