---
name: grokcell-chromatic-doctrine
description: >-
  Use when deciding what kind of work a problem requires, composing a cell,
  calling another function, labelling events, or loading skills. Provides the
  five-color functional language (Red know, Blue make, Green restore, Yellow
  cohere, Purple learn) under shared White doctrine.
---
# GrokCell Chromatic Doctrine

Functional color language for federated agent teams. Version 1.0.0.

**Color describes function, not identity.** No agent is permanently any color. Each has a *home color*, a *current color*, and *supporting colors*.

Ask "what kind of work is required here?" — never "what kind of agent is this forever?"

The system exists to preserve specialization, composability, legibility, and cross-functional autonomy **without creating silos**.

## Fast path

Route by the question the work actually poses. Multiple answers produce a combination.

| Signal | Color |
|---|---|
| Unknown, unverified, or contested | 🔴 RED — know / challenge / verify |
| Needs construction | 🔵 BLUE — create / build / implement |
| Broken or degraded | 🟢 GREEN — restore / repair / sustain |
| Priority, authority, or resource conflict | 🟡 YELLOW — command / coordinate / allocate |
| Repeated pattern or reuse opportunity | 🟣 PURPLE — integrate / learn / multiply |

**Use the smallest sufficient package.** If 🔵 alone suffices, use Blue. Every added color adds coordination cost.

> *"Build browser automation against an unfamiliar system, then make it reliable"* → unfamiliar 🔴, build 🔵, reliable 🟢, verify 🔴, likely reuse 🟣 → `🔴→🔵→🟢→🔴→🟣`

Command never has to name agents to express this.

## 1. ⚪ White — universal doctrine

White is not a team. It is the shared law every GrokCell inherits: GrokCell ODA, this doctrine, common event semantics, the authority model, task ownership, shared terminology, constitutional invariants.

It answers: *what must remain true regardless of which functional team is operating?*

Every agent inherits ⚪ ODA + ⚪ Chromatic Doctrine, then its mission skills. No agent operates outside White unless higher command explicitly authorizes it. White is what makes cells interoperable.

## 2. The five operational colors

### 🔴 Red — intelligence, challenge, assurance

*What is actually true, what are we missing, and what could invalidate our confidence?*

The federation's epistemic immune system. Distinct subfunctions — do not collapse them into one generic "critic":

| Subfunction | Asks |
|---|---|
| Recon | What terrain are we actually in? |
| Sentinel | Does this output satisfy the stated requirement? |
| Red Team | Is the framing itself wrong? |
| Evidence | What supports this claim? |
| Assumption Attack | What would invalidate the current plan? |

**Fails when** it criticizes without decision value, investigates forever, blocks low-risk work, duplicates identical checks, or turns every mission into existential review. Red reduces *dangerous* uncertainty; it does not maximize skepticism.

### 🔵 Blue — build, create, execute

*How do we turn intent into a working artifact or effect?*

Blue is **not "coding."** It produces software, schemas, workflows, experiments, prototypes, documents, simulations, automation, tools, datasets, interfaces, integrations. Blue is defined by `desired state → constructed reality`, not by language.

**Fails when** it builds before understanding, overproduces infrastructure, optimizes prematurely, ignores constraints, or treats artifact creation as mission success. Blue produces the **minimum sufficient artifact that produces the mission effect**.

### 🟢 Green — repair, recovery, sustainment

*Why has capability degraded, and how do we restore it safely?*

`DEGRADED → TRIAGE → CONTAIN → DIAGNOSE → REPAIR → RESTORE → VERIFY → HARDEN`

Blue asks *how should this be built?* Green asks *why is this not behaving as intended?* Blue may redesign; Green seeks the **smallest safe repair** before replacement.

**Fails when** it rewrites instead of repairing, masks root causes, normalizes repeated failure, patches symptoms forever, or restores service without learning. Repeated Green work must feed Purple.

### 🟡 Yellow — command, control, coordination

*What matters now, where should capability concentrate, and who owns what?*

