---
name: grokcell-routine-compiler
description: >-
  Use when the same work keeps recurring — repeated verification, recovery,
  setup, lookup, routing, or coordination — and you are deciding whether to
  encode it as a note, checklist, template, assertion, script, tool, automation,
  or architectural invariant, and how much autonomy it has earned.
---
# GrokCell Routine Compiler

🟣 Purple. Procedural crystallization and natural infrastructure. Version 1.0.0.

**What recurring work should the federation stop reasoning through from scratch?**

The goal is not maximum automation. The goal is to **move stable repeated work out of expensive reasoning while preserving judgment wherever terrain still demands it.**

## Fast path

Stop at the first rung that holds. Most candidates stop at 1 or 2.

1. **Not actually recurring, or terrain still varies** → keep judgment. Nothing to compile.
2. **Recurring knowledge lookup** → an index entry or artifact-intelligence note. Done.
3. **Stable structure, judgment still central** → checklist, template, or skill rule.
4. **An invariant property that can be mechanically tested** → an assertion. Highest-value common case.
5. **Fixed transformation, bounded environment, detectable failure** → script or workflow.
6. **High frequency, safe action, recognizable trigger, minimal judgment** → tool or automation — earned through shadow → advisory → guarded → autonomous.
7. **Universal, stable, and safety-critical** → architectural invariant. Highest bar.

**The test before any of this:** *would I still build this if I knew there were only three future uses?* If no, reconsider.

## 1. Infrastructure must pay rent

`RoutineValue = ExpectedReuse × SavingsPerUse × Reliability − BuildCost − MaintenanceCost − RigidityCost`

Compile when this is positive with enough confidence to act.

`BreakEvenUses = (BuildCost + ExpectedMaintenance) ÷ (ManualCostPerUse − RoutineCostPerUse)`. Expected future uses below break-even → do not compile deeply.

Infrastructure emerges from real work. It is never designed speculatively in advance:

```
DO MISSION → NOTICE RECURRING FRICTION → COMPRESS PATTERN
  → BUILD SMALL INFRASTRUCTURE → FUTURE MISSIONS GET CHEAPER
```

**Maintenance is a real obligation:** version drift, tool and API changes, testing, monitoring, repair, documentation. A routine that saves two minutes and needs constant maintenance is negative leverage.

**Rigidity is a real cost:** `RigidityCost = P(terrain changes) × Cost(routine applies incorrectly)`. Compiled behavior removes freedom — sometimes desirable, sometimes the cause of the next failure.

## 2. Repetition ≠ compilability

Two similar actions do not define a stable procedure. Repeated work may still need contextual judgment, creative synthesis, or high-dimensional reasoning against changing terrain.

**Eligibility test.** Has this recurred? Is the trigger recognizable? Are inputs legible? Is the success condition stable? Is behavior similar across cases? Is judgment limited enough? Can failure be detected? Is it reversible or containable? Will it be used again?

Several *no* answers → keep it as judgment.

A repetitive activity is still a bad candidate if it changes every mission, error consequence is high, verification is poor, frequency is low, or automation is expensive. **Resist automation theater.**

| Stability | Encoding |
|---|---|
| STABLE | may justify rigid encoding |
| SLOWLY CHANGING | moderate |
| VOLATILE / UNKNOWN | keep it soft |

| Variability | Encoding |
|---|---|
| LOW — same transformation every time | automation / tool |
| MEDIUM — fixed skeleton + contextual choices | skill, template, or workflow + judgment |
| HIGH — substantial reasoning each time | memory or lesson only |

## 3. The compilation ladder

Prefer the **least rigid representation that removes meaningful repeated work.**

```
0 MEMORY → 1 INDEXED KNOWLEDGE → 2 CHECKLIST → 3 TEMPLATE → 4 SKILL RULE
  → 5 ASSERTION/TEST → 6 SCRIPT/WORKFLOW → 7 TOOL → 8 AUTOMATION
  → 9 ARCHITECTURAL INVARIANT
```

Higher is more powerful, more rigid, more expensive.

*"Remember API X requires header Y"* needs an artifact-intelligence entry, not a service. *"Every deployment requires the same eleven deterministic checks"* deserves an automated assertion suite.

