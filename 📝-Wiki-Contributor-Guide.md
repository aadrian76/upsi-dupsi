<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de contenidos
    </summary>

  [[_TOC_]]
</details>

## 📝 Changelog

<br>

| Autor                             | Fecha                   | Cambios                                       |
|-----------------------------------|-------------------------|-----------------------------------------------|
| Salamero                          | 18/02/2026              | Traducción al español                         |
| @<C73C5218-17C3-6B53-B15D-E321D12689EB>                  | 25/02/2025              | Primera versión                               |

<br>

---

<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
<b><span style="color:#7C3AED; font-size: 17px;">🚨 LEE ESTO PRIMERO</span></b>
    <br><br>
    Nada de inventar ni ir por libre — <b>sigue la guía</b>.
    <br><br>
    Esta wiki tiene una <b>estructura clara</b> por algo. Respétala.
    <br><br>
    ¿Algo no te queda claro? <b>Mira ejemplos, busca, o pregunta — pero solo después de haberlo intentado.</b>
</div>

**BIENVENIDO 🎉**

Si estás leyendo esto es porque vas a contribuir a la wiki — ya sea por voluntad propia o porque te lo han asignado. Da igual el motivo: lo que importa es que sigas **estas** reglas y directrices.

Esta guía ahorra tiempo a todo el mundo y **evita idas y venidas innecesarias**. A nadie le gusta eso, ¿verdad?

**TL;DR:**

- Sigue esta guía
- **Escribe como un experto**, pero que se entienda y **NO SEAS ABURRIDO**
- Si no sabes algo:
  1. Búscalo y apréndelo
  2. Usa ChatGPT
  3. Escríbelo
- **Nada de muros de texto** — secciones breves y enfocadas
- **Sé consistente**. El formato, la terminología y la estructura importan
- **NO** uses humor forzado, **NO** caigas en lenguaje corporativo vacío
- Usa ejemplos reales, hazlo práctico

La página [🌍 Core Security Concepts](/📆-Week-1/🌍-Core-Security-Concepts) es un **MUY BUEN EJEMPLO** de todo esto. Échale un vistazo.

<div style="background:#F3E8FF; padding:15px; border-left:10px solid #7C3AED; border-radius:6px;">
    <b>💡 En caso de duda, mira los ejemplos de las páginas existentes</b>. Si aún así no lo tienes claro, pregunta
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📌 Principios

Esta wiki sigue un estilo **consistente** y **estructurado** para garantizar legibilidad, claridad y que no sea un tostón leerla.

### ✍️ Principios básicos de redacción

Documentar bien no es soltar información sin más — es hacer que sea **clara, útil y fácil de leer**. Directo, estructurado y sin paja.

- **Sin relleno** – Al grano, sin explicaciones innecesarias
- **Tono directo pero cercano** – Debe sonar como un experto explicando las cosas, no como un documento corporativo
- **Claridad total** – Cada frase debe aportar valor. Nada de formulaciones vagas
- **Formalidad mínima** – Usa un lenguaje natural
- **Flujo lógico** – Las secciones deben conectar de forma natural entre sí
- **Algo de personalidad** – Seguro, directo, pero sin pasarse
- **Nada de tono corporativo** – Esto no es un whitepaper, es una guía que la gente va a usar de verdad
- **NADA DE CRINGE** – Nada de chistes forzados ni abuso de memes

### 🚨 Regla obligatoria de estructura

Cada **sección** (`##`) debe empezar con al menos un párrafo introductorio antes de cualquier subsección (`###`).

**Mal:**

```markdown
## 🏛 Modelos de Seguridad

### 🔺 Tríada CIA
```

**Bien:**

```markdown
## 🏛 Modelos de Seguridad

La seguridad no es simplemente poner un firewall y dar el tema por cerrado — se basa en **principios fundamentales** que guían cada decisión de seguridad.

### 🔺 Tríada CIA
```

### ❌ Qué NO hacer

- **Sobre-explicar**: Si necesitas más de 3 frases, usa bullet points
- **Escribir como un paper académico**: Nada de voz pasiva ni introducciones kilométricas
- **Abusar de los emojis**: Dan color, pero esto no es un blog infantil. Los emojis van en **headings** (`##`, `###`) para separación visual — no en bullet points. Nada de `⬜`, `✅`, `☑️` ni similares como marcadores de lista
- **Pegar enlaces sin contexto**: Cada enlace debe tener una explicación
- **Hacer secciones demasiado largas**: Si se está hinchando, divídela

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🔤 Reglas de estilo y formato

### Changelog

Todas las páginas deben incluir una tabla de changelog justo después del TOC. El formato es siempre el mismo:

```markdown
## 📝 Changelog

<br>

| Autor            | Fecha      | Cambios                          |
|------------------|------------|----------------------------------|
| Nombre           | DD/MM/YYYY | Descripción breve del cambio     |

<br>

---
```

