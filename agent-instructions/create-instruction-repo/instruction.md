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

## Dependencies

(Optional) List other instructions that must be applied before this one:

- **Base Configuration**: https://github.com/team/base-config/blob/v1.0.0/instruction.md
- **TypeScript Setup**: https://github.com/team/typescript-config/blob/v2.1.0/instruction.md

## Dry Run Support

This instruction supports dry-run mode. Users can preview changes by requesting: "Show me what this instruction would do" before applying.

## Instruction Steps

### 1. Git State Verification

The AI agent will:
- Verify repository is in clean state (no uncommitted changes)
- Create feature branch if currently on `main` (e.g., `instruction/[repo-name]-[timestamp]`)
- Reject processing if uncommitted changes exist

### 2. Documentation Updates

Create or update `CLAUDE.md` using the template at [templates/claude-template.md](./templates/claude-template.md) and add:

```markdown
## Instructions Applied

- **Create Instruction Repository**: Applied https://github.com/panter/instruction-instruction/blob/v1.0.0/agent-instructions/create-instruction-repo/instruction.md on [DATE]
  - **Purpose**: Adds standardized instruction file structure for creating reusable AI agent instructions
  - **What it does**: Creates instruction templates, README templates, and folder structure for instruction repositories
  - **Files created**: instruction.md, setup.md, codemod.md templates (or agent-instructions/ folder for existing repos)
  - **Usage**: Enables creation of instruction files that AI agents can execute to modify codebases consistently
```

### 3. Setup Steps

#### 3.1 Create Repository Structure

**For new repositories** or **dedicated instruction repositories**:
Create these files in the root:
- `README.md` - Repository description and usage (use [templates/readme-template.md](./templates/readme-template.md))
- `agent-instructions/[instruction-name]/instruction.md` - The main executable instruction file (use [templates/instruction-template.md](./templates/instruction-template.md))
- `agent-instructions/[instruction-name]/setup.md` - Detailed setup instructions (optional, for complex setups)
- `agent-instructions/[instruction-name]/codemod.md` - Detailed code transformation instructions (optional, for complex codemods)

**For existing repositories** (libraries, applications, etc.):
Create instruction files in a dedicated folder to avoid conflicts:
- `agent-instructions/README.md` - Description of available instructions (use [templates/instructions-readme-template.md](./templates/instructions-readme-template.md))
- `agent-instructions/[feature-name]/instruction.md` - Main instruction file (use [templates/instruction-template.md](./templates/instruction-template.md))
- `agent-instructions/[feature-name]/setup.md` - Setup instructions (optional)
- `agent-instructions/[feature-name]/codemod.md` - Codemod instructions (optional)

Example for existing repository:
```
my-library/
├── src/
├── package.json
├── README.md (existing)
└── agent-instructions/
    ├── README.md
    └── setup-graphql/
        ├── instruction.md
        ├── setup.md
        └── codemod.md
```

#### 3.2 Customize Templates

1. Copy the appropriate template files from this instruction's `templates/` directory
2. Replace all placeholder text (`[Instruction Name]`, `[username]`, `[repo]`, etc.) with your specific values
3. Fill in the actual instruction steps, dependencies, and code transformations
4. Add specific prerequisites and examples for your instruction

#### 3.3 Important Considerations for Your Instruction

When writing your instruction, pay attention to:

**Package Manager Detection**: If your instruction installs dependencies, detect the appropriate package manager:
- Check for `package-lock.json` (npm), `yarn.lock` (yarn), `pnpm-lock.yaml` (pnpm), etc.
- Use the detected package manager in your install commands

**Framework/Tool Detection**: If your instruction is framework-specific:
- Check `package.json` dependencies for framework presence
- Look for configuration files (e.g., `tsconfig.json`, `.eslintrc`, etc.)
- Adapt instructions based on what's detected

**File System Conventions**: Respect existing project structure:
- Check existing folder patterns before creating new ones
- Follow naming conventions already used in the project
- Don't assume specific folder structures

**Conditional Logic**: Make instructions adaptive:
- Skip steps that don't apply to the current project setup
- Provide alternative approaches for different configurations
- Handle edge cases gracefully

### 4. Codemod Instructions

Based on your specific instruction needs:

#### 4.1 Create Instruction Content
- Define the specific changes your instruction should make
- Identify file patterns and code transformations needed
- Specify exact dependency versions and setup steps

#### 4.2 Add Examples
Create `examples/` directory with:
- `before/` - Code samples before applying instruction
- `after/` - Code samples after applying instruction

#### 4.3 Create Helper Scripts (if needed)
Add any setup scripts or codemods to `scripts/` directory.

### 5. Verification Steps

Test your instruction:

1. Create a test project
2. Apply your instruction manually
3. Verify all steps work as expected
4. Document any edge cases or prerequisites
5. Tag your repository with semantic versions (v1.0.0, v1.1.0, etc.) for reproducible URLs

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