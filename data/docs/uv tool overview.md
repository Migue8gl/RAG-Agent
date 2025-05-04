- #python | #uv | #dependencies | #tool
- [[notas whisper]]

# Contexto
- UV es una herramienta que combina múltiples funcionalidades para la gestión de proyectos en Python, incluyendo la administración de dependencias y entornos virtuales.
- Esta herramienta, desarrollada en Rust, promete ser más rápida que otras alternativas existentes en el ecosistema Python.

# Instalación de UV
- Existen varias formas de instalar UV. Para usuarios de Mac, la opción más sencilla es usar *brew* con el comando `brew install uv`. También se puede instalar usando un *curl* para obtener un instalador independiente, o mediante *pip* con `pip install uv`. Otra opción es usar *cargo* y proporcionar el repositorio de Git.
## Comandos iniciales
- Una vez instalado, se puede acceder a UV a través de la línea de comandos. Por ejemplo, se puede habilitar la finalización de comandos en la terminal para facilitar su uso. Además, se puede inicializar un nuevo proyecto con el comando `uv init`, que permite crear aplicaciones o bibliotecas de Python.

# Gestión de dependencias
- UV permite agregar y eliminar dependencias de manera sencilla. Para añadir una dependencia, se utiliza `uv add nombre_paquete`, y para eliminarla, `uv remove nombre_paquete`. Esto actualiza automáticamente el archivo *pyproject.toml* del proyecto.
## Ejemplo de uso
- Para agregar múltiples dependencias, se pueden listar en un solo comando. La eliminación de dependencias es igualmente rápida y eficiente, lo que facilita la gestión del entorno de desarrollo.

# Funcionalidades avanzadas
- UV soporta espacios de trabajo, permitiendo gestionar múltiples proyectos que comparten dependencias. Esto es útil para monorepos que contienen varias aplicaciones de Python. Al inicializar un proyecto dentro de un espacio de trabajo, UV utiliza un entorno virtual compartido.
## Herramientas y scripts
- UV también permite ejecutar herramientas como *ruff* directamente desde la línea de comandos. Se pueden instalar y desinstalar herramientas fácilmente, así como actualizar a nuevas versiones. Además, UV detecta automáticamente las versiones de Python instaladas en el sistema y permite instalar versiones específicas.

# Consideraciones finales
- Aunque UV es una herramienta poderosa, hay características que aún no están implementadas, como la posibilidad de definir scripts personalizados. También se sugiere la inclusión de un backend de construcción propio para simplificar el proceso de publicación de proyectos. Actualmente, se utiliza *hatchling* como backend de construcción por defecto.