| Type | Use when |
|---|---|
| **Checklist** | procedure stable but judgment still central — prevents omission without constraining decisions |
| **Template** | output structure repeats, content stays contextual (recon packet, incident closeout, verification request) |
| **Skill rule** | recurring reasoning principle that cannot be made deterministic — *"prefer current executable artifacts over stale documentation during repository Recon"* |
| **Assertion** | a property should always hold and can be mechanically tested (*one active task owner*). Especially high value: it removes future assurance cost |
| **Script** | fixed transformation, bounded environment, clear failure. Keep small |
| **Workflow** | multiple deterministic steps with state transitions and dependencies. Must expose state to OpsGraph |
| **Tool** | reusable capability, several invocation contexts, stable I/O contract. Purple specifies; Blue builds |
| **Automation** | recognizable trigger, safe action, high repetition, minimal judgment. Demands idempotency, permissions, failure handling, monitoring, stop conditions |
| **Architectural invariant** | instead of telling agents *"remember not to create two owners,"* make two simultaneous owners **impossible**. Universal, stable rules only |

**Whenever a rule is truly invariant, prefer enforced structure over repeated instruction.** That removes cognitive burden from every future mission.

## 4. The judgment boundary

The most important compilation decision: **which parts are deterministic, and which still require reasoning?**

```
INCIDENT
  collect logs         → deterministic
  identify anomaly     → partially automatable
  determine root cause → judgment
  select repair        → judgment
  execute rollback     → deterministic once authorized
```

Do not automate a whole process because parts of it repeat. The preferred architecture is:

```
DETERMINISTIC PREPARATION → AGENT JUDGMENT → DETERMINISTIC EXECUTION
```

This usually produces more leverage than trying to eliminate the agent.

**Isolate the invariant core, not the surface sequence.** A repeated Recon process of *search README → search code → inspect runtime → compare* has an invariant core of *compare declared behavior against executable evidence*. Compile the principle, not the steps. Keep the variable context (which API matters, which claim matters, which artifact is authoritative) outside the routine — **routine prepares evidence, agent interprets it**.

**Judgment points are explicit**, never disguised: question, evidence, options, downstream effect. The routine stops, the agent decides, the routine resumes. This is often the optimal agent/infrastructure interface.

## 5. Candidates

A routine candidate records: repeated behavior, trigger, inputs, outputs, current actor and method, occurrences, frequency, average cost, judgment required, variability, failure modes, consequence, expected reuse, candidate encoding — plus its source lessons.

Any color may emit candidates; **Purple owns compilation judgment**.

| Color | Typical candidates |
|---|---|
| 🔴 | source validation, repository inspection, assumption checks, verification procedures |
| 🔵 | artifact transformation, scaffolding, build steps, integration patterns |
| 🟢 | health checks, containment, rollback, recovery, diagnostics |
| 🟡 | routing, formation decisions, escalation deduplication, state transitions |
| 🟣 | lesson routing, indexing, capability updates |

**Compile behavior, not conversation.** Not *"agent said X, then agent said Y"* — but trigger, input, transformation, decision condition, output, failure behavior. A routine needs operational semantics.

**Candidate classes** suggest different outputs: KNOWLEDGE (repository index), PROCEDURE (bootstrap script), VALIDATION (automated assertion — highest value), TRANSFORMATION (deterministic converter), RECOVERY (runbook or script, depth scaled to consequence), ROUTING (a Force Generation heuristic, not necessarily code), COORDINATION (an event-driven COP routing rule), INFRASTRUCTURE (standard mission bootstrap).

**Mining:** OpsGraph history reveals recurring task subgraphs (`A → B → C → verification`) that may compile into workflows, and recurring cross-color patterns (🔴 recon → 🔵 probe → 🔴 verify for unfamiliar APIs) that may compile into **mission templates** rather than programs. Repeated sequence is candidate evidence, not approval.

**Search before building.** Check existing routines, tools, skills, templates. Reuse, extend, or merge rather than creating parallel infrastructure.

## 6. Routine contract

Every compiled artifact defines: purpose, source lessons, trigger, applicability, preconditions, inputs, outputs, authority, side effects, deterministic parts, judgment points, failure states, stop conditions, rollback, verification, monitoring, owner, maintenance, and `deprecate_when`.

**Applicability boundary is mandatory — both directions.** Not *"always use routine X"* but *"use X for repository initialization when schema version ≥ 3 and no custom migration is present."*

**Preconditions fail closed.** If required state is not established, the routine does not guess — it returns *needs judgment*. Forcing a procedure into mismatched terrain is worse than stopping.

**A premium routine knows when not to run.** Abstention returns status, reason, and required resolution. Abstention preserves both safety and adaptability.

**Authority:** may read / may write / may execute / approval required / prohibited. **Automation never creates its own authority.**

