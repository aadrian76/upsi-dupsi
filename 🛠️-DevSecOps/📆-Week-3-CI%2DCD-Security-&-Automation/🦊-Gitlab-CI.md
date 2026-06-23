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
| @salamero              | 5/02/2026              | 2.0v created             |

<br>

# 🚀 GitLab CI/CD – Fundamentos de Pipelines

GitLab CI/CD es el sistema de integración y entrega continua integrado nativamente en GitLab. Permite automatizar la construcción, prueba, análisis y despliegue de aplicaciones directamente desde el repositorio.

---

## 🔎 ¿Qué es GitLab CI/CD?

GitLab CI/CD es un sistema de automatización basado en pipelines definidos mediante un archivo `.gitlab-ci.yml` ubicado en la raíz del repositorio.

Cada vez que ocurre un evento (push, merge request, tag), GitLab puede:

- Ejecutar builds
- Lanzar tests
- Ejecutar análisis de seguridad
- Publicar artefactos
- Desplegar a entornos

---

## 🧩 Componentes principales

### 📝 Pipeline

Un pipeline es la secuencia completa de tareas automatizadas que se ejecutan tras un evento.

Está compuesto por:

- Stages (etapas)
- Jobs (tareas)
- Runners (ejecutores)

---

### 📦 Stages

Son las fases del pipeline.

Ejemplo conceptual:

- build
- test
- security
- deploy

Las stages se ejecutan en orden.

---

### ⚙ Jobs

Son las tareas individuales que se ejecutan dentro de cada stage.

Cada job:
- Se ejecuta en un runner.
- Puede generar artefactos.
- Puede depender de otros jobs.

---

### 🖥 GitLab Runners

Son los agentes que ejecutan los jobs.

Tipos:
- Shared runners (gestionados por GitLab)
- Self-hosted runners (gestionados por la organización)

---

## 🔐 GitLab CI/CD en DevSecOps

GitLab destaca porque integra capacidades de seguridad nativas:

- SAST
- DAST
- Dependency Scanning
- Container Scanning
- Secret Detection

Esto permite construir pipelines DevSecOps sin depender exclusivamente de herramientas externas.

---

## 📚 Recursos oficiales

📘 Documentación oficial:
https://docs.gitlab.com/ee/ci/

🎥 Video introductorio:
https://www.youtube.com/watch?v=PGyhBwLyK2U

🎥 GitLab CI/CD explicado:
https://www.youtube.com/watch?v=4UoBvXlYdD0

---

## 📌 Puntos clave

- GitLab CI/CD está integrado en la plataforma.
- Se basa en archivo declarativo YAML.
- Permite pipelines complejos y escalables.
- Integra herramientas de seguridad nativas.
- Ideal para entornos DevSecOps integrados.
