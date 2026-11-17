# 读懂 GR00T 2

**在线阅读：<https://wikieden.github.io/reading-gr00t2/>** · [讲义目录](https://wikieden.github.io/reading-gr00t2/lessons/index.html) · [全部动画](https://wikieden.github.io/reading-gr00t2/animations/index.html) · [复习卡片](https://wikieden.github.io/reading-gr00t2/review.html) · [全部讲义书](https://wikieden.github.io/ai-books/)

> 11 章 · 10 个动画（GIF + 可交互页面）· 24 张复习卡片 · 覆盖 GR00T 2 白皮书（2026-11）正文 §1–5 与附录 A–K 的主要内容

## 这本书讲什么

从"WAM 和 VLA 差在哪"讲起，依次走过 GR00T 2 的架构、三阶段预训练、数据配方、跨本体迁移、RL 后训练、agent 协作、人形部署、真机评测方法、实时部署，最后是作者自己列的开放问题。

- **适合谁**：读过 `vla-deep-dive` 第 3 章（action chunking）和第 8 章（π0）；flow matching、Bradley-Terry、PPO 在用到的那一章现场补。
- **读完能做什么**：能独立读懂白皮书附录，评估 WAM 路线在自己项目里的取舍，能复算白皮书里的 token 数、胜率、样本量。
- **怎么读**：按章顺序读。每章先看讲解，再自己做练习，最后用复习卡片隔几天考自己。

## 讲解的特点

