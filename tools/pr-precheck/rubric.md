
# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| plan-fidelity | Compare the changed files and behavior in the diff against the issue, the plan's scope and implementation steps, and any recorded deviations. | Passes if the diff implements the intended issue fix within the plan's stated scope, or any material differences are explicitly recorded and justified in the plan's deviations. Fails if the diff silently adds unrelated work, omits essential planned behavior, or contradicts the issue requirements. | required |
| change-claims-accurate | Compare the PR title, summary, changes list, and reviewer notes against the actual branch diff and plan. | Passes if the PR accurately describes what was implemented, makes no unsupported claims, and clearly discloses material changes or omissions. Concise descriptions are acceptable when accurate. Fails if the description conceals or misrepresents significant differences. | required |
| test-evidence | Compare the plan's test plan with the actual commands, outputs, before/after reproduction evidence, and explanations in the test evidence. | Passes if the evidence demonstrates meaningful verification of the intended change or transparently reports testing limitations and unresolved results with enough detail for a reviewer to assess their significance. Fails if results are fabricated, unsupported, merely asserted, or do not establish what was actually tested. | required |
| repository-checks | Compare the repository's required validation commands against the recorded command executions, results, and explanations in the test evidence. | Passes if all applicable repository-prescribed checks were attempted and their actual outcomes are reported, including failures, skipped checks, or unavailable suites with clear explanations. Fails if required checks are silently omitted or reported as passing without evidence. | required |
| diff-reviewability | Inspect the diff's changed files, hunks, added and removed lines, and any debugging artifacts against the intended fix. | Passes if the change can be reviewed without unrelated edits, debugging leftovers, accidental files, or obsolete commented-out code obscuring its purpose. Fails if unnecessary changes or debris materially interfere with review. A large but necessary change can pass. | required |
| repository-standards | Compare the PR draft against the repository's PR template and contributing rules, including the issue reference, requested testing information, and AI-use disclosure. | Passes if the PR provides the substantive information required by the repository, follows applicable contribution rules, and honestly discloses AI assistance. Fails if material requirements are ignored or misrepresented. Equivalent concise wording is acceptable; exact formatting is not required unless the repository mandates it. | required |
| reviewer-clarity | Read the PR description and reviewer notes against the diff, test evidence, and issue context. | Passes if a reviewer can understand the change, its motivation, and meaningful limitations without reconstructing the entire investigation. Minor wording or stylistic weaknesses alone do not fail the PR. | preferred |

## Verdict rule

Grade every check as `pass`, `fail`, or `unclear`, using specific evidence from the package.

Return `accept` only when every `required` check passes.

Return `reject` if any `required` check is `fail` or `unclear`.

An `unclear` grade means the supplied evidence cannot establish whether the check passes; for verdict purposes, treat it as a failure.

`preferred` checks provide improvement feedback but never change the verdict.

A disclosed limitation or failing test does not automatically require rejection. Judge whether the evidence honestly establishes what was tested, identifies the limitation, and gives reviewers enough information to assess the change. Reject when an essential issue requirement remains demonstrably unmet, when meaningful verification is absent or unverifiable, or when material problems are concealed.

Apply every check before assembling the verdict. Do not stop at the first failure. Do not use a numerical score or create a third verdict.
