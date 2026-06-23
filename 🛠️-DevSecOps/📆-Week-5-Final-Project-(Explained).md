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
| @alvaro      | 21/3/2026              | Fnal Version Created                         |

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


Esta semana es la **definitiva**, en la cual por fin pasaremos directamente a la práctica sin teoría de por medio.
- El principal objetivo es **demostrar** que te has convertido en expert@ en **DevSecOps**.
- Tienes buen manejo de los **conceptos** que has aprendido a lo largo del periodo de **entrenamiento**.
- Eres capaz de resolver problemas de forma autónoma y sabes lo que estás haciendo.

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

Esta semana tiene una estructura diferente a las anteriores, en ella directamente nos pondremos manos a la obra con el último ejercicio, también conocido como el **BOSS FINAL**, que será el mismo para new joiners y para interns. La diferencia radica en el nivel de **ayuda** y **profundidad** que se pedirá en cada caso.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Tip.</b>No necesitas memorizar antes de empezar con la parte práctica. Si algún tema está directamente relacionado con la tarea, puedes ir aprendiendo sobre la marcha, es la mejor manera de aprender. 
</div>

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>✍️ Toma notas.</b> No te dediques solo a leer. <b>Escribe cosas con tus propias palabras.</b> Te ayudará a recordar mejor los conceptos.
</div>

## 🛠 Ejercicios Prácticos

El objetivo de esta semana es demostrar que ya no eres la persona inepta que llegó hace unas semanas sin conocimientos de DSO, ahora puedes pensar por ti mism@ y resolver problemas autónomamente. Y por lo tanto se espera que seas capaz de hacer el ejercicio sin ayuda y sin checkpoint, si hay dudas ya las veremos en la presentación final con **TODO** el equipo.

Dicho lo cual, empecemos con el boss final...

### 🎯 Tarea 1: Integración y despliegue en flujo CI/CD

Como ya hemos comentado esta semana nos sirve para verificar qué has aprendido estas semanas. Pero no queremos hacerte perder el tiempo, y por lo tanto **siempre y cuando** los ejercicios de semanas anteriores los hayas realizado correctamente, podrás reutilizar bastante material y nos centraremos en añadir algunos pasos extra.

1. **Pipeline CI/CD**

En esta primera parte del ejercicio tendrás que construir una pipeline completa, reutilizando los materiales de la semana 3. No tienes que inventarte nada raro, simplemente adaptar lo que ya tienes al nuevo ejercicio.

Las características que debe cumplir son:
- Pipeline basada en **templates reutilizables**, siguiendo el modelo visto en la semana 3 de las shared-libraries.
- Debe poder usarse desde varios **repositorios** (que llamarán a la plantilla) sin duplicar lógica.
- Tiene que tener una estructura **clara, legible y fácil de mantener** (nada de código _guarro_ 💩 lleno de comentarios y completamente ilegible).
- Debe contener los siguientes stages (cada uno con sus correspondientes tareas declaradas de forma coherente):
   - Preflight
   - Build
   - Test
   - Security (Id a sección 4 para esta parte)
   - Deploy ( Id a sección 5 para esta parte)

2. **Seguridad integrada en la pipeline**

Uno de los objetivos principales de este ejercicio es comprobar que entiendes cómo **integrar seguridad de forma nativa en el pipeline**, y no como un añadido de última hora.

Tendrás que ejecutar distintos escaneos de seguridad como los que vimos la semana 3, todos ellos tan pronto como sea posible dentro de la pipeline, siguiendo el **principio de shift-left**.

Los tipos de escaneo que deberás integrar son:
- **SAST**   (Static Application Security Testing) 
-   **SCA** (Software Composition Analysis)
-   **DAST** (Dynamic Application Security Testing)
-   **IaC Scanning** (Infrastructure as Code)   
-  **Secret Scanning**    
-   **Image Scanning**

Posiblemente te preguntes que herramientas debes usar, en la [sección de herramientas](#🧭-herramientas-sugeridas-(se-admiten-otras-previa-aprobación-del-trainer)) tendrás de nuevo las que se indicaron en la semana 3, de hecho **puedes reutilizar los jobs** de la última vez, para así perder poco tiempo en estas primeras fases del ejercicio.

Esta vez los reportes que generen las herramientas tendrán que ser usados, así que ocúpate de guardarlos en algún sitio **dentro de tu pipeline**... .

Como parte de requisito de seguridad, la pipeline debe contar con **Security Gates bloqueantes**, que **bloquearán** la fase de **despliegue** de la pipeline si el proyecto que vamos a desplegar **tiene vulnerabilidades**. Tendrás que revisar como aplicar estos Security Gates para que eviten el despliegue pero **permitan subir los reportes** a la herramienta de gestión de vulnerabilidades.


3. **Despliegue e Integración de un gestor de vulnerabilidades**

Ahora si que empezamos a meterle caña al ejercicio, como has podido comprobar hasta ahora realmente el ejercicio final era reutilizar tu pipeline en formato template y hacer algún pequeño ajuste. Pero ahora si que entramos de lleno con un nuevo añadido, ya que la pipeline tendrá que subir los reportes a **DefectDojo**.

¿Qué es DefectDojo? ¡Buena pregunta para hacerle a Internet ;)!

