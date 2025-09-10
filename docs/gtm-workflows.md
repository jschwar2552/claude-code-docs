# Claude Code for GTM Teams

Essential workflows and tools for Go-to-Market teams using Claude Code.

## MCP Integrations for GTM

### Salesforce Integration
- **Query customer data**: Use `mcp__salesforce__query` for SOQL queries
- **Update records**: Bulk operations with `mcp__salesforce__update`
- **Analytics**: Complex reporting queries across objects

### Google Workspace Integration  
- **Sheets analysis**: Read and analyze sales data with `mcp__gsuite-mcp__read_sheet`
- **Doc generation**: Create proposals with `mcp__gsuite-mcp__create_doc`
- **Drive search**: Find assets with `mcp__gsuite-mcp__search_drive`

### BigQuery Analytics
- **Usage analysis**: Query API usage patterns
- **Customer insights**: Cross-platform data analysis
- **Revenue reporting**: Pipeline and conversion metrics

## Common GTM Workflows

### Customer Health Analysis
```bash
# Query recent API usage
/docs api-usage-patterns

# Analyze support tickets
/docs customer-success-metrics

# Generate health score reports
/docs revenue-forecasting
```

### Competitive Intelligence
- Market research automation
- Competitor feature analysis
- Pricing strategy documentation

### Sales Enablement
- Demo script generation
- Technical FAQ automation  
- ROI calculation templates

## Best Practices

### Data Security
- Use environment variables for API keys
- Implement proper access controls
- Regular audit of data access patterns

### Automation Guidelines
- Start with manual processes
- Gradually automate routine tasks
- Always validate automated outputs

### Team Collaboration
- Shared CLAUDE.md configurations
- Standardized prompt templates
- Documentation of custom workflows

## Integration Examples

### Salesforce + BigQuery Pipeline
1. Extract Salesforce data
2. Transform for analysis
3. Load into BigQuery
4. Generate insights dashboard

### Customer Onboarding Automation
1. Detect new customer signup
2. Create Salesforce record
3. Generate onboarding materials
4. Schedule follow-up tasks

### Revenue Operations
1. Pipeline analysis
2. Forecasting models
3. Commission calculations  
4. Performance dashboards

## Troubleshooting

### Common Issues
- API rate limiting
- Authentication failures
- Data sync conflicts
- Permission errors

### Resolution Strategies
- Implement retry logic
- Use exponential backoff
- Monitor API quotas
- Regular credential rotation

## Resources

- **Salesforce MCP Guide**: `/docs salesforce-patterns`  
- **BigQuery Schemas**: `/docs bigquery-reference`
- **Google Workspace APIs**: `/docs gsuite-integration`
- **Security Best Practices**: `/docs security-guidelines`

---

📖 Official Claude Code docs: https://docs.anthropic.com/en/docs/claude-code