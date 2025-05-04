- #langchain | #agent | #executor
- [[notas whisper]]

# Sección de contexto
- En este video se explica cómo construir un ejecutor de agente equivalente al actual de LangChain desde cero utilizando LangGraph. Se detallan los pasos necesarios para la instalación y configuración de paquetes, así como la creación de un agente y su estado.

# Instalación y configuración
- Para comenzar, se deben instalar varios paquetes: *LangChain*, *LangChain OpenAI* y *Tavilli Python*. Estos paquetes permiten utilizar clases de agente existentes y herramientas de búsqueda. También se deben establecer las claves API necesarias para *OpenAI*, *Tavilli* y *LangSmith*, que es la plataforma de observabilidad.

# Creación del agente
- Se crea el agente utilizando el mismo código que en LangChain. Se define una herramienta de búsqueda y se selecciona el modelo de lenguaje de *OpenAI*. Luego, se establece el estado del gráfico, que es crucial para el seguimiento de la información a lo largo del proceso. Este estado permite que los nodos actualicen la información sin necesidad de pasarla constantemente entre ellos.
## Definición del estado del agente
- El estado del agente incluye mensajes de entrada, historial de chat y resultados de acciones. Se especifica cómo se deben manejar las actualizaciones al estado, permitiendo tanto la sobrescritura como la adición de información.

# Definición de nodos y bordes
- Se definen dos nodos principales: el nodo del agente, que determina la acción a tomar, y el nodo que invoca las herramientas. Además, se añaden bordes condicionales y normales para gestionar el flujo de decisiones basado en los resultados del agente.
## Ejecución de herramientas
- Se implementa una función que ejecuta las herramientas basándose en la decisión del agente. Esta función también registra los pasos intermedios, que se añaden a la lista existente de acciones del agente.

# Construcción del gráfico
- Se crea un nuevo gráfico importando *state graph* de LangGraph y se añaden los nodos definidos anteriormente. Se establece un punto de entrada y se añaden bordes condicionales que determinan si continuar o finalizar el proceso. Finalmente, se compila el gráfico en un ejecutable de LangChain.
## Ejecución y resultados
- Se ejecuta el gráfico con entradas específicas y se observa el resultado de cada nodo. Se pueden ver los resultados intermedios y el estado final del agente, que incluye la entrada, el historial de chat y los resultados de las acciones. Además, se puede visualizar el proceso en LangSmith para un análisis más detallado.