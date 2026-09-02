---
layout: post
title: "ASD: Trading a Bounded Regret Budget for Faster Speculative Decoding"
date: 2026-09-02 10:00:00 +0800
description: Design notes on a bounded-regret acceptance policy for DSpark speculative decoding in SGLang — +13.3% tokens/s on Qwen3-14B at a cost of 0.23 pp accuracy on GSM8K.
tags: [llm-inference, speculative-decoding, sglang]
categories: [research]
---

Speculative decoding accelerates LLM inference by letting a small draft model propose tokens that a large target model verifies in parallel. But the standard acceptance rule is stricter than it needs to be — and the waste is measurable. This post summarizes the design of **ASD (Approximate Speculative Decoding)**, a bounded-regret acceptance policy I implemented for DSpark in [SGLang](https://github.com/sgl-project/sglang), and what it buys in practice. Code: [github.com/Kissmetothemoon/ASD](https://github.com/Kissmetothemoon/ASD) (Apache-2.0).

## The inefficiency of strict verification

Under strict greedy verification, the first draft token that disagrees with the target model's argmax discards the *entire* remaining draft suffix. In practice, many rejected tokens are nearly as good as the argmax — the target logit gap is tiny — yet they take the whole suffix down with them. The draft model's work is wasted, and the mean accepted length (hence throughput) suffers.

## A bounded-regret acceptance policy

ASD relaxes the rule: a draft token is accepted when its **regret** — the gap between the target's top logit and the target's logit on the draft token — keeps the running total within a **per-request bounded budget B**. The budget is spent as accepted tokens accumulate regret, and clamps at zero.

The key property: **at B = 0, ASD exactly recovers strict verification** — not approximately, but token-for-token identical (verified at 0% drift on 1,319 GSM8K requests). The default configuration is therefore lossless; any quality/speed trade-off is an explicit, quantified opt-in.

## Engineering constraints

Three design decisions kept the integration honest:

- **Zero-intrusion adapter.** The ASD adapter returns the same `(correct_len, bonus, cap_trim_lens)` tuple as the native greedy verifier. KV commit, finalization, metrics, and the next draft round are all unaware of the policy switch. With the flag unset, the code path is bit-identical to upstream.
- **No host synchronization on the hot path.** The per-request regret budget lives as a device tensor, bound at the low-frequency prefill seam. The decode hot path never calls `.item()` — control flow stays on device.
- **Fail-loud optional dependency.** The research package is lazily imported: missing package plus unset flag means fully native DSpark; missing package plus set flag raises at startup, not mid-request. Unsupported runtimes (CUDA graph, overlap scheduling) are rejected at launch as well.

## Measured results

Setup: Qwen3-14B, DSpark block7 draft, 8×NVIDIA L20 (46 GB), torch 2.8.0+cu128, `temperature=0`, `num_speculative_tokens=7`, `max_new_tokens=256`, fixed seed.

| Arm | GSM8K accuracy | TPS (tok/s) | Accept rate | Mean accept length |
|---|---:|---:|---:|---:|
| strict | 79.68% | 66.21 | 48.49% | 3.40 |
| ASD, B=0 | 79.68% (identical) | 72.60 (**+9.7%**) | 48.49% | 3.40 |
| ASD, q25 (B=2.06) | 79.45% (**−0.23 pp**) | 75.04 (**+13.3%**) | 51.08% | 3.58 |

Two observations. First, even B=0 is faster than the stock strict path (+9.7%) — an engineering freebie from the adapter implementation. Second, spending a small regret budget (q25) buys another +3.4 points of throughput and lifts the accept rate by 2.6 pp, at a measured accuracy cost of 0.23 pp on GSM8K — well inside a 1.0 pp acceptance budget. Math500 shows the same direction (12.20% → 12.40%, 90.3 → 94.1 tok/s).

Caveats: these are local research-evaluator numbers on fixed-length generation (`ignore_eos=true`), not SGLang CI results; server-side TTFT/ITL benchmarks remain to be run.

## What's next

- Server-path benchmarks (`sglang.bench_serving`, TTFT/ITL) once the target runtime supports the required CUDA kernels
- Budget schedules beyond fixed B (e.g., quantile-adaptive budgets per request phase)
- Applying the same bounded-regret idea to diffusion LM parallel decoding — a natural fit I am currently surveying

If you work on speculative decoding or serving systems, I'd be glad to hear your thoughts — [issues and PRs welcome](https://github.com/Kissmetothemoon/ASD).
