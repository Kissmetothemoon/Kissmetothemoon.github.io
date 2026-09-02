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

I am a researcher at **Beihang University** working on **AI infrastructure**, with a focus on **efficient large language model (LLM) inference** and **compute-in-memory (CiM) architectures**.

My recent work includes **ASD**, a bounded-regret *Approximate Speculative Decoding* acceptance policy for DSpark speculative decoding in [SGLang](https://github.com/sgl-project/sglang) — relaxing strict greedy verification to admit draft tokens whose regret stays within a per-request bounded budget, while exactly recovering strict verification at budget zero. I am also surveying **Diffusion Language Models (DLMs)** and their implications for efficient inference systems.

**Research interests**
- Efficient LLM inference: speculative decoding, serving systems, KV-cache & scheduling
- Compute-in-memory architectures: analog CiM accelerators, noise-aware computation
- Diffusion language models: parallel decoding and system co-design

**Open source**: [ASD](https://github.com/Kissmetothemoon/ASD) (Apache-2.0)

Feel free to reach out via yanruo.f@gmail.com — I'm always happy to discuss inference systems and hardware–algorithm co-design.
