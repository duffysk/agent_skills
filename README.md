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

## Installing a skill (Copilot CLI)

Copy a skill directory into your personal Copilot skills folder, then verify
with `/skills`:

```sh
cp -r bikepacking-planning ~/.copilot/skills/
```

Skills load at session start, so start a new session (or `/restart`) after
installing.
