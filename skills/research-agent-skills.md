# Research Agent Skills

- 项目：<https://github.com/KalarisLabs/research-agent-skills>
- GitHub Star：58（快照日期：2026-10-23；Star 会持续变化）
- 许可证：README 与 `CITATION.cff` 标注 MIT；GitHub API 尚未识别标准许可证文件，使用前仍应检查仓库 LICENSE 与第三方声明
- 形态：280+ 个遵循开放 Agent Skills 规范的科研 Skill
- 兼容性：Codex、Claude Code、Cursor、Gemini CLI 等

## 为什么纳入

这个项目的绝对 Star 数低于前几个项目，但在专门面向科研全过程的 Agent Skills 新项目中已有较高关注度，而且覆盖范围很完整。它把文献综述、假设形成、实验设计、统计分析、论文写作、引用核验和同行评审拆分为可单独安装的 Skill，并提供 AI、机器学习、生物、化学、医学和物理等领域组合包。

## 代表性能力

- `systematic-review-prisma`：系统综述协议、检索、去重、筛选与 PRISMA 流程；
- `citation-verification`：引用存在性与论断支持关系检查；
- `statistical-analysis`：统计分析与结果解释；
- `ml-paper-writing`：机器学习论文写作；
- `autoresearch`：通过内外双循环管理自主研究与实验；
- 各学科专用分析和数据库 Skill；
- `research-agent-skills`：在大型集合中选择最小适用 Skill 组合的索引 Skill。

Skill 名称与数量应以仓库当前 `catalog/skills.json` 和 `skills/` 目录为准。

## 安装方式

交互式选择 Skill：

```bash
npx skills add KalarisLabs/research-agent-skills
```

安装单个 Skill：

```bash
npx skills add KalarisLabs/research-agent-skills --skill systematic-review-prisma
```

对不支持自动安装的 Agent，可直接读取相应 `skills/<name>/SKILL.md`。不建议默认安装全部 280+ 个 Skill；按研究阶段与学科选择最小集合更容易审查权限、依赖和触发条件。

## 推荐组合

系统综述项目可从以下最小组合开始：

```text
systematic-review-prisma
→ citation-verification
→ statistical-analysis（仅在数据与研究设计适用时）
→ 对应学科的专业 Skill
```

机器学习论文可组合文献检索、实验设计、统计分析、可复现性检查与 `ml-paper-writing`，但论文正文必须基于真实实验产物，而不是让写作 Skill 补齐不存在的结果。

## 风险与边界

- 这是更新较快的大型集合，应固定 release 或 commit，并记录实际使用的 Skill 版本；
- 部分 Skill 会执行脚本、访问网络或依赖第三方 API，安装前需审查；
- README 声明的 MIT 许可不自动覆盖所有第三方材料，应检查 `THIRD_PARTY_NOTICES.md`；
- 系统综述中的纳排标准、最终筛选与偏倚判断仍需研究者确认；
- `autoresearch` 的自主运行指令不应绕过项目权限、伦理审批或高风险操作确认。
