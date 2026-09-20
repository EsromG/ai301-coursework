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

[The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.]

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
paste the output here, including the closing JSON block
```

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

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