**Side effects** are classified NONE / LOCAL / SHARED_INTERNAL / EXTERNAL / IRREVERSIBLE — higher consequence, stronger gating. Where meaningful state is mutated, define a rollback path or declare NON-REVERSIBLE and require matching authority.

**Idempotency** is explicit wherever a routine may repeat — automations, retries, recovery, external APIs, state mutation.

**Stop conditions** are mandatory. Never "retry forever." Retry three times then escalate, or continue until condition X.

**Observability:** every autonomous routine exposes invocation, inputs, result, failure, version. **No invisible automation.** Events: `ROUTINE_EXECUTED`, `ROUTINE_ABSTAINED` (reason, unresolved condition, requested capability), `ROUTINE_FAILED` (stage, failure class, affected state, recovery required).

## 7. Earning autonomy

| Mode | Behavior |
|---|---|
| **Shadow** | routine recommends but does not execute; compare against agent decisions |
| **Advisory** | routine prepares a recommendation, agent approves — a valid *permanent* architecture |
| **Guarded** | routine handles known cases, escalates uncertain or high-risk ones — often better than full autonomy |
| **Autonomous** | independent execution inside defined authority; requires stable input domain, deterministic behavior, bounded failure, strong monitoring, available rollback, sufficient evidence |

| Maturity | Meaning |
|---|---|
| R0 CANDIDATE | pattern observed, no durable procedure |
| R1 DOCUMENTED | checklist, template, or skill rule |
| R2 ASSISTED | prepares inputs, evidence, recommendation; agent executes |
| R3 GUARDED | handles known cases, escalates uncertainty |
| R4 AUTONOMOUS | executes independently within authority, monitored |
| R5 INFRASTRUCTURAL | embedded in architecture; agents no longer perceive it as a routine |

**Promotion** requires repeated successful execution, Sentinel evidence, low failure rate, stable applicability, viable maintenance. Never promote because the routine merely exists.

**Demotion is normal.** Terrain changes, false positives rise, incidents occur, assumptions are invalidated → R4 → R3, or disable. **Autonomy is reversible.**

### Assurance scales with blast radius

`AutomationRisk = FailureImpact × ExecutionFrequency × PropagationScope`

A defect executed once is cheap; executed ten thousand times it is systemic. **Repetition amplifies defects**, so required assurance rises with frequency, autonomy, and propagation. A one-click local helper needs light verification; an autonomous federation-wide state mutation needs deep assurance, clear contracts, failure containment, rollback, and monitoring before it runs unattended.

**Sentinel asks:** Does it perform the intended behavior? Does it abstain outside applicability? Is failure bounded? Does it preserve authority? Does repetition amplify hidden defects?

**Failure classes** each have a different remedy: TRIGGER (ran when it should not), INPUT, LOGIC, ENVIRONMENT (terrain changed), AUTHORITY, SIDE-EFFECT, MONITORING (failed silently).

**False positives** — acting when it should not — are especially dangerous for recovery, state mutation, command routing, and external actions. **False negatives** cost efficiency or resilience. Which matters more depends on consequence. **Safe default:** abstain when applicability is uncertain and consequence is high; best-effort output is acceptable for low-risk informational routines.

## 8. Lifecycle

**Versioned.** `routine v4 PASS` does not establish `v5 PASS`. **Verification is version-bound.**

**Dependencies tracked** (tools, interfaces, schemas, assumptions, services) so Artifact Intelligence can map downstream impact. When a dependency version changes, an assumption is invalidated, an interface changes, or a tool disappears → mark **STALE**, and stop autonomous execution where consequence warrants.

**Health states:** CANDIDATE → VALIDATING → ACTIVE → DEGRADED / STALE / DISABLED → DEPRECATED → RETIRED.

**Ownership** is a locus, not a permanent agent — Purple, Sustainment, Sentinel, Forge, Green, or Yellow depending on function. Ownership means responsibility for validity, maintenance, and deprecation. It does **not** mean manual involvement in every execution. **Unowned infrastructure rots.**

**Retire** when unused, terrain changed, superseded, maintenance exceeds savings, or architecture eliminated the need. Where consumers exist: mark deprecated → identify consumers → provide a replacement → migrate → retire, preserving history. **Do not preserve automations because they were once clever.** Organizational forgetting is part of healthy compilation.

**Merge** two routines only when trigger, effect, and semantics genuinely converge — and avoid creating giant universal routines. Sometimes duplication is cheaper than a dangerous abstraction.

