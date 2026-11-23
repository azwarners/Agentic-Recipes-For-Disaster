---
name: github-work-queue-planning
description: Propose an ordered, dependency-aware GitHub issue batch for Redless assessment or implementation. Use when choosing what to work on next or preparing a batch for an existing runner.
---

# GitHub Work Queue Planning

Use available GitHub read tools and, when supplied, the GitHub Issue Classification handoff. Produce a proposed batch for human review. Obtain separate explicit authorization for GitHub changes or queue execution.

## Workflow

1. Identify the repositories, selected issues, requested mode (`assessment` or `implementation`), and any constraints such as batch size, exclusions, or compute target. When the mode is unspecified, clarify it or show separate proposals for the two modes.
2. Inspect current issue state, dependencies, workflow labels, and any recorded approval or invalidation. Use classification records as evidence and verify eligibility from current GitHub state. Preserve the existing three priority levels and verify the repository's actual label meanings. Flag missing prerequisites, contradictory labels, or cycles. Confirm which prerequisites must be completed versus which can be handled earlier in an ordered batch.
3. In **assessment mode**, choose open work that still needs a valid assessment and can be assessed with the available evidence. Put architectural decisions ahead of dependent assessments they could invalidate. Defer an invalidated assessment until the superseding requirements are clear.
4. In **implementation mode**, choose executable issues with current, explicitly approved plans, verified readiness, and satisfied prerequisites. In the ARFD workflow, `planned` records an existing plan, `approved` records approval, and `ready` records readiness. Exclude blocked or stale work and coordination parents whose executable children already cover the work. Honor verified execution-target labels when relevant. If prerequisites are themselves in the proposed batch, put dependent work in a later batch unless the runner can verify prerequisite success before proceeding.
5. Order eligible work by confirmed dependencies first. Within those constraints, prioritize urgent security or production-breaking work and use the established issue priorities for the rest. Honor the operator's selection and show any requested items you could not include and why. Keep issues with unresolved eligibility out of the executable batch.

## Output

Give an ordered list with issue links, inclusion reasons, prerequisite status, and relevant compute targets. List deferred or excluded issues with the evidence and what would make each eligible. Call out any operator-approved overrides.

Before providing runner input, inspect the applicable version of the Shell Script of Power or the operator's selected batch interface. If verified, provide the exact input format or the exact transformation from the planning data. If unavailable, provide a planning-only handoff and identify the compatibility check that remains. A simple handoff can use `mode`, an ordered `items` array (issue, dependencies, reason, execution target when known), and an `excluded` array (issue, reason, evidence).

For example, if an urgent fix has no prerequisites and a feature needs an unresolved architecture decision, propose the urgent fix first. In assessment mode, also include the architecture decision if it qualifies and defer the feature assessment. In implementation mode, include the fix only with verified approval and readiness, and defer the feature until its prerequisites clear.

## Final Reflection

End every completed run with a short reflection on whether the skill helped choose and explain the batch. Note any ambiguous eligibility rule, missing evidence, or unnecessary work. Suggest a specific change to the instructions, examples, references, scripts, or available tools when warranted. Say explicitly when no change is warranted. Offer changes for human review and leave the canonical skill untouched.
