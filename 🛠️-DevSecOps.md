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
| @<C73C5218-17C3-6B53-B15D-E321D12689EB>                  | 14/02/2025              | First Version Created             |
| @salamero              | 5/02/2026              | 2.0v created             |

<br>

---



<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b style="color:#7C3AED; font-size: 17px;">🚨 EMPIEZA POR AQUÍ</b>
    <br><br>
    DevSecOps es solo DevOps… hasta que la seguridad llega <B>demasiado tarde</b>.
    <br><br>
    Desplegar rápido está bien. Desplegar <b>vulnerable</b>, no.
    <br><br>
    -<i>DevSecOps no existe son los padres</i>- Esta frase es bastante habitual, la gente dice que es solo otra forma de llamar al tradicional DevOps, sin embargo en ese tipo de equipos la seguridad suele llegar como Ryanair ✈️  <b>mal y tarde</b>.
  <br><br>
Desplegar rápido y ágil está bien, pero si por ello desplegamos componentes vulnerables, entonces es una <b>mi*rda</b>.

</div>


¿Un secreto hardcodeado? = **Credenciales expuestas**
  
¿Una dependencia sin escanear? = **Compromiso de la cadena de suministro**  

¿Un pipeline sin controles? = **Entornos productivos expuestos**

DevSecOps no trata de frenar a los desarrolladores. Trata de **detectar los problemas antes de que lleguen a producción**. Si tu seguridad empieza cuando ya hay un incidente, **ya vas tarde**.

Bienvenid@ al mejor suboffering de todo CAS 🤘 (algunos diremos que es el mejor de SDC)

En este Training vamos a aprender a:

- Integrar seguridad en **CI/CD**.
- Detectar **vulnerabilidades** desde el código.
- Proteger **secretos y dependencias**.
- **Automatizar** controles de seguridad.
- Evitar que código inseguro llegue a **producción**.

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ IMPORTANTE</span></b>
    <br><br>
Si tienes algún problema o necesitas ayuda, es <b>muy importante</b> que mires <b><a href="https://dev.azure.com/Cloud-Application-Security/Training%20Path/_wiki/wikis/Training%20Path/106/%F0%9F%94%B0-Visi%C3%B3n-General?anchor=%C2%BFc%C3%B3mo-preguntar-un-problema-o-pedir-ayuda%3F">esta sección</a></b> donde se explica como hacerlo.
</div>

# 🎯 Resumen
  
DevSecOps consiste en **integrar la seguridad en todo el ciclo de vida del desarrollo**, no en añadirla como un paso final.

Una estrategia sólida de DevSecOps asegura que:

- La seguridad se valida desde el primer commit.
- Los pipelines bloquean código inseguro automáticamente. 
- Los secretos no viven en repositorios ni variables sin control.  
- Las dependencias y contenedores se analizan continuamente.

Una mala estrategia de DevSecOps significa que:

- La seguridad es manual y opcional.  
- Los pipelines solo validan que “compile”.  
- Las vulnerabilidades se descubren en producción.  
- Cada despliegue es una apuesta.


## 🔑 Áreas clave
Si “confías en que todo está bien”, asume que no lo está.

 DevSecOps cubre:

🧩 **Seguridad en el código (Shift Left):** Detecta vulnerabilidades antes de que el cambio **ya esté en producción**.


🔐 **Gestión de secretos:** Un secreto expuesto es una **brecha** esperando ocurrir.


📦 **Seguridad en dependencias y contenedores:** Tu código es tan seguro como lo más **débil** que importas


⚙️ **Pipelines seguros:** Si el pipeline **no bloquea**, no protege.


🤖 **Automatización de seguridad:** La única forma de escalar sin frenar al equipo.

# 🔎 Contenido Semanal

Como habrás podido observar este Training consta de 5 semanas en las que te convertirás en un experto de la seguridad en la nube y en las aplicaciones (CAS).

A lo largo de cada semana cubriremos:

- **[Week 1](/🛠️-DevSecOps/📆-Week-1-CAS-Core)**: Esta semana cubre los conceptos fundamentales de CAS, con aspectos más genéricos de aplicaciones y arquitectura y conceptos importantes de seguridad.
- **[Week 2](/🛠️-DevSecOps/📆-Week-2--DevSecOps-&-Containers)**: Esta semana comienza fuerte introduciendo conceptos de DevSecOps y definiendo el concepto de contenedores.
- **[Week 3](/🛠️-DevSecOps/📆-Week-3-CI%2DCD-Security-&-Automation)**: Aquí nos metemos de lleno en el concepto de las pipelines y los ciclos CI/CD. Ahora todo te suena a chino, pero llegaremos a ello ;).
- **[Week 4](/🛠️-DevSecOps/📆-Week-4-Kubernetes)**: Si la semana pasada sonó a chino, esto es un idioma inventado... Se trata de Kubernetes, aquí veremos como desplegar aplicaciones en un cluster (menudo palabro acabo de soltar) y como siempre como securizarlo.
- **[Week 5](/🛠️-DevSecOps/📆-Week-5-Final-Project-\(Explained\))**: Esta semana es temida y amada a partes iguales, en ella pondrás en práctica todo lo aprendido durante el mes de training que deberías llevar... Cuando leas el enunciado igual te da un micro infarto (aunque si has ido aprendiendo a lo largo del mes, estará chupao).



