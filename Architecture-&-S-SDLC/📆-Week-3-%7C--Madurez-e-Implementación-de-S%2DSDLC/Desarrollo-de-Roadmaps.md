<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
  [[_TOC_]]
</details>

* * *

# Capítulo 2: Desarrollo de Roadmaps
## ✅Conceptos generales
### ¿Qué es un Roadmap de S-SDLC?

Un **roadmap de S-SDLC** es un plan estratégico y técnico alineado con riesgo y negocio que define:
*   Estado actual de madurez.
    
*   Estado objetivo.
    
*   Fases de implementación.
    
*   Prioridades.
    
*   Métricas de seguimiento.
    
*   Recursos necesarios.
    

### Principios de diseño de un roadmap

1.  Basado en riesgo real.
    
2.  Desarrollarlo de manera progresivo.
    
3.  Priorizar la automatización de procesos.
    
4.  Medible (KPIs claros).

5.  Alineado a cultura DevOps.
    
6.  Integrado con estrategia Cloud.

## ✅ ¿Cómo construir un RoadMap?

### 1. Evaluación del estado actual (Assessment)
Evaluar la madurez de cada fase del S-SDLC, por ejemplo:
*   ¿Existe política de desarrollo seguro?
    
*   ¿Se usa SAST?
    
*   ¿Se escanea IaC?
    
*   ¿Hay separación de entornos?
    
*   ¿El pipeline tiene mínimo privilegio?
    
*   ¿Existen métricas?

Se pueden utilizar modelos como OWASP SAMM o PESA para realizar la evaluación

### 2. Definición del estado objetivo
Una vez evaluado el estado actual, planear y definir acciones de mejora divididas en:
*   Corto plazo
*   Medio plazo
*   Largo plazo

### 3. Priorización por impacto y esfuerzo
Identificar y priorizar las acciones de mejora maximizando el impacto y minimizando el esfuerzo

### 4. Definición de métricas de seguimiento
Establecer métricas que permitan seguir la evolución de la implementación del roadmap. Por ejemplo:
*   Porcentaje de repositorios con SAST activo.
    
*   Porcentaje pipelines con escaneo IaC.
    
*   Número de vulnerabilidades críticas abiertas.
        
*   Tiempo medio de aprobación de Pull Requests con findings.

## ✅ Errores comunes al crear un roadmap
    
1.  No involucrar al equipo DevOps.
    
2.  No asignar responsables específicos a cada tarea.
    
3.  No definir métricas.
    
4.  Hacerlo teórico sin integración en pipeline.
    
5.  No considerar cultura organizacional.
    
6.  No revisar permisos del propio pipeline.