# Claude Code Documentation System

[![Last Update](https://img.shields.io/github/last-commit/jschwar2552/claude-code-docs/main.svg?label=docs%20updated)](https://github.com/jschwar2552/claude-code-docs/commits/main)
[![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Linux-blue)](https://claude.ai/code)

## Purpose

This system enables **agentic search** within Claude Code by providing local access to curated documentation. It allows Claude to quickly reference verified information when responding to questions about Claude Code usage, troubleshooting, and implementation best practices.

### Why This Exists

When working with Claude Code, users often need quick answers to common questions: "How do I set up hooks?" "What's the difference between MCP and direct tool integration?" "How do I structure my CLAUDE.md file?" Rather than requiring manual searches through documentation or waiting for human responses, this system lets Claude provide immediate, accurate answers from approved sources.

The documentation includes:
- **All official Claude Code documentation** (auto-updating from anthropic.com)
- **Approved internal resources** for GTM and product communications teams
- **Verified troubleshooting guides** and implementation patterns

## How It Works

1. **Install once**: Simple one-command installation via GitHub or zip package
2. **Instant access**: Claude can query documentation via `/docs [topic]` commands
3. **Always current**: Official docs auto-sync, internal docs version-controlled
4. **Searchable**: Natural language search across all documentation

## Use Cases

### For Anthropic Teams
- **Support teams**: Quick, consistent responses from verified sources
- **GTM teams**: Approved talking points and customer resources at hand
- **Engineering**: Reference implementation patterns and troubleshooting

### For Claude Code Users
- **Self-service Q&A**: Let Claude answer common questions during onboarding
- **Troubleshooting**: Get help with setup, configuration, and usage issues
- **Best practices**: Learn proven patterns for hooks, MCP, CLAUDE.md files, etc.

## Available Documentation

### Official Claude Code Documentation
All content from [docs.anthropic.com/claude-code](https://docs.anthropic.com/en/docs/claude-code):
- Quickstart guides and setup
- Hooks, MCP, and integrations  
- Security, authentication, and enterprise features
- SDK documentation and CLI reference
- Troubleshooting and best practices

### Enhanced Resources
Additional approved content for team and customer use:

- **Enterprise FAQ** (`/docs enterprise-faq`)
  - Common technical questions from customer implementations and pilots
  - Troubleshooting for Opus access, Visual Studio integration, SSO setup
  - Security and compliance concerns with detailed responses
  - Cost management and usage optimization guidance
  - Authentication issues and API configuration problems

- **Team Rollout Guide** (`/docs team-rollout-guide`)
  - Complete sales process framework for Claude Code opportunities
  - Pilot engagement strategies and success metrics
  - Competitive positioning against GitHub Copilot and Cursor
  - Objection handling for security, cost, and integration concerns
  - ROI calculation frameworks and business value messaging

- **Engineering Best Practices** (`/docs engineering-best-practices`)
  - CLAUDE.md file structure and configuration patterns
  - Effective workflow strategies for different development scenarios
  - Testing patterns and debugging techniques with Claude Code
  - Advanced features like hooks, MCP servers, and custom integrations
  - Performance optimization and context management

- **Research Insights** (`/docs research-software-development-impact`)
  - Quantitative data on Claude Code's impact on development velocity
  - User behavior patterns: automation vs augmentation usage
  - Industry adoption trends and demographic analysis
  - Productivity metrics and workflow transformation patterns

- **GTM Workflows** (`/docs gtm-workflows`)
  - Salesforce MCP integration for customer tracking and reporting
  - Google Workspace automation for proposal and content generation
  - BigQuery integration for usage analytics and business intelligence
  - Sales enablement and marketing automation workflows

- **Anthropic Usage Examples** (`/docs anthropic-teams-usage`)
  - Real examples from Anthropic engineering, product, and research teams
  - Codebase navigation and legacy code modernization patterns
  - Testing automation and debugging workflow examples
  - Cross-team collaboration and knowledge sharing practices

## Installation

### Option 1: Direct from GitHub (Recommended)
```bash
curl -fsSL https://raw.githubusercontent.com/jschwar2552/claude-code-docs/main/install.sh | bash
```

### Option 2: Download and Install
1. Download the latest release zip
2. Extract and run `./install.sh`

## Usage Examples

```bash
# Common questions during onboarding
/docs how do I set up hooks?
/docs what is a CLAUDE.md file and how do I use it?
/docs how do I configure MCP servers?

# Troubleshooting
/docs my hooks aren't working
/docs claude code is not finding my tools
/docs authentication issues

# Discovery and learning
/docs what are some examples of good CLAUDE.md files?
/docs how do other teams use Claude Code?
/docs what are the best practices for enterprise deployment?
```

## Technical Details

**Why Local Documentation vs Web Fetch?**
- **Speed**: Reading from local files (~0.1s) vs web fetches (2-5s per request)
- **Reliability**: Works offline, no API rate limits or network issues
- **Context preservation**: Claude can reference multiple docs without separate API calls
- **Search capability**: Full-text search across all documentation instantly

**How It Works:**
- **Python scraper**: Runs every 3 hours via GitHub Actions to fetch latest docs from anthropic.com
- **Local installation**: Documents stored at `~/.claude-code-docs` with `/docs` slash command
- **Auto-sync**: Git-based updates preserve custom content while syncing official changes
- **Instant access**: Claude reads directly from local markdown files using standard Read tool

**Architecture:**
- Official docs: Automatically scraped from docs.anthropic.com and committed to repo
- Enhanced content: Version-controlled alongside official docs
- Distribution: Single git repository with installer script
- Updates: Pull-based sync preserves local modifications

## Updating

The system automatically updates official documentation. For enhanced content updates:

```bash
cd ~/.claude-code-docs && git pull
```

Or re-run the installer:
```bash
curl -fsSL https://raw.githubusercontent.com/jschwar2552/claude-code-docs/main/install.sh | bash
```

## Uninstalling

```bash
/docs uninstall
```

Or manually:
```bash
~/.claude-code-docs/uninstall.sh
```


## Technical Notes

Based on [ericbuess/claude-code-docs](https://github.com/ericbuess/claude-code-docs) with additional curated content and improved integration.


---

*This system enables Claude Code to provide better self-service support by leveraging curated, searchable documentation directly within the development environment.*