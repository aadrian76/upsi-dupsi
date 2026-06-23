
<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
 [[_TOC_]]
</details>

| Author | Modification Date | Changes |
| :--- | :--- | :--- |
| <Luiggi Rodríguez> | 20/02/2026 | First Version Created |


## Capítulo 1: Metodología de Modelado de Amenazas (Threat Modeling)

### ✅ Resumen y Propósito 

El objetivo final del **Threat Modeling (TM)** es reducir el riesgo mediante un proceso sistemático y repetible. A diferencia del Pentesting o el escaneo de vulnerabilidades (que son reactivos), el TM es **proactivo**: se anticipa a los problemas antes de que existan.

💡 *"Una onza de prevención vale más que una libra de cura"*. 
Detectar un fallo en la fase de diseño es significativamente más económico que corregirlo en producción.



### ✅ ¿Qué es el Threat Modeling?

El **Threat Modeling** es un proceso estructurado que se utiliza para identificar, comprender y mitigar posibles amenazas mediante la **descomposición del diseño de una aplicación**. En lugar de buscar errores (_bugs_) una vez que el código ya está escrito, buscamos **fallos arquitectónicos** antes de que se despliegue una sola línea de código.

Como _Junior Analyst_ en esta compañía, utilizarás el _Threat Modeling_ para responder a las cuatro preguntas principales del _Threat Modeling Manifesto_:

1. **¿En qué estamos trabajando?** (Alcance y Diagramas)
2. **¿Qué puede salir mal?** (Identificación de Amenazas)
3. **¿Qué vamos a hacer al respecto?** (Mitigación y Controles)
4. **¿Hemos hecho un buen trabajo?** (Validación y QA)



