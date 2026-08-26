<p align="center">
  <img src="https://i.imgur.com/OnqBQbn.png" alt="Grok Cell" width="620">
</p>

<h1 align="center">GrokCell</h1>

Four skills for a Grok Bot mission cell: decide whether structure is needed, recon before commitment, build the smallest coherent artifact, restore what broke.

## Layout

Each skill is a directory whose name matches its frontmatter `name:`, containing a single `SKILL.md`:

```
grokcell-oda/SKILL.md
grokcell-recon/SKILL.md
grokcell-forge/SKILL.md
grokcell-recovery-repair/SKILL.md
```

## Install

Copy the skill directories (not this file) into a Grok Bot or Cursor skills root:

```bash
# user-level: available in every project
cp -r grokcell-*/ ~/.cursor/skills/

# project-level: available only in that repo
cp -r grokcell-*/ /path/to/project/.cursor/skills/
```

Then `/grokcell-oda`, `/grokcell-recon`, `/grokcell-forge`, `/grokcell-recovery-repair`. Skills also load when a request matches their `description:`.

## The skills

| Skill | Answers |
|---|---|
| `grokcell-oda` | Should this be a new bot, a skill on an existing owner, or nothing? |
| `grokcell-recon` | What must we understand before committing? |
| `grokcell-forge` | What is the smallest coherent thing that causes the effect? |
| `grokcell-recovery-repair` | What broke, and what is the safest way back? |

## Conventions

Every skill opens with a **Fast path** (stop at the first rung that holds) and closes with **Done when**.

Shared ordering when uncertain:

> **INTENT → EFFECT → EVIDENCE → TEMPO → LEARNING → CEREMONY**
