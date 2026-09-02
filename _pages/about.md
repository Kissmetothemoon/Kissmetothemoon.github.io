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

My research asks how to make LLM inference faster and cheaper, from algorithms down to silicon. On the algorithm–system side, I work on speculative decoding and serving systems: my recent project **[ASD](https://github.com/Kissmetothemoon/ASD)** is a bounded-regret *Approximate Speculative Decoding* acceptance policy for DSpark speculative decoding in [SGLang](https://github.com/sgl-project/sglang). It relaxes strict greedy verification by admitting draft tokens whose regret stays within a per-request bounded budget, while exactly recovering strict verification at budget zero — on Qwen3-14B (GSM8K) this yields +13.3% tokens/s at a cost of 0.23 pp accuracy. On the hardware side, I study analog compute-in-memory accelerators and noise-aware matrix multiplication, exploring how algorithms should be co-designed with the substrates they run on.

Specific directions include:

- efficient LLM inference — speculative decoding, serving systems, KV-cache & scheduling;
- compute-in-memory architectures — analog CiM accelerators, noise-aware computation.

### Beyond research

I enjoy photography. You can find my photographic works on [Xiaohongshu](https://www.xiaohongshu.com/user/profile/68cba2df000000002102beb5) and [Douyin](https://www.douyin.com/user/self?from_tab_name=kissmetothemoon).

Feel free to reach out via yanruo.f@gmail.com — I'm always happy to discuss inference systems and hardware–algorithm co-design.
