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
| @Alvaro Salamero                  | 07/01/2025              | Completed Week 4 - Pending Review    |

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


Por fin sabes lo que es una pipeline!! ¿Quieres un pin? Seguramente te crees expert@ en DSO. Sin embargo las cosas no se van a poner más fáciles ahora...

Bienvenid@ al inferno de Kubernetes (conocido como K8s) donde para el final de la semana deberías ser capaz de desplegar una pequeña aplicación (si consigues evitar el CrashLoopBackOff).

Durante esta semana cubriremos:

- **Fundamentos de Kubernertes:** Qué es, cómo funciona y porqué te duele la cabeza cuando acabas los despliegues.
- **Seguridad en Kubernetes:** ¡Sorpresa! Aquí también hay que asegurarse de que todo cumple con unos requisitos de seguridad, si no luego aparece un despliegue que está levantado como root y nadie sabe qué ha pasado.
- **ArgoCD:** Qué es y para qué nos sirve.

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

Una vez más antes de ponernos manos a la obra con la parte práctica, necesitaremos tener algunos conocimientos teóricos en mente para que el ejercicio no se atragante demasiado:

- **Kubernetes** - Qué es y cómo funciona
    - **Arquitectura** de un cluster
    - **Componentes** (Deployments, Services, PVC,  etc.)
    - Opcional: Deployment vs StateFulSet (**Obligatorio** si eres **New Hire**)
    - Comandos asociados a K8s para trabajar sobre la terminal
- **Minikube** - Qué es y en qué entornos se debe utilizar
- **ArgoCD** - Qué es y cómo funciona
- **Seguridad** en Kubernetes
    - ConfigMaps, Secrets, **Sealed secrets**
    - Seguridad dentro de los pods, deployments, etc.





## 🛠 Ejercicios Prácticos

### 🎯 Tarea 1: Hello Minikube
Como parte del checkpoint inicial, tendrás que completar los tutoriales iniciales de la [documentación oficial de Kubernetes](https://kubernetes.io/es/docs/tutorials/hello-minikube/).
Sobre dicho ejercicios se realizarán una serie de "pruebas" en el checkpoint.

### 🎯 Tarea 2: Despliegue SpringPetClinic en cluster local
Tras el checkpoint, el ejercicio a realizar consiste en reutilizar la imagen optimizada de SpringPetClinic que construimos y analizamos en la semana 2. Con dicha imagen realizaremos un nuevo despliegue en un cluster local (**minikube**), pero esta vez en vez de docker compose, usaremos Kubernetes.

Por lo tanto el principal objetivo de la semana es _Kubernetizar_ SpringPetClinic para que sea operativo y persistente (deberías saber a que nos referimos con eso de persistente). También necesitaremos una base de datos funcional que nos permita **guardar nuevos usuarios** y controlar de forma correcta el **RBAC**.

Además el manejo de secretos y configuraciones de la aplicación y base de datos tendrá que estar bien gestionado, evitando exponer claves y/o datos sensibles.

El servicio debe estar expuesto a Internet, para ello contamos con dos opciones:

1. Expose de kubernetes por terminal eligiendo el formato adecuado para nuestro _Use Case_ (Opción Recomendada)
2. Configurar un proxy inverso (como NGINX) que simule una forma de exponer una aplicación realista y que podríamos encontrar en un caso real (este objetivo es **opcional** para los becarios, y por lo tanto **solo** se realizará previo OK del Trainer, los **New Hires** tienen que usar esta opción como obligatoria).


### 📝 [Documentación] Tarea 2: Despliegue SpringPetClinic en cluster local

- Markdown: Documentación técnica con todos los comandos utilizados y guía paso a paso para replicar el ejercicio. Incluir sección específica de medidas de seguridad aplicadas en las configuraciones y sección de troubleshooting con problemas encontrados y cómo se han resuelto.

---
### 🎯 Tarea 3 (Opcional): Integrar nuestra aplicación en flujo GitOps
Hasta aquí llega el mínimo que se debe lograr para el final de la semana 4, pero para los más atrevidos tenemos una segunda parte, ¿recordáis el concepto de ArgoCD que (sin duda 🤦) habéis leído en la parte teórica? ¡Estupendo! es el momento de ponerlo en práctica.

1. Desplegar en local usando _helm install_ ArgoCD en vuestro cluster.
2. Crear un repositorio en la plataforma DevOps/control de código que hayáis usado en la semana 3 (Gitlab, Azure, Github), subir los manifests de Kubernestes y configurar la conexión del repo con ArgoCD.
3. Finalmente el objetivo sería poder aplicar cambios sobre nuestro cluster de forma sencilla, a través de los commits que se realicen en el repositorio que contiene los manifests y sincronizando desde la interfaz de ArgoCD.

⚠️ **Disclaimer**: Este objetivo es bastante ambicioso para lograrse en una semana, no se espera que se alcance en su totalidad.


---

## 📂 Resumen Entregables

- ✅ Ejercicio Documentación-> MidWeek Checkpoint
- ✅ Aplicación SpringPetClinic -> Final
    - Manifest app
    - Manifest DB
    - Manejo información sensible
    - Expuesto a Internet
- ✅ Documentación Técnica -> Final
- ✅ Integración con ArgoCd -> Final (Opcional)
   - Despliegue de ArgoCD
   - Configuración repositorio
   - Sincronización automática

---

## 🧭 Herramientas Sugeridas (se admiten otras previa aprobación del Trainer)

No aplica

---

## 🔚 Final Checkpoint

Revisaremos:

- Correcto funcionamiento de **todo** el ejercicio.
- Que el trainee ha entendido cómo funciona Kubernetes y sabe lo que ha hecho.
- Documentación completa y correcta.
