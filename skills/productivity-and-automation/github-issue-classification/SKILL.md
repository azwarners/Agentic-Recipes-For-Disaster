---
name: github-issue-classification
description: Classify GitHub issues by work type and priority, identify documented dependencies, and flag stale assessments. Use when triaging new or changed issues or preparing input for GitHub Work Queue Planning.
---

# GitHub Issue Classification

Use the GitHub read tools available in your runtime. Classify the selected issues across one or more repositories and propose changes for review. Apply specific GitHub changes only after explicit human approval of those changes. Classification does not confer implementation approval.

## Workflow

1. Establish the repositories, issue selection, and any classification policy. Default to incremental triage of unclassified, materially changed, or explicitly invalidated issues. Reuse a prior inventory or cutoff when available. If there is no reliable baseline, say what you inspected. Use a full inventory when requested.
2. Read each issue body, existing labels, and recorded dependencies. Follow references that could change the classification. Check the actual repository label definitions and report gaps in tool access or taxonomy.
3. Classify work type independently from priority. Start with security, bug, architecture, enhancement, or documentation, using established repository equivalents. Keep the three priority levels High, Medium, and Low. Explain the impact behind new recommendations and preserve existing human choices by default. Surface ambiguous work types or conflicting labels for review.
4. Identify what each issue blocks or depends on, with an issue reference and evidence for each relationship. When a later architecture decision materially changes the assumptions of an assessment, flag it as stale and explain what changed. Record uncertainty about prerequisites for review.
5. Report the proposal before applying changes. Use existing labels and preserve unrelated labels and history. If the operator authorizes specific edits, verify the resulting labels or relationships by reading the issue back.

## Output

Summarize what you inspected, what needs review, and the proposed GitHub edits. Include current and proposed type and priority, the exact label names where verified, the evidence and confidence for each proposal, the effect of architectural changes, and any unknowns.

For a machine-readable handoff, return a JSON array of issue records. Use full `owner/repo#number` references. Use `null` for unknown values and an empty dependency list only when no prerequisites were found in the inspected evidence. Treat `proposed_labels` as suggested additions, and describe any proposed removal explicitly in the human-readable report. The example is a proposal for review.

```json
[
  {
    "issue": "example/project#22",
    "current_labels": ["ready"],
    "work_type": "enhancement",
    "priority": "medium",
    "proposed_labels": ["enhancement", "priority:P2"],
    "depends_on": ["example/platform#7"],
    "blocks": [],
    "assessment_stale": true,
    "status": "needs-review",
    "confidence": "high",
    "evidence": "Platform #7 replaces the API assumed in the existing assessment.",
    "unknowns": []
  }
]
```

Use `unchanged`, `proposed-edit`, or `needs-review` for `status`. Report missing metadata in `unknowns`. This handoff supplies classification evidence to the planner. It never grants eligibility or approval.

## Final Reflection

End every completed run with a short reflection on how well the skill supported this triage. Note any rule that was ambiguous, evidence it missed, or work it made you repeat. Suggest a specific change to the instructions, examples, references, scripts, or available tools when warranted. Say explicitly when no change is warranted. Offer changes for human review and leave the canonical skill untouched.
