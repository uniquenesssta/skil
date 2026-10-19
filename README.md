# skil

按用途维护规则和相关文件，根目录分为 [Code](Code/) 与 [Figma](Figma/) 两类。

## 文件归属

| 位置 | 内容 |
| --- | --- |
| [Code/](Code/) | 现有 AI 软件开发协作规则、原始文档与版本说明 |
| [Code/0.0.1/](Code/0.0.1/) | 当前优化版本的三份配套规则 |
| [Figma/](Figma/) | 后续新增的 Figma 规则及相关文件，目前仅预留目录 |
| [AGENTS.md](AGENTS.md) | 本仓库维护时的目录归属与规则加载说明 |
| [LICENSE](LICENSE) | 仓库许可证 |

## 路径迁移

| 原路径 | 新路径 |
| --- | --- |
| `0.0.1/` | `Code/0.0.1/` |
| `AGENTS.md`（原始开发规则） | `Code/AGENTS.md` |
| `ALL_AI_CODE(6).md` | `Code/ALL_AI_CODE(6).md` |
| `AI_PROJECT_RULES(3).md` | `Code/AI_PROJECT_RULES(3).md` |
| `README.md`（原开发规则说明） | `Code/README.md` |

引用旧路径的外部任务书或链接需按上表更新。原始三份规则和 `0.0.1` 版本正文保持不变，版本内相对链接仍在同一目录下。

开发规则的使用方式、既有审计结论与历史说明见 [Code/README.md](Code/README.md)。Figma 文件放入 `Figma/`，不与开发规则版本混放。

## Change Log

### 2026-10-19 — 按用途整理目录

- 将现有开发规则及 `0.0.1` 版本统一迁入 `Code/`，保留规则正文和原始文件名。
- 新增 `Figma/` 目录说明，为后续 Figma 文件预留独立位置。
- 根目录改为分类导航，许可证仍保留在根目录；同步更新移动后的路径和加载说明。
- 验证：规则文件逐字节一致、26 个 Markdown 相对链接检查通过；新增及编辑文档的空白检查通过。全量差异检查报告原始 `Code/AGENTS.md` 的既有 CRLF 行尾，保留原文件字节未作格式化。本次仅整理文档，无构建或运行测试；未进行 Windows 实际运行验证。
