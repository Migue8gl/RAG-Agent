- #git | #workflow | #softwaredevelopment
- [[notas whisper]]

# Sección de contexto
- En este video, Niki discute dos modelos populares de flujo de trabajo en *Git*: **Git flow** y **GitHub flow**. Estos modelos son esenciales para gestionar el desarrollo de software en un entorno colaborativo, evitando conflictos entre desarrolladores.

# Git flow
- **Git flow** es un modelo estructurado que utiliza dos ramas principales: `main` y `develop`. La rama `main` contiene el código que puede ser desplegado en producción, mientras que `develop` se utiliza para el desarrollo activo. Los desarrolladores crean ramas de características (feature branches) a partir de `develop`, donde trabajan en nuevas funcionalidades. Una vez completada una característica, se crea un *pull request* (PR) para su revisión y eventual fusión en `develop`. Cuando hay suficientes características en `develop`, se crea una rama de lanzamiento (release branch) para preparar el despliegue en producción. Además, se pueden crear ramas de corrección rápida (hotfix branches) para solucionar problemas críticos directamente desde `main`.
## Estructura de Git flow
- `main` (o `master`) es la rama principal.
- `develop` es la rama de desarrollo activo.
- Ramas de características se crean a partir de `develop`.
- Ramas de lanzamiento se crean para preparar despliegues.
- Ramas de corrección rápida se crean para solucionar problemas críticos.

# GitHub flow
- **GitHub flow** es un modelo más simple y ágil. Comienza con la rama `main`, de la cual se crean ramas de características. A diferencia de Git flow, cada característica debe ser desplegable a producción de manera independiente. Después de realizar cambios en la rama de características, se crea un PR y se puede realizar pruebas en un entorno de pre-producción. Una vez aprobado, se fusiona la característica en `main`, lo que permite un despliegue rápido y continuo.
## Comparación entre Git flow y GitHub flow
- Git flow es más estructurado y adecuado para aplicaciones monolíticas, mientras que GitHub flow es más flexible y se adapta mejor a entornos de microservicios y despliegues continuos. GitHub flow permite iteraciones más rápidas y despliegues más frecuentes, lo que reduce el riesgo de errores en producción.

# Conclusiones sobre los flujos de trabajo
- La elección entre Git flow y GitHub flow depende de la madurez del equipo y del tipo de aplicación que se esté desarrollando. Ambos modelos ofrecen estructura y seguridad en el proceso de desarrollo, pero su efectividad varía según el contexto y las necesidades del equipo.