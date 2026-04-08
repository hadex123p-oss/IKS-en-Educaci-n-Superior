Infografía Interactiva — IKS en Educación Superior
Infografía web de tipo lista interactiva que presenta cinco desafíos clave para la integración de los Sistemas de Conocimiento Indígena (IKS) en la educación superior. Basada en el estudio exploratorio sobre Ayurveda e IKS en programas académicos de India.

Descripción
El recurso transforma una lista tradicional de cinco recomendaciones en una experiencia visual interactiva construida exclusivamente con HTML semántico y CSS puro. Cada ítem incorpora dos efectos de microinteracción activados al pasar el cursor:

Efecto de semicírculo rotativo (#18): el marcador de cada ítem muestra inicialmente medio círculo de color; al hacer hover, el segundo semicírculo rota sobre su eje para completar el fondo circular del ícono.
Línea ondulada animada (#24): al activar el hover sobre un ítem, se revela una línea ondulada codificada como SVG bajo el título, la cual se desplaza horizontalmente en bucle continuo.
Vista previa de los efectos
Estado	Ícono	Título
Reposo	Medio círculo visible	Texto blanco, sin decoración
Hover	Círculo completo (rotación de semicírculo)	Texto coloreado + onda en movimiento
Características técnicas
HTML semántico puro: estructura basada en <main>, <header>, <ul> / <li> y <footer>.
CSS Vanilla sin dependencias: cero líneas de JavaScript, cero frameworks (ni Tailwind ni Bootstrap).
Diseño Mobile First: tres puntos de quiebre responsivos (base móvil, 640 px tablet, 960 px escritorio).
Touch targets accesibles: cada ítem tiene una altura mínima de 48 px para interacción táctil cómoda.
Respeta prefers-reduced-motion: desactiva animaciones y transiciones para usuarios que lo soliciten.
Transiciones consistentes: todas las transiciones usan transition: all 0.4s ease-in-out o variaciones específicas.
Estructura del archivo
infografia-iks.html
│
├── <style>
│ ├── Reset y variables CSS (:root)
│ ├── Estilos base (Mobile First)
│ ├── Decoración de fondo (orbes con blur)
│ ├── Contenedor principal
│ ├── Encabezado
│ ├── Lista infográfica (<ul>)
│ ├── Efecto #18 — Semicírculo del ícono
│ ├── Contenido de texto (columnas)
│ ├── Efecto #24 — Línea ondulada bajo título
│ ├── @keyframes wave-move
│ ├── Pie de página (<footer>)
│ ├── Media queries (tablet y escritorio)
│ └── Accesibilidad (prefers-reduced-motion)
│
├── <main>
│ ├── <header> → Título y subtítulo
│ ├── <ul> → Lista de 5 ítems
│ │ ├── <li> ítem 1 → 🧩 Brecha entre intención y aplicación
│ │ ├── <li> ítem 2 → 🎓 Formación docente como prioridad
│ │ ├── <li> ítem 3 → 📚 Transformación del currículo
│ │ ├── <li> ítem 4 → 🔬 Aprendizaje experiencial e innovador
│ │ └── <li> ítem 5 → 🤝 Colaboración interdisciplinaria
│ └── <footer> → Fuente académica y autoría
│
└── (sin <script>)

text


---

## Paleta de colores

| Color | HEX | Uso |
|-------|-----|-----|
| Azul profundo | `#1F3A5F` | Fondo principal, confianza y rigor científico |
| Verde | `#4CAF50` | Ítems 1, 3, 5 — salud, naturaleza, Ayurveda |
| Naranja suave | `#F4A261` | Ítems 2, 4 — innovación y creatividad |

La alternancia verde/naranja se controla mediante la propiedad personalizada `--item-color` en cada `<li>`.

---

## Guía de personalización

### Cambiar el color de la onda ondulada

Ubica la regla `.item-content h3::after` dentro del `<style>`. En `background-image`, busca `stroke=%23XXXXXX` y reemplaza el código HEX (sin el `#`):

Verde: stroke=%234CAF50
Naranja: stroke=%23F4A261
Blanco: stroke=%23ffffff
Rojo: stroke=%23E53935

text


También puedes ajustar la opacidad global con `stroke-opacity='0.65'` (valor entre 0 y 1).

### Cambiar la amplitud de la onda

En el mismo SVG dentro de `background-image`, modifica los valores de control de la curva cuadrática `Q`:

Onda suave: Q25 1 50 3 (desplazamiento vertical menor)
Onda estándar: Q25 0 50 3 (valor por defecto)
Onda pronunciada: Q25 -1 50 3 (desplazamiento vertical mayor)

text


### Cambiar la velocidad de rotación del semicírculo

Ubica la regla `.item-icon::after` y modifica `transition`:

```css
/* Más rápido */
transition: transform 0.2s ease-in-out;

/* Por defecto */
transition: transform 0.4s ease-in-out;

/* Más lento */
transition: transform 0.7s ease-in-out;

/* Con efecto rebote */
transition: transform 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55);
Cambiar la velocidad de desplazamiento de la onda
Ubica la regla .infographic-list li:hover .item-content h3::after y modifica la duración:

css

/* Más rápida */
animation: wave-move 1s linear infinite;

/* Por defecto */
animation: wave-move 2.5s linear infinite;

/* Más lenta */
animation: wave-move 4s linear infinite;
Nota importante: si modificas el ancho del SVG (actualmente 200), debes actualizar tres valores de forma sincronizada: el atributo width del SVG, background-size y el valor 200px dentro de @keyframes wave-move.

Cambiar el color de un ítem individual
Cada <li> recibe su color a través de --item-color. Edita el atributo style directamente:

Este color se aplica automáticamente al semicírculo del ícono, al borde lateral izquierdo y al color del título en estado hover.

Contenido de la infografía
#
Desafío
Descripción resumida
Emoji
1	Brecha entre intención y aplicación	Consenso existente pero dificultades prácticas en la implementación	🧩
2	Formación docente como prioridad	Necesidad de capacitación específica para el aula	🎓
3	Transformación del currículo	Rediseño con cursos interdisciplinarios y enfoques flexibles	📚
4	Aprendizaje experiencial e innovador	Simulaciones y estudios de caso como metodologías activas	🔬
5	Colaboración interdisciplinaria	Cooperación entre expertos tradicionales y científicos modernos	🤝

Fuente académica
Stakeholder perspectives on integrating Ayurveda and Indian Indigenous Knowledge Systems into higher education: An exploratory study

DOI: 10.1016/j.ssaho.2025.101453

Autoría del diseño
Harold Polack Modenesi

Navegadores compatibles
Navegador
Versión mínima
Chrome	80+
Firefox	78+
Safari	14+
Edge	80+

Se requieren soporte de: propiedades personalizadas CSS (var()), background-image con SVG inline, @keyframes, transform-origin y pseudoelementos ::before / ::after.

Licencia
Uso académico y educativo. Se permite la libre modificación del código con atribución al autor del diseño.
```