- **每章一个动画**：第 1–10 章各配一个，GIF 嵌在讲义"动画演示"一节，同名 `.html` 可单步、拖滑块，目录见 [animations/README.md](https://wikieden.github.io/reading-gr00t2/animations/index.html)。
- **一次一小步**：每个概念按"白话类比 → 公式（每个符号说清楚怎么读）→ 小数字亲手算一遍"讲。
- **对照原文**：讲到原文的地方标 `materials/text/gr00t2-whitepaper.txt` 的行号（如 L130–L131）；推算出来、原文没直接写的数都标了"推算"。
- **保留真实的学习过程**：练习与作答记录里是学习时的原话、对错和点评。
- **术语不设门槛**：缩写第一次出现就给英文全称并逐词解释，全书缩写见 [缩写与术语表](https://wikieden.github.io/reading-gr00t2/lessons/appendix-glossary.html)。
- **每章收尾有口诀**：全部口诀汇总在本页末尾。

## 示例动画

| | | |
|---|---|---|
| ![](https://wikieden.github.io/reading-gr00t2/animations/01-vla-vs-wam.gif)<br>**第 1 章** VLA 与 WAM 能算的 loss · [讲义](https://wikieden.github.io/reading-gr00t2/lessons/01-what-is-a-wam.html) · [▶ 交互](https://wikieden.github.io/reading-gr00t2/animations/01-vla-vs-wam.html) | ![](https://wikieden.github.io/reading-gr00t2/animations/02-token-flow.gif)<br>**第 2 章** token 数与 joint / cached 去噪 · [讲义](https://wikieden.github.io/reading-gr00t2/lessons/02-architecture.html) · [▶ 交互](https://wikieden.github.io/reading-gr00t2/animations/02-token-flow.html) | ![](https://wikieden.github.io/reading-gr00t2/animations/06-cps-grpo.gif)<br>**第 6 章** CPS 探索与带记忆基线 · [讲义](https://wikieden.github.io/reading-gr00t2/lessons/06-rl-post-training.html) · [▶ 交互](https://wikieden.github.io/reading-gr00t2/animations/06-cps-grpo.html) |
| ![](https://wikieden.github.io/reading-gr00t2/animations/08-multirate.gif)<br>**第 8 章** 人形三层频率 · [讲义](https://wikieden.github.io/reading-gr00t2/lessons/08-humanoid.html) · [▶ 交互](https://wikieden.github.io/reading-gr00t2/animations/08-multirate.html) | ![](https://wikieden.github.io/reading-gr00t2/animations/09-elo-arena.gif)<br>**第 9 章** 盲测 A/B 拟合 Elo · [讲义](https://wikieden.github.io/reading-gr00t2/lessons/09-evaluation.html) · [▶ 交互](https://wikieden.github.io/reading-gr00t2/animations/09-elo-arena.html) | ![](https://wikieden.github.io/reading-gr00t2/animations/10-latency-rtc.gif)<br>**第 10 章** 延迟瀑布与 RTC 交接 · [讲义](https://wikieden.github.io/reading-gr00t2/lessons/10-deployment.html) · [▶ 交互](https://wikieden.github.io/reading-gr00t2/animations/10-latency-rtc.html) |

全部动画见 [animations/README.md](https://wikieden.github.io/reading-gr00t2/animations/index.html)。

## 目录

| 章 | 主题 | 一句话精要 | 动画 | 卡片 | 状态 |
|---|---|---|---|---|---|
| 1 | [什么是 WAM](https://wikieden.github.io/reading-gr00t2/lessons/01-what-is-a-wam.html) | WAM 比 VLA 多预测未来画面，这一项让人类视频也能算 loss | [▶](https://wikieden.github.io/reading-gr00t2/animations/01-vla-vs-wam.html) | G01–G03 | 🟡 三步已讲；练习 1 ✓，练习 2、3 待作答 |
| 2 | [架构](https://wikieden.github.io/reading-gr00t2/lessons/02-architecture.html) | 280 token / 路 / 帧，视频和动作同序列一起去噪，Turbo 只换 VAE | [▶](https://wikieden.github.io/reading-gr00t2/animations/02-token-flow.html) | G04–G06 | 🟡 正文已写，练习待作答 |
| 3 | [三阶段预训练与少样本适配](https://wikieden.github.io/reading-gr00t2/lessons/03-pretraining-recipe.html) | 先看后动再认身；rank-32 LoRA 30 分钟 | [▶](https://wikieden.github.io/reading-gr00t2/animations/03-stages-lora.html) | G07–G08 | 🟡 正文已写，练习待作答 |
| 4 | [数据配方](https://wikieden.github.io/reading-gr00t2/lessons/04-data-mixture.html) | 录像管见识、UMI 管任务、遥操作管身体；scaling 未饱和 | [▶](https://wikieden.github.io/reading-gr00t2/animations/04-data-scaling.html) | G09–G10 | 🟡 正文已写，练习待作答 |
| 5 | [X-Adapt](https://wikieden.github.io/reading-gr00t2/lessons/05-x-adapt.html) | 演示定任务、玩耍定身体；几何要对齐、外观交给模型 | [▶](https://wikieden.github.io/reading-gr00t2/animations/05-x-adapt-ablation.html) | G11–G12 | 🟡 正文已写，练习待作答 |
| 6 | [RL 后训练](https://wikieden.github.io/reading-gr00t2/lessons/06-rl-post-training.html) | CPS 加噪、带记忆基线、自模仿最好、世界模型里也能练 | [▶](https://wikieden.github.io/reading-gr00t2/animations/06-cps-grpo.html) | G13–G14 | 🟡 正文已写，练习待作答 |
| 7 | [Agentic](https://wikieden.github.io/reading-gr00t2/lessons/07-agentic.html) | agent 管工序和恢复，图上画点指路；可靠性三层叠 | [▶](https://wikieden.github.io/reading-gr00t2/animations/07-agent-loop.html) | G15–G16 | 🟡 正文已写，练习待作答 |
| 8 | [人形全身](https://wikieden.github.io/reading-gr00t2/lessons/08-humanoid.html) | Turbo 1 Hz 出 80 个 token，SONIC 50 Hz 保平衡；WAM 更会吃仿真 | [▶](https://wikieden.github.io/reading-gr00t2/animations/08-multirate.html) | G17–G18 | 🟡 正文已写，练习待作答 |
| 9 | [评测](https://wikieden.github.io/reading-gr00t2/lessons/09-evaluation.html) | 同场盲测、Bradley-Terry Elo、按任务 bootstrap、仿真相关 0.93 | [▶](https://wikieden.github.io/reading-gr00t2/animations/09-elo-arena.html) | G19–G21 | 🟡 正文已写，练习待作答 |
| 10 | [部署](https://wikieden.github.io/reading-gr00t2/lessons/10-deployment.html) | 加速 2.9–7.2×、noisy-prefix RTC、按阶段变速快 15–26% | [▶](https://wikieden.github.io/reading-gr00t2/animations/10-latency-rtc.html) | G22–G23 | 🟡 正文已写，练习待作答 |
| 11 | [开放问题](https://wikieden.github.io/reading-gr00t2/lessons/11-open-problems.html) | 预测什么、数据汇率、99% 可靠性怎么测 | 无 | G24 | 🟡 正文已写，练习待作答 |

---

本仓库由私有学习仓库里的脚本 `tools/publish-transformer/build.py` 自动生成，内容摘自讲义目录，不要直接修改这里的文件。
