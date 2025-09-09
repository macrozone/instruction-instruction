# Codemod Instructions for Create Instruction Repository

This instruction primarily involves creating files and folder structures rather than transforming existing code. The "codemod" phase consists of content creation and customization tasks.

## Content Creation Tasks

### 1. Template Customization

**What it does**: Replace placeholder content in copied template files with specific values

**Files to process**: All files copied from `templates/` directory

**Transformations needed**:
- Replace `[Instruction Name]` with actual instruction name
- Replace `[VERSIONED-URL]` with actual instruction URL
- Replace `[username]`, `[repo]`, `[version]` with actual values
- Fill in specific prerequisites, setup steps, and code transformations
- Add concrete examples relevant to the instruction being created

### 2. Content Development

**What it does**: Develop the actual instruction content based on specific needs

**Tasks**:
- Define specific changes the instruction should make
- Identify file patterns and code transformations needed  
- Specify exact dependency versions and setup steps
- Create before/after examples
- Write clear, actionable steps for AI agents to follow

### 3. Helper Files (if needed)

**What it does**: Create additional supporting files for complex instructions

**Optional files to create**:
- `examples/before/` - Code samples before applying instruction
- `examples/after/` - Code samples after applying instruction  
- `scripts/` - Any setup scripts or transformation helpers
- Additional template files specific to the instruction

## Notes

- This instruction focuses on file creation rather than code transformation
- The main "coding" work is customizing templates and writing clear instruction content
- Ensure all created content follows the general guidelines: clear, brief, and actionable for AI agents