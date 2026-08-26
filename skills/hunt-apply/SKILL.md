---
name: Hunt apply
description: >-
  Use when running a job application on LinkedIn Easy Apply, Greenhouse, or
  Y Combinator Work at a Startup, or when a form asks a personal, why-us,
  cover, or essay question.
---
# Hunt apply

Draft and fill to the submit gate. Do not freehand narrative. Every personal question goes through ChatGPT (no em dashes). The human submits unless the mouth already named a submit.

Fill [PROFILE.md](../../PROFILE.md). This skill has no applicant identity.

## Owners

| Stage | Owner slot | Does | Does not |
|---|---|---|---|
| Direction | DIRECTION | pick role, rail, resume track | fill, send |
| Surface | SURFACE | open the door, fill facts from PROFILE | freehand covers, click Submit unless named |
| Words | WRITER | ChatGPT on its signed-in session for personal questions | post, save, submit |
| Mouth + tape | MOUTH | human chat, email codes, tracker | spawn a new bot, launch Cloud Agents |
| Submit | HUMAN | captcha, new legal, final Submit | |

Do not add a fourth writer in the human's voice. Apply outreach and academic outreach stay on separate lists.

## Identity

Read HUMAN_*, school, proof, voice, and form lock from PROFILE. Do not invent. If a required field has no slot, park and ask the mouth.

## Resume tracks

Read the track table in PROFILE. Pick by the req. One PDF per apply.

## Form lock

Answer only what PROFILE already states (work auth, veteran/disability if present, relocate, pronouns/gender/race when required, salary only if SALARY_PRECEDENT is filled). Do not rewrite salary up.

SPECIAL_CONSENTS are company-specific. Not a global default.

Stop and ask the mouth on sexuality, transgender status, clearance, export control, or any legal question with no PROFILE precedent.

## Rails (pick one per job)

Skip the door if it is in SKIP_ATS, matches SKIP_RULES, or is already in the tracker. Do not retry PARKED_DOORS. Do not reuse one-time apply codes.

Check TRACKER_URL before opening.

### 1. LinkedIn Easy Apply

1. Open the posting on LinkedIn. Confirm Easy Apply (not a long external ATS).
2. Upload the matching resume.
3. Fill identity + form lock from PROFILE.
4. If a personal / why-us / cover field appears, park and send the prompt below to WRITER.
5. Paste the writer's ChatGPT text. Do not rewrite it.
6. Stop at Submit, captcha, or Cloudflare. If Cloudflare, park and tell the mouth. Do not hammer it.

### 2. Greenhouse

1. Prefer `job-boards.greenhouse.io/...` or `gh_jid=` on the company careers page.
2. Upload the matching resume. Fill identity + form lock from PROFILE.
3. Personal questions: park, WRITER, ChatGPT (same prompt). Respect character caps (cut, do not squeeze with em dashes).
4. Email verification: mouth reads EMAIL_FOR_CODES, sends the code once. One code, one attempt. If two codes fail, park. Do not guess. Do not put codes in the tracker.
5. Stop at Submit unless the mouth named a submit. After a real confirm, keep the confirmation URL.

### 3. Y Combinator Work at a Startup

1. Use the signed-in session on `https://www.workatastartup.com`.
2. Early-career / new-grad engineering only unless PROFILE says otherwise. No senior seats.
3. Apply on the company job page. Upload the matching resume. Fill identity + form lock.
4. YC written fields (why this company, why this role, anything personal) always go through WRITER then ChatGPT. Do not freehand. Do not spawn a YC bot.
5. Stop at Submit unless named. If login or 2FA, stop and tell the mouth.

## ChatGPT prompt (WRITER owns the session)

WRITER opens ChatGPT on the shared computer. SURFACE does not type this itself.

```
Write as {HUMAN_NAME} applying to [company] for [exact role].
Resume track: [track id]. Proof: {SITE_URL} and {PROOF_GITHUB}
Essence: {ESSENCE}
Jobs title: {JOB_TITLE}.
Question: [paste the form question exactly]
Hard limit: [N characters or "short why-us, 2-4 sentences"]
Rules: everyday words, contractions, short sentences. No em dashes. No "passionate." No "excited to." No thought-leadership. One draft, not three options.
```

Short why-us (Easy Apply / one box): 2-4 sentences. Long essays (YC, Greenhouse written): still one draft, still this prompt, still no em dashes.

## Per job (do this, in order)

1. DIRECTION names company, exact role, rail, resume track, posting URL.
2. MOUTH checks the tracker. Duplicate, skip.
3. SURFACE opens the rail and fills facts only.
4. Personal field appears: WRITER runs the ChatGPT prompt. SURFACE pastes.
5. Stop at Submit / captcha / new legal / Cloudflare / second failed code.
6. On confirm, skip, or park: MOUTH writes the tracker row (local time, posting URL, resume track, confirmation URL). Never write codes there.

## Park vs send

**Do alone:** draft, fill facts, summarize, research, ChatGPT copy, tracker row.

**Park:** Submit, Connect, InMail, spend, delete, sign, any new legal, captcha, Cloudflare, a second failed one-time code.

## Red flags (stop)

- Freehanding a why-us or cover
- Opening a SKIP_ATS door "just this once"
- Retrying a parked code-gate
- Reusing a one-time apply code
- Uploading the wrong proof GitHub
- Guessing HS_YEAR or relocate
- Spawning a Greenhouse bot, YC bot, or a fourth writer
- Launching a Cloud Agent unless the mouth named it
- Clicking Submit because the form is almost done

## Tracker row

Company, exact role, rail (Easy Apply / Greenhouse / YC), posting URL, local time, resume track, submitted / skipped / parked, confirmation URL if any. No codes.
