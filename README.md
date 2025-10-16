# AI-Assisted Problem Investigation & Issue Management

> **A practical demonstration of AI-driven workflows**  
> This project was created using AI agents (initially Grok, now Windsurf/Cascade) to show how defining workflows first, then executing them with AI assistance, can speed up problem investigation and issue management.

## 🎯 What This Is

A workflow-based approach to investigating problems and managing issues across different platforms (GitHub, GitLab, Reddit, forums, etc.).

**The idea**: Instead of ad-hoc issue creation, use a structured workflow that:
- Guides systematic problem investigation
- Researches existing solutions before creating new issues
- Documents findings in a reusable format
- Tracks issue status across platforms

## 🤖 How It Works

1. **Define Workflow**: Create a step-by-step investigation process (see [`.windsurf/workflows/problem.md`](.windsurf/workflows/problem.md))
2. **AI Executes**: AI follows the workflow, doing research and documentation
3. **Document & Track**: Everything is organized and tracked for future reference

### Key Features

- **Structured Investigation**: Follow a consistent process instead of random searching
- **Multi-Platform**: Works with GitHub, GitLab, Reddit, forums—wherever you need to post
- **Research First**: Find existing solutions and related work before creating issues
- **Status Tracking**: Keep track of submitted issues and their progress
- **Reusable Knowledge**: Investigations become documentation for future reference

## 🚀 Why Use This

### Saves Time
- Don't lose track of what you investigated
- Avoid creating duplicate issues (research existing ones first)
- Reuse investigation work for similar problems later

### Better Quality
- Structured approach ensures you don't miss important details
- Well-researched issues are more likely to get maintainer attention
- Documentation helps you and others understand the problem later

### Works Anywhere
- Not limited to GitHub—use with any platform
- Same workflow for bugs, features, community discussions
- Organize investigations across multiple projects

## 📁 Project Structure

```
├── .windsurf/
│   └── workflows/
│       └── problem.md           # Main problem investigation workflow
├── problems/                    # Problem investigations and documentation
│   └── [problem-name]/
│       └── README.md           # Complete problem analysis + status tracking
├── github/                      # Platform-specific organization
│   └── projects/               # GitHub projects
│       └── [owner]/[repo]/
│           ├── README.md       # Project index with issue references
│           └── issues/         # Issue drafts (named by issue number)
└── README.md                   # This file
```

### Future Platforms
The structure supports expansion to other platforms:
- `gitlab/projects/` - GitLab issues and merge requests
- `reddit/posts/` - Community discussions and feature requests
- `discord/channels/` - Community support and discussions

## 🔄 The Workflow

The `/problem` workflow guides you through these steps:

1. **Gather Details**: Describe the problem, reproduction steps, environment
2. **Find Projects**: Identify relevant repositories or platforms
3. **Search Existing**: Look for similar issues and existing solutions
4. **Analyze**: Document findings and potential workarounds
5. **Draft Issues**: Create well-researched issue drafts (if needed)
6. **Register Problem**: Document in `problems/` folder with status tracking
7. **Submit**: Post issues to target platforms (with approval)
8. **Track**: Monitor responses and update status

See [`.windsurf/workflows/problem.md`](.windsurf/workflows/problem.md) for the complete workflow.

## 🛠️ Tools and Features

### Workflow Automation (`/problem`)
- Interactive problem investigation workflow
- Automatic research and cross-referencing
- Platform-specific issue drafting
- Status tracking and updates

### Documentation System
- **Problems**: Complete investigations with status tables
- **Projects**: Platform-specific indexes with issue tracking
- **Issues**: Numbered drafts with full context
- **Cross-references**: Links between related problems and solutions

### Multi-Platform Support
- **GitHub**: Issues, pull requests, discussions
- **GitLab**: Issues, merge requests
- **Community**: Reddit posts, Discord threads, forums
- **Extensible**: Easy to add new platforms

## 📋 Example

See [`problems/docker-mcp-toolkit-token-usage/`](problems/docker-mcp-toolkit-token-usage/) for a real example:

1. Started with `/problem` workflow
2. Investigated Docker MCP Toolkit token usage issues
3. Researched existing solutions and related projects
4. Created two well-documented feature requests:
   - [Issue #186: Tool Name Prefixes](github/projects/docker/mcp-gateway/issues/186-tool-name-prefixes.md) ([live on GitHub](https://github.com/docker/mcp-gateway/issues/186))
   - [Issue #187: Meta-MCP Server](github/projects/docker/mcp-gateway/issues/187-meta-mcp-server.md) ([live on GitHub](https://github.com/docker/mcp-gateway/issues/187))
5. Tracking status in [problem documentation](problems/docker-mcp-toolkit-token-usage/README.md)

The investigation is fully documented and can be referenced later.

## 🤝 Contributing

This system is designed to be extensible and customizable:

1. **Add New Platforms**: Create `platform/projects/` directories with appropriate structure
2. **Customize Workflows**: Modify [`.windsurf/workflows/problem.md`](.windsurf/workflows/problem.md) for your needs
3. **Extend Templates**: Add platform-specific issue templates and automation

## 📊 Current Status

- ✅ Basic workflow implemented and tested
- ✅ Multi-platform directory structure
- ✅ Example investigation completed (Docker MCP Toolkit)
- ✅ Status tracking and documentation working

---

**A practical tool for structured problem investigation and issue management.**  
**Shows how AI-assisted workflows can make investigation faster and more thorough.**
