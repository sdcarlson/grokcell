# Grok Cell skills

Reusable how-to files for a Federated Grok Cell: a small, role-locked set of Grok Bots with one mouth to the human.

This repo is the public playbook. Identity, emails, phones, tracker URLs, and bot UUIDs stay in [PROFILE.md](PROFILE.md). Copy that file, fill the slots, keep it private.

## What a Grok Cell skill is

A skill is how. A routine is when. Official Grok Bot docs: skill first, then a Test run (real work), then a routine. [docs.x.ai/grok-bot/skills-routines-and-automations](https://docs.x.ai/grok-bot/skills-routines-and-automations)

A Cell skill is a skill that also names owners and a park gate. It does not invent a new bot. It runs on bots you already have.

Cell laws (locked):

1. One mouth. The human talks to one coordinator. Specialists report to that mouth.
2. Two to four specialists per rail. Groups of 2-6 only when the handoff must be visible.
3. A new rail is a skill on an existing owner, not a new bot.
4. Personal and narrative fields go through a writer plus ChatGPT. No em dashes. One draft.
5. Draft and fill to the submit gate. The human submits unless the mouth already named a submit.
6. Park send, spend, publish, delete, and sign.
7. No Cursor Cloud Agent unless the mouth names it. Those spend the Cursor allowance, not the Grok Bot bucket.
8. No generic empty helper. Leave unnamed bots unnamed.
9. Sidebar Sections group work. Do not add names to organize.

Spawn test (all three must be true before you create a bot):

- the rail has been daily for several days
- the current owner's description would become two jobs
- a one-paragraph law can be written

If any fail, keep the skill.

## What is in here

| Path | What it is |
|---|---|
| [PROFILE.md](PROFILE.md) | Slots the adopter fills. Not committed with real values. |
| [skills/federated-cell/SKILL.md](skills/federated-cell/SKILL.md) | When to form a Cell, spawn test, do-alone vs park. |
| [skills/hunt-apply/SKILL.md](skills/hunt-apply/SKILL.md) | Three apply rails: LinkedIn Easy Apply, Greenhouse, YC Work at a Startup. ChatGPT for personal questions. Stop at submit. |
| [routines/prepare-then-stop.md](routines/prepare-then-stop.md) | Weekday prepare-then-stop template. Silence is valid. |

Only skills that have been run, or Cell laws already locked, live here. No invented rails.

## How to load

1. Fill a private copy of PROFILE.md.
2. Paste the skill body into Grok Bot (Plugins, or a saved skill). Point it at your PROFILE, not this public file.
3. Run one real task. Correct it. Then a Test run. Then the routine on the mouth bot.
4. Do not schedule a demo. A test run does real work.

## What this is not

Not a swarm. Not an applicant-side apply factory. Official Talent Scout is employer-side. The pattern that exists: research, draft, fill, stop at the gate.

Bots share one computer. They are not a security boundary. [docs.x.ai/grok-bot/approvals-security-and-privacy](https://docs.x.ai/grok-bot/approvals-security-and-privacy)
