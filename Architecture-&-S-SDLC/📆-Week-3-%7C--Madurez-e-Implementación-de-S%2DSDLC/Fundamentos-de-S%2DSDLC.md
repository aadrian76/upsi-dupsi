<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
  [[_TOC_]]
</details>

* * *


# Capítulo 1: Fundamentos de S-SDLC
## ✅ Conceptos generales

### ¿Qué es S-SDLC?

El **Secure Software Development Life Cycle (S-SDLC)** es la evolución del SDLC tradicional incorporando seguridad como requisito fundamental.
No se trata de añadir un pentest al final, sino de:
*   Diseñar con seguridad (Security by Design)
    
*   Implementar con seguridad (Secure Coding)
    
*   Validar continuamente
    
*   Monitorizar y responder en producción


### Diferencias entre SDLC y S-SDLC
| SDLC | S-SDLC |
| --- | --- |
| Seguridad al final | Seguridad desde los requisitos |
| Responsabilidad del equipo de seguridad | Responsabilidad compartida |
| Validación manual | Automatización en CI/CD |

## ✅ Principios clave

*   **Shift Left**: incorporación de controles de seguridad en fases tempranas del desarrollo.
    
*   **DevSecOps**: seguridad integrada en pipelines.
    
*   **Threat Modeling** como requisito
        
## ✅  Fases del S-SDLC
*   **Planeamiento:** Definir requisitos de seguridad y cumplimiento.
    
*   **Análisis:** Identificar amenazas y riesgos antes del diseño.
    
*   **Diseño:** Arquitectura segura con mínimo privilegio y gestión de secretos.
    
*   **Desarrollo:** Código seguro y escaneos automáticos.
    
*   **Pruebas:** Validación técnica de vulnerabilidades y configuración Cloud.
    
*   **Implementación:** Despliegue controlado y monitorizado.
    
*   **Mantenimiento:** Mejora continua basada en métricas y monitoreo.

* * *

## ✅ Riesgos y amenazas asociadas

### Riesgos por no implementar S-SDLC

*   Vulnerabilidades en producción
    
*   Exposición de secretos en repositorios
    
*   Uso de dependencias vulnerables
    
*   Despliegue de contenedores inseguros
    
*   Escalada de privilegios en IAM
    


### Amenazas típicas

*   Inyección SQL / RCE
    
*   Supply Chain Attacks
        
*   Exposición de credenciales
        
*   Infraestructura mal configurada (S3 público, buckets GCS públicos)
    

### Riesgo en entornos Cloud

En Cloud, el riesgo aumenta por:    
*   Reutilización de plantillas IaC vulnerables
    
*   Exposición pública por error humano
    
*   CI/CD con permisos excesivos

## ✅ Recursos
https://www.microsoft.com/es-mx/power-platform/topics/phases-of-the-software-development-lifecycle
