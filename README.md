# agent_skills

Various skills for different personal activities, for use with the GitHub
Copilot CLI (and compatible agents).

## Structure

Skills are organised by type, one directory per skill, each containing a
`SKILL.md` with YAML front matter (`name`, `description`) and the skill body:

```
agent_skills/
├── README.md
└── <skill-type>/
    └── SKILL.md
```

## Skills

| Skill | Path | Description |
|-------|------|-------------|
| Bikepacking route planner | [`bikepacking-planning/SKILL.md`](bikepacking-planning/SKILL.md) | Plan multi-day European river/rail bikepacking routes for a group of 6 on loaded panniers — stages, distances, elevation profiles, GPX links, sightseeing, rail bookends, and an LLM-as-judge check. Outputs a Markdown plan file. |

## What is a skill?

A skill is a folder containing a `SKILL.md` file. The `SKILL.md` starts with a
YAML front-matter block declaring a `name` and a `description`, followed by the
instructions the agent should follow:

```markdown
---
name: my-skill
description: >-
  One or two sentences telling the agent WHEN to use this skill.
  Use "USE FOR: ..." and "DO NOT USE FOR: ..." to make matching precise.
---

# My Skill

The body: step-by-step guidance, constraints, output format, etc.
```

The agent reads the `description` to decide, automatically, whether a skill is
relevant to your request. A clear, specific `description` is the single most
important part of a skill.

## How to use these skills

### 1. Install a skill

Copy a skill directory into your personal Copilot CLI skills folder:

```sh
# Clone this repo (once)
git clone https://github.com/duffysk/agent_skills.git
cd agent_skills

# Install one skill...
cp -r bikepacking-planning ~/.copilot/skills/

# ...or install all skills at once
cp -r */ ~/.copilot/skills/
```

Skills are loaded at session start, so begin a **new session** (or run
`/restart`) after installing.

### 2. Verify it loaded

In the Copilot CLI:

- `/skills` — lists installed skills and lets you manage them.
- `/env` — shows everything loaded for the session (skills, MCP servers,
  instructions, etc.).

### 3. Use it

Just describe your task in natural language. The agent matches your request
against each skill's `description` and activates the relevant skill
automatically — you don't have to call it by name:

```
> Plan me a 5-day Drauradweg trip for our group of six.
```

If you want to force a specific skill, name it explicitly:

```
> Use the bikepacking-route-planner skill to compare the Main-Radweg and the Drauradweg.
```

## Adding a new skill

1. Create a new directory named after the skill type, e.g. `my-new-skill/`.
2. Add a `SKILL.md` with `name` + `description` front matter and the body.
3. Add a row to the **Skills** table above.
4. Commit and push.

### Tips for writing a good skill

- **Front-load the `description`** with concrete triggers: `USE FOR: ...` and
  `DO NOT USE FOR: ...`. This is what the agent matches on.
- **Be explicit about output** — format, file names, and where to save results.
- **Encode hard constraints** the agent must always respect.
- **Keep it self-contained** — the agent only sees `SKILL.md`, not this README.

## Keeping installed skills up to date

After pulling new changes, re-copy the updated skill(s) and start a new session:

```sh
git pull
cp -r bikepacking-planning ~/.copilot/skills/
```
