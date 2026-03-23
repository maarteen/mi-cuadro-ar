# STARTER-INIT — Workflow de Maquetación

## Documentación de StarterCSS

> **Nota:** `starter.css` no contiene variables CSS. Todos los valores de spacing están hardcodeados directamente en las clases. Esto hace que el framework sea completamente autocontenido y no dependa de definiciones externas.

### 1. Rhythm — Padding vertical de secciones

Controla el espaciado vertical (padding-block) de cada sección. Es fluido con `clamp()`.

```html
<section class="rhythm--sm"><!-- ~3.5rem → 5rem  --></section>
<section class="rhythm--md"><!-- ~4rem → 6rem    --></section>
<section class="rhythm--lg"><!-- ~5rem → 7rem    --></section>
<section class="rhythm--xl"><!-- ~6rem → 8rem    --></section>
<section class="rhythm--2xl"><!-- ~8rem → 10rem   --></section>
```

Automáticamente aplica: `position: relative`, `overflow: hidden`, `background: var(--section-bg, #ffffff)`.

Para cambiar el fondo, definir `--section-bg` en `styles.css`:

```css
#hero {
  --section-bg: var(--dark);
  background: var(--dark);
}
```

---

### 2. Frame — Contenedor horizontal centrado

Limita el ancho máximo del contenido y lo centra. Agrega padding lateral fluido.

```html
<div class="frame--sm">640px max</div>
<div class="frame--md">896px max</div>
<div class="frame--lg">1152px max</div>
<div class="frame--xl">1280px max</div>
<div class="frame--2xl">1440px max</div>
<div class="frame--full">Sin límite</div>
```

**Patrón típico:**

```html
<section class="rhythm--md">
  <div class="frame--md">
    <!-- contenido aquí -->
  </div>
</section>
```

---

### 3. Flow — Espaciado vertical fluido entre hijos

Aplica `margin-top` fluido a cada hijo directo excepto el primero. Ideal para separar bloques dentro de una sección.

| Clase       | Rango fluido      |
| ----------- | ----------------- |
| `flow--xs`  | 0.25rem → 0.75rem |
| `flow--sm`  | 0.5rem → 1rem     |
| `flow--md`  | 1rem → 2rem       |
| `flow--lg`  | 2rem → 3rem       |
| `flow--xl`  | 2.5rem → 3.5rem   |
| `flow--2xl` | 3rem → 4rem       |
| `flow--3xl` | 3.5rem → 6rem     |

```html
<div class="frame--md flow--md">
  <h2>Título</h2>
  <!-- sin margin-top (primer hijo) -->
  <p>Se separa automáticamente del h2</p>
  <div>También se separa</div>
</div>
```

---

### 4. Stack — Espaciado vertical estático entre hijos

Similar a flow pero con valores **estáticos** (no fluidos). Ideal para micro-layouts: cards, formularios, grupos de texto.

| Clase         | Valor          |
| ------------- | -------------- |
| `stack--none` | 0              |
| `stack--xs`   | 0.5rem (8px)   |
| `stack--sm`   | 0.75rem (12px) |
| `stack--md`   | 1rem (16px)    |
| `stack--lg`   | 1.5rem (24px)  |
| `stack--xl`   | 2rem (32px)    |
| `stack--2xl`  | 2.5rem (40px)  |

```html
<div class="paso stack--xs">
  <h3>Paso 1</h3>
  <p>Descripción del paso</p>
</div>
```

---

### 5. Grid — Sistema de columnas

Las clases `cols-*` activan `display: grid` automáticamente. Gap default: 1.5rem.

**Columnas (responsive):**

```html
<div class="cols-1 md:cols-2">1 col mobile → 2 col tablet+</div>
<div class="cols-1 md:cols-2 lg:cols-3">1 → 2 → 3</div>
```

Breakpoints: `md:` = ≥768px, `lg:` = ≥1024px. Columnas de 1 a 12.

**Gap (separación entre celdas):**

| Clase                  | Valor        |
| ---------------------- | ------------ |
| `gap-none`             | 0            |
| `gap-xs`               | 0.75rem      |
| `gap-sm`               | 1rem         |
| `gap-md`               | 1.5rem       |
| `gap-lg`               | 2rem         |
| `gap-xl`               | 3rem         |
| `gap-2xl` a `gap-10xl` | 4rem → 16rem |

Gaps responsivos: `md:gap-lg`, `lg:gap-xl`, etc.

**Alineación:**

```html
<div class="cols-2 gy-center">
  <!-- Items centrados en Y -->
  <div class="cols-2 gx-center">
    <!-- Items centrados en X -->
    <div class="cols-2 gxy-center">
      <!-- Items centrados en ambos -->
      <!-- Responsive: md:gxy-center, lg:gxy-center -->
    </div>
  </div>
</div>
```

