
<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
 [[_TOC_]]
</details>

Capítulo 1: Modelado de Arquitectura (Los 6 Pilares de la Resiliencia)
------------------------------------------------------------

### ✅ De la Infraestructura Física al "Security as Code"

En el modelo tradicional, la seguridad era un "muro" (Firewall). En la nube, la seguridad es un **tejido** distribuido. El modelado de arquitectura nos permite visualizar cómo los componentes interactúan y dónde debemos aplicar controles antes de que la infraestructura se despliegue mediante herramientas de **IaC (Infrastructure as Code)** como Terraform o Bicep.

* * *


### 1. Micro-segmentación y Zero Trust (ZTA)

El modelo de "red perimetral" es insuficiente. Aplicamos **Zero Trust** segmentando la red hasta el nivel más granular posible.
*   **Concepto:** Cada carga de trabajo (Workload) tiene su propio micro-perímetro.
    
*   **Control Técnico:** Uso de **NSGs/Security Groups** y políticas de red que prohíben el tráfico entre componentes de la misma subred a menos que sea estrictamente necesario.
    
*   **Riesgo Mitigado:** Movimiento lateral del atacante.
    

###  2. Landing Zones y Gobernanza Automática

Garantizamos que cualquier recurso nazca seguro mediante una estructura de cuentas estandarizada.
*   **Concepto:** Implementación de **Guardrails** (vallas de seguridad) y políticas (Azure Policy/SCPs) que impiden configuraciones inseguras de forma automática.
    
*   **Control Técnico:** Despliegue mediante **IaC (Infrastructure as Code)** para asegurar consistencia.
    
*   **Riesgo Mitigado:** Error humano y configuraciones incorrectas (_Misconfigurations_).
    

###  3. Topología Hub & Spoke

Centralizamos el control de tráfico en entornos complejos o de nube híbrida.
*   **The Hub:** Centraliza firewalls (NGFW), VPNs y circuitos privados (ExpressRoute/Direct Connect).
    
*   **The Spokes:** Aíslan las aplicaciones. Todo tráfico hacia internet o hacia On-prem es "forzado" a pasar por el Hub para inspección.
    
*   **Riesgo Mitigado:** Exposición directa de servicios y falta de visibilidad del tráfico.
    

* * *

###  4. IAM Identity-First (El Nuevo Perímetro)

En la nube, la **Identidad** es la primera línea de defensa, incluso antes que la red.
*   **Concepto:** Eliminación de llaves estáticas en favor de **Managed Identities**.
    
*   **Control Técnico:** Implementación de **Just-In-Time (JIT)** y acceso condicional basado en el riesgo del usuario y el dispositivo.
    
*   **Riesgo Mitigado:** Robo de credenciales y escalada de privilegios.
    

###  5. Arquitectura de Observabilidad y Telemetría

Diseñamos la infraestructura para que sea "auditable" por el SOC desde el primer día.
*   **Concepto:** Agregación centralizada de logs (VPC Flow Logs, DNS Logs, CloudTrail) en una zona de seguridad aislada.
    
*   **Control Técnico:** Integración nativa con el **SIEM/SOAR** corporativo.
    
*   **Riesgo Mitigado:** Ceguera operativa y persistencia del atacante por falta de detección.
    

###  6. Resiliencia y Recuperación ante Desastres (DR/BCP)

La seguridad incluye la **Disponibilidad**. Una arquitectura segura debe sobrevivir a un Ransomware.
*   **Concepto:** Creación de **Air-Gapped Vaults** (bóvedas aisladas) para backups que no pueden ser modificados por las credenciales de producción.
    
*   **Control Técnico:** Diseño de _Failover_ multi-región y replicación de datos inmutable.
    
*   **Riesgo Mitigado:** Interrupción del negocio y pérdida definitiva de datos.

* * *

### ✅ Conectividad Híbrida: Asegurando el "Puente"

El analista debe evaluar el riesgo de la conexión entre el centro de datos local (Legacy) y la Cloud:
| **Método** | **Nivel de Seguridad** | **Consideración Técnica** |
| --- | --- | --- |
| **Public Endpoint + WAF** | Bajo/Medio | El servicio es visible en Internet; dependemos totalmente de la capa de aplicación. |
| **Site-to-Site VPN** | Medio/Alto | Cifrado IPsec. Seguro, pero el tráfico viaja por la infraestructura pública de Internet. |
| **Private Connectivity** | Máximo | **Direct Connect (AWS)** o **ExpressRoute (Azure)**. Los datos nunca tocan el internet público. | 

* * *

### 💡 Pro-Tip para el Analista: "Blast Radius" (Radio de Explosión)

Al modelar una arquitectura, pregunta siempre: _“Si este componente es hackeado, ¿qué más puede alcanzar el atacante?”_. Un buen diseño arquitectónico debe **minimizar el Blast Radius** mediante el aislamiento y la segmentación estricta de cuentas y redes.

* * *

### 📝 Ejercicio de Análisis

**Caso de Estudio:** Un atacante compromete una cuenta de desarrollador. Gracias a la **Landing Zone (Pilar 2)**, no puede crear recursos costosos. Gracias a la **Micro-segmentación (Pilar 1)**, no puede saltar del servidor web a la DB.
**Pregunta:** Si el atacante intenta borrar los backups para forzar un pago de rescate, ¿qué pilar debería evitar que lo logre y mediante qué técnica?