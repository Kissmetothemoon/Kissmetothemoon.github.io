---
layout: page
title: WorldDraft
description: Why parallel drafting slows down when a tokenizer splits words into many pieces
importance: 0
category: work
---

On Qwen3-8B, the public DFlash drafter delivers a 2.80× single-request speedup in English and only 1.08× in Telugu. Our study spans 18 language and script conditions. When a tokenizer splits a word into several pieces, the drafter predicts them in parallel from the same prefix. A later piece can therefore be inconsistent with the start of the word.

WorldDraft counts within-word continuations in monolingual text and uses them to rerank and extend draft candidates before verification. In Telugu, it raises the single-request speedup from 1.08× to 1.62× with the same drafter.

Explore the language-by-language results and step through recorded drafts on the project page. Preprint coming soon.

[Interactive project page](https://kissmetothemoon.github.io/worlddraft-page/) · [Code and results](https://github.com/Kissmetothemoon/WorldDraft)
