# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73

**Verdict output**

All five required checks gathered. Verified the issue's premise directly: README.md:24 says "add your OPENROUTER_API_KEY to .env", while .env.example lists only OPENAI_API_KEY and offers "mock" / "openai" for LLM_PROVIDER. The contradiction is real and sits in exactly the two files the issue names.

Grading summary (live mode, codepath/pathreview-ai301-fa26-s3 — inside scope):

- maintainer-active — pass. Human default-branch commits by Aburke225 on 2026-09-16 (4 days ago), and that same COLLABORATOR posted triage comments closing issues on 2026-09-16. Not bot activity.
- repo-active — pass. archived: false, last push 2026-09-16 — well inside 180 days.
- newcomer-scope — pass. One bounded task ("Make the two files agree") across two named files, estimated 1–2 hours, labeled good first issue / tier-1 by a collaborator. No umbrella list, no design debate (zero comments), no abandoned attempts — the repo has no PRs at all.
- issue-available — pass. No assignees; the full issue timeline is only four labeled events, so no linked PR or cross-reference; zero comments; a repo-wide PR search for 73 returns nothing. The one recent claim comment in the repo (acordero4852, 2026-09-19) is on a different issue — and under the Path Review house rule a classmate's claim wouldn't block it anyway.
- contribution-policy — pass. docs/CONTRIBUTING.md exists with no AI clause; no AI_POLICY.md, and the PR template asks only for green CI and tests. Silence passes.

Every required check passes, so the verdict is accept. On fit: this lands squarely in your "clearly explained and reasonably scoped" preference — the issue names the files, states the expected outcome, and needs no architecture decisions. The honest caveat is that it's a docs-consistency fix, so it will build your GitHub-workflow confidence (branch, PR, template, CI) more than your debugging skills; worth following with a bug-labeled tier-1 issue next.

{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
  "checks": [
    {"name": "maintainer-active", "grade": "pass",
     "evidence": "Human commits by collaborator Aburke225 on main 2026-09-16 (4 days ago), plus his COLLABORATOR triage comments same day."},
    {"name": "repo-active", "grade": "pass",
     "evidence": "Repo archived=false and pushed_at=2026-09-16T21:50:20Z, within 180 days."},
    {"name": "newcomer-scope", "grade": "pass",
     "evidence": "Body asks one bounded change across README.md and .env.example, est. 1-2 hours; labeled 'good first issue'/'tier-1'; no comments, no prior PRs."},
    {"name": "issue-available", "grade": "pass",
     "evidence": "assignees: []; timeline contains only 4 'labeled' events (no linked PR); 0 comments; repo-wide PR search for 73 returns total_count: 0."},
    {"name": "contribution-policy", "grade": "pass",
     "evidence": "docs/CONTRIBUTING.md contains no AI-related clause and no AI_POLICY file exists; no stated AI policy passes."}
  ],
  "verdict": "accept"
}

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

- `agreement: 17/20 scored items  (bar: 18/20: below the bar)`
- `agreement: 0/3 scored items`
- `agreement: 3/3 scored items`
- `agreement: 18/20 scored items  (bar: 18/20: PASS)`
- `agreement: 19/20 scored items  (bar: 18/20: PASS)`

The first full run scored 17/20. I then used `--only` on issue-01, issue-15, and issue-19 to test the disagreements. Before changing the rubric, that run scored 0/3. After updating the newcomer-scope check, the same three issues scored 3/3. The next full run scored 18/20, and my final saved run scored 19/20.

**Issue analysis**

I analyzed `issue-15`. My final rubric decision was `reject`, and the gold label was also `reject`, shown in the final run as:

`issue-15  reject  reject   yes`

The issue had been open for several years and had a history of people claiming it and then being unassigned. It also had two closed linked pull requests. My earlier version of the rubric did not treat repeated abandoned attempts as a strong enough scope signal, so it originally accepted this issue. I changed the scope check so that repeated claim-and-abandon cycles or multiple closed unmerged PRs count as evidence that the issue may be harder than it first appears.

**Check rationale**

The check I revised is:

`| newcomer-scope | Issue body, Comments section, and Repo facts linked PR history | Pass if the issue asks for one bounded piece of work. Fail if it is explicitly an umbrella or tracking issue, the comments show unresolved design debate with no maintainer decision, a maintainer explicitly says the work requires core-internal changes, it is only a usage/support question, or its history shows multiple abandoned implementation attempts such as two or more closed unmerged PRs or repeated claim-and-abandon cycles. Do not fail only because the issue touches several files, contains detailed requirements, or describes technically complex implementation ideas. | required |`

I changed this check because my first version was too strict about issues that looked technically complex or touched several files, but it was not strict enough about issues with a long history of abandoned attempts. The revised wording focuses on evidence from the issue history instead of assuming that detailed or technical work is automatically too large for a newcomer.

**Trade-offs**

The change helped with the three issues I re-ran using:

`--only issue-01,issue-15,issue-19`

Before the change, the result was `0/3 scored items`. After the change, it was `3/3 scored items`. The trade-off is that the check can still accept a difficult issue when there is no visible history showing that other contributors struggled with it. I chose not to reject issues only because they sound technical, because that caused acceptable issues like issue-01 and issue-19 to be rejected.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**


1. This issue fits me because it is clearly explained and small enough to finish in the time I have.

2. The verdict correctly identified that it is well scoped, unclaimed, and in an active repo. I also noticed it is more of a documentation/configuration task than a debugging task.

3. I do not expect claiming it to be difficult because it is unassigned and has no active pull request

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
