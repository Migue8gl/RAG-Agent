- #lineal | #transformaciones | #matrices | #algebra
- [[notas whisper]]

# Contexto
- Este contenido se centra en la comprensión de las *transformaciones lineales* y su relación con las matrices en el contexto del álgebra lineal.
- Se exploran las propiedades de estas transformaciones y cómo se pueden representar y calcular utilizando matrices.

# Transformaciones lineales
- Una *transformación* es una función que toma un vector como entrada y produce otro vector como salida. En álgebra lineal, se visualiza como un movimiento de vectores en el espacio.
## Propiedades de las transformaciones lineales
- Las transformaciones son lineales si mantienen dos propiedades: las líneas permanecen rectas y el origen no se desplaza. Esto significa que las transformaciones lineales mantienen las líneas paralelas y equidistantes.

# Representación matricial
- Las transformaciones lineales en dos dimensiones se pueden describir completamente mediante una matriz de $2 \times 2$. Esta matriz se construye a partir de las coordenadas de los vectores base *i-hat* y *j-hat*.
## Multiplicación de matrices
- Para aplicar una transformación a un vector, se multiplica la matriz por el vector. Esto se puede expresar como:
$$\begin{pmatrix} a & b \\ c & d \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} ax + by \\ cx + dy \end{pmatrix}$$
- Esta operación permite deducir la nueva posición del vector tras la transformación.

# Ejemplos de transformaciones
- Un ejemplo de transformación es la rotación de $90$ grados, donde la matriz resultante es:
$$\begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}$$
- Otro ejemplo es la *shear*, donde la matriz tiene la forma:
$$\begin{pmatrix} 1 & k \\ 0 & 1 \end{pmatrix}$$
donde $k$ es el factor de deformación.

# Conclusiones sobre el álgebra lineal
- Las transformaciones lineales son fundamentales para entender el álgebra lineal, ya que permiten visualizar y calcular cómo se mueven los vectores en el espacio.
- Comprender las matrices como representaciones de estas transformaciones facilita el aprendizaje de conceptos más avanzados en álgebra lineal, como la multiplicación de matrices y los valores propios.