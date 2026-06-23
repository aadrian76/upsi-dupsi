
<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
 [[_TOC_]]
</details>

Este capítulo es el "puente" final. De nada sirve identificar una amenaza si no sabemos comunicársela al equipo de desarrollo de forma clara y priorizada. Como analista, tu producto final no es el diagrama, sino los **Requisitos de Seguridad** (Controles) que el equipo debe implementar.

* * *

===============================================================

Capítulo 4: Definición de Requisitos de Seguridad
-------------------------------------------------

### ✅ De la Amenaza a la Acción

El paso final del _Threat Modeling_ es la traducción. Un desarrollador no siempre necesita saber qué es "STRIDE", pero sí necesita saber exactamente qué librería usar o qué validación programar. En **IriusRisk**, esta traducción ocurre mediante la generación automática de **Countermeasures** (Contramedidas).

* * *

### ✅ ¿Qué es un Requisito de Seguridad Accionable?

Para que un requisito sea útil, debe cumplir con tres criterios:
1.  **Específico:** No digas "Asegura la base de datos". Di "Implementar cifrado AES-256 en reposo para la base de datos RDS".
    
2.  **Vinculado a un Estándar:** Cada requisito debe mapearse a un marco de cumplimiento (ej. ASVS de OWASP, NIST, o políticas internas de la compañía).
    
3.  **Verificable:** Debe existir una forma clara de saber si el requisito se ha cumplido (ej. una prueba de unidad o una configuración de infraestructura).
    

* * *

### ✅ El Ciclo de Vida del Requisito en IriusRisk

Como Analyst, gestionarás los requisitos siguiendo este flujo:

#### 1. Priorización (Severidad)

No todos los requisitos tienen la misma urgencia. IriusRisk calcula el riesgo basándose en el **Impacto** y la **Probabilidad**. Tu tarea es validar si la prioridad asignada coincide con el contexto del cliente.

#### 2. Selección de Contramedidas

IriusRisk sugerirá varias opciones. Deberás elegir la más adecuada:
*   **Mitigar:** Implementar el control (ej. añadir MFA).
    
*   **Transferir:** Pasar el riesgo a un tercero (ej. usar un proveedor de identidad gestionado).
    
*   **Aceptar:** Si el riesgo es muy bajo o el coste de mitigación es demasiado alto (requiere aprobación senior).
    

#### 3. Sincronización con Desarrollo (ALM Integration)

Una vez definidos, los requisitos no se quedan en IriusRisk. Se sincronizan con herramientas de gestión de tareas como **Jira** o **Azure DevOps**.
*   El analista "empuja" el requisito.
    
*   El desarrollador lo recibe como una "User Story" o "Task".
    
*   Cuando el desarrollador cierra el ticket, IriusRisk actualiza el estado del modelo automáticamente.
    

* * *

### 💡 Consejos para la Redacción de Requisitos

*   **Usa el lenguaje del desarrollador:** Si el proyecto es en Java, busca si existe una contramedida específica para ese lenguaje.
    
*   **Adjunta referencias:** Incluye links a la documentación de seguridad de la empresa o a guías de OWASP.
    
*   **Define el "Definition of Done" (DoD):** Ayuda al equipo de QA indicando cómo se debería testear ese requisito.
    

* * *

### 📝 Ejercicio: Traduciendo Hallazgos

**Escenario:** En tu DFD identificaste que el flujo entre el _Web Server_ y la _Database_ no tiene cifrado.
1.  **Amenaza:** Intercepción de datos sensibles en tránsito (Information Disclosure).
    
2.  **Tarea del Analista:** Busca en IriusRisk la contramedida adecuada.
    
3.  **Redacción:** Escribe el título y una breve descripción del requisito tal como te gustaría que le apareciera a un desarrollador en su tablero de Jira.
    

* * *

### ✅ Punto de Control Final (Final Checkpoint)

Para completar esta capítulo deberás realizar un ejercicio práctico integral:
**El Reto:** Realizar un "Mini-Threat Model" de una aplicación de **E-commerce que utiliza un recomendador de productos basado en IA**.
1.  **Dibuja el DFD** en IriusRisk (Incluye: Usuario, Web Front-end, API, DB de Clientes y Servicio de IA).
    
2.  **Identifica Trust Boundaries.**
    
3.  **Genera el listado de las 5 amenazas principales** (incluyendo al menos una específica de IA).
    
4.  **Propón 5 requisitos de seguridad** para mitigar esas amenazas.
    