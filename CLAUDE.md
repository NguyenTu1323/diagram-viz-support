# Project Instructions for Claude

This file contains persistent instructions and preferences for this project. Claude will automatically read and follow these guidelines.

## General Preferences

### Currency & Formatting
- **Number Format**: ask to use B or G with billion or giga

### Chart Preferences
- Use Vega-Lite for data visualizations
- Always include tooltips with full values
- Use clear, readable axis labels with proper units
- Default chart colors: Professional blues and earth tones
- Include proper titles and descriptions

### Diagram Preferences
- Use Markdown files with Mermaid code blocks (`.md` not `.mmd`)
- Include documentation around diagrams explaining the architecture

### Slide Preferences
- Use Marp for presentations
- **Do not use Mermaid diagrams** in Marp slides (not supported)
- Use ASCII art, tables, or text layouts instead
- Keep slides clean and professional

## File Organization

- **Diagrams**: `diagrams/*.md` - Mermaid diagrams in markdown
- **Charts**: `charts/*.vl.json` - Vega-Lite specifications
- **Slides**: `slides/*.md` - Marp slide decks
- **Scripts**: `scripts/*.py` - Python presentation generators
- **Outputs**: `outputs/` - Generated files (gitignored)

## Common Tasks

### Creating Charts
- Ask about data type and visualization goal first
- Default to bar charts for comparisons, line charts for trends
- Include tooltips with full precision values

### Creating Diagrams
- Use appropriate Mermaid diagram type (flowchart, sequence, ER, etc.)
- Add styling with colors for different components
- Include documentation explaining the diagram
- Save as `.md` files with mermaid code blocks

### Git Commits
- Use conventional commit format: `type: description`
- Types: feat, fix, docs, style, refactor, test, chore

## Notes

- This is a visualization workspace - focus on creating clear, accurate visual representations
- Always verify data formats and units before creating visualizations
- When in doubt, ask for clarification rather than making assumptions
