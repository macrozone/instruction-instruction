# Create Instruction Repository

**Source**: https://github.com/panter/instruction-instruction/blob/v1.0.0/agent-instructions/create-instruction-repo/instruction.md

## Description

This instruction guides you through creating a standardized instruction repository that AI coding agents can execute to modify codebases consistently. The resulting repository will follow the Instruction-Instruction framework format.

**Target Use Cases:**

- **New repositories**: Create dedicated instruction repositories from scratch
- **Existing repositories**: Add instruction files to existing projects (libraries, applications) without overwriting existing content

## Prerequisites

- Git repository (new or existing)
- Basic understanding of the target technology/pattern you want to instruct
- Git repository in clean state

## Instruction Steps

### 1. Git State Verification

Check that the repository is in a clean state (no uncommitted changes). If on `main` branch, create a feature branch (e.g., `instruction/create-instruction-repo-[timestamp]`). If there are uncommitted changes, reject processing and ask user to commit or stash them first.

### 2. Check for Existing Application

Check if this instruction has already been applied:

1. Look for this instruction in `CLAUDE.md` under "Instructions Applied"
2. If found and user hasn't explicitly requested an update, inform user that instruction is already applied
3. If user requests update or version differs, follow the update process in [update.md](./update.md)
4. If not found, proceed with fresh application

### 3. Documentation Updates

Create or update `CLAUDE.md` using the template at [templates/claude-template.md](./templates/claude-template.md) and add:

```markdown
## Instructions Applied

- **Create Instruction Repository**: Applied https://github.com/panter/instruction-instruction/blob/v1.0.0/agent-instructions/create-instruction-repo/instruction.md on [DATE]
  - **Purpose**: Adds standardized instruction file structure for creating reusable AI agent instructions
  - **What it does**: Creates instruction templates, README templates, and folder structure for instruction repositories
  - **Files created**: instruction.md, setup.md, codemod.md templates (or agent-instructions/ folder for existing repos)
  - **Usage**: Enables creation of instruction files that AI agents can execute to modify codebases consistently
```

### 4. Setup Steps

**See**: [setup.md](./setup.md) for detailed setup instructions.

### 5. Commit Setup Changes

After completing all setup steps, commit the changes following the repository's commit message conventions:

```bash
git add .
git commit -m "[Commit message following repo conventions - typically describing the setup changes made]"
```

### 6. User Confirmation for Codemod

Ask the user for confirmation before proceeding with code transformations:

```
The setup phase is complete. Would you like me to proceed with applying code transformations now?

This will:
- [List specific code changes that will be made]
- [Files that will be modified]
- [Any potentially destructive changes]

Reply 'yes' to proceed or 'no' to stop here.
```

### 7. Codemod Instructions

**See**: [codemod.md](./codemod.md) for detailed transformation instructions.

## Examples

### Before (Empty Repository)

```
my-instruction-repo/
└── README.md (basic)
```

### After (Complete Instruction Repository)

```
my-instruction-repo/
├── README.md
└── agent-instructions/
    └── my-feature/
        ├── instruction.md
        ├── setup.md (optional)
        ├── codemod.md (optional)
        ├── templates/
        └── examples/
```

## Rollback Instructions

**See**: [rollback.md](./rollback.md) for instructions on how to undo these changes.

## Notes

- Tag your repository with semantic versions (v1.0.0, v1.1.0, etc.) for reproducible URLs
- Test instructions on clean codebases before sharing
- Write AI-interpretable instructions rather than executable scripts
- Keep dependencies and versions explicit
- Provide clear rollback procedures for breaking changes
- Consider backward compatibility when updating instructions

## Common Patterns

### Library Installation Instruction

Focus on: dependencies, configuration files, usage patterns, type definitions

### Architecture Pattern Instruction

Focus on: folder structure, file templates, import patterns, naming conventions

### Migration Instruction

Focus on: step-by-step replacement, codemods, dependency changes, cleanup steps
