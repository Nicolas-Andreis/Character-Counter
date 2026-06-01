# Character Counter — Proyecto de Maquetado Web

## Objetivo del proyecto

Replicar visualmente la interfaz de una aplicación de conteo y análisis de texto (Character Counter) utilizando únicamente **HTML semántico y CSS**, sin JavaScript. Los valores son estáticos (hardcodeados) como primera etapa del proyecto.

Live Demo

🌐 Demo: https://nicolas-andreis.github.io/Character-Counter/

## Tecnologías utilizadas

- **HTML5** — estructura semántica con etiquetas como `<header>`, `<main>`, `<section>`, `<article>`, `<ul>`, etc.
- **CSS3** — variables CSS, Flexbox y diseño responsive
- **Google Fonts** — [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk)


## Herramientas extras utilizadas
- **svgrepo**      - iconos
- **tinypng**      - optimizacion de peso de imagenes
- **shots.so**     - mockups
- **github pages** - sitio hosteado

## Organización del HTML

El archivo `index.html` está dividido en tres grandes bloques:

1. **`<header>`** — Logo con ícono SVG y botón de configuración.
2. **`<main>`** — Contiene todas las secciones principales:
   - **Hero** (`<section class="hero">`) — Título + `<textarea>` + controles con checkboxes.
   - **Métricas** (`<section class="metrics">`) — 3 `<article class="card">` con estadísticas.
   - **Letter Density** (`<section class="density">`) — Lista de barras de progreso.

## Cómo se resolvió el CSS

- **Variables CSS (`:root`)** — Paleta de colores, sombras y fuente definidos centralmente.
- **Flexbox** — Usado en header, controles, tarjetas en mobile y filas de densidad.
- **Barras de progreso** — Implementadas con `div` anidados (`.density_bar_track` + `.density_bar_fill`), con ancho definido mediante variables CSS inline (`--ancho`) para permitir animación.
- **Checkboxes personalizados** — Estilizados con `appearance: none` y `:checked`.
- **Animaciones CSS** — Ver sección dedicada más abajo.
- **Responsive** — Media queries para desktop, tablet y mobile.
- **Separación de archivos** — `reset.css`, `variables.css`, `styles.css` y media queries en carpeta dedicada.

## Animaciones implementadas

Todas las animaciones son **CSS puro, sin JavaScript**.

- **Nombre del sitio** (`nav-brand`) — Efecto blur reveal: el texto aparece desenfocado y se va aclarando hasta quedar nítido, con las letras expandiéndose desde un `letter-spacing` amplio hasta su valor normal.
- **Cards de métricas** — Efecto `fadeUp` escalonado: cada card arranca invisible y sube desde abajo con un delay progresivo de 0.1s, 0.25s y 0.4s.
- **Barras de Letter Density** — Animación de expansión: cada barra arranca en `width: 0%` y se expande hasta su valor real (`--ancho`) con delays escalonados, usando variables CSS inline para que cada barra conozca su propio ancho objetivo.
- **Flecha de "See more"** — Rotación de 180° al abrir el `<details>`, usando el selector `details[open]`.
- **Hover en cards** — Efecto `filter: brightness` con transición suave al pasar el cursor.

## Dificultades encontradas

- Al hacer el diseño responsive tuve que ajustar bastante probando en diferentes dispositivos y tamaños de pantalla.
- Conflicto entre `animation` y `transition` en la misma propiedad `transform` en las cards — resuelto separando el hover con `filter: brightness` en lugar de `translateY`.
- Animación de barras de progreso: el ancho de cada barra es distinto, por lo que no se podía usar un `@keyframes` genérico. Se resolvió pasando el valor como variable CSS inline (`style="--ancho: 16.06%"`) y leyéndola desde el `@keyframes`.

## Capturas del resultado
DESKTOP
![desktop1](./assets/mockups/desktop1.png)
![desktop2](./assets/mockups/desktop2.png)
TABLET
![tablet](./assets/mockups/tablet.png)
MOBILE
![mobile](./assets/mockups/smartphone.png)

## Estructura de carpetas

```
proyecto/
├── index.html
├── css/
│   ├── mediaqueries/
│   │   ├── desktop.css
│   │   └── tablet.css
│   ├── reset.css
│   ├── styles.css
│   └── variables.css
├── js/
├── assets/
│   ├── icons/
│   ├── images/
│   │   └── cards/
│   ├── logo/
│   └── mockups/
└── README.md
```

## Próximos pasos

Segunda etapa del proyecto: agregar **JavaScript** para dar comportamiento dinámico:

- Conteo real de caracteres, palabras y oraciones
- Cálculo de tiempo de lectura estimado
- Generación automática de la densidad de letras
- Funcionalidad de los checkboxes (excluir espacios, límite de caracteres)