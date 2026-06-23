
<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
 [[_TOC_]]
</details>


Capítulo 4: Mejora y Evolución (De Legacy a Cloud)
--------------------------------------------------

La migración a la nube es el momento de mayor riesgo para una organización, pero también es la mejor oportunidad para corregir años de "deuda técnica" en seguridad. Como analista, tu misión es definir un plan de acción que eleve la postura de seguridad durante el proceso.

* * *

### 🚀 1. Estrategias de Migración (Los 3 Caminos)

No todos los sistemas se mueven igual. Cada estrategia tiene un nivel de riesgo y una oportunidad de mejora distinta:
1.  **Rehosting (Lift & Shift):** Mover el servidor tal cual está.
    *   _Riesgo:_ Te llevas los virus y parches sin instalar a la nube.
        
    *   _Mejora:_ Es la más rápida, pero requiere aplicar firewalls perimetrales (WAF) inmediatamente para proteger el sistema viejo.
        
2.  **Replatforming:** Mover la aplicación pero cambiar la base de datos a un **Servicio Gestionado** (ej. de SQL Server en un PC a Azure SQL o AWS RDS).
    *   _Mejora:_ El proveedor de nube se encarga de los parches del sistema operativo y la base de datos. Tú te centras solo en los datos.
        
3.  **Refactoring (Modernización):** Rediseñar la aplicación para usar **Serverless** o Contenedores.
    *   _Mejora:_ Es la más segura. Eliminas servidores que mantener y reduces drásticamente la superficie de ataque.
        

* * *

### 🛡️ 2. El Plan de Acción: De lo "Inseguro" a lo "Resiliente"

Para que la evolución sea exitosa, el analista debe seguir estas fases:
*   **Fase 1: Higiene Pre-Migración:** Nunca muevas un servidor comprometido. Realiza un escaneo de vulnerabilidades y limpieza de identidades en el entorno local (On-prem) antes de conectar el túnel a la nube.
    
*   **Fase 2: Establecimiento del Puente Seguro:** Antes de enviar el primer bit, configura una **Landing Zone** con políticas de seguridad y una conexión privada (VPN o Direct Connect) que evite que los datos viajen por el internet público.
    
*   **Fase 3: Modernización de Secretos:** Sustituye las contraseñas escritas en archivos de configuración por servicios de **Bóveda de Secretos** (Secrets Manager) con rotación automática.
    

* * *

### 📈 3. Evolución Continua (Drift Detection)

En el mundo legacy, los cambios eran lentos. En la nube, todo cambia en segundos. La "Mejora" significa pasar de una revisión anual a un **monitoreo en tiempo real**.
*   **Infraestructura como Código (IaC):** La infraestructura debe definirse en archivos (Terraform/CloudFormation).
    
*   **Detección de Desviaciones (Drift):** Si un administrador cambia una regla de firewall manualmente ("clic ops"), el sistema debe alertar al analista de que la arquitectura real ya no coincide con la arquitectura segura aprobada.
    

* * *

### 💡 Pro-Tip del Experto: "La Regla de la Desconexión"

Durante una migración, el mayor peligro es la **conectividad total**. El error típico es conectar la oficina a la nube sin filtros, permitiendo que un ransomware en la oficina salte a la nube. **El Pro-Tip:** Implementa un "Kill Switch" o botón de pánico. Diseña la red de forma que puedas aislar el entorno Legacy del entorno Cloud en segundos si detectas una anomalía, sin interrumpir los servicios nativos de la nube.

* * *

### 📝 Ejercicio de Análisis: El Servidor de Nóminas

**Caso de Estudio:** Una empresa mueve su servidor de nóminas (Windows antiguo) a la nube mediante **Lift & Shift**. El desarrollador quiere abrir un puerto para administrarlo desde su casa para ahorrar tiempo. Sin embargo, el analista de seguridad propone usar un servicio de **Acceso Gestionado (como Azure Bastion o AWS SSM)** que no requiere abrir puertos públicos.

**Pregunta:** ¿Cómo ayuda esta "Mejora y Evolución" a reducir el riesgo de que un atacante encuentre el servidor mediante un escaneo de puertos en Internet?

