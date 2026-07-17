> Part of **[guijios-skills](../../README.md)** — Claude Code skills by GuijiOS. [Back to index ↑](../../README.md)

# GuijiOS Weekly Review

自动生成每周复盘周报的 Claude Skill，从 Claude Desktop（Cowork + Code tab）和 Claude Code 终端 CLI 的全部对话记录中提取本周所有工作内容，输出两份报告：

- **对内周报**：给自己看的全面复盘，含成果清单、时间分配、关键决策、下周计划和反思
- **对外周报**：面向公开读者的精选周记，自动隐去敏感信息

## 特性

- **全量数据采集**：覆盖 Claude Desktop Cowork tab 全部会话（含归档）和 Claude Code（Desktop Code tab + 终端 CLI）全部对话，自动去重 Cowork 派生的子进程
- **数据驱动分类**：不预设工作类别，首次运行时从实际对话内容自动聚类，用户确认后持久化；后续运行自动检测新类别
- **敏感信息过滤**：可配置的过滤规则，确保对外周报不泄露财务、人事、运营数据等隐私信息
- **自动验证**：用 subagent 交叉检查事实一致性和信息泄露

## 安装

### 方式一：Skills CLI（推荐）

使用 [Vercel Labs Skills CLI](https://github.com/vercel-labs/skills) 一键安装：

```bash
npx skills add YuanASI/guijios-skills --skill guijios-weekly-review
```

### 方式二：手动安装

```bash
git clone https://github.com/YuanASI/guijios-skills.git
ln -s "$(pwd)/guijios-skills/skills/guijios-weekly-review" ~/.claude/skills/guijios-weekly-review
```

## 使用

在 Cowork 或 Claude Code 中输入：

```
写周报
```

```
总结一下这周
```

```
weekly review
```

首次运行时会引导你完成简单配置（身份标签、对外周报格式、敏感信息规则），分类体系由 AI 从你的实际对话数据中自动推断。

## 从旧名称迁移

本 skill 曾使用 `GuijiOS-weekly-review` 和 `silevy-weekly-review` 名称。现在的唯一维护入口是 `guijios-weekly-review`。

如果你已经使用过旧版，重新安装后可将旧 skill 目录中的 `config.json` 复制到 `~/.claude/skills/guijios-weekly-review/config.json`，保留原有的身份、分类和敏感信息配置。

## 配置

配置文件 `config.json` 首次运行时自动生成（在 skill 安装目录下），包含以下可定制项：

| 字段 | 说明 |
|------|------|
| `identity` | 身份标签和对外周报的自我介绍 |
| `categories` | 工作分类（首次运行自动填充，后续自动演进） |
| `external_report` | 对外周报的标题模板、主题数量、写作风格、目标读者 |
| `sensitive_filters` | 敏感信息过滤规则（类别 + 示例） |
| `file_naming` | 输出文件命名模板 |

详见 [`references/config-guide.md`](references/config-guide.md)。

## 文件结构

```
skills/guijios-weekly-review/
├── SKILL.md                      # 主指令文件
├── README.md                     # 本文件
├── references/
│   └── config-guide.md           # 配置字段详细说明
└── assets/
    └── config-template.json      # 默认配置模板
```

## License

MIT — see [../../LICENSE](../../LICENSE).
