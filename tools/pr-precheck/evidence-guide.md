
# Evidence guide: where evidence lives in a PR package

Use this guide to locate evidence for each rubric check. In eval mode, use only the supplied package bundle. In live mode, use the student's working copy, issue thread, and repository standards. Do not infer missing evidence or substitute a PR author's claims for observable results.

## Plan fidelity (harness category: silent-drift)

**Where it lives**

- Eval mode: Read the package's issue context and plan-context block, particularly the stated scope, intended files, implementation approach, exclusions, and test plan. Read any documented deviations. Compare those details against the candidate PR's unified diff, changed files, commits, title, description, and changes summary.
- Live mode: Read the GitHub issue thread and `plan.md`, including its scope, implementation steps, and `## Deviations` section. Compare them against the committed changes shown by `git diff main...HEAD`. Read the title, summary, changes list, and reviewer notes in `pr_draft.md`.

**What good looks like**

Every material change in the diff implements the issue within the plan's stated boundary, or is accounted for by an explicit, justified deviation. Essential planned behavior is not silently omitted, and the PR description accurately represents what the diff implements.

**Warning signs**

- Changed files or behavior outside the planned scope without a documented reason.
- Missing essential planned changes with no explanation.
- A description claiming the plan was followed when the diff contradicts it.
- A PR title or summary claiming a fix that the implementation does not deliver.
- Deviations disclosed only in the PR description when the plan requires them to be recorded in `plan.md`.

A justified deviation is not automatically a failure. Judge the actual issue requirements and whether the deviation is documented rather than demanding identical implementation details.

**Related rubric checks:** `plan-fidelity`, `change-claims-accurate`.

## Test evidence (harness category: not-tested)

**Where it lives**

- Eval mode: Read the plan-context block's test plan and the issue's original reproduction steps. Compare them with the candidate PR's test-evidence section, recorded commands, outputs, before/after observations, and testing claims. Read the repo-facts block for required validation commands.
- Live mode: Read the test plan in `plan.md`, reproduction evidence in `repro.md` or the issue thread, and actual results captured in `test_evidence.md`. Compare with the Testing section of `pr_draft.md`. Read `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md` for the required checks.

**What good looks like**

The evidence identifies the behavior tested, the command or reproduction steps used, the expected outcome, and the observed result. Before/after evidence demonstrates whether the issue was addressed, while repository-prescribed checks have recorded outcomes or clearly explained limitations.

**Warning signs**

- Statements such as "tests pass" without observable commands or results.
- Planned tests described as completed without evidence of execution.
- Missing before/after reproduction when that comparison is necessary to verify the fix.
- Required repository checks silently omitted.
- An incomplete or failing check described as successful.
- Test evidence unrelated to the code or documentation that changed.

A documented test failure or unavailable suite is not automatically disqualifying. Distinguish honest reporting of a limitation from missing evidence, a concealed failure, or proof that an essential requirement remains broken.

For Path Review, look specifically for:
- `make test-unit`
- `make test-integration`
- `make lint`
- `make typecheck`

An integration command returning "no tests ran" documents an attempted check; it does not prove integration tests passed.

**Related rubric checks:** `test-evidence`, `repository-checks`.

## Diff quality (harness category: unreviewable)

**Where it lives**

- Eval mode: Inspect the candidate PR's unified diff, changed-file list, and commit list. Compare individual hunks with the issue requirements and planned scope.
- Live mode: Inspect `git diff main...HEAD`, `git diff main...HEAD --stat`, and the committed changes on the current branch. Use `plan.md` to identify whether each significant change belongs to the intended fix.

**What good looks like**

A reviewer can identify the actual fix directly in the changed lines, understand why the files changed, and separate necessary implementation from supporting edits. The diff contains no unrelated modifications or leftover artifacts that materially obscure the fix.

**Warning signs**

- Debugging statements or temporary test code left behind.
- Obsolete commented-out blocks or unused code.
- Unnecessary formatting changes across unrelated files.
- Unrelated feature changes, refactoring, or dependency modifications.
- Temporary files, generated artifacts, or accidental commits.
- A commit history containing unrelated work that becomes part of the PR diff.

Do not penalize a PR merely because its diff is long or contains several commits. Judge whether the changes are necessary, coherent, and reviewable.

**Related rubric check:** `diff-reviewability`.

## Standards and comms (harness category: standards-wall)

**Where it lives**

- Eval mode: Read the repo-facts block for PR template sections, contribution policies, required checks, AI-use disclosure requirements, and maintainer instructions. Compare those requirements against the candidate PR's title, description, testing details, issue reference, and reviewer notes.
- Live mode: Read `.github/PULL_REQUEST_TEMPLATE.md`, `docs/CONTRIBUTING.md`, applicable instructions in the issue thread, and `scope.md`. Compare them against `pr_draft.md`. Also read `voice-guide.md` to evaluate the student's outgoing writing style separately.

**What good looks like**

The PR provides the substantive information required by the repository: what changed and why, which issue it addresses, relevant test results, limitations, and any required AI-assistance disclosure. Explicit maintainer instructions are addressed, and the draft gives reviewers enough context to assess the submission.

**Warning signs**

- Required PR template questions or sections ignored.
- Missing or incorrect issue reference.
- Missing AI-use disclosure when the repository requires it.
- Tests marked successful despite contradictory or absent evidence.
- Explicit contribution requirements or maintainer requests disregarded.
- Template headings retained with meaningless placeholders instead of answers.
- Important reviewer limitations omitted.

Use the repository's actual stated requirements, not generic assumptions about what every PR should contain. Concise wording is acceptable when it communicates the required information.

Assess whether the description accurately represents the diff under **Plan fidelity**, rather than double-counting the same problem as a communication failure.

In live mode, report voice-guide violations in the readable summary. They affect the verdict only if a rubric check explicitly makes them relevant.

**Related rubric checks:** `repository-standards`, `reviewer-clarity`.
