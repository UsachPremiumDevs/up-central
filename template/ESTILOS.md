# Guía de Estilos — Plantilla Institucional Usach Premium

Este documento explica el sistema de estilos usado en `guia-institucional.tex`,
derivado del análisis de `guia1` (estilo formal) y `guia3` (estilo premium).

---

## Origen de los estilos

| Elemento | Fuente |
|---|---|
| Marca de agua con logo transparente | `guia1` |
| Variables globales de configuración (`\curso`, `\guiasnumero`, etc.) | `guia1` |
| Paleta de colores azul/celeste | `guia3` |
| Header con logos + minipage | `guia3` |
| Portada con `tcolorbox` de contenidos | `guia3` |
| Cajas `tcolorbox` para secciones | `guia3` |
| `multicol` para ejercicios en columnas | `guia3` |
| Entornos `ejercicios` / `soluciones` / `introduccion` | `guia1` |
| Desafío especial con caja estilizada | `guia3` |

---

## Colores institucionales

```latex
\definecolor{celesteSuave}{HTML}{F0F7FF}   % Fondo de cajas (azul muy suave)
\definecolor{azulFuerte}{HTML}{1A5276}     % Azul principal (bordes, títulos, links)
\definecolor{turquesaUsach}{HTML}{33CCCC}  % Acento turquesa (uso decorativo)
\definecolor{enlace}{HTML}{1A5276}         % Color de hyperlinks
```

---

## Variables de configuración

Todas en el bloque `INFORMACIÓN DE LA GUÍA` cerca del inicio del `.tex`:

| Comando | Uso |
|---|---|
| `\institucion` | Nombre de la institución (ej: "Usach Premium") |
| `\curso` | Nombre del curso (ej: "Cálculo I") |
| `\guiasnumero` | Número y título de la guía (ej: "Guía 1 - Trigonometría") |
| `\semestre` | Período académico (ej: "1er. Semestre de 2026") |
| `\preparadopor` | Autor o institución (ej: "Marcos Montenegro") |
| `\webinstitucion` | URL sin protocolo (ej: "www.usachpremium.cl") |
| `\instagraminstitucion` | URL completa de Instagram |
| `\transparencia` | Opacidad de la marca de agua (0.0 a 1.0, recomendado 0.05) |
| `\fraseportada` | Frase que aparece en el pie de página |
| `\listacontenidos` | Items `\item[...]` para el tcolorbox de contenidos en portada |

---

## Encabezado y pie de página

El encabezado tiene **3 zonas**:

```
[Logo UP]           [nombre institución + curso + @instagram]   [Logo USACH]
────────────────────────────────────────────────────────────────────────────
```

El pie de página:

```
["frase motivacional"]                                         [Página N]
────────────────────────────────────────────────────────────────────────────
```

La portada usa `\thispagestyle{plain}` para suprimir header/footer.

---

## Marca de agua

El comando `\MarcaAgua` coloca el logo con transparencia al centro de la página.
Se llama **dentro de los entornos** `introduccion`, `ejercicios` y `soluciones`
para que se active a partir de esas secciones (no en la portada).

```latex
\newcommand{\MarcaAgua}{
    \AddToShipoutPicture{
        \AtPageCenter{
            \makebox(0,0){%
                \transparent{\transparencia}%
                \includegraphics[width=0.7\textwidth]{\logofondo}%
            }
        }
    }
}
```

---

## Cajas tcolorbox

### `kitpropiedades` — Kit de propiedades / resumen
- Fondo: `celesteSuave`
- Borde: `azulFuerte`
- Se usa para el resumen de fórmulas antes de los ejercicios.

```latex
\begin{kitpropiedades}{Título de la caja}
    Contenido (puedes usar multicol, itemize, etc.)
\end{kitpropiedades}
```

### `desafiobox` — Problema aplicado / desafío
- Fondo: blanco
- Borde: `azulFuerte` con sombra
- Título blanco sobre azul
- Se usa al final de la sección de ejercicios para el problema integrador.

```latex
\begin{desafiobox}{DESAFÍO: Título}
    Contenido del problema.
\end{desafiobox}
```

### `solbox` — Bloque de solucionario
- Fondo: `celesteSuave`
- Borde: `azulFuerte`
- Se usa dentro del entorno `soluciones` para agrupar respuestas por sección.

```latex
\begin{solbox}{I. Soluciones — Primera Sección}
    \begin{enumerate}[...] ... \end{enumerate}
\end{solbox}
```

---

## Entornos de sección

| Entorno | Efecto |
|---|---|
| `introduccion` | Activa `\section*{Introducción}` + marca de agua |
| `ejercicios` | Activa marca de agua (sin `\section*`) |
| `soluciones` | `\newpage` + banner "SOLUCIONARIO" en tcolorbox azul + `\small` + marca de agua |

---

## Estructura de columnas para ejercicios

| Tipo de ejercicio | Columnas recomendadas |
|---|---|
| Ejercicios muy cortos (cálculo directo) | `\begin{multicols}{4}` |
| Ejercicios medianos | `\begin{multicols}{2}` |
| Ejercicios con desarrollo o sub-ítems | Sin multicol (1 columna) |
| Solucionario compacto | `\begin{multicols}{5}` |

---

## Imágenes

Coloca los archivos en `./images/` relativo al `.tex`:

```
tu-guia/
├── tu-guia.tex
└── images/
    ├── logo_up.png
    ├── logo_usach.png
    └── IMAGEN_PORTADA.png   (opcional)
```

Los logos master están en:
- `1-2026/nivel-1/calculo-1/guías/guia1/images/logo_up.png`
- `1-2026/nivel-1/calculo-1/guías/guia1/images/logo_usach.png`

---

## Compilación

```bash
pdflatex guia-institucional.tex
pdflatex guia-institucional.tex   # segunda pasada para referencias
```

O con latexmk:

```bash
latexmk -pdf guia-institucional.tex
```

---

## Checklist antes de imprimir

- [ ] Editar `\curso`, `\guiasnumero`, `\semestre`, `\preparadopor`
- [ ] Rellenar `\listacontenidos` con los temas reales
- [ ] Copiar logos a `./images/`
- [ ] Reemplazar ejercicios de ejemplo por los reales
- [ ] Rellenar el solucionario
- [ ] Compilar 2 veces con pdflatex
- [ ] Revisar que la marca de agua no tape el texto (ajustar `\transparencia`)
