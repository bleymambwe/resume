# Blessings Mambwe - Resume

LaTeX resume with Claude Code integration for automated content management and web automation.

## Features

- **LaTeX Resume**: Professional CV template with custom formatting
- **Notion Integration**: Manage resume content via Notion workspace
- **Browser Automation**: Screenshot generation and web testing with Playwright
- **Version Control**: Git-based workflow with GitHub

## Quick Start

### Prerequisites

1. **LaTeX Distribution**: Install TeX Live or MiKTeX
2. **Node.js**: Version 18 or higher
3. **Notion API Key**: Get from [Notion Integrations](https://www.notion.so/my-integrations)
4. **Claude Code**: Install from [claude.ai/code](https://claude.ai/code)

### Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/bleymambwe/resume.git
   cd resume
   ```

2. **Configure environment variables**:
   ```bash
   cp .env.example .env
   # Edit .env and add your Notion API key
   ```

3. **Start Claude Code**:
   ```bash
   claude
   ```

4. **Authenticate MCP servers**:
   ```
   /mcp
   ```
   Follow the browser prompts to authenticate with Notion.

### Building the Resume

Compile the LaTeX source to PDF:

```bash
pdflatex BMambwe.tex
```

Output: `BMambwe.pdf`

## MCP Server Configuration

This project uses Model Context Protocol (MCP) servers for enhanced functionality:

### Notion
- **Purpose**: Content management and database queries
- **Usage**: Reference Notion pages with `@notion:` prefix
- **Authentication**: OAuth via browser

### Playwright
- **Purpose**: Browser automation and testing
- **Usage**: Take screenshots, automate web interactions
- **Configuration**: Runs in non-headless mode by default

MCP servers are configured in `.mcp.json` and automatically loaded when Claude Code starts.

## Project Structure

```
resume/
├── .claude/
│   ├── settings.json          # Claude Code project settings
│   └── CLAUDE.md              # Project documentation for Claude
├── .mcp.json                  # MCP server definitions
├── .env.example               # Environment variables template
├── .gitignore                 # Git ignore rules
├── BMambwe.tex                # Resume LaTeX source
├── BMambwe.pdf                # Compiled resume PDF
└── README.md                  # This file
```

## Usage with Claude Code

Once set up, you can use Claude Code to:

- **Query Notion**: "Show me the projects from my Notion database"
- **Update Resume**: "Add my latest job experience to the resume"
- **Generate Screenshots**: "Take a screenshot of my portfolio website"
- **Automate Builds**: "Compile the resume and commit changes"

## LaTeX Template

The resume uses a custom template with:
- Two-column header layout
- FontAwesome icons for contact info
- Custom section formatting
- Hyperlinked references
- TikZ graphics for decorative elements

### Key Commands

- `\resumeJobSubheadingD` - Job experience entry
- `\resumeItemCustom` - Bullet point item
- `\myHref{url}{text}` - Custom dotted underline link

## Contributing

This is a personal resume repository. Feel free to fork and adapt the LaTeX template for your own use.

## License

The LaTeX template is available for personal use. Please credit if you use it as a base for your own resume.

## Contact

- **Email**: bleymambwe@gmail.com
- **LinkedIn**: [linkedin.com/in/bleymambwe](https://linkedin.com/in/bleymambwe)
- **GitHub**: [github.com/bleymambwe](https://github.com/bleymambwe)
