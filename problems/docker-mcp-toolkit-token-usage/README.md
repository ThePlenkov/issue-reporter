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

## Current Workarounds
1. **mcp-filter** (https://github.com/pro-vi/mcp-filter): Proxy server that filters tools, reducing token usage by ~72%
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
| [#187](https://github.com/docker/mcp-gateway/issues/187) | Meta-MCP Server for Tool Discovery and Filtering | docker/mcp-gateway | submitted | 2025-10-16 | 2025-10-16 | Feature request for gateway-style MCP server |

**Status Legend:**
- `submitted`: Issue created and submitted to GitHub
- `acknowledged`: Issue acknowledged by maintainers
- `in_progress`: Work has started on the issue
- `resolved`: Issue has been resolved/closed
- `rejected`: Issue was closed without resolution

## Investigation Date
2025-10-16

## References
- Docker MCP Toolkit: https://docs.docker.com/ai/mcp-catalog-and-toolkit/toolkit/
- Docker MCP Gateway: https://github.com/docker/mcp-gateway
