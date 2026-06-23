<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenido
    </summary>
  
  [[_TOC_]]
</details>

# Capítulo 4: Responsabilidad y Riesgo Compartido

## ✅ Modelo de Responsabilidad Compartida
Es un marco de seguridad y gestión de riesgos en entornos de computación en la nube que define qué aspectos de la seguridad y del cumplimiento corresponden al proveedor de la nube (CSP) y cuáles corresponden al cliente o usuario del servicio. No significa que ambos compartan la responsabilidad sobre los mismos elementos, sino que cada uno tiene su ámbito de control y obligaciones claras para asegurar el entorno cloud en conjunto.

## ✅ División de responsabilidades
La división de responsabilidades depende del modelo de servicio:

### Infrastructure as a Service (IaaS):

**Proveedor:** Seguridad física, redes, virtualización.

**Cliente:** Sistemas operativos, parches, configuraciones, aplicaciones, datos, IAM.

### Platform as a Service (PaaS)
**Proveedor:** Además de lo anterior, gestiona el sistema operativo y plataformas de ejecución.
    
**Cliente:** Código de la app, datos, accesos y configuraciones.

### Software as a Service (SaaS):
**Proveedor:** Gestiona la aplicación, plataforma e infraestructura.
    
**Cliente:** Gestión de usuarios, permisos, políticas de uso de datos y cumplimiento.

## ✅ Comparativa Resumida
| Componente | IaaS | PaaS | SaaS |
| --- | --- | --- | --- |
| Infraestructura física | CSP | CSP | CSP |
| Sistema operativo | Cliente | CSP | CSP |
| Aplicación | Cliente | Cliente | CSP |
| Datos | Cliente | Cliente | Cliente |
| IAM | Cliente | Cliente | Cliente |
