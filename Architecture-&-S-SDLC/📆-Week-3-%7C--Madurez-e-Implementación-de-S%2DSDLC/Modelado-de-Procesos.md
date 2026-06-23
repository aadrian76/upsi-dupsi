<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
  [[_TOC_]]
</details>

# Capítulo 3: Modelado de Procesos

## ✅ ¿Qué es el Modelado de Procesos en S-SDLC?

Es la representación estructurada y documentada del flujo de desarrollo incluyendo:
*   Actividades
    
*   Roles
    
*   Entradas y salidas
    
*   Controles de seguridad
    
*   Puntos de decisión
    
*   Métricas

## ✅ Objetivos del Modelado de Procesos

*   Estandarizar el desarrollo seguro.
    
*   Identificar _gaps_ de seguridad.
    
*   Definir responsabilidades claras.
    
*   Reducir variabilidad entre equipos.
    
*   Automatizar controles.
    
*   Facilitar auditorías.

## ✅ Elementos clave del modelo de proceso

Un modelo completo debe incluir:
    
1.  Actividades por fase de S-SDLC.
    
2.  Controles obligatorios.
    
3.  Evidencias generadas.
    
4.  Roles responsables.
    
5.  Herramientas utilizadas.
    
6.  Criterios de aceptación.

## ✅ Ejemplo de actividades por fase

| Fase | Actividad clave | Control de seguridad |
| --- | --- | --- |
| Planeamiento | Definir requisitos | Documento de requisitos de seguridad |
| Análisis | Threat modeling | Matriz STRIDE | 
| Diseño | Arquitectura segura | Validación IAM y segmentación | 
| Desarrollo | Implementación | SAST + revisión PR
| Pruebas | Validación | DAST + escaneo IaC |
| Implementación | Despliegue | Pipeline firmado | 
| Mantenimiento | Monitorización | Alertas + revisión IAM|
