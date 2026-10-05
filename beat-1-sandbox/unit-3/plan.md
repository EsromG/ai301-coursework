# Plan

## Diagnosis

The setup documentation and example environment file disagree about the LLM API key and provider configuration.

My reproduction showed that after copying `.env.example` to `.env`, the relevant values are:

> `LLM_PROVIDER=mock`  
> `OPENAI_API_KEY=sk-your-key-here`

There is no `OPENROUTER_API_KEY` entry in `.env.example`.

At the same time, `README.md` tells users to add `OPENROUTER_API_KEY` to `.env`, while `docs/SETUP.md` also identifies `OPENROUTER_API_KEY` as the key used for AI features. `core/config.py` already defines OpenRouter-related settings, including `openrouter_api_key`, `openrouter_base_url`, and `openrouter_model`.

Issue #73 specifically identifies `README.md` and `.env.example` as the files that disagree and asks to make them consistent.

`OPENAI_API_KEY` should not simply be removed from `.env.example`, because `ingestion/embeddings/provider.py` still defines an OpenAI embedding provider that expects that environment variable. The documentation fix therefore needs to distinguish the OpenRouter LLM configuration from the existing OpenAI embedding configuration rather than treating the two API keys as interchangeable.

## Scope

### In scope

- Update `README.md` and `.env.example` so the Quick Start instructions and example environment variables agree.
- Add an `OPENROUTER_API_KEY` placeholder to `.env.example`.
- Update the `LLM_PROVIDER` guidance in `.env.example` to include OpenRouter where appropriate.
- Preserve `OPENAI_API_KEY` because it is still used by the OpenAI embedding provider.
- Make the purpose of the OpenRouter and OpenAI keys clear enough that a user copying `.env.example` can follow the README without having to invent a missing variable.

### Out of scope

- Changing LLM runtime behavior.
- Modifying `core/config.py`.
- Modifying `ingestion/embeddings/provider.py`.
- Refactoring the configuration system.
- Adding a new provider implementation.
- Changing unrelated environment variables.
- Changing unrelated documentation.

## Files to Change

- `README.md`
- `.env.example`

`core/config.py` and `ingestion/embeddings/provider.py` will be used as supporting evidence to verify the existing configuration fields and the continued use of `OPENAI_API_KEY`, but I do not expect to modify either file.

## Approach

1. Review the LLM setup instructions in `README.md` and the LLM section of `.env.example`.

2. Update `.env.example` so its LLM configuration explicitly includes an `OPENROUTER_API_KEY` placeholder, matching the key that the README tells users to configure.

3. Update the provider guidance next to `LLM_PROVIDER` so OpenRouter is named as an available configuration instead of listing only `mock` and `openai`.

4. Keep `OPENAI_API_KEY` in `.env.example` because it is still consumed by `ingestion/embeddings/provider.py` when the OpenAI embedding provider is used.

5. Adjust the surrounding comments in `.env.example`, and the README wording if necessary, so the OpenRouter LLM key and OpenAI embedding key are not presented as interchangeable.

6. Keep the implementation limited to `README.md` and `.env.example`; no runtime/provider logic will be changed.

## Test Plan

### Before the fix

1. Copy the example environment file:

```bash
cp .env.example .env
```

2. Inspect the LLM provider and API-key entries:

```bash
grep -E 'LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY' .env
```

Expected current result:

```text
LLM_PROVIDER=mock
OPENAI_API_KEY=sk-your-key-here
```

`OPENROUTER_API_KEY` should be absent, demonstrating the mismatch with the README.

3. Confirm that the README instructs users to configure OpenRouter:

```bash
grep -n 'OPENROUTER_API_KEY' README.md
```

Expected result: the Quick Start section contains an instruction to add `OPENROUTER_API_KEY` to `.env`.

### After the fix

1. Remove the copied test file and recreate it from the updated example:

```bash
rm -f .env
cp .env.example .env
```

2. Inspect the relevant provider/key entries again:

```bash
grep -E 'LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY' .env
```

Expected result:

- `OPENROUTER_API_KEY` is present in the copied environment file.
- `OPENAI_API_KEY` remains present for the existing OpenAI embedding configuration.
- The `LLM_PROVIDER` section/comments identify OpenRouter consistently with the documented setup.

3. Check both setup files together:

```bash
grep -nE 'LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY' README.md .env.example
```

Expected result: the README and `.env.example` refer to the same OpenRouter API-key name, and `.env.example` no longer omits the variable that the README tells users to configure.

4. Verify that only the intended files changed:

```bash
git diff -- README.md .env.example
git status --short
```

Expected result: the implementation changes are limited to `README.md` and `.env.example`; no runtime source files are modified.

## Risks and Unknowns

- `core/config.py` defines `LLM_PROVIDER` and OpenRouter settings, but this documentation-only change does not attempt to prove or modify all runtime provider-selection behavior. The change is limited to resolving the configuration mismatch identified in issue #73.
- `OPENAI_API_KEY` is still needed by the existing OpenAI embedding provider, so removing it while fixing the OpenRouter documentation could break a separate configuration path. It will therefore remain in `.env.example`.
- If implementation inspection shows that `LLM_PROVIDER=openrouter` is not actually consumed by the current runtime, I will not add runtime support as part of this issue. I will keep the documentation change consistent with the configuration already present and record the discrepancy as a deviation or follow-up rather than expanding the scope.

## Deviations

During implementation verification, I found that `LLM_PROVIDER` and the OpenRouter configuration fields are defined in `core/config.py`, but I did not find runtime code outside that configuration module consuming `llm_provider` or `openrouter_api_key`.

I did not add or modify runtime provider support because issue #73 is limited to the setup/configuration mismatch between `README.md` and `.env.example`, and runtime changes are explicitly out of scope for this fix.

The implementation otherwise followed the accepted plan: I changed only `README.md` and `.env.example`, added the missing `OPENROUTER_API_KEY` example and OpenRouter provider guidance, preserved `OPENAI_API_KEY`, and labeled it separately for the existing OpenAI embedding configuration so the two API keys are not presented as interchangeable.