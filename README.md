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
