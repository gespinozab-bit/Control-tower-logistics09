# SDLC Elegido
   El proyecto adopta un SDLC Ágil basado en Kanban, complementado con prácticas de Scrum adaptadas a un entorno de desarrollo 
un modelo ágil simplificado que permite:
•	Entregas incrementales
•	Adaptabilidad a cambios
•	Control visual del flujo de trabajo
•	Priorización continua
•	Integración constante

```mermaid
flowchart TD
    A[Requerimiento] --> B[Análisis]
    B --> C[Diseño]
    C --> D[Implementación]
    D --> E[Pruebas]
    E --> F[Integración Continua]
    F --> G[Entrega Incremental]
    G --> A
```
Este enfoque permite retroalimentación continua y mejora progresiva del sistema.

# Workflow de Desarrollo
     El proyecto utiliza GitHub como repositorio central y aplica un modelo de ramas basado en GitFlow simplificado.

# Estrategia de Ramas
•	main → rama estable (versión lista para entrega)
•	develop → integración de funcionalidades
•	feature/* → nuevas funcionalidades
•	bugfix/* → correcciones de errores

# Flujo de Trabajo
```mermaid
flowchart LR
    A[Crear Issue] --> B[Mover a Ready]
    B --> C[Crear rama feature desde develop]
    C --> D[Implementar funcionalidad]
    D --> E[Crear Pull Request]
    E --> F[Validación CI - Azure Pipeline]
    F --> G[Merge a develop]
    G --> H[Entrega incremental en main]
```

# Modelo de Ramas
```mermaid
gitGraph
    commit
    branch develop
    checkout develop
    commit
    branch feature-inventario
    checkout feature-inventario
    commit
    checkout develop
    merge feature-inventario
    commit
    checkout main
    merge develop
 ```


# Gestión del Trabajo – Kanban
Se utiliza GitHub Projects como tablero Kanban con las siguientes columnas:
•	Backlog
•	Ready
•	In Progress
•	Review
•	Done

```mermaid
flowchart LR
    A[Backlog] --> B[Ready]
    B --> C[In Progress]
    C --> D[Review]
    D --> E[Done]
```
Este flujo permite visualizar el estado de cada tarea y evitar acumulación de trabajo en proceso.

# Definition of Ready (DoR)
     Una tarea puede iniciar desarrollo cuando cumple:
•	 Caso de uso definido
•	 Criterios de aceptación claros
•	 Impacto en la capa Domain identificado
•	 Modelo de datos considerado
•	 Dependencias identificadas
•	 Issue registrada en GitHub


# Definition of Done (DoD)
     Una funcionalidad se considera terminada cuando:
•	 Implementación completa
•	 Código ubicado en la capa correcta 

# (Domain, Application, Infrastructure)
•	 Pruebas implementadas
•	 Build exitoso
•	 Azure Pipeline en estado exitoso
•	 Pull Request aprobado
•	 Documentación actualizada
•	 Sin errores críticos abiertos

#  Arquitectura del Proyecto
  El sistema está estructurado bajo principios de Clean Architecture, con separación clara de responsabilidades.

```mermaid
flowchart TD
    A[Frontend - Controller.web] --> B[API]
    B --> C[Application]
    C --> D[Domain]
    C --> E[Infrastructure]
```

# Estructura Inicial del Repositorio
El repositorio sigue una estructura modular:
control-tower-logistics09/
```mermaid
flowchart LR
    A[control-tower-logistics09]

    A --> B[docs]
    B --> B1[Vision.md]
    B --> B2[Proceso.md]

    A --> C[src]
    C --> C1[backend]
    C1 --> C11[ControllerTower.Api]
    C11 --> C111[Application]
    C11 --> C112[Domain]
    C11 --> C113[Infrastructure]
    C11 --> C114[tests]

    C --> C2[frontend]
    C2 --> C21[Controller.web]

    A --> D[infra]
    D --> D1[docker]
    D --> D2[docker-compose.yml]
    D --> D3[db]
    D --> D4[scripts]

    A --> E[azure-pipeline.yml]
    A --> F[ControllerTower.sln]
    A --> G[README.md]
```

# Integración Continua
Se implementa integración continua mediante:
•	Azure Pipeline
•	Build automático
•	Ejecución de pruebas
•	Validación antes de merge

Esto garantiza estabilidad en cada entrega incremental.
