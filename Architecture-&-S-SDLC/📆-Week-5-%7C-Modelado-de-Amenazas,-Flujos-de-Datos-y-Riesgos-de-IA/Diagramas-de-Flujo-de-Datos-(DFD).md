
<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
 [[_TOC_]]
</details>

<br>


## Capítulo 2: Diagramas de Flujo de Datos (DFD)

### ✅ El Mapa de la Seguridad: Mapeo del Movimiento de Datos
El **DFD** es la herramienta principal del analista para entender la superficie de ataque. A diferencia de un diagrama de red (que muestra hardware y conectividad), el DFD se centra en **cómo viaja la información** a través de los componentes de la aplicación.



### ✅ Los 4 Elementos Fundamentales en IriusRisk
Para construir un modelo efectivo que IriusRisk pueda analizar, utilizamos estos cuatro bloques básicos:

1.  **Entidades Externas (External Entities):** Actores fuera de nuestro control directo (Usuarios, APIs de terceros como Stripe o proveedores de identidad como Azure AD).
2.  **Procesos (Processes):** Cualquier componente que manipule o transforme datos (Microservicios, funciones Serverless, Backends).
3.  **Almacenes de Datos (Data Stores):** Donde los datos residen de forma persistente o temporal (Bases de datos SQL/NoSQL, Buckets S3, Logs, Caché).
4.  **Flujos de Datos (Data Flows):** Las flechas que indican la dirección del dato y el protocolo utilizado (HTTPS, TLS 1.3, SSH, JDBC).

---

### ✅ Conceptos Clave: Trust Zones y Trust Boundaries

Como Analyst, tu capacidad para identificar estos límites es lo que diferencia un diagrama simple de un **Modelo de Amenazas profesional**:

* **Trust Zones (Zonas de Confianza):** Son perímetros que agrupan componentes con un nivel de confianza similar. Por ejemplo: *"Internet Pública"*, *"Red Interna"* o *"Enclave de Datos de Pago"*.
* **Trust Boundaries (Límites de Confianza):** Es el punto crítico donde un dato cruza de una zona de menor confianza a una de mayor confianza (o viceversa). 

> 💡 **La Regla del Analista:** La gran mayoría de las amenazas (Spoofing, Tampering, Information Disclosure) se generan automáticamente en IriusRisk cuando un flujo de datos atraviesa un **Trust Boundary**.



---

### ✅ Niveles de Abstracción: ¿Cuánto detalle necesitamos?

Para que un modelo sea útil para los desarrolladores, debemos elegir el nivel de detalle adecuado:

* **Nivel 0 (Diagrama de Contexto):** Representa todo el sistema como un único proceso. Ideal para entender las interacciones externas de alto nivel.
* **Nivel 1 (Diagrama de Detalle):** Desglosa el sistema en sus servicios principales (Web Server, API, DB). **Este es el estándar que utilizaremos en nuestros proyectos de IriusRisk.**

---

### ✅ Traducción de DFD a Riesgos en IriusRisk

En nuestra metodología, el DFD es el "motor" que alimenta el análisis:
* **Assets (Activos):** Al asignar un activo (ej. *Contraseñas*) a un flujo, IriusRisk identifica que ese flujo es un objetivo de alto valor.
* **Tags de Seguridad:** Si marcas un componente como *"Public Facing"*, el sistema priorizará amenazas de **Denegación de Servicio (DoS)**.
* **Protocolos:** Si el flujo entre un proceso y una base de datos no tiene definido un protocolo seguro, IriusRisk generará automáticamente el requisito de **"Implementar Cifrado en Tránsito"**.

---

### 📝 Ejercicio de Reflexión: "Follow the Data"

Imagina que un usuario realiza una compra. El dato del número de tarjeta de crédito viaja desde su navegador hasta la base de datos de pagos:
1.  ¿Cuántas **Trust Zones** atraviesa ese dato?
2.  ¿En qué punto el flujo de datos sale de nuestro control (Entidad externa)?
3.  ¿Qué pasaría si el **Data Store** no tuviera un límite de confianza que lo aislara del servidor web?

---