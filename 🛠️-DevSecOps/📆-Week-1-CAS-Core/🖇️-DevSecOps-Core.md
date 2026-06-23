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
| Saalamero | 11/2/2026 | First version created |
| @<C73C5218-17C3-6B53-B15D-E321D12689EB> | 18/2/2026 | Reescritura completa |

<br>

---

<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
<b><span style="color:#7C3AED; font-size: 17px;">💡 ¡¡EMPIEZA POR AQUÍ!!</span></b>
    <br><br>
    El Training Path no es algo de <b>leer y seguir</b>, es el <b>punto de partida</b>. Se espera que <b>investigues más allá de lo que se proponga en estos documentos </b>y profundices en los conceptos.
    <br><br>
    Recuerda que los recursos facilitados son una guía pero no el único material que existe.
    <br><br>
    <span style="color:#7C3AED;"><b>La ciberseguridad se basa en la capacidad de resolver los problemas que se plantean</b></span>. Si algo no tiene sentido, <b>investiga</b>. Si parece demasiado sencillo, posiblemente te hayas perdido algo.
<br><br>
O si te quieres poner filosófico con ello, Einstein dijo: "No tengo ningún talento especial. Solo soy muy curioso."
</div>

Antes de meternos de lleno en **DevSecOps**, necesitas entender de dónde viene todo esto. Porque no se inventó de la nada: es el resultado de años de meter la pata, aprender, y volver a meter la pata.

Esta sección cubre la evolución desde el ciclo de vida clásico del software hasta DevSecOps:

- **SDLC**: el ciclo de vida clásico, cómo se construía software antes.
- **S-SDLC**: lo mismo, pero con seguridad metida en cada fase.
- **DevOps**: la revolución cultural y técnica que cambió cómo se entrega software.
- **DevSecOps**: la convergencia de todo lo anterior, seguridad continua, automatizada y desde el minuto cero.

Vamos a hacer un recorrido rápido por cómo ha ido evolucionando todo esto hasta llegar a donde estamos hoy.

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🧱 SDLC – Software Development Life Cycle

El **SDLC (Ciclo de Vida del Desarrollo de Software)** es básicamente la forma clásica de construir software. Define las fases por las que pasa un proyecto desde que alguien dice _"oye, necesitamos una aplicación"_ hasta que esa aplicación está en producción y se mantiene.

Es decir, seis fases, un orden, y a tirar millas.

### Fases típicas del SDLC

1. **Requisitos**: ¿Qué se necesita? ¿Qué tiene que hacer la aplicación?
2. **Diseño**: ¿Cómo lo vamos a construir? Arquitectura, tecnologías, diagramas.
3. **Desarrollo**: Se escribe el código.
4. **Testing**: Se prueba que funcione (o al menos que no explote).
5. **Despliegue**: Se pone en producción.
6. **Mantenimiento**: Se corrigen fallos, se actualizan cosas, se añaden funcionalidades y demás vainas.

Suena lógico y ordenado, ¿no? El problema es que en los modelos tradicionales (tipo **Waterfall**), estas fases se ejecutaban de forma **estrictamente secuencial**. No empezabas a desarrollar hasta que el diseño estaba cerrado. No probabas hasta que el desarrollo estaba terminado. Y no desplegabas hasta que todo estaba probado.

¿Y la seguridad? Se dejaba para el final. **Literalmente**:

- La seguridad se revisaba **al final**, cuando ya estaba todo hecho.
- Las revisiones eran manuales y lentas.
- Corregir vulnerabilidades a esas alturas era **carísimo**.
- El equipo de seguridad iba por su cuenta, aislado del resto.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 ¿Por qué importa esto?</b> Porque <b>cuanto más tarde encuentras un fallo de seguridad, más cuesta arreglarlo</b>. Un error de diseño detectado en la fase de requisitos se corrige en minutos. El mismo error detectado en producción puede costar semanas, miles de euros y una crisis de reputación.
</div>

