- #docker | #fastapi | #uv | #python
- [[notas whisper]]

# Contexto
- En este video se aborda el proceso de contenedorización de una aplicación *FastAPI* utilizando *Docker* y el paquete *UV* para gestionar dependencias.
- Se integran conceptos de gestión de proyectos y entornos en Python, facilitando la instalación y ejecución de aplicaciones web.

# Integración de fastapi y docker
- Para comenzar, se debe crear un archivo *Dockerfile* que contenga las instrucciones necesarias para construir la imagen de la aplicación. Se parte de una imagen base de Python y se instalan las dependencias necesarias.
## Ejemplo de Dockerfile
- Un ejemplo básico de *Dockerfile* para una aplicación *FastAPI* podría ser el siguiente:
```dockerfile
FROM python:3.12-slim
COPY . /app
WORKDIR /app
RUN uv sync --frozen
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

# Comandos de docker
- Para construir la imagen de Docker, se utiliza el comando `docker build`, especificando el nombre de la imagen y el contexto actual. Por ejemplo:
```bash
docker build -t fastapi-app .
```
- Una vez construida la imagen, se puede ejecutar un contenedor con el comando `docker run`, mapeando los puertos necesarios:
```bash
docker run -p 8000:8000 fastapi-app
```

# Gestión de dependencias con uv
- El comando `uv sync` se utiliza para instalar las dependencias especificadas en los archivos `pyproject.toml` y `uv.lock`. Esto asegura que todas las dependencias y subdependencias se instalen correctamente en el entorno del contenedor.
## Estructura de archivos
- Es importante que el proyecto contenga los siguientes archivos:
  - `pyproject.toml`: Define las dependencias del proyecto.
  - `uv.lock`: Contiene un registro de las versiones de las dependencias instaladas.

# Respuesta de la aplicación
- Al acceder a la aplicación en el navegador a través de `localhost:8000`, se espera recibir una respuesta en formato JSON. Por ejemplo, una respuesta simple podría ser:
```json
{"message": "hello from fast API"}
```
- Se sugiere realizar ajustes en la respuesta para que sea más adecuada según el contexto de la aplicación.

# Recursos adicionales
- Se recomienda consultar la documentación de *UV* para más guías de integración, incluyendo el uso de *UV* en aplicaciones *Django* y herramientas de gestión como *pytest* y *ruff*.
- La *pyproject.toml* permite especificar configuraciones para diferentes herramientas en un solo archivo, facilitando la gestión del proyecto.