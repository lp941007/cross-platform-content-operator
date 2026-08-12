# Cross-Platform Content Operator

面向抖音、视频号、小红书、快手、B站、微信公众号等平台的内容运营 Agent Skill。它根据产品或服务的真实资料，生成平台适配的运营方向、选题、文案、脚本、分镜、BGM规格、拍摄流程和可复盘的测试方案。

核心原则：保留真实事实，改变平台表达；不编造卖点、案例、政策或数据，不保证播放量、咨询量和成交量。

## 适用场景

- 为产品、服务、实体门店、创始人IP或机构制定内容运营方案。
- 将同一组真实资料适配成不同平台的内容，而不是一稿搬运。
- 生成选题、标题、开场钩子、口播、分镜、字幕、封面、发布文案和评论引导。
- 设计BGM方向、拍摄流程、人员安排、预算分配和发布节奏。
- 设计自然流量或付费测试，确定指标、停止条件和复盘方法。
- 处理资料不完整的需求：优先一次询问一个关键问题，其余部分用明确标注的保守假设继续。
- 识别医疗、教育、未成年人、隐私、版权和广告宣传等高风险内容。
- 对诊所、医疗服务、医疗器械、医师和健康科普执行“国家法规＋平台规则＋账号资质＋审查样件”检查。
- 医疗内容先区分主体与发布场景，再分别检查平台准入、广告审查、线上诊疗、患者隐私、药品或器械销售资质；其中任何一项获准，都不能代替其他许可。
- 对非医疗养生机构的针刺等侵入性服务、处方药互联网广告、普通评论或私信中的个体诊断和开方、未经授权的患者资料，以及未经复核或未按要求标识的AI医疗内容执行硬停止。

## 工作方式

1. 整理已确认事实、可验证证据、合理推断、待确认信息和不可使用的主张。
2. 判断目标平台、受众任务、运营目标和现实转化路径。
3. 如果有两个或以上方向，只提交精简对比和推荐，由用户选择或要求重做。
4. 用户确认方向后，再生成完整执行包。
5. 给出发布测试指标、停止或调整条件，以及具体风险处理动作。

## 建议提供的资料

信息不完整也可以开始。资料越完整，输出越接近可直接执行。

```text
产品或服务：
已知资料与可证明的卖点：
大致内容框架：
目标平台：
运营目标：
目标人群与地区：
可用人员与出镜条件：
可拍摄场景与已有素材：
预算和周期：
禁止表达或合规限制：
```

## 直接使用

安装后可将下面内容发送给 Agent：

```text
使用 cross-platform-content-operator 处理以下运营需求。

产品或服务：[填写]
已知资料与可证明的卖点：[填写；没有则写“暂无”]
目标平台：[填写]
运营目标：[填写]
可用人员、场景、预算和周期：[填写]

请先区分事实、推断和待确认信息。缺少关键信息时一次只问我一个问题。
如果提供两个或以上方向，先给我精简对比，由我选择；我确认后再输出完整脚本、分镜、BGM、拍摄清单、发布素材、注意事项和测试指标。
```

## 完整执行包包含什么

根据任务需要输出：目标与受众、证据状态、平台定位、内容方向、标题、前三秒开场、逐段口播、逐镜头分镜、屏幕文字、封面、发布文案、CTA、评论引导、人员与道具、拍摄和剪辑说明、BGM规格、发布节奏、测试指标、审批事项及风险清单。

不会把所有字段机械地塞进简单请求；例如只要一条文案时，仅补充必要的假设和风险说明。

## 支持的 Agent

本仓库采用可移植的 Agent Skills 结构：根目录 `SKILL.md` 使用 `name` 和 `description` 元数据，详细方法按需存放在 `references/`。Codex、Claude Code、Cursor、CodeBuddy及其他实现 Agent Skills 的产品可读取核心内容；`agents/openai.yaml` 仅提供可选的 Codex 界面信息。

## Install on supported Agents

Ask your agent to run:

```bash
npx -y skills add lp941007/cross-platform-content-operator --skill cross-platform-content-operator --copy
```

This lets the open `skills` CLI detect the Agent that runs the command. To install for several supported Agents on the same machine, name their IDs explicitly, for example:

