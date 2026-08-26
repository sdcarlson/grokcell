# Prepare-then-stop (weekday)

Template for a Grok Bot routine on the mouth bot. Skill is how. Routine is when.

Official: a test run performs real work. Create a routine only when retries and failure cases are defined. Include a no-data policy. [docs.x.ai/grok-bot/skills-routines-and-automations](https://docs.x.ai/grok-bot/skills-routines-and-automations)

This is generalized from a Hunt weekday prepare routine. Same shape works for any Cell rail that should leave a prepared slate and not act.

## Schedule

`0 9 * * 1-5` in the human's TIMEZONE (weekdays 9:00). Do not use @daily (midnight) or an unbounded hourly.

## Prompt to paste (mouth bot)

Replace slot names from PROFILE.

```
Weekday prepare-then-stop. You are {MOUTH}. Run the Hunt apply skill. Do not submit.

Goal: leave the human a prepared slate, or stay silent if there is nothing new.

1. Read the Hunt apply skill. Follow it. Do not spawn bots. Do not launch Cloud Agents.
2. Check {TRACKER_URL} first. Skip anything already submitted, skipped, or parked. Do not retry {PARKED_DOORS}. Do not reuse one-time apply codes.
3. Ask {DIRECTION} for a short list on the three rails only: LinkedIn Easy Apply, Greenhouse, Y Combinator Work at a Startup. Honor {SKIP_ATS} and {SKIP_RULES}.
4. For each pick, have {SURFACE} open the door and fill facts only. Personal / why-us / cover / essay fields go to {WRITER}, who writes them in ChatGPT (no em dashes). Paste the writer's text. Do not freehand.
5. Stop at Submit, captcha, Cloudflare, a new legal question, or a second failed one-time code. Codes come from {EMAIL_FOR_CODES}; one code, one attempt; never write codes into the tracker.
6. Tell the human only when there is a prepared slate (company, role, rail, resume track, parked-at-submit) or a real blocker. Silence is valid. Never manufacture an update to fill the slot.
7. After a real confirm, skip, or park during this run, update the tracker (local times, posting URL, resume track, confirmation URL). No codes.

If the rail is stood down or the human has not opened a new count, stay quiet.
```

## Install

1. Prove the skill once by hand.
2. Test run. A test run is real work.
3. Create the routine on {MOUTH}, not on a specialist.
4. Cap: 50 routines per bot. Keep a no-data policy.

## What this routine must not do

- Submit
- Spawn
- Launch a Cloud Agent
- Write secrets or codes into a tracker
- Ping the human when nothing changed
