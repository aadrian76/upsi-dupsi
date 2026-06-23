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
    Esta página no es para leerla y cerrarla. Es para tenerla abierta mientras tocas cosas en la terminal.
    <br><br>
    <span style="color:#7C3AED;"><b>Git se aprende rompiendo cosas, no leyendo sobre él.</b></span> Si algo no tiene sentido, pruébalo. El historial de Git está precisamente para que nada sea irreversible.
</div>

**Bienvenido al comando que vas a usar el resto de tu vida. 🙃**

Git es el sistema de control de versiones más usado del mundo. Guarda el historial completo de tu proyecto, te permite volver atrás cuando la lías y hace posible trabajar en equipo sin que todo explote.

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🧠 Conceptos clave

Cuatro conceptos sobre los que se construye todo lo demás. Si los entiendes, el resto viene solo.

### 🔸 Repositorio

La carpeta de tu proyecto donde Git guarda el historial. Puede ser local (en tu máquina) o remoto (GitHub, GitLab, etc.).

### 🔸 Commit

Una "foto" del estado de tus archivos en un momento dado. Cada commit tiene un identificador único, autor, fecha y mensaje. El historial de tu proyecto es una lista de commits ordenados en el tiempo.

### 🔸 Rama (branch)

Una línea de trabajo independiente. Creas una rama para desarrollar algo nuevo sin tocar el código principal. Cuando terminas, la fusionas a la rama principal.

### 🔸 Staging area

El área de preparación. Antes de hacer un commit, seleccionas exactamente qué cambios quieres incluir, en lugar de guardar todo de golpe.

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🔄 Flujo de trabajo

Siempre el mismo patrón, cuatro pasos: 
**Editar archivos → git add → git commit → git push**

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Regla de oro.</b> Commits pequeños y frecuentes, con mensajes claros. <b>"fix stuff"</b> no le dice nada a nadie, ni a ti dentro de dos semanas.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## ⚙️ Configuración inicial

Solo una vez. Git usa esto para firmar cada commit. El flag `--global` aplica la configuración a todos los repos de tu máquina. Si en algún proyecto necesitas una configuración distinta, usa `--local` dentro de ese repo concreto.

```bash
git config --global user.name "Tu nombre"
git config --global user.email "tu@email.com"
git config --list   # comprueba que está bien
```

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🚀 Crear o clonar un repositorio

```bash
git init          # convierte la carpeta actual en un repositorio Git y crea la carpeta .git
git clone <url>   # descarga un repositorio existente con todo su historial
```

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Cuándo usar cada uno:</b> <code style="background:#E9D5FF; padding: 2px 6px; border-radius: 4px; color:#4C1D95;">git init</code> cuando empiezas desde cero, <code style="background:#E9D5FF; padding: 2px 6px; border-radius: 4px; color:#4C1D95;">git clone</code> cuando el repo ya existe. Si te incorporas a un equipo, casi siempre vas a usar <code style="background:#E9D5FF; padding: 2px 6px; border-radius: 4px; color:#4C1D95;">git clone</code>.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📦 Comandos del día a día

### 🔸 Estado del repositorio

```bash
git status            # qué archivos han cambiado y qué hay en staging
git diff              # qué líneas exactas cambiaron, antes del add
```

Úsalo constantemente. Es el comando que más información te da de lo que está pasando en tu repo.

### 🔸 Guardar cambios

```bash
git add <archivo>        # agrega un archivo al staging
git add .                # agrega todo al staging
git commit -m "mensaje"  # guarda el commit
```

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ Cuidado con <code style="background:#FED7AA; padding: 2px 6px; border-radius: 4px; color:#7C2D12;">git add .</code></span></b>
    <br><br>
    Agrega absolutamente todo. Si tienes archivos con contraseñas, claves de API o configuraciones locales, los vas a subir sin darte cuenta. <b>Usa siempre un </b><code style="background:#FED7AA; padding: 2px 6px; border-radius: 4px; color:#7C2D12;">.gitignore</code> y revisa con <code style="background:#FED7AA; padding: 2px 6px; border-radius: 4px; color:#7C2D12;">git status</code> antes de hacer commit.
</div>

### 🔸 Ver el historial

```bash
git log                    # historial completo
git log --oneline          # una línea por commit, mucho más legible
git show <hash>            # detalle de un commit específico
```

### 🔸 Deshacer cosas

```bash
git restore <archivo>             # descarta cambios locales no guardados
git restore --staged <archivo>    # saca un archivo del staging sin perder los cambios
git revert <hash>                 # crea un commit que deshace otro (seguro en equipo)
```

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 revert vs reset.</b> <code style="background:#E9D5FF; padding: 2px 6px; border-radius: 4px; color:#4C1D95;">git reset</code> reescribe el historial. <b>Nunca lo uses en una rama compartida</b>, porque estás borrando commits que otros ya tienen. <code style="background:#E9D5FF; padding: 2px 6px; border-radius: 4px; color:#4C1D95;">revert</code> es siempre la opción segura: deshace cambios añadiendo un commit nuevo, sin tocar el historial.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🌿 Ramas

Trabajar directamente en `main` o `master` es mala idea. Las ramas te dan un espacio aislado para desarrollar sin afectar lo que ya funciona.

```bash
git branch                   # lista las ramas locales
git branch <nombre>          # crea una rama nueva
git switch <nombre>          # cambia a otra rama
git switch -c <nombre>       # crea una rama y cambia a ella (lo más común)
git merge <rama>             # fusiona otra rama en la actual
git branch -d <nombre>       # elimina una rama ya fusionada
```