La seguridad en el SDLC tradicional era **reactiva**: te enterabas del problema cuando ya estaba en producción. Y arreglarlo a esas alturas costaba un ojo de la cara.

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🔐 S-SDLC – Secure Software Development Life Cycle

El **S-SDLC** es la evolución lógica: coger el SDLC de toda la vida y meterle seguridad en **cada fase**, no solo al final.

La idea parece obvia, pero tardó años en calar. Durante mucho tiempo, la seguridad era "cosa de otro equipo". Los desarrolladores construían, el equipo de seguridad revisaba al final, encontraba un montón de problemas, se los devolvía al equipo de desarrollo, y así entraban en un ciclo infinito de _"arregla esto"_ → _"pero es que ya está todo hecho"_ → _"pues deshazlo y arréglalo"_.

El S-SDLC rompe ese ciclo integrando la seguridad **desde el principio**:

### ¿Qué cambia respecto al SDLC?

Veamos cada fase:

- **Requisitos**: se definen requisitos de seguridad y compliance desde el día 1. No solo "qué hace la app", sino "qué debe proteger".
- **Diseño**: se hace Threat Modeling: identificar amenazas y diseñar contramedidas antes de escribir una línea de código.
- **Desarrollo**: secure coding + revisiones de código centradas en seguridad.
- **Testing**: se añaden herramientas automáticas: SAST (análisis estático), DAST (análisis dinámico), SCA (análisis de dependencias).
- **Despliegue**: hardening y configuración segura del entorno.
- **Mantenimiento**: monitorización continua y gestión activa de vulnerabilidades.

Aquí nace el concepto de **Shift Left Security**: mover la seguridad **lo más a la izquierda posible** en el ciclo. En vez de esperar a que las cosas estén hechas para revisarlas, las aseguras desde el diseño.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>☝️🤓 Shift Left.</b> no es solo una palabreja, es la idea de que <b>prevenir es más barato que curar</b>. Y en seguridad, eso se traduce en: encuentra el fallo en el diseño, no en producción.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🔧 DevOps

DevOps surge para resolver un problema completamente distinto: que los de desarrollo (**Dev**) y los de operaciones (**Ops**) se llevaban "fatal".

Tradicionalmente, el equipo de desarrollo escribía código y se lo tiraba por encima del muro al equipo de operaciones para que lo desplegara. Si algo petaba en producción, empezaba el juego de _"eso funciona en mi máquina"_ vs _"pues aquí no"_. Tensión, desconfianza y deploys que daban miedo.

DevOps nace para romper ese muro y crear una **cultura de colaboración** entre ambos equipos, apoyada en automatización. Al final, tanta es la "colaboración, que en muchas empresas ni siquiera existen equipos separados, sino que cada equipo es responsable de todo el ciclo de vida de su aplicación, desde el desarrollo hasta la operación.

### ¿Qué trae DevOps?

- **CI/CD (Integración y Entrega Continua)**: Automatizar el proceso de build, test y despliegue. Cada cambio en el código se integra, se prueba y se puede desplegar de forma automática.
- **Infraestructura como Código (IaC)**: Gestionar la infraestructura con código (Terraform, CloudFormation, Ansible...) en vez de configurar servidores a mano. Reproducible, versionable, auditable.
- **Observabilidad**: Saber qué está pasando en tus sistemas en todo momento. Métricas, logs, trazas.
- **Entregas continuas**: En vez de un gran despliegue al mes (con su correspondiente drama), pequeños despliegues frecuentes que son más fáciles de gestionar y revertir.

El objetivo: **entregar más rápido sin que todo se vaya al garete**.

<div style="text-align: center; margin-bottom: 20px;">
   <img src="https://ubiqware.net/wp-content/uploads/2022/02/devops-on-white-2-1024x509.png" style="border: 3px solid lightgray; width: 500px; padding: 1rem; height: auto;">
</div>

### El problema de DevOps (sin seguridad)

