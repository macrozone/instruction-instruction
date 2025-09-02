# Instruction-Instruction

A standardized framework for creating executable instructions that AI coding agents can follow to modify codebases consistently and reliably.

## Purpose

This repository defines a standard format for creating "instruction files" that can be shared across projects and teams. These instruction files allow developers to tell AI coding agents: "please read and execute these instructions from [URL/path]" to automatically apply consistent patterns, configurations, or architectural changes to their codebase.

## How It Works

When an AI agent processes an instruction file, it follows this standardized workflow:

1. **Git Verification**: Ensures clean repository state and creates feature branch if on `main`
2. **Dependency Processing**: Applies any prerequisite instruction dependencies first
3. **Conditional Analysis**: Detects project characteristics and applies only relevant steps
4. **Documentation Updates**: Updates `claude.md` or other agent configuration files to reference the exact instruction URL used
5. **Setup Execution**: Follows AI-interpretable instructions to install dependencies, create files, and configure tools
6. **Codemod Application**: Follows AI-interpretable instructions to transform existing code according to patterns
7. **User Confirmation**: Informs the user about planned changes and requests approval before execution

The framework also supports **dry-run mode** to preview changes without execution.

## Use Cases

- **Library Integration**: "Install and configure [library] with best practices"
- **Architecture Patterns**: "Implement feature-based folder structure"
- **Technology Migration**: "Replace REST API calls with GraphQL queries using co-located fragments"
- **Code Standards**: "Apply consistent error handling patterns across the codebase"
- **Configuration Setup**: "Configure ESLint + Prettier with team standards"

## Benefits

- **Consistency**: Ensures the same setup/patterns are applied identically across projects
- **Traceability**: Track which instructions were applied and when, enabling easy updates
- **Shareability**: Teams can create and share standardized setups and patterns
- **Updateability**: Check for instruction updates and apply changes incrementally
- **Automation**: Reduce manual setup time and human error

## Example Instruction Repository

**"GraphQL Migration"**: An instruction that migrates from PayloadCMS local API to a GraphQL API, including:
- Setting up the local GraphQL server
- Installing necessary dependencies (GraphQL clients, codegen tools)
- Applying codemods to replace Payload API calls with GraphQL queries
- Setting up co-located fragments and type generation for optimal developer experience

## Repository Structure

Each instruction repository should contain:
- `README.md`: Description of what the instruction does
- `instruction.md`: The main executable instruction file
- `setup.md`: Setup instructions (optional, for complex setups)
- `codemod.md`: Code transformation instructions (optional, for complex codemods)

## Getting Started

To create your own instruction repository, use this repository's own instruction file: `create-instruction-repo.md`

To apply an instruction to your project:
```
"Please read and execute these instructions: https://github.com/username/repo/blob/v1.0.0/instruction.md"
```

**Note**: Always use versioned URLs (tags or commit hashes) instead of `main` branch to ensure reproducible results. The agent should verify and resolve the exact commit when processing instructions.