# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| maintainer-active | Repo facts: last 5 default-branch commits and maintainer first-response sample; issue Comments section for Owner, Member, or Collaborator activity | Pass if there is evidence of recent human maintainer activity, such as a human default-branch commit within the last 90 days or a maintainer response to recent issues within 30 days. Bot-only activity does not count unless it reflects a merged human pull request. | required |
| repo-active | Repo facts: archived flag, latest release, and last push to any branch | Pass if the repository is not archived and has had a push or release within the last 180 days. | required |
| newcomer-scope | Issue body, Comments section, and Repo facts linked PR history | Pass if the issue asks for one bounded piece of work. Fail if it is explicitly an umbrella or tracking issue, the comments show unresolved design debate with no maintainer decision, a maintainer explicitly says the work requires core-internal changes, it is only a usage/support question, or its history shows multiple abandoned implementation attempts such as two or more closed unmerged PRs or repeated claim-and-abandon cycles. Do not fail only because the issue touches several files, contains detailed requirements, or describes technically complex implementation ideas. | required |
| issue-available | Repo facts: this issue assignees and linked PRs; Comments section for claim comments or mentioned PRs | Pass if the issue has no active assignee, no open linked or mentioned pull request, and no clear recent claim showing another contributor is actively working on it. | required |
| contribution-policy | Repo facts: contribution policy; CONTRIBUTING.md, AI policy files, and contributor documentation if available | Pass if the repository does not explicitly prohibit AI-assisted or AI-generated contributions. Policies requiring disclosure, testing, understanding, or human review pass. No stated AI policy also passes. | required |

## Verdict rule

Accept an issue only if every required check passes. If any required check fails, reject the issue. If the evidence for a required check is unclear or insufficient, treat it as a fail. Preferred checks, if added later, may help rank accepted issues but do not change the accept or reject verdict.
