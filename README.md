# up-central

Repositorio para versionar las guías en LaTeX de los distintos ramos que Usach Premium imparte en la universidad.

---

## Estructura de carpetas

```
up-central/
└── {semestre}-{año}/                        # Ej: 1-2026, 2-2026
    └── nivel-{N}/                           # Ej: nivel-1, nivel-2
        └── {ramo}/                          # Ej: nivelacion-mbi, calculo-1
            ├── guías/
            │   └── guia{N}/                 # Unidad Overleaf: la guía del ramo
            │       ├── {nombre-guia}.tex    # Documento principal de la guía
            │       ├── {nombre-guia}.pdf    # PDF compilado
            │       └── images/              # Imágenes referenciadas en el .tex
            └── ayudantia-{N}/               # Unidad Overleaf: notas del ayudante para esa sesión
                ├── miclase.tex              # Pizarra, desarrollo de ejercicios, pauta interna
                ├── {nombre}.pdf             # PDF compilado de miclase
                └── images/                  # Imágenes referenciadas en miclase.tex
```

**Ejemplo real:**
```
1-2026/nivel-1/
├── calculo-1/
│   └── guías/
│       └── guia1/
│           ├── c1-guia1-nivelacion_mbi.tex
│           ├── c1-guia1-nivelacion_mbi.pdf
│           └── images/
└── nivelacion-mbi/
    └── ayudantia-1/
        ├── miclase.tex
        ├── ayudantia1_productos_notables_pizarra.pdf
        └── images/
```

---

## Convenciones de nomenclatura

| Elemento | Formato | Ejemplo |
|---|---|---|
| Carpeta de semestre | `{número semestre}-{año}` | `1-2026`, `2-2026` |
| Carpeta de nivel | `nivel-{N}` | `nivel-1`, `nivel-2` |
| Carpeta de ramo | minúsculas, guiones, sin tildes | `nivelacion-mbi`, `calculo-1` |
| Carpeta de guía | `guia{N}` | `guia1`, `guia2` |
| Archivo de guía | `c{semestre}-guia{N}-{ramo}.tex` | `c1-guia1-nivelacion_mbi.tex` |
| Carpeta de ayudantía | `ayudantia-{N}` | `ayudantia-1`, `ayudantia-2` |

---

## Diferencia entre guías y ayudantías

| | Guía (`guías/guiaN/`) | Ayudantía (`ayudantia-N/`) |
|---|---|---|
| **Qué es** | Documento con los ejercicios del ramo | Notas internas del ayudante para una sesión |
| **Archivo principal** | `{nombre-guia}.tex` | `miclase.tex` |
| **Uso** | Se entrega o comparte con los alumnos | Solo uso interno del ayudante (pizarra, pauta, desarrollo) |
| **Overleaf** | Se sube la carpeta `guiaN/` completa | Se sube la carpeta `ayudantia-N/` completa |
| **Relación** | Una guía puede usarse en N ayudantías | Cada ayudantía es una sesión específica |

---

## Contenido mínimo de una guía

Toda carpeta `guia{N}/` debe contener al menos:

- `{nombre-guia}.tex` — documento LaTeX principal
- `{nombre-guia}.pdf` — PDF compilado
- `images/` — carpeta de imágenes (puede estar vacía si no se usan)

## Contenido mínimo de una ayudantía

Toda carpeta `ayudantia-{N}/` debe contener al menos:

- `miclase.tex` — pizarra y notas internas del ayudante
- `{nombre}.pdf` — PDF compilado de la pizarra
- `images/` — carpeta de imágenes (puede estar vacía si no se usan)

---

## Template institucional

La carpeta `template/` en la raíz del repo contiene la plantilla oficial de guías de Usach Premium.
**Siempre que se cree una guía nueva, hay que partir desde acá.**

```
template/
├── guia-institucional.tex   ← plantilla compilable lista para usar
├── ESTILOS.md               ← documentación completa del sistema de estilos
└── images/
    ├── logo_up.png
    └── logo_usach.png
```

### Estilos que incluye

| Elemento | Descripción |
|---|---|
| Portada | Logos UP + USACH, título en azul, `tcolorbox` de contenidos, pie con links |
| Encabezado | Logo UP a la izquierda, info institucional + logo USACH a la derecha |
| Pie de página | Frase motivacional a la izquierda, número de página a la derecha |
| Marca de agua | Logo UP con transparencia al centro de cada página interior |
| Colores | `azulFuerte` #1A5276, `celesteSuave` #F0F7FF, `turquesaUsach` #33CCCC |
| Secciones | `\subsection*` libre; cajas `kitpropiedades`, `desafiobox`, `solbox` |
| Solucionario | Banner azul + bloques `solbox` con columnas compactas |

### Cómo usar el template para una guía nueva

1. Copia la carpeta `template/` completa al directorio de la nueva guía:
   ```
   cp -r template/ 1-2026/nivel-1/calculo-1/guías/guiaN/
   mv guiaN/guia-institucional.tex guiaN/{nombre-guia}.tex
   ```
2. Edita solo el bloque **INFORMACIÓN DE LA GUÍA** al inicio del `.tex`:
   ```latex
   \newcommand{\curso}{Cálculo I}
   \newcommand{\guiasnumero}{Guía N - Título}
   \newcommand{\preparadopor}{Nombre Ayudante}
   % ...
   \newcommand{\listacontenidos}{
       \item[\color{azulFuerte}$\Rightarrow$] Tema 1
       ...
   }
   ```
3. Rellena los ejercicios y el solucionario.
4. Compila con `pdflatex` dos veces.

> Ver `template/ESTILOS.md` para la documentación completa de todos los comandos, cajas y convenciones de columnas.

---

## Cómo agregar contenido nuevo

### Nueva guía

1. Dentro del ramo correspondiente, crear `guías/guia{N}/`.
2. Agregar `{nombre-guia}.tex`, compilar y subir el PDF, y la carpeta `images/`.

### Nueva ayudantía

1. Dentro del ramo correspondiente, crear `ayudantia-{N}/`.
2. Agregar `miclase.tex`, compilar y subir el PDF, y la carpeta `images/`.
3. La ayudantía puede referenciar cualquier guía existente — no es necesario crear una nueva guía por cada ayudantía.

### Nuevo ramo o semestre

Crear la carpeta siguiendo la jerarquía `{semestre}-{año}/nivel-{N}/{ramo}/` y luego proceder como arriba.

**Ejemplo — agregar ayudantía 2 de Nivelación MBI reutilizando la guía existente:**
```
1-2026/nivel-1/nivelacion-mbi/
├── guías/guia1/          ← guía ya existente, sin cambios
└── ayudantia-2/          ← nueva carpeta
    ├── miclase.tex
    ├── ayudantia2_pizarra.pdf
    └── images/
```
