# Create Instruction Repository

**Source**: https://github.com/panter/instruction-instruction/blob/v1.0.0/create-instruction-repo.md  
**Framework**: Instruction-Instruction v1.0.0  
**Last Updated**: 2025-09-02

## Description

This instruction guides you through creating a standardized instruction repository that AI coding agents can execute to modify codebases consistently. The resulting repository will follow the Instruction-Instruction framework format.

**Target Use Cases:**
- **New repositories**: Create dedicated instruction repositories from scratch
- **Existing repositories**: Add instruction files to existing projects (libraries, applications) without overwriting existing content

## Prerequisites

- Git repository (new or existing)
- Basic understanding of the target technology/pattern you want to instruct
- Git repository in clean state
- Not on main branch (will be created automatically if needed)

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

Update or create the agent configuration file in your target project:

```markdown
## Instructions Applied

- **Create Instruction Repository**: Applied https://github.com/panter/instruction-instruction/blob/v1.0.0/create-instruction-repo.md on [DATE]
  - **Purpose**: Adds standardized instruction file structure for creating reusable AI agent instructions
  - **What it does**: Creates instruction templates, README templates, and folder structure for instruction repositories
  - **Files created**: instruction.md, setup.md, codemod.md templates (or .instructions/ folder for existing repos)
  - **Usage**: Enables creation of instruction files that AI agents can execute to modify codebases consistently
```

### 2. Setup Steps

Execute the following setup in your instruction repository:

#### 2.1 Create Repository Structure

**For new repositories** or **dedicated instruction repositories**:
Create these files in the root:
- `README.md` - Repository description and usage
- `instruction.md` - The main executable instruction file
- `setup.md` - Detailed setup instructions (optional, for complex setups)
- `codemod.md` - Detailed code transformation instructions (optional, for complex codemods)

**For existing repositories** (libraries, applications, etc.):
Create instruction files in a dedicated folder to avoid conflicts:
- `.instructions/README.md` - Description of available instructions
- `.instructions/[feature-name]/instruction.md` - Main instruction file
- `.instructions/[feature-name]/setup.md` - Setup instructions (optional)
- `.instructions/[feature-name]/codemod.md` - Codemod instructions (optional)

Example for existing repository:
```
my-library/
├── src/
├── package.json
├── README.md (existing)
└── .instructions/
    ├── README.md
    └── setup-graphql/
        ├── instruction.md
        ├── setup.md
        └── codemod.md
```

#### 2.2 README.md Template

**For dedicated instruction repositories:**
```markdown
# [Instruction Name]

Brief description of what this instruction does.

## What It Does

- Bullet point list of changes/additions
- Dependencies installed
- Files created/modified
- Patterns applied

## Prerequisites

- List any requirements
- Versions needed
- Existing setup assumptions

## Usage

```
"Please read and execute these instructions: https://github.com/[username]/[repo]/blob/v[version]/instruction.md"
```

**Important**: Never use `main` branch URLs. Always use tagged versions or commit hashes for reproducibility.

## Changelog

Track versions and changes here.
```

**For existing repositories (.instructions/README.md):**
```markdown
# Available Instructions

This directory contains instruction files that can be applied to enhance or modify this repository.

## Instructions Available

### [Feature Name 1]
- **Path**: `.instructions/[feature-name-1]/instruction.md`
- **Description**: Brief description
- **Usage**: `"Please read and execute: https://github.com/[username]/[repo]/blob/v[version]/.instructions/[feature-name-1]/instruction.md"`

### [Feature Name 2]
- **Path**: `.instructions/[feature-name-2]/instruction.md`
- **Description**: Brief description
- **Usage**: `"Please read and execute: https://github.com/[username]/[repo]/blob/v[version]/.instructions/[feature-name-2]/instruction.md"`

## Important Notes

- Always use versioned URLs (tags or commit hashes) for reproducibility
- Instructions are designed to be applied to the root of this repository
```

