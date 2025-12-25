# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is Blessings Mambwe's resume repository with web automation capabilities. The project integrates with Notion for content management and Chrome/Playwright for automated testing and screenshots.

## MCP Server Integration

This project uses the following MCP servers:

### Notion
- Access resume content and project tracking in Notion workspace
- Query databases for experience, projects, and skills
- Update resume sections directly from Notion

### Playwright/Chrome
- Automated browser testing for web portfolio
- Screenshot generation for documentation
- Web scraping for research and content gathering

## File Structure

- `BMambwe.tex` - LaTeX source file for the resume
- `BMambwe.pdf` - Compiled PDF output
- `.mcp.json` - MCP server configuration
- `.claude/settings.json` - Claude Code project settings
- `.env` - Environment variables (gitignored, use `.env.example` as template)

## Building the Resume

To compile the LaTeX document to PDF:

```bash
pdflatex BMambwe.tex
```

Note: Requires a LaTeX distribution (e.g., TeX Live, MiKTeX) with the following packages:
- Standard packages: `inputenc`, `babel`, `geometry`, `hyperref`
- Font packages: `fontawesome`, `marvosym`, `pifont`, `adforn`
- Graphics packages: `tikz`, `graphicx`, `eso-pic`
- Specialized packages: `skak` (chess symbols)

## MCP Server Setup

### Prerequisites
1. Node.js 18+ installed
2. Notion API key from https://www.notion.so/my-integrations
3. Chrome/Chromium browser for Playwright

### Configuration
1. Copy `.env.example` to `.env` and add your Notion API key
2. MCP servers are configured in `.mcp.json`
3. Use `@notion:` prefix to reference Notion resources
4. Playwright commands available for browser automation

## Document Architecture

The resume uses a custom LaTeX template with:
- Custom commands for consistent formatting (`\resumeSubheadingFour`, `\resumeJobSubheadingD`, etc.)
- Two-column header layout (name/intro on left, contact info on right)
- Sections: Skills, Experience, Open-Source Projects, Education
- Hyperlinked references using custom underline styling via TikZ (`\myHref`)

## Key Custom Commands

- `\mytitle`, `\intro` - Header content
- `\email`, `\linkedin`, `\github` - Contact information with icons
- `\resumeJobSubheadingD` - Job entry formatting
- `\resumeItemCustom` - Bullet point items
- `\myHref[url]{text}` - Custom dotted underline hyperlinks

## Editing Guidelines

When modifying the resume:
- Maintain consistent date format: "MMM YYYY -- MMM YYYY | Location"
- Keep bullet points action-oriented and quantified where possible
- Preserve the custom spacing commands (`\vspace`) for layout consistency
- Use `\resumeItemCustom{}` for experience bullet points
- Links should use `\href{url}{text}` or the custom `\myHref` command

## Automation Workflows

- Use Notion to manage resume content, then sync to LaTeX
- Generate PDF previews automatically with pdflatex
- Take screenshots of portfolio websites using Playwright
- Update GitHub repository after significant changes
