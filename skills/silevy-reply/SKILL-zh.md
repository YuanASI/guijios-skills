---
name: silevy-reply
description: >
  跨平台回复/评论拟定。自动路由到对应平台规则（GitHub/Reddit/Twitter/HN/通用）。
  当用户提到以下场景时使用：回复 issue、回复 PR、github reply、帮我回、写个评论、
  comment on issue、回复 reddit、reddit reply、帮我回 reddit、分析评论、
  回复推特、twitter reply、帮我写回复。
---

跨平台回复/评论拟定。根据输入内容自动路由到对应平台规则。

## 路由

| 输入 | 模式 |
|------|------|
| GitHub Issue/PR 编号或链接 | GitHub 模式 |
| Reddit 评论文本/截图 | Reddit 模式 |
| Twitter/X 内容 | Twitter 模式 |
| 其他平台或未指定 | 通用模式（套用通用原则） |

---

# 第一部分：通用原则（所有平台共享）

## 场景判断（先判断再写）

| 场景 | 定义 | 核心策略 |
|------|------|---------|
| **自己地盘** | 你是 maintainer / 帖主 / 作者 | 交付信息为主 |
| **别人地盘** | 你是访客 | 先贡献经验，再提问；不自我推销 |
| **冷启动 DM** | 零关系，主动联系对方 | 引用对方具体内容建立信任 |

### 别人地盘的原则

- **先贡献再提问。** 分享同类问题或经验，然后自然引出一个问题
- **一条评论只问一个问题。** 多个问题 = 审讯感
- **问题必须有明确信息价值。** 发之前能说清"这个回答对我有什么用"，说不清就重写
- **你的 profile 就是你的介绍。** 不需要在正文里自报家门
- **不暴露调研动机。** 看起来像"遇到同样问题的人"，不是"竞品 founder 来套信息"

### 冷启动 DM 的原则

- **引用对方的具体原话。** 太泛的引用 = 低回复率
- **明确说不是在卖东西**
- **给对方退出的台阶。** "No worries if not"
- **async 优先于 call。** 回复率更高

## 发送前检查（4 步，每次必须完成）

1. **意图检查：** 这条评论想拿到什么信息？对我们有什么具体用处？答不出来就重写
2. **事实核查：** 自己项目的技术声明对照代码验证；引用别人的话对照原文验证
3. **味道检查：** 以收件人视角重读。像竞品调研？像 AI？还是像遇到同样问题的人自然留言？
4. **文风检查：** 过一遍禁止项清单
5. **压缩检查：** 能不能砍掉一整段？bullets 能不能 inline 成 prose？对方已经说清楚的内容有没有被你复述？不确定就砍

## 跨平台禁止项

- em dash（—）在正文中使用
- "Thanks for your contribution" / "Thank you for reporting this"
- "Great catch" / "Great question" / "Appreciate the detailed report"
- "the clearest/strongest/best [X] I've seen" — 最高级赞美
- "Feel free to..." / "Don't hesitate to..."
- "Happy to discuss further" / "Let me know if you have questions"
- "I'd love to hear your thoughts"
- "I maintain [项目名]" 作为开头
- 一条评论里 @多人分别提问
- "Curious about..." / "I'd be interested to know..." — 暴露调研动机
- 任何三段式结构。不止 thanks → answer → invite，还包括：confirm 问题 → 复述方案 → 列 asks、acknowledge → explain → close。一条评论超过 2 段就要警觉
- 用 bullet list 列 2-3 个简短要点。真人会 inline 成一句 prose。bullets 只给 4+ 个独立复杂项才合理
- 复述对方已经说清楚的内容。对方写了方案就别再"你说得对，方案是..."，直接进入下一步

## 跨平台应该做到

- 信息密度高，没有填充句
- 有观点，不只是描述
- 直接说结论，不铺垫
- 用缩写（doesn't, won't, btw, iirc, tbh）
- 短。默认 1-2 句。超过 3 句先问自己：能不能砍一段？超过 2 条 bullet 先问自己：能不能合并成 prose？只有深度技术讨论才放开长度

