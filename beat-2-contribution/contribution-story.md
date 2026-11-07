# Contribution: jerry ast parse/query: json_output param is dead code

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** 1 

**Student:** Esrom Ghebreweldi 

**GitHub Username:** EsromG

**Issue:** https://github.com/geekatron/jerry/issues/378

**Pull Request:** Pending


One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Built and improved issue-scout for finding and evaluating Python open-source issues.**

I customized the issue-scout skill with Python-focused GitHub search queries, ranking filters, and a rubric for evaluating beginner-friendly issues. My initial scan found 297 unique issues and graded five, but three were incorrectly accepted despite depending on unfinished work. I updated the newcomer-scope check to reject blocked issues and documented the findings. I then used the improved skill to evaluate two issues from the CodePath tracker and selected geekatron/jerry#378 as my contribution.

**Unit 6:  Installed and tested voice-guard and updated issue-scout for real-world contributions.**

I consolidated my existing voice guides into one shared file and installed the voice-guard hook to check outgoing GitHub comments. I verified the hook by attempting `gh issue comment --help`, which was correctly blocked before execution. I also updated issue-scout with the `scope-feasible` rubric and regraded my selected issues. For Jerry #378, I created a 40-line `CLAUDE.local.md` containing the repository conventions, relevant CLI files, and development commands. I used a focused Claude Code investigation instead of mapping the entire repository, and configured `.git/info/exclude` to keep the memory file out of my pull request.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I used my customized issue-scout skill to search for Python open-source issues that matched my experience and were suitable for a focused contribution. My initial scan found 297 unique issues, which were reduced to 248 after filtering. During evaluation, I discovered that some issues passed the rubric despite depending on unfinished work, so I improved the scope check and documented the results. I then directly evaluated two candidates from CodePath's Issue Selection site: geekatron/jerry#378 and emfcamp/Website#1075. Both were accepted by the scout, but I selected Jerry #378 because it had a clearer problem description, identified the affected functions, and recommended a specific fix.

Jerry #378 involves removing an unused json_output parameter from two Python CLI functions. The issue fits my Python experience and gives me an opportunity to work with an unfamiliar open-source codebase, follow its contribution standards, and practice test-driven development. My updated scout rated the issue accepted with straightforward difficulty. The scout was helpful for narrowing down candidates, but its original scope check was too restrictive for real-world issues. In Unit 6, I replaced newcomer-scope with scope-feasible so that open design questions inform difficulty rather than automatically rejecting an issue. I also learned that claiming an issue does not necessarily require waiting for the maintainer's reply before beginning the investigation.

Claim comment: 

https://github.com/geekatron/jerry/issues/378#issuecomment-6549787788 

**Toolkit**

- Tool: issue-scout, customized with Python-focused search queries, ranking filters, and a five-check evaluation rubric.
- What it produced: An initial scan of 297 unique issues, 248 filtered candidates, and two directly graded Python issues. Jerry #378 received an accepted verdict with straightforward difficulty.
- Difficulties: The initial rubric accepted issues blocked by unfinished work. My later newcomer-scope check also risked rejecting otherwise feasible real-world issues with open design questions.
- What changed: I first improved the scope check to identify blocked work. In Unit 6, I applied the official patch, replacing newcomer-scope with scope-feasible and adding straightforward, moderate, and ambitious difficulty notes. I documented the changes in scan-notes.md and regraded both candidates.

---

## Understanding the Issue

**Problem Description**

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

[What a stranger would need to stand this up: your operating system,
the relevant versions (language, runtime, package manager, the project
itself), and how you set the project up. Then the challenges you faced
and how you solved them, or that none came up.]

**Steps to Reproduce**

1. [Step 1]
2. [Step 2]
3. [Observed result]

**Reproduction Evidence**

- **Commit showing reproduction:** [link to commit in your fork]
- **Screenshots/logs:** [if applicable]
- **My findings:** [what you discovered during reproduction; an
  honest, evidenced cannot-reproduce that led you to re-pick or ask
  the maintainer belongs here and costs you nothing]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
