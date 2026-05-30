# Second Brain Wiki - Instrucciones para Claude

## Propósito

Este es un sistema de wiki personal para organizar conocimiento de lecturas (artículos, libros, tweets, videos, podcasts). Claude actúa como motor de ingesta y mantenimiento de la wiki.

## Estructura

```
Second Brain/
├── raw/                      # Fuentes originales (inmutables tras ingesta)
├── wiki/
│   ├── index.md              # Índice principal por categorías
│   ├── log.md                # Registro cronológico
│   ├── conceptos/            # Páginas de conceptos interconectados
│   └── fuentes/              # Resúmenes de cada fuente ingestada
└── CLAUDE.md                 # Este archivo
```

## Formato de Entrada (raw/\*.md)

```yaml
---
title: "Título del recurso"
source: "https://url-original.com"
author:
  - "[[Nombre Autor]]"
published: YYYY-MM-DD
created: YYYY-MM-DD
description: "Descripción breve"
ingested: false
---
[Contenido, notas o extractos del recurso]
```

## Proceso de Ingesta

Cuando el usuario pida ingestar un archivo específico:

1. **Leer** el archivo de `raw/`
2. **Analizar** el contenido y extraer:
   - Resumen conciso (2-3 párrafos)
   - Conceptos clave (3-7 conceptos)
   - Ideas principales (lista)
   - Categoría(s) apropiada(s)
3. **Crear/Actualizar** página en `wiki/fuentes/[nombre-archivo].md`
4. **Crear/Actualizar** páginas de conceptos en `wiki/conceptos/`
   - Si el concepto no existe, crear página nueva
   - Si existe, añadir referencia a la nueva fuente
5. **Actualizar** `wiki/index.md` añadiendo la fuente a su(s) categoría(s)
6. **Registrar** en `wiki/log.md` con fecha y acción
7. **Marcar** `ingested: true` en el archivo original

## Formato de Página de Fuente (wiki/fuentes/\*.md)

```markdown
---
title: "Título"
source_file: "[[raw/nombre-archivo]]"
url: "https://url-original.com"
author: "[[Nombre Autor]]"
type: articulo | libro | tweet | video | podcast
categories:
  - Categoría1
  - Categoría2
date_published: YYYY-MM-DD
date_ingested: YYYY-MM-DD
---

## Resumen

Párrafo(s) explicando el contenido principal del recurso.

## Conceptos Clave

- [[concepto-1]] - Breve explicación de la relación
- [[concepto-2]] - Por qué es relevante

## Ideas Principales

1. Primera idea importante
2. Segunda idea importante
3. Tercera idea importante

## Citas Destacadas

> "Cita relevante del texto original"

## Conexiones

- Relacionado con [[otra-fuente]]
- Expande ideas de [[concepto-x]]
```

## Formato de Página de Concepto (wiki/conceptos/\*.md)

```markdown
---
title: "Nombre del Concepto"
aliases:
  - alias1
  - alias2
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

## Definición

Explicación clara y concisa del concepto.

## Fuentes

- [[fuentes/articulo-1]] - Contexto de cómo se menciona
- [[fuentes/articulo-2]] - Contexto de cómo se menciona

## Conceptos Relacionados

- [[otro-concepto]]
- [[concepto-relacionado]]
```

## Categorías

Categorías iniciales (crear nuevas según necesidad):

- **Desarrollo** - Programación, arquitectura de software, herramientas de desarrollo
- **Management** - Gestión de equipos, liderazgo, procesos
- **AI Agents** - Agentes de IA, LLMs, automatización inteligente
- **Cocina** - Recetas, técnicas culinarias, gastronomía

Reglas para categorías:

- Si una fuente no encaja en ninguna categoría existente, crear una nueva
- Una fuente puede pertenecer a múltiples categorías
- Los nombres de categoría van en español y con mayúscula inicial

## Convenciones

- **Idioma**: Todo en español de España
- **Links en archivos**: Usar wikilinks `[[nombre-pagina]]` (compatible con Obsidian)
- **Links en respuestas**: Usar rutas reales (`wiki/conceptos/nombre.md`) para que el usuario pueda copiar y abrir directamente
- **Nombres de archivo**: kebab-case sin tildes (`machine-learning.md`, no `Machine Learning.md`)
- **Fechas**: Formato ISO `YYYY-MM-DD`
- **Frontmatter**: Siempre usar YAML válido

## Comandos Comunes

- "Ingesta [nombre-archivo]" → Procesar archivo específico de raw/
- "Lista pendientes" → Mostrar archivos con `ingested: false`
- "Actualiza índice" → Regenerar wiki/index.md
- `/consulta [concepto]` → Slash command para buscar en la wiki