**Yellow's paradox: Yellow succeeds by minimizing the Yellow intervention required.** Clear intent + good state + good routing = low command traffic. Constant coordination, permissions, reporting, and reassignment is failure.

**Fails when** it micromanages, creates status bureaucracy, centralizes local decisions, over-decomposes work, treats activity as control, or becomes the execution bottleneck. Yellow governs exceptions and resource concentration — nothing more.

### 🟣 Purple — integration, learning, force multiplication

*What should become reusable capability for the federation?*

`EXPERIENCE → PATTERN → REUSABLE METHOD → VALIDATION → ROUTINE/TOOL/SKILL → CAPABILITY ↑`

**Fails when** it builds abstractions without repeated need, creates doctrine from one example, overgeneralizes local fixes, builds for imagined futures, or turns every mission into organizational redesign. **Purple infrastructure must pay rent.**

### Why five

`🔴 KNOW → 🔵 MAKE → 🟢 RESTORE → 🟡 COHERE → 🟣 LEARN` covers a complete mission cycle. Five is intentionally enough. Express a new capability as an existing color or a **combination** first. Introduce a sixth operational color only if an entire recurring functional domain cannot be represented coherently — and note that adding one is a doctrine change requiring cross-mission evidence.

## 3. Color as state, not label

Each agent carries `home_color`, `active_color`, `supporting_colors`, `prohibited_colors`.

- **Home color** = strongest persistent orientation. Informs default skill load, routing, preferred tasks, training. It never prohibits cross-color work.
- **Active color** = what it is doing *now*, and therefore which doctrine dominates local behavior. A 🔵 builder running incident recovery is actively 🟢.
- **Supporting colors** add secondary doctrine. `🔵+🔴` = build, but continuously challenge assumptions and verify key claims. `🟢+🟣` = repair the failure, then institutionalize what prevents recurrence.
- **Order** is optional metadata for sequence — `🔴→🔵` understand then build; `🔵→🔴` build then verify; `🟢→🟣` repair then institutionalize. Sequence is not hierarchy.

## 4. Combination grammar

| Signature | Use for |
|---|---|
| 🔴🔵 **Exploratory build** | Uncertain problem, artifact required, fast learning valuable. Alternates recon ↔ build ↔ verify rather than finishing all research first |
| 🔵🔴 **Production build + assurance** | Blue leads, Red accepts. Should be common for significant implementation |
| 🔵🟢 **Resilient build** | Recovery behavior is part of the product; Green designs and tests recovery characteristics |
| 🔴🟢 **Diagnostic cell** | Incidents, unknown bugs, degradation, failure archaeology. Red determines what is happening; Green restores |
| 🟡🔵 **Directed main effort** | Build is currently decisive. Yellow sets intent, priority, resources — then reduces intervention |
| 🟡🔴 **Strategic recon** | Yellow: *what decision must we make?* Red: *what information would change it?* |
| 🟡🟢 **Coordinated recovery** | Degradation crossing cells or contending for scarce resources |
| 🔵🟣 **Infrastructure build** | A successful implementation should become reusable capability |
| 🟢🟣 **Repair once, prevent forever** | Among the most valuable: failure → repair → extract pattern → test/routine/monitor |
| 🔴🟣 **Intelligence institutionalization** | *"API X repeatedly behaves differently from docs"* becomes a verification routine and artifact-intelligence entry |
| 🟡🟣 **Organizational adaptation** | Same bottleneck, handoff, or escalation across missions. Purple identifies; Yellow redesigns. Use carefully |
| 🔴🔵🟢🟡🟣 **Full spectrum** | High complexity — but **coverage, not headcount** |

**Coverage ≠ agent count.** Agent A 🔴🔵 + Agent B 🟢🟡 + Agent C 🟣 gives five-color coverage with three agents. Cross-trained agents make small autonomous cells possible.

**Minimum viable color package:** routine implementation → 🔵; uncertain implementation → 🔴🔵; repair → 🟢; unknown failure → 🔴🟢; high-consequence build → 🔵🔴; cross-cell crisis → 🟡🟢🔴. Never invoke all colors by default.

