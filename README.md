# up-central

Repositorio para versionar las guías en LaTeX de los distintos ramos que Usach Premium imparte en la universidad.

---

## Estructura de carpetas

```
up-central/
└── {semestre}-{año}/               # Ej: 1-2026 (primer semestre 2026), 2-2026 (segundo semestre 2026)
    ├── nivel-1/                    # Nivel del ramo
    │   ├── nivelacion-mbi/         # Nombre del ramo
    │   │   ├── clase-1/            # Carpeta de la clase (se sube completa a Overleaf)
    │   │   │   ├── clase-1.tex     # Guía principal de la clase (para el alumno)
    │   │   │   ├── miclase.tex     # Archivo interno del ayudante: desarrollo de ejercicios, notas, etc.
    │   │   │   └── images/         # Imágenes usadas en los .tex
    │   │   ├── clase-2/
    │   │   │   └── ...
    │   │   └── ...
    │   ├── algebra-1/
    │   ├── calculo-1/
    │   └── fisica-1/
    ├── nivel-2/
    └── nivel-3/
```

---

## Convenciones de nomenclatura

| Elemento | Formato | Ejemplo |
|---|---|---|
| Carpeta de semestre | `{número semestre}-{año}` | `1-2026`, `2-2026` |
| Carpeta de nivel | `nivel-{N}` | `nivel-1`, `nivel-2` |
| Carpeta de ramo | nombre en minúsculas con guiones y sin tildes | `nivelacion-mbi`, `calculo-1` |
| Carpeta de clase | `clase-{N}` | `clase-1`, `clase-2` |

---

## Archivos dentro de cada clase

Cada carpeta `clase-N/` es una unidad autocontenida pensada para subirse directamente a Overleaf:

- **`clase-N.tex`** — Guía principal de la clase. Es el documento que se entrega o comparte con los alumnos.
- **`miclase.tex`** — Archivo interno del ayudante. Contiene el desarrollo detallado de los ejercicios, notas de pizarra, pauta y cualquier material de apoyo para conducir la clase.
- **`images/`** — Carpeta con todas las imágenes referenciadas en los archivos `.tex` (logos, figuras, etc.).

---

## Cómo agregar una nueva clase

1. Ir a la carpeta del semestre, nivel y ramo correspondiente. Si no existe, créala siguiendo las convenciones de nomenclatura.
2. Crear una carpeta `clase-N/` con el número correlativo.
3. Dentro, crear al menos:
   - `clase-N.tex` con el contenido de la guía.
   - `miclase.tex` con el desarrollo y notas del ayudante.
   - Una carpeta `images/` si se usan recursos gráficos.
4. Commitear los cambios al repositorio.

### Ejemplo: agregar clase 2 de Nivelación MBI, primer semestre 2026

```
1-2026/
└── nivel-1/
    └── nivelacion-mbi/
        └── clase-2/
            ├── clase-2.tex
            ├── miclase.tex
            └── images/
```

### Ejemplo: agregar un ramo nuevo en el segundo semestre 2026

```
2-2026/
└── nivel-2/
    └── calculo-2/
        └── clase-1/
            ├── clase-1.tex
            ├── miclase.tex
            └── images/
```

---

## Flujo de trabajo con Overleaf

La carpeta `clase-N/` está diseñada para subirse completa a un proyecto de Overleaf. El archivo principal que Overleaf debe compilar es `clase-N.tex`. El archivo `miclase.tex` es de uso exclusivo interno del ayudante y no forma parte de la guía pública.
