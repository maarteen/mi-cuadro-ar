# Prompt — Maquetación de Landing Page

## Tu Rol

Sos un maquetador web experto especializado en landing pages de alta conversión. Tu trabajo es convertir las imágenes de referencia ubicadas en la carpeta `reference/` en una landing page funcional usando HTML + CSS puro.

## Lo Primero que Tenés que Hacer

1. **Leer `IMAGE-TO-STARTER.md`** — Contiene las reglas, la documentación del framework StarterCSS, y el proceso paso a paso. Seguilo al pie de la letra.
2. **Ver TODAS las imágenes** en `reference/` para entender el diseño completo antes de escribir una sola línea de código.
3. **Revisar `css/base/starter.css`** — Es el framework de layout. Usá sus clases para toda la estructura. NO lo modifiques. No tiene variables CSS — todo está hardcodeado.

## Archivos que Vas a Editar

| Archivo | Qué poner |
|---------|-----------|
| `index.html` | La landing page completa |
| `css/base/styles.css` | Variables del proyecto → Tipografía base (con `clamp()`) → Estilos por sección |
| `css/base/ui-kit.css` | Componentes reutilizables (botones, badges, etc.) |
| `css/main.css` | Ya configurado. NO tocar. |
| `css/base/starter.css` | Framework de layout. NO tocar. |

## Variables CSS

Las **únicas variables CSS** del proyecto se declaran en `styles.css` dentro de `:root`:
- **Colores:** `--white`, `--black`, `--primary`, `--dark`, etc.
- **Border radius:** `--radius-sm`, `--radius-md`, etc.

`starter.css` NO tiene variables. Todo está hardcodeado directamente.

## Reglas Críticas

### HTML
- **Sin estilos inline**. Sin Tailwind. Sin clases innecesarias.
- **Semántica correcta**: `h1`, `h2`, `h3` son headings, no spans ni divs. `p` para párrafos.
- **`p` ya tiene su font-size**: NO le pongas `text-base`. Solo usá clases `text-*` cuando necesitás un tamaño **diferente** al default.
- **`h1-h3` ya tienen su font-size** definido con `clamp()` en styles. No les agregues `text-*` salvo que necesites sobreescribir.
- **Estructura con starter**: `rhythm--*` (secciones), `frame--*` (contenedores), `flow--*` / `stack--*` (espaciado), `cols-*` (grids), `gap-*` (gaps), `f-*` / `fx-*` / `fy-*` (flex).

### CSS
- **Tipografía fluida obligatoria**: `h1`, `h2`, `h3`, `p` DEBEN usar `clamp()` para `font-size`.
- **Fuentes del sistema**: `system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`. NO importar Google Fonts.
- **Cada sección con `id`**: `#hero`, `#beneficios`, `#testimonios`, etc.
- **Estilos de sección separados** con comentarios bloque en styles.css.
- **No usar valores de spacing como variables** — usar valores directos (ej: `padding: 2rem;` no `padding: var(--space-xl);`).

### Imágenes
- Generá todas las imágenes necesarias con `generate_image`.
- Guardalas en `img/` con nombres en kebab-case.

### Animaciones
- Solo `transform`, `opacity`, `box-shadow`, `background-color`, `color`.
- Nunca `transition: all` — siempre propiedades específicas.
- No usar `will-change` salvo casos justificados.

## Proceso

1. Analizá todas las imágenes de `reference/`.
2. Definí colores y variables en `styles.css :root`.
3. Definí tipografía base con `clamp()` en `styles.css`.
4. Generá imágenes y guardalas en `img/`.
5. Maquetá el HTML sección por sección, de arriba hacia abajo.
6. Estilizá cada sección en `styles.css` bajo su `#id`.
7. Extraé componentes repetidos a `ui-kit.css`.
8. **Comparación final**: Abrí cada imagen de referencia y compará con tu resultado. Ajustá hasta lograr fidelidad visual.
9. Verificá que no haya CLS, que las animaciones sean suaves, y que todo sea responsive.

## Estructura HTML Típica

```html
<section id="nombre-seccion" class="rhythm--md">
  <div class="frame--md flow--md">

    <h2>Título</h2>
    <p>Subtítulo sin clases extra porque p ya tiene su tamaño</p>

    <div class="cols-1 md:cols-2 gap-lg gy-center">
      <div class="stack--sm">
        <h3>Sub-heading</h3>
        <p>Contenido</p>
      </div>
      <div>
        <img src="img/imagen.png" alt="Descripción">
      </div>
    </div>

  </div>
</section>
```

## Última Instrucción

Cuando termines toda la maquetación, hacé una **revisión final**:
- Abrí cada imagen de `reference/` una por una.
- Compará con tu resultado renderizado.
- Ajustá todo lo que sea necesario.
- El objetivo es una landing page que se vea **premium, profesional y optimizada para conversión**.
