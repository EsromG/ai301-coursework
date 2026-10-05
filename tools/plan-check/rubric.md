# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| bounded-scope | Read the plan's scope statement, files-to-change list, and stated exclusions against the issue and repo facts. | Passes if the plan proposes one bounded change, identifies the relevant files or areas it expects to touch, states meaningful limits on what it will not change, and avoids unrelated cleanup or scope creep. | required |
| diagnosis-grounded | Read the plan's stated cause against the reproduced behavior and repro evidence. | Passes if the diagnosis follows from the reproduced evidence, does not contradict it, and identifies the underlying cause rather than merely describing the visible symptom. | required |
| executable-by-a-stranger | Read the plan's files and implementation approach against the repo facts. | Passes if a developer unfamiliar with the issue could begin implementing the change without needing to guess the main target files, the intended change, or the core implementation approach. | required |
| test-decisive | Read the plan's test plan against the repro steps and expected behavior. | Passes if the plan gives concrete steps or commands to verify the change and states an observable expected result that would distinguish the fixed behavior from the reproduced failure. | required |
| comment-faithful | Read the draft plan comment against the candidate plan, issue thread highlights, and repo conventions. | Passes if the comment accurately reflects the plan, addresses relevant maintainer or thread constraints, and promises only work that the plan actually contains. | required |
| honesty | Read the plan's risks, unknowns, assumptions, and any deviations against the repro evidence and repo facts. | Passes if unresolved questions are identified as uncertainties rather than stated as facts, and any implementation deviation is recorded honestly when applicable. | required |

## Verdict rule

Accept only if every required check passes.

Grade a check `unclear` when the available evidence is missing, ambiguous, or insufficient to determine whether the pass condition is satisfied.

An `unclear` grade on a required check counts as a failure.

Reject if any required check is `fail` or `unclear`.