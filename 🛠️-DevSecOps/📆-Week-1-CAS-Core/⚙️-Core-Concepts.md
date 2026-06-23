<div style="text-align: justify;">

<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Table of Contents
    </summary>
  
  [[_TOC_]]
</details>

## 📝 Changelog

| Author | Date | Changes |
|--------|------|---------|
| Antonio                                 | 12/01/2026 | First version created |
| Saalamero                               | 12/2/2026 | Correción y revisión |
| @<C73C5218-17C3-6B53-B15D-E321D12689EB> | 18/2/2026 | Reescritura completa |

<br>

---

<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
<b><span style="color:#7C3AED; font-size: 17px;">💡 ¡¡EMPIEZA POR AQUÍ!!</span></b>
    <br><br>
    El Training Path no es algo de <b>leer y seguir </b>, es el <b>punto de partida</b>. Se espera que <b>investigues más allá de lo que se proponga en estos documentos </b>y profundices en los conceptos.
    <br><br>
    Recuerda que los recursos facilitados son una guía pero no el único material que existe.
    <br><br>
    <span style="color:#7C3AED;"><b>La ciberseguridad se basa en la capacidad de resolver los problemas que se plantean</b></span>. Si algo no tiene sentido, <b>investiga</b> . Si parece demasiado sencillo, posiblemente te hayas perdido algo.
<br><br>
O si te quieres poner filosófico con ello, Einstein dijo: "No tengo ningún talento especial. Solo soy muy curioso."
</div>

Antes de hablar de seguridad, necesitas entender **cómo se construyen las aplicaciones hoy en día**. No puedes proteger algo que no entiendes, y no puedes evaluar riesgos si no sabes qué componentes tiene un sistema ni dónde se ejecuta.

Esta sección cubre tres conceptos fundamentales que vas a encontrar **constantemente** en tu día a día:

- **Frontend vs Backend**: las dos caras de cualquier aplicación.
- **Monolitos vs Microservicios**: cómo se estructura el código y por qué importa.
- **IaaS, PaaS y SaaS**: los modelos de servicio en la nube y quién se encarga de qué.

No son conceptos de seguridad en sí mismos, pero **si no los pillas, la seguridad no va a tener sentido**. Es como intentar ser mecánico sin saber qué es un motor.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>✍️ Toma notas.</b> No te dediques solo a leer. <b>Escribe cosas con tus propias palabras.</b> Te ayudará a recordar mejor los conceptos. Y si no sabes explicar algo con tus propias palabras, probablemente no lo has entendido del todo.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🌐 Frontend vs Backend

Toda aplicación web tiene dos partes: lo que **el usuario ve** y lo que **el usuario no ve**. Así de simple.

### Frontend

El **frontend** es todo lo que el usuario toca, ve y con lo que interactúa en su navegador. Los botones, los formularios, los menús, las animaciones chulas que a alguien le parecieron buena idea... todo eso es frontend.

Se construye con:

- **HTML**: la estructura (el esqueleto)
- **CSS**: el estilo (la ropa)
- **JavaScript**: el comportamiento (el cerebro)

Frameworks típicos: **React**, **Angular**, **Vue.js**, **Next.js**.

Un **framework** es una colección de herramientas, librerías y convenciones que te ayudan a construir aplicaciones más rápido. En lugar de escribir todo desde cero, **usas las piezas del framework** para montar tu aplicación.

El código del frontend **se ejecuta en el navegador del usuario**. Esto es importante: significa que el usuario puede verlo, inspeccionarlo e incluso modificarlo. Abre las DevTools de tu navegador (F12) y verás exactamente de qué hablo.

### Backend

El **backend** es todo lo que ocurre en el **servidor**. Cuando el usuario le da a "Iniciar sesión", el frontend envía esa petición al backend, que comprueba las credenciales, consulta la base de datos y devuelve una respuesta.

Se construye con lenguajes como **Python**, **Java**, **Node.js**, **Go**, **C#**, etc.

El backend se encarga de:

- **Lógica de negocio**: las reglas de cómo funciona la aplicación.
- **Acceso a datos**: leer y escribir en bases de datos.
- **Autenticación y autorización**: comprobar quién eres y qué puedes hacer.
- **Integraciones**: hablar con APIs externas, servicios de terceros, etc.

### ¿Cómo se comunican?

Frontend y backend se comunican a través de **APIs** (normalmente **REST** o **GraphQL**). El frontend hace peticiones HTTP (GET, POST, PUT, DELETE...) y el backend responde con datos, generalmente en formato **JSON**.

