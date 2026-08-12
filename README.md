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

## Install on WorkBuddy

WorkBuddy uses the same `SKILL.md`-based package structure, but it is not currently a named target in the `skills` CLI. Use WorkBuddy's native import instead:

1. Download this repository as a ZIP and extract it.
2. Open WorkBuddy's **Skills** page and choose **+ Add Skill**.
3. Import the entire `cross-platform-content-operator` folder. Keep `SKILL.md` and `references/` together.
4. Enable the skill, then restart WorkBuddy if it is not detected immediately.

For a project-level WorkBuddy/CodeBuddy setup, copy the entire folder to:

```text
.codebuddy/skills/cross-platform-content-operator/
```

## Manual installation for another Agent

If an Agent implements the Agent Skills specification but is not supported by the CLI, copy the entire repository folder into that Agent's documented skills directory. Do not copy `SKILL.md` alone because the workflow loads files from `references/`.

Compatibility means the Agent can load standard Agent Skills. It does not mean every AI product supports skills, nor that every Agent exposes the same tools.
