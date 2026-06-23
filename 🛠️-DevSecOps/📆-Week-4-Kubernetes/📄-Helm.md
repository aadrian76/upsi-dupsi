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
| @Alvaro                  | 09/01/2025              | First Version Created                         |

<br>

---


## Introducción

[Helm](https://helm.sh/docs/) es un gestor de paquetes para Kubernetes que nos permite definir, instalar y actualizar nuestras aplicaciones en un Cluster de forma sencilla y reproducible.

## 🧩 Conceptos clave de Helm

### 📦 **Chart**

Es un **paquete de Helm**.  
Contiene todo lo necesario para desplegar una app:
*   Manifests de Kubernetes (YAML)
    
*   Templates
    
*   Valores configurables (`values.yaml`)
    
*   Metadatos
    
Ejemplo: un chart para desplegar **una app + base de datos + servicios + ingress**.

Normalmente podemos crear varios `values.yaml` para que, en función del entorno en el que estemos haciendo el despliegue se apliquen unas configuraciones u otras.
