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
| Saalamero                               | 13/02/2026 | Revisión final |
| @<C73C5218-17C3-6B53-B15D-E321D12689EB> | 18/2/2026  | Reescritura completa |

<br>

---

<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
<b><span style="color:#7C3AED; font-size: 17px;">💡 ¡¡EMPIEZA POR AQUÍ!!</span></b>
    <br><br>
    El Training Path no es algo de <b>leer y seguir </b>, es el <b>punto de partida</b>. Se espera que <b>investigues más allá de lo que se proponga en estos documentos </b>y profundices en los conceptos.
    <br><br>
    Recuerda que los recursos facilitados son una guía pero no el único material que existe.
    <br><br>
    <span style="color:#7C3AED;"><b>La ciberseguridad se basa en la capacidad de resolver los problemas que se plantean</b></span>. Si algo no tiene sentido, <b>investiga</b>. Si parece demasiado sencillo, posiblemente te hayas perdido algo.
<br><br>
O si te quieres poner filosófico con ello, Einstein dijo: "No tengo ningún talento especial. Solo soy muy curioso."
</div>

La **seguridad no va de herramientas, checklists ni dashboards llamativos**: va de **principios**. Si no entiendes los conceptos fundamentales, ni las mejores herramientas del mundo te van a salvar. Pero si los entiendes, puedes asegurar **cualquier cosa**: desde entornos cloud hasta esa lavadora LG medio chapucera que probablemente ya forme [parte de una botnet](https://www.tomshardware.com/networking/your-washing-machine-could-be-sending-37-gb-of-data-a-day).

Esta sección no trata de memorizar definiciones ni de repetir "**CIA Triad**" como si fuera un mantra. Trata de **entender por qué la seguridad importa**. Porque si no entiendes el _por qué_, jamás vas a acertar con el _cómo_.

Aquí cubriremos:

- **Modelos de seguridad**: los principios que hay detrás de cada decisión de seguridad (CIA Triad, Zero Trust, Defensa en Profundidad, Mínimo Privilegio, Security by Design).
- **IAM (Identity & Access Management)**: quién entra, qué puede hacer, y por qué _"dame admin y ya está"_ es siempre una idea terrible.
- **Defects**: la diferencia entre un bug, una debilidad y una vulnerabilidad (spoiler: no son lo mismo).

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/buddy-buzz-vulnerabilities-everywhere-meme-b7ef6e7b-59a7-49ae-9e6d-bac96dd3cf83.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main"
         style="border: 3px solid lightgray; width: 500px; padding: 1rem; height: auto;"
         alt="Buddy frightened by Buzz words">
    <div style="color: gray; font-size: small; font-style: italic;">Don't be buddy, don't be frightened, don't push vulnerabilities to prod</div>
</div>

La seguridad **no es una casilla que se marca al final**, como a muchos managers les encanta pensar. Si las vulnerabilidades llegan a producción, arreglarlas va a ser **mucho más caro, arriesgado y doloroso**. Tu trabajo es prevenir los problemas antes de que existan, no ir apagando fuegos.

Antes de nada, vamos a ver la diferencia entre tres palabrejas que mucha gente usa como sinónimos pero que no lo son.

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🐞 Defects

En seguridad mucha gente usa **"bug"**, **"debilidad"** y **"vulnerabilidad"** como si fueran lo mismo. No todos los errores son explotables, y no todas las malas prácticas son vulnerabilidades.

### 🚨 Vulnerability (Vulnerabilidad)

Una **vulnerabilidad** es un defecto o debilidad que **puede explotarse** (o ya ha sido explotado) para provocar un **impacto real**. Existe un **camino práctico** para que un atacante lo use a su favor, en un contexto concreto.

**Ejemplos:**

- **SQL Injection** en un endpoint expuesto
- **SSRF** con acceso a metadatos cloud
- **RCE** por deserialización insegura
- **Bucket público** con datos sensibles

### 🧩 Weakness (Debilidad)

Una **weakness** es una condición del sistema que lo hace **más propenso a sufrir ataques**. El sistema puede funcionar perfectamente, pero está construido de una forma que **facilita que algo malo ocurra**. Suele ser una **mala práctica** o un **patrón inseguro**. Muchas están catalogadas como **CWE (Common Weakness Enumeration)**.

**Ejemplos:**

- Contraseñas **débiles** permitidas
- Falta de **rate limiting** en login (puerta abierta a **fuerza bruta**)
- **Logs insuficientes** (si no registras nada, no detectas nada)
- Uso de **criptografía obsoleta**

### 🔧 Defect / Flaw (Defecto / fallo)

Un **error en el sistema**. Puede ser de **diseño**, de **implementación**, de **configuración** o de **proceso**. Son cosas **mal hechas o incompletas** que pueden afectar tanto a la funcionalidad como a la seguridad. **Pueden ser explotables o no**, pero deben corregirse para evitar problemas futuros.

**Ejemplos:**

- Lógica de autenticación **mal implementada**
- Control de errores que **revela información** interna
- Configuración **insegura por defecto**
- Falta de **validación de inputs** en un endpoint

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>☝️🤓 En resumen.</b> Un <b>defect</b> es algo mal hecho. Una <b>weakness</b> es un patrón inseguro que aumenta el riesgo. Una <b>vulnerability</b> es una weakness o defect que <b>un atacante puede explotar</b> con impacto real. Cuanto antes los detectes, menos te va a costar arreglarlos.
</div>

### 📚 Lecturas recomendadas

**📖 Artículos y documentación**

| Título | Descripción | Fuente |
|-------|-------------|--------|
| [OWASP – Vulnerabilities](https://owasp.org/www-community/vulnerabilities/) | Tipos de vulnerabilidades más comunes en aplicaciones, con explicaciones y ejemplos prácticos | OWASP |
| [OWASP – Business Logic Vulnerability](https://owasp.org/www-community/vulnerabilities/Business_logic_vulnerability) | Cómo los atacantes abusan de flujos válidos de la aplicación para causar impactos de seguridad | OWASP |
| [CWE - Common Weakness Enumeration](https://cwe.mitre.org/) | Catálogo oficial de debilidades de software. Si trabajas en AppSec, vas a vivir aquí | MITRE |

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🏛 Modelos de seguridad

La seguridad no consiste en **poner un firewall y darse por satisfecho**. Consiste en **entender los principios fundamentales** que guían cada decisión. A estos principios se les llama **modelos de seguridad**.

Si no los entiendes, estarás siguiendo reglas a ciegas sin saber por qué. Y eso es una receta estupenda para tomar **decisiones de seguridad horribles**. No son teoría abstracta: son la base de todo lo que harás en este campo.

A lo largo de esta sección verás:

- 🔺 **CIA Triad**: la regla de oro. **Confidencialidad, Integridad y Disponibilidad**.
- ⛔ **Zero Trust**: no asumas que nada es seguro. **Nunca**.
- 🧅 **Defensa en profundidad**: la seguridad no es una sola capa, es **toda una cebolla**.
- 🔑 **Least Privilege**: si no lo necesitas, **no lo tienes**.
- 🛠 **Security by Design**: la seguridad no es un añadido, es un **requisito desde el día uno**.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>☝️🤓 No memorices.</b> Si no puedes explicar con tus propias palabras por qué "Least Privilege" importa, no lo has entendido. Y si no lo has entendido, no lo vas a aplicar bien.
</div>

### 🔺 CIA Triad

Bienvenido al **modelo de seguridad por excelencia**. Si no lo conoces, no conoces la seguridad. Punto. Todo absolutamente todo lo que hacemos en este campo se alinea con al menos **uno de estos tres principios**:

- 🔐 **Confidentiality (Confidencialidad)**: si no deberías verlo, **no lo puedes ver**.
- ⚖️ **Integrity (Integridad)**: si los datos cambian, deberías **poder saberlo**.
- 🖥️ **Availability (Disponibilidad)**: si no puedes acceder a la información cuando la necesitas, **no sirve de nada**.

La **CIA Triad** se suele representar como un triángulo, con cada principio en un vértice, para mostrar que son **interdependientes**: si uno falla, los demás se resienten y **te acaban hackeando**. Así de simple.

Aquí hemos decidido usar **círculos** porque representan mejor la **conexión real** entre estos principios. Si uno se rompe, todo el sistema queda en riesgo. Y también porque, seamos sinceros, somos así de elegantes.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/cia-triad-7d322409-414b-43ad-9043-02fd0fad6f28.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main"
         style="border: 3px solid lightgray; width: 750px; padding: 1rem; height: auto;"
         alt="CIA Triad">
    <div style="color: gray; font-size: small; font-style: italic;">Sad faces = bad security, but the center happy face = good security</div>
</div>

¿Un sistema con gran **confidencialidad** pero sin **disponibilidad**? Inútil. ¿Uno que prioriza la **disponibilidad** pero ignora la **integridad**? Desastre asegurado. Estos tres principios deben equilibrarse en función del riesgo y de las necesidades del negocio. Cuando la seguridad falla, casi siempre es porque alguien ignoró uno (o más) de estos principios.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💭 Recuerda.</b> La seguridad no es bloquearlo todo. Se trata de encontrar un <b>equilibrio</b> entre confidencialidad, integridad y disponibilidad basado en <b>riesgo</b> y <b>necesidades de negocio</b>. Si lo bloqueas todo, nadie trabaja. Si no bloqueas nada, te hackean.
</div>

<center>

::: video
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/kPPFNrlN3zo"
    title="What is the CIA Triad" frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
</iframe>
:::

<br>
</center>

#### 🔐 Confidencialidad

Si no puedes mantener los datos en privado, **nada más importa**. La confidencialidad garantiza que la información sensible **solo sea accesible para quien debe verla**. Suena obvio, pero la cantidad de empresas que fallan en esto es para echarse a llorar.

**¿Por qué es importante?**

- **Brechas de datos** = desastre inmediato (contraseñas, datos personales, información financiera...).
- Evita el **espionaje industrial** — porque sí, hay gente que **intentará robar tus secretos**.
- Mantiene fuera a atacantes, empleados sin autorización y **curiosos imprudentes**.

**¿Cómo garantizarla?**

- **Cifra todo**. Datos en reposo y en tránsito, **siempre**. Si los roban cifrados, no sirven de nada.
- **Control de accesos**. Limita quién accede a qué: RBAC, MFA, acceso temporal. Cuantos menos ojos, mejor.
- **Monitoriza**. Registra quién accede, cuándo y desde dónde. Si alguien entra a datos sensibles a las **2 de la mañana desde un país que no debería**, más vale que te enteres.

**Fallos en el mundo real**

- **Equifax (2017)**. 148 millones de registros robados por no parchear una vulnerabilidad conocida. Así de simple.
- **Filtraciones de Snowden (2013)**. Un administrador con privilegios excesivos filtró secretos de la NSA a nivel mundial.

🔎 **Lección**: ¿ves el patrón? **Mal control de accesos = alguien se lleva tus datos.**

#### ⚖️ Integridad

Si los datos pueden modificarse sin que nadie se entere, **no puedes confiar en nada**. La integridad garantiza que la información sea **correcta, consistente y fiable**. Que lo que lees es lo que realmente se escribió.

**¿Por qué es importante?**

- **Logs manipulados** = ni siquiera sabrás que te han atacado.
- **Transacciones alteradas** = el dinero se esfuma.
- Previene **ataques a la cadena de suministro**, donde se mete malware en software legítimo (hola, **SolarWinds**).

**¿Cómo garantizarla?**

- **Hashing**. Verificar que los datos no han sido tocados. Si el hash no coincide, alguien ha metido mano.
- **Firmas digitales**. Demostrar que los datos vienen de quien dicen venir.
- **Control de cambios**. Si algo cambia, tienes que saber **quién**, **cuándo** y **por qué**.

**Fallos en el mundo real**

- **SolarWinds (2020)**. Malware introducido en una actualización legítima, comprometiendo a más de **18.000 empresas**. Nadie sospechó porque la actualización parecía auténtica.
- **Stuxnet (2010)**. Malware que alteró los datos del programa nuclear iraní, provocando la autodestrucción de centrifugadoras. Ciencia ficción hecha realidad.

🔎 **Lección**: sin integridad = **no hay confianza**. Y sin confianza, **estás perdido**.

#### 🖥️ Disponibilidad

Si tu sistema no está disponible cuando lo necesitas, **no sirve para nada**. La disponibilidad garantiza que **datos, aplicaciones y servicios** funcionen cuando se necesitan, **incluso bajo ataque**.

**¿Por qué es importante?**

- **Caídas del sistema** = pérdida de ingresos, acceso y confianza.
- **Sistemas críticos** (hospitales, banca, infraestructuras) **no se pueden permitir caer**.
- Los ataques de **ransomware y DDoS** apuntan directamente aquí porque es donde más duele al negocio.

**¿Cómo garantizarla?**

- **Redundancia**. Si un sistema falla, otro toma el relevo. Sin interrupciones.
- **Backups, backups y más backups**. Si el ransomware borra datos, los restauras y a otra cosa.
- **Balanceo de carga y failover**. Ningún sistema único debería poder tumbar todo el chiringuito.
- **Planes de respuesta a incidentes**. Porque no se trata de _si_ algo va a fallar, sino de _cuándo_.

**Fallos en el mundo real**

- **Colonial Pipeline (2021)**. Un ransomware paralizó el suministro de combustible en la costa este de EE. UU. durante días.
- **Caída de AWS (2021)**. Un fallo interno dejó fuera de servicio **Netflix, Disney+, Slack y más**. Me encantaría ver esa factura de AWS...

🔎 **Lección**: si un atacante controla tu disponibilidad, **controla tu negocio**.

#### 📚 Lecturas recomendadas

¿Quieres profundizar más? Estas son nuestras referencias principales para reforzar lo aprendido.

**📖 Artículos y documentación**

| 🔗 Título | 📜 Descripción | 🔍 Fuente |
| --- | --- | --- |
| [La tríada CIA: definición, componentes y ejemplos](https://www.csoonline.com/article/2127754/cia-triad-definition-components-and-examples.html)| Análisis detallado del modelo CIA con aplicaciones reales | CSO Online |
| [Que es la Tríada CIA?](https://www.coursera.org/articles/cia-triad) | Visión general completa de los principios CIA y su importancia | Coursera |
| [Tríada CIA: Confidencialidad, Integridad y disponibilidad](https://www.sailpoint.com/identity-library/cia-triad/) | Explicación profunda de cada pilar de la triada | SailPoint |

**🎥 Vídeos**

| 🎬 Título | ⏳ Duración | 🔍 Fuente |
| --- | --- | --- |
| [Que es la Tríada CIA](https://www.youtube.com/watch?v=kPPFNrlN3zo) | 4 min | IBM Technology |
| [Arquitectura de ciberseguridad](https://www.youtube.com/watch?v=EqNe55IzjAw)| 12 min | IBM Technology |

**🛠 Herramientas y laboratorios prácticos**

| 🛠 Herramienta / Lab | 🔍 Descripción | 🔗 Fuente |
| --- | --- | --- |
| [TryHackMe: Security Principles – Task 2](https://tryhackme.com/room/securityprinciples) | Reto interactivo para aplicar la CIA Triad | TryHackMe |

### ⛔ Zero Trust

_"Confiar pero verificar"_ está muerto. **No confíes en nada. Verifica todo.** Eso es **Zero Trust** en una frase.

No importa si estás dentro de la red corporativa, usando un portátil de la empresa o accediendo con tu propia cuenta. **Tienes que demostrar que eres quien dices ser**. Cada solicitud es una **amenaza potencial** hasta que se demuestre lo contrario. Si no estás verificado, **no entras**.

¿Cómo hemos llegado hasta aquí? Durante años, las empresas pensaron que estar dentro de la red corporativa significaba estar a salvo. Un foso digital y todos contentos. Esa ilusión se hizo añicos cuando **credenciales de VPN empezaron a venderse en la dark web** como churros. Los atacantes se dieron cuenta de que **no necesitaban atacar la red** si alguien les entregaba las llaves directamente. Y si la red **no tenía controles internos**, podían pasar de _"acabo de iniciar sesión"_ a _"soy admin del dominio"_ en cuestión de minutos.

El modelo de confianza tradicional tiene **tres problemas gordos**:

- **Las redes ya no son seguras por defecto**.
- **El movimiento lateral es real**: una vez dentro, los atacantes se mueven libremente.
- **Los usuarios son el eslabón más débil**: phishing, robo de credenciales e ingeniería social siguen siendo los vectores de ataque más comunes.

**Zero Trust no es paranoia**. Es **sentido común aplicado a la seguridad moderna**.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/Zero%20Trust%20meme%20-%20Batman%20slapping%20Robin-95635d57-fa69-4c56-84bb-faa1b965037c.jpeg&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main"
         style="border: 3px solid lightgray; width: 500px; padding: 1rem; height: auto;"
         alt="Zero Trust meme - Batman slapping Robin">
    <div style="color: gray; font-size: small; font-style: italic;">If you don't want to get slapped, you better apply this model...</div>
</div>

#### 🔍 Cómo funciona

**Zero Trust** significa **verificarlo todo**, sin importar de dónde venga. No es simplemente poner **MFA en la pantalla de login** y dar el trabajo por terminado. Implica:

- **Sin confianza implícita**. No obtienes acceso por estar dentro de la red. Cada solicitud se trata como **sospechosa** hasta que se demuestre lo contrario.
- **Least Privilege (mínimo privilegio)**. Solo accedes a lo que necesitas, **nada más** y **solo durante el tiempo necesario**.
- **Microsegmentación**. Dividir la red en **zonas muy pequeñas**. Nada de redes "planas" donde una sola brecha implica acceso total y movimiento lateral sin límites*.

El objetivo es **limitar el daño**. Si un atacante compromete un sistema, no puede moverse lateralmente. Si roba credenciales, no puede acceder a todo. Cuando algo falla (y fallará), **no es el fin del mundo**.

\* _¿Ves lo que he hecho ahí? Movimiento lateral... literalmente. Sí, lo sé, soy un genio._

#### 💀 ¿Qué ocurre cuando falla?

Cuando las empresas **no aplican Zero Trust**, los atacantes se mueven libremente una vez dentro. Estos son dos de los **peores casos reales**:

- **Capital One (2019)**. Un exingeniero de AWS encontró un **rol de IAM mal configurado** y se llevó más de **100 millones de registros de clientes**. Un solo permiso mal puesto.
- **Uber (2022)**. **MFA débil + ingeniería social** = control administrativo total sobre los sistemas internos. Duele solo de leerlo.

Zero Trust no evita los ataques. Los hace **caros, lentos y frustrantes**. Un dolor de cabeza para el atacante. Y a los atacantes no les gustan los objetivos difíciles. **Sé un objetivo difícil.**

#### 📚 Lecturas recomendadas

¿Quieres profundizar más? Estas son nuestras referencias principales para reforzar lo aprendido.

**📖 Artículos y documentación**

| 🔗 Título | 📜 Descripción | 🔍 Fuente |
|----------|---------------|----------|
| [Arquitectura Zero Trust](https://www.csoonline.com/article/2124679/what-is-zero-trust-a-model-for-more-effective-security.html) | Análisis en profundidad del modelo Zero Trust y su implementación | CSO Online |
| [Visión general de Zero Trust](https://www.microsoft.com/security/business/zero-trust) | Guía completa de Microsoft para entender y desplegar Zero Trust | Microsoft |
| [Guía de la NSA en Zero Trust](https://www.nsa.gov/Press-Room/News-Highlights/Article/Article/2470035/embracing-a-zero-trust-security-model/) | Enfoque de la NSA sobre el pilar de Visibilidad y Analítica de Zero Trust | NSA |
| [BeyondCorp de Google](https://cloud.google.com/beyondcorp) | Aproximación de Google a Zero Trust con BeyondCorp | Google Cloud |

**🎥 Vídeos**

| 🎬 Título | ⏳ Duración | 🔍 Fuente |
|----------|------------|----------|
| [Zero Trust explicado en 4 mins](https://www.youtube.com/watch?v=yn6CPQ9RioA) | 4 min | IBM Technology |
| [Cyberseguridad y Zero Trust](https://www.youtube.com/watch?v=FMMWSLIcaME) | 5 min | IBM Technology |

**🛠 Herramientas y laboratorios prácticos**

| 🛠 Herramienta / Lab | 🔍 Descripción | 🔗 Fuente |
| --- | --- | --- |
| [Zero Trust Lab Guide](https://microsoft.github.io/ztlabguide/) | Guía estructurada de Microsoft para construir un laboratorio Zero Trust | Microsoft |
| [Palo Alto Networks Zero Trust Lab](https://github.com/PaloAltoNetworks/lab-aws-zero-trust) | Scripts y labs prácticos para desplegar políticas Zero Trust en AWS | GitHub |
| [ATARC Zero Trust Lab](https://atarc.org/atarc-zero-trust-lab/) | Laboratorio con soluciones Zero Trust integradas de varios proveedores | ATARC |

### 🧅 Defensa en profundidad

La seguridad **no es una única capa**: es **toda una cebolla**. Si solo confías en un único mecanismo de defensa, **enhorabuena**, acabas de hacerle la vida muy fácil a un atacante.

La **defensa en profundidad (Defense in Depth, DiD)** consiste en tener **múltiples capas superpuestas**: si una falla, hay **otra detrás** para frenar el ataque. Cada capa **ralentiza al atacante**, aumenta las probabilidades de pillarlo y **le complica la existencia**.

La idea es simple: **más capas = más oportunidades de parar un ataque**.

Piensa en un **castillo medieval**. Si todo lo que tienes es una puerta principal, los atacantes la rodearán, cavarán un túnel o sobornarán al guardia. Por eso los castillos tenían:

- **Un foso** (_seguridad perimetral_): dificulta incluso acercarse.
- **La puerta principal** (_firewalls_): bloquea amenazas evidentes, pero no es impenetrable.
- **Guardias armados** (_autenticación_): comprueban quién puede entrar.
- **Puertas cerradas en el interior** (_least privilege_): aunque alguien se cuele, no puede ir a todas partes.
- **Torres de vigilancia** (_logging y monitorización_): detectan amenazas antes de que lleguen demasiado lejos.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/defense-in-depth-castle-631fcd3a-85f1-4239-939e-d2ae0b868b6a.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main"
         style="border: 3px solid lightgray; width: 750px; padding: 1rem; height: auto;"
         alt="Defense in Depth: A Medieval Castle Analogy">
    <div style="color: gray; font-size: small; font-style: italic;">**Capas sobre capas sobre capas.**  
Genial si eres un castillo, **no tanto si eres un atacante**.</div>
</div>

Si una capa falla, **las demás siguen en pie**. Ese es **todo el objetivo**.

Pero no existe un conjunto universal de capas que sirva para todo. Qué proteges y cómo lo despliegas determina qué defensas necesitas.

<center>

::: video
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/hQXvsfoEhfg"
    title="Cybersecurity Fundamentals - Defense in Depth" frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
</iframe>
:::

<br>
</center>

#### 🏰 Capas principales

Se aplican en **cualquier entorno**, ya sea un centro de datos, una app SaaS o incluso un router doméstico:

1. **Seguridad perimetral**. Primera línea de defensa: **mantener las amenazas fuera**. Firewalls, VPNs y WAFs.
2. **Seguridad de red**. Una vez que superan el perímetro, **impedir que se muevan libremente**. Segmentación, VLANs y NAC.
3. **Autenticación y control de acceso**. Quién puede entrar y **qué puede hacer dentro**. MFA, RBAC y ABAC.
4. **Seguridad de endpoints**. Protección de dispositivos: antivirus, EDR, hardening y parcheo.
5. **Logging y monitorización**. Detectar ataques **antes de que se propaguen**. SIEM, IDS/IPS y EDR.

Estas son las **capas base**. Dependiendo de **qué protejas**, puede que necesites más.

#### 🎭 Capas variables

La seguridad depende del **contexto**: las capas cambian según **qué protejas y cómo esté desplegado**:

- **Seguridad de los datos**. Cifrado en reposo y en tránsito, DLP y enmascarado de datos.
- **Seguridad de aplicaciones**. Desarrollo seguro, WAFs, SAST, DAST y SCA.
- **Seguridad en la nube**. IAM, configuraciones seguras, CSPM y CASB.
- **Seguridad física**. Cámaras, alarmas, vigilantes, tarjetas de acceso y biometría.

Por ejemplo, si proteges un **entorno cloud**, probablemente necesites:

- **IAM**. Controlar quién accede a qué, aplicar **mínimo privilegio** y forzar **MFA**.
- **Configuraciones seguras**. Evitar la clásica cagada: buckets S3 abiertos, permisos débiles, APIs expuestas.
- **Logging y monitorización**. Detectar amenazas **antes de que se conviertan en un desastre**.

Pero si proteges una **aplicación**, necesitas cosas distintas:

- **Desarrollo seguro**. Para no introducir vulnerabilidades desde el código.
- **WAFs**. Para bloquear ataques antes de que lleguen a la app.
- **SAST, DAST y SCA**. Para encontrar y corregir vulnerabilidades **antes de que las exploten**.

La clave: **entender qué proteges y cómo está expuesto**. Así se eligen **las capas correctas**.

#### 🛡️ Defensa en profundidad en acción

Imagina que un atacante intenta comprometer tu sistema:

- Roba una contraseña → **MFA lo bloquea**.
- Phishing a un empleado → **sin privilegios de admin**, no puede hacer gran cosa.
- Encuentra un servidor sin parches → **la segmentación de red** impide el movimiento lateral.
- Despliega ransomware → **las copias de seguridad** restauran todo, no se paga rescate.
- Intenta exfiltrar datos → **DLP (Data Loss Prevention)** lo detiene.

Cada capa lo **frena**, lo **retrasa** o **le complica la vida**. Ese es el poder de la defensa en profundidad. No necesitas que cada capa sea perfecta: necesitas que el atacante tenga que **superar todas**.

#### 📚 Lecturas recomendadas

¿Quieres profundizar más? Estas son nuestras referencias principales para reforzar lo aprendido.

**📖 Artículos y documentación**

| 🔗 Título | 📜 Descripción | 🔍 Fuente |
| --- | --- | --- |
| [Defensa en profundidad](https://www.csoonline.com/article/2120511/what-is-defense-in-depth.html) | Introducción a la defensa en profundidad, su importancia e implementación | CSO Online |
| [Fortificando Fronteras digitales](https://medium.com/@stevan.lake/fortifying-digital-frontiers-a-cyber-threat-intelligence-journey-71141824428d) | Visión profesional sobre el refuerzo de defensas | Medium |
| [Guía DiD de Microsoft](https://docs.microsoft.com/en-us/microsoft-365/security/defender/defense-in-depth?view=o365-worldwide) | Enfoque de Microsoft sobre DiD en entornos cloud | Microsoft |
| [Guía del NIST para defensa en profundidad](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-53r5.pdf) | Guía oficial del NIST sobre seguridad por capas | NIST |
| [Guía de SANS para defensa en profundidad](https://www.sans.org/blog/defense-in-depth-a-practical-strategy-for-achieving-information-assurance-in-todays-highly-networked-environments/) | Estrategias prácticas de seguridad por capas | SANS |

**🎥 Vídeos**

| 🎬 Título | ⏳ Duración | 🔍 Fuente |
| --- | --- | --- |
| [Concepto de defensa en profundidad](https://www.youtube.com/watch?v=CHKS2FcEMek) | 7 min | John Savill's Technical Training |
| [Defense in Depth Is Dead, Long Live Depth in Defense](https://www.youtube.com/watch?v=3Qv1ZJ3v7ZQ) | 14 min | RSA Conference |
|[¿Que es la defensa en profundidad?- Como implementar defensa en profundidad](https://www.youtube.com/watch?v=a3JR1i2HBoU)| 25 min | CyberPlatter |

### 🔑 Mínimo privilegio

El principio de **Least Privilege** consiste en dar a cada usuario **únicamente los permisos que necesita para hacer su trabajo**. Ni más, ni menos. Porque **cada permiso de más es un vector de ataque nuevo**.

"**Dame permisos de admin**" y "**solo por esta vez**" son las **dos frases más peligrosas** que vas a escuchar en este campo.

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/Items?path=/.attachments/least-privilege-elmo-meme-83ea0476-ee0b-4476-b06a-a66038bb1a3e.jpg&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=main"
         style="border: 3px solid lightgray; width: 450px; padding: 1rem; height: auto;"
         alt="Elmo bad, elmo dones't implement least privilege">
    <div style="color: gray; font-size: small; font-style: italic;">A los equipos de seguridad <b>les gusta</b> lo último de lo último</div>
</div>

#### Cómo implementarlo

- **RBAC (Role-Based Access Control)**. Asigna permisos **en función del rol**, no de la persona.
- **Revisiones periódicas**. Revoca los accesos que ya no sean necesarios. Lo que necesitabas hace seis meses puede que hoy sobre.
- **Privilegios temporales**. Para acciones de alto riesgo: acceso justo cuando lo necesitas, y se revoca automáticamente.

Imagina que eres desarrollador. No necesitas acceso a la **base de datos de producción**, ¿verdad? Pero si lo tienes, puedes causar mucho daño: borrar registros, robar datos o simplemente romper cosas sin querer.

Y no solo nos preocupamos por ti. ¿Qué pasa si **te roban las credenciales**? Si tienes permisos de admin, el atacante hará **todo lo que tú puedas hacer**. Si solo tienes acceso a lo justo, lo peor que puede pasar es... bueno, **no demasiado**.

Eso es el **poder del mínimo privilegio**.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>☝️🤓 Recuerda</b>. Cuando le das acceso a alguien, no solo confías en esa persona: <b>confías en todo el que interactúa con ella.</b>
</div>

#### 📚 Lecturas recomendadas

¿Quieres profundizar más? Estas son nuestras referencias principales para reforzar lo que acabas de aprender.

**📖 Artículos y documentación**

| 🔗 Título | 📜 Descripción | 🔍 Fuente |
| --- | --- | --- |
| [Principio de mínimo privilegio](https://en.wikipedia.org/wiki/Principle_of_least_privilege) | Explicación completa del principio de mínimo privilegio | Wikipedia |
| [Principio de mínimo privilegio:definición, Métodos y ejemplos](https://www.okta.com/identity-101/minimum-access-policy/) | Visión general de las políticas de mínimo privilegio y estrategias de implementación | Okta |
| [El principio de mínimo privilegio explicado (con buenas prácticas)](https://www.splunk.com/en_us/blog/learn/least-privilege-principle.html) | Análisis del principio y mejores prácticas para su aplicación | Splunk |
| [Implementando modelos administrativos de mínimo privilegio](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models)| Guía para aplicar el mínimo privilegio en contextos administrativos | Microsoft |
| [Mejores prácticas en IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) | Recomendaciones de IAM con énfasis en el mínimo privilegio | AWS |

**🎥 Vídeos**

| 🎬 Título | ⏳ Duración | 🔍 Fuente |
| --- | --- | --- |
| [¿Cual es el principio de privilegio mínimo?](https://www.youtube.com/watch?v=8GZ6516Kao4) | 7 min | Google Cloud Tech |

**🛠 Herramientas y laboratorios prácticos**

| 🛠 Herramienta / Lab | 🔍 Descripción | 🔗 Fuente |
| --- | --- | --- |
| [Analizador de acceso de IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)| Herramienta de AWS para identificar y reducir permisos excesivos, alineada con el principio de mínimo privilegio | AWS |
| [Soluciones de gestión de accesos privilegiado](https://www.beyondtrust.com/resources/glossary/privileged-access-management-pam) | Suite de herramientas de BeyondTrust para aplicar el mínimo privilegio en distintos entornos | BeyondTrust |

### 🛠 Security by Design

¿Por qué **pegar la seguridad con celo al final** cuando puedes **construirla desde el principio**? Eso es exactamente lo que propone **Security by Design**: que la seguridad esté presente en **cada decisión**, desde la arquitectura hasta el despliegue. No es un parche, es un **requisito desde el día uno**.

El problema clásico: un equipo diseña y desarrolla una aplicación, la lanza a producción, y **luego** alguien dice "oye, ¿y la seguridad?". Para entonces, arreglar los fallos de diseño cuesta **entre 10 y 100 veces más** que si se hubieran pensado desde el principio. No es exageración, es lo que dice el NIST.

#### Principios clave

- **Modelado de amenazas desde el diseño**. Antes de escribir una línea de código, identifica dónde están los riesgos. Si no sabes qué puede fallar, no puedes protegerlo.
- **Secure by Default**. La configuración más segura debe ser la opción **por defecto**. Si el usuario tiene que activar la seguridad manualmente, la mayoría no lo hará.
- **Desarrollo seguro**. Usar prácticas que prevengan vulnerabilidades en el código: validación de inputs, manejo seguro de errores, principios OWASP.
- **Automatización de pruebas de seguridad**. SAST, DAST, SCA integrados en el pipeline de CI/CD. Si no está automatizado, no se hace.
- **Diseñar para el fallo**. Asume que alguna parte del sistema **será comprometida**. Diseña para que el daño sea contenido.
- **Formación continua**. Todo el equipo debe entender los fundamentos de seguridad. No solo los de seguridad: también los devs, los de infra, los de producto.

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#1F1B2D;">
    <b>⚠️ Ojo.</b> Security by Design <b>no significa que todo tiene que ser Fort Knox</b>. Significa que la seguridad se considera desde el diseño, se adapta al riesgo, y se integra en el proceso. Ni más, ni menos.
</div>

#### Ejemplo real: ¿por qué importa?

Imagina un equipo que desarrolla una API. Si desde el diseño deciden:

- Validar todos los inputs
- Usar autenticación con tokens de corta duración
- Limitar los permisos de las cuentas de servicio
- Registrar cada acceso

...entonces cuando (no _si_, sino _cuando_) alguien intente explotar esa API, las barreras ya están ahí. Pero si estos controles se añaden "después", siempre quedan huecos.

#### 📚 Lecturas recomendadas

¿Quieres profundizar más? Estas son nuestras referencias principales para reforzar lo que acabas de aprender.

**📖 Artículos y documentación**

| 🔗 Título | 📜 Descripción | 🔍 Fuente |
| --- | --- | --- |
| [Seguro por diseño](https://www.cisa.gov/securebydesign) | Guía de CISA para integrar la seguridad en el ciclo de vida del desarrollo de software y prevenir vulnerabilidades | CISA |
|[Seguridad por diseño: Los 10 principios para hacerlo bien](https://medium.com/@tahirbalarabe2/security-by-design-the-ten-principles-of-getting-it-right-68c6ff00ffe1)| Artículo que describe diez principios esenciales para aplicar Security by Design de forma eficaz | Medium |
| [Seguridad por diseño: una lista anotada](https://www.lawfaremedia.org/article/security-by-design-an-annotated-resource-list) | Lista curada de documentos, guías y análisis gubernamentales sobre Security by Design | Lawfare |

**🎥 Vídeos**

| 🎬 Título | ⏳ Duración | 🔍 Fuente |
| --- | --- | --- |
| [10 principios de Seguridad desde el Diseño: integrando la seguridad en tus sistemas](https://www.youtube.com/watch?v=3l8GwLv2f3E) | 15 min | YouTube |
| [Diseño seguro: mejores prácticas de endurecimiento](https://www.youtube.com/watch?v=cGoWeFlV2ZQ) | 20 min | YouTube |
| [Principios de diseño seguro](https://www.youtube.com/watch?v=lL1Lg-DvnYk) | 12 min | YouTube |

**🛠 Herramientas y laboratorios prácticos**

| 🛠 Herramienta / Lab | 🔍 Descripción | 🔗 Fuente |
| --- | --- | --- |
| [Microsoft Threat Modeling Tool](https://www.microsoft.com/en-us/securityengineering/sdl/threatmodeling) | Herramienta de Microsoft para identificar y mitigar problemas de seguridad durante la fase de diseño | Microsoft |
| [IriusRisk](https://www.iriusrisk.com/) | Plataforma para modelado de amenazas automatizado y diseño seguro integrado en el proceso de desarrollo | IriusRisk |

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🗝 Identity & Access Management (Gestión de Identidades y Accesos)

Si la seguridad tuviera un **único punto de fallo**, sería este. **IAM** es el **portero de todo tu sistema**. Si falla, **nada más importa**: los atacantes no necesitan hackear tus servidores si pueden **iniciar sesión directamente**.

Las empresas invierten en herramientas de seguridad carísimas. Pero si un atacante puede saltarse todo **robando una contraseña**, nada de eso sirve. Un IAM débil convierte el resto de tu seguridad en **un fallo aplazado**.

👏 **Deja.** 👏 **De.** 👏 **Hacer.** 👏 **Esto.** 👏

IAM trata de **quién entra**, **qué puede hacer** y **durante cuánto tiempo**. Piénsalo como la seguridad de un aeropuerto:

- **Autenticación (AuthN)**: demostrar quién eres.
- **Autorización (AuthZ)**: controlar qué puedes hacer.
- **Gestión de sesión**: asegurarse de que el acceso **expira cuando debe**.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>☝️🤓 Que no se te olvide.</b> Autenticación = <b>"¿Quién eres?"</b> / Autorización = <b>"¿Qué puedes hacer?"</b>. Son cosas distintas. Confundirlas es un clásico.
</div>

Suena simple, ¿verdad? Pues la **mayoría de los incidentes de seguridad implican fallos de IAM**. Los atacantes no necesitan forzar la entrada si pueden simplemente **iniciar sesión**. Y una vez dentro, una mala configuración de IAM les permite **moverse libremente, escalar privilegios y hacer lo que les dé la gana**.

### 🪪 Autenticación

La autenticación es el **primer paso** del IAM. Si falla, **nada más importa**. Los atacantes no necesitan exploits si simplemente pueden iniciar sesión. La mayoría de los robos de credenciales se deben a **una autenticación débil o a un mal comportamiento del usuario**.

Existen tres formas de verificar la identidad:

1. **Algo que sabes**: contraseñas, PINs, preguntas de seguridad  
2. **Algo que tienes**: un dispositivo, una llave de seguridad, una app autenticadora  
3. **Algo que eres**: biometría como huellas dactilares o reconocimiento facial  

> ⚠️ **El MFA debe combinar al menos dos de estos factores**. Usar dos contraseñas (por ejemplo, contraseña + pregunta de seguridad) **no es MFA real**: sigue siendo solo “algo que sabes”.

#### Debilidades de la autenticación

La autenticación falla de dos formas:

- **MFA débil y mala seguridad de contraseñas**. Si la autenticación es débil, el IAM es solo una ilusión  
- **Sesiones de larga duración y secuestro de sesión**. La autenticación no consiste solo en **entrar**, sino en asegurarse de que **los atacantes no puedan quedarse**

> **💡 La mayoría de los robos de credenciales ocurren** porque la autenticación es demasiado débil o demasiado incómoda, por lo que los usuarios se la saltan.

##### [Avanzado] MFA débil y seguridad de contraseñas

- **2FA basado en SMS**. El SIM swapping es tan sencillo que los atacantes **tienen literalmente call centers** dedicados a estafar a operadoras móviles  
- **Verificación por correo electrónico**. Si un atacante compromete tu email, **lo controla todo**  
- **Autenticación solo biométrica**. Tu cara y tus huellas **no se pueden cambiar** si se ven comprometidas. Además, los **deepfakes** y la **suplantación de sensores** son cada vez mejores  
- **Credenciales hardcodeadas en el código fuente**. Los desarrolladores aún lo hacen y los atacantes siguen escaneando GitHub en busca de claves expuestas  

##### [Avanzado] Sesiones de larga duración y secuestro de sesión

- **Sin expiración de sesión**. Si un atacante roba un token antiguo, tiene acceso para siempre  
- **Sin reautenticación para acciones críticas**. El usuario debería volver a verificar su identidad antes de cambiar configuraciones de seguridad o realizar acciones sensibles  
- **Secuestro de sesión mediante cookies**. Si un atacante roba una cookie de sesión (por ejemplo, mediante **XSS** o ataques **MITM**), se salta la autenticación por completo  

#### Buenas prácticas

- **Usar MFA resistente al phishing en todas partes**. Nada de 2FA por SMS. Solo FIDO2, passkeys o tokens hardware  
- **Forzar políticas de contraseñas fuertes**. Bloquear contraseñas reutilizadas, débiles o filtradas  
- **Rotar y expirar tokens de sesión**. Limitar la exposición forzando cierres de sesión automáticos  
- **Usar autenticación adaptativa**. Si un usuario inicia sesión desde un dispositivo o ubicación nueva, solicitar verificación adicional  
- **Implementar Single Sign-On (SSO)**. Menos contraseñas = menos oportunidades de liarla  

#### Protocolos de autenticación

Estos son los protocolos de autenticación **estándar de la industria** que cualquiera que trabaje con IAM **debe** conocer:

- **OpenID Connect (OIDC)**: el protocolo de **autenticación** más usado, construido sobre OAuth 2.0. Se utiliza en logins web y móviles (por ejemplo, “Iniciar sesión con Microsoft”)  
- **Kerberos**: protocolo de autenticación **basado en tickets**, usado en entornos empresariales (Active Directory, SSO corporativo). Elimina la reutilización de contraseñas mediante tickets criptográficos  
- **FIDO2/WebAuthn**: estándar de **autenticación sin contraseña** que usa claves criptográficas almacenadas en dispositivos de seguridad hardware (por ejemplo, YubiKeys o biometría)

> **💡 OAuth 2.0 NO es un protocolo de autenticación.** Es un framework de autorización. Por eso existe OpenID Connect: para añadir autenticación encima de OAuth.

### 👮 Autorización

Incluso si un atacante consigue credenciales válidas, **la autorización debería impedir que cause daños reales**.  
La autenticación determina **quién entra**, pero la autorización controla **qué puede hacer** una vez dentro.

Una mala autorización es la razón por la que los atacantes **no necesitan 0-days**: basta con comprometer **una cuenta con demasiados privilegios** para que el sistema pase a ser suyo.

#### Debilidades de la autorización

Los fallos de autorización **no siempre parecen brechas de seguridad** al principio. Muchos son **errores silenciosos de permisos** que permanecen ocultos hasta que un atacante los explota.

- **Cuentas con demasiados privilegios**. Si todo el mundo es admin, nadie lo es  
- **Políticas IAM mal configuradas en la nube**. Buckets S3 abiertos, APIs expuestas y permisos débiles son consecuencia directa de malas políticas IAM  
- **Falta de revisiones de acceso y auditoría**. Si no sabes quién tiene acceso a qué, no puedes detectar cuentas sobre-privilegiadas  

##### [Avanzado] Cuentas con demasiados privilegios

La mayoría de los usuarios tiene **mucho más acceso del que realmente necesita**. Esto es una catástrofe esperando a ocurrir.

- **Acceso “por si acaso”**. En lugar de conceder permisos solo cuando se necesitan, se dan por defecto  
- **Cuentas admin usadas para tareas diarias**. Si un atacante compromete una cuenta admin, lo obtiene todo  
- **Sin separación de roles**. Desarrolladores con acceso directo a producción, equipos financieros capaces de modificar logs. Desastre asegurado  

##### [Avanzado] Políticas IAM mal configuradas en la nube

Los permisos en la nube son **notoriamente fáciles de liarla**. A los atacantes les encantan las **políticas IAM mal configuradas** porque suelen acabar en **acceso total accidental**.

- **Permisos demasiado amplios**. `"Action": "*"`, `"Resource": "*"` significa **acceso total a todo**  
- **Sin restricciones en cuentas de servicio**. Una API key filtrada con permisos ilimitados = **atacantes usando tu infraestructura cloud a tu costa**  
- **Sin restricciones basadas en red**. IAM debería tener en cuenta ubicación, dispositivo y comportamiento, no solo usuario y contraseña  

Las fugas de datos en AWS han ocurrido repetidamente porque buckets S3 estaban configurados como públicos, permitiendo a cualquiera descargar datos sensibles sin siquiera autenticarse.

##### [Avanzado] Falta de revisiones de acceso y auditoría

El IAM a menudo se **configura una vez y se olvida**, dejando agujeros de seguridad invisibles.

- **Cuentas huérfanas**. Ex-empleados con acceso durante meses o años  
- **Sin logs de acceso**. Si no registras la actividad IAM, no sabes cuándo se abusa de ella  
- **Privilege creep**. Los permisos se acumulan con el tiempo hasta que usuarios de bajo nivel tienen casi acceso de admin  

#### Buenas prácticas

- **Implementar Role-Based Access Control (RBAC)**. Asignar permisos a roles, no a individuos  
- **Usar Attribute-Based Access Control (ABAC)**. Limitar el acceso según ubicación, dispositivo y comportamiento  
- **Forzar acceso Just-in-Time (JIT)**. Conceder permisos de admin solo cuando se necesitan y revocarlos automáticamente  
- **Requerir aprobación para escalado de privilegios**. Nadie debería poder concederse permisos de admin a sí mismo  
- **Revisar y eliminar permisos innecesarios de forma regular**  

#### Modelos de autorización

Diferentes modelos definen cómo se asignan y aplican los permisos:

- **Role-Based Access Control (RBAC)**: permisos asignados según roles (por ejemplo, rol “Finanzas” con acceso a software contable)  
- **Attribute-Based Access Control (ABAC)**: el acceso se determina mediante atributos (ubicación, departamento, nivel de seguridad)  
- **Discretionary Access Control (DAC)**: los usuarios pueden conceder acceso a otros (bueno para colaboración, terrible para seguridad)  
- **Mandatory Access Control (MAC)**: acceso estricto basado en políticas, usado en entornos de alta seguridad (militar, gobierno)  

RBAC es el más común por su simplicidad, pero **ABAC es más flexible para entornos cloud modernos**.

### ⏳ Gestión de sesiones

La autenticación te permite entrar, **la gestión de sesiones te mantiene bajo control**. Controla **cuánto tiempo permaneces autenticado**, si tu sesión sigue siendo válida y con qué rapidez un atacante puede abusar de un token robado.

Una sesión es, básicamente, el **estado de un usuario autenticado**.  
¿El problema? Si un atacante roba un token de sesión, **ya no necesita credenciales**: simplemente reutiliza una sesión existente y entra directamente.

La seguridad de sesiones se basa en tres reglas clave:

1. Ninguna sesión debería durar para siempre. Si sigues conectado desde **2019**, algo va muy mal  
2. Acciones importantes, como cambiar contraseñas o configuraciones de seguridad, deben **forzar reautenticación**  
3. Si cambias tu contraseña o revocas una sesión, **todas las sesiones activas deben cerrarse inmediatamente**

La gestión de sesiones es **tan importante como la autenticación**.  
Si un atacante roba o secuestra una sesión, **ya está dentro**.

**O arreglas la gestión de sesiones, o no te molestes en implementar autenticación.**

#### Fallos comunes en la gestión de sesiones

La gestión de sesiones falla de cuatro formas principales:

- **Sesiones de larga duración**. Si las sesiones nunca expiran, el atacante mantiene acceso indefinidamente  
- **Secuestro de sesión**. El atacante roba el token de sesión (mediante XSS, MITM o malware) y se salta la autenticación por completo  
- **Session Fixation**. El atacante fuerza a la víctima a usar un ID de sesión que él ya controla  
- **Sin revocación de sesiones**. Si cambiar la contraseña no invalida sesiones activas, **el reset no sirvió de nada**

La conclusión es clara:  
**Sesiones = credenciales**.  
Si un atacante roba tu sesión, **es literalmente tú**.

#### Buenas prácticas

Una buena gestión de sesiones no consiste solo en **mantener usuarios conectados**, sino en **mantener a los atacantes fuera**.

##### Usar sesiones de corta duración

- **Definir tiempos de expiración estrictos**. Las sesiones deben expirar en minutos, no en días  
- **Usar refresh tokens** en lugar de sesiones infinitas  
- Los **tokens de API deben ser de corta duración**, y las claves de larga duración deben requerir autenticación adicional  

##### Rotar y revalidar sesiones

- **Regenerar tokens de sesión en cada login** para evitar session fixation  
- **Rotar tokens en cambios de privilegios** (por ejemplo, cuando un usuario pasa a ser admin)  
- **Forzar reautenticación** para acciones de alto riesgo  

##### Vincular sesiones al contexto

- **Restringir sesiones por IP o dispositivo**  
- **Detectar anomalías**: si una sesión cambia de ubicación de forma repentina, asumir compromiso  

##### Endurecer cookies de sesión

- **Usar cookies `HttpOnly`** para impedir acceso desde JavaScript  
- **Activar `Secure`** para evitar envío por HTTP  
- **Usar `SameSite=Strict`** para prevenir ataques CSRF  
- Nunca almacenar tokens en **localStorage o sessionStorage**  

##### Revocar sesiones cuando ya no sean necesarias

- **Cerrar todas las sesiones al cerrar sesión o cambiar contraseña**  
- **Permitir al usuario ver y revocar sesiones activas**  
- **Implementar Single Logout (SLO)** en autenticación federada  

#### Lecturas adicionales

**📖 Guías y Cheat Sheets**

- [OWASP Session Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)

**🎥 Vídeos**

- [Introduction to Session Management - Identifying Security Vulnerabilities](https://www.youtube.com/watch?v=usqf6EhUdoA)
- [Session vs Token Authentication in 100 Seconds](https://www.youtube.com/watch?v=UBUNrFtufWo)
