> Part of **[silevy-skills](../../README.md)** — Claude Code skills by Silevy. [Back to index ↑](../../README.md)

# silevy-reply

A Claude Code skill for drafting cross-platform replies and comments. Auto-routes to platform-specific rules for GitHub, Reddit, Twitter/X, Hacker News, and more.

## What it does

When you need to reply to an issue, PR, Reddit comment, tweet, or any online discussion, this skill:

1. **Routes** to the right platform ruleset based on your input
2. **Analyzes** context (your turf vs. someone else's, cold DM, etc.)
3. **Drafts** a reply that sounds human, not AI
4. **Checks** before sending: intent, facts, tone, style

## Platform support

| Platform | Trigger |
|----------|---------|
| GitHub Issues/PRs | Paste issue/PR number or link |
| Reddit | Paste comment text or screenshot |
| Twitter/X | Paste tweet content |
| HN / Discord / Forums | Auto-applies general principles |

## Key principles

- **High information density.** No filler sentences.
- **Have an opinion.** Don't just describe.
- **Lead with the conclusion.** No preamble.
- **Short.** 2-5 sentences unless deep technical discussion.
- **Sound human.** Contractions, casual tone, no AI-speak.

## Anti-AI-smell checklist

The skill maintains a detailed blocklist of phrases and patterns that scream "AI-generated", including:

- Em dashes in body text
- "Great question" / "Great catch"
- "Feel free to..." / "Happy to discuss further"
- Thank > Answer > Invite three-part structure
- Addressing every single point in a reply

## Installation

### Option 1: `npx skills add` (recommended)

Works with Claude Code, Codex, Cursor, GitHub Copilot, OpenCode, and other agents supported by [Vercel's skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add YuanASI/silevy-skills --skill silevy-reply
```

### Option 2: Manual install

Two language versions: `SKILL.md` (English, default) and `SKILL-zh.md` (Chinese / 中文版).

```bash
# English version (default)
git clone https://github.com/YuanASI/silevy-skills.git
ln -s "$(pwd)/silevy-skills/skills/silevy-reply" ~/.claude/skills/silevy-reply

# Chinese version — swap SKILL.md to point at the zh file
cp "$(pwd)/silevy-skills/skills/silevy-reply/SKILL-zh.md" \
   ~/.claude/skills/silevy-reply/SKILL.md
```

Then use it in Claude Code by typing `/silevy-reply` followed by the content you want to reply to.

## Examples

**GitHub issue reply:**
```
/silevy-reply #72
```

**Reddit comment analysis:**
```
/silevy-reply [paste reddit comments]
```

**Draft a tweet reply:**
```
/silevy-reply [paste tweet]
```

## License

MIT — see [../../LICENSE](../../LICENSE).
