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


## 🌐 Introducción

Un **cluster de Kubernetes (k8s)** es un **conjunto de máquinas (nodos) que trabajan juntas para ejecutar y administrar aplicaciones en contenedores**, coordinadas por **Kubernetes**.

### ¿Qué lo compone?

Un cluster de k8s se divide en dos grandes partes:

#### 🧠 Control Plane (plano de control)

Es el “cerebro” del cluster. Se encarga de:
*   Decidir **dónde** se ejecutan los contenedores
    
*   Mantener el **estado deseado** del sistema
    
*   Gestionar escalado, actualizaciones y fallos
    
Componentes clave:
*   **API Server**
    
*   **Scheduler**
    
*   **Controller Manager**
    
*   **etcd** (base de datos del estado del cluster)
    

#### 💪 Worker Nodes (nodos de trabajo)

Son las máquinas que **ejecutan las aplicaciones**.  
En cada nodo hay:
*   **Pods** (uno o más contenedores)
    
*   **kubelet** (agente del nodo)
    
*   **container runtime** (Docker, containerd, etc.)
    
*   **kube-proxy** (red)
    

### ¿Para qué sirve un cluster de k8s?

*   🚀 Desplegar aplicaciones de forma automática
    
*   📈 Escalar contenedores según demanda
    
*   🔁 Reiniciar servicios si fallan
    
*   🔄 Hacer actualizaciones sin downtime
    
*   🌐 Gestionar red y balanceo de carga


## ¿Qué es Iluvatar?

Quizás lo hayas visto u oído en alguna reunión, pero todavía no sabes lo que es. Es **NUESTRO CLUSTER** de Kubernetes, y tenemos mucha documentación sobre su arquitectura y cómo conectarse al mismo.

Dejo por aquí algunos enlaces:

- [Arquitectura de Iluvatar](https://dev.azure.com/Yggdrasil-Infrastructure/One%20Yggdrasil/_wiki/wikis/One%20Yggdrasil/1089/Cluster-Arquitecture-Diagram)
- [Acceso al Cluster](https://dev.azure.com/Yggdrasil-Infrastructure/One%20Yggdrasil/_wiki/wikis/One%20Yggdrasil/1133/Access-to-the-Cluster)



