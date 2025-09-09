# Rollback Instructions for [Instruction Name]

Instructions for undoing the changes made by this instruction.

## Rollback Steps

To undo these changes:

1. **[Rollback Step 1]**
   - [Description of what to undo]
   - [Specific commands or actions]

2. **[Rollback Step 2]**
   - [Description of what to undo]
   - [Specific commands or actions]

3. **Remove the instruction entry from `CLAUDE.md`**
   - Open `CLAUDE.md`
   - Remove the "[Instruction Name]" entry from the "Instructions Applied" section

## File Cleanup

Files to remove:
- `[file-path-1]` - [Description of file]
- `[file-path-2]` - [Description of file]
- `[directory/]` - [Description of directory and contents]

Commands:
```bash
rm [file-to-remove]
rm -rf [directory-to-remove/]
```

## Configuration Cleanup

Settings to revert:
- [Configuration setting 1]
- [Configuration setting 2]

## Git Commands

If you need to revert to the state before applying this instruction:

```bash
# Find the commit before this instruction was applied
git log --oneline

# Revert to that commit (replace COMMIT_HASH with actual hash)
git reset --hard COMMIT_HASH

# Or create a revert commit instead of hard reset
git revert COMMIT_HASH..HEAD
```

## Notes

- [Important note about rollback process]
- [Warning about dependencies or side effects]
- [Recommendation for backup before rollback]