El nombre de la rama debe describir qué hace, no quién la hace. Por convenio se usan prefijos para identificar el tipo de trabajo de un vistazo:

| Prefijo | Cuándo usarlo |
|---|---|
| `feature/` | Nueva funcionalidad |
| `fix/` | Corrección de un bug |
| `hotfix/` | Corrección urgente en producción |
| `docs/` | Solo documentación |
| `refactor/` | Limpieza o reestructuración de código |

```bash
# Bien
git switch -c feature/login
git switch -c fix/error-500-api

# Mal
git switch -c mirama
git switch -c olaya
```

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ Antes de nombrar ramas en un proyecto de equipo</span></b>
    <br><br>
    Estos prefijos son una convención habitual, pero cada equipo puede tener la suya. <b>Si te incorporas a un proyecto que ya tiene ramas, mira cómo están nombradas y sigue ese patrón.</b>
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## ☁️ Repositorio remoto

El remoto es el servidor donde se almacena el código (GitHub, GitLab...). Por convenio se llama `origin` y la rama principal suele ser `main` o `master`.

```bash
git remote -v                  # muestra las URLs remotas configuradas
git fetch                      # descarga cambios del remoto sin fusionarlos
git pull                       # descarga y fusiona (fetch + merge)
git push                       # sube tus commits al remoto
git push -u origin <rama>      # sube una rama nueva y la enlaza con el remoto
```

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;"> <b><span style="color:#9A3412; font-size: 17px;">⚠️ IMPORTANTE!!!</span></b> <br><br> Antes de ponerte a trabajar, haz siempre <code style="background:#FED7AA; padding: 2px 6px; border-radius: 4px; color:#7C2D12;">git fetch</code> para ver qué ha cambiado en el remoto, y luego <code style="background:#FED7AA; padding: 2px 6px; border-radius: 4px; color:#7C2D12;">git pull</code> para traerte los cambios. Si te saltas este paso y empiezas a trabajar con el repo desactualizado, cuando intentes hacer push te lo va a rechazar y tendrás que resolver conflictos que podrían haberse evitado. </div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## ✍️ Conventional Commits

Un commit bien escrito vale más que diez commits de "fix" y "cambios". Conventional Commits es un estándar para escribir mensajes de commit consistentes que todo el equipo entiende de un vistazo, y que además permite generar changelogs automáticos.

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b><span style="color:#9A3412; font-size: 17px;">⚠️ Antes de aplicar esto en un proyecto de equipo</span></b>
    <br><br>
    Conventional Commits es un buen estándar de partida, pero si te incorporas a un proyecto que ya tiene commits, <b>mira primero cómo están escritos los commits existentes y sigue ese patrón</b>. Cada equipo puede tener sus propias convenciones y lo importante es la consistencia.
</div>

### 🔸 Estructura

**tipo(scope): descripción corta**

El `scope` o alcance es opcional, indica qué parte del proyecto estás tocando. La descripción va en minúsculas y sin punto final.

### 🔸 Tipos principales

| Tipo | Cuándo usarlo |
|---|---|
| `feat` | Añades algo nuevo |
| `fix` | Corriges un bug |
| `docs` | Solo tocas documentación |
| `refactor` | Cambias código sin añadir ni corregir nada |
| `test` | Añades o modificas tests |
| `chore` | Tareas de mantenimiento, dependencias, configuración |

### 🔸 Ejemplos

```bash
# Bien
git commit -m "feat(auth): añadir login con Google"
git commit -m "fix(api): corregir error 500 en endpoint de usuarios"
git commit -m "docs: actualizar README con instrucciones de instalación"
git commit -m "chore: actualizar dependencias de seguridad"

# Mal
git commit -m "fix"
git commit -m "cambios"
git commit -m "WIP"
git commit -m "arreglado"
```

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Consejo.</b> Si no sabes qué tipo poner, pregúntate: ¿esto añade algo nuevo? <code style="background:#E9D5FF; padding: 2px 6px; border-radius: 4px; color:#4C1D95;">feat</code>. ¿Arregla algo roto? <code style="background:#E9D5FF; padding: 2px 6px; border-radius: 4px; color:#4C1D95;">fix</code>. ¿Solo mueves o limpias código? <code style="background:#E9D5FF; padding: 2px 6px; border-radius: 4px; color:#4C1D95;">refactor</code>.
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📚 Para profundizar

**📖 Documentación**

| 🔗 **Título** | 📜 **Descripción** |
|---|---|
| [Pro Git](https://git-scm.com/book/es/v2) | El libro oficial de Git, gratuito y en español |
| [Referencia de comandos](https://git-scm.com/docs) | Documentación oficial de todos los comandos |
| [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/) | Especificación oficial del estándar |

**🎥 Vídeos**

| 🎬 **Título** | ⏳ **Duración** |
|---|---|
| [Git and GitHub for Beginners](https://www.youtube.com/watch?v=RGOj5yH7evk) | 1h |
| [Git Tutorial for Beginners](https://www.youtube.com/watch?v=8JJ101D3knE) | 1h |

**🛠 Herramientas y labs**

| 🛠️ **Herramienta** | 🔍 **Descripción** | 🔗 **Enlace** |
|---|---|---|
| Learn Git Branching | Tutorial interactivo visual para entender las ramas | [Learn Git Branching](https://learngitbranching.js.org/) |
| Oh My Git! | Juego para aprender Git desde cero | [Oh My Git!](https://ohmygit.org/) |

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 No te limites a leer, experimenta.</b> Crea un repo de prueba y rompe cosas a propósito. Así es como <b>de verdad</b> se aprende Git.
</div>