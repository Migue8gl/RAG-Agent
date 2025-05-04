# 27/02/2025
## Kit Consulting
- Dos proyectos con fundacion esclerosis madrid.
	- crear un chatbot de whasapp:
        - mandar recordatorios a una base de datos.
        - no interacción. 
	- análisis de datos:
        - informes sobre personas con esclerosis.
        - toma de requisitos online con ellos.
- Formación de IA enfocada en utilización de herramientas B2C (nada técnico).

# 03/03/2025
## Pregunta sobre debuggeo de aplicación de langgraph
- Se utiliza ngrok para debuggear por whatsapp. 
- Para debuggear archivo de run -> python -X utf8 -m app.run

# 18/03/2025
## Reunión con cliente, mantenimiento de Data Lake
- Su objetivo es mantener lo que hay. Querían añadir informes de encuestas.
- Quieren meter un agente de IA.
- Tenant de la organización.
- Fuentes del Ministerio de Sanidad.
- Servicios:
	- Una cuenta de almacenamiento del tipo Azure Data Lake Gen2 con Jerarquía de Archivos. 
	- Un servicio de Azure Synapse, para la ingesta, modelado y explotación de los datos, siendo su uso:  
		- Servicios de copia de datos con Synapse Integration Service  
		- Servicio de SQL Serveless Pool de Azure Synapse
- Incorporan algunos datos por excel (nos llega excel).
- Análisis de los datos e informes con Power BI.
- Quieren añadir nuevos informes y nuevos conectores.
### Requisitos
- Tenant de la organización (accesos y configuraciones en Azure).
- Informes de encuestas (fuentes, estructura, frecuencia de actualización).
- Funcionalidad esperada del agente de IA.
- Nuevos informes y conectores (datos adicionales y origen).
- Jerarquía de archivos y organización en Data Lake.
- Uso actual de Synapse Integration Service.
- Origen de los datos almacenados (fuentes internas y externas, APIs utilizadas) y documentación acerca de su significado.