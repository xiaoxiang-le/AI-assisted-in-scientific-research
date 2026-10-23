# Scientific Agent Skills

- 项目：<https://github.com/K-Dense-AI/scientific-agent-skills>
- GitHub Star：54,129（快照日期：2026-10-23；Star 会持续变化）
- 许可证：仓库为 MIT；每个 Skill 可能有自己的许可证，安装前需逐项检查
- 形态：177 个遵循 Agent Skills 开放规范的独立 Skill
- 兼容性：Codex、Claude Code、Cursor、Gemini CLI 等支持 Agent Skills 的客户端

## 为什么值得关注

这是目前 GitHub 上关注度最高、覆盖面最广的科研 Agent Skills 集合之一。它不只辅助写论文，还把科研中常见的软件包、数据库和分析流程封装为可按需加载的 Skill，重点覆盖生物信息学、基因组学、化学信息学、药物发现、临床研究、材料科学、统计分析、科研可视化、文献检索和科学写作。

与“生成一篇论文”的单体工具不同，它更适合作为科研工作台的能力库：先选取与课题相关的少量 Skill，再将数据分析、证据检索、绘图、引用管理和写作串成可核验流程。

## 与论文直接相关的能力

- `paper-lookup`：查找论文与元数据；
- `literature-review`：组织文献综述流程；
- `scientific-writing`：按科学论文结构写作；
- `citation-management`：处理 BibTeX 和引用；
- `peer-review`：对稿件进行结构化评审；
- `scientific-critical-thinking`：检查论证、证据与替代解释；
- `scientific-visualization`、`scientific-slides`：生成科研图表与汇报材料；
- 大量领域 Skill：用于实际分析，而不仅是润色文字。

技能名称和目录会随版本变化，使用前应以仓库当前 `skills/` 目录为准。

## 安装建议

优先只安装当前课题需要的 Skill：

```bash
npx skills add K-Dense-AI/scientific-agent-skills
```

也可以克隆仓库后，审查并复制单个 `skills/<name>/` 目录到 Codex 的 Skill 目录。正式科研项目应固定 release tag 或 commit SHA，记录 Skill 版本、依赖版本和运行日期，不要让进行中的分析静默跟随 `main` 更新。

## 推荐用法

```text
请使用 literature-review、paper-lookup 和 citation-management：
1. 围绕明确研究问题建立检索式；
2. 分开记录发现来源和核验来源；
3. 导出 DOI、题名、作者、年份和 BibTeX；
4. 对关键结论回到原文核验；
5. 输出检索盲区和未核验项目。
```

## 风险与边界

- Skill 是能影响 Agent 行为并可能执行脚本的代码，应审查 `SKILL.md`、`scripts/`、网络访问和凭据需求；
- 不要一次性安装全部 Skill；领域依赖可能庞大或相互冲突；
- 仓库采用 MIT 不代表每个独立 Skill 都是 MIT；
- 自动安全扫描只能降低风险，不能证明 Skill 安全；
- 检索结果、统计输出、临床或监管内容仍需领域专家核验。