```text
[Usuario] → [Frontend (navegador)] → [API Request] → [Backend (servidor)] → [Base de datos]
                                   ← [API Response] ←
```

### ¿Y esto qué tiene que ver con la seguridad?

**Todo**. Porque los ataques son diferentes según dónde apunten:

- **Frontend**: Un atacante inyecta JavaScript malicioso que roba cookies de sesión. Ejemplos: XSS, CSRF, Clickjacking, Open Redirects
- **Backend**: Un atacante manipula una petición para acceder a datos de otro usuario. Ejemplos: SQL Injection, Broken Auth, SSRF, IDOR

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ Regla de oro</span></b>
    <br><br>
    <b>Nunca confíes en el frontend.</b> Todo lo que viene del navegador del usuario puede estar manipulado. La validación en el frontend es para la <b>experiencia de usuario</b>; la validación en el backend es para la <b>seguridad</b>.
    <br><br>
    Si tu backend acepta lo que le mandan sin comprobar nada porque "ya se valida en el frontend"... enhorabuena, acabas de hacer la vida muy fácil a cualquier atacante con un proxy como Burp Suite.
</div>

Un buen equipo de seguridad necesita entender **ambos lados**. Si solo miras el frontend, te pierdes las inyecciones SQL. Si solo miras el backend, no detectarás un XSS almacenado.

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🛠 Monolitos vs Microservicios

Cuando construyes una aplicación, tienes que decidir **cómo organizas el código**. Y básicamente hay dos enfoques: meterlo todo junto en un bloque, o dividirlo en piezas pequeñas.

### 🧱 Arquitectura monolítica

Un **monolito** es una aplicación donde **todo el código está en un único proyecto y se despliega como una sola unidad**. El frontend, el backend, la lógica de negocio, el acceso a datos... todo convive en el mismo bloque.

Piensa en ello como una casa unifamiliar: todo está bajo el mismo techo. Si quieres reformar la cocina, puede que tengas que tocar la fontanería del baño.

**Ventajas:**

- **Simplicidad**: un solo proyecto, un solo despliegue, fácil de entender al principio.
- **Desarrollo rápido** para equipos pequeños o proyectos que están empezando.
- **Debugging directo**: todo está en el mismo sitio, puedes hacer trazas de punta a punta sin saltar entre servicios.
- **Sin latencia de red interna**: los componentes se llaman directamente en memoria, no a través de la red.

**Desventajas:**

- **Escala fatal**: si una parte necesita más recursos, tienes que escalar **todo** el bloque.
- **Despliegues de alto riesgo**: cualquier cambio, por pequeño que sea, requiere redesplegar **toda** la aplicación.
- **Acoplamiento**: con el tiempo, los componentes se van enredando y tocar una cosa rompe tres.
- **Un fallo puede tumbarlo todo**: si se cae un módulo, se cae la aplicación entera.

### 🧩 Arquitectura de microservicios

Los **microservicios** son lo contrario: divides la aplicación en **múltiples servicios pequeños e independientes**, cada uno responsable de una funcionalidad concreta. Cada servicio tiene su propia base de datos (idealmente), se despliega por separado y se comunica con los demás a través de APIs o colas de mensajes.

Piensa en ello como un bloque de pisos: cada piso es independiente. Si se inunda un piso, los demás siguen funcionando (más o menos).

**Ventajas:**

- **Escalado independiente**: puedes escalar solo el servicio que lo necesite, no todo.
- **Despliegues independientes**: puedes actualizar un servicio sin tocar los demás.
- **Libertad tecnológica**: cada servicio puede usar el lenguaje o framework que mejor le vaya.
- **Resiliencia**: si un servicio falla, los demás pueden seguir funcionando.
- **Equipos autónomos**: cada equipo se encarga de su servicio de punta a punta.

**Desventajas:**

- **Complejidad operativa**: más servicios = más cosas que monitorizar, desplegar y mantener.
- **Latencia de red**: los servicios se comunican por red, que es más lenta que una llamada en memoria.
- **Debugging distribuido**: rastrear un bug que cruza cinco servicios es un infierno si no tienes buen observability.
- **Consistencia de datos**: mantener datos coherentes entre servicios es complicado (hola, transacciones distribuidas).

### Comparativa rápida

