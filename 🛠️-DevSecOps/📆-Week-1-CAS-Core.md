[[_TOC_]]

## 📝Changelog

| Author | Modification Date | Changes |
|------|-------------------|---------|
| @Antonio| 07/01/2026 | First Version Created |

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

¡Enhorabuena ya estás aquí! Disfruta de esta semana, será la más fácil de todo el Training Path.

En esta semana no veremos nada de configuraciones ni de código solo la teoría fundamental que toda persona dentro de CAS y DevSecOps debe tener como base.

Cubriremos:

- Teoría básica de aplicaciones.
- Tipos de arquitectura en aplicaciones.
- Tipos de servicio en informática.
- Conceptos de seguridad.

Esta teoría no hay que aprendérsela como para un examen palabra por palabra pero si entenderla y saber diferenciar entre un concepto u otro.

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ ATENTO</span></b>
    <br><br>
    <i>(Deberías saberlo, pero por si acaso)</i>
    <br><br>
Antes de continuar, hay que tener claro una cosa. El Training Path no es para nosotros, sino para <b>ti</b>. No queremos que memorices el contenido o te prepares respuestas, lo más importante y lo que se busca es que realmente <b>aprendas</b>.
    <br><br>
No esperamos perfección, sino esfuerzo. Lo que se pide lo tienes que hacer TÚ. Si detectamos algo raro, la entrega será rechazada. Sin excepción.
    <br><br>
    <b>No seas ese pringad@ </b>
</div>

Antes de nada asegúrate de haber leído la página de las fases: 👉 **[📚 Fases](/✏️-Guía-del-Training/📚-Fases)**
Si te la saltaste, léetela, no vamos a repetirlo aquí, de esa forma podrás entender las siguientes secciones :
- **Checkpoints & Expectations** (no nos preguntes)
- **How to approach exercises** (no nos preguntes)

Si haces alguna pregunta sobre algo que está **claramente explicado ahí**, es muy probable que no te contestemos.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
<b>☝️🥸 Google existe.</b> Si te bloqueas, úsalo. Si sigues bloqueado, pregúntale a tu trainer.
</div>

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ IMPORTANTE</span></b>
    <br><br>
Si tienes algún problema o necesitas ayuda, es <b>muy importante</b> que mires <b><a href="https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/106/%F0%9F%94%B0-Visi%C3%B3n-General?anchor=%C2%BFc%C3%B3mo-preguntar-un-problema-o-pedir-ayuda%3F">esta sección</a></b> donde se explica como hacerlo.
</div>

📌 Week Structure
-----------------

Independientemente de si eres un Intern (becario) o New Hire (contratado), haremos lo mismo durante esta semana:

- Aprender conceptos fundamentales
- Aplicar los conceptos a ejercicios prácticos.
- Demostrar el aprendizaje mediante entregas y defensas que se vayan a realizar.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Tip. </b>No necesitas memorizar antes de empezar con la parte práctica. Si algún tema está directamente relacionado con la tarea, puedes ir aprendiendo sobre la marcha, es la mejor manera de aprender.
</div>

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>✍️ Toma notas.</b> No te dediques solo a leer. <b>Escribe cosas con tus propias palabras.</b> Te ayudará a recordar mejor los conceptos.
</div>

🧱 Conceptos fundamentales
--------------------------

Antes de pasar a la práctica deberías tener estos conceptos interiorizados:

- [**Frontend y backend**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/470/%E2%9A%99%EF%B8%8F-Core-Concepts?anchor=%F0%9F%8C%90-frontend-vs-backend): qué es cada tipo, en qué se diferencian y cómo se complementan dentro de una aplicación.

- [**Microservicios vs Monolitos**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/470/%E2%9A%99%EF%B8%8F-Core-Concepts?anchor=%F0%9F%9B%A0-**microservicios**): qué es cada arquitectura, sus diferencias, ventajas y desventajas, y en qué casos es más adecuado usar cada enfoque.

- [**IaaS, PaaS y SaaS**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/470/%E2%9A%99%EF%B8%8F-Core-Concepts?anchor=%E2%98%81%EF%B8%8F-**iaas%2C-paas-y-saas**): qué ofrece cada modelo de servicio en la nube y cuáles son sus principales diferencias en términos de responsabilidad y control.

- [**Defects**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/472/%F0%9F%8C%8D-Core-Security-Concepts?anchor=%F0%9F%90%9E-**defects**&_a=edit): qué es un defecto, una debilidad y una vulnerabilidad, y cuáles son las diferencias entre estos conceptos.

- [**CIA triad**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/472/%F0%9F%8C%8D-Core-Security-Concepts?anchor=%F0%9F%94%BA-cia-triad): qué es la tríada de la seguridad y en qué consisten sus tres pilares: confidencialidad, integridad y disponibilidad.

- [**Zero Trust**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/472/%F0%9F%8C%8D-Core-Security-Concepts?anchor=%E2%9B%94zero-trust): qué significa este modelo de seguridad y por qué no se debe asumir confianza implícita en ningún usuario o sistema.

- [**Security by Design**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/472/%F0%9F%8C%8D-Core-Security-Concepts?anchor=%F0%9F%9B%A0-seguridad-desde-el-dise%C3%B1o): qué implica integrar la seguridad desde las primeras fases de diseño y desarrollo del sistema.

- [**Least Privilege**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/472/%F0%9F%8C%8D-Core-Security-Concepts?anchor=%F0%9F%94%91-m%C3%ADnimo-privilegio): qué significa el principio de mínimo privilegio y cómo se aplica para limitar accesos y reducir el impacto de un ataque.

- [**Defensa en profundidad**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/472/%F0%9F%8C%8D-Core-Security-Concepts?anchor=%F0%9F%A7%85-defensa-en-profundidad): qué es la estrategia de seguridad por capas y cómo ayuda a limitar el impacto cuando una defensa falla.

