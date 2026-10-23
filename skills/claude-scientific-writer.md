# Claude Scientific Writer

- 项目：<https://github.com/K-Dense-AI/claude-scientific-writer>
- GitHub Star：2,516（快照日期：2026-10-23；Star 会持续变化）
- 许可证：MIT
- 形态：科学写作 CLI / Python API / Claude Code 插件，内置一组经过选择的科研 Skills
- 主要定位：从检索和证据整理到论文、综述、基金申请、海报等成品

## 为什么值得关注

该项目把科研 Skill 与可直接运行的写作工具整合在一起。它强调“先研究、后写作”，支持实时文献查询、可核验引用、IMRaD 结构、图表和数据文件接入，以及 Word、LaTeX、PDF 等输出流程。相比只提供提示词的 Skill，它更接近一个可编程的科研写作应用。

## 核心能力

- 生成论文、文献综述、技术报告、基金申请和科研海报；
- 将 CSV、图像和已有文档纳入写作流程；
- 通过 `research-lookup` 搜索文献；
- 通过 `citation-management` 管理 BibTeX 与引用格式；
- 通过 `peer-review` 对稿件做结构化评估；
- 提供 Python API，便于集成到已有科研流水线；
- 使用上游 Scientific Agent Skills 的固定版本快照，提高构建可复现性。

## 安装方式

CLI/API 可从 PyPI 安装：

```bash
pip install claude-scientific-writer
```

从源码安装：

```bash
git clone https://github.com/K-Dense-AI/claude-scientific-writer.git
cd claude-scientific-writer
uv sync
```

在 Codex 中使用时，可从仓库的 `skills/` 目录选择需要的标准 `SKILL.md`，或把相关指令合并到项目级 `AGENTS.md`。插件安装命令主要面向 Claude Code，不能直接等同于 Codex 的安装命令。

## 推荐用法

```text
基于我提供的研究问题、数据表和已核验文献，生成 IMRaD 初稿。
要求：
- 不生成不存在的数据或引用；
- 每个事实性结论关联到可核验来源；
- 图表只使用提供的数据；
- 将无法核验的内容列入单独清单；
- 输出正文、BibTeX 和生成日志。
```

## 风险与边界

- “publication-ready” 是项目的产品定位，不代表生成稿已经达到投稿或同行评议标准；
- 实时检索能力可能依赖外部服务、API 密钥和网络传输，未公开稿件与敏感数据应先确认授权；
- 提示词中给出的数字也必须由原始数据或分析脚本验证；
- 应固定版本并保存生成配置、输入文件哈希、引用核验结果和人工修改记录。