| | **Monolito** | **Microservicios** |
| --- | --- | --- |
| **Estructura** | Un solo bloque de código | Múltiples servicios independientes |
| **Despliegue** | Todo junto, de golpe | Cada servicio por separado |
| **Escalado** | Todo o nada | Servicio por servicio |
| **Complejidad inicial** | Baja | Alta |
| **Complejidad a largo plazo** | Alta (se convierte en un monstruo) | Moderada (si se gestiona bien) |
| **Ideal para** | Proyectos pequeños, MVPs, equipos reducidos | Aplicaciones grandes, equipos múltiples, alta escala |

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Consejo.</b> No todo tiene que ser microservicios. Muchas startups fracasan por intentar hacer microservicios desde el día uno con un equipo de tres personas. La arquitectura debe adaptarse al <b>contexto</b>, no a las modas. Un monolito bien hecho <b>puede ser perfectamente válido</b>.
</div>

### ¿Y la seguridad?

Aquí es donde la cosa se pone interesante. Cada arquitectura tiene sus propios dolores de cabeza en seguridad:

**En un monolito:**

- La superficie de ataque está **más concentrada**: menos puntos de entrada, más fácil de proteger.
- Pero una vulnerabilidad puede comprometer **toda** la aplicación de golpe.
- La autenticación es más sencilla: un único punto de control.

**En microservicios:**

- La superficie de ataque **se multiplica**: cada servicio es un punto de entrada potencial.
- La comunicación entre servicios debe ser **segura** (mTLS, tokens, etc.), porque la red interna ya no es de fiar.
- Cada servicio necesita su propia **autenticación y autorización**. Si un servicio confía ciegamente en otro, un atacante que comprometa uno tiene acceso a todo.
- La gestión de **secretos** (API keys, credenciales de BBDD) se complica: hay más servicios que necesitan más secretos.
- **Observability** es crítico: si no puedes ver qué pasa entre servicios, no vas a detectar un ataque.

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ Cuidado con esto</span></b>
    <br><br>
    Muchos equipos asumen que la <b>red interna es segura</b> y no cifran ni autentican la comunicación entre microservicios. Error. Si un atacante consigue acceso a la red interna (y lo hará), se puede mover lateralmente entre servicios sin que nadie se entere. <b>Zero Trust aplica también dentro de tu propia infraestructura.</b>
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## ☁️ IaaS, PaaS y SaaS

Si trabajas en seguridad hoy en día, vas a trabajar con la nube. Y para entender la seguridad en la nube, necesitas tener claro **qué te da el proveedor y qué te toca a ti**. Porque ese reparto de responsabilidades cambia completamente según el modelo de servicio.

Los tres modelos principales son:

### 🏗️ IaaS – Infrastructure as a Service

El proveedor te da la **infraestructura básica**: máquinas virtuales, red, almacenamiento, y poco más. El resto es cosa tuya.

Es como alquilar un local vacío: te dan las cuatro paredes y la luz, pero los muebles, la decoración y la limpieza corren de tu cuenta.

**Tú gestionas**: sistema operativo, parches, middleware, runtime, aplicación, datos y seguridad de todo lo anterior.
**El proveedor gestiona**: hardware físico, red física, virtualización.

**Ejemplos**: AWS EC2, Azure Virtual Machines, Google Compute Engine.

**Cuándo usarlo**: migraciones de sistemas legacy, cuando necesitas control total sobre el entorno, configuraciones muy específicas que PaaS no soporta.

### ⚙️ PaaS – Platform as a Service

El proveedor te da la **plataforma entera** para que solo te preocupes de tu código. Nada de configurar servidores, instalar runtimes ni gestionar parches del SO.

Es como un coworking: llegas con tu portátil y te pones a trabajar. El Wi-Fi, la limpieza, el café... todo eso ya está.

**Tú gestionas**: tu código, datos, configuración de la aplicación y accesos.
**El proveedor gestiona**: infraestructura, SO, runtime, middleware, parches, escalado.

**Ejemplos**: Azure App Service, AWS Elastic Beanstalk, Google App Engine, Heroku.

**Cuándo usarlo**: desarrollo rápido de aplicaciones modernas, cuando quieres centrarte en el producto y no en la infraestructura.

### 📦 SaaS – Software as a Service

El proveedor te da una **aplicación completa lista para usar**. Tú no tocas código, ni servidores, ni nada técnico. Solo la usas.

Es como ir a un restaurante: te sientas, pides y comes. No cocinas, no friegas y no compras los ingredientes.

