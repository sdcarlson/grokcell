# PROFILE

Private. Fill this once. Do not put real values in the public repo.

A Cell skill reads these slots. If a slot is empty, park and ask the mouth. Do not invent.

## Human

| Slot | Fill |
|---|---|
| HUMAN_NAME | |
| HUMAN_EMAIL | |
| HUMAN_PHONE | |
| HUMAN_CITY | |
| WORK_AUTH | e.g. US citizen, no sponsorship |
| RELOCATE | Yes or No, and any city rule |
| PRONOUNS | only if a form requires it |
| GENDER | only if a form requires it |
| RACE | only if a form requires it; leave blank if voluntary |
| SALARY_PRECEDENT | only a number you have already used. Do not rewrite up. Empty means park. |
| SPECIAL_CONSENTS | company-specific only, never a global default |

## School and proof

| Slot | Fill |
|---|---|
| DEGREE | |
| SCHOOL | |
| GRAD_DATE | |
| HIGH_SCHOOL | |
| HS_YEAR | the year you actually graduated. Do not guess. |
| LINKEDIN_URL | |
| SITE_URL | public work |
| PROOF_GITHUB | org or proof repo, not a personal handle you do not want as the proof link |

## Voice

| Slot | Fill |
|---|---|
| JOB_TITLE | public title for applications |
| STUDIO_TITLE | public title when speaking as the studio |
| ONE_LINE | one sentence. What you build. |
| ESSENCE | one sentence. How you work. |
| FORBIDDEN_TITLES | titles you will not use |

## Resume tracks

One PDF per apply. Pick by the req.

| Track id | File path | Use on |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

## Tracker

| Slot | Fill |
|---|---|
| TRACKER_URL | private list of submitted / skipped / parked. Not this repo. |
| PARKED_DOORS | doors you will not retry |
| SKIP_ATS | e.g. Ashby, Workday |
| SKIP_RULES | e.g. 1h+ take-home, clearance, wrong class year, transcript required |

## Cell owners (names, not UUIDs)

| Slot | Role |
|---|---|
| MOUTH | only bot the human talks to |
| DIRECTION | picks role, rail, resume track |
| SURFACE | opens the apply door, fills facts |
| WRITER | ChatGPT session for personal questions |
| HUMAN | the person who submits |

Do not add a fourth writer in the human's voice. Outreach lists stay separate from apply lists.

## Runtime

| Slot | Fill |
|---|---|
| TIMEZONE | for weekday routines |
| CHATGPT | writer owns the signed-in session |
| EMAIL_FOR_CODES | inbox the mouth reads for one-time apply codes |
| CODE_RULE | one code, one attempt. Never write codes into the tracker. |

## Form lock extras

Stop and ask the mouth on sexuality, transgender status, clearance, export control, or any legal question with no precedent in this file.
