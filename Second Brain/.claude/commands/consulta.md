Busca en la wiki todo lo relacionado con: $ARGUMENTS

## Proceso

1. Buscar en `wiki/conceptos/` si existe una página del concepto o algún alias que coincida
2. Buscar en `wiki/fuentes/` menciones del término en títulos, resúmenes y conceptos clave
3. Leer los archivos relevantes encontrados

## Formato de respuesta

```
## [Concepto consultado]

**Definición**: [Extraer de la página de concepto si existe]

**Aparece en:**
- [[fuentes/nombre]] — breve contexto de cómo se menciona
- [[fuentes/otro]] — breve contexto

**Conceptos relacionados:** [[concepto-1]], [[concepto-2]]

**Ideas clave:**
- Punto relevante extraído de las fuentes
- Otro punto relevante
```

Si no hay resultados, responder:

> El concepto "[término]" no está en la wiki todavía. Añade fuentes relacionadas a `raw/` y pídeme que las ingeste.