Aunque DevOps mejora enormemente la velocidad y la colaboración, tiene un agujero importante: **la seguridad no forma parte de la ecuación**. En muchos sitios:

- La seguridad se sigue añadiendo al final, como un parche.
- Se convierte en un _"gate manual"_ que ralentiza todo el pipeline y frustra a los equipos.
- O directamente se le endosa a un equipo separado: _"ya lo revisarán ellos"_.

El resultado es que los equipos entregan más rápido... pero **también entregan vulnerabilidades más rápido**. Y cuanto más automatizas sin seguridad, más rápido pones código inseguro en producción.

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🔐 DevSecOps

DevSecOps **no sustituye** a DevOps. Es DevOps **con seguridad metida de serie**. La "Sec" no es un añadido, es una parte integral.

> **DevOps + Seguridad integrada de forma continua y automatizada = DevSecOps**

La idea es llevar los principios del **S-SDLC** directamente a los **pipelines de CI/CD**. Donde antes era _"primero desarrollo, luego ya veremos la seguridad"_, ahora la seguridad **va integrada en cada paso del pipeline de forma automática**.

### ¿Qué significa en la práctica?

- **SAST** (Static Application Security Testing) se ejecuta en cada commit, analizando el código fuente en busca de vulnerabilidades.
- **SCA** (Software Composition Analysis) revisa las dependencias de terceros — porque sí, ese paquete de npm que instalaste hace tres años puede tener vulnerabilidades conocidas.
- **DAST** (Dynamic Application Security Testing) ataca la aplicación en ejecución para encontrar fallos que el análisis estático no detecta.
- **IaC scanning** revisa que tu infraestructura como código no tenga misconfigurations — porque un Terraform con un security group abierto al mundo es tan peligroso como un SQL injection.
- **Container scanning** analiza las imágenes Docker para encontrar vulnerabilidades en las capas base.
- **Secret detection** busca credenciales hardcodeadas en el código — API keys, contraseñas, tokens... cosas que no deberían estar ahí pero que siguen apareciendo.

Todo esto se ejecuta **de forma automática en el pipeline**, sin que el desarrollador tenga que hacer nada especial. El feedback es inmediato: si introduces una vulnerabilidad, te enteras en minutos, no en semanas.

<div style="text-align: center; margin-bottom: 20px;">
   <img src="https://media.licdn.com/dms/image/v2/D4D12AQG886tZA7WObg/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1678866159676?e=2147483647&v=beta&t=pnKntg_zVRCrSo5QQyzezHKwPurFr6u4X2z3_ZynZIo" style="border: 3px solid lightgray; width: 700px; padding: 1rem; height: auto;">
</div>

### DevSecOps no es solo herramientas

Meter un escáner en el pipeline y darlo por hecho **no es DevSecOps**, es poner una herramienta. DevSecOps es un cambio de mentalidad:

- **La seguridad es responsabilidad de todos**, no solo del equipo de seguridad.
- **Los desarrolladores escriben código seguro** porque saben por qué importa, no porque alguien les obligó.
- **La seguridad no bloquea**, sino que acompaña. Si el equipo de seguridad solo dice "no" y bloquea releases, nadie va a querer trabajar con ellos.
- **El feedback es rápido y accionable**. No sirve de nada un informe de 200 páginas que nadie lee. Sirven alertas concretas en el momento del commit.

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ Esto es importante</span></b>
    <br><br>
    DevSecOps no es "instalar SonarQube y ya está", es un <b>cambio cultural</b>. Si el equipo de desarrollo ve la seguridad como un enemigo que les ralentiza, <b>algo estás haciendo mal</b>. La seguridad debe ser un aliado que ayuda a entregar software de calidad, no un muro que bloquea entregas.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## ⚖️ Evolución Comparativa

Para que quede claro cómo encaja todo, aquí tienes la evolución de un vistazo:

