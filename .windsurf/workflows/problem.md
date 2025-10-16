---
description: Investigate and document a problem, find/create GitHub issues
---

# Problem Investigation Workflow

## Step 1: Gather Problem Details
- Ask user for complete problem description
- Identify affected systems/components
- Determine expected vs actual behavior
- Gather error messages, logs, reproduction steps
- Note environment details (OS, versions, etc.)

## Step 2: Find Relevant GitHub Projects
- Based on problem details, identify potential GitHub repositories
- Search GitHub for related projects using keywords
- Verify project relevance and activity status

## Step 3: Search Existing Issues
- Search each relevant project for similar issues
- Look for open and closed issues with similar symptoms
- Note issue numbers, status, and any workarounds mentioned

## Step 4: Analyze and Document
- Summarize findings in structured format
- Document potential workarounds from existing issues
- Identify if this is a new unique problem

## Step 5: Draft New Issues (if needed)
- For new problems, draft issue templates
- Include all relevant details: reproduction steps, environment, expected behavior
- DO NOT submit issues automatically - wait for user approval

## Step 6: Register Problem
- Create structured documentation in problems/ folder
- Create a status table template tracking submitted issues
- Use cross-references between problems and potential issues
- Support multiple issues per problem across different projects
- Maintain clear links between related items

## Step 6.5: Create Issue Drafts
- For new issues, create draft files in platform-specific folder structure
- Use platform/project path from repository (e.g., github/projects/docker/mcp-gateway/issues/)
- Include issue number placeholders for future tracking (e.g., 001-issue-title.md)
- Cross-reference with problem documentation

## Step 7: Submit Issues (if approved)
- Submit drafted issues to GitHub repositories using available tools
- Capture actual issue numbers upon successful submission
- Rename draft files to use actual issue numbers (e.g., 186-tool-name-prefixes.md)
- Update all cross-references in problem documentation with actual issue links
- Update problem status table to mark issues as "submitted"
- Create/update project README.md with issue references

## Step 8: Create Project Index (if needed)
- Create platform/projects/[project]/README.md with project overview
- Include links to repository, submitted issues, and related problems
- Maintain index of all issues submitted for the project
- Update when new issues are created

// turbo