**Overgeneralization** — one generic "handle all failures" automation — loses to bounded lease recovery, bounded cache reset, bounded session renewal. Narrow reliable routines beat universal brittle machinery. **Undergeneralization** — one script per nearly identical case — wastes maintenance when a stable parameterized transformation exists.

**Prefer composability:** clear trigger, clear input, clear output, bounded state. A chain (`detect stale lease → classify owner state → reclaim if safe → register event`) stays separately testable. Complex repeated processes compile into a small workflow graph, not one monolithic black box.

## 9. Interfaces

| System | Boundary |
|---|---|
| **AAR** | says *what should change*; Routine Compiler asks *can that change become reusable procedure?* Keep them distinct |
| **Blue / Forge** | builds executable tooling from Purple's contract. **Purple is not the implementation team** |
| **Red / Sentinel** | verifies assumptions, external semantics, and routine safety before and after compilation |
| **Green** | supplies failure patterns, recovery procedures, health checks; owns degraded-state semantics. Recovery automation stays conservative |
| **Yellow** | repeated command friction may become a decision rule, authority default, or routing rule — but Mission Command owns policy. Purple proposes |
| **OpsGraph** | compiled workflows register state, ownership, outputs, failure. **A routine must never become an invisible parallel control plane** |
| **Capability Registry** | validated routines become capability providers with qualification, cost, latency, readiness |
| **Force Generation** | asks whether any required capability can be supplied by routine instead of Grok. This is direct force multiplication |
| **Artifact Intelligence** | indexes purpose, version, capability, dependencies, consumers, validation — otherwise routines become invisible infrastructure |
| **Sustainment** | owns operational health after deployment: availability, version compatibility, drift. **No routine is free forever** |

## 10. Force multiplication

**Agent capacity released** is the point — track agent-hours avoided, context avoided, handoffs avoided, Sentinel effort avoided.

**Coordination compression** is often larger than execution savings. Before: Blue asks Red → Red checks → Red reports → Blue continues. After: an automatic assertion. One routine removed a task, a handoff, a message, and a context switch.

**Cognitive compression** turns many repeated reasoning steps into one reusable primitive — effectively a new instruction in the federation's organizational language. Capability then compounds: mission N creates X; N+1 uses X and creates Y; N+2 reasons in terms of X + Y.

**Maintain a small, high-value portfolio** — usage, savings, reliability, maintenance, last validation. **Do not optimize for routine count.**

## 11. Budget

Routine compilation should normally consume **0–10%** of current mission effort, and often **0%** during execution with Purple work following afterward.

Compile mid-mission only if the repeated work is blocking the current mission, a small tool solves the immediate problem, or future reuse is highly likely. **Otherwise finish the mission first.**

## 12. Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| **Automate everything** | Reasoning is not waste when uncertainty is genuine |
| **One repeat = routine** | One repetition may be coincidence |
| **Automating a broken process** | Do not make a bad procedure faster; establish the procedure's value first |
| **Giant universal tool** | A platform built to solve a narrow recurring task |
| **Hidden judgment** | Disguising agent cognition as deterministic infrastructure |
| **Full autonomy too early** | Shadow → advisory → guarded → autonomous exists for a reason |
| **No abstain** | A routine that cannot say "I don't know" is dangerous in variable terrain |
| **No monitoring** | Unobservable autonomy is invisible risk |
| **No version / no owner** | Assurance is version-bound; unowned infrastructure rots |
| **Automation as authority** | Automation cannot grant itself permission |
| **Savings without maintenance** | Counting build-time savings and ignoring lifecycle cost |
| **Permanent legacy** | Keeping routines that stopped paying rent |
| **Routine sprawl** | A thousand micro-automations add more complexity than they remove |
| **Memory note as automation** | Markdown does not guarantee future behavior when recurrence and consequence are high |
| **Invariant too early** | Strong constraints need strong evidence; do not make changing terrain impossible to adapt to |
| **Purple implements everything** | Purple compiles the requirement; Blue builds, Red verifies, Green owns recovery, Yellow owns command rules |

## 13. Sequence

**Compile:** load candidate and source evidence → search existing routines → identify repeated effect, trigger, inputs, outputs → isolate invariant core and variable judgment → estimate frequency, manual cost, maintenance, rigidity risk → determine compilability → select encoding level → define applicability, abstention, failure, rollback, authority, verification → route the build to the right color.

**Validate:** build → local self-check → Sentinel verification → **test outside applicability** → test failure behavior → shadow mode if warranted → compare against manual baseline → promote maturity → register in Capability Registry → index in Artifact Intelligence → hand health to Sustainment → monitor.

