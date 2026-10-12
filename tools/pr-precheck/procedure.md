
# Procedure: how this tool grades a PR package

## Read order

1. Determine the mode before reading evidence:
   - Live mode reviews the student's branch and draft PR.
   - Eval mode reviews exactly one supplied package bundle.

2. In live mode, read `scope.md` first. Verify that the repository matches the configured `Repo:` value. Stop without grading if the scope is missing, unfilled, or mismatched. Read `voice-guide.md` for the outgoing PR's communication requirements. In eval mode, ignore both files.

3. Read `rubric.md`, `references/evidence-guide.md`, and this procedure. Stop without grading if the rubric has no substantive checks or the procedure has no substantive steps.

4. Read the issue requirements before evaluating the implementation:
   - Live: read the linked GitHub issue thread, including its problem statement, reproduction evidence, and relevant discussion.
   - Eval: use only the issue context included in the package bundle.
   Record the expected behavior and any explicit constraints.

5. Read the plan before the diff. Record:
   - Intended fix and root cause.
   - Scope and files expected to change.
   - Implementation approach and exclusions.
   - Planned test steps and expected outcomes.
   - Any `## Deviations` explaining changes to the original plan.

6. Read the actual implementation:
   - Live: run `git diff main...HEAD` from the repository root to inspect all committed branch changes.
   - Eval: read the diff included in the package.
   Record each changed file, material modification, and any unrelated or suspicious changes.

7. Read the test evidence. Record each test command, observed output, before/after reproduction result, failure, skipped check, and stated limitation. Do not interpret a planned test as an executed test.

8. Read the draft PR title, description, and reviewer notes. Record its summary, issue reference, changes list, testing claims, limitations, and AI-use disclosure.

9. Read the applicable repository standards:
   - Live: `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md`.
   - Eval: the repository facts, template requirements, and contribution rules included in the bundle.

Complete these reads before assigning any grades.

## Evidence gathering

Use `references/evidence-guide.md` to locate the following evidence families.

1. **Plan fidelity**
   - List the files and intended behavior from the plan.
   - List the changed files and behavior shown by the diff.
   - Compare the lists side by side.
   - Identify missing implementation, extra changes, or changes to the intended approach.
   - Check whether material deviations are recorded and justified in `plan.md`.
   - Record specific filenames and diff evidence for each discrepancy.

2. **Change claims**
   - Extract the claims in the PR title, summary, changes list, and reviewer notes.
   - Match each material claim to the corresponding diff hunk or recorded deviation.
   - Record unsupported claims, omitted significant changes, or inaccurate descriptions.
   - Do not treat polished language as implementation evidence.

3. **Test evidence**
   - Extract the planned tests and expected outcomes from `plan.md`.
   - Match them to actual executions and outputs in `test_evidence.md` or the eval package.
   - Compare before/after reproduction results against the issue's expected behavior.
   - Record whether the tests verify the intended change, what remains unverified, and whether any limitations were disclosed.
   - Distinguish observed failures from missing evidence. An honestly documented failure is not automatically a rejection.

4. **Repository checks**
   - Identify required validation commands from the repository standards.
   - For Path Review, look for `make test-unit`, `make test-integration`, `make lint`, and `make typecheck`.
   - Match each required command to its execution result and explanation.
   - Record commands that were omitted, failed, skipped, or unavailable.
   - Treat a documented "no tests ran" integration result as evidence of execution, not proof that integration tests passed.

5. **Diff quality**
   - Inspect the changed files and hunks for debugging statements, temporary files, obsolete commented-out code, accidental changes, and unrelated edits.
   - Compare suspicious hunks against the plan and issue to determine whether they are necessary.
   - Record only problems that materially affect reviewability; do not penalize necessary complexity or diff length alone.

6. **Standards and communication**
   - Extract substantive requirements from the PR template and contribution rules.
   - Compare them against the draft PR description.
   - Verify the issue reference, summary, meaningful changes, testing disclosure, reviewer notes, and AI-use disclosure where required.
   - Record missing material requirements or claims that conflict with the evidence.
   - In live mode, check the title and description against `voice-guide.md` and record violations separately.

7. **Reviewer clarity**
   - Determine whether a reviewer can identify what changed, why it changed, and any important risks or limitations from the draft and evidence.
   - Record any material ambiguity, without penalizing concise wording.

Keep the evidence tied to its source. Never fill gaps by assuming that a command passed, a file changed, or a requirement was satisfied.

## Check execution

1. Execute every check in `rubric.md` in table order:
   - `plan-fidelity`
   - `change-claims-accurate`
   - `test-evidence`
   - `repository-checks`
   - `diff-reviewability`
   - `repository-standards`
   - `reviewer-clarity`

2. For each check, use the evidence already gathered and apply its exact pass condition:
   - `pass`: the available evidence satisfies the stated condition.
   - `fail`: the evidence demonstrates that the condition is not satisfied.
   - `unclear`: the evidence is insufficient or conflicting, so the condition cannot be verified.

3. Write one concise evidence line for every grade. Include the specific filename, command result, diff detail, or PR statement that determined it.

4. Do not infer success from silence. If a required command or material claim has no verifiable evidence, grade the affected check `unclear` unless the evidence positively establishes a violation, in which case grade `fail`.

5. Do not reject a PR solely because a check failed during testing if the failure was honestly reported and the rubric's pass condition is otherwise satisfied. Distinguish a disclosed environmental limitation from evidence that the intended fix does not work.

6. Reuse gathered evidence across relevant checks. Re-read a source only when the gathered evidence is insufficient to decide the check. Never invent missing facts.

7. Evaluate all checks, even if an earlier required check fails. Preferred checks receive grades but do not determine the verdict.

## Verdict assembly

1. Collect every check's name, grade, weight, and one-line evidence in rubric order.

2. Apply the verdict rule from `rubric.md`:
   - Return `accept` if every required check is `pass`.
   - Return `reject` if at least one required check is `fail` or `unclear`.
   - Treat `unclear` as failing for verdict purposes.
   - Preferred checks never change the verdict.

3. When the verdict is `reject`, identify the first failing or unclear required check in rubric order as the primary deciding failure. Quote its concrete evidence in the readable summary. Also report other failures so the student can address them.

4. When the verdict is `accept`, identify the evidence supporting the required checks and mention any disclosed limitations or preferred improvements without changing the verdict.

5. In live mode, report voice-guide violations separately from the rubric verdict unless an explicit rubric check makes them decisive.

6. Produce a short readable per-check summary followed by a fenced JSON block matching the exact schema in `SKILL.md`:
   - `item`: the PR URL in live mode or the bundle identifier in eval mode.
   - `checks`: every rubric check, in table order, each with `name`, `grade`, and one-line `evidence`.
   - `verdict`: exactly `accept` or `reject`.

7. Ensure the JSON is valid, with no additional fields, scores, or alternative verdict values. Nothing may follow the final fenced JSON block.
