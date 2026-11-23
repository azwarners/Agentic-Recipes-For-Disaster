---
name: redless-plan-review
description: Critically review DeepSeek or Redless implementation assessments and action plans, explain them to a human, right-size work for the current local models, and publish only explicitly approved GitHub plans with verified workflow labels. Use when asked to review, revise, or approve an assessment or its proposed implementation tasks.
---

# Redless Plan Review

## Purpose and boundaries

Act as an independent senior architecture partner. Treat a generated assessment or action plan as a draft, not authority. Produce a technically credible, understandable plan for human approval, grounded in the parent issue, actual repository, existing implementation, and available tools. An assessment may have been generated proactively. Review **one parent issue at a time**, unless explicitly asked otherwise.

Planning, approval, readiness, implementation, and acceptance are distinct. **Review or planning permission never authorizes GitHub writes.** Do not create, edit, relabel, close, or merge GitHub work until the human explicitly approves the proposed changes. Approval of a plan authorizes only publication of that agreed plan, **not code implementation or merging**. The human may reject individual tasks or revise the proposal repeatedly.

The skill is portable: use whatever repository and issue tools the current runtime actually provides. Do not require a particular model, orchestration service, GitHub integration, or test runner. If tools or information are unavailable, report the limitation instead of simulating access or success.

## Workflow states and labels

Determine and verify the repository's **actual label names and selection behavior** before writing; do not invent semantics from label names. For the established ARFD/Redless workflow:

- `planned`: an assessment/plan exists; **not** evidence of approval. Eventually the assessment agent may apply it as soon as planning completes to prevent repetitive assessment. The reviewer should ensure the marker is present where appropriate, but must not claim it prevents repeat assessment without checking the queue's filter.
- `approved`: **explicit human approval** of the implementation plan. The implementation engineer selects authorized work using this marker. Never infer it from `planned` or `ready`.
- `ready`: work can proceed; `blocked`: a concrete impediment prevents proceeding. **They are mutually exclusive.** Either can coexist with `planned`, and either can coexist with `approved`. State the blocker and what would clear it.
- Preserve unrelated labels, priority, and issue history. Do not silently remove or replace labels. If the live repository's semantics disagree with these assumptions, identify the discrepancy and resolve it before mutation.

On approved publication, explicitly apply `planned` and `approved` to each **approved executable implementation issue**; set **exactly one** of `ready` or `blocked` as supported. When a parent is decomposed into children, mark the parent `planned`, link its children, and avoid leaving the parent eligible for duplicate implementation; distinguish summary parent from executable children. Do not mark rejected or merely assessed work `approved`. If a required label is missing, find the established equivalent or report the gap; never silently invent one.

## Review workflow