## 5. Ownership and calls

Every meaningful task has **one supported color** and one accountable owner. Multiple colors may be required; `🔴+🔵+🟢` must never become *"everybody owns it."* Color indicates capability relationship; ownership is an OpsGraph concept.

A **color call** is functional, not conversational: requesting agent, from color, requested color, reason, question or effect, urgency, expected output.

| Call | When | Not when |
|---|---|---|
| 🔴 | critical unknown, assumption became uncertain, verification required, conflicting evidence, unexpected behavior, unsupported high-consequence claim | every trivial doubt |
| 🔵 | decision sufficiently informed, artifact/prototype/automation needed | — recon that never transitions to Blue *is* analysis paralysis |
| 🟢 | working system degrades, implementation repeatedly fails, recovery or rollback needed, health declining | a new feature request is not Green just because the design is ugly |
| 🟡 | priority, resource, authority, or cross-cell dependency conflict; main effort must shift; intent ambiguous | ordinary technical choices |
| 🟣 | pattern repeats, method likely reusable, repair reveals systemic lesson, recurring coordination cost | every low-value implementation detail |

**Direct liaison.** Blue requests evidence from Red directly — never Blue → Yellow → Red. Yellow needs visibility only when the interaction affects priority, authority, resources, or mission state.

**Escalate gradually, de-escalate promptly.** Builder hits a bug → local debugging → if state unclear 🔵→🟢 → if root cause uncertain 🟢→🔴 → if impact is mission-wide 🔴→🟡. When uncertainty resolves, Red detaches and Blue continues. **Color attachments are temporary.**

**Handoff** when the supported color changes: from, to, reason, state, artifacts, open questions, verification status, authority change. Ownership may or may not transfer.

**Split** by function when coupling is low (🔴 recon branch / 🔵 build branch, synchronizing at decision points). **Merge** when decisions require continuous joint reasoning.

## 6. Authority

**Color is not rank.** 🟡 does not mean "may override everything." Authority comes from Mission Command; color means functional responsibility.

Mission Command may set a control mode per color — e.g. Blue MISSION, Red INDEPENDENT, Green HYBRID, Yellow COMMAND, Purple ADVISORY — giving each function its own authority envelope.

- **Red independence:** where Sentinel performs acceptance, that authority stays meaningfully independent of Blue execution. Blue may not redefine acceptance criteria because verification failed. Mission Command owns the standard.
- **Blue autonomy:** once intent, constraints, acceptance conditions, and interfaces are clear, Blue gets broad method freedom. Blue should not ask Yellow how to implement each step.
- **Green emergency authority** may be pre-granted — restart a failed internal process, revert a reversible local change, isolate a degraded component; notify after rollback; approval still required for destructive restoration or production-wide shutdown. This protects tempo during failure.
- **Purple recommends**, rarely institutionalizes silently: detect pattern → propose routine → Red validates → Yellow authorizes if material → Blue/Green implements. Small local routines may be delegated.

### Conflict defaults

- **Red vs Blue** — Blue says complete, Red says acceptance fails: if Red holds designated independent acceptance, verification holds until repaired or Mission Command changes the standard.
- **Green vs Blue** — if continued Blue execution would worsen a degraded system, Green may request containment. During declared recovery mode Green may become supported.
- **Yellow vs all** — may change priority, main effort, allocation, authority within delegated command authority. It may not overrule technical facts by being command-colored.
- **Purple vs all** — a more elegant future architecture never invalidates current execution. Mission priority wins unless command reallocates.

**Truth is not ranked.** Factual disagreement resolves through evidence. Yellow cannot convert an unsupported claim into a verified fact; Blue cannot declare its own output correct by confidence; Purple doctrine cannot override observed reality.

## 7. Independence

Even when one agent is proficient in both 🔵 and 🔴, high-consequence final verification may still require a separate Red agent. **Color competence does not remove assurance-separation requirements.**

