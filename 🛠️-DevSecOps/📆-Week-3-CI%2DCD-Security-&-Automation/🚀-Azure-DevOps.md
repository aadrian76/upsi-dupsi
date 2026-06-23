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

# ☁ Azure DevOps Pipelines – CI/CD en entornos Enterprise

Azure DevOps Pipelines es el sistema de integración y entrega continua de Microsoft, diseñado para entornos empresariales y ecosistemas híbridos (on-premise + cloud).

---

## 🔎 ¿Qué es Azure Pipelines?

Azure Pipelines permite automatizar:

- Builds
- Testing
- Análisis de código
- Despliegues
- Infraestructura como Código

Puede trabajar con:

- GitHub
- Azure Repos
- Repositorios externos


## 🧩 Componentes principales

### 📝 Pipeline

Un pipeline define el proceso automatizado de construcción y despliegue.

Puede configurarse:

- Desde interfaz gráfica (Classic)
- Mediante YAML (recomendado)


### 🏗 Stages

Representan fases del ciclo de vida:

- Build
- Test
- Deploy (Dev, QA, Prod)

Permiten definir aprobaciones manuales y gates.


### 🖥 Agents

Son los ejecutores del pipeline.

Tipos:
- Microsoft-hosted agents
- Self-hosted agents



### 📦 Artifacts

Permiten almacenar resultados del build para usarlos en despliegues posteriores.


## 🔐 Azure Pipelines en DevSecOps

Azure DevOps se integra con:

- Microsoft Defender for Cloud
- SonarQube
- Escaneo de dependencias
- Control de políticas
- Aprobaciones y gates

Es fuerte en:

- Compliance
- Gobernanza
- Control de accesos (RBAC)
- Integración con entornos corporativos



## 📚 Recursos oficiales

📘 Documentación oficial:
https://learn.microsoft.com/en-us/azure/devops/pipelines/

🎥 Introducción a Azure Pipelines:
https://www.youtube.com/watch?v=0m75Z4YhZz8

🎥 Azure DevOps para CI/CD:
https://www.youtube.com/watch?v=YgCDBqj2g9k


## 📌 Puntos clave

- Enfocado a entornos enterprise.
- Integración fuerte con ecosistema Microsoft.
- Control avanzado de permisos y gobernanza.
- Compatible con multi-cloud y entornos híbridos.
- Muy utilizado en organizaciones grandes.
