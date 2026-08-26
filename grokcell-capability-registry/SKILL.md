---
name: grokcell-capability-registry
description: >-
  Use when deciding who or what should do a task, composing a mission cell,
  checking readiness, recording capability evidence after a mission, or asking
  whether the federation can field a required capability at all. Routes by
  demonstrated capability instead of declared role.
---
# GrokCell Capability Registry

Transactive memory for the federation. Version 1.0.0.

**Route by demonstrated capability, not by declared role.**

The Registry answers one question: *who or what can reliably produce the capability this mission requires right now?* Providers are AGENTS, ROUTINES, TOOLS, or SERVICES — not only Groks.

## Fast path

Stop at the first rung that holds. Most requests stop by rung 3.

1. **A validated routine or tool covers it deterministically** → use it. Do not spend a reasoning agent.
2. **One agent already holds current context and adequate qualification** → assign that agent alone. Done.
3. **A known-good pairing exists for this mission shape** → reuse it.
4. **Coverage needs two or three providers** → pick the smallest set that covers the capability vector, then check independence.
5. **No provider reaches the required level** → emit a capability gap. Do not silently assign an unqualified agent.

Do not run a ranking exercise for trivial assignments. Filter dominated candidates and move.

## 1. Registry vs directory

A directory says `Forge-1 = coder`. The Registry says what Forge-1 has demonstrated, under what verification, with what tools, at what load.

Static titles describe intent. The Registry describes observed capability. Titles do not update themselves; evidence does.

## 2. Capability vs skill

- **Skill** = doctrine or operating procedure (`grokcell-recon`, `Forge`).
- **Capability** = ability to produce a useful effect (`repository archaeology`, `TypeScript implementation`, `lease recovery`).

Reason in capabilities first, then map to skills and providers.

Granularity: `engineering` is too broad; `edit-line-143-of-file-X` is too narrow. Aim for units reusable across missions — `distributed lease design`, `statistical leakage detection`, `incident triage`.

## 3. Object model

```
AGENT ── POSSESSES → CAPABILITY
      ├─ QUALIFIED_FOR → SKILL
      ├─ PROFICIENT_IN → COLOR
      ├─ HAS_ACCESS_TO → TOOL
      ├─ DEMONSTRATED_IN → MISSION
      ├─ PAIRS_WELL_WITH → AGENT
      └─ LIMITED_BY → CONSTRAINT
```

Relationships matter as much as objects.

### Agent profile

| Field | Holds |
|---|---|
| `id`, `status` | READY / BUSY / DEGRADED / OFFLINE / RESERVED |
| `home_color`, `chromatic_profile` | per-color proficiency + confidence (see Chromatic Doctrine) |
| `primary_capabilities`, `secondary_capabilities` | T-shaped: 1–2 deep, several supporting |
| `validated_skills` | with qualification state |
| `tool_access`, `environment_access` | availability, not proficiency |
| `authority_ceiling` | what it may legitimately do |
| `current_assignments`, `current_load` | marginal capacity, not busy/idle |
| `context_affinity` | environments where startup cost is low |
| `known_strengths`, `known_limitations` | with evidence and mitigation |
| `qualification_evidence`, `trust_profile`, `last_updated` | provenance |

The profile is not hand-authored forever. It evolves through evidence.

### Capability provider

Any provider — agent, routine, tool, service — carries: `capabilities`, `readiness`, `cost`, `latency`, `reliability`, `authority`, `tool_dependencies`, `limitations`.

Never ask "which agent can do this?" Ask "what is the cheapest reliable provider of this capability?"

## 4. Evidence

Confidence derives from evidence, and only from evidence.

| Valid evidence | Weak evidence |
|---|---|
| Verified mission completion | Agent says it is good at X |
| Independent Sentinel PASS | Prompt says "specialist X" |
| Repeated success on similar tasks | One unverified attempt |
| Successful recovery, accepted integration | Role title |
| Validated routine, demonstrated tool use | Task count |

Each evidence record carries: agent, capability, mission, role, outcome, verification result, difficulty, independence, artifact, failure context, date, weight.

`EvidenceValue ≈ Outcome × Difficulty × VerificationStrength × Recency`. Do not formalize coefficients before you have data.

