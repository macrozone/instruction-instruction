# Claude Configuration

## Project Overview

This repository defines the **Instruction-Instruction Framework** - a standardized format for creating executable instructions that AI coding agents can follow to modify codebases consistently and reliably.

See [README.md](./README.md) for detailed information about the framework's purpose and benefits.

## Instructions Applied

None currently applied. When instructions are applied to this repository, they will be documented here with exact URLs used.

## Rules and Guidelines

### When Processing Instruction Files

1. **Git State Verification**: Before processing any instruction:
   - Verify the repository is in a clean state (no uncommitted changes)
   - If on `main` branch, automatically create and switch to a new feature branch
   - Reject processing if there are uncommitted changes
   - Example branch naming: `instruction/[repo-name]-[timestamp]`

2. **Dry-Run Support**: When user requests dry-run mode (e.g., "show me what this would do"):
   - Parse the instruction file
   - Show all planned changes without executing them
   - List files that would be created/modified
   - Display dependencies that would be installed

3. **Always Reference URLs**: When applying instructions, update this file to reference the exact URL used. Reject URLs using `main` branch - require versioned URLs (tags or commit hashes) for reproducibility

4. **Process Dependencies**: Before executing main instruction:
   - Check for dependency instructions that must be applied first
   - Verify all dependencies are satisfied
   - Apply dependency instructions in correct order

5. **Follow the Standard Workflow**:
   - Verify git state and create branch if needed
   - Process any dependency instructions
   - Update documentation (this file) with detailed instruction references including purpose, changes made, and usage
   - Execute setup steps with user confirmation
   - Apply codemods with user review
   - Verify changes don't break existing functionality

6. **User Confirmation Required**: Always inform the user about planned changes and request approval before:
   - Installing dependencies
   - Creating or modifying files
   - Applying code transformations

7. **Conditional Execution**: Process conditional steps based on project state:
   - Detect project type, frameworks, and existing configurations
   - Apply only relevant conditional instructions
   - Skip steps that don't apply to the current project

8. **Maintain Traceability**: Document what was changed, when, and why to enable future updates and rollbacks. Include comprehensive details about each instruction's purpose and effects so future agents can understand and potentially update or rollback changes

### When Creating Instruction Files

1. **Follow Framework Standards**: Use the format defined in `create-instruction-repo.md`
2. **Use AI-Interpretable Instructions**: Write setup and codemod instructions that AI agents can follow directly
3. **Include Version Information**: Always specify versions for dependencies and tools  
4. **Test Instructions**: Verify instructions work on clean codebases before sharing

### Repository Maintenance

- Keep instruction files up to date with latest best practices
- Tag releases when making breaking changes to instruction formats
- Maintain backward compatibility when possible
- Document breaking changes in release notes
- **Always verify our own instruction files against our templates**: Before publishing, ensure all instruction files follow the structure and requirements defined in our own templates

## Development Guidelines

- All instruction files should be tested against real codebases
- Use clear, actionable language that AI agents can interpret and execute
- Include error handling and rollback procedures where applicable
- Break complex instructions into modular files (`setup.md`, `codemod.md`) when needed