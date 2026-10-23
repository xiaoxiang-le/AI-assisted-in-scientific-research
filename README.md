# AI 辅助科研工具与 Codex Skills 使用指南

这份指南整理了一组适合科研人员使用的 AI 工具与 Codex Skills，覆盖文献发现、研究问题收敛、系统综述、论文写作、同行评审、文字修订和可度量实验迭代。

它们并不是功能重复的“全能助手”。更可靠的组合方式是：

1. 用 **Undermind、Elicit、Consensus 和传统学术数据库**发现文献；
2. 用 **Connected Papers、ResearchRabbit 和 Litmaps**扩展并可视化论文关系；
3. 用 **Academic Research Skills for Codex（ARS-Codex）**管理研究、筛选、写作和审查流程；
4. 用 **Codex Autoresearch**迭代可由命令量化的代码或实验指标；
5. 用 **Anti-Defensive Writing**完成论文语言的最后一轮校准；
6. 由研究者确认检索范围、纳排标准、关键证据、作者决策和最终结论。

## 工具总览

GitHub Star 为 **2026-10-23 快照**，会随时间变化。“—”表示该工具不是以 GitHub 开源仓库为主要入口。新增 Skill 项目的筛选标准是：仓库公开可访问、提供可复用的 `SKILL.md` 或科研 Agent Skill 集合、能直接服务于文献检索、实验、论文写作、引用核验或同行评审，并具有较高社区关注度或在细分领域有较完整覆盖。

