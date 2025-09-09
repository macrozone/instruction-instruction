# [Instruction Title]

**Source**: [VERSIONED-URL]

## Description

Clear description of what this instruction accomplishes and its intended outcome.

## Prerequisites

List what must be in place before this instruction can be applied:
- [Prerequisite 1]
- [Prerequisite 2] 
- [Required versions/tools]

## Dependencies

(Optional - only include this section if there are dependencies)

Other instructions that must be applied before this one:
- **[Instruction Name]**: [URL]


## Instruction Steps

### 1. Git State Verification

The AI agent will:
- Verify repository is in clean state (no uncommitted changes)
- Create feature branch if currently on `main` (e.g., `instruction/[repo-name]-[timestamp]`)
- Reject processing if uncommitted changes exist

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

#### 4.1 [Setup Step Name]

Describe what this step does and why it's needed.

*Example setup steps might include:*
- Installing dependencies
- Creating configuration files
- Setting up folder structure
- Initializing tools

#### 4.2 [Another Setup Step]

[Description of step]

### 5. Commit Setup Changes

After completing all setup steps, commit the changes following the repository's commit message conventions:

```bash
git add .
git commit -m "[Commit message following repo conventions - typically describing the setup changes made]"
```

### 6. Conditional Steps

(Optional) Steps that only apply under certain conditions:

#### 6.1 If [Condition] is detected

**Detection**: [How to detect this condition]
**Action**: [What to do when condition is met]

*Example conditions might include:*
- Detecting specific frameworks or libraries
- Checking for existing configuration files
- Identifying project types or patterns

### 7. User Confirmation for Codemod

Ask the user for confirmation before proceeding with code transformations:

```
The setup phase is complete. Would you like me to proceed with applying code transformations now? 

This will:
- [List specific code changes that will be made]
- [Files that will be modified]
- [Any potentially destructive changes]

Reply 'yes' to proceed or 'no' to stop here.
```

### 8. Codemod Instructions

Describe code transformations needed.

For complex transformations, reference a separate `codemod.md` file:
**See**: [codemod.md](./codemod.md) for detailed transformation instructions.

#### 5.1 [Transformation Name]

**What it does**: [Description of the transformation]

**Pattern to Find**:
```[language]
[code pattern to find]
```

**Replace With**:
```[language]
[replacement code pattern]
```

**Files to Target**: `[glob pattern for files to modify]`


## Examples

### Before State
```[language]
[example of code/structure before applying instruction]
```

### After State
```[language]
[example of code/structure after applying instruction]
```

## Rollback Instructions

To undo these changes:

1. [Rollback step 1]
2. [Rollback step 2]

## Notes

Additional information that helps with applying this instruction:
- [Important detail 1]
- [Common gotcha or issue]
- [Troubleshooting tip]