- El `<br>` antes y después de la tabla es obligatorio (da separación visual)
- El `---` después cierra la sección de cabecera
- Las entradas más recientes van arriba

### Cómo escribir la introducción

La **introducción** **NO forma parte de ninguna sección** (`##`). Va **por encima de la primera sección** y sirve para dar contexto y establecer el tono de la página.

📌 **Reglas para las introducciones:**

- **Sin heading (`##`)**: **NO** forma parte de las secciones estructuradas
- **Corta, directa y que enganche**: Evita explicaciones largas y secas
- **Explica el propósito de la página**: ¿Por qué debería importarle al lector?
- **Establece expectativas**: ¿Qué se cubre? ¿Qué es importante?
- **Humor o sarcasmo** (opcional): Si encaja, úsalo con moderación
- **Callout boxes** (si hace falta): Para reforzar puntos clave

📌 **Ejemplos de páginas existentes:**

- **📝 Wiki Contributor Guide** → Establece las reglas desde el principio
- **🌐 Bienvenido** → Sarcástico pero informativo
- **Cualquier página de conceptos** → Intro breve de "por qué esto importa"

### Headings

- Sin negritas (`**`) dentro de los headings
- Cada heading debe estar separado por una línea en blanco
- Cada heading debe llevar un emoji para separación visual

Ejemplo:

```markdown
## 🔺 Tríada CIA
```

### Spacers entre secciones

Entre cada sección principal (`##`) se añade un spacer HTML para dar aire visual. Siempre se usa este patrón exacto:

```html
<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>
```

Solo entre `##`, no entre subsecciones (`###`).

### Callout boxes

Tenemos **dos tipos** de callout box. Usa el que corresponda según el contexto:

**Morado** — para consejos, información destacada y notas:

```html
<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Consejo</b>: Piensa siempre primero en los modelos de seguridad
</div>
```

**Naranja** — para avisos, disclaimers y red flags:

```html
<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b>⚠️ Aviso</b>: Esto puede romper cosas si no tienes cuidado
</div>
```

No mezclar los colores ni inventar variantes. Solo estos dos.

### Listas y bullet points

Cortos, claros y sin punto final.

Ejemplo:

```markdown
- 🔐 **Confidencialidad** – Si no deberías verlo, no lo ves
- ⚖️ **Integridad** – Si los datos cambian, deberías saberlo
- 🖥️ **Disponibilidad** – Si no puedes acceder cuando lo necesitas, no sirve de nada
```

O sin títulos:

```markdown
- Las redes ya no son tan seguras
- El movimiento lateral es una amenaza real — una vez dentro, los atacantes pueden ir a cualquier parte
- Los usuarios son el eslabón más débil — phishing, credenciales robadas e ingeniería social siguen siendo los vectores de ataque más comunes
```

### Tablas

Que estén **limpias** y **bien estructuradas**.

Ejemplo:

```markdown
| 🔗 **Título** | 📜 **Descripción** | 🔍 **Fuente** |
|---|---|---|
| [La Tríada CIA](https://example.com) | Visión general de la Tríada CIA | **CSO Online** |
```

### Imágenes y memes

**Se anima a usarlos si son relevantes**, pero deben **aportar valor**.

Ejemplo:

```html
<div style="text-align: center; margin-bottom: 20px;">
    <img src="IMAGE_URL" style="border: 3px solid lightgray; width: 500px; padding: 1rem;">
    <div style="color: gray; font-size: small; font-style: italic;">Pie de imagen aquí</div>
</div>
```

### Vídeos

Usar iframes embebidos.

Ejemplo:

```html
<center>
::: video
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/kPPFNrlN3zo"
    title="What is the CIA Triad" frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen>
</iframe>
:::
</center>
```

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🚀 Equilibrio entre humor y shitposting

Sí, pero con mesura y que sea **de verdad** gracioso.

- **¿Dónde?** En introducciones, transiciones, o como un one-liner bien colocado
- **Lo que NO hacemos:**
  - Nada de humor forzado
  - Nada de muros de texto "gracioso"
  - Nada de abusar de memes
  - Nada de cringe

**Buenos ejemplos**

- _"La seguridad no es poner un firewall y dar el tema por cerrado."_
- _"La Tríada CIA no es una agencia secreta, es **el** modelo de seguridad."_

**Malos ejemplos**

- _"Jajaja imagina hackear la NASA con un S3 bucket mal configurado lol"_
- _"Bro, este modelo es tipo, re OP la verdad"_

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 📂 Plantilla completa de ejemplo

