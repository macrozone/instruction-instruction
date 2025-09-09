# Update [Instruction Name]

## Version Information

- **Current Version**: [URL from CLAUDE.md]
- **Target Version**: [New URL being applied - from instruction URL or latest release]

## Update Process

### 1. Compare Versions

Quickly diff the current and target instruction files to understand what has changed:
- Changes in setup steps
- Changes in codemod transformations  
- New or removed files
- Updated dependencies or prerequisites

### 2. Apply Target Instruction

Follow the target instruction normally, but:
- Skip steps that are already correctly applied
- Pay attention to changes identified in the diff
- Update existing configurations rather than creating from scratch where appropriate

### 3. Update Documentation

Update `CLAUDE.md`:
```markdown
- **[Instruction Name]**: Updated to [TARGET-URL] on [DATE]
  - **Previous version**: [CURRENT-URL] 
  - **Key changes**: [Brief summary from diff]
```

## Notes

- The update process is essentially re-applying the instruction with awareness of what changed
- Focus on the differences rather than rebuilding everything from scratch
- Test that the update works as expected