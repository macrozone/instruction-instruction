# [Instruction Title]

**Source**: [VERSIONED-URL]

## Description

Clear description of what this instruction accomplishes and its intended outcome.

## Prerequisites

List what must be in place before this instruction can be applied:
- [Prerequisite 1]
- [Prerequisite 2] 
- [Required versions/tools]

## Instruction Steps

### 1. Git State Verification

Check that the repository is in a clean state (no uncommitted changes). If on `main` branch, create a feature branch (e.g., `instruction/[repo-name]-[timestamp]`). If there are uncommitted changes, reject processing and ask user to commit or stash them first.

### 2. Check for Existing Application

Check if this instruction has already been applied:

1. Look for this instruction in `CLAUDE.md` under "Instructions Applied"
2. If found and user hasn't explicitly requested an update, inform user that instruction is already applied
3. If user requests update or version differs, follow the update process in [update.md](./update.md)
4. If not found, proceed with fresh application

### 3. Documentation Updates

Update or create `CLAUDE.md`:

```markdown
## Instructions Applied

- **[Instruction Name]**: Applied [VERSIONED-URL] on [DATE]
  - **Purpose**: [Why this instruction was applied]
  - **What it does**: [Main changes/additions made]
  - **Files affected**: [Files created/modified]
  - **Usage**: [How to use the new functionality]
  - **Dependencies**: [New dependencies or tools required]
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

### Before State
```[language]
[example of code/structure before applying instruction]
```

### After State
```[language]
[example of code/structure after applying instruction]
```


## Notes

Additional information that helps with applying this instruction:
- [Important detail 1]
- [Common gotcha or issue]
- [Troubleshooting tip]