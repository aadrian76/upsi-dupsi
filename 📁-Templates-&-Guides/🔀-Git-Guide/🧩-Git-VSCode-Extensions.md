<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de Contenidos
    </summary>

  [[_TOC_]]
</details>

## 📝 Changelog

<br>

| Autor                             | Fecha de Modificación   | Cambios                                       |
|-----------------------------------|-------------------------|-----------------------------------------------|
| Tsesmelis Villaverde, Olaya Europa                  | 09/06/2025              | Primera versión creada                        |

<br>

---

<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b><span style="color:#7C3AED; font-size: 17px;">🚨 ANTES DE EMPEZAR</span></b>
    <br><br>
    Esta página asume que ya tienes Git instalado y sabes lo básico. Si no, empieza por <b>Git CLI</b> primero.
    <br><br>
    <span style="color:#7C3AED;"><b>Aquí no vas a tocar la terminal. Todo lo que ves en Git CLI se puede hacer desde VSCode, y esta página te enseña cómo.</b></span>
</div>

VSCode tiene integración nativa con Git, pero con las extensiones adecuadas se convierte en algo bastante más potente. Esta página cubre las tres que usamos y cómo sacarles partido.

- Cómo instalar y usar **GitLens**
- Cómo visualizar el historial con **Git Graph**
- Cómo explorar el historial de archivos con **Git History**
- Cómo escribir **Conventional Commits** desde la interfaz

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🔌 Instalación

Las tres extensiones se instalan desde el marketplace de VSCode. Abre el panel de extensiones con `Ctrl+Shift+X`, busca cada una y dale a instalar.

| Extensión | Autor | Para qué sirve |
|---|---|---|
| **GitLens** | GitKraken | Información de autoría, historial y commits desde el editor |
| **Git Graph** | mhutchie | Visualización gráfica de ramas y commits |
| **Git History** | Don Jayamanne | Historial de archivos y comparación de commits |

<div style="text-align: left; margin: 0; display: inline-block; width: fit-content;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/Extensiones-6b5a2951-7773-42de-b51b-d819465a33cd.png" style="border: 2px solid lightgray; max-width: 100%; height: auto; display: block;" alt="Panel de Source Control">
    <div style="color: gray; font-size: small; font-style: italic; text-align: center;">Las tres extensiones en el marketplace de VSCode</div>
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📦 Source Control: el panel de Git en VSCode

Antes de entrar en las extensiones, el panel de  Source Control es el punto de partida. Lo abres con `Ctrl+Shift+G G` o desde el icono de la barra lateral.

Desde aquí puedes hacer prácticamente todo lo del día a día sin tocar la terminal.

### 🔸 Staging y commit

Cuando modificas algo en el repositorio aparece en la lista de cambios. Desde ahí:

<div style="text-align: left; margin: 0; display: inline-block; width: fit-content;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/SourceControl-d5992795-8916-429e-af24-eae64d3238d1.png" style="border: 2px solid lightgray; max-width: 100%; height: auto; display: block;" alt="Panel de Source Control">
    <div style="color: gray; font-size: small; font-style: italic; text-align: center;">Panel de Source Control con cambios e iconos de acción</div>
</div>

Los iconos que aparecen al lado de cada archivo:

- **+** → equivale a `git add`, manda el archivo al staging
- **-** → equivale a `git restore --staged`, saca el archivo del staging
- ↶ → equivale a `git restore`, descarta los cambios

Los colores del nombre del archivo también dan información:

| Color | Badge | Significa |
|---|---|---|
| Verde | **U** | Untracked — archivo nuevo, Git aún no lo conoce |
| Verde | **A** | Added — está en staging, listo para el commit |
| Amarillo | **M** | Modified — modificado pero no en staging |
| Naranja | **M** | Modified con warnings |
| Rojo | **D** | Deleted — archivo eliminado |
| Naranja | *(número)*, badge| Warnings en el archivo |
| Rojo | *(número)*, badge | Errores en el archivo |

Escribe el mensaje en el campo de texto y pulsa **Commit** para guardar.

### 🔸 Push, Pull y Fetch

Los tres puntitos (`...`) del panel abren el menú con todas las opciones de Git:

<div style="text-align: left; margin: 0; display: inline-block; width: fit-content;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/TresPuntos-b4342150-b6b3-4c1c-a39d-cb545c064530.png" style="border: 2px solid lightgray; width: 500px; height: auto; display: block;" alt="Panel de Source Control">
    <div style="color: gray; font-size: small; font-style: italic; text-align: center;">Menú de opciones de Git desde los tres puntitos</div>
</div>

Desde aquí tienes acceso a Pull, Push, Fetch, Branch, Remote y todo lo demás sin escribir un solo comando.

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ Importante</span></b>
    <br><br>
    Igual que en la terminal, haz siempre <code style="background:#FED7AA; padding: 2px 6px; border-radius: 4px; color:#7C2D12;">Fetch</code> antes de ponerte a trabajar para ver qué ha cambiado en el remoto, y luego <code style="background:#FED7AA; padding: 2px 6px; border-radius: 4px; color:#7C2D12;">Pull</code> para traerte los cambios.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🔍 GitLens

