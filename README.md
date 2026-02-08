# Diagram & Visualization Workspace

A prompt-driven workflow for creating diagrams, charts, slides, and presentations using AI assistance.

## Project Structure

```
diagram_viz_support/
├── diagrams/          # Mermaid diagrams (.mmd)
├── charts/            # Vega-Lite specs (.vl.json)
├── slides/            # Marp markdown slides (.md)
├── scripts/           # Python scripts for pptx generation
├── outputs/           # Generated files (png, svg, pptx, pdf)
└── .vscode/          # VS Code configuration
```

## Supported Visualization Types

### 1. Mermaid Diagrams (diagrams/)

Create flowcharts, sequence diagrams, ER diagrams, and system architectures.

**Example Prompts:**
- "Create a flowchart showing the user authentication process"
- "Generate a sequence diagram for a REST API request/response cycle"
- "Draw an ER diagram for a blog database with users, posts, and comments"
- "Create a system architecture diagram showing microservices communication"

**Preview:** Use the Mermaid Preview extension in VS Code

**Export:** Use Mermaid CLI or online tools to export to PNG/SVG:
```bash
mmdc -i diagrams/example.mmd -o outputs/example.png
```

### 2. Vega-Lite Charts (charts/)

Create interactive data visualizations with declarative JSON specs.

**Example Prompts:**
- "Create a bar chart comparing Q1-Q4 revenue for 2024"
- "Generate a line chart showing temperature trends over 12 months"
- "Make a scatter plot correlating hours studied vs test scores"
- "Create a pie chart showing market share distribution"

**Preview:** Use the Vega Viewer extension in VS Code

**Export:** Use vega-cli to render charts:
```bash
vl2png charts/example.vl.json outputs/example.png
```

### 3. Marp Slides (slides/)

Create simple, beautiful slide decks using Markdown.

**Example Prompts:**
- "Create a 5-slide presentation introducing our new product"
- "Generate slides explaining the software development lifecycle"
- "Make a deck with our Q4 results including charts and diagrams"
- "Create an onboarding presentation for new engineers"

**Preview:** Use Marp for VS Code extension

**Export:** Marp can export to HTML, PDF, or PPTX:
```bash
marp slides/example.md -o outputs/example.pdf
marp slides/example.md -o outputs/example.pptx
```

### 4. Python-PPTX Presentations (scripts/)

Generate rich, data-driven PowerPoint presentations programmatically.

**Example Prompts:**
- "Create a Python script to generate a sales report presentation with charts"
- "Generate a PPTX with our quarterly metrics including tables and graphs"
- "Make a presentation script that visualizes survey results"
- "Create a data dashboard presentation with matplotlib charts"

**Run Scripts:**
```bash
cd scripts
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
python example_pptx.py
```

## Getting Started

### Prerequisites

1. **VS Code Extensions** (recommended via `.vscode/extensions.json`):
   - Markdown Mermaid for diagram preview
   - Marp for VS Code for slides
   - Vega Viewer for chart preview
   - Python extension

2. **Optional Command-Line Tools**:
   - [Mermaid CLI](https://github.com/mermaid-js/mermaid-cli): `npm install -g @mermaid-js/mermaid-cli`
   - [Vega CLI](https://vega.github.io/vega/usage/): `npm install -g vega vega-lite vega-cli`
   - [Marp CLI](https://github.com/marp-team/marp-cli): `npm install -g @marp-team/marp-cli`

### Workflow

1. **Prompt Claude** with your visualization needs using the example prompts above
2. **Save outputs** to the appropriate directory (diagrams/, charts/, slides/, scripts/)
3. **Preview** in VS Code using the recommended extensions
4. **Export** to outputs/ folder for sharing or embedding
5. **Version control** your source files (git automatically ignores generated outputs)

## Tips for Effective Prompts

- **Be specific** about data, labels, colors, and layout preferences
- **Include sample data** when creating charts or tables
- **Specify the audience** and purpose for slides/presentations
- **Request iterations**: "Make the colors more vibrant" or "Add annotations to highlight X"
- **Combine types**: "Create a Marp slide deck that includes this Mermaid diagram"

## Examples

Check out the example files to see working samples:
- `diagrams/example.mmd` - System architecture flowchart
- `charts/example.vl.json` - Monthly revenue bar chart
- `slides/example.md` - Product overview deck
- `scripts/example_pptx.py` - Automated presentation generator

## Contributing

This workspace is designed to evolve. Add new examples, improve scripts, or extend the workflow to suit your needs.

---

**Happy visualizing! 📊🎨**
