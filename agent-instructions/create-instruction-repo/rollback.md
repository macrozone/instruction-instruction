# Rollback Instructions for Create Instruction Repository

Instructions for undoing the changes made by this instruction.

## Rollback Steps

To undo these changes:

1. **Delete the created `agent-instructions/` folder and its contents**
   ```bash
   rm -rf agent-instructions/
   ```

2. **Remove the instruction entry from `CLAUDE.md`**
   - Open `CLAUDE.md`
   - Remove the "Create Instruction Repository" entry from the "Instructions Applied" section

3. **If repository was created specifically for this instruction, consider removing the entire repository**
   - This applies only if the repository was created solely to house this instruction
   - Otherwise, keep the repository and only remove the instruction-related files

4. **Revert any template customizations made to existing files**
   - If any existing files (like `README.md`) were modified during setup, revert those changes
   - Check git history to identify any other files that were modified

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

- Always verify what you're deleting before running removal commands
- Consider backing up any customized content before rolling back
- If other instructions depend on this one, they may also need to be rolled back