```bash
npx -y skills add lp941007/cross-platform-content-operator --skill cross-platform-content-operator --agent claude-code cursor codex --copy
```

Restart the Agent or start a new session if the skill does not appear immediately.

## Make an Agent associate the task with this Skill

Automatic activation depends on each Agent's Skill implementation. Use one of these methods, from least to most explicit.

### 1. Natural-language activation

The Skill metadata covers common Chinese and English operations terms. Ask normally, for example:

```text
帮我为这个产品制定抖音和小红书运营方案。先核对可证明卖点，多方案先让我选择，确认后再输出脚本、分镜、BGM和测试指标。
```

Typical association phrases include: `平台运营方案`, `抖音同城获客`, `小红书文案`, `视频号脚本`, `短视频选题`, `拍摄分镜`, `BGM`, `投流测试`, and `内容复盘`.

### 2. Explicit invocation

Use the Skill name when the task is important or the Agent did not activate it automatically:

```text
使用 cross-platform-content-operator 处理以下需求：
产品或服务：
已知资料与可证明卖点：
大致内容框架：
目标平台：
运营目标：
可用人员、场景、预算和周期：
```

In an Agent interface that supports a Skill picker or slash command, select `cross-platform-content-operator` before sending the request.

### 3. Project-level automatic association

Add this portable rule to the project's Agent instruction file, such as `AGENTS.md`, `CLAUDE.md`, or the equivalent file documented by that Agent:

```markdown
## Social-media operations

For any request involving social-media strategy, platform adaptation, content topics, copy, scripts, storyboards, BGM, publishing, paid promotion, acquisition, or performance review, use the installed `cross-platform-content-operator` Skill before drafting the answer. If multiple directions are proposed, present a compact comparison and wait for user selection before producing the full execution package. Preserve verified facts, label assumptions, and never guarantee traffic, leads, or sales.
```

This rule improves association inside that project. It cannot make an Agent use Skills if the product itself does not support the Agent Skills format.

## Install on WorkBuddy

WorkBuddy uses the same `SKILL.md`-based package structure, but it is not currently a named target in the `skills` CLI. Use WorkBuddy's native import instead:

1. Download this repository as a ZIP and extract it.
2. Open WorkBuddy's **Skills** page and choose **+ Add Skill**.
3. Import the entire `cross-platform-content-operator` folder. Keep `SKILL.md` and `references/` together.
4. Enable the skill, then restart WorkBuddy if it is not detected immediately.

After installation, either select the Skill in WorkBuddy's task bar or send:

```text
使用 cross-platform-content-operator，基于我提供的真实资料制定平台运营方案。信息不足时一次只问一个关键问题；多方案先让我选择，确认后再输出完整执行包。
```

For a project-level WorkBuddy/CodeBuddy setup, copy the entire folder to:

```text
.codebuddy/skills/cross-platform-content-operator/
```

## Manual installation for another Agent

If an Agent implements the Agent Skills specification but is not supported by the CLI, copy the entire repository folder into that Agent's documented skills directory. Do not copy `SKILL.md` alone because the workflow loads files from `references/`.

Compatibility means the Agent can load standard Agent Skills. It does not mean every AI product supports skills, nor that every Agent exposes the same tools.

## 更新 Skill

使用 `skills` CLI 安装的用户可以运行：

```bash
npx -y skills update cross-platform-content-operator
```

WorkBuddy 用户需要重新下载最新仓库 ZIP，并在技能管理页面重新导入或更新。更新前建议查看变更内容；第三方 Skill 会以用户授权的权限运行。

## 使用边界

- 不承诺爆款、排名、播放量、咨询、到店或成交。
- 不虚构产品能力、价格、证书、用户评价、案例或前后对比。
- 热门BGM、平台政策、投流设置和平台功能属于时效信息，使用前需实时核验。
- 医疗、健康、教育、金融等受监管内容必须先确认资质、审查要求和属地规则。
- 输出是运营决策与执行辅助，不替代法律、医疗、财务或平台官方审核。

## 仓库结构

```text
cross-platform-content-operator/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── intake-and-evidence.md
    ├── platform-adaptation.md
    ├── content-production.md
    ├── music-and-audio.md
    ├── testing-and-metrics.md
    ├── compliance.md
    ├── medical-content-rules.md
    └── output-contract.md
```
