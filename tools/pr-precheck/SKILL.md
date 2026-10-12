
---

name: pr-precheck 

description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.

---

# pr-precheck: rubric-driven PR grading

## The question

You are grading exactly one PR package to answer one question: is this ready to submit?

A PR package includes a candidate PR title and description, committed changes, branch diff, test evidence, and the plan the change claims to implement, read against the original issue and repository standards.

Do not answer from gut feel. Execute `procedure.md`, apply the checks and verdict rule in `rubric.md`, and use `references/evidence-guide.md` to locate and evaluate supporting evidence.

## Inputs and modes

Use one of two modes:

- **Live mode**: Review the student's own PR package. Read `plan.md`, including any `## Deviations` notes; the committed branch diff produced by `git diff main...HEAD` from the repository root; the proposed PR title and description in `pr_draft.md`; and command results and reproduction evidence in `test_evidence.md`.

  Gather issue-side evidence from the issue thread using the supplied issue URL. Read `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md` to determine the repository's PR requirements.

  Compare the diff against the issue and plan, tests against the planned test steps, and the PR description against the actual diff.

  For a house-chain submission, use the supplied house issue, repro pack, plan, and working branch instead of the student's original work. Apply the same rubric.

- **Eval mode**: Read exactly one practice package bundle from `eval/packages/`. The bundle contains the evidence needed to grade the candidate PR. Use ONLY the bundle text. Do not fetch GitHub information, inspect other repository files, or invent missing evidence.

  Eval mode always grades the complete package: every rubric check and the full verdict rule.

## The scope seam (live mode only)

In live mode, read `scope.md` before gathering any other evidence.

Use its `Repo:` line to determine where the PR must belong and apply its repository-specific rules. Refuse to grade a PR outside the scoped repository.

If `Repo:` is missing or still contains an unfilled placeholder, stop without grading and instruct the student to replace it with their section's Path Review repository. Never guess the repository.

In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

In live mode, read `voice-guide.md` and compare the draft PR title and description against the student's writing rules.

Report any violated rule in the readable summary, identifying the relevant wording and the rule it breaks.

A voice-guide violation does not independently change the verdict unless a rubric check explicitly evaluates it.

In eval mode, ignore `voice-guide.md` entirely.

## Component reads

Read `rubric.md`. It defines:

1. A table of checks, each with a name, evidence, pass condition, and weight (`required` or `preferred`).
2. A verdict rule defining how `pass`, `fail`, and `unclear` grades combine into `accept` or `reject`.

Use `references/evidence-guide.md` to identify where each evidence family lives and what satisfactory evidence looks like.

Execute `procedure.md` as written. It must establish the read order, evidence gathering, check execution, and verdict assembly.

If the procedure leaves a necessary step unspecified, report that gap instead of silently inventing a step.

If `rubric.md` contains no substantive checks or `procedure.md` contains no substantive operating steps, refuse to grade. Identify the missing component rather than improvising a replacement.

## Verdict and output

The verdict space is binary: `accept` (ready to submit) or `reject` (hold). There is no third verdict, conditional acceptance, or numerical score.

Before the JSON block, provide a short readable per-check summary. Include concrete failures, missing evidence, and any live-mode voice-guide violations.

End every completed grading response with the following fenced JSON block, populated using the actual evidence. Nothing may follow it.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

- **Evidence first**: Never grade a check without identifying the specific fact, diff, command output, or quote that decided it. "Looks fine" is not evidence.
- **Grade the change, not the polish**: A short but complete PR can be ready. A polished PR with unrelated changes, missing tests, or unsupported claims must not pass because it reads well.
- **The rubric decides**: Apply each check's written pass condition and the stated verdict rule. Do not override them with personal judgment.
- **The procedure decides how**: Follow `procedure.md` exactly. Report procedure gaps instead of inventing missing steps.
- **Compare claims with evidence**: Verify that the diff matches the plan, test results support the claimed verification, and the PR description accurately represents the change.
- **Treat uncertainty consistently**: Use `unclear` when evidence cannot establish a check's result. Follow the rubric's verdict rule; if it is silent, treat `unclear` as `fail`.
