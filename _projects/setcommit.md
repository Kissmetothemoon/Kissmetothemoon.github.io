---
layout: page
title: SetCommit
description: Coordinated token commitments for few-step diffusion language model decoding
importance: 1
category: work
---

**SetCommit** is a training-free commitment-selection layer for masked diffusion language models (DLMs).

Few-step DLM decoding must decide, at each denoising step, *which* token predictions to commit and which to keep revisable. Tokens that look reliable individually can be jointly inconsistent, and premature commitments lose later conditioning. SetCommit treats this as a set-selection problem: it balances per-token reliability against local joint commitment risk, and performs budget-neutral local exchanges so newly revealed context can replace vulnerable earlier commitments. It adds no model forward, requires no training, and composes with Native sampling, Fast-dLLM fixed/adaptive modes, and entropy-bounded (EB) sampling.

- **Code**: [github.com/Kissmetothemoon/SetCommit](https://github.com/Kissmetothemoon/SetCommit) (MIT)
- **Blog post**: [Coordinating Parallel Token Commitments in Few-Step Diffusion Language Models](/blog/2026/setcommit-coordinated-token-commitments/)
- **Benchmarks**: LLaDA-8B / Dream-7B on GSM8K, MATH-500, MBPP, HumanEval — up to +7.4 pp accuracy at 32 NFE; 1.44–1.74x geometric-mean incremental speedups at matched quality