**Difficulty scale:** ROUTINE, STANDARD, COMPLEX, NOVEL, FRONTIER. Success on trivial work does not imply elite capability.

### Failure is evidence — after classification

Classify before you downgrade anything:

| Cause | Meaning |
|---|---|
| CAPABILITY | agent lacked skill — this one lowers capability confidence |
| RESOURCE | required tool unavailable |
| AUTHORITY | agent could not act |
| MISSION | objective impossible |
| COORDINATION | interfaces or dependencies failed |
| SPECIFICATION | requirements were unclear |

An agent that says "I cannot do this because capability X is missing" is showing judgment. Record CORRECT ESCALATION, not FAILED EXECUTION. Never penalize honest blockage.

### Decay and requalification

Weight declines with age at a rate set by environment volatility, not by the calendar. General reasoning decays slowly; vendor API knowledge fast; repo architecture in between. Old evidence is never deleted, only reweighted.

Requalify when: toolchain changes materially, skill doctrine changes, a major verification escape occurs, the underlying model changes, the environment shifts, or the capability sits unused past its horizon. Keep requalification lightweight. Do not retest stable capability without cause.

On **model change**, open a new evidence horizon: inherit history, discount it. Same identity is not the same capability.

## 5. Qualification

| Level | Meaning |
|---|---|
| Q0 DECLARED | claim exists, little evidence |
| Q1 OBSERVED | seen once |
| Q2 VALIDATED | verified successful execution |
| Q3 RELIABLE | repeated success on similar tasks |
| Q4 ADVANCED | success on difficult or novel tasks |
| Q5 EXPERT | repeated frontier performance **plus** ability to improve others |

Never promote on age or prestige. Expert should stay rare: it implies diagnosing failure modes, supporting others, creating reusable methods, and adapting doctrine — not just high throughput.

**Proficiency ≠ confidence.** Highly capable with sparse evidence is `proficiency HIGH / confidence MODERATE`. Reliable on easy work with a low ceiling is `proficiency MODERATE / confidence HIGH`. Force Generation needs both.

**Capability ceiling:** record the highest difficulty actually demonstrated. Reliable on routine work does not mean ready for frontier work.

Self-reported claims enter as DECLARED and may steer exploration. They cannot alone establish qualification. Use a targeted qualification challenge only when routing confidence matters and real mission evidence is insufficient — never a synthetic test when live evidence exists.

**Revocation** on repeated verified failures, a major escape exposing a blind spot, or doctrine/toolchain change beyond competence. Record the reason. Do not silently erase history.

## 6. Readiness ≠ capability

Capability is what an agent can do. Readiness is whether it can deploy *now*.

`Readiness = Competence × ToolReady × Authority × LoadAvailable` — one near-zero factor makes the deployment ineffective.

State: READY / LIMITED / DEGRADED / UNAVAILABLE, with `known_blockers`.

Readiness is invalidated by: tool unavailable, context exhausted, critical error, stale environment, too many commitments, authority removed. Capability remains. This distinction prevents pointless retraining.

**Tool access ≠ tool proficiency.** `DeployableCapability = Competence × Access`. A brilliant agent with no repo access is not usable for that mission.

**Load is not busy/idle.** Track task intensity, context-switch risk, and critical-path responsibility. One main-effort task may leave less capacity than three light background tasks.

**Authority:** `EffectiveAuthority = min(RegistryCeiling, MissionGrant)`. The Registry records what an agent *can* do; Mission Command grants what it *may* do this mission. Never conflate capable with authorized, and never hand out credentials merely because an agent is competent.

**Context affinity** lowers startup cost and improves local knowledge. It never means ownership or territory, and it decays much faster than qualification.

## 7. Composition

The Registry supplies variables; Force Generation makes the decision.

`Fitness(C) = Coverage + Complementarity + ContextAffinity + Readiness − CoordinationCost − LoadPenalty − SinglePointRisk`

Keep this interpretable. Do not train an opaque optimizer.

**Minimum cell principle.** Mission needs 🔴 Recon + 🔵 Build + 🟢 Recovery. One agent covering 🔴🔵 plus one covering 🟢 beats three single-color agents when competence is comparable — lower coordination cost. Cross-trained agents are what make small cells possible.