**Tú gestionas**: usuarios, permisos, configuración funcional, y poco más.
**El proveedor gestiona**: absolutamente todo lo técnico.

**Ejemplos**: Microsoft 365, Salesforce, Slack, Google Workspace, ServiceNow.

**Cuándo usarlo**: soluciones estándar donde no necesitas personalización profunda. Correo, CRM, herramientas de colaboración, etc.

### Comparativa

| | **IaaS** | **PaaS** | **SaaS** |
| --- | --- | --- | --- |
| **Control** | Máximo | Medio | Mínimo |
| **Responsabilidad tuya** | Casi todo | Solo el código y los datos | Solo usuarios y config |
| **Complejidad operativa** | Alta | Media | Baja |
| **Flexibilidad** | Total | Limitada por la plataforma | Muy limitada |
| **Cuándo usarlo** | Control total, legacy, configs específicas | Apps modernas, desarrollo rápido | Soluciones estándar, cero mantenimiento |

### El modelo de responsabilidad compartida

Este es **el concepto más importante** de la seguridad en la nube. La idea es sencilla: el proveedor cloud se encarga de la seguridad **de** la nube (infraestructura física, hipervisores, red), y tú te encargas de la seguridad **en** la nube (tus datos, tus accesos, tu configuración).

El problema es que **dónde acaba la responsabilidad del proveedor y dónde empieza la tuya** cambia según el modelo:

<div style="text-align: center; width: 500px; margin: auto;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/iaas-vs-paas-vs-saas.png" style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;" alt="IaaS vs PaaS vs SaaS">
    <div style="color: gray; font-size: small; font-style: italic;"></div>
</div>

Recuerda que "estar en la nube" no es sinónimo de "estar seguro". La mayoría de las brechas en la nube no son culpa del proveedor, sino de una mala configuración por parte del cliente. Buckets S3 públicos, permisos IAM demasiado amplios, credenciales hardcodeadas, bases de datos expuestas a internet... el proveedor se encarga de que su infraestructura sea segura, pero de que tú la uses bien, te encargas tú.

### Seguridad según el modelo

- **IaaS**: tú parcheas, tú configuras el firewall, tú endureces el SO, tú gestionas los accesos. Tienes máximo control, pero también **máxima responsabilidad**. Si se te olvida un parche, es tu problema.

- **PaaS**: el proveedor se encarga de la infraestructura, pero tú sigues siendo responsable de **tu código, tus datos y tus accesos**. Una inyección SQL en tu aplicación sigue siendo tu culpa, aunque el servidor lo gestione Azure.

- **SaaS**: parece que no tienes nada que hacer, ¿verdad? Pues no. Eres responsable de **quién tiene acceso, con qué permisos, y cómo están configuradas las opciones de seguridad** de la herramienta. Un Slack con canales privados abiertos a todo el mundo o un Microsoft 365 sin MFA es un desastre esperando a ocurrir.

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📚 Lecturas recomendadas

¿Quieres profundizar más? Aquí tienes recursos para cada tema.

### 📖 Artículos

| 🔗 Título | 📜 Descripción | 🔍 Fuente |
| --- | --- | --- |
| [Frontend vs Backend](https://www.geeksforgeeks.org/frontend-vs-backend/) | Comparativa clara entre frontend y backend con ejemplos | GeeksForGeeks |
| [Microservices vs Monolith](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith) | Comparativa detallada de ambas arquitecturas con pros y contras | Atlassian |
| [IaaS vs PaaS vs SaaS](https://www.ibm.com/think/topics/iaas-paas-saas) | Explicación clara de los tres modelos de servicio cloud | IBM |
| [Shared Responsibility Model](https://learn.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility) | El modelo de responsabilidad compartida de Azure | Microsoft |

### 🎥 Vídeos

| 🎬 Título | ⏳ Duración | 🔍 Fuente |
| --- | --- | --- |
| [Frontend vs Backend Explained](https://www.youtube.com/watch?v=PRSyHTajxPk) | 12 min | Fireship |
| [Microservices Explained in 5 Minutes](https://www.youtube.com/watch?v=lL_j7ilk7rc) | 5 min | IBM Technology |
| [IaaS vs PaaS vs SaaS](https://www.youtube.com/watch?v=9CVBohl6w0Q) | 10 min | IBM Technology |
| [Cloud Shared Responsibility Model](https://www.youtube.com/watch?v=jI3ZfWUrBx8) | 5 min | IBM Technology |
