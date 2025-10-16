# Docker MCP Toolkit Token Usage and Tool Management Issues

## Problem Summary
The Docker MCP Toolkit allows connecting multiple MCP servers from a catalog, resulting in hundreds of tools being exposed to IDEs. This creates significant usability and performance issues:

1. **Token Usage**: Every message consumes thousands of tokens due to tool descriptions
2. **IDE Limits**: IDEs like Cursor/Windsurf have MCP server limits
3. **Tool Organization**: No way to identify which MCP server a tool belongs to
4. **Filtering**: No built-in way to filter or search through available tools

## Impact
- Excessive API costs due to bloated token usage
- Poor user experience in IDEs with tool overload
- Difficult to manage and organize tools from multiple sources
- Potential performance degradation

## Quantitative Analysis

### Token Usage Measurements

#### Baseline (All Tools Loaded)
- **Tool Count**: 150+ tools from Docker MCP catalog (varies by enabled servers)
- **Average Tool Description**: ~100 tokens per tool (estimated)
- **Total Context**: ~15,000 tokens per message (estimated)
- **Cost Impact**: ~$0.015 per message at GPT-4 pricing (estimated)

#### With mcp-filter Proxy
- **Filtered Tool Count**: ~40 tools (configurable)
- **Total Context**: ~4,000 tokens per message (estimated)
- **Reduction**: ~72% token savings (claimed by project, needs verification)
- **Source**: [mcp-filter repository](https://github.com/pro-vi/mcp-filter)

#### Projected with Meta-MCP Server
- **On-Demand Loading**: Only load tools when requested
- **Initial Context**: ~500 tokens (server list only, estimated)
- **Reduction**: ~97% for initial messages (estimated)
- **Trade-off**: Additional request for tool details when needed

### IDE Practical Limits
- **Cursor**: Recommended max ~10 MCP servers (community reports)
- **Windsurf**: Tested stable with ~15 servers (empirical)
- **VSCode**: Performance degrades beyond ~20 servers (community reports)
- **Source**: Empirical testing and community feedback (needs formal benchmarking)

*Note: Measurements are estimates based on typical configurations. Actual numbers vary by enabled servers and tool descriptions. Formal benchmarking needed for precise quantification.*

## Current Workarounds
1. **mcp-filter** (https://github.com/pro-vi/mcp-filter): Proxy server that filters tools, reducing token usage by ~72% (claimed)
2. Manual server enable/disable via `docker mcp server enable/disable`
3. Individual tool inspection via `docker mcp tools inspect`

## Potential Solutions
This problem can be addressed through multiple complementary approaches:

### 1. Tool Name Prefixes
**[Issue #186](https://github.com/docker/mcp-gateway/issues/186)**
- Add configurable prefixes to tool names indicating their source MCP server
- Examples: `github:create_issue`, `filesystem:read_file`
- Benefits: Clear identification, better organization, debugging aid

### 2. Meta-MCP Server
**[Issue #187](https://github.com/docker/mcp-gateway/issues/187)**
- Additional MCP server providing tool listing and filtering capabilities
- Features: `list_mcps`, `list_tools`, `get_tool_details`, selective filtering
- Benefits: On-demand loading, reduced token usage, selective discovery

### 3. On-Demand Loading
- Load tool specifications only when needed (inspired by RooCode #5373)
- Could be implemented as part of the Meta-MCP server approach

### 4. Tool Categories
- Group tools by MCP server with collapsible categories
- Could complement the prefix approach

## Issue Status Tracking

| Issue # | Title | Project | Status | Submitted | Last Updated | Notes |
|---------|-------|---------|--------|-----------|--------------|-------|
| [#186](https://github.com/docker/mcp-gateway/issues/186) | Tool Name Prefixes for MCP Server Identification | docker/mcp-gateway | submitted | 2025-10-16 | 2025-10-16 | Feature request for configurable tool name prefixes |
| [#187](https://github.com/docker/mcp-gateway/issues/187) | Meta-MCP Server for Tool Discovery and Filtering | docker/mcp-gateway | submitted | 2025-10-16 | 2025-10-16 | Feature request for gateway-style MCP server. [Comment added](https://github.com/docker/mcp-gateway/issues/187#issuecomment-3411423560) clarifying relationship to existing MCP Gateway & Registry |

## Related External Projects & Issues

### Existing Solutions
- **[mcp-filter](https://github.com/pro-vi/mcp-filter)**: Open-source proxy that filters MCP tools, reducing token usage by ~72%
- **[MCP Gateway & Registry](https://github.com/agentic-community/mcp-gateway-registry)**: Enterprise-ready MCP gateway with dynamic tool discovery, registry functionality, and unified access - directly implements the meta-MCP server concept

### Related MCP Specifications
- **[MCP SEP-986](https://github.com/modelcontextprotocol/modelcontextprotocol/issues/986)**: Official MCP specification proposal for standardized tool naming with support for namespacing using forward slashes
- **[ShotGrid MCP Server Tool Naming](https://pipeline-f26f1c83.mintlify.app/guides/tool-naming-convention)**: Real-world implementation using prefixed tool names for organization

### Similar Issues in Other Projects
- **[RooCode Issue #5373](https://github.com/RooCodeInc/Roo-Code/issues/5373)**: On-demand MCP tool specification loading proposal
- **[AWS Q Developer CLI #2397](https://github.com/aws/amazon-q-developer-cli/issues/2397)**: Token usage breakdown by tool/MCP
- **[n8n #17144](https://github.com/n8n-io/n8n/issues/17144)**: Similar token usage issues with tool descriptions

## Project Structure
```
problems/docker-mcp-toolkit-token-usage/
├── README.md                    # This consolidated problem documentation
└── [links to issue drafts in github/projects/ folder]

github/projects/docker/mcp-gateway/
├── README.md                    # Project index with issue references
└── issues/
    ├── 186-tool-name-prefixes.md           # Issue #186 draft
    └── 187-meta-mcp-server.md              # Issue #187 draft
```

## Investigation Status
- ✅ Problem documented and analyzed
- ✅ Related issues and implementations researched
- ✅ Draft issues prepared and submitted
- ✅ Issues #186 and #187 created in docker/mcp-gateway repository
- ✅ Project index and status tracking implemented
- ✅ Workflow enhancements completed

## Investigation Date
2025-10-16

## References
- Docker MCP Toolkit: https://docs.docker.com/ai/mcp-catalog-and-toolkit/toolkit/
- Docker MCP Gateway: https://github.com/docker/mcp-gateway