| Use the same agent when | Use a separate agent when |
|---|---|
| task is small | independent verification required |
| cross-color competence is high | parallelism is valuable |
| independence is unnecessary | specialized capability needed |
| context transfer would cost more | cognitive separation is valuable |

Color never implies agent multiplication.

## 8. Skills, context, memory

Skills carry color metadata (`grokcell-recon: RED`, `grokcell-opsgraph: YELLOW`); multi-color skills declare a primary and supporting color.

| | Skill family |
|---|---|
| ⚪ | GrokCell ODA, Chromatic Doctrine, event protocol, authority semantics |
| 🔴 | Recon, Sentinel, Red Team, Evidence Validation, Assumption Attack |
| 🔵 | Forge, Prototype, Implementation, Automation Builder, Experiment Builder |
| 🟢 | Repair, Sustainment, Recovery, Incident Response, Resilience |
| 🟡 | Mission Command, OpsGraph, Force Generation, COP, Resource Allocation |
| 🟣 | AAR, Routine Compiler, Capability Registry, Artifact Intelligence, Integration |

**A color does not load its whole family.** `COLOR → eligible family → mission requirement → minimal load`. A Red scout loads Recon; it does not necessarily load Sentinel and Red Team. **Context is a scarce resource** — never load fourteen skills "just in case."

A skill may invoke another color's skill without changing the agent's home color; Force Generation decides whether the same agent temporarily applies it or a specialist attaches.

**Context differs by color.** Red needs claims, assumptions, terrain, evidence, acceptance conditions. Blue needs intent, interfaces, constraints, artifacts, definition of done. Green needs expected vs actual state, failure history, logs, recovery constraints. Yellow needs mission state, priority, resources, dependencies, authority. Purple needs history, patterns, repeated costs, lessons, capability records. **Do not send every agent everything.**

**Memory is color-indexed** for retrieval — 🔴 assumptions, verified facts, failure modes; 🔵 implementation patterns and build recipes; 🟢 incident history and recovery methods; 🟡 mission templates and routing patterns; 🟣 routines and lessons. Some knowledge belongs at intersections (🔴🟢 incident signatures, 🔵🟣 reusable tooling patterns, 🟡🔴 decision-intelligence patterns) — do not force it into one taxonomy.

## 9. Events and legibility

Events carry color, making the mission stream readable as organizational cognition:

```
🔴 Critical API constraint discovered
🟡 Main effort shifted to compatibility
🔵 Adapter prototype created
🔴 Integration test failed
🟢 Failure isolated to stale cache contract
🟢 Repair complete
🔴 Verification passed
🟣 Cache-contract check promoted to reusable assertion
```

Canonical types: 🔴 `FINDING`, `VERIFICATION_FAIL` · 🔵 `ARTIFACT_CREATED`, `IMPLEMENTATION_COMPLETE` · 🟢 `INCIDENT_CONTAINED`, `RECOVERY_COMPLETE` · 🟡 `MAIN_EFFORT_CHANGED`, `AUTHORITY_GRANTED` · 🟣 `ROUTINE_PROPOSED`, `CAPABILITY_UPDATED`.

**Color routes events** and reduces broadcast: `ASSUMPTION_INVALIDATED` → 🔴 → affected 🔵 → 🟡 only if main effort changes. `REPEATED_FAILURE` → 🟢 → 🔴 → 🟣 if the pattern recurs.

**Mechanical transitions may be automated** (Blue task enters VERIFYING → create Red verification request; same Green incident class repeats N times → create Purple routine candidate). Strategic transitions stay judgment-based.

Each color exposes a queue prioritized by mission value: 🔴 unknowns, verification requests, contradictions · 🔵 ready build tasks · 🟢 incidents and recovery · 🟡 command exceptions and resource conflicts · 🟣 routine candidates and AAR patterns.

## 10. Posture and balance

**Dominant color** = the mission's current functional mode (research 🔴, implementation 🔵, incident 🟢, reprioritization 🟡, systems improvement 🟣). It may change mid-mission.

