---
name: skill-finder-zh
description: 为用户的一句话或模糊任务严谨寻找、验证、比较和推荐最匹配的 Codex/ChatGPT/AI agent skills。Use when the user asks to find skills, recommend skills, installable skills, GitHub skills, skillsmp.com skills, skill marketplace results, workflow skill combinations, or says they need a skill for a domain such as coding standards, video editing, painting, design, research, spreadsheets, presentations, documents, automation, browsing, GitHub, or any task where suitable skills must be discovered from GitHub, https://skillsmp.com/search, official/curated registries, or the web.
---

# Skill Finder 中文

## 目标

把用户的一句话需求转化为可执行的 skill 推荐。必须主动理解需求、联网检索、交叉验证来源、比较候选项，并给出可以直接使用的最佳 skill 或 skill 组合。

典型输入：

- “需要编程规范的 skill”
- “我想做一个剪辑相关的任务，我需要使用哪些 skill 来完成？”
- “我是画家，请你给我对应的 skill”
- “帮我找 GitHub 上最适合做数据分析的 skill”

## 核心原则

- 先理解任务，再搜索关键词。不要只机械匹配用户原词。
- 必须优先检索 `https://skillsmp.com/search` 和 GitHub；必要时扩展到官方文档、awesome lists、社区仓库、插件/skill 市场页、发行说明或作者主页。
- 因为 skill 列表、仓库状态和安装方法经常变化，推荐前必须联网核验最新信息。
- 推荐必须基于证据：来源链接、最后更新或活跃度、README/说明质量、适配平台、安装路径、许可证/维护风险。
- 少而准优先。默认给 3-7 个候选；如果用户只想要“最佳”，给 1 个主推荐和 2 个备选。
- 当用户描述模糊时，先做合理推断并说明推断；只有在无法安全判断平台、预算、隐私或安装环境时才追问。
- 不要把不存在、无法验证、来源不明或过时明显的 skill 当成确定推荐。

## 快速流程

1. 解析用户意图：
   - 任务域：编程、设计、剪辑、绘画、数据、文档、演示、研究、自动化、浏览器、GitHub、产品等。
   - 产出类型：找单个 skill、找组合、比较、安装指导、替代方案。
   - 平台约束：Codex skill、ChatGPT GPT/Action、MCP、插件、CLI、agent workflow。
   - 隐含能力：例如“画家”可能需要图像生成、参考管理、作品集、色彩分析、社媒发布、版权/合同文档。

2. 生成检索词：
   - 中文关键词：用户原词 + 同义词 + 任务名 + “skill” + “Codex skill” + “AI agent skill”。
   - 英文关键词：domain + `skill`, `codex skill`, `agent skill`, `workflow`, `github`, `marketplace`。
   - 站内搜索：
     - `site:skillsmp.com/search <keywords>`
     - `site:skillsmp.com <keywords> skill`
     - `site:github.com <keywords> codex skill`
     - `site:github.com <keywords> SKILL.md`

3. 检索来源：
   - 首选：`https://skillsmp.com/search`。
   - 首选：GitHub 仓库、目录、`SKILL.md`、release、issue、README。
   - 次选：官方 registry、作者主页、文档站、package/plugin marketplace、可信列表。
   - 对中文需求，也同时用英文检索，因为 skill 名称和 README 常以英文为主。

4. 过滤候选：
   - 必须有明确名称、用途说明、来源 URL。
   - 必须能看出如何安装或使用，或者至少能定位 skill 目录/仓库。
   - 排除明显无关、纯文章无可用 skill、失效页面、复制站、无法确认来源的结果。
   - 对安全敏感任务，例如医疗、法律、金融、账号自动化，要强调限制、来源可信度和人工复核。

5. 评分排序：
   - 需求匹配度：0-5 分。
   - 可安装性/可使用性：0-5 分。
   - 维护活跃度：0-5 分，参考最近提交、release、issue 响应。
   - 文档质量：0-5 分，参考 README、示例、参数、限制说明。
   - 可信度：0-5 分，参考作者、stars/forks、许可证、社区引用、官方性。
   - 风险扣分：过久未更新、权限过大、安装说明不明、闭源、功能夸张、和用户平台不兼容。

