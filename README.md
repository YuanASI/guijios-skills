# silevy-skills

> 🌐 **For international visitors:** This is a **Chinese-first** Claude Code skills monorepo by [Silevy (硅基杠杆)](https://github.com/JackChen-me). Most skills target Chinese content creation workflows; some `SKILL.md` files are Chinese-only. The repo layout, install commands, and trigger words below work the same regardless of language. Translation PRs are welcome but may take time to review — see [Contributions](#contributions).

由 **Silevy（硅基杠杆）** 出品的 Claude Code skill 合集。最初是 `silevy-reply` 这一个 skill，现已扩展为面向中文内容创作者和 indie hacker 的系列工具。

## Skills 索引

| Skill | 用途 | 语言 |
|---|---|---|
| [**silevy-reply**](skills/silevy-reply/) | 跨平台回复拟稿（GitHub / Reddit / Twitter / HN），自带反 AI 痕迹规则 | 中文 + EN |
| [**silevy-weekly-review**](skills/silevy-weekly-review/) | 自动采集 Cowork 和 Claude Code 对话，自动聚类，生成对内复盘 + 对外周记 | 中文 |

后续会有更多 silevy-* skill 陆续加入，请关注本仓更新。

## 安装

### 安装整个 monorepo

```bash
npx skills add JackChen-me/silevy-skills
```

### 只装某一个 skill

```bash
npx skills add JackChen-me/silevy-skills --skill silevy-reply
npx skills add JackChen-me/silevy-skills --skill silevy-weekly-review
```

### 手动安装

```bash
git clone https://github.com/JackChen-me/silevy-skills.git
ln -s "$(pwd)/silevy-skills/skills/silevy-reply" ~/.claude/skills/silevy-reply
ln -s "$(pwd)/silevy-skills/skills/silevy-weekly-review" ~/.claude/skills/silevy-weekly-review
```

支持 Claude Code、Codex、Cursor、GitHub Copilot、OpenCode 等所有兼容 [Vercel 的 skills CLI](https://github.com/vercel-labs/skills) 的 agent。

## 关于

作者：Jack（[@JackChen-me](https://github.com/JackChen-me)），公众号「硅基杠杆 OS」/ 小红书「杰克西｜硅基杠杆」/ B站「杰克西｜硅基杠杆」。

每个 skill 的具体用法请进对应子目录查看 README。

## Contributions

欢迎 issue 和 PR，特别是：

- 🐛 Bug 报告 / skill 触发不准的场景
- 🌍 翻译 PR（中文 → 英文，或英文 → 中文）
- ✨ 新 skill 提议（请先开 issue 讨论）

⚠️ **维护说明**：本仓由我一人维护，PR review 可能不及时。中文 skill 的英文翻译版本**不在我的主动维护范围内**——欢迎国际用户自行提交并维护翻译分支。

**For international contributors:** PRs welcome, especially for English translations of Chinese-only skills. As this is a solo-maintained side project, reviews may take time — please be patient. I won't proactively translate skills to English, but I will gladly review and merge community translations.

## License

MIT — see [LICENSE](LICENSE).