| 工具 | 类型 | Star 快照 | 最适合的任务 | 不应单独承担的任务 | 详细说明 |
|---|---|---:|---|---|---|
| [Scientific Agent Skills](https://github.com/K-Dense-AI/scientific-agent-skills) | Agent Skill 集合 | 54,129 | 177 个科研 Skill，覆盖领域分析、数据库、文献、写作、引用和可视化 | 不经审查一次性安装全部 Skill；替代领域专家核验 | [单独文件](skills/scientific-agent-skills.md) |
| [ARS-Codex](https://github.com/Imbad0202/academic-research-skills-codex) | Codex Plugin / Skill 套件 | 13,393 | 研究问题、综述、筛选、论文写作、引用检查、同行评审、端到端科研流程 | 保证检索库全覆盖，替代领域数据库或研究者判断 | [单独文件](skills/academic-research-skills-codex.md) |
| [Codex Autoresearch](https://github.com/leo-lilinxiao/codex-autoresearch) | Codex Skill | 3,007 | 围绕数值指标自动执行“修改—验证—保留/回退”实验循环 | 无法量化的理论判断、开放式文献综述、不可复现实验 | [单独文件](skills/codex-autoresearch.md) |
| [Claude Scientific Writer](https://github.com/K-Dense-AI/claude-scientific-writer) | 科研写作工具 / Skills | 2,516 | 检索驱动的论文、综述、基金、海报生成，支持 CLI/API | 未经核验直接投稿或补造实验结果 | [单独文件](skills/claude-scientific-writer.md) |
| [Anti-Defensive Writing](https://github.com/Kiterlin/anti-defensive-writing) | Codex Skill | 1,331 | 删除道歉式表达、重复限定和叠加模糊词，增强论文表达 | 文献检索、事实核验、替作者扩大结论 | [单独文件](skills/anti-defensive-writing.md) |
| [Open Scholar Skill](https://github.com/joshzyj/open-scholar-skill) | 学术研究 Skill 集合 | 177 | 社会科学研究、理论与方法、写作、核验、投稿和伦理 | 无条件商业使用；替代作者的理论和因果识别决策 | [单独文件](skills/open-scholar-skill.md) |
| [Research Agent Skills](https://github.com/KalarisLabs/research-agent-skills) | Agent Skill 集合 | 58 | 280+ 个跨学科 Skill，覆盖综述、实验、统计、写作与评审 | 默认安装全部 Skill；跳过依赖、许可和脚本审查 | [单独文件](skills/research-agent-skills.md) |
| [Undermind](https://www.undermind.ai/) | 在线文献研究平台 | — | 复杂自然语言问题、深度文献发现、全文工作区、引用追踪 | 作为系统综述的唯一检索源 | [正文](#4-undermind) |
| [Elicit](https://elicit.com/) | 在线文献研究平台 | — | 语义检索、论文筛选、结构化数据提取、研究报告 | 替代完整数据库检索协议和人工全文核验 | [正文](#5-elicit) |
| [Consensus](https://consensus.app/) | AI 学术搜索平台 | — | 从同行评议研究中检索、综合证据、查看研究快照和证据倾向 | 把聚合答案当作最终结论，跳过原文核验 | [正文](#6-consensus) |
| [Connected Papers](https://www.connectedpapers.com/) | 论文关系可视化 | — | 从一篇种子论文生成相似论文图，寻找先行与后续工作 | 关键词数据库检索或完整引文树 | [正文](#connected-papers) |
| [ResearchRabbit](https://www.researchrabbit.ai/) | 文献发现与关系图谱 | — | 迭代收藏、个性化推荐、论文/作者/主题关系探索 | 可复现数据库检索协议 | [正文](#researchrabbit) |
| [Litmaps](https://www.litmaps.com/) | 引文网络与文献监测 | — | 从种子文献扩展引文网络、制作 Litmap、监测新论文 | 单独证明综述检索完整 | [正文](#litmaps) |

Star 只反映关注度，不等于方法质量、安全性或结果可靠性。安装任何 Skill 前应审查 `SKILL.md`、脚本、网络访问、凭据需求、许可证和第三方声明；进行中的科研项目还应固定 release tag 或 commit SHA。

## 1. Anti-Defensive Writing

项目地址：<https://github.com/Kiterlin/anti-defensive-writing>

### 核心功能

该 Skill 用于修改学术和技术文本的表达方式。它会：

- 删除没有增加信息的免责声明和预防性道歉；
- 把“本文不声称……”改成清楚、正面的研究范围；
- 减少“可能或许在一定程度上”等叠加保留词；
- 保留真实的方法限制、证据边界和伦理限定；
- 让摘要、引言、贡献、讨论和回复信直接呈现论点与证据；
- 客观表达指标权衡，不把单项较弱结果写成整体失败。

它是**语言与论证姿态校准器**，不是“把话写得更夸张”的工具。观察性结果仍应写成相关关系，样本范围、测量误差和因果识别限制仍需保留。

### 在 Codex 中调用

```text
$anti-defensive-writing

请修改论文引言：
1. 删除道歉式开场和重复限定；
2. 用正面范围陈述替代“本文不试图……”；
3. 保留真实的方法限制；
4. 不新增数据、因果关系或贡献；
5. 输出修改稿和关键修改说明。
```

适合放在科研流程的最后阶段：内容、数据和引用确定后，再做语言校准。

## 2. Academic Research Skills for Codex（ARS-Codex）

项目地址：<https://github.com/Imbad0202/academic-research-skills-codex>

ARS-Codex 将多个科研工作流封装为一个 Codex Skill：`academic-research-suite`。安装后新建 Codex 对话，通过 `$academic-research-suite` 调用。

### 六类工作流

| 工作流 | 功能 |
|---|---|
| `deep-research` | 研究问题收敛、文献综述、系统综述、元分析、事实核查 |
| `academic-paper` | 论文计划、大纲、摘要、正文、修订、引用检查、格式转换、AI 使用披露 |
| `academic-paper-reviewer` | 方法学审查、领域审查、模拟同行评审、编辑决定和复审 |
| `academic-pipeline` | 从研究问题到论文定稿的分阶段端到端流程 |
| `sr-screener` | 纳排协议、题目摘要筛选、全文筛选、冲突裁决、排除审计和数量报告 |
| `experiment-agent` | 代码实验、人类参与者研究方案、统计解释和可重复性检查 |

### 在 Codex 中调用

只有宽泛选题时，先收敛研究问题：

```text
使用 $academic-research-suite。

我想研究“生成式 AI 对大学教学质量的影响”，但还没有明确研究问题。
请进入 deep-research 的 socratic 模式，通过提问帮我收敛问题。
现在不要生成大纲或正文。
输出语言：简体中文。
```

已有清晰研究问题时，生成论文架构：

```text
使用 $academic-research-suite：ars-outline。

研究问题：……
已有材料：文献矩阵、方法说明和初步结果。
请生成 IMRaD 大纲，并标出每一节的论点、证据和缺口。
引用格式：APA 7。
停止点：完成大纲后等待我确认。
```

执行引用检查：

```text
使用 $academic-research-suite：ars-citation-check。

检查附件论文的正文引用与参考文献：
- 核验 DOI 或官方元数据；
- 检查正文与参考文献的一致性；
- 区分“已核验”“无法核验”“格式问题”；
- 不得补造文献。
```

模拟同行评审：

```text
使用 $academic-research-suite：ars-reviewer。

对附件论文执行完整评审，重点检查方法、贡献、统计解释、引用完整性和拒稿风险。
只审查，不修改原稿。
```

### 常用别名

Codex 客户端可能拦截斜杠命令，因此优先使用不带 `/` 的普通别名：

- `ars-plan`：论文计划；
- `ars-outline`：论文大纲；
- `ars-abstract`：摘要；
- `ars-lit-review`：文献综述；
- `ars-citation-check`：引用核查；
- `ars-revision-coach`：修改路线图；
- `ars-revision`：按确认路线图修改；
- `ars-reviewer`：同行评审；
- `ars-full`：端到端科研流程。

## 3. Codex Autoresearch

项目地址：<https://github.com/leo-lilinxiao/codex-autoresearch>

### 核心功能

Codex Autoresearch 用于**可测量、可复现、可回退**的自主实验。基本循环是：

```text
检查证据 → 修改一个聚焦点 → 运行验证 → 指标改善则保留，否则回退 → 继续迭代
```

适合的目标包括：

- 降低测试失败数、类型错误或警告数；
- 提升测试覆盖率；
- 降低延迟、内存占用或二进制体积；
- 优化模型误差、损失函数或其他可重复计算的指标；
- 修复可由命令稳定复现的安全问题。

每次运行都应有一个数值指标、一个明确目标、允许修改的路径和可选的回归保护命令。Skill 使用 Git 提交保存每次试验，并回退没有改善或破坏保护条件的修改。

### 在 Codex 中调用

```text
$codex-autoresearch

目标：把 `python scripts/evaluate.py` 最后一行 JSON 中的 `rmse` 从当前值降到 0.15 以下。
允许修改：src/model.py、configs/experiment.yaml。
验证命令：python scripts/evaluate.py。
指标解析：JSON 键 rmse，越低越好。
回归保护：python -m pytest tests。
最多迭代：20。
运行方式：前台。
```

使用前应满足：

- 仓库处于干净、具名的 Git 分支；
- 指标命令可重复运行并输出有限数值；
- 允许修改的路径范围明确；
- 指标未覆盖的重要行为由 guard 命令保护；
- 不把主观论文质量当作伪数值指标。

## 4. Undermind

官方网址：<https://www.undermind.ai/>

Undermind 面向复杂研究问题进行深度文献发现，适合：

- 用自然语言描述细分、跨学科或难以构造关键词的研究问题；
- 从大量候选论文中寻找高相关度文献；
- 在工作区中管理开放获取 PDF 和自行上传的全文；
- 沿引用定位论述依据；
- 对全文、图表和证据进行进一步阅读。

推荐把 Undermind 用作**高召回候选发现通道**，将导出的 DOI、标题、作者和年份合并进主文献表，再进行去重和数据库核验。

示例查询：

```text
寻找研究“生成式 AI 反馈如何影响大学生写作自我效能”的实证论文。
优先纳入具有对照组、纵向设计或明确测量工具的研究；同时寻找相反或无效结果。
```

## 5. Elicit

官方网址：<https://elicit.com/>

Elicit 适合把自然语言研究问题转换为语义检索，并对候选论文执行结构化处理：

- 语义检索和相关性排序；
- 通过筛选问题缩小结果；
- 从论文中提取样本、方法、干预、结局和结果；
- 建立可导出的证据表；
- 生成带来源定位的研究报告；
- 辅助系统综述的筛选和数据提取。

示例工作流：

1. 输入明确的研究问题；
2. 检查 Elicit 推荐的研究问题细化建议；
3. 设置年份、研究类型和人群等筛选条件；
4. 创建结构化字段，如样本量、设计、干预、效应方向和局限；
5. 导出结果并与其他数据库结果合并；
6. 回到原文核验关键数据和引用上下文。

## 6. Consensus

官方网址：<https://consensus.app/>

Consensus 是面向学术研究的 AI 搜索和证据综合平台。它适合用自然语言提出可由研究证据回答的问题，并将相关论文、引用和结构化研究信息组织到同一界面中。

### 主要功能

- 搜索同行评议论文并生成带引用的综合回答；
- 使用高级过滤器限定年份、研究类型、领域等条件；
- 查看 Study Snapshot，快速识别样本、方法、研究设计和结果；
- 对选定论文或上传的全文继续提问；
- 使用 Consensus Meter 了解研究结果的总体倾向；
- 保存检索和论文，导出到 Zotero、EndNote、Paperpile 等工具；
- 使用 Citation Graph 从结果继续探索论文关系。

### 使用方法

1. 把宽泛主题改写成明确问题，例如“X 是否改善 Y？”或“X 与 Y 的关系在 Z 人群中如何？”；
2. 查看检索结果中的研究类型、样本和年份，不只阅读 AI 摘要；
3. 使用过滤条件建立多个查询版本，记录查询文本和运行日期；
4. 对支持、反对和无显著结果的论文分别抽样核验；
5. 导出 DOI、题名和元数据，与 Undermind、Elicit 和数据库结果合并去重；
6. 打开原文核对效应方向、统计条件、研究设计和限制。

Consensus 的聚合结果适合快速判断证据地形，但 Consensus Meter 不是元分析结果，也不能替代风险偏倚评价。

## 7. 论文关系可视化工具

这三类工具从论文之间的引用或相似性关系出发，可以发现关键词检索没有命中的邻近工作。它们最适合接在 Undermind、Elicit、Consensus 或数据库检索之后。

### Connected Papers

官方网址：<https://www.connectedpapers.com/>

Connected Papers 以一篇种子论文为起点生成论文相似性图。节点距离反映相似程度，其关系主要基于共被引和文献耦合；即使两篇论文没有直接互引，也可能在图上靠近。因此它展示的是相似论文空间，不是传统的直接引文树。

使用步骤：

1. 输入一篇高相关度种子论文的题名、DOI 或链接；
2. 检查图中的聚类、年份和高连接节点；
3. 查看 Prior Works，寻找领域基础工作；
4. 查看 Derivative Works，寻找后续发展；
5. 更换不同年代、方法或观点的种子论文重复建图；
6. 将候选论文导回主文献表并核验 DOI 和原文。

### ResearchRabbit

官方网址：<https://www.researchrabbit.ai/>

ResearchRabbit 通过收藏和持续探索建立个性化文献发现流程，可以可视化论文、作者和主题之间的联系。随着收藏内容增加，推荐会根据探索行为调整，适合长期维护一个研究方向的阅读网络。

使用步骤：

1. 建立与项目或子问题对应的 collection；
2. 加入数篇代表不同方法和观点的种子论文；
3. 查看相似论文、参考文献、被引论文和作者网络；
4. 把相关论文加入 collection，让推荐逐步聚焦；
5. 为不同子主题建立独立 collection，避免推荐被单一主题主导；
6. 定期导出或同步文献管理工具，并回到原文核验。

### Litmaps

官方网址：<https://www.litmaps.com/>

Litmaps 使用引用与参考文献网络发现和展示论文关系。它可以从一篇或多篇种子文献扩展 Litmap，支持标注、过滤、共享、Zotero 同步和新论文监测，适合持续更新的文献综述。

使用步骤：

1. 搜索并添加一篇或多篇种子论文；
2. 选择 Explore Related Articles 扩展相关工作；
3. 用时间、引用关系和自定义标签观察研究脉络；
4. 保存相关论文并标记纳入状态或主题；
5. 对关键节点继续扩图，直到新增结果趋于稳定；
6. 开启监测，在新论文进入相关引文网络时接收更新；
7. 将地图或文献清单用于团队沟通，不把图上距离解释成证据强度。

### 与 Undermind 的组合方式

推荐的闭环是：

```text
Undermind 深度语义检索
        ↓
选出 3–10 篇高相关种子论文
        ↓
Connected Papers：快速观察相似论文簇与先行/后续工作
ResearchRabbit：按子主题持续收藏、推荐和作者网络探索
Litmaps：建立可维护的引文地图并监测新论文
        ↓
合并 DOI/题名 → 去重 → 数据库核验 → 人工筛选
```

种子论文会影响关系图的覆盖范围。至少选择不同年份、不同方法和不同结论的多篇种子文献，并将图谱结果与关键词数据库检索交叉比较。

## 8. 已安装 Codex 插件：功能、使用与配置

以下清单来自本机 Codex 配置中当前启用的插件。通常应在 Codex Desktop 的 Plugins 设置中启用、停用或更新插件；`~/.codex/config.toml` 中对应条目的 `enabled = true` 表示已启用。修改插件状态后，新建对话可避免旧会话继续使用缓存能力。

### 科研内容与文件插件

| 插件 | 可以实现什么 | 在 Codex 中怎么用 | 关键配置 |
|---|---|---|---|
| **ARS-Codex** | 研究问题、综述、筛选、论文写作、同行评审、实验规划 | `使用 $academic-research-suite：ars-outline ...` | 安装 marketplace 后启用 `ars-codex@ars-codex`；更新后新建对话 |
| **Documents** | 创建、读取、修改、检查和导出 DOCX 文档 | “把这些研究笔记整理为一份 Word 研究报告，并检查标题层级和参考文献页” | 指定输入文件、输出路径、语言、样式和是否允许覆盖 |
| **PDF** | 读取、提取、创建、渲染和验证 PDF | “提取这些 PDF 的方法与结果表，并逐页标注来源” | 扫描版先确认 OCR；涉及页码引用时验证页面结构和渲染结果 |
| **Spreadsheets** | 创建、分析和导出 XLSX/CSV/TSV，制作表格和图表 | “把检索结果 CSV 去重，建立筛选状态、排除理由和 DOI 核验列” | 指定工作表、主键、列类型、公式和输出文件；编辑已打开 Excel 时需连接 Excel Live Control |
| **Presentations** | 创建、修改、渲染和导出 PPTX/演示文稿 | “根据论文生成 12 页组会汇报，包含研究问题、方法、结果和局限” | 指定页数、受众、比例、模板、视觉风格和讲者备注 |
| **Template Creator** | 将已有文档、表格、幻灯片或图像转成可复用模板 | “以这份组会 PPT 为参考，创建保持版式和色彩的可复用模板” | 提供明确参考文件；说明哪些结构固定、哪些字段每次替换 |
| **Visualize** | 创建交互式图表、关系图、地图、数据探索器和模拟 | “把文献矩阵做成按年份、主题和方法筛选的交互式证据图” | 提供结构化数据和字段含义；指定筛选器、编码方式和需要突出的关系 |

### 浏览器、桌面与协作插件

| 插件 | 可以实现什么 | 在 Codex 中怎么用 | 关键配置 |
|---|---|---|---|
| **Browser** | 控制 Codex 内置浏览器，打开、点击、输入和截图 | “用内置 Browser 打开本地文献仪表板并测试筛选功能” | 主要用于本地页面或明确网页；需要交互时保持浏览器标签可用 |
| **Chrome** | 使用现有 Chrome 标签、登录状态、Cookie 和扩展 | “在我已登录的 Chrome 中打开 Elicit，导出当前项目结果” | 在设置中授权 Chrome；登录态可能包含敏感信息，限定目标网站和操作范围 |
| **Computer Use** | 操作 Windows 桌面应用 | “在 Zotero 中导入这个 RIS 文件，并新建指定 collection” | 允许目标应用访问；高风险提交、购买、发送或删除动作仍需明确确认 |
| **Unified Computer Use** | 为浏览器自动化提供统一运行时 | 通常由 Browser、Chrome 或 Computer Use 间接调用 | 一般无需单独提示或配置；负责底层自动化会话 |
| **Code Review** | 查看和管理 GitHub Pull Request、diff、检查与评论 | “审查这个 PR，按严重程度列出可操作问题” | 需要 GitHub 账户连接与仓库权限；合并或发表评论属于外部写操作 |
| **Codex App Tools** | 管理 Codex 对话、工作树、文件标签、自动化和应用状态 | “打开刚生成的报告”“把这个任务归档”“等待另一个任务完成” | 属于 Codex Desktop 基础能力，通常不单独调用或配置 |

### 推荐的科研插件组合

| 场景 | 推荐组合 |
|---|---|
| 文献检索与关系扩展 | Chrome/Computer Use + Undermind/Elicit/Consensus + Connected Papers/ResearchRabbit/Litmaps |
| 系统综述筛选 | ARS-Codex + Spreadsheets + PDF + Documents |
| 论文证据图 | Spreadsheets + Visualize + Documents |
| 组会或答辩 | Documents/PDF + Presentations + Template Creator |
| 代码实验与论文 | Codex Autoresearch + ARS-Codex + Spreadsheets + Visualize |
| GitHub 协作 | Code Review + Codex App Tools |

### 配置时应注意

- **最小权限**：浏览器和桌面插件只授权当前任务需要的网站、应用和文件；
- **文件边界**：明确输入、输出和是否覆盖，重要原稿保留副本；
- **登录状态**：Chrome 可访问现有登录状态，使用前说明目标网站和允许的动作；
- **外部上传**：未公开稿件、受限全文或敏感数据进入 Elicit、Undermind、Consensus 等服务前，检查机构政策和服务条款；
- **新对话加载**：新安装、更新或启用 Skill/插件后，新建 Codex 对话；
- **任务提示**：优先描述最终产物和约束，Codex 会根据文件类型自动选择 Documents、PDF、Spreadsheets 或 Presentations。

## 文献检索不全与漏掉论文的风险

任何单一 AI 搜索工具都可能漏掉论文。原因包括索引范围、更新时间、语义排序、语言覆盖、付费全文、会议论文与预印本收录差异，以及查询表达造成的偏差。AI 工具返回的“高度相关”结果不是“检索已完整”的证明。

### 推荐的多通道检索策略

正式综述至少组合以下通道：

1. **领域数据库**：按学科使用 Web of Science、Scopus、PubMed/MEDLINE、Embase、IEEE Xplore、ACM Digital Library、PsycINFO、ERIC、CNKI 等；
2. **语义发现**：Undermind、Elicit、Consensus、Semantic Scholar 等；
3. **关系图谱与引文追溯**：Connected Papers、ResearchRabbit、Litmaps，以及核心论文的参考文献和“被引用”记录；
4. **作者与团队追踪**：检索关键作者、实验室、项目和试验注册；
5. **灰色文献**：预印本、学位论文、会议论文、机构报告和临床试验注册；
6. **更新检索**：在投稿或定稿前重新运行检索，并记录最后检索日期。

### 在 Codex 中要求可审计检索

```text
使用 $academic-research-suite 设计文献检索方案。

要求：
1. 分开记录数据库检索、Undermind、Elicit、Consensus 和关系图谱/引文追溯结果；
2. 为每个数据库保存检索式、筛选条件、运行日期和命中数；
3. 合并后按 DOI、PMID、标题和作者年份去重；
4. 建立“已找到来源—发现通道”矩阵；
5. 对关键综述执行前向和后向引文追溯；
6. 不得把 AI 排名靠后等同于不相关；
7. 输出尚未覆盖的数据库、语言、年份和文献类型。
```

系统综述还应预先确定检索协议、纳排标准和人工质控规则。AI 可以提高速度，但最终纳排决定、全文判断和证据解释仍由研究团队负责。

## 推荐的组合科研流程

### 阶段 A：问题形成

- 使用 ARS-Codex 的 `deep-research/socratic` 收敛研究问题；
- 明确 PICO、SPIDER、PICo 或适合本领域的结构；
- 预先定义研究范围、时间范围、语言和文献类型。

### 阶段 B：文献发现

- 在领域数据库执行可复现关键词检索；
- 用 Undermind 发现复杂语义相关论文；
- 用 Elicit 补充语义检索和结构化提取；
- 用 Consensus 快速检查同行评议证据倾向并发现补充论文；
- 用 Connected Papers、ResearchRabbit 和 Litmaps 梳理论文关系；
- 对核心论文执行前向、后向引文追溯。

### 阶段 C：筛选与证据表

- 合并结果并去重；
- 使用 ARS-Codex `sr-screener protocol` 确认筛选协议；
- 先进行人工标注的 pilot，再决定是否扩大 AI 辅助筛选；
- 保留排除理由、冲突裁决和抽样复核记录。

### 阶段 D：实验与分析

- 使用 ARS-Codex `experiment-agent` 设计实验和可重复性检查；
- 对可命令化的代码指标使用 Codex Autoresearch；
- 固定数据版本、随机种子、环境和评价脚本；
- 保存失败结果和没有改善的假设。

### 阶段 E：写作与审查

- 使用 ARS-Codex 生成大纲、正文、摘要和引用检查；
- 使用 `ars-reviewer` 模拟方法与领域评审；
- 由作者确认修改路线图后再执行 revision；
- 最后使用 Anti-Defensive Writing 校准表达；
- 投稿前人工复核每条关键引用、数字、图表和结论。

## 在 Codex Agent 中配置协作规则

可以把本仓库的 [`AGENTS.example.md`](AGENTS.example.md) 复制到科研项目根目录并改名为 `AGENTS.md`。该文件会告诉 Codex：

- 哪类任务调用哪个 Skill；
- 文献检索必须使用多通道策略；
- 如何区分发现、核验、筛选与写作；
- 哪些决定必须由研究者确认；
- 如何防止编造引用、扩大结论和覆盖用户文件。

## 一个完整的 Codex 提示词模板

```text
使用 $academic-research-suite 管理本次任务，并在最终语言修订时使用
$anti-defensive-writing。

研究问题：
当前阶段：
已有材料：
尚缺材料：
目标数据库与外部检索工具：
引用格式：
输出语言：简体中文/英文
本次交付物：
停止点：

检索要求：分别记录数据库、Undermind、Elicit、Consensus、关系图谱和引文追溯结果；
不得声称检索完整；列出仍未覆盖的来源与风险。

写作要求：不得编造引用、数据或因果关系；保留真实方法限制；
删除不必要的防御性表达。
```

## 使用原则

- AI 负责加速检索、整理、检查和生成候选方案，研究者负责学术判断与责任；
- 每一条关键事实都应回到原始论文或权威元数据核验；
- 发现工具的排名用于排序工作量，不用于替代纳排标准；
- 检索、筛选、提取、综合和写作应保留可审计记录；
- 私有稿件、未公开数据和受限全文上传到外部服务前，应确认机构政策、数据授权和服务条款；
- 工具功能和索引范围会变化，实际使用前查看各项目与产品的最新官方说明。

