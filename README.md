# JD Vance 深度调查报告

> 一个由 AI Agent 在超长时间跨度下独立完成的深度调研与可视化项目。

**数据截止日期**：2026 年 3 月 24 日。所有新闻引用、民调数据、社交媒体采集和预测市场数据均截至该日期，报告发布后的事件不在覆盖范围内。

## 项目概述

本报告对 J.D. Vance 的政治生涯进行了全景式深度调查，从俄亥俄州 Middletown 的童年创伤，到耶鲁法学院、海军陆战队服役、硅谷风投圈、副总统竞选、慕尼黑演讲引发的外交地震、伊朗战争中被边缘化的困境，直至 2028 总统大选的权力博弈——七个章节，约 40 万字的调研文字，浓缩为一份交互式的可视化网页报告。

**整个项目——选题策划、资料搜集、深度调研、数据分析、结构化写作、前端可视化设计、代码生成——全部由 [duoduo](https://github.com/openduo/duoduo) agent 在人类编辑的极少量方向性指导下完成。** 人类角色的介入仅限于：确认调研方向、提供图片下载辅助、对可视化风格提出修正意见。文字内容、数据交叉验证、论点构建、代码实现均由 Agent 独立产出。

本项目是 [Long-Context Agent 研究验证](#项目目的)的一部分，旨在测试 AI Agent 在长时间、多阶段、跨领域复杂任务中的连贯性和产出质量。

## 在线阅读

访问 https://kuaner.github.io/jd-vance-report/ 阅读完整报告。

## 项目结构

```
jd-vance-report/
├── index.html                          # 首页：报告导览
├── rust-belt-son.html                  # 第一章：铁锈带之子
├── hillbilly-elegy.html                # 第二章：乡下人的悲歌
├── metamorphosis.html                  # 第三章：蜕变
├── silicon-valley-kingmakers.html      # 第四章：硅谷造王者
├── munich-shockwave.html               # 第五章：慕尼黑震动
├── iran-trap.html                      # 第六章：伊朗困境
├── road-to-the-throne.html             # 第七章：王座之路
├── assets/                             # 49 张配图（~24MB）
│   ├── vance-*.jpg                     # Vance 肖像与活动照片
│   ├── thiel-*.jpg                     # Peter Thiel 肖像
│   ├── sacks-*.jpg                     # David Sacks 肖像
│   ├── andreessen-02.jpg               # Marc Andreessen 肖像
│   ├── lonsdale-02.jpg                 # Joe Lonsdale 肖像
│   ├── musk-04.jpg                     # Elon Musk 肖像
│   ├── hillbilly-elegy-*.jpg/png       # 书籍封面与 Netflix 海报
│   ├── munich-*.jpg/png                # 慕尼黑安全会议现场
│   ├── iran-war-*.jpg                  # 伊朗战争相关
│   ├── mar-a-lago-*.jpg                # Mar-a-Lago 战情室
│   ├── vpdebate-*.jpg                  # 副总统辩论
│   └── ...
└── research/                           # 调研原始数据（不发布）
    ├── topics/
    │   ├── topic-1.md ~ topic-7.md    # 7 章完整调研文稿（~205KB）
    │   └── prep-*.md                  # 各专题预备数据
    ├── biography-family.md             # 传记与家庭背景
    ├── silicon-valley-network.md       # 硅谷关系网络
    ├── diplomacy-speeches.md           # 外交演讲与政策
    ├── polling-data.md                 # 民调数据汇编
    ├── quotes-and-speeches.md          # 言论与演讲原文
    ├── competitors-2028.md             # 2028 竞争对手分析
    ├── image-assets.md                 # 图片来源索引
    ├── reddit-*.json (17 files)        # Reddit 数据采集
    ├── twitter-*.json (17 files)       # Twitter/X 数据采集
    └── social-tw-munich.json           # 慕尼黑演讲社媒数据
```

## 七章内容

| 章 | 标题 | 核心议题 |
|----|------|---------|
| I | [铁锈带之子](https://kuaner.github.io/jd-vance-report/rust-belt-son.html) | Middletown 童年创伤、海军陆战队、耶鲁法学院——信念内核的形成 |
| II | [乡下人的悲歌](https://kuaner.github.io/jd-vance-report/hillbilly-elegy.html) | 回忆录的商业化成功、300 万册销量、身份叙事与真实之间的裂缝 |
| III | [蜕变](https://kuaner.github.io/jd-vance-report/metamorphosis.html) | 8 条反 Trump 原话的 180 度翻转、Streisand 效应、社交媒体病毒传播 |
| IV | [硅谷造王者](https://kuaner.github.io/jd-vance-report/silicon-valley-kingmakers.html) | Thiel/Sacks/Andreessen/Lonsdale 权力网络、$15M 投资、社交资本变现 |
| V | [慕尼黑震动](https://kuaner.github.io/jd-vance-report/munich-shockwave.html) | MSC 2025 演讲全文逐段分析、欧洲跨大西洋地震、Musk vs Greta 效应 |
| VI | [伊朗困境](https://kuaner.github.io/jd-vance-report/iran-trap.html) | 五大政策领域全面溃败、41% 战争支持率（历史最低）、Vance vs Rubio 权力消长 |
| VII | [王座之路](https://kuaner.github.io/jd-vance-report/road-to-the-throne.html) | 好感度崩塌、预测市场冲击、Draft Rubio 运动、2028 初选格局 |

## 技术实现

- **纯前端**：每个 HTML 文件完全自包含（CSS + JS 内联），无构建步骤，可独立访问和分享
- **数据可视化**：Chart.js 折线图/柱状图 + 手工编码 SVG 图表 + CSS 数据卡，融入叙事流
- **深色编辑主题**：oklch() 色彩空间、Display serif + 几何无衬线 + 中文黑体的字体层级
- **响应式**：640px 断点适配移动端
- **中英双语引用**：所有英文原文引用均附中文翻译
- **总计 8 个 HTML 文件**，约 400KB；49 张配图，约 24MB

## 数据来源

### 社交媒体数据采集（34 个 JSON 数据集，约 2.7MB）

通过 Reddit 和 Twitter/X 公开 API 进行结构化数据采集，覆盖 17 个主题维度：

**Reddit 数据（17 个数据集）**

| 数据集 | 子版块 | 数据内容 |
|--------|--------|---------|
| `reddit-hillbilly.json` | r/HillbillyElegy, r/Books | 《乡下人的悲歌》读者评价与讨论 |
| `reddit-nevertrump.json` | r/NeverTrump, r/politics | Never Trump 运动与 Vance 立场转变 |
| `reddit-catladies.json` | r/PoliticalDiscussion 等 | "Cat ladies" 争议事件 |
| `reddit-vpdebate.json` | r/politics, r/C_S_P | 副总统辩论讨论 |
| `reddit-2028.json` | r/politics, r/Republican | 2028 总统大选前瞻 |
| `reddit-rubio-2028.json` | r/politics | Rubio vs Vance 2028 对比 |
| `reddit-rubio-vance.json` | r/politics | Rubio 与 Vance 关系动态 |
| `reddit-munich.json` | r/europe, r/worldnews | 慕尼黑演讲国际反应 |
| `reddit-iran.json` | r/worldnews, r/iran | 伊朗战争舆论 |
| `reddit-2028.json` | r/Republican, r/Conservative | GOP 基层选情 |
| `reddit-silicon-valley.json` | r/technology, r/SiliconValley | Vance 与科技行业关系 |
| `reddit-silicon.json` | r/SiliconValley, r/tech | 硅谷政治参与 |
| `reddit-a16z.json` | r/a16z, r/vc | 风投圈与 Vance 关系 |
| `reddit-tech-network.json` | r/technology | 科技精英网络分析 |
| `reddit-thiel.json` | r/technology, r/politics | Peter Thiel 政治影响 |
| `reddit-politics-thiel.json` | r/politics | Thiel 政治活动讨论 |
| `reddit-musk.json` | r/technology, r/EnoughMuskSpam | Musk 政治转向讨论 |

**Twitter/X 数据（17 个数据集）**

| 数据集 | 关注维度 |
|--------|---------|
| `twitter-jdvance-latest.json` | Vance 近期言论与互动 |
| `twitter-nevertrump.json` | 2016 年反 Trump 推文存档 |
| `twitter-hillbilly.json` | 《乡下人的悲歌》相关讨论 |
| `twitter-catladies.json` | "Cat ladies" 争议 |
| `twitter-vpdebate.json` | 副总统辩论反应 |
| `twitter-munich.json` | 慕尼黑演讲传播 |
| `twitter-iran.json` | 伊朗战争舆论 |
| `twitter-2028.json` | 2028 大选讨论 |
| `twitter-rubio-2028.json` | Rubio 2028 动态 |
| `twitter-rubio-vance.json` | Rubio vs Vance 对比 |
| `twitter-thiel.json` | Thiel 政治活动 |
| `twitter-sacks.json` | David Sacks 推文 |
| `twitter-andreessen.json` | Marc Andreessen 推文 |
| `twitter-lonsdale.json` | Joe Lonsdale 推文 |
| `twitter-musk.json` | Musk 政治推文 |
| `twitter-silicon.json` | 硅谷科技圈政治 |
| `social-tw-munich.json` | 慕尼黑演讲社媒热度 |

### 新闻媒体与深度报道

调研文字交叉引用了以下新闻来源的报道（部分）：

**美国主流媒体**
- The Atlantic — Vance 被边缘化专题报道
- New York Magazine / Intelligencer — 外交政策分析、2028 前瞻
- New York Times — 专栏报道、政治分析
- Washington Post — Musk-Trump-Vance 三角关系
- NPR — 采访与报道
- CNN、CBS News、NBC News — 辩论、竞选报道
- Fox News — Vance 采访
- Time — 政治领袖评价
- The Hill — "DeMinished" DeSantis 分析
- Slate — 2016 年 Vance 言论存档
- ABC News — "Draft Rubio" 运动报道

**国际媒体**
- The Guardian (UK) — 慕尼黑演讲报道
- BBC — 慕尼黑安全会议报道
- Rossiya 1 (俄罗斯) — 欧洲反应

### 民调与预测数据

- **RealClearPolitics (RCP)** — 好感度综合平均、初选民调
- **Rasmussen Reports** — 好感度追踪
- **Pew Research Center** — 人口统计好感度
- **Decision Desk HQ (DDHQ) / The Hill** — 好感度趋势
- **YouGov** — 国际视角好感度
- **PredictIt / Polymarket** — 2028 共和党提名预测市场
- **Betfair / Kalshi** — 大选 matchup 赔率

### 官方与公共领域资料

- **MSC 官方** — 慕尼黑安全会议演讲全文 PDF 及官方视频
- **Wikimedia Commons** — 官方肖像、公共领域照片
- **C-SPAN** — 国会听证与演讲记录
- **联邦选举委员会 (FEC)** — 竞选财务数据

### 图片来源

49 张配图**并非后期单独搜集，而是在调研检索阶段就被 Agent 刻意保留的**。Agent 在浏览新闻网页、Wikimedia Commons、Reddit 帖子等来源收集资料时，同步将发现的配图候选（URL、描述、版权信息）记录到 `image-assets.md` 日志中，按章节和主题分类索引（共 13 个类别、64+ 条来源记录）。当调研稿撰写完成并标注 `[VIS:]` 配图需求后，Agent 直接从已有的图片日志中匹配、筛选和下载，而非重新搜索。

完整工作流：

1. **资料检索阶段**：Agent 在调研过程中浏览新闻页面、Wikimedia、社交媒体时，主动识别和记录潜在的配图来源，写入 `image-assets.md`（含 URL、描述、版权状态）
2. **需求标注**：调研稿撰写时通过 `[VIS:]` 标记指定每章配图需求（场景、人物、事件）
3. **匹配下载**：Agent 从图片日志中匹配需求，通过 wikimedia-image-fetch skill 解析 Wikimedia 页面、curl 批量下载到 `assets/` 目录，记录到 `image-download-log.md`（含文件名、URL、描述、大小）
4. **去重校验**：可视化阶段 Agent 对比图片实际内容（而非文件名）识别重复，例如发现 `munich-03.jpg` 与 `munich-msc-og.jpg` 为同一场景后自动移除

图片来源包括：
- **Wikimedia Commons** — 官方肖像、公共领域照片、MSC 官方 CC BY-SA 授权
- **Getty Images / AP / Reuters** — 新闻现场摄影（VP 辩论、RNC 大会等）
- **官方竞选与政府发布** — White House、MSC 官方
- **社交媒体公开截图** — 注明来源

部分外部新闻网站图片因版权限制无法直接下载，Agent 采用 CSS 占位符或替代图片处理，人类辅助提供了 6 张关键图片的直接下载链接。

## 项目目的

本项目是一个 **AI Agent Long-Running 能力验证实验**，核心验证问题包括：

### 1. 长程连贯性

Agent 能否在跨越多个会话（context window 多次刷新）的情况下，保持调研方向的一致性和论点的内在逻辑性？

- 项目从选题到最终交付跨越了数十个会话周期，每次 context 刷新后 Agent 通过文件系统重新加载上下文
- 7 章调研文字（~205KB）和 8 个 HTML 页面（~400KB）之间保持了事实一致、叙事连贯、无内部矛盾
- 章节间的交叉引用（如第三章引用第一章的童年创伤、第六章回溯第四章的硅谷关系网络）均准确无误

### 2. 多阶段任务管理

从选题→资料搜集→深度调研→结构化写作→可视化设计→代码生成，Agent 能否自主推进并管理阶段间的依赖关系？

- Agent 自主规划了三阶段工作流，并为每个阶段建立了检查点和依赖关系
- 调研阶段 Agent 确定了 7 章结构，每章约 25-36KB 的深度调研文字
- 可视化阶段 Agent 将 205KB 的文字转化为 8 个自包含的 HTML 页面，包含 Chart.js 图表、SVG 图解和 49 张配图
- 阶段间的衔接——如图片资产分配、`[VIS:]` 标记解析、数据提取——均由 Agent 自动完成

### 3. 多 Agent 协同

duoduo 的 dual-loop 认知模型（Cortex 前台会话 + Subconscious 后台分区）和 subagent 编排能力如何支撑复杂项目？

- 前台 Agent 负责交互式决策和代码实现，后台 subconscious 分区在空闲时自动整合记忆、反思会话、维护知识广播板
- 专用 subagent 被用于并行化的独立子任务：Reddit 数据采集、Twitter 数据采集、图片搜索与下载、代码探索
- subagent 之间通过文件系统传递中间产物（JSON 数据集、markdown 调研稿），而非依赖共享内存
- 关键观察：subagent 的输出质量高度依赖 prompt 的精确度——模糊的指令会导致数据格式不一致或采集范围偏移

### 4. Memory 生命周期管理

Agent 的持久化记忆系统在长期项目中是否真正有效？

duoduo 采用 filesystem-first 架构，所有状态——对话历史、产出物、目标追踪、记忆——都以文件形式持久化。本项目验证了以下 memory 机制：

- **文件系统作为数据库**：调研稿（`topic-*.md`）、数据集（`reddit-*.json`）、配图索引（`image-assets.md`）全部作为文件存储，Agent 在每次会话恢复时通过文件读取重建上下文，而非依赖 in-memory 状态
- **目标追踪（Goals）**：通过 `.duoduo/goals/active/` 目录管理进行中的目标状态，Agent 在会话开始时自动检查并在进展时更新，实现了跨会话的任务持久化
- **记忆系统（Memory）**：Agent 将跨会话的上下文写入 `~/.claude/projects/.../memory/` 目录，包括用户偏好（feedback 类型）、项目状态（project 类型）和参考资料（reference 类型）。本项目验证了记忆的写入→检索→更新的完整生命周期
- **Event Sourced 恢复**：duoduo 的 WAL（Write-Ahead Log）机制确保进程崩溃后可从事件日志精确恢复执行状态。本项目期间经历了多次自然中断，每次恢复后 Agent 均能从断点继续而非从头开始
- **关键问题**：记忆的衰减和陈旧——Agent 在后期会话中偶尔引用早期会话中已被修正的结论，说明 memory 的时效性管理仍需改进

### 5. 数据交叉验证能力

Agent 能否从 34 个社交媒体数据集、数十个新闻来源和多家民调机构中提取信息，进行有效的交叉验证而非简单汇总？

- Agent 自主发起了 34 次 rdt-cli 和 twitter-cli 的结构化数据采集，覆盖 17 个主题维度
- 民调数据从 6 家独立机构（RCP、Rasmussen、Pew、DDHQ、YouGov、PredictIt）交叉比对
- 新闻来源覆盖美国主流媒体、国际媒体和官方渠道，Agent 在引用时标注了出处和矛盾点

### 6. 输出质量与迭代能力

在极少量人类干预的条件下，Agent 产出的调研报告是否达到专业标准？能否根据反馈准确修正？

- 人类反馈示例：`"这个表格太丑了"` → Agent 理解为 UI 组件需要重新设计，将 grid 表格重构为 card 布局
- 人类反馈示例：`"不要强行猜测英文原文"` → Agent 立即停止在 topic 源文件中不存在的英文引用上添加翻译，并建立了"仅在源文件有原文时才翻译"的规则
- 人类反馈示例：`"ch5 有重复图片"` → Agent 对比了所有图片的实际内容（而非文件名），识别并移除了 3 组重复图片

## 许可

本项目内容仅用于 AI Agent 能力研究验证。图片版权归原作者/机构所有。

## 工具

- [duoduo](https://github.com/openduo/duoduo) — 自主 Agent 运行时（基于 Claude，filesystem-first + event-sourced + dual-loop 认知模型）
- [rdt-cli](https://github.com/public-clis/rdt-cli) — Reddit 数据采集 CLI（浏览 feed、搜索帖子、读取评论、投票等）
- [twitter-cli](https://github.com/public-clis/twitter-cli) — Twitter/X 数据采集 CLI
- [Chart.js](https://www.chartjs.org/) — 数据可视化
