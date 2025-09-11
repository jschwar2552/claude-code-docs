# Claude Code Documentation System

[![Last Update](https://img.shields.io/github/last-commit/jschwar2552/claude-code-docs/main.svg?label=docs%20updated)](https://github.com/jschwar2552/claude-code-docs/commits/main)
[![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Linux-blue)](https://claude.ai/code)

*Created by Jason Schwartz at Anthropic*

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
- **Enterprise FAQ**: Common technical questions from customer implementations
- **Team Rollout Guide**: Internal process guidance for successful adoption
- **Engineering Best Practices**: Proven development workflow patterns
- **Research Insights**: Data on Claude Code's impact on software development
- **GTM Workflows**: Sales and marketing team integration patterns
- **Anthropic Usage Examples**: How our internal teams use Claude Code

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

- **Installation**: Installs to `~/.claude-code-docs` with `/docs` slash command
- **Auto-updating**: Official docs sync automatically, preserves custom content
- **Platform support**: macOS and Linux (Windows not yet supported)
- **Dependencies**: git, jq, curl (usually pre-installed)
- **Architecture**: Local files + git-based updates, no external API calls

## System Requirements

- **Claude Code**: Must be installed and configured
- **Operating System**: macOS or Linux  
- **Dependencies**: git, jq, curl (typically pre-installed)
- **Disk Space**: ~50MB for complete documentation

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

## Distribution

This system is designed for:
- **Internal Anthropic teams**: Enhanced productivity and consistent responses
- **Customer onboarding**: Self-service documentation and Q&A
- **Partner enablement**: Comprehensive reference for implementation support

## Technical Architecture

Based on [ericbuess/claude-code-docs](https://github.com/ericbuess/claude-code-docs) with:
- Enhanced content management and version control
- Improved search and categorization
- Custom content integration while preserving official doc updates
- Streamlined installation and distribution

## Support

- **GitHub Issues**: [Report issues or request features](https://github.com/jschwar2552/claude-code-docs/issues)
- **Original System**: [ericbuess/claude-code-docs](https://github.com/ericbuess/claude-code-docs)
- **Official Documentation**: [docs.anthropic.com/claude-code](https://docs.anthropic.com/en/docs/claude-code)

---

*This system enables Claude Code to provide better self-service support by leveraging curated, searchable documentation directly within the development environment.*