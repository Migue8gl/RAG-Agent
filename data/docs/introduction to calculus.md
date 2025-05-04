- #cálculo | #derivadas | #tangentes | #funciones
- [[notas whisper]]

# Contexto
- Este resumen presenta una introducción al cálculo, enfocándose en conceptos fundamentales como la pendiente, la tasa de cambio promedio y la derivada.
- Se exploran las transiciones de la notación de línea a la notación de función y se introduce el concepto de límite.

# Pendiente de una línea
- La pendiente de una línea se define como el cambio en la altura (rise) dividido por el cambio en la distancia horizontal (run), expresado como $m = \frac{y_2 - y_1}{x_2 - x_1}$.
- En notación de funciones, esto se convierte en $m = \frac{f(x_2) - f(x_1)}{x_2 - x_1}$.

## Tasa de cambio promedio
- Cuando se trabaja con funciones no lineales, la pendiente se interpreta como una **tasa de cambio promedio** entre dos puntos.
- Esta tasa se puede visualizar conectando dos puntos en la gráfica, formando una línea secante.

# Límite y tasa de cambio instantánea
- A medida que los puntos se acercan, la distancia $h$ se reduce a cero, lo que transforma la línea secante en una **línea tangente**.
- La **tasa de cambio instantánea** se define como el límite de la tasa de cambio promedio cuando $h$ tiende a cero, representada como $\lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$.

## Derivada
- La derivada se denota como $f'(x)$ y representa la pendiente de la línea tangente en un punto específico de la función.
- Por ejemplo, para la función $f(x) = x^2$, la derivada se calcula como $f'(x) = 2x$.

# Ejemplo práctico
- Para encontrar la pendiente de la tangente a la parábola $f(x) = x^2$ en el punto $(1,1)$, se evalúa $f'(1) = 2(1) = 2$.
- Esto indica que la pendiente de la tangente en ese punto es $2$.

## Conclusión
- El cálculo permite analizar cómo cambian las funciones en puntos específicos, utilizando herramientas como límites y derivadas para obtener información sobre su comportamiento.