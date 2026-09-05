# Grok Bot templates

Four focused Bots, with one optional workflow for choosing among them.

- [First Principles](first-principles/README.md): clarify the problem and challenge assumptions.
- [Product Ideation](product-ideation/README.md): choose what to build and how to test demand.
- [Red Flag](red-flag/README.md): review an existing plan, code change, or claim.
- [Garbage Collector](garbage-collector/README.md): remove unnecessary code and architecture.

## Use

Open a package and follow its public Bot link to add the published template. To configure a Bot from source, use its `PROFILE.md` and complete `skills/<name>/SKILL.md`. Inspect the saved instructions after setup. The files alone do not install a Bot or grant it tools, account access, or connections to other Bots.

For a compatible local skill loader, copy only the specific `skills/<name>/` directory you want into its configured skills root. Preserve the directory name and frontmatter identifier. Do not load all four into one Bot by default: First Principles includes Bot-specific always-on instructions.

The [Firstmate workflow](workflow/README.md) is optional. It delegates only when a specialist can help, checks the result, and stops when the task is done. The existing `grokcell-red-team` coordination skill and the standalone Red Flag Bot serve different scopes; installing one does not install the other.

## Evidence

Each package documents prepared cases, observed behavior, and limitations. Native observations were recorded during setup on September 4-5, 2026. They were not rerun as part of this source migration. Public share links were verified in those publication sessions; this release does not claim marketplace catalog admission.

Garbage Collector also includes [reproducible Python fixture checks](garbage-collector/eval/README.md). Those check example code, not the reasoning quality of a model.

## Maintained source

This directory is the maintained source for these four Bot packages and the shared workflow. Skill identifiers and instruction bodies were preserved during consolidation. Public templates are separate deployed snapshots; future source edits require a separate inspected publication step to update them.

Garbage Collector originated in [SyberLabs/grok-bot-aggressive-deletion](https://github.com/SyberLabs/grok-bot-aggressive-deletion), whose earlier source and evaluation history remain available. Future changes belong here. Local setup records, account identities, private transcripts, and draft social posts are not part of this package.
