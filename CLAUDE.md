# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a personal resume repository containing LaTeX source files for Blessings Mambwe's CV.

## File Structure

- `BMambwe.tex` - LaTeX source file for the resume
- `BMambwe.pdf` - Compiled PDF output

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
