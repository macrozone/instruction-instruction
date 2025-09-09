# Setup Instructions for Create Instruction Repository

Detailed setup steps for creating a standardized instruction repository.

## 1. Create Repository Structure

### 1.1 For New Repositories or Dedicated Instruction Repositories

Create these files in the root:

- `README.md` - Repository description and usage (use [templates/readme-template.md](./templates/readme-template.md))
- `agent-instructions/[instruction-name]/instruction.md` - The main executable instruction file (use [templates/instruction-template.md](./templates/instruction-template.md))
- `agent-instructions/[instruction-name]/setup.md` - Detailed setup instructions (use [templates/setup-template.md](./templates/setup-template.md))
- `agent-instructions/[instruction-name]/codemod.md` - Detailed code transformation instructions (use [templates/codemod-template.md](./templates/codemod-template.md))

### 1.2 For Existing Repositories

Create instruction files in a dedicated folder to avoid conflicts:

- `agent-instructions/README.md` - Description of available instructions
- `agent-instructions/[feature-name]/instruction.md` - Main instruction file (use [templates/instruction-template.md](./templates/instruction-template.md))
- `agent-instructions/[feature-name]/setup.md` - Setup instructions (use [templates/setup-template.md](./templates/setup-template.md))
- `agent-instructions/[feature-name]/codemod.md` - Codemod instructions (use [templates/codemod-template.md](./templates/codemod-template.md))

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
        ├── codemod.md
```

## 2. Customize Templates

1. Copy the appropriate template files from this instruction's `templates/` directory
2. Replace all placeholder text (`[Instruction Name]`, `[username]`, `[repo]`, etc.) with your specific values
3. Fill in the actual instruction steps, dependencies, and code transformations
4. Add specific prerequisites and examples for your instruction

## 3. Important Considerations for Your Instruction

When writing an instruction, pay attention to:

**General Guidelines**: Instructions are written for AI coding agents, so they should be:
- Clear and unambiguous in their requirements
- Brief and direct without unnecessary explanations
- Actionable with specific steps the agent can execute

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