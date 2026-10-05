# Evidence guide: where evidence lives in a plan package


## Diagnosis and grounding

### Where it lives

In eval mode, look at:
- the candidate plan's diagnosis or stated cause,
- the repro-evidence block,
- the issue context when it describes the observed failure.

In live mode, look at:
- the diagnosis in the draft plan,
- the student's posted reproduction comment,
- the issue thread for the original reported behavior.

### What good looks like

The stated cause explains behavior that the repro evidence actually shows and does not contradict evidence that rules out that cause.

A good diagnosis identifies the underlying break rather than only repeating the visible symptom.



## Scope

### Where it lives

In eval mode, look at:
- the candidate plan's scope statement,
- its in-scope and not-in-scope boundaries,
- the files or areas it says it will change,
- the issue context and repo-facts block for the requested change.

In live mode, look at:
- the scope section of the draft plan,
- the files-to-change list,
- the issue thread,
- relevant repository documentation or contributing guidance.

### What good looks like

The plan describes one bounded change tied to the issue and states meaningful limits on what will not be changed.

The named files or areas support that change without unrelated cleanup, opportunistic refactors, migrations, or other work that expands the scope.

## Executability

### Where it lives

In eval mode, look at:
- the candidate plan's files or areas to change,
- the implementation approach,
- any stated order of work,
- the repo-facts block for repository structure and conventions.

In live mode, look at:
- the draft plan's files and approach sections,
- the repository tree,
- relevant source files,
- repository documentation when it explains how the affected area works.

### What good looks like

A developer unfamiliar with the issue can identify where to start, which files or components to work in, and the main change to make without asking the author for the missing core approach.

The plan does not need line-by-line code, but it must provide enough direction to begin implementation without guessing the main design.

## Test plan

### Where it lives

In eval mode, look at:
- the candidate plan's test plan,
- the repro-evidence block,
- the original reproduction steps,
- the observed before-fix output or artifact.

In live mode, look at:
- the test plan in the draft plan,
- the student's posted reproduction,
- any commands, logs, screenshots, or other artifacts used to demonstrate the bug.

### What good looks like

The test plan names concrete steps or commands and an observable expected result after the fix.

The after-fix result should clearly distinguish corrected behavior from the reproduced failure. A vague instruction such as "verify it works" is not enough.

## Honesty


### Where it lives

In eval mode, look at:
- the candidate plan's risks and unknowns,
- any assumptions in the diagnosis, scope, or approach,
- the Deviations section when evaluating a plan after implementation,
- repo facts or repro evidence that show whether a claim is actually established.

In live mode, look at:
- the draft plan's risks and unknowns,
- unresolved questions in the issue thread or reproduction,
- the plan's Deviations section after the build.

### What good looks like

Known facts are stated as known, and unresolved questions are labeled as risks, assumptions, or unknowns rather than presented as certainty.

If implementation differs from the original plan, the Deviations section records what changed and why instead of pretending the original plan was followed exactly.

## Comms

### Where it lives

In eval mode, look at:
- the draft plan comment,
- the candidate plan,
- issue thread highlights,
- the repo-facts block,
- contribution templates, repository conventions, and any AI-use disclosure requirements included in the package.

In live mode, look at:
- the draft comment,
- the full GitHub issue thread,
- maintainer replies,
- CONTRIBUTING documentation,
- issue or pull request templates,
- repository policies that apply to the contribution.

### What good looks like

The comment reflects the actual diagnosis, scope, approach, and test plan rather than promising work that the plan does not contain.

It responds to relevant maintainer signals and repository conventions instead of using generic boilerplate. If the repository requires disclosures, templates, or contribution-specific information, the comment follows those requirements.
