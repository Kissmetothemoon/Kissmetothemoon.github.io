---
layout: page
title: ASD
description: Bounded-regret approximate acceptance policy for speculative decoding
importance: 1
category: work
---

**ASD (Approximate Speculative Decoding)** is a bounded-regret acceptance policy for speculative decoding.

It relaxes strict greedy verification — which discards the entire draft suffix at the first mismatch — by admitting draft tokens whose regret (the gap between target logits and draft tokens) stays within a per-request bounded budget. At budget B = 0, ASD exactly recovers strict verification. The policy is implemented as a zero-intrusion adapter: downstream KV commit, finalization, and metrics paths observe an interface identical to the native greedy verifier.

- **Paper**: [arXiv:2608.03447](https://arxiv.org/abs/2608.03447)
- **Code**: [github.com/Kissmetothemoon/ASD](https://github.com/Kissmetothemoon/ASD) (Apache-2.0)
- **Benchmarks**: Qwen3-14B + DSpark on CUDA 12.8 — see the repository for detailed results
