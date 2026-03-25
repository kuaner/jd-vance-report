# J.D. Vance: Seven Faces — Deep Investigation Report

[中文](#中文) | [English](#english)

---

## 中文

> 一个由 AI Agent 在超长时间跨度下独立完成的深度调研与可视化项目。

**数据截止日期**：2026 年 3 月 24 日。所有新闻引用、民调数据、社交媒体采集和预测市场数据均截至该日期，报告发布后的事件不在覆盖范围内。

**项目持续时间**：约 24 小时（2026-03-24 00:11 首个调研文件创建 → 2026-03-24 23:49 最终页面完成）。Agent 在单日内连续完成了从资料搜集到可视化交付的全流程。

### 项目概述

本报告对 J.D. Vance 的政治生涯进行了全景式深度调查，从俄亥俄州 Middletown 的童年创伤，到耶鲁法学院、海军陆战队服役、硅谷风投圈、副总统竞选、慕尼黑演讲引发的外交地震、伊朗战争中被边缘化的困境，直至 2028 总统大选的权力博弈——七个章节，约 40 万字的调研文字，浓缩为一份交互式的可视化网页报告。

**整个项目——选题策划、资料搜集、深度调研、数据分析、结构化写作、前端可视化设计、代码生成——全部由 [duoduo](https://github.com/openduo/duoduo) agent 在人类编辑的极少量方向性指导下完成。** 人类角色的介入仅限于：确认调研方向、提供图片下载辅助、对可视化风格提出修正意见。文字内容、数据交叉验证、论点构建、代码实现均由 Agent 独立产出。

本项目是 [Long-Context Agent 研究验证](#项目目的)的一部分，旨在测试 AI Agent 在长时间、多阶段、跨领域复杂任务中的连贯性和产出质量。

### 在线阅读

访问 https://kuaner.github.io/jd-vance-report/ 阅读完整报告（自动根据浏览器语言切换中英文，也可手动切换）。

### 项目结构

```
jd-vance-report/
├── index.html                          # 入口：自动检测语言跳转
├── ch/                                 # 中文版
│   ├── index.html                      # 首页：报告导览
│   ├── rust-belt-son.html              # 第一章：铁锈带之子
│   ├── hillbilly-elegy.html            # 第二章：乡下人的悲歌
│   ├── metamorphosis.html              # 第三章：蜕变
│   ├── silicon-valley-kingmakers.html  # 第四章：硅谷造王者
│   ├── munich-shockwave.html           # 第五章：慕尼黑震动
│   ├── iran-trap.html                  # 第六章：伊朗困境
│   └── road-to-the-throne.html         # 第七章：王座之路
├── en/                                 # 英文版
│   ├── index.html                      # Home: Report Overview
│   ├── rust-belt-son.html              # Chapter I: Son of the Rust Belt
│   ├── hillbilly-elegy.html            # Chapter II: Hillbilly Elegy
│   ├── metamorphosis.html              # Chapter III: Metamorphosis
│   ├── silicon-valley-kingmakers.html  # Chapter IV: The Silicon Valley Kingmakers
│   ├── munich-shockwave.html           # Chapter V: The Munich Shockwave
│   ├── iran-trap.html                  # Chapter VI: The Iran Trap
│   └── road-to-the-throne.html         # Chapter VII: Road to the Throne
├── assets/                             # 49 张配图（~24MB）
├── screenshots/                        # 中文版截图
└── research/                           # 调研原始数据（不发布）
```

### 七章内容

| 章 | 标题 | 核心议题 |
|----|------|---------|
| I | [铁锈带之子](https://kuaner.github.io/jd-vance-report/ch/rust-belt-son.html) | Middletown 童年创伤、海军陆战队、耶鲁法学院——信念内核的形成 |
| II | [乡下人的悲歌](https://kuaner.github.io/jd-vance-report/ch/hillbilly-elegy.html) | 回忆录的商业化成功、300 万册销量、身份叙事与真实之间的裂缝 |
| III | [蜕变](https://kuaner.github.io/jd-vance-report/ch/metamorphosis.html) | 8 条反 Trump 原话的 180 度翻转、Streisand 效应、社交媒体病毒传播 |
| IV | [硅谷造王者](https://kuaner.github.io/jd-vance-report/ch/silicon-valley-kingmakers.html) | Thiel/Sacks/Andreessen/Lonsdale 权力网络、$15M 投资、社交资本变现 |
| V | [慕尼黑震动](https://kuaner.github.io/jd-vance-report/ch/munich-shockwave.html) | MSC 2025 演讲全文逐段分析、欧洲跨大西洋地震、Musk vs Greta 效应 |
| VI | [伊朗困境](https://kuaner.github.io/jd-vance-report/ch/iran-trap.html) | 五大政策领域全面溃败、41% 战争支持率（历史最低）、Vance vs Rubio 权力消长 |
| VII | [王座之路](https://kuaner.github.io/jd-vance-report/ch/road-to-the-throne.html) | 好感度崩塌、预测市场冲击、Draft Rubio 运动、2028 初选格局 |

### 技术实现

- **纯前端**：每个 HTML 文件完全自包含（CSS + JS 内联），无构建步骤，可独立访问和分享
- **数据可视化**：Chart.js 折线图/柱状图 + 手工编码 SVG 图表 + CSS 数据卡，融入叙事流
- **深色编辑主题**：oklch() 色彩空间、Display serif + 几何无衬线 + 中文黑体的字体层级
- **响应式**：640px 断点适配移动端
- **中英双语**：根据浏览器语言自动切换，支持手动切换，`localStorage` 记住偏好
- **总计 16 个 HTML 文件**（中英各 8 个），约 800KB；49 张配图，约 24MB

### 数据来源

#### 社交媒体数据采集（34 个 JSON 数据集，约 2.7MB）

通过 Reddit 和 Twitter/X 公开 API 进行结构化数据采集，覆盖 17 个主题维度。

#### 新闻媒体与深度报道

调研文字交叉引用了 The Atlantic、New York Magazine、New York Times、Washington Post、NPR、CNN、BBC、The Guardian 等数十家媒体来源。

#### 民调与预测数据

- RealClearPolitics、Rasmussen Reports、Pew Research、DDHQ/The Hill、YouGov、PredictIt/Polymarket、Betfair/Kalshi

#### 图片来源

49 张配图来自 Wikimedia Commons、Getty Images、AP、Reuters、官方竞选发布等。Agent 在调研阶段主动识别和记录潜在配图来源，写入 `image-assets.md`，可视化阶段直接匹配下载。

### 项目目的

本项目是一个 **AI Agent Long-Running 能力验证实验**，验证长程连贯性、多阶段任务管理、多 Agent 协同、Memory 生命周期管理、数据交叉验证能力和输出质量与迭代能力。

### 工具

- [duoduo](https://github.com/openduo/duoduo) — 自主 Agent 运行时
- [rdt-cli](https://github.com/public-clis/rdt-cli) — Reddit 数据采集 CLI
- [twitter-cli](https://github.com/public-clis/twitter-cli) — Twitter/X 数据采集 CLI
- [Chart.js](https://www.chartjs.org/) — 数据可视化

### 许可

本项目内容仅用于 AI Agent 能力研究验证。图片版权归原作者/机构所有。

---

## English

> A deep investigation and visualization project independently completed by an AI Agent over an extended time span.

**Data cutoff date**: March 24, 2026. All news citations, polling data, social media captures, and prediction market data are current as of this date. Events after publication are not covered.

**Project duration**: ~24 hours (2026-03-24 00:11 first research file created → 2026-03-24 23:49 final page completed). The Agent completed the full pipeline — from research to visual delivery — in a single day.

### Overview

This report provides a comprehensive deep investigation into J.D. Vance's political career — from childhood trauma in Middletown, Ohio, through Yale Law School, Marine Corps service, Silicon Valley venture capital, the vice presidential campaign, the diplomatic earthquake of the Munich speech, the marginalization during the Iran war, to the power dynamics of the 2028 presidential election. Seven chapters, approximately 400,000 words of research, distilled into an interactive visual web report.

**The entire project — topic planning, research collection, deep investigation, data analysis, structured writing, frontend visual design, and code generation — was completed entirely by the [duoduo](https://github.com/openduo/duoduo) agent with minimal directional guidance from a human editor.** Human intervention was limited to: confirming research directions, providing image download assistance, and suggesting visual style corrections. All text content, data cross-verification, argument construction, and code implementation were produced independently by the Agent.

This project is part of a [Long-Context Agent Research Validation](#project-purpose) effort, testing AI Agent coherence and output quality across long-duration, multi-stage, cross-domain complex tasks.

### Read Online

Visit https://kuaner.github.io/jd-vance-report/ to read the full report (automatically switches between Chinese and English based on browser language, with manual toggle available).

### Project Structure

```
jd-vance-report/
├── index.html                          # Entry: auto language detection redirect
├── ch/                                 # Chinese version
│   ├── index.html                      # Home: Report Overview
│   ├── rust-belt-son.html              # Ch.I: Son of the Rust Belt
│   ├── hillbilly-elegy.html            # Ch.II: Hillbilly Elegy
│   ├── metamorphosis.html              # Ch.III: Metamorphosis
│   ├── silicon-valley-kingmakers.html  # Ch.IV: The Silicon Valley Kingmakers
│   ├── munich-shockwave.html           # Ch.V: The Munich Shockwave
│   ├── iran-trap.html                  # Ch.VI: The Iran Trap
│   └── road-to-the-throne.html         # Ch.VII: Road to the Throne
├── en/                                 # English version
│   ├── index.html                      # Home: Report Overview
│   ├── rust-belt-son.html              # Ch.I: Son of the Rust Belt
│   ├── hillbilly-elegy.html            # Ch.II: Hillbilly Elegy
│   ├── metamorphosis.html              # Ch.III: Metamorphosis
│   ├── silicon-valley-kingmakers.html  # Ch.IV: The Silicon Valley Kingmakers
│   ├── munich-shockwave.html           # Ch.V: The Munich Shockwave
│   ├── iran-trap.html                  # Ch.VI: The Iran Trap
│   └── road-to-the-throne.html         # Ch.VII: Road to the Throne
├── assets/                             # 49 images (~24MB)
├── screenshots/                        # Report screenshots
└── research/                           # Raw research data (not published)
```

### Seven Chapters

| Ch | Title | Core Issue |
|----|-------|------------|
| I | [Son of the Rust Belt](https://kuaner.github.io/jd-vance-report/en/rust-belt-son.html) | Middletown childhood trauma, Marine Corps, Yale Law — the formation of core beliefs |
| II | [Hillbilly Elegy](https://kuaner.github.io/jd-vance-report/en/hillbilly-elegy.html) | Commercial success of a memoir, 3M copies sold, the gap between identity narrative and reality |
| III | [Metamorphosis](https://kuaner.github.io/jd-vance-report/en/metamorphosis.html) | 8 anti-Trump quotes reversed 180°, Streisand effect, social media viral spread |
| IV | [The Silicon Valley Kingmakers](https://kuaner.github.io/jd-vance-report/en/silicon-valley-kingmakers.html) | Thiel/Sacks/Andreessen/Lonsdale power network, $15M investment, social capital conversion |
| V | [The Munich Shockwave](https://kuaner.github.io/jd-vance-report/en/munich-shockwave.html) | MSC 2025 speech paragraph-by-paragraph analysis, transatlantic earthquake, Musk vs Greta effect |
| VI | [The Iran Trap](https://kuaner.github.io/jd-vance-report/en/iran-trap.html) | Five policy domains in full collapse, 41% war support (historic low), Vance vs Rubio power shift |
| VII | [Road to the Throne](https://kuaner.github.io/jd-vance-report/en/road-to-the-throne.html) | Favorability collapse, prediction market shock, Draft Rubio movement, 2028 primary landscape |

### Technical Implementation

- **Pure frontend**: Each HTML file is fully self-contained (inline CSS + JS), no build step, independently accessible and shareable
- **Data visualization**: Chart.js line/bar charts + hand-coded SVG diagrams + CSS data cards, woven into the narrative
- **Dark editorial theme**: oklch() color space, Display serif + geometric sans-serif + CJK type hierarchy
- **Responsive**: 640px breakpoint for mobile
- **Bilingual**: Auto-switches based on browser language, manual toggle supported, preference saved in `localStorage`
- **16 HTML files** (8 Chinese + 8 English), ~800KB; 49 images, ~24MB

### Data Sources

#### Social Media Data Collection (34 JSON datasets, ~2.7MB)

Structured data collection via Reddit and Twitter/X public APIs, covering 17 topic dimensions.

#### News Media & In-Depth Reporting

Research cross-references dozens of media sources including The Atlantic, New York Magazine, New York Times, Washington Post, NPR, CNN, BBC, The Guardian, and more.

#### Polling & Prediction Data

- RealClearPolitics, Rasmussen Reports, Pew Research, DDHQ/The Hill, YouGov, PredictIt/Polymarket, Betfair/Kalshi

#### Image Sources

49 images sourced from Wikimedia Commons, Getty Images, AP, Reuters, official campaign releases, etc. The Agent proactively identified and logged potential image sources during the research phase into `image-assets.md`, then matched and downloaded them during the visualization phase.

### Project Purpose

This project is an **AI Agent Long-Running Capability Validation Experiment**, testing long-range coherence, multi-stage task management, multi-agent coordination, memory lifecycle management, data cross-verification capability, and output quality & iteration ability.

### Tools

- [duoduo](https://github.com/openduo/duoduo) — Autonomous Agent runtime
- [rdt-cli](https://github.com/public-clis/rdt-cli) — Reddit data collection CLI
- [twitter-cli](https://github.com/public-clis/twitter-cli) — Twitter/X data collection CLI
- [Chart.js](https://www.chartjs.org/) — Data visualization

### License

This project's content is for AI Agent capability research validation only. Image rights belong to their respective authors/institutions.
