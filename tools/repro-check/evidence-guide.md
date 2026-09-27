# Evidence guide: where proof lives in a reproduction package

## Environment

Where it lives: In an eval bundle, look at the repro report's environment record and compare it with the issue context and the repo-facts block. In live mode, look at the environment information in the student's draft repro comment, the GitHub issue thread, and the repository's setup or contribution documentation.

What good looks like: The environment identifies the version and OS needed to place the reproduction, plus relevant build/toolchain information and commit or tag when applicable. It matches the issue's targeted environment, or any meaningful difference is explicitly called out.

## Steps

Where it lives: In an eval bundle, look at the reproduction steps in the repro report and use the issue context and repo-facts block to identify the required starting state. In live mode, look at the student's draft repro comment together with the GitHub issue and the repository's setup documentation.

What good looks like: A stranger can start from the stated starting state and follow the actions through the exact command or action that triggers the observed result without guessing a necessary command, input, setting, or prerequisite.

## Behavior shown

Where it lives: In an eval bundle, compare the issue's described behavior with the repro report's observed result and artifacts, such as terminal output, logs, screenshots, or other recorded evidence. In live mode, compare the student's supplied evidence directly with the behavior described in the GitHub issue.

What good looks like: The evidence shows the same relevant behavior described by the issue. Evidence of a different error, failure, command, or adjacent problem does not count as reproducing the target issue.

## Honesty

Where it lives: In an eval bundle, compare the claim comment and repro report's conclusions with the environment, steps, observed result, artifacts, and issue description. In live mode, compare the student's statements with the evidence in the draft and the issue thread.

What good looks like: The report states only what the available evidence supports. A cannot-reproduce result is acceptable when the report clearly records what was attempted and what was actually observed; unsupported certainty or claiming reproduction when the evidence shows a different result is not.

## Comms

Where it lives: In an eval bundle, compare the claim comment and repro report with the issue context, repo-facts block, repository contribution rules, issue templates, and any stated AI-use disclosure requirements. In live mode, compare the student's draft with the GitHub issue and the repository's README, CONTRIBUTING file, AGENTS.md, issue templates, or other contributor instructions where applicable.

What good looks like: The communication is specific to the issue, accurately states the contributor's current status and next action, and follows the repository's stated contribution, template, and disclosure requirements. If the repository requires an AI-use disclosure, that disclosure must be explicitly present with the required details; a missing required disclosure fails this check. A pre-reproduction claim promises the repro work rather than claiming the bug has already been reproduced.


