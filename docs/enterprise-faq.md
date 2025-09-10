# Claude Code: Most Common Technical Questions

**DRI**: Samuel Flamini, Francis Wilson, Jonathan Dahlberg  
**Status**: Reviewed  
**Last updated**: Sep 5, 2025

## TLDR

As of September 2025, Applied AI is currently having difficulty keeping up with the volume of inbound Claude Code opportunities (particularly for smaller opps < $200k or early stage opps). To fill the gap, we've prepared a set of assets to help support technical discovery and value positioning with your customers.

Below are some of the most common questions that customers ask during a CC pilot/implementation, please refer to these before bringing in AAI.

## Technical FAQ and Answers

### Model Access and Configuration

**Q: Is there a way to disable Opus model access across our entire organization in Claude Code?**

A: Yes, set the Opus rate limit to 0 in your Vertex/Bedrock project settings. For 1P users, this can be configured through rate limiting in the console. Note that even if disabled in Vertex, users may be able to switch models in Claude Code, so rate limiting is the most effective approach.

### IDE Integration

**Q: Does Claude Code support Microsoft Visual Studio IDE integration (not VS Code)?**

A: No current Visual Studio 2022 integration exists. Claude Code currently supports VS Code, Cursor, and other VS Code forks. Visual Studio integration is being considered for the roadmap given it's the #2 most popular IDE on Stack Overflow.

### Automation and CI/CD

**Q: How can we implement PR review automation with Claude Code?**

A: While there isn't a turnkey PR reviewer solution yet, teams are using the Claude Code GitHub Actions integration for automated reviews. The team is working on open-sourcing an internal PR review agent. For now, you can use the security review action as a template and customize it for general PR reviews. This is also a good use case for the Claude Code SDK.

### Authentication and Access

**Q: How do I set up SSO for Claude Code?**

A: We have detailed instructions here, but you need to be on an enterprise plan to enable SSO in the console. For more details on the Enterprise Plan, see here [note to AEs: this doc has a great walkthrough on the Console SSO setup process and covers the bases on several edge cases including permissions issues, custom IdP FAQs, and info on how to test that SCIM is working]

**Q: A user is getting an error message that "Claude Max or Pro is required to connect to Claude Code" but we know that their broader org has access. How should we troubleshoot?**

A: It's likely that this user selected the wrong login method from the setup screen. Can you have them run /login and make sure that they pick the account associated with their primary work email address?

### Data Security and Privacy

**Q: What data is sent to Anthropic when using Claude Code with Bedrock/Vertex API keys?**

A: When configured with Bedrock/Vertex and CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC is set, only essential telemetry is sent. All model API requests go directly to your Bedrock/Vertex endpoints. Review the data flow documentation at docs.anthropic.com/en/docs/claude-code/security for complete details.

**Q: Is there a way to access Claude Code via Bedrock/Vertex without exposing a secret key/access key?**

A: Yes. Our setup guides for Bedrock & Vertex show how you can enable this: for example in the Bedrock case you can run `aws configure` to configure the AWS CLI before adding the necessary configs & running Claude Code with the Bedrock, or you can use Bedrock API keys (a new feature from AWS that enables API keys for Bedrock usage that don't require full AWS credentials).

### Advanced Features

**Q: Is the 1M context window available in Claude Code, and will users be warned about higher pricing?**

A: Long context support is currently in limited EAP for Claude Code users on Max 20x plans, available only to a small number of users. The 1M context window is not generally available for Claude Code users yet, including those accessing Claude via the API.

**Q: Are subagents available in Claude Code SDK and GitHub Actions?**

A: Subagents are available via the Claude Code SDK. They're not yet integrated into GitHub Actions, but this is being considered. The UX collapses outputs when more than 3 subagents run in parallel to manage complexity.

**Q: Can subagents be configured to use specific MCP tools?**

A: Yes, when creating a subagent, you can specify which tools it has access to using the `tools` field in the configuration. In the subagent configuration file, you can either omit the tools field to inherit all tools from the main thread, or you can specify individual tools as a comma-separated list for more granular control. More on this here.

### Enterprise Deployment

**Q: How can we deploy Claude Code with custom environment variables and permissions across our organization?**

A: Create wrapper scripts that set environment variables before running Claude Code. For permissions, use .claude/settings.json files with allow/deny lists. Note that wildcard patterns (*) don't always match as expected - test permissions thoroughly. Enterprise teams often inject standardized Claude.md files for consistent configurations.

**Q: How do we add users to Claude Code when using a Console account?**

A: Add users directly to your Console organization with a dev or Claude Code role - that's all that's needed. Users then run /login from within Claude Code and select the intended Console account. Don't try to manually create API keys in the Claude Code workspace.

### Cost Management

**Q: How can we manage Claude Code costs, especially for automated workflows?**

A: For automated workflows like security reviews, switch from Opus to Sonnet using the claude-model config option for cost savings (with some accuracy tradeoff). Monitor usage through your console dashboard and set appropriate rate limits: note that you can use Workspaces to set more granular spend limits for different user groups - you can learn more about Workspaces here. We also allow you to view spend per API key in the console (see here). Per-user spend caps are coming soon.

### Network and Infrastructure

**Q: Can Claude Code work through corporate proxies like LiteLLM?**

A: Yes, Claude Code supports corporate proxy configurations as long as they support the Anthropic API spec. Follow the proxy setup instructions at docs.anthropic.com/en/docs/claude-code/corporate-proxy. Common issues arise from port restrictions in restricted environments.

### Compliance and Code Scanning

**Q: Does Claude Code have public code filtering or attribution capabilities on the roadmap?**

A: Not currently on the roadmap. Some customers use BlackDuck for code scanning, though feedback on cost and false positives has been mixed. The team is aware this is a blocker for scaling Claude Code to more users and is considering solutions.

### Team Collaboration

**Q: Is there team-based memory or knowledge sharing beyond Claude.md files?**

A: Currently, Claude.md files are the primary mechanism. IT teams can inject standardized Claude.md files into every machine's .claude directory for org-wide configurations. More advanced team memory features are being explored but not yet available.

### Troubleshooting

**Q: Why am I seeing "Workflow validation failed" errors in GitHub Actions?**

A: This typically occurs with reusable workflows. Check that your workflow syntax is correct and that all required parameters are passed. If the error persists, file an issue on github.com/anthropics/claude-code-action with your workflow configuration.

**Q: How do permissions work in Claude Code, and why aren't my allow lists being respected?**

A: Permissions use pattern matching in .claude/settings.json or settings.local.json. Wildcard syntax can be tricky - "Bash(atlassian-api:*)" should work but may need exact command matching. Use "Yes, and don't ask again for similar commands" to build up permissions incrementally. Check both global (~/.claude/settings.json) and local settings files.

### Platform Integration

**Q: Can Claude Code integrate with CI/CD, version control, and observability platforms?**

A: Yes, Claude Code integrates with GitHub Actions for CI/CD, supports git operations, and can connect to various platforms via MCP servers. Check the docs for specific integrations. GitLab integration is actively being developed with their team.

### Technical Architecture

**Q: Does Claude Code index my entire codebase or use a vector database to store information about my codebase?**

A: No. Claude Code has access to a system prompt and a series of tools that it can use to navigate your codebase on command. For example, if Claude Code needs to understand something about your codebase, it will use a search tool to search through your codebase and read files on command. We find that this is more effective and flexible than full codebase indexing: Claude Code is really good at knowing how to sift through a codebase to gather context it needs on the fly!

---

📖 Official Claude Code docs: https://docs.anthropic.com/en/docs/claude-code