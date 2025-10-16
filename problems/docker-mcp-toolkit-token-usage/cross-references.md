# Cross-References for Docker MCP Toolkit Issues

## Related External Projects & Issues
- **mcp-filter**: https://github.com/pro-vi/mcp-filter
  - Provides proxy-based tool filtering solution
  - Reduces token usage by ~72%
  - Relevant to: token usage problem

- **RooCode Issue #5373**: https://github.com/RooCodeInc/Roo-Code/issues/5373
  - Request for on-demand tool specification loading
  - Directly addresses token usage concerns
  - Related to: meta-MCP server concept

- **AWS Q Developer CLI Issue #2397**: https://github.com/aws/amazon-q-developer-cli/issues/2397
  - Feature request for token usage breakdown by tool/MCP
  - Related to: tool identification and monitoring

- **n8n Issue #17144**: https://github.com/n8n-io/n8n/issues/17144
  - Excessive token usage from tool descriptions
  - Similar problem in different MCP implementation

## Potential Docker MCP Gateway Issues
This problem could be addressed through multiple separate issues:

1. **[Tool Name Prefixes]**: [docker/mcp-gateway#186](https://github.com/docker/mcp-gateway/issues/186)
   - Clear tool-to-server identification
   - Configurable prefixes for better organization

2. **[Meta-MCP Server]**: [docker/mcp-gateway#187](https://github.com/docker/mcp-gateway/issues/187)
   - Gateway-style MCP server for tool discovery and filtering
   - On-demand tool loading to reduce token usage
   - Selective tool exploration capabilities

## Project Structure
```
problems/docker-mcp-toolkit-token-usage/
├── README.md                    # Problem summary and analysis + issue status table
├── cross-references.md         # This file - external links and relationships
└── [links to issue drafts in projects/ folder]

projects/docker/mcp-gateway/
├── README.md                    # Project index with issue references
└── issues/
    ├── 186-tool-name-prefixes.md           # Issue #186 draft
    └── 187-meta-mcp-server.md              # Issue #187 draft
```

## Related Projects and Solutions
- **[MCP Gateway & Registry](https://github.com/agentic-community/mcp-gateway-registry)**: Enterprise-ready MCP gateway with dynamic tool discovery, registry functionality, and unified access - directly implements the meta-MCP server concept
- **[MCP SEP-986](https://github.com/modelcontextprotocol/modelcontextprotocol/issues/986)**: Official MCP specification proposal for standardized tool naming with support for namespacing using forward slashes
- **[ShotGrid MCP Server Tool Naming](https://pipeline-f26f1c83.mintlify.app/guides/tool-naming-convention)**: Real-world implementation using prefixed tool names for organization
- **[mcp-filter](https://github.com/pro-vi/mcp-filter)**: Open-source proxy that filters MCP tools, reducing token usage by ~72%
- **[RooCode Issue #5373](https://github.com/RooCodeInc/Roo-Code/issues/5373)**: On-demand tool specification loading proposal
- **[AWS Q Developer CLI #2397](https://github.com/aws/amazon-q-developer-cli/issues/2397)**: Token usage breakdown by tool/MCP
- **[n8n #17144](https://github.com/n8n-io/n8n/issues/17144)**: Similar token usage issues with tool descriptions

## Status
- Problem documented: ✅
- Related issues identified: ✅
- Draft issue prepared: ✅
- Issues submitted to docker/mcp-gateway: ✅
- Issue #186: [Tool Name Prefixes](https://github.com/docker/mcp-gateway/issues/186)
- Issue #187: [Meta-MCP Server](https://github.com/docker/mcp-gateway/issues/187)
- Project index created: ✅
- Status tracking table: ✅
- Workflow enhancements: ✅
