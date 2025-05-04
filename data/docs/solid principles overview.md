- #programming | #solid | #principles
- [[notas whisper]]

# Sección de contexto
- En esta conversación se discuten los principios SOLID, que son fundamentales para el desarrollo de software en lenguajes orientados a objetos. Se explican cada uno de los principios y su importancia en la escritura de código limpio y mantenible.

# Sección 1: Single Responsibility Principle
- El **Single Responsibility Principle** establece que una clase debe tener una única responsabilidad. Si una clase tiene múltiples responsabilidades, es más probable que se introduzcan errores al realizar cambios. Por ejemplo, en una aplicación de enseñanza, una clase de estudiante que maneja múltiples funciones (almacenamiento de datos, envío de correos, inscripción) rompe este principio. Se sugiere dividir estas responsabilidades en clases separadas para evitar conflictos y facilitar la reutilización del código.

# Sección 2: Open/Closed Principle
- El **Open/Closed Principle** indica que el código debe estar abierto a extensiones pero cerrado a modificaciones. Para agregar funcionalidad sin modificar clases existentes, se pueden utilizar patrones como el *decorator pattern* o *extension methods*. Esto permite añadir nuevas funcionalidades sin romper las pruebas unitarias existentes y minimiza efectos secundarios no deseados.

# Sección 3: Liskov Substitution Principle
- El **Liskov Substitution Principle** establece que una clase hija debe poder sustituir a su clase padre sin alterar el comportamiento del programa. Si una clase hija no puede realizar todas las funciones de la clase padre, se rompe este principio. Para solucionarlo, se debe crear una jerarquía de clases adecuada que respete esta relación.

# Sección 4: Interface Segregation Principle
- El **Interface Segregation Principle** sugiere que las interfaces no deben ser demasiado grandes, obligando a las clases a implementar métodos que no utilizan. Para evitar esto, se pueden dividir las interfaces en varias más pequeñas, permitiendo que las clases implementen solo lo que necesitan. Esto mejora la claridad y la mantenibilidad del código.

# Sección 5: Dependency Inversion Principle
- El **Dependency Inversion Principle** establece que los módulos de alto nivel no deben depender de módulos de bajo nivel, sino de abstracciones. Esto se logra mediante la inyección de dependencias, donde se crea una interfaz para las clases de repositorio y se inyecta en las clases de servicio. Esto permite que el código sea más flexible y fácil de probar, ya que se pueden usar *mocks* durante las pruebas.