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


## 🏗️ Shared-Libraries

Una Shared-Library en el contexto de las pipelines es una **librería centralizada** que contiene toda la **lógica** de trabajo CI/CD que aplicamos sobre **múltiples proyectos**. Con el fin de que todos ellos cuenten con una serie de **stages, tasks y jobs comunes** para evitar **duplicación** de código, **estandarizar** procesos y facilitar el **mantenimiento**.

El uso de este tipo de librerías centralizadas nos permite hacer una única definición de todos los procesos que se van a realizar en nuestras pipelines, de tal forma que desde cada proyecto se importará la plantilla especificando que jobs se deben ejecutar en cada caso.

### 🧠 Beneficios Clave
- **Reutilizar** **código**: Si tenemos que modificar algún fichero, dicha modificación tiene efecto directo en todos los proyectos que usan la librería.
- **Consistencia**: Al hacer una definición común, es más sencillo que todos los proyectos realicen de forma correcta todos los pasos definidos, sin gran esfuerzo.
- **Escalabilidad**: Facilita la propagación de sistemas CI/CD en proyectos con numerosos repositorios.

### 🛠 Diseño

Este tipo de plantillas se definen en un repositorio cuya única finalidad es **mantener** y **mejorar** la librería, normalmente se crea una estructura robusta de **archivos yaml** de configuración que luego se pueden importar desde el fichero central de "creación" de la pipeline.

Luego desde cada repositorio que queremos **integrar en un flujo CI/CD** llamamos al repositorio que contiene las plantillas para incluir aquellos stages y jobs que necesitemos en cada caso.

Este proceso no es exactamente igual en todos los entornos CI/CD, y la forma de importar las plantillas tiene una pequeña variación en función de la tecnología concreta:

**Azure DevOps**

![image.png](/.attachments/image-4b5a0f7a-4b3c-41ab-bb13-ec2642741e38.png)

**GitlabCI**

![image.png](/.attachments/image-25394807-28e9-406c-885c-1fe5fb6c57b3.png)

### ⭐ Conclusión

Las Shared-Libraries son estructuras de templates que facilitan la integración del ciclo CI/CD en múltiples repositorios de forma unificada, consiguiendo así un estándar en cuanto a procesos de construcción, testing y seguridad.



 



