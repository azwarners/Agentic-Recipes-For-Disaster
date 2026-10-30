Failed to create stream fd: Operation not permitted
Failed to create stream fd: Operation not permitted
Failed to create stream fd: Operation not permitted
---
name: skill-creator
description: Create or improve a portable agent skill. Use when a user requests a reusable skill with clear boundaries, instructions, and any needed supporting resources.
---

# Skill Creator

## Purpose

Create a focused, portable agent skill that solves the requested capability and can be discovered and used by compatible agent runtimes. This skill guides authoring and validation; it does not define a runtime or modify canonical skills based on reflection.

## Workflow

1. Clarify the intended capability, task boundaries, expected deliverable, target users or runtime constraints, and how success can be checked. Ask only for details that materially affect the result; otherwise state reasonable assumptions.
2. Inspect relevant existing skills, templates, authoring guidance, and repository conventions. Reuse a mature solution or extend an existing skill when appropriate instead of creating a duplicate.
3. Choose the best category for the skill's primary workflow and a concise lowercase kebab-case skill name. Keep category folders as navigation aids; do not assume a runtime will discover only the current task's category.
4. Write lean YAML frontmatter with `name` matching the skill directory and a description that clearly states the capability and when to use it. Give actionable, standalone instructions with clear boundaries and expected outputs.
5. Add relative `references/`, `scripts/`, or `assets/` only when they materially help. Keep the core workflow in `SKILL.md`, explain when supporting files are needed, and avoid unnecessary dependencies.
6. Validate the name, frontmatter, links, relative resource paths, and discovery behavior. Check that the skill can be found through its name and description without relying on category-specific runtime filtering.
7. Exercise the skill against at least one realistic example or task. Report what was actually tested, the findings, and any proposed tests that were not run. Do not claim compatibility with a runtime that was not tested.
8. Deliver the skill path, a concise summary of its behavior and boundaries, validation and exercise results, and any follow-up recommendations.

## Final Reflection

End every completed task, including this skill's first execution, with a concise reflection. Evaluate how effectively Skill Creator supported the actual task; identify ambiguities, omissions, or inefficiencies; and recommend improvements to Skill Creator's instructions, references, scripts, and toolchain, including useful existing or new tools. If no improvement is warranted, state that explicitly. Present actionable suggestions for human review. Do not automatically edit Skill Creator or any other canonical skill, and do not start another implementation cycle based on the reflection.
