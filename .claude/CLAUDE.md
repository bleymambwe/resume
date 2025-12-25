# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Hunt** is an AI-powered job application automation system targeting senior ML/AI Engineer roles at top global companies (Google, Anthropic, Stripe, etc.). Built for a Zambian-based AI engineer seeking international remote/visa-sponsored opportunities.

## Core Workflow

### Phase 1: Research & Populate Hunt Tracker
1. **Research job platforms** (LinkedIn, AngelList, company career pages)
2. **Extract job details** (URL, company, role, requirements, application steps)
3. **Add to Hunt Tracker** (Notion database) with:
   - Job URL
   - Company name
   - Role title
   - Notes field containing: required form inputs, qualifications, custom questions
   - Match score (based on resume analysis)
   - Application complexity (3-5 steps preferred)
   - Visa sponsorship status
   - Remote work eligibility

### Phase 2: Automated Application Processing
1. **Browse Hunt Tracker** database in Notion
2. **Filter for**: Status = "Ready to Apply" AND Match Score ≥ 75%
3. **For each job**:
   - Navigate to Job URL using Playwright
   - Read notes field for required inputs
   - **If manual form fields detected**:
     - Extract information from `BMambwe.tex` resume
     - Auto-fill form fields (name, email, experience, etc.)
   - **If resume upload required**:
     - Upload `BMambwe.pdf`
   - **If custom questions detected**:
     - Generate responses using resume context
   - Submit application
   - Update Hunt Tracker status to "Applied"
   - Record application date

### Phase 3: Sync to GitHub
1. **After each session**, commit changes:
   - Updated Hunt Tracker data (JSON export)
   - Resume updates if modified
   - Application logs
2. **Push to GitHub** (https://github.com/bleymambwe/resume)
3. **Ensure repo is ready** for Claude Code Desktop or other workflows

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

### Core Files
- `BMambwe.tex` - LaTeX resume source (extract data from here for applications)
- `BMambwe.pdf` - Compiled resume PDF (upload this to application forms)
- `JOB_SEARCH_STRATEGY.md` - Comprehensive job search guide with platform rankings
- `NOTION_SETUP.md` - Hunt Tracker database setup instructions

### Configuration
- `.mcp.json` - MCP server configuration (Notion + Playwright)
- `.claude/settings.json` - Claude Code project settings
- `.env` - Environment variables (Notion API key)
- `package.json` - Node.js dependencies (Playwright)

### Automation Scripts (to be created)
- `scripts/apply.js` - Main application automation script
- `scripts/extract-resume-data.js` - Parse resume for form filling
- `scripts/notion-sync.js` - Sync Hunt Tracker with local data

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

## Resume Data Extraction

When filling application forms, extract information from `BMambwe.tex`:

### Personal Information
- **Name**: Blessings Mambwe
- **Email**: bleymambwe@gmail.com
- **Phone**: +260 761 233 907
- **Location**: Lusaka, Zambia (GMT+2)
- **LinkedIn**: linkedin.com/in/bleymambwe
- **GitHub**: github.com/bleymambwe

### Current Role
- **Position**: AI & Automation Engineer
- **Company**: Stanbic Bank
- **Duration**: Aug 2025 - Present
- **Location**: Hybrid (Lusaka, Zambia)

### Key Skills
- **Languages**: Dart, Python, Javascript
- **Frameworks**: Flutter, Docker, FastAPI, Pytorch/Tensorflow, Google Cloud, AWS, SQL, Tableau, PowerBI
- **Specializations**: LLMs, RAG systems, Computer Vision, ML infrastructure, Full-stack development

### Top Achievements (for "Why you?" questions)
1. "Automated MT940 statement processing using SQL, Python, and Power Automate, enabling faster reconciliation and supporting a projected $1.3M increase in liability capacity."
2. "Built a secure AI-powered HR conversational interface with governance, compliance, and data-leakage controls for safe enterprise knowledge access."
3. "Developed a full-stack gamified aptitude test platform with anti-LLM safeguards and real-time scoring, helping HR teams save thousands of dollars in screening costs."
4. "Led project management for the myMTN app, collaborating with stakeholders, IT, Group, and third parties to resolve technical issues, introduce new features and drive revenue growth."
5. "Analyzed call center data to identify common queries, redirecting 25% of traffic to the myMTN app, saving $50,000."

### Education
- **Degree**: BEng (Hons) Mechanical Engineering
- **University**: Manchester Metropolitan University
- **Years**: 2015 - 2019
- **Location**: Manchester, UK

### Visa/Work Authorization
- **Current**: Zambian citizen
- **Needs**: Visa sponsorship for US/EU roles OR Remote international work authorization
- **Willing to relocate**: Yes
- **Remote work experience**: Proven (multiple remote positions 2024-2025)

## Automation Workflows

### Daily: Job Research & Hunt Tracker Population
1. Browse job platforms (see JOB_SEARCH_STRATEGY.md for ranked list)
2. For each relevant job:
   - Analyze job description against resume
   - Calculate match score (0-100%)
   - If ≥75%: Add to Hunt Tracker with:
     - Job URL
     - Company, Role
     - Notes: Required form fields, custom questions
     - Status: "Ready to Apply"

### Weekly: Batch Application Processing
1. Query Hunt Tracker: `Status = "Ready to Apply" AND Match Score ≥ 75%`
2. For each job (automated with Playwright):
   - Open Job URL
   - Parse application form
   - Auto-fill from resume data
   - Upload BMambwe.pdf if required
   - Generate custom responses if needed
   - Submit
   - Update Hunt Tracker: Status = "Applied", Application Date = today
3. Commit and push changes to GitHub

### Ongoing: Pipeline Management
- Update interview statuses in Hunt Tracker
- Generate weekly reports (applications sent, responses, interviews)
- Follow up on applications >1 week old
- Sync all data to GitHub for portability