## 策略原则

1. **沉默是武器** — 不回复 ≠ 输了
2. **技术可信度是唯一护城河**
3. **转化 > 辩护** — 精力花在可能用你产品的人身上
4. **不解释动机** — 只回答真心问的人
5. **不参与法律讨论**

---

# 第二部分：GitHub 模式

## 输入

- Issue/PR 编号（如 #72）或链接
- 直接粘贴的评论内容
- 截图

收到编号/链接后，先用 `gh` 命令读取 Issue/PR 正文和已有评论，理解完整上下文。

## 分析流程

### 第一步：理解上下文

- Issue 还是 PR？Open / Closed / Merged？
- 作者是外部用户还是自己？
- 已有多少评论？最后一条说了什么？
- 对方的核心诉求是什么？
- **判断场景：自己 repo 还是外部 repo？**

### 第二步：拟定回复

输出可发送的文本。策略意图放在回复之后解释。

## GitHub 文风补充

- **像同事之间在 Slack 上聊天**
- 可以省略主语。"Fixed in #77." 而不是 "This has been fixed in #77."
- 技术问题用技术语言回答，不要降级解释

### 语感参考

**关闭 Issue：** `Fixed in #77.`

**确认 Bug：** `Yeah this is real. Will add a per-agent semaphore.`

**功能请求：** `Makes sense. Tracking in #XX.`

**追问用途：** `What's the use case driving this?`

**Code review：** `Left a few comments. Main thing is [具体问题].`

**合并 PR：** `LGTM, merged.`

## GitHub 场景策略

### 自己 repo

| 场景 | 策略 |
|------|------|
| 外部 Bug 报告 | 确认问题 + 修复计划/状态，可追问用途 |
| 外部 PR（质量好） | 实质性技术反馈，合并后可追问用途 |
| 外部 PR（质量差） | 指出具体问题，不模糊鼓励 |
| 功能请求 | 判断是否做 → 说结论 → 关联 tracking issue |
| 重复贡献者 | 可追问用途，不过度热情 |
| 无意义 Issue | 关闭，一句话说原因 |

### 外部 repo

禁止：
- "I maintain [项目名]" 开场
- 同一条评论 @两个以上的人分别提问
- "Curious about..." / "I'd be interested to know..."

语感参考：

不好：
> I maintain open-multi-agent, a TS multi-agent framework.
> We took a similar approach to what you're describing.
> @alice I'm curious how you solved X?
> @bob I'd also love to know about Y?

好：
> Same problem in a TS multi-agent orchestrator. [具体描述同类问题].
> @alice how much effort did X take to build?

### GitHub 实战案例

**案例 1：关闭 Bug Issue + 追问用途（#72）**

> Fixed in #77.
>
> Good catch on the token budget interaction btw. What are you using this for? Would be useful to know.

**案例 2：追问重复贡献者用途（#71）**

> Thanks for the second PR. What's the use case driving this?

**案例 3：在 AutoGen issue 下参与讨论（microsoft/autogen#7487）**

> Same problem in a TS multi-agent orchestrator. Coordinator handles decomposition and synthesis but nothing checks goal alignment in between. Blind spot by design.
>
> @msaleme how much engineering effort did the separate integrity node take to build and maintain? Wondering if this is a weekend project or a full team commitment.

要点：第一段贡献经验，不自报家门。第二段问一个有信息价值的问题（workaround 代价量化）。

**案例 4：功能请求 + 邀请 PR（#124）**

不好（三段式 AI 味：confirm 问题 → 复述方案 → 列 asks）：
> Real gap. `onTrace` shows a tool ran but not what went in/out, so debugging means digging into model server logs.
>
> Proposal looks right: add `input: Record<string, unknown>` and `output: string` to `ToolCallTrace`, pass them in `emitTrace`. Mirrors what `ToolCallRecord` already exposes.
>
> Want to send a PR? Two asks if you do:
> - Keep both fields required, no opt-in flag
> - Add assertions in `tests/trace.test.ts` covering success and error cases