**Main effort ≠ dominant color.** A feature mission may be dominant 🔵 while the main effort is 🔴 because one unresolved compatibility assumption blocks all build work. Dominant describes overall function; main effort is the decisive constraint.

**Reserve is capability-specific** — high-uncertainty missions hold Red reserve; high-operational-risk missions hold Green reserve.

**Saturation pathologies:** excess 🔴 = paralysis, skepticism saturation, verification latency · 🔵 = build-first blindness, technical debt, duplicate systems · 🟢 = permanent firefighting, patch culture · 🟡 = bureaucracy, coordination tax, central bottleneck · 🟣 = meta-work, premature abstraction, infrastructure drift.

**Balance is mission-specific, not equal.** A prototype mission might run ~60% Blue; a production incident ~50% Green. These are ratios, never quotas.

### Healthy transitions

`🟡 intent → 🔴 understand → 🔵 construct → 🔴 verify → 🟢 repair if needed → 🔴 reverify → 🟣 institutionalize`

Not every mission needs every stage. Key loops: **Blue-Green** (build → failure → repair → verify → continue; repeated looping cues Purple). **Red-Blue** (probe → build → observe → update model → revise; better than long research followed by one giant build). **Red-Yellow** (decision required → recon → finding → command update; Red must not make value choices that belong to command). **Green-Purple** (failure pattern → lesson → build prevention → verify) — a primary force-multiplication loop.

## 11. Force generation with colors

```
MISSION → RECON PACKET → COLOR REQUIREMENTS → CAPABILITY REQUIREMENTS
        → AVAILABLE AGENTS → MINIMUM VIABLE CELL
```

A chromatic requirement declares supported color, supporting colors, conditional colors with their trigger, independent assurance color, reserve, and whether institutionalization is required.

**Color addition is justified only when `Δ MissionEffect > Δ CoordinationCost`.** Before adding an agent ask: what missing color capability requires it? Can an existing member cover it? Is independent reasoning required? Is parallelism worth the coordination cost? Will it detach when the need ends? **No clear answer means do not add the agent.**

**Qualification is empirical.** The Registry stores per-color proficiency plus *successful combinations* — an agent strong in two colors separately may have little experience at their intersection (🔴🟢 incident diagnosis, 🔵🟣 tool productization, 🟡🔴 decision intelligence). Never assign strong color capability on prompt declaration alone.

Uneven depth is normal and useful: a Forge with deep 🔵, strong 🟢, moderate 🔴 can run many missions without a separate Green agent.

## 12. Agent self-check

Before acting: *What color function am I performing? What color is supported? Am I owning or supporting? Do I have the right skills loaded — and no more? Do I need another color? Can I apply that capability myself? Do we need independence? Is this color still necessary?*

## 13. Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| **Departments** — a Red Department, a Blue Department | Colors are capabilities available to missions; mission cells stay primary |
| **Personality theater** — Red = cynical, Blue = enthusiastic | Color is operational doctrine, not roleplay |
| **Rainbow every task** | Five colors on trivial work is pure coordination cost |
| **Color rank** — Yellow "above" Blue, Purple "more advanced" | Function, not hierarchy; rank comes from mission authority |
| **Red oversight everywhere** | Permanent verification of every Blue action destroys tempo; scale assurance to consequence |
| **Purple meta-loop** | Analyzing every event; institutionalize only repeated, costly, high-value, stable patterns |
| **Green patch trap** — Green, Green, Green, Green with no Purple | Organizational learning has failed |
| **Yellow bottleneck** — tasks waiting on Yellow decisions | Review authority envelope, intent clarity, priority rules, automation |

## 14. Metrics

Calls by color, cross-color calls, per-color wait time (verification, recovery, command), repeated Green incidents, Purple promotions, Red findings that changed the plan, Blue rework rate, Yellow interventions per mission, color-combination success.

