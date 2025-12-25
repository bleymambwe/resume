# Hunt - AI-Powered Job Search Platform

Intelligent job hunting system combining resume management, application tracking, and automation for landing roles at top global tech companies.

**Current Status**: AI & Automation Engineer at Stanbic Bank
**Target**: Senior ML/AI Engineer roles at Google, Anthropic, Stripe, and top fintech/AI companies
**Location**: Zambia → Global (Remote/Visa Sponsorship)

## Features

### 🎯 Job Search & Tracking
- **Hunt Tracker**: Notion-powered application pipeline management
- **Smart Matching**: AI-powered resume-to-job fit scoring
- **Platform Database**: Curated list of simple-application job sites
- **Application Automation**: Streamlined workflows for high-volume applications

### 📄 Resume Management
- **LaTeX Resume**: Professional CV template with custom formatting
- **Version Control**: Git-based workflow with GitHub
- **PDF Generation**: Automated compilation and updates

### 🤖 Automation Tools
- **Notion Integration**: Track applications, interviews, and follow-ups
- **Browser Automation**: Playwright for job site navigation and screenshots
- **Email Monitoring**: Track application responses
- **Analytics**: Success rate tracking by platform and company type

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

## Job Hunt Workflow

### 1. Set Up Hunt Tracker (One-time)
1. Follow instructions in `NOTION_SETUP.md`
2. Create Hunt Tracker database in Notion
3. Import template with top companies
4. Connect integration to the page

### 2. Research & Strategy (Read First)
- Open `JOB_SEARCH_STRATEGY.md` for comprehensive guide
- Review ranked job platforms (by application simplicity)
- Understand your resume match scores for different roles
- Plan weekly application targets

### 3. Daily Workflow
```
1. Browse job platforms (LinkedIn Easy Apply, AngelList, etc.)
2. Ask Claude: "Analyze this job and rate my fit"
3. If 75%+ match: "Add this to Hunt Tracker"
4. Apply through platform (3-5 steps max)
5. Update status in Notion
```

### 4. Weekly Review
```
> Generate weekly application report
> Show applications needing follow-up
> Update interview statuses
> Plan next week's targets (10-15 applications)
```

## Top Job Platforms (Ranked by Simplicity)

| Platform | Steps | Time | Best For |
|----------|-------|------|----------|
| **LinkedIn Easy Apply** | 3 | 3 min | All companies |
| **AngelList** | 3-4 | 5 min | Startups |
| **Anthropic Careers** | 3 | 5 min | AI Safety |
| **Hugging Face Jobs** | 3-4 | 8 min | ML/NLP |
| **Stripe Careers** | 4 | 10 min | Fintech |
| **YC Jobs** | 3 | 5 min | YC companies |

See `JOB_SEARCH_STRATEGY.md` for complete list with visa/remote filters.

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
Hunt/
├── .claude/
│   ├── settings.json          # Claude Code project settings
│   └── CLAUDE.md              # Project documentation for Claude
├── .mcp.json                  # MCP server definitions
├── .env.example               # Environment variables template
├── .gitignore                 # Git ignore rules
├── JOB_SEARCH_STRATEGY.md     # Comprehensive job search guide
├── NOTION_SETUP.md            # Hunt Tracker database setup
├── BMambwe.tex                # Resume LaTeX source
├── BMambwe.pdf                # Compiled resume PDF
├── package.json               # Node.js dependencies
└── README.md                  # This file
```

## Usage with Claude Code

### Job Hunting Commands

- **Track Applications**: "Add this job to Hunt Tracker: [paste URL]"
- **Smart Matching**: "Analyze this job description and rate my fit"
- **Pipeline Status**: "Show me all active applications"
- **Interview Prep**: "What interviews do I have this week?"
- **Follow-ups**: "Which applications need follow-up?"
- **Analytics**: "Generate my weekly application report"

### Resume Management

- **Update Resume**: "Add my latest Stanbic experience to the resume"
- **Compile PDF**: "Build the resume PDF"
- **Version Control**: "Commit resume changes"

### Automation

- **Screenshot Jobs**: "Take screenshots of my portfolio sites"
- **Email Tracking**: "Check for responses from companies"
- **Batch Apply**: "Help me apply to top 5 ML Engineer roles"

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