1. **Gather evidence.** Read the original GitHub issue, complete assessment, source revision, relevant code, architecture, conventions, linked issues, and comments. Check current repository state where possible; note differences from the assessment snapshot. Separate verified facts, assumptions, missing information, and speculation. When access is limited, continue provisionally but say what could not be checked.
2. **Explain the system and plan first.** Before tables or critiques, use the Executive Summary contract below. Identify concrete scripts, services, commands, interfaces, inputs, outputs, handoffs, and what actually changes for the operator. Do not assume familiarity with an implementation's internals.
3. **Review every original task.** Mark keep / revise / split / combine / remove / investigate. For each, explain its purpose in technical and everyday language; identify output, independent usefulness, explicit acceptance criteria, dependencies, readiness/blockers, and whether it duplicates work. Assess security, compatibility, scope, tests, portability, and existing functionality.
4. **Inspect existing work and dependencies.** Search relevant issues and code for duplicates, conflicts, overlapping requirements, or already implemented behavior; read likely matches beyond their titles. Recommend reuse, linking, narrowing, deferring, or omission. Do not change existing issues without approval.
5. **Size implementation units for today's infrastructure.** Prefer bounded, explicit work that a local GPU model can execute reliably, without assuming future dynamic model delegation or Grace-led orchestration already exists. Consider BOTH limited-model capability and the cost of independent implementation, context loading, review, test, and merge cycles. **Checklist steps are not automatically child issues.** If one cohesive deliverable (for example, one skill file plus its fixtures) can be reviewed and merged together, prefer adding a detailed checklist to the existing parent issue and creating **no children**. Create child issues for genuinely independent, closable, reviewable deliverables. Retain fine-grained decomposition *within* an issue where useful.
6. **Recommend the execution tier for each executable issue.** Select **GPU** (fast available model, such as Step-3.7-Flash or MiniMax) by default for bounded, well-specified, low-ambiguity tasks; reserve **Xeons / CPU DeepSeek** for substantial architectural reasoning, difficult coding, high-risk ambiguity, or tasks not realistically manageable by GPU models. Base recommendations on current available infrastructure and observed capability, not parameter count alone or hypothetical future routing. State confidence and why. Flag work needing the human or another environment; VM manipulation and verification may favor the AI PC when practical. Do not claim a model was tested unless it was.
7. **Design verification proportionally.** Every implementation issue has its own appropriate checks and evidence. Treat verification of a cohesive deliverable as part of its **single** review/test/merge cycle. Create separate VM/integration verification or hands-on user acceptance issues **when distinct environment, ownership, schedule, or closure evidence justify them**, not by default for a trivial task. Where separate, state dependencies and avoid making human acceptance testing an automatic prerequisite for closing completed implementation. Document test failures: repair within the current task only when small and in scope; propose follow-up work for unrelated scope or substantial investigation; never hide failed/unrun tests.
8. **Present a revised plan, then stop.** Identify parent readiness, each disposition, exact deliverables, recommended owner/tier, blockers, dependencies, acceptance evidence, and any disputed decisions. Explain whether to update the parent or produce children. Ask for explicit human approval. **Do not publish or label issues while approval is pending.** Review feedback and revise as often as needed.
9. **Publish only the approved plan.** Update the existing issue with complete implementation checklist and tests when a single implementation unit suffices. Otherwise create or reuse scoped child issues with acceptance criteria, dependencies, review boundaries, and model recommendation; keep the parent a concise outcome/coordination summary and link its children. Set the verified planning, approval, and readiness labels according to the label contract above; preserve other labels and do not claim actual implementation has occurred.
10. **Read back and confirm.** Fetch every modified issue and verify body, links, labels (`planned`, `approved`, exactly one of `ready`/`blocked` for executable work), model recommendation, dependencies, and intended assessment/implementation queue eligibility. Check the runner's actual selector where available; otherwise say it is unverified. Report links, changed labels, what was and wasn't created, and remaining blockers. If a write partially failed, report the actual state, not a blanket success.
11. **End with Final Reflection.** After every completed review, briefly evaluate whether the skill helped, ambiguities, mistakes, unnecessary overhead, and changes to instructions, resources, tools, or workflow that would improve it. Explicitly say when none are needed. Offer suggestions for human consideration; **never automatically edit this canonical skill, its references, or start another review/implementation loop** because of reflection.

## Executive Summary — mandatory first section

Put one self-contained **Executive summary** at the start of the review, before technical findings or an approval request. Write for a technically capable Linux operator who might be unfamiliar with the particular software.

1. **Narrative walkthrough:** In cohesive plain English, explain the problem, what happens today, the proposed change, concrete operator action, what named tools/scripts/services do and how they hand off, and what the operator sees when it finishes. Distinguish what this issue delivers from what requires future integration. Include verified constraints and significant unknowns.
2. **Labeled task-by-task explanation:** Give at least one full plain-language sentence for the **parent issue**, one for the **implementation plan as a whole**, and one for **every original task** using its original ID/name; describe what it produces or proves and whether it stays, changes, combines, or is removed. Explain each newly proposed task and separate verification/acceptance work where applicable. Pair technical descriptions with ELI5 explanations.
3. **Decision picture:** Summarize implementation unit count (including **zero child issues** where appropriate), key dependencies, readiness/blockers, GPU versus Xeon recommendations, and the specific decision awaiting approval.

Keep exact command syntax, schemas, test matrices, and detailed evidence in the subsequent technical review. Before sending, verify that the executive summary makes sense without reading those later sections.

## Issue publication checklist

Before GitHub mutation:
- [ ] The human has explicitly approved the current proposed plan and publication scope.
- [ ] Parent-vs-children decision minimizes unnecessary separate review/test/merge cycles while remaining suitable for current GPU capability.
- [ ] Every executable issue has actionable scope, measurable acceptance/test evidence, blockers/dependencies, and a recommended execution tier.
- [ ] Duplicates and existing issue relationships have been checked; unexpected scope changes are not silently made.
- [ ] Repository workflow labels and queue filters have been inspected, or limitations are disclosed.
- [ ] `planned` indicates planning, **not approval**; `approved` is applied explicitly only to approved executable work; `ready` and `blocked` never coexist.
- [ ] Permissions and write targets have been verified.

After mutation:
- [ ] All intended issues are read back; check the exact labels, bodies, dependencies, and links.
- [ ] Confirm parent cannot accidentally be selected for duplicate implementation if children are executable.
- [ ] Distinguish planning finished from implementation finished; report any unverified queue behavior.
- [ ] Complete the Final Reflection.

## Output

Deliver the executive summary, evidence-based review and dispositions, revised issue structure, model/owner assignments, readiness and unresolved decisions, and a clear approval request. Following approval, deliver actual GitHub URLs, verified final states, publication limitations, and reflection. In a review-only conversation with no approval, deliver **no GitHub mutations** and still reflect when the review is complete.