#### 2.3 Instruction File Template

```markdown
# [Instruction Title]

**Version**: X.Y.Z
**Framework**: Instruction-Instruction v1.0.0
**Last Updated**: YYYY-MM-DD

## Description

Clear description of what this instruction accomplishes.

## Prerequisites

- List prerequisites
- Required versions
- Existing conditions

## Instruction Steps

### 1. Documentation Updates

Update or create agent configuration file (claude.md, agent.md, etc.):

```markdown
## Instructions Applied

- **[Instruction Name]**: Applied [VERSIONED-URL] on [DATE]
  - **Purpose**: [Brief description of why this instruction was applied]
  - **What it does**: [Bullet points of main changes/additions]
  - **Files affected**: [List of files created/modified]
  - **Usage**: [How to use the new functionality or patterns]
  - **Dependencies**: [Any new dependencies or tools required]
```

### 2. Setup Steps

#### 2.1 Install Dependencies

```bash
# List exact commands
npm install [package]@[version]
```

#### 2.2 Create Configuration Files

Create `[filename]` with the following content:

```[language]
[file content]
```

### 4. Conditional Steps

(Optional) Steps that only apply under certain conditions:

#### 4.1 If React is detected
**Detection**: Check for `react` in package.json dependencies
**Action**: Apply React-specific configuration

#### 4.2 If TypeScript is present
**Detection**: Check for `typescript` in devDependencies or `tsconfig.json`
**Action**: Add TypeScript-specific setup

#### 4.3 If tests exist
**Detection**: Check for `test` or `spec` files in project
**Action**: Update test patterns and configuration

### 5. Codemod Instructions

For simple transformations, include them here. For complex codemods, reference a separate `codemod.md` file:

**See**: [codemod.md](./codemod.md) for detailed transformation instructions.

#### 5.1 [Simple Transformation Name]

**Pattern to Find**: 
```[language]
[old pattern]
```

**Replace With**:
```[language]
[new pattern]
```

**Files to Target**: `[glob pattern]`

### 6. Verification Steps

After applying changes:

1. Run tests: `[test command]`
2. Check build: `[build command]`  
3. Verify functionality: [verification steps]
4. Confirm git branch was created if started from main

## Examples

### Before
```[language]
[before code]
```

### After
```[language]
[after code]
```

## Rollback Instructions

To undo these changes:

1. [Step to undo]
2. [Step to undo]

## Notes

- Additional context
- Common issues
- Troubleshooting tips
```

### 3. Codemod Instructions

Based on your specific instruction needs, define:

#### 3.1 Create Instruction Content
- Define the specific changes your instruction should make
- Identify file patterns and code transformations needed
- Specify exact dependency versions and setup steps

#### 3.2 Add Examples
Create `examples/` directory with:
- `before/` - Code samples before applying instruction
- `after/` - Code samples after applying instruction

#### 3.3 Create Helper Scripts (if needed)
Add any setup scripts or codemods to `scripts/` directory.

### 4. Verification Steps

Test your instruction:

1. Create a test project
2. Apply your instruction manually
3. Verify all steps work as expected
4. Document any edge cases or prerequisites

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
├── instruction.md
├── setup.md (optional)
└── codemod.md (optional)
```

## Notes

- Tag your repository with semantic versions (v1.0.0, v1.1.0, etc.) for reproducible URLs
- Test instructions on clean codebases before sharing  
- Write AI-interpretable instructions rather than executable scripts
- Keep dependencies and versions explicit
- Provide clear rollback procedures for breaking changes
- Consider backward compatibility when updating instructions
- Use modular files (`setup.md`, `codemod.md`) for complex instructions

## Common Patterns

### Library Installation Instruction
Focus on: dependencies, configuration files, usage patterns, type definitions

### Architecture Pattern Instruction  
Focus on: folder structure, file templates, import patterns, naming conventions

### Migration Instruction
Focus on: step-by-step replacement, codemods, dependency changes, cleanup steps