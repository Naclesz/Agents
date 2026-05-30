# Agents

Colección de agentes y herramientas de IA diseñados para automatizar y asistir en distintas tareas del día a día. Cada agente está configurado para trabajar con [Claude Code](https://github.com/anthropics/claude-code) y puede usarse de forma independiente.

## Agentes Disponibles

### Second Brain

Wiki personal para organizar conocimiento de lecturas: artículos, libros, tweets, videos y podcasts.

**Finalidad:** Convertir el consumo pasivo de contenido en conocimiento estructurado y conectado. Claude actúa como motor de ingesta que analiza las fuentes, extrae conceptos clave, genera resúmenes y mantiene las conexiones entre ideas.

**Cómo funciona:**

1. Guardas el contenido en `raw/` con un formato YAML básico (título, URL, autor)
2. Pides a Claude que ingeste el archivo
3. Claude genera automáticamente:
   - Resumen de la fuente en `wiki/fuentes/`
   - Páginas de conceptos en `wiki/conceptos/`
   - Actualización del índice y log

**Uso básico:**

```
# Ingestar una fuente nueva
> Ingesta articulo-sobre-llms.md

# Ver qué hay pendiente de procesar
> Lista pendientes

# Buscar en la wiki
> /consulta machine learning
```

**Requisitos:**
- [Claude Code](https://github.com/anthropics/claude-code) instalado
- Ejecutar Claude Code desde el directorio `Second Brain/`

**Compatibilidad:** Los archivos generados usan wikilinks (`[[concepto]]`) compatibles con [Obsidian](https://obsidian.md/).