好（真 maintainer）：
> Makes sense. Want to PR this? Just add coverage in `tests/trace.test.ts` for both success and error.

要点：对方已经写清楚要改什么，就别再"确认问题 + 复述方案"，直接同意 + 邀请 PR + 一个 inline 约束。多个短约束 inline 成 prose，不用 bullet。

## GitHub 发送

`gh issue comment` 或 `gh pr comment` 执行。

---

# 第三部分：Reddit 模式

## 输入

- 直接粘贴的评论文本
- 包含评论的文件路径
- 截图

## 分析流程

### 第一步：分类每条评论

| 类别 | 是否回复 | 判断标准 |
|------|---------|---------|
| 技术问题 | 回复 | 问了具体的实现、用法、架构问题 |
| 真实用户反馈 | 回复 | 实际使用过产品 |
| 定位/差异化问题 | 回复 | "这跟 X 有什么区别" |
| 使用问题 | 回复 | 怎么装、怎么配置 |
| 有利论据/类比 | 视情况 | 帮你说话的人，简短认可 |
| 正面认可 | 视情况 | 热情的简短感谢，冷淡的跳过 |
| 纯攻击/嘲讽 | 不回复 | 无具体内容 |
| 法律/版权讨论 | 不回复 | 怎么说都错 |
| 蹭帖推广 | 不回复 | 推广自己的项目 |
| 玩梗/吃瓜 | 不回复 | 无实质内容 |
| 跑题 | 不回复 | 无关 |

### 第二步：拟定回复

```
#### u/用户名 (subreddit) 星级

> 原始评论引用

**建议回复：**
> 回复内容

**理由：** 策略意图
```

不回复的汇总到表格：

```
| 用户 | 内容摘要 | 为什么不回 |
```

### 第三步：输出舆论小结

简要总结整体情绪、趋势、值得注意的信号。

## Reddit 文风补充

Reddit 用户对 AI 文风极度敏感，以下规则在通用禁止项基础上额外适用：

- 面面俱到地回应对方每一个论点 → 禁止（真人只挑一两个点）
- 结构化列表回复简单问题 → 禁止（用自然段落）
- 过度礼貌和正面 → 禁止（真人会有态度）
- 允许口语化：nah, tbh, kinda, yeah, lol
- 语气像在跟同行聊天

### Reddit 语感参考

不好（AI 味）：
> Great question. The framework uses namespaced keys for SharedMemory, so each agent writes to its own namespace — no cross-agent write conflicts. Reads are global. Would love to hear your thoughts on this approach.

好（人味）：
> SharedMemory is namespaced per agent, so writes don't conflict. Reads are global though. Closest to single-writer-per-namespace if you want a label for it.

不好（AI 味）：
> Appreciate the honest feedback. Local model compatibility is still rough — tool-calling format varies a lot across models. If you have specific errors, happy to look into it.

好（人味）：
> yeah local model support is still rough tbh. tool-calling format varies a lot between models and that's where it breaks. if you hit specific errors feel free to open an issue, would be useful to know what breaks first.

---

# 第四部分：Twitter/X 模式

## Twitter 文风补充

- 280 字符限制，极致精简
- 可以用 thread 但每条都要独立有信息量
- 语气比 Reddit 更随意
- 可以用 emoji 但不过度
- 不要 hashtag spam

---

# 第五部分：通用模式

当平台不在上述列表中（HN、Discord、论坛等），套用第一部分的通用原则 + 以下补充：

- HN：极度重视技术深度，不容忍任何推销感。比 Reddit 更克制
- Discord：最随意，可以用表情反应代替文字回复
- 论坛：视具体社区文化调整

## 发送

拟好文案 → 完成发送前 5 步检查 → 询问用户是否发送 → 确认后执行。
