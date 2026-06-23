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

# 🐙 GitHub Actions – CI/CD Integrado en GitHub

GitHub Actions es la solución de CI/CD integrada en GitHub. Permite automatizar flujos de trabajo directamente desde el repositorio.

## 🔎 ¿Qué es GitHub Actions?

Es un sistema basado en workflows definidos en archivos YAML dentro del directorio `.github/workflows/`.

Se activa por eventos como:

- Push
- Pull request
- Release
- Schedule
- Manual trigger


## 🧩 Componentes principales

### 📝 Workflow

Define el flujo completo de automatización.

Incluye:
- Eventos (triggers)
- Jobs
- Steps

### ⚙ Jobs

Agrupan pasos relacionados.

Pueden ejecutarse:
- En paralelo
- Secuencialmente
- En distintos entornos

### 🔄 Steps

Son las acciones individuales dentro de un job.

Pueden:
- Ejecutar comandos
- Usar acciones preconstruidas del marketplace

### 🖥 Runners

Son las máquinas que ejecutan los workflows.

Tipos:
- GitHub-hosted runners
- Self-hosted runners


## 🔐 GitHub Actions en DevSecOps

GitHub integra:

- Dependabot (gestión de dependencias)
- Code scanning (CodeQL)
- Secret scanning
- Container scanning

Además permite integrar herramientas externas fácilmente.

Es muy potente en:
- Open Source
- Integraciones rápidas
- Ecosistema amplio (Marketplace)

## 📚 Recursos oficiales

📘 Documentación oficial:
https://docs.github.com/en/actions

🎥 GitHub Actions explicado:
https://www.youtube.com/watch?v=R8_veQiYBjI

🎥 DevSecOps con GitHub:
https://www.youtube.com/watch?v=4nP8nNfKjCk


## 📌 Puntos clave

- Integración nativa en GitHub.
- Configuración simple y declarativa.
- Gran ecosistema de acciones reutilizables.
- Fuerte integración con seguridad (Dependabot, CodeQL).
- Muy popular en proyectos Open Source y startups.
