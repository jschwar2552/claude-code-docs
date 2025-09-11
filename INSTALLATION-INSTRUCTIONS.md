# Claude Code Documentation System - Installation Instructions

This system enables Claude Code to provide instant answers to common questions by giving Claude access to curated documentation. Built by Jason Schwartz at Anthropic for team productivity and customer onboarding.

## What This Provides

**Agentic Search for Claude Code**: Enable Claude to instantly answer questions like "How do I set up hooks?" or "What's the best way to structure my CLAUDE.md file?" using verified documentation.

**Documentation included**:
- ✅ **All official Claude Code docs** (auto-updating from anthropic.com)
- ✅ **Enterprise FAQ** - Common technical questions and solutions
- ✅ **Implementation guides** - Proven patterns for hooks, MCP, CLAUDE.md
- ✅ **Troubleshooting resources** - Solutions to common setup issues  
- ✅ **Best practices** - How Anthropic teams use Claude Code effectively
- ✅ **Research insights** - Data on Claude Code's development impact

## Quick Installation

### Option 1: Direct from GitHub (Recommended)
```bash
curl -fsSL https://raw.githubusercontent.com/jschwar2552/claude-code-docs/main/install.sh | bash
```

### Option 2: From Zip Package

1. **Extract the zip file**:
   ```bash
   unzip claude-code-docs-enhanced-v1.0.zip
   cd claude-code-docs-enhanced
   ```

2. **Run the installer**:
   ```bash
   ./install.sh
   ```

## What the Installation Does

1. **Installs to `~/.claude-code-docs`** (standard location)
2. **Creates `/docs` slash command** for Claude Code
3. **Sets up auto-updating** for official docs (custom content preserved)
4. **Integrates with existing workflow** - no breaking changes

## Using Your Enhanced Docs

### New Enhanced Content
```bash
/docs enterprise-faq          # Technical FAQ & troubleshooting
/docs team-rollout-guide      # Internal team rollout process  
/docs engineering-best-practices  # Engineering workflow guidance
/docs gtm-workflows           # Sales and marketing workflows
/docs research-impact         # Development impact research
/docs anthropic-teams         # How Anthropic teams use Claude Code
```

### All Original Commands Still Work
```bash
/docs hooks                   # Official hooks documentation
/docs mcp                     # Model Context Protocol
/docs security               # Security guidelines
/docs -t                     # Check sync status
/docs what's new             # Recent changes
```

## Verification

After installation, verify everything works:

```bash
# Check that enhanced content is available
/docs enterprise-faq

# Verify official docs still work  
/docs hooks

# Check all available topics
/docs
```

You should see both official and enhanced content in the topic list.

## System Requirements

- **Operating System**: macOS or Linux
- **Dependencies**: git, jq, curl (usually pre-installed)
- **Claude Code**: Must be installed and configured

## Use Cases

### For Anthropic Teams
- **Consistent responses**: Support teams get quick, accurate answers from verified sources
- **GTM enablement**: Sales and Customer Success have approved resources at hand
- **Engineering productivity**: Reference proven patterns and troubleshooting solutions

### For Claude Code Users  
- **Self-service onboarding**: Claude answers common setup and usage questions
- **Instant troubleshooting**: Get help with hooks, MCP servers, authentication, etc.
- **Best practice discovery**: Learn from proven implementation patterns

### For Customer Deployment
- **Onboarding acceleration**: Reduce time-to-value with guided Claude Code setup
- **Reduced support burden**: Users can self-serve answers to common questions
- **Knowledge retention**: All troubleshooting and guidance captured in searchable form

## Troubleshooting

### Installation Issues
If installation fails:
```bash
# Check dependencies
git --version && jq --version && curl --version

# Manual installation
git clone https://github.com/jschwar2552/claude-code-docs.git ~/.claude-code-docs-manual
cd ~/.claude-code-docs-manual && ./install.sh
```

### Command Not Found
If `/docs` doesn't work:
```bash
# Restart Claude Code
# Check command file exists
ls ~/.claude/commands/docs.md

# Re-run installer if needed  
curl -fsSL https://raw.githubusercontent.com/jschwar2552/claude-code-docs/main/install.sh | bash
```

### Missing Enhanced Content
If only official docs appear:
```bash
# Check installation source
grep "jschwar2552" ~/.claude/commands/docs.md

# Should show github.com/jschwar2552/claude-code-docs
# If not, re-run installation
```

## Updating

The enhanced docs system automatically updates official content while preserving custom additions. To get the latest enhanced content:

```bash
cd ~/.claude-code-docs && git pull
```

Or re-run the installer:
```bash
curl -fsSL https://raw.githubusercontent.com/jschwar2552/claude-code-docs/main/install.sh | bash
```

## Uninstalling

To completely remove:
```bash
/docs uninstall
```

Or manually:
```bash
rm -f ~/.claude/commands/docs.md
rm -rf ~/.claude-code-docs
# Remove hooks from ~/.claude/settings.json
```

## Support

- **GitHub Issues**: https://github.com/jschwar2552/claude-code-docs/issues
- **Original Project**: https://github.com/ericbuess/claude-code-docs
- **Official Docs**: https://docs.anthropic.com/en/docs/claude-code

## License & Attribution

- **Enhanced content**: Created for internal team use and customer success
- **Original system**: Based on ericbuess/claude-code-docs (open source)
- **Official documentation**: Copyright Anthropic

---

🎉 **Ready to go!** Your enhanced Claude Code documentation system is now installed and ready to use.

Try `/docs enterprise-faq` to get started with the enhanced content!