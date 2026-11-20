# Web CV

Práctica del bootcamp de Full Stack de The Bridge.

## Qué es

Un currículum en formato web, maquetado a partir de la plantilla Read.cv de Figma. Hice un fork del repositorio del profesor, que traía la cabecera del perfil, la sección "About" y los dos primeros puestos de experiencia. Mi trabajo fue completar el resto de la plantilla con HTML y CSS. La persona del CV, Sara Lawrence, es la de la plantilla: los datos son de ejemplo.

## Qué hice

En `index.html` completé la plantilla entera:

- **Work Experience**: seis puestos, cada uno con fechas, cargo y ciudad. El segundo lleva una fila de imágenes del portfolio.
- **Writing**: siete artículos. El primero lleva una tarjeta con imagen, título y tiempo de lectura.
- **Speaking**: tres charlas.
- **Side Projects**: tres proyectos personales.
- **Education**: el máster y el grado.
- **Contact**: enlaces a seis redes (Threads, Figma, Instagram, Bluesky, Mastodon y X).

Para no repetir estilos, monté un bloque `item` que sirve para todas las secciones: `item__meta` para la fecha a la izquierda, `item__details` para el contenido, `item__title` e `item__subtitle`. La tarjeta de los artículos es otro bloque, `writing-card`.

En `css/styles.css` cambié los colores de las etiquetas y los bordes a un tono rosa claro (`--color-bg-tag: #efe1e1`) y ajusté los tamaños de letra para que quedaran como en el diseño. En pantallas de menos de 768px cada `item` pasa a columna y la fecha queda encima del texto.

## Mis commits

Los hice entre el 5 y el 7 de octubre en `main`, encima del trabajo del profesor:

```
9f82296 modificando el css
010d369 modificando el css
da4bd65 modificando el css
a654cda modificando el css
1474173 modificando el css
8cb43d6 terminando html
a7a0709 terminando html
5e4766d terminando html
bf56b6f orla cghtml<
2008b89 estructurando html
```

Primero el HTML y después el CSS. El profesor siguió subiendo cambios a su repositorio después (un formulario de contacto y un botón para volver arriba), pero esos no están en mi copia.

## Cómo verlo

Abre `index.html` en el navegador. No hace falta instalar nada.

## Qué aprendí

**A reutilizar un bloque CSS.** Experiencia, artículos, charlas y proyectos tienen la misma forma: fecha a un lado y texto al otro. Con un solo bloque `item` los maqueto todos sin repetir reglas.

**A trabajar sobre un fork.** El repositorio viene del profesor (`upstream`) y yo subo a mi copia (`origin`). Con `git log --all` veo los dos historiales y en qué commit se separan.

**A leer un diseño de Figma.** Saqué de la plantilla los tamaños, los márgenes y los colores para que la página se pareciera lo más posible.

## README original del proyecto

Este es el README que traía el repositorio del profesor. Explica el diseño de partida y las convenciones del proyecto:

# Web CV

Currículum vitae en formato web: una página con perfil, sección "About" y experiencia laboral con portfolio de imágenes. Es responsive (mobile-first) y está hecha con HTML y CSS, sin frameworks ni dependencias.

## Diseño

Basado en la plantilla **Read.cv Template** de Figma Community:
[Ver diseño en Figma](https://www.figma.com/site/DLpJPoqFbKbEl6uUpzIUVc/Read.cv-Template--Community-?node-id=0-1)

## Stack

| Tecnología | Uso |
|---|---|
| HTML5 | Estructura semántica de la página |
| CSS3 | Estilos, layout con Flexbox y custom properties |
| [Inter](https://rsms.me/inter/) | Tipografía, servida en local desde `assets/fonts/` |

No hace falta instalar nada ni compilar.

## Cómo verlo

Abre `index.html` en el navegador, o usa la extensión **Live Server** de VS Code para que la página se recargue al guardar.

## Estructura

```
web-cv/
├── index.html
├── css/
│   └── styles.css
└── assets/
    ├── fonts/Inter/     # Pesos de Inter usados en el CSS + licencia (OFL)
    └── images/          # Foto de perfil e imágenes del portfolio
```

## Convenciones

### HTML
- **Semántica:** `header`, `main`, `section` y `article` según el papel de cada bloque. Fechas con `<time datetime="...">`.
- **Jerarquía de títulos:** un único `h1` (el nombre), `h2` para las secciones y `h3` para cada puesto. El nivel indica estructura, no tamaño: el tamaño se decide en CSS.
- **Accesibilidad:**
  - Todas las imágenes llevan `alt`. Si una imagen es decorativa, `alt=""`.
  - Los iconos decorativos (como `↗`) van con `aria-hidden="true"`.
  - Los enlaces externos llevan `target="_blank" rel="noopener noreferrer"`.

### CSS
- **Nombres de clase con [BEM](https://getbem.com/):** `bloque__elemento--modificador`.
  ```html
  <article class="work-experience">
    <h3 class="work-experience__title">...</h3>
  </article>
  ```
  Los elementos no se encadenan (`profile__name`, no `profile__data__name`) y los selectores son de una sola clase, para que todos tengan la misma especificidad.
- **Colores en variables con nombre según su función:** `--color-{grupo}-{papel}`, definidas en `:root`.
  ```css
  --color-text-heading   /* títulos */
  --color-text-body      /* texto general */
  --color-text-meta      /* datos secundarios: fechas */
  --color-bg-page        /* fondo de la página */
  --color-bg-tag         /* fondo de etiquetas */
  --color-border         /* bordes */
  ```
  En las reglas nunca se escribe un color directamente: siempre `var(--color-...)`.
- **Unidades:**
  - `font-size` en `rem`, para respetar el tamaño de letra que configure el usuario.
  - `line-height` sin unidad (`1.8`), para que se recalcule según el tamaño de letra de cada elemento.
  - `px` solo para detalles que no deben escalar, como bordes de `1px`.
- **Flexbox:** `flex-direction` se declara siempre de forma explícita, aunque sea `row`.
- **Responsive mobile-first:** los estilos base son para móvil y las media queries usan `min-width` (punto de corte: `768px`).
- **Comentarios:** solo cuando aportan algo que el código no dice (por ejemplo, dónde se usa cada variable de color).

### Git
- Mensajes en inglés siguiendo [Conventional Commits](https://www.conventionalcommits.org/): `feat:`, `fix:`, `refactor:`, `chore:`...
- Primera línea en imperativo y de menos de 72 caracteres. El cuerpo explica el porqué.
- Los archivos `.DS_Store` de macOS están en `.gitignore`.

## Créditos

- Diseño: [Read.cv Template](https://www.figma.com/site/DLpJPoqFbKbEl6uUpzIUVc/Read.cv-Template--Community-?node-id=0-1) (Figma Community).
- Tipografía: [Inter](https://rsms.me/inter/), de Rasmus Andersson, bajo licencia [SIL Open Font License](assets/fonts/Inter/OFL.txt).
