# Workspace Rules for AI-First Issue Management System

## File Organization

### Temporary Analysis Files
- **Location**: Always use `./tmp/` folder for temporary analysis, working documents, and files that should NOT be committed
- **Examples**: 
  - Analysis documents (ANALYSIS.md)
  - Improvement suggestions (IMPROVEMENTS.md)
  - Draft notes and brainstorming
  - Temporary research files
  - Working documents during investigation

### Permanent Documentation
- **Location**: Root or appropriate subdirectories
- **Examples**:
  - README.md (project overview)
  - problems/ (problem investigations)
  - github/projects/ (issue drafts and project indexes)
  - .windsurf/workflows/ (workflow definitions)

## Git Ignore
The `./tmp/` folder is gitignored and will never be committed to the repository.

## Workflow
When creating analysis or improvement documents:
1. Create them in `./tmp/` folder
2. Review with user
3. If user wants to keep them permanently, move to appropriate location
4. Otherwise, they stay in `./tmp/` and are not committed

## Rationale
- Keeps repository clean and focused on reusable content
- Separates working documents from permanent documentation
- Allows AI to create analysis freely without cluttering the repo
- User has control over what becomes permanent