**Independence overrides minimization.** If the mission requires independent Red acceptance, a single agent covering 🔵 and 🔴 is invalid regardless of competence. The Registry exposes competence; Force Generation enforces separation.

**Substitution:** strong static analysis may partially cover manual inspection. Record adequacy and conditions.

**Complementarity:** some pairs multiply — repository archaeology + architecture reasoning; incident diagnosis + runtime tooling. Learn these from outcomes.

**Negative interaction is real:** two builders editing one tightly coupled artifact; two commanding Yellows; agents with identical blind spots. The best team is not the set of individually highest-scoring agents.

**Cognitive diversity** matters for uncertain or adversarial work. Store only coarse, behavior-derived indicators with demonstrated routing value (`evidence-first`, `implementation-first`, `systems-oriented`). Never personality pseudoscience.

**Pairing and cell history:** record mission shape, color signature, agents, outcome, cycle time, rework, coordination cost. Measure mission outcomes, not chemistry. This becomes mission-shape memory: *unknown backend bug → 🔴🟢 → Scout-1 + Forge-2 → strong historical outcome.*

## 8. Scarcity, gaps, and redundancy

**Scarcity** per capability: qualified providers, ready providers, demand.

**Single point:** exactly one deployable provider for a critical capability → flag `CAPABILITY_SINGLE_POINT`. Responses: cross-train, build a routine, document the environment, retain reserve. Aim for two usable providers where economically justified — and redundancy is functional, so *agent + routine* counts.

Healthy redundancy is overlapping capability with complementary strengths, not five identical clones.

**Gap severity:**

| | |
|---|---|
| G0 | minor preference |
| G1 | efficiency reduction |
| G2 | meaningful mission friction |
| G3 | mission blocker |
| G4 | strategic single point of failure |

Gaps must surface *before* heavy commitment. `Gap(C) = Demand(C) − ReadySupply(C)`; persistent positive gaps justify investment.

**Resolving a gap — pick by need shape:**

| Need | Resolution |
|---|---|
| One-time | attach an external enabler (scoped, expiring, not a permanent member) |
| Recurrent, needs judgment | cross-train and qualify an agent |
| Recurrent, deterministic | build a routine (Routine Compiler) |
| Strategic and critical | build redundancy |

Do not resolve every gap by spawning a permanent agent.

**Routing under scarcity:** protect rare experts from routine work when a sufficient cheaper provider exists. Main effort gets the strongest qualified provider; supporting tasks get minimum sufficient capability. Before committing an agent, ask what critical capability that leaves unrepresented in reserve — and answer it.

## 9. Query and routing

A capability request carries: required capabilities with minimum levels, chromatic signature, assurance independence, main-effort flag, resource and reserve constraints, max load.

The response returns **ranked eligible providers with reasons**, plus gaps, scarcity, readiness, pairing history, and deployment risks (capability gap, tool gap, context gap, overload, independence conflict, single-point). Risk does not auto-reject a candidate; it makes the tradeoff visible.

Routing must be explainable:

> Forge-2 selected: Q4 TypeScript, Q3 distributed systems, recent work in this repo, load 0.3, strong 🔵🟢 history, no independence conflict.

That beats "the optimizer chose agent 7." Interpretability is how you debug organizational failure.

### Readiness matrix

| Capability | Provider | Qual | Ready | Color | Tools |
|---|---|---|---|---|---|
| Repository recon | Scout-1 | Q4 | Yes | 🔴 | Yes |
| TypeScript build | Forge-1 | Q4 | Yes | 🔵 | Yes |
| Incident repair | Forge-2 | Q3 | Busy | 🟢 | Yes |
| Stale lease check | Routine-7 | Q4 | Yes | 🟢 | N/A |

The Registry is this matrix, generalized.

### Skill load

Skills consume context. Load only the relevant families and track approximate context cost. Prefer a specialized provider with a small skill load over one omni-agent whose context is saturated.

## 10. Colors

Color proficiency (per Chromatic Doctrine) summarizes broad functional behavior and never replaces specific capability data.

