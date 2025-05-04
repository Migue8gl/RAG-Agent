- #facialrecognition | #ai | #googlecloud | #ethics
- [[notas whisper]]

# Contexto
- Este estudio de caso describe cómo los principios y procesos de revisión de IA de Google Cloud han influido en su enfoque hacia la tecnología de reconocimiento facial.
- Se examinan las decisiones tomadas para mitigar sesgos y asegurar un uso responsable de esta tecnología.

# Desarrollo del API de reconocimiento de celebridades
- En $2019$, Google Cloud lanzó el API de *Celebrity Recognition*, diseñado para ayudar a los clientes de medios y entretenimiento a etiquetar celebridades en su contenido. Este API es un modelo de IA preentrenado que reconoce miles de actores y atletas basándose en imágenes licenciadas. A pesar de ser una solicitud popular, el reconocimiento facial fue inicialmente excluido del *Cloud Vision API* debido a preocupaciones sobre sesgos injustos. 
## Proceso de revisión de IA
- La revisión de IA permitió un análisis crítico del contexto social y los desafíos de la tecnología. Se identificaron usos positivos, como la autenticación facial para el acceso a información sensible y su aplicación en la lucha contra la trata de personas. Sin embargo, se enfatizó la necesidad de desarrollar estas tecnologías de manera responsable, evitando la vigilancia que infrinja normas internacionales y protegiendo la privacidad de las personas.

# Evaluación de impacto en derechos humanos
- Google colaboró con expertos externos y líderes de derechos civiles para incorporar diversas experiencias en su revisión. Se realizó una evaluación de impacto en derechos humanos con la consultora *Business for Social Responsibility* (BSR), que ayudó a definir las capacidades y políticas del API, asegurando que se consideraran los derechos humanos durante todo el ciclo de desarrollo del producto.
## Análisis de equidad
- Se llevaron a cabo pruebas de equidad para evaluar el rendimiento del API en función del tono de piel y género. Se descubrieron errores en los conjuntos de datos de entrenamiento, especialmente para personas de piel más oscura. Se ajustaron las etiquetas de tono de piel utilizando la escala de tipo de piel de Fitzpatrick, basada en investigaciones previas sobre sesgos en algoritmos de análisis facial.

# Mejora del conjunto de datos
- Se identificó que un pequeño número de actores representaba una proporción significativa de las identificaciones erróneas. Al revisar las imágenes de los actores, se encontró que las imágenes de entrenamiento no representaban adecuadamente su apariencia actual. Se amplió el conjunto de datos para incluir imágenes de celebridades en diferentes etapas de sus carreras, lo que mejoró el rendimiento del modelo.
## Importancia de la representación
- Este proceso subrayó la importancia de considerar el contexto general de la solución y la representación en los medios. Solo después de un análisis exhaustivo y mejoras en la equidad, Google se sintió cómodo lanzando el API. 

# Conclusiones sobre el desarrollo responsable de IA
- En $2020$, Google observó que otras empresas tecnológicas estaban limitando o abandonando su negocio de reconocimiento facial debido a preocupaciones sobre la tecnología. El proceso de gobernanza de IA de Google permitió investigar y definir un producto que se alineara con sus principios de IA. Además, se lanzó la escala de tono de piel *Monk Skin Tone MST*, que ayuda a comprender mejor la representación en las imágenes.