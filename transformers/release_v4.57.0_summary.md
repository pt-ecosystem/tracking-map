# Transformers v4.57.0 — Analysis

Release link: https://github.com/huggingface/transformers/releases/tag/v4.57.0  

## New models

| Model / Entry | Short description (key points) | Reference (PR / notes) |
|---|---|---|
| Qwen3‑Next | Next‑generation foundation models optimized for extreme context length and parameter efficiency. Key innovations: Hybrid Attention (Gated DeltaNet + Gated Attention), High‑Sparsity MoE (activation ratio ~1:50), Multi‑Token Prediction (MTP), zero‑centered & weight‑decayed layernorm, improved stability. Example: Qwen3‑Next‑80B‑A3B (80B total, ~3B active). | Added in #40771 (release notes / Qwen blog) |
| Vault Gemma | Text‑only Gemma derivative (1B) that drops some norms after Attention/MLP and uses full attention in all layers. Trained with sequence‑level differential privacy (DP‑SGD) and provides a (ε ≤ 2.0, δ ≤ 1.1e‑10) per 1024‑token sequence guarantee. | Added in #40851 (release notes / VaultGemma tech report) |
| Qwen3 VL | Multimodal vision‑language series (dense & MoE variants, Instruct & Thinking versions). Improvements: enhanced MRope with interleaved layout, DeepStack integration for multi‑level ViT features, improved video time alignment (text timestamp alignment). | Added in #40795 (release notes / paper) |
| LongCat‑Flash | 560B MoE model with dynamic activation (~18.6B–31.3B active, avg ~27B). Shortcut‑connected MoE architecture for faster inference (>100 tokens/s), supports up to 128k context length, strong reasoning & benchmark performance (e.g., MMLU). | Added in #40730 (release notes / LongCat‑Flash report) |
| Flex Olmo | MoE architecture designed for distributed training without data sharing (independent expert training) and data‑flexible inference with domain‑informed routing. Trained on FlexMix (public + domain datasets). | Added in #40921 (release notes / FlexOlmo paper) |
| LFM2‑VL | Liquid AI’s device‑aware vision‑language models (LFM2 backbone + SigLIP2 NaFlex encoders). Variants: shape‑optimized and base vision encoders; supports native resolutions up to 512×512 and thumbnail+patch strategies. | Added in #40624 (release notes / Liquid AI blog) |
| BLT (Byte Latent Transformer) | Byte‑level LLM with entropy‑based dynamic patching. Two‑model design (Patcher entropy model + Main transformer). Dynamic patch sizes allocate compute where needed; aims to match tokenization‑level performance while improving efficiency. | Work in progress: #38579 (release notes / BLT paper) |
| Qwen3 Omni MoE (Qwen2.5‑Omni lineage) | Unified multimodal model family supporting text/audio/video outputs. Multiple generation classes: combined, text‑only, audio‑only. Processor helpers (chat template), notes about audio single‑batch and processor.max_pixels for video OOM. | Added in #41025 (release notes / Qwen Omni report) |
| Parakeet | NVIDIA NeMo Parakeet ASR models: Fast Conformer encoder + CTC / RNNT / TDT decoders. Includes ParakeetForCTC (Fast Conformer + CTC). | Added in #39062 (release notes / NVIDIA NeMo) |
| EdgeTAM | On‑device adaptation of SAM2 for real‑time video segmentation using a 2D Spatial Perceiver to optimize memory attention for mobile devices. | Added in #39800 (release notes / EdgeTAM paper) |
| OLMO3 | Olmo3 model added (details to be expanded in model docs). | Added in #40778 (release notes) |

---

## Core features

| Feature | Short description (key points) | Reference / notes |
|---|---|---|
| Continuous Batching (CB) — stable | Introduces Continuous Batching as a stable feature for efficient batched generation. Primary use case: batched generation in GRPO training/evaluation and general batched inference. CB supports both full attention and sliding‑window attention (so it works for many models including LLaMA, Gemma3, gpt‑oss). Integrated with `transformers serve` to enable OpenAI‑compatible HTTP serving. Includes API like `model.generate_batch(inputs=...)` and generated_tokens decoding. Release notes include a usage snippet demonstrating dataset tokenization and `model.generate_batch`. | Release notes (detailed usage snippet provided) |

---

## Breaking changes

All items listed in the release notes under "Breaking changes" are reproduced here to ensure full coverage of changes that may affect users' code or behavior.

| Breaking change | Short description / impact | Reference (PR) |
|---|---|---|
| Remove Group Beam Search decoding strategy | Group Beam Search decoding strategy removed — users relying on this decoding strategy must migrate to alternatives. | #40495 |
| Remove Constrained Beam Search decoding strategy | Constrained Beam Search decoding strategy removed — users relying on this must adapt generation approach. | #40518 |
| Allow `check_model_inputs` in core VLMs | Core VLMs now allow the `check_model_inputs` flag — impacts how VLM input validation is handled. | #40342 |
| Update Glm4V to use config values | Glm4V updated to respect config values (behavior and defaults may change). | #40712 |
| Fix inconsistent `input_feature` and `attention_mask` lengths in WhisperFeatureExtractor | WhisperFeatureExtractor input length vs attention_mask length inconsistency fixed — could change expected preprocessing shapes/behavior. | #39221 |
| Add ministral model (⚠️ 🔴) | A ministral model was added (flagged in breaking section). Check release notes for migration/compat details if you rely on model lists or tooling that enumerates models. | #40247 |
| Move variable output controls to `_prepare_generation_config` | Variable output control logic moved to `_prepare_generation_config` — generation configuration and hooking points may need code updates. | #40715 |
| Make `center_crop` fast equivalent to slow | The fast `center_crop` implementation made behaviorally equivalent to the slow implementation — image processor results may change slightly if relying on previous fast behavior. | #40856 |

---