[OWASP: What is Threat Modeling](https://owasp.org/www-community/Threat_Modeling)

<br>

### ✅ ¿Cuándo realizar Threat Modeling?
En entornos **Agile**, el TM debe integrarse en cada sprint, idealmente al inicio de cada _user story_. El principio fundamental es: **cuanto antes, mejor**. El TM no solo genera una lista de amenazas, sino que produce **diagramas precisos** que sirven como la "fuente de verdad" arquitectónica para todo el equipo.

<br>
  
### ✅ Objetivos: De la Teoría a las Tareas del Analista

Aunque el objetivo general es "mejorar la seguridad", tus tareas diarias como analista se centrarán en:
* **Asset Discovery:** Identificar qué datos (PII, credenciales, datos financieros) estamos protegiendo realmente.
* **Attack Surface Reduction:** Minimizar las "puertas y ventanas" que un atacante puede utilizar.
* **Security Requirements Generation:** Proporcionar a los desarrolladores una lista clara de tareas (p. ej., "Implementar MFA", "Cifrar datos en reposo").
* **Risk Acceptance:** Ayudar a los _stakeholders_ a decidir qué riesgos vale la pena asumir y cuáles deben corregirse de inmediato.

<br>

### ✅ Los "Componentes": Vulnerability, Weakness, y Threat

Para comunicarte eficazmente con arquitectos senior, debes utilizar la terminología correcta:

| **Término** | **Definición** | **Ejemplo en el mundo real** |
| :--- | :--- | :--- |
| **Weakness (CWE)** | Un fallo en el diseño o código que _podría_ dar lugar a una vulnerabilidad. | Uso de un algoritmo de hashing débil (MD5). |
| **Vulnerability (CVE)** | Un agujero específico y explotable en un sistema. | Una instancia de Log4j sin parchear en un servidor de producción. |
| **Threat** | El actor o evento que explota una vulnerabilidad. | Un grupo de _ransomware_ intentando robar datos. |
| **Attack Pattern (CAPEC)** | El "método" o "receta" que utiliza la amenaza. | **SQL Injection (CAPEC-66):** Manipular una consulta para saltarse el login. |   

💡 **Pro-Tip:** Utilizamos **CAPEC** (_Common Attack Pattern Enumeration and Classification_) para "pensar como un atacante". Nos proporciona la lógica paso a paso que utiliza un adversario para convertir una debilidad en una brecha exitosa.

<br>

### ✅ Metodologías y Frameworks

Aunque existen diversas metodologías, tu trabajo se centrará principalmente en dos enfoques:

1. **STRIDE (El "Cómo"):** Excelente para analistas técnicos para encontrar amenazas a nivel de componente.
    * **S**poofing, **T**ampering, **R**epudiation, **I**nformation Disclosure, **D**enial of Service, **E**levation of Privilege.
    * [Guía sobre STRIDE](https://learn.microsoft.com/en-us/previous-versions/commerce-server/ee823878(v=cs.20)?redirectedfrom=MSDN)
    
2. **PASTA (Enfoque centrado en el riesgo):** Se utiliza a menudo para la alineación con el negocio. Significa _Process for Attack Simulation and Threat Analysis_. [Metodología PASTA](https://www.threatmodelingmanifesto.org/)

<br>
    
### ✅ Threat Modeling con IriusRisk

En Accenture, no hacemos _Threat Modeling_ en una pizarra; utilizamos **IriusRisk** para automatizar y escalar el proceso.

**¿Por qué IriusRisk?**
* **Automated Threat Generation:** Al dibujar un diagrama, IriusRisk sugiere automáticamente amenazas basadas en una biblioteca masiva de reglas.
* **Regulatory Alignment:** Mapea las amenazas directamente con estándares como **ISO27001, NIST o GDPR**.
* **Bi-directional Sync:** Puede enviar tareas de seguridad directamente a los desarrolladores en **Jira** o **Azure DevOps**.

<br>

### 🏆 Ruta de Ceritifaciones IriusRisk

Para asegurar que estás listo para proyectos con clientes, tu _onboarding_ incluye estas certificaciones de IriusRisk. **Objetivo: Completar los Niveles 1 y 2 al finalizar la Semana 4.**

1. **[IriusRisk - Threat Modeling Foundations (TM-F)](https://iriusrisk.academy/course/iriusrisk-threat-modeling-foundations):** Presenta los fundamentos del modelado de amenazas.
2. **[IriusRisk - Threat Modeling Champion (IR-TMC)](https://iriusrisk.academy/course/iriusrisk-threat-modeling-champion):** Creación de un modelo de amenazas completo en la herramienta IriusRisk.
3. **[IriusRisk - Associate (IR-Assoc.)](https://iriusrisk.academy/course/iriusrisk-associate):** Formación avanzada en Seguridad por Diseño.
4. **[IriusRisk - Threat Modeling AI/ML Systems Essentials (IR-TMAIS)](https://iriusrisk.academy/course/iriusrisk-threat-modeling-aiml-systems-essentials):** Guía optimizada sobre el modelado de amenazas en entornos de IA/ML.

<br>

📝 Ejercicio de Análisis y Reflexión: "La Mentalidad del Analista"
------------------------------------------------------------------

Este ejercicio no requiere el uso de herramientas, sino tu capacidad de observación y análisis crítico.

### ✅ Escenario: El Quiosco de Autoservicio

Imagina que un cliente te pide realizar un _Threat Model_ de un **Quiosco Digital** situado en un centro comercial. Los usuarios lo utilizan para comprar tarjetas de regalo. El quiosco tiene:
1.  Una pantalla táctil.
    
2.  Un lector de tarjetas de crédito físico.
    
3.  Una conexión Wi-Fi a los servidores centrales.
    

### ✅ Parte 1: Aplicando las 4 Preguntas

Responde brevemente a lo siguiente basándote en el escenario:
1.  **¿En qué estamos trabajando?** Define el alcance. ¿Debemos preocuparnos solo por el software del quiosco o también por el hardware físico?
    
2.  **¿Qué puede salir mal?** Enumera tres eventos catastróficos para el negocio (ej. robo de datos de tarjetas).
    
3.  **¿Qué vamos a hacer al respecto?** Piensa en una medida defensiva para uno de esos eventos.
    
4.  **¿Hemos hecho un buen trabajo?** ¿Cómo verificarías que la medida defensiva realmente funciona?
    

* * *

### ✅ Parte 2: El Desafío STRIDE

Para cada categoría de **STRIDE**, identifica una amenaza potencial específica para este quiosco:
*   **S (Spoofing):** ¿Alguien podría fingir ser el servidor central para engañar al quiosco?
    
*   **T (Tampering):** ¿Qué pasaría si alguien manipula físicamente el lector de tarjetas?
    
*   **R (Repudiation):** Un usuario compra una tarjeta y luego dice: _"Yo no fui, el sistema falló"_. ¿Qué registros (_logs_) necesitamos para probar que miente?
    
*   **I (Information Disclosure):** ¿Se queda algún dato del usuario visible en la pantalla tras finalizar la sesión?
    
*   **D (Denial of Service):** ¿Cómo podría un atacante bloquear el quiosco para que nadie más lo use?
    
*   **E (Elevation of Privilege):** ¿Existe alguna forma de salir de la aplicación de ventas y acceder al sistema operativo del quiosco (ej. Windows/Linux)?
    

* * *

### 💡 Reflexión Final para el Onboarding

Tras completar el análisis, reflexiona sobre lo siguiente:

> _"Como analista, si tuvieras que explicarle al cliente por qué el Threat Modeling es mejor que simplemente hacer un Pentest una vez que el quiosco esté instalado, ¿qué tres argumentos usarías basándote en lo aprendido?"_
 