Tendrás que preparar la pipeline para subir los reportes que generen las diferentes herramientas de escaneo.

Como es lógico para poder usar DefectDojo necesitamos que esté desplegado en nuestro cluster. Para esta parte usaremos Helm, como hicimos con ArgoCD la semana anterior. Aquí van los requisitos del despliegue de DefectDojo:

- El despliegue deberá estar **versionado en un repositorio independiente**   
- El despliegue deberá gestionarse **sí o sí con ArgoCD**.   

Todo esto no debería llevarte demasiado tiempo ya que Helm debería facilitarte bastante el despliegue.

4. **Stage Security**

Este stage solo se ocupará de lanzar las **security gates centralizadas**, si así lo determina la pipeline. 

Esto significa que **debe** existir un parámetro que permita seleccionar si la pipeline se bloqueará detrás de cada escaneo o si de lo contrario, se hará un recuento de las vulnerabilidades ya centralizadas en Defectdojo y se bloqueará justo antes de hacer el despliegue.


5. **Despliegue automático en la pipeline**

Seguramente tengas dudas de qué vamos a desplegar con nuestra plantilla de pipelines, ha llegado el momento de desvelarlo... Esta vez usaremos dos proyectos:

- Proyecto inseguro ([WebGoat](https://owasp.org/www-project-webgoat/)):
  - Proyecto con vulnerabilidades conocidas.
  - Comprobará el funcionamiento de los Security Gates.
  - **NO** conseguirá desplegarse.
- Proyecto seguro ([Spring PetClinic](https://github.com/spring-projects/spring-petclinic)):
  - No debe contener vulnerabilidades críticas.
  - Debe superar los Security Gates.
  - Debe conseguir desplegarse.

De esta forma podremos comprobar el funcionamiento real de tu pipeline en función del riesgo expuesto en las aplicaciones a integrar.

En cuanto a qué estrategia de despliegue vamos a seguir, será la siguiente:

- Proyecto Inseguro:
  - El despliegue se realiza con **Docker Compose** (si las SecGates lo permiten).
- Proyecto Seguro:
  - El despliegue se realiza con **Kubernetes en nuestro cluster local.**
  - Vuestro trainer os indicará si el despliegue tiene que estar controlado con:
    - ArgoCD: con sync automático.
    - Manual: haciendo _kubectl apply_ desde la pipeline.


### 📝 [Documentación] Tarea 1: Integración y despliegue en flujo CI/CD

Como ya viene siendo habitual el ejercicio tendrá que estar documentado correctamente, y como te puedes imaginar, esta semana no pasa desapercibida  ya que tendrás que entregar tres documentos distintos:

- **Word ejecutivo** explicando el proyecto, características, problemas encontrados y una breve conclusión el documento debe ser corto, no más de 4 páginas (lo típico que te pedirían en el cole vamos).
- **Markdown técnico**, con un nivel de detalle elevado en el que se explican los aspectos más técnicos del ejercicio, la idea es que sea complementario al Word, no repetitivo, que sino los pobres Trainers se aburren de leer lo mismo.
- **PPT** que sirva para entender el proyecto realizado, dando por hecho que el perfil de oyentes son compañeros de la Service Line, pero que no tiene porque saber algunos aspectos técnicos. El reto está en encontrar el equilibrio entre una PPT interesante, técnica y con la que **nadie** se quede dormido, es difícil pero se puede conseguir.

---

## 📂 Resumen Entregables

- ✅ Pipeline Template
- ✅ Llamada desde ambos proyectos
- ✅ Despliegue e integración de DefectDojo
- ✅ Documento Word
- ✅ Markdown Técnico
- ✅ PPT Final
---

## 🧭 Herramientas Sugeridas (se admiten otras previa aprobación del Trainer)

- **SAST**: Semgrep
- **SCA**: DependencyCheck
- **DAST**: ZAP
- **Image** **Scanning**: Trivy
- **IaC**: KICS
- **Secret Scanning**: TruffleHog


---

## 🔚 Final Checkpoint

Revisaremos:

- Correcto funcionamiento de **todo** el ejercicio.
- Que el trainee se ha convertido en una máquina DSO y sabe lo que ha hecho.
- Documentación completa y correcta.
- Capacidad de justificar las decisiones tomadas ante la atenta mirada del equipo.

