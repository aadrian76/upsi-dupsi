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
| @Alvaro Salamero                  | 13/02/2026              | Empezando Docker ARea|

<br>

---

# 🐳 Fundamentos de Docker

Docker es una tecnología clave en DevOps y DevSecOps. Permite empaquetar aplicaciones y sus dependencias en **contenedores**, logrando consistencia entre entornos (local, QA, producción) y facilitando la automatización en pipelines CI/CD.

## 📦 ¿Qué es [Docker](https://docs.docker.com/get-started/overview/)?

Docker es una plataforma de **contenerización** que permite crear, ejecutar y distribuir aplicaciones en [contenedores](https://www.docker.com/resources/what-container/).

Un **contenedor** es una unidad de ejecución **ligera y portable** que:
- Incluye la aplicación y sus dependencias.
- Aísla procesos y parte del filesystem.
- Comparte el kernel del sistema operativo del host (no es una VM completa).
- Es reproducible y fácil de versionar (mediante imágenes).

### 🧠 ¿Por qué Docker es importante?

Antes de Docker era común:
- “En mi máquina funciona” por diferencias de entorno.
- Configuración manual y **no reproducible**.
- Dificultad para **escalar** o replicar entornos.

Con Docker:
- Entornos **reproducibles**.
- Despliegues más **rápidos y consistentes.**
- Portabilidad (Dev → QA → Prod).
- Base de arquitecturas Cloud Native y orquestación con Kubernetes.
---

## 🧩 ¿Qué es [Docker Compose?](https://docs.docker.com/compose/)

Docker Compose es una herramienta para definir y ejecutar **aplicaciones multi-contenedor** usando un archivo de configuración (normalmente `docker-compose.yml`).

Se usa especialmente en:
- Desarrollo local.
- Laboratorios y formación.
- Pruebas de integración.
- Orquestación sencilla (no producción a gran escala).

Con Compose puedes definir:
- Servicios (contenedores).
- Redes.
- Volúmenes.
- Variables de entorno.
- Dependencias entre servicios (orden lógico de arranque).

> Nota: Compose no sustituye a un orquestador como Kubernetes en producción, pero es ideal para escenarios locales o educativos.

---
## 🏗 Componentes principales de Docker

Docker se compone de varios elementos que trabajan en conjunto para construir imágenes, ejecutar contenedores y distribuir artefactos.


### ⚙ Docker Engine

Es el núcleo de Docker y el componente que realmente “hace el trabajo”.

Se encarga de:
- Construir imágenes.
- Ejecutar contenedores.
- Gestionar redes y conectividad.
- Gestionar volúmenes y persistencia.
- Exponer una API para operar Docker de forma programática.

En términos prácticos: si Docker “corre”, es porque el Engine está funcionando.



### 💻 Docker Client

Es la interfaz con la que interactúa el usuario (normalmente mediante CLI).

El cliente:
- Envía órdenes al Docker Engine a través de la API.
- Permite ejecutar las operaciones habituales (construir, correr, listar, parar, etc.).

En términos simples: el Client es “lo que tú usas”; el Engine es “lo que ejecuta”.



### 🖼 Docker Images y Containers

#### Docker Image (Imagen)

Una imagen es una plantilla inmutable que contiene:
- La aplicación.
- Librerías y dependencias.
- Configuración necesaria para ejecutarse.

Características clave:
- Inmutable y versionable.
- Basada en capas (layers), lo que optimiza almacenamiento y distribución.
- Se puede publicar y descargar desde un registry.

Las imágenes suelen construirse desde un `Dockerfile`, que define cómo empaquetar la app.

#### Docker Container (Contenedor)

Un contenedor es una **instancia en ejecución** de una imagen.

Relación conceptual:
- Imagen → “plantilla”
- Contenedor → “proceso en ejecución”

Un contenedor:
- Está aislado (a nivel de proceso y recursos).
- Puede ser efímero (se crea y destruye con facilidad).
- Puede conectarse a redes y usar volúmenes para persistencia.



### 🌍 Docker Registries

Un Docker Registry es un repositorio donde se almacenan y distribuyen imágenes.

Tipos:
- Públicos (ej.: Docker Hub, GitHub Container Registry).
- Privados (ej.: Azure Container Registry, Amazon ECR, Harbor).

Un registry es clave para:
- Compartir imágenes entre equipos y entornos.
- Controlar versiones (tags).
- Establecer políticas de acceso y autenticación.
- Soportar procesos de seguridad (escaneo, firmas, trazabilidad).

---

## 🔐 Docker en el contexto DevSecOps

Docker no es solo “empaquetar y correr”. En DevSecOps se convierte en un punto central de control de seguridad.

Aspectos a tener en cuenta:
- Selección segura de imágenes base (evitar imágenes obsoletas o no mantenidas).
- Escaneo de vulnerabilidades en imágenes y dependencias.
- Gestión correcta de secretos (no embebidos en imágenes ni expuestos en variables sin control).
- Hardening del contenedor (mínimos permisos, usuario no root, filesystem read-only cuando aplique).
- Reducción de superficie de ataque (imágenes mínimas, paquetes estrictamente necesarios).
- Principio de menor privilegio y controles en runtime.

> Un contenedor mal configurado puede ser tan inseguro como un servidor tradicional.

---

## 📌 TL;DR

- Docker permite ejecutar aplicaciones en contenedores portables.
- Docker Compose facilita levantar stacks multi-contenedor (ideal en local/labs).
- Docker Engine es el backend que construye y ejecuta.
- Docker Client es la interfaz (CLI) para operar Docker.
- Imágenes = plantillas inmutables versionadas.
- Contenedores = instancias en ejecución de imágenes.
- Registries = repositorios para almacenar y distribuir imágenes.
- En DevSecOps, la seguridad de contenedores y supply chain es parte del pipeline.
