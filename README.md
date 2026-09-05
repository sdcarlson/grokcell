<p align="center">
  <img src="https://i.imgur.com/OnqBQbn.png" alt="Grok Cell" width="620">
</p>

<h1 align="center">GrokCell</h1>

Reusable Grok Bot templates and skills for problem-solving, product ideas, review, and code simplification.

## Bots

- [First Principles](bots/first-principles/README.md) - clarify the problem, question assumptions, and choose a next step.
- [Product Ideation](bots/product-ideation/README.md) - turn customer problems into ideas and inexpensive tests.
- [Red Flag](bots/red-flag/README.md) - check plans, code, and AI answers for consequential failures and unsupported claims.
- [Garbage Collector](bots/garbage-collector/README.md) - simplify code while preserving required behavior.

Each package includes the source instructions, a profile, a public Bot link, and documented behavior checks. These are experiments with bounded test evidence, not guarantees of model behavior. The public template retains the name **Aggressive Product Ideation**.

Start with the [bot guide](bots/README.md). The optional [Firstmate workflow](bots/workflow/README.md) helps choose a useful specialist and check its answer; using all four is not required.

## Coordination skills

The original fifteen `grokcell-*` skills cover coordination, research, construction, recovery, review, and learning. They remain separate from the four standalone Bot packages below `bots/`.

## Layout

Each skill is a directory whose name matches its frontmatter `name:`, containing a single `SKILL.md`:

```
grokcell-oda/SKILL.md
grokcell-mission-command/SKILL.md
...
```

## Install

Copy the skill directories (not `_originals/` or this file) into a skills root:

```bash
# user-level — available in every project
cp -r grokcell-*/ ~/.claude/skills/

# project-level — available only in that repo
cp -r grokcell-*/ /path/to/project/.claude/skills/
```

Then `/grokcell-oda`, `/grokcell-recon`, and so on. Skills also load automatically when a request matches their `description:`.

## The skills

**⚪ Doctrine** — the substrate everything else runs on

| Skill | Answers |
|---|---|
| `grokcell-oda` | Should this be a new bot, a skill on an existing owner, or nothing? |
| `grokcell-command-and-control` | How does the federation stay coherent while cells act independently? |
| `grokcell-chromatic-doctrine` | What kind of work does this problem require? |
| `grokcell-black-protocol` | Normal control has become unsafe — what stops, what is preserved? |

**🟡 Command** — intent, organization, shared reality

| Skill | Answers |
|---|---|
| `grokcell-mission-command` | Why, what success looks like, who may decide what |
| `grokcell-force-generation` | What is the smallest organization that can produce this effect? |
| `grokcell-common-operational-picture` | What is happening now, and who needs to know? |

**🔴 Know** — reduce uncertainty, challenge confidence

| Skill | Answers |
|---|---|
| `grokcell-recon` | What must we understand before committing? |
| `grokcell-red-team` | What if the frame, not the implementation, is wrong? |

**🔵 Make · 🟢 Restore** — build and keep working

| Skill | Answers |
|---|---|
| `grokcell-forge` | What is the smallest coherent thing that causes the effect? |
| `grokcell-recovery-repair` | What broke, how far did it spread, what is the safest way back? |
| `grokcell-sustainment` | What must stay healthy so recovery stays rare? |

**🟣 Learn** — turn experience into capability

| Skill | Answers |
|---|---|
| `grokcell-after-action` | What should change because of what actually happened? |
| `grokcell-routine-compiler` | What should we stop reasoning through from scratch? |
| `grokcell-capability-registry` | Who or what can reliably do this right now? |

## Conventions

Every skill opens with a **Fast path** — a ladder where you stop at the first rung that holds, so the common case exits in a few lines — and closes with **Done when**, stating verifiable completion. In between: a numbered Constitution of invariants, and an anti-patterns table naming the failure modes.

Shared ordering when uncertain:

> **INTENT → EFFECT → EVIDENCE → TEMPO → ORGANIZATIONAL LEARNING → CEREMONY**