GitLens añade información de autoría directamente en el editor. La función más visible es el **blame inline**: al colocarte en cualquier línea de código ves quién la escribió, cuándo y en qué commit.

<div style="text-align: left; margin: 0; display: inline-block; width: fit-content;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/BlameInline-6059cc9c-6dd5-41fe-9d07-a977107c8b2f.png" style="border: 2px solid lightgray; width: 700px; height: auto; display: block;" alt="GitLens">
    <div style="color: gray; font-size: small; font-style: italic; text-align: center;">GitLens mostrando el blame inline en el editor</div>
</div>

En la barra inferior también aparece información del commit actual de la línea donde tienes el cursor.

<div style="text-align: left; margin: 0; display: inline-block; width: fit-content;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/BlameInlineBarraInferior-e11c452c-0737-41fa-bc4f-560b4399054a.png" style="border: 2px solid lightgray; width: 700px; height: auto; display: block;" alt="GitLensBarraInf">
    <div style="color: gray; font-size: small; font-style: italic; text-align: center;">GitLens mostrando el blame inline en la barra inferior</div>
</div>

### 🔸 Panel de GitLens

En el panel de Source Control, GitLens añade una sección propia con los commits de todos los repos abiertos en el workspace:

<div style="text-align: left; margin: 0; display: inline-block; width: fit-content;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/PanelGitLens-24b3d1b9-71d4-4858-9862-43fe730cf5ab.png" style="border: 2px solid lightgray; width: 300px; height: auto; display: block;" alt="PanelGitLens">
    <div style="color: gray; font-size: small; font-style: italic; text-align: center;">Panel de GitLens con los commits del workspace</div>
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📊 Git Graph

Git Graph es la extensión más visual de las tres. Muestra el historial de commits y ramas en forma de grafo, y desde ahí puedes hacer fetch, checkout y merge sin salir de la vista.

### 🔸 Cómo abrirlo

Haz clic en el botón **Git Graph** de la barra de estado inferior:

<div style="text-align: left; margin: 0; display: inline-block; width: fit-content;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/GitGraphAbrir-65889456-5a4c-44ff-b90d-2b017cde0435.png" style="border: 2px solid lightgray; width: 400px; height: auto; display: block;" alt="GitGraphAbrir">
    <div style="color: gray; font-size: small; font-style: italic; text-align: center;">Botones para abrir Git Graph</div>
</div>

### 🔸 El grafo

Desde los selectores de la parte superior puedes cambiar entre repositorios y filtrar por rama. El botón de fetch está arriba a la derecha, úsalo antes de empezar a trabajar para tener el grafo actualizado.

En el grafo, cada línea de color es una rama y cada punto es un commit. Las etiquetas muestran el nombre de la rama y si es local, remota o ambas. La rama activa se distingue por el círculo hueco (○) en lugar del punto relleno (●), y también aparece en la barra de estado inferior.

<div style="text-align: left; margin: 0; display: inline-block; width: fit-content;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/GitGraph-70f36689-e01d-46b2-a2e6-510367b3b039.png" style="border: 2px solid lightgray; width: 700px; height: auto; display: block;" alt="GitGraph">
    <div style="color: gray; font-size: small; font-style: italic; text-align: center;">Vista del grafo</div>
</div>

## 🕐 Git History

Git History te permite explorar el historial de un archivo concreto y comparar versiones. Útil cuando quieres saber cuándo se introdujo un cambio específico en un archivo sin revisar todo el grafo.

Para usarlo, haz clic derecho sobre cualquier archivo y selecciona **Git: View File History**, o teniendo el archivo concreto abierto con `Alt+H`.

<div style="text-align: left; margin: 0; display: inline-block; width: fit-content;">
    <img src="https://dev.azure.com/Cloud-Application-Security/6d69cfb2-1f19-40c4-9922-a48675136385/_apis/git/repositories/475632c5-1968-4de9-b912-d71ba61b92b6/items?path=/.attachments/Screenshot%202026-06-12%20105914-2277a7e2-9093-47ea-9dbd-e14ccc2939df.png" style="border: 2px solid lightgray;  width: 700px; height: auto; display: block;" alt="GitHistory">
    <div style="color: gray; font-size: small; font-style: italic; text-align: center;">Git History mostrando el historial de un archivo</div>
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## ✍️ Conventional Commits

Aplica exactamente lo mismo que en **Git CLI**. La única diferencia es que aquí escribes el mensaje en el campo de texto del panel de Source Control en lugar de en la terminal.

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Consejo.</b> Si aún no has leído la sección de Conventional Commits de Git CLI, léela. Está todo explicado ahí.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📚 Para profundizar

**🎥 Vídeos**

| 🎬 **Título** | ⏳ **Duración** |
|---|---|
| [Git Graph VSCode Extension](https://www.youtube.com/watch?v=u9ZQpKGTog4) | 10min |


<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;"> <b>💡 Una vez te acostumbras a trabajar desde aquí, volver a la terminal pura se hace raro.</b> Úsalas las dos según el momento, que para eso están. </div>