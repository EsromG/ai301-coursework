# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | The repro report's environment record, read against the issue's environment/version context and the repo-facts block; use the Environment section of `references/evidence-guide.md`. | Pass when the environment identifies the version and OS needed to place the reproduction, plus relevant build/toolchain or commit/tag information when applicable, and it either matches the issue's targeted environment or clearly identifies the meaningful difference. | required |
| steps-followable | The repro report's reproduction steps, read with the issue context and repo-facts block; use the Steps section of `references/evidence-guide.md`. | Pass when a stranger could start from the stated starting state and perform the actions needed to reach the reported result without guessing a necessary command, input, setting, or prerequisite. | required |
| behavior-matches | The repro report's actual result and artifacts, such as terminal output, logs, screenshots, or other evidence, read directly against the behavior described by the issue; use the Behavior shown section of `references/evidence-guide.md`. | Pass when the evidence shows the same relevant behavior described by the issue, or clearly shows that the issue could not be reproduced after following the documented reproduction attempt. Fail when the evidence instead shows a different or merely adjacent failure while the report claims the target issue was reproduced. | required |
| outcome-honest | The claim comment and repro report's conclusions, read against the environment, steps, observed result, artifacts, and issue description; use the Honesty section of `references/evidence-guide.md`. | Pass when every conclusion is supported by the recorded evidence. An evidenced cannot-reproduce result passes; unsupported certainty, overstating the evidence, or claiming reproduction when the artifact shows a different result fails. | required |
| comms-conform | The claim comment and repro report, read against the issue context, repo-facts block, repository contribution rules, templates, and any AI-use disclosure requirements; use the Comms section of `references/evidence-guide.md`. | Pass when the communication is specific to the issue, accurately states the contributor's current status and next action, and follows the repository's stated contribution, template, and disclosure requirements. A claim posted before reproduction must promise the repro work rather than assert that reproduction already happened. | required |



## Verdict rule

Accept only when every required check passes. Reject if any required check fails or is unclear. Preferred checks, if added later, never change the verdict.
