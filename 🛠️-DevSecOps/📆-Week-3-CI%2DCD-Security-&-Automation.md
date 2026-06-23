<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Table of Contents
    </summary>
  
  [[_TOC_]]
</details>

## 📝 Changelog

<br>

| Author                            | Modification Date       | Changes                                       |
|-----------------------------------|-------------------------|-----------------------------------------------|
| @<C73C5218-17C3-6B53-B15D-E321D12689EB>      | 14/02/2025              | First Version Created                         |
| @Alvaro Salamero                  | 12/01/2025              | Almost Completed Week 3 -  Pending  Review  |


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

Esta semana cubriremos la seguridad en ciclos CI/CD, es decir, conseguir que los flujos de desarrollo automatizados sean seguros.

- **Seguridad CI/CD**: Implementar medidas de seguridad en pipelines (pero sin romperlas constantemente).
- **SAST, DAST, and SCA**: Deberías conocer estos acrónimos a estas alturas. Uno encuentra vulnerabilidades en el código fuente, otra "ataca" tu aplicación y el otro te dice si las dependencias de tu aplicación son seguras.
- **Secrets Management**: Donde **NO** queremos almacenar las credenciales

Para el final de la semana, deberíamos tener una pipeline segura y automatizada que ejecute escáneres y maneje los secretos correctamente.

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

Antes de nada asegúrate de haber leído la pagina de las fases:
👉 **[📚 Fases](/✏️-Guía-del-Training/📚-Fases)**

Si te la saltaste, léetela, no vamos a repetirlo aquí, de esa forma podrás entender las siguientes secciones :
- **Checkpoints & Expectations** (no nos preguntes)
- **How to approach exercises** (no nos preguntes)

Si haces alguna pregunta sobre algo que está **claramente explicado ahí**, es muy probable que no te contestemos.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
<b>☝️🥸 Google existe.</b> Si te bloqueas, úsalo. Si sigues bloqueado, pregúntale a tu trainer.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📌 Week Structure

Independientemente de que seas un Intern o New Hire, lo que haremos a lo largo de la semana será:
- Aprender los Conceptos fundamentales
- Aplicar los conceptos sobre tareas guiadas.
- Demostrar la adquisición de conocimientos en los entregables y "defensas" que se realicen.

La diferencia radica en el nivel de ayuda y profundidad que se pedirá en cada caso.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Tip.</b>No necesitas memorizar antes de empezar con la parte práctica. Si algún tema está directamente relacionado con la tarea, puedes ir aprendiendo sobre la marcha, es la mejor manera de aprender. 
</div>

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>✍️ Toma notas.</b> No te dediques solo a leer. <b>Escribe cosas con tus propias palabras.</b> Te ayudará a recordar mejor los conceptos.
</div>

## 🧱 Conceptos fundamentales

Antes de ponernos manos a la obra con aspectos técnicos del ejercicio práctico que realizarás esta semana es importante tener claros algunos conceptos clave para que       el ejercicio no se te atragante.

- **¿Qué significa CI/CD?**
  - Diferencia entre Integración Continua, Entrega Continua y Despliegue Continuo.
  - ¿Cómo afectan en el desarrollo y despliegue software?
  - Ejemplo práctico de un flujo real
- **¿Qué es una pipeline?**
  - Estructura: Stages, jobs, tasks, ...
  - Relación con la automatización de builds, tests y despliegues
  - Ejemplo práctico de un flujo real
- **Principales plataformas: Gitlab, Azure y Github**
  -  Diferencias en configuración, YAML vs UI, flexibilidad
  -  Soporte para self-hosted runners
- **[Shared Libraries](/🛠️-DevSecOps/📆-Week-3-CI%2DCD-Security-&-Automation/📖-Shared%2DLibraries)**




## 🛠 Ejercicios Prácticos

El objetivo de esta semana consistirá en crear una **pipeline DevSecOps** sobre un proyecto vulnerable como WebGoat. Lo principal para esta semana es que termines entendiendo a la perfección qué son las pipelines y el motivo por el cual es tan importante que existan **controles** y **medidas** de **seguridad** en las mismas.
### 🎯 Tarea 1: Diseño Inicial
La primera parte del ejercicio consiste en que nos plantees un diseño de pipeline CICD completo, que tendrá que cubrir todo el flujo DevSecOps, pasando por **escaneos de seguridad, compilado de la aplicación, posterior build de la imagen y despliegue del aplicativo**.

Queremos que nos plantees que **estructura** a nivel de **stages** y **jobs** tendrá tu pipeline, especificando que tareas (escáneres, compilación, construcción, etc.) se llevarán a cabo en cada una de ellas.

Cualquier consideración extra de seguridad que creas oportuna también la puedes añadir.

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b>⚠️ A tener en cuenta</b><br><br>
    <ul style="margin:0;">
 No solo se trata de una pipeline de seguridad, también engloba aspectos de desarrollo. Trataremos el repo vulnerable como si fuese un proyecto que desarrollamos nosotros, y por lo tanto necesitamos asegurarnos de que el código compila y se puede buildear la imagen Docker correctamente.
</div>

### 🎯 Tarea 2: Creación de la pipeline
Con el feedback recibido sobre el diseño planteado, tendrás el resto de la semana para llevar a cabo la implementación de la pipeline con los requisitos que se habrán definido durante la sesión junto con el trainer.

### 📝 Tarea 3: Documentación Final

Para el final de la semana deberás entregar un documento técnico en formato Markdown como en semanas anteriores. En este debes incluir una guía del ejercicio, así como una sección específica de Seguridad de la Pipeline y otra sección centrada en el troubleshooting (problemas que hayas tenido y como los has solucionado).

---
## 📂 Resumen Entregables

- ✅ Diseño Inicial Pipeline-> MidWeek Checkpoint
- ✅ Pipeline Completa DSO -> Final
    - Correcta definición de Stages
    - Escáneres de seguridad bien implementados
    - Manejo información sensible
    - Funcionamiento correcto de todo el ciclo CI/CD
- ✅ Documentación Técnica -> Final

---

## 🧭 Herramientas Sugeridas (se admiten otras previa aprobación del Trainer)

- SAST: Semgrep
- SCA: Dep Check
- DAST: ZAP
- Secret Scanning: TruffleHog
- Image Scanning: Trivy


---

## 🔚 Final Checkpoint

Revisaremos:
- Correcta implementación de todo el flujo CI/CD.
- Reportes de las herramientas de seguridad.
- Correcta aplicación del concepto Shared-Llibrary
- Documentación completa y clara.


