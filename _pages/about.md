---
layout: about
title: about
permalink: /
subtitle: Beihang University · Efficient LLM Inference · Compute-in-Memory

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  more_info: >
    <p>Beihang University</p>
    <p>Beijing, China</p>

selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: false # includes a list of news items（在 _news/ 中准备好内容后改回 true）
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: true
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

I am a PhD student at **Beihang University** and an intern at **ByteDance-PH**. I study how language models generate text, from the way a drafter proposes tokens in different languages to the way analog hardware affects the words a model produces.

**November 2026.** Our paper on diffusion language models for analog in-memory computing was accepted at **DATE 2027**. Yubing Ye and I contributed equally. In hybrid measurements on a 16-chip eFlash system, diffusion models tolerated 1.4–3× as much weight noise as comparable autoregressive models. [Read the paper on arXiv](https://arxiv.org/abs/2611.32223).

### Research

**Multilingual decoding.** Why does the public DFlash drafter on Qwen3-8B deliver a 2.80× single-request speedup in English and only 1.08× in Telugu? In **WorldDraft**, we study 18 language and script conditions and trace part of the gap to tokenization. When a word spans several tokens, a parallel drafter predicts its later pieces before it can see how the word starts. We use counts from monolingual text to propose more likely continuations. The code and interactive results are available now. Preprint coming soon. [Project page](https://kissmetothemoon.github.io/worlddraft-page/) · [Code](https://github.com/Kissmetothemoon/WorldDraft)

**Efficient inference.** ASD lets a speculative verifier accept small token-level deviations within a per-request regret budget. SetCommit coordinates which tokens a diffusion model commits at each step, improving few-step decoding without retraining or extra forward passes. [ASD paper](https://arxiv.org/abs/2608.03447) · [ASD code](https://github.com/Kissmetothemoon/ASD) · [SetCommit](https://github.com/Kissmetothemoon/SetCommit)

**Analog in-memory computing.** I study how generation algorithms respond to noise in physical memory arrays. My earlier work covers noise-aware training, hybrid projection decomposition for state space models, adaptive sampling for diffusion models, expert routing, and KV cache protection. [ASICON 2025 and DATE 2026 papers](/publications/) · [ASSERT](https://arxiv.org/abs/2609.00955) · [ROMER](https://arxiv.org/abs/2605.11800) · [KV cache protection](https://arxiv.org/abs/2607.29076)

### Beyond research

I enjoy photography. You can find my photographic works on [Xiaohongshu](https://www.xiaohongshu.com/user/profile/68cba2df000000002102beb5) and [Douyin](https://www.douyin.com/user/self?from_tab_name=kissmetothemoon).

Feel free to reach out via yanruo.f@gmail.com (or ynfeng@buaa.edu.cn) — I'm always happy to discuss inference systems and hardware–algorithm co-design.
