
<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
 [[_TOC_]]
</details>

# Capítulo 3: Análisis de Vulnerabilidades Cloud (Servicios Nativos)


En la nube, el sistema operativo es la API. Por lo tanto, las vulnerabilidades más críticas no residen en "bugs" de software, sino en la **configuración de servicios nativos**. Como analista, tu objetivo es detectar el riesgo sistémico antes de que sea explotado.

### 1. IAM (Identity and Access Management): El Talón de Aquiles

IAM es el nuevo perímetro. Un error de permisos puede convertir un acceso limitado en un control total sobre la infraestructura (_Privilege Escalation_).
*   **Vulnerabilidades Críticas:**
    *   **Over-Privileged Roles:** Uso de comodines (`*`) en políticas. El analista debe buscar roles que permitan acciones como `iam:PassRole`, permitiendo a un atacante asignar privilegios administrativos a servicios que él controla.
        
    *   **Vulnerabilidad de Metadatos (IMDSv1):** El uso de versiones antiguas del servicio de metadatos permite que un ataque de tipo SSRF extraiga credenciales temporales del rol de la instancia.
        
    *   **Políticas de Confianza Abiertas:** Permitir que cuentas externas asuman roles sin una validación estricta (falta de `ExternalID` o condiciones de red).
        
*   **Análisis de Experto:** Implementar **Permission Boundaries**. Son "vallas" que limitan el máximo privilegio que una identidad puede alcanzar, independientemente de las políticas que tenga asociadas.
    

* * *

### 2. Almacenamiento (Cloud Storage): La Persistencia del Riesgo

Los buckets (S3, Blobs) son el objetivo principal debido a la sensibilidad de los datos que contienen. El riesgo aquí es la **exfiltración y el borrado malintencionado**.
*   **Vulnerabilidades Críticas:**
    *   **Exposición a "Usuarios Autenticados":** Un error común es permitir acceso a "Authenticated Users". En la nube, esto incluye a **cualquier persona con una cuenta personal** del mismo proveedor, no solo a miembros de tu empresa.
        
    *   **Falta de Inmutabilidad (Object Lock):** Ante un Ransomware Cloud, el atacante intenta borrar tus backups originales. Sin _Object Lock_ o _Versioning_, el borrado es definitivo e instantáneo.
        
    *   **Cifrado sin Separación de Funciones:** Usar llaves gestionadas por el proveedor (SSE) en lugar de **Customer Managed Keys (KMS)**. Si el proveedor controla la llave y el acceso, el cifrado es vulnerable ante una escalada de privilegios interna.
        
*   **Análisis de Experto:** Activar el **MFA Delete** y configurar políticas de **Bucket Inmune** (WORM) para registros de auditoría y copias de seguridad críticas.
    

* * *

### 3. Redes Nativas (VPC / VNet): Perímetros Porosos

La red cloud es efímera y difícil de visualizar. El riesgo principal es la **exposición involuntaria** y el movimiento lateral.
*   **Vulnerabilidades Críticas:**
    *   **Puertos de Gestión Abiertos (0.0.0.0/0):** Mantener SSH (22) o RDP (3389) accesibles desde cualquier IP de Internet.
        
    *   **Exfiltración vía Red Pública:** Instancias en subredes privadas que acceden al almacenamiento a través del Internet Gateway en lugar de usar **VPC Endpoints**.
        
    *   **Shadow Peering:** Conexiones entre redes (Peering) que no están debidamente inspeccionadas por un Firewall central, permitiendo que el tráfico de una red de "Desarrollo" llegue a una de "Producción".
        
*   **Análisis de Experto:** Implementar **VPC Endpoint Policies**. Esto garantiza que tus servidores solo puedan hablar con _tus_ buckets de almacenamiento, bloqueando intentos de subir datos robados a cuentas personales del atacante.
    

* * *

### 🚀 La Tríada del Riesgo Cloud (Visión de Analista)

Para realizar un análisis de vulnerabilidades de alto nivel, no busques fallos aislados; busca la **combinación de factores**:
1.  **Exposición (Red):** Una instancia con un puerto expuesto accidentalmente.
    
2.  **Identidad (IAM):** Esa instancia posee un rol con permisos de lectura excesivos.
    
3.  **Dato (Almacenamiento):** Un bucket que contiene datos sensibles sin cifrado de cliente.
    
**Resultado:** Esta combinación es la que permite el éxito de un ataque. Tu labor es romper esta cadena en cualquiera de sus tres eslabones.

* * *

### 📝 Checklist de Auditoría Técnica

| **Componente** | **Qué buscar** | **Control Recomendado** |
| --- | --- | --- |
| **IAM** | Permisos `iam:PassRole` sin restricciones | Service Control Policies (SCP) |
| **Storage** | Buckets sin "Block Public Access" activo | KMS con Customer Managed Keys (CMK) |
| **Network** | Acceso a S3/SQL vía Internet pública | VPC Endpoints + Private Link |
| **Resiliencia** | Backups sin protección de borrado | Object Lock (Modo Compliance) |

### 💡 Pro-Tip del Experto: "El Principio de la Doble Llave"

En la nube, nunca confíes en un solo control. El error más común de los analistas junior es pensar: _"El bucket es seguro porque no tiene IP pública"_.
Un **Analista Senior** aplica la **Doble Llave**:
1.  **Llave de Identidad (IAM):** Configura una _Bucket Policy_ que solo permita el acceso a una identidad específica.
    
2.  **Llave de Red (VPC):** Añade una condición (`Condition`) en la política que solo permita el acceso si la petición proviene de un **VPC Endpoint** específico.
    
**¿Por qué?** Porque si las credenciales de la identidad son robadas, el atacante no podrá usarlas desde su propia computadora (fuera de tu red) porque no tiene la "llave de red". Esta técnica anula el 90% de los ataques por robo de credenciales.

### 📝 Ejercicio de Análisis: El Robo de Credenciales

**Caso de Estudio:** Un atacante logra robar las claves de acceso de un administrador de sistemas. Intenta entrar al almacenamiento de datos confidenciales desde su propia casa. Sin embargo, el analista de seguridad configuró una **VPC Endpoint Policy (Red)** que solo permite el acceso si la petición viene desde dentro de la red de la oficina.

**Pregunta:** Aunque el atacante tiene las claves correctas (identidad), ¿qué servicio nativo de red está bloqueando su acceso y qué técnica de "doble llave" se está aplicando para proteger el dato?