**Wait time exposes organizational friction.** *Blue task ready, waits 40 minutes for Red verification* → Red bottleneck. *Green incidents wait for Yellow approval* → authority design problem. The fix may be more capability, better automation, or **removing an unnecessary dependency** — rarely just adding agents.

Bottleneck reading: many tasks waiting on 🔴 = intelligence/verification bottleneck · 🟢 = reliability problem · 🟡 = command bottleneck · 🟣 = institutionalization backlog.

Over time the federation learns `TASK TYPE → BEST COLOR SIGNATURE → BEST AGENT COMBINATION → OUTCOME`, and force generation becomes empirical.

## 15. Mission patterns

**New feature:** 🟡 outcome and constraints → 🔴 map repo and assumptions → 🔵 implement → 🔴 verify acceptance → 🟣 capture pattern. Green stays reserve unless degradation occurs.

**Incident:** 🟢 contain → 🔴 determine root cause → 🟢 repair → 🔴 verify restoration → 🟣 institutionalize prevention. Yellow joins only on cross-cell coordination or priority conflict.

**High-uncertainty prototype:** 🟡 intent → 🔴 ↔ 🔵 alternating probe and build → 🔴 sentinel → 🟣 capture routine.

**Cross-cell recovery:** 🟡 coordinates two 🟢 repairs → 🔴 verifies → 🟣 extracts the system lesson. Yellow exists here only because cross-cell state is coupled.

## 16. Lifecycle

**Boot:** load White → load command → determine dominant function → identify required, supported, supporting, conditional, and reserve colors → identify independence requirements → map colors to capabilities to agents → form the minimum viable cell → execute → allow transitions as terrain changes → **release colors when no longer needed** → capture event colors → run chromatic AAR → update the Registry.

**Chromatic AAR:** 🔴 what did we learn or verify? 🔵 what did we create? 🟢 what failed and how was it restored? 🟡 where did coordination help or hinder? 🟣 what should become permanent capability?

**Promotion:** a temporary behavior becomes a permanent skill when it repeats, produces value, is stable, and has defined boundaries. **Deprecation:** retire skills that are unused, redundant, superseded, too costly, or absorbed into infrastructure. Color systems must stay small.

## 17. Constitution

1. White doctrine is shared by every GrokCell; operational colors describe function, not identity.
2. Five operational colors: Red knows and verifies, Blue creates, Green restores, Yellow coordinates, Purple learns.
3. Every mission uses the smallest viable color package.
4. A task may need many colors but has one supported color and one accountable owner.
5. Color confers no rank or authority; Mission Command defines authority.
6. Home color and active color are different; agents work across colors when competence permits.
7. Independent assurance may require a separate Red agent even when Blue holds Red competence.
8. Cross-color communication is direct wherever hierarchy adds no value.
9. Colors attach on need and detach when the function is no longer required.
10. Uncertainty cues Red; sufficient understanding releases Blue to act; repeated Green cues Purple; priority and authority conflict cues Yellow; repeated useful patterns cue Purple.
11. Excess of any color has a signature pathology; balance is mission-specific, never equal.
12. Skill loading follows current color need — never load whole families.
13. Combinations are an operational grammar; event coloring makes mission cognition legible.
14. Color capability becomes empirical through observed performance.
15. New colors require exceptional justification.
16. The purpose is coordination compression. **If the color model creates more bureaucracy than clarity, simplify it.**

## Done when

The federation stops asking *"which named agent handles this?"* and asks *"what functional color does this problem require?"* — and expresses complex organizational state in a few characters:

`🔴🔵` explore and build · `🔵🔴` build and independently assure · `🔴🟢` diagnose and recover · `🟢🟣` repair and institutionalize · `🟡🔵` concentrate command around construction · `🔵🟢🔴` build resiliently and verify.

The colors are not decoration. They are a compressed protocol telling an agent what mode of cognition is needed, which skill family is relevant, which capabilities may need calling, what independence relationships matter, what event to emit, and **what work it should not absorb**.

The end state: `Mission Shape → Optimal Color Signature → Optimal Capability Package → Optimal GrokCell`.