**Re-evaluate:** track usage, failures, abstentions, savings, maintenance → detect terrain change → promote, demote, or update → retire when value disappears.

**Before deploying, ask:** Is the behavior actually recurring and stable? What part is truly deterministic and what still needs judgment? What is the lowest sufficient encoding? Can it detect when it should not run? Are inputs and outputs explicit? What happens when it fails, and what side effects propagate? Is it idempotent where needed? Who authorizes it, who verifies it, who maintains it? How many future reasoning steps does it remove — and will it still pay rent after maintenance?

## 14. Metrics

Candidate count, compilation rate, usage, manual work avoided, coordination events avoided, success rate, escape rate, abstention rate, maintenance cost, maintenance-to-savings ratio, shadow disagreement rate, retirement rate, agent capacity released, deterministic provider share.

- `EscapeRate = material failures undetected before effect ÷ executions`. High → demote or redesign.
- **Abstention rate** — very high means applicability is too narrow or terrain too variable; very low may mean overconfidence. Interpret against outcomes.
- `MSR = maintenance cost ÷ manual cost avoided`. Growing too high → simplify or retire.
- **Zero usage** may mean the need disappeared, the routine is undiscoverable, routing broke, or it was a poor candidate. Investigate before retiring.
- **Shadow disagreement** between routine recommendation and qualified agent judgment: high disagreement means not ready, or applicability poorly defined. Investigate — never average blindly.
- **Deterministic provider share** — how much recurring deterministic work is served by routines rather than reasoning agents. A maturing federation increases this, **not toward 100%, but toward the appropriate boundary**.

## 15. Constitution

1. Compile repeated *stable* work, not all work. Repetition does not imply compilability.
2. Preserve judgment where terrain remains variable.
3. Infrastructure must pay rent — count build, maintenance, and rigidity costs.
4. Prefer the least rigid representation that removes meaningful friction. Memory beats a tool when memory suffices; a checklist beats automation when judgment is central; an assertion beats repeated instruction when a property is invariant.
5. Architectural constraints require the strongest evidence.
6. Compile behavior, not conversation. Every routine needs a recognizable trigger and explicit applicability *and* non-applicability.
7. High-consequence routines must be able to abstain; preconditions fail closed.
8. Keep judgment points explicit — split deterministic preparation from judgment from deterministic execution.
9. Automation depth follows consequence and evidence; frequency raises both value and risk.
10. Prefer shadow before consequential autonomy; advisory and guarded are valid long-term architectures. Autonomy is earned and reversible.
11. A routine never creates its own authority. Side effects are explicit, idempotency is specified, stop conditions exist, rollback exists where state is mutated.
12. Autonomous routines are observable; routine state belongs in organizational systems, not hidden logs.
13. Routines are versioned; verification is version-bound; dependency change can stale a routine.
14. Persistent routines need maintenance ownership; Sustainment owns health after deployment.
15. Validated routines are capability providers; Force Generation should prefer them when cheaper and more reliable.
16. Coordination savings and cognitive compression count as force multiplication.
17. Search existing capability before building. Avoid universal tools *and* micro-routine sprawl.
18. Track real usage, savings, maintenance, failures, and abstentions. Retire what stops multiplying force.
19. Do not accelerate a bad process; do not disguise reasoning as infrastructure; do not remove judgment because automation is aesthetically attractive.
20. Natural infrastructure emerges from real missions — most missions spend little or no effort compiling during execution.
21. Repeated deterministic verification, safe recovery, and state reconciliation are the highest-value targets. Repeated human *value judgment* is never an automation target.
22. The goal is not fewer agents. **The goal is to stop spending intelligence on problems the federation has already solved.**

## Done when

```
AGENT REASONS → REASONS AGAIN → PATTERN RECOGNIZED → PROCEDURE EXTRACTED
  → ROUTINE VALIDATED → ROUTINE BECOMES CAPABILITY
  → AGENT NO LONGER NEEDED FOR THE ROUTINE CASE
  → AGENT CAPACITY MOVES TO THE HARDER PROBLEM
```

Each good routine adds a primitive to the federation's instruction set. Cells that could do A, B, C gain `X = A+B+C`, then reason in terms of X — and later `Y = X+D+E`. Capability compounds through **progressive compression of solved work into reliable primitives**, not through more agents or more elaborate orchestration.

**Never spend intelligence twice where reliable infrastructure can remember the solution.**