- [**IAM**](https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/472/%F0%9F%8C%8D-Core-Security-Concepts?anchor=%F0%9F%97%9D-identity-%26-access-management-(gesti%C3%B3n-de-identidades-y-accesos)): qué es la gestión de identidades y accesos y cómo controla quién puede acceder a qué recursos y bajo qué condiciones.

- [**DevSecOps Core**](/🛠️-DevSecOps/📆-Week-1-CAS-Core/🖇️-DevSecOps-Core): qué es DevSecOps y cómo nace la necesidad de introducirlo en el SDLC.

En esta tabla de aquí vamos a ver para cuando deberíais tener los conceptos aprendido.
 Hay dos categorías: Midweek (para mitad de semana) y Final (para final de semana).

| ITEM                     | WEEK |
|--------------------------|------|
| Frontend y backend       |  ✅ Midweek    |
| Microservices vs monolithic |  ✅ Midweek    |
| IaaS, PaaS y SaaS        |    ✅ Midweek  |
| Defects                  |   ✅ Midweek|
| CIA triad                |  ✅ Midweek    |
| Zero Trust               |  ✅ Midweek    |
| Security by Design       |    ✅ Midweek  |
| Least Privilege          |   ✅ Final|
| Defensa en profundidad   |  ✅ Final   |
| IAM                      |   ✅ Final   |
| DevSecOps Core                   |   ✅ Final  |

## 🛠 Ejercicios Prácticos

Para afianzar los conocimientos que has visto  tendrás que hacer tres ejercicios prácticos durante la semana:

### 🎯Tarea 1: Correo a un "cliente"
Deberás escribir un correo pensando que el receptor es un cliente (tu trainer), explicando que es el OWASP Top 10. El correo deberá ser estructurado y profesional.

**¿Que incluir?**

- ¿Que es el OWASP Top 10?
- ¿Como se compara con OWASP ASVS?
- ¿Por qué es importante para su compañía/proyecto?
- Un ejemplo de una vulnerabilidad asociada a OWASP Top 10.

**Requisitos** :

- Mantener estructura y lenguaje profesional.
- Tiempo límite: 1.5 horas, si te lleva más tiempo lo estás sobre pensando.

### 🎯Tarea 2: Primera parte del PowerPoint

⚠️ **¡¡QUIET@!!**: Antes de empezar con la PPT deberías tener una sesión formativa de buenas prácticas, formatos y estandarización con tu trainer. Tendrás una convocatoria en Teams para ver esto el segundo día de la semana 1.

Crea una presentación estructurada explicando <b>SAST, DAST, SCA</b> con buena estética y ejemplos en el mundo real.

Esta presentación la dividiremos en dos partes, haremos un checkpoint a mitad de semana para revisar antes de terminarla.
En esta primera parte crearás la primera parte de la presentación (como máximo 3 diapositivas).

**¿Qué incluir?**

- <b>Definición de SAST, DAST, SCA</b>: qué son y cómo funcionan
- <b>Ejemplos del mundo real de cada tipo</b>.
- <b>Diagrama o tabla de comparación</b>.

**Requisitos:**

- Añadir <b>elementos visuales </b> - NO mucho texto.
- Cada diapositiva se debe explicar por si misma, se deberán entender aunque tú no las expongas.
- <b>Máximo 3 diapositivas</b> de contenido.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
  <b>✍️ Si tus diapositivas parecen como si las hubiera hecho un ciego, prepárate para sufrir.</b>  En Accenture no queremos diapositivas feas. Por lo que tómate tu tiempo y asegúrate de que tus diapositivas son claras, estéticas y profesionales. Si no es así, tu trainer te lo hará saber y tendrás que rehacerlas.
</div>

## 🔎 Midweek Checkpoint

Aquí veremos qué es lo que habéis hecho para poder ver qué errores o qué cosas se pueden mejorar del trabajo. Vuestro trainer verá:

- <b>Email del cliente</b>: mirará la claridad, la estructura y cómo de correcto es.
- <b>Primera parte del PPT</b>: se asegurará de que se sigue el formato y la estructura de Accenture. Si las diapositivas no son claras o pierden puntos clave habrá que hacerlas de nuevo.

- <b>Entendimiento</b>: tu trainer te hará preguntas con el fin de saber si has entendido los conceptos.

Esta es una oportunidad para:

- Coger <b>feedback</b> y evitar arreglos de último minuto.
- Hacer <b>preguntas sobre conceptos</b> de la primera parte.
- Arreglar fallos de formato.

### 🎯Tarea 3: Terminar presentación

Después del Midweek Checkpoint, terminarás la segunda parte de la presentación. Es tu oportunidad para aplicar el feedback del anterior checkpoint.

**¿Qué incluir?**

- Definición de <b> SAST, DAST, SCA</b>: qué son y cómo funcionan
- Ejemplos del mundo real de cada servicio.
- Diagrama o tabla de comparación.

**Requisitos:**

- Añadir elementos visuales - NO mucho texto.
- Cada diapositiva se debe explicar por si misma, se deberán entender aunque tú no las expongas.
- Máximo 3 diapositivas de contenido.

## 📂 Resumen de las tareas

| **Item** | **Fecha** |
| --- | --- |
|Correo OWASP TOP 10| ✅ Midweek |
|Inicio PPT| ✅ Midweek |
| Terminar PPT| ✅ Final |

## 🔚 Final Checkpoint

Tu trainer revisará:

- <b>Presentación de PowerPoint</b>: estructura, contenido, formato y claridad.
- <b>Comprensión</b>: Espera que te hagan preguntas para ver **qué** has aprendido realmente.
