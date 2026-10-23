# Academic Research Skills for Codex（ARS-Codex）

- 项目：<https://github.com/Imbad0202/academic-research-skills-codex>
- GitHub Star：13,393（快照日期：2026-10-23；Star 会持续变化）
- 许可证：仓库包含自定义许可与上游材料，使用和再分发前应检查当前 LICENSE、manifest 与各组件声明
- 形态：Codex 原生 Plugin / `academic-research-suite` Skill 套件
- 主要定位：人机协作的完整学术研究、论文写作和审查流程

## 六类工作流

| 工作流 | 主要任务 |
|---|---|
| `deep-research` | 研究问题收敛、文献综述、系统综述、元分析、事实核查 |
| `academic-paper` | 论文计划、大纲、摘要、正文、修订、引用检查、格式转换、AI 使用披露 |
| `academic-paper-reviewer` | 方法学和领域审查、模拟同行评审、编辑决定、复审 |
| `academic-pipeline` | 从研究问题到定稿的分阶段端到端流程 |
| `sr-screener` | 纳排协议、题目摘要与全文筛选、冲突裁决、排除审计、数量报告 |
| `experiment-agent` | 代码实验、人类参与者研究方案、统计解释、可重复性检查 |

## 在 Codex 中调用

宽泛选题应先收敛研究问题：

```text
使用 $academic-research-suite。

我想研究“生成式 AI 对大学教学质量的影响”，但还没有明确研究问题。
进入 deep-research 的 socratic 模式，通过提问帮我收敛问题。
现在不要生成大纲或正文。
```

已有明确材料时可使用普通别名：

```text
使用 $academic-research-suite：ars-outline。

研究问题：……
已有材料：文献矩阵、方法说明和初步结果。
请生成 IMRaD 大纲，并标出每节的论点、证据和缺口。
```

常用别名包括 `ars-plan`、`ars-outline`、`ars-abstract`、`ars-lit-review`、`ars-citation-check`、`ars-revision-coach`、`ars-revision`、`ars-reviewer` 和 `ars-full`。

## 适用原则

- 发现文献与核验文献分开记录；
- 系统综述先确认协议和纳排标准，再执行筛选；
- 引用必须回到 DOI、官方元数据或原文核验；
- 修改路线图由作者确认后再应用；
- 保留人工决策点、未核验状态、分歧和降级信息。

## 风险与边界

- 不能保证任何数据库或检索策略的完整覆盖；
- 不能替代领域数据库、伦理审查、统计专家或作者责任；
- 未公开稿件和私有数据发送到外部模型或 API 前必须确认授权；
- 套件包含多阶段状态和脚本，安装、更新和跨版本恢复时应固定版本并检查变更。