**Span:**

```html
<div class="col-span-2">Ocupa 2 cols</div>
<div class="col-span-full">Ocupa todas</div>
<!-- Responsive: md:col-span-2, lg:col-span-3 -->
```

**Auto-fit (grillas dinámicas):**

```html
<div class="auto-fit-xs">Mín 120px</div>
<div class="auto-fit-sm">Mín 200px</div>
<div class="auto-fit-md">Mín 280px</div>
<div class="auto-fit-lg">Mín 360px</div>
```

---

### 6. Flex — Utilidades flexbox

```html
<div class="f-row">Horizontal</div>
<div class="f-col">Vertical</div>
<div class="fx-center">Centrar X</div>
<div class="fy-center">Centrar Y</div>
<div class="fxy-center">Centrar todo</div>
<div class="fx-between">Space between</div>
<div class="f-wrap">Wrapping</div>
<div class="f-1">Flex 1</div>
<div class="f-grow">Grow</div>
<div class="f-shrink-0">No shrink</div>
<!-- Responsive: md:f-row, lg:fx-center, etc. -->
```

---

### 7. Text Size Utilities — Tipografía fluida

Usar SOLO cuando el tamaño default del elemento no es suficiente:

| Clase       | Rango fluido       | Uso típico                      |
| ----------- | ------------------ | ------------------------------- |
| `text-2xs`  | 0.625rem → 0.75rem | Microtext, disclaimers          |
| `text-xs`   | 0.7rem → 0.8rem    | Small labels                    |
| `text-sm`   | 0.8rem → 0.95rem   | Pre-headlines, captions         |
| `text-base` | 0.9rem → 1.1rem    | _(ya asignado a `p` en styles)_ |
| `text-md`   | 1rem → 1.2rem      | Subtítulos ligeros              |
| `text-lg`   | 1.125rem → 1.4rem  | Subtítulos prominentes          |
| `text-xl`   | 1.25rem → 1.65rem  | Headlines secundarios           |
| `text-2xl`  | 1.5rem → 2.25rem   | Headlines medianos              |
| `text-3xl`  | 2rem → 2.75rem     | Hero subtítulos                 |
| `text-4xl`  | 2.5rem → 3.5rem    | Hero títulos                    |

**Regla de oro:** `p` ya tiene `text-base` definido en `styles.css`. `h1-h3` ya tienen su `font-size` con `clamp()` en `styles.css`. Solo usar `text-*` cuando necesitás un tamaño **diferente** al que el elemento ya tiene.

---

### 8. Otros Utilities

```html
<!-- Max width -->
<div class="maxw-sm">40rem</div>
<!-- md:maxw-md, lg:maxw-lg disponibles -->

<!-- Viewport heights -->
<div class="min-h-screen">100dvh mínimo</div>

<!-- Aspect ratio -->
<div class="ratio ratio--square">1:1</div>
<div class="ratio ratio--landscape">16:9</div>

<!-- Full-bleed -->
<div class="bleed">Full viewport width</div>
```

---

## Patrón de Maquetación — Ejemplo Completo

```html
<!-- Sección con fondo oscuro, centrada, espaciado medio -->
<section id="hero" class="rhythm--md">
  <div class="frame--md flow--sm">
    <p class="text-sm pre-headline">Texto pequeño introductorio</p>
    <h1>Título Principal Grande</h1>
    <p class="text-md subtitle">Subtítulo descriptivo</p>

    <!-- Card con 2 columnas -->
    <div class="hero-cta cols-1 md:cols-2 gap-none">
      <div class="hero-cta__media">
        <img src="img/producto.png" alt="Descripción" />
      </div>
      <div class="hero-cta__content stack--md">
        <h3 class="text-xl">Headline del CTA</h3>
        <p>Descripción (sin clase extra, p ya tiene su tamaño)</p>
        <a href="#" class="btn btn--primary">Acción</a>
      </div>
    </div>
  </div>
</section>

<!-- Sección con fondo blanco, pasos numerados -->
<section id="pasos" class="rhythm--md">
  <div class="frame--md flow--md">
    <div class="stack--xs">
      <h2>Título de Sección</h2>
      <p class="subtitle">Subtítulo sin text-base extra</p>
    </div>

    <div class="cols-1 md:cols-2 gap-lg gy-center">
      <div class="stack--lg">
        <div class="paso stack--xs">
          <h3>Paso 1</h3>
          <p>Descripción sin clases de texto.</p>
        </div>
      </div>
      <div>
        <img src="img/bundle.png" alt="Producto" />
      </div>
    </div>
  </div>
</section>
```

**Notar:** El HTML usa casi exclusivamente clases de `starter.css` para la estructura. Las clases propias del proyecto son mínimas y solo definen estilos visuales (colores, bordes), NO layout.
