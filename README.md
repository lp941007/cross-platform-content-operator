# Cross-Platform Content Operator

An evidence-based Agent Skill for creating truthful, executable, platform-specific content strategies, scripts, BGM plans, production workflows, and measurable growth tests.

It uses the portable Agent Skills layout: a root `SKILL.md` with `name` and `description` frontmatter plus on-demand files in `references/`. The optional `agents/openai.yaml` adds Codex UI metadata; other Agents can ignore it.

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
