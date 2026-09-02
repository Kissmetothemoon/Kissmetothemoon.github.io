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

I am a researcher at **Beihang University**, working on **AI infrastructure** — efficient large language model (LLM) inference and compute-in-memory (CiM) architectures.

### Research

**Current — AI infrastructure for efficient inference.** I work on making LLM inference faster and cheaper. My recent project **[ASD](https://github.com/Kissmetothemoon/ASD)** ([arXiv:2608.03447](https://arxiv.org/abs/2608.03447)) introduces a bounded-regret approximate acceptance policy for speculative decoding. I am currently working on efficient inference optimization for **Diffusion Language Models (DLMs)**.

**Past — software–hardware co-optimization for compute-in-memory.** I studied how to deploy neural networks robustly on analog CiM, a new AI acceleration substrate, addressing hardware noise through co-design: noise-aware training and straight-through estimation ([ASICON'25a](/publications/)), hybrid projection decomposition for state space models ([ASICON'25b](/publications/)), noise-aware sampling for diffusion models ([DATE'26](/publications/)), and noise-resilient LLM inference on CiM ([ROMER](https://arxiv.org/abs/2605.11800), [KV cache protection](https://arxiv.org/abs/2607.29076)).

### Beyond research

I enjoy photography. You can find my photographic works on [Xiaohongshu](https://www.xiaohongshu.com/user/profile/68cba2df000000002102beb5) and [Douyin](https://www.douyin.com/user/self?from_tab_name=kissmetothemoon).

Feel free to reach out via yanruo.f@gmail.com (or ynfeng@buaa.edu.cn) — I'm always happy to discuss inference systems and hardware–algorithm co-design.
