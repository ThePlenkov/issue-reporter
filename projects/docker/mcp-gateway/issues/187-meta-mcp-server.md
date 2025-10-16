# [Feature Request] Meta-MCP Server for Tool Discovery and Filtering

## Problem Description
When using the Docker MCP Toolkit with multiple MCP servers enabled, IDEs face significant challenges:

1. **Token Usage**: Every message includes tool descriptions for hundreds of tools, consuming thousands of tokens
2. **IDE Limits**: Many IDEs have practical limits on the number of MCP servers they can effectively handle
3. **Tool Overload**: Users are overwhelmed by the sheer number of available tools
4. **Discovery Issues**: No built-in way to browse/filter available tools without enabling all servers

## Current Impact
- Excessive API costs due to bloated context windows (every tool description loaded upfront)
- Poor IDE performance with large tool sets
- Users cannot selectively explore tools without enabling entire servers
- Manual workarounds required (like mcp-filter proxy)

## Proposed Solution: Meta-MCP Server
Provide an additional MCP server that acts as a gateway/directory for other MCP servers, offering:

### Core Tools
- `list_mcps`: List all available MCP servers with their status and basic info
- `list_tools`: List all tools across servers with filtering capabilities
- `get_tool_details`: Get detailed information about specific tools on-demand
- `enable_mcp`/`disable_mcp`: Programmatically control server enable/disable status

### Advanced Filtering
- Filter by MCP server (e.g., show only GitHub tools)
- Free text search across tool names and descriptions
- Category-based filtering (filesystem, database, communication, etc.)
- Tool count limits for paginated results

## Benefits
- **Token Savings**: Load tool specs only when needed instead of upfront (similar to RooCode issue #5373)
- **Selective Discovery**: Users can explore tools without overwhelming context
- **Better IDE Integration**: Work within IDE limits through intelligent filtering
- **Cost Efficiency**: Reduce API costs through smaller, on-demand context windows

## Usage Example
```
# List all available MCP servers
list_mcps

# Show only GitHub-related tools
list_tools --filter-server github

# Search for tools containing "issue"
list_tools --search issue

# Get detailed info for a specific tool before using it
get_tool_details github:create_issue
```

## Implementation Notes
- Meta-MCP server would be automatically available alongside regular servers
- Could proxy actual tool execution to the appropriate underlying MCP server
- Backward compatibility maintained - existing direct server connections continue to work
- Could integrate with existing `docker mcp` CLI commands for consistency

## Architecture
```
[MCP Client] <-> [Meta-MCP Server] <-> [Individual MCP Servers]
                    |
                    v
             [Tool Registry/Cache]
```

The meta-server maintains a lightweight registry of available tools without loading full descriptions upfront.

## Related Issues
- **MCP Gateway & Registry**: [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) - Enterprise-ready MCP gateway with dynamic tool discovery, registry functionality, and unified access (directly implements the proposed meta-MCP server concept)
- **MCP Gateway & Registry Docs**: [agentic-community.github.io/mcp-gateway-registry](https://agentic-community.github.io/mcp-gateway-registry/) - Dynamic tool discovery and runtime MCP server enumeration features
- **[RooCode #5373](https://github.com/RooCodeInc/Roo-Code/issues/5373)**: On-demand MCP tool specification loading
- **[AWS Q Developer CLI #2397](https://github.com/aws/amazon-q-developer-cli/issues/2397)**: Token usage breakdown by tool/MCP
- **[mcp-filter project](https://github.com/pro-vi/mcp-filter)**: External proxy solution for tool filtering

## Environment
- Docker MCP Toolkit via Docker Desktop
- IDEs: Cursor, Windsurf, VSCode with MCP extensions
