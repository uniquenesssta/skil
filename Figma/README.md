# Figma 通用设计与代码交接规则

本目录是一套可用于不同项目的配套规则与模板，不是已安装的 Skill，也不是某个项目的当前设计或验收记录。

| 文件 | 职责 |
| --- | --- |
| [AGENTS.md](AGENTS.md) | 规则入口、项目适配与 Figma 专用要求 |
| [docs/design/figma-handoff.md](docs/design/figma-handoff.md) | 设计流程、交接字段及验证方法 |
| [docs/design/figma-asset-licenses.md](docs/design/figma-asset-licenses.md) | 资源登记规范与保留的第三方许可参考 |
| [docs/design/figma-state.json](docs/design/figma-state.json) | 未配置的项目状态模板，schemaVersion 2 |
| [docs/design/figma-tokens.json](docs/design/figma-tokens.json) | 可选 token 示例，schemaVersion 2；不是默认批准主题 |

## 与 Code 配合

采用时从 [Code/0.0.1/AGENTS.md](../Code/0.0.1/AGENTS.md) 加载配套工程规则，再读取本目录入口。Code 管工程设计、职责拆分、验证、交付和项目记录；Figma 补充设计系统、节点、原型与代码映射要求。这里的 Code 是规则目录，不是源码目录。

在目标项目中保留现有指令并合并适用入口，不直接覆盖。整体采用或单独放置时同步调整链接，按真实项目填写需求依据、角色、技术栈、仓库/分支、设计文件及授权；不自动创建分支、安装依赖或进入实施阶段。

## 模板状态与迁移

状态中的 null、空集合和 not_run 表示尚未配置或验证；不能用它们作为完成证据。Token 的 example ID 仅用于本地示例引用，实际操作需替换为真实 Figma 导出 ID。保留示例数值不代表强制使用某种颜色、字体或尺寸。

本次将项目快照整理为通用模板，旧项目节点、历史授权、业务样例和验收结论不再作为通用默认。已有项目数据保留在原项目和 Git 历史；若消费旧 JSON 的脚本需要使用新版，先按 schemaVersion 适配，不直接覆盖已有运行数据。

返回 [README.md](../README.md)。
