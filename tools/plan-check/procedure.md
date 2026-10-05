# Procedure: how this skill grades a plan package

## Read order

1. Read the repro evidence first and note the reproduced behavior, the observed failure, and any evidence that rules out possible causes. This establishes the baseline before reading the plan so the diagnosis can be checked against evidence rather than accepted at face value.

2. Read the issue thread highlights next and note the requested behavior, maintainer constraints, and any conventions or boundaries the maintainer has already stated.

3. Read the repo-facts block and note the relevant files, components, commands, and repository conventions that affect where the change belongs.

4. Read the candidate plan and record:
   - its stated diagnosis,
   - what is in scope,
   - what is explicitly out of scope,
   - the files or components it plans to change,
   - its implementation approach,
   - its test plan,
   - any risks or unknowns.

5. Read the draft plan comment last and note what it promises to change, how it describes the diagnosis, and how it says the fix will be verified.

6. Do not grade any rubric check until all of the above have been read and the relevant facts have been noted.


## Evidence gathering

1. For `bounded-scope`, gather:
   - the plan's scope statement,
   - the plan's stated exclusions,
   - the files or areas it expects to change,
   - the issue request and relevant repo facts.
   Record whether the proposed work is one bounded change or whether it includes unrelated cleanup, migration, refactoring, or extra work.

2. For `diagnosis-grounded`, gather:
   - the plan's stated cause,
   - the reproduced behavior,
   - the repro output or observations,
   - any repro evidence that supports or contradicts the stated cause.
   Record whether the diagnosis follows from the reproduction and whether it identifies a cause rather than only restating the symptom.

3. For `executable-by-a-stranger`, gather:
   - the target files or components,
   - the implementation approach,
   - the relevant repo facts.
   Record whether a developer unfamiliar with the issue would know where to start and what change to make without guessing the main implementation details.

4. For `test-decisive`, gather:
   - the original repro steps,
   - the observed before-fix result,
   - the plan's verification steps or commands,
   - the expected after-fix result.
   Record whether the expected result is observable and would clearly distinguish fixed behavior from the reproduced failure.

5. For `comment-faithful`, gather:
   - the draft plan comment,
   - the candidate plan,
   - maintainer signals and issue-thread constraints,
   - relevant repo conventions.
   Record whether the comment matches the plan and whether it promises only work the plan actually contains.

6. If evidence required by a check cannot be found in the named package parts, record that evidence as missing rather than inferring it.


## Check execution

1. Grade the checks in this order:
   1. `diagnosis-grounded`
   2. `bounded-scope`
   3. `executable-by-a-stranger`
   4. `test-decisive`
   5. `comment-faithful`

2. For each check, compare only the gathered evidence for that check against its pass condition in `rubric.md`.

3. Grade `pass` when the evidence clearly satisfies the pass condition.

4. Grade `fail` when the evidence clearly shows that the pass condition is not satisfied or directly contradicts it.

5. Grade `unclear` when evidence needed to decide is missing, ambiguous, or insufficient.

6. Do not turn missing evidence into a pass by assuming what the author probably meant.

7. Do not fail a plan because of formatting, section names, length, or writing style unless the rubric explicitly makes that relevant.

8. When grading a check, record the specific line, statement, or package fact that justifies the grade so the final output can quote the submission's own evidence.

9. A check may be graded without re-reading the whole package if the relevant evidence was already gathered and recorded in the earlier stage.

## Verdict assembly

1. Apply the verdict rule from `rubric.md` after all checks have been graded.

2. If every required check is `pass`, return `accept`.

3. If any required check is `fail` or `unclear`, return `reject`.

4. Treat `unclear` exactly as the rubric specifies; for this rubric, `unclear` on a required check counts as a failure.

5. Preferred checks, if any are added later, do not change the final verdict.

6. In the output, include every check's grade and a short reason based on the gathered evidence.

7. For a `reject` verdict, identify the deciding required check or checks and quote the submission evidence that caused the failure or uncertainty.

8. For an `accept` verdict, state that all required checks passed and quote enough evidence to show why the package is ready to post and build from.