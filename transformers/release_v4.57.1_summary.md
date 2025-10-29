# Transformers v4.57.1 — Release Analysis

Release link: https://github.com/huggingface/transformers/releases/tag/v4.57.1  


## New models

| Model | Short description / Notes |
|---|---|
| None in this release | This patch release does not add any new models. (See v4.57.0 for the major model additions.) |

---

## Core features

| Feature | Short description / Notes |
|---|---|
| None in this release | No new core features were introduced. v4.57.1 is a patch release focusing on fixes and maintenance. |

---

## Breaking changes

| Breaking change | Short description / Impact |
|---|---|
| None in this release | No breaking changes were introduced in v4.57.1. This patch preserves public APIs and feature semantics. |

---

## Patch fixes (concise list — not summarized in the tables)

- Fix for an optional dependency (`optax`) that caused parsing errors with `poetry`.  
  - Commit: https://github.com/huggingface/transformers/commit/0645c9ec3188e000aecf5060e2cdabcc156bb794
- Remove `offload_state_dict` from kwargs to avoid related issues.  
  - Commit: https://github.com/huggingface/transformers/commit/a92b1e8a45e1863b95c5e2caa12f5597aee80279
- Fix bnb FSDP loading for pre-quantized checkpoints. (PR #41415)
- Fix FSDP-related tests. (PR #41422)
- Fix Trainer compatibility for Python 3.9. (PR #41359)
