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
| @alvaro                       | 20/10/2025              | Week 2 — Containers, Hardening & Scanning     |
| @Alvaro Salamero                  | 07/01/2025              | Completed Week 2 - Pending  Review   |

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

Has sobrevivido a la primera semana, no está mal ... pero no te acomodes porque de ahora en adelante las cosas se empiezan a poner un poco más complicadas.

Esta va a ser tu primera semana de conceptos DSO (apréndete las siglas que las vas a usar mucho...). Vamos a adentrarnos en la contenerización y securización de aplicaciones, así como en el escaneo de vulnerabilidades. La seguridad no solo es arreglar lo que está roto, si no evitar que las cosas se rompan.

Cubriremos:
- **Contenedores y Docker**: Qué son, cómo funcionan.
- **Optimización y hardenización de contenedores**: Mejores prácticas para minimizar la superficie de ataque de nuestros contenedores.
- **Escaneo de Imágenes**: Identificar vulnerabilidades antes de que sean atacadas en producción.
- **Supply Chain Security**: Recuerda que tus dependencias también son tu problema aunque no las hayas desarrollado tú.

Cuando termine la semana deberías ser capaz de asegurar y analizar un entorno contenerizado correctamente por tu cuenta.

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

Antes de nada asegúrate de haber leído la página de las fases:
👉 **[📚 Fases](/✏️-Guía-del-Training/📚-Fases)**

Si te la saltaste, léetela, no vamos a repetirlo aquí, de esa forma podrás entender las siguientes secciones :

- **Checkpoints & Expectations** (no nos preguntes)
- **How to approach exercises** (no nos preguntes)

Si haces alguna pregunta sobre algo que está **claramente explicado ahí**, es muy probable que no te contestemos.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
<b>☝️🥸 Google existe.</b> Si te bloqueas, úsalo. Si sigues bloqueado, pregúntale a tu trainer.
</div>

## 📌 Week Structure

Independientemente de que seas un Intern o New Hire, lo que haremos a lo largo de la semana será:
- Aprender los Conceptos fundamentales
- Aplicar los conceptos sobre tareas guiadas.
- Demostrar la adquisición de conocimientos en los entregables y "defensas" que se realicen.

La diferencia radica en el nivel de ayuda y profundidad que se pedirá en cada caso.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Tip. </b>No necesitas memorizar antes de empezar con la parte práctica. Si algún tema está directamente relacionado con la tarea, puedes ir aprendiendo sobre la marcha, es la mejor manera de aprender. 
</div>

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>✍️ Toma notas.</b> No te dediques solo a leer. <b>Escribe cosas con tus propias palabras.</b> Te ayudará a recordar mejor los conceptos.
</div>



---

## 🧱 Conceptos fundamentales

Para cuando abras por primera vez un Dockerfile, deberías entender todos estos conceptos sin pasar por Google:

- **[Docker](/🛠️-DevSecOps/📆-Week-2--DevSecOps-&-Containers/📄-Docker)**
- **Arquitectura y Seguridad en Docker**: cómo funciona internamente Docker, cómo podemos mantener nuestros contenedores seguros y qué riesgos podemos encontrar.
- **Contenedor vs VM**: namespaces, cgroups, union filesystems (AUFS/overlay2), imágenes OCI y capas
- **Imágenes**: imágenes base, layering, multi-stage builds, `.dockerignore`
- **Seguridad en tiempo de ejecución**: Linux capabilities, seccomp, AppArmor/SELinux, sistema de archivos de solo lectura, user namespaces, rootless
- **Redes**: bridge vs host vs none, puertos publicados, este–oeste vs norte–sur
- **Secretos**: nunca hardcode; usar inyección en tiempo de ejecución (Docker secrets, variables de entorno + almacenes de secretos externos)
- **Cadena de suministro**: SBOM (SPDX/CycloneDX), bases de datos de vulnerabilidades, firmado y procedencia de imágenes (Sigstore Cosign, SLSA), gestión de dependencias (Renovate/Dependabot)
- **Enfoques de análisis**: análisis de imágenes (SO + dependencias del lenguaje), linting de configuración (buenas prácticas de Dockerfile), riesgo en tiempo de ejecución (privileged, capabilities)

---

## 🛠 Ejercicios Prácticos

El ejercicio de esta semana se centra en Docker **(DOCKER CLI, NADA DE DOCKER DESKTOP)**, lo que haremos será crear, optimizar y securizar un Dockerfile.

### 🎯 Tarea 1: Dockerfile Inicial

El primer paso es crear un **Dockerfile** que despliegue una aplicación web, nosotros recomendamos usar Spring PetClinic, pero se pueden considerar otras opciones. El principal objetivo es aplicar prácticas de seguridad a la hora de declarar el Dockerfile. También tendrás que tener en cuenta el uso de técnicas de optimización.
### 🎯 Tarea 2: Despliegue en Docker 
Cuando tengas una imagen funcional, tendrás que hacer el despliegue con y sin **Docker Compose**. Ten en cuenta la persistencia de los datos si es necesario. Comprueba que tu contenedor es accesible y que todo está correctamente configurado antes de presentarlo.
### 📝 [Documentación] - Tareas 1 & 2: Dockerfile y Despliegue
El siguiente paso será crear un archivo **MARKDOWN** a modo de guía técnica de como has hecho el ejercicio paso a paso, proporcionando justificación para las decisiones tomadas. Incluye dos secciones separadas para profundizar sobre las técnicas de securización y optimización que has aplicado.
### 🎯 Tarea 3: Auditar la imagen
Posteriormente la segunda fase del ejercicio será escanear tu "creación". Para ello haremos escaneo en tiempo de ejecución y _linting_ de tu Dockerfile.

Con los resultados obtenidos nos presentarás un informe en un Word (siguiendo las plantillas y el formato de Accenture) con las vulnerabilidades encontradas por las herramientas. Aplicarás las correcciones que consideres necesarias y harás un reescaneo para asegurar que tu contenedor está listo para pasar a producción ;).

### 📝 Documentación Final
Con todo el ejercicio finalizado tendrás que crear un Word (siguiendo el template que encontrarás en _Cloud & Application Security Iberia/ [General] Principal / Shared /00 Templates_) explicando el ejercicio de forma _ejecutiva_, donde la has liado y los distintos fallos y problemas que hayas tenido, así como la resolución de los mismos.

También tendrás que **corregir** y **completar** el Markdown con la guía de cómo realizaste la sección de auditar la imagen.

---

## 📂 Deliverables Summary

| **Item**                           | **Interns**                          | **New Hires**               |
|-----------------------------------|--------------------------------------|-----------------------------|
| Dockerfile Hardenizado               | ✅ Midweek                            | ✅ Final                     |
| Lint & Hardening Markdown          | ✅ Midweek                            | ✅ Final                     |
| Image Scan Reports (2 tools)      | ✅ Midweek                            | ✅ Final                     |
| Dockerfile Corregido                    | ✅ Final                              | ✅ Final                     |
| Markdown Corregido                    | ✅ Final                              | ✅ Final                     |
| Documento Word Completo     | ✅ Final                              | ✅ Final                                   |

---

## 🧭 Suggested Tools (choose equivalents if you must)

- **Linting/Best Practices**: [KICS](https://docs.kics.io/latest/)
- **Vuln Scanners**: [Trivy](https://trivy.dev/docs/latest/guide/)


---

## 🔚 Final Checkpoint

Revisaremos:

- **Artefacto Construido** ( imagen, configuración, contenedor)
- **Documentación** ( Estructura, consistencia, nivel de detalle)
- **Comprensión del temario** (Preguntas sobre los conceptos vistos)

