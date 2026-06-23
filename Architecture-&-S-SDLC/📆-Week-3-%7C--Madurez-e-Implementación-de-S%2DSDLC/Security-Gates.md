<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
  [[_TOC_]]
</details>

* * *
# Capítulo 4: Security Gates

## ❓ ¿Qué son los Security Gates?

Un **Security Gate** es un punto de control obligatorio dentro del ciclo de desarrollo donde se evalúan criterios de seguridad antes de permitir que el software avance a la siguiente fase.
Se implementan como:
*   Controles manuales (revisiones)
    
*   Controles automatizados (escaneos)
    
*   Políticas como código
    
*   Validaciones en CI/CD
    
*   Controles de compliance en cloud

## ✅ Ubicación de Security Gates en el S-SDLC
| Fase | Security Gate | Control Técnico | Criterio de Bloqueo |
| --- | --- | --- | --- |
| **Planeamiento** | Aprobación de requisitos de seguridad | Definición formal de requisitos de seguridad, clasificación de activos y análisis preliminar de riesgos | No existen requisitos de seguridad definidos o no están alineados con el nivel de riesgo |
| **Análisis** | Threat Modeling aprobado | Identificación de amenazas, análisis de impacto y definición de mitigaciones documentadas | Amenazas críticas sin mitigación o sin aceptación formal del riesgo |
| **Diseño** | Validación de arquitectura segura | Revisión de arquitectura contra estándares internos y principios de seguridad (mínimo privilegio, segmentación, cifrado, resiliencia) | Incumplimiento de controles de seguridad obligatorios |
| **Desarrollo** | SAST + SCA | Análisis estático de código, detección de vulnerabilidades en dependencias y secretos | Vulnerabilidades críticas o exposición de credenciales |
| **Pruebas** | DAST + Test de seguridad | Pruebas dinámicas, validación de autenticación/autorización, pruebas de APIs | Vulnerabilidades explotables de severidad alta o crítica |
| **Implementación** | Escaneo de infraestructura como código + Validación de configuraciones | Análisis de configuraciones, cumplimiento de políticas y controles de seguridad definidos | Recursos no conformes o configuraciones inseguras |
| **Mantenimiento** | Monitorización continua + Control de desviaciones | Gestión de vulnerabilidades, detección de configuraciones desviadas y revisión periódica de riesgos | Vulnerabilidades críticas activas o desviaciones no remediadas |


## ✅ Buenas prácticas
* **Automatización total de los controles**:  Los _gates_ manuales generan fricción y relentizan el desarrollo.

* 2. **_Thresholds_ claros**: Definir criterios técnicos medibles.

* 3. **Separación de ambientes**: Configurar controles y _thresholds_ específico para cad entorno (Dev, Prod,...).

* 4. **Observabilidad de seguridad**: Unificar la información de todas las _gates_ en un único dashboard.

* 5. **Security as Code**: Versionar políticas en Git.

* 6. **Excepciones controladas**: Todas las excepciones tienen que estar justificadas y tener un tiempo de expiración.
