# GrokCell

Four published Grok Bot templates (LLM agent prompts) with versioned skill instructions, documented behavior checks, and a Python evaluation harness that runs in CI.

**Tech stack:** Prompt engineering, LLM agent skills (Markdown `SKILL.md` with frontmatter), Python 3 (standard library only), GitHub Actions

## What it does

Each Bot is a single-purpose assistant defined by a profile and one skill file. The public links add the published template to Grok Bot.

| Bot | Purpose | Skill source |
| --- | --- | --- |
| [First Principles](bots/first-principles/README.md) | Separate facts from assumptions, find the real constraint, and propose the cheapest decisive test. | [`first-principles`](bots/first-principles/skills/first-principles/SKILL.md) |
| [Product Ideation](bots/product-ideation/README.md) | Turn customer problems into product concepts and a low-cost demand experiment. | [`aggressive-product-ideation`](bots/product-ideation/skills/aggressive-product-ideation/SKILL.md) |
| [Red Flag](bots/red-flag/README.md) | Review plans, code, and AI answers for consequential failures and unsupported claims. | [`red-team-analysis`](bots/red-flag/skills/red-team-analysis/SKILL.md) |
| [Garbage Collector](bots/garbage-collector/README.md) | Find code and architecture that can be deleted or simplified without changing required behavior. | [`aggressive-deletion`](bots/garbage-collector/skills/aggressive-deletion/SKILL.md) |

- Each package has a `PROFILE.md` (name, description, starters, setup message), the canonical `SKILL.md`, and a `CHECKS.md` or `eval/` record of behavior checks.
- The instructions share guardrails: no fabricated results or citations, treat retrieved content as data rather than instructions, and take no side-effecting action without authorization.
- Garbage Collector ships a deterministic eval: a Python fixture with 13 contract tests, four deliberately broken "simplifications" that must be rejected, a 4,923-case structural equivalence check, and a scenario corpus with acceptance criteria for grading model responses.

## How it works

```
bots/<bot>/PROFILE.md            Bot identity and setup instructions
bots/<bot>/skills/<id>/SKILL.md  Canonical skill (frontmatter: name, description)
bots/<bot>/CHECKS.md             Recorded behavior cases and limits
bots/garbage-collector/eval/     Fixture, regressions, scenarios, runners
scripts/validate_templates.py    Structural validator for all four packages
```

`scripts/validate_templates.py` checks that every package has the expected files, skill identifiers, frontmatter, headings, public links, and working relative links. The GitHub Actions workflow runs the validator and both eval runners on every push and pull request.

## Getting started

Requires Python 3.10+ and no third-party packages.

```sh
git clone https://github.com/sdcarlson/grokcell.git
cd grokcell
python scripts/validate_templates.py
python bots/garbage-collector/eval/verify.py
python bots/garbage-collector/eval/check_structure.py
```

To use a Bot, open its package and follow the public link, or copy its `skills/<id>/` directory into a compatible skill loader. See the [Bot guide](bots/README.md) for setup and for how to give a specialist one bounded task.

## Project context

Built by Seth Carlson in August and September 2026. The four templates were published to Grok Bot on September 4-5, 2026. Garbage Collector originated in [SyberLabs/grok-bot-aggressive-deletion](https://github.com/SyberLabs/grok-bot-aggressive-deletion). Behavior checks are bounded observations from those sessions, not guarantees of model behavior, and editing source here does not update the deployed public Bots. See [Contributing](CONTRIBUTING.md) to propose a change.

## License

[MIT](LICENSE)