```markdown
<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Tabla de contenidos
    </summary>

  [[_TOC_]]
</details>

## 📝 Changelog

<br>

| Autor        | Fecha             | Cambios              |
|--------------|-------------------|----------------------|
| @<Tu Nombre> | <DD/MM/YYYY>      | Mensaje de cambios   |

<br>

---

<div style="background:#F3E8FF; padding:15px; margin-top:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b><span style="color:#7C3AED; font-size: 17px;">🚨 <TÍTULO DEL CALLBOX></span></b>
    <br><br>
    <Frase de apertura sobre el propósito de esta página o sección. Debe ser clara, directa y establecer expectativas.>
    <br><br>
    <Contexto adicional, refuerzo o instrucciones. Si hace falta, añade más párrafos para aclarar qué debe hacer o tener en cuenta el lector.>
    <br><br>
    <Nota final importante, tipo "Si algo no queda claro, mira ejemplos, busca, o pregunta — pero solo después de haberlo intentado." Si el humor encaja, añádelo de forma natural.>
</div>

<El tamaño del callout box depende del contexto y del contenido. Puede tener 2 o más párrafos, según la importancia del mensaje.>

**<TÍTULO DE LA INTRODUCCIÓN, FRASE O ALGO GRACIOSO> 🎉**

<Esto es la introducción. Explica por qué existe la página, qué cubre y por qué importa. Breve, directo y que enganche. Si hace falta, usa varios párrafos para aclarar puntos clave.>

⚡ **Puntos clave:**

- <Por qué existe esta página>
- <Qué se cubre aquí>
- <Qué se espera del lector>

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Esto es un callout box</b>: <Se usa para resaltar información importante.>
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🔹 <Primera sección principal>

<Párrafo de apertura explicando de qué va esta sección. Conciso y al grano. Debe introducir al lector en el tema sin relleno innecesario.>

<Opcionalmente, añade algún párrafo más, pero siempre dependiendo del contexto.>

### 🔸 <Subsección>

<Escribe el contenido en un **lenguaje claro y directo**. Párrafos cortos, sin explicaciones innecesarias.>

- **Usa bullet points** para listar conceptos clave
- **Frases directas** y con contenido
- **Sin punto final** en los bullet points
- **Incluye ejemplos reales** cuando aplique

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 Consejo</b>: <Si necesitas añadir una nota, usa un callout morado como este.>
</div>

<div style="background:#FFEDD5; padding:15px; margin-bottom:15px; border-left:10px solid #F97316; border-radius:6px; color:#7C2D12;">
    <b>⚠️ Aviso</b>: <Para advertencias o disclaimers, usa el callout naranja.>
</div>

### 🔹 <Otra subsección>

<Otra breve introducción antes de entrar en detalle.>

| 🔗 **Título** | 📜 **Descripción** | 🔍 **Fuente** |
|---|---|---|
| [Recurso de ejemplo](https://example.com) | <Breve descripción de por qué es útil> | **Sitio de ejemplo** |

<div style="text-align: center; margin-bottom: 20px;">
    <img src="IMAGE_URL" style="border: 3px solid lightgray; width: 500px; padding: 1rem;">
    <div style="color: gray; font-size: small; font-style: italic;"><Añade un pie de imagen si hace falta></div>
</div>

#### 📚 Para profundizar

<Forma parte de la subsección de cada tema. Proporciona recursos adicionales para quien quiera saber más.>

<No hace falta incluir los 3 tipos de recursos (artículos, vídeos, herramientas) si no son necesarios.>

¿Quieres ir más allá? Aquí van nuestras **recomendaciones** para reforzar lo que acabas de aprender:

**📖 Artículos y documentación**

| 🔗 **Título** | 📜 **Descripción** | 🔍 **Fuente** |
|---|---|---|
| Título | Descripción | Fuente |

**🎥 Vídeos**

| 🎬 **Título** | ⏳ **Duración** | 🔍 **Fuente** |
|---|---|---|
| Título | Duración | Fuente |

**🛠 Herramientas y labs**

| 🛠️ **Herramienta / Lab** | 🔍 **Descripción** | 🔗 **Enlace** |
|---|---|---|
| Herramienta | Descripción | [Enlace](#) |

**📌 TL;DR**

- **📖 Lee** → Artículos, documentación oficial y casos de estudio
- **🎥 Mira** → Vídeos cortos y largos
- **🛠 Prueba** → Herramientas y labs prácticos

<div style="background:#F3E8FF; padding:15px; margin-bottom:15px; border-left:10px solid #7C3AED; border-radius:6px; color:#1F1B2D;">
    <b>💡 No te limites a leer — experimenta</b>. Rompe cosas. Arregla cosas. Así es como <b>de verdad</b> se aprende
</div>

<!-- Spacer to visually separate major sections (## headings) -->
<div style="margin-top: 40px;"></div>

## 🔹 <Otra sección principal>

[...]
```