**Home color** is the strongest stable orientation — it may bias default skill load and training investment. It must not become a caste: if observed behavior shows another color is stronger, update the Registry. Reality outranks assignment.

**Combinations are their own capabilities.** 🔴🟢 incident diagnosis, 🔴🔵 exploratory engineering, 🔵🟣 reusable tooling, 🟡🔴 decision intelligence. Strength in two colors separately does not imply strength at their intersection — track the intersection explicitly.

**Color health** aggregates capacity, demand, scarcity, and readiness per color. Do not seek equal capacity across colors. Seek capacity aligned with mission demand.

## 11. Trust

Trust stays multidimensional: mission alignment, evidence quality, completion reliability, authority compliance, escalation judgment, verification history, state discipline, handoff quality. Do not collapse it into one mystical score.

Trust ≠ capability. High capability with poor state discipline is an organizational risk; moderate capability with very high reliability is the right pick for some missions. Preserve the dimensions.

**Calibration:** compare self-reported confidence against outcomes and record over/under-confidence patterns. A well-calibrated agent is preferable for autonomous command because it escalates appropriately. Track whether agents escalate too much, too little, or correctly — this matters most for Yellow, Green, and high-autonomy roles.

**State discipline:** registers artifacts, renews leases, releases ownership, records blockers, produces clean handoffs. Handoff quality is measured by the receiving agent's reconstruction cost.

## 12. Learning loop

```
MISSION → ASSIGNMENT → OUTCOME → SENTINEL EVIDENCE → AAR
   → CAPABILITY UPDATE → BETTER NEXT ASSIGNMENT
```

Updates are evidence-weighted and carry direction (increase / decrease / unchanged) plus confidence change.

**No single-mission overreaction.** One excellent mission does not create an expert; one failure does not erase a record. Exception: catastrophic failure exposing a fundamental blind spot may justify immediate restriction of that capability.

**Live updates during execution:** tool lost, agent overloaded, gap discovered, unexpected strength demonstrated, qualification invalidated. Update readiness immediately when current routing is affected — do not wait for mission completion.

**Feedback sources:** Sentinel supplies verified success/failure and escapes (it does not assign overall rank). AAR exposes routing mistakes, pairing strengths, bottlenecks, unnecessary specialists. Green repair missions reveal hidden diagnostic competence invisible in build metrics. Purple substitution moves demand from agents to routines.

**Capability migration to infrastructure** is the maturity signal: frequent deterministic agent work should progressively become routines and tools, freeing agents for higher-order judgment. Measure it.

**Discovery:** if an agent labeled Scout repeatedly does excellent architecture synthesis, promote the observed capability. Do not force evidence to fit the taxonomy.

## 13. Taxonomy hygiene

Create a capability label only when the behavior recurs, existing labels describe it inadequately, and it has routing value. Merge operationally indistinguishable labels (`repo exploration` + `repository archaeology` → one canonical name). Archive obsolete, unused, or subsumed labels. Version a capability only where the change actually matters.

The ontology must stay small enough to use.

## 14. Integrity

The Registry influences organizational power, so every material change records source, evidence, actor, time, and reason. Agents may submit claims, evidence, and readiness changes; durable qualification upgrades derive from verified mission evidence, AAR, Sentinel results, or system observation. No silent self-promotion.

Evidence is the source of truth; the profile is a projection over it:

```
MISSION EVIDENCE → REGISTRY REDUCER → CURRENT PROFILE
```

Never overwrite history — scoring logic will change, and past evidence must remain re-evaluable. Store evidence, derive qualification / confidence / readiness from it. Do not persist opaque scores with no provenance.

### Events

`AGENT_REGISTERED`, `CAPABILITY_DECLARED | OBSERVED | VALIDATED | UPGRADED | DOWNGRADED`, `QUALIFICATION_REVOKED`, `TOOL_ACCESS_CHANGED`, `READINESS_CHANGED`, `LOAD_CHANGED`, `PAIRING_OBSERVED`, `CAPABILITY_GAP_DETECTED`, `CAPABILITY_SINGLE_POINT`, `CAPABILITY_SUPPLY_REDUCED`.

Status updates through events, never through manual directory edits.

