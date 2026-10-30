# Authoring skills

Place each skill in `skills/<category>/<skill-name>/SKILL.md`. Choose the category that best matches the skill's primary workflow. If no category fits, propose a concise lowercase kebab-case category rather than placing skills directly in `skills/`. Keep skill directory names short, descriptive, and lowercase kebab-case.

The `name` in the skill frontmatter should match the skill directory name (not the category name).

## Required structure

Begin each `SKILL.md` with YAML frontmatter containing:

- `name`: the skill identifier, matching the skill directory name.
- `description`: a concise explanation of what this skill does and when an agent should use it.

Write the instructions for an agent that has not seen the surrounding conversation. State the task boundary, workflow, and expected output. Prefer concrete steps and reference bundled resources by relative path.

## Supporting files

Add files only when they help the skill do its job:

- `scripts/` for executable helpers.
- `references/` for material the agent should consult as needed.
- `assets/` for templates or other files used by the skill.

Keep the main `SKILL.md` focused. Explain when and why to read supporting files. Avoid duplicating long reference material in the instructions.

## Before submitting

- Confirm the category exists and is the best fit for the skill's primary workflow.
- Confirm the skill directory and frontmatter `name` match.
- Check that the description makes the intended use clear.
- Verify all referenced files exist and use paths relative to the skill directory.
- Remove placeholders and instructions that do not apply.
