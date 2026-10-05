# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

EsromG

**Plan comment**


https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5987254292

I reproduced the setup inconsistency described in #73.

The current `.env.example` includes `LLM_PROVIDER=mock` and `OPENAI_API_KEY`, but does not include `OPENROUTER_API_KEY`, while `README.md` and `docs/SETUP.md` direct users to configure OpenRouter. `core/config.py` already defines the corresponding OpenRouter settings, and `OPENAI_API_KEY` is still used separately by the OpenAI embedding provider.

My plan is to keep the change limited to `README.md` and `.env.example`: add the missing `OPENROUTER_API_KEY` example, make the `LLM_PROVIDER` guidance consistent with the documented OpenRouter setup, and keep `OPENAI_API_KEY` for the existing embedding configuration. I won’t change runtime behavior.

I’ll verify the change by copying `.env.example` to `.env` again and grepping for `LLM_PROVIDER`, `OPENAI_API_KEY`, and `OPENROUTER_API_KEY`, then checking that the README and example environment file use consistent configuration names.

---

## Your branch

**Branch**

fix/73-openrouter-env-config

**Evidence**

Before the fix:

```bash
cp .env.example .env
grep -E 'LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY' .env
```

Output:

```text
LLM_PROVIDER=mock
OPENAI_API_KEY=sk-your-key-here
```

`OPENROUTER_API_KEY` was missing even though the README instructed users to configure it.

After the fix:

```bash
rm -f .env
cp .env.example .env
grep -E 'LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY' .env
```

Output:

```text
LLM_PROVIDER=mock
OPENROUTER_API_KEY=sk-or-your-key-here
OPENAI_API_KEY=sk-your-key-here
```

I also checked the relevant configuration references:

```bash
grep -nE 'LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY' README.md .env.example
```

Output:

```text
README.md:24:# Configure environment, then add your OPENROUTER_API_KEY to .env
.env.example:18:LLM_PROVIDER=mock
.env.example:19:OPENROUTER_API_KEY=sk-or-your-key-here
.env.example:20:OPENAI_API_KEY=sk-your-key-here
```

The final implementation commit changed only the intended files:

```bash
git show --stat --oneline HEAD
```

Output:

```text
33212cc fix: align OpenRouter environment setup
 .env.example | 3 ++-
 README.md    | 2 +-
 2 files changed, 3 insertions(+), 2 deletions(-)
```


## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

Run 1: 19/20

**Package analysis**

Package: pkg-20

Rubric verdict: accept

Gold label: reject 

My rubric accepted this package because the diagnosis was directly grounded in the reproduced crash, the proposed scope was bounded to the stale prev pointer and capacity-change handling, and the plan gave concrete implementation and regression-test steps. It also acknowledged the performance risk and explicitly kept broader cached-pointer investigation out of scope. 

The gold label was reject, which shows that my rubric was too permissive for this case. The package proposed a specific generation-counter design even though the issue thread said there were multiple detection approaches worth comparing for cost. My rubric treated that implementation detail as sufficiently executable instead of requiring stronger evidence that the chosen mechanism respected the maintainer's performance constraint.

**Check rationale**

> `honesty` — Passes if unresolved questions are identified as uncertainties rather than stated as facts, and any implementation deviation is recorded honestly when applicable.

I kept this check because a plan can look technically complete while still overstating what has been verified. During my own plan review, this check caught that I had treated OpenRouter runtime behavior as more certain than the code evidence supported. I revised the plan to explicitly state that I had not found runtime code outside `core/config.py` consuming `llm_provider` or `openrouter_api_key`, and I recorded that finding under `## Deviations` instead of claiming there were no deviations. This made the rubric require plans to distinguish verified facts from assumptions and to document what actually happened during implementation.

**Trade-offs**

The clearest trade-off in my final rubric is `pkg-20`. My rubric accepted it, while the gold label rejected it. I accepted that result because the plan was strongly grounded in the reproduction, had a bounded scope, concrete implementation steps, regression tests, and an explicit performance risk. The trade-off is that my rubric gives some credit to a plan that chooses a specific implementation approach before fully benchmarking alternative approaches mentioned by the maintainer. Tightening the rubric enough to reject `pkg-20` could also make it too strict on otherwise executable plans that responsibly identify an open implementation trade-off.


---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