Keep a `registry_snapshot` (agents ready, providers by capability, color capacity, scarce capabilities, gaps, single points, load, reserve, latest updates) so Force Generation never rebuilds state from history.

**Storage:** agents, capabilities, skills, agent_capabilities, skill_qualifications, tool_access, context_affinities, mission_evidence, capability_evidence, agent_load, readiness, pairings, cell_compositions, capability_demand, capability_gaps, registry_events. SQLite is sufficient for an initial federation. Keep it simple.

## 15. Interfaces

| Skill | Supplies → Receives |
|---|---|
| Recon | required capabilities → available capability, gap |
| Force Generation | capability request → ranked providers, gaps, risks |
| Mission Command | posture questions → capacity, scarcity, single-point answers |
| OpsGraph | assignments, task requirements, queue demand → qualified providers, readiness, load |
| Chromatic Doctrine | "this needs 🔴🟢" → who holds validated Red/Green |
| Sentinel | verification results → confidence updates |
| Routine Compiler | — → repeated gaps, single points, routine candidates |
| COP | — → critical gaps, main-effort staffing risk, reserve health only |

COP gets headline capability state, not every qualification detail.

Human judgment is itself a scarce capability (strategic preference, external authority, value judgment, irreversible approval). Represent it. Never treat the human as a worker queue.

## 16. Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| **Omni-agent** — one agent, every skill, every color | Context overload, no independence, single point of failure, weak specialization |
| **Over-specialization** — one capability, one permanent agent | Handoff explosion, idle specialists, fragile cells, bureaucracy |
| **Score worship** — reducing an agent to `87.4` | Hides the evidence that makes routing debuggable |
| **Static registry** — never updated from missions | Becomes fiction |
| **Taxonomy explosion** — thousands of near-identical labels | Unusable ontology |
| **Personality labels** — `creative`, `stubborn`, `smart` | No routing value; convert to observable behavior or drop |
| **Role lock-in** — Scout always researches | Ignores demonstrated broader capability |
| **Universalism** — all Groks are equivalent, same base model | Context, tools, skill load, and history make them operationally different |
| **Specialist hoarding** — cell keeps a scarce expert past need | Starves the federation |
| **Idle expert** — reserve preserved while main effort is blocked | Reserve exists for maneuver; commit it |
| **Gaming** — many trivial tasks, avoiding uncertain missions | Volume is not competence; weight by difficulty and effect |

Target architecture is **T-shaped**: one or two deep capabilities, several useful supporting ones, shared doctrine. Cross-functional does not mean infinitely loaded.

## 17. Constitution

1. Route by demonstrated capability, not static role.
2. Skills describe doctrine; capabilities describe effects.
3. Every material capability assessment has evidence with provenance.
4. Self-description alone never establishes qualification.
5. Proficiency and confidence are separate; so are capability and readiness.
6. Task difficulty is part of every performance judgment.
7. Classify failure before it changes confidence; never punish honest blockage.
8. Tool access, tool proficiency, and authority are three different things.
9. Home color does not constrain active color; color intersections are their own capabilities.
10. Context affinity has routing value but never confers ownership.
11. The strongest agent is not always the best available assignment; load and coordination cost count.
12. Independence requirements override headcount minimization.
13. Critical capabilities avoid unnecessary single points; redundancy is functional, not duplicative.
14. Protect scarce expertise from low-value work; keep reserve visible.
15. Routines and tools are capability providers — prefer the cheapest reliable one.
16. Capability gaps surface before expensive commitment; repeated gaps drive cross-training or infrastructure.
17. Qualification decays only when environment or relevance justifies it.
18. Cumulative evidence rules; catastrophic evidence may still justify immediate restriction.
19. Trust is multidimensional and is not capability.
20. Pairings and cell compositions are learned empirically, not assumed.
21. Registry updates are traceable; no silent self-promotion.
22. The Registry succeeds when each new mission starts with a better answer to *who or what should do this?*

## Done when

- Every provider recommendation names the evidence behind it.
- Gaps and single points were visible before commitment, not discovered mid-mission.
- The chosen cell is the smallest set that covers the requirement and satisfies independence.
- Mission outcome produced at least one evidence record.
- The federation can state what it cannot currently field.