6. 验证最佳候选：
   - 打开候选来源，不只看搜索摘要。
   - 核对 README 或 `SKILL.md` 的实际能力。
   - 检查最近更新时间或仓库活动；如果无法确认，标为“未确认活跃度”。
   - 如果是 GitHub skill，优先确认目录结构是否含 `SKILL.md`、`agents/openai.yaml`、scripts/references/assets 等。
   - 如果是 skillsmp.com 结果，确认页面标题、描述、安装入口、作者/来源链接。

## 推荐格式

默认用中文输出，除非用户要求英文。

给出：

1. 结论：一句话说明最推荐哪个 skill 或组合。
2. 推荐表格：
   - 名称
   - 适合的需求
   - 来源链接
   - 可信依据
   - 主要限制/风险
   - 推荐等级：强烈推荐 / 推荐 / 可选 / 谨慎
3. 最佳使用组合：
   - 单一任务给主 skill + 备选。
   - 复杂任务给链路，例如“素材整理 -> 剪辑 -> 字幕 -> 发布”的 skill 组合。
4. 安装或使用建议：
   - 如果用户需要 Codex skill，说明仓库路径、skill 目录、安装命令或手动复制路径。
   - 如果安装方式无法核实，明确说“我还不能确认安装方式”，并给出下一步核验建议。
5. 证据与时间：
   - 列出核验过的链接。
   - 标注“已于 YYYY-MM-DD 核验”。

## 模糊需求推断规则

对职业、身份或大目标，拆成多个可能工作流再推荐。

- “我是画家”：可能需要图像参考、色彩调色板、作品集整理、作品说明文案、版权合同、社媒发布、展览申请。
- “我要做剪辑”：可能需要视频剪辑、字幕、转写、B-roll 搜索、音频清理、封面图、发布文案。
- “编程规范”：可能需要 lint、代码审查、架构规范、提交规范、文档规范、语言/框架专项规则。
- “科研”：可能需要论文检索、文献管理、数据分析、图表、实验记录、写作润色。

输出时先说“我把你的需求理解为……”，再推荐最贴近的 skill。

## 搜索策略细节

优先组合多种查询，不要依赖一个结果：

```text
<用户关键词> skill
<用户关键词> Codex skill
<英文领域词> agent skill GitHub
site:github.com <英文领域词> SKILL.md
site:skillsmp.com <用户关键词>
site:skillsmp.com/search <英文领域词>
```

如果搜索结果不足：

- 扩展同义词，例如“剪辑”扩展为 video editing、post-production、captioning、transcription、ffmpeg。
- 改查底层工具生态，例如 `ffmpeg skill`、`premiere automation skill`、`davinci resolve skill`。
- 查 GitHub topic、README、awesome list。
- 查官方平台或插件市场。
- 明确告知“没有找到足够可靠的现成 skill”，并建议创建一个新 skill 的范围。

## 严谨性检查

推荐前逐项检查：

- 名称和链接是否真实可打开。
- 推荐理由是否来自页面内容，而不是搜索摘要臆测。
- 是否匹配用户平台和任务。
- 是否存在更官方、更活跃或更具体的替代项。
- 是否把“工具/库/插件”误称为“skill”；如果不是 skill，要标注为替代工具。
- 是否需要多个 skill 才能完成完整任务。
- 是否存在安全、隐私、版权、账号封禁或许可证风险。

## 示例输出骨架

```markdown
我把你的需求理解为：你需要用于“编程规范落地”的 skill，不只是代码格式化，还包括 review、lint、提交规范和团队规则沉淀。

最推荐：...

| 推荐 | 来源 | 为什么匹配 | 风险 |
|---|---|---|---|
| ... | ... | ... | ... |

最佳组合：
1. ... 用于 ...
2. ... 用于 ...

已于 2026-05-05 核验这些来源：...
```

## 不确定时的处理

- 如果结果质量低，不要硬凑。说明没有找到高可信匹配，并给出最接近的候选。
- 如果用户要求“最准确”，宁可少推荐，也不要列一堆弱相关结果。
- 如果需要登录、私有仓库或付费访问才能确认，标明未核验部分。
- 如果用户需要安装，先确认目标环境；若可以合理推断为 Codex，则给 Codex skill 安装路径建议。
