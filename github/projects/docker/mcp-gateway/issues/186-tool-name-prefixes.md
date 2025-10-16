# [Feature Request] Tool Name Prefixes for MCP Server Identification

## Problem Description
When using the Docker MCP Toolkit with multiple MCP servers enabled, users cannot easily identify which MCP server a tool belongs to from its name alone. This creates confusion when:

1. **Tool Identification**: Multiple servers may have tools with similar names (e.g., `create_issue`, `read_file`, `query`)
2. **Debugging**: Users need to determine which server is causing issues or providing certain functionality
3. **Server Management**: Users want to enable/disable tools by server category
4. **Tool Discovery**: Users browse available tools and need to understand their origins

## Current Impact
- User confusion about tool origins and capabilities
- Difficulty in managing tools by server category
- Manual workarounds required to track tool-to-server mappings
- Poor user experience when working with multiple MCP servers

## Proposed Solution: Tool Name Prefixes
Add configurable prefixes to tool names indicating their source MCP server:
- `github:create_issue` instead of just `create_issue`
- `filesystem:read_file` instead of just `read_file`
- `database:query` instead of just `query`
- `slack:send_message` instead of just `send_message`

## Benefits
- **Clear Tool Organization**: Immediately identify which server provides each tool
- **Better UX**: Users can mentally categorize and filter tools by server
- **Server Transparency**: Always know which servers are active and contributing tools
- **Debugging Aid**: Easier to isolate issues to specific servers

## Implementation Notes
- Prefixes should be configurable per MCP server in the server configuration
- Default prefixes could be derived from server names or allow custom specification
- Backward compatibility maintained - existing configurations continue to work
- Could integrate with existing `docker mcp tools ls` command to show prefixed names

## Example Configuration
```yaml
servers:
  - name: github
    prefix: "github"
    # ... other config
  - name: filesystem
    prefix: "fs"
    # ... other config
```

## Related Issues
- **MCP SEP-986**: [Specify Format for Tool Names](https://github.com/modelcontextprotocol/modelcontextprotocol/issues/986) - Official MCP specification proposal for standardized tool naming, including support for forward slashes (/) for namespacing
- **ShotGrid MCP Server**: [Tool Naming Convention](https://pipeline-f26f1c83.mintlify.app/guides/tool-naming-convention) - Real-world implementation using prefixed tool names (e.g., `prefix_action_qualifier`)
- **[AWS Q Developer CLI #2397](https://github.com/aws/amazon-q-developer-cli/issues/2397)**: Token usage breakdown by tool/MCP (related to tool identification)
- **[mcp-filter project](https://github.com/pro-vi/mcp-filter)**: External proxy solution for tool filtering (addresses similar organization needs)

## Environment
- Docker MCP Toolkit via Docker Desktop
- IDEs: Cursor, Windsurf, VSCode with MCP extensions
