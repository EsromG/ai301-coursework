# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

EsromG

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5859651837

Picking this up. I’ll verify the configuration mismatch between README.md and .env.example around OPENROUTER_API_KEY and the supported LLM provider configuration, document the exact files and behavior I observe, and post a repro report before making any changes.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5859972483

## Environment

* macOS 15.7.3
* Git 2.39.5
* Python 3.12.7
* Node.js 22.16.0
* npm 10.9.2
* Docker 29.7.2
* Docker Compose 5.5.1
* Commit: 2f4e82f52efbcfcc57d65b3fa5348672163ca088

## Steps to reproduce
1. Clone the repository and enter the project directory.
2. Follow the environment setup instructions: cp .env.example .env
3. Inspect the LLM-related variables in the copied .env: grep -n "LLM_PROVIDER\|OPENROUTER_API_KEY\|OPENAI_API_KEY" .env
4. Compare the result with the instructions in README.md and docs/SETUP.md, which tell the user to configure OPENROUTER_API_KEY.

## Expected behavior
The example environment file should match the documented setup instructions. If the documentation requires OPENROUTER_API_KEY, .env.example should include that variable and clearly document the corresponding provider configuration.

## Observed behavior
After copying .env.example to .env, the relevant values are:
18:LLM_PROVIDER=mock
19:OPENAI_API_KEY=sk-your-key-here
There is no OPENROUTER_API_KEY entry.
At the same time, README.md and docs/SETUP.md instruct the user to set OPENROUTER_API_KEY, while .env.example lists the supported provider options as only mock and openai.
The application configuration in core/config.py also defines OpenRouter-related settings, including openrouter_api_key, openrouter_base_url, and openrouter_model.

## Result
Reproduced. The setup documentation and .env.example are inconsistent about OpenRouter configuration.


## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

20/20 
I confirm the full eval run agreed with the gold labels on all 20 scored packages. The final saved run in eval-run.txt records agreement:
categories: clear-accept 8/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4
agreement: 20/20 scored items  (bar: 18/20: PASS)

**Package analysis**

For `pkg-01`, my rubric returned `accept`, and the gold label was also `accept`. My rubric accepted it because the package satisfies all required checks. The environment is specific: HTTPie 3.2.4, Python 3.12.4, multidict 6.6.0, and macOS 14.5 arm64 are recorded. The reproduction steps are followable because they give the exact `http --offline` commands. The observed behavior matches the issue: with exactly one custom header, `Content-Type: application/json` is missing, while the control run without a custom header includes it. The conclusion is also supported by the recorded terminal output, so the package does not overstate what was reproduced.

**Check rationale**

I used this check from my final rubric: 

> **_outcome-honest_** - Pass when every conclusion is supported by the recorded evidence. An evidenced cannot-reproduce result passes; unsupported certainty, overstating the evidence, or claiming reproduction when the artifact shows a different result fails. I kept this check because the goal of a reproduction report is not just to produce a confident conclusion; it is to make sure the conclusion matches the evidence.

I wanted the rubric to accept an honest cannot-reproduce result when it is well documented, while rejecting reports that claim success without evidence or that reproduce a different problem.

**Trade-offs**

The outcome-honest check is intentionally strict about unsupported conclusions, which means it can reject a report even when the steps and environment are otherwise good if the final claim goes beyond the evidence. The trade-off is that this favors evidence-backed reporting over confident wording. In my final full eval run, this did not introduce a scored-package regression: the rubric matched all 20 gold labels, with agreement: 20/20 scored items.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