| Modelo | Seguridad | ¿Cuándo se detectan problemas? | Cultura |
|---------|------------|-------------------------------|----------|
| **SDLC tradicional** | Reactiva — al final, si es que se hace | En producción (o peor: después de un incidente) | Silos — cada equipo por su cuenta |
| **S-SDLC** | Preventiva — en cada fase | Durante el ciclo de desarrollo | Seguridad integrada en el proceso |
| **DevOps** | No prioritaria — depende del equipo | Variable — a veces al final, a veces nunca | Colaboración Dev + Ops |
| **DevSecOps** | Continua y automatizada | Desde el commit — feedback inmediato | Seguridad como responsabilidad compartida |

La evolución es clara: de **"la seguridad es problema de otro"** a **"la seguridad es problema de todos"**. Y de **"revisamos al final"** a **"revisamos continuamente"**.

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🚀 ¿Por qué DevSecOps es la evolución lógica?

Porque junta todo lo weno:

- La **estructura del S-SDLC**: seguridad en cada fase.
- La **automatización de DevOps**: feedback rápido y entregas continuas.
- La **cultura colaborativa**: desarrollo, operaciones y seguridad trabajando juntos.
- La **seguridad integrada desde el minuto cero**: no como parche, sino como parte del ADN del proyecto.

Y resuelve el gran problema del mundo moderno: en entornos cloud, con microservicios y despliegues continuos, **no te puedes permitir revisar la seguridad a mano al final**. La seguridad tiene que escalar al mismo ritmo que el desarrollo, o estás vendido.

Piénsalo así. **DevOps** responde a:

> _¿Cómo entregamos más rápido?_

Mientras que **SDLC** responde a:
> _¿Cómo entregamos más rápido **sin que nos hackeen por el camino**?_

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📌 Resumen

- **SDLC**: El ciclo clásico de toda la vida. Seguridad al final (si acaso).
- **S-SDLC**: Lo mismo, pero con seguridad en cada fase. Nace el concepto de _Shift Left_.
- **DevOps**: Automatización, CI/CD y entrega continua. Pero la seguridad no pinta nada.
- **DevSecOps**: Todo lo anterior + seguridad continua, automatizada y como responsabilidad compartida.

DevSecOps no es solo meterle un escáner al pipeline y ya, es una **evolución cultural y técnica** del SDLC adaptada al mundo cloud-native.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>☝️🤓 Google existe.</b> Si te bloqueas, úsalo. Si sigues bloqueado, pregúntale a tu trainer.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📚 Lecturas recomendadas

¿Quieres profundizar más? Aquí tienes recursos para cada tema.

### 📖 Artículos

| 🔗 Título | 📜 Descripción | 🔍 Fuente |
| --- | --- | --- |
| [What is SDLC?](https://aws.amazon.com/what-is/sdlc/) | Explicación completa del ciclo de vida del desarrollo de software | AWS |
| [What is the Secure SDLC?](https://snyk.io/learn/secure-sdlc/) | Cómo integrar seguridad en cada fase del SDLC | Snyk |
| [What is DevOps?](https://aws.amazon.com/devops/what-is-devops/) | Introducción a DevOps, sus principios y prácticas | AWS |
| [What is DevSecOps?](https://www.redhat.com/en/topics/devops/what-is-devsecops) | Visión general de DevSecOps y cómo implementarlo | Red Hat |
| [DevSecOps Manifesto](https://www.devsecops.org/) | El manifiesto original de DevSecOps | DevSecOps.org |

### 🎥 Vídeos

| 🎬 Título | ⏳ Duración | 🔍 Fuente |
| --- | --- | --- |
| [DevOps in 5 Minutes](https://www.youtube.com/watch?v=Xrgk023l4lI) | 5 min | IBM Technology |
| [What is DevSecOps?](https://www.youtube.com/watch?v=J73MELGF6u0) | 8 min | IBM Technology |
| [DevSecOps explained](https://www.youtube.com/watch?v=nrhxNNH5lt0) | 9 min | GitHub |
| [Shift Left Security](https://www.youtube.com/watch?v=g1f29TJ5Xwo) | 5 min | Snyk |

</div>
